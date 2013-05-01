I did something stupid a few years back. I downloaded a CPAN module &mdash;
don't remember which one anymore &mdash; that would generate all possible
permutations of an array. I fed it an array of 20 elements and asked it to
give me all of the permutations so that I could loop over them. I ran the
program.

And waited.

And waited.

It was somewhere around here that I started reflecting whether I hadn't carried
over a Perl 6 assumption to this Perl 5 CPAN module.

Often enough, you end up in a situation where one bit of a program *produces*
items, and another bit of the program *consumes* them. This happens
surprisingly often. Laziness is simply the idea of not having to run the code
to produce something until the consumer asks for it. Producer and consumer
take turns doing their bit.

Unix pipes work (almost) like this, by the way. All sections of the pipe run in
parallel, blocking on earlier sections can't keep up generating stuff.

Truth is, it's a wonderful way to separate concerns. Instead of entangling the
producer code and the consumer code, you can keep them apart. Smaller pieces;
more cohesive. And both producer and consumer code can potentially be re-used
and plugged into other things.

In Perl 6, we have `gather` as our flagship laziness construct. But many other
common builtins, such as `map` and `grep`, will also work lazily by default.

Laziness saves memory. On the way, you get the ability to handle not just the
very large, but also the potentially infinite.

    $ perl6 -e 'constant @fibs := 0, 1, * + * ... Inf; say @fibs[10]'
    55

Laziness is also a bit of a hazard. Haskell is all beautiful and lazily
evaluated, for example &mdash; but the backside of this is that the execution
model is harder to understand and reason about. Even Perl 6, where we limit
laziness to lists, has had to navigate a few reefs to make sure laziness
doesn't bit people. The problem is when people use laziness but don't expect
to.

For non-lazy languages like Perl 5, hope is far from lost, since the Iterator
pattern will easily step up and emulate laziness for you. You just have to make
do with doing all of your producing-consuming through some (object) API or
other, rather than a language feature.

An iterator, at its simplest, is an object with two methods:

* `.has_next()`, which returns a Bool indicating whether there's something left
  to iterate over.

* `.next()` which steps to the next thing, and returns it.

**«** [Previous](PLAYLIST.md) **|** [Next](FRINGE.md) **»**
