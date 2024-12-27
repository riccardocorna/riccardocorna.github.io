---
date: 2022-02-08T08:00:00-00:00
description: "Disponibile in preview la possibilità di gestire la membership dei gruppi locali di un PC attraverso Microsoft Endpoint Manager."
featured_image: "/images/01-mem-endpoint-security-account-protection.jpg"
categories: [ "Modern Endpoint" ]
tags: [ "Intune", "News" ]
title: "Configurazione dei gruppi locali su PC in Microsoft Endpoint Manager (preview)"
url: "/configurazione-dei-gruppi-locali-microsoft-endpoint-manager"
---
Alzi la mano chi stava aspettando questa funzione: 🙋🏻‍♂️. Finalmente, tramite un menu nativo ed integrato a portale Microsoft Endpoint Manager, sarà possibile configurare i membri dei gruppi locali su PC, gestendone quindi la membership con utenti e/o gruppi di Azure AD e di Active Directory on-prem!

Questa configurazione è ora in **preview** da portale MEM e si può trovare al seguente nodo:

- **Endpoint security** –> **Account protection**

[![Intune Account protection blade](/images/01-mem-endpoint-security-account-protection.jpg)](/images/01-mem-endpoint-security-account-protection.jpg)

Una volta dentro le impostazioni del profilo, sarà possibile configurare le policy del caso per gestire le membership dei gruppi locali dei PC.

Questa è una feature che in tantissimi aspettavano e, a mio modo di vedere, segna un punto davvero importante di svolta nel percorso evolutivo della gestione full-cloud dei dispositivi.

Vuoi saperne di più? Ecco la solita vagonata di articoli utili e documentazione ufficiale:
- [New settings available to configure local user group membership in endpoint security – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/intune-customer-success/new-settings-available-to-configure-local-user-group-membership/ba-p/3093207)
- [Manage account protection settings with endpoint security policies in Microsoft Intune | Microsoft Docs](https://docs.microsoft.com/en-us/mem/intune/protect/endpoint-security-account-protection-policy)

***Nota***: *al momento la funzionalità è in **preview**. E se tu avessi necessità di gestire in maniera automatica che un utente sia o meno amministratore di macchina in fase di deployment del PC, attraverso Windows Autopilot? Ho la risposta per te nel prossimo articolo: stay tuned!*

E tu, che ne pensi di questa funzionalità in anteprima? Parliamone insieme sui miei social, ti aspetto!

Il tuo IT Specialist, Riccardo
