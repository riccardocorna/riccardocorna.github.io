---
date: 2019-05-27T08:00:00-00:00
description: "La topologia di rete hub spoke è un modello di implementazione delle VNet Azure che centralizza servizi condivisi e isola workload specifici."
featured_image: "/images/01-Azure-Topologia-di-Rete-Hub-Spoke.png"
categories: [ "Cloud Datacenter" ]
tags: [ "Azure", "Network", "Hub & Spoke" ]
title: "Topologia di rete Hub Spoke in Azure"
url: "/topologia-di-rete-hub-spoke-azure"
---
La topologia di rete hub spoke è un modello architetturale secondo cui organizzare le virtual network in Azure che permette da una parte di centralizzare i servizi che vengono utilizzati in maniera condivisa dai workload del cliente e, dall’altra parte, di isolare i workload in virtual network diverse.

[![Topologia di rete Hub & Spoke su Virtual Network Azure](/images/01-Azure-Topologia-di-Rete-Hub-Spoke.png)](/images/01-Azure-Topologia-di-Rete-Hub-Spoke.png)

## Cosa si intende per “Hub”
Da un punto di vista di rete, per Hub si intende una Virtual Network (VNet) in Azure che agisce come punto centrale di connettività con il tuo datacenter on-premises. Questa [Virtual Network](/glossario-azure/#VirtualNetwork) sarà infatti collegata al tuo datacenter principale attraverso un [VPN Gateway](/glossario-azure/#VPNGateway), un [gateway ExpressRoute](/glossario-azure/#ExpressRouteGateway), una Network Virtual Appliance (NVA) e sarà il primo punto di contatto della tua rete corporate con il cloud Azure.

Da un punto di vista più logico/architetturale, all’interno dell’hub sono contenuti tutti i servizi del cliente che sono condivisi da vari workload applicativi. Ad esempio, all’interno di un hub, oltre alla parte di connettività citata sopra, potremmo distribuire i Domain Controller, i DNS, dei server FTP su cui riconciliare i dati dei workload, insomma tutte quelle risorse che erogano dei servizi di base e che sono utilizzati da altri ambienti applicativi.

## Cosa si intende per “Spoke”
Gli spoke contengono workload specifici che possono afferire logicamente ad un’isola applicativa oppure ad un dipartimento, un ambiente di produzione o di test e via dicendo. Ad esempio, all’interno di uno spoke potremmo trovare tutte le componenti cloud di un’applicazione specifica: web server, load balancer, database (se dedicato a quell’applicazione), eccetera.

Le virtual network spoke, a livello di rete e connettività, sono in comunicazione via peering con la VNet hub ma non direttamente con le altre VNet spoke (a meno di voler implementare un peering diretto).
Una VNet spoke può comunicare con il data center on-premises se su entrambi i peering da/verso l’hub vengono abilitate le opportune opzioni per consentire di usare l’hub come gateway.

Una virtual network spoke può anche essere messa all’interno di un’altra sottoscrizione per fornire un ulteriore isolamento a livello logico, di fatturazione, di controllo dei costi e di segregazione degli aspetti di sicurezza.

## In quali situazioni si usa una topologia di rete hub spoke?
Se le tue esigenze si avvicinano a quanto stai per leggere nei prossimi punti, la topologia di rete hub spoke potrebbe fare al caso tuo:
- hai dei workload di diverse isole applicative, diversi ambienti (produzione, test) oppure diversi dipartimenti che hanno però la necessità di appoggiarsi - agli stessi servizi di base condivisi (Active Directory, DNS, NTP, ecc);
- da una parte hai la necessità di controllare centralmente alcuni aspetti come connettività verso il datacenter on-premises, sicurezza, firewall;
- dall’altra parte hai bisogno di separare la gestione di singoli ambienti applicativi di modo che siano isolati l’uno dall’altro.

## Quali sono i vantaggi di una topologia di rete hub spoke?
Ecco quali sono i vantaggi nell’utilizzare questo tipo di topologia di rete:
- centralizzi in un unico punto i servizi condivisi da più workload, evitando di “duplicarli” in ogni ambiente e risparmiando quindi su questa voce di costo;
- hai la possibilità di separare a livello di fatturazione e tracciabilità dei costi i differenti componenti del tuo ambiente cloud;
- allo stesso modo, puoi completamente segregare gli aspetti di gestione e sicurezza dei vari ambienti.

## E gli svantaggi?
Ogni soluzione ha sempre due facce: per quanto riguarda la topologia di rete hub spoke il rovescio della medaglia riguarda i costi di connettività, con particolare riferimento ai peering tra l’hub e i vari spoke.

Non è possibile dare a proporzione esatta una percentuale esatta dell’incidenza dei costi di connettività sul totale del tuo ambiente cloud ma di sicuro, in questo tipo di architettura, il costo della connettività e dei peering è uno di quelli che potrebbe incidere maggiormente.

## Best practice quando implementi una topologia di rete hub spoke
Di seguito alcune regole generali di implementazione dei vari componenti di questa architettura.

> Queste sono regole generali che, calate nella realtà del tuo ambiente, potrebbero non essere più valide: presta molta attenzione alla fase di pianificazione e di disegno della tua architettura di rete ibrida.
- la virtual network Hub e le virtual network Spoke dovrebbero essere distribuite in differenti resource group o addirittura in differenti sottoscrizioni;
- la GatewaySubnet non dovrebbe essere più piccola di una /27, di modo da evitare che si “riempia” troppo facilmente in caso di future esigenze di crescita;
- se stai utilizzando un gateway ExpressRoute e desideri aumentare l’affidabilità della connettività tra il tuo datacenter on-premises ed Azure, puoi affiancare ad ExpressRoute un VPN gateway come failover;
- se hai necessità che due virtual network Spoke comunichino direttamente tra loro, puoi implementare tra loro un VNet peering;
    - attenzione: se il numero degli spoke da mettere in comunicazione cresce, implementare tanti VNet peering potrebbe portarti ad esaurire velocemente il numero massimo di peering consentiti per una virtual network;
    - in questo tipo di scenario è probabilmente meglio usare una NVA con delle User Defined Route (UDR);
- se desideri che gli spoke comunichino con il tuo datacenter on-premises ricordati di impostare le opportune configurazioni sul peering tra hub e spoke e viceversa:
    - configura il VNet peering **Hub** –> **Spoke** con l’opzione **Allow gateway transit**;
    - configura ogni VNet peering **Spoke** –> **Hub** che ti interessa mettere in comunicazione con la rete on-premises con l’opzione **Use remote gateways**.

## Conclusioni
Grazie per avermi seguito fino alla fine leggendo questo articolo tostissimo 🙂

Se vuoi approfondire ulteriormente l’argomento, ecco una serie di risorse ufficiali Microsoft che ho raccolto per te:
- [Implement a hub-spoke network topology in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
- [Implement a hub-spoke network topology with shared services in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/shared-services)
- [Choose a solution for connecting an on-premises network to Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/)
- [Azure Networking: introduzione al modello Hub-Spoke](https://francescomolfese.it/2018/08/azure-networking-introduzione-al-modello-hub-spoke/)

Se hai dubbi, domande o qualche elemento utile da aggiungere a quello che ti ho raccontato, ti aspetto nei commenti.

A presto!

Riccardo