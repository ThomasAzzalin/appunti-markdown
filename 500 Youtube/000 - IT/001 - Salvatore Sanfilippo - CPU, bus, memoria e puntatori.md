## Video
[link](https://www.youtube.com/watch?v=et0MKBtrj4E)
data pubblicazione: 14.05.2025
data visione: 14.05.2025
voto: 8.5
Topics: #IT #C #hardware #puntatori #commodor64 

## Riassunto
Imparare bene il *C* e' utile per scrivere programmi a basso livello, come driver e programmi ad altissime prestazioni.
Ma anche a *programmare con linguaggi ad alto livello*, perche' sapendo cosa succede a basso livello avremo una visione di insieme differente che ci permette di fare delle azioni differenti

## Contenuto
Lo stesso *ragionamento* si puo' fare anche andando ancora piu' *a fondo*, avendo un'idea, anche generica, del funzionamento dell' *l'hardware* possiamo diventare *sviluppatori migliori* anche quando scriviamo in *C*.

Visto che adesso le *architetture sono complesse*, ci basiamo su tecnologie piu' vecchie:
Nel nostro caso il *commodore 64*: ha *64K di DRAM*, (Dinamic RAM) cioe' una memoria che *necessita* di essere *constantemente "rinfrescata"*, e la sua *CPU* e' la *6502*; e' *processore a 8 bit* ma utilizza degli *indirizzi a 16 bit*.
La RAM non e' troppo diversa da quella utilizzata oggi, quello che invece *cambia* e' il *modo in cui avveniva l'accesso alla memoria*. 

Il **Commodore 64** aveva già alcuni **chip integrati** speciali che potevano **intercettare e gestire certe operazioni** a seconda di quali aree di memoria il processore cercava di usare. 
In pratica, questi chip facevano da *intermediari* e decidevano come e quando eseguire certe operazioni, velocizzando così alcuni processi e rendendo il sistema più efficiente. Alcuni dei chip integrati piu' importanti:
- **VIC-II**: il chip video, responsabile della grafica.
- **SID**: il chip audio, responsabile del suono.
- **CIA (Complex Interface Adapter)**: gestiva I/O.
La stessa cosa e' presente nel *rasperry PI*.  

La CPU ha dei piedini, *16 pin* sono il *bus degli indirizzi* (mono-direzionale), e *8 pin* sono il *bus dati* (multi-direzionale).
Un'altro importante *pin era il R/W (Read/Write)*; era un *pin di controllo*, veniva settato in alto per la *lettura* e in basso per la *scrittura*.
Inoltre vi era un *pin* che avevano il compito di gestire il *clock*, chiamato *`Φ2` (phi-2)*, perche' l'accesso alla memoria e ai chip doveva essere sincronizzato.


> [!Example] Esempio
> se il processore voleva leggere cosa c'era nell'indirizzo 1000 della RAM, inseriva nei *16 pin* del *bus indirizzi* **(A0-A15)** il codice binario corrispondente a quell'indirizzo; poi settava il *pin R/W* a 1 e quando il *clock* `Φ2` andava alto, la RAM forniva i dati. Cioe' metteva il contenuto della cella di memoria sul *bus dati*. **(D0-D7)**


Un processore moderno ha altre questioni che complicano il tutto, ma alla base c'e' sempre la stessa logica:
- *bus indirizzi*
- *bus dati*
- *clock*

Nello stesso modo in cui la *6502* legge e scrive nella *RAM*, scrive e legge anche nella *memoria video*.

Nei processori più moderni esiste il concetto di **indirizzamento virtuale**: grazie a questo, ogni *processo* crede di avere a disposizione uno spazio di memoria esclusivo e separato dagli altri processi.  
In pratica, l’indirizzo 1000 di un processo può corrispondere a una posizione fisica completamente diversa dall’indirizzo 1000 di un altro processo.
Questa traduzione dagli indirizzi virtuali a quelli fisici reali avviene tramite una struttura chiamata **page table**.  
La **page table** è una tabella che *mappa* gli *indirizzi virtuali di un processo* agli *indirizzi fisici effettivi nella memoria RAM*.
Di conseguenza, l’accesso alla memoria è fortemente mediato e gestito dal sistema operativo, garantendo *isolamento*, *sicurezza* e *flessibilità* nella gestione della memoria.

Questo preambolo è molto utile per programmare in **C**, perché ci permette di avere un modello mentale semplificato di come funziona un computer moderno.
Se torniamo a pensare ai **64 KB di memoria** presenti nella DRAM del **Commodore 64**, dobbiamo immaginarla come una distesa continua di celle di memoria, numerate da 0 fino all’ultimo byte compreso nei 64 KB.

Supponiamo che, all’indirizzo **1000**, sia memorizzata una struttura dati che rappresenta la posizione di una pallina visibile a schermo. Per esempio:
- I primi 2 byte contengono la coordinata **X**;
- I successivi 2 byte contengono la coordinata **Y**.
Quindi, essendo che la struttura dati parte dalla posizione 1000, il campo successivo inizierà dall’indirizzo **1004**
A seguire, ci sono altri 8 byte usati per memorizzare due numeri in virgola mobile che rappresentano la velocità della pallina lungo gli assi X e Y. Così, arriviamo a occupare fino all’indirizzo **1011** incluso.
Se avessimo un **puntatore** che punta a questa struttura dati, si tratterebbe di una variabile intera che contiene il valore **1000**: cioè l’indirizzo di memoria dove inizia la struttura.
Il puntatore, quindi, è semplicemente l’indirizzo della cella di memoria in cui è registrato il dato.

> [!Example] Esempio
> Abbiamo un programma in C che descrive lo stato di una pallina.
Per descrivere un oggetto con diversi campi in *C*, si usa la **struttura** (`struct`).
>```c
struct ballPosition{
short x;
short y;
float vx;
float vy;
}
>```
In questo modo abbiamo definito un nuovo *tipo* in C composto da piu' campi.
Ora creiamo una variabile chiamata `ball` di tipo `struct ballPosition` e assegniamo dei valori ai campi:
>```c
struct ballPosition ball;
ball.x = 5;
ball.y = 3;
ball.vx = 1.5;
ball.vy = 1.5;
>```
>Supponiamo che questa struttura sia memorizzata in memoria a partire dall’indirizzo **1000**.
>#### Come funziona in memoria?
Anche se non usiamo esplicitamente i puntatori, durante la compilazione il compilatore:
>- Sa dove si trova la struttura in memoria (es. indirizzo 1000)
>- Calcola gli **offset** di ogni campo all’interno della struttura
>- Per esempio, il campo `x` è al **offset 0** (quindi indirizzo 1000 + 0)
>- Il campo `y` potrebbe essere a offset 2 (dipende dall’architettura e allineamento), quindi indirizzo 1002
>- E così via per `vx` e `vy`
>
>Il compilatore traduce quindi le istruzioni in operazioni di lettura/scrittura sulla memoria fisica a partire dall’indirizzo base + offset.
>
>Possiamo anche dichiarare un puntatore a questa struttura:
>```c
struct ballPosition* p;
p = &ball;
>```
In questo caso, `p` conterrà semplicemente l’indirizzo **1000**, ovvero la locazione di memoria in cui è memorizzato l’oggetto `ball`.


Se per esempio creiamo una funzione che va a modificare il contenuto della struct e invece di passare la struttura passo il puntatore, cioè l’indirizzo dove si trova la struttura, è molto più efficiente perché passo solo un numero intero.  
Così la funzione, modificando direttamente la memoria, cambia i dati della struttura originale, quindi le modifiche si vedono anche fuori dalla funzione.

## parole chiave
*MicroPython*
*indirizzamenti virtuali*
*puntatore*

## Opinione
Figata questo video, mi ha fatto capire meglio cosa sono i puntatori e perche' rendono effettivamente piu' efficiente il codice.
Sfortunatamente non parla in un modo chiarissimo Salvatore, pero' i concetti si capiscono tutti.
La parte che ho trovato "meno importante" ma comunque interessante e' stata la spiegazione del modo con cui il commodor 64 accedeva alla memoria RAM.
