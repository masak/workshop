Testing plays a central role in a lot of domains, so I thought we'd come back
to it here.

* Evolving the domain
* "Knowledge crunching" (learning from the code and making the design better)
* Giving courage to refactor when needed
* Debugging

I think the point where people "get" testing might be when they realize that we
can put the thing we want to test into a "fake" environment, and test its
interaction with that whole environment. That's faster, safer, more convenient,
and less messy than putting the thing in a real environment.

People call this "Dependency Injection". A rather big name for a simple
principle: instead of the object itself deciding what other objects it needs,
we give it a set of objects with the right methods. Do we really need an actual
email sender? No, we need an object that resonds to a `.send($recipient,
$message)` method call. Do we really need a database? No, we... and so on.
