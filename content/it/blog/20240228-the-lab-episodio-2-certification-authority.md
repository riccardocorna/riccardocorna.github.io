---
date: 2024-02-28T05:00:00-00:00
description: "Oggi video velocissimo ma fondamentale: aggiungiamo il secondo pezzettino di laboratorio, mettendo in pista una Certification Authority."
featured_image: "/images/01-the-lab-episode-2-enterprise-certification-authority.jpg"
images:
  - "/images/01-the-lab-episode-2-enterprise-certification-authority.jpg"
categories : [ "Identity & Security" ]
tags: [ "The Lab", "Certification Authority", "Episodio 2" ]
title: "The Lab - Episodio 2 - Installare una Enterprise Certification Authority"
url: /the-lab-episodio-2-certification-authority
---
Specialisti IT, ciao a tutti! Oggi video velocissimo ma fondamentale: aggiungiamo il secondo pezzettino di laboratorio, mettendo in pista una Certification Authority.

## Video
Trovate l'intero video qui sotto, altrimenti potete continuare a leggere l'articolo.

{{< youtube 4U9W6x399Ms >}}

## Perché è utile una Certification Authority in laboratorio?
Ecco per quale motivo può esseere utile una Certification Authority in laboratorio:
1.	Perché una CA è sempre utile, a prescindere. 😊 
2.	Perché voglio implementare fin da subito LDAPS su Active Directory (e il prossimo video parlerà proprio di questo).
3.	Perché, più avanti nel laboratorio, voglio implementare la Certificate Based Authentication direttamente su Microsoft Entra.

## Consigli e risorse per disegnare una vera infrastruttura PKI
Come vedrete tra poco, andremo dritti al sodo senza troppi fronzoli. Non è scopo di questo video spiegare per filo e per segno quanti e quali tipi di Certification Authority esistono né approfondire in maniera completa come disegnare un’infrastruttura PKI.

Diciamo solo che, in un ambito di laboratorio, ci è più che sufficiente installare un’Enterprise CA da lasciare sempre attiva e a nostra disposizione.

**In un ambito di produzione, però, bisogna disegnarla molto più attentamente.**

Potrebbe essere un’infrastruttura a 2 o 3 tier, nei casi più complessi e, ultimo ma non ultimo accorgimento, è bene spegnere la Root CA e conservare il tutto in un luogo sicuro.

Ma, come dicevo, l’argomento è davvero troppo vasto per esaurirlo qui nel nostro laboratorio.

Quindi, per approfondire l’argomento, vi lascio una serie di bellissimi articoli di Microsoft Tech Community:!

- [Designing and Implementing a PKI: Part I Design and Planning](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-i-design-and-planning/ba-p/396953)
- [Designing and Implementing a PKI: Part II Implementation Phases and Certificate Authority Installation](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-ii-implementation-phases/ba-p/397198)
- [Designing and Implementing a PKI: Part III Certificate Templates](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-iii-certificate-templates/ba-p/397860)
- [Designing and Implementing a PKI: Part IV Configuring SSL for Web Enrollment and Enabling Key Archival](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-iv-configuring-ssl-for-web/ba-p/399104)
- [Designing and Implementing a PKI: Part V Disaster Recovery](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-v-disaster-recovery/ba-p/399106)

## Installazione e configurazione Active Directory Certificate Services
Come al solito, ho una macchina Windows Server 2022 Datacenter già pronta in Azure, con immagine smalldisk, l’ho joinata a dominio e quindi siamo pronti per installare e configurare il ruolo!

{{< youtubestartend 4U9W6x399Ms 117 214 >}}

Non ci crederete ma abbiamo già finito: la nostra CA è in piedi, pronta per essere utilizzata.

Dal momento che ora siamo pronti a sfornare certificati a pioggia, **nel prossimo video vedremo come implementare LDAPS su Active Directory**.

## Conclusioni
Come avrete notato, quello di oggi è stato un video velocissimo e, durante questa serie si alterneranno video più lunghi ad altri molto più veloci, a seconda di quello che dovremo implementare.

In ogni caso, grazie di avermi seguito anche in questo video e, se vi è piaciuto e se vi piace questo tipo di contenuti, iscrivetevi al mio canale YouTube: a voi non costa nulla ma, per me, è molto importante e fa tutta la differenza!

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< / rawhtml >}}

Alla prossima, vi aspetto... MITICI!

Il vostro IT Specialist,  
Riccardo