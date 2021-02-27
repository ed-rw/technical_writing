- Credit to Rory for idea for post.

# Intro
Will write this from the perspective of a team building a web based application.

You've just joined a team. Currently there's only one other developer and their
development process involves SSHing into an EC2 instance that runs _the_
instance of the application, editing the Python source code with vim, reloading
the uWSGI process, and asking the users if the change worked. If it worked, a
commit is made to master and pushed up to GitHub.

- reference architecture without an end state talk

- organizing these by cost vs benefit

# 1
## Separate dev and prod

- Dev need to run the code they write, before it get served to users
- importance of parity
  - 12factor.net
  - how things are run is less important than what it run
- usually worthwhile to invest in automation from the get go here
  - much easier to remember how to get other people going, and allows them to
  start contributing faster
  - sets the stage for other environments, though they are not necessary now
- Set up easiest way possible to move code from source to artifact to running
process
  - e.g. git pull on to prod server
  - ensure compiled code is always compiled on same machine

# Thinking ahead - versioning

- go ahead and start some sort of versioning scheme for endpoints
- will make life easier in the future



# 2
## Add a little process when it comes to source code - Trunk based development

- yes - individuals and interactions over processes and tools, but
- scales well
- removes need for complex CI
- feature flags, not long lived feature branches
  - can delay implementation if product can keep features small at first

# Thinking ahead - you are writing tests aren't you?

  - write tests.

# Breather
  - Just have the devs working commit to master when they're done with tasks
  - make product happy, goal is to deliver value to users
  - wont continue to say this, but make sure focus on developer tooling isn't
  resulting in lack of value delivered to users


# 3
Next two can happen in either order

# 3.a
## Upgrade prod

- dockerize or imagify, or even just packagify your code. make artifacts and
deploy that.
- manual is fine

# 3.b
## Automated running of tests AKA CI server

- Server to watch for PRs to master, pull and run, merge, build (if necessary),
and tests and report back on failures
- just makes sure those tests are being runs. saves reviewers time from
reviewing broken code

# 4
## Tie it all together

- Whether you're gonna do continuous delivery or continuous deployment, automate
as much as you can

# 5
## To the moon and beyond

- More testing
- canary deployments
- rollbacks
- centralized logs and monitoring,
- database schema migrations
