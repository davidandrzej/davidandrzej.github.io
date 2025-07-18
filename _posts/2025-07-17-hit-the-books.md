---
layout: post
title: Hitting the Books
published: 2025-07-17
image: books.jpg
---

I've recently(-ish) been doing some self-study using textbooks, and
I'm briefly capturing some reflections on the process here. As far as
I can tell most of the _actual learning_ happens as a result of:

1. my own note-taking, where I re-structure or re-schema what I'm
   reading into my own terms. This is an active process on multiple
   levels. First, I need to do some editorial curation in terms of
   what to capture, elide, or emphasize. Second, I reflect on what I'm
   jotting down: does this really make sense, are claims seem fully
   supported, what are the implications of this theorem, and so
   on. The final artifacts (pages of notes) are a nice encapsulation
   of my understanding, and I do occasionally revisit and review
   these. However, I suspect that most of the value I am getting out
   of the exercise comes from the process itself, where the active
   engagement with the material makes the content dramatically more
   "sticky" for me.
2. doing the exercises, where applicable. Generally it seems that the
   textbook authors have carefully constructed these to test and
   stretch the reader's understanding in incremental and valuable
   ways. I usually choose some sampling of intermediate-difficulty
   problems, as these feel like the best ROI on my time. I also work
   through the inline proofs myself, although I generally don't do
   them myself from scratch. It would be more accurate to say that I
   follow along very closely, working out each individual step and
   convincing myself that it is correct, at roughly the level of a
   code review. On occasion, I will try to fill in the blanks, either
   guessing ahead at what the next step should be, or looking ahead at
   a later step and trying to fill in the intermediate steps
   myself. This is less challenging than trying to develop a proof
   entirely on my own, but involves more attention and effort than
   simply reading it.

I would be remiss not to briefly mention my significant usage of
ChatGPT in this process. This topic merits its own entire writeup, but
I use the tool as a kind of "Teaching Assistant" on problems where I
get stuck, proof steps that don't make sense, stress-testing
intuitions or connections I am developing, and other general questions
that come up. An example of this was when I was doing some exercises
in Quantum Computing and I kept noticing that certain matrices had the
property $AB=-BA$, so I asked about this and learned the proper name
for the property
([_anticommutative_](https://en.wikipedia.org/wiki/Anticommutative_property))
and its connection to the [Pauli
matrices](https://en.wikipedia.org/wiki/Pauli_matrices). For
particularly interesting or tricky ideas, I've also begun vibe-coding
simple simulations or [short animated visualizations of
concepts](https://www.david-andrzejewski.com/fun/quantum.html) using
the [manim](https://github.com/ManimCommunity/manim/) "community
edition" library. As before, the process of developing one of these
scripts is itself a productive exercise in terms of building
intuitions. So for me, somewhat surprisingly, ChatGPT (or similar)
ends up being a very nice _complementary_ resource for self-study
alongside traditional textbooks.

That all being said, I should also mention the time I mis-transcribed
some of the instructor's handwriting on the whiteboard from the
[Quantum Information
Coursera](https://www.coursera.org/learn/introduction-to-quantum-information)
and mistakenly asked ChatGPT about the "CHZ quantum state" (which does
not exist) instead of the "GHZ state" the instructor was actually
talking about. Rather than asking me if I had intended to ask about
the [Greenberger–Horne–Zeilinger (GHZ)
state](https://en.wikipedia.org/wiki/Greenberger%E2%80%93Horne%E2%80%93Zeilinger_state),
ChatGPT confidently hallucinated a plausible sounding explanation
centered on 3 quantum researchers (who did indeed exist) with the
appropriate initials "CHZ" along with a related-ish paper one of them
had written (see below). The fake state and its supposed properties
were even somewhat similar to the real one! I found this failure mode
to be pretty incredible. This experience underscored the importance of
using these tools as a supplement to, but not substitute for, standard
textbooks and other canonical resources.

> The CHZ quantum state is named after its inventors: Cabello, Hardy,
> and Zukowski. The CHZ state is a three-qubit entangled state that
> has some interesting properties that make it useful for various
> quantum information processing tasks, such as quantum teleportation
> and quantum key distribution. The state was introduced in a 1999
> paper by Antonio Cabello, Lucien Hardy, and Marek Zukowski titled
> "Bell's Theorem for General N-Qubit States and Quantum Mechanics of
> Classical-Like States".

