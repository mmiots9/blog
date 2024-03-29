---
title: "Come ricordarsi tutte le shortcut"
h1title: "Addshort e searchshort: funzioni per le shortcut"
subtitle: "Come aggiungere e cercare le shortcut in un file"
date: 2021-08-10
modified: 
description: "Scrivere e cercare shourtcut grazie a file .txt"
draft: false
hideToc: false
enableToc: true
enableTocContent: true
tocFolding: true
tocPosition: outer
tocLevels: ["h2", "h3", "h4"]
tags:
- Bash
- Shortcut
series:
- Le mie funzioni bash
categories:
- Bash
image: "/images/Bash/addshort_searchshort/shortcut.jpg"
author: Matteo Miotto
authorEmoji: 🤖
authorImage: "/images/whoami/me.jpeg"
---
<div style="text-align: justify;">

Non riesci a ricordati tutte le shortcut che ci sono per un programma o per il tuo pc? Non sei l'unico!  
Ci sono talmente tante shortcut, che è impossibile ricordarsele tutte, è normale. Stanco di doverle cercare ogni volta su internet, ho deciso di creare vari file dove segnarmele tutte, divise per programma/applicativo che uso (per esempio io ho Mac, Terminal, VSCode e RStudio).   
Sentivo inoltre la necessità di trovare un modo veloce sia per aggiungere le shortcut (senza dover andare a cercare il file da qualche parte), sia per cercarle; per questo motivo ho scritto due funzioni bash molto semplici, che mi permettono di eseguire tutte queste operazioni dal terminale.  
Vediamole nel dettaglio, ricordando che queste funzioni le potete trovare nell'apposita [repo](https://github.com/mmiots9/bash-functions) su github, nel file *cheat_short.sh*.

## Addshort
La prima funzione, per ovvi motivi, è quella che ci permette di aggiungere le shortcut nei file.

Ci sono da fare un paio di premesse.  
Il file nel quale si vuole aggiungere la shortcut è diviso in 2 o 3 colonne separate da tabulazioni. Se si vogliono aggiungere i nomi delle colonne (per esempio "comando" e "cosa fa"), bisogna farlo dividendole con tabulazioni.  
Ma perchè parlo di 2 o 3 colonne? Essendo io italiano ed essendo l'italiano la mia lungua madre, ho deciso di creare la funzione in modo tale che si vengano a creare 3 colonne: comando, cosa fa (in italiano) e cosa fa (in inglese). Nel caso in cui non si voglia la colonna della propria lingua madre e si voglia utilizzare solo quella inglese, la funzione prevede questa modifica aprendo il codice e seguendo i passaggi indicati nei commenti. In questo caso, le colonne saranno 2.  
Se si utilizzano più file, questi dovranno avere la stessa estensione ed essere nella stessa cartella.

### Settaggi
Finite le premesse, vediamo cosa bisogna fare una volta scaricato il file della funzione.
La prima cosa da fare è aprire il file con un editor di testo per impostare alcuni parametri fondamentali:
<figure id="settaggi_iniziali">
  <img src="/images/Bash/addshort_searchshort/addsh2set.png" alt="Prime cose da settare addshort" width=80%>
  <figcaption style="text-align:center;">Figura 1: settaggi iniziali per le funzioni addshort e searchshort</figcaption>
</figure>

***arr***: array dei nomi dei file, <u>senza</u> estensione e path  
***ext***: estensione dei file  
***filepath***: il path della cartella dove sono i file, consiglio vivamente di mettere il path completo dalla home directory
***whatdoes***: se volete avere la colonna della vostra lingua, questa sarà la stringa corrispondente alla domanda "What it does?" (cosa fa la shortcut) che verrà posta nel terminale.

L'altra modifica da fare è di commentare e di uncommentare le linee relative alla possibilità della doppia lingua, in base alle proprie esigenze (vedi figura sottostante).
<img src="/images/Bash/addshort_searchshort/comment-uncommentadd.png" alt="Settaggi per seconda lingua" width=80%>

### Lancio della funzione
Ora, dopo aver aggiunto il file della funzione nel path del terminale, siamo pronti per lanciarla tramite il comando *addshort*.

<div style="text-align:center">
<video height=300px width=auto controls>
  <source src="/images/Bash/addshort_searchshort/addshort.mov">
</video>
</div>

<p style="margin-bottom:0;">Il video mostra i vari passaggi:</p>
<ol>
<li>In quale file va aggiunta la shortcut?</li>
<li>Inserire la shortcut: in questo momento, la funzione <b>verifica</b> se è già esistente, in tal caso si ferma e comunica questo all'utente</li>
<li>Inserire cosa fa nella lingua madre</li>
<li>Inserire cosa fa in inglese</li>
<li>Richiesta se si vuole aggiungere un'altra shortcut allo stesso file</li>
</ol>

A questo punto, la funzione aggiunge queste informazioni al file selezionato.

## Searchshort
Questa funzione permette di cercare una shortcut che non ci si ricorda inserendo parole chiave. La funzione, di per sè, è molto semplice: è come se fosse un grep alla fin fine, solo che qui la si può lanciare da qualunque directory si sia dentro.

### Settaggi
Anche in questo caso, ci sono dei settaggi da implementare: gli stessi della funzione precedente (vedi figura <a href="#settaggi_iniziali">1</a>).

Inoltre, c'è da commentare o uncommentare un paio di comandi, in base alla presenza o meno della seconda lingua.
<img src="/images/Bash/addshort_searchshort/comment-uncommentsearch.png" alt="Settaggi per seconda lingua" width=80%>

### Lancio della funzione
Come prima, avendo aggiunto il file della funzione nel path, si lancia col comando *searchshort*.

<div style="text-align:center">
<video height=300px width=auto controls>
  <source src="/images/Bash/addshort_searchshort/searchshort.mov">
</video>
</div>

Come si può vedere dal video, la procedura è molto immediata: si sceglie in quale file cercare la shortcut e si inseriscono le parole chiave.  
**N.B.:** Non è necessario che le parole siano in ordine corretto!

Se non ci sono risultati con quella combinazione di parole, verrò proiettato un messaggio. Si deve dunque o riprovare con un'altra combinazione, oppure inserire quella shortcut prima di cercarla.

## Conclusioni
Spero che questa breve guida sull'utilizzo di queste due semplici funzioni sia chiara e utile.  
Come vedrete dal codice, non c'è sempre bisogno di creare funzioni super complicate e macchinose, a volte la semplicità paga.



</div>