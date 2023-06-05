---
date: 2023-06-07T05:00:00-00:00
description: "Ogni foresta e dominio di Active Directory dovrebbero avere LDAPS implementato ma in pochissimi casi lo è davvero. L'argomento spaventa perché ci sono di mezzo i certificati ma, una volta capiti alcuni concetti di base, è più facile di quanto sembri da domare. Vediamo come implementarlo!"
featured_image: "/images/01-LDAPS.png"
categories : [ "Identity & Security" ]
tags: [ "Active Directory", "LDAPS", "Video" ]
title: "Implementare LDAPS in Active Directory on-premises"
url: /ldaps-active-directory-on-premises
---
Specialisti IT, ciao a tutti! Oggi, dopo un po' di tempo, torniamo a parlare di una configurazione dal sapore decisamente on-premises: **LDAPS in Active Directory**.  
Ormai ogni foresta e ogni dominio dovrebbero avere LDAPS implementato ma in pochissimi casi lo è davvero. L'argomento spaventa perché ci sono di mezzo i certificati ma, una volta capiti alcuni concetti di base, è più facile di quanto sembri da domare.  
Vediamo come implementarlo!

## Video
Trovate l'intero video qui sotto, altrimenti potete continuare a leggere l'articolo.

{{< youtube sqWKhZPsEJU >}}

## Articolo

Con tutto questo parlare di cloud, mi sono accorto di aver trascurato la nostra amata Active Directory! Non dobbiamo e non possiamo dimenticarla, perché nella stragrande maggioranza delle aziende, è l’autorità designata alla gestione delle identità e sono proprio quelle identità che noi sincronizziamo attraverso Azure AD Connect che dobbiamo mettere in sicurezza.

Oggi, quindi, vi racconto di come mettere un po’ più in sicurezza l’intera infrastruttura di Active Directory attraverso l’implementazione della versione sicura del protocollo LDAP: **LDAPS**!

## Che cos'è LDAP?

Credo che quasi tutti sappiate cosa sia ma lo ripeto velocemente giusto per parlarne magari ai colleghi più giovani o, per dirla in maniera più elegante e moderna, ai colleghi “cloud native”. 😉 

Il protocollo LDAP, acronimo di **Lightweight Directory Access Protocol**, è un protocollo di rete utilizzato per accedere e gestire informazioni all'interno di una directory. Ad esempio, un qualunque applicativo di anagrafica che debba recuperare i dati e gli attributi di un utente della nostra AD, per farlo usa LDAP. Insomma, LDAP ci aiuta ad accedere e a gestire le informazioni degli oggetti memorizzati al suo interno: utenti, gruppi, computer account, eccetera eccetera...

## Come funziona?

Fisicamente, come si fa a recuperare queste informazioni? Senza entrare nel dettaglio formalmente tecnico del protocollo e della connettività, diciamo che, per recuperare quello che serve quando si fa una query LDAP, tipicamente ci si connette ai domain controller su porta TCP 389 e si fa un’autenticazione con nome utente e password (inviati in chiaro).  
Quest’ultima operazione si chiama “bind ldap”. La bind quindi non è altro che un'operazione di autenticazione effettuata da un client LDAP per stabilire una connessione e ottenere l'accesso ad Active Directory o a una specifica parte di essa.

Come dicevo poco fa, questa operazione, tipicamente è sempre avvenuta in chiaro: quando questo avviene parliamo di “simple bind”

{{< youtubestartend sqWKhZPsEJU 134 157 >}}

Come avete visto, avviene tutto in chiaro e il fatto che avviene in chiaro... non ci piace. 😠

Ed è proprio questo su cui oggi caleremo la nostra scure di sicurezza, fatta di certificati e altre cose brutte! LDAPS, infatti, è la versione sicura del protocollo che ci permetterà di dire “Addio” alle nostre simple bind... o Simple Minds... come volete

## Implementare ed usare LDAPS

Come avviene tutto questo? La connessione LDAPS avviene su porta TCP 636 e la bind avverrà attraverso dei certificati rilasciati dalla nostra Certification Authority.

L’obiettivo di oggi, quindi, è fare in modo che non sia più possibile fare bind LDAP in chiaro.

Ad alto livello, quindi, cosa faremo e cosa ci serve?
- un template di certificato adatto all’occasione
- pubblicare il template in AD
- fare l’enrollment dei certificati sui domain controller
- verificare che la connettività sulla porta 636 funzioni
- configurare un paio di GPO per dire ai domain controller di accettare solo query LDAPS e dire a client e server di inviare solo richieste sicure in LDAPS
- testare che non riescano più a fare delle bind in chiaro sui DC

A questo punto, vi starete già facendo delle domande, ad esempio:

> *“E se ci sono applicativi, o più in generale, se ci sono degli elementi della mia infrastruttura che non supportano LDAPS? Che succede?”*

