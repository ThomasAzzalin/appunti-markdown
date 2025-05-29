## L'evoluzione tecnologica moderna
Negli ultimi anni, la *capacita' computazionale* e' aumentata grazie all'*aumento della velocita' di elaborazione delle CPU*. Inoltre i moderni sistemi operativi cercano di sfruttare al massimo il *[[school/tpsit/capitolo 1/999 - explainations#Parallelismo fisico|Parallelismo fisico]]* per:
- Minimizzare i **tempi di risposta**
- Aumentare il **[[school/tpsit/capitolo 1/999 - explainations#throughput|throughput]]**

### Problematiche attuali
Nonostante tutti questi miglioramenti, la *gestione del processore* deve essere *ottimizzata*, perche' spesso si presentano *situazioni critiche*. Ed e' proprio a questo che serve il **Sistema Operativo (SO)**.

## I programmi
I **programmi** sono delle entita' **passive** che contengono le **istruzione** che dovranno poi essere eseguite. Quando un programma viene caricato in *memoria* e mandato in *esecuzione* diventa un **processo**

## I processi
I **processi**, invece, sono *istanze* dei *programmi* che vengono caricati nella **RAM**.
Sono entita' **attive**, ovvero *evolvono* nel tempo, man mano che la *CPU* esegue le sue istruzioni.

### Cosa caratterizza un processo
Un *processo*, in ogni momento, e' caratterizzato da diversi *elementi*:
- **PID**, il *Program IDentifier*, valore univoco che identifica ogni processo in un sistema
- **Stato del processo**.
- **Segmento di codice**, il codice del *programma* che sta eseguendo.
- **Segmento dei dati**, che contiene tutti i dati statici del processo, come:
	- *Variabili globali*
	- *Costanti*
- **Program counter (PC)**, l'indirizzo della prossima *istruzione* che il processore deve eseguire.
- **Registri della CPU**, che contenuto di tutti i registri assegnati al processo:
	- *Registri generali*
	- *Registri di puntamento*: registri che contengono l'indirizzo dei puntatori di determinate memorie, come lo *Stack*
	- *Registri di stato*: flag per le condizioni, come quelle di *overflow* o *carry*
- **Stack**, che contiene tutti i dati relativi all'esecuzione delle funzioni o delle chiamate di sistema, come:
	- *Variabili locali*
	- *Parametri delle funzioni*
	- *Indirizzi di ritorno*, per le chiamate di funzione
- **Heap**, una memoria dinamica assegnata al processo per allocare e gestire dati durante l'esecuzione, come *Strutture dati dinamiche* (oggetti, array, liste, ecc.).

Tutti questi elementi sono salvati nel **PCB (Program Control Block)**

### Risorse assegnate ad un processo
Ad ogni *processo* il *SO* puo' assegnare delle **risorse** che gli servono ad *evolvere*, come:
- *Processore*
- *Memoria ram*
- *File*
- *Risorse di rete*
- *Dispositivi I/O*

## Algoritmi di schedulazione (scheduling)
Nel **modello a processi** tutti i software che possono essere eseguti sono organizzati in *processi sequenziali* (detti piu' semplicemente *processi*).
Visto che un singolo **processore** sara' condiviso da diversi processi vengono utilizzati algoritmi di **scheduling** per decidere quale processo eseguire successivamente sulla *CPU*, e quando interromperne altri.

### Tecnica di multiprogrammazione
Questi algoritmi sono utilizzati nella **multiprogrammazione**, che per essere messa in pratica ha bisogno che ci siano *contemporaneamente* diversi processi in memoria.

#### Come fa ad esistere questa tecnica
L'esecuzione di un processo e' costituito dalla successione di due cose:
- *fasi di elaborazione*, in cui la CPU e' occupata ad eseguire il codice.
- *fasi di attesa*, in cui la CPU deve aspettare l'esecuzione di altre operazioni sulle risorse.

Durante le *fasi di attesa*, la CPU rimane inattiva.
Quindi grazie alla **multiprogrammazione** il processore puo' eseguire in contemporanea piu' processi, limitando al minimo i tempi morti.

## Interazione tra processi
I processi si possono dividere in 3 macro categorie, in base a come interagiscono tra di loro abbiamo:
### Processi indipendenti
Un processo si dice *indipendente* se per *evolvere* non necessita di informazioni generate da altri processi.

### Processi cooperativi
Due o piu' processi si dice che *cooperano* se per *evolvere* hanno bisogno di *scambiarsi informazioni, dati, messaggi*. 
Per scambiare informazioni due processi devono **sincronizzarsi**.
#### Utilita' dei processi che cooperano
Avere processi che cooperano e' molto utile per diversi motivi:
- **Condivisione delle risorse**: questo permette di evitare duplicazioni e attese inutili, e sfruttare al meglio le risorse disponibili.
- **Parallelismo**: consiste nel suddividere un lavoro complesso in piu' parti che verranno poi eseguite in contemporanea.
- **Replicazione di un servizio**: un processo puo' essere replicato in modo tale che se uno va giu', ci saranno comunque altri processi che svolgono lo stesso compito.
- **Modularita'**: diversi processi possono operare all'interno della stessa applicazione per risolvere problemi differenti.

### Processi in competizione
Due o piu' processi possono essere in *competizione* se si *"ostacolano"* a vicenda *compromettendo* il buon funzionamento di uno o dell'altro. 
Ad esempio  due processi che *competono* per *utilizzare* la stessa risorsa, come la CPU.
Al contrario dei processi che *cooperano*, i processi in *competizione* evolvono in modo individuale.

#### Problematiche dei processi in competizione
Questa interazione tra processi puo' portare a delle *situazioni indesiderate* come ad esempio **blocchi individuali** o **critici**
