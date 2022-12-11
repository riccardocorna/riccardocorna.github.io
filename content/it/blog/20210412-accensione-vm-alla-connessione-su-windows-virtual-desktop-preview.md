---
date: 2021-04-12T08:00:00-00:00
description: "Una funzionalità di Windows Virtual Desktop attesa da molti è finalmente disponibile: l'accensione VM alla connessione!"
featured_image: "/images/01-accensione-vm-alla-connessione-windows-virtual-desktop.jpeg"
categories: [ "Cloud Datacenter"]
tags: [ "Azure", "Azure Virtual Desktop", "News"]
title: "Accensione VM alla connessione su Windows Virtual Desktop (preview)"
url: "/accensione-vm-alla-connessione-su-windows-virtual-desktop-preview"
---
Una funzionalità di Windows Virtual Desktop attesa da molti è finalmente disponibile (in public preview al momento in cui scrivo): l’accensione VM alla connessione!

[![Azure Virtual Desktop ccensione VM alla connessione](/images/01-accensione-vm-alla-connessione-windows-virtual-desktop.jpeg)](/images/01-accensione-vm-alla-connessione-windows-virtual-desktop.jpeg)

La funzionalità di accensione VM alla connessione permette di accendere automaticamente una VM di un host pool di Windows Virtual Desktop, nel momento in cui un utente tenta di connettervisi.

Perché è una grande novità?
- perché permette di “risvegliare” macchine stoppate e deallocate senza dover andare ad accenderle preventivamente sul portale;
- perché, unendo questa novità ad un’opportuna pianificazione automatica di spegnimento, aiuta a risparmiare sui costi;
- perché, in questo modo, le macchine saranno sempre disponibili per i tuoi utenti, che siano accese o spente.

Al momento ci sono alcune limitazioni, data la condizione di preview. Per ogni altro dettaglio, se vuoi approfondire, ecco alcune risorse utili:
- [Public preview: Start VM on connect feature for Windows Virtual Desktop | Azure updates | Microsoft Azure](https://azure.microsoft.com/en-us/updates/public-preview-start-vm-on-connect-feature-for-windows-virtual-desktop/)
- [Start virtual machine connect – Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-desktop/start-virtual-machine-connect)
- [Windows Virtual Desktop Start VM Connect FAQ – Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-desktop/start-virtual-machine-connect-faq)

Personalmente aspettavo davvero tanto questa funzione perché alleggerisce di molto il carico di gestione sull’IT e semplifica decisamente l’implementazione di automatismi di spegnimento/accensione. E tu, quali altri accorgimenti usi per ottimizzare le spese di Windows Virtual Desktop? Parliamone nei commenti o sui miei social. A presto!

Il tuo IT Specialist, Riccardo