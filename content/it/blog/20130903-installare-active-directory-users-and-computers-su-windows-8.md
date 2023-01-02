---
date: 2013-09-03T08:00:00-00:00
description: "Come installare Active Directory Users And Computers su Windows 8 con tutti gli altri snap-in di amministrazione."
featured_image: "/images/RSAT-Slider.png"
categories: [ "Archivio" ]
tags: [ "Active Directory", "RSAT", "Guida" ]
title: "Installare Active Directory Users And Computers su Windows 8"
url: "/installare-active-directory-users-and-computers-su-windows-8"
---
Per chi lavora tutti i giorni con Active Directory è una buona pratica avere installato sul proprio PC un tool indispensabile come Active Directory Users And Computers. Fino a qualche anno fa, con Windows 2003, bastava scaricare l’ormai mitico adminpak.msi ma oggi, con Windows 7 e Windows 8 le cose sono un pochino cambiate. Vediamo quindi come installare Active Directory Users And Computers (e non solo) su Windows 8.

Una piccola premessa prima di continuare: con questo pacchetto non installeremo solo l’ADUC bensì una serie completa di tool amministrativi chiamati R**emote Server Administration Tools**, attraverso i quali potremo amministrare remotamente ruoli di Windows Server 2008, Windows Server 2008 R2 e alcuni ruoli di Windows Server 2003. Il sistema operativo supportato è Windows 8 solo su architetture x86 e x64 mentre sono escluse le piattaforme basate su ARM.

Prima di tutto scarichiamo il pacchetto presente all’indirizzo:

http://www.microsoft.com/en-us/download/details.aspx?id=28972

Clicchiamo su Download a scegliamo la versione (32bit o 64bit).  
Una volta scaricato il file eseguiamolo, confermando di voler procedere

[![RSAT Install confirmation](/images/1-RSAT-Install-confirmation.png)](/images/1-RSAT-Install-confirmation.png)

Accettiamo i termini di licenza

[![RSAT License](/images/2-RSAT-License.png)](/images/2-RSAT-License.png)

A questo punto non ci resta altro che attendere…

[![RSAT installation waiting](/images/3-RSAT-installation-waiting.png)](/images/3-RSAT-installation-waiting.png)

... e riavviare il computer al termine dell’installazione

[![RSAT Restart PC](/images/4-RSAT-Restart-PC.png)](/images/4-RSAT-Restart-PC.png)

Una volta che il PC sarà riavviato, nella schermata Start di Windows 8 comparirà la seguente icona

[![Icona Administrative Tools](/images/5-RSAT-Icona-Start.png)](/images/5-RSAT-Icona-Start.png) 

Clicchiamoci sopra per eseguirla. Comparirà una semplice finestra dove troverete l’elenco **completo** dei tool amministrativi tipici di un ambiente Windows. Ci sarà quindi il nostro Active Directory Users And Computers ma anche gli snap-in di **DNS**, **DHCP**, **DFS**, **ODBC**, e chi più ne ha più ne metta, il tutto finalmente a portata del nostro PC, senza vagare in Remote Desktop tra un server e l’altro! Ecco l’elenco completo dei tool di cui potrete usufruire installando i Remote Server Administration Tools.

[![RSAT Administrative Tools List](/images/6-RSAT-Administrative-Tools-List.png)](/images/6-RSAT-Administrative-Tools-List.png) 