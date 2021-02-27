# CI/CD from scratch

_Credit to my former manager, former dream team team-member, and friend Rory
Scott for the idea for this post, along with other ahhh... material used here._

### Introduction

Goal here is to outline my ideas on how to implement what is commonly know as
continuous integration and continuous delivery on a team that is doing none of
that. I'll write this from the perspective of a team focused on building web
based applications, though the ideas should be somewhat transferable to teams
with a different focus as well. Another assumption here is that the team is
small, and may not have buy in from management.

One thing to keep in mind is that if you approach this project as something
that is going to happen in one big bang, things probably are not going to work
out too well. Figuring out how to approach this iteratively, delivering value
every step of the way, will work out much better. One way to achieve this is
what I intend to show.

So here's the situation - you've just joined a team. Currently there's only one
other developer and their development process involves SSHing into an EC2
instance that runs _the_ instance of the application, editing the Python source
code with vim, reloading the uWSGI process, and asking the users if the change
worked. If it worked, a commit is made to master and pushed up to GitHub.

Say what you will about the process there, but lead time for changes is measured
in seconds. You may have thought you were killing it with 10 minutes.

### Stage 1
#### Separate Dev and Prod

Developers need to run the code they write, ideally without that new code
serving actual users. Our first goal here is to make sure that's possible by creating
a development environment. This will allow multiple developers to make and
safely test changes to the source code for the application, integrate
those changes in source code version control, and then release those changes
to users when they are ready.

