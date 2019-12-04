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