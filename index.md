---
title: TAP Documentation
keywords: Trusted Analytics Platform
tags:
  - Overview
sidebar: mydoc_sidebar
permalink: index.html
summary: >-
  Welcome to the Trusted Analytics Platform version 0.8 technical documentation.
  For simpler instructions on how to use TAP please visit our community site
  using the link in the header.
published: true
---

## Overview

The [Trusted Analytics Platform (TAP)](http://www.trustedanalytics.org) is a Platform-as-a-Service cloud stack for data scientists and application developers to build and operate domain-specific applications driven by data analysis at scale.

The Trusted Analytics Platform is dedicated to ensuring the security and integrity of big data storage and analytics. Read more about the [platform security features](mydoc_security_features) created for TAP.  Visit the [TAP architecture](mydoc_architecture) documentation for more detailed information about design behind the platform. 

TAP includes an intuitive user interface carefully designed around a data science and  application development collaborative workflow.  Take a [walk through the TAP console](mydoc_console_walkthrough) to become familiar with the TAP experience. 

Trusted Analytics Platform (TAP) can easily be deployed on [Amazon Web Services](mydoc_deployment_aws) or as an [on premises deployment](mydoc_deployment_onprem), or you can download the [TAP sources and binaries](mydoc_deployment_sourcesandbinaries). 

##  Getting Started

We provide [use case examples](mydocs_use_case_examples) to get you started with your TAP environment.  Visit our [community site](http://www.community.trustedanalytics.org) for workshops and tutorials that walk you through the TAP workflow.

## Data Platform

In addition to the managed data services in the [[Application Platform]], TAP includes a core data hub built on top of Cloudera's distribution of Hadoop (CDH). 

### CDH

This Analytics PaaS includes a scalable [Cloudera Enterprise Data Hub](https://s3.amazonaws.com/quickstart-reference/cloudera/hadoop/latest/doc/Cloudera_EDH_on_AWS.pdf). The main components of CDH are: 

* HBase
* HDFS 
* Kafka
* Spark
* YARN
* Zookeeper

### Cloudera Director

In addition to core CDH components, TAP includes recently released the [Cloudera Director](http://www.cloudera.com/content/cloudera/en/products-and-services/director.html). The main objective for deploying Director within TAP is to enable operations and provide:

* Self-service cluster spinup/teardown capability
* Dynamic scaling for unpredictable workloads

Cloudera Director is _not_ exposed to end-users; only TAP system admins have access to it.

## Application Platform

### Cloud Foundry

The core application platform capabilities in the TAP Analytics PaaS is delivered through custom deployment of [Cloud Foundry (CF)](http://docs.cloudfoundry.org/concepts/architecture/), which is composed of the following components:

* Director
* Blob store
* Workers
* Message bus
* Health monitor
* Agents
* Cloud platform integration
  - AWS
  - OpenStack (_not_ validated)

### CLI

The TAP Analytics PaaS is API-compatible with the open-source release of CF and supports the [Command Line Interface (CLI) client for Cloud Foundry](https://github.com/cloudfoundry/cli) (also OSS).

You can find further documentation on CLI [here](http://docs.cloudfoundry.org/devguide/#cf). There is also help available in the CLI client itself. Type `cf help` for more information. Each command also has help output available via `cf [command] --help` or `cf [command] -h`.
  
### Managed Services 

In addition to the core platform capabilities offered by CF, TAP includes a growing set of managed services. Services currently available include: 

* Key/value stores
  - Consul
  - Redis
  - etcd
* Document stores
  - Elasticsearch
  - MongoDB
  - CouchDB
  - RethinkDB
* Relational stores
  - MySql
  - PostgreSQL
* Memcache stores
  - Memcached
* Graph stores
  - Neo4j
* Message queues
  - RabbitMQ
  - Kafka
  - Nats
* Other 
  - Logstash (logs collection)
  - SMTP (email sending)
  - ArangoDB (multipurpose NoSQL memory DB)

These services are managed by the platform and are dedicated in most cases. They support a set of predefined plans (for example, small, medium, and large), which can be customized for each deployment.
 
### Shared Services 

In addition to managed services outlined above, TAP delivers a set of shared services on top of the [[Data Platform]] in a multinode architecture:

* HBase
* HDFS 
* Zookeeper
* YARN
* Spark
* Kafka

These multitenant and scalable services are provisioned by the individual service brokers and expose a "slice" of the shared resource pool in the [[Data Platform]] during the binding process.


