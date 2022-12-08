---
date: 2021-05-05T08:00:00-00:00
description: "Come funziona Azure AD Identity Protection e cosa significa il concetto di rischio applicato ad un utente e ad un sign-in."
featured_image: "/images/03-Zero-Trust-Security-Conditional-Access.png"
categories: [ "Identity & Security"]
tags: [ "Azure AD", "Identity Protection"]
title: "Azure AD Identity Protection: cos’è il rischio in Azure AD?"
url: "/azure-ad-identity-protection-rischio"
---
In un approccio [Zero Trust Security](/zero-trust-security/), dove l’identità è un elemento fondamentale, la sicurezza delle autenticazioni è in qualche modo misurabile in base ai cosiddetti “segnali”. L’analisi di questi segnali restituisce quindi un livello di “rischio” di un certo utente quando effettua l’autenticazione ai servizi Microsoft 365. Oggi ti racconto cos’è Azure AD Identity Protection e cosa significa il concetto di “rischio”.

Come sempre, prima di buttarci a capofitto in questo viaggio “rischioso” (battutaccia 🤣), serve introdurre un altro concetto: devi capire cosa siano i **segnali**.

## Cos’è un segnale?
In Azure AD si definisce segnale una proprietà o una condizione particolare che un utente e un’autenticazione hanno. Ecco alcuni esempi:
- indirizzo IP dell’utente;
- geolocalizzazione dell’IP e dell’utente;
- applicazione a cui sta tentando di accedere;
- sistema operativo del dispositivo che sta usando (Windows, Linux, macOs, iOS, Android?);
- che tipo di client sta usando l’utente per accedere ai servizi di M365? Un’app che supporta [Modern Authentication](/modern-authentication-multi-factor-authentication-exchange-online-skype-for-business-online/), un browser o un’app che supporta solo legacy authentication?
- se è un browser, quale browser?
- a quali gruppi di Azure AD appartiene la sua utenza?
- e via dicendo...

Questi sono tutti **segnali** e, come vedi, Azure AD è in grado di rilevarne molti.

Ti starai chiedendo: *“Rick, perché mi stai ammorbando con questa storia dei segnali?”*

Rispondo subito e senza troppi giri di parole: **perché il “rischio” è un segnale**!

[![Conditional Access](/images/03-Zero-Trust-Security-Conditional-Access.png)](/images/03-Zero-Trust-Security-Conditional-Access.png)

E quindi, come si inserisce il rischio tra i segnali e che cos’è?

## Cos’è il rischio in Azure AD Identity Protection?
Il rischio in Azure AD Identity Protection è una valutazione delle azioni degli utenti, delle autenticazioni e delle loro proprietà. **L’analisi incrociata delle proprietà e delle azioni effettuate dagli utenti, fornisce una valutazione di quanto l’autenticazione sia pulita o sospetta e di quanto l’utente sia in sicurezza o meno.**

Il rischio può essere:
- calcolato in tempo reale (valutazioni disponibili in 5/10 minuti);
- calcolato dall’intelligenza del cloud Microsoft, sulla base di un’analisi degli eventi di autenticazione del tuo tenant, che avviene in background (valutazioni disponibili in qualche ora).

A sua volta, si distingue in due tipologie:
- User Risk;
- Sign-in Risk.

{{< rawhtml >}}
  <style>
    table {
      border-collapse: collapse;
      font-family: sans-serif;
      font-size: 0.75em;
    }
    table, th, td {
      border: 1px solid black;
      padding: 10px;
    }
    thead {
      background: #777777;
      color: white;
    }
    blockquote {
      border-left: solid blue;
      padding-left: 10px;
    }
</style>
{{< /rawhtml >}}

## User Risk
Ecco i segnali di rischio associati ad un utente.

| Rischio                      | Descrizione                                                                                                                                                                                                                                                                                                |
|:-----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Credenziali compromesse**  | Microsoft acquisisce dal dark web e da altre fonti le password compromesse e le mette a confronto con le credenziali dell'utente. Se viene rilevata una corrispondenza tra l'attuale password dell'utente e una delle password compromesse, viene calcolato un livello di rischio "alto" per quell'utenza. |
| **Attività utente inusuale** | In base alle proprietà dell'utente e ad una sorta di "analisi comportamentale", se viene rilevata un'attività insolita, viene attribuito un livello di rischio.                                                                                                                                            |

I segnali sono in costante aggiornamento e miglioramento. Quelli riportati qui sopra sono quelli disponibili al momento della scrittura di questo articolo. Se vuoi avere la sicurezza di essere sempre aggiornato, ti consiglio di fare riferimento alla documentazione ufficiale:

- [What is risk? Azure AD Identity Protection | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks)

## Sign-in Risk
Ecco i segnali di rischio associati ad una singola autenticazione.

