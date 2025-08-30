## Info
#WEB #SISTEMI #HTTP #CLIENT-SERVER 

## Architettura client server: Il Cuore del Web
L'**architettura client-server** rappresenta un modello fondamentale di progettazione dei [[08 - Architettura client server#sistemi informatici distribuiti|sistemi informatici distribuiti]], dove le responsabilità sono chiaramente separate tra due entità distinte che comunicano attraverso una rete.

## Definizione e Principi Fondamentali

L'architettura client-server è un paradigma di comunicazione asincrona basato sul principio della **separazione dei ruoli**. In questo modello, abbiamo due componenti principali:

Il **client** è il programma o processo che inizia la comunicazione richiedendo servizi, dati o risorse. È tipicamente l'entità che si trova più vicina all'utente finale e ha il compito di presentare l'interfaccia utente e gestire l'interazione.

Il **server** è il programma o processo che risponde alle richieste del client, fornendo i servizi, i dati o le risorse richieste. 
Il server è progettato per essere *sempre in ascolto* e in grado di *gestire multiple richieste contemporaneamente*.

## Caratteristiche Tecniche dell'Architettura

La comunicazione avviene attraverso un **protocollo di rete** standardizzato. 
Nel caso del Web, il protocollo principale è [[02 - HTTP - Fondamenti e Primi Passi]], che definisce come client e server devono formattare e trasmettere i messaggi.

Il server mantiene uno **stato di ascolto** su una [[08 - Architettura client server#porta|porta]] specifica (nel caso del Web, tipicamente la porta *80 per HTTP* e *443 per HTTPS*). Quando un client vuole comunicare, stabilisce una connessione TCP/IP con il server sulla porta appropriata.

La comunicazione segue un modello **request-response**: il client invia una richiesta strutturata secondo il protocollo, il server elabora la richiesta e invia una risposta appropriata. Dopo la risposta, la connessione può essere chiusa o mantenuta aperta per ulteriori richieste.

## Vantaggi dell'Architettura Client-Server

Questa architettura offre diversi vantaggi significativi. La **centralizzazione** delle risorse permette di mantenere dati e logica applicativa in un punto centrale, facilitando la gestione, l'aggiornamento e la manutenzione del sistema.

La **scalabilità** è un altro punto di forza: un singolo server può gestire centinaia o migliaia di client contemporaneamente, e se necessario, si possono aggiungere più server per distribuire il carico.

La **specializzazione** consente di ottimizzare ciascun componente per il suo ruolo specifico. I client possono essere ottimizzati per l'interfaccia utente e l'esperienza utente, mentre i server possono essere ottimizzati per prestazioni, sicurezza e gestione dei dati.

## L'Architettura Client-Server nel World Wide Web

Nel contesto del Web, l'architettura client-server assume caratteristiche specifiche. Il **web browser** agisce come client universale, capace di interpretare e renderizzare contenuti HTML, CSS e JavaScript. Il browser gestisce l'interfaccia utente, interpreta i link, gestisce la cronologia e mantiene lo stato della sessione utente.

Il **web server** è un software specializzato che rimane in ascolto per richieste HTTP. Quando riceve una richiesta per una risorsa (una pagina HTML, un'immagine, un file CSS), il server localizza la risorsa nel suo file system o la genera dinamicamente, quindi la invia al client insieme agli appropriati header HTTP.

## Evoluzione e Varianti

L'architettura client-server ha subito diverse evoluzioni nel tempo. L'architettura **thin client** mantiene la maggior parte della logica applicativa sul server, mentre il client si occupa principalmente della presentazione. Questo approccio era comune nei primi anni del Web.

L'architettura **thick client** sposta più logica applicativa sul client, che diventa più intelligente e capace di elaborazioni complesse. Questo è evidente nelle moderne applicazioni web che utilizzano JavaScript intensivamente.

L'architettura **multi-tier** estende il modello tradizionale introducendo livelli intermedi. Nel Web moderno, spesso abbiamo un web server che comunica con un application server, che a sua volta comunica con un database server.

## Protocolli e Comunicazione

La comunicazione client-server nel Web si basa su protocolli stratificati. Al livello più basso, TCP/IP gestisce la trasmissione affidabile dei dati. HTTP opera sopra TCP e definisce la struttura delle richieste e risposte Web.

Una richiesta HTTP tipica include un metodo (GET, POST, PUT, DELETE), un URL che identifica la risorsa, header che forniscono metadati sulla richiesta, e opzionalmente un body con dati aggiuntivi.

La risposta HTTP include uno status code che indica l'esito della richiesta, header di risposta con metadati, e il body che contiene la risorsa richiesta o informazioni sull'errore.

## Gestione della Concorrenza

Un aspetto critico dell'architettura client-server è la gestione di multiple richieste simultanee. I server Web moderni utilizzano diverse strategie: alcuni creano un nuovo processo per ogni richiesta, altri utilizzano thread multipli, e i più avanzati implementano modelli di programmazione asincrona per gestire migliaia di connessioni simultanee con efficienza.

Questa architettura ha reso possibile la nascita e l'evoluzione del World Wide Web, fornendo un modello scalabile, distribuito e flessibile per la condivisione di informazioni su scala globale.