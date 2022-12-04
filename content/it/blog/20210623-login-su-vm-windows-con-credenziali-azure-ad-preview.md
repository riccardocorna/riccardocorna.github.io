---
date: 2021-06-23T08:00:00-00:00
description: "Finalmente, in anteprima, la possibilità di fare login su VM Windows con credenziali Azure AD. Analizziamone caratteristiche e benefici."
featured_image: "/images/azure-portal-login-with-azure-ad.png"
categories: [ "Identity & Security", "Cloud Datacenter" ]
tags: [ "Azure AD", "Virtual Machine", "Azure", "News"]
title: "Login su VM Windows con credenziali Azure AD (preview)"
url: "/login-su-vm-windows-con-credenziali-azure-ad-preview"
---
Finalmente, anche se solo in preview, è disponibile una funzione che **TUTTI** stavano aspettando: la possibilità di autenticarsi ad una macchina virtuale ospitata su Azure attraverso le credenziali Azure AD. Vediamo insieme le caratteristiche principali e quali sono gli enormi benefici che comporta poter fare login su VM Windows con credenziali Azure AD:
- riduzione dell’utilizzo di utenze locali;
- possibilità di usare le proprie credenziali aziendali per accedere alle VM in cloud;
- l'accesso alle VM verrà regolato tramite ruoli RBAC specifici;
- possibilità di regolare l’accesso alle VM tramite l’accesso condizionale (questa possibilità, in particolare, mi piace TANTISSIMO);
- le VM potranno sfruttare l’auto-enrollment su MEM (Intune – richiede almeno Azure AD Premium P1).
- integrazione con le password policy stabilite in cloud;

Queste sono le cose che mi sono piaciute di più ma, per ulteriori approfondimenti, ti rimando all’articolo ufficiale:
- [Sign in to Windows virtual machine in Azure using Azure Active Directory | Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows)

Dopo aver capito perché è una notizia importantissima, vediamo alcuni requisiti e come impostare questa funzione.

## Requisiti
La funzionalità di login tramite credenziali Azure AD è disponibile per:
- Windows Server 2019 Datacenter;
- Windows 10 1809 e successive;
- per i requisiti di rete dettagliati ti rimando al seguente articolo: [Sign in to Windows Virtual Machine with Azure AD – Network requirements](https://docs.microsoft.com/en-us/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows#network-requirements).

## Come abilitare il login tramite credenziali Azure AD
Molto semplice: al momento della creazione di una VM, nella blade “Management”, abilita l’opzione con la spunta.

[![Blade Azure VM Login with Azure AD credentials](/images/azure-portal-login-with-azure-ad.png)](/images/azure-portal-login-with-azure-ad.png)

## Come abilitare gli utenti a collegarsi con le loro credenziali Azure AD
Come dicevo ad inizio articolo, è sufficiente abilitare utenti o gruppi agli specifici ruoli Azure RBAC. Ne sono stati creati 2 nuovi ad-hoc:
- **Virtual Machine Administrator Login**: gli utenti con questo ruolo potranno collegarsi alle VM in Azure con privilegi amministrativi;
- **Virtual Machine User Login**: gli utenti con questo ruolo potranno collegarsi alle VM in Azure con privilegi standard.

## Conclusioni e ragionamenti su Azure Virtual Desktop
Questo è un enorme passo avanti ed era una funzionalità che aspettavo da tanto tempo. Leggendo fuori dalle righe, io ci vedo una sorta di milestone intermedia per raggiungere lo stesso risultato anche su Azure Virtual Desktop. Infatti, al momento, il login con credenziali Azure AD è disponibile solo su VM al di fuori di un host pool AVD ma, spero, presto avremo un Azure Virtual Desktop senza più l’obbligo di un’Active Directory.

E tu che ne pensi? Hai già fatto qualche test di login su VM Windows con credenziali Azure AD? Ti aspetto nei commenti per parlarne insieme!

Il tuo IT Specialist, Riccardo
