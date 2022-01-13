# [WIP] My Rubric for Evaluating Software Organizations

### Introduction

This is my attempt to put together a rubric for grading software engineering
organizations. These are criteria that I've noticed that I think are
important for organizations to get right in order to be successful. It's worth
noting that this list may be somewhat biased by my history of only being an
individual contributor (IC), and will probably evolve over time.

I've broken this into five broad categories - communication, organizational
effectiveness, product, technical, and compensation. I've tried to keep these
criteria fairly independent, wouldn't want to knock an org too many times
for one thing, but obviously some things (like communication) can have a lot of
influence on others. I was tempted to try to apply weights to some of these
criteria, but then I don't think I would have ever gotten this finished. At
this time I am trying to consider all of these items as equally important. With
this in mind, don't read too much into ordering here.

### Communication

I originally had communication as just one criteria, but it feels too
important for that. I've broken it into two pieces, information transfer and
feedback. Organizations are all about getting groups of people to work together, and
communication between people is the most fundamental need in order for that to
happen.

Communication in an organization is something that has been written about
extensively, and by people much smarter than me. This is also something not
unique to software engineering organizations, all groups of human being face
this issue. Continually asking the question of how organizations can be more
effective and efficient with their communications is one of the best things a
company or team can do to be successful.

##### Information Transfer

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

##### Feedback

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
individuals with good, structured feedback for different sources (_e.g._ direct
managers, peers, skip-level managers) on a regular basis. Organizations that are
doing poorly with this are not going to be providing individuals feedback at
all.

### Organizational Effectiveness

##### Onboarding to the Company

Onboarding effectiveness is a [key
part](https://www.shrm.org/resourcesandtools/hr-topics/talent-acquisition/pages/onboarding-key-retaining-engaging-talent.aspx)
of employee retention. I've broken onboarding into two parts here - to the
company and to the system. Here I'm merely talking about how smooth the process
is for a new employee to get everything they need to get their job done, receive
their compensation, and hopefully feel like they fit in to the team. Examples of
things that can improve this process are: ensuring there is a clear point of
contact and schedule for what they should do on their first day, making sure
their accounts for various systems are set up properly, having someone on hand
to help with registration for benefits (and a plus is using software that makes
this dead simple), and scheduling time to get to know, on a personal level,
their manager and the people they are going to be working with. Ideally all
these things are done with the first couple weeks of a new hire's start date.

Joining a new company is big life decision for most people, they are already
going to be somewhat stressed. Anything that can be done to not add to this
stress is worthwhile. The last thing you want is a new employee regretting their
decision to join a company on the first day, that sets a tone for their
employment that can be hard to turn around.

##### Career Development

Seeing a path into the future is a powerful motivator, uncertainty is
uncomfortable at best. Making sure employees know what they need to be doing to
advance their career (get raises, promotions) help them see the path forward at
the company and introduces a strong incentive to stay. Clearly establishing the
various responsibilities of different levels of roles at the company, and (this
is important!) communicating them to employees is key to helping define what
they should be doing to advance their career. Being consistent in the criteria
used to promote people and ensuring deserving individuals are promoted builds
trust in the system being used.

##### Team Organization

This is first criteria that is going to reference the [BAPO
model](https://janbosch.com/blog/index.php/2017/11/25/structure-eats-strategy/).
I would recommended reading up on it, as it will be referenced again. The basic
idea is that the business visions should influence/drive the architecture used,
the architecture should drive the process, and the process should drive the
organizational structure. Many organizations get this backwards. Their business
vision is constrained by their architecture, which is a reflection of their
organizational structure (and the process is a mess).

What I'm evaluating with "Team Organization" is this the last component in the
BAPO model - organization. Are teams and departments structured and chartered in
a way that supports the process, architecture and ultimately the business
vision? Does the structure [balance autonomy and empowerment with technical
simplicity](https://martinfowler.com/articles/strong-weak-arch.html)? It is hard
to discuss organization strucutre with out thinking about [Conway's
Law](https://en.wikipedia.org/wiki/Conway%27s_law) these days. The key to this
is being intentional about the isomorphism (symmetry) your organizational
structure and technical architecture are inclined to display.

Companies that excel at team organization are going to have clear lines of
ownership between teams and departments, and enable autonomy at the right
levels. Working in companies that are doing poorly organizationally will feel
like bumbling through a maze - inter-team dependencies and duplicated projects
will be common, information transfer will be difficult due to lack clear
ownership. Team organization is something that is hard to get right and should
not be tinkered with too often, but with all the software companies in the world
there are a lot of experiments that can be learned from, use them.

##### Process

### Product

##### Vision

< is the business vision clearly defined and coherent >

##### Developer Input

< do developer have input on what is being built >

##### Measurement & Metrics

##### Culture

<lean product thinking, agile software development values held>

### Technical

##### Architecture

##### Code and Systems Quality

##### Onboarding to the System and Code Base

##### Developer Experience and Productivity

##### "Interesting" Problems

##### Excellence

< are the individuals in the org strong engineers, "dont be the smartest guy in
the room", "A-team players want to play with other A-team players" >

##### Culture

< devops, agile software development values held, ci/cd principles >

### Compensation

##### Pay

< is the pay fair >

##### Benefits

##### Work/Life Balance