Cercherò di rispondere a tutti i dubbi che potrebbero sorgere, più avanti nel video, per ora concentriamoci su come implementarlo.

**Vale però, come sempre, il solito concetto: tutto quello che vedi nei miei video è fatto in un laboratorio, dove ci sono delle condizioni e delle configurazioni sicuramente diverse rispetto al vostro ambiente di produzione. Quindi, usate questo video solo come uno spunto da applicare solo dopo aver calato tutti questi concetti all’interno della vostra specifica realtà. Ok?**

### Creazione del certificate template

Perfetto, ora creiamo e pubblichiamo il template di certificato su Active Directory! Ho scelto di usare, come base, il template **Kerberos Authentication**, facendo alcune modifiche.

{{< youtubestartend sqWKhZPsEJU 288 375 >}}

### Configurazione autoenrollment del certificato e test

Per comodità e dal momento che la situazione del mio ambiente di laboratorio me lo permette, ho scelto di fare in modo che il certificato LDAPS sia gestito in autoenrollment direttamente dai domain controller.  Se hai notato, poco fa, nella tab dei permessi mentre creavo il template, il gruppo di dominio dei domain controller aveva permessi di autoenrollment.

Ora vediamo in che situazione iniziale è il domain controller. Dopo di che, creiamo la GPO per l’autoenrollment, la applichiamo e vediamo se il certificato si è distribuito correttamente!

{{< youtubestartend sqWKhZPsEJU 406 484 >}}

### Test connessione su porta TCP 636

Se tutto è andato come previsto, e sembra di sì, ora dovremmo riuscire a connetterci sulla porta TCP 636 del domain controller, vediamo se è così!

{{< youtubestartend sqWKhZPsEJU 493 512 >}}

Perfetto, funziona!

### Configurazione delle GPO per il signing di LDAPS

Ora è il momento di fare un paio di GPO.

La prima verrà applicata ai Domain Controller e servirà per dire proprio ai Domain Controller che dovranno accettare esclusivamente bind sicure.

{{< youtubestartend sqWKhZPsEJU 525 565 >}}

La seconda verrà applicata alle OU che contengono i computer e i server del vostro dominio e che, in questo contesto, sono dei client LDAP; con questa GPO imposteremo che i client LDAP useranno esclusivamente LDAPS!

{{< youtubestartend sqWKhZPsEJU 581 638 >}}

### Test simple bind

Dopo aver applicato le GPO, verifichiamo se riusciamo a fare una simple bind come eravamo riusciti a fare ad inizio video.

{{< youtubestartend sqWKhZPsEJU 645 667 >}}

Ottimo, non riusciamo più a farla ed è quello che volevamo!

### Quali dubbi? Come pianificare l'implementazione di LDAPS?

Ora cerco di fugare il principale dubbio che potrebbe esserti venuto in mente durante la visione di questo video.

> *Posso implementare così com'è questa configurazione?*

La risposta è “probabilmente NO” o, per lo meno, “non immediatamente”, perché all’interno della vostra infrastruttura, probabilmente, ci sono ancora applicativi o server o, spero di no, client che fanno ancora query LDAP in chiaro.

**Come si fa a sapere chi o cosa sta facendo delle query LDAP in chiaro?**

Bisogna iniziare da un’attività di audit, facilmente implementabile distribuendo alcune chiavi di registro sui domain controller, ecco un po' di documentazione super fresca e dettagliata per aiutarvi a farlo:
- [How to discover clients that do not use the Require signing option](https://learn.microsoft.com/en-us/troubleshoot/windows-server/identity/enable-ldap-signing-in-windows-server#how-to-discover-clients-that-do-not-use-the-require-signing-option)

- [How to configure Active Directory and LDS diagnostic event logging](https://learn.microsoft.com/en-GB/troubleshoot/windows-server/identity/configure-ad-and-lds-event-logging)

Una volta concluso l’audit, avrete in mano l’elenco completo di quali sono le macchine che fanno query LDAP in chiaro e, a quel punto, dovrete riconfigurare questi sistemi/applicativi per poter fare query LDAPS, quindi sicure. Fino a quel momento, lato Domain Controller, non potrete impostare la GPO sul valore “Require Signing”, altrimenti potreste avere qualche problema.

## Conclusioni

Come sempre, una buona conoscenza e un’analisi preventiva della propria infrastruttura sono molto utili a capire come procedere evitando danni.

Spero che questo video vi sia stato utile: in questo folle mondo cloud, l’Active Directory non va mai trascurata!  
E voi avete implementato LDAPS? Se sì, parliamone insieme nei commenti e sui miei profili social!

Come sempre, grazie di avermi seguito fino a qui e, se vi è piaciuto questo video e se vi piacciono questi argomenti, iscrivetevi al mio canale YouTube!

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< / rawhtml >}}

Alla prossima, vi aspetto... MITICI!