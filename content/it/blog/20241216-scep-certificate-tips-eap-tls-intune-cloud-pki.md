---
date: 2024-12-16T05:00:00-00:00
description: "Autenticate dispositivi via certificato (EAP-TLS) con Intune Cloud PKI e profili SCEP su server NPS Windows, configurate il SAN con l'UPN del computer account per evitare problemi e scoprite di più sui requisiti dei certificati e le best practice su Intune."
featured_image: "/images/01-scep-san-add.png"
images:
  - "/images/01-scep-san-add.png"
categories : [ "Identity & Security" ]
tags: [ "Intune", "SCEP","Certificato", "Dispositivo", "Autenticazione", "SAN", "NPS" ]
title: "Quick tip sul profilo SCEP per autenticazione dispositivo EAP-TLS"
url: /scep-certificate-tips-eap-tls-intune-cloud-pki
---
🚨Quick tip del lunedì che vi salverà ore di troubleshooting. Grazie a [Yuri Gasparini](https://www.linkedin.com/in/yurigasparini/) per la chicca. 🙏🏻

## 💻 Scenario
Volete autenticare un dispositivo via certificato (EAP-TLS), usando Intune Cloud PKI, profili SCEP via Intune e il server è un NPS Windows Server. I client sono joinati a dominio, Hybrid Entra Joined e gestiti da Intune.

## 🔨 Configurazione
Il certificato SCEP, in questo caso, ha dei requisiti ben precisi soprattutto sul Subject Alternative Name (SAN). Li trovate qui:

📃 [Certificate requirements when you use EAP-TLS or PEAP with EAP-TLS](https://learn.microsoft.com/en-us/troubleshoot/windows-server/networking/certificate-requirements-eap-tls-peap#client-certificate-requirements)

## ⚠️ Attenzione: ecco la chicca
Ma la vera chicca è questa. Al di là dei soliti parametri da configurare su Intune nel profilo SCEP, è fondamentale, in questo scenario, popolare correttamente il SAN con l'UPN del computer account. Peccato non esista una variabile dedicata e pronta all'uso. Come fare?
Usando una combinazione mista di variabili e testo statico, così:

1️⃣ **User Principal Name (UPN)** ➡️ **{{DeviceName}}@nomedominio.local**

E non dimenticate lo strong mapping!

2️⃣ **URI** ➡️ **{{OnPremisesSecurityIdentifier}}**

Per ulteriori approfondimenti sui profili SCEP:  
📃 [Create and assign SCEP certificate profiles in Intune](https://learn.microsoft.com/en-us/mem/intune/protect/certificates-profile-scep)  
📃 [KB5014754: Certificate-based authentication changes on Windows domain controllers](https://support.microsoft.com/en-us/topic/kb5014754-certificate-based-authentication-changes-on-windows-domain-controllers-ad2c23b0-15d8-4340-a468-4d4f3b188f16)

Il vostro IT Specialist,  
Riccardo