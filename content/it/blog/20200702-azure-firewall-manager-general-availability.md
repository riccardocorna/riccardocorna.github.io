---
date: 2020-07-02T08:00:00-00:00
description: "Azure Firewall Manager, servizio di gestione delle policy di sicurezza e delle rotte per perimetri cloud-based, è in General Availability"
featured_image: "/images/01-Azure-Firewall-MAnager-GA.png"
categories: [ "Cloud Datacenter"]
tags: [ "Azure", "Azure Firewall", "News" ]
title: "Azure Firewall Manager è in general availability"
url: "/azure-firewall-manager-general-availability"
---
Azure Firewall, quando è stato implementato tempo fa, ha aiutato molto a raggiungere un livello di gestione più granulare delle reti cloud-based in Azure. Mancava però uno strumento di gestione che ne rendesse migliore l’esperienza di gestione: da oggi c’è, Azure Firewall Manager è in general availability!

![Azure Firewall Manager](/images/01-Azure-Firewall-MAnager-GA.png)

Finalmente questo strumento è disponibile in tutte le cloud region di Azure, ecco le caratteristiche principali:
- gestione centralizzata del deployment e della configurazione di Azure Firewall;
- gestione e distribuzione gerarchica delle policy;
- integrazione con altrei servizi di sicurezza di terze parti;
- filtraggio del traffico utilizzando due security provider: Azure Firewall per il traffico privato e un altro securitypartner provider per il traffico Internet.

La notizia è ottima ma, come sempre quando si tratta di un servizio “giovane”, occhio ad alcune limitazioni note:
- il traffing splitting non è supportato;
- limite di un solo secured hub per regione;
- la comunicazione tra Secured Virtual Hub non è supportata;
- tutti i Secured Virtual Hub che condividono la stessa virtual WAN devono essere nello stesso resource group.

Per approfondire tutti i dettagli, ecco la notizia e le risorse di documentazione:
- [Azure Firewall Manager is now generally available](https://azure.microsoft.com/en-us/updates/azure-firewall-manager-is-now-generally-available/)
- [Pricing](https://azure.microsoft.com/en-us/pricing/details/firewall-manager/)
- [Documentation](https://docs.microsoft.com/en-us/azure/firewall-manager/)

Il tuo IT Specialist, Riccardo
