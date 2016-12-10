---
title:        "From zero to production"

description:  ""
image:        ""
author:       "sarbull"
---

Production is the environment where your customers acces your application. This is the place where they go in order to use your services and interact with your business.

It is important for you as a company to serve them your services in the best way possible.

In at least 95% of your business flows users need to fulfill their requirements without any interruptions or unhandled errors that may occur and are not solvable by their input.

Considering this, there are some steps that you need to follow in order to achieve this.

From my experience it is very important, at the beginning of the project, that you create or build a perfect setup for the application that you will release it for the customers.

Days of manual deployment and manual restart are gone due to human errors, but also when releasing or deploying, customers have a time where they can't use your services so this may result in a bad user experience for them.

Of course, automation in deploying applications was a must and it is now used by all companies that want their users to have the best experience in production.

Next, having these phases during you first release cycle will result a long term solution.

Create a raw architecture plan for how should components will interact with each other.

Your application must be versionable by any current tool that exists(git, svn..), this is one key setup phase that you need to adopt.

Choose your technologies that you are going to use, you can choose your technologies accordingly to your needs.

Technologies are not even relevant anymore if you adopt a microservice api architecture.

Setup up three environments: production, test, development. Doing so you will be able to develop the application, testing it with all sorts of inputs and finally delivering it a to a production environment.

Setup build agents that on every change in the project, it runs the build, unit tests and integration tests and, tells you if the project is still buildable.

These kind of build agents are the so called build validators, best of them out there are called Travis, TeamCity or Jenkins.

After creating the raw architecture, choosing the technologies, setup the hooks for the build agents, figure out what the project is going to do, always deploy the "Hello World!" into production first.

Deploying "Hello World!" into production will result in a first successful release with no issues at all. After having this T0 in your project you can now say that your application is stable and from here you can start your very own first feature of the app using this zero to production cycle.
