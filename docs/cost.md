---
layout: default
title: "Cost & Sizing"
nav_order: 3
parent: "Home"
description: "Cost & Sizing"
has_children: false
---


<h1>Costs</h1>
Discussing the HCL Domino server default configuration deployed pursuant to this guide, AWS general best practices, and options for securing your solution on AWS.

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Costs

The cost of the environment depends on the AWS ressources used and the number of HCL Domino licenses required. The following assets are required to provide a functional platform:
* 1 Amazon EC2 Instances

Use the guidelines in the Sizing section to determine what instances are appropriate for your deployment.
   
Here is a sample calculation with the instances listed for the “<500 users“ tier listed in the Sizing section of this guide: 

{: .note }
Storage and data transfer are not included as these vary depending on configuration. Please consult AWS Pricing for the latest information.

Below is a table of our license cost mapped to Amazon EC2 instance sizes in all regions:

## Sizing

The following table outlines recommendations for Amazon EC2 instance size as well as Amazon EFS performance mode. If you need assistance with sizing your implementation, please contact HCL for additional sizing guidance. 

.  | Test Environment | <100 | >100 - 2.000 | >2.000
---| --- | --- | --- | ---
EC2 | t2.medium | t2.large | t2.2xlarge | Contact HCL
EFS | General Purpose  | General Purpose  | General Purpose  | General Purpose  | 