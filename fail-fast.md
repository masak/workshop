> "With engineering, I view this year's failure as next year's opportunity to
> try it again. Failures are not something to be avoided. You want to have them
> happen as quickly as you can so you can make progress rapidly." &mdash;
> Gordon Moore (as in "Moore's Law"), co-founder of Intel

Perl sometimes swallows errors completely. A typical example is `open`. At its
default setting, the `open` function *doesn't* stop program execution if
opening a file fails; it keeps going, sort of hoping for the best.

The more you write code, the more you will find that that's a bad default. You
want to be notified of errors as early as possible. Which is why you will see
people use the `open ... or die ...` pattern. Better yet, `use autodie;`.
Having the program not report this to you is like that scene in the first
third of a movie when the teenager willfully hides something from the parent,
which directly leads to all the complexity and drama, and only by the end of
the movie does a belated confession happen. "But you could have told me that
the file didn't exist!" &mdash; "I know dad, but I was afraid you wouldn't
love me anymore..." &mdash; "Come here, my sweet child. I will always love
you."

So here's the general principle: make your program a cry-baby. Make it run
screaming to the programmer at the smallest provocation. *Anything* you didn't
expect is a potential error until you say otherwise.

I believe this is actually the path to robustness, strange as it may sound. One
of my math lecturers once said "You'll make 50 mistakes on this course. That's a
*constant*. Be clever and do the exercises; then the mistakes will happen there
and not on the exam." I believe it's the same thing with software development.
Robustness comes from failing early in the process. And then going in and
implementing individual improvements that make the program fail less.

A regex might fail? Match the regex `or die`. Then you'll be notified about
individual places where it fails. Much better than just continuing after the
failed regex, and who knows what might happen.

Don't ignore undefinedness warnings. They're trying to tell you something. As
much as possible, try to *promote* undefinedness warnings into erros which
stop the program. That way, you have to take them seriously.

Sometimes, I have on the order of 50 lines of dissimilar data I want to go
through. I tend to start by handling one of the easy cases, and just doing
`die` on all of the other cases. The program runs for a really short while, and
then dies on the first line it couldn't handle. So I add code for that case.
And I repeat that. A really neat way to make quick progress. In fact, I try to
sort the lines of input in increasing order of length, where that makes sense.
The shorter cases are usually the more simple to handle. This is actually a
kind of Test-Driven Development in disguise.

Oh, and "failing" might happen on many levels, and Perl has excellent support
for failing more or less hard.

    do_something() or die;              Stop the program

    do_something() or return;           Return unsuccessfully from the routine
    do_something() or fail;             (Perl 6) fail routine softly

    do_something() or next;             Try the next iteration
    do_something() or last;             Stop the loop

    do_something() or 0;                Or empty string/list, or undefined, or...

**«** [Previous](ROMAN.md) **|** [Next](end-weight.md) **»**
