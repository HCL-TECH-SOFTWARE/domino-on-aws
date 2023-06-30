---
layout: default
title: "Backup and Recovery"
nav_order: 5
parent: "Home"
description: "Backup and Recovery"
has_children: false
---


<h1>Backup and Recovery</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Introduction

HCL Domino is a stateful application where each instance is commonly installed as a "share nothing" instance to achieve  resiliency. Each instance can operate independent from other machines, making it an ideal product for distributed operations which even supports offline use.

For the high availability scenarios described below it is required to run a minimum of two Domino servers configured to form a Domino cluster and configured to replicate.

## Backup


https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html


## Database Failure

In case a database, or 'Application' in Domino is unavailable, clients will search for the next available replica of the same application in the environment. Typically the next replica is hosted on a cluster member.

## Instance Failure

In case of an instance failure, Notes client traffic will fail over to the cluster partner automatically. For internet protocols the network load balancer will have to dispatch traffic to an available instance.

## Availability Zone Failure

In case of an availability zone failure, NRPC traffic will fail over to the cluster partner automatically. For internet protocols the network load balancer will have to dispatch traffic to an available instance.

## Region Failure

In case of an availability zone failure, NRPC traffic will fail over to the cluster partner automatically. For internet protocols the network load balancer will have to dispatch traffic to an available instance.

## General Failure Considerations

Failover functionality in the HCL Notes client is different from internet protocols. When setting up the HCL Notes client for the first time, it will receive a list of servers that belong to the same cluster, this list is updated on a regular basis. In case a Domino server is unavailable, the client will try to connect to other members of the same cluster automatically.

All data is stored on Amazon EFS, we highly recommend you do daily back-ups and snapshots to ensure minimal loss and downtime for your application. Please visit the following links for details:
* [Amazon EFS Backup](https://docs.aws.amazon.com/efs/latest/ug/awsbackup.html)