---
date: 2023-10-06T08:00:00-00:00
description: "Come funziona Entra ID Protection e cosa significa il concetto di rischio applicato ad un utente e ad un sign-in."
featured_image: "/images/03-Zero-Trust-Security-Conditional-Access.png"
images:
  - "/images/03-Zero-Trust-Security-Conditional-Access.png"
categories: [ "Identity & Security"]
tags: [ "Entra ID", "Identity Protection"]
title: "Microsoft Entra ID Protection: cos’è il rischio in Entra ID?"
url: "/entra-id-protection-rischio"
aliases:
  - /azure-ad-identity-protection-rischio/
---
In un approccio [Zero Trust Security](/zero-trust-security/), dove l’identità è un elemento fondamentale, la sicurezza delle autenticazioni è in qualche modo misurabile in base ai cosiddetti “segnali”. L’analisi di questi segnali restituisce quindi un livello di “rischio” di un certo utente quando effettua l’autenticazione ai servizi Microsoft 365. Oggi ti racconto cos’è Entra ID Protection e cosa significa il concetto di “rischio”.

Come sempre, prima di buttarci a capofitto in questo viaggio "rischioso" (battutaccia 🤣), serve introdurre un altro concetto: devi capire cosa siano i **segnali**.

## Cos’è un segnale?
In Entra ID si definisce segnale una proprietà o una condizione particolare che un utente e un’autenticazione hanno. Ecco alcuni esempi:
- indirizzo IP dell’utente;
- geolocalizzazione dell’IP e dell’utente;
- applicazione a cui sta tentando di accedere;
- sistema operativo del dispositivo che sta usando (Windows, Linux, macOs, iOS, Android?);
- che tipo di client sta usando l’utente per accedere ai servizi di M365? Un’app che supporta [Modern Authentication](/modern-authentication-multi-factor-authentication-exchange-online-skype-for-business-online/), un browser o un’app che supporta solo legacy authentication?
- se è un browser, quale browser?
- a quali gruppi di Entra ID appartiene la sua utenza?
- e via dicendo...

Questi sono tutti **segnali** e, come vedi, Entra ID è in grado di rilevarne molti.

Ti starai chiedendo: *"Rick, perché mi stai ammorbando con questa storia dei segnali?"*

Rispondo subito e senza troppi giri di parole: **perché il "rischio" è un segnale**!

[![Conditional Access](/images/03-Zero-Trust-Security-Conditional-Access.png)](/images/03-Zero-Trust-Security-Conditional-Access.png)

E quindi, come si inserisce il rischio tra i segnali e che cos’è?

## Cos’è il rischio in Entra ID Protection?
Il rischio in Entra ID Protection è una valutazione delle azioni degli utenti, delle autenticazioni e delle loro proprietà. **L’analisi incrociata delle proprietà e delle azioni effettuate dagli utenti, fornisce una valutazione di quanto l’autenticazione sia pulita o sospetta e di quanto l’utente sia in sicurezza o meno.**

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

| Rischio                                                       | Tipo di rilevamento       | Descrizione                                                                                                                                                                                                                                                                                                | Livello di licenza |
|:--------------------------------------------------------------|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| **Leaked credentials**                                        | Offline                   | Microsoft acquisisce password compromesse dal dark web e da altre fonti e le confronta con le credenziali dell'utente. Se viene trovata una corrispondenza tra la password corrente dell'utente e una delle password compromesse, viene calcolato un livello di rischio "alto" per quell'utente.           | Nonpremium         |
| **Anomalous user activity**                                   | Offline                   | Basandosi sulle proprietà dell'utente e su una forma di "analisi comportamentale", se viene rilevata un'attività insolita, viene assegnato un livello di rischio.                                                                                                                                          | Premium            |
| **Possible attempt to access Primary Refresh Token (PRT)**    | Offline                   | Questo tipo di rilevamento del rischio è scoperto utilizzando informazioni fornite da Microsoft Defender for Endpoint (MDE).                                                                                                                                                                               | Premium            |
| **User reported suspicious activity**                         | Offline                   | Questo tipo di rilevamento del rischio viene segnalato quando un utente rifiuta una richiesta di autenticazione multifattore (MFA) e la segnala come attività sospetta. Una richiesta MFA non inizializzata da un utente potrebbe indicare che le sue credenziali sono compromesse.                        | Premium            |
| **Additional risk detected**                                  | Real-time o Offline       | Questa rilevazione indica che è stata rilevata una delle rilevazioni premium. Poiché le rilevazioni premium sono visibili solo ai clienti con licenze Microsoft Enter ID P2, vengono denominate "rischio aggiuntivo rilevato" per i clienti senza licenze Microsoft Entra ID P2.                           | Nonpremium         |
| **Microsoft Entra threat intelligence**                       | Offline                   | Questo tipo di rilevamento del rischio indica attività dell'utente che è insolita per l'utente o coerente con modelli di attacco conosciuti.                                                                                                                                                               | Nonpremium         |

