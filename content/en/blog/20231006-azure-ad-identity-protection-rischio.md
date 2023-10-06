---
date: 2023-10-06T08:00:00-00:00
description: "How Microsoft Entra ID Protection works and what the concept of risk means when applied to a user and a sign-in."
featured_image: "/images/03-Zero-Trust-Security-Conditional-Access.png"
images:
  - "/images/03-Zero-Trust-Security-Conditional-Access.png"
categories: [ "Identity & Security"]
tags: [ "Entra ID", "Identity Protection"]
title: "Microsoft Entra ID Protection: what is Risk in Entra ID?"
url: "/en/entra-id-identity-protection-risk"
---
In a [Zero Trust Security](/zero-trust-security/) approach, where identity is a fundamental element, the security of authentications can be measured to some extent based on the so-called "signals." Analyzing these signals provides a level of "risk" for a particular user when authenticating to Microsoft 365 services. Today, I'll tell you about Mirosoft Entra Identity Protection and what the concept of "risk" means.

As always, before diving headfirst into this "risky" journey (pun intended 🤣), we need to introduce another concept: you need to understand what **signals** are.

## What is a signal?
In Entra ID, a signal is defined as a property or a particular condition that a user and an authentication have. Here are some examples:
- User's IP address.
- IP and user geolocation.
- Application they are trying to access.
- The operating system of the device they are using (Windows, Linux, macOS, iOS, Android?).
- What type of client the user is using to access M365 services? An app that supports [Modern Authentication](/modern-authentication-multi-factor-authentication-exchange-online-skype-for-business-online/), a browser, or an app that only supports legacy authentication?
- If it's a browser, which browser?
- Which Azure AD groups does their account belong to?
- And so on...

These are all **signals**, and as you can see, Entra ID is capable of detecting many of them.

You might be wondering: *"Rick, why are you bothering me with this signal stuff?"*

I'll answer that without too much beating around the bush: **because "risk" is a signal**!

[![Conditional Access](/images/03-Zero-Trust-Security-Conditional-Access.png)](/images/03-Zero-Trust-Security-Conditional-Access.png)

And so, how does risk fit in among the signals, and what is it?

## What is risk in Entra ID Protection?
In Entra ID Protection, risk is an assessment of user actions, authentications, and their properties. **Cross-analysis of user properties and actions provides an assessment of how clean or suspicious the authentication is and how secure or insecure the user is**.

Risk can be:
- Calculated in real-time (evaluations available in 5/10 minutes).
- Calculated by Microsoft cloud intelligence based on an analysis of authentication events in your tenant, which happens in the background (evaluations available in a few hours).
It is further divided into two types:
- User Risk.
- Sign-in Risk.

{{< rawhtml >}}
  <style>
    table {
      border-collapse: collapse;
      font-family: sans-serif;
      font-size: 0.75em;
    }
    table, th, td {
      border: 1px solid black;
      padding: 10px;
    }
    thead {
      background: #777777;
      color: white;
    }
    blockquote {
      border-left: solid blue;
      padding-left: 10px;
    }
</style>
{{< /rawhtml >}}

## User Risk
Here are the risk signals associated with a user.

| Risk                                                       | Detection type       | Description                                                                                                                                                                                                                                                                                                | Licensing level |
|:-----------------------------------------------------------|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| **Leaked credentials**                                     | Offline              | Microsoft acquires compromised passwords from the dark web and other sources and compares them to the user's credentials. If a match is found between the user's current password and one of the compromised passwords, a "high" risk level is calculated for that user.                                   | Nonpremium      |
| **Anomalous user activity**                                | Offline              | Based on user properties and a form of "behavioral analysis," if unusual activity is detected, a risk level is assigned.                                                                                                                                                                                   | Premium         |
| **Possible attempt to access Primary Refresh Token (PRT)** | Offline              | This risk detection type is discovered using information provided by Microsoft Defender for Endpoint (MDE).                                                                                                                                                                                                | Premium         |
| **User reported suspicious activity**                      | Offline              | This risk detection is reported when a user denies a multifactor authentication (MFA) prompt and reports it as suspicious activity. An MFA prompt not initiated by a user may mean their credentials are compromised.                                                                                      | Premium         |
| **Additional risk detected**                               | Real-time or Offline | This detection indicates that one of the premium detections was detected. Since the premium detections are visible only to Microsoft Entra ID P2 customers, they're titled "additional risk detected" for customers without Microsoft Entra ID P2 licenses.                                                | Nonpremium      |
| **Microsoft Entra threat intelligence**                    | Offline              | This risk detection type indicates user activity that is unusual for the user or consistent with known attack patterns.                                                                                                                                                                                    | Nonpremium      |

These signals are constantly updated and improved. The ones listed above are those available at the time of writing this article. If you want to ensure you are always up to date, I recommend referring to the official documentation:

- [What are risk detections? | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks)

## Sign-in Risk
Here are the risk signals associated with a single authentication.

