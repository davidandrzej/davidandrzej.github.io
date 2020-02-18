---
layout: post
title: Probabilistic modeling of crime scene blood
published: 2020-02-17
image: northeastern.jpg
---

> Disclaimer: IANAFB (I Am Not A Forensic Biologist): what follows
should be construed as any kind of authoritative source on these
topics (or, heaven forbid, legal advice), but rather something more
akin to an interested layman's summarization of some basic
introductory materials and research papers. Errors may abound!  Please
reach out on [Twitter](https://www.twitter.com/davidandrzej) if you
have any feedback or feel I've grossly misreprsented anything.

# Forensics: high-stakes uncertainty  

In popular culture (eg, police procedural television shows), some
stray snippet of hair is handed off to a possibly wise-cracking lab
technician who feeds it into a computer which then immediately renders
the face and dossier of the identified suspect onto the screen. The
technical details of the potentially life-or-death process of how a
stray piece of biological material can be used to support or discredit
the hypothesis that a specific person was at a particular place at a
given time are significantly more involved, and more interesting.

The following will assume some passing familiarity with the very basic
concepts of molecular biology (central dogma, human chromosomal
inheritance, and so on), roughly on the level of, say, a Chinese high
schooler or American college student.

# Basics of the data-generating process


1. PCR is used to amplify samples

2. Key reference allele variants are identified

3. Gel electrophoresis is combined with some peak thresholding to
characterize which allelic variants are present in the sample

4. This genotypes are compared to the suspect

5. If a match is found, population-level variant frequencies are
combined under the assumption of Hardy-Weinberg equilibrium to
calculate the probability of a false positive.

One critical weakness of this approach is the (up to now) implicit
"single contributor" assumption: that the retrieved sample contains
the biological materials of _exactly one_ individual. However, say
that, for example, our sample tests positive (ie, shows high
concentrations) for _three_ allelic variants. Barring some chromosomal
abnormality, contamination, or other anomaly, this strongly implies
the contribution of multiple individuals.

# More sophisticated modeling: STRMIX and beyond

This brings us to a "cutting edge" of forensic science: can we use
more sophisticated statistical modeling to overcome the limitations of
existing techniques?

## Limitation: threshold-quantization of gel peaks

## Limitation: single contributor assumption
