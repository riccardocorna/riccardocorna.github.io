---
date: 2024-06-05T05:00:00-00:00
description: "Oggi vediamo il primo risultato concreto della costruzione del nostro laboratorio ibrido ispirato ad una gestione moderna di identità e dispositivi: testeremo insieme se un PC Windows Entra Joined può accedere in single sign-on ad una risorsa on-premises, in particolare ad un file server."
image: "01-the-lab-episode-5-sso-on-prem-windows-entra-joined-pc.jpg"
categories : [ "Security", "Modern Work" ]
tags: [ "Single Sign-On", "Active Directory", "Microsoft Entra", "Windows", "Entra Join", "Video", "The Lab" ]
title: "The Lab - Episodio 5 - SSO su risorse on-premises di un PC Windows Entra Joined"
url: /the-lab-episode-5-sso-on-prem-windows-entra-joined-pc
---
Oggi vediamo il primo risultato concreto della costruzione del nostro laboratorio ibrido ispirato ad una gestione moderna di identità e dispositivi: testeremo insieme se un PC Windows Entra Joined può accedere in single sign-on ad una risorsa on-premises, in particolare ad un file server.

Funzionerà? Lo vedrete nel video :)

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube vmAxRlVrh1o >}}

## SSO su risorse on-premises di un PC Windows Entra Joined

### Introduzione
Specialisti IT, ciao a tutti! Abbiamo iniziato da un po’ di tempo la serie The LAB: insieme, abbiamo costruito un laboratorio di un ambiente ibrido pressoché completo.

Un domain controller Active Directory, una Certification Authorithy, abbiamo visto come implementare LDAPS e, infine, come sincronizzare le identità di Active directory on-premises su Entra ID, per ibridare con il cloud la nostra infrastruttura.

Questo di oggi è **IL** video in cui vediamo il primo risultato concreto del nostro lavoro.

Proveremo infatti ad accedere ad una cartella di rete di un file server on-premises, joinato normalmente a dominio, da un PC Windows 11 Entra Joined.

Il PC, quindi, è joinato direttamente in cloud a Microsoft Entra, non al dominio on-premises.

Perché ci tengo tanto che funzioni e tengo ancora di più a farvelo vedere?

1. Perché l’esperienza sul campo mi suggerisce che in pochissimi sono a conoscenza del fatto che questo tipo di single sign on è possibile nativamente, out-of-the box.
2. Perché questo, a mio modo di vedere è un passo fondamentale nel ridurre la dipendenza dall’active directory on-premises, almeno per i dispositivi Windows degli utenti finali.
3. Perché questo era uno degli scopi dichiarati di questo laboratorio: gestire i client in maniera cloud-native senza metterli a dominio

Funzionerà? Vediamolo insieme, partendo dai requisiti e dalla descrizione dello scenario.

### Requisiti
Iniziamo, appunto, dai requisiti:
- un PC Windows, in questo caso Windows 11, Entra Joined, ovvero joinato direttamente ad Entra Id: ce l’abbiamo
- aver ibridato Active Directory con Entra Id attraverso Microsoft Entra Connect: fatto!
- il PC, per poter accedere al file server, deve essere in visibilità di rete con il domain controller e, chiaramente, anche con il file server stesso.

***ATTENZIONE***: *non bisogna confondere autenticazione con raggiungibilità di rete! Noi ora stiamo testando che un PC non joinato a dominio possa accedere, autenticandosi, ad un file server di dominio ma, testandolo in questo modo, stiamo simulando una situazione ben precisa: il PC, pur non essendo a dominio, è però in rete aziendale.*

Riassumendo: oggi il nostro utente è in ufficio, ok?

Questo cosa significa? Che, se provassimo a fare questo stesso test da una rete che non sia quella aziendale, di sicuro non riusciremmo ad accedere al file server interno, a meno di avere una VPN, o altre soluzioni, o bla bla bla.

### Verifica dello scenario
Detto questo, facciamo tutte le verifiche del caso: non c’è trucco, non c’è inganno!

