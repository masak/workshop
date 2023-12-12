Let's place you on a regular Sunday walk in your favorite park. You're wearing
your best Sunday clothes (because it's like 1880 and that's what people do,
they stroll in the park on their day off), brids are chirping, etc.

And then there's that guy. Again.

He's standing on a soap box, like a parody of the kind of political agitator
who usually stand on soap boxes. And he's shouting, every Sunday:

* "The minister of internal affairs is an ass!"
* "The secretary of state is an ass!"
* "The prime minister is an ass!"

Every. Single. Time.

So one day you stop in front of him and go "Dude," (because that's totally how
people spoke back in 1880), "all you ever do is go 'The [INSERT POLITICIAN
HERE] is an ass!' Frankly, it feels like a Monty Python sketch without a
punchline. And what's up with constantly bringing insult on donkeys?"

Well, congratulations. You've just practiced the ancient and noble art of
abstraction. Wearing your best 1880s clothes, at that.

Abstraction means "pulling away". You get to pull apart things that change from
things that remain constant. Or things that matter from things that don't. Or
interface from implementation.

We can do abstraction with subroutines:

    sub insult(Str $politician) {
        return "The $politician is an ass!";
    }

Or maybe we decide that even the "ass" part should be abstracted out into a
general kind of badness, with a sensible default:

    sub insult(Str $politician, Str $badness = "an ass") {
        return "The $politician is $badness!";
    }

Subroutines are great at this: they allow you to go "given these ingredients,
here's how to bake this cake". In this case, given a certain politician and a
possible badness, we can whip up a soap box insult. We've essentially replaced
Angry Soap Box Guy with a very short Perl script.

Objects are also great at this. They're actually very like subroutines, except
that they emphasize their ability to bundle persistent data with behavior:

    class Soapbox::Guy {
        has Str $.badness is rw = "an ass";

        method insult(Str $politician) {
            return "The $politician is $.badness!";
        }
    }

A bunch of other language features help us with abstracting things, too.
Variables. Data structures. Types. Macros. It's all about reaching for the
appropriate tool whenever we find some repetition that can be eliminated.

Apparently there's a principle called the
[abstraction principle](https://en.wikipedia.org/wiki/Abstraction_principle)
that says that you should abstract as often as you can. Cats are great at this:
try making a repeated pattern with your hand in front of a cat &mdash; chances
are it will put its paw on your hand and glare at you, as if they also wanted
to say "Dude", and explain to you that you were repeating yourself. That's how
we should be with our programs. (Cats, however, do not necessarily enjoy wearing
Sunday clothes from the 1880 very much.)

I must confess I stopped reading [The Daily WTF](http://thedailywtf.com/)
because it simply became too painful to me to watch people fail at abstracting
things properly. You probably know the type of post I have in mind; the one
where instead of doing something simple, the programmer copy+pastes a print
statement 2000 times. Made me depressed, so I decided to stop reading that
blog.

In the subsequent sections we will see where this principle can take us.

**«** [Previous](central.md) **|** [Next](PROMISE.md) **»**
