SCCS development started in 1972 and the first public version was released in 1977. It wasn't until 1982 though that Walter F. Tichy started work on RCS at Purdue.

> TODO: Insert slide with picture of Walter F. Tichy.

Tichy, born in 1952, is a German computer scientist who received his MS and PhD from Carnegie Mellon in 1976 and 1980 respectively. After that he served for six years on the faculty of Purdue University. It was during his time at Purdue that he developed RCS.

> TODO: Insert slide for RCS = Revision Control System

Who here has ever used RCS? I can actually raise my hand for this one. During the summer of 2006 I was an undergraduate research assistant. All of the source code and LaTeX for the research's paper was stored in RCS. I didn't know much about version control in 2006, but I remember raising my eyebrows about it even back then.

----

So, why did Tichy create RCS and what advantages did it have over SCCS? Let's look at his 1982 paper _Design, Implementation, and Evaluation of a Revision Control System_.

Reading through these old papers is a delight, so I'm going to pull out some choice parts while we go through the advantages of RCS over SCCS.

Right away in the introduction we get reminded that even in 1982 software was never done.

> An important characterist of software is that it changes constantly. The plasticity of software fosters a mode of development in which modification of a released software product is the norm rather than the exception.

The core operations of RCS are very simple. _ci_ for checkin and _co_ for checkout. So, if you wanted to create the initial revision of a file you would do

> $ ci -i demo.txt

The _-i_ indicates that the file must be initialized. This creates _demo.txt.v_ on disk. The _.v_ sufix is an RCS convention. It's very important to note here that RCS, like SCCS, does revisions on one file at a time.

Then, when you want to modify _demo.txt_ you can run

> $ co demo.txt
> ... make your modifications
> $ ci demo.txt

to check it out and commit your changes.

Revision numbers have a similar concept of releases and levels to SCCS. Also similar to SCCS, you can do some reasonably powerful searching to checkout a specific revision by criteria beyond an exact revision number.

RCS also locks files. If you need to lock a file you can do so on checkout with

> $ co -l demo.txt

You can also pass _-l_ on checkin to keep the lock. This will keep your working copy of the file too. Without that flag RCS would remove it.

RCS does support branches, but I don't have any information on how often they were used. My guess would be rarely.

> TODO: Insert picture from paper of branch tree.

This is an example of branching. We can see that each fork appends a another number to the version. You can also give a friendlier label to the branches as an alias. One possible usage for this is to manage releases. If you create a labeled branch for every file, then you can retrieve every file for a release with

> $ co -rconfig1 *.v

These friendlier labels is something that SCCS did not provide.

> The important aspect of the log message is that RCS reminds the programmer to supply the information. Of course, an uncooperative person may answer with an empty message, but his name is recorded anyway.

Software developers. Providing poor commit messages since the dawn of version control itself.

There were also some auxilary commands. The most interesting of them is _rcs_, which lets you break locks. Even using RCS on a very small project in college, people forgot to release locks on a regular basis. Interestingly, breaking the lock also sends an email to the person who held the lock.

RCS also copied the _sccsid_ concept from SCCS. As far as I can tell, this is the last major version control system to use this concept.

RCS departs from SCCS in the way it stores deltas. SCCS stored all the deltas interleaved with each other. Interleaved deltas have a couple of performance characteristics.

* The time it takes to retrieve any revision is the same. The whole revision file must be scanned no matter what.
* Inserting a new delta is more complicated. First the old revision must be regenerated, diff'd with the new revision, and then the new delta info in interleaved.

RCS instead uses reverse deltas. The newest revision is stored intact, since that is what you will usually want to check out. If you want to go back one revision, you take the newest revision and apply a reverse delta to go back to that revision and so on to go back to any revision in the history. Adding a new revision is just getting the latest revision and executing diff to get the reverse delta. Then concatenate new revision and the new reverse delta to the already existing deltas. Done.

Of course, the disadvantage here is that going further back in history is more expensive. There is also additional complexity with branching with forward deltas being used on non-trunk branches for storage reasons.

TODO:
* Better integration with MAKE (see pg. 15 for details)
* Performance comparison of SCCS's interleaved deltas vs RCS's reverse, separate deltas. (pg. 17)

A big advantage of RCS is that it was designed to be easily used with MAKE. SCCS pre-dated MAKE, so it was unnecessarily difficult to integrate the two. The big difference is that the file naming conventions of RCS were designed to be easily used with MAKE.

Tichy also noted that the access control of SCCS could be too strict. In practice, everybody ended up needing the extra privilege of needing to break locks, but breaking a lock left no trace. This led to RCS allowing anybody to break a lock, but sending an email to the holder of the lock when it is broken.

Also, he notes that the identification mechanism (_sccsid_) is not used in practice because of it's complexity. His hope was that RCS's system would be much easier to use, but I don't have any information on how true that was. If anybody here is an RCS guru, I would love to hear your take on it.

SCCS provided no mechanism for merges either. RCS branches do support merging, but it's not clear how good that was in practice. Wikipedia implies that teams mostly used locking on a single head branch instead of branching. That seems likely, but I did not attempt to validate that claim at all.

One big thing that RCS was missing (at least in 1982. I didn't check if it was added later), is checksumming. SCCS did this.

----

RCS is also a bit of case study in the evolution of open source licenses. Through version 3, which was distributed in BSD 4.3, it had the following license.

> Copyright (C) 1982 by Walter F. Tichy [...] All rights reserved. No part of this software may be sold or distributed in any form or by any means without the prior written permission of the author.

This license looks crazy today. You needed the explicit written permission of Walter F. Tichy to distribute RCS! This was true until 1989 when the license was altered to

> Redistribution and use in source and binary forms are permitted provided that the above copyright notice and this paragraph are duplicated in all such forms and that any documentation, advertising materials, and other materials related to such distribution and use acknowledge that the software was developed by Walter Tichy.

This is pretty similar to BSD licenses of the day. It's just missing anything about using the Walter Tichy's name to endorse or promote derived products and anything about the software being provided _as is_.

With RCS 4.3 on July 26, 1990 it became distributed by the Free Software Foundation under the GPL.

----

Today RCS is a GNU project and easily installable as a package through Homebrew on a Mac or your package manager of choice in Linux. The latest release was 5.9.4 on January 22, 2015. The project is currently maintained by Thien-Thi Nguyen.

Tichy is still an active professor in Germany at the Karlsruhe Institute of Technology in Germany.