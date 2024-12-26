---
date: 2020-07-10T08:00:00-00:00
description: "Da oggi in preview la possibilità di usare Azure Private Link per connettere virtual network ad Azure Automation usando endpoint privati."
image: "01-Azure-Automation-1.png"
categories: [ "Cloud Datacenter"]
tags: [ "Azure", "Azure Automation", "Azure Private Link", "News" ]
title: "Azure Automation supporta Azure Private Link (preview)"
url: "/azure-automation-supporta-azure-private-link-preview"
---
Azure Automation permette di realizzare cose davvero incredibili, una delle poche cose che mancava era la possibilità di connettere virtual network ad Automation tramite endpoint privati con [Azure Private Link](/azure-private-link-general-availability/): da oggi la funzionalità è in preview.

![](01-Azure-Automation-1.png)

Quali possibilità offre questa nuova funzione? Ad esempio, stabilire una connessione privata ad Automation senza aprire un accesso pubblico o fare in modo che l’accesso ai dati di Automation siano acceduti solo da una rete autorizzata.

Insomma, è sicuramente una grande notizia per quei contesti dove le automazioni devono interagire con altre risorse e sistemi che sono nella rete corporate e aggiunge infinite possibilità di automazione. In alcuni progetti ai quali ho partecipato, avere a disposizione questa funzionalità mi sarebbe stato davvero molto utile!

Ecco alcune risorse utili per cominciare a prederci un po’ di confidenza:
- [Azure Private Link support for Azure Automation is now available in preview](https://azure.microsoft.com/en-us/updates/public-preview-private-link-azure-automation-is-now-available/)
- [Private Link documentation](https://docs.microsoft.com/en-us/azure/private-link/)
- [Azure Automation documentation](https://docs.microsoft.com/en-us/azure/automation/)

Il tuo IT Specialist, Riccardo