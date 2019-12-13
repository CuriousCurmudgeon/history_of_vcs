As we move through history, I'm expecting to see more hands up in the air.

# Who has used CVS?
Which brings us to CVS. So, who here has used CVS? When did you last use it and where?

# Creator(s)
CVS can be said to have two creators. 

## Dick Grune
Dick Grune was born in 1939 in Enschede, the Netherlands. He got his Master of Physics in 1967 from Rijksuniversiteit Utrecht. From there he worked in Israel as a systems programmer for a couple of years before starting research in Amsterdam. He got his PhD in Computer Sciense in 1982 from the University of Amsterdam. He spent the rest of his career at Vrije Universiteit, Amsterdam before retiring in 2004.

## Brian Berliner
Brian Berliner received his BS in Computer Sciene from the University of Illinois in 1985. He's had a long career working on supercomputers, CVS, and business systems. He's been a founder and an executive. Advisor and board member. He's been busy. 

# What prompted the development of CVS?

# Early Development

Dick Grune created the initial version of RCS in 1984-1985. The details are a bit fuzzy.

> I created CVS to be able to cooperate with my students, Erik Baalbergen and Maarten Waage, on the ACK (Amsterdam Compiler Kit) C compiler. The three of us had vastly different schedules (one student was a steady 9-5 worker, the other was irregular, and I could work on the project only in the evenings). Their project ran from July 1984 to August 1985. CVS was initially called cmt, for the obvious reason that it allowed us to commit versions independently.

When this project finished up he cleaned up the shell scripts and renamed it CVS. These shell scripts were just wrappers over RCS. The initial commit of CVS under itself was on November 23, 1985. He posted the improved scripts to comp.sources.unix on June 23, 1986. You can still find those online today at https://groups.google.com/forum/?hl=en#!msg/mod.sources/eqze_AHbIK0/uE90wCq3ui4J

From there, Brian Berliner comes into the picture. He took those original scripts and ported them to C in roughly two weeks. This port turned into the official CVS. He started it in Apirl 1989 with input from other contributors while working at Prisma. Prisma was a third-party developer working on the SunOS kernel. His port was released under the GPL and CVS 1.0 became a Free Software Foundation project on November 19, 1990. It's relationship with GNU is a bit murky. Some GNU pages called it a GNU project and others did not.

# Advances over RCS
CVS was the first version control system of what became known as the second generation.

# CVS Today
Today, I would consider CVS to be a dead project. The last release was 1.11.23 on May 8, 2008. There have been some maintenance bug fixes since then, but no releases. The last checkin was on March 30, 2011.

There is a fork called CVSNT that began in 1998 with the initial goal of improving Windows support. I assume this is where the "NT" comes from. Its history is extremely messy. It's not that important, so I won't go into it. Suffice to say, if you wish, you can pay for a commercial version of CVS today.

The real future of CVS was... (SVN)