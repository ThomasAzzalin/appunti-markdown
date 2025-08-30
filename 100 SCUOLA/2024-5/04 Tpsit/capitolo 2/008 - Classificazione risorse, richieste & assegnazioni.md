## Risorse, richieste & assegnazioni
Come abbiamo detto precedentemente i *processi* possono richiedere delle *rirorse* che gli servono per *evolvere* e il *SO*, gliele *assegnera'*; pero' non tutte le *richieste*, non tutte le *risorse*  & e non tutte le *assegnazioni* sono uguali, per possiamo catalogarle.

## Classificazione delle richieste
Le *richieste* che un *processo* fa al sistema si possono classificare in base:
- **Numero**
- **Tipologia di richiesta**

### Classificazione per numero
- **Singola**: la richiesta singola, e' il caso piu' comune, ed avviene quando un *processo* richiede ad il sistema una generica istanza di una *classe* specifica. 
Cioe' un *processo* richiede *una sola risorsa alla volta*.
- **Multipla**: la richiesta multipla avviene quando un *processo* richiede contemporaneamente almeno due risorse per poter *evolvere*. 
Ad esempio richiedendo almeno due *istanze* della stessa *classe*, o piu' *istanze* di piu *classi*.

### Classificazione per tipologia
- **Richiesta bloccante**: e' il caso in cui un *processo* richiede una *risorsa*, e se essa non gli viene assegnata immediamente comporta la *sospensione* del processo stesso, e quindi un cambio di stato in *attesa* di ricevere la *risorsa* che gli serve per poter evolvere.
- **Richiesta non bloccante**: e' il caso in cui il *processo* puo' *evolvere* anche se non gli viene assegnata immediatamente la *risorsa*. 
In questo caso il sistema effettua una *notifica* che il processo *elaborera'* senza interrompersi.

## Classificazione delle assegnazioni
Le *risorse* che vengono richieste da un *processo* viene *assegnata* dal *SO*, questa *assegnazione* puo' essere di due tipologie:
- **Statica**: l'assegnazione statica di una *risorsa* avviene quando il processo viene creato per la prima volta, e gli rimane *dedicata* fino alla sua terminazione.
Ad esempio l'area della memoria RAM in cui il processo e le sue variabili sono caricate.
- **Dinamica**: e' il caso piu' frequente, avviene spesso con le *risorse condivise* che i *processi* *richiedono* durante la loro esecuzione; queste risorse vengono *utilizzate* quando necessarie, e *rilasciate* quando non piu' utili a far evolvere il processo.


## Classificazione delle risorse
Le risorse che possono essere assegnate ad un processo possono essere divise per:
- **Mutua esclusivita'**
- **Modalita' di utilizzo**

### Classificazione per mutua esclusivita'
- **Risorse seriali**: sono tutte quelle risorse che non possono essere assegnate contemporaneamente a piu' processi che devono quindi attendere il proprio turno per poterne fare uso. Si chiamano **risorse ad accesso mutualmente esclusivo**.
- **Risorse non seriali**: le risorse che ammettono l'accesso contemporaneamente da parte di piu' processi, sono anche chiamate **risorse di molteplicita' infinita**. Un'esempio potrebbero essere i file in sola lettura.

### Classificazione per modalita' di utilizzo
- **[[school/tpsit/capitolo 2/999 - explainations#Risorsa preemptive|Risorse pre-rilasciabili (preemptive)]]**: si chiama cosi' una *risorsa* che mentre sta venendo usata da un processo puo' essere *rilasciata* prima che esso abbia finito di utilizzarla, *senza provocare danni* al processo stesso; quando essa gli viene *riassegnata* puo' *continuare il lavoro da dove si era fermato*. 
- **Risorse non prerilasciabili (non-preemptive)**: una *risorsa* si chiama cosi' se una volta assegnata ad un processo* non si puo' sottrargliela* senza *provocare danni*; come il pericolo di dover *ripetere da capo la sua esecuzione*.

## Risorse in condivisione e private
Tutto il discorso affrontato precedentemente riguardava solo le *Risorse private*, cioe' quelle risorse *accessibili* e *visibili* da tutti i processi che ne hanno le autorizzazioni.
Ma esistono anche delle *risorse private* cioe' assegnate dal *SO* in modo **esclusivo** ad un processo e neppure visibili ad altri processi, e che quindi non necessitano di essere gestite come quelle condivise.