I segnali sono in costante aggiornamento e miglioramento. Quelli riportati qui sopra sono quelli disponibili al momento della scrittura di questo articolo. Se vuoi avere la sicurezza di essere sempre aggiornato, ti consiglio di fare riferimento alla documentazione ufficiale:

- [What are risk detections? | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks)

## Sign-in Risk
Ecco i segnali di rischio associati ad una singola autenticazione.

| Risk                                                     | Detection Type       | Description                                                                                                                                                                                                                                                                                                                                                                                             | Licensing level |
|----------------------------------------------------------|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| **Anonymous IP address**                                 | Real-time            | L'accesso avviene da un indirizzo IP anonimizzato, ad esempio dalla rete Tor o da una VPN.                                                                                                                                                                                                                                                                                                              | Nonpremium      |
| **Activity from anonymous IP address**                   | Offline              | Questo rilevamento viene scoperto utilizzando informazioni fornite da Microsoft Defender for Cloud Apps. Questa rilevazione identifica che gli utenti sono stati attivi da un indirizzo IP identificato come indirizzo proxy anonimo.                                                                                                                                                                   | Premium         |
| **Atypical travel**                                      | Offline              | Vengono identificate due autenticazioni per lo stesso utente da luoghi diversi, di cui almeno uno può essere familiare in base al comportamento usuale dell'utente. Viene considerato anche il tempo tra le due autenticazioni e la distanza tra i due luoghi.                                                                                                                                          | Premium         |
| **Malware linked IP address**                            | Offline              | Questo rischio viene rilevato quando l'indirizzo IP di origine dell'autenticazione è noto per essere collegato a attività di malware e bot. (**Rilevamento deprecato**)                                                                                                                                                                                                                                 | Premium         |
| **Unfamiliar sign-in properties**                        | Real-time            | Questo tipo di rilevamento del rischio considera la storia degli accessi precedenti per cercare accessi anomali. Il sistema conserva informazioni sugli accessi precedenti e attiva un rilevamento del rischio quando avviene un accesso con proprietà non familiari all'utente.                                                                                                                        | Premium         |
| **Admin confirmed user compromised**                     | Offline              | Gli amministratori di Entra ID hanno la possibilità di classificare un utente come compromesso. Se un utente classificato in questo modo effettua un'autenticazione, il livello di rischio aumenta.                                                                                                                                                                                                     | Nonpremium      | 
| **Malicious IP address**                                 | Offline              | Questo rilevamento indica un accesso da un indirizzo IP malevolo. Un indirizzo IP è considerato malevolo in base all'alto tasso di accessi non riusciti dovuto a credenziali non valide ricevute dall'indirizzo IP o da altre fonti di reputazione dell'indirizzo IP.                                                                                                                                   | Premium         |
| **Suspicious inbox manipulation rules**                  | Offline              | Questo rilevamento viene scoperto utilizzando informazioni fornite da Microsoft Defender for Cloud Apps. Questo rilevamento esamina il tuo ambiente e attiva gli avvisi quando vengono impostate regole sospette che eliminano o spostano messaggi o cartelle nella casella di posta di un utente.                                                                                                      | Premium         |
| **Password spray**                                       | Offline              | Un attacco di password spray avviene quando più utenti vengono forzati contemporaneamente.                                                                                                                                                                                                                                                                                                              | Premium         |
| **Impossible travel**                                    | Offline              | Rilevato quando un utente effettua due autenticazioni da luoghi geografici in un intervallo di tempo più breve rispetto al tempo necessario per spostarsi tra i due luoghi. Questo rischio è rilevato da Microsoft Defender for Cloud Apps.                                                                                                                                                             | Premium         |
| **New country**                                          | Offline              | Vengono considerate le località di accesso precedenti per creare una sorta di "cronologia" e determinare nuove località non familiari. Questo rischio è rilevato da Microsoft Defender for Cloud Apps.                                                                                                                                                                                                  | Premium         |
| **Suspicious inbox forwarding**                          | Offline              | Questo rilevamento viene scoperto utilizzando informazioni fornite da Microsoft Defender for Cloud Apps. Questo rilevamento cerca regole sospette di inoltro di posta elettronica, ad esempio se un utente ha creato una regola nella casella di posta per inoltrare una copia di tutti i messaggi a un indirizzo esterno.                                                                              | Premium         |
| **Anomalous Token**                                      | Offline              | Questo rilevamento indica che ci sono caratteristiche anomale nel token, come una durata del token insolita o un token riprodotto da una posizione non familiare. Questo rilevamento copre Token di Sessione e Token di Aggiornamento.                                                                                                                                                                  | Premium         |
| **Token issuer anomaly**                                 | Offline              | Questo rilevamento del rischio indica che l'emittente del token SAML associato al token SAML è potenzialmente compromesso. Le dichiarazioni incluse nel token sono insolite o corrispondono a modelli di attacco noti.                                                                                                                                                                                  | Premium         |
| **Suspicious browser**                                   | Offline              | La rilevazione di un browser sospetto indica un comportamento anomalo basato sull'attività di accesso sospetto in vari tenant da paesi diversi nello stesso browser.                                                                                                                                                                                                                                    | Premium         |
| **Mass access to sensitive files**                       | Offline              | Questo rilevamento viene scoperto utilizzando informazioni fornite da Microsoft Defender for Cloud Apps. Questo rilevamento esamina il tuo ambiente e attiva gli avvisi quando gli utenti accedono a più file da Microsoft SharePoint o Microsoft OneDrive. Un avviso viene attivato solo se il numero di file accessi è insolito per l'utente e i file potrebbero contenere informazioni sensibili.    | Premium         |
| **Verified threat actor IP**                             | Real-time            | Questo tipo di rilevamento del rischio indica attività di accesso coerente con gli indirizzi IP noti associati a attori statali o gruppi criminali nel cyber, basati sul Microsoft Threat Intelligence Center (MSTIC).                                                                                                                                                                                  | Premium         |
| **Additional risk detected***                            | Real-time o Offline  | Questo rilevamento indica che è stata rilevata una delle rilevazioni premium. Poiché le rilevazioni premium sono visibili solo ai clienti con licenze Microsoft Entra ID P2, vengono denominate "rischio aggiuntivo rilevato" per i clienti senza licenze Microsoft Entra ID P2.                                                                                                                        | Nonpremium      |
| **Microsoft Entra threat intelligence**                  | Real-time o Offline  | Questo tipo di rilevamento del rischio indica attività dell'utente che è insolita per l'utente o coerente con modelli di attacco conosciuti. Questo rilevamento si basa su fonti di intelligence sulle minacce interne ed esterne di Microsoft.                                                                                                                                                         | Nonpremium      |

