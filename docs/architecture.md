---
layout: default
title: "Architecture"
nav_order: 2
description: "Architecture"
has_children: false
---

<h1>Architecture</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

HCL Domino supports containerized deployments on EKS and traditional deployments on AMI using Windows or Linux - all for test, development, staging, and production environments.

## Typical deployment overview
The typical use case for HCL Domino is providing a mail and application platform where for a small deployment all AWS based components of HCL Domino are deployed into a single AWS availability zone. 

A deployment consists of a single server (either a docker container or a virtual machine with Windows or Linux) with preferably 2 CPU cores, 8 GB RAM and 50 GB storage that can be deployed in any availability zone. 
Storage, memory, and CPU resources can be added as needed to the deployment. For more information see [sizing](sizing.md)

### HCL Domino componentes

HCL Domino Server is an all in one product where a single instance of the product is providing access to rich clients and web browser, a NAT gateway is used to provide access to TCP ports 1352, 80/443, and other ports as needed. 

### Scalability

An HCL Domino environment can scale in multiple dimensions.
* Vertially by adding more ressources to a single instance
* Horizontally by adding more servers to an environment, either in the same cluster, by adding clusters, or by adding additional Domino Domains.

## Single AZ Architecture Diagram

A typical non-HA deployment of HCL Domino would look like this:
![uncached image](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/HCL-TECH-SOFTWARE/domino-on-aws/main/docs/assets/plantuml/domino-aws-single-az.puml)

HCL Domino may be able to be deployed in a single availability zone for development and evaluation purposes. This solution does not provide high availability nor fault tolerance and is not recommended for production use.

To deply this scenario, follow these [step by step instructions](deployment-steps.md)

## Multi-AZ Fault Tolerant Architecture Diagram

A simple HA deployment of HCL Domino in a multi-AZ deployment would look like this:
![uncached image](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/HCL-TECH-SOFTWARE/domino-on-aws/main/docs/assets/plantuml/domino-aws.puml)

In the multi-AZ fault tolerant deployment option, the instances are situated behind a network load balancer. HCL Domino is deployed across 2 or more availability zones to ensure high availability and fault tolerance. The [architecture](architecture.md) of the HCL Domino product does not support auto-scaling, additional instances can however be joined to an existing deployment to support a growing demand.

## Deployment