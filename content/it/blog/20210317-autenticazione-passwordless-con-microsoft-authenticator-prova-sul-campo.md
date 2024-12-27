---
date: 2021-03-17T08:00:00-00:00
description: "Scopri l'autenticazione passwordless: dimentica la tua password e autenticati a tutti i servizi di Microsoft 365 col solo aiuto di un'app."
featured_image: "/images/02-autenticazione-passwordless-azure-ad-schermate.png"
categories: [ "Identity & Security"]
tags: [ "Azure AD", "Multi Factor Authentication", "Passwordless", "Microsoft authenticator"]
title: "Autenticazione passwordless con Microsoft Authenticator: prova sul campo"
url: "/autenticazione-passwordless-con-microsoft-authenticator-prova-sul-campo"
---
Diario del capitano, data astrale 20210317: l’autenticazione passwordless permette di usare servizi e applicazioni senza ricordare la propria password e, quando questa scade dopo i classici 60 o 90 giorni che l’amministratore IT ha impostato, dopo averla cambiata non è più necessario doverla reinserire 4 o 5 volte per dispositivo.

Sembra fantascienza o un futuro lontanissimo? In realtà la data astrale è quella di oggi, 17 Marzo 2021, e il meccanismo che ti ho illustrato non è il futuro ma è già tra noi 🙂

Nelle ultime settimane ho testato una delle possibilità di accesso passwordless che Microsoft mette a disposizione: ti racconto com’è andata e vedremo insieme quali sono le varie possibilità.

Prima però, fissiamo alcuni concetti di base.

## Cosa significa “Passwordless”?
L’autenticazione passwordless è un metodo di autenticazione che, pur basandosi in un qualche modo sulla classica combinazione username/password, la sostituisce completamente. Come?

Un’autenticazione, in generale, può avvenire in diversi modi e puoi dimostrare che “tu sei proprio tu” attraverso:
- **qualcosa che conosci**: questo è il metodo “classico” utilizzato da tutti fino ad ora, ovvero basato sulla conoscenza (appunto, qualcosa che conosci) di due parametri: nome utente e password;
- **qualcosa che possiedi**: è il tipico caso dell’autenticazione a più fattori (Multi Factor Authentication o, per gli amici, MFA). Attraverso un codice, una OTP o un qualunque cosa che presupponga la presenza di qualcosa che tu e solo tu puoi possedere, dimostri che tu sei proprio tu;
- **qualcosa che “sei”**: in un certo senso, siamo sempre nell’ambito dell’autenticazione a più fattori con l’unica particolarità che uno dei fattori di autenticazione non è una password e non è qualcosa che possiedi ma sei proprio tu con le tue caratteristiche fisiche, come ad esempio il viso, le impronte digitali, la retina, eccetera.

Cosa c’entra l’autenticazione passwordless con tutto questo? C’entra perché **un’autenticazione passwordless sostituisce la password con qualcos’altro che conosci, che possiedi o che sei**.

Intendiamoci, alla base di tutto questo c’è comunque una password associata alla tua utenza che continuerà a scadere ogni N giorni secondo le policy aziendali ma il grande vantaggio è che, sfruttando opportune configurazioni e usando applicazioni che supportano la [Modern Authentication](/modern-authentication-multi-factor-authentication-exchange-online-skype-for-business-online/), **sarai in grado di autenticarti ai tuoi servizi Microsoft 365 anche senza ricordare la tua password**:
- qualcos’altro che conosci, come ad esempio un **PIN**;
- qualcosa che possiedi: nel caso di questa prova sul campo, uno smartphone dove ho installato e configurato l’app **Microsoft Authenticator**;
- una tua caratteristica fisica: ad esempio, la scansione del tuo viso o le tue impronte digitali nel caso di **Windows Hello for Business**.

