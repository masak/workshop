Anemic APIs have problems expressing the users wishes effectively. It's not
that you can't *do* everything &mdash; you can &mdash; it's just that what
should be powerful, swiping workflows instead feel like sucking your workload
through a very thin straw. The "bandwidth" of the API somehow isn't enough
for the complexity of the domain.

This is far too common, unfortunately.

People tend to describe this as application builders thinking of their
applications as big HTML forms or (poor-man's) Excel spreadsheets, where the
only operation is "update".

Whereas what you *can* do is "focus on the verbs". What verbs are natural when
interacting with your API? Try different ones &mdash; which one works best?

Verbs carry *intent*, often not just about what you're updating but also *how*
and *why* you're updating. They're often a step up from just "update".

Lately, I've come to think about these APIs as not just anemic, but *amnesiac*,
too. The API doesn't remember where you were and what you did five seconds ago.
And it probably doesn't care where you're going, either. As programmers, we
should zoom out from just accepting or rejecting the latest request, and think
about the workflow that the user is in.

Example: I was using PayPal, and it popped up a message saying something like:
"Hey, you just had money transferred to your PayPal account, and the next step
is probably to transfer it to one of your bank accounts, but I notice you don't
have any bank accounts tied to your account. Would you like to add one?"

The PayPal system detected that I was at a certain place in a workflow and that
a certain condition held so that the probable next step would be impossible, so
it suggested an action for me. Nice. That's service!

It's easy to accidentally make our APIs anemic and amnesiac. We should aim
higher.

**«** [Previous](GRAPH.md) **|** [Next](INTENT.md) **»**
