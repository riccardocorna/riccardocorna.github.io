---
date: 2021-03-27T08:00:00-00:00
description: "I Mac in azienda con Microsoft 365: come vanno? Funziona? Ti racconto la mia esperienza personale con un MacBook Air, M365 ed Intune."
featured_image: "/images/01-Mac-Azienda.png"
categories: [ "Altro"]
tags: [ "macOS", "Microsoft 365", "Intune"]
title: "Opinione: Mac in azienda con Microsoft 365"
url: "/mac-in-azienda-opinione-macos-microsoft365"
---
Mac in azienda con Microsoft 365: come va? Funziona? Chi mi segue da un po’ di tempo sa che, sotto sotto, il mio cuore è a forma di Mela. L’uscita dei nuovi Mac basati su M1 e i grandi progressi fatti ultimamente nel funzionamento dei software Microsoft su macOS, mi hanno incuriosito e, dopo 2 anni di “pausa di riflessione”, a casa è tornato un Mac: più precisamente un MacBook Air M1. Mi piace tanto, mi diverte, funziona bene, ha un prezzo giusto ed è veramente una bomba di prestazioni e autonomia. Ti racconto la mia esperienza dopo alcuni mesi di utilizzo continuo, in ambito personale e lavorativo.

![Schermata di macOS con login su Azure AD](/images/01-Mac-Azienda.png)

***Avvertenza!*** *In questo articolo non parlerò di come va il MacBook Air M1 in sé: per analizzarne prestazioni e scheda tecnica ci sono tantissime testate online e YouTuber che l’hanno sviscerato e raccontato molto meglio di quanto possa fare io.*
*In questo post parlerò, piuttosto, di una mia personale esperienza legata agli aspetti di utilizzo degli strumenti di Microsoft 365 ([Modern Workplace](/cosa-significa-modern-workplace/)) e di gestione/integrazione in ottica [Modern Management](/modern-workplace-management/), attraverso MEM (Intune) ed Azure AD.*
***Questo post, quindi, non è e non vuole essere una recensione né un giudizio assoluto: è semplicemente il racconto di un’esperienza e di un’opinione personale, maturata in un ambito di utilizzo specifico e limitato alle mie modalità di utilizzo personali e lavorative. Ok?***

Pronto? Via, si comincia!

## Outlook, Word, Excel, Powerpoint
A riguardo dei software Office classici, non posso che essere contento! Funziona tutto davvero bene: la resa a schermo dei documenti Word è ottima e fedele alla controparte Windows, Excel viaggia bene e, a riguardo di Powerpoint, grazie alla migliore gestione nativa dei PDF da parte di macOS, sono riuscito a creare una presentazione portando facilmente e *velocissimamente* contenuti da PDF a PPTX.

Capitolo a parte per Outlook: anche qui un’ottima esperienza, sebbene l’interfaccia di Outlook per Mac avrebbe bisogno di una leggera svecchiata, a mio modo di vedere. Durante la sua prima esecuzione mi è stato proposto di testare la nuova esperienza grafica e, giuro, avrei voluto tanto farlo ma, purtroppo, la beta non supporta ancora le caselle condivise di Exchange Online. Ho quindi optato per usare l’interfaccia classica ma ci riproverò tra qualche tempo: a primo impatto, la beta mi era piaciuta.

## OneDrive
Paragrafo a parte per OneDrive che, purtroppo, è l’unica nota un pochino dolente. Perché? Perché risente del fatto di essere emulato tramite Rosetta 2 (al momento di scrivere questo articolo è l’unico software della suite che non è ancora stato “tradotto”): la sync è lenta e il plugin del Finder che gestisce la funzionalità di Files On Demand, di tanto in tanto, si imbizzarrisce e, letteralmente, si schianta. Sono però sicuro che migliorerà quando arriverà la versione nativa.

## Teams
Non poteva mancare un breve racconto per un software ormai imprescindibile per la vita lavorativa di tantissime persone. Come va Teams su macOS? Anche qui, direi bene! Ho usato il MacBook Air più volte durante call di lavoro, con la webcam, con condivisione schermo attiva durante un utilizzo multi-monitor e non ha fatto una piega. Posso quindi dire che, secondo me, è stato fatto un grandissimo lavoro da parte di Microsoft.

## Edge
Che dire: ormai ho sostituito completamente Chrome e Safari. Finalmente, dopo decenni bui, Microsoft ha fatto centro con il nuovo browser Edge Chromium! Ho apprezzato tantissimo il supporto a Continuity tra Edge su iPhone e per il Mac: se stai navigando sul tuo iPhone tramite Edge, puoi continuare la navigazione sul Mac senza problemi.

## E quindi come vanno i Mac con Microsoft 365?
Se aggiungiamo a tutto quello che ho descritto poco fa
- la possibilità di fare SSO su Azure AD per autenticarsi sulle applicazioni di M365 (purtroppo non ancora il login vero e proprio sul Mac);
- la possibilità di gestire in cloud tutto il parco macchine, che sia Windows, macOS/iOS, in ottica Modern Work con un unico strumento (MEM/Intune), gestendo tutti gli aspetti di distribuzione applicazioni, configurazioni di sistema, baseline di sicurezza, eccetera;
- l’integrazione facile ed efficace di MEM (Intune) con un tool come Jamf che, di fatto, è lo standard per la gestione dei Mac in azienda...

… la mia personale opinione è: credo che oggi, 2021, ci sia la congiuntura migliore mai esistita tra i due mondi (Apple e Microsoft), tecnologicamente parlando e nell’ottica di avere dei Mac in azienda. Mai prima d’ora, sia lato client, sia lato strumenti di gestione che tipicamente si trovano nelle enterprise, questi due mondi sono andati così d’accordo.

Quindi, concludendo:

{{< rawhtml >}}
  <p class="tc">Mac in azienda</p>
  <p class="tc">+</p>
  <p class="tc">strumenti di produttività di Microsoft 365</p>
  <p class="tc">+</p>
  <p class="tc">gestione centralizzata e cloud dei dispositivi tramite MEM o Jamf+MEM</p>
  <p class="tc">?</p>
  <p class="tc">Per me la risposta è: <strong>SÌ</strong>!</p>
{{< / rawhtml >}}

È un ambito che mi stuzzica parecchio e che, per quanto mi è possibile, cercherò in tutti i modi di approfondire.

Che ne pensi? Se hai esperienza a riguardo e ti va di fare quattro chiacchiere, ti aspetto sui miei social! Sono davvero curioso di sentire i tuoi racconti sul campo coi Mac in azienda.

Il tuo IT Specialist, Riccardo