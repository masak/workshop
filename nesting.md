Perl has arrays for ordered sequences of things, and hashes for unordered maps
of things. It's quite nice and good and pleasant.

    my @stooges = ("Moe", "Larry", "Curley");
    # or write it like this: my @stooges = qw<Moe Larry Curley>;

    my %phone_numbers = (
        "Moe"    => "60997021",
        "Larry"  => "77942517",
        "Curley" => "35741912",
    );

And you can index, at which point the sigil of the variable changes to a `$`
(because you're accessing one scalar value):

    say $stooges[0];                # Moe
    say $phone_numbers{Curley};     # 35741912

A nice thing that Perl does is called *slicing*, where you can access a list of
several items by passing in a list of indices or keys. In this case, the sigil
changes from `$` to `@`, because you're accessing a sequence of things:

    say @stooges[0..1];             # Moe Larry
    say @stooges[2, 0, 0, 1, 2];    # Curley Moe Moe Larry Curley
    say @phone_numbers{@stooges};   # 60997021 77942517 35741912

(Not in Perl 6, though. In Perl 6, the sigil remains the same as in the
original variable, whatever you're doing with it. So the above would be
`@stooges[...]` and `%phone_numbers{...}` no matter what in Perl 6.)

All this is pretty great. The one *surprising* thing for people tends to be
that when you put an array or a hash in list context, it *flattens* into its
surrounding context. You won't get any nesting by default.

    my @small = (3, 4, 5);
    my @big = (1, 2, @small, 6);    # gets 6 elements, not 4

In this case, if we wanted a nested list, how would we do it? There are two
ways:

    my @nested = (1, 2, \@small, 6);    # use @small directly
    my @nested = (1, 2, [@small], 6);   # use a clone of @small

Both of these lead to a data structure that looks like this in `Data::Dumper`:

    [
      1,
      2,
      [
        3,
        4,
        5
      ],
      6
    ];

The key is *references*. If you need to brush up on references, let me heartily
recommend [`perldoc perlreftut`](http://perldoc.perl.org/perlreftut.html).
Something nice may also be had from [`perldoc
perllol`](http://perldoc.perl.org/perllol.html), perldoc's most frivolously
named chapter.

I'll just summarize things here with a handy little table:

                            |  scalar      array       hash
    ========================+=====================================
    sigil                   |    $           @           %
                            |
    build                   |               ()          ()
                            |
    index one element       |              $ + []      $ + {}
                            |
    slice several elements  |              @ + []      @ + {}
                            |
    reference to original   |    \$         \@          \%
                            |
    anonymous reference     |               []          {}

Hope that helps.

One last thing: objects are actually not very far removed from this. What
usually happens in Perl 5 is that one takes a hash reference and says "I now
bless you into being... a Node!" or whatever object we're creating. Which means
that hash indexing etc will still work on the object, but so will calling
methods on it.

This holds true even if we're using Moose or Moo or whatver, it's just that we
have to think less about actually handing the hash ourselves. It holds less
true in Perl 6, where objects by default are actually opaque things, and not
hashes.
