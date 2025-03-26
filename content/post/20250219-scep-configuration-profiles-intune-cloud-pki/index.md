---
date: 2025-02-19T05:00:00-00:00
description: "Scopri come utilizzare una Cloud PKI con Microsoft Intune per richiedere certificati con i profili di configurazione SCEP. Tutorial completo su creazione e distribuzione certificati digitali."
image: "01-scep-configuration-profiles-intune-cloud-pki.jpg"
categories : [ "Modern Work", "Security" ]
tags: [ "Microsoft Intune", "Cloud PKI", "SCEP", "Configuration Profiles", "Video", "Guida", "Cloud Endpoint Diary" ]
title: "Profili di configurazione SCEP per Intune Cloud PKI"
url: /scep-configuration-profiles-intune-cloud-pki
---
Specialisti IT, ciao a tutti! Vi ricordate che qualche tempo fa abbiamo visto [come mettere in piedi una Cloud PKI con Microsoft Intune](/intune-cloud-pki-byoca-cloud-endpoint-diary)? Bene, è arrivato il momento di usarla richiedendo certificati con i profili di configurazione SCEP!

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube zej8tN6fD3w >}}

## Profili di configurazione SCEP per Intune Cloud PKI
Utilizziamo Cloud PKI con Microsoft Intune per richiedere certificati con i profili di configurazione SCEP.

### Cos'è SCEP?
SCEP, acronimo di Simple Certificate Enrollment Protocol, è un protocollo utilizzato per semplificare la gestione e la distribuzione dei certificati digitali. In ambito Intune Cloud PKI, SCEP viene utilizzato per distribuire certificati ai nostri dispositivi gestiti, che saranno poi utilizzati per autenticarsi a risorse aziendali.

### Creazione dei Profili di Intune
Iniziamo creando i profili di Intune per distribuire i certificati, partendo dai Trusted Certificates, quindi la Root CA e la Issuing CA, che abbiamo creato poco tempo fa con Intune Cloud PKI. Se non ve lo ricordate, andate a recuperare il video precedente.

{{< youtubestartend zej8tN6fD3w 57 121 >}}

### Configurazione del Profilo SCEP
Ora è il momento di creare finalmente il nostro profilo SCEP, che configureremo in modo da stuzzicare la nostra Cloud PKI. Fate attenzione in particolare al parametro SCEP URL. Vediamo prima la configurazione di un certificato utente e poi la configurazione del profilo SCEP per richiedere un certificato macchina.

#### Profilo SCEP per certificato utente
{{< youtubestartend zej8tN6fD3w 136 180 >}}

#### Profilo SCEP per certificato macchina
{{< youtubestartend zej8tN6fD3w 185 226 >}}

### Verifica emissione certificati
Perfetto, ora verifichiamo che i certificati siano effettivamente stati emessi.

{{< youtubestartend zej8tN6fD3w 237 261 >}}

### Consigli Utili
- Mantenete coerenza tra le assegnazioni dei profili Trusted Certificate e profili SCEP, assegnandoli allo stesso gruppo e, soprattutto, siate coerenti sulla tipologia di oggetto che popola il gruppo: o utenti o dispositivi. Questo perché c'è una precisa tabella di supportabilità per fare in modo che i certificati vengano effettivamente emessi. Vi riporto la tabella qui di seguito.

| Trusted certificate profile assignment includes User | Trusted certificate profile assignment includes Device | Trusted certificate profile assignment includes User and Device |
|------------------------------------------------------|-------------------------------------------------------|---------------------------------------------------------------|
| **SCEP certificate profile assignment includes User** | Success                                               | Failure                                                       | Success                                                       |
| **SCEP certificate profile assignment includes Device** | Failure                                               | Success                                                       | Success                                                       |
| **SCEP certificate profile assignment includes User and Device** | Success                                               | Success                                                       | Success                                                       |


Altri consigli utili:
- Se avete un ambiente ibrido, rispettate i requisiti di strong mapping (dettagli nella documentazione allegata qui sotto).

## Documentazione
Ecco tutta la documentazione a cui ho fatto riferimento durante il video.

📃 [Use SCEP certificate profiles with Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/protect/certificates-profile-scep)  
📃 [Troubleshoot deployment of Simple Certificate Enrollment Protocol (SCEP) certificate profiles to devices with Microsoft Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/certificates/troubleshoot-scep-certificate-profile-deployment)  
📃 [Troubleshoot use of Simple Certificate Enrollment Protocol (SCEP) certificate profiles to provision certificates with Microsoft Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/certificates/troubleshoot-scep-certificate-profiles)  
📃 [Troubleshoot delivery of Simple Certificate Enrollment Protocol (SCEP) certificates](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/certificates/troubleshoot-scep-certificate-delivery)  
📃 [Support tip: Implementing strong mapping in Microsoft Intune certificates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-implementing-strong-mapping-in-microsoft-intune-certificates/4053376)

## Conclusione
**Come sempre, questo è un ambiente di laboratorio, quindi fate le opportune analisi prima di mettere tutto in produzione.**  
Grazie per aver visto il video fino a qui. Iscrivetevi al mio canale YouTube e aiutatemi a farlo crescere per produrre contenuti sempre migliori. Per il resto, vi aspetto su LinkedIn e sul mio blog ITSpecialist.cloud!

Grazie ancora! A presto... MITICI!

Il vostro IT Specialist,  
Riccardo