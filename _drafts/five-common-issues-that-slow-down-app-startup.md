---
layout: post
title:  "Five Common Issues That Slow Down Apps"
author: junfeng/sarvar
comments: true
visible: true
---

Analyzed top 7,500 apps
Excluded games (heavy native)

Five common issues

- getResourceAsStream
  what it is
  percentage of app affected
  amount of delay
  why is that? Android does extra stuff
  fix

- load large JSON resources
  what it is
  percentage of app affected
  amount of delay
  why is that? parsing is CPU intensive
  fix

- dynamic dependency injection
  what it is
  percentage of app affected
  amount of delay
  why is that? CPU intensive
  fix

- reflection
  what it is
  percentage of app affected
  amount of delay
  why is that? Android limitation
  fix

- SDKs that have one of the above issues
  what it is
  percentage of app affected
  amount of delay
  why is that?
  fix

Summary Table
Issue       Apps affected    Startup delay      Potential fix
