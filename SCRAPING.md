Take <https://news.ycombinator.com/rss> and parse it *in some way* to yield a
data structure looking like this:

    [
        {
            title => "After 25 years in jail, the Internet blew my mind",
            article => "http://www.salon.com/2013/03/14/after_25_years_in_jail_the_internet_blew_my_mind_partner/",
            comments => "https://news.ycombinator.com/item?id=5620122"
        },

        {
            title => "I long for the future where I can safely assume my passwords are stolen",
            article => "https://medium.com/i-m-h-o/898b8f78b021",
            comments => "https://news.ycombinator.com/item?id=5619995"
        },

        [...]
    ]

There will be CPAN modules or modules.perl6.org modules to help you with some
of the sub-tasks. Ask on the channel.
