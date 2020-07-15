---
layout: post
title: Graph theory for product development
published: 2020-07-11
image: "project-tree.png"
---

## Context 

Software product development can be thought of as "spending" scarce
time, effort, and attention in order to (hopefully) deliver customer
value. The
[actual details](https://www.reddit.com/r/funny/comments/eccj2/how_to_draw_an_owl/)
of how this happens in practice are rarely as simple as "go build
XYZ", instead messy reality consists of a complex web of target users
and use cases, deliverables and milestones, noisy estimates, and
interlocking dependencies. Teams must navigate questions of
prioritization and sequencing in the context of this complexity and
uncertainty, and mental models frameworks can be useful tools to help
impose some order onto the chaos. This post describes one possible
framing inspired by a well-known combinatorial optimization problem
over graphs, Prize Collecting Steiner Trees (PCST).

### Minimum viable product

Let's say you are on a team building a simple analytics service to
help email marketers better understand the performance of their
campaigns.

Assuming we understand the target user needs well enough,
delivering some bare minimum system for this use case will require
implementing a handful of foundational functionalities. For example,
perhaps we require:

* instrumentation to determine if emails are opened or links are clicked, sending outcomes to ... 
* collection machinery for capturing and ingesting this data into a ... 
* database for persistently storing this information in a form suitable for ... 
* query interfaces for users to run various analyses.

### Feature backlog

The magic of software is that additional potential use cases and
capabilities beyond this basic core are limited only by the
imaginations of the users, product management (PM), and engineering
team. For example, marketing analysts may also wish to do one or more of:

* join target emails against other customer information (eg, demographics) to slice and dice success rates
* generate pleasant and informative data visualizations
* use those visualizations to create real-time business dashboards
* train predictive machine learning (ML) models to optimize email personalization
* do all of the above from their mobile device.

Of course none of this comes for free. All the additional code has to
be designed, written, tested, bugfixed, deployed, and
monitored. Weighing these costs against the expected benefits of the
resulting features is one of the principal tasks of product
development.

### Dependency structure

However there also exists an underlying dependency structure among
these enhancements. It is unlikely that you can successfully ship
"real-time dashboards" before building "basic charting", and training
ML models will require being able to integrate your click data with
other data sources for feature generation. How can we incorporate this
additional complexity into our planning and decision-making?

## Put a graph on it

Just as someone with a hammer sees all problems as nails, a Computer
Science (CS) background can lead a person to perceiving all problems
as amenable to a _graph_-based approach, which is exactly what we'll
do here. Let $G=(V,E)$ be a _directed acyclic graph_ (DAG)
representing our product roadmap, where vertices (or nodes) $v \in V$
correspond to features or capabilities (such as "basic charting") and
their incoming edges $e \in E$ correspond to the aforementioned
dependency structure. For example, if $v_{b}$ "real-time dashboarding"
requires $v_a$ "basic charting", we can represent it with a directed
edge $(v_a, v_b)$:

![Dependency edge](/assets/img/ab-edge.png){:class="img-responsive" : .center-image}

We can then define a special root vertex $r$ to represent the current
state of our system, and populate out the rest of the capabilities
and dependencies as nodes and edges connected to $r$:

![Project graph](/assets/img/project-graph.png){:class="img-responsive"}

What about the costs and benefits? We can model these with a
non-negative _cost_ function over edges $c: E \rightarrow
\mathbb{R}^+$ and a similar _profit_ function over nodes $p: V
\rightarrow \mathbb{R}^+$. Intuitively, we would like to devise our
development plans to achieve maximum benefit for minimum cost. This
goal can be translated into the problem of identifying a _connected
subgraph_ $T \subset G$ containing $r$ (in fact, $T$ will always be a _tree_) to
maximize the objective function

$$ \max_T \sum_{v' \in T_v} p(v') - \sum_{e' \in T_e} c(e')$$

where if $T = (V', E')$ then $T_v$ is the set of vertices $V'$ and
$T_e$ is the set of edges $E'$.

Each candidate solution $T \subset G$ corresponds to some tree rooted
at $r$. In our problem domain, this corresponds to a development plan
spending the effort $\sum_{e' \in T_e} c(e')$ to achieve the
milestones $v' \in T_v$. Our domain dependency constraints are
guaranteed to be met via the graph encoding, the connectivity
requirement on $T$, and the inclusion of root $r$.

![Selected tree](/assets/img/project-tree.png){:class="img-responsive"}

It turns out that this is an instance of a well-studied problem in
theoretical CS known as the
[Prize-Collecting Steiner Tree (PCST)](https://homepage.univie.ac.at/ivana.ljubic/research/pcstp/)
(ie, nodes are "prizes"). Example applications of this problem are
optimizing network layouts in
[telecommunication infrastructure](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.29.8697&rep=rep1&type=pdf)
or
[sensors in the utility grid](https://core.ac.uk/reader/159147314). The
basic problem setting is undirected and rootless, whereas the special
case shown here with directed edges and a defined root $r$ is an
instance of a _rooted Steiner arborescence_.

## Implications for project management 

The utility of a model like this can be evaluated by how it helps us
reason about situations and consider the effective allocation of
scarce resources. We can examine some some well-known product
development failure modes and advice through the lens of this
framework. In each of these scenarios we show simplified schematic
_payoff charts_ of total _cost_ (effort expended) on the x-axis
versus _profit_ (value delivered) on the y-axis.

### Peanut-buttering / breadth-first

"Peanut-buttering" refers to spreading efforts too thinly across too
many goals. Consider a relaxation of the PCST problem where you can
_partially_ buy edges, but only gain the profit when an edge is fully
purchased. In a peanut-buttering strategy, we allocate our spend across
many edges, corresponding to highly parallelizing work streams across
as many tasks as possible. The downside is that no value is delivered
whatsoever until tasks start crossing the finish line, as shown in
the payoff chart:

![Peanut buttering](/assets/img/peanut-butter.JPG){:class="img-responsive" :height="50%" width="50%" : .center-image }

In practice this strategy can be even worse than it looks here, due to
uncertainty effects that will be mentioned below.

### Over-specialization / depth-first

Going to another extreme, we can imagine pursuing some single longest
path as deeply as possible. This could correspond to building out
some very specific niche use case to the exclusion of any even basic
complementary capabilities.

![Over-specialization](/assets/img/depth-first.JPG){:class="img-responsive" :height="50%" width="50%" : .center-image }

In this scenario, we can initially make good progress but eventually
plateau into diminishing returns by continuing to invest in further
incremental improvements along this deep dependency path. Returning to
our marketing analytics example, this could be a development plan
where we continue to deliver increasingly sophisticated and esoteric
advanced ML capabilities without ever investing in even basic
visualization or reporting functionality, or data import/export
connectivity. 

### Happy medium

In the idealized case, work is done in such a way to continuously
balance the advancement of two purposes:

* deliver immediate value
* unblock subsequent high-value items.

If everything works out, the hope is that this approach can navigate
between the Scylla of overly-diffuse efforts and the Charybdis of
overy-narrow plans to yield a nice "up and to the right" payoff chart.

![Happy medium](/assets/img/medium.JPG){:class="img-responsive" :height="50%" width="50%": .center-image }

### Graphs all the way down: RPCTS for technical architecture

While the motivating examples so far focused on tangible end-user
value, we can apply the same ideas to more purely technical tracks of
work as well. In this context, the prizes might be de-risking a
particularly tricky part of the design, unblocking teammates, or
accelerating overall development through improved tooling or
infrastructure.

## [The map is not the territory](https://ciudadseva.com/texto/del-rigor-en-la-ciencia/)

Of course this model is not perfect and elides crucial complicating details that make real situations so interesting:

* team capacity is not an undifferentiated mass of abstract “points” - there are different skillsets, working styles, and team dynamics
* goals are not simple binary outcomes, the quality and particulars matter tremendously
* true costs and benefits are not actually known
* even the graph structure is probably not known
* everything is continuously changing over time, both in terms of the underlying reality as well as our own imperfect knowledge.

In such an environment, the “prizes” can take the form of new
information itself, such as learning whether the technical design can
meet the desired performance constraints or if the target feature
satisfactorily solve the customer use case. This added dimension means
that the real-life optimization problem more closely resembles messy
“explore vs exploit” trade offs than well-understood computational
bottlenecks.

### Your mileage may vary

Would I recommend literally encoding your plans into this format and
dumping them into solver software to decide the optimal course of
action? Probably not. Is it nice to have this mental model simmering
in the background of your consciousness when making judgments under
uncertainty?  Perhaps. Can visually sketching out approximations of
these graphs help communicate and coordinate within and across teams?
Try it and find out!

## References

The idea of encoding dependencies into graphs is ubiquitous in
large-scale project management, but most resources I had found were
more in the context of tracking the _execution_ of some predetermined
plan, eg with Gantt charts. The messier business of deciding _which_
areas to pursue at all, and in what order, did not seem to be the
focus in quite the same way as described here. In some sense,
[Lean Product Playbook](https://leanproductplaybook.com/) and similar
resources more closely capture the general idea and motivation, but
without the explicit graph formalisms..

PCST is known to be NP-hard, and has been the subject of very
interesting research, in particular on Linear Programming (LP)
techniques for guaranteed-factor approximation. A nice collection of
results for Steiner tree variations can be
[found here](http://theory.cs.uni-bonn.de/info5/steinerkompendium/netcompendium.pdf),
and some landmark results on this specific problem are:

* [Bienstock, Goemans,  Simchi-Levi,  Williamson](https://math.mit.edu/~goemans/PAPERS/BienstockGSW-1993-PrizeCollecting.pdf): 3-approximation
* [Goemans and Williamson](https://math.mit.edu/~goemans/PAPERS/GoemansWilliamson-1995-AGeneralApproximationTechniqueForConstrainedForestProblems.pdf): 2-approximation
* [Archer, Bateni, Hajiaghayi, Karloff](https://core.ac.uk/reader/21173016): $(2 - \epsilon)$-approximation
  