I segnali sono in costante aggiornamento e miglioramento. Quelli riportati qui sopra sono quelli disponibili al momento della scrittura di questo articolo. Se vuoi avere la sicurezza di essere sempre aggiornato, ti consiglio di fare riferimento alla documentazione ufficiale:

- [What are risk detections? | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks)

## Come può essere utile il rischio in Entra ID Protection?
Il concetto di rischio è **utilissimo** se usato in maniera combinata con **Conditional Access** e **Multi Factor Authentication**! Ancora di più se hai a disposizione [Azure Sentinel](/come-capire-azure-sentinel-in-5-passaggi/) e vuoi automatizzare delle reazioni automatiche.

Esempi concreti? Eccoli:
- se vengono rilevate due autenticazioni da Italia e Spagna a distanza di 5 minuti (viaggio impossibile), richiedo la Multi Factor Authentication per accedere (Conditional Access + MFA);
- se viene rilevato che la password utilizzata dall’utente combacia con una password comparsa in elenchi pubblici di credenziali compromesse (rischio), blocco l’autenticazione (Conditional Access), alzo un incident e blocco l’utenza (Azure Sentinel).

## Dove si trovano le valutazioni di rischio e gli eventi?
È sufficiente navigare nel portale di Entra ID alla sezione **Microsoft Entra ID** –> **Security** –> **Identity Protection**

##  Requisiti di licenza per Entra ID Protection
Ecco un documento ufficiale Microsoft che ti chiarirà quali licenze servono per poter usufruire di queste funzionalità:
- [License Requirements | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection#license-requirements)

## Conclusioni su rischio e Entra ID Protection
Come vedi, il limite per mettere in sicurezza in maniera semplice ed automatica le tue identità è solo la fantasia e, naturalmente, un’attenta analisi delle tue esigenze e dell’ambiente.

E tu stai già utilizzando Entra ID Protection? Hai già automatizzato delle reazioni in caso di rischio alto? Parliamone nei commenti o sui miei social, ti aspetto!

Il tuo IT Specialist, Riccardo