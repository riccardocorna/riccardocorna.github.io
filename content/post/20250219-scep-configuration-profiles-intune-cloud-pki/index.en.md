---
date: 2025-02-19T05:00:00-00:00
description: "Discover how to use a Cloud PKI with Microsoft Intune to request certificates with SCEP configuration profiles. Complete tutorial on creating and distributing digital certificates."
image: "01-scep-configuration-profiles-intune-cloud-pki.jpg"
categories: [ "Modern Work", "Security" ]
tags: [ "Microsoft Intune", "Cloud PKI", "SCEP", "Configuration Profiles", "Video", "Tutorial" ]
title: "SCEP Configuration Profiles for Intune Cloud PKI"
url: /en/intune-enhanced-device-hardware-inventory
---
IT specialists, hello everyone! Do you remember that some time ago we saw [how to implement a Cloud PKI with Microsoft Intune](/en/intune-cloud-pki-byoca-cloud-endpoint-diary)? Well, it's time to use it by requesting certificates with SCEP configuration profiles!

## Video
You can find the entire video below, or you can continue reading the article.

{{< youtube zej8tN6fD3w >}}

## SCEP Configuration Profiles for Intune Cloud PKI
We use Cloud PKI with Microsoft Intune to request certificates with SCEP configuration profiles.

### What is SCEP?
SCEP, which stands for Simple Certificate Enrollment Protocol, is a protocol used to simplify the management and distribution of digital certificates. In the context of Intune Cloud PKI, SCEP is used to distribute certificates to our managed devices, which will then be used to authenticate to various corporate resources.

### Creating Intune Profiles
Let's start by creating Intune profiles to distribute the certificates, starting with the Trusted Certificates, namely the Root CA and the Issuing CA, which we created a short time ago with Intune Cloud PKI. If you don't remember, go back and watch the previous video.

{{< youtubestartend zej8tN6fD3w 57 121 >}}

### Configuring the SCEP Profile
Now it's finally time to create our SCEP profile, which we will configure to interact with our Cloud PKI. Pay particular attention to the SCEP URL parameter. First, let's see the configuration of a user certificate and then the configuration of the SCEP profile to request a machine certificate.

#### SCEP Profile for User Certificate
{{< youtubestartend zej8tN6fD3w 136 180 >}}

#### SCEP Profile for Machine Certificate
{{< youtubestartend zej8tN6fD3w 185 226 >}}

### Verifying Certificate Issuance
Perfect, now let's verify that the certificates have actually been issued.

{{< youtubestartend zej8tN6fD3w 237 261 >}}

### Useful Tips
- Maintain consistency between the assignments of Trusted Certificate profiles and SCEP profiles by assigning them to the same group and, above all, be consistent with the type of object that populates the group: either users or devices. This is because there is a specific supportability table to ensure that the certificates are actually issued. Here is the table below.

| Trusted certificate profile assignment includes User | Trusted certificate profile assignment includes Device | Trusted certificate profile assignment includes User and Device |
|------------------------------------------------------|-------------------------------------------------------|---------------------------------------------------------------|
| **SCEP certificate profile assignment includes User** | Success                                               | Failure                                                       | Success                                                       |
| **SCEP certificate profile assignment includes Device** | Failure                                               | Success                                                       | Success                                                       |
| **SCEP certificate profile assignment includes User and Device** | Success                                               | Success                                                       | Success                                                       |

Other useful tips:
- If you have a hybrid environment, comply with the strong mapping requirements (details in the documentation attached below).

## Documentation
Here is all the documentation I referred to during the video.

📃 [Use SCEP certificate profiles with Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/protect/certificates-profile-scep)  
📃 [Troubleshoot deployment of Simple Certificate Enrollment Protocol (SCEP) certificate profiles to devices with Microsoft Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/certificates/troubleshoot-scep-certificate-profile-deployment)  
📃 [Troubleshoot use of Simple Certificate Enrollment Protocol (SCEP) certificate profiles to provision certificates with Microsoft Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/certificates/troubleshoot-scep-certificate-profiles)  
📃 [Troubleshoot delivery of Simple Certificate Enrollment Protocol (SCEP) certificates](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/certificates/troubleshoot-scep-certificate-delivery)  
📃 [Support tip: Implementing strong mapping in Microsoft Intune certificates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-implementing-strong-mapping-in-microsoft-intune-certificates/4053376)


## Conclusions
**As always, this is a lab environment, so do the appropriate analysis before putting everything into production.**  
Thank you for watching the video up to this point. Subscribe to my YouTube channel and help it grow to produce even better content. For the rest, I'll see you on LinkedIn and on my blog ITSpecialist.cloud!

Thanks again! See you soon... LEGENDS!

Your IT Specialist,  
Riccardo