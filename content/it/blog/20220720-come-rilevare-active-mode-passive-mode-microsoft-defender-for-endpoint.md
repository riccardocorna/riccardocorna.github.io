---
date: 2022-07-20T09:00:00-00:00
description: "Come sapere se un endpoint protetto da Microsoft Defender for Endpoint è in Active o Passive mode con una comoda query KQL."
featured_image: "/images/01-MDE-Hunting-Query-Active-Passive-Mode-1.jpg"
categories: [ "Identity & Security" ]
tags: [ "Microsoft Defender for Endpoint" ]
title: "Come sapere se Microsoft Defender for Endpoint è in Active o Passive mode su un endpoint"
url: "/come-rilevare-active-mode-passive-mode-microsoft-defender-for-endpoint"
---
In alcuni frangenti capita di fare onboarding di dispositivi su Microsoft Defender for Endpoint quando ancora il vecchio “antivirus” di terze parti è installato e attivo. Cosa succede in questi casi? I due software di protezione fanno a pugni? La risposta è: “No”. Oggi ti racconto cosa sia il passive mode e come sapere quanti/quali endpoint stanno usando MDE come software di protezione primario (Active mode) oppure no (Passive mode).

## Active mode e Passive mode di Microsoft Defender for Endpoint
Come dicevo poco fa, nel caso in cui sull’endpoint sia attivo un altro antivirus, MDE è in grado autonomamente (su Windows) di capirlo e di mettersi in una sorta di “stand-by”. Non appena il software di protezione di terze parti viene disinstallato, MDE ne diventa subito consapevole e attiva tutte le sue funzioni (Active mode), diventando l’antivirus primario sulla macchina.

Ecco alcuni dettagli su queste modalità:
- [Comparing active mode, passive mode, and disabled mode | Microsoft Docs](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows?view=o365-worldwide#comparing-active-mode-passive-mode-and-disabled-mode)

## Perché è utile sapere la modalità di esecuzione?
In distribuzioni massive di MDE dove si va a sostituire un altro prodotto di protezione, potrebbe capitare di trovarsi in una fase di “interregno” per un po’ di tempo e, quindi, è utile sapere quanti client siano in Active mode e quanti siano in Passive mode, giusto per avere un monitoraggio dello stato di avanzamento della distribuzione e dell’adozione di Defender for Endpoint.

## Le cose semplici? MAI!
Purtroppo, una volta fatto l’onboarding dei dispositivi Windows in MDE, non esiste una vista o un workbook centralizzato/preconfezionato per avere questa informazione. I metodi documentati sono questi:

- direttamente sull’endpoint di cui vuoi verificare lo stato, lanciare il pannello:
    **Security** –> **Virus & Threat protection** –> **Who’s protecting me?**
- usare PowerShell, sempre sull’endpoint finale con il cmdlet **Get-MpComputerStatus**

Se vuoi ulteriori dettagli, ecco qui una lettura notturna davvero rilassante:
- [Check the state of Microsoft Defender Antivirus on your device | Microsoft Docs](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows?view=o365-worldwide#check-the-state-of-microsoft-defender-antivirus-on-your-device)

Come hai potuto notare, tutti questi metodi prevedono che tu esegua delle operazioni fisicamente e in maniera interattiva sull’endpoint, a meno di scriptare qualche accrocchio che, da remoto, vada ad interrogare tutti gli endpoint, ammesso che siano in visibilità di rete. Decisamente poco pratico ed efficace.

## La via oscura e seducente di MDE: le query KQL di hunting
Cercando qua e là, ho trovato una query che è davvero utilissima e consente, dalla console di Hunting di Microsoft Defender for Endpoint, di creare una tabella con i seguenti dati:

- Device ID
- Nome del dispositivo
- Versione delle firme
- Versione del motore di MDE
- **Modalità di esecuzione**
- altre amenità…

Da portale Microsoft Defender, quindi, clicca sul menu di sinistra alla sezione **Hunting** –> **Advanced Hunting** e incolla questa magica query che andrebbe conservata e portata in salvo come l’antico vaso dell’Amaro Montenegro.

```
let avmodetable = DeviceTvmSecureConfigurationAssessment
| where ConfigurationId == "scid-2010" and isnotnull(Context)
| extend avdata=parsejson(Context)
| extend AVMode = iif(tostring(avdata[0][0]) == '0', 'Active' , iif(tostring(avdata[0][0]) == '1', 'Passive' ,iif(tostring(avdata[0][0]) == '4', 'EDR Blocked', 'Unknown')))
| project DeviceId, AVMode;
DeviceTvmSecureConfigurationAssessment
| where ConfigurationId == "scid-2011" and isnotnull(Context)
| extend avdata=parsejson(Context)
| extend AVSigVersion = tostring(avdata[0][0])
| extend AVEngineVersion = tostring(avdata[0][1])
| extend AVSigLastUpdateTime = tostring(avdata[0][2])
| project DeviceId, DeviceName, OSPlatform, AVSigVersion, AVEngineVersion, AVSigLastUpdateTime, IsCompliant, IsApplicable
| join avmodetable on DeviceId
| project-away DeviceId1
```

Ecco un esempio del risultato:

![Defender for Endpoint advanced hunting con query KQL](/images/01-MDE-Hunting-Query-Active-Passive-Mode.jpg)

Visto? Pur non essendo in tempo reale e pur non avendo la comodità di un workbook o di una dashboard, è di gran lunga il modo migliore per sapere quali e quanti endpoint sono in Active o Passive mode, senza scomodare l’utente con sessioni di assistenza remota per eseguire script Powershell o altro. Puoi anche salvarla per successive esecuzioni oppure esportarne i risultati in un comodo file CSV.

Questa query non è farina del mio sacco e quindi, se vuoi approfondire tutti i dettagli dei risultati e dei dati che fornisce, ecco i riferimenti degli articoli originali:
- [Defender AV – Active/Passive Mode – Advanced Hunting – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/defender-av-active-passive-mode-advanced-hunting/m-p/2585781)
- [Windows Defender Antivirus (Active or Passive) : DefenderATP (reddit.com)](https://www.reddit.com/r/DefenderATP/comments/lfd5zy/comment/gmynulv/?utm_source=share&utm_medium=web2x&context=3)

E tu ti sei mai trovato nella situazione di dover avere questa informazione sulla modalità di esecuzione di Defender for Endpoint? Oppure conosci modi ancora più semplici e veloci di ottenerla? Parliamone insieme sui miei profili social ti aspetto!

Il tuo IT Specialist, Riccardo