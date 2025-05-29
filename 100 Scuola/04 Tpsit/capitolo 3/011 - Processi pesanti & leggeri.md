## Differenza fra processi leggeri e processi pesanti
Fino a questo momento abbiamo sempre e solo parlato di *processi*, che possiamo anche chiamare *processi pesanti*, da questo momento parleremo anche anche dei *thread* o *processi leggeri*.
La differenza fra i *processi leggeri* e i *processi pesanti* e' la difficolta' che *SO* ha nel gestirli in un *sistema multiprogrammato*, e cioe' il costo ed il numero delle operazioni che deve eseguire ogni volta che bisogna fare un *content switch*.

## Processi pesanti
Possiamo vedere i *processi pesanti* come l'insieme di due elementi, l'**immagine** e le **risorse**:
- **Immagine**, e' la parte del *processo* che contiene il **PID**, il **PC**, gli stati dei registri, stack, codice dei dati, segmento del codice ecc
- **Risorse**, sono tutte le risorse che gli sono state assegnate per poter evolvere, file, processi figli, dispositivi I/O ecc.

> [!warning] caratteristica fondamentale processi
> Ogni processo ha un proprio *spazio di indirizzamento* **privato** ed **isolato** a cui puo' accedere solo lui.
> Questa caratteristica permette la **separazione** e la **sicurezza** fra i vari *processi*.

### Cambio di contesto nei processi pesanti
Quando un *processo* si sospende ed il *SO* deve eseguire un *contex switch* le operazioni che va ad eseguire sono *molteplici* e *complesse*, perche' deve:
- Salvare il contesto del processo che si sospende
- Ripristinare il contesto del nuovo processo che va in esecuzione

Queste operazioni richiedono l'utilizzo di *tempo di CPU*, che quindi viene "*sprecato*" per eseguire operazioni non utili alla risoluzione di problemi.
### Overhead
Il tempo che la *CPU* impiega per eseguire un *content switch* si chiama **overhead** e puo' essere definito come il *costo di gestione* per realizzare il *multitasking*.
Naturalmente l'obbiettivo dei *SO* e' quello di ridurre al minimo l'**overhead** migliorando gli algoritmi di *scheduling*.

## Processi leggeri
I processi possono in oltre essere visti come:
- **L'esecuzione del codice**, cioe' il programma che evolve
- **Le risorse** che il processo utilizza e che sono salvate nel suo *spazio di indirizzamento*

Il *SO* gestisce queste due componenti in modo *indipendente*, questa caratteristica e' alla base dei **thread**:
- La parte di *esecuzione del codice* alla quale viene assegnata la *CPU* viene definito *processo leggero (thread)*
- La parte che possiede le *risorse* viene definita *processo pesante (task)*

### Cos'e' quindi un thread
Possiamo quindi dire che un *thread* e' un'unita' di esecuzione interna ad un *processo*.
possono esistere piu' *thread* all'interno di uno stesso *processo*.
Inoltre la caratteristica principale e' che tutti i *thread* presenti in un *processo* hanno accesso alle *stesse aree di memoria*, e quindi se uno modifica ad esempio una variabile, un'altro vedra' la modifica immediatamente.
L'unica cosa che ogni thread ha di privato e' il **TCB** e lo **Stack**.

### Multithreading
Con il termine **multithreading** ci riferiamo alla molteplicita' di flussi di esecuzione all'interno dello stesso processo pesante.
Per *evolvere parallelamente* ad altri *thread*, esso ha un insieme di propri elementi che lo caratterizzano in ogni momento, in analogo ai [[001 - Il modello a processi#Cosa caratterizza un processo|PCB]] dei *processi* abbiamo i **TCB (Thread Control Block)**.

### TCB
Come abbiamo detto prima, il **TCB** e' un contenitore di elementi che caratterizzano ogni thread, esso e' costituito da:
- **THREADID**, valore univoco che identifica ogni thread nel sistema. Analogo al *PID*.
- **Stato del thread**, lo stato corrente del *thread*, proprio come il *processo*
- **Registri della CPU**, vengono salvati i valori dei registri quando il *thread* viene interrotto
- **PC (Program Counter)**
- **Puntatore allo stack**, per chiamare funzioni, salvare variabili locali ecc

### Variabili personali
I *thread* possono inoltre creare delle variabili *"personali"* cioe' accessibili solo attraverso l'utilizzo di una *chiave*, in modo tale che nessun'altro thread o processo possa *vederle* e *modificarle*.

## Utilita' dei thread
I *thread* permetto di sfruttare meglio le *architetture multiprocessore*, e di *scambiare* e *comunicare* informazioni ad altri thread in modo *immediato*.

### Routine di libreria rientranti
Per poter esistere i *thread* necessitano che le **routine di libreria siano rientranti**, cioe' che *permettano* a piu' thread di *accedervi contemporaneamente* senza incorrere in errori.
Questo perche' i *thread* interagiscono con il *SO* mediante *[[school/tpsit/capitolo 3/999 - explainations#System calls|System call]]* che usano *dati* e *tabelle* dedicate al processo, per questo esse devono essere progettate per permettere a piu' *thread* di accedervi contemporaneamente.

## Codici eseguibili con thread
Non tutti i codici sono eseguibili con i *thread*; i programmi che ne permettono l'utilizzo hanno un propieta' particolare, chiamata **Thread safety**.

### Thread safety
Come abbiamo detto prima, un codice per essere eseguito con i *thread* deve essere **Thread safety**, cioe':
- Permettere di essere eseguito da piu' *thread* contemporaneamente
- Permettere a un solo *thread* alla volta di accedere alle risorse condivise, sia per leggerle che per modificarle
