> TODO: Insert let there be light slide and/or 2001 black monolith slide.

Like most ideas, there are a lot of pre-cursors that had some elements of version control, but it's widely agreed that SCCS (Source Code Control System), not to be confused with SCSS, is the first true version control system. The systems that existed before SCCS were mostly about deltas. And while deltas are extremely valuable, they do not make a version control system.

Unfortunately, my research failed me when trying to find any detailed information about pre-cursors to SCCS. I know that systems like IBM's CLEAR (Controlled Library Environment and Resources) and DEC's CMS existed, but I wasn't able to find out much beyond that.

There is a little bit of information about CLEAR from a software engineering technique's conference sponsored by the NATO Science Committee in 1969. CLEAR was a larger system that "tried to assist with the administration and accomplishment of the program development cycle." (http://homepages.cs.ncl.ac.uk/brian.randell/NATO/nato1969.PDF pg. 40) One part of that system used deltas to help with versioning releases, but I was not able to find any other information.

----

Like many projects of the 1970s, SCCS was started at Bell Labs.

In 1972, Marc Rochkind was struggling to deal with change management. In his 1975 paper _The Source Code Control System_, he describes four problems he was trying to solve.

> 1. The amount of space to store the source code (whether on disk, tape, or cards) may by several times that needed for any particular version.
> 2. Fixes made to one version of a module sometimes fail to get made to other versions.
> 3. When changes occur it is difficult to tell exactly what changed and when.
> 4. When a customer has a problem it is hard to figure out what version he has.

It's important to remember that memory was precious at this time. The size of files on disk was important, so an efficient storage format was essential.

Distribution of releases was also difficult. There was no internet. Computers were still only owned by large organizations. If you were distributing software, chances are it was an "enterprise" model and customziations for the customer were common. Dealing with versioning of all these releases was a challenge.

The first version was writen in SNOBOL 4 using the SPITBOL compiler for an IBM System/370 running OS/MVT. That's a lot of acronyms.

> TODO: Insert picture of IBM System/370.

SNOBOL = StriNg Oriented and symBOlic Language
SPITBOL = (Speedy Implementation of SNOBOL)
IBM 370 = https://en.wikipedia.org/wiki/IBM_System/370
OS/MVT = Multiple Programming with a Variable Number of Tasks (A version of OS/360)

They felt that the concept of version control was too out there to win people over with a specification, so they prioritized ease of development. SNOBOL 4 was chosen because of it's expressive power and ease of use. For it's day it was an incredibly powerful language. One person was able to write the initial prototype in three months. Depending on the domain you work in, that might seem ridiculous by modern standards, but you have to remember that this is 1972. We stand on the shoulders of giants. This is quite a few shoulders below us.

The downside of SNOBOL 4 and SPITBOL is size and speed, but that wasn't an issue during the six month trial run.

In the fall of 1973 there were several more projects interested in using SCCS and the decision was made to write a new version. The interested projects were on multiple OS's, but the existing version of SCCS only supported OS/360 still. Instead of writing different versions for each OS (which was standard operating procedure then), the decided to write just one version that would run on a PDP 11/45 under UNIX.

> TODO: Insert picture of PDP 11/45.

Source code would be stored on the PDP 11 and sent to the appropriate machine for compilation. Given the future dominance of UNIX, this turned out to be a wise decision.

----

So, that's all well and good, but how did SCCS work?

> TODO: Add information about SCCS structure.

----

> TODO: Add information about SCCS end of life. When was the last version? When was it last used? Other interesting tidbits.