---
date: 2021-06-09T08:00:00-00:00
description: "Panoramica sul Multi-Factor Authentication licensing in Azure AD e Microsoft 365, con una comparativa delle funzionalità in base alla licenza."
featured_image: "/images/03-Zero-Trust-Security-Conditional-Access.png"
categories: [ "Identity & Security"]
tags: [ "Azure AD", "Conditional Access", "Multi Factor Authentication", "Licensing"]
title: "Multi-Factor Authentication licensing in Microsoft 365 ed Azure AD"
url: "/multi-factor-authentication-licensing-microsoft-365-azure-ad"
---
Qualche giorno fa ho avuto un’interessante conversazione privata in cui mi è stato proposto di fare un articolo per chiarire meglio alcune questioni sul Multi-Factor Authentication licensing in Azure AD e sul Conditional Access (CA): in particolare, quali sono le caratteristiche disponibili in base alla licenza posseduta?

![Conditional Access](/images/03-Zero-Trust-Security-Conditional-Access.png)

Prima di tutto, è necessario chiarire il concetto base: la tecnologia dietro MFA e CA è la stessa dietro qualunque licenza, quello che cambia sono le caratteristiche disponibili in base alla licenza posseduta o alla versione di Azure AD. Questo fa sì che, agli occhi di chi si approccia al licensing, tutto sembri un po’ complesso e che ci siano tante versioni. In realtà, come già detto poco fa, ciò che cambia sono solo ed esclusivamente le caratteristiche disponibili a seconda del piano di licenza, tutto qui.

Ho raccolto per te queste tabelle che spiegano davvero bene e in maniera immediata tutte le informazioni che servono per diventare dei piccoli guru del licensing della MFA di Azure AD.

**Attenzione! Questo articolo è stato scritto a Giugno 2021. Le informazioni di licensing, purtroppo, cambiano spesso e volentieri e quindi potrei non essere stato in grado di aggiornare tempestivamente le tabelle di seguito. Se vuoi delle informazioni sempre fresche e attendibili, ti prego di fare riferimento alla seguente documentazione ufficiale:**
- **[Available versions of Azure AD Multi-Factor Authentication](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-mfa-licensing#available-versions-of-azure-multi-factor-authentication)**
- **[Feature comparison of versions](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-mfa-licensing#feature-comparison-of-versions)**

## Versioni disponibili di MFA e CA rispetto alla licenza
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

| Se la tua licenza è...                             | Versione di MFA e CA disponibile                                                                                                                                                                                                                                               |
|:---------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **M365 E3 EMS E3**                                 | EMS E3 e Microsoft 365 E3 includono Azure AD Premium P1. Disponibili TUTTE le funzionalità della MFA di Azure AD, attivabile manualmente o tramite Conditional Access. Disponibili tutte le funzionalità del Conditional Access ad eccezione del Risk-Based Conditional Access |
| **M365 E5 EMS E5**                                 | EMS E5 e Microsoft 365 E5 includono Azure AD Premium P2. Disponibili TUTTE le funzionalità della MFA di Azure AD, attivabile manualmente o tramite Conditional Access. Disponibili le funzionalità complete del Conditional Access, compreso il Risk-Based Conditional Access. |
| **Tutti gli altri piani Office 365/Microsoft 365** | MFA disponibile con funzionalità di base, è possibile abilitarla per tutti oppure utente per utente, dal portale amministrativo di Microsoft 365 / Azure AD. Conditional Access disponibile solo per i piani che includono Azure AD Premium P1.                                |
| **Azure AD Free**                                  | MFA disponibile con il solo metodo di verifica "Microsoft Authenticator App", è possibile attivarla per tutti ma non utente per utente. È possibile attivarla per gli utenti con ruolo Global Administrator a livello di tenant.                                               |

## Funzionalità della MFA disponibili rispetto alla licenza

| Funzionalità                                                           | Azure AD Free (utenti standard) | Azure AD Free (Global Administrators) | Altri piani Office 365 - Microsoft 365 | Piani con Azure AD Premium P1 o P2 |
|:-----------------------------------------------------------------------|:-------------------------------:|:-------------------------------------:|:--------------------------------------:|:----------------------------------:|
| **Protezione account amministrativi del tenant con MFA**               |                X                |                   X                   |                    X                   |                  X                 |
| **App come secondo fattore**                                           |                X                |                   X                   |                    X                   |                  X                 |
| **Chiamata telefonica come secondo fattore**                           |                                 |                   X                   |                    X                   |                  X                 |
| **SMS come secondo fattore**                                           |                                 |                   X                   |                    X                   |                  X                 |
| **Controllo amministrativo sui metodi di verifica disponibili**        |                                 |                   X                   |                    X                   |                  X                 |
| **Fraud Alert**                                                        |                                 |                                       |                                        |                  X                 |
| **Reportistica MFA**                                                   |                                 |                                       |                                        |                  X                 |
| **Messaggio personalizzato per la chiamata al telefono**               |                                 |                                       |                                        |                  X                 |
| **ID chiamate personalizzato per la verifica via chiamata telefonica** |                                 |                                       |                                        |                  X                 |
| **Trusted IPs**                                                        |                                 |                                       |                                        |                  X                 |
| **Ricorda la MFA per i dispositivi verificati**                        |                                 |                   X                   |                    X                   |                  X                 |
| **MFA per applicazioni on-premises**                                   |                                 |                                       |                                        |                  X                 |

## Conclusioni e fonti
Perfetto, ora ti è più chiaro? Spero di sì! come vedi, il miglior valore, da questo punto di vista, lo danno le licenze che includono almeno un livello di Azure AD Premium P1, meglio ancora se una Premium P2, che contiene anche il [Conditional Access basato sul rischio](/azure-ad-identity-protection-rischio/). Se sei già in possesso di una licenza di questo tipo o superiore, ti consiglio caldamente di liberare tutto il potenziale della MFA e del Conditional Access!

Il tuo IT Specialist, Riccardo

P.S.: un ringraziamento a [Riccardo Cozzi](https://www.linkedin.com/in/riccardo-cozzi-7170039/): questo articolo è scaturito da un’interessante conversazione avuta con lui su Linkedin.