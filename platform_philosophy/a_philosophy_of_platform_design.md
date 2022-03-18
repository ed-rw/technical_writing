# [WIP] A Philosophy of Platform Design
_(Yes, I stole the title from Ousterhout)_

### Introduction

The concept of a "platform" is something that gets thrown around a lot these
days. Teams are dedicated to building an organizations platform. We've had the
idea of platform-as-a-service (PaaS) around for a while. I recently realized
that while I've used this term "platform" many times, I've never taken the time
to outline exactly what I mean when using that term. In this essay I'll clarify
what this concept actually means to me, and the properties that I think make a
good platform.

### What is a platform?

First, why do we use the word "platform" when we're talking about this concept?

[Merriam-Webster provides several
definitions](https://www.merriam-webster.com/dictionary/platform) of platform,
the ones that are relevant to us are:

> 1 a : a flat horizontal surface that is usually higher than the adjoining
area: such as [...] \
> b : device or structure incorporating or providing a
platform

>  6 a : operating system also : the computer architecture and equipment using a
particular operating system \
> b : an application or website that serves as a
base from which a service is provided

The first definition [precedes](https://www.etymonline.com/word/platform) the
latter, which makes sense. At some point while building software we decided to
refer to the collection of hardware and/or the OS that we were building on top
of as an abstraction known as the "platform". The Free Online Dictionary of
Computing has a [definition of platform](https://foldoc.org/platform) that
follows this idea. Something consistent here with the platform concept that I am
attempting to define is that a platform is something that is used to run code. I
will sometimes add the qualifier "runtime" to clarify that I am referring to a
platform used to run code.

Now with the growth of the internet the word platform has started to be used in
a number of different ways. We talk about smartphones and accompanying app stores as
platforms. Browsers are considered a platform. Ethereum provides platform for
decentralized applications. Cloud providers can be said to provide a platform.
In modern software (really society) we are building on top of _a lot_ of
different "surfaces". Something that differentiates these uses of the word
platform from my common usage is that they are meant to run code not created by
people in the same company/organization as the people creating the runtime
platform. For this reason I'll add the qualifier "internal" to runtime platform.


Now after that descent though what I'd like to think of as something akin to
analytic philosophy, but you may consider needlessly pedantic, we can arrive at
the definition I like for "platform":

TL;DR

**An _internal runtime platform_ is "an abstraction encompassing the systems
used to run your code".**

A platform is used to run code. It is used to run _your_ code, not other
people's. And in modern times it can involve multiple systems. Systems being
loosely defined as other (virtual) machine(s), or processes.

From this it follows that a platform exists any where your code is run - you
have a production platform, you probably have a local development platform
(possibly reimplemented by each dev in your company), you may have a platform
for testing your applications, etc. I do consider platform a different concept
than environment, though each environment will have at least one platform.

I would also say that a platform exists whether or not you intentionally built
it (assuming you run you code somewhere). So when trying to build a platform,
what should we focus on?

### What are the properties of a good platform?

Defined, Opinionated/Batteries Included, Modular/Layered (pierce-able abstractions), Scalable, Deployable


12 Factor describes properties of an application that will run well with the ideas commonly used by modern cloud platforms.


### What capabilities are provided by a good platform?

Runtime, Storage, Deployments, Service Discovery, Load Balancing & Traffic Shaping, Configuration Mgmt, Secrets Mgmt & Delivery, Observability (metrics, logs, tracing) & Access

<!-- ### Ramble about micro-platforms -->
