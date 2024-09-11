---
title: LAB-12 Configure RIPv1
description: Configuration and verification of RIPv1 in R1, R2, and R3 routers.
pubDate: 2024-09-12 01:30
author: Niladri Das
tags:
  - Networking
  - RIPv1
  - Cisco
imgUrl: '../../assets/astro.jpeg'
layout: ../../layouts/BlogPost.astro
---

## Introduction to RIPv1

RIPv1 (Routing Information Protocol version 1) is a distance-vector routing protocol that is used to exchange routing information among routers. It is a simple protocol that uses hop count as the metric to determine the best path.

## Theory

RIPv1 uses the following key concepts:

* **Distance-vector algorithm**: RIPv1 uses a distance-vector algorithm to calculate the best path to a destination network. Each router maintains a routing table that lists the best path to each destination network.
* **Hop count**: RIPv1 uses hop count as the metric to determine the best path. The hop count is the number of routers that a packet must pass through to reach the destination network.

## Summary

RIPv1 is a simple protocol that does not support subnet masks, classless inter-domain routing (CIDR), or multicast updates. It is an older protocol that has been largely replaced by RIPv2.

## Configuration and Verification

### RIPv1 configuration in R1:

```shell
R1(config)#router rip
R1(config-router)#network 192.168.1.0
R1(config-router)#network 192.168.2.0
R1(config-router)#network 192.168.12.0
R1(config-router)#network 192.168.13.0
R1(config-router)#end
```

### R1 Verification

```shell
R1#show ip route
R1#show ip protocols
R1#show ip rip database
```

### RIPv1 configuration in R2:

```shell
R2(config)#router rip
R2(config-router)#network 192.168.3.0
R2(config-router)#network 192.168.4.0
R2(config-router)#network 192.168.12.0
R2(config-router)#network 192.168.23.0
R2(config-router)#end
```

### R2 Verification

```shell
R2#show ip route
R2#show ip protocols
R2#show ip rip database
```

### RIPv1 configuration in R3:

```shell
R3(config)#router rip
R3(config-router)#network 192.168.5.0
R3(config-router)#network 192.168.6.0
R3(config-router)#network 192.168.13.0
R3(config-router)#network 192.168.23.0
R3(config-router)#end
```

### R3 Verification

```shell
R3#show ip route
R3#show ip protocols
R3#show ip rip database
```