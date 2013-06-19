Between

    if ($state eq "FINISHED") {
        last;
    }

and

    last if $state eq "FINISHED";

...I definitely prefer the latter.

Why? Because I consider `last` to be the important bit of this piece of code.
It's control flow: if this `if` statement triggers, it will have drastic
effects on where in the program we are. (This control flow business is
effectively the only time I use the reversed form of `if` statements. But
people will differ there, and even I'm not 100% consistent.)

In his great book "Perl Best Practices", Damian Conway explains this principle
by saying that people tend to read programs by scanning the "left contour" of
the program code, looking at the beginnings of lines first. So it's wise to put
the important bits there.

But there's another good reason to move important bits up front. In literature,
writing can become more dynamic and interesting by saving surprises till last.
Oscar Wilde and Ambrose Bierce have great quotes that build on this.

> He is really not so ugly after all, provided, of course, that one shuts one's
> eyes, and does not look at him.

> **Absurdity**, n. A statement or belief manifestly inconsistent with one's
> own opinion.

> **Bride**, n. A woman with a fine prospect of happiness behind her.

> **Circus**, n. A place where horses, ponies and elephants are permitted to
> see men, women and children acting the fool.

But this trick fills absolutely no function in a program, where the whole
purpose is to communicate intent, to inform the reader about what's going on.
Sure, it may be less literary and more boring, but it's also easier to read.

Don't save the best till last. Think about what's the most important part of a
statement, and try to shift it to the front, so that the reader sees it first.

**«** [Previous](fail-fast.md) **|** [Next](central.md) **»**
