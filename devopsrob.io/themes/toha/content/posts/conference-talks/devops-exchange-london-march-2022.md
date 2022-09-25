---
title: "DevOps Exchange London March 2022"
date: 2022-03-25T08:06:25+06:00
hero: images/conference-talks/dox.jpeg
description:  In this talk, I’m going to show you a simple workflow that removes Secret Zero from application code and uses Cloud native identities to authenticate to HashiCorp Vault.
theme: Toha
author:
  name: Rob Barnes
  image: /images/authors/hashiconf.jpg
menu:
  sidebar:
    name: "DevOps Exchange London March 2022"
    identifier: devops-exchange-london-march-2022
    weight: 500
    parent: conference-talks
---

Centralising your secrets management platform and Identity Provider is an essential part of adopting a Zero Trust mindset, but one of the biggest challenges facing DevSecOps Engineers and Developers in this new paradigm is how systems and applications can get that initial secret that grants access to the secrets management platform. This is commonly referred to as `Secret Zero` and can’t be stored in plaintext in the application code due to the high risk of exposure.

In this talk, I’m going to show you a simple workflow that removes Secret Zero from application code and uses Cloud native identities to authenticate to HashiCorp Vault. I will demonstrate how to attach Cloud identity to a workload and configure HashiCorp Vault’s auth methods to use this identity for Authentication. By the end of this demo, you will understand how to configure the cloud components, Vault and how to refactor a simple Go application to facilitate this workflow.

[![https://www.youtube.com/watch?v=Jouts5NTorU](https://img.youtube.com/vi/Jouts5NTorU/0.jpg)](https://www.youtube.com/watch?v=Jouts5NTorU)
