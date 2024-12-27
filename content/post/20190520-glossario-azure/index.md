---
date: 2019-05-20T08:00:00-00:00
description: "In questo glossario Azure i miei appunti personali di definizioni e terminologia cloud, relative alla piattaforma di casa Microsoft."
image: "glossario-Azure.png"
categories: [ "Cloud Datacenter" ]
tags: [ "Azure", "Glossario"]
title: "Glossario Azure e di terminologia cloud"
url: "/glossario-azure"
---
In questo glossario Azure ho deciso di raccogliere sotto forma di appunti personali una serie di definizioni e terminologie comuni nell’ambito della piattaforma cloud di Microsoft.

## Glossario Azure
Come diceva un certo Albert, non hai veramente capito qualcosa finché non sei in grado di spiegarlo a tua nonna (o era ad un bambino di 6 anni?… mmm… non ricordo ma direi che ci siamo capiti, no? 😉 )

|                                                                                                                                                                                                                                                                                                                     |
|:---:                                                                                                                                                                                                                                                                                                                |
|![Un sistemista che racconta di Azure a sua nonna...](william-krause-673736-unsplash.jpg)                                                                                                                                                                                                                    |
|Un sistemista che racconta di Azure a sua nonna... Photo by [William Krause](https://unsplash.com/photos/IL6M6cmhEpM?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/grandma?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)|

Dato che lo scopo di questo articolo è anche fissare alcuni concetti nella mia stessa testolina, ho preso spunto dal [glossario Azure](https://docs.microsoft.com/en-us/azure/azure-glossary-cloud-terminology) pubblicato sul sito Microsoft, aggiungendo qua e là alcuni piccoli tocchi personali che sono quelli che mi hanno aiutato a capire davvero alcune nozioni. **Ultima nota prima di partire: questo è solo l’inizio di un glossario Azure che diventerà sempre più ampio, spero anche grazie al tuo aiuto. Se c’è un qualunque termine in ambito cloud che vorresti inserire qui, scrivimi! Sarò lieto di inserirlo ed arricchirlo sempre di più!** Cominciamo!

## Availability Set
Un Availability Set è una funzionalità di Azure che, al momento del deployment di una macchina virtuale, consente di raggruppare logicamente macchine virtuali isolandole l’una dall’altra a livello di switch di rete, storage, rack, server fisico sui quali sono allocate. Nel momento in cui, all’interno del data center Azure, dovesse accadere un guasto o se dovessero esserci attività di manutenzione programmata, avere le proprie VM all’interno di un availability set dà la garanzia che non siano down tutte contemporaneamente. Un Availability Set quindi protegge i propri workload da guasti hardware o attività di manutenzione che coinvolgono gli apparati all’interno di un datacenter. I raggruppamenti all’interno di un Availability Set sono fatti sulla base di due criteri: [Fault Domain](#fault-domain) e [Update Domain](#update-domain).

## Availability Zone
Le Availability Zone sono località separate fisicamente entro una Azure Region. Ogni availability zone è costituita da uno o più data center dotati di impianti indipendenti per l’energia, il raffreddamento e la rete. Una Availability Zone quindi protegge i propri workload da eventi catastrofici che coinvolgono interi datacenter.

## Azure Classic Deployment Model
Fino al 2014, nel modello di deployment Classic, le risorse che venivano distribuite su Azure erano sostanzialmente indipendenti le une dalle altre. Venivano create manualmente da portale oppure attraverso uno script all’interno del quale ci si doveva preoccupare di gestire tutto il deployment in una maniera in qualche modo coordinata ma comunque “manuale”. Stessa cosa per cancellare una risorsa.

## Azure Resource Manager Deployment Model
A partire dal 2014 è stato introdotto il concetto di Resource Group nel contesto del Resource Manager Deployment Model. Questo tipo di approccio prevede di poter effettuare il deployment, la gestione, il monitoraggio di tutte le risorse ed i servizi come un raggruppamento piuttosto che individualmente. I vantaggi principali sono:
- essendo distribuite come raggruppamenti che hanno legami e dipendenze, le risorse possono essere deployate ripetutamente all’interno della tua soluzione cloud con la sicurezza che questo avvenga in maniera sempre consistente
- in fase di controllo degli accessi e dei permessi sulle risorse, è molto più semplice gestirli su un gruppo (resource group) che individualmente
- si possono applicare tag per tracciare meglio risorse e costi ad esse associati

## ExpressRoute Gateway
L’ExpressRoute Gateway è un tipo di [Virtual Network Gateway](#virtual-network-gateway) usato per mettere in comunicazione Azure con reti on-premises attraverso una connessione privata (e quindi non Internet) con i datacenter Microsoft. ExpressRoute è un servizio disponibile solo presso alcuni operatori/fornitori di connettività e offre il più alto livello di connettività in termini di prestazioni, banda e sicurezza.

## Fault Domain
Un raggruppamento logico di macchine virtuali che, all’interno di un [Availability Set](#availability-set), condividono la stessa sorgente di alimentazione e sono attestate sullo stesso switch di rete. Macchine virtuali in uno stesso Availability Set ma in Fault Domain differenti si attestano su sorgenti di alimentazione e switch di rete differenti.

## Geography
Una Azure Geography è un’area definita del mondo che contiene almeno una [Azure Region](#region) e all’interno della quale vengono mantenuti i requisiti di residenza dei dati, conformità, sovranità.

## Private Link
È una connessione sicura e privata alle risorse dei servizi di Azure, che possono essere PaaS (storage, SQL ecc) oppure ai marketplace services. Le risorse (ead esempio blob storage) vengono mappate attraverso un indirizzo IP privato con il relativo record DNS. È possibile effettuare l’accesso privato dalle Virtual Network (anche di tipo peered) e da reti on-premises.

## Region
Una regione è un’area all’interno di una [Geography](#geography) costituita da un insieme di datacenter distribuiti entro un perimetro di latenza, connessi attraverso una rete regionale dedicata a bassa latenza.

## Resource Group
È un contenitore di risorse che condividono un ciclo di vita comune. Esempio pratico: un resource group di nome “DomainControllers” all’interno del quale hai deployato le VM che saranno i tuoi domain controller conterrà al suo interno tutti gli oggetti legati alle tue VM. Le macchine virtuali stesse, le schede di rete dei domain controller, i dischi, eccetera.

# SKU (Stock Keeping Unit)
Rappresenta le diverse forme e le diverse caratteristiche attraverso cui uno stesso prodotto è disponibile. Esempio: un Public IP in Azure (il prodotto), è disponibile in due varianti (SKU Basic e SKU Standard) che hanno differenti caratteristiche.

## Subscription
Un contratto sottoscritto tra Microsoft e cliente che consente a quest’ultimo di usufruire dei servizi della piattaforma cloud Azure. Tariffazione e termini di utilizzo dipendono dalla tipologia esatta di offerta che è stata scelta.

## Traffic Manager
È un bilanciatore a livello DNS che consente la distribuzione del traffico verso diversi endpoint nel backend (VMs con Public IP, Azure Web App, cloud services ed anche on-premises endpoint). A differenza di Azure Application Gateway, Traffic Manager non effettua routing né forwarding verso gli endpoint di backend. In ottica di BCDR (Business Continuity Disaster Recovery), permette il monitoraggio dello status relativo ai siti (sorgente e destinazione): in caso di failure del sito sorgente, Traffic Manager redirige automaticamente il traffico sul target site.

## Update Domain
Un raggruppamento di macchine virtuali che, all’interno di un [Availability Set](#availability-set), vengono riavviate contemporaneamente in seguito ad un aggiornamento pianificato dell’infrastruttura fisica Azure sottostante che le ospita. Microsoft non riavvia mai più di un Update Domain alla volta. Per questo motivo VM all’interno di uno stesso Availability Set ma in Update Domain differenti non verranno mai riavviate con temporaneamente.

## Virtual Machine
È l’implementazione software di un computer fisico che esegue un sistema operativo. In altre parole, si può dire che è un modo per eseguire più sistemi operativi contemporaneamente sullo stesso hardware.

## Virtual Network
Una Virtual Network Azure (VNet) è una rappresentazione di una rete in cloud. In altre parole, rappresenta gli spazi di indirizzamento IP del tuo datacenter in cloud. Logicamente, si può anche definire come un ambiente di rete isolato all’interno del quale eseguire macchine virtuali e applicazioni. Virtual Network differenti non comunicano tra loro a meno di connetterle via VPN o attraverso un peeering. Una Virtual Network può essere messa in comunicazione con un datacenter on-premises attraverso un [VPN Gateway](#vpn-gateway) o un [ExpressRoute gateway](#expressroute-gateway).

## Virtual Network Gateway
Un Virtual Network Gateway serve per mettere in comunicazione ed indirizzare il traffico di rete tra Azure e reti on-premises. È costituito da due o più macchine virtuali, invisibili e non amministrabili dall’utente, che sono distribuite in una specifica subnet (la GatewaySubnet) e contengono configurazioni, tabelle di routing e servizi specifici del gateway.
Un Virtual Network Gateway può essere di due tipi: [VPN Gateway](#vpn-gateway) oppure [ExpressRoute gateway](#expressroute-gateway).

## VPN Gateway
Il VPN Gateway è un tipo di [Virtual Network Gateway](#virtual-network-gateway) usato per mettere in comunicazione Azure con reti on-premises (o anche tra VNet Azure) attraverso una connessione cifrata su rete pubblica Internet. Le modalità tipiche di implementazione di un VPN Gateway sono Site-To-Site, Point-To-Site, VNet-To-VNet.

## Contributi alle definizioni
Per le voci di glossario e le relative definizioni che sono state aggiunte nel tempo, vorrei ringraziare: [Ottavio De Marco](https://www.linkedin.com/in/ottaviodemarco/).