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

Countainer source: https://github.com/qoricode/activemq-artemis-docker

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

