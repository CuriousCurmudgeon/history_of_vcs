This is the actual script for my talk. It's going to be in a lot of flux as I attempt to write this.

----

Good morning/afternoon. How is everybody doing? Awake? Exhausted?

> TODO: Insert joke slides here for intro. Maybe a picture of the IRT booth.

I'm Brian Meeker. I'm a software developer for InfernoRed Technology. I work as a consultant, mostly in .NET and JS/Typescript, but also a bunch of other things. My official title is Engineering Wizard, but I'm a jack of all trades, master of none kind of guy. Stop by the InfernoRed booth if you want to chat about this talk or any other cool stuff you've seen at CodeMash this week.

So, you're here for a history talk. What makes me qualified to give a history talk? This is me putting my imaginary history minor to use. You see, I took all the courses to get a history minor, but never actually talked to anybody in the history department about it, so... no minor for me. But I put in all the work, and I think that's the important part. I'm pretty sure that avoiding the paperwork and the human interaction required to complete a task is the most stereotypical software developer behavior you can imagine.

I also want to thank Jenny Manning for doing her talk at last year's CodeMash - _Mommy, where do new programming languages come from?_ last year. Her talk was the inspiration for me submitting this talk and speaking here this year.

> So, "Daddy, where do version control systems come from?"
TODO: Insert slide of Emily and/or Olivia asking me a question here.

----
Let's step back though and talk about the dark ages. The before time. The time before version control. 

> TODO: Insert picture of punch card deck.

Can anybody tell me what this is?

Has anybody here actually used these before? Looking around the room, I feel pretty confident that the answer for just about everybody is no. If anybody has, can you tell me when you used them and where?

So, how do you think you would organize these? Do you think it's possible to have any concept of version control?

The answer to the second question is, not really. Given two decks of punch cards, there isn't an easy way to diff them. There were machines to duplicate a punch card deck, but not anything that would compare them as far as I know.

So, I think the best we can do is talk about how a programmer would maintain his punch card deck with the understanding that it is not version control.

> TODO: Insert picture of keypunch machine.

Does anybody know what this is? This is a keypunch machine. After writing your program on coding sheets, you would take your sheets over to a keypunch operator, usually a woman. The keypunch operator would use this machine to turn your written source code into something that could be fed into a computer.

> TODO: Insert picture of punch card deck.

But, could a computer directly run these punch cards? Look closely at the top of the card here. What do you see? Source code. The punch cards from the keypunch machine are just your source code in a format that can be fed into the computer. And what do we do with source code before the machine actually runs it? We compile. Some languages today still make this an explicit step. Some do it implicitly, but the code is always compiled before the machine can run it.

> TODO: Insert picture of compiled punch card

So you would take your punch card deck to the computer operator and they would attempt to compile it for you. If you were incredibly lucky/good/fortunate to have a simple task, then your program would compile the first time. Let's assume it did compile correctly though. Next, the computer operator would load your deck of compiled punch cards into the machine to execute the program. You would then get your original deck, compiled deck, and printed output back.

Now, chances are good that your program didn't work correctly the first time. It almost never does and you have to remember that these programmers had no real time feedback. There was no test suite running constantly. No debugger. No IDE. Nothing. So, now we can finally get to the real problem. How did a programmer manage changes to their punch card deck?

> TODO: Insert picture of punch card deck with diagonal line across top.

First, your helpful keypunch operator would often draw a diagonal line like this across the top of your cards. Now, if you dropped your deck, you could put it back in order by recreating the line. Not the most reassuring of systems, but it was a nice start for a new deck.

There was also a machine to quickly create a copy of your deck, a punched card duplicator.

But what would happen when you start making edits to your deck. The keypunch operator shouldn't have to type up a new copy of your deck every time you make a change. As a programmer, you should be able to type up a new card as needed to insert into your deck. However, your line won't be very useful in that case. It will quickly become a jagged mess.

> TODO: Insert picture of punch card with sequence numbers.

Does anybody know how many columns there are on a standard punch card? 80. If you look closely at this card, you will see the columns labeled at the bottom all the way to 80. However, it was common practice for compilers to only look at the first 72 columns on the card. So, that gives us 8 unused columns and those columns are the key to ordering the deck. You can make an 8 bit sequence number to order the cards with.

> TODO: Insert picture of punched card sorter.

That kinds of just shifts the problem around though. What if we have our sorted deck and we want to insert a new card in the middle of our program. For example, we want to insert a new card 32 and shift the rest of the deck back. How do we easily renumber our cards? Easy, you write a program for it. So you feed your deck into the machine, assume it's correctly ordered. The machine ignores the existing sequence numbers and copies your deck with new sequence numbers.

There are still a lot of limitations here. Getting new sequence numbers is automated, but if you put a card in the wrong spot in the deck you won't have any record of that. You'll have to compile and, if it compiles successfully, execute your program to recognize your mistake.

There's also no trail of any changes. Collaborating with another programmer on a problem is very difficult. You would have to very, very carefully negotiate who is working on what. And even when working by yourself, you can't look at your history and figure out where you introduced a bug.

> TODO: Insert information about PATCHY (https://rahul.gopinath.org/post/2011/12/30/version-control-systems/ and https://inis.iaea.org/collection/NCLCollectionStore/_Public/22/031/22031927.pdf)

But, as far as I can tell, this as far as the punch card world got. Punch cards weren't long for this world though. We were about to enter the world of multi-user operating systems and teletypes. Pretty soon punch cards would begin to fade out and source code would live on the computer itself. Which meant it was time to start looking into software to manage it.

----

So, what is version control?

Wikipedia says that it
> is the management of changes to documents, computer programs, large web sites, and other collections of information. (https://en.wikipedia.org/wiki/Version_control)

The Git documentation says
> Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. (https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

You'll notice these definitions don't lay out any specific requirements about what features a version control system needs to have. We would certainly like it to be easy to visualize changes. We would certainly like to have atomic commits. We would certainly like it to be easy to manage releases. But none of these are required. You just need to record changes so you can get back to a specific version if needed. That's it.

> TODO: Insert slide with meanings of VCS, SCM, etc.

One other terminology note before we dive in. I'm going to use some terms interchangeably here.

VCS = Version Control Software
SCM = Source Control Management (or Software Configuration Management. I'm using the term just for source control here.)
Revision Control

Any distinction between these terms is generally meaningless. Software Configuration Management can have a slightly different meaning depending on context, but that isn't important in the context of this talk.

----

> Insert let there be light slide and/or 2001 black monolith slide.

Like most ideas, there are a lot of pre-cursors that had some elements of version control, but it's widely agreed that SCCS is the first true version control system. The systems that existed before SCCS were mostly about deltas. And while deltas are extremely valuable, but they do not make a version control system.

Unfortunately, my research failed me when trying to find any detailed information about pre-cursors to SCCS. I know that systems like IBM's CLEAR (Controlled Library Environment and Resources) and DEC's CMS existed, but I wasn't able to find out much beyond that.

There is a little bit of information about CLEAR from a software engineering technique's conference sponsored by the NATO Science Committee in 1969. CLEAR was a larger system that "tried to assist with the administration and accomplishment of the program development cycle." (http://homepages.cs.ncl.ac.uk/brian.randell/NATO/nato1969.PDF pg. 40) One part of that system used deltas to help with versioning releases, but I was not able to find any other information.