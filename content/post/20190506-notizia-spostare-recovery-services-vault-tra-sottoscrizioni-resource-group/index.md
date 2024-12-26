---
date: 2019-05-06T08:00:00-00:00
description: "Novità su Azure Backup: da oggi puoi spostare Recovery Services Vault tra una sottoscrizione e l'altra e tra un resource group e l'altro."
image: "01-spostare-recovery-services-vault.png"
categories: [ "Cloud Datacenter" ]
tags: [ "Azure", "Azure Backup", "Recovery Services Vault", "News"]
title: "Notizia: è ora possibile spostare Recovery Services Vault tra sottoscrizioni o resource group"
url: "/notizia-spostare-recovery-services-vault-tra-sottoscrizioni-resource-group"
---
Notizia fresca fresca di qualche giorno fa (25 Aprile 2019): da oggi è in general availability la possibilità di spostare Recovery Services Vault tra una sottoscrizione e l’altra e anche tra un resource group e l’altro.

## Cos’è un Recovery Services Vault
![Icona Azure Recovery Services Vault](01-spostare-recovery-services-vault.png)

Brevissima introduzione giusto per rinfrescare la memoria: un Recovery Services Vault è una risorsa di Azure Resource Manager afferente all’ambito Azure Backup e al suo interno contiene le funzionalità e gli strumenti per gestire tutte le necessità di backup e disaster recovery.

Esempi? Backup di VM, backup di dati all’interno di VM o di macchine fisiche anche al di fuori di Azure nel caso di salvataggio fatto tramite agente ASR, eccetera.

## Cosa è possibile fare ora
È possibile finalmente spostare un recovery services vault tra sottoscrizioni o tra resource group, cosa che prima non era possibile.

Questo rende molto più flessibile eventuali riorganizzazioni dei propri ambienti cloud come, ad esempio, nei casi di un cambio di dipartimento, spostamenti di vault da una sottoscrizione di test ad una di produzione, spostamenti di oggetti da una vecchia sottoscrizione ad una nuova, riorganizzazione dei resource group, e via dicendo.

La cosa molto interessante è che nel processo di migrazione tutti i backup, le policy, i punti di ripristino, le impostazioni sono mantenuti.
Non è ancora possibile spostare Recovery Services Vault che vengono utilizzati per Azure Site Recovery (ASR).

Per approfondimenti:
- [Announcing Azure Backup Support to move Recovery Services Vaults](https://azure.microsoft.com/en-us/blog/announcing-azure-backup-support-to-move-recovery-services-vaults/)

{{< rawhtml >}}
  <p class="tc">
    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">Now you can migrate a vault between subscriptions and resource groups with just a few steps. Read more about the new <a href="https://twitter.com/hashtag/Azure?src=hash&amp;ref_src=twsrc%5Etfw">#Azure</a> Backup feature: <a href="https://t.co/5bwAh009NW">https://t.co/5bwAh009NW</a></p>&mdash; Microsoft Azure (@Azure) <a href="https://twitter.com/Azure/status/1121813689005486080?ref_src=twsrc%5Etfw">April 26, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
  </p>
{{< / rawhtml >}}

Una bella e utilissima novità! Sto già preparando un tutorial per raccontarti come si fa fisicamente ma soprattutto per approfondire i prerequisiti e le eventuali limitazioni.
Continua a seguirmi per scoprirlo 😉

A presto!

Riccardo