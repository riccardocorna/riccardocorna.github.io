---
date: 2020-09-07T08:00:00-00:00
description: "Azure Migrate supporta le availability zone: finalmente tutte le funzionalità di resilienza di Azure anche per VM migrate con Azure Migrate."
featured_image: "/images/01-Azure-Migrate-supporta-le-availability-zone-AVZone.png"
categories: [ "Cloud Datacenter"]
tags: [ "Azure", "Availability Zones", "News" ]
title: "Azure Migrate supporta le Availability Zone"
url: "/azure-migrate-supporta-le-availability-zone"
---
Finalmente viene colmata una grande lacuna: Azure Migrate supporta le Availability Zone ed è finalmente possibile sfruttare tutte le funzionalità di resilienza di Azure anche per quelle VM e quei workload che vengono migrati in modalità lift & shift!

![Schema delle Availability Zones di Azure](/images/01-Azure-Migrate-supporta-le-availability-zone-AVZone.png)

Qualche mese fa sono stato coinvolto in un grande progetto di migrazione verso Azure, in cui erano coinvolti centinaia di server on-premises. Il cliente aveva espresso la volontà, per una buona parte di essi, di utilizzare lo strumento Azure Migrate, in modo da minimizzare l’effort di alcune attività pre e post migrazione.

Durante le fasi di progettazione della landing zone in cloud è però emerso che alcuni di questi workload avevano necessità di un livello di resilienza alto, ovvero di usare le availability zone. Con Azure Migrate, purtroppo, al tempo era possibile sfruttare solo gli availability set e quindi, per quei workload specifici, abbiamo optato per altre soluzioni.

Da oggi, finalmente, Azure Migrate supporta le Availability Zone, in modo da avere massima resilienza anche per quelle VM che vengono portate in cloud in modalità “lift & shift” con Azure Migrate!

Puoi trovare i dettagli nell’articolo dove viene dato l’annuncio:
- [Migrate to Azure Availability Zones](https://azure.microsoft.com/en-us/updates/migrate-to-azure-availability-zones/)

Ed ecco infine un po’ di documentazione:
- [What’s new in Azure Migrate](https://docs.microsoft.com/en-us/azure/migrate/whats-new)
- [Regions and Availability Zones in Azure](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview)

Usi abitualmente le Availability Zone di Azure per i tuoi workload? Se sì, con quali criteri? Ti aspetto nei commenti o sui miei profili social per parlarne.

Il tuo IT Specialist, Riccardo

