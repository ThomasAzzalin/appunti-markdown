## Risorse condivise da piu' processi
Come abbiamo detto prima, succede molto spesso che due o piu' *processi* necessitino di una *risorsa* che e' presente nel sistema in quantita' limitata, e che quindi va condivisa.
Percio' e' necessario stabilire delle *regole* di *assegnazione*, e di *gestione* delle risorse.
Per poter decidere a chi e secondo quali criteri vada assegnata una *risorsa condivisa*.

### Caratteristica secondaria delle risorse condivise
Condividendo una *risorsa* tra piu' *processi* si possono inoltre **scambiare informazioni**.
#### Esempio
Ad esempio se due *processi* stanno condividendo una stessa area di memoria dove sono definite determinate variabili, allora se il processo A apporta delle modifiche, e poi la risorsa viene data al processo B quest'ultimo vedra' le modifiche apportate.
In questo modo due processi possono *cooperare* tra di loro.

## Natura delle risorse
Le risorse possono essere divise in due *macro* categorie:
- *Risorse* di natura **statica** 
- *Risorse* di natura **dinamina**
Questa suddivisione e' importante per la loro gestione da parte del *SO*, che svolgera' delle operazione per una tipologia di *risorsa* e non per l'altra.

### Risorse di natura statica
Quando abbiamo a che fare con una *risorsa* di natura *statica*, il *SO* dovra' pianificarne la sua assegnazione per garantiere un *uso efficiente* della risorsa stessa. 
Durante questo processo il *SO* dovra' svolgere alcune operazioni, tra cui:
- *Allocazione*, cioe' l'assegnazione vera e propria della *risorsa* ad un *processo*
- *Disponibilita'*, il *SO* deve prima controllare di avere un'*istanza* della classe disponibile
- *Costo*, Cioe' il prezzo computazionale che il sitema deve affrontare per assegnare una risorsa

### Risorse di natura dinamica
Quando abbiamo a che fare con una *risorsa* di natura *dinamica*, stiamo parlando di risorse che possono essere:
- *Create*
- *Modificate*
- *Allocate*
- *Liberate*
Anche mentre il processo e' in esecuzione.
Per gestire correttamente questo tipo di *risorse* il *SO* deve svolgere alcune operazione specifiche come:
- *Ottimizzazione*, cioe' gestire e allocare in modo efficiente le risorse dinamiche per massimizzare le prestazioni e minimizzare i costi
- *Autenticazione*, cioe' controllare che l'*entita'* che sta richiedendo la *risorsa* sia autorizzato ad utilizzarla e a manipolarla.
- *Controllo di correttezza delle operazioni ed eccezioni*, il *SO* deve controllare che le operazioni che il processo sta svolgendo sulla risorsa e' corretto e autorizzato.

## Cosa fa il SO per ogni risorsa
Il *SO* mette a disposizione per ogni *risorsa*:
- **Gestore** della risorsa, un programma che ne regola l'utilizzo corretto, le suo funzioni principali sono:
	- **Allocare** la risorsa
	- **Rilasciare** la risorsa
	- **Utilizzare correttamente** la risorsa, evitando conflitti o abusi
- **Protocollo di accesso** alla risorsa, definisce le regole e le procedure che un *processo* deve seguire per accedere ad una *risorsa*.



