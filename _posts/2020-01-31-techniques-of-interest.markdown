---
title: Techniques of interest
published: 2020-01-31
image: techniques.png
---

> *Note:* cross-posted from (my
   website)[http://www.david-andrzejewski.com/interests.html], where I
   recently attempted to jot down some brief descriptions of the
   problem domain I'm currently focused on as well as some tools and
   techniques I am particularly interested in.

## Machine learning

One might expect software system behavior and its associated telemetry
to be perfectly well-ordered and predictable. Setting aside the
_Entscheidungsproblem_, the complexity, dynamism, and human-driven
nature of these systems mean that, in practice, much of the data is
actually noisy or chaotic. This provides a promising environment for
machine learning and data mining: we have some domain knowledge about
the underlying structure and mechanics of the data-generating process,
but randomness and noise in the observed signals. Some example
families of relevant machine learning approaches and problem
formulations here are

* time-series modeling
* clustering and dimensionality reduction
* partial or implicit supervision
* structure extraction/induction
* exploitation of graphical structure
* anomaly or outlier detection
* classifiers and their explanations

### Population modeling

Another interesting question is how to pool or combine
data across different instances when estimating models. We
could consider each entity (eg, host machine running some
application) to be totally unique and then estimate models
for each in complete isolation. Going the other way, we
could naively estimate a single model to cover all
instances. The question of how to use metadata or domain
knowledge to best interpolate between these extremes is a
rich area for exploration, closely related to Bayesian
hierarchical modeling or parameter tying in deep neural
nets. Ideas from differential privacy may also be relevant
in this context.


### Software reliability

The challenges of ensuring that software works as intended
can easily exceed the nominal effort and cost of creating
that software in the first place, especially as you
continue to iterate. Beyond the standard best practices
around testing code and instrumenting systems, there are
exciting opportunities in this area around functional
programming, static typing, and the monitoring and testing
of complex data-dependent systems like data pipelines and
machine learning models.
          
### Approximation algorithms

Resource limitations are an inescapable reality of practical data
analytics systems, but surprisingly often it is possible to
dramatically expand the operating envelope by accepting some small
probability of non-exact results. These techniques are especially
appealing where your use case is insensitive to a small approximation
error, or if this error is insignificant in comparison to sources of
noise or distortion already present in your data.

### Product development

How do teams build the right thing, the right way? In general these
are hard problems, and can be even trickier on the frontier of novel
technologies, applications, or data resources. The effective
allocation of scarce effort and attention under conditions of
uncertainty within the context of organizational coordination across
teams and timezones is a "grand challenge" problem in its own right.

## Prior work

Previously, I worked on partially supervised probabilistic modeling of
grouped event count data with latent variables. Specifically, I
focused on text mining applications where we model word count
representations of documents with _latent topic models_, a class of
techniques that can exploit word co-occurrence patterns to recover
human-meaningful "topics". Often these purely statistical topics are
not well-aligned to ultimate end-user modeling goals, motivating my
research exploring mechanisms by which user-provided side information
or domain knowledge could help guide statistical topic recovery, and
how these learned topics could then be used in applications such as
biomedical research or national security.
