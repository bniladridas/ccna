---
title: LAB-13 Configure RIPv2
description: Configuration and verification of RIPv2 in R1, R2, and R3 routers.
pubDate: 2024-09-12 01:49
author: Niladri Das
tags:
  - Networking
  - RIPv2
  - Cisco
imgUrl: '../../assets/astro.jpeg'
layout: ../../layouts/BlogPost.astro
---

## Introduction to RIPv2

RIPv2 (Routing Information Protocol version 2) is a distance-vector routing protocol that is used to exchange routing information among routers. It is an improvement over RIPv1, with support for subnet masks, classless inter-domain routing (CIDR), and multicast updates.

## Theory

RIPv2 uses the following key concepts:

* **Distance-vector algorithm**: RIPv2 uses a distance-vector algorithm to calculate the best path to a destination network. Each router maintains a routing table that lists the best path to each destination network.
* **Hop count**: RIPv2 uses hop count as the metric to determine the best path. The hop count is the number of routers that a packet must pass through to reach the destination network.
* **Split horizon**: RIPv2 uses split horizon to prevent routing loops. Split horizon means that a router will not advertise a route back to the router from which it learned the route.


## Configuration RIPv1 in R1

```shell
R1(config)#router rip
R1(config-router)#version 2
R1(config-router)#no auto-summary
R1(config-router)#network 192.168.1.0
R1(config-router)#network 192.168.10.0
R1(config-router)#end
```

### R1 Verification

```shell
R1#show ip route
R1#show ip protocols
R1#show ip rip database
```

## Configuration RIPv2 in R2

```shell
R2(config)#router rip
R2(config-router)#version 2
R2(config-router)#no auto-summary
R2(config-router)#network 192.168.1.0
R2(config-router)#network 192.168.10.0
R2(config-router)#end
```

### R2 Verification

```shell
R2#show ip route
R2#show ip protocols
R2#show ip rip database
```

## Configuration RIPv2 in R3

```shell
R3(config)#router rip
R3(config-router)#version 2
R3(config-router)#no auto-summary
R3(config-router)#network 192.168.1.0
R3(config-router)#network 192.168.10.0
R3(config-router)#end
```

### R3 Verification

```shell
R3#show ip route
R3#show ip protocols
R3#show ip rip database
```