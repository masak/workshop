We talked about laziness, where we want to decouple producer and consumer a
bit, and also make life easier for the producer.

Let's talk about the observer pattern, which also decouples producer and
consumer. But now the focus is on making life easier for the consumer. Instead
of completely blocking and waiting for the consumer to come back with a result,
the producer just leaves its business card, says "you know where to reach me",
and gets on with its own code.

This is great for building any kind of "reactive" system with many parts that
need to function independently of each other. GUIs are one example. Web
applications and web services are another. Event-based systems in general.

For laziness, the iterator (on the producer's side) was the object of exchange.
In this case, it's an observer (on the consumer's side) that interests us. The
observer object can *subscribe* to an observable on the producer's side. The
observer has three methods:

* `.on_next()`, called for each item produced.
* `.on_completed()`, called when there are no more items left.
* `.on_error($error)`, called when something goes wrong in the producer.

The really cool thing here is that the observer pattern is the "dual", in a
very real sense, of the iterator pattern. They are opposites of each other in
the following sense: the iterator interface has three methods that all produce
something, but the observer interface has the *same* three methods that
*consume* something.

    Iterator            Observer

    .has_next()         .on_completed()
    .next() (success)   .on_next()
    .next() (excpetion) .on_error()

Kind of cool. This fact went unnoticed for decades, it seems. From 1991 when
the "Design Patterns" book was published, and up until the time when Microsoft
Research started developing Reactive Extensions for .NET.
