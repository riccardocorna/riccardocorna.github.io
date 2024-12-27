---
date: 2020-07-01T08:00:00-00:00
description: "Quali sono gli strumenti che permettono allo staff IT di implementare una strategia di Modern Workplace Management efficace e consistente?"
featured_image: "/images/07-Modern-Workplace-Management-Approach.png"
categories: [ "Modern Endpoint"]
tags: [ "Modern Workplace", "Intune", "Modern Device Management" ]
title: "Modern Workplace management: cosa c’è dietro le quinte?"
url: "/modern-workplace-management"
---
Dopo aver visto [il significato di Modern Workplace e le sue implicazioni dal punto di vista dell’utente finale](/cosa-significa-modern-workplace/), oggi affronto gli aspetti di Modern Workplace Management ovvero tutto ciò che c’è dietro le quinte e interessa a noi giovani (più o meno) nerd che implementiamo e gestiamo questo popò di roba.

## Cos’è il Modern Workplace Management?
Parto subito con una definizione che aggiunge una nuova sfumatura alla definizione di Modern Workplace: definiamo ora cos’è il Modern Workplace Management:

> *Il Modern Workplace Management racchiude tutte le tecnologie che servono a gestire, organizzare, orchestrare gli strumenti digitali usati dalle persone. Queste tecnologie devono garantire un’esperienza utente consistente, sicura, produttiva e devono permettere il miglior compromesso possibile tra mobilità ed usabilità. Inoltre, devono permettere una gestione unificata e semplice per lo staff IT.*

Perfetto! Ora che sai cosa significa Modern Workplace Management, approfondiamo quali sono le caratteristiche che queste tecnologie devono implementare e garantire:

- **Servizi e applicazioni cross-platform**: la possibilità di accedere a servizi e applicazioni aziendali indipendentemente dal sistema operativo utilizzato, che sia Windows, macOS, iOS o Android;
Mobilità: deve essere possibile accedere agli strumenti lavorativi anche al di fuori della rete aziendale;
- **Service Identity**: deve essere garantito un accesso sicuro ad utenti e dispositivi alle risorse aziendali, verificando contemporaneamente “chi può accedere a cosa” in maniera puntuale e granulare;
- **Device Management**: è necessario garantire una gestione di tutto il ciclo di vita dei dispositivi: deployment e configurazione, software distribution, aggiornamenti di sicurezza e di sistema operativo; il tutto, in un approccio 100% Modern Workplace, deve poter essere gestito anche al di fuori della rete aziendale, ovunque l’utente si trovi;
- **Device Security**: sono le soluzioni di sicurezza attiva, passiva, dei dati e dell’identità che vengono implementate per proteggere gli endpoint;
- **Application Security**: riguarda metodi moderni per mettere in sicurezza le applicazioni aziendali, specialmente se esposte su Internet;
- **Data Cloud Storage**: i dati aziendali e degli utenti in un approccio Modern Workplace sono memorizzati in cloud, in uno storage remoto gestito dal fornitore e accessibile via Internet.

Ottimo! Ma cosa viene adesso? Come è possibile ottenere i risultati appena descritti? Come già accennato nel precedente articolo di questa serie, i punti nevralgici di un approccio Modern Workplace sono due:
- **l’identità dell’utente**;
- **il suo PC**.

Finalmente ora posso mostrarti quali strumenti Microsoft mette in campo per consentirti di gestire a 360° un’esperienza Modern Workplace. Te li racconto uno per uno, suddividendoli secondo gli ambiti di gestione di un dispositivo e delle identità:
- **Security**;
- **Client Deployment**;
- **Software Distribution**;
- **Update Management**;
- **Mobile Device Management**.

## Security
Come garantire la sicurezza delle identità e dei dispositivi?

### Multi Factor Authentication

![Multi Factor Authentication](/images/01-Modern-Workplace-Management-MFA.png)

