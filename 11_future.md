In 1972 we got the first version control system in SCCS. In 1985 we got the first iteration of CVS, kicking off the second generation of version control systems. Then, in 2005 we got git, which kicked the third generation into high gear, bringing distributed version control systems to the mainstream. But 2005 was a long time ago now. Is there anything else on the horizon that could replace git?

In just about every other area of developer tooling there are new options created every year. Sadly, after the explosion in DVCS's in the mid-2000s, there isn't much to talk about. Let's look at a few though.

# Pijul
https://pijul.org/
Pijul can be thought of as a newer version of Darcs that attempts to fix its performance issues. It is written in Rust and has a slightly updated version of Darcs's patch theory.

I haven't used Pijul myself, but I would be excited to try it on a collaborative project. I liked Darcs. A version with better performance and other improvments sounds like something really cool to try. Easier to use cherry picking sounds great too.

Pijul is still considered beta quality, so use at your own risk.

# Plastic SCM
https://www.plasticscm.com/
Plastic is a commercial tool that was first released in 2006. It has a couple of differentiating features.
* Focus on the game industry. This wasn't the original focus, but a shift as git continued to eat the world. One of git's weaknesses is binary assets, so the games industry is one area where git has not achieved widespread adoption. Focusing on a niche is one way that a new VCS could gain a foothold.
* Language awareness allows for history of specific methods/functions instead of just lines. This seems really cool and something I would love to play with.

# Why no serious competitors?
> TODO: Slide with GitHub logo and the PR logo.

GitHub, not git, is the primary reason that no viable replacement for git is on the horizon. Previous generations of version control didn't have to deal with such a strong network effect when replacing the old. Everything works with GitHub. All new open source projects are hosted there by default. An entire DevOps industry has sprung up around it. Realistically, any new version control system would have to be adopted by GitHub to gain significant traction.

Git was so dominant in the Stack Overflow Developer Survey that they don't even ask the question anymore. It had almost 90% adoption in 2018, so they didn't even ask in 2019. We obviously don't have numbers for the entire history of version control, but I feel confident in saying that no other version control system has ever had such numbers. The market was fragmented across many open source and commercial options before.

Pijul is the only new VCS I could find with any buzz around it and even that is minimal. I can't decide if this is a depressing note to end on or not, but that's the current state. 

# Thanks for coming
So, that was fifty years of history in what I'm hoping was approximately fifty minutes.

I would like to thank all of you for getting up early and coming to his session. If you have any questions or want to chat, feel free to come on up. I'll also be at the InfernoRed Technology booth after this session, so feel free to stop by there to chat. Enjoy the rest of your conference!
