## Intro

- Sharing a simple model I have used to quickly gain an understanding of how
deployments (source code -> running process) work for a system.
- First formalized while serving on a committee to investigate CI/CD for dept.
- Also found it useful when discussing deployments with friends.
- Not sure where I picked this up, if it's fairly common knowledge or if people
will find it useful.

## The Model

- Three components
  - Source code
  - Artifacts/"Something Deployable" (sometimes optional)
  - Running process

## Source Code

## Artifacts/"Something Deployable"

## Running Process

## Examples

- Editing Python code directly running on server
  - most people's dev env?
- Writing code (locally), push to github, pull to server, restart process
- Writing code, push to github, ci builds docker container and saves in ECR, cd
runs container in ECS cluster

- How does this model fit to your process?

## How this relates to CI/CD
