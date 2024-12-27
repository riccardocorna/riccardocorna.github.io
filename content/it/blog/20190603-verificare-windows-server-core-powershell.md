---
date: 2019-06-03T08:00:00-00:00
description: "Come verificare se sul tuo server è in esecuzione Windows Server Core con PowerShell, grazie a due semplici comandi e una chiave di registro."
featured_image: "/images/01-Verificare-Windows-Server-Core-Powershell.png"
categories: [ "Altro" ]
tags: [ "Windows Server", "PowerShell" ]
title: "Verificare se un server è Windows Server Core con Powershell"
url: "/verificare-windows-server-core-powershell"
---
Per un progetto al quale sto lavorando di recente, mi è capitato di dover verificare al volo se l’installazione di Windows di una macchina remota fosse di tipo Windows Server Core. Ottenere questa informazione in una sessione remota con PowerShell è estremamente semplice: vediamo come si fa!

## Breve panoramica su Windows Server Core
[Windows Server Core](https://docs.microsoft.com/en-us/windows-server/administration/server-core/what-is-server-core) è un’opzione di installazione di Windows Server Standard edition o Datacenter edition senza l’interfaccia grafica tipica di Windows Server. Questa versione permette di installare una buona parte dei ruoli di Windows, consente di risparmiare spazio disco, risorse computazionali e, grazie al fatto che l’interfaccia grafica è assente, riduce di molto la superficie d’attacco del codice.

Quest’opzione di installazione è ideale in ambienti dove si vogliono implementare policy di sicurezza più stringenti e se si vuole ridurre l’effort amministrativo di gestione delle macchine.

## Come verificare il tipo di installazione di Windows con PowerShell
Per verificare con che tipo di installazione si ha a che fare, c’è una precisa chiave di registro da andare ad interrogare:

    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion

In particolare puoi verificare quale dicitura assume il valore

    InstallationType

che, su un’installazione Server Core è uguale a “**Server Core**“.

Perfetto! Collega una sessione remota di PowerShell e segui questi due semplici passaggi.

Imposta una variable con il percorso della chiave di registro che contiene l’informazione del tipo di installazione

    $regKey = "hklm:/software/microsoft/windows nt/currentversion"

Dopo di che, potrai passare all’interrogazione vera e propria, dove verificherai che il valore InstallationType sia “Server Core”

    $SrvCore = (Get-ItemProperty $regKey).InstallationType -eq "Server Core"

Questo comando restituirà un valore Booleano *True* o *False* e, a mio modo di vedere, è un controllo molto comodo che si può inserire in un eventuale script per verificare una batteria di server in maniera pressoché immediata.

[![Sessione remota di PowerShell](/images/01-Verificare-Windows-Server-Core-Powershell.png)](/images/01-Verificare-Windows-Server-Core-Powershell.png)

Se ti vengono in mente altre maniere di verificare che tipo di installazione di Windows hai davanti, ti aspetto nei commenti per parlarne.
A presto!

Riccardo