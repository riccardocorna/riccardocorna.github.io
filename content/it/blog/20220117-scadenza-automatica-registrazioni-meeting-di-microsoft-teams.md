---
date: 2022-01-17T08:00:00-00:00
description: "Nuova funzionalità: è stata introdotta la scadenza automatica per le registrazioni dei meeting di Microsoft Teams."
featured_image: "/images/01-microsoft-teams-meeting-recording-expiration.jpg"
categories: [ "Altro" ]
tags: [ "Microsoft Teams", "Microsoft 365"]
title: "Scadenza automatica registrazioni meeting di Microsoft Teams"
url: "/scadenza-automatica-registrazioni-meeting-di-microsoft-teams"
---
Quante volte ti hanno chiesto di registrare un meeting, perché “non si sa mai” oppure perché “così lo riguardo con calma?”. 🙋🏻‍♂️ Ebbene, il 99% delle registrazioni su Microsoft Teams non viene mai visualizzato nei 60 giorni successivi al meeting. Uno spreco di spazio e, potenzialmente, un problema di sicurezza, nel caso in cui la registrazione contenga dei frammenti dove vengono (consciamente o meno) condivisi dettagli sensibili.

Finalmente è stata introdotta la possibilità di impostare una data di scadenza per i video registrati! Come fare per gestirla e configurarla?

Da [portale di amministrazione di Teams](https://admin.teams.microsoft.com/), è sufficiente navigare i menu fino a:
- **Meetings** –> **Meeting policies**

Da qui è possibile creare o modificare la policy andando ad agire sui settaggi della sezione **Recording & Transcription**:
- attivando **Meetings automatically expire**;
- impostando il numero di giorni che preferisci in un range di valori tra 1 e 99.999 (273 anni) alla voce **Default expiration time** (il valore di default è 60).

![Scadenza automatica registrazioni dei meeting di Microsoft Teams](/images/01-microsoft-teams-meeting-recording-expiration.jpg)

Alcune considerazioni:
- è possibile modificare queste impostazioni anche da PowerShell;
- questa nuova impostazione non impatta i video che venivano automaticamente salvati in Stream fino a qualche tempo fa ma solo i video creati automaticamente da Teams su OneDrive;
- non sono impattate le registrazioni create prima della distribuzione di questa nuova funzionalità (gennaio 2022);
- se la registrazione giunge a scadenza e viene cancellata, arriva una mail all’utente e, in caso di necessità, l’amministratore del tenant o del sito SharePoint ha 90 giorni per recuperarla.

Per ulteriori approfondimenti e per tutti i dettagli del caso, come sempre, ho raccolto per te il solito malloppo di documentazione, fresco fresco e pronto all’uso 😉:
- [How to Manage Microsoft Teams Meeting Recording Auto-Expiration – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/how-to-manage-microsoft-teams-meeting-recording-auto-expiration/ba-p/3053035)
- [Meeting policies and meeting expiration in Microsoft Teams – Microsoft Teams | Microsoft Docs](https://docs.microsoft.com/en-gb/MicrosoftTeams/meeting-expiration)
- [End user expiration override controls](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24)
- [Record a meeting in Teams (microsoft.com)](https://support.microsoft.com/en-us/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24#bkmk_view_change_expiration_date)

E tu che ne pensi di questa nuova funzionalità? Ti aspetto sui miei profili social per parlarne!

Il tuo IT Specialist, Riccardo