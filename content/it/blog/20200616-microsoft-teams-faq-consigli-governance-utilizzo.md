---
date: 2020-06-16T08:00:00-00:00
description: "Ho raccolto in questo articolo le Microsoft Teams FAQ più spinose e dilemmatiche che mi sono state poste sul tool di collaborazione Microsoft"
featured_image: "/images/01-Microsoft-Teams-FAQ.jpg"
categories: [ "Altro "]
tags: [ "Microsoft Teams", "Microsoft 365", "FAQ" ]
title: "Microsoft Teams FAQ, consigli di governance e utilizzo"
url: "/microsoft-teams-faq-consigli-governance-utilizzo"
---
Microsoft Teams è un raccoglitore di strumenti ognuno dei quali, preso singolarmente, ha le sue best practice di utilizzo e di gestione: può essere spiazzante da usare e anche da gestire. In questo articolo ho raccolto le Microsoft Teams FAQ più spinose a cui nessuno ha mai voluto risponderti.

![](/images/01-Microsoft-Teams-FAQ.jpg)

La crescita di Microsoft Teams è ormai inarrestabile anche in questa fase post lockdown: molte persone lavorano ancora in smart working e finalmente le aziende italiane hanno iniziato un’adozione massiva (per quanto forzata) degli strumenti di collaborazione tipici di un approccio [Modern Workplace](/cosa-significa-modern-workplace/).

Esistono tantissimi e bellissimi tutorial su Teams, sia per gli utenti finali sia per gli IT Admin. **Pochi però danno consigli di governance: ho pensato quindi di raccogliere in maniera veloce e semplice le domande più spinose su come approcciare questo strumento e i suoi limiti dal punto di vista della gestione**. Spero che questo elenco si possa arricchire sempre di più anche con il tuo aiuto. Via con le Microsoft Teams FAQ!

## Quali sono i criteri secondo cui creare un Team?
Un team è un gruppo di persone che lavorano insieme per realizzare qualcosa. I criteri con cui creare un team sono principalmente due:
- **il tipo di lavoro svolto**, ad esempio:
    - Team Ingegneria
    - Team Marketing
    - Team HR
    - ... insomma, un raccoglitore di risorse di collaborazione in base al ruolo d’appartenenza aziendale.
- **i progetti su cui si sta lavorando**, come ad esempio:
    - Progetto Migrazione Lift & Shift;
    - Progetto IlPortaleDegliSmanettoni.com;
    - Ristrutturazione Edificio Storico Villa Dei Nerd;
    - Progetto Video Promozionale Estate 2020;
    - ... e così via, insomma un’attività progettuale che coinvolge un team di persone.

## Che tipi di team posso creare?
Potenzialmente infiniti, tecnicamente 3 ma, per darti una soluzione pratica e veloce da implementare, direi di dare ai team i seguenti “tagli”, che sono un mix di criteri di creazione e tipologie che la piattaforma mette a disposizione:
- **Organizational**: tutti quanti all’interno dell’organizzazione sono automaticamente membri di questo Team; tipologia di team da usare con molta parsimonia;
- **Basati sul ruolo**: ad esempio “Team HR”; a livello di tipologia tecnica di team qui utilizzerei un team Privato;
- **Progetti**: se vuoi implementare un’area di collaborazione e scambio su un’attività molto specifica che ha un inizio e una fine (un progetto, per l’appunto), Teams è uno strumento straordinario che spingerà la collaborazione al 110%; anche qui Team privato con i canali opportuni;
- **Cross-unit**: potrebbe essere un ambito aziendale sul quale collaborano più dipartimenti ma che non si esaurisce in un singolo progetto; potresti implementare vari canali privati e non.

## Come chiamo il team?
Questa è una questione spinosissima! Mi è capitato di vedere Team chiamati “cippalippa”, “Gialappa’s Band” e altri nomi tutt’altro che consoni ad un ambito aziendale. I due consigli più rapidi che mi vengono in mente sono:
- individua una naming convention solida e parlante, in cui i vari segmenti descrivano in pochi caratteri che tipo di team hai davanti, come ad esempio:
    - *Marketing-PRJ-NuovoPortale*: è un progetto del dipartimento Marketing relativo ad un nuovo portale;
    - *Team Ingegneria*: questo team sicuramente è luogo di un simposio di fini pensatori 😉
- grazie ad Azure AD e ai gruppi Office 365, puoi [impostare una naming convention](https://docs.microsoft.com/en-us/microsoft-365/admin/create-groups/groups-naming-policy?view=o365-worldwide) sostanzialmente automatica; sfrutta questa possibilità!

## Come creare un’area più protetta all’interno di un Team?
Nel 2019 era la funzionalità più attesa di Teams: sto parlando dei [Private Channels](https://docs.microsoft.com/en-us/microsoftteams/private-channels)! All’interno del Team puoi creare un canale visibile ed utilizzabile solo ad un sottoinsieme definito dei membri del team.

## Posso impedire che chiunque possa creare un team e restringere questa possibilità solo ad un numero ristretto di utenti?
Domanda lunghissima, risposta brevissima: **Sì**! È possibile restringere ai soli membri di un security group la possibilità di creare un Team.

Come? Seguendo le indicazioni di Microsoft per [gestire chi può creare gruppi Office 365](https://docs.microsoft.com/en-us/microsoft-365/admin/create-groups/manage-creation-of-groups?view=o365-worldwide).

## Esiste un numero “giusto” di team di cui far parte?
Non esiste un numero “giusto” di team di cui far parte ma, per un utilizzo efficace e produttivo dello strumento, si suggerisce di non superare i 10/15 team a livello di partecipazione attiva.

## Posso mettere in ordine i team di cui sono membro?
Sì! Puoi, anzi ti consiglio caldamente di mettere in ordine i team di cui fai parte in base alle tue preferenze, sulla barra di sinistra.

## E quando il team non serve più?
Se il team non serve più o se i dati che contiene devono essere “congelati” senza possibilità di essere modificati, **cancellalo** o **archivialo**.

## Come abilitare o disabilitare in maniera corretta il Guest Access?
L’accesso dei guest esterni all’organizzazione è un argomento che divide parecchio e le cui impostazioni sono sparse ovunque in Azure AD e Microsoft 365.

Ecco una comoda [checklist del guest access in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) per verificare ed impostarlo a tutti i livelli!

## Quali sono i limiti di canali, membri, team?
I limiti della piattaforma sono in costante aggiornamento ed ampliamento: fai riferimento a questo articolo ufficiale Microsoft in cui vengono riportati i [limiti e le specifiche di Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/limits-specifications-teams).

## Posso mettere una data di scadenza ad un team?
La domanda sembra assurda e in pochi lo sanno ma la risposta è sì! Attraverso le [policy di scadenza dei gruppi Office 365](https://docs.microsoft.com/en-us/microsoft-365/admin/create-groups/office-365-groups-expiration-policy?view=o365-worldwide), è possibile impostare una scadenza ad un Team.

## Conclusioni
Le Microsoft Teams FAQ sono potenzialmente infinite: qui ho raccolto le prime che mi sono venute in mente e in cui mi sono imbattuto sul campo durante questi mesi. **Mi piacerebbe che queste Frequently Asked Questions potessero ulteriormente arricchirsi anche col tuo aiuto**. Se vuoi farmi una domanda su Teams o se pensi di avere un consiglio utile da condividere, scrivimi pure o lascia un commento. Come sempre, grazie per avermi seguito fino a qui.

Il tuo IT Specialist, Riccardo
