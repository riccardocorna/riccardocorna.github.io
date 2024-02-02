---
date: 2024-02-14T05:00:00-00:00
description: "Finalmente iniziamo a mettere davvero le mani su questo laboratorio: oggi, infatti, creiamo la foresta (e il dominio) Active Directory on-premises che ci serve per il nostro ambiente ibrido"
featured_image: "/images/01-the-lab-episodio-1-new-active-directory-forest.jpg"
images:
  - "/images/01-the-lab-episodio-1-new-active-directory-forest.jpg"
categories : [ "Identity & Security" ]
tags: [ "The Lab", "Active Directory", "Episodio 1", "Domain Controller" ]
title: "The Lab - Episodio 1 - Creare una nuova foresta di Active Directory"
url: /the-lab-episodio-1-nuova-foresta-active-directory
---
Specialisti IT, ciao a tutti! Finalmente iniziamo a mettere davvero le mani su questo laboratorio: oggi, infatti, creiamo la foresta (e il dominio) Active Directory on-premises che ci serve per il nostro ambiente ibrido.

## Video
Trovate l'intero video qui sotto, altrimenti potete continuare a leggere l'articolo.

{{< youtube NIYKflNX2BY >}}

## Prima di cominciare
Solo un paio di osservazioni.

Prima osservazione: come detto nello scorso video, quello che vi mostrerò nella costruzione del laboratorio, lo vedremo più dal punto di vista dell’identità (di utenti e di dispositivi) e della loro messa in sicurezza.

Tutto ciò che riguarda un corretto dimensionamento di Active Directory, tutto quello che è correlato a tematiche più “datacenter” e capacity, non verrà trattato in questa serie di video. Ci sono canali e risorse molto più a tema rispetto a quanto possa pubblicare io.

Per non lasciare comunque nulla di intentato, cercherò di lasciarvi tutti i link di approfondimento possibili e utili nelle descrizioni dei vari video.

Seconda osservazione: se ancora non fosse chiaro, questo è un laboratorio! Quindi, cosa significa? Significa che, per quanto io mi possa sforzare di seguire ogni best practice, potremmo non fare tutto “a puntino”, in maniera “super ortodossa”, questo per diverse ragioni.

1. Nonostante la sottoscrizione Azure ottenuta grazie allo status di MVP, non ho risorse infinite su Azure e, quindi, come tutti, devo cercare di ottimizzare le risorse di compute. Molto probabilmente, anzi, sicuramente, escludendo il domain controller che rimarrà dedicato, installerò diversi altri ruoli sulla stessa macchina. Chiaramente, tutto questo, nei limiti di compatibilità tra un servizio e l’altro e, ovviamente, non fatelo in produzione.

2.	Per mantenere vivo il lab, devo gestirlo e, come tutti, non impazzisco all’idea di gestire, nel tempo libero, un altro ambiente super-complesso oltre a quelli che vedo già quotidianamente.

3.	È un laboratorio con uno scopo abbastanza preciso (andate a recuperare il video di introduzione, se non l’avete visto, vi lascio il link qui sotto in descrizione) e quindi, per scelta puramente tecnica e anche editoriale, approfondirò solo gli aspetti utili e pertinenti allo scopo di questa serie

Ovviamente, se pensate che io abbia dimenticato qualcosa, scrivetelo nei commenti! Potrebbe essere un’idea da aggiungere a posteriori in questo lab!

## Setup ruolo Active Directory Domain Services
Perfetto, ci siamo! Ho già una macchina pronta su Azure, ha un paio di configurazioni interessanti lato Azure che vedremo dopo ma direi che siamo pronti per partire. 

Iniziamo col solito wizard di installazione del ruolo di Windows

{{< youtubestartend NIYKflNX2BY 179 222 >}}

## DCPromo
Perfetto, tutto bene, ora facciamo la cosa più croccante: creiamo una nuova foresta di Active Directory, con livello funzionale Windows Server 2016, il più alto e recente a disposizione nel momento in cui sto girando questo video.

