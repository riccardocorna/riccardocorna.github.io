---
date: 2022-06-27T09:00:00-00:00
description: "Grandi novità nella Windows 11 Insider Preview Build 25145 per LAPS: supporto nativo e in corso di sviluppo anche per Azure AD."
featured_image: "/images/laps1a-1024x629-1.jpg"
categories: [ "Identity & Security" ]
tags: [ "Windows", "LAPS", "News" ]
title: "Grandi novità per LAPS in Windows 11"
url: "/novita-laps-in-windows-11-insider-preview-build-25145"
---
Il Windows 11 Insider blog negli scorsi giorni ci ha dato una soddisfazione enorme: tra le (tante) novità delle nuove build di Windows, ce n’è una che spicca in particolare, anzi due.

![Windows LAPS GPO Settings](/images/laps1a-1024x629-1.jpg)

1. LAPS sarà integrato in Windows 11 nativamente
2. È in fase di progressiva estensione delle funzionalità un supporto nativo di LAPS su Azure Active Directory!

Per chi si stesse chiedendo:

> *“Rick, ma cosa diamine è LAPS?”*

Microsoft LAPS è un meccanismo di gestione delle password di amministratore locale per i computer joinati a dominio dei tuoi utenti. Fino a un po’ di tempo fa (e, in realtà, ancora oggi in molti fanno così), la password di amministratore locale era unica per tutte le postazioni, impostata su un’utenza che era “cablata” nell’immagine del sistema operativo che veniva eventualmente preparata e distribuita. Con LAPS, le password vengono impostate in modo casuale e archiviate in Active Directory (AD), protette da ACL, in modo che solo gli utenti idonei possano leggerle o richiederne la reimpostazione. LAPS è la soluzione al problema dell’uso di un account locale comune con una password identica in ogni computer in un dominio.

Quindi, perché queste due novità sono importanti?

- Perché, essendo ora incluso nativamente in Windows, si riduce l’effort di implementazione di LAPS, che è ormai una soluzione imprescindibile per qualunque parco client
- Perché, con il supporto ad Azure AD, viene abbattuto un altro grande vincolo nella dipendenza da un’infrastruttura on-premises

**Attenzione: come riporta il blog Microsoft, al momento la parte Azure AD è sì già presente, ma è ancora tutta da estendere e offre solo un set minimo di funzionalità. Ritengo quindi utile provarla più avanti nel tempo, quando sarà un po’ più matura.**

Ecco l’estratto a cui ho fatto cenno:

> *Note: the feature is fully functional for Active Directory domain-joined clients, but Azure Active Directory support is limited for now to a small set of Insiders. We will make an announcement once Azure Active Directory support is more broadly available.*

Come sempre, ecco il link all’annuncio e un po’ di documentazione relativa a LAPS:
- [Announcing Windows 11 Insider Preview Build 25145 | Windows Insider Blog](https://blogs.windows.com/windows-insider/2022/06/22/announcing-windows-11-insider-preview-build-25145/)
- [Microsoft Defender for Identity Microsoft LAPS usage assessments | Microsoft Docs](https://docs.microsoft.com/en-us/defender-for-identity/cas-isp-laps)

Detto questo, non vedo l’ora di metterci le mani sopra e di provarlo sul campo. E tu hai implementato LAPS nella tua infrastruttura? Il supporto ad Azure AD potrebbe farti considerare di muoverti verso un modello full-cloud di trust tra client e directory? Parliamone insieme nei commenti, ti aspetto!

Il tuo IT Specialist, Riccardo