---
title: "Kafka Summit EU 2021: Encrypting Kafka messages at rest to secure applications"
date: 2020-02-22T08:06:25+06:00
hero: images/conference-talks/banner_home_left.png
description:  Learn how to configure a HashiCorp Vault server to help secure access to a RabbitMQ message queue in this talk for HashiTalks conference 2020.
theme: Toha
author:
  name: Rob Barnes
  image: /images/authors/hashiconf.jpg
menu:
  sidebar:
    name: "Kafka Summit EU 2021: Encrypting Kafka messages at rest to secure applications"
    identifier: kafka-summit-2021
    weight: 500
    parent: conference-talks
---

Whilst Kafka has the ability to encrypt data in transit, it does not have the functionality out of the box to encrypt data at rest. This places the responsibility of encryption of data placed on message queues on developers. Implementing cryptography correctly in our applications is challenging and time consuming.

In this demo-driven talk, I will show you how you can use HashiCorp Vault’s API to implement a simple workflow that offsets the complexity of cryptography to Vault. In just a few lines of code, I will demonstrate how message producers will be able to encrypt its data, whilst message consumers can decrypt message payloads with minimal development effort. I will also show how to troubleshoot common errors from the API.

By the end of this talk, you will learn how to implement symmetric and asymmetric encryption of your application data before placing it on Kafka message queues. You will also learn how to implement this workflow using Format Preserving Encryption (FPE).

[![https://videos.confluent.io/watch/Pv1d66kHKogErJ4f9wxhHr?](https://play.vidyard.com/Pv1d66kHKogErJ4f9wxhHr.jpg)](https://videos.confluent.io/watch/Pv1d66kHKogErJ4f9wxhHr?)
