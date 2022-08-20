---
layout: post
title: "Encoder: Elements of Clojure by Zachary Tellman"
published: 2022-08-20
image: nhs.jpg
---

> *Encoder:* experimenting with posting summaries or highlights of my
> (often quite) rough notes on books or papers I've read.

## [Elements of Clojure by Zachary Tellman](https://elementsofclojure.com/)

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Names are not the only means of creating indirection, but they are the most common. The act of writing software is the act of naming, repeated over and over again.</p>&mdash; Elements of Clojure (@elementsofclj) <a href="https://twitter.com/elementsofclj/status/1071086965913735173?ref_src=twsrc%5Etfw">December 7, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

In the earlier days of the "big data" buzzword, it seemed that perhaps
data processing and analysis could sensibly be done using the JVM due
to its rich libraries, mature tooling, and optimized
performance. However, Java seemed a bit clunky and verbose for this
purpose, opening the door for non-Java languages that targeted the
JVM, probably most notably [Scala](https://spark.apache.org/) (which
[Spark](https://spark.apache.org/) is written in) but also including a
Lisp dialect called [Clojure](https://clojure.org/). At some point, I
did some minor experimentation with using Clojure for data science,
and at any rate I found writing a bit of non-trivial code in a Lisp to
be an educational experience.

[Elements of Clojure by Zachary
Tellman](https://elementsofclojure.com/) is not intended to be an
entry point into learning Clojure, but rather to provide a conceptual
scaffolding and vocabulary for discussing higher-level tradeoffs and
design choices. From the publisher's description:

> And so this book does not offer knowledge, it offers clarity. It
> is aimed at readers who know Clojure, but struggle to articulate
> the rationale of their designs to themselves and others. Readers
> who use other languages, but have a passing familiarity with
> Clojure, may also find this book useful.

Only 1 of the 4 sections of the book is truly Clojure-specific, the
other 3 are densely packed with what I would perhaps loosely call
"applied philosophy" of programming. Much of this content seemed to be
more crisply distilled articulations of themes I've seen in
code/design review feedback I had either given or received over the
years working in (non-Clojure) software.

As promised by the description above, my experience of reading this
book was unique among technical books I've read. Rather than telling
me new things I didn't previously know (eg, how does borrow checking
work in Rust), it often gave me different ways to describe or
understand ideas that had previously been lurking in the background of
countless technical discussions.

Given all this, I don't think I could recommend it to beginning
programmers. Without a substrate of hands-on trial-and-error
experience, many of the passages I found most fascinating would
probably come across as vague fortune-cookie programming
aphorisms. But for someone who "has touched the hot stove"[^1] a few
times, the book contains many sentences that I found remarkable for
their insight and concision. Concepts are repeatedly stripped down to
their essence, abstracted from the idiosyncrasies of particular
technologies or application domains.

Two example themes that really stuck with me were naming things in
software (arguably all one can ever do, as mentioned in the excerpt
above), and careful consideration of the context in which your
software will operate:

> Over-engineering is not a property of our software, but of how we
> intend to use it.

The book also draws upon an unusual breadth and depth of references:
Frege, Baudrillard, Hoare, _Seeing Like a State_ by James L. Scott,
_Complex Adaptive Systems_ by Miller and Page, at least 2 different
short stories by Jorge Luis Borges, and so on - perhaps making this
book a great recommendation for [the engineer on your
team](https://www.linkedin.com/in/kumaravijit/) whose code review
comments cite [Leibniz's "Identity of Indiscernibles"
principle](https://en.wikipedia.org/wiki/Identity_of_indiscernibles).

If you are looking for a silver bullet salesman, keep looking. But if
the below passage resonates with you, then there is probably some cool
stuff for you here.

> This is not a problem that can be fully solved. We speak ambiguous
> words, we think ambiguous thoughts, and any project involving
> multiple people exists in a continuous state of low-level
> confusion.


[^1]: Credit [Stefan Zier](https://www.linkedin.com/in/szier/) for this euphemism (intended as a compliment) for experienced programmers, which is fundamentally in agreement with this assertion from the book: "The 'seniority' of an engineer derives more from their ability to predict adverse environments than from mastery of any particular technology."









