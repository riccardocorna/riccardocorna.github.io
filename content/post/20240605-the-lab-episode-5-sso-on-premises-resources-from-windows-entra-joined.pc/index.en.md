---
date: 2024-06-05T05:00:00-00:00
description: "Today we see the first concrete result of building our hybrid lab inspired by a modern management of identities and devices: we will test together if a Windows Entra Joined PC can access an on-premises resource in single sign-on, specifically a file server."
image: "01-the-lab-episode-5-sso-on-prem-windows-entra-joined-pc.jpg"
categories: [ "Security", "Modern Work" ]
tags: [ "Single Sign-On", "Active Directory", "Microsoft Entra", "Windows", "Entra Join", "Video", "The Lab" ]
title: "The Lab - Episode 5 - SSO on On-Premises Resources with a Windows Entra Joined PC"
url: /en/the-lab-episode-5-sso-on-prem-windows-entra-joined-pc
---
Today we see the first concrete result of building our hybrid lab inspired by a modern management of identities and devices: we will test together if a Windows Entra Joined PC can access an on-premises resource in single sign-on, specifically a file server.

Will it work? You’ll see in the video :)

## Video
You can find the full video below, or you can continue reading the article.

{{< youtube vmAxRlVrh1o >}}

## SSO on On-Premises Resources with a Windows Entra Joined PC

### Introduction
IT specialists, hello everyone! We started the series The LAB some time ago: together, we have built a nearly complete hybrid lab environment.

An Active Directory domain controller, a Certification Authority, we have seen how to implement LDAPS and, finally, how to synchronize on-premises Active Directory identities with Entra ID, to hybridize our infrastructure with the cloud.

Today’s video is **THE** one where we see the first concrete result of our work.

We will try to access a network folder on an on-premises file server, normally joined to the domain, from a Windows 11 Entra Joined PC.

The PC is joined directly to Microsoft Entra in the cloud, not to the on-premises domain.

Why am I so keen that it works and even more eager to show it to you?

1. Because field experience suggests that very few people are aware that this type of single sign-on is possible natively, out-of-the-box.
2. Because this, in my view, is a fundamental step in reducing dependence on on-premises Active Directory, at least for users’ Windows devices.
3. Because this was one of the declared goals of this lab: to manage clients in a cloud-native way without domain joining them.

Will it work? Let’s see together, starting with the requirements and scenario description.

### Requirements
Let’s start with the requirements:
- A Windows PC, in this case, Windows 11, Entra Joined, meaning directly joined to Entra ID: we have it.
- Hybridized Active Directory with Entra ID through Microsoft Entra Connect: done!
- The PC, to access the file server, must have network visibility with the domain controller and, clearly, with the file server itself.

***ATTENTION***: *do not confuse authentication with network reachability! We are now testing that a non-domain joined PC can access, by authenticating, a domain file server but, testing it this way, we are simulating a specific situation: the PC, while not domain-joined, is in the corporate network.*

Summarizing: today our user is in the office, okay?

What does this mean? That if we tried to do this same test from a network other than the corporate one, we certainly wouldn’t be able to access the internal file server unless we had a VPN, or other solutions, or blah blah blah.

### Scenario Verification
That said, let’s do all the necessary checks: no tricks, no cheating!

#### Verify the Windows PC Hostname
Let’s start by seeing what our test PC is called

{{< youtubestartend vmAxRlVrh1o 173 184 >}}

#### Verify Non-Domain Join
Perfect, now let’s verify that it is NOT joined to the on-premises domain itspecialist.local, our Active Directory for The LAB.

{{< youtubestartend vmAxRlVrh1o 193 205 >}}

Okay, we didn’t find it.

#### Verify Entra Join
Let’s look it up on Microsoft Entra.

{{< youtubestartend vmAxRlVrh1o 209 222 >}}

Found it! It is our Entra Joined PC.

#### Verify Status with dsregcmd
Still don’t believe it? Let’s do the acid test directly on the device by verifying its registration status with the dsregcmd command.

{{< youtubestartend vmAxRlVrh1o 236 254 >}}

#### Verify Domain Controller Visibility
To make sure the scenario is clear, i.e., to show you that the user is in the office today, let’s see if I can ping the domain controller...

{{< youtubestartend vmAxRlVrh1o 264 271 >}}

#### Verify File Server Reachability
And if we can ping our file server.

{{< youtubestartend vmAxRlVrh1o 275 283 >}}

### Let's Test Single Sign-On!
Okay! We’ve reached the moment of truth!

Now, finally, after months of building our lab, we finally see if our cloud-joined PC can access an on-premises file server without batting an eyelid...

{{< youtubestartend vmAxRlVrh1o 301 321 >}}

Yes, we did it. We took the first step to reduce dependence on Active Directory and, now, we can begin to soar towards true modern and cloud-native management of users’ devices.

### Supported SSO Scenarios on On-Prem Resources
So, ultimately, what can an Entra Joined device do SSO for when it comes to on-premises resources?

At the moment, two scenarios are fully covered:
- Access to a UNC path on a domain member server, such as a file server.
- Access to a domain web server configured with Windows Integrated Authentication.

There are some limitations which you can explore in detail through the usual ton of documentation below:

🔗 [What is a Microsoft Entra Joined device?](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join)  
🔗 [How SSO to on-premises resources works on Microsoft Entra joined devices](https://learn.microsoft.com/en-us/entra/identity/devices/device-sso-to-on-premises-resources)

### Conclusions
As always, I tried to show you the highlights of everything needed to achieve this result: to get there in your production environment requires a thorough analysis, especially at the application level!

Application authentication, especially if it relies on on-premises Active Directory, is the most important issue to clear up in any evolutionary project involving authentication, whether user or device.

That said, what’s next for The LAB?

We will continue to configure our environment: strong authentications, Conditional Access, Password Protection, device enrollment in Intune, onboarding devices to Defender for Endpoint, in short, we will continue to expand our lab like a Sim City, or... we could set ourselves an even more ambitious goal!

If, like me, you want to conquer and dominate the cloud world, keep following this series and, if you haven’t already, subscribe to my YouTube channel or follow me on LinkedIn and Instagram.

You can find all the references on my blog ITSpecialist.cloud.

See you next time, I’ll be waiting... LEGENDS!