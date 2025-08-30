## Descrittore del processo vs PCB
Nei *SO* *\*nix like* il *descrittore del processo* & il *PCB* sono la stessa cosa.
Per comodita' andremo avanti a chiamarlo *PCB*.

### Cosa contiene il PCB
Il *PCB* contiene tutte le informazioni riguardanti uno specifico processo, nello specifico:
- **PID (Program IDentifier)**, identificatore unico di ogni processo.
- **Stato** corrente del processo.
- **Registri della CPU**, il contenuto nei registri viene salvato quando avviene un *content switch*.
- **Informazioni sulla priorita' e sullo scheduling**, la priorita' sul processo e i dati che necessita lo *scheduler* per gestire al meglio il processo.
- **PC (Program Counter)**, Indirizzo della prossima operazione del processo che il processore deve elaborare.
- **Puntatori**, i puntatori alla memoria del processo, 
- **Informazioni su dispositivi I/O**, quali file sono aperti dal processo.
- **Accounting**, da quanto tempo il processo sta utilizzando la CPU, e altre informazioni

## Contesto del processo
Il contesto del processo e' un'insieme di elementi che variano al variare del processo.
E' proprio questo che cambia quando parliamo di *Content Switch*.
Inoltre questo elemento puo' essere chiamato **area di salvataggio dello stato della CPU**, e contiene:
- *Program Counter (PC)*
- *Registri*
- *Accounting*
- *Stato dell' I/O*, che tiene traccia dei file e dei dispositivi che servono al processo

### Vita del PCB
Il PCB viene creato ed assegnato ad ogni processo quando nascono, vengono modificate le sue informazioni interne man man che il processo evolve, e quando quest'ultimo viene terminato anche esso viene cancellato.

## Il ruolo del PCB nel sistema
Il *SO* per far funzionare il *modello a processi* necessita della *Process Table*, cioe' una tabella in cui tutti i processi sono inseriti con i loro relativi *PCB*, in modo tale da avere sempre a disposizione le informazioni riguardanti qualsiasi processo. 

Salvando tutte le *informazioni* di un *processo* in un luogo specifico, quando un processo viene *interrotto* e poi fatto *ripartire* il *processore* sa perfettamente dove era arrivato e puo' proseguire come se non fosse mai stato fermato.
