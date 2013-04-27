Time to implement a small subset of jQuery, which is a good example of a
composable API.

Create two classes, `Element` and `Text`, to support this simple kind of
representation of an HTML document object model (DOM):

    my $body = Element->new(tag => "body", children => [
        Element->new(tag => "h1", children => [
            Text->new(text => "Gettysburg Address"),
        ]),
        Element->new(tag => "p", class="intro", children => [
            Text->new(text => "Four score and seven years ago our fathers brought forth..."),
        ]),
        Element->new(tag => "p", children => [
            Text->new(text => "Now we are engaged in a great civil war..."),
        ]),
        Element->new(tag => "p", children => [
            Text->new(text => "But, in a larger sense, we can not dedicate..."),
        ]),
        Element->new(tag => "ul", children => [
            Element->new(tag => "li", class="intro", children => [...]),
            Element->new(tag => "li", children => [...]),
            Element->new(tag => "li", children => [...]),
        ]),
        Element->new(tag => "ul", children => [
            Element->new(tag => "li", children => [...]),
            Element->new(tag => "li", children => [...]),
        ]),
    ]);

Create a subroutine `query` which wraps any DOM object you give it in a
*selection* object:

    my $qb = query($body);

The selection object is conceptually a set of DOM nodes. It supports a `find`
method, which searches all the descendents of the selection:

    my $uls = $qb->find("ul");  # a new selection with the two ul elements

`find` is non-destructive. It just returns a new selection, and leaves the
original one in place.

If the selection contains several DOM nodes, the `find` method searches all of
them, and returns the result as a single selection.

    my $lis  = $uls->find("li");    # a selection with the five li elements
    my $lis2 = $qb->find("li");     # same five li elements

It should also be possible to search for classes:

    my $intros = $qb->find(".intro");   # the first p and the first li

A selection should have methods `addClass` and `removeClass`, which manipulate
the class attribute in the appropriate way on all the DOM nodes in the
selection:

    $intros->removeClass("intro");
    $intros->addClass("introduction");
