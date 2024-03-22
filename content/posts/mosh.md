---
title: "Mosh"
date: 2024-03-22T12:13:22+05:30
draft: false
---

A short guide on how to setup mosh on Lightsail or Hetzner server

<!--more-->

- Install mosh package on the server `sudo apt install mosh`
- Run `locale-gen en_US.UTF-8 && update-locale LC_ALL="en_US.UTF-8"`
- Open UDP ports 60000 - 61000 on the firewall
