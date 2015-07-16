---
layout:     post
title:      Docker and Microservices - Part 1
date:       2014-09-04
summary:    What are Microservices? A look into the value they can provide as well as the challenges and costs associated with them.
author:     Scott Martin
categories: microservices, docker
---

I recently gave a talk along with my coworker Joseph Gimenez at PeopleMatter about how Docker can help you achieve a Microservices style architecture. Joseph is on the Devops team, and I am on the Engineering team, so we were able to show the usefulness of Docker from 2 very different perspectives, which made the experience really enjoyable and enlightening.

## What's all this about Microservices?

The term itself is a fad, but the idea has been around for a while. Instead of creating your enterprise application as one big "monolithic" application, create it as a system of multiple independent services; each service focusing on doing *one* thing well. 

Don't get caught up in how big micro should be, or how you define "one thing". "One thing" is about the level of abstraction. A *function* should do one thing, as a *class* should do one thing, as a *service* should do one thing, as an *application* should do one thing, as even an *organization* should do one thing. The definition of "one thing" should only be as granular as the current level of abstraction.

> “The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms. These services are built around business capabilities and independently deployable by fully automated deployment machinery.” -- [Lewis, Fowler](http://martinfowler.com/articles/microservices.html)

## What is the VALUE?

You should never use a style of architecture simply because it's cool. You have to ask the question: "What value does this bring to my customers?". In an enterprise application, microservices can bring a lot of value to your customer. From the Fowler quote above a couple of words stick out to me: "small" and "independently deployable". Here are some benefits:

* Smaller codebases --> faster development. Monolithic applications tend to accumulate more and more cruft over time which makes developing new features take longer and longer. Smaller codebases will be easier for developers to learn what is going on. And when you are working in a small codebase, you are more likely to understand what your changes will affect.
* You can choose the right technologies for the job. Different services might benefit from using different types of data stores, or different languages. Monolithic applications lock you in to one.
* It is easier to change direction. Agile development is all about embracing the inevitable change. In a monolithic application changing direction mid-sprint or mid-release can be difficult, undoing all those check-ins is a nightmare, and dead code usually gets left behind. It is much easier to abandon or rewrite a service that does one thing.
* Development teams can work relatively independent of each other. No more twiddling your thumbs for an hour because somebody broke the build.

### Independently Deployable

This is the real value. This is what will let you get features out to customers sooner. Imagine a world where you don't have to retest module A when somebody added a feature to module B.

Since services are independent, you no longer have the expensive release overhead. Now we can get rid of the mindset that we need enough "features" in order to make the effort of releasing "worthwhile".

If you've never read "The Lean Startup", I highly recommend it. Eric Ries describes the importance of getting our ideas out to the customer as soon as possible, so that we can learn whether our hypotheses are correct. This is in stark contrast to our natural inclination to try and make something as polished as possible before we reveal it to the world; when in reality, iterating over unpolished features allows us to get immediate feedback about the customer's real needs. 

In software, this translates to *continuous delivery*. Independently deployable services that are small make continuous delivery much more attainable than a monolith, because of the significantly lower overhead.

## Not a free lunch! What is the cost?

So microservices provide some great benefits, but they come with their own set of challenges and questions to answer.

* Interprocess communication
* Decentralized data
* Synchronizing data
* Service discovery
* Logging
* Deployment pipelines
* Development environments
* Operations overhead
* Shifting organizational thinking
* ... and more

There are solutions to all of these issues. One of the first issues that you face will be the significant increase in operations overhead, and this was in fact the inspiration for this series.

> “The operations challenges of keeping Microservices up and available mean you definitely need high quality DevOps and release automation skills embedded within your development team. You simply can't throw applications built in this style over the wall to an operations team.” --[Wootton](http://highscalability.com/blog/2014/4/8/microservices-not-a-free-lunch.html)

Think about it, before these devops guys only had one or two processes to monitor, possibly distributed across multiple servers - and they were busy. Now every week you're piling more and more onto their plate. That's not very nice. So we have to put a system in place, and find tools to help us manage all this added complexity.

Fortunately, there is a tool called docker that has drastically mitigated the severity of many of those challenges. It doesn't solve every problem, but it is a gamechanger for us. Without docker, I question whether a microservices architecture would really be attainable for us.

In **Part 2** Joseph and I will explain more about what Docker is and how it helps both software and devops engineers.

