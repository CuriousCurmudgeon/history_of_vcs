# Who has used BitKeeper
Who here has heard of BitKeeper? Who has used it? I have no personal experience with this tool, but, as we'll see, it's an incredibly important version control system for two reasons.

# Early Development
The history of BitKeeper is inescapably entangled with Linux's use of version control.

There isn't a lot of information available about the history of BitKeeper. Most of what I was able to find comes from their now open-sourced repository. Their repository mentions that Larry McVoy wrote a semi-distributed VCS while working at Sun. That was later turned into Teamware. You can also see the complete history of the project all the way back to when it became self hosting in March 1999.

On Sept. 30 1998 Larry McVoy sent a message to the kernel mailing list outlining a proposal for how to solve the Linus scaling problem. At the time, Linux was experiencing growing pains. Linus was a bottleneck for getting patches merged into the kernel. The proposed solution was a DVCS that would allow others to test and tweak patches in a very transparent manner as they made their way towards Linus through his circle of trust. This DVCS would be developed by his company, BitMover.

In that message Larry also linked to a page about BitSCCS (http://www.bitmover.com/bitsccs/), which is fascinating. It's a reimplementation of SCCS that also adds a number of new features. It served as the underpinnings of BitKeeper. In a harbinger of things to come, there is a licensing section that highlights that it will be free as in beer for free software development, but paid for commercial development. As of October 1, 1998, Larry estimated that he has lost $118,000 from quitting his job to work on this project with the explicit goal of helping Linus.

BitKeeper became self-hosting in March 1999. Early access betas became available in May 1999 and the first public release on May 4, 2000.

# Adoption by Linux

In 2002, BitKeeper was adopted by the Linux kernel. This decision was highly controversial. Torvalds and other core developers accepted the free license, but other core developers did not. This tension would come to a head in 2005.

BitKeeper's free software license prevented any attempts at reverse engineering. In April 2005, BitMover announced that it would be revoking this license because Andrew Tridgell (pronunciation?) had started reverse engineering the wire protocol to develop a third-party BitKeeper client. Larry McVoy said this violated the license and a lot of heated arguments ensued, with Torvalds in the middle. Tridgell had also been instrumental in reverse engineering SMB to create Samba, so this was very on brand for him. (He had also co-developed rsync for his PhD dissertation.)

In another interesting note, Tridgell and Torvalds were both fellows for the Open Source Development Labs (OSDL) at the time. This later merged with the Free Standards Group in January 2007 to become the Linux Foundation.

Tridgell argued that he had never bought or owned a BitKeeper. Thus, he had never agreed to its license and was not bound by it's restrictions around reverse engineering. It was ethical reverse engineering, just like Samba. Tridgell claimed that all he had done was telneted into a BitKeeper server and typed _help_. His goal was to provide features around metadata and comparing past revisions, features that were only available in the commercial version of BitKeeper.

In the end a very angry Torvalds was left to find a replacement for BitKeeper. We'll come back to that. (Foreshadowing!)


# Strengths
BitKeeper became the first widely used distributed version control system (DVCS). If you're going to pick a VCS to start the 3rd generation of version control. BitKeeper is probably your best bet. This means that BitKeeper had all the strengths of a DVCS compared to it's centralized competitors.

# Weaknesses
BitKeeper's licensing was... problematic. It tried to straddle the line between the free and commercial worlds. This kind of setup is fairly common today. BitKeeper compounded that though by adding a clause preventing users of the free version from participating in the development of a competing tool. You couldn't contribute to any other VCS if you used BitKeeper without violating the license.

# BitKeeper today
BitKeeper was open sourced under Apache 2.0 on May 9 2016 with version 7.2ce (CE = community edition), in what many interpreted as a belated attempt for relevance. Like just about every version control system in the wake of git, by 2016 BitKeeper was mostly a forgotten relic. It was mostly remembered for it's role in the creation of git.

The current stable release is 7.3.3 on Dec. 29 2018. The public repository on bkbits.net has no commits since. It's not clear what the development status of the product is.

# Resources
* https://www.theregister.co.uk/2005/04/15/perens_on_torvalds/
* https://www.theregister.co.uk/2005/04/14/torvalds_attacks_tridgell/
* https://www.theregister.co.uk/2005/04/13/torvalds_letters/
* Finally open sourced: https://news.slashdot.org/story/16/05/10/1840255/11-years-after-git-bitkeeper-is-open-sourced
* http://bkbits.net/
* https://www.bitkeeper.org/
* https://www.infoworld.com/article/2670360/linus-torvalds--bitkeeper-blunder.html
* http://static.lwn.net/1999/features/BitKeeper.php3
* Tridgell explains how he "reverse engineered" BitKeeper. http://www.groklaw.net/articlebasic.php?story=20050421023821174