> **NOTA:** con la prossima release di Windows Server 2025, mi aspetto novità anche dal punto di vista dei livelli funzionali.

### Scelta del FQDN: routable o non routable?
Come vedrete, ho scelto un FQDN non routable e diverso dal dominio effettivo che useremo pubblicamente: questo, a mio modo di vedere, ci evita alcune rotture di scatole nella gestione del DNS e degli UPN. 
Se volete approfondire questo aspetto vi ho lasciato un link qui sotto in descrizione per chiarire ogni dubbio a riguardo!

{{< youtubestartend NIYKflNX2BY 313 335 >}}

### Scelta della password di Directory Service Restore Mode
Mi raccomando scegliete una password di Directory Service Restore Mode sicura, annotatela e conservatela al sicuro. 

In un ambiente di produzione, tipicamente si conserva in cassaforte o in un repository sicuro di password, ad esempio un CyberArk o simili.

{{< youtubestartend NIYKflNX2BY 362 381 >}}

### Dove posizionare database, log, SYSVOL
Dove posizionare DB, log e le varie cartelle di AD? Io, su questa macchina, ho un secondo disco, metto tutto lì.

Come esperienza sul campo, posso dire di aver visto ogni tipo di approccio: qualcuno lo fa, qualcuno mette tutto su C:, dipende da molte cose.

Ho fatto così perché credo sia una buona pratica e anche perché, essendo il mio DC su Azure, c’è una questione legata all’host caching che non piace moltissimo ad Active Directory e, quindi, voglio essere sicuro di avere un disco senza host caching. 

Vi faccio vedere al volo l’impostazione sul portale di Azure.

{{< youtubestartend NIYKflNX2BY 421 428 >}}

### Conclusione DCPromo
Ora andiamo avanti con la DCPROMO e concludiamola!

{{< youtubestartend NIYKflNX2BY 433 469 >}}

Perfetto, il server si è riavviato e noi abbiamo quasi finito questa prima fase!

## Subnet e siti di Active Directory
Faccio solo un ultimo settaggio sui siti di Active Directory: io ne ho solo uno uno solo ma voglio comunque farlo, e aggiungerò lo spazio di indirizzi IP della nostra virtual network.

{{< youtubestartend NIYKflNX2BY 487 499 >}}

## Creazione alberatura Organizational Unit
Perfetto, ora siamo pronti per creare qualche Organizational Unit!

Chiaramente, mi sono inventato di sana pianta l’alberatura logica, mettendo delle OU che, tipicamente, ci sono quasi ovunque ma che, fatte in questo modo, potrebbero esserci molto utili per il tiering di Active Directory.

Vediamo!

{{< youtubestartend NIYKflNX2BY 520 574 >}}

## Impostazione DNS per la virtual network di Azure
Ultima cosa, lato Azure: imposto come DNS dell’intera Virtual Network l’indirizzo privato del mio domain controller.

Così facendo, ogni altro server che creerò in questa virtual network, userà fin da subito il nostro domain controller come server DNS.

Chiaramente, questa è una configurazione che fa comodo a me in quanto laboratorio: in produzione potreste avere una topologia di rete totalmente diversa, quindi, fate le opportune verifiche prima di impostare una cosa del genere.

{{< youtubestartend NIYKflNX2BY 606 612 >}}

## Conclusione
Perfetto, direi che ci siamo! Nel prossimo video, vedremo l’installazione della Certification Authority perché è obbligatorio, dal mio punto di vista, implementare LDAPS, fin da subito!

Come sempre, grazie di avermi seguito fino a qui. Se vi è piaciuto questo video e se vi piacciono questi argomenti, iscrivetevi al mio canale YouTube e seguitemi sul mio blog ITSpecialist.cloud

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< / rawhtml >}}

Alla prossima, vi aspetto... MITICI!