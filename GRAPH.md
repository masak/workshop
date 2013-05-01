Implement a `Graph` class that can contain this kind of information. It's up
to you whether to model the nodes and edges internally as separate classes, or
just data structures.

    my $g = Graph->new(
        nodes => [ qw/ A B C D E F / ],
        edges => { qw/ A B   B C   C A
                       C D   D E   D F / },
    );

The edges are *undirected*, so `C` is connected to `D` just as much as `D` is
connected to `C`.

The graph object should be able to return a list of a node's neighbors, and
which nodes are adjacent:

    $g->neighbors("C");             # A, B, D (in any order)
    $g->are_adjacent("D", "E");     # true
    $g->are_adjacent("A", "F");     $ false

Write a method that finds a path between two nodes in the graph with the fewest
number of edges. (There might be several shortest paths. Just return the first
you find.)

    $g->shortest_path("A", "F");    # A, C, D, F

Hint: this can be done with a breadth-first search. Check on Wikipedia or ask
on the channel for further hints.

Throughout all of this, keep a close eye on reference leakage. Make sure your
`Graph` objects don't unnecessarily leak references to internal data
structures.

**«** [Previous](leakage.md) **|** [Next](anemic.md) **»**
