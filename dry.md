So, yeah. Don't Repeat Yourself. Fine.

We've all been there. We copy-paste a bit of code and modify the copy a little.
Because what's the worst thing that can happen? Hehe.

Two months later, or five minutes later, or somewhere in between disaster
strikes. The disaster can be traced straight back to the copy-pasting. We
realize that we should have abstracted things, not duplicated them.

So duplication ends up being the culprit.

That's with code. The same thing happens in relational databases: we normalize
stuff &mdash; keep it de-duplicated &mdash; because we know that if we don't,
it hurts when we come back and want to make an update.

The same principle is applied in both cases: if suddenly you have two
authoritative copies of *something*, and they start to diverge, this usually
spells trouble. And pain.

> "Every piece of knowledge must have a single, unambiguous, authoritative
> representation within a system." &mdash;
> [Wikipedia](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

(Heh. Just learned through
[c2.com](http://www.c2.com/cgi/wiki?DontRepeatYourself) that the opposite of
"DRY" is "WET": "We Enjoy Typing".)

I think the DRY principle is excellent, and correct, and useful. It's a really
good indicator of when you need to refactor. It's just that it has a limit,
outside of which it doesn't apply. For some reasons, people don't tend to talk
about when DRY doesn't apply.

As far as I can see, DRY applies pretty much all-out to code. You want to
remove a *lot* of redundancy from your code. Sometimes to the point of making
your algorithm data-driven.

So let's talk about when DRY stops applying to data.

It doesn't apply when you go "OK, you hold the *master* data, I'm just gonna
make a copy of it over here and store it/project it/render it somehow. If we
diverge, I lose and you win. You're the boss."

So, "views" of data are completely OK. They're OK because they're not
*authoritative* copies; they're slave data, and the master data is always
right.

Anyway, it's not as if we've suddenly "broken" DRY. It's just that we've found
that "authoritative" is the operative word here, and if we're completely clear
on "who owns what", we can start playing around with data, copying it all over
the place. To the uninitiated, it may look like we're breaking DRY, but we're
not.

All this is really good news, because when you can have several views of the
same master data, then the views can start to specialize. Each view can get its
own responsibility, the code gets simpler and more cohesive, we get specialized
models... all sorts of goodness starts to happen.

Actually, it's rather lucky that this loophole to DRY exists; otherwise we
wouldn't even be able to assign from one variable to another with good
conscience.

**«** [Previous](PROMISE.md) **|** [Next](HEX.md) **»**
