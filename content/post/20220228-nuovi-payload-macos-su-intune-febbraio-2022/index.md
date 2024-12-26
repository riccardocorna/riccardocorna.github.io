---
date: 2022-02-28T09:00:00-00:00
description: "Nuovi payload nativi di macOS su Intune, per gestire alcune configurazioni che prima era possibile gestire solo con Custom Profile."
image: "01_new-in-mem-2202.png"
categories: [ "Modern Work" ]
tags: [ "macOS", "Intune", "News" ]
title: "Nuovi payload macOS su Intune (Febbraio 2022)"
url: "/nuovi-payload-macos-su-intune-febbraio-2022"
---
Era un po’ che non parlavo di macOS e Intune! Rimedio subito a questa mancanza raccontadoti di alcune novità e nuove impostazioni disponibili su Intune per la gestione di macOS.

Ci sono infatti nuovi settaggi disponibili nel catalog di gestione per macOS, ecco quali sono:
- **Domains**: gestione dei domini per le mail, per il salvataggio delle password di alcune URL, impostazione di quali domini considerare gestiti (approfondimenti su [Domains | Apple Developer Documentation](https://developer.apple.com/documentation/devicemanagement/domains))
- **Global HTTP Proxy**: ora ci sono tutti i payload necessari per configurare un proxy (approfondimenti su [GlobalHTTPProxy | Apple Developer Documentation](https://developer.apple.com/documentation/devicemanagement/globalhttpproxy))
- **Printing**: tutti i payload necessari per configurare le stampanti (approfondimenti su [Printing | Apple Developer Documentation](https://developer.apple.com/documentation/devicemanagement/printing))
- **Profile Removal Password**: è possibile richiedere una password per permettere la rimozione di un profilo (approfondimenti su [ProfileRemovalPassword | Apple Developer Documentation](https://developer.apple.com/documentation/devicemanagement/profileremovalpassword))

Come sempre, oltre alla descrizione delle novità, ho raccolto per te anche un bellissimo video “hands-on”, giusto per vedere subito all’opera questi nuovi payload.

{{< youtube wCKngitN_6o>}}

Infine, ecco un approfondimento su queste novità e altre novità di Intune per questo mese di Febbraio 2022:
- [Blog | New in Microsoft Endpoint Manager – 2202 | Tech Community](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2202-february-edition/ba-p/3211530)

Questi payload erano tra i più richiesti dalla community nonché tra i più complessi e rognosetti da configurare con un Custom Profile: da oggi queste impostazioni sono native!

Ultima nota: questa è solo la prima release di un’ondata di payload nativi per macOS che arriveranno. Intune 💓 sempre di più macOS! 😉

E tu hai mai provato a configurare questi profili in maniera custom? Se sì, passerai subito a quelli nativi? Parliamone insieme su Linkedin o Twitter!

Il tuo IT Specialist, Riccardo