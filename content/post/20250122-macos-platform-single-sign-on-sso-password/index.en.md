---
date: 2025-01-22T05:00:00-00:00
description: "How to configure Platform Single Sign-On on macOS with Microsoft Entra and Intune. Quick guide on authentication methods, compliance policies, and useful tips for secure and integrated login."
image: "01-macos-platform-single-sign-on-sso-password.jpg"
categories: [ "Security", "Modern Work" ]
tags: [ "Microsoft Intune", "Intune", "macOS", "Platform SSO", "Single Sign-On", "Microsoft Entra", "Video", "Tutorial" ]
title: "macOS Platform SSO: Mac login with Microsoft Entra username and password"
url: /en/macos-platform-single-sign-om-sso-password
---
Hello everyone, IT specialists! Today we are talking about Platform Single Sign-On on macOS!

## Video
You can find the entire video below, or you can continue reading the article.

{{< youtube qtEkLFvppG8 >}}

## Login on macOS with Microsoft Entra account: Here is Platform SSO

### Introduction
What is Platform Single Sign-On? It is a feature that allows you to log in to your Mac with your Microsoft Entra credentials. Exactly, not just applications anymore: I'm talking about using Entra credentials on the Mac login screen.

### Supported Authentication Methods
There are several supported authentication methods, such as Secure Enclave, password, and smart card. For more details on each of these methods, I refer you to the documentation I always leave below.

- [Configure Platform SSO for macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/platform-sso-macos)

### Policy Configuration
Without further ado, today I will show you how to configure the Platform Single Sign-On policy in password authentication mode. We will also see the process of joining the Mac to Entra ID and finally a login experience with UPN and password.

Ready? Let's create the policy!

{{< youtubestartend qtEkLFvppG8 58 166 >}}

Here are the values I used to set the configuration profile.

- **Screen Locked Behavior**: Do Not Handle
- **Registration Token**: {{DEVICEREGISTRATION}}
- **Platform SSO**
  - **Authentication Method**: UserSecureEnclaveKey
  - **Enable Authorization**: Enabled
  - **Enable Create User At Login**: Enabled
  - **New User Authorization Mode**: Admin
  - **Token To User Mapping**
    - **Account Name**: preferred_username
    - **Full Name**: name
  - **Use Shared Device Keys**: Enabled
  - **User Authorization Mode**: Admin
- **Team Identifier**: UBF8T346G9
- **Extension Identifier**: com.microsoft.CompanyPortalMac.ssoextension
- **Type**: Redirect
- **URLs**
  - https://login.microsoftonline.com
  - https://login.microsoft.com
  - https://sts.windows.net
  - https://login.partner.microsoftonline.cn
  - https://login.chinacloudapi.cn
  - https://login.microsoftonline.us
  - https://login-us.microsoftonline.com

### Joining the Mac to Entra
The policy has been created and assigned. Now we just have to wait for it to be received by the Mac and then join it to Entra ID.

{{< youtubestartend qtEkLFvppG8 173 211 >}}

Perfect! Joined! Now let's see if everything went well by doing a couple of checks on the Mac.

{{< youtubestartend qtEkLFvppG8 217 228 >}}

### Authentication Test with UPN and Password
Okay, we've come this far, why not do an authentication test on the Mac login screen with UPN and password? Let's do it! Done! That's it! Now we can finally log in to the Mac with our Microsoft Entra credentials.

{{< youtubestartend qtEkLFvppG8 236 254 >}}

### Useful Tips
Quick tip: if you implement password authentication mode on Intune and are using compliance policies that enforce the complexity of the local password on the Mac, get rid of this setting because it clashes quite a bit with Platform Single Sign-On. So let the password policy of Microsoft Entra or your Active Directory take control of the password complexity.

Another quick tip: if you are using the Enterprise Single Sign-On plugin, which allowed you to do SSO authentication on applications, unassign this policy. Platform Single Sign-On completely replaces Enterprise Single Sign-On and having both policies can lead to conflicts, indeed it definitely leads to conflicts.

### Conclusion
We are at the end of this video. Thank you for following me this far. Have you already implemented Platform Single Sign-On? Tell me about your experience in the video comments or on my social profiles.

As always, I invite you to subscribe to my YouTube channel and press the bell. This allows you not to miss any content and for me, it is a great help to grow the channel. Thanks again!

See you soon... LEGENDS!

Your IT Specialist,  
Riccardo