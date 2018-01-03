---
title: "Quickstart Mongo Replicaset"
date: 2018-01-02T20:11:43-08:00
draft: true
---

# How to create a local mongo replicaset

The goal of this tutorial is to teach you how to create a simple mongodb replica set for development in localhost. I can't stress enough on how much of a bad idea would be to use these instructions to setup your production databases.

At the end of it, you will have three instances of mongo running on different ports. One of them is going to be your master and the other two are going to be the replicas. You can then play around with configurations and debugging techniques that are going to be handy in real life scenarios (there is a TL;DR; version at the end if you don't need to be educated on what is a replicaset and what is happening under the hood after each command).
