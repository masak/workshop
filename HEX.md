A hex board looks like this:

    . . . . . . . . . .
     . . . . . . . . . .
      . . . . . . . . . .
       . . . . . . . . . .
        . . . . . . . . . .
         . . . . . . . . . .
          . . . . . . . . . .
           . . . . . . . . . .
            . . . . . . . . . .
             . . . . . . . . . .

The "columns" are labeled `a..j` from left to right. The rows are labeled `1..10`
from top to bottom. So the upper left corner is `a1` and the lower right corner
is `j10`.

Each cell on the board can have a black stone, a white stone, or be empty.

Your taks is to find "third-row templates". They look like this:

       O _
      _ _ _
     _ _ _ _
      x x x

The cell marked `O` should be either a black stone or a while stone. The cells
marked `_` have to be empty. The `x` things are either all stones of the same
color as the `O` stone, *or* (more commonly) actually outside of the board.
This is called an "edge template" because it typically connects to some edge
or other. The template can be rotated or *mirrored* in all possible ways.

Example:

    . . . . . . . . . .
     . . . . . . . . . .
      . . . . W . . . . .
       . . . . . . . . . .
        . . . . . . . . . .
         . . . . . . . . . .
          . . . . . . . . . .
           . . W . . . . . . .
            . . . . . . . . . .
             . . . . . . . B . .

This would output something like this:

    Template at e3: empty cells d1 e1 f1 g1 d2 e2 f2 d3
    Template at e3: empty cells e1 f1 g1 h1 e2 f2 g2 f3
    Template at c8: empty cells d8 b9 c9 d9 a10 b10 c10 d10
    Template at h10: empty cells j7 i8 j8 h9 i9 j9 i10 j10

The order of the templates and the empty cells doesn't much matter, though.
Just need to find all the possible templates.

**«** [Previous](dry.md) **|** [Next](tell-vs-ask.md) **»**
