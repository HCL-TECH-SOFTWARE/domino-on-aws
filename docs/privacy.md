---
layout: default
title: "Privacy"
parent: "Home"
nav_order: 1
description: "Privacy"
has_children: false
---

<h1>Privacy</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Location of all sensitive information

This Amazon Machine Image (AMI) provides an unconfigured HCL Domino server without any sensitive data in the first place. 
When configuring this server the customer will either use existing Domino certificates or will create a new Domino certificate and new Domino ID file for the administrator - both are a set of public/private key pairs that are stored on the server in the DATA directory so the customer can retrieve them for storing offline.

None of the keys, certificates or passwords the customer created at setup time are shared with the product vendor HCL.

## Data encryption configuration

HCL Domino does NOT require AWS Data Encryption to operate properly. 
Data is stored in Domino databases (*.nsf) which the customer can choose to encrypt using encryption keys in Domino that only the customer is in possession of. 

For more information, please refer to the following links/information  
* Domino itself is [encrypting data at rest](https://help.hcltechsw.com/domino/12.0.2/admin/database_encryption.html). Customers can choose to enable the Domino Attachment and Object Service (DAOS) which will store file attachments outside of the Domino database. The DAOS repository is encrypted by default. For more information about DAOS encryption please see
* [Encryption new attachment files with a private key](https://help.hcltechsw.com/domino/12.0.2/admin/admn_encryptingattachmentfileswithoutsharedkey.html)

For more information on encryption standards of HCL Domino in general, see this documentation https://help.hcltechsw.com/domino/12.0.2/admin/conf_aesencryption_c.html


## Instructions for rotating programmatic system credentials and cryptographic keys. 

Aside from credentials or keys used to access the operating system, HCL Domino access is establishing a public/private key infrastructure. Certificates and key material is valid for a (configurable) time and will need to be rotated before they expire or when needed. This process is called a key-rollover and is explained in the following article.

* [HCL Domino - Requesting a key rollover](https://help.hcltechsw.com/domino/12.0.0/admin/secu_le_keyrollover.html)

furthermore the following book describes the key rollover process in details:
* [HCL Domino Certificates Key Rollover (EN)](https://www.madicon.de/notes-domino/books/hcl-domino-certificates-key-rollover-en/)

## Encryption techniques used

For more information about encryption techniques used by HCL Domino please refer to [security](security.md).