#### Verifica hostname del PC Windows
Iniziamo a vedere come si chiama il nostro PC di test

{{< youtubestartend vmAxRlVrh1o 173 184 >}}

#### Verifica join a dominio on-prem
Perfetto, ora verifichiamo che NON sia joinato al dominio on-premises itspecialist.local ovvero la nostra Active Directory di The LAB.

{{< youtubestartend vmAxRlVrh1o 193 205 >}}

Ok, non l’abbiamo trovato.

#### Verifica Entra Join
Andiamo a cercarlo su Microsoft Entra.

{{< youtubestartend vmAxRlVrh1o 209 222 >}}

Trovato! È lui il nostro PC Entra Joined.

#### Verifica stato con dsregcmd
Non ci credete ancora? Facciamo la prova del 9 direttamente sul dispositivo verificandone lo stato di registrazione con l’apposito comando dsregcmd

{{< youtubestartend vmAxRlVrh1o 236 254 >}}

#### Verifica visibilità del domain controller
Per essere sicuri sicuri che lo scenario sia chiaro, ovvero farvi capire che l’utente oggi è in ufficio, vediamo se riesco a pingare il domain controller...

{{< youtubestartend vmAxRlVrh1o 264 271 >}}

#### Verifica raggiungibilità del file server
E se riusciamo a pingare il nostro file server.

{{< youtubestartend vmAxRlVrh1o 275 283 >}}

### Proviamo il Single Sign-On!
Ok! Siamo arrivati al momento della verità!

Ora, finalmente, dopo mesi di costruzione del nostro lab, vediamo finalmente se il nostro PC joinato in cloud riesce ad accedere senza battere ciglio ad un file server on-premises...

{{< youtubestartend vmAxRlVrh1o 301 321 >}}

Ebbene sì, l’abbiamo fatto. Abbiamo fatto il primo passo per ridurre la dipendenza da Active Directory e, ora, possiamo iniziare a spiccare il volo verso una vera gestione moderna e cloud native dei dispositivi degli utenti.

### Scenari supportati di SSO su risorse on-prem
Quindi, in definitiva, su cosa può fare SSO un dispositivo Entra Joined, quando si tratta di risorse on-premises?

Al momento, sono completamente coperti due scenari:
- accesso ad un path UNC su un server membro di dominio, quindi, ad esempio, il file server.
- accesso ad un server web di dominio configurato con autenticazione Windows Integrated.

Ci sono quindi alcune limitazioni di cui potrete approfondire i dettagli attraverso la solita tonnellata di documentazione qui sotto:

🔗 [What is a Microsoft Entra Joined device?](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join)  
🔗 [How SSO to on-premises resources works on Microsoft Entra joined devices](https://learn.microsoft.com/en-us/entra/identity/devices/device-sso-to-on-premises-resources)

### Conclusioni
Come sempre, ho cercato di farvi vedere i punti salienti di tutto quello che serve per ottenere questo risultato: per arrivarci nella vostra infrastruttura di produzione è necessaria un’analisi approfondita, specialmente a livello applicativo!

L’autenticazione applicativa, specialmente se si appoggia all’Active Directory on-premises, è la questione più importante da smarcare in qualunque progetto evolutivo che coinvolga in qualche modo l’autenticazione, sia utente che dispositivo.

Detto questo, cosa sarà ora di The LAB?

Andremo avanti a configurare il nostro ambiente: autenticazioni forti, Conditional Access, Password Protection, enrollment dei dispositivi in Intune, onboarding dei dispositivi su Defender for Endpoint, insomma continueremo ad espandere il nostro laboratorio come una città di Sim City, oppure... potremmo porci un obiettivo ancora più ambizioso!

Se, come me, volete conquistare e dominare il mondo del cloud, continuate a seguire questa serie e, se non lo siete ancora, iscrivetevi al mio canale YouTube o seguitemi su LinkedIn e su Instagram.

Trovate tutti i riferimenti sul mio blog ITSpecialist.cloud.

Alla prossima, vi aspetto... MITICI!