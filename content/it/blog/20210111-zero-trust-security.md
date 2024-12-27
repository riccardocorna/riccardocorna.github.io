---
date: 2021-01-11T08:00:00-00:00
description: "Il modello Zero Trust Security: cos'è, come funziona, motivi per cui adottarlo e perché è fondamentale per un vero Modern Workplace"
featured_image: "/images/01-Zero-Trust-Security-General-Diagram.png"
categories: [ "Identity & Security"]
tags: [ "Zero Trust Security" ]
title: "Modello Zero Trust Security: cos’è, come funziona, perché adottarlo"
url: "/zero-trust-security"
---
In questo pazzo mondo cloud, si sente parlare sempre più spesso di Zero Trust Security. Questo concetto esiste da alcuni anni ma solo ora si vede sul campo una sua applicazione diffusa e sempre più necessaria. Scopriamo cos’è la Zero Trust Security, come funziona e perché è uno dei fondamenti del [Modern Worplace](/cosa-significa-modern-workplace/) e del [Modern Management](/modern-workplace-management/).

[![Zero Trust Security principles](/images/01-Zero-Trust-Security-General-Diagram.png)](/images/01-Zero-Trust-Security-General-Diagram.png)

## Cos’è la Zero Trust Security
Per capire meglio il significato di questo termine, cominciamo col tradurlo in Italiano, letteralmente: “Sicurezza a fiducia zero”. Suona male o, più semplicemente, suona un po’ strano perché non siamo più abituati a tradurre i termini tecnici dall’Inglese alla nostra lingua.

Questo però è di gran lunga il modo più semplice per comprendere il principio guida che sta dietro: “sicurezza a fiducia zero” significa approcciare la sicurezza della propria infrastruttura partendo dal presupposto che non esistono luoghi o reti sicure, non ci si fida di nessun dispositivo e di nessuna utenza e l’accesso alle risorse viene continuamente verificato, indipendentemente dal fatto che avvenga dall’interno della rete aziendale o meno.

Torno all’inglese e provo a definirla in maniera molto più stringata ma altrettanto chiara:

{{< rawhtml >}}
  <p class="tc f2">"Never Trust, always verify"</p>
{{< / rawhtml >}}

Ok? Perfetto, ora che sai cosa significa Zero Trust Security, vediamo perché questo approccio è diventato fondamentale in un mondo cloud.

## Perché adottare un modello Zero Trust Security
Fino ad oggi, la sicurezza IT in ambito aziendale è sempre stata approcciata in maniera perimetrale. Semplificando, questo significa che, nella maggior parte dei casi, l’idea di base era la seguente:

> *Fiducia piena di quanto avviene all’interno della rete e dell’infrastruttura gestita, fiducia zero di tutto ciò che viene dall’esterno.*

Il perimetro quindi era la rete.
E quindi, perché oggi non è più possibile fare questo ragionamento?
**Perché l’avvento del cloud computing ha reso fruibili via Internet e da qualunque luogo, servizi che prima erano disponibili solo all’interno della rete aziendale.**

{{< rawhtml >}}
  <p class="tc f3 i">Le sole strategie di sicurezza basate sulla rete e sul suo perimetro, quindi, non sono più sufficienti ed è necessario aggiungere altre componenti all’equazione della sicurezza per la tua infrastruttura.</p>
{{< / rawhtml >}}

## Principi di Zero Trust Security
Ho già enunciato poco sopra il principio fondante che, da solo, è già sufficiente a spiegare la Zero Trust Security: “Never trust, always verify” ma ritengo sia utile esploderlo insieme a te, per capirne di più.

### 1. Verifica esplicita e continua
Anziché presupporre che tutto ciò che si trova dietro il firewall aziendale sia sicuro, ogni richiesta di accesso a risorse deve essere autenticata ed autorizzata valutando tutti gli elementi in gioco, sempre: identità dell’utente, caratteristiche del suo sign-in, dispositivi, servizio a cui viene richiesto l’accesso, classificazione dei dati.

### 2. Least Privileged Access
Ogni accesso alle risorse deve prevedere il minimo dei privilegi sufficienti e necessari per permettere alle persone di svolgere il proprio lavoro in maniera produttiva e sicura.

Le policy di accesso valutano criteri di rischio in tempo reale e calcolati attraverso un motore di intelligenza artificiale, che analizza dinamicamente comportamenti e condizioni degli accessi.

