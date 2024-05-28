---
date: 2024-04-16T05:00:00-00:00
description: "Siamo finalmente ad un punto di svolta nella creazione del nostro laboratorio ibrido. Oggi, prepariamo il nostro ambiente per l’installazione, la configurazione e l’attivazione di Entra Connect."
featured_image: "/images/01-the-lab-episode-4-entra-connect.jpg"
images:
  - "/images/01-the-lab-episode-4-entra-connect.jpg"
categories : [ "Identity & Security" ]
tags: [ "Microsoft Entra Connect", "Active Directory", "Video" ]
title: "The Lab - Episodio 4 - Installare e configurare Microsoft Entra Connect"
url: /install-configure-microsoft-entra-connect
---
Specialisti IT, ciao a tutti! Siamo finalmente ad un punto di svolta nella creazione del nostro laboratorio ibrido che, fino a qui, di ibrido aveva avuto ben poco, dato che avevamo creato una foresta AD e installato una Certification Authority, quindi tutte componenti on-prem.

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube SPL4Bwz3Z50 >}}

## Installare e configurare Microsoft Entra Connect

Oggi, prepariamo il nostro ambiente per l’installazione, la configurazione e l’attivazione di Entra Connect. Ebbene sì, finalmente ibridiamo il nostro ambiente, sincronizzando le identità con Entra ID. Anche in questo caso, si potrebbero aprire diversi ed infiniti capitoli su come progettare e mettere in piedi una strategia di sincronizzazione con Entra ID.

### Decisioni di design

Vediamo insieme le principali sfide decisionali e di design

#### Modalità di sincronizzazione
Microsoft, da tempo, sta iniziando a spingere con più forza quella che si chiama Cloud Sync, in luogo della Connect Sync (ovvero quella a cui siamo più abituati col server Entra Connect o, per i più nostalgici, Azure AD Connect).

Cos’è Cloud sync? Un metodo più “leggero”, passatemi il termine, di sincronizzare le identità tra AD ed Entra, basato su un agente. È molto utile in situazioni specifiche, come ad esempio in una topologia a più foreste dove le foreste sono disconnesse tra di loro.C'è poi la classica Connect Sync

Come scegliere tra Connect sync e Cloud Sync? Al di là del caso specifico che vi ho nominato poco fa, per approfondire l’argomento vi lascio un bel link qui sotto!

🔗 [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)

#### Topologia delle directory e dei tenant
Quante foreste di Active Directory avete bisogno di sincronizzare?  
Gli utenti, in caso di ambiente multi-foresta, sono rappresentati più volte nelle varie foreste?  
Oppure, avete necessità di sincronizzare su più tenant?  

Bisogna insomma pianificare, progettare e preparare con cura il tutto, per evitare di incorrere in situazioni non supportate che potrebbero mettere a rischio la consistenza della sincronizzazione!

Anche in questo caso, vi lascio un bellissimo e chiarissimo documento sulle topologie supportate di Entra Connect, che vi aiuterà molto in questa fase di progettazione, sicuramente tra le più delicate!

🔗 [Topologies for Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/plan-connect-topologies)

#### Architettura di autenticazione ibrida
Che si fa? Sincronizziamo le password con Password Hash sync? Installiamo un ADFS per fare in modo che tutte le autenticazioni avvengano comunque su Active Directory on-prem?

Oppure, sempre nel caso in cui vogliamo mantenere il punto di arrivo delle autenticazioni sulla nostra Active Directory on-premises, mettiamo in piedi la Pass Through Authentication con qualche agente installato sui server on-prem?

Ci sono diverse possibilità. Partiamo dal presupposto che ADFS lo scarterei a priori, dato che Microsoft stessa ormai da anni ha messo a disposizione tonnellate di strumenti e sta portando avanti imponenti campagne di workshop, comunicazioni volte a far passare il concetto che ADFS è ora di dismetterlo!

Ci rimangono a disposizione PHS e PTA. Vi lascio, qui in descrizione un altro bellissimo documento che contiene un diagramma di flusso decisionale che vi aiuta a scegliere la modalità di autenticazione ibrida ideale rispetto al vostro ambiente e ai vostri obiettivi.

🔗 [Choose the right authentication method for your Microsoft Entra hybrid identity solution](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn)  
🔗 [What is password hash synchronization with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-phs)  
🔗 [User sign-in with Microsoft Entra pass-through authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta)  
🔗 [What is federation with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-fed)

### Configurazione scelta per il nostro laboratorio

Torniamo a noi: io cosa ho scelto per il nostro laboratorio? Vediamolo punto per punto rispetto alle decisioni chiave di cui vi ho parlato poco fa:

1. **Modalità di sincronizzazione** con **Entra Connect Sync**, perché il mio scopo è testare un tipo di ambiente il più vicino possibile a quello che si può trovare “là fuori nel mondo reale”, dove la stra-grande maggioranza delle realtà usa Entra Connect 
2. **Topologia**: qui c’è poco da scegliere, è un laboratorio basato **su un solo tenant e una foresta mono-dominio**
3. **Architettura di autenticazione ibrida**: voglio cercare di abilitare uno scenario il più possibile orientato verso il cloud, in modo che io possa più facilmente implementare le azioni evolutive che mi possano aiutare a ridurre la dipendenza da Active Directory, quindi la scelta è **Password Hash Sync**.

Perfetto, smarcate le principali decisioni di design, ora è tutto apparecchiato, iniziamo a sporcarci le mani!

### Verifica del dominio personalizzato sul tenant

