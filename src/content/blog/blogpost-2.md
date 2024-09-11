---
title: LAB-9 Configure Multiple Interfaces and Static Routing
description: Configuration and verification of multiple interfaces and static routing in R1 and R2 routers.
pubDate: 2024-09-12 12:50
author: Niladri Das
tags:
  - Networking
  - Static Routing
  - Cisco
imgUrl: '../../assets/astro.jpeg'
layout: ../../layouts/BlogPost.astro
---

## Introduction to Static Routing

Static routing is a technique used to configure routes in a router manually. It is used to provide a specific path for packets to follow when the destination network is not present in the routing table.

## Theory

Static routing uses the following key concepts:

* **Static routes**: Static routes are used to configure routes in a router manually.
* **Route tables**: Route tables are used to store the configured routes in a router.

## Summary

Static routing is a simple technique used to provide a specific path for packets to follow when the destination network is not present in the routing table. It is commonly used in small networks where the network topology is simple.

## Configuration and Verification

## R1

### R1 Configuration

```shell
Router>enable
Router#configure terminal
Router(config)#hostname R1
R1(config)#interface fastEthernet 0/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#exit
R1(config)#interface fastEthernet 0/1
R1(config-if)#ip address 192.168.2.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#exit
R1(config)#interface serial 0/0/0
R1(config-if)#ip address 192.168.10.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#clock rate 64000
R1(config-if)#exit
```

### Configure Static Routing in R1

```shell
R1(config)#ip route 192.168.3.0 255.255.255.0 192.168.10.2
R1(config)#ip route 192.168.4.0 255.255.255.0 192.168.10.2
R1(config)#exit
```

### R1 Verification

```shell
R1#show running-config
R1#show ip route
R1#write
```

## R2

### R2 Configuration

```shell
Router>enable
Router#configure terminal
Router(config)#hostname R2
R2(config)#interface fastEthernet 0/0
R2(config-if)#ip address 192.168.3.1 255.255.255.0
R2(config-if)#no shutdown
R2(config-if)#exit
R2(config)#interface fastEthernet 0/1
R2(config-if)#ip address 192.168.4.1 255.255.255.0
R2(config-if)#no shutdown
R2(config-if)#exit
R2(config)#interface serial 0/0/0
R2(config-if)#ip address 192.168.10.2 255.255.255.0
R2(config-if)#no shutdown
R2(config-if)#exit
```

### Configure Static Routing in R2

```shell
R2(config)#ip route 192.168.1.0 255.255.255.0 192.168.10.1
R2(config)#ip route 192.168.2.0 255.255.255.0 192.168.10.1
R2(config)#exit
```

### R2 Verification

```shell
R2#show running-config
R2#show ip route
R2#write
```
