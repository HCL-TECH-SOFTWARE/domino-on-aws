---
layout: default
title: "Security"
nav_order: 1
parent: "Home"
description: "Security"
has_children: false
---


<h1>Security</h1>
Discussing the HCL Domino server default configuration deployed pursuant to this guide, AWS general best practices, and options for securing your solution on AWS.

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Principles

In HCL Domino, administrative priviliges can be restricted according to the least privilege principle / role-based administration according to this documentation.
* [Restricting administrator access](https://help.hcltechsw.com/domino/12.0.2/admin/conf_restrictingadministratoraccess_t.html) 
* Best practices for futher physically securing the HCL Domino server are provided in the documentation [Securing the Domino server](https://help.hcltechsw.com/domino/12.0.2/admin/conf_physicallysecuringthedominoserver_t.html) 

For more information, see [The Domino® security model](https://help.hcltechsw.com/domino/12.0.2/admin/othr_thedominosecuritymodel_c.html)


## IAM Role

Following the least privileges principle when granting access to the individual IAM user accounts.

It is up to the customer to determine which roles and policies to create for your environment. At a minimum, to deploy HCL Domino on AWS, you will need to create an appropriate role to perform the steps required in this deployment guide.

The following roles will be required during this implementation:

IAM permissions required by AWS user to create the resources to deploy the solution:
•	Domino installation require IAM permissions related to 
o	EC2 instances: Create, Destroy, Update
o	Security Groups
o	ALB / ELB creation and update
o	AMI Creation and AMI Access for deployment.
•	Domino Server setup assumes that Customer has AWS VPC created.


## Encrypting Data at Rest

All customer data is stored inside HCL Domino databases (=*.nsf files) locally on the server. 

The customer can choose to encrypt this datais and is in possession of all encryption keys that are used for encryption, there is no data transfer to a third party nor the vendor HCL.


## Encrypting Amazon EFS Data & Metadata at Rest

Customers may choose to encrypt the storage underneath the Domino server as long as this is transparent to the Domino server process and sufficient disk I/O is provided.

## Certificate Manager for SSL/TLS Certificates

Domino does NOT use the Amazon Certificate Manager SSL/TLS Certificates, but provides its own integrated [Domino Certificate Manager](https://help.hcltechsw.com/domino/12.0.2/admin/secu_le_using_certificate_manager.html) to easily manage SSL/TLS certificates within a Domino deployment.

## Secrets stored in AWS Secrets Manager

HCL Domino does NOT require the storage of secrets to operate properly, it does however require Domino certificates to be created and maintained - not using the AWS secrets manager.

As a best practice not covered in this guide, it’s recommended to store all critical points of data, like, admin credentials, Domino certficates, etc. in secrets vault of your choosing outside of your AWS deployment. 

The following credentials are used by the HCL Domino server – they are NOT stored in the AWS secrets manager.
•	Certifier passwords
•	UserIDs and passwords


## Logging/Auditing

The HCL Domino AMI is using an Amazon EFS file system and other AWS resources to monitor and send notifications if the burst credit balance of the file system drops below predefined thresholds.

HCL Domino stores application access and error logs in the Domino log (log.nsf) and/or in the Domino program files directory on the provisioned EFS storage. It defaults to <DominoData>/logs. For information about how to analyze these logs, please consult the [HCL Domino product documentation](https://help.hcltechsw.com/domino/12.0.2/admin/admn_thedominoserverloglognsf_c.html)

Optionally, the Domino Web server log can be enabled to log requests sent over web protocols. For details see
https://help.hcltechsw.com/domino/12.0.2/admin/admn_thedominowebserverlogdomlognsf_c.html

The default implementation does not enable AWS CloudTrail logs. You can enable CloudTrail logging by navigating to the CloudTrail service console, and enabling CloudTrail logs.
With CloudTrail, activity related to actions across your AWS infrastructure are recorded as an event in CloudTrail. This helps you enable governance, compliance, and operational and risk auditing of your AWS account.