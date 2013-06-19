Here's a typical program:

    input ----> [do stuff] ----> output

Typically the middle part, "do stuff", is the interesting one. Perl shines a
bit extra there. The typical backronym for Perl, "Practical Extraction and
Reporting Language" focuses on Extraction (input handling) and Reporting
(output handling), but truth is Perl (5 and 6) is quite good at handling the
middle bit as well.

When I want to solve a quick input/output problem of this kind, I tend to first
think if I can do things with a one-liner. Is my input a set of lines of
comma-separated values, and I want to sort them?

    48, 33, 100, 5, 14
    9, 17, 34, 8, 19, -6

No problem, that's just a one-liner:

    $ perl -pwle '$_ = join ",", sort { $a <=> $b } split /,/' input
     5, 14, 33,    48, 100
     -6, 8,    9, 17, 19, 34

(To be read "backwards": the script splits on commas, sorts numerically, and
then joins on commas again.)

The nice thing about Perl (5 and 6) is that I can be brief like this when I'm
doing one-off things, but I can also be explicit and clear when I'm writing
programs that I or others will keep around and maybe extend or maintain.

Just to show the difference, here's the same problem solved but in script form,
where attention is paid more to structure and naming:

    use strict;
    use warnings;

    local $\ = "\n";    # newline at the end of each line printed
    while (my $line = <>) {
        chomp $line;
        my @values = split /,/, $line;
        my @sorted_values = sort { $a <=> $b } @values;
        print join ",", @sorted_values;
    }

Both modes are great. You can be brief and succinct when you need to, and the
shortcuts of Perl will often work in your advantage in nice ways. But you can
also be more discursive and explicit, so that it's easier to maintain.

**«** [Previous](GOLF.md) **|** [Next](ONELINER.md) **»**
