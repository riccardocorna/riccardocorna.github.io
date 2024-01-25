---
date: 2023-05-03T05:00:00-00:00
description: "With the release 2304 of Intune, Windows LAPS arrives with direct support for Entra ID, a highly anticipated feature. Let's see how to implement it and how it works."
featured_image: "/images/01-windows-laps-azuread-preview.png"
images:
  - "/images/01-windows-laps-azuread-preview.png"
categories : [ "Modern Endpoint" ]
tags: [ "LAPS", "Windows", "Entra", "Video" ]
title: "Windows LAPS in Entra ID (preview)"
url: /en/windows-laps-azuread-intune-preview
---
I have tried the new Windows LAPS (Local Administrator Password Solution) with direct support for Entra ID.

{{< youtube oGbAqOxJOhQ >}}

If you have Windows 11 machines (which natively support it), it is really simple and fast to implement.

Here are some useful information:

📌 No licensing requirement, available from Entra ID Free and above

📌 Supported operating systems:
- Windows 11 22H2 - April 11, 2023 Update
- Windows 11 21H2 - April 11, 2023 Update
- Windows 10 20H2, 21H2, and 22H2 - April 11, 2023 Update
- Windows Server 2022 - April 11, 2023 Update
- Windows Server 2019 - April 11, 2023 Update

In the video, besides configuring the Intune profile to re-enable the built-in local Administrator, I also tested a slightly more specific scenario by renaming the Administrator. It is a good hardening practice that I have often encountered in the field, and it is very easy to configure via Intune Settings Catalog.

What can I say, you just have to watch the video for all the other details 😉

Are you already using LAPS in your infrastructure? Let's discuss it together on my social profiles!

Enjoy watching!

Riccardo