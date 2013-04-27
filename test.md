Let's say I wanted to write a function that would repeat a string up to a given
length. Where would I start? I would probably start with a simple test, something
setting up an expectation for the function:

    is repeat("again", 20), "againagainagainagain";

So I'm testing that when I pass the 5-character string `"again"`, along with
the desired length 20, I get a 20-character string back. (I was tempted to
write `"again" x 4` there instead. Just so you know.)

Then I go ahead and implement the code that makes that pass:

    sub repeat {
        my ($substring, $length) = @_;
        my $repetitions = $length / length $substring;
        return $substring x $repetitions;
    }

And then I would think if there's any situation I'm still not covering. In this
case, yes, there is: I'm only testing when a (5-char) substring fits exactly a
whole number of times into the expected length (20 characters). What about the
case where it doesn't?

So I write a new test:

    is repeat("bla", 10), "blablablab";

And I can observe the test fail:

    1..2
    ok 1
    not ok 2
    #   Failed test at repeat line 10.
    #          got: 'blablabla'
    #     expected: 'blablablab'
    # Looks like you failed 1 test of 2.

So now I know what I have to go back and fix. In this case, I just change the
end of my subroutine, so that it looks like this instead:

    sub repeat {
        my ($substring, $length) = @_;
        my $repetitions = $length / length $substring;
        my $rest = substr($substring, 0, $length % length $substring);
        return $substring x $repetitions . $rest;
    }

And now my tests pass:

    1..2
    ok 1
    ok 2

I like tests. They tend to guide development, point out bugs early, ease
debugging, and form a practical means of communication between developers.
To me, tests are not "an extra thing". They are an important 50% of your
program; the part that makes sure your expectations are in sync with your
implementation.

Because tests are the best way I know to communicate requirements, the form a
part of most exercises.

Seriously, if I could give people one piece of advice for how to better
themselves as programmers, it's to boost up their unit testing skills. It pays
off amazingly.
