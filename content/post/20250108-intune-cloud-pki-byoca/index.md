---
date: 2025-01-08T05:00:00-00:00
description: "Scopri come configurare Intune Cloud PKI in modalità BYOCA. Guida passo-passo per semplificare la gestione dei certificati per dispositivi Intune, senza server locali. Video didattico con documentazione aggiornata."
image: "01-cloud-endpoint-diary-intune-cloud-pki-byoca.jpg"
categories : [ "Security", "Modern Work" ]
tags: [ "Microsoft Intune", "Intune", "Cloud PKI", "Security", "BYOCA", "Video", "Guida" ]
title: "Intune Cloud PKI (Bring Your Own Certification Authority)"
url: /intune-cloud-pki-byoca-cloud-endpoint-diary
---
Specialisti IT! Come promesso, video VELOCISSIMO su Intune Cloud PKI in modalità di implementazione Bring Your Own Certification Authority.

## Video
Trovate l’intero video qui sotto, altrimenti potete continuare a leggere l’articolo.

{{< youtube xKfFpOhDJvs >}}

## Intune Cloud PKI (Bring Your Own Cetification Authority)

### Cos'è e come funziona Intune Cloud PKI
Riassunto rapido su cos’è Microsoft Cloud PKI: è un servizio basato su cloud che semplifica e automatizza la gestione del ciclo di vita dei certificati per i dispositivi gestiti da Intune.

Come fa a fare tutto questo? Grazie ad un'infrastruttura a chiave pubblica (PKI) dedicata sotto forma di servizio SaaS, senza server, connettori o hardware locali.  
La Certification Authority può essere totalmente cloud creata su Intune oppure, se avete una vostra CA privata on-premises (Microsoft integrata con AD oppure anche non Microsoft), questa può essere agganciata con Cloud PKI.  
Come si fa? Si crea la CA issuing (di emissione) in cloud e, con un’opportuna procedura, il certificato ROOT della vostra CA on-prem viene agganciato a Cloud PKI.
È proprio quello che vedremo oggi!

### Creazione Issuing CA su Intune Cloud PKI
Iniziamo subito: creiamo la Issuing CA su Intune

{{< youtubestartend xKfFpOhDJvs  64 116 >}}

## Esportazione certificato Root CA on-premises
Sulla CA on prem, intanto, esportiamo la trust chain completa che comprende il certificato di root della CA.

Ecco il comando per esportare tutta la trust chain.

   ```
    certutil -ca.chain C:\temp\fullchain.p7b
   ```

{{< youtubestartend xKfFpOhDJvs  123 135 >}}

## Download CSR da Intune Issuing CA
Torniamo su Intune, scarichiamo la CSR da dare in pasto alla CA on-prem per generare il certificato della Issuing

{{< youtubestartend xKfFpOhDJvs  143 147 >}}

## Firma CSR e generazione certificato della Issuing CA
Firmiamo la richiesta e generiamo il certificato della CA Issuing.

Ecco il comando per generare il certificato.

   ```
    certreq -submit -attrib "CertificateTemplate:<template_name>" -config "<CA_server_name>\<CA_name>" <request_file> <response_file>  
   ```  

**Questa è una sintassi di esempio: sostituite le voci in parentesi con i vostri parametri!**

{{< youtubestartend xKfFpOhDJvs  152 169 >}}

## Upload dei certificati su Intune e creazione finale della Issuing CA
Perfetto, ora carichiamo in cloud la trust chain e il certificato generato

{{< youtubestartend xKfFpOhDJvs  165 187 >}}

## Considerazioni finali
Abbiamo creato la nostra CLOUD PKI!

Guardate la durata di questo video e ditemi se non è pazzesco riuscire a mettere in piedi una CA cloud, integrata con la vostra CA on-prem, nel tempo di questo video.

**Domanda**: come si fa a innescare questa CA, per fare in modo che rilasci certificati? Con i profili di configurazione SCEP ma questo è un altro video.

{{< rawhtml >}}
  <div class="disclaimer-box" style="background-color:rgb(252, 229, 183); border: 1px solid rgb(252, 229, 183); padding: 15px; margin: 20px 0; border-radius: 5px; color: #333; font-weight: bold;">
    <p>⚠️ **DISCLAIMER**: come sempre, questo è un video fatto a fini didattici. Essendo in un laboratorio, ho dovuto fare delle assunzioni sulle configurazioni delle policy, dei certificati, eccetera eccetera.</p>
  </div>
{{< / rawhtml >}}


In produzione fate le opportune analisi, prima di buttarvi a capofitto nell’integrazione della vostra CA con Intune Cloud PKI!
Per approfondire l’argomento vi lascio qui sotto la solita documentazione che profuma ancora di capodanno 2024-2025.

**Documentazione: trovate la documentazione aggiornata nei link qui sotto.**

📃 [Overview of Microsoft Cloud PKI for Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-cloud-pki-overview)  
📃 [Microsoft Cloud PKI fundamentals](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-cloud-pki-fundamentals)  
📃 [Configure Microsoft Cloud PKI - Bring your own CA](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-cloud-pki-configure-byoca)  
📃 [How to export Root Certification Authority Certificate](https://learn.microsoft.com/en-us/troubleshoot/windows-server/certificates-and-public-key-infrastructure-pki/export-root-certification-authority-certificate)

Fatemi sapere se vi piacciono questi video più veloci e leggeri, scrivetemelo qui nei commenti.

Come sempre, seguitemi sui miei profili social e, se vi va, iscrivetevi al mio canale: per me è molto importante!

A presto... MITICI!
