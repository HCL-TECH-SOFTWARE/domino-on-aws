---
layout: default
title: "Cost & Sizing"
nav_order: 3
parent: "Home"
description: "Cost & Sizing"
has_children: false
---


<h1>Costs and Sizing</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

Discussing the HCL Domino server default configuration deployed pursuant to this guide, AWS general best practices, and options for securing your solution on AWS.

## Costs

HCL Domino software is available through several product offerings and associated software licenses, for product entitlement and licensing please reach an HCL Software representative or business partners for proper sizing and licensing for your use case.

The cost of the environment depends on the AWS ressources used and the number of HCL Domino licenses required. The following assets are required to provide a functional platform:
* 1 Amazon EC2 Instances
* 1 EC2 general purpose storage
* 1 Virtual Proviate Cloud (VPC) to create a private network
* 1 NAT Gateway (optional)

Use the guidelines in the Sizing section to determine what instances are appropriate for your deployment.
   
Here is a sample calculation with the instances listed for the “<100 users“ tier listed in the Sizing section of this guide: 

{: .note }
Storage and data transfer are not included as these vary depending on configuration. Please consult AWS Pricing for the latest information.

Below is a table of our license cost mapped to Amazon EC2 instance sizes in all regions:

## Sizing

The following table lists the estimated sizing for Amazon EC2 instance for the HCL Domino platform based on the number of users. The sizing of an environment does not always depend on the numner of users, other factors like [known limits](https://help.hcltechsw.com/dom_designer/11.0.1/basic/H_NOTES_AND_DOMINO_KNOWN_LIMITS.html) of the Domino platform may require custom sizing / custom deployment architectures. 

Users | CPU Cures | Memory | AWS EC2 Machine Type
---|---|---|---
10    |	1 Cores	| 4 GByte  | t2.nano
100	  | 2 Cores |	8 GByte  | t2.large
1000  | 4 Cores	| 16 GByte | t2.2xlarge
1000+	| contact HCL |	contact HCL | contact HCL

For more information about sizing and limitations, see [Domino known limits](https://help.hcltechsw.com/dom_designer/11.0.1/basic/H_NOTES_AND_DOMINO_KNOWN_LIMITS.html)


