So, an object should protect its data, and not allow others to change it. If we
don't enforce that, the object can not reasonably enforce its invariants,
because other players can go in and change stuff at any time.

But this is harder than it first sounds. Just look at this:

    package Company;
    use Moose;

    has employees => (
        is => 'ro',
        isa => 'ArrayRef[Employee]'
    );

Moose helpfully autogenerates a getter for you. And this getter *leaks a
reference* to the `employees` array. Using that, any outside player can go in
and change the contents of the array.

    $c->employees->[1] = Employee->new(name => "MAD MAX");

This is a surprisingly little-known problem. In order to keep its data safe, an
object shouldn't leak references. If it does, it's much harder to maintain the
object's invariants. You have to rely on trusting everyone else not to mess
with your data.

The solution? Redirect the default reader, and provide one that clones the
array and provides a new one:

    has employees => (
        is => 'ro',
        isa => 'ArrayRef[Employee]',
        reader => '_employees',
    );

    sub employees {
        my ($self) = @_;
        return [@{$self->{employees}}];
    }

In this case, the array is shallow, and doesn't itself contain any references.
If it did, we'd have to do a deep clone to be on the safe side.

Be careful! This problem occurs not just when using getter methods, but also
when using constructors and setter methods. In that case, the client code can
simply hold on to the reference they passed into the object, and have an
unprecedented reach to mess with stuff. Now, in the case of Dependency
Injection and other patterns, that's great. But in terms of keeping the object
data consistent, it sucks.

References are great. But they sometimes get in the way to upholding
invariants. Leaking a reference is a bit like accidentally giving the keys to
your house to someone along with your business card. Be aware of leaks.

**«** [Previous](KENYA.md) **|** [Next](GRAPH.md) **»**
