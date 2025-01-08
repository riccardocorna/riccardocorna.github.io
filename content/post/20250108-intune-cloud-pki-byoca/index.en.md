---
date: 2025-01-08T05:00:00-00:00
description: "Learn how to configure Intune Cloud PKI in BYOCA mode. Step-by-step guide to simplify certificate management for Intune devices without on-premises servers. Educational video with updated documentation."
image: "01-cloud-endpoint-diary-intune-cloud-pki-byoca.jpg"
categories : [ "Security", "Modern Work" ]
tags: [ "Microsoft Intune", "Intune", "Cloud PKI", "Security", "BYOCA", "Video", "Guide" ]
title: "Intune Cloud PKI (Bring Your Own Certification Authority)"
url: /en/intune-cloud-pki-byoca-cloud-endpoint-diary
---
IT Specialists! As promised, a very quick video on Intune Cloud PKI in Bring Your Own Certification Authority implementation mode.

## Video
You can find the entire video below, or you can continue reading the article.

{{< youtube xKfFpOhDJvs >}}

## Intune Cloud PKI (Bring Your Own Certification Authority)

### What is Intune Cloud PKI and how does it work
A quick summary of what Microsoft Cloud PKI is: it is a cloud-based service that simplifies and automates the lifecycle management of certificates for devices managed by Intune.

How does it do all this? Thanks to a dedicated public key infrastructure (PKI) in the form of a SaaS service, without on-premises servers, connectors, or hardware.  
The Certification Authority can be entirely cloud-based created on Intune or, if you have your own private on-premises CA (Microsoft integrated with AD or even non-Microsoft), it can be connected with Cloud PKI.  
How is it done? The issuing CA is created in the cloud and, with an appropriate procedure, the ROOT certificate of your on-premises CA is connected to Cloud PKI.
That's exactly what we will see today!

### Creating Issuing CA on Intune Cloud PKI
Let's get started: let's create the Issuing CA on Intune

{{< youtubestartend xKfFpOhDJvs  64 116 >}}

## Exporting Root CA certificate on-premises
On the on-prem CA, meanwhile, we export the complete trust chain that includes the root certificate of the CA.

Here is the command to export the entire trust chain.

   ```
    certutil -ca.chain C:\temp\fullchain.p7b
   ```

{{< youtubestartend xKfFpOhDJvs  123 135 >}}

## Downloading CSR from Intune Issuing CA
Back on Intune, we download the CSR to feed to the on-prem CA to generate the Issuing certificate

{{< youtubestartend xKfFpOhDJvs  143 147 >}}

## Signing CSR and generating Issuing CA certificate
We sign the request and generate the Issuing CA certificate.

Here is the command to generate the certificate.

   ```
    certreq -submit -attrib "CertificateTemplate:<template_name>" -config "<CA_server_name>\<CA_name>" <request_file> <response_file>  
   ```  

**This is a sample syntax, replace the entries in parentheses with your parameters!**

{{< youtubestartend xKfFpOhDJvs  152 169 >}}

## Uploading certificates to Intune and final creation of Issuing CA
Perfect, now we upload the trust chain and the generated certificate to the cloud

{{< youtubestartend xKfFpOhDJvs  165 187 >}}

## Final considerations
We have created our CLOUD PKI!

Look at the duration of this video and tell me if it's not amazing to be able to set up a cloud CA, integrated with your on-prem CA, in the time of this video.

**Question**: how do you trigger this CA to issue certificates? With SCEP configuration profiles but that's another video.

{{< rawhtml >}}
  <div class="disclaimer-box" style="background-color:rgb(252, 229, 183); border: 1px solid rgb(252, 229, 183); padding: 15px; margin: 20px 0; border-radius: 5px; color: #333; font-weight: bold;">
    <p>⚠️ **DISCLAIMER**: as always, this is an educational video. Being in a lab, I had to make assumptions about the configurations of policies, certificates, etc.</p>
  </div>
{{< / rawhtml >}}

In production, do the appropriate analysis before diving headfirst into integrating your CA with Intune Cloud PKI!
To delve deeper into the topic, I leave you the usual documentation that still smells like New Year's Eve 2024-2025.

📃 [Overview of Microsoft Cloud PKI for Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-cloud-pki-overview)  
📃 [Microsoft Cloud PKI fundamentals](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-cloud-pki-fundamentals)  
📃 [Configure Microsoft Cloud PKI - Bring your own CA](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-cloud-pki-configure-byoca)  
📃 [How to export Root Certification Authority Certificate](https://learn.microsoft.com/en-us/troubleshoot/windows-server/certificates-and-public-key-infrastructure-pki/export-root-certification-authority-certificate)


Let me know if you like these faster and lighter videos, write it here in the comments.

As always, follow me on my social profiles and, if you like, subscribe to my channel: it is very important to me!

See you soon... LEGENDS!
