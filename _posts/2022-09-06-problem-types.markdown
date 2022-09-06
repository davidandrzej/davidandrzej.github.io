---
layout: post
title: "Software problems"
published: 2022-09-05
image: 4thAndKing.jpg
---

# What do you do with a problem like software?

Everyone in technology loves solving problems, you can just read their
cover letters and LinkedIn bios where they say so. But what are
"problems" in the context of software, exactly? 

What follows below is a crude and idiosyncratic categorization of some
different problem flavors one might encounter in software
development. If this line of inquiry sounds intriguing, I would highly
recommend reading the classic essay [*No Silver Bullet--Essence and
Accident in Software
Engineering*](http://worrydream.com/refs/Brooks-NoSilverBullet.pdf) by
Frederick P. Brooks, Jr.


## Code Problems

You have an `accountId` provided as an argument to a method you're
working in, but in order to make a required API call you actually need
a `customerId`. There is another microservice that can perform the
necessary translation, but the class you're working in doesn't have a
handle to it in scope. You will need to ensure a valid handle is
available to your class at construction-time. However, this service is
not currently used in the particular binary you're working on, so you
need to familiarize yourself with the mechanics of the underlying
service discovery and runtime dependency injection to wire it all
up. Also you now need some additional mocking or stubbing for
automated testing of your method to avoid relying on external
services. Finally, after all of this you are able to
`getAccountDetails()`, and it is a big hit at the biweekly sprint
review.

The preceding stylized fiction is an example of what we could call
_Code Problems_: difficulties encountered in achieving our goals that
are largely artifacts of the organization and structure of the code
itself. You're not up against any fundamental laws of nature here,
it's just that, as-is, the code doesn't currently do what you want and
you'll need to re-arrange a few things to remedy that. 

### What to do about Code Problems?

Ask this question to 2 software engineers and get 3 answers. Many
"best (?) practices” can be interpreted as attempting to minimize Code
Problems, such as Test Driven Development (TDD), static type systems,
pair programming, Functional Programming (FP), design/code reviews,
and so on. Refactoring can help make code easier to work with,
but is also likely subject to diminishing returns. 

It isn’t obvious (to me) if there exist any conclusive answers or
one-size-fits-all fixes. Both [Dan
Luu](https://danluu.com/empirical-pl/) and [Hillel
Wayne](https://twitter.com/hillelogram/status/1119709859979714560?s=20&t=Akmo-0GWe-DUHHIsuVYuGQ)
have conducted interesting surveys of empirical software engineering
research. See for yourself, but the results are generally mixed.

One other thought is that the sums of money at stake in software
development are vast. If there were $100 bills of "free lunch"
productivity improvements lying on the ground, wouldn’t someone have
already picked them up? Of course there would never be any forward
progress on anything if people took this line of thinking too
seriously, but it would seem surprising for there to be massive
obvious wins hiding in plain sight in a such a fast-moving and
competitive industry.

## Physics Problems

> As a _business analyst_, I want to _query unlimited amounts of data
> instantly and for free_, so that I can _answer any arbitrary question
> that pops into my head_.

Cloud-related advertising you might see at the airport
notwithstanding, both the data and calculations required by the
aforementioned use case are, at present, regrettably carried out by
physical storage and compute devices, with all of their attendant
costs and limitations.

It may be a bit obvious or simplistic to put it this way, but this
physical reality means that

- data (ie, actual 1’s & 0’s) has to be **physically** moved to some compute device: this includes networking, memory to cache, and beyond
- some compute device (CPU, GPU, TPU, or Quantum) has to perform the desired Beta reductions, run the Turing machine, etc

These (ultimately) physics-imposed constraints (of current
technologies) can therefore, in some sense, be described as ‌*Physics
Problems*.

### What to do about Physics Problems?

For reasons that are probably fascinating in their own right, Computer
Science education seems to pay a great deal of attention to this
topic. Let’s define Computer Science Cleverness™ as the study of how
to eke out a bit (or a lot) more “bang for the buck” by organizing or
implementing our systems differently. This could include things like
caching tricks, improved algorithms, well-suited architectural
choices, or various micro-optimizations up and down the stack.

Armed with our requirements and Computer Science Cleverness™, we then
have (at least) three possible ways to deal with Physics Problems:

1. Balancing the tradeoffs between desired scale and performance and the costs and capabilities of available resources - on some level this may mean either spending more money or compromising on performance
2. Using Computer Science Cleverness™ 
3. Wait a bit for Applied Physicists and Electrical Engineers to somehow bail you out with their own brand of cleverness

Given the Net Present Value (NPV) of a delivering software solution
today versus waiting for Physicists and EE's to invent solutions to
your problems, teams tend to opt for some mixture of 1 and 2 in
practice.


## Reality Problems

> If people do not believe that mathematics is simple, it is only
> because they do not realize how complicated life is. -[John von
> Neumann](https://en.wikiquote.org/wiki/John_von_Neumann#Quotes)

On this topic, I would highly advise checking out [Hillel Wayne's
recommendation](https://buttondown.email/hillelwayne/archive/data-and-reality-2nd-edition/)
of _Data and Reality_. In the very first chapter of that book,
seemingly trivial everyday notions ("what is a thing") are thoroughly
inspected, and quick or easy answers are mercilessly ripped to shreds.
What is so difficult about encoding "common sense" in software? At
least part of the issue is that the dumb precision of code
necessitates explicit reckoning with a combinatorial explosion of
subtleties that, in everyday life, can (usually) be successfully
navigated well enough by an embodied human intelligence capable of
combining contextual cues with prior knowledge. This gap between human
day-to-day reasoning capabilities and the effort required to codify
"correct" behavior in software is an endless source of challenges and
bugs.

For another perspective, talk with anyone who has ever worked on
medical or governmental software. The dizzying complexity of the
target bureaucratic system cannot help but be reflected in any
software designed to interact with it. These concerns constitute
*Reality Problems*, and these challenges are more or less irreducible,
inherent to the real-world objectives of your software development
endeavors.

### What to do about Reality Problems?

Can we find an easier reality? Here it may be beneficial to widen the
scope of your solution space to include the context in which your
software will be used. If 0.001% of cases require escalation to some
human judgment, maybe that’s ok, especially if excluding those cases
from the scope of requirements for the software may make things 1000x
easier.

Zachary Tellman's fascinating [*Elements of
Clojure*](http://blog.david-andrzejewski.com/elements-of-clojure.html)
articulates this nicely. Paraphrasing an idea that I found
particularly resonant from that book, we could say that what is
commonly meant by “over-engineered” is that a system correctly handles
a _broader range of inputs or operating conditions_ than is necessary
or intended, whereas conversely an “under-engineered” system exhibits
degraded or undesirable behaviors in some contexts in which we _do_
wish it to work properly. Distinguishing between the two, especially
in collaborative work, therefore requires carefully establishing a
common understanding of the target environments and use cases.

## The Actual Problem

Setting aside code organization, performance/resource constraints, and
the mind-boggling complexity of the real world, there is still the
_actual original problem_ you are trying to solve, eg enabling the
user to buy a widget from their phone. Assuming the problem itself is
indeed the right problem (a major undertaking on its own), how can we
achieve the desired goals? 

### What to do about The Actual Problem?

A particularly memorable Computer Science course I had the opportunity
to take was [Special Topics Seminar in Approximation
Algorithms](https://pages.cs.wisc.edu/~shuchi/courses/880-S07/).
Besides the fascinating content and expert instructor, part of what
made it interesting was that the other students in the class were
deeper specialists in CS Theory than I had typically encountered. I
was struck by the ease and rapidity with which, upon seeing
essentially any algorithmic problem, my classmates would pause like
the Mentat in Denis Villenueve's _Dune_ for 2 seconds before
proclaiming something like "reduces to Hamiltonian Cycle."[^1]

Mapping new situations to a "vocabulary" of known patterns is a
powerful technique that seems to recur across domains[^2], and it is
not clear why software should be any different.  To what extent is
your specific task a completely unique snowflake? Accepting that even
highly innovative systems contain many "commodity" problems, much of
the work becomes deconstructing your situation into its atomic pieces,
mapping them to known solutions, modifying or adapting them to your
specific circumstances where necessary, and appropriately combining
them to yield the desired result. 

This is not to say one can simply master this vocabulary and
relax. Rapid evolution in hardware, infrastructure, ecosystems, and
tooling mean that yesterday's solutions may not map perfectly to
today's problems. A solid understanding of the strengths, weaknesses,
and nuances of different techniques is critical to applying them
intelligently in new situations.

## Meta-problem: problem management

Which problems are the most important? As the classic senior engineer
maxim goes: “it depends”. In any given context, it becomes a
meta-problem to identify, categorize, and assess the severity of the
various problems, as well as to understand the _relationships_ among
them. For example, code that is highly optimized for performance (to
solve _Physics Problems_) may be tricky to later refactor or extend,
creating _Code Problems_ for future engineers (possibly including your
future self). Navigating this dynamic portfolio of interrelated
problems is arguably a significant piece of what effective software
engineers get paid to do.

Furthermore, this discussion has focused primarily on problems
associated with **the code itself**. Many of the thorniest challenges
occur at a remove from the technical details, having to do with
concerns at the "human level of the stack" such as coordination,
communication, and alignment. These deserve an altogether separate
discussion.


[^1]: Fun example: given a collection of key-value "documents", what is the minimum set of keys required for each docoument to be uniquely identified? [Why Decluttering Complex Data in Legends is Hard](https://www.sumologic.com/blog/organizing-data-legends/)
[^2]: [The Cognitive Cost Of Expertise](https://www.wired.com/2010/11/the-cognitive-cost-of-expertise/), _WIRED_.
