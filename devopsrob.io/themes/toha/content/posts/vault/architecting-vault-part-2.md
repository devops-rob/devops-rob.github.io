---
title: "Architecting Vault - Part 2"
date: 2019-07-21T08:06:25+06:00
hero: images/vault/part2-hero.png
description: Part 2 in a blog series exploring architectural the design decisions of a Vault architect
theme: Toha
author:
  name: Rob Barnes
  image: /images/authors/hashiconf.jpg
menu:
  sidebar:
    name: Architecting Vault - Part 2
    identifier: architecting-vault-part-2
    weight: 500
    parent: vault
---

In the previous blog post, i discussed hosting options for Hashicorp Vault and things to consider when making decisions about the platform to deploy your production Vault Cluster on to. This post will focus on the next architectural decision that you need to make when designing your vault cluster.

### Which backend do i want to use for my Vault Cluster?

Firstly, let’s define what a backend is in the context of Vault and what capabilities a backend can enable for our cluster. Backend in the world of Vault is actually a storage backend which holds all of Vault’s information. Vault supports many different storage backends, 19 to be precise, each of which have their pro’s and cons. Let’s look at some of the main backend options in more detail.

### Consul
ß
Consul is another offering from Hashicorp which provides a Key/Value store amongst other services which are beyond the scope of this article. As this backend is also made by Hashicorp, it functions seamlessly as a backend for vault and provides High Availability clustering possibilities. As this offering is not specific to any one particular cloud vendor, it makes it a good option for organisations who want to avoid vendor lock-in as part of their cloud strategy.

### Azure

Organisations that are heavily invested in Azure cloud may wish to use azure storage containers as a backend for their vault instances. Azure storage blobs provide a cheap storage option which is useful for organisations with budget constraints. Whilst this may be an attractive option for these organisations, there are some limitations that need to be taken into consideration.

Firstly, this backend does not have High Availability support, which I imagine would be unacceptable for many organisations; however, this will depend on how you plan on using Vault. If uptime is not a concern for your organisation then this may not be a deal breaker for you.

The next thing to note about this back end option is the storage limitation it has for Vault’s information. As of the time of writing this, Azure storage containers can only support a maximum of 4MB of data per blob.

It’s also worth pointing out that this backend is supported by the Hashicorp Azure community. In general, the community support is really good; however, some organisations may deem that to be an unacceptable risk for their Secrets Management Platform.

### S3

Similarly to the Azure storage backend, organisations that are heavily invested in AWS may also find this to be an attractive option, especially as S3 provides cheap storage. S3 also lacks High Availability support and is also community supported.

### DynamoDB

Organisations using AWS also have the option of using DynamoDB as a storage backend for Vault. DynamoDB is a NoSQL document database which makes it suitable as a Key/Value store for Vault.

Unlike the S3 option, DynamoDB does offer support for High Availability clustering but this is a more expensive option than S3 storage.

### Etcd

This is a simple Key/Value store which is also used in Kubernetes to store cluster state data. Etcd provides High Availability capabilities to Vault. This backend is also community supported and is very easy to setup.

### Filesystem

This backend uses the directory structure of the local file system to store data for vault. For obvious reasons, this backend does not provide High Availability functionality. Filesystem is an official backend for Vault and as such, is supported by Hashicorp. In general, this option is not the most suitable of options for production Vault deployments that require zero downtime.

Access to the file system where the Vault data persists requires close attention to avoid unauthorised access to the information held there.

### Google Cloud Storage

GCS is one of the storage offerings from GCP. Just like Azure blob storage and AWS S3 storage buckets, this offers cheap and flexible storage. Organisations that are heavily invested in GCP will find this to be an attractive option. This backend can also be configured for High Availability which is a plus for these organisations. This storage backend is also community supported.

### In-Memory

In memory is a storage backend that persists the Vault data entirely in the memory of the local machine. Not only is this not a good option for production, it’s not an option at all. In-memory is useful for spinning up local test instances, which is what the Vault server uses when started up in dev mode using the -dev flag. When the platform hosting Vault is restarted, all the data that was previously persisted in memory is lost.

There are many other backend options which include various SQL offerings, both cloud native and traditional SQL databases like MySQL, PostgreSQL and MSSQL. Some of these options do offer High Availability options. Further reading of the official Vault documentation is recommended.

When considering which backend to use for Vault, there are some questions that need answering to find the most suitable solution.

### Is the organisation heavily invested in a particular Cloud Vendor?

Some organisations, like Microsoft Gold Partners, are likely already invested heavily in a particular cloud vendor, in this case, Azure. This is more than an investment, this is a technological partnership between the organisation and Microsoft.

Similarly, many organisations are also partnered with Google, Amazon and Alicloud. The existence of such partnerships strongly suggest that the chances of these organisations moving to a different cloud vendor are minimal to non-existent in the long term technology roadmap. The point here is that as an architect, we do not need to take vendor lock-in concerns into consideration when making this design decision for the organisation.

These organisations will likely already have the skill set required to set up and manage the cloud vendor specific storage backend, which lessens the support overhead of the backend. This could be an important factor in whatever decision is made.

### How will the organisation use the Vault deployment?

Organisations have different use cases for deploying Vault, for example, some will use it to serve secrets to applications and services which need to be accessible at all times. Other organisations may be using it as a storage tool for secrets. There are of course many other use cases but for the purposes of this blog, the two mentioned will suffice.

The answer to this question will more than likely dictate the answer to the next two questions.

### How important is High Availability to the organisation?

In the first example above, those that wish to use it to serve applications and services with secrets will more than likely value High Availability over most things. In this example, applications and services cannot perform their functions if Vault is unavailable for a period of time. In this scenario, you almost certainly choose an option which provides High Availability like Consul or maybe Google Cloud Storage if you’re heavily invested in Google Cloud Platform.

### Backup and restore process

To some organisations, the data being stored in vault is of the upmost importance and as such will value the ease of backup and restore process above most other factors. Does the organisation already possess the skillsets to easily implement backup and restore processes for a particular storage backend option? This is something that will also need to be taken into consideration.

### Summary

As you can see from the above discussion, choosing the correct storage backend for each individual use-case requires a lot of thought and consideration. In order to make the right decision, you will need to understand the organisation as it is today, where the organisation is heading and the relevant skill sets they already possess. You will also need to understand the areas where they will need to up-skill, how much support overhead each option will cost them and if this cost is acceptable.

Understanding the future ambitions of the organisation will aid in producing a future proofed design with the appropriate backend. The above is by no means an exhaustive list of questions; however, it provides a good base to start the right conversations to extract the information needed to produce the best possible design for the organisation.