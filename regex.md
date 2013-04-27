Maybe you've heard horror stories about job interviews where programmers were
asked to extract names and phone numbers from a data file containing phone book
information, and they spend an hour writing weird contortions with substrings
and string indices and stuff...

Well, regexes are what makes us do something quickly and easily in such a
situation. They're a language for matching and manipulating strings.

They're meant to be used [swinging from a liana in the
roof](http://xkcd.com/208/).

Under "Expert" (stage 4) in [Seven Stages of a Perl
Programmer](http://jwenet.net/notebook/2005/1075.html), we find the item
"Begins to look at all data in terms of regular expressions." I think that
captures some of the Perl spirit quite well. Many, many problems can be reduced
to *textual* problems, and munched from there. Example: someone once solved a
problem [6 million times as fast as my
solution](http://strangelyconsistent.org/blog/speed-up-by-a-factor-of-6-million),
by thinking of it as a textual/regex problem.

See [this handy guide](http://www.perlmonks.org/?node_id=42330) to the stages
of regex mastery.

If you feel new with regexes, spending a bunch of time in this section will
greatly reward the rest of your Perl mastery. Maybe start with [`perldoc
perlrequick`](http://perldoc.perl.org/perlrequick.html) and [`perldoc
perlretut`](http://perldoc.perl.org/perlretut.html) and work upward? [`perldoc
perlre`](http://perldoc.perl.org/perlre.html) is nice too.

If you're on a Perl 6 quest, starting with
[`JSON::Tiny::Grammar`](https://github.com/moritz/json/blob/master/lib/JSON/Tiny/Grammar.pm)
and [S05](http://perlcabal.org/syn/S05.html) might be a nice combination. But
S05 is quite big, and it's a really good idea to combine reading it with
talking to other Perl 6 people, and writing small stuff on your own to try
things.
