---
date: 2021-03-10T08:00:00-00:00
description: "Come trovare il nome del server Azure AD Connect in pochi secondi se devi recuperarlo al volo o il cliente non se lo ricorda."
featured_image: "/images/01-Come-trovare-nome-server-Azure-AD-Connect.png"
categories: [ "Identity & Security"]
tags: [ "Azure AD", "Azure AD Connect", "Active Directory"]
title: "Come trovare il nome del server Azure AD Connect se non lo ricordi"
url: "/come-trovare-il-nome-del-server-azure-ad-connect-se-non-lo-ricordi"
---
Una chicca super veloce: capita che il cliente non si ricordi su che server è installato Azure AD Connect. Come trovare il nome del server Azure AD Connect in maniera semplice, veloce e autonoma?

[![Schermata di ricerca server in Active Directory](/images/01-Come-trovare-nome-server-Azure-AD-Connect.png)](/images/01-Come-trovare-nome-server-Azure-AD-Connect.png)

Se hai installato Azure AD Connect usando l’utenza di default per la sincronizzazione, è facilissimo: su Active Directory Users and Computer, cerca tra le utenze con la semplice stringa “MSOL”.

Quella è l’utenza di servizio per la sincronizzazione.

Nelle sue proprietà avanzate, recupera la descrizione dell’utenza. Esatto, proprio la descrizione. Perché? Perché contiene il nome del server! Ecco un esempio:

*Account created by the Windows Azure Active Directory Sync tool with installation identifier ‘xxxxxxxxxxxxxxx’ running on computer ‘**AD-CONNECT-SERVERNAME**’ configured to synchronize to tenant ‘*

In alternativa, se questo metodo non funziona, puoi sempre andare sul portale **https://admin.microsoft.com** alla sezione
- **Health** –> **Directory Sync Status**

Tra le informazioni che compaiono, la voce “**Directory sync service account**” contiene il nome del server: è il segmento compreso tra “Sync_” e la serie di numeri prima della chiocciola.

[![Schermata Azure AD Connect su portale amministrativo di Microsoft 365](/images/02-Come-trovare-nome-server-Azure-AD-Connect-Admin-Portal.png)](/images/02-Come-trovare-nome-server-Azure-AD-Connect-Admin-Portal.png)

Visto? Semplice e veloce! E tu hai escogitato altri tricks su come trovare il nome del server Azure AD Connect?

A presto con la prossima chicca!

Il tuo IT Specialist, Riccardo
