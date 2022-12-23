---
date: 2020-04-05T08:00:00-00:00
description: "Un concept su come usare Microsoft Teams in condominio per migliorare la collaborazione tra condòmini e la condivisione di informazioni utili."
featured_image: "/images/Microsoft-Teams-in-condominio-Featured-image.png"
categories: [ "Altro"]
tags: [ "Microsoft Teams", "Guida" ]
title: "[Concept] – Microsoft Teams in condominio ai tempi del Coronavirus"
url: "/concept-microsoft-teams-in-condominio"
---
Fermi tutti! So già che, immediatamente dopo aver letto il titolo, hai pensato: “*Rick, ti sei bevuto il cervello?!?*“.

**So che può sembrare folle una cosa del genere ed ero molto indeciso se scrivere questo articolo o meno ma poi ho pensato che:**
- **oggi avevo tempo e voglia di scrivere**
- **non dovevo uscire di casa** 😉
- **questo concept potrebbe essere utile in qualche modo!**

**E quindi mi sono detto: “Perchè no?!?”**

Ora che ti ho rassicurato sul fatto che non mi sono (ancora) definitivamente ammattito, possiamo cominciare 🙂

Come moltissime altre persone, anch’io abito in un condominio. Sono fortunato, i vicini di casa sono fantastici e c’è un bel rapporto anche con tutto il resto della scala: abbiamo persino un gruppo Whatsapp di scala in cui si parla, ci si chiede l’un l’altro piccoli favori, si condividono anche alcune comunicazioni “ufficiali” condominiali. Insomma, si comunica e si condividono idee, foto e altri dati, quasi come un gruppo di lavoro!

Ed è proprio quando ho realizzato quest’idea che l’altro giorno mi si è accesa una lampadina in testa: “**E se usassi Microsoft Teams in condominio per migliorare ulteriormente le conversazioni e condividere documenti e informazioni utili?**”.

Ebbene sì, questa quarantena forzata mi ha fatto malissimo alla testa e l’ho creato 🙂 Siamo ancora in fase di test ma credo che abbia le potenzialità per funzionare.

Sei pronto a vedere come sfruttare al massimo Microsoft Teams in condominio per migliorare la comunicazione e la collaborazione? OK, si comincia!

## Fase 1 – Utenti e licenze
Il tutto è ospitato sul mio tenant Office 365 personale con licenza **Office 365 Business Essentials** (che dal 21 Aprile 2020 cambierà nome in [Microsoft 365 Business Basic](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/30/new-microsoft-365-offerings-small-and-medium-sized-businesses/)).

Ovviamente non ho comprato licenze per tutti i condòmini. 🙂 Il team è ospitato sul mio tenant personale di Office 365 e quindi **tutti i condòmini sono dei guest di Azure AD**: sono conscio del fatto che sia una soluzione “quick & dirty” e che costringa tutti i guest che ne sono sprovvisti a registrarsi un Microsoft Account ma volevo “mettere a terra” l’idea del team in maniera molto rapida e questa era la via più immediata.

Puoi fare pre-staging dei guest in Azure AD e aggiungerli successivamente oppure, se le impostazioni del tuo tenant lo permettono, puoi aggiungerli direttamente da Teams: ci penserà lui a creare l’utente guest sul tenant.

