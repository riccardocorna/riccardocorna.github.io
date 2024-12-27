---
date: 2020-07-22T08:00:00-00:00
description: "La governance di Sharepoint online è un insieme di regole, processi e obbiettivi da stabilire per un uso efficace della piattaforma."
featured_image: "/images/05-governance-di-sharepoint-online-sharepoint-logo.png"
categories: [ "Altro"]
tags: [ "Sharepoint online", "Governance", "Microsoft 365" ]
title: "Governance di Sharepoint Online: come definirla, suggerimenti, best practice"
url: "/governance-di-sharepoint-online"
---
Ebbene sì, dopo mesi interamente dedicati ad Azure, in questo periodo sto svolgendo tutt’altro tipo di attività: sto definendo le politiche di governance di Sharepoint Online per un cliente che ha necessità di fissare, per così dire, le regole del gioco di questa piattaforma all’interno dell’azienda. Ormai sono quasi arrivato alla fine di questa analisi e credo sia utile condividere con te le principali indicazioni di governance da tenere a mente per Sharepoint Online.

## Cosa significa “governance”?
Prima di cominciare fissiamo un concetto fondamentale: cosa significa la parola “governance” e, in particolare, cosa significa applicata in ambito IT ad uno strumento di produttività come Sharepoint Online?

> *La governance è un insieme di principi, di regole e di procedure che riguardano la gestione e il governo di una piattaforma tecnologica.*

Realizzare una governance per Sharepoint Online quindi significa definire:
- obiettivi e modalità di utilizzo dello strumento;
- la struttura e le metodologie di gestione delllo strumento;
- i processi da mettere in campo funzionali al raggiungimento degli obiettivi prefissati;
- le regole e le modalità attraverso cui monitorare processi e obiettivi.

Un esempio concreto delle domande alle quali una governance ben definita può rispondere:
- Chi è responsabile dei contenuti di una site collection?
- Quali sono le tassonomie e i metadata definiti per le site collection?
- Quali sono le configurazioni standard di una site collection quando deve essere creata?
- Quali metriche devo monitorare per garantire il buon funzionamento della piattaforma?

Eccetera, eccetera, potrei continuare all’infinito. Come vedi, è importante definire una governance perché le regole che avrai fissato ti permetteranno di avere una piattaforma omogenea e standard, eliminando inefficienze e margini di discrezionalità che minano la coerenza delle configurazioni. Sharepoint Online è, a tutti gli effetti, uno strumento di collaborazione che abbraccia il paradigma [Modern Workplace](/cosa-significa-modern-workplace/) ed è molto importante che venga usato e gestito nella maniera corretta.

Perfetto! Ora vediamo quali sono le principali politiche ed indicazioni da tenere a mente quando si definisce la governance di Sharepoint Online.

## Provisioning & Administration
![Schermata di un sito Sharepoint Online](/images/01-governance-di-sharepoint-online-provisioning.png)

Le prime cose da considerare sono la fase di creazione del sito e la sua successiva amministrazione.

Per quanto riguarda il provisioning della site collection (ovvero la sua creazione), le principali regole da definire e da mettere nero su bianco sono:
- le informazioni minime indispensabili per creare il sito, come ad esempio: nome, descrizione, scopo del sito, se è un hub site o se sarà agganciato ad un hub site, chi avrà accesso al sito e in che modo (lettura o scrittura), eccetera; l’ideale sarebbe presentare queste domande attraverso un form elettronico da compilare;
- è buona norma definire quali e quante tipologie di siti sia possibile richiedere, ad esempio: il sito è dipartimentale (e quindi basato sul ruolo aziendale) o è un progetto?
- potrebbe essere utile definire un template per ogni tipologia di sito richiedibile dagli utenti che contenga tutte le configurazioni generiche minime; riducendo le configurazioni manuali si riduce anche il margine di errore;
- il flusso di provisioning deve essere tracciato e gestito in ogni suo passaggio; l’ideale sarebbe veicolarlo e gestirlo attraverso un sistema di ticketing.

Perfetto! Ora che il sito è creato, chi lo amministra? Quali sono le responsabilità in ogni ambito di gestione che impatta sul sito?
- definisci dei ruoli a livello di tenant, ad esempio:
    - chi è responsabile di creare i siti?
    - chi è responsabile della sicurezza dei siti e chi definisce i permessi e i ruoli?
    - chi darà supporto di secondo livello specifico su Sharepoint?
    - chi deciderà le tassonomie?
    - chi verifica che i siti siano gestiti in maniera uniforme e rispettosa dei criteri di governance?
