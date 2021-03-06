Perl has quite a bit of focus on syntax. The language tries hard not to be in
your way, syntax-wise. Which means that if you find yourself repeating stuff
over and over again in a program, there's probably some Perl syntax you can use
to make things better and less painful.

For example,

    $line =~ s/foo1/bar1/g;
    $line =~ s/foo2/bar2/g;
    $line =~ s/foo3/bar3/g;

Works fine, but can be turned into

    given $line {
        s/foo1/bar1/g;
        s/foo2/bar2/g;
        s/foo3/bar3/g;
    }

Which reduces a bunch of noise. (On older versions of Perl 5, you'd use `for`
instead of `given`.)

Thing is, Perl leaves a lot of the syntax decisions up to you. This is the core
of TIMTOWTDI &mdash; "There Is More Than One Way To Do It". For example, if you
look into [`perldoc perlstyle`](http://perldoc.perl.org/perlstyle.html), you'll
see that there are loose recommendations, but that's about it. There is a wide
recognition that people will have different styles, and not only that, but that
different circumstances will call for different layouts and ways to do things.

That said, there are some style guidelines that we really shouldn't ignore.

> *Choose mnemonic identifiers. If you can't remember what mnemonic means,
> you've got a problem.* &mdash; `perldoc perlstyle`

I can't really emphasize enough how important I think it is to name your
identifiers (variables, classes, constants) well. Usually it takes a while for
the names in my program to "settle": I go back and change them now and then
because I realize there's a better name for something. But making such a rename
can lead to serious improvements in my understanding of the program, which in
turn lead to improvements in the program itself. It's almost a bit scary how
often that happens.

People say syntax doesn't matter. Well, that's true in about the same sense
that it doesn't matter whether an utterance is spoken normally, or SCREAMED AT
THE TOP OF ONE'S VOICE. The same utterance will have the same information
content both times, but one of those will get annoying really quickly. And all
the screaming stops you from thinking clearly about what's said.

What about one-character names, like `$i`? My rule of thumb is that they are OK
in small enough scopes. You probably shouldn't have an important variable that
plays a role in various parts of your program called `$i`, then it should
probably be more like `$number_of_employees` or something. (`$i` is a bit
special too because there's a cross-language convention that that's the name
of an index variable in an outermost loop. So if you must use `$i`, use it
only for that purpose, because using it for something else will confuse
readers.)

Perl's syntax allows you to pick and choose how your code will look. Use that
to your advantage. Make the code highlight what's important in your program.

**«** [Previous](central.md) **|** [Next](GOLF.md) **»**
