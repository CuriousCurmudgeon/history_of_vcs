As we move through history, I'm expecting to see more hands up in the air.

# Who has used CVS?
Which brings us to CVS. So, who here has used CVS? When did you last use it and where? 

# Early Development

CVS can be said to have two creators. The initial creator was Dick Grune.

Dick Grune was born in 1939 in Enschede, the Netherlands. He got his Master of Physics in 1967 from Rijksuniversiteit Utrecht. From there he worked in Israel as a systems programmer for a couple of years before starting research in Amsterdam. He got his PhD in Computer Sciense in 1982 from the University of Amsterdam. He spent the rest of his career at Vrije Universiteit, Amsterdam before retiring in 2004.

Dick Grune created the initial version of RCS in 1984-1985. The details are a bit fuzzy.

> I created CVS to be able to cooperate with my students, Erik Baalbergen and Maarten Waage, on the ACK (Amsterdam Compiler Kit) C compiler. The three of us had vastly different schedules (one student was a steady 9-5 worker, the other was irregular, and I could work on the project only in the evenings). Their project ran from July 1984 to August 1985. CVS was initially called cmt, for the obvious reason that it allowed us to commit versions independently.

When this project finished up he cleaned up the shell scripts and renamed it CVS. These shell scripts were just wrappers over RCS. The initial commit of CVS under itself was on November 23, 1985. He posted the improved scripts to comp.sources.unix on June 23, 1986. You can still find those online today at https://groups.google.com/forum/?hl=en#!msg/mod.sources/eqze_AHbIK0/uE90wCq3ui4J

From there, Brian Berliner comes into the picture.

Brian Berliner received his BS in Computer Sciene from the University of Illinois in 1985. He's had a long career working on supercomputers, CVS, and business systems. He's been a founder and an executive. Advisor and board member. He's been busy.

Brian Berliner took those original scripts and ported them to C in roughly two weeks. This port turned into the official CVS. He started it in April 1989 with input from other contributors while working at Prisma. Prisma was a third-party developer working on the SunOS kernel. His port was released under the GPL and CVS 1.0 became a Free Software Foundation project on November 19, 1990. It's relationship with GNU is a bit murky. Some GNU pages called it a GNU project and others did not.

# Advances over RCS
CVS was the first version control system of what became known as the second generation. It's primary advancements were

* The ability to work with multiple files at once. Files are still versioned independently, but you can commit multiple at once. The huge shortcoming of this is that those commits are not atomic. You are not guaranteed that all of them or none of them will succeed. Any number could succeed or fail.
* Client-server architecture. The server contains the centralized repository and clients talk to that repository to check code out, commit code, and other operations. The server is the centralized point of truth and all operations must go through it.
* Concurrent edits. File locks are no longer necessary. Instead, multiple developers may work on a file at once. If developer A commits first, then developer B will be required to pull the new changes in first and resolve conflicts if necessary before they are able to commit their changes. If there are no conflicts, then this process is transparent.

# CVS Adoption
Unfortunately I was not able to find any hard data on CVS adoption, but I've found enough indirect evidence that I'm willing to state the CVS was the dominant version control system of the 90's.

> TODO: Insert slide with survey info http://git.wiki.kernel.org/index.php/GitSurvey2007
> http://git.wiki.kernel.org/index.php/GitSurvey2008 (This one says that a majority of respondents had used CVS. SVN was second with only 30%.)
> https://stackoverflow.com/questions/882788/are-there-any-popularity-usage-statistics-available-for-the-free-rcs-scm-vcs-s

A 2007 survey by git of it's users found that CVS and SVN were by far the most common version control systems that git users also had experience with. This is not the most representative sample though. An early adopter of git is probably not representative of the average developer.

CVS became the de facto standard for open source development. There were competing paid products, such as Perforce, ClearCase, and Visual SourceSafe, but they never became as ubiquitious as CVS. Although, I think that Perforce did offer free licences to open source projects.

# CVS Today
Today, I would consider CVS to be a dead project. The last release was 1.11.23 on May 8, 2008. There have been some maintenance bug fixes since then, but no releases. The last checkin was on March 30, 2011.

There is a fork called CVSNT that began in 1998 with the initial goal of improving Windows support. I assume this is where the "NT" comes from. Its history is extremely messy. It's not that important, so I won't go into it. Suffice to say, if you wish, you can pay for a commercial version of CVS today.

The real future of CVS was... (SVN)