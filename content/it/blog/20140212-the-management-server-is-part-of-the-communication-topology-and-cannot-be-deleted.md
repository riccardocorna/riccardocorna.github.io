---
date: 2014-02-12T08:00:00-00:00
description: "Come dismettere un Management Server SCOM e risolvere l'errore The management server is part of the communication topology and cannot be deleted"
featured_image: "/images/SCOM_Gateway_Delete_Error.png"
categories: [ "Archivio" ]
tags: [ "SCOM" ]
title: "Errore “The management server is part of the communication topology and cannot be deleted” su SCOM"
url: "/the-management-server-is-part-of-the-communication-topology-and-cannot-be-deleted"
---
Negli scorsi giorni mi è stato chiesto di dismettere il gateway SCOM di una sede remota del cliente presso il quale attualmente svolgo le mie mansioni. Nel tentativo di cancellarlo però mi sono imbattuto in un errore che recita:”The management server is part of the communication topology and cannot be deleted”. Cosa significa?

Ecco l’errore incriminato che, almeno inizialmente, mi aveva fatto trasalire

![Errore The management server is part of the communication topology and cannot be deleted](/images/SCOM_Gateway_Delete_Error.png)

Se ti compare questo errore, significa che **esistono ancora agenti o dispositivi di rete monitorati che riportano a quel management server**. Nel mio caso in particolare, avevo rimosso correttamente gli agenti ma **mi ero dimenticato di rimuovere un network device**. Una volta cancellato anche quello dalle viste di SCOM, è stato sufficiente tornare sulla vista di amministrazione dei Management Servers, cliccare sul server interessato col tasto destro e selezionare Delete: l’errore non si è più ripresentato e sono riuscito a dismettere una volta per tutte il gateway.

Morale della favola?

Se vuoi dismettere un Management Server o un gateway di SCOM:
1. sposta/cancella tutti gli agenti che riportano ad esso;
2. oltre agli agenti, ricordati di verificare anche eventuali network device!

Ti segnalo anche questo articolo di Microsoft Technet su [come dismettere un management server in SCOM](http://technet.microsoft.com/en-us/library/hh456439.aspx), se vuoi informazioni più approfondite a riguardo.

E tu che procedura segui per dismettere un management server? Hai altri consigli utili da aggiungere? Parliamone nei commenti!