### 3. Assume breach
Comportati, ragiona e agisci come se una violazione sia già avvenuta. Applica i principi precedenti:
- **verifica esplicita e continua** per autenticare, cifrare, autorizzare gli accessi alle risorse;
- **least privileged access** per segmentare gli accessi in base all’identità, ai dispositivi, alla rete di provenienza, alle applicazioni, limitando i movimenti laterali.

Usa gli strumenti di analisi ed intelligenza messi a disposizione dal cloud per capire al meglio come reagire e come prevenire situazioni di minaccia.

## Componenti della Zero Trust Security
Perfetto, dopo aver visto la Zero Trust Security da un punto di vista “filosofico”, eccoci (finalmente) arrivati a quella che definirei “la ciccia” . Mettiti comodo perché questa parte è tanto tosta quanto importante.

Per dirla in poche parole, l’elenco delle componenti che vedrai ora è composto dalle risposte a queste domande:
- **Che cosa devi difendere?**
- **Come applicare i principi di Zero Trust Security a ciò che devi proteggere?**

Sei pronto? Andiamo!

### Identità

[![Multi Factor Authentication](/images/02-Zero-Trust-Security-Identity.png)](/images/02-Zero-Trust-Security-Identity.png)  
[![Conditional Access](/images/03-Zero-Trust-Security-Conditional-Access.png)](/images/03-Zero-Trust-Security-Conditional-Access.png)

Le identità rappresentano le persone e i servizi e sono la base di ogni accesso a dati, applicazioni, reti, infrastrutture.

Per mettere in sicurezza le identità in maniera efficace, la tua strategia di sicurezza dovrà prevedere di:

- verificare continuamente le identità con metodi di autenticazione forte come **Multi Factor Authentication** + **Conditional Access**;
- assicurarsi che l’accesso sia conforme e coerente per quell’identità, attraverso l’utilizzo di strumenti avanzati per concedere permessi e privilegi come **Privileged Identity Management**, **Just In Time**, i ruoli **RBAC** di **Azure AD** ed **Azure**, e via dicendo;
- prevedere una strategia di monitoraggio e reportistica dei sign-in sospetti, in modo da prevenire minacce o reagire velocemente in caso di intrusione o attacco, come **Azure Sentinel** o **Cloud App Security**.

