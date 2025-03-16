---
date: 2025-03-19T05:00:00-00:00
description: "Tutorial essenziale su Intune Endpoint Privilege Management:scopri come fare in modo che gli utenti standard possano lanciare eseguibili con privilegi amministrativi, in sicurezza. 🚀"
image: "01-microsoft-intune-endpoint-privilege-management.jpg"
categories : [ "Modern Work", "Security" ]
tags: [ "Microsoft Intune", "EPM", "Endpoint Privilege Management", "Video", "Guida"]
title: "Microsoft Intune Endpoint Privilege Management"
url: /microsoft-intune-endpoint-privilege-management
---
Ciao a tutti, specialisti IT! 👋 Oggi vediamo insieme una funzionalità molto interessante di Microsoft Intune: **Endpoint Privilege Management (EPM)**. 

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube 1CT2xqCQrns >}}

## Cos'è l'Endpoint Privilege Management?
L'Endpoint Privilege Management è una funzionalità della Intune Suite che consente agli utenti non amministrativi di eseguire attività con privilegi elevati, come l'esecuzione di file .exe, .msi e .ps1. In altre parole, permette l'installazione e l'esecuzione di software e script senza richiedere una password amministrativa.

## How to: implementazione di EPM

### Creazione delle Policy di Elevation Settings
Per attivare la funzionalità di EPM, è necessario creare una policy di **elevation settings**. Questa policy serve per risvegliare la funzionalità all'interno del client Windows e stabilire la baseline di default in caso di elevazione.
In questo video, a titolo esemplificativo,ho creato una policy che nega tutte le richieste di elevazione.

{{< youtubestartend 1CT2xqCQrns 69 101 >}}

Vediamo se è effettivamente così!

{{< youtubestartend 1CT2xqCQrns 112 123 >}}

Perfetto, funziona! Ora creiamo la prima Elevation Rule.

### Creazione e gestione delle Elevation Rules

Le **elevation rules** servono a stabilire il comportamento di una specifica richiesta di elevazione, intercettando file specifici tramite nome, hash o altri parametri. Queste regole possono richiedere un flusso approvativo o essere eseguite automaticamente.

#### Esempio di elevation rule con approvazione
Creiamo un'elevation rule con approvazione.

{{< youtubestartend 1CT2xqCQrns 156 187 >}}

Ok, ora andiamo a verificare sul client cosa succede se proviamo ad installare 7-Zip.

{{< youtubestartend 1CT2xqCQrns 193 212 >}}

Visto? È richiesta un'approvazione da parte dell'amministratore di sistema. La richiesta di elevazione può essere approvata direttamente sul portale di Intune.

{{< youtubestartend 1CT2xqCQrns 221 239 >}}

Torniamo sulla nostra macchina Windows per vedere se ora l'utente riesce ad installare 7-Zip.

{{< youtubestartend 1CT2xqCQrns 244 259 >}}

Perfetto, funziona tutto! 😊

#### Esempio di Elevation Rule automatica
Proviamo ora a creare un'elevation rule automatica ovvero che non richiede nessun flusso approvativo per l'esecuzione del file. Un caso d'uso tipico per questa situazione potrebbe essere un software aziendale sviluppato internamente.

Vediamo come creare la regola per questa situazione.

{{< youtubestartend 1CT2xqCQrns 283 313 >}}

Regola creata! Andiamo a vedere ora cosa succede sul client Windows.

{{< youtubestartend 1CT2xqCQrns 316 325 >}}

Visto? Tutto liscio al primo colpo senza nessun messaggio o interazione ulteriore.

### Strategie per la Gestione delle Versioni dei Software
Se cambia la versione dell'installer di un software, è necessario ricalcolare l'hash o recuperarlo dal portale di Intune nel report delle elevazioni. Con quelli si può creare una nuova policy. Tuttavia, esistono tecniche per intercettare tutti i software di un certo publisher utilizzando i **reusable settings**. Questi settings permettono di associare diverse policy senza dover creare nuove regole ogni volta.

## Documentazione allegata
Come sempre, ecco il paccone di documentazione per i vostri approfondimenti.

📌 [Use Endpoint Privilege Management with Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-overview)  
📌 [Guidance for creating elevation rules with Endpoint Privilege Management](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-guidance-for-creating-rules)  
📌 [Configure policies for Endpoint Privilege Management](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-policies)  
📌 [Deployment Considerations and frequently asked questions for Endpoint Privilege Management](https://learn.microsoft.com/en-us/mem/intune-service/protect/epm-deployment-considerations-ki)

## Conclusione

L'Endpoint Privilege Management di Microsoft Intune offre un modo efficace per gestire i privilegi degli utenti standard, consentendo loro di eseguire attività con privilegi elevati in modo controllato. Se volete approfondire ulteriormente, lasciate un commento e iscrivetevi al mio canale YouTube per non perdere i prossimi video! 📚🔔  
Grazie!


Il vostro IT Specialist,  
Riccardo