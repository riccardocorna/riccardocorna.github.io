---
date: 2025-04-02T05:00:00-00:00
description: "Windows Passwordless Experience: una guida completa su cos'è, come configurarla tramite Intune e i suoi vantaggi per la sicurezza."
image: "01-windows-passwordless-experience.jpg"
categories : [ "Modern Work", "Security" ]
tags: [ "Microsoft Intune", "Windows", "Passwordless Experience", "Windows Hello for Business", "Video", "Guida", "Cloud Endpoint Diary"]
title: "Windows Passwordless Experience"
url: /windows-passwordless-experience
---
Ciao a tutti, specialisti IT! 👋 In questo articolo, esploreremo la funzionalità di Windows chiamata "Passwordless Experience". Scopriremo insieme cos'è, come si configura tramite Intune e quali sono i suoi vantaggi per la sicurezza. 🚀

## Video
Se preferite guardare il video completo, potete vederlo qui sotto oppure sul mio canale YouTube. Altrimenti, continuate pure a leggere uqesto articolo.

{{< youtube t-UKX39Mc5w >}}

## Introduzione alla Windows Passwordless Experience
La Windows Passwordless Experience è una policy di sicurezza che promuove l'utilizzo di metodi di autenticazione senza password, come Windows Hello for Business e chiavette FIDO2. Questa configurazione è impostata tramite Intune e si attiva per l'ultimo utente che ha effettuato il login sulla postazione.

Vediamo qual è la situazione standard su una macchina dove è configurato Windows Hello for Business ma senza Passwordless Experience.

{{< youtubestartend t-UKX39Mc5w 78 95 >}}

## Configurazione della policy di sicurezza via Intune
Configurare la Windows Passwordless Experience tramite Intune è molto semplice. Basta attivare un interruttore nelle impostazioni di Intune. Questo permette di promuovere l'utilizzo di metodi di autenticazione senza password sulla schermata di login e in altre situazioni specifiche dove è richiesta un'autenticazione.

Ecco come si configura.

{{< youtubestartend t-UKX39Mc5w 103 138 >}}

## Effetti della configurazione sulla schermata di login e sui settings di sistema
Una volta configurata la policy, la schermata di login dell'utente non mostrerà più l'opzione per l'autenticazione tramite password. Tuttavia, la password può ancora essere utilizzata in situazioni specifiche, come l'elevazione dell'UAC (User Account Control) o per l'autenticazione di un operatore di help desk.

Vediamo cos'è successo dopo aver configurato e applicato la policy al nostro client Windows.

{{< youtubestartend t-UKX39Mc5w 149 170 >}}

## Come continuare a utilizzare la password quando necessario
Nonostante la promozione dei metodi di autenticazione senza password, è possibile continuare a utilizzare la password. Ad esempio, un operatore di help desk può autenticarsi sulla postazione utilizzando l'opzione "Other User". Questo garantisce che la configurazione non inibisca totalmente l'uso della password, ma invogli l'utente ad utilizzare metodi di autenticazione più sicuri.

Vediamo come usare la password anche con la Passwordless Experience configurata.

{{< youtubestartend t-UKX39Mc5w 209 230 >}}

## Documentazione allegata
Volete approfondire? Ecco un bel documento con tutti i dettagli della funzionalità.

📌 [Windows Passwordless Experience](https://learn.microsoft.com/en-us/windows/security/identity-protection/passwordless-experience/)

## Conclusione
Se avete già implementato Windows Hello for Business nella vostra infrastruttura, la configurazione della Windows Passwordless Experience può essere un ottimo complemento per migliorare la sicurezza. Avete mai provato la Passwordless Experience? Lasciate un commento e parliamone insieme! Non dimenticate di seguirmi su LinkedIn, sul blog e di iscrivervi al mio canale YouTube per non perdervi nemmeno un contenuto. 📲

Grazie per aver letto l'articolo fino alla fine e a presto... mitici! 🎉

Il vostro IT Specialist,  
Riccardo