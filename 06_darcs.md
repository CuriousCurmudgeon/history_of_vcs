# Who has used Darcs
Has anyone here used Darcs? How many here even know what Darcs is? How were you using it? Professionally? Hobby? Just testing it out?

# DVCS (3rd Generation)
Darcs is the first version control system we're going to talk about from the 3rd generation. The defining trait of this generation is distributed. We mostly think of git when we talk about distributed version control systems, but several others existed first. Linus Torvalds was certainly aware of existing distributed options, but, as we'll see when we get to git, none of them met all of his criteria.

# Early Development
David Roundy is creator of Darcs. His background is a bit different then what you would expect from someone creating a version control system. He received his Ph.D. in physics from U.C. Berkely in 2001. While doing post-doctoral work, he was also working on a cross-platform online bridge game called aBridge. He was using CVS on SourceForge, but wasn't happy with it. Subversion was really new at the time and Roundy was interested in the idea of a distributed system, so he started looking into Arch.

Arch didn't really satisfy him either though. In June 2002 he got involved in discussions about creating a new patch format for arch, but it became clear that his proposal would never be incorporated. He found the ideas interesting though, started playing around with them, and, behold, darcs was born. (And since a developer can really only dedicate sufficent time to one side project, aBridge essentially died to give us darcs.)

The initial version of darcs was written during the summer of 2002 in C++. However, there was a lot of experimentation as Roundy figured out what exactly he was trying to implement, so by that autumn he had a very solid mass of bugs that was difficult to debug. Around that time he had also started looking into Haskell, so... guess what happened next? When you have a side project you should always make it more complicated by re-writing in a language you barely know.

The first public release of darcs was v0.9.3 on April 3, 2003. Windows support was added that summer. 

In April 2008, Darcs 2.0 was released. It "introduced a more robust repository format, as well as a new patch semantics called "darcs-2", aimed at minimizing exponential merge issues." (https://en.wikipedia.org/wiki/Darcs)

# Advantages
## Early DVCS
Git is one of the first distributed version control systems. It's not THE first, but it is an early part of the 3rd generation. If you wanted a DVCS in 2003, then darcs was one of the few options to choose from.

## Patch Theory
By far the most interesting part of darcs is its theory of patches. In darcs, a repository is a set of patches that are not necessarily ordered with respect to other patches. Darcs automatically calculates whether patches can be reordered and how it should be done. If your patches modify independent parts of the code, then they are not dependent upon each other and can be applied in any order. This makes it easy to merge individual patches. Since darcs calculates the dependencies between them, it will also tell you what dependent patches need merged as well.

## Very Interactive CLI
Who hear knows the ins and outs of the git CLI? Definitely not me. I always have to reference the docs once I get off my happy path. Darcs on the other hand has a very explicit goal of an easy to use, interactive CLI.

Who here uses _git add -i_? That type of interactive command is the default it darcs. A lot of time and care has been spent to make it feel usable and intuitive to mere mortals.
> TODO: CLI examples

# Weaknesses
## Speed
The biggest weakness of darcs is speed and memory usage. This was far more pronounced pre-darcs 2.0, but still exists to some extent. This was one of the big strikes against darcs when Linus Torvalds was searching for a version control system to use before giving up and creating git.

## Very Interactive CLI
And depending on your preferences, the very interactive CLI could be seen as a con. It's been a long time since I used darcs on a regular basis (early 2012), but I don't remember having any issue with it.

# Darcs Today
Today, darcs is a very niche version control system. It's still actively developed, but at a pretty slow pace. 2.14.2 came out in January 2019 and when I checked on December 17, 2019, there hadn't been a single commit since October 2, 2019.

My understandig is that it is more common in the Haskell community, which makes sense since it's written Haskell. But even the darcs die hards have mostly accepted that git has become The One True VCS. Even way back in 2011 there was talk in the community about Haskell projects starting to move away from darcs to git.