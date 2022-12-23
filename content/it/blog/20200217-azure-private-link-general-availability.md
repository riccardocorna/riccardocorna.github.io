---
date: 2020-02-17T08:00:00-00:00
description: "Con Azure Private Link finalmente puoi rendere disponibili alla virtual network degli endpoint PaaS senza doverli esporli pubblicamente."
featured_image: "/images/01-Azure-Private-Link-Diagram.png"
categories: [ "Cloud Datacenter"]
tags: [ "Azure", "Private Link" ]
title: "Azure Private Link è in general availability"
url: "/azure-private-link-general-availability"
---
Questa mattina, appena ho consultato i feed RSS dove mi aggiorno con [le ultime notizie dal mondo Microsoft](/rubrica-risorse-utili-microsoft/), ho fatto un salto sulla sedia: Azure Private Link è finalmente disponibile!

![Azure Private Link diagramma](/images/01-Azure-Private-Link-Diagram.png)

## Cos’è Private Link?
[Azure Private Link](/glossario-azure#PrivateLink) è un modo per connettersi ed utilizzare servizi PaaS di Azure (e non solo) in maniera privata, rimanendo all’interno della propria virtual network. I servizi Azure compatibili (ad esempio Azure Storage, Azure Cosmos DB, Azure SQL Database) saranno quindi disponibili come endpoint privati.

## Principali vantaggi di Private Link
I vantaggi di questo nuovo servizio:
- semplificazione dell’architettura di rete;
- gli endpoint sono raggiungibili anche da reti on-premises;
- non è più obbligatorio esporre gli endpoint su Internet con indirizzi pubblici e il traffico rimane all’interno del backbone Microsoft;
- in caso di problemi è un efficace metodo per evitare l’esfiltrazione di dati verso Internet dalle risorse Azure.

## Link utili
Se vuoi approfondire le caratteristiche di questo nuovo servizio, i prezzi e altri dettagli, ecco alcuni link utili:
- [Azure Private Link is now generally available](https://azure.microsoft.com/en-us/updates/private-link-now-available-in-ga/)
- [Private Link Documentation](https://docs.microsoft.com/en-us/azure/private-link/)
- [Prezzi](https://azure.microsoft.com/en-us/pricing/details/private-link/)
- [Mappa dei servizi Private Link e regioni dove sono disponibili](https://docs.microsoft.com/en-us/azure/private-link/private-link-overview#availability)

Come sempre, spero di averti dato informazioni utili per il tuo ambiente cloud. Se questo articolo ti è piaciuto, condividilo sui tuoi social network preferiti! Buon approfondimento! 😉

Riccardo