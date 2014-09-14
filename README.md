# Operation Plausible Deniability

> Back in 2002, science fiction author Robert J. Sawyer wrote an [essay](http://sfwriter.com/privacy.htm "Privacy: Who Needs It?") about the trade-off between privacy and security, and came out in favor of less privacy. [...]

>> Whenever I visit a tourist attraction that has a guest register, I always sign it. After all, you never know when you'll need an alibi.

> Since I read that, whenever I see a tourist attraction with a guest register, I do the same thing. I sign "Robert J. Sawyer, Toronto, ON" -- because you never know when he'll need an alibi.

-- [Bruce Schneier](http://www.schneier.com/blog/archives/2009/09/robert_sawyers.html "Robert Sawyer's Alibis")

Operation Plausible Deniability (OPD) is a script which randomly uses traffic on the [Tor](https://www.torproject.org/) network.  It does this by building a list of URLs, then randomly visits them over Tor.

While Tor has so far proven, when properly run, to be an effective method for anonymity, encrypted Tor traffic itself is easy to detect over a network connection.  For example, you could be accused of a crime based on time-based monitoring of an exit node versus encrypted Tor traffic originating from your network.  By continually running OPD, you have a plausible deniability venue since you are consistently generating Tor traffic.

## Usage

OPD requires a working Tor installation.  It also requires bash and curl, which should be available on most Unix systems.

OPD requires a source of URLs to use.  By default it uses a URL server at [4dmavioww6random.onion](http://4dmavioww6random.onion/), which simply lists a number of random URLs.  If you do not wish to use this service, set USE_URLSERVER=0, and the fallback will be to query random words against DuckDuckGo's hidden service.  If you use DuckDuckGo, you must have Perl installed, and a usable dictionary.

By default, OPD stores its URL list in /dev/shm, a ramdisk.  After a reboot, it will take an hour or so to build up a large enough URL list.

To run:

    $ ./tor_opd &
