---
date: 2025-01-22T05:00:00-00:00
description: "Come configurare Platform Single Sign-On su macOS con Microsoft Entra e Intune. Guida rapida su metodi di autenticazione, policy di compliance e consigli utili per un login sicuro e integrato."
image: "01-macos-platform-single-sign-om-sso-password.jpg"
categories : [ "Security", "Modern Work" ]
tags: [ "Microsoft Intune", "Intune", "macOS", "Platform SSO", "Single Sign-On", "Microsoft Entra", "Video", "Guida" ]
title: "macOS Platform SSO: login sul Mac con utenza Microsoft Entra"
url: /macos-platform-single-sign-om-sso-password
---
Ciao a tutti, specialisti IT! Oggi parliamo di Platform Single Sign-On su macOS!

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube qtEkLFvppG8 >}}

## Login su macOS con utenza Microsoft entra: ecco il Platform SSO

### Introduzione
Che cos'è il Platform Single Sign-On? È una funzionalità che permette di fare login sul Mac con le proprie credenziali Microsoft Entra. Esatto, non più solo applicazioni: parlo proprio di usare le credenziali di Entra sulla schermata di login del Mac.

### Metodi di Autenticazione Supportati
Ci sono diversi metodi di autenticazione supportati, come Secure Enclave, password e smart card. Per approfondimenti e dettagli su ognuno di questi metodi, vi rimando alla documentazione che vi lascio come sempre qui sotto.

- [Configure Platform SSO for macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/platform-sso-macos)

### Configurazione della Policy
Bando alle ciance, oggi quindi senza ulteriori fronzoli vi faccio vedere come si configura la policy del Platform Single Sign-On in modalità di autenticazione password. Vedremo anche la fase di join del Mac ad Entra ID e infine un'esperienza di login con UPN e password.

Pronti? Creiamo la policy!

{{< youtubestartend qtEkLFvppG8 58 166 >}}

### Join del Mac ad Entra
La policy è stata creata e assegnata. Ora non resta che attendere che venga recepita dal Mac per poi joinarlo ad Entra ID.

{{< youtubestartend qtEkLFvppG8 173 211 >}}

Perfetto! Joinato! Ora vediamo se effettivamente è tutto andato a buon fine facendo un paio di verifiche sul Mac.

{{< youtubestartend qtEkLFvppG8 217 228 >}}

### Prova di Autenticazione on UPN e password
Ok, siamo arrivati fino a qui, perché non fare una prova di autenticazione sulla schermata dei login del Mac con UPN e password? Facciamolo! Finito! Tutto qui! Ora possiamo finalmente fare login sul Mac con le nostre credenziali Microsoft Entra.

{{< youtubestartend qtEkLFvppG8 236 254 >}}

### Consigli Utili
Consiglio veloce: se implementate la modalità di autenticazione password su Intune e state usando delle policy di compliance che forzano la complessità della password locale sul Mac, liberatevi di questa impostazione perché fa abbastanza a pugni col Platform Single Sign-On. Lasciate quindi che sia la password policy di Microsoft Entra o della vostra Active Directory a prendere il controllo della complessità della password.

Altro consiglio velocissimo: se state usando l'Enterprise Single Sign-On plugin, quello che vi permetteva di fare autenticazione in SSO sulle applicazioni, disassegnate questa policy. Platform Single Sign-On infatti sostituisce completamente l'Enterprise Single Sign-On e avere entrambe le policy può portare a dei conflitti, anzi sicuramente porta a dei conflitti.

### Conclusione
Siamo alla fine di questo video. Grazie per avermi seguito fino a qui. Voi avete già implementato Platform Single Sign-On? Raccontatemi la vostra esperienza nei commenti del video o sui miei profili social.

Come sempre vi invito ad iscrivervi al mio canale YouTube e a premere la campanella. Questo permette a voi di non perdere nemmeno un contenuto e per me è invece un grosso aiuto per far crescere il canale. Grazie ancora!

A presto... MITICI!

Il vostro IT Specialist,  
Riccardo