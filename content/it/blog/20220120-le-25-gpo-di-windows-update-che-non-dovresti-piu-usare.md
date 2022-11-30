---
date: 2022-01-20T08:00:00-00:00
description: "Importanti novità per le impostazioni dei template ADMX sulle GPO di Windows Update in Active Directory."
featured_image: "/images/01-windows-update-gpo-not-to-use.jpg"
categories: [ "Identity & Security" ]
tags: [ "Active Directory", "Windows Update"]
title: "Le 25 GPO di Windows Update che non dovresti più usare"
url: "/le-25-gpo-di-windows-update-che-non-dovresti-piu-usare"
---
Ci sono 25 GPO che non dovresti impostare per gestire Windows Update, se il tuo parco client ha versioni di Windows dalla 20H2 in su, Windows 11 compreso. Perché?

In breve: la gestione degli update via GPO da Windows 10 1511 è cambiata MOLTO. Come risultato, si sono accumulate diverse impostazioni legacy che, sulle versioni più recenti di Windows, potrebbero portare ad un’esperienza poco efficace e funzionale per quanto riguarda gli aggiornamenti.

Per questo, nel nuovo template ADMX per Windows 11, tutto ciò che riguarda le impostazioni di Windows Update considerate “legacy” si trova ora in una sottocartella chiamata “Legacy Policies”.

Morale della favola: se vuoi gestire in maniera efficace gli update sui client Windows 10 (>= 20H2) e Windows 11, usa tutte le altre impostazioni al di fuori della cartella Legacy Policies 😃.

![Windows Update GPO](/images/01-windows-update-gpo-not-to-use.jpg)

Troverai tutti i dettagli in questo articolo Microsoft molto interessante che merita la massima diffusione, in ottica di aggiornamento del parco client con le versioni più recenti di Windows 10 o con Windows 11.
- [Why you shouldn’t set these 25 Windows policies – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/why-you-shouldn-t-set-these-25-windows-policies/ba-p/3066178)

L’aggiornamento dei template ADMX è una cosa molto importante da fare: quando è stata l’ultima volta che lo hai fatto sulla tua infrastruttura? Ti aspetto sui miei social per parlarne insieme!

Il tuo IT Specialist, Riccardo