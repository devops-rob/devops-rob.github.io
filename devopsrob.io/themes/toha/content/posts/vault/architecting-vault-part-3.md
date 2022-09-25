---
title: "Architecting Vault - Part 3"
date: 2019-07-29T08:06:25+06:00
hero: images/vault/part3-hero.jpeg
description: Part 3 in a blog series exploring architectural the design decisions of a Vault architect
theme: Toha
author:
  name: Rob Barnes
  image: /images/authors/hashiconf.jpg
menu:
  sidebar:
    name: Architecting Vault - Part 3
    identifier: architecting-vault-part-3
    weight: 500
    parent: vault
---

So far in this blog series, we have covered hosting options for Vault deployments and also explored the different options available for Storage backends and some of the considerations needed when making your design decision.

This post will look at the auth methods that are available for you to enable in your Vault deployment and how to make the right decision as to which option to choose for your use case.

### What is an Auth Method?

As a secrets management platform, Vault holds sensitive information to which access needs to be carefully managed and controlled. In order to understand how Vault can achieve this, there are two concepts which I will briefly discuss which are authentication and authorisation.

### Authentication

Authentication is the process of assigning an identity to a user, much like what happens when you sign into most modern day applications. It will ask you for a username, which is you telling the application who you are. Next it will ask for a password which is a method of proving that you are who you say you are. Some applications may have an extra layer of security such as multi-factor authentication. Once you have signed in, the application will assign you your identity in the context of the application.

### Authorisation

Authorisation is the process of managing what resources, files and data that each identity should and shouldn’t have access to. There is a dependancy on authentication to enable authorisation to work effectively. Authentication and authorisation are two halves that make up the same coin to deliver the coin’s value, access control.

With this context now set out, let’s go back and address the original question, what is an auth method? From Vault’s perspective, an auth method is a way of assigning an identity to a user accessing Vault (authentication).

### Which auth method do I choose?

Vault provides several different ways to do authentication, some of which are more suitable to some organisations than others. Below is a list of some of the commonly used auth methods available to us to use in our Vault deployment design.

1. GitHub
2. Okta
3. LDAP
4. Username and password
5. AWS
6. Azure
7. GCP

Which auth method you choose will depend on what you use to manage identities for other platforms and applications. For example, I think it’s fair to say that majority of enterprise size organisations would use something like Active Directory to manage user accounts in the organisation. In this example, a lot of time and effort would have already been placed into the design of the directory structure, organisational units and groups. You can all but guarantee that the directory contains user accounts for the entire organisation and security groups have been set up according to the business structure and business logic. In this case, it make the most sense to use the LDAP auth method as most of the structural work is already done for us.

I want to point out that Vault allows you to enable multiple auth methods in your deployment so that gives you flexibility when choosing which auth methods to enable.

To demonstrate this, I’ll use a different example use case which is a small tech startup with 1–20 users. These organisations typically would not have an Active Directory in place as it’s more than likely not cost effective for the number of users they have. They do use GitHub to store and manage their source code, which means most of the organisation’s developers would have GitHub accounts which are linked to the organisation’s GitHub account. The organisation may also have a Marketing Director and a Finance & HR Director who both don’t have GitHub accounts for understandable reasons. In this case, it makes the most sense to enable both the GitHub auth method and the username & password auth method.

### Application identities

For the most part, the methods listed above are geared towards assigning users an identity for vault, but what about assigning identities to applications? Vault offers some auth methods which are better suited this, as listed below:

1. AppRole
2. JWT / OIDC
3. TLS
4. Kubernetes

Depending on the nature of your application, these options should provide effective ways of it authenticating. If your application is made up of micro-services which are orchestrated using Kubernetes, then this will also be a sensible choice of auth method.

Approle is in my opinion, the most flexible of the above listed auth methods for applications as it allows for multiple differing workflows, which makes it suitable for almost all applications and services, no matter how different they are. You should bare in mind that this level of flexibility can easily inject added complexities into your design if you don’t design the workflows with the wholistic view in mind.

### Summary

When choosing which auth methods to enable, you need to understand some of the following things in order to produce a suitable design:

Who will need to log in to Vault and why?
How is the organisation currently managing identity and user accounts?
What platforms are existing services and applications being hosted on?
How are existing applications currently handling authentication?
What are the future plans on the roadmap for existing applications and services as well as new ones?
The answers to these questions will guide you into choosing the right combination of auth methods. Auth methods can be enabled and disabled at any time so you can evolve your Vault platform as your roadmap moves along. Another thing to consider is if the organisation has or is moving towards a Single Sign On (SSO). If there is already SSO in place or plans to implement it, your choice of auth method should reflect this.

It’s also worth noting that you may need to re-architect parts of your existing applications to work with some of these auth methods so you will also need to ascertain how much technical debt it will incur and if this debt is acceptable.