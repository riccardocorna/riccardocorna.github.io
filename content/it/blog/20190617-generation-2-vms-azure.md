---
date: 2019-06-17T08:00:00-00:00
description: "Finalmente le macchine virtuali di seconda generazione (Generation 2 VMs) sono disponibili in public preview su Azure con molte novità!"
featured_image: "/images/01-Azure-Generation-2-vms.png"
categories: [ "Cloud Datacenter" ]
tags: [ "Azure", "Virtual Machine", "News" ]
title: "Azure Generation 2 VMs in public preview"
url: "/generation-2-vms-azure"
---
Finalmente sono arrivati caldo e bel tempo e, insieme a loro, le buone notizie: le macchine virtuali di seconda generazione (Generation 2 VMs) sono disponibili in public preview su Azure! Ti racconto quali sono le principali novità e i vantaggi che questa nuova generazione di macchine virtuali porta con sé.

![Azure Virtual Machine](/images/01-Azure-Generation-2-vms.png)

## Novità e caratteristiche principali delle Generation 2 VMs
Quali sono le caratteristiche principali di una macchina di seconda generazione, rispetto a quelle di prima generazione?
- boot basato su UEFI e non più su BIOS;
- disco di sistema operativo che può superare i 2 TB (fino ad un massimo raccomandato di 4 TB);
- capacità di calcolo e limiti di memoria ampliate;
- disponibile solo per tagli di VM che supportano storage di tipo premium.

## Immagini di sistema operativo disponibili
Attualmente sono state pubblicate le seguenti immagini di Windows per le generation 2 VM:
- Windows Server 2019 Datacenter (2019-datacenter-gen2);
- Windows Server 2016 Datacenter (2016-datacenter-gen2);
- Windows Server 2012 R2 Datacenter (2012-r2-datacenter-gen2);
- Windows Server 2012 Datacenter (2012-datacenter-gen2).

## Consigli e best practice
Prima di tutto, è bene ricordare che **le Generation 2 VMs sono in stato di “public preview” e quindi non è consigliato utilizzarle in ambienti di produzione** perché non fornite di alcun Service Level Agreement.

In secondo luogo, **dal momento che è una public preview, alcune delle seguenti considerazioni potrebbero cambiare in futuro quando il loro stato cambierà in General Availability**.

Ok, fatte le dovute premesse, ecco alcune informazioni utili emerse dalla documentazione che ho letto:
- nessuna differenza di prezzo rispetto alle VM di generazione 1;
- possono essere create solo con tagli di VM che supportano storage premium;
- possono usare Ultra SSD;
- supportano l’Accelerated Networking;
- una volta scelta la generation (1 o 2), non è più possibile cambiarla;
- supportato solo vhd, non vhdx;
- possono essere utilizzate anche per Virtual Machine Scale Set;
- al momento non disponibili Azure ASR ed Azure Backup.

Se vuoi approfondire ulteriormente l’argomento, ecco due link che ho raccolto per te:
- Blog Announcement: [Generation 2 virtual machines in Azure – Public Preview](https://azure.microsoft.com/en-us/updates/generation-2-virtual-machines-in-azure-public-preview/)
- Docs: [Generation 2 VMs (preview) on Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/generation-2)

È tutto! Nei prossimi giorni farò sicuramente qualche test per prendere confidenza con queste nuove caratteristiche.

Se ho dimenticato qualcosa, se vuoi fare un’osservazione o se semplicemente vuoi fare quattro chiacchiere sulle Generation 2 VMs di Azure, ti aspetto nei commenti.

Buona settimana!

Riccardo

