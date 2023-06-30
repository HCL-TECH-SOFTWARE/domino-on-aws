---
layout: default
title: "Home"
nav_order: 1
description: "HCL Domino on Amazon Web Services (AWS)"
has_children: true
---

[AWS Marketplace]( https://aws.amazon.com/marketplace/ ){: .btn .btn-green }
[View on GitHub](https://github.com/HCL-TECH-SOFTWARE/domino-on-aws){: .btn }

<h1>HCL Domino on Amazon Web Services (AWS)</h1>
This website is providing information on how to run HCL Domino on AWS.

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Background
This guide will detail the steps to deploy the HCL Domino Server following AWS best practices. In this guide, we cover the following types of deployments:
* Single availability zone deployment

## Prerequisites and Requirements

The following AWS services are required to deploy HCL Domino running on AWS.
* AMS Virtual Private Cloud (VPC)
* AMS Elastic Compute Cloud (EC2)

System requirements for HCL Domino regardless of the deployment type are outlined in article [KB0073794](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0073794)

On high level, the minimum requirements are:
•	min. 1 CPU Core, recommending 2 CPU Cores
•	min. 3 GByte Disk storage
•	min. 4 GByte Memory

### Time

The deployment will take about 5min, but configuration
and testing could take up to an hour.

### Product License

An AWS Marketplace subscription is required for production use of the HCL Domino AMI. The two options for obtaining a subscription and/or license are:
* Pay as you go (PAYG) - Subscribe through the AWS Marketplace and pay for time-based usage. Costs are outlined in the AWS Marketplace and in the costs section of this guide. This method does not require a separate license from the HCL sales team.
* Bring your own license (BYOL) - Subscribe through the AWS Marketplace and apply an existing license. Please contact us directly to order a license at XXXXX@hcltechsw.com.


### AWS Account

You must have an AWS account set-up. 
Start [here](https://aws.amazon.com/getting-started/)

### Knowledge Requirements

The following table lists the skills and knowledge needed to deploy and operate HCL Domino on AWS.

Skill |	Description
---|---
AWS Engineer | To deploy all required resources as per design and administration.
Domino Administrator | for administration of HCL Domino server, this is a vendor specific skill.
