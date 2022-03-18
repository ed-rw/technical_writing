# [WIP] Criteria for Evaluating Software Organizations

## Introduction

This is my attempt to put together criteria that can be used as part of a rubric
for grading software engineering organizations. These are criteria that I've
noticed that I think are important for organizations to get right in order to be
successful and fulfilling for members. It's worth noting that this list may
be somewhat biased by my history of only being an individual contributor (IC),
and will probably evolve over time.

I've broken the criteria into five broad categories - communication,
organizational effectiveness, product, technical, and compensation. I've tried
to keep these criteria fairly independent, wouldn't want to knock an org too
many times for one thing, but obviously some things (like communication) can
have a lot of influence on others. I've tried to explain why these criteria are
important, and examples of good and bad for each criteria. I was tempted to try
to apply weights to some of these criteria, but then I don't think I would have
ever gotten this finished. At this time I am trying to consider all of these
items as equally important. With this in mind, don't read too much into ordering
here.


## Rubric Criteria

### Communication

I originally had communication as just one criteria, but it feels too important
for that. I've broken it into two pieces, information transfer and feedback.
Organizations are all about getting groups of people to work together, and
communication between people is the most fundamental need in order for that to
happen.

Communication in an organization is something that has been written about
extensively, and by people much smarter than me. This is also something not
unique to software engineering organizations, all groups of human beings (and
really even animals) need communication in order to work together. Continually
asking the question of how organizations can be more effective and efficient
with their communications is one of the best things a company or team can do to
be successful.

#### Information Transfer

While all communication can be considering information transfer, what I am
referring to here is how information (_e.g._ changes to a service API,
vision/goals, instances being decommissioned, etc.) moves between individuals on
teams, and between teams in the organization. Communication, and especially this
component of it - information transfer, is something that can influence a lot of
the other criteria. It is hard to have any sense of what is going on if
communication is poor.

What I'm thinking about when evaluating information transfer in an organization
is how effective and efficient is the flow of information. Effective information
transfer means that information gets to the right people at the right time.
Efficient information transfer means that the transfer is targeted to just the
people that need to receive it (as defined by the receiver), and people that
aren't concerned with the information don't receive it. Optimizing solely for
one of these components often comes at the expense of the other. You could
effectively transfer your information by using the `@channel` tag in a Slack
channel that the whole company is in, but this would by no means be efficient.
On the other hand, efficient information transfer has to solve the hard problem
of knowing which people in the organization are interested in the information
you have. Without mind readers, an over optimization of efficiency will
invariably end up excluding some people that are interested in the information.

Organizations that are top notch at information transfer are going to be doing a
good job optimizing both the effectiveness and efficiency of their
communication.  People will receive relevant, useful information at a time when
it is actionable. A telltale sign of organizations that are not competent at
information transfer will be people receiving information too late for it to be
actionable, or not at all (ineffectiveness). It can also be the case that people
are exposed to too much information (inefficiency), and either ignore the
information they receive or waste an inordinate amount of their time trying to
parse through it to find things that are relevant to them.

#### Feedback

While feedback is information transfer, it is a very special (and important)
type information transfer. It is the transfer of information from the
organization back to an individual on what they are doing that works
(affirmative feedback) and doesn't work well (constructive feedback) for the
organization. This is important since it gives individuals the opportunity to
double down on, or adjust, certain behaviors to better align with what the
organization needs. Some very perceptive individuals may be able to figure out
how best to adapt to the organization without feedback, but the most effective
and efficient way for all individuals is for them to have feedback communicated
directly to them.

