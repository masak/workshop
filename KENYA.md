*Kenya Believe It! Tours* is a postmodern travel company in east Africa.
They're doing rather well. (Smaller competitors in the area are *Uganda See
This! Tours* and *Boaty in Djibouti*, and *Do the Congo! Tours*.)

Write a tour allocator for *Kenya Believe It! Tours*. Given a set of tours,
vehicles, and drivers, the allocator should find a (unique) driver and a
(unique) vehicle for each tour. Furthermore,

* The vehicle must be big enough to hold the number of passengers already
  booked on the tour.

* The driver must have a permit for the vehicle.

Because the tour company wants to save fuel, also try to cleverly book the
vehicles such that you don't unnecessarily use (say) a bus, when a jeep would
do.

Here's a test to get you started:

    use Test::More tests => 1;

    my @tours = (
        { name => "Giraffe climbing", passengers => 10 },
        { name => "Drive-by Lion Taunting", passengers => 2 },
    );

    my @vehicles = (
        { name => "J1", type => "Jeep", capacity => 4 },
        { name => "B1", type => "Bus", capacity => 20 },
    );

    my @drivers = (
        { name => "Guy", permits => [ qw/Bus Jeep/ ] },
        { name => "Lester", permits => [ qw/Jeep/ ] },
    );

    my %allocation = allocate(\@tours, \@vehicles, \@drivers);

    is_deeply \%allocation,
        {
            "Giraffe climbing"       => ["B1", "Guy"],
            "Drive-by Lion Taunting" => ["J1", "Lester"],
        },
        "allocated to vehicles with enough passengers";

**«** [Previous](tell-vs-ask.md) **|** [Next](leakage.md) **»**
