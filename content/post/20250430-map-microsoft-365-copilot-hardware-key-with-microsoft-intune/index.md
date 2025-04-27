---
date: 2025-04-30T05:00:00-00:00
description: "Semplificate l'esperienza utente di Microsoft 365 Copilot utilizzando le policy di Microsoft Intune per mappare il tasto fisico Copilot sui PC più recenti"
image: "01-map-m365-copilot-key-with-microsoft-intune.jpg"
categories : [ "Modern Work"]
tags: [ "Microsoft 365 Copilot Chat", "Microsoft Intune", "Copilot", "Video", "Guida", "Cloud Endpoint Diary"]
title: "Lanciare Microsoft 365 Copilot con un solo tasto mappato via Microsoft Intune"
url: /map-microsoft-365-copilot-hardware-key-with-microsoft-intune
---
Ciao a tutti, specialisti IT! In questo articolo, continuiamo la nostra mini serie su come semplificare l'esperienza utente di Microsoft 365 Copilot e Microsoft 365 Copilot Chat utilizzando le policy di Microsoft Intune. Oggi vedremo come mappare il tasto fisico Copilot sui PC più recenti per lanciare l'app con un solo tasto.

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube afa98hkVrn4 >}}

## Mappatura del Tasto Fisico Copilot

Oggi ci concentriamo sulla mappatura del tasto fisico Copilot, presente sui PC più recenti. Questo tasto permette di lanciare l'app Microsoft 365 Copilot con un solo tocco, semplificando ulteriormente l'esperienza utente. Per ottenere questo risultato, utilizziamo un OMA-URI custom di Microsoft Intune.

Vediamo subito come creare la policy e distribuire questa impostazione.

### Creazione di un OMA-URI Custom
La creazione di un OMA-URI custom è un processo semplice e veloce: i dettagli specifici dell'OMA-URI utilizzato sono disponibili qui sotto, subito dopo lo spezzone di video.

{{< youtubestartend afa98hkVrn4 78 133 >}}


```
➡️ Name: SetCopilotHardwareKey
➡️ OMA-URI: ./User/Vendor/MSFT/Policy/Config/WindowsAI/SetCopilotHardwareKey
➡️ Data type: String
➡️ Value: Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe!Microsoft.MicrosoftOfficeHub

```
### Verifica del recepimento della policy
Vediamo cosa succede sul client Windows nel pannello delle personalizzazioni.

{{< youtubestartend afa98hkVrn4 143 157 >}}

### Test con il tasto Copilot
È arrivato il momento di premere il tasto per vedere se tutto funziona!

{{< youtubestartend afa98hkVrn4 166 172 >}}

Perfetto, funziona tutto! 😊

## Documentazione allegata
Come sempre, ecco un po' di documentazione utile:

📌 [SetCopilotHardwareKey](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsai#setcopilothardwarekey)    
📌 [How to find the AUMID](https://learn.microsoft.com/en-us/windows/configuration/store/find-aumid?tabs=ps%2Cexplorer&pivots=windows-11)  

## Conclusione
Grazie per aver seguito anche questo articolo fino alla fine! Implementare queste policy è un modo efficace per fluidificare l'esperienza utente di Microsoft 365 Copilot. Se avete già dei PC con il tasto fisico Copilot nel vostro parco macchine, questa policy è semplice da implementare e offre grandi benefici.

Fatemi sapere cosa ne pensate nei commenti del videoo sui miei profili social!

A presto, mitici!

Il vostro IT Specialist,  
Riccardo