Good feedback is specific, timely, and actionable. This means it relates to a
specific behavior and event. The feedback is given within a short time frame of
an example of the behavior occurring (as soon as is appropriate), and contain
information on how the individual should act moving forward. There are
[models](https://jacobian.org/2021/apr/22/three-feedback-models/) you can use
for giving feedback that help structure this information.

Feedback should not be limited to just things people should do differently, it
should include things that they are doing well. [Research has
shown](https://hbr.org/2013/03/the-ideal-praise-to-criticism) that the most
effective teams have a ratio of 6 items of affirmative feedback for every one
item of constructive feedback. [Being
intentional](https://jacobian.org/2021/may/12/praise-vs-positive-feedback/) when
giving affirmative feedback is important, it still needs to be a specific,
timely, and actionable.

Organizations that are doing well with giving feedback are going to be providing
individuals with good, structured feedback from different sources (_e.g._ direct
managers, peers, skip-level managers) on a regular basis. Organizations that are
doing poorly with this are not going to be providing individuals feedback at
all.

### Organizational Effectiveness

#### Onboarding to the Company

Onboarding effectiveness is a [key
part](https://www.shrm.org/resourcesandtools/hr-topics/talent-acquisition/pages/onboarding-key-retaining-engaging-talent.aspx)
of employee retention. With onboarding I'm thinking about how smooth the process
is for a new employee to get everything they need to get their job done, receive
their compensation, and feel like they fit in to and contribute to the team.
Examples of things that can improve this process are: ensuring there is a clear
point of contact and schedule for what they should do on their first day, making
sure their accounts for various systems are set up properly, having someone on
hand to help with registration for benefits (and a plus is using software that
makes this dead simple), and scheduling time to get to know, on a personal
level, their manager and the people they are going to be working with. Ideally
all these things are done with the first couple weeks of a new hire's start
date.

Joining a new company is big life decision for most people, they are already
going to be somewhat stressed. Anything that can be done to not add to this
stress is worthwhile. The last thing you want is a new employee regretting their
decision to join a company on the first day, that sets a tone for their
employment that can be hard to turn around.

#### Career Development

Seeing a path into the future is a powerful motivator, uncertainty is
uncomfortable at best. Making sure employees know what they need to be doing to
advance their career (get raises, promotions) helps them see the path forward at
the company and introduces a strong incentive to stay. Clearly establishing the
various responsibilities of different levels of roles at the company, and (this
is important!) communicating them to employees is key to helping define what
they should be doing to advance their career. Being consistent in the criteria
used to promote people and ensuring deserving individuals are promoted builds
trust in the system being used.

#### Team Organization

This is first criteria that is going to reference the [BAPO
model](https://janbosch.com/blog/index.php/2017/11/25/structure-eats-strategy/).
I would recommended reading up on it, as it will be referenced again. The basic
idea is that the business visions should drive the architecture used, the
architecture should drive the process, and the process should drive the
organizational structure. Many organizations get this backwards. Their business
vision is constrained by their architecture, which is a reflection of their
organizational structure (and the process is a mess).

What I'm evaluating with "Team Organization" is this the last component in the
BAPO model - organization. Are teams and departments structured and chartered in
a way that supports the process, architecture and ultimately the business
vision? Does the structure [balance autonomy and empowerment with technical
simplicity](https://martinfowler.com/articles/strong-weak-arch.html)? It is hard
to discuss organization structure without thinking about [Conway's
Law](https://en.wikipedia.org/wiki/Conway%27s_law) these days. The key to this
is being intentional about the isomorphism (graph symmetry) your organizational
structure and technical architecture are inclined to display.

Building any piece of software is a learning process in which highly specific
information is acquired by the team writing the software. It is difficult, if
not impossible, to effectively or efficiently hand-off this knowledge. Teams and
the work they do should be structured around keeping that learned information
with the software over the course of that software's lifetime. The best way to
do this is to organize teams around software products that the team builds,
maintains, and operates.

Companies that excel at team organization are going to have clear lines of
ownership between teams and departments, and enable autonomy at the right
levels. Working in companies that are doing poorly organizationally will feel
like bumbling through a maze - inter-team dependencies and duplicated projects
will be common, information transfer will be difficult due to lack clear
ownership. Team organization is something that is hard to get right and should
not be tinkered with too often, but with all the software companies in the world
there are a lot of experiments that can be learned from, use them.

#### Process

I think of process as the standards and ways people interact while getting work
done in the organization. In essence the right process should be a function of
all the people involved in the work, and the work itself. Due to this process
should be constantly evolving - it needs to adapt to changes in personnel,
responsibilities, and the type of work itself.

Process follows architecture in the [BAPO
model](https://janbosch.com/blog/index.php/2017/11/25/structure-eats-strategy/),
and as such it should be regularly evaluated as to whether it supports the
desired or best architecture. As an example of where process influences
architecture - say there are extra code reviews needed from a separate team when
changes happen to a certain area of a component. The best architecture would
involve keeping this area of the component with the rest of it, but to avoid the
extra reviews causing significant delays in code deployment the team splits the
component into two highly coupled, but separate components. This enables them to
get their work done efficiently, but the architecture has been unduly influenced
by the process used and the organization of teams.   

The [manifesto for agile software development](https://agilemanifesto.org/)
gives us a set of values and principles that can serve to guide teams and
organizations as they grow their process. It is important to differentiate
between the values and principles described in the manifesto, and ["Dark
Agile"](https://martinfowler.com/articles/agile-aus-2018.html) - "agile that's
just the name, but none of the practices and values in place." While I do
subscribe to the values from the agile manifesto and try to follow the
principles, I do think over all what is most important is ensuring the process
follows the architecture, is adapted to the type of work being done, and
supports the people involved. Agile software development practices may not be
the best thing to use for all types of work and groups of people.

Since good process is highly specific to the organization and type of work being
done, this is a tricky criteria to assess. Above all, process should support the
architecture and business vision, not be an end in itself. Generally speaking,
process should not hinder individuals getting work done in their day to day, but
should encourage collaboration and communication when necessary. It should
support the effective and efficient flow of information though the organization.
Mostly importantly, good process will involve a frequently used feedback loop
for improvement.

_Related: I've written a short essay on [guardrails vs
speedbumps](../guardrails_vs_speed_bumps/guardrails_vs_speed_bumps.md) in
process as well._

### Product

It is worth noting that a lot of my thinking on product was informed by reading
[John Cutler](https://cutle.fish/). He has written extensively and much more
authoritatively about the subjects below.

#### Vision

This is the "business" part of the [BAPO
model](https://janbosch.com/blog/index.php/2017/11/25/structure-eats-strategy/).
This is the ultimate strategic goal (or goals) of the organization. It's
important to note that vision breaks down at all levels of the of the
organization. The tactical steps in a strategy become the vision for a lower
levels of the organization ([strategy vs
tactics](https://diogomonica.com/2018/10/07/a-pirates-take-on-strategy-vs-tactics/)).
This is why we can talk about the vision for a single team, or for a department.

If you can answer yes to the following questions, I would consider the vision
for the company to be in a good place.
* Is the strategy communicated?
* Is it coherent?
* Can teams connect the work they are doing to the vision for their team, and
for the company?

#### Developer Input

The best user experiences are going to come from [product minded
engineers](https://blog.pragmaticengineer.com/the-product-minded-engineer/). Not
allowing engineers to have input into the features they are building kills any
motivation they may have for being product minded. Now that said, engineers
should not be the _only_ source of new product ideas and features, but they
should be allowed, and encouraged, to provide input on the product roadmap and
strategy.

Companies that are doing well with this are going to regularly solicit
developers for their input on the product, and listen to the feedback they
provide. Companies doing poorly here will not provide time for developers to
give product feedback, and will actively discourage them if they do provide it.

#### Measurement & Metrics

As Peter Drucker said, you cannot improve what you do not measure.

Before starting work on a product or feature define what success will look like
in a quantitative way. It is important to avoid assuming just deploying or
enabling a feature means it is done, or was successful. The new functionality
should be evaluated using the metrics defined beforehand (don't go changing the
goal posts!) to determine success. This information should be communicated back
to the development team as well so they have the opportunity to adjust their
thinking and processes in the light of the success or failure of the work they
have done previously.

Measurement and metrics of product success is probably one of the hardest things
to do well from the product perspective for an organization. It's amazing how
many organizations get caught up in the process of just shipping products and
functionality without and analysis of value generated for users by the new
software (it is easy to note these products too - they're the ones full of
feature you don't use).

### Technical

#### Architecture

The last element of the [BAPO
model](https://janbosch.com/blog/index.php/2017/11/25/structure-eats-strategy/).
Architecture is the technologies that are used, and how they are composed, to
deliver the product vision for the business. As mentioned, Conway's Law imposes
a symmetry between the structure of the organization and the technical
architecture of the system.

I think my favorite definition of architecture is given by Martin Fowler -
roughly ["architecture is the things that are both important and hard to change
later on"](https://kylecordes.com/2015/fowler-software-architecture) (Fowler
credits this definition to Ralph Johnson in a [great
article](https://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf)). From
this comes a corollary that "the best designs are those which minimize the
important things that are hard to change later on". Fowler also discusses
architecture as a social construct, which means it is something that is going to
be directly affected by the ability of the organization to effectively
communicate.

So how do you know if you have a good architecture? Unsurprisingly the answer is
similar to the answer for how you know if you have a good team structure. Clear
dependencies, "loose coupling" ([at the right
levels](https://martinfowler.com/articles/strong-weak-arch.html)), and
extensibility of components are all indicators of good architecture. Unnecessary
complexity, "spooky action at a distance", inability to accommodate changes in
requirements are all indicators of poor architecture.

#### Code and Systems Quality, Developer Experience and Productivity

I originally had code and system quality, and developer experience and
productivity as two separate things. But in working on them I've decided that I
think they are different ways of looking at the same thing.

I view code and systems quality as a separate thing from product quality, and
when I complain about the "quality" of the code or system I'm working in, what
I'm really complaining about is the experience I'm having as a developer
contributing to that code base. Most of the suggestions you see to make "quality
code" are suggestions that ostensibly make it easier to comprehend and
contribute to that code base. In other words, to improve the experience of the
developers working in that code base.

The difference between these two views lies in who/what determines quality.
Using the developer experience inherently democratizes the idea of quality.
Generally when talking just about code quality more senior engineers or
"architects" dominate the discussion. Or tools like linters and cyclomatic
complexity algorithms are used. While the opinions of experienced individuals
are important and these tools can provide useful signals, ultimately what is
most important here is the qualitative answers to the question of "As a
developer do you feel happy and productive working in this code or system?".

I'm deliberately avoiding asserting what I consider my opinions are of quality
code, even opinions I think that are held by most engineers. For instance, it is
pretty common to consider good test coverage as part of code quality. While I
would (now) generally consider a code base without of tests to be of low
quality, I recognize that there are teams (or my former self) that have built
code bases without tests and that were happy with the quality of that code and
their ability to safely contribute to it.

The only property of a system that I think is somewhat important as a measure of
quality for both codebases and systems is how quickly individuals you have hired
can be onboarded to the system, _i.e._ how long it takes them to start
contributing. This directly relates to the developer experience and
productivity. The reason I say "individuals you have hired" is note that if you
want to have a complex code base and/or system, you're going to need to hire
(and pay for) very intelligent individuals if onboarding is to happen quickly
and smoothly. If you don't want to always have to find and pay for "rockstars"
and PhDs, it is worth focusing on having a simpler code base and system that
facilitates easy onboarding.

It is worth noting that using this idea of quality, the quality of a code base
and system can change without any changes to the code itself, but with changes
to the team contributing to the code. This is why "legacy code and systems" is
often a euphemism for "poor quality". Quality is something that needs to be
actively managed, both as contributions are made and as team members are added.

#### Opportunities for Growth

This is a bit of a funny criteria to add, especially in the sense that it is
fairly subjective, but it is important to me nonetheless. I originally had this
criteria as two separate criteria, "interesting problems" and "engineering
excellence". I think the underlying principal of those initial criteria was that
the organization presents opportunities for growth to individuals within the
organization. Individuals may not capitalize on these opportunities, but I think
to be a top notch organization the opportunities must be present for those that
wish to capitalize.

One component of growth opportunities is how challenging and engaging for
engineers the types of problems they are working on are. Churning out CRUD apps
all day is going to be inherently less engaging (at least for me) than scaling
systems with hard computer science problems at their core. This is not to say
that every project or task every day should only consist of novel, hard
problems, but engineers do need opportunities to work on interesting problems so
they can grow.

It should also be noted that when not given real, challenging problems some
engineers have a tendency to invent problems. This is a source of unnecessary
complexity that contributes to bad architecture, poor developer experience, and
inability to deliver business value.

["If you’re the smartest person in the room, you are in the wrong
room."](https://www.forbes.com/sites/theyec/2022/02/10/why-you-never-want-to-be-the-smartest-person-in-the-room/)

You also want your engineers working in a organization they view as composed
of other individuals that excel at their work. Working with people that level
them up, that they can learn from. Encouraging more senior individuals to coach
more junior individuals, and building forums for senior individuals to learn
from  each other are great way to present opportunities for engineers to become
better at their craft. An organization with a lot of individuals not interested
in continuing to learn new things, or not interested in coaching and learning
from others can create a culture that stunts engineers around them.

### Compensation

I think most of these criteria are fairly subjective, so I've left out explicit
definitions of what "good" looks like.

Obviously things like high compensation and good benefits will make people more
willing to deal with issues in the above criteria. That doesn't mean you can
just throw money at people and not fix other issues.

#### Pay

Is the salary or hourly wage the individual receives fair for their level of
experience and skill?

Ultimately the determination of what is fair is between
the individual and the organization, but due information asymmetry I think it is
important for both side to act in good faith during and after negotiations. If
an employee or potential employee doesn't have a good idea of what they are
worth to the organization, the organization should not take advantage of that.
Employment represents an ongoing relationship between the employee and
organization. This is not like haggling with a vendor at a flea market. If the
organization acts in bad faith it is only a matter of time until the employee
finds out. I don't come into work everyday thinking "what's the least amount of
effort and quality I can put into my work today", employers should not apply
that same thinking to salary negotiations.

An idea I've seen recently that I think helps side step this issue, is the idea
of [transparent
pay](https://blog.bit.io/how-our-early-stage-startup-is-offering-fair-equal-and-transparent-compensation-ae582a1ad8e4)
and a calculation for determining the salary for all individuals in the company.
I consider equity grants and options as part of pay as well.

#### Benefits

Benefits are similar to pay in that the determination of what is fair is between
the individual and organization. The benefits I am referring to here are the
standard medical/dental/vision insurance and retirement savings plans. They
could be considered as part of pay, but, while being necessary for most people,
they are not likely to sway someone (or at least me) when comparing jobs.

I think it is good to evaluate the quality of benefits separate from pay since
it is very difficult to assign a dollar value to them, and employee (once again,
or at least me) end up somewhat stuck with what you get.

#### Work/Life Balance

Work/life balance often gets rolled up in to benefits, but I think it is
something to consider separately as there are other aspects of it aside from
"unlimited PTO" and "flexible work hours". The COVID-19 pandemic managed to move
working remotely from being a benefit to being a way of doing business now (one
silver lining from COVID). What I'm thinking about with work/life balance
involves the paid time off, but also things like how often do I have to work
outside my desired work hours? How easy is it to disconnect from work?

Now I have to mention having engineers "on call" here. I view on call as a
necessary evil. It vastly improves the structure of teams and positively
influences the the code and systems quality, but at best it is going to
negatively affect work/lift balance and at worst it can destroy it.  I'm not
going to give suggestions on how to handle this here (because I'd end up on a
rant) but this tradeoff should be acknowledged and monitored by managers,
product owners and technical leaders.
