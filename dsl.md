DSLs are a slightly contentious topic. The idea is really simple: a
Domain-Specific Language is a "small" language, not meant for everything like
Perl is, but for a specific task or problem.

Just as a simple example, here's a hypothetical bowling DSL:

    frame {
        hit 6;
        hit 2;
    }

    frame {
        hit 7;
        hit 3;
    }

    frame {
        strike;
    }

In some sense, I can see why people think DSLs are over-hyped. They're
basically cute APIs with suggestive naming.

But that's also missing the point a bit. Suggestive naming counts for a lot.
DSLs allow you to pretend for a while that Perl is a much smaller language, one
which contains all the right words for your favorite domain. And that can be
very useful sometimes.

Ruby programmers seem to like to claim that their language is especially
well-suited for building DSLs. I happen to think that Perl 5 and 6 are
well-suited for it too. The biggest difference is probably that Ruby
programmers are a little more attached to cuteness than Perl 5 programmers.
With Perl 6 programmers I'm less sure.

Of course, DSLs also have a price. In some sense, you're leaving the general
language behind and hiding inside of a little fantasy world. That sometimes
pays off, sometimes not. Knowing when to make a DSL and when not to, is key.

See [Martin Fowler's bliki
page](http://www.martinfowler.com/bliki/DomainSpecificLanguage.html) for more
on the topic.

**«** [Previous](HIGHLIGHT.md) **|** [Next](SHIPPING.md) **»**
