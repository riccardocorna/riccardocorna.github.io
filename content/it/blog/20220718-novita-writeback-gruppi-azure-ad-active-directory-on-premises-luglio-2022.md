---
date: 2022-07-18T09:00:00-00:00
description: "Nuove funzionalità e possibilità di sincronizzazione dei gruppi da Azure AD verso Active Directory on-premises."
featured_image: "/images/01-AAD-Groups-WriteBack.jpg"
categories: [ "Identity & Security" ]
tags: [ "Azure AD", "Azure AD Connect" ]
title: "Novità sul writeback dei gruppi da Azure AD verso Active Directory on-premises"
url: "/novita-writeback-gruppi-azure-ad-active-directory-on-premises-luglio-2022"
---
Qualche giorno fa sono state annunciate (in preview) nuove funzionalità di sincronizzazione per i gruppi, da Azure AD verso Active Directory on-premises. Vediamo insieme caratteristiche, limitazioni e conseguenze di queste novità.
- i gruppi di tipologia M365 potranno essere sincronizzati su AD on-prem come Universal Distribution Group, Security Group, Security Mail-Enabled Group e questa impostazione potrà essere gestita da PowerShell, MS Graph o dal portale Azure.
- Per i gruppi M365 è possibile anche impostare un settaggio tenan-wide affinchè i nuovi gruppi creati vengano sincronizzati.
- I gruppi di tipologia Security potranno essere sincronizzati su AD come Universal Security Group, anche in questo caso usando PowerShell, MS Graph o Microsoft Entra.

Ci sono quindi diverse possibilità di gestione della sincronizzazione attraverso il portale Microsoft Entra.

![Azure AD Groups Writeback](/images/01-AAD-Groups-WriteBack.jpg)

Quali sono gli scenario che si aprono? Opinioni personali e, quindi, del tutto discutibili:
- Dal punto di vista della flessibilità, questo è sicuramente un passo avanti.
- Bisognerà essere molto attenti a darsi una governance di permessi e di gestione dei gruppi, per evitare confusione e disordine sulle directory (sia AAD che AD on-premises).
- Dal punto di vista della sicurezza, si apre un grande tema di tiering di eventuali gruppi con privilegi: il tiering diventa ancora più importante di quanto non sia ora.

Per ulteriori approfondimenti, ecco tutti i riferimenti che ti servono per diventare un guru del writeback😃:
- [Use cloud groups in on-premises Active Directory with group writeback – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/use-cloud-groups-in-on-premises-active-directory-with-group/ba-p/3118023)
- [Azure AD Connect: Group Writeback – Microsoft Entra | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-group-writeback-v2)
- [group resource type – Microsoft Graph beta | Microsoft Docs](https://docs.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta)

E tu che ne pensi? Credi che queste novità ti saranno utili? Parliamone insieme nei commenti!

Il tuo IT Specialist, Riccardo