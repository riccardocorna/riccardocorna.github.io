---
date: 2024-01-31T05:00:00-00:00
description: "Iniziamo ad introdurre il laboratorio che sto costruendo, basato su Microsoft Entra, Active Directory, Microsoft Intune, Microsoft 365 e Microsoft Defender for Endpoint."
featured_image: "/images/01-the-lab-episodio-0-introduzione.jpg"
images:
  - "/images/01-the-lab-episodio-0-introduzione.jpg"
categories : [ "Identity & Security" ]
tags: [ "The Lab", "Introduzione", "Episodio 0" ]
title: "The Lab - Episodio 0 - Introduzione al laboratorio"
url: /the-lab-episodio-0-introduzione
---
Specialisti IT, ciao a tutti! Non ci vediamo da un po’ in video ma, nonostante tutto, in questi mesi di assenza ho tramato nell’ombra portando avanti altri progetti e iniziative, di cui vedrete i risultati sui miei canali e sulla community Microsoft Security Italian Users Group. 😉

Bando alle ciance però, non è questo né il video né la giusta occasione per raccontarvi il perché, il percome, eccetera eccetera: se state vedendo questo video, è perché siete degli assatanati di tutto quello che riguarda Microsoft Entra, Intune, Active Directory, Microsoft 365 e, quindi, lasciamo da parte le storielle e cominciamo a vedere... LA CICCIA!

## Video
Trovate l'intero video qui sotto, altrimenti potete continuare a leggere l'articolo.

{{< youtube 80OXHAhVQhk >}}

## Introduzione

Intorno a fine anno 2023, ho pubblicato un post in cui, in maniera del tutto innocente, vi raccontavo di voler ricostruire il mio laboratorio ibrido, per testare una serie di cose.

Ingenuamente, vi ho domandato se foste interessati a vedere qualche video preso durante la costruzione del lab.

È proprio qui che è successo il patatrac...

Non l’avessi mai fatto! Nella mia testa pensavo “Ma sì è un laboratorio, figurati se interessa a qualcuno”..., davvero, la ritenevo una cosa molto poco interessante. E invece più di 100 di voi hanno espresso un interesse esplicito verso questo argomento, anzi, vi dirò di più, credo che sia uno dei post più visti del 2023!

E quindi... potevo deludervi? Ovviamente NO e, quindi, ecco l’idea! 

A differenza dei miei video passati, non più dei video slegati tra di loro che parlano di vari argomenti a macchia di leopardo ma una serie, un vero e proprio percorso di video legati da un sottile filo: la costruzione di un ambiente, fatta insieme a voi passo per passo.

Quindi, vediamo che cosa stiamo andando a costruire!

## Come sarà fatto questo laboratorio?

Prima di tutto, ho deciso di costruire un laboratorio IBRIDO, con un’Active Directory on-premises. Questo può sembrare controintuitivo ma, in realtà, credo che avere un laboratorio ibrido sia la scelta più utile per voi per me, che vedere-persone-testare-cose e, soprattutto, per voi specialisti IT che mi seguite!

## Perché un laboratorio ibrido?

Perché? Perché, nonostante la direzione intrapresa da Microsoft e dal mercato ci porti inesorabilmente verso il cloud, verso la riduzione della dipendenza da infrastrutture on-premises, eccetera, prima di gridare “Il cloud, il cloud!” bisogna considerare alcuni elementi chiave.

Aziende e, più in generale, realtà nate negli ultimi anni, e tutte quelle che nasceranno da qui (anno 2024) in avanti, hanno già tutto apparecchiato per essere “cloud first”.

Il tessuto dei sistemi informativi delle aziende italiane, però, dalla piccola/media realtà fino a quelle più grandi e strutturate, 10,15,20 anni fa hanno fatto un investimento in una o più infrastrutture on-premises, in molti casi basate su Active Directory e altri prodotti Microsoft o non Microsoft.

Significa quindi che, come specialisti IT, noi abbiamo un compito delicatissimo e importantissimo: guidare, aiutare, prendere per mano tutte queste realtà e portarle verso questo pazzo mondo cloud, tenendo conto dell’eredità tecnologica che si portano e che ancora sta facendo il suo dovere.

Quindi, lo spirito di questo laboratorio è quello di provare insieme ad iniziare a pensare un modo per ridurre la dipendenza da Active Directory, implementando e testando quello che abbiamo a disposizione oggi e che avremo a disposizione man mano che nuovi strumenti verranno rilasciati.

## Microsoft Entra Kerberos, il fulcro del lab

Perfetto, facciamo il secondo passo, quello più interessante secondo me: l’Active Directory mi servirà solo per sincronizzare gli utenti (tramite Entra Connect) e per joinare eventuali server. Fine.

Quindi, nessun client Windows 10/11 verrà joinato a questo dominio on-prem. I dispositivi degli utenti finali verranno joinati direttamente in cloud, su Microsoft Entra.

Per dirla in altre parole, i dispositivi degli utenti saranno Entra Joined.

Pensate: tutti i PC degli utenti potrebbero, potenzialmente, essere gestiti ovunque si trovino e, quando in rete aziendale, potrebbero accedere alle risorse o alle applicazioni on-premises a dominio, in maniera trasparente e come se anche loro lo fossero.

## Cosa vedrete e cosa non vedrete

Perfetto, quindi, dopo tutta questa introduzione filosofica, come andiamo avanti e quali sono i prossimi passi? Cosa vedrete e cosa non vedrete?

Vedremo insieme come costruire questo tipo di ambiente ibrido, dal punto di vista dell’identità e della sicurezza. 

Vedremo come installare un domain controller e alcuni elementi di sicureza basilari su AD, vedremo come installare e configurare un Entra Connect.

Metteremo in sicurezza le identità e le risorse con MFA e Conditional Access.

Joineremo i dispositivi Windows ad Entra, li gestiremo con Intune, li metteremo in sicurezza con Microsoft Defender for Endpoint.

Con questi client proveremo ad accedere a risorse on-premises pur non essendo essi a dominio.

E poi... cosa vedremo?

La risposta è “non lo so”, perché, potenzialmente, le cose da vedere sono infinite.

Ma, se c’è qualcosa che vi stuzzica, se c’è qualche configurazione, qualche feature che vi incuriosisce vedere all’opera (ovviamente considerando i limiti che un ambiente di lab può avere), non vi resta che lasciare un commento, qui, su Linkedin o su Threads.

## Conclusioni

Non vedo l’ora di fare questo percorso insieme e di iniziare a costruire questo laboratorio: dopo questa chiacchierata introduttiva, vedremo insieme come installare un Domain Controller creando una nuova foresta e quindi non perdetelo perché inizieremo finalmente a mettere le mani in pasta!

Come sempre, grazie di avermi seguito fino a qui. Se vi è piaciuto questo video e se vi piacciono questi argomenti, iscrivetevi al mio canale YouTube e seguitemi sul mio blog ITSpecialist.cloud

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< / rawhtml >}}

Alla prossima, vi aspetto... MITICI!