La [Multi Factor Authentication](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-mfa-howitworks) è un meccanismo di autenticazione che richiede, oltre alla classica password, altri “fattori” di autenticazione per provare la tua vera identità, come ad esempio il tuo viso, le tue impronte digitali, un codice che ti arriva via SMS. La MFA messa a disposizione da Azure AD è efficace per [bloccare il 99,9% degli attacchi alle identità](https://www.microsoft.com/security/blog/2019/08/20/one-simple-action-you-can-take-to-prevent-99-9-percent-of-account-attacks/).

### Conditional access

![Conditional Access](/images/02-Modern-Workplace-Management-Conditional-Access.png)

Il [Conditional Access di Azure Active Directory](https://docs.microsoft.com/it-IT/azure/active-directory/conditional-access/) consente, attraverso alcune impostazioni, permettere o meno l’accesso alle risorse e dati aziendali solo se la tua identità e il tuo dispositivo rispettano alcuni vincoli e requisiti.

### Zero Trust Security
Più in generale, il modern management segue i principi della **Zero Trust Security**. A questo proposito, ho scritto un articolo molto approfondito dove potrai trovare tutte le informazioni del caso.

[Modello Zero Trust Security: cos’è, come funziona, perché adottarlo](/zero-trust-security/)

## Client Deployment
Come si installa il sistema operativo su un client secondo un approccio Modern Workplace?

### Intune, Autopilot, Azure AD

![Windows Autopilot](/images/03-Modern-Workplace-Management-Intune-Autopilot-Azure-AD.png)

Le installazioni dei client fatte con SCCM + Active Directory hanno giocato e continuano a giocare un ruolo fondamentale in molte aziende. Oggi però è sempre più crescente la necessità di alleggerire la dipendenza da sistemi on-premises e poter gestire l’installazione e la configurazione di un client ovunque esso sia. Come ottenere questo risultato? Con la combinazione di questi tre strumenti:
- Intune: è uno strumento cloud-based di gestione dei dispositivi, siano essi mobile o dei PC;
- [Autopilot](/windows-autopilot/): è una collezione di tecnologie utilizzate per pre-configurare i dispositivi secondo i criteri aziendali; il nuovo dispositivo viene recapitato all’utente che, alla prima accensione, effettuerà il login con le sue credenziali aziendali; immediatamente dopo il login, comincerà una procedura di configurazione del PC secondo le policy aziendali e secondo la profilazione stabilita dell’utente; il tutto senza alcun intervento dello staff IT e senza dover essere in rete aziendale;
- Azure Active Directory: è un tenant cloud e fully managed di gestione delle identità, che permette agli utenti di accedere a risorse e applicazioni.

Quali sono i vantaggi di un client deployment secondo l’approccio appena descritto?
- potrai gestire centralmente l’installazione delle postazioni di lavoro anche per gli utenti di uffici remoti dove Active Directory non è presente;
- sarai in grado di gestire i client degli utenti ad alta mobilità fornendo loro aggiornamenti e applicazioni senza dover passare dall’ufficio e senza interventi intermedi dello staff IT;
- otterrai un alto livello di standardizzazione e normalizzazione dei processi di installazione e di gestione dei client, sia che il dispositivo sia in ufficio o no;
- avrai meno sistemi da gestire nel tuo data center on-premises;
- ridurrai la dipendenza da sistemi on-premises;
- riuscirai a definire una strategia quasi “self-service” di upgrade del sistema operativo, in modo da avere una base omogenea di versioni installate con un effort amministrativo minimo.

### Microsoft Endpoint Manager

![Microsoft Endpoint Manager](/images/04-Modern-Workplace-Management-MEM.png)

Se invece hai un processo di installazione dei client che è fortemente basato su una custom image, allora la strada da seguire è quella di evolvere SCCM verso **Microsoft Endpoint Manager (MEM)**: Microsoft ha presentato questo prodtto a Novembre 2019 e consiste **in una piattaforma che integra in un’unica esperienza di gestione Configuration Manager ed Intune**. Esatto! Un unico entry point di gestione per i PC e per i dispositivi mobile.

Quali sono le implicazioni di avere un’unica esperienza di gestione per l’intero parco dei tuoi dispositivi aziendali?
- lo staff IT potrà continuare ad usare Configuration Manager come sempre ma arricchito con nuovi strumenti moderni;
- MEM è il primo passo verso l’evoluzione del processo di client deployment ad un approccio 100% Modern Workplace con Intune e Autopilot;
- MEM è lo strumento ideale per abbracciare gradualmente il paradigma “Windows-as-a-Service”.

## Software Distribution e Update Management
Come gestire la distribuzione di software e degli aggiornamenti?

### Configuration Manager e Intune Co-Management

![Configuration Manager](/images/05-Modern-Workplace-Management-CoManagement.png)

Questo è il cuore di una gestione moderna delle postazioni di lavoro! **Abilitare il [co-management](https://docs.microsoft.com/en-us/mem/configmgr/comanage/overview) di MEM ti consentirà di gestire i client Windows scegliendo tra Configuration Manager o Intune**. Sfruttando sia l’agente di SCCM sia l’enrollment di Intune, avrai i benefici di entrambe le piattaforme! Il co-management è sia una destinazione che un ponte verso una gestione moderna delle workstation. Quali sono i vantaggi chiave di adottare questa soluzione?
- una configurazione dell’OS semplice, snella e misurabile per ogni tipo di dispositivo del tuo parco macchine;
- una distribuzione più semplice delle applicazioni aziendali, sia per i dispositivi mobile sia per i PC Windows 10;
- la possibilità di poter scegliere quale sia lo strumento di gestione migliore per ogni client: Intune o Configuration Manager;
- se hai dei dispositivi legacy, sarai sempre in grado di gestirli secondo le modalità classiche offerte da Configuration Manager;
- sarai in grado di poter scegliere da dove distribuire gli aggiornamenti, localmente o direttamente via Windows Update seguendo i criteri aziendali impostati con [Windows Update for Business](https://docs.microsoft.com/en-us/windows/deployment/update/waas-manage-updates-wufb).

## Mobile Devices
E i dispositivi mobili come si gestiscono in uno scenario Modern Workplace?

### Intune

![Intune](/images/06-Modern-Workplace-Management-Intune.png)

Microsoft Intune è la soluzione MDM/MAM che può gestire i dispositivi mobili della tua azienda in tutti i loro aspetti:
- creazione di profili di configurazione che ti consentiranno di gestire i dispositivi aziendali in maniera standard, automatizzata e aderente alle policy aziendali;
- distribuzione delle app aziendali con un effort amministrativo molto basso;
- integrazione con strumenti e policy di sicurezza per un accesso sicuro e ben definito alle risorse aziendali.

Un utilizzo completo di tutte le possibilità offerte da Intune consente di raggiungere tutti i risultati di un approccio Modern Workplace:
- **Si riduce il rischio derivante dai dispositivi non gestiti che accedono alle risorse aziendali**: definire in maniera precisa un flusso di accesso alle risorse aziendali da parte dei dispositivi mobili è vitale per la sicurezza.
- **Riduzione dei costi**: definire i servizi MDM/MAM per i dispositivi BYOD ti aiuta a ridurre il numero effettivo di dispositivi che l’azienda deve acquistare, portando ad una riduzione dei costi di possesso, svecchiamento, gestione.
- **Esperienza utente e di gestione consistente**: il fatto che la gestione del dispositivo sia indipendente dal fatto che si trovi in rete aziendale o meno, rende consistente la fruibilità dello strumento da parte dell’utente e la facilità di gestione da parte dello staff IT.
- **Semplificazione delle richieste allo staff IT**: avere un parco dispositivi standard gestito da un unico entry point di gestione è indubbiamente un fattore che riduce la pressione sul reparto IT.
- **Consenti alla tua forza lavoro di sfruttare tutto il potenziale del Modern Workplace**: il grado di mobilità dei lavoratori è in costante aumento e il poter usufruire di tutti gli strumenti aziendali in maniera completa, indipendentemente che essi si trovino in rete aziendale o meno, è un fattore di crescita della produttività e della collaborazione.

## Come arrivare ad un Modern Workplace Management?

![Modern Workplace approach](/images/07-Modern-Workplace-Management-Approach.png)

Dipende dal tuo scenario di partenza. Vediamone velocemente alcuni.
- **Cloud first scenario**: se i tuoi workload esistono unicamente in cloud, sei già pronto per abbracciare al 100% il paradigma Modern Workplace;
- **Transizione “Big Switch”**: se devi gestire la transizione a Modern Workplace di una grande azienda, modernizzare tanti workload contemporaneamente non è né efficace né efficiente perché:
    - la gestione contemporanea di più progetti evolutivi è complessa, costosa, richiede un effort altissimo di orchestrazione delle risorse e delle attività;
    - è rischioso per gli utenti perché si possono introdurre disservizi multipli;
    - il rischio di conflitti tra le attività dei vari progetti è molto alto.
- **Transizione “Group by group”**: consiste nel migrare verso nuovi strumenti un tot di gruppi di utenti e risorse alla volta. Se devi gestire un insieme grande e strutturato di gruppi e di risorse, anche questa soluzione potrebbe avere dei problemi:
    - gruppi di utenti e risorse migrati potrebbero potenzialmente usare strumenti diversi rispetto a chi non è stato ancora migrato ed impattare la collaborazione tra utenti;
    - non indirizza gli obbiettivi dell’intera azienda ma solo di pochi sottoinsiemi alla volta;
    - pianificare gruppo per gruppo rallenta le attività evolutive.
- **Transizione in Co-Management: questa è la soluzione, vediamo perché...**

> *Il Co-Management è sia una destinazione che un ponte verso il Modern Workplace*

- **il Co-Management è un ponte perché parte da ciò che hai già facendo leva sugli investimenti che hai già sostenuto in infrastrutture IT;**
- **il Co-Management è una destinazione perchè aggiunge le funzionalità Modern Workplace ai tuoi strumenti di gestione dei dispositivi e delle identità.**

![The Bridge Destination approach of Modern Endpoint Management](/images/08-Modern-Workplace-Management-Bridge-Destination.png)

## Conclusioni sul Modern Workplace Management
Grazie per avermi seguito fino a qui. È uno degli articoli più tosti e difficili a cui io abbia mai lavorato, un po’ per la difficoltà degli argomenti in sé e un po’ per la complessità di condensarli sotto forma di articolo. Spero di esserci riuscito e spero di averti acceso quella scintilla che guida tutti noi, specialisti IT, alla ricerca di come evolvere, migliorare e semplificare la vita delle persone, siano essi gli utilizzatori finali di queste tecnologie o i gestori di tutto quello che ci sta dietro. Mi piacerebbe sapere la tua esperienza a questo riguardo, ti aspetto nei commenti o sui miei profili social. A presto!

Il tuo IT Specialist, Riccardo