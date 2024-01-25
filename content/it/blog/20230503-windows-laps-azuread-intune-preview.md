---
date: 2023-05-03T05:00:00-00:00
description: "Con la release 2304 di Intune arriva Windows LAPS con il supporto diretto ad Entra ID, una funzionalità che in tantissimo stavano aspettando. Vediamo come implementarlo e come funziona."
featured_image: "/images/01-windows-laps-azuread-preview.png"
images:
  - "/images/01-windows-laps-azuread-preview.png"
categories : [ "Modern Endpoint", "Identity & Security" ]
tags: [ "LAPS", "Windows", "Entra", "Video" ]
title: "Windows LAPS in Entra ID (preview)"
url: /windows-laps-azuread-intune-preview
---
Ho provato il nuovo Windows LAPS (Local Administrator Password Solution) con supporto diretto ad Entra ID.

{{< youtube oGbAqOxJOhQ >}}

Se avete macchine Windows 11 (che lo supportano nativamente), è veramente semplice e veloce da implementare.

Ecco alcune informazioni utili:

📌 Nessun requisito di licenza, è disponibile da Entra ID Free in su  

📌 Sistemi operativi supportati:  
- Windows 11 22H2 - April 11 2023 Update
- Windows 11 21H2 - April 11 2023 Update
- Windows 10 20H2, 21H2 and 22H2 - April 11 2023 Update
- Windows Server 2022 - April 11 2023 Update
- Windows Server 2019 - April 11 2023 Update

Nel video, oltre a configurare il profilo Intune per riabilitare l'Administrator locale built-in, ho testato anche una situazione un po' più particolare, rinominando l'Administrator. È una buona pratica di hardening che mi è capitato spesso di trovare sul campo ed è molto semplice da configurare via Intune Settings Catalog.

Che dire, non vi resta che vedere il video per tutti gli altri dettagli 😉

E voi state già usando LAPS nella vostra infrastruttura? Parliamone insieme sui miei profili social!

Buona visione!

Riccardo
