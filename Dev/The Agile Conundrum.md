> Agile is like communism. It fails because it has never been implemented correctly.

I've started my developer career just a few years ago so I have never experienced the *old way* of software development. I hear stories of massive specification documents, fines for not releasing before deadline, fights over the contract. Even though I haven't been through it I can see why approaching SW development as any other engineering project is flawed and so I fully get why something like agile manifesto came up. That being said I'd like to have a look at my personal experience with agile development, methodologies etc. I'd like to comment on the quote at the beginning of this article. Finally I'd like to humbly present you with a few of my ideas on how to exercise agile development.

## Reasons for the Agile Manifesto
As far as I understand the main driving force behind legends like Cunningham, Beck and Fowler gathering at a mountain cabin and instead of having a nice BBQ party coming up with the Agile Manifesto was **frustration**. They were working in the corporate environment that was awfully inflexible, punishing and just overall not suitable for developing software. I guess the kind of programmers who have been building their stuff in garage haven't faced the same problems as the manifesto-men. So it was this group of hardened and frustrated programmers who put together these [4 values](https://agilemanifesto.org/): 

>- **Individuals and interactions** over processes and tools  
>- **Working software** over comprehensive documentation  
>- **Customer collaboration** over contract negotiation  
>- **Responding to change** over following a plan

