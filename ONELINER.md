Take these five programs and render them as oneliners. Be as brief as you can.
Be clever.

    # Program 1 -- print the third column of each line
    while (my $line = <>) {
        chomp $line;
        my @columns = split(' ', $line, 0);
        print $columns[2];
    }

    # Program 2 -- treat each line as a number and sum all lines
    my $sum = 0;
    while (my $line = <>) {
        $sum += $line;
    }
    print "$sum\n";

    # Program 3 -- print an empty line after each line
    while (my $line = <>) {
        print $line;
        print "\n";
    }

    # Program 4 -- number the lines
    my $num = 0;
    while (my $line = <>) {
        $num++;
        print "$num. $line";
    }

    # Program 5 -- print everything between START and END
    my $printing = '';
    while (my $line = <>) {
        if ($line =~ /^END$/) {
            $printing = '';
        }
        if ($printing) {
            print $line;
        }
        if ($line =~ /^START$/) {
            $printing = 1;
        }
    }

Take these five oneliners and render them as full programs. Use descriptive
variable names. Define subroutines where it makes sense. Strive for
maintainability.

    perl -pwle 'print "    "'

    perl -nwle 'print if 20..30'

    perl -nwle 'print if $_ eq reverse'

    perl -pwle 's/\bPERL\b/Perl/g and $n++; END { print $n }'

    perl -anwle 'print join " : ", @F[2..4]'
