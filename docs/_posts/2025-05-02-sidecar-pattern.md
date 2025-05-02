---
layout: post
title: Understanding Sidecar Pattern
date: 2025-05-02
categories:
  - Today I Learned
---
### May 02, 2025

- The sidecar pattern involves deploying a secondary container (sidecar) or a service alongside the main service container within the same pod.
- Applications often need extra functions like monitoring, logging, configuration, and networking. These tasks can be handled by separate components or services.
- If these tasks are built into the application, they share resources efficiently but aren't well isolated. An issue in one part can affect the whole application. They also need to be written in the same language as the main application.
- When services are split into different components, each can use different languages and technologies, offering flexibility. However, each component has its own dependencies and needs specific libraries to access shared resources. This can add complexity and latency.
- Deploying these features as separate services can make the application slower and more complex to manage, especially regarding hosting, deployment, and dependencies.

### Use Cases:

- Logging and Monitoring: Sidecars can collect logs and metrics from the main service and forward them to a central logging or monitoring system.
- Networking: Sidecars can manage network proxies, service mesh functionalities, or handle communication between services.
- Security: Sidecars can manage authentication, authorization, encryption, and other security-related tasks.

### Example / Real use case

Atlassian has a microservice which help provides details on tenant contexts, which helps other services to get the contexts and move forward with their respective operations.

Since this tenant details are crucial for most of the operations, almost all services are using this.

The TCS service itself was pretty rock solid – it was fast, reliable, and quiet. However, from time to time we had to particular internal teams complaining consistently that TCS was slow or failing. When they looked into it, we came up with the a chart, which reflects the average latency for calling TCS, as perceived from the client (this includes network time, as well as JWT token generation, which takes 1-3ms on average).

After some investigation, we found that the service in question was simplify not configured optimally to call TCS. The service have not written code to make calls to TCS in optimal way causing delays in responses etc.

Instead of fixing this problem for one team, TCS team fixed it for all consumers, by implementing sidecar for all such consumers.

![Sidecar-Pattern]({{ site.baseurl }}/assets/images/sidecar.png)

They built a sidecar service which will be deployed along side with consumer, and this side car will take care of the all the communications to be done with TCS, this sidecar services is written with all optimisations and best practices to get most out of TCS service.

Now since this sidecar services is already running locally with same service in same host, for consumer it is more of local HTTP call to sidecar which will be lot faster.

#### Why not library?

Why TCS team not went building library or package for same. The reason was simple, they had to build package library for each consumer based on their choice of language and maintaining these libraries and packages would be tough.
