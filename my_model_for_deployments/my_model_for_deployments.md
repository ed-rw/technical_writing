# My Model for Understanding Deployments

### Introduction

Thought it would be nice to explain and share a simple model I use to
understand how source code becomes a running process (a "deployment") in a system.

I believe I developed this understanding while building continuous
deployment tooling for the team I was on in 2016 and discovered its usefulness
while serving on a department committee investigating how to spread CI/CD
practices and tooling to other teams. I've also found the model useful in
discussions with friends about how their deployments work as well.

Not sure if I picked this up reading somewhere or if I came to it on my own.
This may seem like common knowledge to some, or maybe it will be insightful. At
the very least writing will let me harp on a subject I enjoy for a little while.

### The Model

The way I see it there are three major components that are involved in any deployment:
- Source code
- Artifacts ("Something that is Deployable")
- A running process or processes on a machine

Deciding what plays the role of each of these components in a particular system
makes it much easier to frame an understanding of how deployments occur for
that system. It should be noted that sometimes the source code and artifacts
components may be the same "thing".

### Source Code

The source code is fairly self explanatory, it is the code that you or other
developers are writing. Hopefully to make the world a better place. It may be
Python or C or something else, but generally it's going to be saved as files on
a machine somewhere. Most developers and teams these days will be using some
sort of version control system (_e.g._ git) and having a central location that
can be used to share that code between machines and, by extension, other people.
Though I do remember the days when I was just starting to code and just had a
set of files saved in a folder that I occasionally backed up to an external
drive. That works too.

The key here is to understand what set of files represent the code that should
be running, and how to access them. Are the files stored on GitHub? Or GitLab?
Or just FTP'd to a server managed by the team? What branch of git represents
the code that should be running? Is it the latest commit on that branch or is a
tag applied to the specific commit that contains the desired source code? What
credentials are necessary to access the source code? How can these files be
downloaded?

Nailing down exactly where and how to access the files that contain the source
code is an important step in determining how that code is going to become a
running process. It's incredibly hard to navigate if you don't know where you're
starting from, and where the right set of files is located is essentially your
starting point.

### Artifacts ("Something that is Deployable")

The next thing to get a handle on is what is it that is actually run by the
system, how is that created, and where is it stored. I use the word artifact
here, as this is usually the artifact of some build process, but it is really
that which is deployed (I've debated avoiding using "artifact" and just using
"deployable", but that seems a bit vague).

Are you just running some Python code? Your artifact may just be the set of
source code files in the latest commit on the master branch (_i.e._ the source
code previously identified). The artifact may be the binary that is compiled or
a container image that is built. The goal is to determine what it is that is
going to be run and what, if any, are the steps taken produce it.

The artifact that is produced will most likely be stored in a repository
somewhere, and ideally versioned. Continuing the example from above with Python
files, you could consider GitHub the repository and the specific commit id the
version. Or maybe ECR or Dockerhub is your repository for the container image
and tags are used for versioning.

I like the think of the artifacts as a check point between source code and
running code. Going from source code to a running process can seem like a long
way, but having a well defined stop in the middle makes the journey seem not
quite as long. What artifacts are and how they are managed can give you a lot
of information on what the next stage is going to look like, what will need to
happen to getting that artifact running correctly, and how or if you'll be able
to perform various operational strategies (_e.g._ rollbacks, canary
deployments).

### A running process or processes on a machine

The ultimate goal of most code that is written is that it is run by a machine,
somewhere. This code is going to be executed by a CPU, GPU, etc. within the
context of a process or group of processes. The last step in a deployment
is creating or updating the process(es) that run the artifact.

Knowing where these processes are running and what system requirements
they have is very useful in understanding this component of the deployment. I've
always enjoyed having the ability to get on the machine running my code and to
watch the running process in `top`, or to look at the ports that is has open and
inspect the network traffic with WireShark. I think that gives you a good
understanding of how your code is acting in and interacting with the environment
in which it's run. While this isn't always possible, either due to
security/operational constraints or just being abstracted away from that level
(_e.g._ serverless/AWS Lambda), it is not an excuse for not taking the time to
think about where and what will be running your code.

When trying to understand this component I'm often thinking about or asking
questions such as: What OS is running this process? What are the system
requirements of my process (_e.g._ dependencies, services, firewall rules)? How
will the artifact be moved on to the machine? How will the artifact become a
running process or group of processes? Should and how can the process be
restarted if it crashes? How can it be safely stopped?

I think it's very important for the person writing code to keep these sorts of
things in mind and to know the answers to these questions. It can be easy to get
caught up in the beauty and details of source code, but remember that ultimately
(hopefully) code is going to be a process running somewhere and that process is
how code fulfills its purpose.

### Examples

I'm going to go over a few scenarios and apply the model to them.

First, let's consider the situation that you're editing some Python files
on the machine that is running the Python interpreter and executing those files.
Now hopefully you're not doing this in production, but I think this is a common
situation for development environments. In this scenario your source code is
this set of Python files, your artifacts are the Python files as well (maybe
versioned through a series of small commits on your feature branch), and your
running process is the Python interpreter, which running on your laptop. The
steps for a "deploy" are to save your code, maybe make a small commit, and then
to run or restart the Python interpreter.

The second scenario is that maybe you're writing code on your machine (using a
process like above to run/test it) and to move it to production you make a
commit to master, push that to GitHub, SSH into your production server, do a
`git pull` to pull that latest code onto the server, and then send a SIGHUP to
your uWSGI master process to gracefully reload your application. Your source
code is once again the set of Python files, but in this situation the "official"
source code is stored on GitHub. Your artifact repository is GitHub and the
versioning is done through commits. To get the code you just wrote on your
server you're using git to download the latest files and then instructing uWSGI
to gracefully restart the group of processes running your application code to
run the latest and greatest.

This last scenario is an example of a more "modern" process. Similar to the
second scenario you write your code on your machine, and push it to GitHub on a
short-lived feature branch when you're done. After a teammate reviews your code
you squash merge it on to the master branch. A CI/CD system sees the new commit,
pulls the code to a server, runs the tests (which pass, yay!), builds a new
Docker container image, pushes it to ECR, and then runs Terraform code to create
new task definitions and updates your ECS service to use the new task definition.
ECS then handles shutting down old containers on your ECS container instances,
and pulling and then running the new container image. There's a lot going on
there, but once again your source code is stored on GitHub, with the master
branch representing what should be running. Here though your artifact is the
Docker container image and the artifact repository is ECR. Your running
processes are the processes within the cgroup that corresponds to the container
run by ECS on your container instances. ECS and Docker are handling shutting
down the old processes and running the new ones for you to complete the
deployment.

### How this relates to continuous integration and Continuous Delivery

I view continuous integration as primarily concerned with ensuring the
correctness of source code, and that different branches being worked on don't
cause issues when integrated. Continuous Delivery is concerned with automating
this process of transforming source code into artifacts and allowing
the deployment of an artifact to occur with the click of a button by automating
the process that turns artifacts into running processes. Continuous Deployment
just removes the button click and deploys every new production ready change to
the source code.

### Conclusion

Structuring how you think about deployments can make it easier to focus in the
important information when you're trying to design or understand a system that
uses CI/CD tooling. Even when you're not using tooling like that, keeping these
components in mind can help you think more fluidly about what you're doing while
turning your shiny new code into processes that provide value.
