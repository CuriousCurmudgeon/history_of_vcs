# Who has used Monotone
Who here has heard of monotone? What about used it? Personally, I have no experience with it and hadn't even heard of it until starting to do research for this talk.

# Early Development
The initial release was on April 6, 2003, but I wasn't able to find much information besides that. The initial creator of monotone was Graydon Hoare. Does anybody know what else Graydon Hoare is assoicated with? He's the initial creator of Rust!

It's hard to find much information about the early development of monotone. The mailing list starts on April 9, 2003. Similarly, the IRC logs only go back to Oct. 26, 2005.

> TODO: Read https://graydon.livejournal.com/186550.html
> TOOD: References to monotone in Graydon's livejournal: https://www.livejournal.com/rsearch?page=3&q=monotone&journal=graydon&journalId=218026&searchArea=post
> TODO: I need to move the section on BitKeeper first in the last of DVCS's.

# Strengths
Monotone uses SHA-1 files to identity revisions, much like git.

The SHA-1 is actually used for security with a certificate.

# Weaknesses
Performance is notoriously bad. The project placed a higher emphasis on on integrity instead of performance.

# Monotone Today
Monotone never caught on. It's only real moment in the sun came from Linus Torvalds mentioning that he looked at it before writing git. He discarded it because of the poor performance.

The last release was 1.1 on May 4, 2014. That was over five years ago. Looking through the mailing list, that release seems to have been a last gasp just to package together various patches that that distro packages were accumulating. There have been no commits since, although it's hard to tell because the official source repository seems to be offline.