---
date: 2022-07-11T09:00:00-00:00
description: "Con Microsoft Defender for Endpoint Troubleshooting Mode risulta più semplice verificare ed eventualmente modificare alcune configurazioni."
featured_image: "/images/MDE-TroubleshootingMode.jpg"
categories: [ "Identity & Security" ]
tags: [ "Microsoft Defender for Endpoint", "Guida" ]
title: "Microsoft Defender for Endpoint Troubleshooting mode"
url: "/microsoft-defender-for-endpoint-troubleshooting-mode"
---
A volte, quando si implementano delle policy di Microsoft Defender for Endpoint in un nuovo ambiente, è necessario fare un po’ di affinamenti vari alle configurazioni. Può però non essere comodo ed immediato “sottrarre” un dispositivo ad una policy per fare l’opportuno troubleshooting di cosa non stia funzionando.

![Microsoft Defender for Endpoint Troubleshooting Mode](/images/MDE-TroubleshootingMode.jpg)

Esiste una funzionalità, chiamata Troubleshooting Mode, che ti viene incontro proprio in questo: attivandola da portale per un singolo dispositivo, consentirà per 3 ore all’amministratore locale di macchina di fare override a tutte le policy MDE impostate, tamper protection compresa.

Risulta quindi molto utile per:
- fare verifiche funzionali sull’agente di Microsoft Defender for Endpoint installato sul dispositivo
- testare localmente una modifica delle configurazioni gestite dalle policy MDE, per verificare se sia lì il problema
- avere dati diagnostici aggiuntivi (disponibili alla fine del periodo di troubleshooting) ed avanzati

Al termine delle 3 ore, tutto viene riportato sotto policy, override e configurazioni comprese. Insomma, molto utile e pratico per effettuare verifiche che, altrimenti, dovrebbero essere fatte mettendo il dispositivo fuori policy o che, in ogni caso, sarebbero più complesse da fare.

Se vuoi approfondire requisiti e best practice, come sempre, ecco un po’ di documentazione da leggere come un saggio, sotto l’ombrellone o in un prato di montagna: 🤣
- ➡️ [Troubleshooting mode for Microsoft Defender for Endpoint now Generally Available – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/troubleshooting-mode-for-microsoft-defender-for-endpoint-now/ba-p/3347344)
- ➡️ [Get started with troubleshooting mode in Microsoft Defender for Endpoint | Microsoft Docs](https://docs.microsoft.com/en-gb/microsoft-365/security/defender-endpoint/enable-troubleshooting-mode?view=o365-worldwide)
- ➡️ [Troubleshooting mode scenarios in Microsoft Defender for Endpoint | Microsoft Docs](https://docs.microsoft.com/en-gb/microsoft-365/security/defender-endpoint/troubleshooting-mode-scenarios?view=o365-worldwide)

Hai mai usato questa modalità? Se sì, l’hai trovata utile? Parliamone insieme nei commenti!

Il tuo IT Specialist,Riccardo