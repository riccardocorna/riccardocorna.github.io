---
date: 2020-01-29T08:00:00-00:00
description: "Una panoramica completa di tutti i metodi online e offline per trasferire dati dal tuo datacenter verso Azure nel miglior modo possibile."
featured_image: "/images/01-Come-trasferire-dati-su-Azure-Data-Box.png"
categories: [ "Cloud Datacenter"]
tags: [ "Azure", "Data Box" ]
title: "Trasferire dati su Azure: come scegliere il miglior metodo di trasferimento"
url: "/trasferire-dati-su-azure"
---
Trasferire dati su Azure è un aspetto molto importante da tenere in considerazione mentre pianifichi il viaggio verso soluzioni cloud dei tuoi servizi o della tua infrastruttura.

Azure offre molte soluzioni per ottenere questo risultato, ma queste non sono interscambiabili tra loro. Un corretto approccio prevede, in primo luogo, che tu ti ponga alcune domande che ti permetteranno di scegliere la modalità corretta per trasferire dati su Azure:

Di che tipo di dati si tratta: file, blob, managed disk, altro?
Quanti dati devi trasferire: sei nell’ordine dei MByte, Gbyte o TByte?
Quanto spesso lo devi fare: è un trasferimento una tantum o è sistematico e continuo?
Di seguito ho raccolto per te le caratteristiche salienti di tutti i metodi di trasferimento dati, divisi per tipologia e con un suggerimento su quale sia la situazione corretta di utilizzo di un modo rispetto ad un altro.
Vedremo infine come avere una stima del tempo necessario per trasferire i tuoi dati con metodi online, in base alla quantità e alla banda a disposizione.

## Tipologie di trasferimento dati
Cominciamo a distinguere due macro-categorie di tipologie di trasferimento dati:
- **Online**: i dati vengono trasferiti attraverso una connessione di rete;
- **Offline**: si caricano tutti i dati che hai intenzione di trasferire su un dispositivo fisico che verrà spedito. Microsoft si occuperà poi di riversare tutto il contenuto del dispositivo su Azure.
Per ognuna di queste tipologie esistono vari metodi per portare a termine il trasferimento: vediamoli uno per uno.

## Metodi di trasferimento online
Di seguito una panoramica completa di come trasferire dati su Azure attraverso una connessione di rete.

- **AzCopy**: è un file eseguibile che non richiede alcuna installazione e fornisce una linea di comando che ti permette di trasferire file o blob verso uno storage account di Azure.
    - **Quando usarlo?** Nel caso in cui ti serva un trasferimento dati in blocco (bulk) con alto throughput per file, blob, tabelle da e verso storage account.
    - **Per approfondimenti**: [Get Started with AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)
- **Azure PowerShell**: è l’insieme dei cmdlet PowerShell che ti consente di gestire vari aspetti delle risorse Azure, tra cui anche i trasferimenti di dati.
    - **Quando usarlo?** Per trasferimenti automatizzati attraverso script di piccoli set di dati.
    - **Per approfondimenti**: [Get started with Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/get-started-azureps?view=azps-3.3.0&viewFallbackFrom=azps-1.4.0)
