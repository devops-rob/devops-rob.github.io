---
title: "What is the future of DevOps"
date: 2019-06-10T08:06:25+06:00
hero: images/devops/what-is-the-future-of-devops/devops-770x510.png
description: Exploring what the future could look like for the world of DevOps
theme: Toha
author:
  name: Rob Barnes
  image: /images/authors/hashiconf.jpg
menu:
  sidebar:
    name: What is the future of DevOps
    identifier: what-is-the-future-of-devops
    weight: 500
    parent: devops
---

The way business is conducted, marketing campaigns executed, and sales are concluded have all changed. Whereas the focus used to be on the product and the marketing around it, we are now in a world of experience and convenience. Consumers are now paying for experience and convenience above most things. This evolution can be seen with examples like Air bnb, the world’s largest hotel chain that doesn’t own a single hotel. Uber, the world’s largest cab firm that don’t own a single car. Just Park, a huge car park company that doesn’t own a single parking space. I build state of the art platforms using cutting edge technology to help my customers deliver these experiences to their customers. Business, sales, marketing, have all become agile business functions.

Business is the main driver behind technological innovation and technology, how we interact with it and each other is also changing. We are seeing a huge increase in data-driven applications, utilising data science models and machine learning, AI based applications and applications built on serverless architecture. Data has fast become one of the most valuable commodities to corporations.

The days of typical web application infrastructure consisting of web servers and database servers are fading away into the past and are being replaced with containerised applications and severless applications, which, in many cases, are more scalable and cost effective. The volume of data that these applications are now generating are enormous and the way this data is being used and re-modelled is evolving. This has given birth to a wave of new tech buzz words and phrases. DataOps, Big Data, AIOps to join the more established DevOps and WebOps phrases.

Such evolution begs the question, what does the future hold for so called DevOps Engineers across the world? 

To examine how our roles could evolve over the coming years, it’s important to understand what a DevOps Engineer is. I’m often asked to explain what DevOps is to me. It’s a great question because DevOps is often a very misunderstood and misused phrase. It is the type of question to which 10 people would give you 10 different answers. That tells me there is no definitive correct answer to the question, but rather a general consensus to the key attributes.

With that said, to me, DevOps is bridging the gap between development and Operations teams promoting collaboration between the teams throughout the design, development, testing and deployment stages of the software release cycle. It requires developers to have infrastructure in their considerations when developing applications and features and on the flip side, Operations engineers to have Developers and their code at the forefront of their infrastructure design considerations, thus, increasing productivity and speeding up the software delivery cycle with improved quality. 

Often, I see jobs specs which imply that DevOps is Docker, Terraform, AWS, Azure, Jenkins etc, which couldn’t be further from the truth. These are merely tools and services that help in implementing the benefits of a DevOps culture. Two of the tools that don’t get as much mentions in such implications are Slack and Git which are at the heart of what it is to be DevOps. These tools enable collaboration between teams immensely. The tools don’t define DevOps, they enable and enhance it.

In short, DevOps isn’t something you do. DevOps is something you are! 

So, with this context, let’s now examine what serverless is. Serverless applications rely on third party services to provide the backend of the application, often referred to as Backend as a Service (BaaS). An example of this is the DynamoDB offering by AWS which provides applications with their required databases without needing to manage the infrastructure. This significantly reduces the support overhead and as there is no “always on” server hosting the database, the cost of such a service can be much more efficient.

The term serverless, however; can be slightly misleading, as it implies that there are no servers, which isn’t the case. The servers are simply not the responsibility of the Operations Engineers but instead, are the responsibility of the service providers.

From a Data science perspective, we now have cloud solutions like AWS Kinesis which streams large volumes of data in a very timely manner as well as AWS EMR (Elastic Map Reduce) which supports Apache Spark and Hadoop and is great at undertaking the machine learning element of data processing.

We must also consider the future of containerised applications. Containers have been around for a while, but over the last few years, has become much more widely adopted. The need to have a Docker host is now being replaced with container services like Amazon ECS (Elastic Container Service) and Azure Container Service. 

With significantly less server infrastructure to manage (virtual/cloud-based/physical), does this make the role of a DevOps Engineer redundant in the distant or near future? Where does the DevOps Engineer as we know it today, fit into this new direction? Do we have to grow into Software Engineers?

These are all great questions to which we can’t possibly have any definitive answers, but we can speculate and develop predictions.

I believe the Operations role will still be required in an evolved way. Developers need to be developers and focused on building profitable features and robust bug fixes.  Data Scientists will need to focus on building useful data models. Operations engineers will still need to decide what infrastructure approach is the best for each solution, be it a Containerised application or a serverless one. We will also need to choose the right Serverless functions for the application, from SQL and NoSQL database back ends to api Gateways and authentication providers for optimal application performance. Operations Engineers will need to ensure there is enough compute processing power to process the huge amounts of data being streamed and trained for machine learning.  We may even have to work more closely with developers to help optimise their code in order to work better and more efficiently with these third-party functions. Effective development/testing/deployment pipelines will still need to be built and managed

In the future, operations engineers may need to evolve to become more code aware to understand the infrastructure requirements of applications and data pipelines. DataOps, AIOps still serves the same purpose as DevOps and promote the same collaboration and philosophy between developers/data scientists and operations teams. 

In short, Ops is going nowhere and is growing and coming of age. We must evolve with the technology as ever, becoming even more agile and expand our skill set to bring about a more cohesive union between our developer’s code and the serverless functions we choose to use.

Change, when embraced is a great thing and here, I see no exception to that statement. Such change will only increase the close relationship between operations and development teams and promote even more collaboration, which after all, is what DevOps is about.
