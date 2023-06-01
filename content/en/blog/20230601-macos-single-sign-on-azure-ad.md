---
date: 2023-06-01T05:00:00-00:00
description: "Thanks to macOS Single Sign-On for Azure AD, the number of authentication requests to Microsoft 365 will be significantly reduced."
featured_image: "/images/01-macOS-AzureAD-single-Sign-On.png"
categories: [ "Identity & Security"]
tags: [ "macOS", "Azure AD", "Single Sign-On"]
title: "macOS Single Sign-On on Azure AD"
url: "/en/macos-single-sign-on-azure-ad"
---
About 2 years ago (June 2021), I had fun experimenting with a new feature that was in preview: macOS Single Sign-On (SSO) for Azure AD on Microsoft 365 applications and services.

![Azure AD Single Sign-On Extension macOs](/images/01-macOS-AzureAD-single-Sign-On.png)

⚠️ **Update as of June 1, 2023** The "Microsoft Azure AD" plug-in is finally in General Availability and is ready to use in production environments!

You might be wondering, "What on earth is it for?"

**This feature allows you to authenticate yourself and your fantastic Mac more easily to Microsoft 365 services and applications without repeated credential prompts**, making the user experience even smoother and seamless.

**It is important to note that this extension does not allow device-level login on macOS. it is only for applications.**

Below, however, I'll provide you with some resources:

- The link to my video where I talked about and demonstrated the user experience

{{< youtube jKLXHIbLu0s >}}

- A wonderful infographic by [Merill Fernando](https://twitter.com/merill), Product Manager at Microsoft (follow his profile, he's truly an endless source of useful information!).

{{< rawhtml >}}
  <iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:7066440254492151808" height="811" width="504" frameborder="0" allowfullscreen="" title="Post incorporato"></iframe>
{{< /rawhtml >}}

If your Mac is managed by Intune, the configuration requires:
- Installing the Company Portal app on the Mac
- The operating system version to be macOS 10.15 or higher

Here's all the necessary information: 😉

- [Microsoft Enterprise SSO for Apple Devices Is Now Available for Everyone](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/microsoft-enterprise-sso-for-apple-devices-is-now-available-for/ba-p/3827395)
- [Microsoft Enterprise SSO plug-in for Apple devices – Microsoft identity platform | Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/develop/apple-sso-plugin)
- [Create iOS/iPadOS or macOS device profile with Microsoft Intune – Azure | Microsoft Docs](https://docs.microsoft.com/en-us/mem/intune/configuration/device-features-configure#single-sign-on-app-extension)
- [macOS device feature settings in Microsoft Intune – Azure | Microsoft Docs](https://docs.microsoft.com/en-us/mem/intune/configuration/macos-device-features-settings#single-sign-on-app-extension)

In a private conversation I had some time ago, I wrote the following: "...I believe there has never been a moment before when the products of the two worlds (Microsoft and Apple) have worked so well together..."

And I am increasingly convinced of this every day when I test features like macOS Single Sign-On. Microsoft is truly working closely with Apple, and the results are evident.

How about you? What measures have you taken to integrate macOS effectively within your company? I look forward to discussing.

Riccardo
