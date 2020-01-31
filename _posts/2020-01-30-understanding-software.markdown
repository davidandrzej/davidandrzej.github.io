---
title: Understanding software behavior
published: 2020-01-30
image: outdoor-kitchen.jpg
---

> *Note:* cross-posted from [my
   website](http://www.david-andrzejewski.com/interests.html), where I
   recently attempted to jot down some brief descriptions of the
   problem domain I'm currently focused on as well as some tools and
   techniques I am particularly interested in.

Cloud-based software systems should be considered among the most
fascinating artifacts of human civilization. They provide the
commercial and social infrastructure of modern life, with each of us
probably interacting with many of them daily. We (quite reasonably) do
so without any consideration of the dizzying complexity of the
underlying software: vast interconnected information, control, and
communication flows lurking behind the innocuous app icon on our
mobile phone screen, continuously evolving to compete in the
marketplace.

But somebody must pilot the [Ship of
Theseus](https://en.wikipedia.org/wiki/Ship_of_Theseus). While
software may ostensibly exist entirely in the pure realm of ones and
zeros stored in some source code repository, the smooth and safe
operation of a live production service is utterly dependent on the
continuous attention of human experts working within carefully
developed teams and processes.

However, these professionals cannot touch the CPUs nor smell the error
messages. In order to operate our technology, we must use
technology. Organizations achieve the extrasensory perception required
to infer the state of their systems by instrumenting components to
emit terabyte-scale streams of heterogeneous events and numerical
measurements that are in turn consumed by a [prosthetic nervous
system](https://www.sumologic.com/) built for the integration and
processing of these signals, capable of transducing them into alerts,
summaries, and data visualizations suitable for human consumption.

As the complexity and scale of systems continues to grow, a bottleneck
is emerging at the interface between the human operators and this
keyhole view into the machine world. It is therefore becoming
necessary to investigate how we might push (some of) the higher-level
"intelligence" across the divide, using automated methods to provide
human users with more relevant information, richer contexts, and more
powerful tools for exploring, formulating, and testing hypotheses
about observed system behaviors. Machine learning and data mining
technologies are natural candidate tools for this task.
