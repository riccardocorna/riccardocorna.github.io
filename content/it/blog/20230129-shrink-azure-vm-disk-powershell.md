---
date: 2023-01-29T08:00:00-00:00
description: "Come ridurre le dimensioni del disco di una virtual machine su Azure con PowerShell e risparmiare sui costi di storage."
featured_image: "/images/01-shrink-azure-vm-disk.png"
categories : ["Cloud Datacenter"]
tags: [ "Azure", "Virtual Machine", "PowerShell" ]
title: "Ridurre le dimensioni del disco di una VM Azure con PowerShell"
url: /shrink-azure-vm-disk-powershell
---
Shrink del disco di una VM in Azure per risparmiare sui costi di storage? Con qualche martellata qua e là e un po' di PowerShell, si può fare. 

Oggi esco un pochino dal perimetro degli argomenti che tratto solitamente. 😉

![Resize dei dischi su un server Windows](/images/01-shrink-azure-vm-disk.png)

Qualche giorno fa stavo dando un'occhiata al consumo della mia sottoscrizione di laboratorio e ho notato che i costi dei dischi si mangiavano una buona fetta del mio (risicato) budget mensile.

La cosa non mi andava particolarmente a genio, dato che le poche VM che uso sono quasi sempre spente e l'occupazione reale di disco era ridicola in relazione alla grandezza dei dischi (Standard SSD, E10 da 128GB).

Quindi mi sono detto:

> *"Perché pagare un E10 quando basterebbe un E6 da 64 GB?"*

E così mi sono messo a scandagliare la rete in cerca di qualcosa di utile che, infine, ho trovato. Ecco qua una bellissima procedura per ridurre la dimensione dei dischi di una VM Azure:

➡️ [Shrink an Azure VMs OS Managed Disk using PowerShell](https://jrudlin.github.io/2019-08-27-s)

***Nota bene***: ***chiaramente la procedura è da valutare in maniera molto attenta in ambienti di produzione critici e che prevedano configurazioni particolari sui managed disk. Lo script viene fornito dall'autore "as-is", senza garanzie di alcun tipo.*** 

Esperienza personale: io l'ho provato su due macchine di **laboratorio**, di cui una è un domain controller ed è andato tutto liscio. A riguardo dell'esecuzione dello script, è meglio eseguirlo copiando e incollando passo per passo ogni singolo spezzone di comando, perché (come dice anche l'autore sul suo blog), non c'è alcuna logica di error handling e quindi, in caso di problemi, diventerebbe difficile capire a che punto si è "incartato".

**Rimane comunque il consiglio di valutare molto attentamente il tutto prima di eseguire la prcedura su workload di produzione.**

Bene: ora sei pronto per risparmiare. 😃 In bocca al lupo!

Riccardo