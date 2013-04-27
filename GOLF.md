Here's a working program that produces the solutions to the 8-queen problem.
(92 solutions, though some of them will be rotations and reflections of each
other.)

    #! /usr/bin/perl
    use strict;
    use warnings;
    use 5.010;

    sub all_unique {
        my %seen;
        for (@_) {
            return if $seen{$_}++;
        }
        return 1;
    }

    sub vertical_clash {
        my ($rows_ref, $v) = @_;

        return !all_unique(@$rows_ref, $v);
    }

    sub diagonal_clash {
        my ($rows_ref, $v) = @_;

        my $i1 = 0;
        my @diagonals1 = map { $_ - ++$i1 } @$rows_ref, $v;

        my $i2 = 0;
        my @diagonals2 = map { $_ + ++$i2 } @$rows_ref, $v;

        return !all_unique(@diagonals1) || !all_unique(@diagonals2);
    }

    my $MAX_N = 8;

    sub try_row_n {
        my ($n, $values) = @_;

        if ($n > $MAX_N) {
            say "[", (join ",", @$values), "]";
            return;
        }

        CANDIDATE:
        for my $new_value (1 .. $MAX_N) {
            next CANDIDATE if vertical_clash($values, $new_value);
            next CANDIDATE if diagonal_clash($values, $new_value);

            my $new_values = [@$values, $new_value];
            try_row_n($n + 1, $new_values);
        }
    }

    try_row_n(1, []);

Now write a program that does the same in as few characters as possible. I once
got this program golfed down to fit inside a signature block (80 chars x 2
lines). You can probably do better.
