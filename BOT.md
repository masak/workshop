A while back, there was discussion on `#perl6` to implement an IRC bot which
would flag up state changes in whether modules passed tests or not. As an
exercise, implement the core functionality of such a bot.

In essense, this is what we want the bot to do:

* Regularly receive statistics about passing and failing modules.
* Send a message when a module starts failing.
* *Don't* send a message when the module keeps failing.
* Send a message when the module starts passing again.

...and that's about it.

Here, let's summarize this with some tests:

    use Test::More tests => 3;

    sub set_things_up_so_everything_passes {
        my ($tester) = @_;

        $tester->statistics({
            "module C" => "PASS",
            "module W" => "PASS",
        });
        return;
    }

    sub set_things_up_so_something_fails {
        my ($tester) = @_;

        $tester->statistics({
            "module W" => "FAIL",
            "module C" => "PASS",
        });
        return;
    }

    {
        my $tester = Mock::Module::Tester->new();
        my $channel = Mock::IRC::Channel->new();
        my $bot = TestBot->new(
            tester => $tester,
            channel => $channel,
        );

        set_things_up_so_everything_passes($tester);
        $bot->receive_statistics();
        $channel->clear_messages();

        set_things_up_so_something_fails($tester);
        $bot->receive_statistics();

        is_deeply $channel->messages(), [
            "Module W just failed its test suite."
        ], "Bot tells channel when module starts failing";
    }

    {
        my $tester = Mock::Module::Tester->new();
        my $channel = Mock::IRC::Channel->new();
        my $bot = TestBot->new(
            tester => $tester,
            channel => $channel,
        );

        set_things_up_so_something_fails($tester);
        $bot->receive_statistics();
        $channel->clear_messages();

        set_things_up_so_something_fails($tester);
        $bot->receive_statistics();

        is_deeply $channel->messages(), [],
            "Bot keeps quiet when module keeps failing";
    }

    {
        my $tester = Mock::Module::Tester->new();
        my $channel = Mock::IRC::Channel->new();
        my $bot = TestBot->new(
            tester => $tester,
            channel => $channel,
        );

        set_things_up_so_something_fails($tester);
        $bot->receive_statistics();
        $channel->clear_messages();

        set_things_up_so_everything_passes($tester);
        $bot->receive_statistics();

        is_deeply $channel->messages(), [
            "Module W just started passing its test suite.",
        ], "Bot reports when a module starts passing its test suite again";
    }

**«** [Previous](test-2.md) **|** [Next](nesting.md) **»**