## Fase 2 – Verifica del guest access
Verifica che l’accesso ai guest sia attivo per la tua organizzazione di Teams. Per farlo è sufficiente andare sul [portale amministrativo di Teams](https://admin.teams.microsoft.com/), navigare fino alla sezione Org-wide settings e abilitare l’apposita opzione.

[![Impostazione del guest access in Microsoft Teams](/images/00-Microsoft-Teams-in-condominio-requisiti-gues-access.png)](/images/00-Microsoft-Teams-in-condominio-requisiti-gues-access.png)

## Fase 3 – Struttura del condominio e del team
Il condominio dove abito è struttrato in questo modo:
- 3 palazzi;
- 2 scale per ogni palazzo (D/E, F/G, H/I).

Ho quindi immaginato questa struttura per il team:
- **il team corrisponde all’intero condominio** e quindi ne porta anche il nome;
- il canale ***General*** del team sarà usato **solo per le comunicazioni più “istituzionali” e di interesse generale/condominiale**;
- per le scale ho deciso di sfruttare una funzionalità relativamente nuova di Teams: il Private Channel; **ogni scala quindi è un canale privato di Teams all’interno del quale inserirò solo le persone che abitano in una certa scala**; ho scelto questa soluzione perchè attualmente è così che funziona nel mio condominio, ovvero ogni scala ha un gruppo Whatsapp;
- **il team è rigorosamente privato e ci si può entrare solo su invito**.

Ecco la struttura realizzata.

[![Microsoft Teams in condominio: struttura del team](/images/01-Microsoft-Teams-in-condominio-Struttura-Team.png)](/images/01-Microsoft-Teams-in-condominio-Struttura-Team.png)

## Fase 4 – Impostazioni del team
Perfetto, ora puoi cominciare a mettere davvero le mani dentro il team. Ecco le configurazioni che ho pensato per il team, una per una:

- **Immagine del team**: una bella foto del condominio è il minimo, no? 😉
- **Permessi dei membri**: in realtà non abbiamo “member” nel vero senso della parola perchè tutti gli utenti (tranne me) sono dei guest senza licenza e quindi queste impostazioni non avranno effetti sui guest che appartengono al team; come buona pratica ho comunque **ristretto** i seguenti permessi:
    - creare e ripristinare canali;
    - aggiungere e rimuovere app;
    - aggiungere e rimuovere le tab;
    - aggiungere e rimuovere i connettori;
- **Permessi dei guest**: ho inibito ai guest la possibilità di creare, aggiornare, cancellare i canali;
- **Menzioni**: al momento ho lasciato la possibilità a tutti di menzionare team e canale;
- **Codice del team**: non ho creato alcun codice per joinare automaticamente il team;
- ho lasciato libera la possibilità di usare le GIF, con filtro impostato su “Moderato”;
- solo l’owner del team può definire i tag.

Ecco la configurazione implementata!

[![Microsoft Teams in condominio: impostazioni team](/images/02-Microsoft-Teams-in-condominio-impostazioni-team.png)](/images/02-Microsoft-Teams-in-condominio-impostazioni-team.png)

## Fase 5 – Canale General
Ho pensato al canale General come il luogo perfetto per comunicazioni “istituzionali” e annunci di interesse generale che riguardino tutto il condominio e non le singole scale. Alcuni esempi:
- annunci di iniziative condominiali;
- condivisione di dati depositati nella document library del team come ad esempio preventivi, consuntivi, altri documenti (dopo ti spiego nel dettaglio la parte della document library).

Inizialmente avevo pensato di restringere ai soli owner del team la possibilità di pubblicare nel canale General e di dare questo privilegio ai consiglieri. Purtroppo però i guest del team non possono diventare owner e quindi ho optato per una configurazione del canale General dove **gli utenti vengono avvisati che qualunque cosa si scrive qui è pubblica e visibile a tutti i membri del team (e quindi a tutti i condomìni)**.

[![Tutto quello che scriverai sul canale General sarà pubblico e visibile a tutti](/images/03-Microsoft-Teams-in-condominio-canale-general-1.png)](/images/03-Microsoft-Teams-in-condominio-canale-general-1.png)

Perfetto! E ora come usare il canale General? Ecco alcune idee che ho realizzato:
- la tab “Files” con la document library di Sharepoint è il luogo perfetto per condividere i documenti condominiali!

[![Microsoft Teams in condominio: la cartella dei documenti condominiali](/images/04-Microsoft-Teams-in-condominio-document-library.png)](/images/04-Microsoft-Teams-in-condominio-document-library.png)

I documenti condominiali: regolamento, capitolati, verbali, eccetera…
- **altre tab**: ecco altre idee per arricchire il canale General:
    - una tab che punti al sito web del condominio;
    - una tab PDF che visualizzi il regolamento condominiale;
    - un planner
    - un calendario con le scadenze... insomma ci si può sbizzarrire!!
- **annuncio di benvenuto**: un’altra idea utile per “accogliere” i condòmini mano a mano che vengono aggiunti potrebbe essere quella di redarre un piccolo annuncio di benvenuto che contenga informazioni utili e norme di comportamento;

[![Annuncio benvenuto](/images/05-Microsoft-Teams-in-condominio-annuncio-benvenuto.png)](/images/05-Microsoft-Teams-in-condominio-annuncio-benvenuto.png)

Ora siamo pronti per la vera interazione! 😉

## Fase 6 – Il canale di scala
Prima di cominciare a conversare, qualche configurazione è d’obbligo 😉
- come già detto, non abbiamo “member” nel vero senso della parola ma ho comunque ristretto la possibilità di creare, aggiornare e rimuovere tab nel canale;
- menzioni e “fun stuff” sono abilitati.

[![Configurazione del canale di scala](/images/05a-Microsoft-Teams-in-condominio-impostazioni-canale-scala.png)](/images/05a-Microsoft-Teams-in-condominio-impostazioni-canale-scala.png)

E finalmente si può cominciare ad interagire! Eccome come l’ho pensata:
- la bacheca di scala potrebbe essere assimilabile alla chat di gruppo su Whatsapp;
- si possono condividere immagini, documenti, altri dati;
- anche qui c’è la possibilità di usare la document library di canale per depositare documenti di utilità;
- è possibile sfruttare la funzionalità “Meet now” per fare una videochiamata con tutti;
- chi più ne ha, più ne metta, puoi davvero sbizzarrirti!

[![Configurazione del canale di scala](/images/06-Microsoft-Teams-in-condominio-bacheca-di-scala.png)](/images/06-Microsoft-Teams-in-condominio-bacheca-di-scala.png)

## Conclusioni sull’utilizzo di Microsoft Teams in condominio

> *"Rick, ti sei bevuto il cervello!"*

È possibile, forse hai ragione ma ormai sono alla 6a settimana di lavoro da casa con incursioni nel mondo reale solo per fare la spesa ogni 15gg circa. Ci può stare che io cominci a straparlare, no? 😉

Come sempre, spero di averti fornito uno spunto utile con questo concept a metà tra il serio e il faceto e ti aspetto nei commenti o sui miei social per parlarne insieme: sono curioso di sapere se hai implementato il team di condominio e come sta andando.

Grazie per avermi seguito fino a qui!

Riccardo


