# Who has used SVN?
So, who here has used SVN? When did you last use it and where? Personally, I used SVN for the first time in college on a group project. Another member of the group that I hadn't worked with before used it on all of his projects, so the entire team adopted it. I would go on to use it from 2007-2010 at my first job out of college.

# Early Development
> TODO: Most of of this data comes from http://svnbook.red-bean.com/en/1.7/svn.intro.whatis.html#svn.intro.history

The Subversion project was started in 2000 by CollabNet with the explicit goal of making CVS, but better. CollabNet offered a software suite called CollabNet Enterprise Edition (CEE), which included version control. They were using CVS for that part, but the limitations were obvious. Unfortunately, CVS had become so ubiquitous that there wasn't a better open source option.

There are few people who are most responsible for the early design and development of the project. These are Karl Fogel, Jim Blandy, and Ben Collins-Sussman.

Karl Fogel was the author of _Open Source Development with CVS_. He had already been discussing a design for a new version control system with Jim Blandy. Those two had previously founded Cyclic Software in 1995 to provide CVS support contracts, so they were well aware of the strengths and weaknesses of CVS.

In February 2000, CollabNet reached out to Karl Fogel to ask about his interest in working on a version control system to replace CVS. By coincidence Karl and Jim were already discussing such a system, Karl immediately joined. Jim was working for Red Hat Software at the time and convinced them to essentially donate him for an indefinite period of time to work on the project. CollabNet also hired Ben Collins-Sussman at this time.

Their initial goals were simple. Jim already had a name, Subversion, and a basic design for the data store from his previous musings with Karl. They didn't want to break any new ground, they just wanted to fix CVS. They wanted to match CVS's features and development model, but avoid the big flaws. It didn't need to be a drop-in replacement, but it needed to feel very familiar to a CVS user to make the transition relatively painless.

Subversion became self-hosting on August 31, 2001, after 14 months of development. Up until this point the code was actually managed with CVS.

# Becoming an Apache Project
In November 2009, Subversion was accepted into Apache Incubator. Things moved quickly and it became a top-level Apache project on Feburary 17, 2010. It remains an Apache project to this day.

One major factor in Subversion becoming an Apache project was Brian Behlendorf. He was one of the founders of CollabNet, along with Tim O'Reilly (yes, the one you're thinking of) and Bill Portelli. Behlendorf is best know for being the primary developer of the Apache Web Server and found the Apache Group, which became the Apache Software Foundation.

# Advantages over CVS
> TODO: See https://en.wikipedia.org/wiki/Apache_Subversion#Features

# SVN Adoption


# SVN Today

## Karl Fogel
> TODO: https://www.red-bean.com/kfogel/

Karl Fogel would go on to write _Producing Open Source Software: How to Run a Sucessful Free Software Project_. He would draw on his experience with Subversion a lot during the book. He currently is a partner at Open Tech Strategies, LLC, where he helps organizations launch and participate in open source projects.

In addition, he founded QuestionCopyright.org, a non-profit that advocates for copyright reform.

## Jim Blandy
> TODO: https://www.red-bean.com/~jimb/
> https://www.oreilly.com/talent/25f8e-jim-blandy
Today, Jim Blandy works for Mozilla. He is also the author, along with Jasen Ordendorff of _Programming Rust_. In addition, he has also been the maintainer of GNU Emacs, GNU Guile, and GDB.

## Ben Collins-Sussman
> TODO: https://www.red-bean.com/sussman/
Ben Collins-Sussman has gone on to co-found Google's engineering office in Chicago. He ported Subversion to use Google's BigTable as storage and was instrumental in the launch of Google Code. Today he manages teams in charge of Google's search's overall latency and speed.

## SVN Usage Today
Subversion has definitely fallen out of favor today, but remains the most widely used centalized version control system. It's still actively developed. Version 1.13 was released on October 30, 2019.