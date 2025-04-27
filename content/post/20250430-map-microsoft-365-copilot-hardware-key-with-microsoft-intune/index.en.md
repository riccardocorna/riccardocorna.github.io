---
date: 2025-04-30T05:00:00-00:00
description: "Simplify the user experience of Microsoft 365 Copilot using Microsoft Intune policies to map the physical Copilot key on newer PCs"
image: "01-map-m365-copilot-key-with-microsoft-intune.jpg"
categories : [ "Modern Work"]
tags: [ "Microsoft 365 Copilot Chat", "Microsoft Intune", "Copilot", "Video", "Tutorial", "Cloud Endpoint Diary"]
title: "Launch Microsoft 365 Copilot with a Single Key Mapped via Microsoft Intune"
url: /en/map-microsoft-365-copilot-hardware-key-with-microsoft-intune
---
Hello everyone, IT specialists! In this article, we continue our mini-series on how to simplify the user experience of Microsoft 365 Copilot and Microsoft 365 Copilot Chat using Microsoft Intune policies. Today, we'll see how to map the physical Copilot key on newer PCs to launch the app with a single key press.

## Video
You can find the entire video below, or you can continue reading the article.

{{< youtube afa98hkVrn4 >}}

## Mapping the Physical Copilot Key

Today, we focus on mapping the physical Copilot key, present on newer PCs. This key allows you to launch the Microsoft 365 Copilot app with a single touch, further simplifying the user experience. To achieve this, we use a custom OMA-URI from Microsoft Intune.

Let's see how to create the policy and distribute this setting.

### Creating a Custom OMA-URI
Creating a custom OMA-URI is a simple and quick process: the specific details of the OMA-URI used are available below, right after the video snippet.

{{< youtubestartend afa98hkVrn4 78 133 >}}

```
➡️ Name: SetCopilotHardwareKey
➡️ OMA-URI: ./User/Vendor/MSFT/Policy/Config/WindowsAI/SetCopilotHardwareKey
➡️ Data type: String
➡️ Value: Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe!Microsoft.MicrosoftOfficeHub
```

### Verifying Policy Reception
Let's see what happens on the Windows client in the personalization panel.

{{< youtubestartend afa98hkVrn4 143 157 >}}

### Testing the Copilot Key
It's time to press the key to see if everything works!

{{< youtubestartend afa98hkVrn4 166 172 >}}

Perfect, everything works! 😊

## Attached Documentation
As always, here is some useful documentation:

📌 [SetCopilotHardwareKey](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsai#setcopilothardwarekey)    
📌 [How to find the AUMID](https://learn.microsoft.com/en-us/windows/configuration/store/find-aumid?tabs=ps%2Cexplorer&pivots=windows-11)  

## Conclusion
Thank you for following this article to the end! Implementing these policies is an effective way to streamline the user experience of Microsoft 365 Copilot. If you already have PCs with the physical Copilot key in your fleet, this policy is simple to implement and offers great benefits.

Let me know what you think in the video comments or on my social profiles!

See you soon, legends!

Your IT Specialist,  
Riccardo