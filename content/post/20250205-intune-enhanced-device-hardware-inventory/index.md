---
date: 2025-02-05T05:00:00-00:00
description: "Scopri come raccogliere dati hardware dettagliati sui dispositivi con Intune e la nuova funzionalità Enhanced Device Hardware Inventory. Ottieni report in 24 ore!"
image: "01-enhanced-device-hardware-inventory-cover.jpg"
categories : [ "Modern Work" ]
tags: [ "Enhanced Device Hardware Inventory", "Properties Catalog", "Microsoft Intune", "Intune", "Video", "Guida" ]
title: "Intune Enhanced Device Hardware Inventory"
url: /intune-enhanced-device-hardware-inventory
---
Specialisti IT! Ciao a tutti! Qualche cliente mi ha fatto più di una volta questa domanda:

> *"Con Intune è possibile raccogliere le proprietà e i dati hardware dai dispositivi? Magari da più dispositivi, tutti o un gruppo?!*

Fino a poco tempo fa non era possibile fare questo in maniera nativa su Intune ma, da dicembre 2024, si può fare! Come? Con una nuova funzionalità chiamata **Enhanced Device Hardware Inventory**!

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube z3S3hANsFHE >}}

## Intune Enhanced Device Hardware Inventory

### Introduzione
Per "dati hardware" intendo, ad esempio, presenza o meno del chip TPM, versione, oppure, per i laptop, quanti cicli di carica ha fatto la batteria. Potrebbero essere dati sul disco, sulla RAM, insomma tutte le proprietà hardware!

Fino a poco tempo fa non era possibile fare questo in maniera nativa su Intune ma, da dicembre 2024, si può fare!

Bando alle ciance, vediamo subito come farlo con un esempio concreto. 
Raccogliamo informazioni sul chip TPM delle macchine: se è presente o meno sul PC, versione, produttore, eccetera eccetera.

### Policy Properties Catalog
Creiamo la policy, usando il nuovissimo Properties Catalog, impostiamola e assegniamola!

{{< youtubestartend z3S3hANsFHE 71 107 >}}

### Visualizzazione dell'hardware inventory raccolto
Perfetto, dopo circa 24 ore dalla prima impostazione della policy, vedremo i risultati nei report!

{{< youtubestartend z3S3hANsFHE 114 130 >}}

## Documentazione allegata
Ecco i link alla documentazione ufficiale di queste funzionalità.

📃 [Enhanced hardware inventory in Intune](https://techcommunity.microsoft.com/blog/microsoftintuneblog/enhanced-hardware-inventory-in-intune-coming-in-december/4303744)  
📃 [Properties catalog in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/properties-catalog)

### Conclusioni
Ora è davvero molto più facile raccogliere informazioni hardware sul proprio parco macchine.  
Chiaramente ci sono alcuni requisiti che i dispositivi devono avere, in termini di sistemi operativi e tipologia di enrollment/gestione su Intune: vi ho lasciato tutto il necessario per approfondire, qui sotto in descrizione!

Avete già usato questa funzionalità? Pensate vi sarà utile? Parliamone insieme nei commenti o sui miei profili social!

Grazie per aver seguito questo video: vi aspetto, come sempre, su Linkedin, sul blog e su questo canale YouTube: iscrivetevi!
A presto... MITICI!

Il vostro IT Specialist,  
Riccardo
