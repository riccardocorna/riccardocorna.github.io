---
date: 2025-01-29T05:00:00-00:00
description: "Esplorate come assegnare e gestire le policy di Microsoft Intune per ottimizzare la sicurezza e l'efficienza dei vostri dispositivi e utenti. Mini-guida con consigli pratici e best practice."
image: "01-include-exclude-user-device-groups-matrix.png"
categories : [ "Modern Work" ]
tags: [ "Microsoft Intune", "Profili di configurazione", "Policy", "Best practice","Guida" ]
title: "Consigli veloci per assegnare le policy di Intune"
url: /intune-policy-assignment-support-matrix
---
🚀Specialisti IT! Alcune best practice quando si assegnano policy su Intune. 

E salvatevi l'immagine allegata con la matrice di supportabilità per le inclusioni ed esclusioni, stampandola in formato cartaceo chilometrico per essere appesa su tutti i muri. 😀

## Tabella di supportabilità delle assegnazioni

![Matrice di supportabilità per le assegnazioni, inclusioni ed esclusioni di profili di configurazione Microsoft Intune](01-include-exclude-user-device-groups-matrix.png)


| Scenario | Supporto |
|----------|-----------|
| 1 | ❕ Parzialmente supportato: Assegnare politiche a un gruppo di dispositivi dinamico escludendo un altro gruppo di dispositivi dinamico è supportato. Tuttavia, non è raccomandato in scenari sensibili alla latenza. Qualsiasi ritardo nel calcolo dell'appartenenza al gruppo di esclusione può causare l'offerta di politiche ai dispositivi. In questo scenario, si consiglia di utilizzare filtri anziché gruppi di dispositivi dinamici per escludere i dispositivi. |
| 2 | ✅ Supportato: Assegnare una politica a un gruppo di dispositivi dinamico escludendo un gruppo di dispositivi statico è supportato. |
| 3 | ❌ Non supportato: Assegnare una politica a un gruppo di dispositivi dinamico escludendo gruppi di utenti (sia dinamici che statici) non è supportato. Intune non valuta le relazioni tra gruppi di utenti e dispositivi, e i dispositivi degli utenti inclusi non sono esclusi. |
| 4 | ❌ Non supportato: Assegnare una politica a un gruppo di dispositivi dinamico escludendo gruppi di utenti (sia dinamici che statici) non è supportato. Intune non valuta le relazioni tra gruppi di utenti e dispositivi, e i dispositivi degli utenti inclusi non sono esclusi. |
| 5 | ❕ Parzialmente supportato: Assegnare una politica a un gruppo di dispositivi statico escludendo un gruppo di dispositivi dinamico è supportato. Tuttavia, non è raccomandato in scenari sensibili alla latenza. Qualsiasi ritardo nel calcolo dell'appartenenza al gruppo di esclusione può causare l'offerta di politiche ai dispositivi. In questo scenario, si consiglia di utilizzare filtri anziché gruppi di dispositivi dinamici per escludere i dispositivi. |
| 6 | ✅ Supportato: Assegnare una politica a un gruppo di dispositivi statico escludendo un altro gruppo di dispositivi statico è supportato. |
| 7 | ❌ Non supportato: Assegnare una politica a un gruppo di dispositivi statico escludendo gruppi di utenti (sia dinamici che statici) non è supportato. Intune non valuta le relazioni tra gruppi di utenti e dispositivi, e i dispositivi degli utenti inclusi non sono esclusi. |
| 8 | ❌ Non supportato: Assegnare una politica a un gruppo di dispositivi statico escludendo gruppi di utenti (sia dinamici che statici) non è supportato. Intune non valuta le relazioni tra gruppi di utenti e dispositivi, e i dispositivi degli utenti inclusi non sono esclusi. |
| 9 | ❌ Non supportato: Assegnare una politica a un gruppo di utenti dinamico escludendo gruppi di dispositivi (sia dinamici che statici) non è supportato. |
| 10 | ❌ Non supportato: Assegnare una politica a un gruppo di utenti dinamico escludendo gruppi di dispositivi (sia dinamici che statici) non è supportato. |
| 11 | ✅ Supportato: Assegnare una politica a un gruppo di utenti dinamico escludendo altri gruppi di utenti (sia dinamici che statici) è supportato. |
| 12 | ✅ Supportato: Assegnare una politica a un gruppo di utenti dinamico escludendo altri gruppi di utenti (sia dinamici che statici) è supportato. |
| 13 | ❌ Non supportato: Assegnare una politica a un gruppo di utenti statico escludendo gruppi di dispositivi (sia dinamici che statici) non è supportato. |
| 14 | ❌ Non supportato: Assegnare una politica a un gruppo di utenti statico escludendo gruppi di dispositivi (sia dinamici che statici) non è supportato. |
| 15 | ✅ Supportato: Assegnare una politica a un gruppo di utenti statico escludendo altri gruppi di utenti (sia dinamici che statici) è supportato. |
| 16 | ✅ Supportato: Assegnare una politica a un gruppo di utenti statico escludendo altri gruppi di utenti (sia dinamici che statici) è supportato. |

## Consigli e buone pratiche

📌 **Gruppi Inclusi o Esclusi**: Usate questi gruppi come punto di partenza per assegnare le policy. Il gruppo Microsoft Entra è il gruppo limitante, quindi usate l'ambito del gruppo più piccolo possibile e filtri per affinare l'assegnazione.

📌 **Gruppi statici**: I gruppi Microsoft Entra assegnati possono essere aggiunti ai gruppi Inclusi o Esclusi. Assegnate staticamente i dispositivi pre-registrati o per implementazioni ad hoc.

📌 **Gruppi dinamici di utenti**: Possono essere aggiunti ai gruppi Inclusi o Esclusi.

📌 **Gruppi Esclusi**: Possono contenere utenti o dispositivi.

📌 **Gruppi dinamici di dispositivi**: Possono essere aggiunti ai gruppi Inclusi, ma possono avere latenza nel popolamento. In scenari sensibili alla latenza, usate filtri per indirizzare dispositivi specifici e assegnate le policy ai gruppi di utenti.

📌 **Scenari sensibili alla latenza**: Per assegnare policy ai dispositivi appena registrati, create un filtro per indirizzare i dispositivi desiderati e assegnate la policy con questo filtro ai gruppi di utenti. Non assegnate ai gruppi di dispositivi.

📌 **Scenari senza utenti**: Create un filtro per indirizzare i dispositivi desiderati e assegnate la policy con il filtro al gruppo "Tutti i dispositivi".

📌 **Evitare gruppi dinamici di dispositivi nei gruppi Esclusi**: La latenza nel calcolo del gruppo dinamico durante la registrazione può causare risultati indesiderati, come la distribuzione di app e policy indesiderate prima che l'appartenenza al gruppo escluso sia popolata.

## Documentazione allegata
Ecco il documento ufficiale che mi ha dato lo spunto per questo post.

📖 [Assign policies in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/device-profile-assign)