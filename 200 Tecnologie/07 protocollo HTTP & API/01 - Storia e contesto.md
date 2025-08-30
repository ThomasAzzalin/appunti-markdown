## Info
tags: #SISTEMI #INTERNET #PROTOCOLLI #HTTP #API

## Le origini: prima del web
Siamo negli anni 80, i computer e internet esisono gia', ma e' un mondo completamente diverso da quello di oggi.
Internet veniva usato principalmente da *universita'* e *centri di ricerca* per scambiare file e messaggi di testo.
Non esistevano *pagine web*, *browser* e non si poteva navigare.
Il problema era che c'erano **moltissime informazioni** sparse su computer diversi, ma non vi era un modo comodo ed uniforme per accedervi.

> [!Example] Similitudine
> Era come avere una biblioteca gigantesca dove ogni libro è scritto in una lingua diversa e conservato in un edificio diverso.

---

## La Nascita del World Wide Web (1989-1991)
In questo contesto un'uomo, **Tim Berners-Lee**, un fisico britannico che lavorava al *CERN*, si trovava di fronte a un problema pratico:
I ricercatori del *CERN* avevano difficolta' a condividere e accedere alle informazioni sui loro progetti.
La sua intuizione fu la seguente:
Creare un sistema dove ogni informazioni aveva un indirizzo univoco e poteva essere collegato a qualsiasi altra informazioni.
Nasce in questo modo il concetto di Ipertesto Globale.
Per sviluppare la sua idea invento' tre tecnologie che utilizziamo tutt'oggi.
- [[01 - Storia e contesto#HTML (HyperText Markup Language)|HTML]]
- [[01 - Storia e contesto#HTTP (HyperText Transfer Protocol)|HTTP]]
- [[01 - Storia e contesto#URL (Uniform Resource Locator)|URL]]

### HTML (HyperText Markup Language)
E' un linguaggio per strutturare le informazioni e creare collegamenti tra documenti.
Lo definisce come il *DNA* di una pagina web, definisce *cosa c'e'* nella pagina e come e' *organizzato*.

### HTTP (HyperText Transfer Protocol)
E' il protocollo che regola le comunicazione che permettono ai computer di scambiarsi documenti HTML.
Nel corso degli anni questa tecnologia ha subito [[02 - HTTP - Fondamenti e Primi Passi|moltissimi miglioramenti]].


### URL (Uniform Resource Locator)
L'indirizzo univoco di ogni risorsa su internet. Ogni pagina web, immagine, video ha il suo URL.

### Primo sito web
Il primo sito web fu pubblicato il 6 agosto 1991. 
Era semplicissimo: solo testo e alcuni collegamenti. Ma conteneva qualcosa di rivoluzionario: la spiegazione di cos'era il *World Wide Web* e come usarlo.

---

## L'Architettura Client-Server: Il Cuore del Web
Per capire come funziona il web, e' indispensabile assimilare il concetto di *archiettura client-server*.

**Il Client** è il tuo *browser* - Chrome, Firefox, Safari. Quando digiti un [[01 - Storia e contesto#URL (Uniform Resource Locator)|URL]] o clicchi su un link, il browser **richiede** una pagina web al *server*.

**Il Server** è un computer potente che conserva le pagine web e le **restituisce** ai client che le richiedono. Quando il server riceve la richiesta del tuo browser, prepara la pagina web richiesta e te la invia.

**Il Processo** funziona così: il tuo browser invia una **richiesta HTTP** al server specificando quale pagina vuole (usando l'URL). Il server elabora la richiesta, trova la pagina richiesta, e la invia indietro al browser usando sempre il protocollo [[01 - Storia e contesto#HTTP (HyperText Transfer Protocol)|HTTP]]. Il browser riceve la risposta e mostra la pagina sullo schermo.

Questo sistema è incredibilmente **scalabile**: un singolo server può servire migliaia di client contemporaneamente, e un client può richiedere informazioni da migliaia di server diversi.

---

## L'Evoluzione del Web: Le Tre Ere
### Web 1.0 (1991-2004): Il Web Statico
Il web delle origini era principalmente "*read-only*", potevi solo leggere contenuti. 
Le pagine erano *statiche*; era come leggere una rivista digitale: informazioni utili, ma non potevi interagire molto. 
I siti erano semplici, con testo, immagini e alcuni link.

### Web 2.0 (2004-2010): Il Web Sociale 
Questa e' stata la prima e vera rivoluzone: il web è diventato *interattivo* e sociale; sono nati Facebook, YouTube, Wikipedia e i blog. 
Ora non eri più solo un lettore, ma potevi *creare contenuti*, *commentare*, *condividere*. 
Le tecnologie come JavaScript, AJAX e i CSS avanzati hanno reso le pagine web più dinamiche e interattive. 
È nato il concetto di **"user-generated content"**: contenuti creati dagli utenti.

### Web 3.0 (2010-oggi): Il Web Semantico e Mobile 
Il web è diventato più *intelligente* e *accessibile* ovunque. 
I motori di ricerca capiscono meglio il significato delle tue ricerche, le applicazioni web sono potenti quanto i software desktop, e soprattutto il web si è spostato sui dispositivi mobili. 
Oggi il web "sa" dove sei, cosa stai facendo, e può fornirti *informazioni personalizzate*.

---

## La tecnologia web oggi
In meno di 35 anni, siamo passati da un web che serviva poche pagine di testo a un ecosistema che gestisce miliardi di utenti, streaming video in 4K, e-commerce globale, social media, e applicazioni complesse che funzionano interamente nel browser.

L'*architettura client-server* si è evoluta ma è rimasta fondamentalmente la stessa. Quello che è cambiato è la complessità: oggi i server possono essere cloud distribuiti su tutto il pianeta, i client possono essere smartphone potenti quanto i computer di una volta, e tra client e server ci possono essere decine di altri sistemi che ottimizzano, proteggono e migliorano l'esperienza.

Il web ha democratizzato l'accesso all'informazione e ha creato opportunità economiche che prima non esistevano. Ha cambiato il modo in cui lavoriamo, studiamo, ci intratteniamo e ci relazioniamo con gli altri.

Ecco perché la visione di Tim Berners-Lee di un "web aperto e universale" è stata così potente: ha creato non solo una tecnologia, ma un nuovo modo di organizzare la conoscenza umana.