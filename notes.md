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

> TODO: Insert content about punch card organization here.

----

So, what is version control?

> TODO: Insert definition of version control here. What criteria needs to be met to qualify as version control?

> TODO: Insert discussion of systems that pre-date SCCS. They met some of the criteria, but not all.

> TODO: Insert discussion of difference between VCS, SCM, etc.

----

> Insert let there be light slide and/or 2001 black monolith slide.

Like most ideas, there are a lot of pre-cursors that had some elements of version control, but it's widely agreed that SCCS is the first true version control system. The systems that existed before SCCS were mostly about deltas. And while deltas are extremely valuable, but they do not make a version control system.