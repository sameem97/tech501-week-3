# Why CI/CD?

- Make devs and IT life easier, less work for them.
- Quickly get changes to end users e.g. new features, bux fixes - just click of a button. So more business value, users use the latest code more quickly.
- Reduce risk of big changes breaking codebase. Small changes with consistent build, test and deployment. Less room for human error.

INSERT DIAGRAM FOR CI/CD

## Continuous Integration

- Branching strategy: Feature branch -> Dev branch -> Main branch
- For code changes in feature branch, automate the build and testing with CI. If successful, merge with the dev or main branch.
- CI triggered often by a push to the feature branch.
- Webhook to CI server e.g. Jenkins, tells the server that a change has been made to the codebase and need to run the CI related jobs.
- In our case, we won't be building a containerised application or an custom azure image, we will be simply testing our new application code, and if it passes then merging it with the main branch.

## Continuous Deployment

- Post successful CI job, CD will run to deploy the code out to the production server.
- In our case, will be a VM. But a lot of other places the product of the CI stage will be a Docker container and the production environment will be a kubernetes cluster with several VM worker machines.
- When collaborating with several developers each working in their own feature branch, need to make sure our changes are always on the latest version of the codebase. And post testing, it is exactly that which gets deployed to prod.
- Once code reaches prod, features or updates available for end-users to use.

## Why Jenkins for CI/CD?

- automation server, commonly used for CICD
- free
- powerful plugins e.g. for certain testing
- great to understand CI/CD

## Get started

1. Allocate to Jenkins server 2 running on AWS EC2 instance.
2. Use: <jenkins_server_ip>:8080 for access: `http://52.31.15.176:8080/`
3. login with username and password.

On jenkins server:

- `New item` creates a new project. This is more akin to a "job".
- Jobs can be comprised of multiple steps e.g. run a bash script (see build steps).
- Can link multiple jobs together via "post build actions" i.e. run the next job.
