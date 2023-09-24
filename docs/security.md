---
layout: default
title: "Security"
nav_order: 2
parent: "Architecture"
description: "Security"
has_children: false
---


<h1>Security</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

Discussing the HCL Domino server default configuration deployed pursuant to this guide, AWS general best practices, and options for securing your solution on AWS.
## Principles

In HCL Domino, administrative priviliges can be restricted according to the least privilege principle / role-based administration according to this documentation.
* [Restricting administrator access](https://help.hcltechsw.com/domino/12.0.2/admin/conf_restrictingadministratoraccess_t.html) 
* Best practices for futher physically securing the HCL Domino server are provided in the documentation [Securing the Domino server](https://help.hcltechsw.com/domino/12.0.2/admin/conf_physicallysecuringthedominoserver_t.html) 

For more information, see [The Domino® security model](https://help.hcltechsw.com/domino/12.0.2/admin/othr_thedominosecuritymodel_c.html)
and [Overview of Domino security](https://help.hcltechsw.com/domino/12.0.0/admin/othr_overviewofdominosecurity_c.html)

## IAM Role

Following the least privileges principle when granting access to the individual IAM user accounts.

It is up to the customer to determine which roles and policies to create for your environment. At a minimum, to deploy HCL Domino on AWS, you will need to create an appropriate role to perform the steps required in this deployment guide.

The following roles will be required during this implementation:

IAM permissions required by AWS user to create the resources to deploy the solution:
* Domino installation require IAM permissions related to 
  - EC2 instances: Create, Destroy, Update
  - Security Groups
  - ALB / ELB creation and update
  - AMI Creation and AMI Access for deployment.
* Domino Server setup assumes that Customer has AWS VPC created.

## Encrypting Data at Rest

All customer data is stored inside HCL Domino databases (=*.nsf files) locally on the server. 

The customer can choose to encrypt this datais and is in possession of all encryption keys that are used for encryption, there is no data transfer to a third party nor the vendor HCL.

Data encryption configuration
HCL Domino does NOT require AWS Data Encryption to operate properly. 

Data is stored in Domino databases (*.nsf) which the customer can choose to encrypt using encryption keys in Domino that only the customer is in possession of. For details, please see  
* Domino itself is encrypting data at rest using [database encryption](https://help.hcltechsw.com/domino/12.0.2/admin/database_encryption.html).
Customers can choose to enable the Domino Attachment and Object Service (DAOS) which will store file attachments outside of the Domino database. The DAOS repository is encrypted by default. For more information about DAOS encryption please see
* [Encryption new attachment files with a private key](https://help.hcltechsw.com/domino/12.0.2/admin/admn_encryptingattachmentfileswithoutsharedkey.html)

For more information on encryption standards of HCL Domino in general, see [this documentation](https://help.hcltechsw.com/domino/12.0.2/admin/conf_aesencryption_c.html) and [Encryption and electronic signatures](https://help.hcltechsw.com/domino/12.0.2/admin/conf_encryption_c.html)

## Purpose and location of keys
Users in HCL Domino will obtain a public/private key pair are stored inside Domino. Creation, management, and security of those keys is entirely done in Domino with zero dependencies to AWS
For more information about user IDs, please refer to the following documentation
* [How to register users](https://help.hcltechsw.com/domino/12.0.2/admin/conf_userregistration_c.html) 
* [Secure IDVault store](https://help.hcltechsw.com/domino/12.0.2/admin/conf_notesidvault_c.html)

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

Optionally, the Domino Web server log can be enabled to log requests sent over web protocols. For details see [Domino Web server log](https://help.hcltechsw.com/domino/12.0.2/admin/admn_thedominowebserverlogdomlognsf_c.html)


The default implementation does not enable AWS CloudTrail logs. You can enable CloudTrail logging by navigating to the CloudTrail service console, and enabling CloudTrail logs.
With CloudTrail, activity related to actions across your AWS infrastructure are recorded as an event in CloudTrail. This helps you enable governance, compliance, and operational and risk auditing of your AWS account.

## Instance Metadata Service Version 1 (IMDSv1)

N/A - Instance Metadata Service is not used by HCL Domino
