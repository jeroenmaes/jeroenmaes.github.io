---
title: "Run ActiveMQ Artemis in Docker for local development"
date: "2021-12-15"
categories: 
  - "activemq"
tags: 
  - "containers"
  - "docker"
  - "activemq"
---

The Redhat AMQ Broker docker images are not publicly available for download...

While investigating some of the AMQP client connection options for .NET I had to find an alternative solution.
Luckily, Redhat AMQ Broker is basically just ActiveMQ Artemis under the hood.

After a litte search I found a valid image for my test scenario that works on Docker Desktop: https://github.com/qoricode/activemq-artemis-docker

```

#Pull image
docker pull qoricode/activemq-artemis

#Run container
docker run -it --rm -p 8161:8161 -p 61616:61616 qoricode/activemq-artemis

#Login to web portal
http://localhost:8161/console/artemis
u: artemis 
p: simetraehcapa

```
![](artemismqdocker.png)

Link to my amqpnet test console project: https://github.com/jeroenmaes/amqp-test-console