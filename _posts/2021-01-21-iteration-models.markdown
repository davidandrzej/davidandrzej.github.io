---
layout: post
title: "Models and iteration speed in coding"
published: 2021-01-21
image: wiener-cat.jpg
---

> "The best material model of a cat is another, or preferably the same, cat." -Arturo Rosenblueth and Norbert Wiener, [The Role of Models in Science](https://nemenmanlab.org/~ilya/images/9/99/Rosenblueth-wiener-1945.pdf)

What do programmers do when they are programming? One interpretation
is that they are high-throughput empiricists, iteratively developing
and testing many small hypotheses about what various pieces of code
(including their own!) _actually do_ by quickly running many
micro-experiments. Thinking about how to make these experiments fast,
cheap, and reliable can be a useful lens for understanding the costs
and benefits of various software development settings, tools, and
practices.

## Software development: a day in the life

A few significant challenges around coding are

1. not knowing what we are trying to do
1. not knowing how to do it
1. not knowing if we’ve successfully done it

Challenge 1 is often a bigger picture business context question that
we’ll set aside for this discussion, but Challenges 2 & 3 arguably
constitute a sizable chunk of day-to-day “hands on keyboard”
development activity. For a very simple example, say we have a data
structure representing a set of customer orders and we want to find
the order with the largest purchase price. This use case is probably
easy to accomplish with the standard libraries, but maybe we don’t
know the exact invocations off the top of our heads. By all means we
should certainly [RTFM](https://en.wikipedia.org/wiki/RTFM), but to
know for sure the fastest and easiest thing might be to work it out
empirically with a small code snippet. This could be done in the
[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop),
via a quick script, or in a small unit test. Minutes of trial and
error tinkering here could save hours of debugging later when the
larger system isn’t behaving as intended.

## Fast feedback, high fidelity

This kind of cheap, iterative experimentation with fast feedback is
the closest thing to a “free lunch” as is likely to found in software
development productivity. So what exactly is going on here? In the
above example is our simple script, test, or REPL session is acting a
_model_ of the use case in our program, preserving the essential
characteristics while being more amenable to rapid experimentation
than the full system we're building. The critical properties of such a
model are:

1. _Fast feedback_: quick and easy cycles from making changes to observing their results 
1. _High fidelity_: reasonable likelihood that behaviors will transfer
   or replicate to the true target context

_Fast feedback_ is important because, as nicely described in
["You are solving the wrong problem"](https://uxmag.com/articles/you-are-solving-the-wrong-problem),
the limiting factor in this mode of developer productivity is the
number of experiments we can run, and faster cycle times means more
iterations. Back to our example, imagine how painful it would be if
understanding each minor change to our hypothetical
`largestPurchase()` function required re-compiling a 1M LOC
application, packaging and deploying it, and then manually verifying
the behavior from some UI flow.

_High fidelty_ is critical to the usefulness of the experimental
findings. If the experimental context is too far removed from the
target environment, we run the risk that our results do not apply in
the settings we care about. Simple examples of this are a unit test
where the test stub of an external dependency diverges siginficantly
from the implementation, or the
["works on my machine" phenomenon](https://blog.codinghorror.com/the-works-on-my-machine-certification-program/).

In the ideal case, imagine working in some kind of magical
"ultimate debug mode" that instantly surfaced arbitrarily detailed
information about the entire set of consequences of even the smallest
change exactly as they would play out in the full system. 

## Success stories

We can apply this approach to understand the appeal and utility of
various development technologies and approaches:

- Data Science Notebooks
- JavaScript in the browser
- REPLs
- Test-driven development (TDD)
- Compilers, type checkers, and linters

All of the above leverage interactivity to quickly convey the impacts
of small changes back to the user. In the cases of Data Science
Notebooks and JavaScript, the target environment itself is well-suited
to direct experimentation (data analysis in the web notebook, or
webpage behavior in the browser). REPLs and TDD can be used to quickly
test and verify the behavior of isolated pieces of code, after which
the user can reason about how those findings will translate into the
program context. Compile-time or IDE-assisted type checking and linting
can also be thought of in this way: these tools embody some very
limited model of the program, and can therefore give you very fast
feedback about your changes, such as "you are referencing an undefined
variable", "you are trying to do arithmetic on a String", and so on.

## More challenging domains

Looking for cases where it is _difficult_ to get this kind of fast and
reliable feedback can also be an interesting exercise. These cases are
often instantiations of the "Norbert Wiener's cat" quoted above: truly
high fidelity experiments require basically doing the thing for real
(i.e., the only model is the actual cat), which can incur long feedback
cycle times, business risk, or other costs.

### Microservices

Coding in a microservices architecture often involves dependencies on
other services, which raises the question of how one can quicky
experiment and verify your understanding of other services and your
own code's usage of them.  Spinning up an entire versions of the full
service may be complex or impractical (failing _fast feedback_), and
test fixtures or other simulators of other services may not be fully
realistic (failing _high fidelity_). Adapting development tools and
practices to microservices is a huge topic, which is a testament to
the difficulties here. For a much deeper and more comprehensive
discussion of this issue, see
["Testing Microservices, the sane way"](https://copyconstruct.medium.com/testing-microservices-the-sane-way-9bb31d158c16)
by Cindy Sridharan.

### Infrastructure

"Infrastructure as code" is a popular phrase, but (so far) the IDE is
unlikely to be able to tell us what is going to happen when we switch
over to a different load balancer, spin up a new service, or change
the firewall rules. The lower-level details at play here tend to
resist abstraction (hard to get _high fidelity_), with practices
converging towards some variant of “try it and see” (which can suffer
from expensive _feedback_ cycles).

### X as a Service

Applications increasingly involve stitching together external services
provided by cloud providers and other platforms. In some sense, we can
consider these as "external microservices", and they inherit many of
the same complications, albeit while being possibly even more opaque.

## Evaluating ideas and improving pain points

To the extent that this framework accurately captures characteristics
of software development, what can it tell us? Whenever we encounter
excessive developer tedium or friction, we can try to see if we are
suffering from cases where our models of the target system lack
fidelity, have long feedback cycles, or both. Possible approaches to
improving things can likewise then be understood as attacking one of
these fronts:

1. developing a _higher fidelity_ proxy or model to the target system
2. getting _faster feedback_ on the existing target

Many emerging tools or practices around microservices, infrastructure,
and cloud applications can be understood as trying to enable faster
feedback cycles. Stretching the "Norbert Wiener's cat" analogy to the
breaking point, the "test in prod" school of thought is arguably about
builiding a suitably robust, flexible, and well-instrumented cat. On
the other hand, trying to develop higher fidelity simulations or
models of these environments (without using the actual cat) seems like
a relatively less well-explored direction so far.