| Rischio                                                | Tipo di rilevamento | Descrizione                                                                                                                                                                                                                                                                    |
|--------------------------------------------------------|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Indirizzo IP anonimo**                               | Tempo reale         | L'accesso viene effettuato da un IP anonimizzato, ad esempio da rete Tor o da una VPN.                                                                                                                                                                                         |
| **Viaggio atipico**                                    | Calcolato           | Vengono identificate due autenticazioni per lo stesso utente da luoghi diversi, di cui almeno uno può essere familiare per il comportamento solito dell'utente. Viene considerato anche il tempo che intercorre tra i due login e la distanza tra i due luoghi.                |
| **IP legato a malware noti**                           | Calcolato           | Questo rischio viene rilevato quando l'indirizzo IP origine dell'autenticazione è noto per essere collegato ad attività di malware e bot.                                                                                                                                      |
| **Proprietà di autenticazione insolite**               | Tempo reale         | Vengono rilevate e prese in considerazione alcune proprietà di autenticazione tipiche dell'utente. Se viene effettuata un'autenticazione con proprietà diverse rispetto al solito, viene alzato il livello di rischio.                                                         |
| **Utente classificato come "compromesso" dagli admin** | Calcolato           | Gli amministratori di Azure AD hanno la possibilità di classificare un utente come compromesso. Se viene fatta un'autenticazione di un utente così classificato, viene alzato il livello di rischio.                                                                           |
| **Indirizzo IP sospetto**                              | Calcolato           | Un indirizzo viene considerato sospetto quando ad esso sono legati molti eventi di autenticazioni fallite o viene considerato pericoloso da altre fonti di IP reputation.                                                                                                      |
| **Regole sospette sulla Inbox dell'utente**            | Calcolato           | Nell'inbox della casella di posta legata all'utente vengono rilevate regole sospette. Questo rischio viene rilevato da Microsoft Cloud App Security (MCAS).                                                                                                                    |
| **Password spray**                                     | Calcolato           | Un attacco di tipo password spray è il caso in cui più utenti vengono attaccati contemporaneamente a forza bruta.                                                                                                                                                              |
| **Viaggio impossibile**                                | Calcolato           | Viene rilevato quando un utente effettua due autenticazioni da luoghi geografici in un intervallo temporale che è più breve rispetto a quanto ci si impiegherebbe a spostarsi da una località all'altra. Questo rischio viene rilevato da Microsoft Cloud App Security (MCAS). |
| **Nuovo paese**                                        | Calcolato           | Vengono prese in considerazione le località dei login precedenti per costruire una sorta di "storico" e determinare nuove località non familiari. Questo rischio viene rilevato da Microsoft Cloud App Security (MCAS).                                                        |
| **Regole sospette di inoltro della posta elettronica** | Calcolato           | Regole di inoltro di posta elettronica sospette. Questo rischio viene rilevato da Microsoft Cloud App Security (MCAS).                                                                                                                                                         |

I segnali sono in costante aggiornamento e miglioramento. Quelli riportati qui sopra sono quelli disponibili al momento della scrittura di questo articolo. Se vuoi avere la sicurezza di essere sempre aggiornato, ti consiglio di fare riferimento alla documentazione ufficiale:

- [What is risk? Azure AD Identity Protection | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks)

## Come può essere utile il rischio in Azure AD Identity Protection?
Il concetto di rischio è **utilissimo** se usato in maniera combinata con **Conditional Access** e **Multi Factor Authentication**! Ancora di più se hai a disposizione [Azure Sentinel](/come-capire-azure-sentinel-in-5-passaggi/) e vuoi automatizzare delle reazioni automatiche.

Esempi concreti? Eccoli:
- se vengono rilevate due autenticazioni da Italia e Spagna a distanza di 5 minuti (viaggio impossibile), richiedo la Multi Factor Authentication per accedere (Conditional Access + MFA);
- se viene rilevato che la password utilizzata dall’utente combacia con una password comparsa in elenchi pubblici di credenziali compromesse (rischio), blocco l’autenticazione (Conditional Access), alzo un incident e blocco l’utenza (Azure Sentinel).

## Dove si trovano le valutazioni di rischio e gli eventi?
È sufficiente navigare nel portale di Azure AD alla sezione **Azure Active Directory** –> **Security** –> **Identity Protection**

##  Requisiti di licenza per Azure AD Identity Protection
Ecco un documento ufficiale Microsoft che ti chiarirà quali licenze servono per poter usufruire di queste funzionalità:
- [Active Directory Identity Protection License Requirements | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection#license-requirements)

## Conclusioni su rischio e Azure AD Identity Protection
Come vedi, il limite per mettere in sicurezza in maniera semplice ed automatica le tue identità è solo la fantasia e, naturalmente, un’attenta analisi delle tue esigenze e dell’ambiente.

E tu stai già utilizzando Azure AD Identity Protection? Hai già automatizzato delle reazioni in caso di rischio alto? Parliamone nei commenti o sui miei social, ti aspetto!

Il tuo IT Specialist, Riccardo