Io ho già un mio dominio pubblico verificato sul tenant, non ho documentato questa parte perché,  non ho preso i video quando l'ho fatto. Se volete i dettagli, vi lascio qui sotto il link ad una guida scritta dall’amico Nicola Ferrini di ictpower.it: nella prima parte della guida troverete un esempio di come verificare e configurare un dominio personalizzato.

📌 [Configurare Microsoft Entra Connect per sincronizzare le identità con Entra ID](https://www.ictpower.it/cloud/configurare-microsoft-entra-connect-per-sincronizzare-le-identita-con-entra-id.htm)

### Aggiunta del dominio come suffisso UPN su Active Directory
Iniziamo a preparare la nostra AD, aggiungendo il nostro dominio personalizzato tra i possibili suffissi utilizzabili nello User Principal Name dell’utente.

{{< youtubestartend SPL4Bwz3Z50 328 339>}}

### IdFix e remediation degli UPN
Ok, ora dobbiamo fare in modo che tutti gli utenti che vogliamo sincronizzare abbiano come UPN il nostro dominio personalizzato routable e, soprattutto, che sia tutto in ordine anche dal punto di vista di caratteri speciali e altri attributi.

Vi ricordo che, come FQDN del nostro dominio on-premises abbiamo scelto itspecialist.local, ovvero un dominio non routable.

E se avessimo degli utenti che, come UPN, stanno usando itspecialist.local? Che facciamo?

E se, invece, qualcuno avesse nello username dei caratteri speciali o non supportati da Entra Connect? Come si fa?

Dovremmo scovare quali sono questi utenti e fare una bella bonifica!

Dobbiamo farlo a mano? No, per scovarli possiamo chiedere aiuto ad IdFIx, un tool gratuito rilasciato da Microsoft che, fatta una query in AD, scoverà per noi tutte le situazioni non conformi rispetto ad una corretta sincronizzazione di AD con Entra.

Per scaricarlo e approfondirne i dettagli di funzionamento e i codici di errore, vi lascio un link qui sotto.

🔗 [Microsoft IdFix tool](https://microsoft.github.io/idfix/)

Installiamolo e vediamolo in azione nel trovare utenti con UPN non routable e utenti con caratteri non supportati in fase di sync.

{{< youtubestartend SPL4Bwz3Z50 425 468 >}}

Beccati! Ora intraprendiamo le dovute azioni correttive e rifacciamo la query per verificare di aver effettivamente corretto tutto.

{{< youtubestartend SPL4Bwz3Z50 476 504 >}}

Perfetto, abbiamo bonificato tutto! Ovviamente, io ho fatto manualmente perché erano solo 2 oggetti ma, in particolare per correggere gli UPN, la soluzione migliore se avete tanti utenti è quella di scriptare il tutto con PowerShell!

### Installazione di Entra Connect

Andiamo avanti, ora siamo pronti, FINALMENTE, per installare Entra Connect!

Facciamo partire il setup e configuriamolo personalizzando le opzioni in base alle decisioni prese poco fa!

Oltre alle configurazioni derivate dalle decisioni di design, come vedrete, ho impostato anche altri settaggi.

Ve li anticipo qui, prima di iniziare col wizard.

1. Ho configurato il Single Sign-On, anche se, in teoria, non dovrebbe servirci ma non si sa mai!

2. Ho lasciato che fosse Entra Connect a creare l’utenza di servizio che effettuerà la sincronizzazione. In questo modo, si occupa Entra Connect di crearla a permessi minimi e non devo preoccuparmi di gestirne le credenziali.

3. Ho configurato, come scope di sincronizzazione, solo alcune Organizational Unit perché non voglio in nessun modo portarmi in cloud oggetti inutili o, ORRORE, sincronizzare le utenze e i gruppi privilegiati. **Non fatelo!**

4. Ho configurato il password writeback, che ci sarà MOLTO utile quanto implementeremo il Self Service Password Reset!

5. Infine, ho scelto come ancora (o ImmutableID) l’attributo ***ms-DS-ConsistencyGuid***: è questa la scelta migliore che consiglio anche in ambienti di produzione e, se usate ancora come ancora l’ObjectGUID, valuterei un’azione evolutiva in questo senso nel vostro ambiente, soprattutto se multi-foresta!

Perfetto, finalmente vediamo il setup!

{{< youtubestartend SPL4Bwz3Z50 615 766 >}}

Finito! Prima di concludere, verifichiamo solo che la sync abbia avuto successo.

### Verifica della sync

{{< youtubestartend SPL4Bwz3Z50 772 787 >}}

Perfetto, ci siamo, tutto sincronizzato!

## Conclusioni
Come avete visto durante l’esecuzione del wizard, è stato tutto molto semplice e veloce ma solo ed esclusivamente perché abbiamo dedicato le giuste forze, la giusta attenzione e il giusto tempo alla fase di pianificazione e di design.

Se si approccia questa prima fase correttamente, tutto viene più semplice, veloce e naturale.

Non sottovalutate mai questa fase e LOTTATE per dedicarci la giusta attenzione!

Oggi video tosto, quindi doppio ringraziamento per essere sopravvissuti fino a qui, con me che parlo a vanvera e dico cose bla bla bla!

Se vi è piaciuto e se vi piace questo tipo di contenuti, iscrivetevi al mio canale YouTube: a voi non costa nulla, è solo un click ma, per me, è molto importante!

Per tutti gli altri aggiornamenti, vi aspetto anche su LinkedIn e sul mio blog ITSpecialist.cloud.

Vi aspetto, a presto! MITICI!