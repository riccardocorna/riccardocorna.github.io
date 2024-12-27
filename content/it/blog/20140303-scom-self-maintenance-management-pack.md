---
date: 2014-03-03T08:00:00-00:00
description: "Con l'OpsMgr Self Maintenance Management Pack puoi automatizzare le tipiche operazioni di gestione e manutenzione quotidiana del tuo ambiente SCOM."
featured_image: "/images/OpsMgr-Self-Maintenance-Management-Pack-Slider.png"
categories: [ "Archivio" ]
tags: [ "SCOM", "Management Pack" ]
title: "SCOM Self Maintenance Management Pack"
url: "/scom-self-maintenance-management-pack"
---
Oggi ricomincio la settimana da dove l’avevo conclusa, ovvero da Operations Manager, per parlarti di un management pack molto molto utile che ci ha aiutati parecchio nello snellire alcune operazioni noiose e ripetitive tipiche della gestione quotidiana di SCOM: il Self Maintenance Management Pack di Tao Yang.

![Logo di System Center Operations Manager](/images/8551.SCOM_3535026B.png)

Se gestisci quotidianamente un’infrastruttura SCOM avrai sicuramente a che fare con alcune operazioni che, non ho mai capito perchè, non sono nativamente automatizzabili o programmabili. Questo management pack ti aiuta in tutti quelli che sono i piccoli dolori quotidiani di noi “scommisti” come ad esempio:
- bilanciare automaticamente il numero di agenti che riportano ad un gruppo di Management Server;
- chiudere automaticamente allarmi obsoleti;
- convertire gli agenti da “manually installed” a “Remote Manageable”: questa è una delle funzioni che preferisco di questo MP perchè in questo modo ti permette di installare a mano o di scriptare l’installazione degli agenti SCOM senza la noia di doverli successivamente aggiornare manualmente in caso di un cumulative update. In questo modo anche gli agenti installati a mano verranno visti come se fossero stati installati tramite la push da console;
- puoi programmare il backup di **tutti** i management pack, sia sealed che unsealed;
- monitora [la dimensione della tabella LocalizedText](http://blogs.technet.com/b/kevinholman/archive/2008/10/13/does-your-opsdb-keep-growing-is-your-localizedtext-table-using-all-the-space.aspx) del database di Operations Manager che alle volte accusa problemi di performance.

Nel luogo in cui svolgo attualmente le mie mansioni di “scomista” l’abbiamo installato qualche tempo fa e ci ha aiutato davvero molto: le caratteristiche che ci sono state più utili sono sicuramente la conversione degli agenti da manually isntalled a remote manageable e il backup dei management pack.
Ci sono però molte altre funzioni utilissime che tengono conto anche delle novità introdotte da Operations Manager 2012: il mio consiglio è di provare assolutamente questo management pack.

Esiste in due versioni, una compatibile con SCOM 2007 R2 e 2012 e una espressamente studiata per SCOM 2012. Ovviamente è consigliata la seconda se il tuo ambiente è basato sulla release 2012. Puoi leggere ed approfondire tutte le caratteristiche di questo management pack direttamente andando sul [blog dell’autore](http://blog.tyang.org/2013/03/03/opsmgr-self-maintenance-management-pack/).

Hai mai sentito parlare di questo management pack? L’hai mai usato nella tua infrastruttura? Parliamone insieme nei commenti!