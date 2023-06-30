---
layout: default
title: "Health Check"
nav_order: 4
parent: "Home"
description: "Health Check"
has_children: false
---


<h1>Health Check</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Health Check
tbd

## Certificate Expiration

Domino certificates as well as any SSL/TLS certificates must be monitored for expiration. HCL Domino provides an integrated process for monitoring certificate expiration which, when configured, will notify administrators or even auto-renew certificates that are about to expire.

For details see [Admin Central] and [Certificate Manager](https://help.hcltechsw.com/domino/12.0.2/admin/secu_le_using_certificate_manager.html)

Furthermore AWS provides an AWS CloudFormation template that can help set up an alarm for expiring SSL/TLS certificates. Please visit [this link](https://docs.aws.amazon.com/config/latest/developerguide/acm-certificate-expiration-check.html) for details