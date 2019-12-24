Git wasn't the only version control system to emerge from the ashes of the BitKeeper fallout. There was also Mercurial.

# Who has used Mercurial?
Who here has used git? Now, who is currently using it on a daily basis? Who used to? Anybody who started using it way back in 2005?

# Early Development
The early history of Mercurial is tightly linked to BitKeeper and git.

Matt Mackall first announced Mercurial on April 19, 2005, thirteen days after Torvalds announced git. His initial goals were (https://lkml.org/lkml/2005/4/20/45)

 - to initially be as simple (and thereby hackable) as possible
 - to be as scalable as possible
 - to be memory, disk, and bandwidth efficient
 - to be able to do "clone/branch and pull/sync" style development

# Comparisons to git
The comparisons to git are inevitable. With regards to performance, git has generally always been faster for most operations, but Mercurial is close behind it. Both of them generally blow away any other DVCS.

Mercurial is written mostly in Python, with some sections written in C/C++ for performance reasons. Because of the choice to use Python, Mercurial was cross-platform from day one. It took quite some time for git to become usable across platforms, especially Windows.

Mercurial prioritized a very usable CLI from day one. This is a big contrast to git, which for years had a reputation for being unusable by mere mortals.

The trade off was that Mercurial lacked many features that git had. For example, Mercurial did not initially support branches. The preferred workflow was to just create another clone of the repo.

The Mercurial team also argued against operations that allowed users to change history, such as rebase. Their philosophy was that that a project's history should be complete and fixed.

Similar to git, Mercurial also took design inspiration from monotone in it's use of hashes.

> https://web.archive.org/web/20090129015244/http://ldn.linuxfoundation.org/article/dvcs-roundup-one-system-rule-them-all-part-2#hg

# Mercurial Today
Sadly, today Mercurial is fading as we move ever close to a git monoculture. Bitbucket was orignally GitHub, but for Mercurial. Even they have given in though, announcing that Mercurial support will be deprecated in February 2020 and removed on June 1, 2020. Their announcement noted that less than 1% of new repositories were using Mercurial.

The most recent Stack Overflow Developer Survey showed that almost 90% of developers use git, but only 3% use Mercurial.

It is still under active development though. Version 5.2 was released on Nov. 5, 2019.

I think there definitely is an alternate reality where Mercurial won, but all the factors that have led to such wide adoption of git all worked against Mercurial.