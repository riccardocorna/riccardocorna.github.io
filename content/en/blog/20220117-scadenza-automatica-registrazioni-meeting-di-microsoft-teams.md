---
date: 2022-01-17T08:00:00-00:00
description: "New feature: Automatic expiration has been introduced for Microsoft Teams meeting recordings."
featured_image: "/images/01-microsoft-teams-meeting-recording-expiration.jpg"
categories: [ "Altro" ]
tags: [ "Microsoft Teams", "Microsoft 365"]
title: "Automatic Expiration of Microsoft Teams Meeting Recordings"
url: "/en/automatic-expiration-teams-meeting-recordings"
---
How many times have you been asked to record a meeting because "you never know" or because "I want to review it later"? 🙋🏻‍♂️ Well, 99% of the recordings in Microsoft Teams are never viewed within 60 days after the meeting. It's a waste of space and, potentially, a security issue if the recording contains sensitive information that is consciously or inadvertently shared.

Finally, the ability to set an expiration date for recorded videos has been introduced! How can you manage and configure it?

From the [Teams administration portal](https://admin.teams.microsoft.com/), simply navigate to:

- **Meetings** -> **Meeting policies**
From here, you can create or modify the policy by adjusting the settings in the Recording & Transcription section:
- enable **Meetings automatically expire**.
- set the preferred number of days within a range of 1 to 99,999 (273 years) in the **Default expiration time** field (the default value is 60).

Da qui è possibile creare o modificare la policy andando ad agire sui settaggi della sezione **Recording & Transcription**:
- attivando **Meetings automatically expire**;
- impostando il numero di giorni che preferisci in un range di valori tra 1 e 99.999 (273 anni) alla voce **Default expiration time** (il valore di default è 60).

![Automatic expiration Teams meeting recordings](/images/01-microsoft-teams-meeting-recording-expiration.jpg)

Some considerations:
- These settings can also be modified using PowerShell.
- This new setting does not affect videos that were automatically saved in Stream until some time ago, but only videos automatically created by Teams in OneDrive.
- Recordings created before the deployment of this new feature (January 2022) are not affected.
- If a recording reaches its expiration and gets deleted, an email is sent to the user, and if necessary, the tenant or SharePoint site administrator has 90 days to recover it.


For further information and all the details you need, as always, I have gathered a bunch of fresh documentation just for you 😉:
- [How to Manage Microsoft Teams Meeting Recording Auto-Expiration – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/how-to-manage-microsoft-teams-meeting-recording-auto-expiration/ba-p/3053035)
- [Meeting policies and meeting expiration in Microsoft Teams – Microsoft Teams | Microsoft Docs](https://docs.microsoft.com/en-gb/MicrosoftTeams/meeting-expiration)
- [End user expiration override controls](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24)
- [Record a meeting in Teams (microsoft.com)](https://support.microsoft.com/en-us/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24#bkmk_view_change_expiration_date)

What do you think about this new feature? I'm waiting for you on my social profiles to discuss it!

Your IT Specialist, Riccardo