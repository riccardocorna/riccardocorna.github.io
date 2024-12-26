---
date: 2024-12-16T05:00:00-00:00
description: "Authenticate devices via certificate (EAP-TLS) with Intune Cloud PKI and SCEP profiles on Windows NPS server, configure the SAN with the computer account's UPN to avoid issues, and learn more about certificate requirements and best practices with Intune."
image: "01-scep-san-add.png"
categories : [ "Security" ]
tags: [ "Intune", "SCEP","Certificate", "Device", "Authentication", "SAN", "NPS" ]
title: "Quick tip on SCEP profile for EAP-TLS device authentication"
url: /en/scep-certificate-tips-eap-tls-intune-cloud-pki
---
🚨Monday quick tip that will save you hours of troubleshooting. Thanks to [Yuri Gasparini](https://www.linkedin.com/in/yurigasparini/) for the gem. 🙏🏻

## 💻 Scenario
You want to authenticate a device via certificate (EAP-TLS), using Intune Cloud PKI, SCEP profiles via Intune, and the server is a Windows NPS server. Clients are domain-joined, Hybrid Entra Joined, and managed by Intune.

## 🔨 Configuration
The SCEP certificate, in this case, has specific requirements, especially for the Subject Alternative Name (SAN). You can find all the details here:

📃 [Certificate requirements when you use EAP-TLS or PEAP with EAP-TLS](https://learn.microsoft.com/en-us/troubleshoot/windows-server/networking/certificate-requirements-eap-tls-peap#client-certificate-requirements)

## ⚠️ Attention: here's the key tip
But the real key tip is this. Beyond the usual parameters to configure in the SCEP profile on Intune, it's crucial in this scenario to correctly populate the SAN with the computer account's UPN. Too bad there isn’t a dedicated, ready-to-use variable. How can you do it?  
By using a mixed combination of variables and static text, like this:

1️⃣ **User Principal Name (UPN)** ➡️ **{{DeviceName}}@domainname.local**

And don’t forget strong mapping!

2️⃣ **URI** ➡️ **{{OnPremisesSecurityIdentifier}}**

For further insights into SCEP profiles:  
📃 [Create and assign SCEP certificate profiles in Intune](https://learn.microsoft.com/en-us/mem/intune/protect/certificates-profile-scep)  
📃 [KB5014754: Certificate-based authentication changes on Windows domain controllers](https://support.microsoft.com/en-us/topic/kb5014754-certificate-based-authentication-changes-on-windows-domain-controllers-ad2c23b0-15d8-4340-a468-4d4f3b188f16)

Your IT Specialist,  
Riccardo
