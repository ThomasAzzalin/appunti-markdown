## Risorse
Come abbiamo detto precedentemente, ogni *processo* per evolvere necessita' delle *risorse* del **sistema di elaborazione**.
Possiamo infatti vedere quest'ultimo come un'insieme di *risorse* che il *SO* puo' assegnare ai vari *processi* che le *richiedono*.
> [!NOTE] definizione di risorsa
> Una *risorsa* e' una qualsiasi componente *riusabile* o *non riusabile*, *software* o *hardware*, necessaria ad un processo o ad il sistema

### Come fa un processo ad accedere ad una risorsa
I *processi* per accedere alle *risorse* sono in *competizione*, perche' molto spesso il numero di *risorse* disponibili e' inferiore ai *processi* che le richiedono; per esempio ogni *processo* necessita' di almeno una *risorsa* per evolvere, cioe' il *processore*, che deve essere *condiviso* fra piu' *processi*.

## Come possiamo suddividere le risorse
Le *risorse* possono essere suddivise in **classi**, e tutte le *risorse* appartenenti alla stessa *classe* vengono dette *equivalenti*, cioe' una "vale" l'altra.

Le *risorse* di una *classe* vengono chiamate **istanze della classe**.
Il numero di *istanze di una classe* viene detto **molteplicita' di risorsa**.

> [!info]- Molteplicita' di risorsa
> Possiamo dire che la *molteplicita' di una risorsa* ci indica il _numero massimo di processi che la possono usare contemporaneamente_.


#### Esempio
Possiamo vedere la RAM come una *classe* di risorsa, e ogni cella di memoria e' un'*istanza  della classe*, la capacita' totale della memoria e' la *molteplicita' di risorsa*.

### Come fa un processo a richiedere una risorsa
Quando ad un processo serve una *risorsa* per *evolvere*, fa una **generica richiesta di risorsa** al *SO*.
Per generica richiesta intendiamo intendiamo che il *processo* puo' richiedere solo una risorsa di una *specifica classe*, e sara' poi il *SO* ad assegnargli una qualsiasi *istanza* di quella classe.
> [!warning] 
> La *richiesta* di una risorsa avviene *sempre* prima della sua **assegnazione**