- oltre ai ruoli a livello di tenant, devi definire delle responsabilità anche internamente ad ogni site collection:
    - quali responsabilità avranno gli owner del sito?
    - chi gestirà il contenuto del sito?
    - chi decide i membri del sito?

Come vedi, è un lavoro duro che richiede una profonda introspezione all’interno dei flussi di gestione della piattaforma.

Vediamo ora la parte di accesso e controllo al sito e cosa occorre definire a livello di strategia.

## Access & Control

![Governance di Sharepoint Online: Access & Control (permessi)](/images/02-governance-di-sharepoint-online-access-and-control.png)

Questa parte è centrale perché rappresenta il cuore della sicurezza della tua piattaforma Sharepoint Online.

Le questioni principali da considerare in questo ambito sono:
- i ruoli di Sharepoint e i gruppi a cui dare i vari permessi;
- i permessi all’interno del sito e sulle document library;
- come gestire l’ereditarietà e le eccezioni che verranno (sicuramente) richieste dagli utenti?
- in che modo gestire le condivisioni tramite link e verso quali soggetti abilitare questa possibilità? Interni o anche esterni?
- un utente può richiedere in autonomia di avere accesso ad un sito oppure no?
- come implementare delle aree riservate e a che livello dei siti o delle document library?

Lasciare queste questioni indefinite può portare a diversi problemi sui tuoi siti e sulle tue document library: data breach, problemi di accesso e di audit, troubleshooting difficile in caso di assistenza. È tosta, lo so, ma devi definire in maniera meticolosa questa parte!

Abbiamo finito? Neanche per sogno, è ora di scrivere le regole del gioco per quanto riguarda il monitoraggio!

## Monitoring

![Governance di Sharepoint Online: monitoring](/images/03-governance-di-sharepoint-online-monitoring.png)

Senza monitoraggi o report di alcun tipo, perderai entro brevissimo tempo il controllo della tua piattaforma Sharepoint Online. Quali tipi di reportistica è utile implementare? Vediamoli insieme:
- prima di tutto è necessario implementare un meccanismo di reportistica che ti dia consapevolezza dei permessi e dei ruoli assegnati su ogni singolo sito;
- devi conoscere anche i permessi sulle singole document library per verificare che le policy di ereditarietà che hai definito nella fase di “Access & Control” siano rispettate;
- devi tenere traccia delle condivisioni via link per verificare eventuali anomalie;
- devi verificare e gestire il ciclo di vita della site collection, misurando le metriche di utilizzo della document library per individuare quelle non più utilizzate e gestire la loro archiviazione.

Ci siamo quasi, mancano solo alcune cose da definire... ecco la Compliance!

## Compliance

![Governance di Sharepoint Online: compliance](/images/04-governance-di-sharepoint-online-compliance.jpg)

Per far sì che i tuoi dati rispettino i requisiti interni e legali che il tuo business ti richiede, cosa devi definire? Vediamolo immediatamente:
- una strategia di backup e restore dei siti e delle document library;
- una strategia di retention, lifecycle e archiviazione dei contenuti non più attivi;
- devi definire come gestire le aree riservate e la loro eventuale cifratura;
- se, prima di definire la governance con questi criteri, stavi già usando Sharepoint Online e avevi dei siti già attivi, devi pianificare il loro adeguamento alle nuove politiche di governance, coinvolgendo gli owner dei siti.

## Conclusioni
Questa volta è davvero tutto 🙂 Grazie per avermi seguito fino a qui . La definizione delle politiche di governance è un’attività davvero tosta che richiede tempo, una profonda conoscenza dei flussi di gestione della piattaforma e dei propri flussi di amministrazione IT. Non è una cosa scontata e di sicuro ti fermerai a riflettere molto su alcune delle domande che ti ho suggerito. La governance di Sharepoint Online è da considerare come un investimento che richiede un grande sforzo iniziale, ripagato da una successiva semplificazione di gestione che eliminerà inefficienze e margini di discrezionalità dal tuo ambiente di collaborazione. In bocca al lupo! Se hai suggerimenti, come sempre, ti aspetto nei commenti.

Il tuo IT Specialist, Riccardo