The fringe of a binary tree is all the leaves in the order we find them if we
traverse the tree from left to right. (Inorder traversal.)

Like so:

      *
     / \
    a   *
       / \
      b   c

The nodes with stars are irrelevant. We just care about the leaves. Traversing
the leaves, we find them in the order a-b-c.

Well, we do for this tree as well:

        *
       / \
      *   c
     / \
    a   b

It also has the order a-b-c. So these two different trees have the same
fringe.

Write a program that, given two binary trees, finds out whether they have the
same fringe.

Just to tie this back to laziness: while we *could* just traverse both trees at
once, finding all the leaves, and then comparing the fringes, it feels like we
could use laziness to separate these tasks. That way, we won't have to traverse
more of the trees than necessary &mdash; we could stop at the first difference.

Oh, and there's a Perl 6 solution for this problem. But try writing your own.

**«** [Previous](lazy.md) **|** [Next](observe.md) **»**