## Quali sono i metodi di autenticazione passwordless supportati da Microsoft?
Vediamoli subito:
- **Microsoft Authenticator app**: **è il metodo oggetto di questa prova sul campo** e può essere usato per autenticarsi alle applicazioni di M365 da qualunque dispositivo; non può essere usato come metodo di autenticazione alla propria workstation: per ottenere quel risultato dovrai vedere il punto successivo;
- **Windows Hello for Business**: sfrutta le caratteristiche biometriche di scansione del viso (se hai una webcam che è in grado di rilevare la profondità del campo) oppure delle impronte digitali o, ancora, tramite PIN; questa tecnologia è specifica per introdurre una sorta di MFA alla login del proprio PC. Il presente articolo non tratta questa casistica;
- **FIDO2 security keys**: tipicamente sono delle chiavette da inserire nella presa USB del proprio PC, in caso di autenticazione da PC, e che comprendono spesso anche un chip NFC da usare nel caso in cui l’autenticazione avvenga da smartphone. Il presente articolo non tratta questa casistica.

## Scenario della mia prova sul campo
È un argomento molto complesso e non è facile “mettere a terra” questi concetti complessi in così poche righe e in un solo articolo. **Per questo motivo, per ora ho deciso di documentare questa prova sul campo limitandomi al solo metodo di autenticazione “Microsoft Authenticator app”**, che copre i casi d’uso che ti ho raccontato nel paragrafo precedente. Inoltre, il mio scenario ha delle caratteristiche peculiari che, in un certo senso, semplificano l’implementazione di tale tecnologia. Ecco le sue caratteristiche:
- utenza full cloud, senza nessuna Active Directory on-premises;
- la mia utenza è già configurata per effettuare la MFA e, quindi, ho già registrato i miei contatti e i miei fattori di verifica (requisiti necessario);
- Azure AD Premium P1;
- ho installato e configurato sul mio smartphone l’applicazione Microsoft Authenticator, che puoi trovare ai seguenti link:
    - [Microsoft Authenticator su Apple App Store](https://apps.apple.com/it/app/microsoft-authenticator/id983156458);
    - [Microsoft Authenticator su Google Play Store](https://play.google.com/store/apps/details?id=com.azure.authenticator).
- lo smartphone su cui è installata l’app Microsoft Authenticator deve essere registrato ad Azure AD (anche questo è un requisito necessario);
- **dopo aver configurato gli opportuni requisiti lato portale Azure AD, ho cambiato la password della mia utenza con una stringa di 20 caratteri contenenti maiuscole, minuscole, numeri, caratteri speciali. Non ho memorizzato questa password, non la ricordo e, anche volendo, credo che mi sarebbe molto difficile farlo.**

## Perfetto, ora che abbiamo apparecchiato lo scenario, vediamo come funziona.
Come funziona l’autenticazione passwordless tramite Microsoft Authenticator app?
Ecco il flusso di funzionamento di questo tipo di autenticazione.

[![Flusso di autenticazione passwordless con Microsoft Authenticator App](/images/01-autenticazione-passwordless-azure-ad-flusso-app.png)](/images/01-autenticazione-passwordless-azure-ad-flusso-app.png)

1. inserisci il tuo nome utente;
2. Azure AD rileva che la tua utenza è configurata con un metodo di autenticazione forte e quindi scatena il relativo flusso;
3. viene inviata una notifica al tuo smartphone (iOS/Android);
4. ricevi la notifica e apri l’app Microsoft Authenticator;
5. una volta aperta l’app, Azure AD riceve il segnale che l’app è stata aperta ed invia la “challenge” per verificare che “tu sei proprio tu”; il contenuto è una sorta di “quiz” a risposta multipla in cui una delle opzioni è lo stesso numero che è comparso sullo schermo del PC;
6. completi la challenge inserendo la risposta corretta;
7. la tua risposta viene firmata con una chiave crittografica privata e rispedita ad Azure AD;
8. Azure AD fa le sue verifiche e restituisce un token di accesso.

Questa la spiegazione formale: ti sei perso? Tranquillo, anch’io! 🤣
Guardiamo in faccia tutti gli elementi che ti ho appena descritto come se stesse accadendo ora e semplificando i passaggi!

[![Microsoft Authenticator App challenge](/images/02-autenticazione-passwordless-azure-ad-schermate-b.png)](/images/02-autenticazione-passwordless-azure-ad-schermate-b.png)

Hai appena aperto il browser Edge e vuoi andare sul portale di Office.  
Inserisci il tuo nome utente nel browser per autenticarti a Microsoft 365.  
Compare a schermo il numero 83 (la “challenge”).  
Ti arriva la notifica.  
Tocchi la notifica, si apre Microsoft Authenticator, compare il “mini quiz” (i puristi mi perdoneranno questa metafora a fine didattico).  
Tocchi il numero che rappresenta la soluzione corretta al quiz: in questo caso, “83”.  
**La soluzione è corretta? Sì? Perfetto, sei autenticato!**

[![Autenticato sul portale di Microsoft 365](/images/03-autenticazione-passwordless-azure-ad-successful-auth.png)](/images/03-autenticazione-passwordless-azure-ad-successful-auth.png)

**Hai notato? In tutto questo flusso, non viene richiesta in nessun modo la password!**

Visto? Così è più semplice!

Perfetto, ora abbiamo visto come funziona.
Ma come si configura? Dopo alcune riflessioni, ho deciso di non pubblicare una procedura di configurazione perché, come avrai visto dalla descrizione fatta qualche paragrafo più in alto, il mio scenario è un po’ troppo semplicistico rispetto alle esigenze di uno scenario “reale” e non sarebbe stato molto utile descrivere la procedura.

## Autenticazione Passwordless: Frequently Asked Questions (F.A.Q.)
Ho però pensato di stilare una lista di Frequently Asked Question che potrebbero venirti in mente approcciandoti per la prima volta all’autenticazione passwordless. Eccole!

### Il mio scenario è full cloud ma con tante utenze, funzionerà come hai descritto?
Risposta semplice: sì! E puoi anche abilitare questa funzione in maniera graduale, selezionando uno o più gruppi di AD/Azure AD e popolandoli mano a mano.

### Scenario ibrido con Active Directory on-premises: come funziona?
Quando ti autenticherai su applicazioni, file server o, più in generale, su qualunque workload on-premises, sfrutterai Active Directory e non verrà scatenato questo meccanismo.
Quando ti autenticherai a servizi Microsoft 365, verrà scatenato questo meccanismo ad ogni scadenza del token o ad ogni autenticazione da un nuovo dispositivo/browser/applicazione.

### E quando scade la password che succede?
Scenario full-cloud: la cambi e, all’autenticazione successiva, ti verrà proposta una nuova challenge.
Scenario ibrido con AD on-premises: devo ancora testarlo e, appena avrò modo di farlo, integrerò i risultati in questo stesso articolo.

### Davvero posso dimenticarmi la password?
Al momento la risposta è: **NO**. Perché? Perché in alcuni scenari aziendali dove l’utenza di dominio è utilizzata per autenticarsi anche ad altri servizi/applicazioni che non supportano Modern Authentication, come ad esempio una rete Wi-Fi aziendale, la cara vecchia password è sempre necessaria! 🙁 Quindi, nonostante tutto, usa una password sicura e conservala in un posto sicuro!

Ti vengono in mente altre domande? Parliamone sui miei profili social in modo da arricchire questo elenco!

## Per approfondire l’autenticazione passwordless
Ecco una raccolta di articoli ufficiali Microsoft che ti aiuteranno ad approfondire in maniera più completa l’argomento e soddisferanno la tua sete di “passwordless”! 😉
- [Azure Active Directory passwordless sign-in | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-authentication-passwordless)
- [Passwordless sign-in with the Microsoft Authenticator app – Azure Active Directory | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-authentication-passwordless-phone)

## Grazie
Come sempre, grazie di avermi seguito fino alla fine di questo articolo lunghissimo e tostissimo. A presto!