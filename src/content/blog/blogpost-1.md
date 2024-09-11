---
title: LAB-8 Configure Security Features and DHCP
description: Configuration and verification of security features and DHCP in R1 router.
pubDate: 2024-09-12 12:30
author: Niladri Das
tags:
  - Networking
  - Security
  - DHCP
  - Cisco
imgUrl: '../../assets/astro.jpeg'
layout: ../../layouts/BlogPost.astro
---

## Introduction to Security Features and DHCP

Security features and DHCP are essential components of a network infrastructure. Security features provide authentication and authorization mechanisms to secure access to the network, while DHCP provides dynamic IP address allocation to devices on the network.

## Theory

Security features use the following key concepts:

* **Local login**: Local login provides authentication and authorization mechanisms to secure access to the network.
* **SSH server**: SSH server provides secure remote access to the network.
* **DHCP**: DHCP provides dynamic IP address allocation to devices on the network.

## Summary

This lab demonstrates the configuration and verification of security features and DHCP in R1 router. The security features include local login, SSH server, and SDM, while DHCP provides dynamic IP address allocation to devices on the network.

## Configuration and Verification

## R1

### R1 Configuration

```shell
Router>enable
Router#configure terminal
Router(config)#hostname R1
R1(config)#username anatto password google@123
R1(config)#line console 0
R1(config-line)#login local
R1(config-line)#exit
R1(config)#line vty 0 15
R1(config-line)#login local
R1(config-line)#exit
```

### R1 Verification

```shell
R1# show running-config | include username
R1# show running-config | section line vty
```

### Verify Local Login

### Console Login

```shell
Router> enable
Password: <enter password>
```

### VTY Login

```shell
ssh -l anatto <router-ip-address>
```

### Configure SSH Server

```shell
R1(config)#line vty 0 15
R1(config-line)#login local
R1(config-line)#privilege level 15
R1(config-line)#transport input ssh
R1(config-line)#exit
R1(config)#username anatto privilege 15 password google@123
R1(config)#ip domain-name google.com
R1(config)#crypto key generate rsa
```

### Verify SSH Server

### Check SSH Configuration

```shell
R1# show ip ssh
```

### SSH Login

```shell
ssh -l anatto <router-ip-address>
```

### Access From Host

```shell
Start -> Run -> CMD
ssh –l admin 192.168.1.254
```

### Configure DHCP

```shell
R1(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.50
R1(config)#ip dhcp pool lan1
R1(dhcp-config)#network 192.168.1.0 255.255.255.0
R1(dhcp-config)#default-router 192.168.1.1
R1(dhcp-config)#dns-server 8.8.8.8
```

### Verify DHCP

```shell
R1# show ip dhcp pool
```

### Check DHCP Pool

```shell
R1# show ip dhcp pool
```

### Check DHCP Bindings

```shell
R1# show ip dhcp binding
```

### Configure SDM

```shell
R1(config)#line vty 0 15
R1(config-line)#login local
R1(config-line)#privilege level 15
R1(config-line)#transport input ssh
R1(config-line)#exit
R1(config)#username anatto privilege 15 password google@123
R1(config)#ip domain-name google.com
R1(config)#crypto key generate rsa
R1(config)#ip http server
R1(config)#ip http authentication local
R1(config)#ip http secure-server
```

### Verify SDM

### Check HTTP Server

```shell
R1# show ip http server status
```

### Access SDM

```shell
https://<router-ip-address>
```