## L'elaborazione parallela
Esistono diverse *applicazioni*, anche di tipologie molto differente fra di loro, che richiedono l'*elaborazione parallela*.
La necessita' di *collaborare* e di *condividere risorse* e' diversa per ciascuna applicazione.
E' quindi importante avere piu' strumenti possibili per *descrivere* nella maniera migliore le *situazioni* in cui e' necessario un *alto grado di parallelismo*, dove sono presenti molte risorse in condivisione; ma anche nelle situazioni con *cooperazione molto ridotta*, con le *attivita'* svolte in parallelo che sono *quasi indipendenti fra di loro*.

### Punto di forza dei processi
I *processi* sono **entita' autonome**, e quindi sono molto utili quando bisogna eseguire delle **attivita' autonome** con *poche risorse condivise*; ma non sono invece adatti per la scrittura di applicazione che necessitano di una *forte cooperazione*.

### nuova entita': I thread
Per risolvere il *punto debole dei processi*, cioe' la creazione di applicazioni che richiedono una forte cooperazione, e' stata implementata una *nuova entita'*: i **thread** (chiamati anche **processi leggeri**).
Questa nuova *entita'* ha delle *caratteristiche* che *agevolano* la risoluzione di problemi che richiedono *alta cooperazione* e *condivisione di risorse*.
Sono piu' indicata per realizzare *"attivita'"* piuttosto che *compiti singoli*. 