Now some teams and organizations get hung up on having all sorts of environments
\- QA, integration, staging, etc. I think they miss the point. Just two - dev
and prod - and a commitment to as much
[parity](https://12factor.net/dev-prod-parity) as possible can get you pretty
far (this is just an opinion, and one I sometimes catch flak for, so take it
with a grain of salt). When setting up your development environment now, and
when considering future improvements, always strive to keep it as close as
possible to your production environment with regard to backing services, data in
databases, system package versions, etc. One thing I think about is making sure
these two environments look very similar, _when looking around the environment
from the perspective of my application_. For instance - from the perspective of
your application, when it's talking to the database it doesn't know or
particularly care whether that PostgreSQL database is running on an RDS
instance, as a system service on your local VM, or in a Docker container. Your
application just needs an IP address and port it can connect to. It does matter
though if the database it talks to in the development environment is SQLite, and
in production it's PostgreSQL. Or if the PostgreSQL database it talks to in the
development environment is running version 12.5 and the one in production is
running version 9.6.20. How things are run generally matters much less than what
is run when you're thinking about parity ([though that doesn't mean you can
forget about how things are run](https://www.virtualbox.org/ticket/819)).

When setting up your development environment it's also worthwhile to go ahead
and invest in automation from the beginning. I'm a big fan of tools like
[Vagrant](http://vagrantup.com) for this purpose. A big shell script is fine to
start off here, you can make it fancy using Ansible or SaltStack later. Beware
of gold plating things at this time. Ensuring your development environment is
easy to set up makes it much faster to onboard team members, switch to new
machines, and sets you up to automate the creation and tear down of downstream
environments.

I would argue against automating too much in your production environment in the
beginning. Unless people on the team already have expertise with infrastructure
as code tooling, I think the cost of learning and getting comfortable with these
tools can slow things down. Not to mention - the landscape of your production
environment may change rapidly at first as your application grows and,
hopefully, has to scale.

The last consideration at this time is setting up the **simplest** way to turn
your source code into artifacts, and to move those artifacts into production.
This can be as simple as a manual git pull of the source code on to the prod
machine and sending a signal to the web server to reload. Once again expect your
production environment to grow and change later, focus on the most simple thing
that works here. One caveat I would add here is - if your software needs to be
compiled, make sure production builds are always compiled on the same machine.
You can achieve that by have one developer responsible for deploys, by having
a VM dedicated to that, or ensuring your prod box has enough compute to serve
your application and build a new version at the same time. Inconsistencies in
your build machines could lead to tricky to diagnose bugs in production (though
what do I know - I'm a Python guy!).

#### Thinking ahead - Versioning

I think it's good to also spend a little time thinking about how you want to do
versioning. Both for your artifacts, and for the endpoints (or other external
interfaces) your application exposes.

Artifact versioning can as simple as an incrementing number and as complicated
as [Semver](http://semver.org). I've wasted a lot of time debating whether a
change counts as a "major" or "minor" version increment in Semver... For web
apps don't make this more complicated than it needs to be. I think something
like the short commit id from git can work well as a version.

Interface versioning is one of the things that can be somewhat difficult to
change later, so it's better to spend a little time here upfront. My
recommendation is to prefix URIs with a version (_e.g._ `/v1/some_resource`),
though that has its drawbacks as well. Having some sort of scheme here will make
it much easier in the future when you need to make backwards incompatible
changes.

### Stage 2
#### Add a little process when it comes to source code - Trunk Based Development

The next thing to get in place is a some process around your git workflows. Now
I'm not one that likes getting saddled with burdensome, confusing processes for
my daily workflows (individuals and interactions over processes and tools,
right?). But, some lightweight process around when git branches are used, how
you manage them, and how you implement your application -
[Trunk Based Development](https://trunkbaseddevelopment.com) - can go a long
way. I would highly recommend spending some time on the website linked there, it
provides much more detail than what I'll be able to cover in this post. I'm just going
to give you my sellers pitch for this process.

A quick overview of how this works, with trunk based development there is a
single branch called the trunk (often master in git). Development is done on
short-lived feature branches. I would say 80+% of my feature branches were
active less than two days. Feature branches are quickly integrated into the
trunk to avoid the issue of trunk and the feature branch diverging too much.
Fix any issues with trunk ASAP. Pre-integration checks before merging feature
branches is a good idea. And that's it.

_Side note: I'm personally a fan of a rebase (to get changes to trunk on my
feature branch) and squash merge (when merging to trunk, makes my feature branch
look like one commit). You can get nice clean git commit histories this way._

Why is this so great? You're achieving continuous integration with a lightweight
process and dodging the need for more complex tooling. People tend to conflate
continuous integration with automatically running tests. This isn't quite the
point (or else it'd be called continuous testing). When you look at [the
material](http://www.extremeprogramming.org/rules/integrateoften.html), the goal
of continuous integration is to avoid "merge hell" at the end of big projects.
"Merge hell" is a result of different teams/people hammering away on their own
branches for a long time, and finding out all their changes affect one another
when they eventually try to merge (integrate) all their branches. Continuous
integration advocates ensuring every change integrates with other changes
without "breaking the build". In projects using long lived branches this means
the continuous integration tooling needs to "know" how to identify these long
lived branches (and when they are no longer in use), know how to merge them all,
and then produce a build and verify that it works (AKA tests). Using trunk based
development dodges the need for these first two steps, which means continuous
integration is much easier to achieve.

The most common argument I hear against trunk base development is: "Ok sure
that works great when you have small features, but I'm doing _real_ development
and there's no way to implement the features I'm building in two days". Very
true, some (most?) features are going to need more time to be developed
properly. Trunk based development's response to this is the use of "feature
flags". These are flags in the codebase that disable the new feature's
functionality until it is ready. This means that your new feature's code is
being added to trunk right next to all the other features and bug fixes that are
being  developed. It may add a little complexity to development, but that's
because  you're paying for integration issues then and there, not deferring them
until right before you think you're done with the feature. This also encourages
you to break large features down and work iteratively on them, which can
sometimes mean getting these feature in the hands of users faster. I've heard it
said
["[long lived] feature branching is a poor man's modular architecture"](https://martinfowler.com/articles/branching-patterns.html#importance-modularity).

#### Thinking ahead - Tests

You are writing some sort of automated tests, aren't you?

Unit tests, integration (AKA contract) tests, end-to-end tests, pick something.
Make sure you're starting to develop some sort of test suite. I'm a big fan of
contract tests - tests that focus on the external interfaces of the application,
and that are not tightly coupled to the implementation of the application. This
allows your internal application architecture to change and grow while having a
test suite that ensures consumers of that API don't see changes.

#### Don't forget about delivering value to users

Once you've gotten your development environment set up and made some important
architectural decisions, take some time to make product happy and deliver some
value to your users.

You have a way for multiple developers to collaborate on building the product
and you have a way to get those changes to production, so get some changes out
there.

I'm not saying you need to stay like this forever, or even for a long time, but
don't let the pursuit of awesome developer tooling result in a lack of value
delivered to users. You might have the coolest CI/CD pipeline in the world,
but if the application it delivers doesn't do anything, what good is it?

### Stage 3

The next two things are roughly equal in priority to me, without any sort of
pressure otherwise. If you are having regression type bugs slip through into
production because tests aren't being run by developers, maybe start with
automated running of tests. If your production setup feels fragile or if
deployments have become painful, maybe prioritize updating the production
environment.

#### Automated running of tests (what most people think of as CI)

At this point it's time to implement the last step for continuous integration -
automatically verifying that every change builds and works. As discussed, most
people think this is all there is to CI and forget about the actual integration
part. With Trunk Based Development all our changes are being quickly
integrated so the goal now is to automatically verify that these changes work
after integration.

Essentially what you need here is a server, or service, that runs set of checks
(AKA a pipeline) when there are changes to your source code. I tend to run two
different CI pipelines - one on incoming pull requests from the short-lived
feature branches and another on the master branch after those pull requests are
merged. There are a lot of different systems and services out there on which to
implement CI pipelines. Jenkins has been my go-to choice for software to run
these pipelines in the past, but more so because it's the devil I know than
because I think it's the bee's knees.

The pipeline for incoming pull requests is there to verify that there are no
merge conflicts between that branch and master (which should be unlikely with a
short-lived branch), merge the branches, create a build, run the test suite, and
alert the team if there are any failures. Dev-prod parity and the automation for
setting up your development environment should prove useful when looking at how
to automate your tests. It's hard to give very much specific advice on how to
get these automated tests running. That's going to depend on your chosen CI
software, the language/frameworks in use, and your specific setup for your
tests. Needless to say, plan on spending some time tinkering with things to get
all these pieces playing nicely together.

The pipeline for the master branch can, at first, be fairly similar to the
pipeline for pull requests. It should create a build, run the test suite, and
alert the team to failures upon all new changes to the master branch. This
pipeline ensure commits directly to master are still checked, and that no
mistakes have been introduced in the process of merging a pull request.
Obviously should a (broken) commit mistakenly land on master we would want a
pipeline to catch that and report it to us. This also allows developers to
commit directly to master should they see a need to circumvent the short-lived
branch creation and pull request process (definitely a debatable need). Most
importantly this pipeline will eventually evolve to help implement Continuous
Delivery or Deployment.

#### Upgrade your production environment

The other step here is to start upgrading your production environment. Making
your production environment run off of more standardized artifacts, _e.g._ a
docker image, machine image, or whatever packaging is used by your language.
Setting up a versioned repository of these artifacts should go along with this
too. Having your system run off of images or packages like this will make it
much easier to enable scaling (both vertical and horizontal) and produced more
consistent deploys.

I would say it's also time to define your
[infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code)
using a tool such as [Terraform](https://www.terraform.io/). It is possible to
import existing infrastructure in Terraform, but setting up the new production
environment from the ground up to use an infrastructure as code tool will be
much easier.

Once again, for now, I would say it is ok to keep deploys manual. Take some time
to iron out and simplify the deployment process steps (like actually do 10+
deploys). If you automate an error prone and complex deployment process, you
just end up with an error prone and complex deployment automation script.

### Stage 4
#### Tie it all together

Now, the moment you've been waiting for, it's time to tie all all these pieces
together and implement Continuous Delivery/Deployment.

The first step here is to decide what you actually want to do. Do you want every
commit to master to be deployed (Continuous Deployment)? Or do you just want
every change ready to be deployed at the click of a button whenever product says
"ship it" (Continuous Delivery)? This is a discussion the development team needs
to have amongst themselves and with product. I will say, as a counter-point to
the most common argument against deploying all the changes, that there is [good
evidence](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339)
that more frequent deployments (_i.e._ practicing Continuous Deployment) can
lead to more stable applications.

Either way, first you can incorporate the steps for producing and uploading an
artifact to your artifact repository into your master branch CI pipeline. Now
every commit to master will result in a new artifact being created which you can
deploy. One thing to figure out here is how to handle incrementing the
version used for the artifacts. How this can be done depends on the
versioning scheme being used. While using [Semver](http://semver.org), I have
used a simple file in the repo called  `VERSION` that contains the version
number for the code, and it is the programmers responsibly to specify the new
version as part of their pull request. This works fine, though simpler
versioning schemes may be able to completely automate this.

For Continuous Deployment, just continue by adding another step to your master
branch pipeline that runs your now automated, simple, rock solid deployment
process. Now every commit to master is going straight out the door to
production.

For Continuous Delivery, choose the interface that will have your "Deploy Now"
button (your CI server/service is a good choice) and tie this button click to
your now automated, simple, rock solid deployment process. Now your latest and
greatest code is ready to go whenever product makes up their mind.

### Stage 5
#### To the moon, and beyond

If you've gotten to this point you're in a pretty good place, but that doesn't
mean you can't make it better. I'll just throw out a handful of ideas for places to go next.

- More (automated) testing - post-release tests, end-to-end tests, property
based testing, fuzzing
- Rollbacks
- Database schema migrations
- Centralized logs
- Monitoring/Observability tooling
- Canary deployments
