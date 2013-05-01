Why do we create classes? Because we want to bundle a bunch of methods around
the same data.

Why do we create grammars? Because we want to bundle a bunch of regexes around
the same source text.

That's the technical side of it, and as a first approximation, it's not
half-bad. Actually the analogy between "grammar" and "class" can run quite
deep, and does run quite deep in Perl 6. (A grammar is a class with a different
`ClassHOW`.)

But there's a more pressing non-technical reason, too. With regexes, the focus
is on the text, and the text is *flat*. With grammars, the focus is on the
resulting match object, and that is *deep*. It has structure. It is a tree.

Steve Yegge makes a [long and elaborate
point](http://steve-yegge.blogspot.se/2007/06/rich-programmer-food.html) about
this: basically, if you can bulid compilers, you can solve a lot of problems
that plague programmers every day. And I think that path starts with grammars.

As an example, think of how various refactoring operations work in a modern
IDE. You can extract methods, rename variables, and other similar things. All
fairly safely and predictably. The IDE is just fixing up the program the way
you want. How does that work? Short answer: by working on the deep structure of
the program. The IDE is working not with the text in the foreground, but with a
tree-like thing in the background where all the methods, statements, and
variables hang off of each other.

Where regexes teach us that "everything's text", grammars teach us that
"everything's structured data". Grammars lift you up from messing with text to
thinking in terms of structures.

Sometimes I do text manipulation tasks with regexes that should reasonably be
done with grammars. I'm lazy just like most programmers, and grammars have a
bit of a higher threshold. Almost invariably, I end up wishing I had used
grammars instead. Just manipulating everything in-place in the string turns
messy really quickly. With grammars, you parse everything into a structure, and
then you can play around with the structure, independently of the source text.

**«** [Previous](SCRAPING.md) **|** [Next](HIGHLIGHT.md) **»**
