---
title: "Quickstart Mongo Replicaset"
date: 2018-01-02T20:11:43-08:00
draft: true
---

# How to create a local mongo replicaset

The goal of this tutorial is to teach you how to create a simple mongodb replica set for development in localhost. I can't stress enough on how much of a bad idea would be to use these instructions to setup your production databases.

At the end of it, you will have three instances of mongo running on different ports. One of them is going to be your master and the other two are going to be the replicas. You can then play around with configurations and debugging techniques that are going to be handy in real life scenarios (there is a TL;DR; version at the end if you don't need to be educated on what is a replicaset and what is happening under the hood after each command).

## Warm up

Before we dig into the steps and code, let's quickly talk about replica sets and why this is an important architecture in distributed systems (specially in regards to databases):

When you are designing your database architecture, you have to think about how it is going to scale and how to make sure your data is always up (or to mitigate the risk of it becoming unaveilable). We are always playing with single instances of a database in our pet projects and school but once things get real you don't want the database to be a single point of failure in the whole ecosystem.

Our goal here is to make sure we are not overloading any particular instance by creating multiple instances of the same db. We also wanna make sure the data is consistent across the instances and that if something goes wrong our systems is going to recover beautifully in a way that  our users are not going to notice.

MongoDB has a lot flaws (I'd be happy to dedicate an entire post complaining about Mongo) but it does make replication very easy to do. We're gonna be configuring a replicaset with one master for write operations and two slaves that will split the load of the reading operations. Of course this is silly because everything will be running on localhost but again, this is just to illustrate the idea.

## The plan

* I will be using **MongoDB 3.6.2** but I'd expect these instructions to work on any 3.x version (lemme know if it doesn't)
* Our master is going to run on port 27018 and we'll have slaves on 27019 and 27020

