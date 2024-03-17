---
layout: post
title: Conway and Coase on Collaboration in Software
published: 2024-03-17
image: basketball.jpg
---

Building software is a team sport, but who's on your team? The answer may surprise you!

## Conway & Coase

[Conway’s Law](https://martinfowler.com/bliki/ConwaysLaw.html) states that the structure of a large software project will inevitably come to resemble the organizational structure of the teams who build it. Colloquially, you are destined to “ship your org chart.” A critical insight here is the immense influence of human coordination mechanics on how software is built.

Loosely speaking, [Coase’s Theory of the Firm](https://onlinelibrary.wiley.com/doi/full/10.1111/j.1468-0335.1937.tb00002.x) answers the question: if markets are so effective a means of coordinating activity, why do we have sizable firms that internally use non-market information aggregation and decision-making processes? Oversimplifying, the answer is *transaction costs*: compared with simple command-and-control authority (eg, your boss tells you to do something), market transactions may entail additional friction in the form of price discovery, negotiation, contracts and assurances, and other coordination. 

However, as technology and processes evolve, the “frontier” of which needs can be best met internally (via in-house capabilities) or externally (via the market) *can shift*. For example, standardization of a given physical input (like screws, or integrated circuits) can facilitate the sourcing of these components from third-party suppliers in the marketplace by decreasing the transaction costs. 

## The Cloud & SaaS

We might consider the evolution of the software industry through this lens. Open-source or commercial libraries or systems such as databases are analogous to physical inputs to a manufacturing process and have long been a part of the “software supply chain." More recently, cloud computing has exploded in popularity and Software-as-a-Service (SaaS) vendors and use cases have rapidly proliferated. 

For many SaaS vendors, the explicit value proposition for their customers is that acquiring the associated functionality (when not deemed essential to competitive differentiation) from the vendor can be a more attractive proposition than expensive and risky custom software development. Why should your business build your own payroll, authentication, or customer support systems? Ideally, this is a classic story of gains from specialization and trade: the vast majority of businesses are much better off outsourcing these functionalities to a constellation of external vendors who are each manically focused on their respective domains.

Taken together, Conway and Coase give us some interesting tools with which to think about modern software. In some sense, _using AWS is a specially structured and intermediated collaboration with the Amazon teams who build and operate those services_. If you build your application on AWS, certain architectural design patterns fit more naturally with the assortment of services offered by AWS, and in fact this is explicitly captured in in their various [best practice architecture guidance docs](https://aws.amazon.com/architecture/). It’s Conway’s Law in action, but you’re shipping the AWS service offering catalog (ie, *their* org chart)! In a further fun twist, many of the aforementioned SaaS vendors are providing some coherent bundle of functionality and business value by building their services *on top of AWS*. 

## The past and future of software and coordination

One potential perspective on this dynamic is that recent technical and organizational changes have lowered transaction costs and shifted the "build-vs-buy" boundary between problems best tackled internally versus those where it makes more sense to shop for solutions in the marketplace. Software engineers have excellent reasons for building their apps by cleverly combining various vendor APIs and cloud services, but perhaps don't often enough have the opportunity to step back and appreciate the deeper nature of the implicit globe-spanning inter-firm collaboration networks in which they are participating. While these ideas can be useful for understanding the recent history of software, it is an interesting open question whether they can help us navigate its near future as well.

> Practical men, who believe themselves to be quite exempt from any intellectual influence, are usually the slaves of some defunct economist. -[John Maynard Keynes](https://en.wikiquote.org/wiki/John_Maynard_Keynes#The_General_Theory_of_Employment,_Interest_and_Money_(1936))