➡ **Per approfondimenti**: [Securing Identity with Zero Trust](https://docs.microsoft.com/en-us/security/zero-trust/identity).

### Dispositivi

[![Dispositivi](/images/04-Zero-Trust-Security-Dispositivi.png)](/images/04-Zero-Trust-Security-Dispositivi.png)

I dati e le applicazioni della tua azienda sono acceduti e lavorati da una moltitudine di dispositivi, sia aziendali che (sempre più spesso) personali. Questa disomogeneità di configurazioni e del livello di update può creare gravi problemi di sicurezza e di gestione.

In un modello Zero Trust Security, qualunque dispositivo viene verificato di continuo, a prescindere dal fatto che sia personale o aziendale. Le policy di sicurezza vengono applicate in ogni situazione, su qualunque device e indipendentemente dal fatto che tu acceda dalla rete aziendale o meno.

Quali sono i punti da tenere in considerazione per proteggere i tuoi dispositivi in un modello Zero Trust Security?
- verifica continua dello stato di salute e della compliance, ad esempio attraverso **Microsoft Endpoint Manager**;
- le applicazioni installate devono essere aggiornate e rispettare i vincoli di conformità;
- i dispositivi devono essere messi in sicurezza rapidamente in caso di compromissione;
- l’identità del dispositivo deve essere verificata ancora prima di accedere a dati e applicazioni aziendali.

➡ **Per approfondimenti**: [Securing Endpoints with Zero Trust](https://docs.microsoft.com/en-us/security/zero-trust/endpoints).

### Applicazioni

[![Applicazioni](/images/05-Zero-Trust-Security-Applicazioni.png)](/images/05-Zero-Trust-Security-Applicazioni.png)

Identità e dispositivi accedono alla tua infrastruttura principalmente per utilizzare applicazioni.

Azure AD offre molti strumenti per registrare e mettere in sicurezza ogni tipo di applicazione aziendale insieme alle sue API. Cosa devi considerare per ottenere una protezione efficace?
- verificare di continuo i permessi, ovvero “chi può fare cosa su quale risorsa”;
- valutare in tempo reale parametri di rischio per limitare l’accesso;
- monitorare e tenere sotto controllo comportamenti e azioni anomale degli utenti sulle applicazioni
- monitorare continuamente l’ambiente applicativo per verificarne conformità e configurazioni.

➡ **Per approfondimenti**: [Securing Applications with Zero Trust](https://docs.microsoft.com/en-us/security/zero-trust/applications).

### Dati

[![Dati](/images/06-Zero-Trust-Security-Dati.png)](/images/06-Zero-Trust-Security-Dati.png)

La protezione dei dati è di primaria importanza ed è necessario fare in modo che questi vengano protetti sempre e ovunque: quando li si usa, quando vengono archiviati e, idealmente, anche quando vengono “spostati” dal loro luogo di nascita per essere condivisi attraverso altre reti, dispositivi, organizzazioni.
I dati devono anche essere censiti, classificati, etichettati, in modo da poterli proteggere da accessi o utilizzi non autorizzati.

Come mettere in atto una strategia di successo per la sicurezza dei tuoi dati?
- **conosci i tuoi dati**: dovrai censirli per comprendere esattamente che tipo di dati possiedi e quali hanno bisogno di più protezione;
- **proteggi i tuoi dati e previeni una loro eventuale perdita**: assicurati che solo chi è autorizzato ad accedere ai dati possa farlo e metti in atto strategie proattive per evitare la loro perdita;
- **monitora i tuoi dati e gestiscili**: esegui azioni continue di monitoraggio, verifiche e reportistica in modo da rilevare violazioni delle regole aziendali e avere tutti gli elementi per intraprendere azioni proattive e correttive.

➡ **Per approfondimenti**: [Securing Data with Zero Trust](https://docs.microsoft.com/en-us/security/zero-trust/data).

### Infrastruttura

[![Infrastruttura](/images/07-Zero-Trust-Security-Infrastruttura.png)](/images/07-Zero-Trust-Security-Infrastruttura.png)

Cosa significa esattamente “infrastruttura”? Questo termine racchiude moltissimi componenti ed è l’insieme di hardware, software, servizi, reti che compongono il tuo ambiente, siano essi fisici o virtuali. È quindi necessario e vitale proteggere tutti questi elementi e, in un modello Zero Trust Security, puoi facilitarti la vita con diversi strumenti come ad esempio **Azure Policies**, **Azure Security Center**, **Azure Sentinel**, ed **Azure Sphere**, attraverso i quali potrai ottenere diversi risultati:
- gestire le configurazioni infrastrutturali del tuo ambiente, avendole sempre sotto controllo
- concedere privilegi con scadenze temporali definite (Just In Time), assegnando permessi con ambiti ben definiti (RBAC);
- monitorare continuamente parametri di telemetria dei tuoi server, per rilevare segnali anomali;
- rilevare e bloccare automaticamente comportamenti rischiosi, prendendo le opportune contromisure.

➡ **Per approfondimenti**: [Securing Infrastructure with Zero Trust](https://docs.microsoft.com/en-us/security/zero-trust/infrastructure).

### Rete

[![Rete](/images/08-Zero-Trust-Security-Rete.png)](/images/08-Zero-Trust-Security-Rete.png)

La rete è sicuramente la componente più impattata da questo approccio di sicurezza zero trust: una volta era l’unico perimetro, ora non lo è più. Come cambiano le strategie di sicurezza e protezione in questo modello che ti sto raccontando? Come già accennato, cambia un assunto di base fondamentale: **ciò che è dietro il firewall aziendale, non deve essere più considerato sicuro, perché le tue risorse (utenti, dispositivi, app, dati) non sono più contenute esclusivamente al suo interno**.

Per adeguarti a questo nuovo paradigma, devi considerare le seguenti azioni sulla tua rete:
- creazione di micro-perimetri e segmentazione di alcuni ambiti infrastrutturali, applicativi e di rete, secondo il modello [Hub and Spoke](/topologia-di-rete-hub-spoke-azure/);
- cifrare, monitorare, filtrare anche il traffico di rete interno;
- rivedere secondo nuove logiche i perimetri della tua rete verso l’esterno.

➡ **Per approfondimenti**: [Securing Networks with Zero Trust](https://docs.microsoft.com/en-us/security/zero-trust/networks).

## Conclusioni sulla Zero Trust Security
Ora che ti ho raccontato cosa significa mettere in sicurezza la tua infrastruttura in questo pazzo pazzo mondo cloud, vorrei ringraziarti per avermi seguito fino a qui. È un articolo lungo, tosto, denso che ha richiesto tutta la tua attenzione per diverse decine di minuti. **Grazie**.

Come sempre, sarei davvero felice di fare quattro chiacchiere insieme a te sulla tua infrastruttura, per sapere se hai già abbracciato questo modello di sicurezza o se stai pensando di farlo. Ti aspetto nei commenti o sui miei social per parlarne insieme! A presto 🙂

Il tuo IT Specialist, Riccardo