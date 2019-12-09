> TODO: Insert let there be light slide and/or 2001 black monolith slide.

Like most ideas, there are a lot of pre-cursors that had some elements of version control, but it's widely agreed that SCCS (Source Code Control System), not to be confused with SCSS, is the first true version control system. The systems that existed before SCCS were mostly about deltas. And while deltas are extremely valuable, they do not make a version control system.

Unfortunately, my research failed me when trying to find any detailed information about pre-cursors to SCCS. I know that systems like IBM's CLEAR (Controlled Library Environment and Resources) and DEC's CMS existed, but I wasn't able to find out much beyond that.

There is a little bit of information about CLEAR from a software engineering technique's conference sponsored by the NATO Science Committee in 1969. CLEAR was a larger system that "tried to assist with the administration and accomplishment of the program development cycle." (http://homepages.cs.ncl.ac.uk/brian.randell/NATO/nato1969.PDF pg. 40) One part of that system used deltas to help with versioning releases, but I was not able to find any other information.

----

Like many projects of the 1970s, SCCS was started at Bell Labs.

The year is 1972 and Marc Rochkind is struggling to deal with change management. In his 1975 paper _The Source Code Control System_, he describes four problems he was trying to solve.

> TODO: Insert slide with picture of Marc Rochkind.

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

The protoype was very successful and several large appliations were using it internally. In the fall of 1973 there were several more projects interested in using SCCS and the decision was made to write a new version. The interested projects were on multiple OS's, but the existing version of SCCS only supported OS/360 still. Instead of writing different versions for each OS (which was standard operating procedure then), the decided to write just one version that would run on a PDP 11/45 under UNIX.

> TODO: Insert picture of PDP 11/45.

Source code would be stored on the PDP 11 and sent to the appropriate machine for compilation. Given the future dominance of UNIX, this turned out to be a wise decision.

----

So, that's all well and good, but how did SCCS work? First, at a high level, it's important to remember that SCCS worked on individual files. This will probably feel a bit alien to just about everybody in this room. Who here has used a version control system that is focused on individual files? This means your commits are limited to one file at a time. Does anybody here still use a VCS like this, such as RCS?

Let's walk through an example of common SCCS usage. I'm going to use the POSIX syntax here. And no, you almost certainly can't follow along on your machine. It's part of the POSIX standard, but vendors have made the extremely reasonable choice to not ship with SCCS support.

