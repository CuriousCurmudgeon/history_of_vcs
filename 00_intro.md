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
