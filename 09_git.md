# Who has used git
Who here has used git? I expect to see most hands in the air for this one. Now, who is currently using it on a daily basis? Anybody who started using it way back in 2005?

# Early Development
The early history of git is tightly bound to the history of Linux version control. As we already discussed, in 2002 Linus decided to adopt BitKeeper for kernel development. The use of a closed source version control tool remained a point of tension until finally boiling over in April 2005 when Larry McVoy rescinded the free license for open source software over Tridgell's reverse engineering efforts.

This left Torvalds and the wider Linux development community in a tough place. Torvalds set the following criteria for any system that would replace BitKeeper.
* A patch should take no more than three seconds to apply.
* Take CVS as an example of what not to do; if in doubt, make the exact opposite decision.
* Support a distributed, Bitkeeper-like workflow
* Include very strong safeguards against corruption, either accidental or malicious.

Torvalds's disdain for CVS was widely known. He had even gone so far as to say that kernel development would revert back to using no version control at all instead of using CVS. He spent a bit of time evaluating monotone and darcs, but ended up rejecting both for performance reasons. Monotone though provided inspiration in its use of hashes.

Following the release of kernel v2.6.12-rc2, Torvalds was able to start dedicating all of his time to the first version of git. Development was rapid.

* April 3, 2005: Development begins
* April 6, 2005: Torvalds announces the project
* April 7, 2005: Git becomes self-hosting. The README also contains multiple meanings of the name, although Linus seems to have decided that the true origin is the British slang "git", which means "a silly, incompetent, stupid, annoying, or childish person". He claims that he's now been arrogant enough to name two projects after himself, Linux and git.
* April 18, 2005: First merge of multiple branches
* April 29, 2005: Performance goals met. Recorded 6.7 patches per second to the Linux kernel tree
* June 16, 2005: Git managed the kernel 2.6.12 release.

# Development Post-Torvalds
Torvalds turned over maintenance to Junio Hamano on July 26, 2005. Hamano had been a major contributor.

1.0 was released on December 21, 2005. Hamano remains the project maintainer to this day.

# Wider Adoption
Git had a huge advantage compared to any other VCS in history. The highly visible conflict over BitKeeper, on the most highly visible open source project in the world, with the most famous open source developer in the world as a central figure gave it an enormous amount of visibility. Git was then able to capitalize on that visibility by rapdily creating an initial version and using it to manage a release of the Linux kernel.

In the early days, git was notorious for being difficult to use. Linus had developed a system designed specificially for his workflow around merging patches into the Linux kernel. It's taken many years of work to make the project more usable. In a 2007 talk at Google, Torvalds mentioned that he thought that git was mostly usable for other projects at that point.

We'll talk more about GitHub soon, but it's launch in April 2008 was instrumental in driving more widespread adoption of git.

Atlassian put together a nice infograph for git's ten year anniversary. It unfortunately doesn't link to exact sources, but it claims that in git installations on Debian Linux skyrocketed in January 2010. By January 2011, git installations on Debian Linux had surpassed Bzr, CVS, Mercurial, SVN, and Darcs combined. Obviously Debian Linux users aren't a necessarily representative group, but I think it's safe to say that git was becoming dominant by this time. I remember joining a company that was using Darcs around this time and one of my questions for them in the interview was why not git.

In October 2011, Bitbucket added git support. Up until then it only supporter Mercurial. In retrospect, the writing was on the wall at this point.

> TODO: https://www.atlassian.com/git/articles/10-years-of-git

> TODO: Comparison in searches for Git vs Mercurial vs SVN vs CVS: https://trends.google.com/trends/explore?date=2005-04-01%202019-12-23&geo=US&q=%2Fm%2F05vqwg,%2Fm%2F08441_,%2Fm%2F012ct9,%2Fm%2F09d6g I'll note that it's really hard to get Google Trends data for CVS and not get noise around CVS Pharmacy as well.

> TODO: Insert adoption graph from 10 years of git: https://www.atlassian.com/git/articles/10-years-of-git# Unfortunately, it doesn't say where this data came from. By 2014, 33% of developers were using git. Is this from the Eclipse community survey?

In case there was any doubt, in June 2014 Git surpassed SVN in the Eclipse Community Survey.

These answers exlude GitHub. (https://softwareengineering.stackexchange.com/a/150791)
2009: 2.4%
2010: 6.8%
2011: 12.8%
2012: 27.6%
2013: 30.3%
2014: 33.3%

With GitHub
2012: 32%
2013: 36.3%
2014: 42.9%

By 2018 the Stack Overflow community survey showed that almost 90% of 74,000 developers surveyed preferred to use git.

# Influences on Git
This isn't a technical talk, so I'm not going to dive into any details of git internals, but I think that it is very important to point out how unique git is compared to what came before it and why.

There are three primary constraints/influences that had a large effect on the initial design
* Torvalds's experience maintaining a large distributed development project.
* Torvalds's intimate knowledge of file system performance.
* The urgent needs to have a working project in short order.

Torvalds gave himself a two week deadline for the initial version of git. 

## BitKeeper
It's hard to overstate the influence of BitKeeper. It was the first DVCS and Torvalds had built his entire workflow around it for the past three years. It was inevitable that BitKeeper would have a large influence on git. Torvalds was aware of that though and had a desire to not just back a BitKeeper clone.

> When I did git, one of the things that actually _helped_ me was that I 
   was consciously trying to not do a BK clone. I wanted to do the same 
   things that BK did, but I very much did _not_ want to do them the _way_ 
   BK did them. I respect Larry too much, and I didn't want there to be 
   any question about git being just a "clone".
>
> So a lot of the git design ended up very much trying to avoid old 
   designs on purpose, and I think that really helped. The fact that I 
   didn't have a background in SCM's, and that I thought all the weaves 
   etc were confusing, meant that I instead went for a radically different 
   way of doing things.
>
> And I'm 100% convinced that "radically different" was the right thing 
   to do. That was what allowed git to really soar. A lot of the good 
   things in git come exactly from the fact that git does _not_ do things 
   like most traditional SCM's do. But BK should still get a lot of 
   credit, because it was what taught me (and a lot of other people) what 
   being "distributed" really meant.
>
> https://marc.info/?l=git&m=116129092117475

## "Series of Patches" Model
While trying to come up with a compromise between Tridgell and McVoy, Torvalds had proposed a generic export format from BitKeeper. The format was a series of patches with parenthood information. (See https://marc.info/?l=git&m=114685143200012)

Whe no compromise could be reached and Torvalds was searching for a replacement for BitKeeper, this idea was already in his head. If nothing else could be found, he would just go back to lists of patches rather than use CVS.

He eventually extended the series of patches idea to include a "cache" since rebuilding the current state from the beginning was expensive. Conceptually this became the git "index" file and working tree. 

## Monotone
The biggest contribution from monotone is the idea that every object has a corresponding hash. Torvalds was already planning on using hashes for the history, but monotone took it further. Every object had a hash. This became a central part of git as well.

# Git Today
> TODO: Just one big slide that says "It Won"

> TODO: Probably out of scope right now, but GVFS is really cool. https://devblogs.microsoft.com/bharry/the-largest-git-repo-on-the-planet/

# Notes

> At some point, "performance" is just more than a question of how fast 
things are, it becomes a big part of usability.
>
> https://marc.info/?l=git&m=116128307511686