---
date: 2023-02-13T08:00:00-00:00
description: "Novità in ambito Security Settings Management, una modalità di distribuzione via Intune delle impostazioni di Microsoft Defender for Endpoint anche per dispositivi non enrollati in Intune."
featured_image: "/images/endpoint-security-overview.png"
categories : ["Identity & Security"]
tags: [ "Microsoft Defender for Endpoint", "Intune" ]
title: "Microsoft Defender for Endpoint Security Settings Management: supporto ampliato per le regole di ASR"
url: /supporto-ampliato-asr-rules-security-settings-management-microsoft-defender-for-endpoint
---
Novità interessante in Public Preview per in ambito Security Settings Management di Microsoft Defender for Endpoint: è stato ampliato il supporto alle regole di Attack Surface Reduction in questa modalità.

Cos'è il "Security Settings Management" in Microsoft Defender for Endpoint?
È una modalità di gestione delle impostazioni di sicurezza di MDE realizzata per fare in modo di poterle distribuire via Intune anche per quei dispositivi che non sono "enrollati"/"enrollabili", come ad esempio macchine Windows Server, eccetera.
È una buona alternativa alle GPO e l'indubbio vantaggio è quello di poter gestire la distribuzione delle policy di sicurezza da un unico punto centralizzato, ovvero Intune, anziché usare, ad esempio, le GPO di Active Directory. Funziona bene anche per macchine standalone che non sono a dominio, per esempio.
Fino ad ora, però, essendo una funzione relativamente nuova, a mio modo di vedere mancava qualcosina rispetto ad altri strumenti più consolidati.

Con questa aggiunta di regole di Attack Surface Reduction, il Security Settings Management diventa sicuramente più appetibile!

Alcuni link per approfondire l'argomento:
- [Expanding support for Attack surface reduction rules with Microsoft Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/expanding-support-for-attack-surface-reduction-rules-with/ba-p/3733358)
- [Push ASR rules with Security Settings Management on Microsoft Defender for Endpoint managed devices](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/push-asr-rules-with-security-settings-management-on-microsoft/ba-p/3635129)
- [Security Settings Management in Microsoft Defender for Endpoint is now generally available](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/security-settings-management-in-microsoft-defender-for-endpoint/ba-p/3356970)
- [Manage Microsoft Defender for Endpoint on devices with Microsoft Endpoint Manager](https://learn.microsoft.com/en-us/mem/intune/protect/mde-security-integration?view=o365-worldwide#configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management)

Qualcuno di voi ha già sfruttato questa modalità di gestione? Parliamone insieme sui profili social di ITSpecialist.cloud!

Riccardo