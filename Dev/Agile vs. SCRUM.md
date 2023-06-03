> Agile is like communism. It fails because it has never been implemented correctly.

As far as I understand the main driving force behind legends like Cunningham, Beck and Fowler gathering at a mountain cabin and instead of having a nice BBQ party coming up with the Agile Manifesto was **frustration**. They were working in the corporate environment that was awfully inflexible, punishing and just overall not suitable for developing software. I guess the kind of programmers who have been building their stuff in garage haven't faced the same problems as the manifesto-men. So it was this group of hardened and frustrated programmers who put together these [4 values](https://agilemanifesto.org/): 

>- **Individuals and interactions** over processes and tools  
>- **Working software** over comprehensive documentation  
>- **Customer collaboration** over contract negotiation  
>- **Responding to change** over following a plan

They also have come up with [12 principles](https://agilemanifesto.org/principles.html) but the core values are enough for figuring out why Agile Manifesto exists. Obviously the four things on the left were at the time sidelined in favour of the four things on the right.

Documentation, plan, processes... that sounds like *a bridge construction project!* The favourite comparison of SW development and bridge-building is a bit flawed. Civil engineering and software engineering are obviously different disciplines but so are mechanical engineering and electrical engineering. The overarching notion should be that each engineering discipline is different and thus the software engineering should be treated accordingly as a separate discipline.

Agile Manifesto was a public movement that has pointed this out and tried to give us a description of what building software is and how it should be approached.

## Idea vs. Methodology
The Agile Manifesto is an expression of an idea. A model of software development and how this kind of work should be approached. (Reading the [12 principles](https://agilemanifesto.org/principles.html) now is a good idea.)

The Agile Manifesto is not a prescriptive document. It doesn't give us a todo list that upon completion would grant us the AGILE stamp. It sure does suggest some practices but no methodologies.

>The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.

There's nothing about how, when, how often etc. should such conversation happen. It's simply saying that instead of sending an email or memo you should get up, come to your coworker and tell them what you need.

> Simplicity--the art of maximising the amount of work not done--is essential.

It's up to you to decide what this means. Minimising premature optimisation? Perhaps.

> At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behaviour accordingly.

There is nothing specific about this principle. It just states that you should confer regularly how you do your work.

What brings specificity to the table are agile frameworks. Unlike the manifesto frameworks are prescriptive. They suggest methodologies that should be practiced in order to use the framework effectively.

For example XP (extreme programming) comes up with things like sprint, pair programming, mob code review, mob programming etc. SCRUM comes up with its ceremonies aka meetings. Kanban is the ubiquitous project board.

In an essence the Agile Manifesto is exactly what manifestos are, an idea. The frameworks are then exercising the idea, interpreting the principles and values and  putting them to practice.

## SCRUM Ceremonies aren't Agile
Unfortunately SCRUM is almost synonymous to agile these days. Due to that people who would sincerely like to make agile work for their team and coworkers have often no choice but to do SCRUM.

Now, what is a ceremony? For anyone outside the SW development it's probably tight to religion or some social practice. The Cambridge dictionary:

> (a set of) formal acts, often fixed and traditional, performed on important social or religious occasions

And here's the definition of ritual which I believe to be very similar to a ceremony:

> a way of doing something in which the same actions are done in the same way every time

"formal act", "fixed", "done in the same way every time" well that sounds an awful lot like a corporate process. Let's remind ourselves the first agile value: **Individuals and interactions** over processes and tools. This is why SCRUM is flawed.

Here's a list of usual SCRUM ceremonies: daily standup, refinement, planning, retrospective, demo. 

Standup can last 5-20 minutes the other meetings can take 20 minutes to 2 hours. Often it's about 4-5 hours each sprint doing meta-work = working in order to eventually actually work on the software. On top of that many organisations and teams have company-wide meetings, various guild meetings, interest-groups meetings etc. And to take it to the extreme these meetings tend to be longer when working remotely because of technical problems and the fact that many people in one video-call just slow everything down. And don't get me started on the mental toll that these activities have on people. The ceremonies stress the same muscle as the work we do - the brain.

> Simplicity--the art of maximising the amount of work not done--is essential.

In the spirit of agility let's assess the meta-work that ceremonies are and find a way how to minimise the time spent on them.

- Daily: if you have a blocker, talk to someone who can help you immediately. For checking the status of work, see the board.
- Refinement, planning: in my opinion these are contradictory to the agile principles in the most blatant way. They serve only as micro-management tools.
- Retrospective: if you have an idea how to improve the way we do our work, present it to the interested people whenever you have time. You can talk about it at lunchtime.
- Demo, review: this is probably only reasonable meeting. Gather the team and the users and show them what's been released and how to take advantage of it.

SCRUM ceremonies are not necessary and definitely not agile. They as a core part of the framework render it as a whole not agile. The amount of focus on meta-work itself is contradictory to agile principles which stress the importance of actually working on the software. Does that make SCRUM bad? Not necessarily but it makes it bad agile implementation.

> Agile is like communism. It fails because it has never been implemented correctly. *Because everyone tries only SCRUM.*

### My Few Ideas
- for the authors of the Agile Manifesto communication was crucial. But communication must be natural and needs no schedule. **Communicate whenever you need it, don't wait for a meeting.**
- **don't do any meta-work.** Concentrate maximum of your time on developing and/or discussing the software.
- **focus on building your own methodology**, your own practices and let them naturally surface. Like the nature of the product, the work itself is volatile. Using a prefabricated framework leads to apathy, inefficiency and bad software. **Abolish ceremonies.**
- **Consider moving away from sprints.** They don't bring much value to software developers or users. They bring value to the management because they introduce subtle deadlines and a way how to measure (although inefficiently) work. Develop whatever you agree on is most important and when you are done just pick another feature and show the finished work to the users.
- lastly **not working in an agile way doesn't necessarily mean that you have to get back to waterfall.** Agile is relying heavily on the face-to-face communication. It can be hard to work that way remotely for example. Just imagine open-source software being built in an agile way. It doesn't work. Agile is meant for small concentrated teams. **Don't be afraid to embrace a different approach.** 