- **Azure CLI**: è una linea di comando secifica per gestire le risorse Azure che puoi utilizzare anche per trasferire dati.
    - **Quando usarlo?** A mio parere, il miglior scenario di utilizzo è il trasferimento automatizzato attraverso script di piccoli set di dati, come per Azure PowerShell. L’orientamento verso CLI o PowerShell dipende dal “linguaggio” che hai scelto: nel caso in cui tu abbia già implementato da qualche parte degli script per gestire risorse Azure, mantenere un linguaggio più coerente tra script è una buona pratica che ti aiuta a mantenere ordine.
    - **Per approfondimenti**: [Install the Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- **Azure Data Factory**: è uno strumento di integrazione di dati cloud in modalità serverless.
    - **Quando usarlo?** Per trasferimento ricorrenti e organizzati in pipeline e flussi. le sorgenti possono essere diverse (ad esempio Amazon S3, Azure Data Lake, Cosmos DB, eccetera) e vengono gestite attraverso dei connettori.
    - **Per approfondimenti**: [Data Factory](https://azure.microsoft.com/en-us/services/data-factory/)
- **Azure Storage da Portale Azure**: è l’interfaccia di gestione degli upload/download degli storage messa a disposizione dal portale di Azure.
    - **Quando usarlo?** puoi usare il portale Azure quando devi trasferire file in maniera puntuale, uno per uno e non hai necessità o possibilità di installare lo Storage Explorer o altri tool a linea di comando come quelli descritti nei paragrafi precedenti.
    - Per approfondimenti: [Data transfer for small datasets with low to moderate network bandwidth](https://docs.microsoft.com/en-us/azure/storage/common/storage-solution-small-dataset-low-moderate-network)
- **Azure Storage Explorer**: è un software da installare su client che fornisce un’interfaccia grafica che rende molto semplice la gestione dei file. Attraverso questa GUI è possibile caricare e scaricare file, blob, tabelle, code e istanze Azure Cosmos DB
    - **Quando usarlo?** Se desideri gestire file, blob e dati di Azure Cosmos DB in maniera sporadica e puntuale con la semplicità di un’interfaccia grafica.
    - **Per approfondimenti**: [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/)
- **Azure Storage REST API / SDK**: le REST API di Azure offrono accesso via http/https alo storage di Azure in tutte le sue declinazioni: code, file services, tabelle, blob.
    - Quando usarlo? Ideale per accedere allo storage di Azure da applicazioni custom che sono in grado di inviare e ricevere richieste e risposte http/https.
    - **Per approfondimenti**: [Azure Storage REST API Reference](https://docs.microsoft.com/en-us/rest/api/storageservices/)
- **Azure Stack Edge**: (una volta conosciuto come Azure Data Box Edge) è un’applicazione fisica gestita che puoi installare nel tuo datacenter locale. Fornisce funzionalità di memorizzazione, calcolo, machine Learning. Questi dati vengono immagazzinati in maniera veloce all’interno dell’appliance per poi essere trasferiti su Azure in background, utilizzando banda di rete ridotta. Supporta SMB/NFS.
    - **Quando usarlo?** Quando hai necessità di elaborare operazioni di machine Learning, calcolo, dati IoT in luoghi, siti o datacenter remoti dove la connettività di rete potrebbe essere un problema per la quantità di dati che elabori.
    - **Per approfondimenti**: [Azure Stack Edge e Data Box Gateway](https://azure.microsoft.com/en-us/services/databox/edge/)
- **Azure Data Box Gateway**: è un’appliance virtuale che puoi installare sul tuo hypervisor locale e ha sostanzialmente le stesse caratteristiche di Azure Stack Edge.
    - **Quando usarlo?** stesso scenario di Azure Stack Edge.
    - **Per approfondimenti**: [Azure Stack Edge e Data Box Gateway](https://azure.microsoft.com/en-us/services/databox/edge/)

## Metodi di trasferimento offline
Dopo aver visto come trasferire dati su Azure attraverso una connessione di rete, vediamo uno per uno i metodi per farlo offline, attraverso la spedizione fisica di dischi o dispositivi di memorizzazione.


**Azure Data Box**: è un dispositivo fisico che Microsoft recapita presso la tua struttura e ha un capacità totale di 100TB, di cui 80 TB utilizzabili per memorizzare file, blob, managed disk tramite SMB/NFS/REST.
I dati memorizzati nel dispositivo sono ovviamente cifrati. Una volta terminato il caricamento dei dati è sufficiente riconsegnare a Microsoft il dispositivo e Microsoft si occuperà di riversare i dati in cloud.
- **Quando usarlo?** per trasferimenti iniziali di grandi quantità di dati.
- **Per approfondimenti**: [Azure Data Box For Offline Transfer](https://azure.microsoft.com/en-us/services/databox/data/)

{{< rawhtml>}}
  <p class="tc"><img src="/images/blog_41.png"></p>
{{< / rawhtml>}}

**Azure Data Box Disk**: è un set di dischi SSD che puoi montare utilizzando USB 3.1 o SATA e su cui è possibile caricare file, blob e managed disk. Una volta terminato il caricamento dati, analogamente ad Azure Data Box, è sufficiente riconsegnare i dischi a Microsoft la quale si occuperà poi del riversamento dati in cloud.
- **Quando usarlo?** Per trasferimenti iniziali di grandi quantità di dati.
- **Per approfondimenti**: [Azure Data Box For Offline Transfer](https://azure.microsoft.com/en-us/services/databox/data/)

{{< rawhtml>}}
  <p class="tc"><img src="/images/blog_42.png"></p>
{{< / rawhtml>}}

**Azure Data Box Heavy**: è un dispositivo rugged, molto capiente (1 PB di capacità di cui 800 TB sono utilizzabili), sul quale è possibile riversare file, blob, managed disk attraverso SMB, NFS, REST. Una volta terminato il caricamento dati, analogamente ad Azure Data Box, è sufficiente riconsegnare il dispositivo a Microsoft la quale si occuperà poi del caricamento dati in cloud.
- **Quando usarlo?** Per trasferimenti iniziali di quantità di dati molto grandi.
- **Per approfondimenti**: [Azure Data Box For Offline Transfer](https://azure.microsoft.com/en-us/services/databox/data/)

{{< rawhtml>}}
  <p class="tc"><img src="/images/blog_43.png"></p>
{{< / rawhtml>}}

**Azure Import/Export**: sei già attrezzato con i tuoi dischi?  Perfetto! Dopo averli caricati con file o blob, spediscili (fino ad un massimo di 10) e poi ci penserà mamma Microsoft a riversarne il contenuto in cloud. 
- **Quando usarlo?** per trasferimenti iniziali di quantità di dati medio/grandi, avendo già a disposizione dei dischi.
- **Per approfondimenti**: [What is Azure Import/Export service?](https://docs.microsoft.com/en-us/azure/storage/common/storage-import-export-service)

## Come scegliere il metodo giusto?

Se hai ancora dubbi su quale sia il metodo giusto per trasferire i tuoi dati su Azure, il portale ti viene incontro con uno strumento prezioso: una sorta di calcolatore/pianificatore automatico che, in base alla quantità di dati da trasferire, alla banda a disposizione e alla frequenza di trasferimento, ti suggerisce automaticamente quali tra i metodi di trasferimento dati a disposizione sia il migliore per la tua situazione.

Per usare il calcolatore è sufficiente accedere ad un qualunque storage account e selezionare la blade **Data Transfer**.

Comparirà un form composto da 3 menu a tendina:
- **Estimated data size for transfer**: da questa tendina puoi selezionare l’ordine di grandezza del quantitativo di dati che devi trasferire, da un minimo di 50 GB fino ad un massimo di 5 PB.
- **Approximate available network bandwidth**: qui puoi indicare approssimativamente la larghezza di banda che hai a disposizione per effettuare il tuo trasferimento.
- **Transfer frequency**: è un trasferimento dati iniziale che farai solo una volta o è ricorrente?

In base a questi 3 parametri, il tool Data Transfer ti fornirà una o più soluzioni che potrebbero fare al caso tuo, siano esse online o offline. Risulta quindi un ottimo aiuto per orientarsi in questa miriade di possibilità!

Nell’esempio in figura, ho impostato un trasferimento dati di 100 GB attraverso una connessione di rete da 100 Mbps, come caricamento iniziale di dati verso il cloud. Come puoi vedere, i metodi suggeriti per un trasferimento di questo tipo sono prettamente online: AzCopy ed Azure Storage Explorer, e viene stimata una durata di 3 ore circa.

[![Storage account Data Transfer tool](/images/blog_44.jpg)](/images/blog_44.jpg)

## Conclusioni
I metodi per trasferire dati da un ambiente on-premises ad Azure sono molti ma, grazie ai consigli che ti ho dato ed aiutandoti col Data Transfer calculator, individuare il metodo giusto sarà molto più facile di quanto pensi!

Grazie per avermi seguito fino a qui in questo articolo tostissimo e lunghissimo! E tu, che esperienze hai avuto quando ti sei trovato a dover trasferire dati su Azure? Ti aspetto sui miei profili social per parlarne. A presto!