---
tags:
  - DDD
  - softwareDesign
  - betsys
  - en
---
# Domain-Driven Design by Eric Evans
When I took on my current role at [Betsys](https://www.betsys.com/) as a Node.js developer, I was quite thrilled to start working in a whole new field, both in terms of programming, since I was a FE developer before, and also from the business perspective since I used to work at a software agency and now I'm working on a product. There were plenty of things that I had to learn, e.g. the Nest.js framework, Angular to help also on FE side of the application, hexagonal architecture and **DDD** - Domain-Driven Design. 

This concept was unknown to me even though it's apparently been around for quite some time and has gained a lot of popularity among those who design robust software systems - the enterprise kind. I did get some introduction to the topic from my team members but that wasn't enough. I then found out the origin of this concept - which is the book by Eric Evans. 

This article would be too long if I were to sum up the whole book, so I have focused only on the main principles that you're gonna need if you want to employ DDD. The rest of the book, that I have not covered, is also full of examples which are really helpful, but I don't see the point in copying them here.

## Ubiquitous language

Fans of Philip K. Dick should be intrigued when they see the word _ubiquitous_ or shortly [_Ubik_](https://www.supersummary.com/ubik/summary/). But in the case of DDD this isn’t a spray that reverses regression of time and space. The ubiquitous language is actually a foundation of DDD. If all you take from DDD is ubiquitous language, then you have already learned an important lesson.

Usually people who work with code, people who design graphical interfaces, people who work with clients… they all tend to have their own jargon, specific vocabulary. One group might refer to a user of an application as a client, other as a customer. Developers can call a group of data a table but to a business analyst these are simply stock items. When these professionals get together their _languages_ may collide. Someone may stand out as a so to speak translator, a person who have learnt multiple of these languages. Then they become a bottleneck of the communication.

The fact that different professions have their way to speak and talk about they work is… well a fact. We would hardly get them to change they jargon and it wouldn’t be much useful. But people naturally, when trying to achieve a common goal, want to and try to communicate effectively. Paying attention to this human trait, cultivating it and investing in it our time and energy bears fruit.

So on a software project different teams have their _language_ but they share a common goal. They want to develop a piece of software and they need to talk about it for various reasons. We also need to realise that the communication is crucial. Software development is a teamwork (mostly) and core concept in teamwork is communication. Key thing to achieving smooth and effective communication is minimising ambiguity and maximising clarity. We all need to be on the same page. Thus we need a common language to talk, write, document, model, plan… our project.

It would be naive thinking that such language can be put together at the beginning of a project and used effectively during the whole life of the project. Ubiquitous language should feel natural so its creation must also be natural and natural processes take some time. Basically the whole team and even clients, everyone involved in the project should right from the beginning at least know that there is a goal of having some ubiquitous language. A bit contrary to the beginning of this paragraph, a significant amount of the vocabulary will be created at the initial phase of the project as the basic form of a model will be put together. Some foundation has to be present when embarking on an adventure that developing software is. But this foundation must be scrutinised. Throughout the project’s life more and more precise language and model will be shaped naturally.

Important notion about the foundation of and ubiquitous language is that it should not be a synthetic mix of different jargons, vocabularies etc. The DDD defines a _domain expert_, a person who knows the most about the project’s domain. It can be for example a user of the to be created SW. Now the domain expert’s language should be the foundation of the ubiquitous language. We want the whole team to be able to talk about the domain and using an existing language is natural, compared to making up a completely new one probably consisting of a professional vocabulary forced on to the domain. I can even imagine this foundation being right in the beginning of a project altered by let’s say a developer to better reflect how the domain will be represented in the model and the actual code. But this is already initialising the process of creating a working ubiquitous language.

The ubiquitous language is quite similar to what is in linguistics called a _pidgin._ The pidgin is a kind of made up language. When two tradesmen from different cultures have met for the first time, speaking completely different languages but sharing a common goal - making a deal - they would eventually create a new language, simplified mixture of the two original languages designed only to achieve the common goal.

### Practical tips for ubiquitous language

-   keep an up to date dictionary. It's an easy to maintain documentation of the project and can help immensely to onboard new team members.
-   discuss and scrutinise the language as often as you can, this way you not only get a consensus but also make everyone consider twice how will they name their next variable, function etc.


![Example from the book](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xg7skdyj5cklj70pmyxi.jpeg)

## Isolating the domain

It can be hard to focus on one _thing_ when another _thing_ gets in your way. How can you find anything in your drawer when there is everything in there. It would be much more practical to have a few drawers one for each kind of things you want to keep there. If you are familiar with the office drawer cabinet you can take that as an illustration of the concept that will unfold on the lines to come.

Understandably the DDD must focus on domain. That is the one thing. But when developing an application there is more things that we have to deal with other than domain. We need to show something to the user, we need to store data somewhere, etc. An quite often in an OOP program the domain is spread in the whole project. There is a piece in the UI, piece in a controller and some of it right at the place where we query our database. At scale this brings a lot of problems. It gets hard to follow the trace and we can easily change the business logic when fixing some UI issue. Much like when we want to get something from a drawer everything in it moves inevitably and uncontrollably.

The solution presented by DDD and a prerequisite for applying the DDD principles is to separate concerns. Most importantly, isolate the domain from the rest of the application. The separation of concerns can be fairly complex but commonly it is done by creating layers. The DDD requires practically just two layers - domain layer and everything else layer - but that wouldn’t be thorough. So instead of such simplistic solution, DDD encourages at least 4 layered structure. The layers are: UI layer, application layer, domain layer, infrastructure layer.

|Layer                                 |Description   |
|--------------------------------------|--------------|
|User Interface (or Presentation Layer)|Responsible for showing information to the user and interpreting the user's commands. The external actor might sometimes be another computer system rather than a human user.|
|Application Layer                     |Defines the jobs the software is supposed to do and directs the expressive domain objects to work out problems. The tasks this layer is responsible for are meaningful to the business or necessary for interaction with the application layers of other systems. This layer is kept thin. It does not contain business rules or knowledge, but only coordinates tasks and delegates work to collaborations of domain objects in the next layer down. It does not have state reflecting the business situation, but it can have state that reflects the progress of a task for the user or the program.|
|Domain Layer (or Model Layer)         |Responsible for representing concepts of the business, information about the business situation, and business rules. State that reflects the business situation is controlled and used here, even though the technical details of storing it are delegated to the infrastructure. This layer is the heart of business software.|
|Infrastructure Layer                  |Provides generic technical capabilities that support the higher layers: message sending for the application, persistence for the domain, drawing widgets for the UI, and so on. The infrastructure layer may also support the pattern of interactions between the four layers through an architectural framework.|
*Evans, E. (2004) Domain-Driven Design. p. 70*

DDD only *really requires* one isolated layer which is the Domain Layer.

> The "domain layer" is the manifestation of the domain model and all directly related design elements.

Simply because it's impractical to mix the domain with other parts of a program - the domain model must be separated. How we decide to further isolate other parts of the structure is entirely up to us. 

## Expressing the domain-model in the software
### Entity
Basis of any domain model are objects. They describe different actors, patients, commodities etc. of the domain and in OOP they carry the actions that can be invoked on them. Some of these objects are unique. Like a customer for example. We need to be sure that one customer can't be mistaken for another. We need to express and ensure their uniqueness within the program. These objects are called Entities in DDD.

The uniqueness of an Entity mustn't rely simply on its attributes. There can be two customers living in the same building and having the same name. There is thousands of Toyota Corollas yet they are not the same. Each of them has some kind of identifier to tell them apart. Perhaps a VIN number. Similar to that, Entities tend to have an ID (or some other unique attribute, a fingerprint).

To ensure system that is not error prone we need to match Entities predominantly by these fingerprints. Creating such IDs that persist through time and even in distributed or mixed systems is a delicate matter. Still the concern of DDD is to have unique entities identified.

### Value Object

Many objects have no conceptual identity. These objects describe some characteristic of a thing. They are not merely missing an identity they are holding a value that can be used independent of its application. E. g. digit 7 doesn't need any ID because it's nothing unique. You can use it in "17" or "57" and we don't care which instance of the digit 7 you have used. 

Another example is a child drawing a picture with crayons. If the kid wants to use a yellow crayon to draw sun and there is 3 yellow crayons on the table, the child doesn't care which one they use. Its identity is irrelevant. But if the crayon is a storage item of an art supply store we may want to identify it in some way.

Whether an object is a VO or an Entity is something to be discussed and depends on the context. When we design a model we should ask ourselves do we need this object to be differentiated from others? If the answer is "Yes." then it's an Entity and vice versa.

An Entity may be comprised of VOs. VO can be, since they aren't unique, reused or shared by Entities. For example when two people have a same name we don't need to create a second "John" we can reuse the first one. But to make sure this is safe VOs must be immutable. So to change a value you need to use another VO and not change the original one's value. If John changes his name to Clarence we mustn't change the content of the "John" VO, we need to use the "Clarence" VO. 

> A Value Object can give information about an Entity. It should be conceptually whole.

### Services

In OOP developers fit everything from the domain to objects - attributes and functionalities. The same developers commonly stumble upon a functionality that they can't properly assign to an object because it may fit to multiple objects or none at all. Such functionalities are in DDD called Services. They are independent from Entities and VOs. We keep Services separated in order to not distort conceptuality of Entities and VOs and they hold **no state**. 

Services are also called operations. Each operation should perform one functionality, its name should come from Ubiquitous language. Parameters and results of an operation should be domain objects.

---
If you are not a fan of OOP you may take this a step forward and separate all the functionality from domain objects. Keep in mind that this article focuses on the book by Eric Evans but DDD is not exclusive to OOP as it may seem in this book. Actually DDD fits well with functional programming and it's compositional principle. You can learn more about that in videos by [Scott Wlaschin](https://www.youtube.com/watch?v=2JB1_e5wZmU) And feel free not to constrain yourself with the choice between those two paradigms, in fact at our company we mix concepts from both and the result is great developer experience. 

---
## Conclusion
This book has a lot more to offer: how to refactor toward a deeper domain insight, practical examples, using DDD in large-scale application... I only wanted to offer you a summary of the main concepts but I strongly recommend you to explore the book yourself.