| Risk                                                     | Detection Type       | Description                                                                                                                                                                                                                                                                                                                                                                         | Licensing level |
|----------------------------------------------------------|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| **Anonymous IP address**                                 | Real-time            | The access is made from an anonymized IP, such as from the Tor network or a VPN.                                                                                                                                                                                                                                                                                                    | Nonpremium      |
| **Activity from anonymous IP address**                   | Offline              | This detection is discovered using information provided by Microsoft Defender for Cloud Apps. This detection identifies that users were active from an IP address that has been identified as an anonymous proxy IP address.                                                                                                                                                        | Premium         |
| **Atypical travel**                                      | Offline              | Two authentications for the same user are identified from different locations, at least one of which can be familiar based on the user's usual behavior. The time between the two logins and the distance between the two locations are also considered.                                                                                                                            | Premium         |
| **Malware linked IP address**                            | Offline              | This risk is detected when the authentication's source IP is known to be linked to malware and bot activities. (**Deprecated detaction**)                                                                                                                                                                                                                                           | Premium         |
| **Unfamiliar sign-in properties**                        | Real-time            | This risk detection type considers past sign-in history to look for anomalous sign-ins. The system stores information about previous sign-ins, and triggers a risk detection when a sign-in occurs with properties that are unfamiliar to the user.                                                                                                                                 | Premium         |
| **Admin confirmed user compromised**                     | Offline              | Entra ID administrators have the ability to classify a user as compromised. If an authentication is made by a user classified this way, the risk level is increased.                                                                                                                                                                                                                | Nonpremium      | 
| **Malicious IP address**                                 | Offline              | This detection indicates sign-in from a malicious IP address. An IP address is considered malicious based on high failure rates because of invalid credentials received from the IP address or other IP reputation sources..                                                                                                                                                        | Premium         |
| **Suspicious inbox manipulation rules**                  | Offline              | This detection is discovered using information provided by Microsoft Defender for Cloud Apps. This detection looks at your environment and triggers alerts when suspicious rules that delete or move messages or folders are set on a user's inbox.                                                                                                                                 | Premium         |
| **Password spray**                                       | Offline              | A password spray attack is when multiple users are simultaneously brute-forced.                                                                                                                                                                                                                                                                                                     | Premium         |
| **Impossible travel**                                    | Offline              | Detected when a user makes two authentications from geographic locations within a timeframe shorter than the time it would take to travel between the two locations. This risk is detected by Microsoft Defender for Cloud Apps.                                                                                                                                                    | Premium         |
| **New country**                                          | Offline              | The previous login locations are considered to build a sort of "history" and determine unfamiliar new locations. This risk is detected by Microsoft Defender for Cloud Apps.                                                                                                                                                                                                        | Premium         |
| **Suspicious inbox forwarding**                          | Offline              | This detection is discovered using information provided by Microsoft Defender for Cloud Apps. This detection looks for suspicious email forwarding rules, for example, if a user created an inbox rule that forwards a copy of all emails to an external address.                                                                                                                   | Premium         |
| **Anomalous Token**                                      | Offline              | This detection indicates that there are abnormal characteristics in the token such as an unusual token lifetime or a token that is played from an unfamiliar location. This detection covers Session Tokens and Refresh Tokens.                                                                                                                                                     | Premium         |
| **Token issuer anomaly**                                 | Offline              | This risk detection indicates the SAML token issuer for the associated SAML token is potentially compromised. The claims included in the token are unusual or match known attacker patterns.                                                                                                                                                                                        | Premium         |
| **Suspicious browser**                                   | Offline              | Suspicious browser detection indicates anomalous behavior based on suspicious sign-in activity across multiple tenants from different countries in the same browser.                                                                                                                                                                                                                | Premium         |
| **Mass access to sensitive files**                       | Offline              | This detection is discovered using information provided by Microsoft Defender for Cloud Apps. This detection looks at your environment and triggers alerts when users access multiple files from Microsoft SharePoint or Microsoft OneDrive. An alert is triggered only if the number of accessed files is uncommon for the user and the files might contain sensitive information. | Premium         |
| **Verified threat actor IP**                             | Real-time            | This risk detection type indicates sign-in activity that is consistent with known IP addresses associated with nation state actors or cyber crime groups, based on Microsoft Threat Intelligence Center (MSTIC).                                                                                                                                                                    | Premium         |
| **Additional risk detected***                            | Real-time or Offline | This detection indicates that one of the premium detections was detected. Since the premium detections are visible only to Microsoft Entra ID P2 customers, they're titled "additional risk detected" for customers without Microsoft Entra ID P2 licenses.                                                                                                                         | Nonpremium      |
| **Microsoft Entra threat intelligence**                  | Real-time or Offline | This risk detection type indicates user activity that is unusual for the user or consistent with known attack patterns. This detection is based on Microsoft's internal and external threat intelligence sources.                                                                                                                                                                   | Nonpremium      |


These signals are constantly updated and improved. The ones listed above are those available at the time of writing this article. If you want to ensure you are always up to date, I recommend referring to the official documentation:

- [What are risk detections? | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks)

## How can risk in Entra ID Protection be useful?
The concept of risk is **extremely useful** when used in combination with **Conditional Access** and **Multi-Factor Authentication**! Even more so if you have access to [Azure Sentinel](/come-capire-azure-sentinel-in-5-passaggi/) and want to automate automatic responses.

Concrete examples? Here they are:
- If two authentications from Italy and Spain are detected within 5 minutes (impossible travel), I request Multi-Factor Authentication for access (Conditional Access + MFA).
- If it's detected that the user's password matches one found in public lists of compromised credentials (risk), I block the authentication (Conditional Access), raise an incident, and lock the user account (Azure Sentinel).

## Where can you find risk assessments and events?
You can simply navigate to the Entra ID portal under **Microsoft Entra ID** -> **Security** -> **Identity Protection**.

##  License requirements for Entra ID Protection
Here's an official Microsoft document that will clarify which licenses are required to take advantage of these features:
- [License Requirements | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection#license-requirements)

## Conclusions on risk and Entra ID Protection
As you can see, the limit to securing your identities in a simple and automated way is only your imagination and, of course, a careful analysis of your needs and environment.

Are you already using Entra ID Protection? Have you automated reactions in case of high risk? Let's discuss it in the comments or on my social media channels; I'm here!

Your IT Specialist, Riccardo