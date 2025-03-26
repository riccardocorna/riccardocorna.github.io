---
date: 2025-03-19T05:00:00-00:00
description: "Essential tutorial on Intune Endpoint Privilege Management: learn how to enable standard users to run executables with administrative privileges, securely. 🚀"
image: "01-microsoft-intune-endpoint-privilege-management.jpg"
categories: [ "Modern Work", "Security" ]
tags: [ "Microsoft Intune", "EPM", "Endpoint Privilege Management", "Video", "Tutorial", "Cloud Endpoint Diary"]
title: "Microsoft Intune Endpoint Privilege Management"
url: /en/microsoft-intune-endpoint-privilege-management
---

Hello everyone, IT specialists! 👋 Today we will explore a very interesting feature of Microsoft Intune: **Endpoint Privilege Management (EPM)**.

## Video
You can find the entire video below, or you can continue reading the article.

{{< youtube 1CT2xqCQrns >}}

## What is Endpoint Privilege Management?
Endpoint Privilege Management is a feature of the Intune Suite that allows non-administrative users to perform tasks with elevated privileges, such as running .exe, .msi, and .ps1 files. In other words, it allows the installation and execution of software and scripts without requiring an administrative password.

## How to: Implementing EPM

### Creating Elevation Settings Policies
To activate the EPM feature, you need to create an **elevation settings** policy. This policy serves to awaken the feature within the Windows client and establish the default baseline in case of elevation.
In this video, as an example, I created a policy that denies all elevation requests.

{{< youtubestartend 1CT2xqCQrns 69 101 >}}

Let's see if it really works!

{{< youtubestartend 1CT2xqCQrns 112 123 >}}

Perfect, it works! Now let's create the first Elevation Rule.

### Creating and Managing Elevation Rules

**Elevation rules** are used to establish the behavior of a specific elevation request, intercepting specific files by name, hash, or other parameters. These rules can require an approval flow or be executed automatically.

#### Example of an Elevation Rule with Approval
Let's create an elevation rule with approval.

{{< youtubestartend 1CT2xqCQrns 156 187 >}}

Okay, now let's check on the client what happens if we try to install 7-Zip.

{{< youtubestartend 1CT2xqCQrns 193 212 >}}

See? Approval from the system administrator is required. The elevation request can be approved directly on the Intune portal.

{{< youtubestartend 1CT2xqCQrns 221 239 >}}

Let's go back to our Windows machine to see if the user can now install 7-Zip.

{{< youtubestartend 1CT2xqCQrns 244 259 >}}

Perfect, everything works! 😊

#### Example of an Automatic Elevation Rule
Now let's try to create an automatic elevation rule that does not require any approval flow for file execution. A typical use case for this situation could be internally developed company software.

Let's see how to create the rule for this situation.

{{< youtubestartend 1CT2xqCQrns 283 313 >}}

Rule created! Now let's see what happens on the Windows client.

{{< youtubestartend 1CT2xqCQrns 316 325 >}}

See? Everything runs smoothly without any additional messages or interactions.

### Strategies for Managing Software Versions
If the version of a software installer changes, you need to recalculate the hash or retrieve it from the Intune portal in the elevation report. With those, you can create a new policy. However, there are techniques to intercept all software from a certain publisher using **reusable settings**. These settings allow you to associate different policies without having to create new rules each time.

## Attached Documentation
As always, here is the documentation package for your further study.

📌 [Use Endpoint Privilege Management with Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-overview)  
📌 [Guidance for creating elevation rules with Endpoint Privilege Management](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-guidance-for-creating-rules)  
📌 [Configure policies for Endpoint Privilege Management](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-policies)  
📌 [Deployment Considerations and frequently asked questions for Endpoint Privilege Management](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-deployment-considerations-ki)

## Conclusion

Microsoft Intune's Endpoint Privilege Management offers an effective way to manage the privileges of standard users, allowing them to perform tasks with elevated privileges in a controlled manner. If you want to learn more, leave a comment and subscribe to my YouTube channel to not miss the next videos! 📚🔔  
Thank you!

Your IT Specialist,  
Riccardo