They also have come up with [12 principles](https://agilemanifesto.org/principles.html) but the core values are enough for figuring out why Agile Manifesto exists. Obviously the four things on the left were at the time sidelined in favour of the four things on the right.

Documentation, plan, processes... that sounds like *a bridge construction project*. That's a favourite analogy even though it's a bit flawed. Civil engineering and software engineering are obviously different disciplines but so are mechanical engineering and electrical engineering. The overarching notion should be that each engineering discipline is different and thus the software engineering should be treated accordingly as a separate discipline.

There has been times when software engineering was frowned upon. It has been viewed as inferior discipline compared to the more established or traditional engineering disciplines. Agile Manifesto was a public movement that has pointed this out and tried to give us a description of what building software is and how it should be approached.

## Methodology vs. Idea
It's important to realise what the Agile Manifesto is and isn't. It is an expression of an idea. A model of software development and how this kind of work should be approached. (Reading the [12 principles](https://agilemanifesto.org/principles.html) now is a good idea.)

The Agile Manifesto is not a prescriptive document. It doesn't give us a todo list that upon completion would grant us the AGILE stamp. It sure does suggest some practices but no methodologies.

>The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.

There's nothing about how, when, how often etc. should such conversation happen. It's simply saying that instead of sending an email or memo you should get up, come to your coworker and tell them what you need.

> Simplicity--the art of maximizing the amount of work not done--is essential.

It's up to you to decide what this means. Minimising premature optimisation? Perhaps.

> At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.

There is specific about this principle. It just states that you should confer regularly how you do your work.

What brings specificity to the table are agile frameworks. There is plenty of them but I personally have been exposed only to SCRUM, Kanban and XP. And in the case of SCRUM I can say that I have seen all 50 shades of it.

Unlike the manifesto frameworks are prescriptive. They suggest methodologies that should be practiced in order to use the framework effectively.

For example XP (extreme programming) comes up with things like sprint, pair programming, mob code review, mob programming etc. SCRUM comes up with its ceremonies aka meetings. Kanban is the ubiquitous project board.

In an essence the Agile Manifesto is exactly what manifestos are an idea. The frameworks are then exercising the idea, interpreting the principles and values and  putting them to practice.

## SCRUM Ceremonies aren't Agile
SCRUM is such a benevolent word. For many people it's synonymous for agile. I have seen SCRUM as a corporate watered-down packaging of agile, umbrella term form chaos, gas-lighting tool for management, micro-management toolbox and I yet have to see it being actually useful.

Sorry for the minor rant there. I need to clarify that unfortunately SCRUM being almost synonymous with agile these days casts some of it's practitioners in bad light. These people are trying to make agile work for their organisation and their coworkers and only by chance are they stamped with the SCRUM stigma. But they are only exceptions unfortunately.

Now, what is a ceremony? For anyone outside the SW development it's probably tight to religion or some social practice. Let's ask the Cambridge dictionary:

> (a set of) formal acts, often fixed and traditional, performed on important social or religious occasions

And here's the definition of ritual which I believe to be very similar to a ceremony:

> a way of doing something in which the same actions are done in the same way every time

"formal act", "fixed", "done in the same way every time" well that sounds an awful lot like a corporate process. Let's remind ourselves the first agile value: **Individuals and interactions** over processes and tools. This is why SCRUM (as it is generally implemented) is flawed.

Here's a list of usual SCRUM ceremonies: daily standup, refinement, planning, retrospective, demo. 

Daily can last 5-20 minutes, refinement 1 hour, planning 1 hour, retro 1-2 hours, demo 15-30 minutes. That's about 4-5 hours each sprint doing meta-work = working in order to eventually actually work on the software. On top of that many organisations and teams have company-wide meeting for an hour quarterly or monthly, various guild meetings, interest-groups meetings etc. And to take it to the extreme these meetings tend to be longer when working remotely because of technical problems and many people in one video-call just slow everything down. And don't get me started on the mental toll that these activities have on people. I mean imagine a mason building a wall after running a marathon. The ceremonies stress the same muscle as the work we do - the brain.

> Simplicity--the art of maximising the amount of work not done--is essential.

In the spirit of agility let's assess the meta-work that ceremonies are and find a way how to minimise the time spent on them.

- Daily: if you have a blocker, talk to someone who can help you immediately. For checking the status of work, see the board.
- Refinement, planning: in my opinion these are contradictory to the agile principles in the most blatant way. They serve only for micro-management or contract negotiation.
- Retrospective: if you have an idea how to improve the way we do our work, present it to the interested people whenever you have time. You can talk about it on lunch.
- Demo: this is probably only reasonable meeting. Gather the team and the users and show them what's been released and how to take advantage of it.

I think that it's obvious now that SCRUM ceremonies are not agile. They as a core part of the framework render it as a whole not agile. The amount of focus on meta-work itself is contradictory to agile principles which stress the importance of actually working on the software. Does that make SCRUM bad? Not necessarily but it makes it bad agile implementation.

## O True Agile, Where Art Thou?
Let's adjust the quote from the beginning: 

> Agile is like communism. It fails because it has never been implemented correctly. Because everyone tries only SCRUM.

When I read the manifesto I can get behind most of the ideas presented in it because software as a product of engineering is a volatile. It's an exploratory work. Each new project is unique even though sometimes it feels like we're doing the same thing over and over. Nevertheless building software means figuring a way how to serve the user of that software. And once we have served one group of users and we move onto another group we need to again figure out how to serve them. It will never be the same. Because if it were the exact same problem well you can just copy paste it, it's software!

Now, imagine an explorer trying to cross a jungle for the first time in the history. They can sit around and use their field glass, send out drones or whatever and construct a plan and then finally go and exercise it. It might work but probably they'll find out that they didn't take tigers in account or some similar setbacks will happen. Agile explorer would just pack his bag, pick up a machete and enter the jungle praying that the tigers that have killed the previous explorer are already full.

### My Few Ideas
- for the authors of the Agile Manifesto communication was crucial. But communication must be natural and needs no schedule. **Communicate whenever you need it, don't wait for a meeting.**
- **don't do any meta-work.** Concentrate maximum of your time on developing and/or discussing the software.
- **focus on building your own methodology**, your own practices but let them naturally surface. Like the nature of the product, the work itself is volatile. Using a prefabricated framework leads to apathy, inefficiency and bad software. **Abolish ceremonies.**
- this one might be the hardest to wrap our SCRUM-washed head around. **Consider moving away from sprints.** They don't bring much value to software developers or users. They bring value to the management because they introduce subtle deadlines and a way how to measure (although inefficiently) work. Develop whatever you agree on is most important and when you are done just pick another feature and show the finished work to the users.
- lastly **not work in an agile way doesn't necessarily mean that you have to get back to waterfall.** Agile is relying heavily on the face-to-face communication. It can be hard to work that way remotely for example. Just imagine open-source software being built in an agile way. It doesn't work. Agile is meant for small concentrated teams. **Don't be afraid to embrace a different approach.**