##  Ciclo di vita di un processo
Un *programma* diviene *processo* quando inizia ad essere eseguito dal *processore*, e la sua *terminazione* puo' essere causata da diversi avvenimenti:
- Viene eseguita un'*istruzione macchina di terminazione*.
- Quando effettua un'*operazione illecita*.
- Quando si presenta un'*errore* che non gli permette di proseguire.

### Dall'avvio alla sua terminazione
Dal suo primo avvio alla sua terminazione un processo segue un ciclo di vita, possiamo individuare un'insieme di situazione in cui un processo si puo' trovare, questi stati vengono chiamati **stati del processo**, e sono associati all'*evoluzione* del processo e alla sua *situazione* rispetto al *processore*, e alle *risorse*.

## Stati del processo
Un processo, come abbiamo detto prima, durante il suo ciclo di vita varia il suo stato.
Rispetto al *processore* puo' trovarsi nei seguenti stati:
- **Nuovo (init, new)**: Un processo appena creato, quando viene cioe' richiesta l'esecuzione di un *programma* che risiede sul disco.
- **Esecuzione (running)**: Il processo sta *evolvendo*, il *processore* sta eseguendo le sue *istruzioni*. Il *processore* e' quindi assegnato a questo processo.
- **Attesa (waiting)**: il processo sta *aspettando* che il *SO* gli assegni delle *risorse* che gli servono per evolvere. (*risorse* oltre al *processore*). Sta quindi aspettando che si verifichi un' *evento*, che liberi una risorsa che gli serve
- **Pronto (ready-to-run)**: Il processo ha tutte le risorse che gli servono per evolvere, tranne il *processore*. Sta quindi aspettando che il *SO* gli assegni il suo *time-slice di CPU*
- **Terminato (terminated)**: Tutto il *codice* del processo e' stato eseguito. Quando un processo *termina* il *SO* deve liberare le risorse che il processo stesso stava utilizzando.

### Cos'e' quindi lo stato di un processo
Con *stato di un processo* intendiamo una tra le 5 situazione descritte precedentemente.
Puo' assumere una ed una sola volta gli stati di *Nuovo* e *Terminato*. E puo' variare infinite volte tra gli altri 3 stati: *Esecuzione*, *Attesa*, *Pronto*.

### Vita di un processo
Seguiamo le prime fasi della nascita di un processo:
Quando un nuovo processo *"nasce"* gli viene assegnato un'identificatore **PID (Process IDentifier)**, e viene inserito nella *lista dei processi pronti (RL, Ready List)*  

### Come nasce un nuovo processo
Ogni processo e' generato da un *processo padre*, mentre lui prende il nome di *processo figlio*. Unica eccezione e' il processo **init**, cioe' il primo ad essere eseguito dal *SO*, che non ha *nessun padre*.

### Lo stato di esecuzine
Quando ad un processo che si trova nella *RL* viene assegnata la *CPU*, il processo passa nello stato di *esecuzione*. 
Ci sono tre motivi che possono far uscire il processo dallo stato di esecuzione:
- Termina la sua esecuzione, non c'e' piu' codice da eseguire (**exit**).
- Termina il suo *time-slice di CPU*, quindi torna nella *RL*.
- Per poter evolvere necessita di una *risorsa* che al momento non e' disponibile, il processo si *sospende* e viene messo nella **WL (Waiting List)**.


