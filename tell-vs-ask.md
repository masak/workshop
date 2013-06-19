"Tell, Don't Ask" is one of my favorite object-oriented principles.

It puts into practice how your should think about objects being the owners of
their data, responsible for one particular workflow, and in some sense
incorruptible.

Let's define "Tell" and "Ask":

* **Tell**: sending instructions to the object, which it may accept or reject.

* **Ask**: getting information out of the object.

Now, both of these sound good, right? So why do we recommend the former and
discourage the latter?

Let's take a day schedule as an example. **Tell** would be, for example, "book
this thing at this time" (which may or may not succeed), and **ask** could be
"give me all the bookings for the day".

If clients keep asking for the bookings for the day, they might be tempted to
make their own determinations about overlapping bookings and optimal booking
times and so on. But this is data that belongs to the schedule! And it would be
better for everyone involved if the schedule handled all of the data that
belonged to it, instead of logic leaking out of the schedule class into other
parts of the program.

In some sense, it's about not micromanaging our objects. They've grown up now,
so let them go out into the world and make a life of their own.

The extreme point of this is to design objects that are complete black boxes.
All you can ever really do is tell them things, and see if the object accepts
it or not. It's an interesting way to program, and it works surprisingly well.

A new-ish movement in programming called CQRS (Command-Query Responsibility
Segregation) builds partly on this principle: to separate **tell** and **ask**
into completely different objects in the system. The "tell" objects are
excellent for business logic which shouldn't leak out to the rest of the
system. The "ask" objects make excellent derived views of the "tell" objects.

TimToady pointed out during the workshop that introspection is another example
of "tell, don't ask" being broken. In that case, we're leaking logic out of the
language and type system itself, trying to rebuild our own (probably weaker)
version of it from the outside.

Consider making your classes more focused by leaning more heavily on telling
your objects things, not asking them and risking logic leaks.

**«** [Previous](HEX.md) **|** [Next](KENYA.md) **»**
