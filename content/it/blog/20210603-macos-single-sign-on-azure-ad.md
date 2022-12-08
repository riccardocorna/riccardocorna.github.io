---
date: 2021-06-03T08:00:00-00:00
description: "Grazie al macOS Single Sign-On per Azure AD, diminuiranno sensibilmente il numero di richieste di autenticazione a Microsoft 365."
featured_image: "/images/01-macOS-AzureAD-single-Sign-On.png"
categories: [ "Identity & Security"]
tags: [ "macOS", "Azure AD", "Single Sign-On"]
title: "macOS Single Sign-On su Azure AD"
url: "/macos-single-sign-on-azure-ad"
---
In questi giorni di ponte in cui i clienti sono in ferie e io no 😒, mi sono divertito a sperimentare una nuova funzionalità in preview: il macOS Single Sign-On (SSO) per Azure AD. Esatto, potrai fare Single Sign-On su applicazioni e servizi Microsoft 365 con il Mac!

![Schermata Azure AD Single Sign-On Extension per macOs](/images/01-macOS-AzureAD-single-Sign-On.png)

Ti starai domandando: "A cosa diamine serve?"

**Questa funzionalità servirà ad autenticare te e il tuo fantastico Mac molto più facilmente ai servizi e alle applicazioni di Microsoft 365 senza ripetuti prompt di inserimento credenziali**, rendendo l’esperienza utente ancora più liscia e senza soluzione di continuità.

La configurazione richiede che:
- sia installata l’app Company Portal sul Mac;
- che il Mac sia stato registrato su MEM (Intune) in modalità User Approval, tramite Apple School Manager o Apple Business Manager.

⚠️ ***Attenzione!*** Il plug-in di tipo “Microsoft Azure AD” è in preview e quindi non è ancora consigliabile usarlo in produzione. Se vuoi sperimentare anche tu, testalo in un ambiente isolato dove sei sicuro di non dare alcun tipo di impatto agli utenti finali. Per quanto riguarda il mio piccolo esperimento, nei prossimi giorni terrò d’occhio come si comporta e ti aggiornerò.

Ecco qui tutte le informazioni del caso, se il tarlo della curiosità si è impossessato di te: 😉

- [Microsoft Enterprise SSO plug-in for Apple devices – Microsoft identity platform | Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/develop/apple-sso-plugin)
- [Create iOS/iPadOS or macOS device profile with Microsoft Intune – Azure | Microsoft Docs](https://docs.microsoft.com/en-us/mem/intune/configuration/device-features-configure#single-sign-on-app-extension)
- [macOS device feature settings in Microsoft Intune – Azure | Microsoft Docs](https://docs.microsoft.com/en-us/mem/intune/configuration/macos-device-features-settings#single-sign-on-app-extension)

In una conversazione privata che ho avuto qualche tempo fa, ho scritto quanto segue: "... credo che mai prima d’ora ci sia stato un momento dove i prodotti dei due mondi (Microsoft ed Apple) vanno così d’accordo..."

E ne ho ogni giorno di più conferma quando testo funzionalità come il macOS Single Sign-On.
Microsoft sta davvero lavorando a strettissimo contatto con Apple e i risultati si vedono.

E tu, quali misure hai adottato per integrare al meglio macOS all’interno dell’azienda? Ti aspetto nei commenti per parlarne!

Il tuo IT Specialist, Riccardo
