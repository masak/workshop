Create a class `Promise`, with the following properties:

* An object can be in either of the states `PENDING`, `FULFILLED`, or
  `REJECTED`. There's a method `.state()` for querying the state of the object
  (but not for setting it).

* There are methods `.fulfill($value)` and `.reject($reason)` to change the
  state of the object into that respective state. `$value` and `$reason`
  should be stored away so that they can be used in the `then` method.

* However, if the state is already either of these two (i.e. not `PENDING`),
  calling `fulfill` or `reject` should be a no-op, and not change state.

* It should be possible to pass the current state into the constructor.
  (The default is `PENDING`.) If `FULFILLED` is passed in, then a `value`
  argument is required. If `REJECTED` is passed in, then a `reason` argument
  is required.

* There is a method `.then(&onFulfilled?, &onRejected?)` which always
  returns the `Promise` itself, after doing one of three state-dependent
  things:
    * If in `PENDING` state, store the (optional) `&onFulfilled` and
      `&onRejected` callables for later, in their respective queues.
    * If in `FULFILLED`, call `&onFulfilled` immediately, with the
      previously stored `$value`.
    * If in `REJECTED`, call `&onRejected` immediately, with the
      previously stored `$reason`.

In other words, a `Promise` object is a kind of double pipe in which you can
plan for a successful future or a future where things go south. And in the
cases where the future has already been distributed to the `Promise` object,
it just lets things through at once.

Here are some tests to get you started:

    use Test::More tests => 9;

    {
        my $promise = Promise->new;

        my $value = 0;
        $promise->then(sub { $value = shift });
        ok !$value, "Hasn't been fulfilled yet";

        $promise->fulfill("OH HAI");

        is $promise->state, "FULFILLED", "Correct state";
        is $value, "OH HAI", "Code has been run";
    }

    {
        my $promise = Promise->new(state => "FULFILLED", value => "yay!");
        is $promise->state, "FULFILLED", "Already correct state";

        my $value = 0;
        $promise->then(sub { $value = shift });

        is $value, "yay!", "Code ran immediately";
    }

    {
        my $promise = Promise->new;

        my $value = 0;
        my $reason = 0;
        $promise->then(sub { $value = shift }, sub { $reason = shift });
        ok !$reason, "Hasn't been rejected yet";

        $promise->reject("OH NOES");

        is $promise->state, "REJECTED", "Correct state";
        ok !$value, "Fulfill code didn't run";
        is $reason, "OH NOES", "Reject code has been run";
    }

**«** [Previous](abstraction.md) **|** [Next](dry.md) **»**
