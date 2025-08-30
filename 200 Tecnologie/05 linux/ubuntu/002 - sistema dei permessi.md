![[002 -excalidraw- sistema dei permessi]]
## Utenti, gruppi e propieta'
**Concetto fondamentale**: ogni file appartiene a qualcuno.
Ogni file nel sistema ha *2* propietari:
- un *utente*
- un *gruppo*

Di solito l'*utente propietario* e' quello che ha creato il file, mentre il *gruppo* rappresenta un insieme di utenti che condividono determinati privilegi.
Quando crei un file, diventi automaticamente il suo propietario *utente*, e il tuo *gruppo primario* diventa il *gruppo propietario*. 

Questo doppio sistema di doppia propieta' e' geniale perche' permette la condivisione di file facilmente.

## La tripartizione dei permessi
*Unix* divide il mondo in 3 categorie per ogni file:
- *owner*
- *group*
- *world*, cioe' tutti gli altri

Per ogni categoria *unix* definisce esattamente *tre* tipi di permessi:
- *read*
- *write*
- *execute*

Questi permessi hanno significati diversi a seconda se stiamo parlando di *file* o di *directory*.

## Permessi sui file
Tutti questi *permessi* sono *indipendenti fra di loro*.
Potresti avere un file che puoi leggere ma non modificare, o un file che puoi eseguire ma non leggere e/o modificare.

- *Read* -> Permette di aprire e visualizzare il contentuo del file. 
- *Write* -> Permette di aprire e modificare il file, sovrascrivere o cancellare il contenuto.
- *Execute* -> Indica che il file puo' essere lanciato come *programma* o *script*.

## Permessi sulle directory
Le *directory* seguono regole diverse, che possono magari inizialmente confondere, ma seguono una logica ben precisa.

- *Read* -> La lettura su una directory ti permette di poter vedere il suo contenuto, cioe' i file al suo interno.
- *Write* -> Questo permesso ti permette di *creare*, *eliminare* o *rinominare* file all'interno di una directory. MA NON DI MODIFICARE IL CONTENUTO DEI FILE STESSI.
- *Execute* -> Da il diritto di "attraversare" la *directory*, cioe' di usarla come parte di un percorso per raggiungere file che si trovano piu' in *profondita'*.


Potresti avere il diritto di *execute* ma non di *lettura*. Quindi se conosci il nome esatto di un file lo potresti raggiungere, ma non vedere tutti i file che sono all'interno della stessa directory.

## Rappresentazione simbolica e numerica
*Unix* rappresenta questi permessi in due modi.

### Rappresentazione simbolica
La *rappresentazione simbolica* utilizza 9 caratteri, e ogni *terzetto* segue lo schema *read-write-execute* (**RWE**).:
- primi 3 per il propietario
- successivi 3 per il gruppo
- ultimi 3 per gli altri

Ad esempio un file con permessi *rwxr--r--* significa:
- puo' essere letto modificato ed eseguito dall'owner
- letto dal gruppo
- letto da tutti gli altri

### Notazione numerica
La *notazione numerica ottale* comprime il tutto in *3 cifre*, ogni cifra rappresenta una delle tre categorie (*owner*, *group* e *world*). 
Ogni cifra e' la somma di valori: 
- *4* -> *Read*
- *2* -> *Write*
- *1* -> *Execute*

Ad esempio un file con permessi *755* significa:
- il *propietario* puo' *leggere*, *scrivere* ed *eseguirlo* (4 + 2 + 1)
- Il *gruppo* puo' *leggere* ed *eseguire* (4 + 1)
- tutti *gli altri* possono *leggere* ed *eseguire* (4 + 1)

## Come modificare questi permessi
Esistono diversi Comandi che ci permettono di modificare quello di cui abbiamo parlato fino ad ora.
Il piu' famoso e semplice e' il comando *chmod* che permette di cambiare i permessi (utilizzando la rappresentazione numerica).
*chown* cambia il propietario;
*chgrp* cambia il gruppo.