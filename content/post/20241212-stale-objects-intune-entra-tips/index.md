---
date: 2024-12-12T05:00:00-00:00
description: "Alcuni consigli, risorse e best practice su come approcciare i dispositivi obsoleti su Microsoft Intune ed Entra."
image: "01-entra-users-activity.png"
categories : [ "Security" ]
tags: [ "Intune", "Entra","Manutenzione", "Dispositivi" ]
title: "Dispositivi obsoleti su Microsoft Intune ed Entra: tips & tricks"
url: /stale-objects-intune-entra
---
Suggerimenti al volo per gestire i dispositivi inattivi/obsoleti in Microsoft Intune e Microsoft Entra. Pur sembrando banale, in questi mesi, sul campo ho percepito che la questione è molto sentita ma, al tempo stesso, sottovalutata e poco gestita.
Potrei farci un video ma, per intanto, ecco due dritte al volo.

1️⃣ **Intune** - Usate le [Device Cleanup Rules](https://learn.microsoft.com/en-us/mem/intune/remote-actions/devices-wipe#automatically-delete-devices-with-cleanup-rules)

2️⃣ **Entra** - Implementate un flusso di pulizia basato sull'[Activity del dispositivo (attributo ApproximateLastSignInDate)](https://learn.microsoft.com/en-us/entra/identity/devices/manage-stale-devices).

[![Dettaglio dell'ultima attività degli utenti su Microsoft Entra](01-entra-users-activity.png)](01-entra-users-activity.png)

3️⃣ Hybrid Entra Joined devices: implementate un flusso di pulizia su Active Directory on-premises. Cancellate i computer object inutilizzati oppure muoveteli al di fuori delle OU sincronizzate con Entra Connect. In questo modo il corrispettivo oggetto in cloud sparirà da Entra. Non vale il contrario.

E voi come approcciate la pulizia degli oggetti obsoleti su Intune ed Entra? Parliamone insieme sui miei profili social!

Il vostro IT Specialist,  
Riccardo