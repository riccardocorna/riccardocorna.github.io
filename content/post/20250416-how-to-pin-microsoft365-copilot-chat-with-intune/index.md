---
date: 2025-04-16T05:00:00-00:00
description: "Tutorial su come controllare il pinning di Microsoft 365 Copilot Chat attraverso Microsoft Intune in maniera graduale e controllata."
image: ""
categories : [ "Modern Work"]
tags: [ "Microsoft 365 Copilot Chat", "Microsoft Intune", "Copilot", "Video", "Guida", "Cloud Endpoint Diary"]
title: "Come controllare il pinning di Microsoft 365 Copilot Chat con Intune"
url: /pinning-microsoft-365-copilot-chat-intune
---
Ciao a tutti, specialisti IT! Oggi parliamo di un argomento caldissimo: **Microsoft 365 Copilot Chat** e di come possiamo controllarne la distribuzione attraverso **Microsoft Intune**. Questo articolo sarà un approfondimento, quindi preparatevi a una lettura più lunga del solito. Valeva la pena spiegare tutto in maniera più strutturata, perché interessa praticamente chiunque abbia una licenza Microsoft 365.

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube 4l9LOnKgV6k >}}

## Cos'è Microsoft 365 Copilot Chat?

Microsoft 365 Copilot Chat è un nuovo livello di offerta degli strumenti di Copilot, che mette a disposizione la chat all'interno dei principali piani di licenza di Microsoft 365. Oltre alla chat, ci sono altre funzionalità come gli agenti in modalità pay-as-you-go. Per dettagli sui piani di licenza in cui Copilot Chat è inclusa e per una panoramica delle differenze rispetto a un piano licenza di Copilot canonico, vi lascio alcuni link che troverete in fondo a questo articolo

➡️ [Documentazione allegata](#documentazione-allegata)

## Utilizzare Microsoft Intune per il Pinning di Copilot Chat

Il focus di questo articolo è come utilizzare Microsoft Intune per gestire il pinning di Microsoft 365 Copilot Chat sulla navigation bar e sulla taskbar di Windows, il tutto in maniera graduale e controllata. Il pinning è abilitato di default per chi ha una licenza Copilot vera e propria. Ma cosa intendiamo per pinning? Si tratta dell'azione di puntare l'icona di Microsoft 365 Copilot sulla barra di navigazione del portale e sulla taskbar di Windows.

## Configurazione della Policy di Intune

Per fare il pinning sulla taskbar di Windows, serve configurare una policy di Intune. Prima di tutto, dobbiamo recuperare l'identificativo dell'app con un semplice comando PowerShell.

{{< youtubestartend 4l9LOnKgV6k 266 274 >}}

Una volta ottenuto l'identificativo, possiamo creare la policy per pinnare l'icona sulla taskbar.

{{< youtubestartend 4l9LOnKgV6k 280 325 >}}

Dopo aver creato la policy, vediamo il risultato: l'icona è puntata sulla taskbar, portando a casa la prima parte di pinning. Notate come, invece, non è ancora pinnata alla taskbar: vedremo tra poco come fare!

{{< youtubestartend 4l9LOnKgV6k 336 348 >}}

## Gestione del Pinning sulla Navigation Bar

Ora vediamo come gestire il pinning sulla navigation bar. Useremo delle app policy specifiche, ma prima vediamo la policy globale a livello di tenant e cosa succede quando la salviamo nel portale amministrativo di Microsoft 365. In questo caso, ho disabilitato globalmente il pinning per distribuirlo gradualmente.

{{< youtubestartend 4l9LOnKgV6k 371 384 >}}

Visto? Salvando l'impostazione dal pannello amministrativo di Microsoft 365, si è generata una policy tenant-wide: vediamo come è fatta.

{{< youtubestartend 4l9LOnKgV6k 398 418 >}}

Quindi, una volta generata questa policy che disabilita il pinning per tutti, possiamo creare una policy che abilita il pinning per un gruppo specifico di utenti, da popolare gradualmente.

{{< youtubestartend 4l9LOnKgV6k 433 489 >}}

Attenzione però: per fare in modo che la nostra policy specifica vinca su quella che disabilita tutto, dobbiamo fare una piccola inversione di preiorità: vediamo come.

{{< youtubestartend 4l9LOnKgV6k 506 524 >}}

Perfetto, ci siamo: vediamo cosa è successo sul nostro client Windows!

{{< youtubestartend 4l9LOnKgV6k 535 545 >}}

Anche la Navigation Bar è stata pinnata! 🥳

## Documentazione allegata
Ecco tutta la documentazione a cui faccio riferimento durante il video.

### Tabella delle differenze tra Microsoft 365 Copilot Chat e Microsoft Copilot
![Tabella delle differenze tra Microsoft 365 Copilot Chat e Microsoft Copilot](https://www.microsoft.com/en-us/microsoft-365/blog/wp-content/uploads/sites/2/2025/01/Copilot-Licensing-Blog-Image-3600px-scaled.jpg)

### Altra documentazione utile
📌 [Manage Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/copilot/manage)  
📌 [Configure the applications pinned to the taskbar](https://learn.microsoft.com/en-us/windows/configuration/taskbar/pinned-apps?tabs=intune&pivots=windows-11)  
📌 [Find the Application User Model ID of an installed app](https://learn.microsoft.com/en-us/windows/configuration/store/find-aumid?tabs=ps%2Cexplorer&pivots=windows-11)  
📌 [Policies to manage the Copilot key](https://learn.microsoft.com/en-us/windows/client-management/manage-windows-copilot#policies-to-manage-the-copilot-key)

## Conclusione

{{< rawhtml >}}
<div class="old-article-warning" style="background-color:#ffbe3b;border:1px solid #fbc02d;padding:15px;margin:20px 0;border-radius:5px;color:#333;font-weight:700"><p>🚨 ATTENZIONE: distribuzione della policy di pin sulla navigation bar gestita in questo modo è adatta solo per una fase iniziale, un POC. Una volta validata l'esperienza, compreso come funziona la Copilot Chat e prodotto il materiale di comunicazione e formazione per gli utenti, il consiglio è quello di abilitare il pinning per tutti dall'admin panel di M365!</p></div>
{{</ rawhtml >}}

In questo modo, riusciamo a distribuire gradualmente Copilot Chat. L'idea potrebbe essere di creare un calendario di attivazione in cui abilitare batterie di utenti per un POC, affiancando il tutto a una campagna di informazione e educazione sull'utilizzo dello strumento.

Possiamo fare altro su Copilot con queste policy? Sì, con altre app policy o con il settings catalog per le impostazioni di Edge: ad esempio, possiamo anche scegliere come mappare il tasto fisico sui CopilotPC+ attraverso Intune.  
E voi, a che punto siete con la distribuzione di Microsoft 365 Copilot Chat? Parliamone insieme nei commenti.

Grazie per aver seguito il mio articolo fino alla fine. Per nuovi contenuti, vi aspetto sul mio blog itspecialist.cloud. A presto... mitici!

Il vostro IT Specialist,  
Riccardo