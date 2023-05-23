---
date: 2023-05-24T05:00:00-00:00
description: "Come gestire la membership dei gruppi locali dei PC joinati ad Azure AD? In questo video vediamo come funziona la policy di Local User Group Membership nell'ambito dell'Account Protection su Intune. Inoltre, alcune dritte per convertire facilmente ObjectId e SID di gruppi e di ruoli Azure AD."
featured_image: "/images/01-intune-account-protection-local-user-group-membership-cover.png"
categories : [ "Modern Endpoint" ]
tags: [ "Intune", "Azure AD Join", "Local Administrators" ]
title: "Intune Account Protection: Local user group membership"
url: /intune-account-protection-local-user-group-membership
---
Specialisti IT, ciao a tutti! Dopo che nello scorso video ho giocato con [il nuovo Windows LAPS](https://youtu.be/oGbAqOxJOhQ), stavo rivedendo la lista degli amministratori locali della mia macchina di laboratorio e, essendo la macchina registrata in Azure AD Join, l’utente di Azure AD che l’ha joinata è diventato amministratore. 

Questo è un comportamento normale e atteso che però... non ci piace 

Oltre a questo, di default, chiunque abbia ruolo di Global Admin o di Azure AD Joined Device Local Administrator, è amministratore di macchina. Come si può fare quindi per evitare che l’utente di una macchina joinata ad Azure AD diventi in pianta stabile amministratore di macchina? Più in generale, quali sono le opzioni che abbiamo in Azure AD per gestire gli amministratori locali di macchina? 

Ci sono alcune opzioni possibili: vediamole! 
1. Con Autopilot è possibile impostare nel profilo che, una volta joinata la macchina Windows ad Azure AD, l’utente sia standard. Bene, ma se, come nel mio caso, il PC non è sotto Autopilot, dobbiamo pensare ad altro. 
2. Possiamo usare l’opzione di gestione degli amministratori locali aggiuntivi, per intenderci quella che si trova nei Device Settings di Azure AD. Anche qui, però, prestiamo il fianco a qualche problema perché andiamo ad aggiungere altri amministratori che, inoltre, avranno accesso a tutte le macchine joinate ad Azure AD. L’impostazione, infatti, è globale e non è assegnabile ad un gruppo di macchine. 
3. Una policy Local User Group Policy che è possibile impostare da Account Protection, all’interno del nodo Endpoint Security di Intune.

Quest'ultima è la soluzione che ho scelto! Capiamo cosa si può fare e come funziona. Con questa soluzione possiamo modificare le membership gruppo locale per gruppo locale, aggiungendo o addirittura sostituendo le membership in essere con quello che vogliamo noi. Inoltre, possiamo aggiungere utenti locali di macchina già presenti (ad esempio quello del LAPS), utenti di directory, gruppi e persino ruoli di Azure AD. Infine, possiamo indirizzare e distribuire le policy per gruppi di macchine, andando a differenziare le impostazioni se necessario.

Insomma, sembra proprio quello che ci serve! 

Come accennato poco fa, possiamo gestire i gruppi locali inserendo utenti, gruppi e ruoli di Azure AD. Bisogna però fare attenzione al formato con cui si inseriscono queste voci: 
- Per gli utenti cloud: **AzureAD\username@dominio.com**
- Per gli utenti sincronizzati da AD on-premises: **DOMINIO\samAccountName** 
- Per i gruppi: bisogna usare il **SID** 
- Per i ruoli: bisogna usare il **SID** 

E qui viene il bello: per i gruppi è molto facile una conversione ObjectId – SID e viceversa, basta infatti dare in pasto uno dei due parametri ad uno script PowerShell o (come ho fatto io) ad un tool online. Se nella nostra policy vogliamo quindi inserire un gruppo, basta andare sul portale, convertire l’ObjectId in un SID e inserire il SID nella nostra policy. Per i ruoli di Azure AD, né il SID né l’ObjectId vengono esposti direttamente a portale. Se, ad esempio, volessimo mantenere tra gli amministratori chi ha il ruolo Azure AD Joined Device Local Administrator, come potremmo fare a verificarne il SID? 

Tra poco lo vediamo ma, come sempre, un piccolo accenno su come è fatto l’ambiente e su quello che vedrete esattamente e su cosa vogliamo ottenere. 

La mia è una macchina Windows 11 joinata ad Azure AD. 

Negli amministratori locali ci sono alcuni account su cui possiamo sorvolare, il mio utente standard con cui però ho fatto l’Azure AD Join (e che è amministratore) e, come vedrete, ci sono due SID. Uno è quello del ruolo Global Admin, l’altro è quello del ruolo Azure AD Joined Device Local Administrator. Come facciamo a sapere quale SID appartiene a quale ruolo? 

Tra poco lo scopriamo ma intanto vediamo come è configurata la macchina prima di implementare la policy! 

{{< youtubestartend wFiocHs-MQ4 253 280 >}}

L’elenco degli amministratori è quello che vi ho accennato prima. 

Ora, qual è la configurazione che voglio ottenere? Voglio che gli unici amministratori locali della macchina siano l’utente LAPS e chiunque abbia ruolo Azure AD Joined Device Local Administrator, fine! 

Una nota su questa configurazione: l’ho fatta così a puro scopo didattico, per mostrare che è possibile inserire anche i ruoli e per mostrare come trovare SID e ObjectId di un ruolo di Azure AD. A livello di sicurezza, fatta così, presta potenzialmente il fianco dei nostri PC a movimenti laterali, avendo aggiunto agli amministratori locali un intero ruolo di Azure AD, seppur non il Global Admin. Non è argomento di questo video discutere quali siano le possibili configurazioni perché ogni ambiente è diverso e ogni realtà ha le sue esigenze. Questo tipo di policy va sempre condiviso e concordato con il cliente o con chi di dovere, prima di essere messo in produzione. 

Di sicuro, però, possiamo pensare di:
- Togliere i Global Admin
- Inserire l’utente LAPS, che, tutto sommato, è l’Administrator built-in rinominato e quindi va inserito per forza altrimenti la policy va in errore 
- Se, eventualmente, decidete di lasciare il ruolo di Azure AD Joined Device Administrator come ho fatto io, si potrebbe pensare di metterlo sotto Privileged Identity Management (per intenderci, il PIM). 
 
Non racconterò di questa configurazione ora ma, se volete che io faccia un video a riguardo, lasciate un commento. 

Perfetto, ora vediamo quale dei due SID è il ruolo che abbiamo scelto per rimanere negli admin locali, lo convertiamo in un ObjectId e interroghiamo Microsoft Graph per verificare di aver preso il SID giusto! 

{{< youtubestartend wFiocHs-MQ4 280 439>}}

Mi è andata bene, ho scelto il ruolo giusto, quello col nome lunghissimo! 😉 Ora, non ci resta che implementare la policy di Intune. Prima, però, un’ultima precisazione.

All’interno delle policy abbiamo a disposizione 3 azioni: 
- Aggiungere in Update: specifichiamo chi aggiungere al gruppo e qualunque membro già esistente che non sia specificato nel nostro elenco, non verrà intaccato in alcuna maniera 
- Rimuovere in Update: specifichiamo chi togliere e, analogamente a prima, qualunque membro già esistente che non sia specificato nel nostro elenco, non verrà intaccato in alcuna maniera
- Aggiungere in Replace: qui andiamo ad impattare in maniera più pesante perché noi specifichiamo i membri del gruppo e il risultato finale sarà che qualunque membro già esistente che non sia nel nostro elenco verrà rimosso, quindi attenzione! 

Come dicevo prima, dal momento che siamo in un ambiente di laboratorio e abbiamo già fatto tutte le dovute considerazioni, aggiungo l’utente del LAPS e il ruolo Azure AD Joined Device Local Administrator in modalità Replace. 

Quindi cosa ci aspettiamo? Che tutti gli altri amministratori di macchina vengano spazzati via, compresi i Global Admin e il mio utente che ha joinato il PC ad Azure AD. Deve rimanere solo ciò che ho messo in elenco. 

Vediamo come impostare la policy! 

{{< youtubestartend wFiocHs-MQ4 521 603>}}

E ora vediamo cos’è successo ai nostri amministratori 

{{< youtubestartend wFiocHs-MQ4 608 626>}}

Perfetto, ha funzionato! Gli unici amministratori locali ora sono l’utente LAPS e chiunque abbia ruolo Azure AD Joined Device Local Administrator! 

Repetita Iuvant: questa che ho fatto è una configurazione piuttosto forte, prima di implementare una cosa simile in produzione fate tutte le verifiche e analisi del caso. 

Se volete approfondire l’argomento, come sempre, vi lascio un po’ di documentazione fresca e profumata di ammorbidente! 

E voi, cari specialisti IT, avete già usato questa policy? Se sì, come l’avete configurata? Parliamone insieme nei commenti o sui miei profili social!

E... a proposito di profili social, iscrivetevi al mio canale Youtube! Per me è molto importante, a voi non costa nulla e così sarete sicuri di non perdervi nemmeno un contenuto! Vi aspetto!  

A presto… MITICI! 

Riccardo