(https://docs.oracle.com/cd/E19504-01/802-5880/6i9k05dhp/index.html)
> $ sccs create demo.txt

First, you must create the file through SCCS. We'll get into the structure of an SCCS file in a minute. For now, just note that this is different from _touch_. You can't just open up demo.txt and start editing it.

> $ sccs get demo.txt (gets a readonly version)  
> $ sccs get -r1.1 demo.txt

If you want to see a readonly version of demo.txt, you can get one like this. You can also check out a specific version of demo.txt by using the -r flag. We'll discuss versioning soon.

> $ sccs edit demo.txt  
> $ sccs get -c demo.txt (equivalent to the above)  

The _edit_ command lets you check out a version for editing. Only one user can check out a file for editing at a time.

> $ sccs delta demo.txt

The _delta_ command checks in your changes to demo.txt. You will be prompted to add a commit message. Even in Rochkind's original 1975 paper he notes that

> the quality of the reason (like the quality of the change itself) depends on the conscientousness of the programmer. Reasons like "Trouble Report 5576: change SUM header" are what one likes to see. Sometimes, unforunately, one sees instead things like "Another bug" or "Tried again."

So, let's say that you've made some commits to demo.txt and you want to make a release. You would do

> $ sccs edit -r 2 demo.txt (There is also a command to add a release for all files in the SCCS directory.)

I mentioned that mangaging the versioning of releases was a very big problem that SCCS hoped to tackle. It did this through the concept of releases and levels. Each commit would increment the level of a release. For example, when we created demo.txt, it was implicitly Release 1, Level 1, or 1.1. Committing a delta would increment the level to 2, so we're not at 1.2. The release number would only increment if you explicitly started a new release with `edit -r`.

You had a lot of power over managing those releases. For example, if you needed to make a fix to release 1, but release 2 is the most recent, you could explicitly checkout the latest level from release 1 and make a change. That change would not apply to release 2. You would have to make the change in release 2 by yourself if necessary.

You also had a lot of power to search and display history, but I'm not going to dive into that here.

> TODO: Insert info about _sccsid_. This feels like a historical oddity that is worth pointing out.

----

I don't want to dive too deep into implementation details with every system that I discuss today, but I do think it's important to talk a bit about how SCCS worked to set a baseline for comparison. Plus it's a great excuse to dive into old papers.

> TODO: Add information about SCCS structure.

The core of SCCS is something called _interleaved deltas_.

> The attempt by SCCS to record every version of every module that ever existed is rather ambitious. The system would be impractical unless it used a storage technique and accessing algorithm that allowed many deltas to be kept at a reasonable cost in terms of disk space and processing time. (1975 paper)

Interleaved deltas satisfied both requirements. The space required to store the delta is only slightly greater then the amount of text inserted by the delta. Access speed was mostly flat. Any level could be reached in equal time.

> TODO: Insert picture of interleaved delta.

All changes are stored with just two primitives. Lines are either being inserted or deleted. This should still be familiar today, because that is how diff works. Each _module_ is a separate sequential file. The deltas are stored in the _body_. The _body_ consists of _text records_ and _control records_. _Text records_ contain the source code. _Control records_ specify the effects of each delta.

> TODO: Create additional animations on the slide showing how information is added to the interleaved delta. See 1975 paper for guidance.

In 2015, Marc Rochkind sent an email to a mailing list outlining how he came up with the algorithm for interleaved deltas. I love this story because it shows that even in 1972 computer programmers were solving thorny problems by getting away from their work. (http://sccs.sourceforge.net/sccs_invention.html)

Marc was walking his girlfriend's dog. Marc didn't like the dog, so he would let his mind wander when walking it. He had been struggling with the problem of how to store both the source code and the deltas all in the same file. He came up with the idea of surrouding the pieces of text with markers. When he got back to his apartment he started sketching out details of how it might work.

When he thought he had a workable solution, he enumerated what he thought were all the possible cases of insertions mixed with deletions and worked through each example. From there it was pretty simple to code and he had it running in SNOBOL4 in a day or two.

----

> TODO: Add information about SCCS end of life. When was the last version? When was it last used? Other interesting tidbits.

As the first "real" version control system, SCCS was obviously extremely influential, but it also had a surprisingly long life-span. The project started in 1972, but didn't have it's first public release until version 4 on February 18, 1977. It even ended up becoming part of the Single UNIX Specification. It's still part of the POSIX standard, which really makes me wonder what other sort of random, irrelevant by-today's-standards utilities are part of POSIX.

> TODO: Include screenshot of SCCS in POSIX Shell and Utilities documentation. https://pubs.opengroup.org/onlinepubs/9699919799/utilities/sccs.html

The file format is actually still (or was?) used by more modern version control systems like BitKeeper and TeamWare.

You can still find a modern fork of SCCS that was open sourced by Sun as part of OpenSolaris on SourceForge. This site is actually a treasure trove of information. For example, it contains the version 4 release announcement from 1977. It contains important information, such as SCCS files now being stored as ASCII instead of binary. We can also see that it was still being distributed as part of a larger tool suite called Programmer's Workbench (PWB).

> TODO: Look up info on ASCII adoption in the 1970s to see how big of a deal this was.

You can also find a link to the SCCS development mailing list! It had a grand total of... one message in 2019. Asking if Windows 10 support was planned.

> TODO: Insert link to SourceForge. http://sccs.sourceforge.net/

GNU also provides CSSC, which is their version of SCCS. The source code of course lives in a git repository. It was converted from CVS to git in 2010. There is actually one dev (James Youngman) actively making contributions to it this past year.  The intent of the project is to help convert old SCCS repos over to a more modern option.

----
> TODO: Information about Marc Rochkind today.