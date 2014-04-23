flookup
=======

Fast Lookup - A Quick utility to perform hostname or IP address lookups

Background
----------
Whilst testing something else entirely I had occasion to make sure that a change to an /etc/hosts file was working as expected. Using nslookup here doesn't work, at least not on Linux as it uses the DNS servers specified in /etc/resolv.conf and ignores the host lookup order you may have set in /etc/nsswitch.conf. This makes sense for nslookup (the clue is in the name I guess), but didn't help with my problem. A quick google seems to suggest that people are testing such changes with the application intended to use them, which is fine, but not always the quickest and most practical solution.

Solution
--------
So the solutions was to write a tool to perform host and IP lookups properly, honouring the order in nsswitch.conf. The Python socket library has a couple of functions, gethostbyname() and gethostbyaddr() which work in the correct way.

It's not the best written tool on the planet, but it does it's job pretty well. In cases where the lookup is successful the result is returned to the user very quickly. Lookup failures take quite a bit longer.
