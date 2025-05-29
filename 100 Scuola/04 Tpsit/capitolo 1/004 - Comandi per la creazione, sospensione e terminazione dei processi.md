## Creazione di un processo
Nei sistemi operativi della famiglia *\*Nix like* per creare un nuovo processo viene utilizzata la funzione **fork()**
```c
pid fork(void);
```
### Come funziona il Fork()
Quando la funzione fork() viene chiamata viene generato un *processo figlio* identico al suo *processo padre*. Piu' nello specifico nel sistema avvengono queste cose:
- Viene generato un nuovo **PID** e un nuovo **PCB**, per il processo figlio
- Il *SO* crea una copia dello *stato della memoria del processo padre* (variabili globali e statiche, le istruzioni del programma) e lo assegna al processo figlio
- Tutte le risorse utilizzate dal processo padre sono *condivise* con il processo figlio

## Terminazione del processo figlio
Quando un processo figlio *termina* mediante *operazione di exit()* o perche' ha *eseguito tutto il codice*, il *SO* esegue delle operazioni:
- Chiude i file che erano aperti
- Rilascia la memoria che era utilizzata
- Salva il valore dell' *exit status* nel *PCB* per poi darlo al processo padre
- Il *PCB* non viene eliminato, si modifica lo stato in *zombie* e gli vengono inserite all'interno altre informazioni come l' *exit status*, oltre a quelle che c'erano gia' prima come il *PID*.
 
### Exit status
L'*exit status* di un processo e' composto da **2 byte**, e contiene le informazioni riguardanti come un processo e' terminato. 
Piu' nello specifico:
- *Negli 8 bit piu' significativi (MSB)*: viene specificato il *valore di terminazione del processo* che e' stato inserito nella chiamata Exit(status).
- *Negli 8 bit meno significativi (LSB)*: Viene segnalata la ragione della terminazione, che puo' essere di tipo naturale o mediante un segnale.

## funzione wait()
Il *processo padre* puo' invocare la funzione *wait()* che gli permette di *sospendere* la sua evoluzione fin quando il *processo figlio* non viene *terminato*.
Quando il *processo figlio* termina, il *SO* restituisce al *processo padre* l' *exit status* e le altre informazioni contenuto nel *PCB*, a questo punto il *SO* puo' eliminare definitivamente queste informazioni dalla memoria.
dopo che il *processo padre* utilizza la funzione *wait()*  lui ed il *processo figlio* si *sincronizzano*.

