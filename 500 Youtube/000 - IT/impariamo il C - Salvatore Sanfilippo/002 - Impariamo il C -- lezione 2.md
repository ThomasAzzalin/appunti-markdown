## Video
[link](https://www.youtube.com/watch?v=Z84vlG1RRtg)
data pubblicazione: 22.05.2025
data visione: 08.06.2025
voto: 8
Topics: #IT #C 


## Riassunto
Il video tratta aspetti fondamentali del linguaggio C, con particolare attenzione alla logica dei valori booleani in Unix, alla gestione delle funzioni, alle variabili e alle peculiarità di questo linguaggio compilato e fortemente tipato. Vengono inoltre illustrate le funzioni variadiche e le convenzioni sul valore di ritorno del programma.
## Contenuto

### Vero e falso in Unix
Nei sistemi Unix, l’exit status 0 indica **successo** (cioè un risultato positivo), mentre qualsiasi valore diverso da 0 indica un errore o un fallimento.  
Questa convenzione è diversa dalla logica booleana del linguaggio C, dove **0 è false** e ogni valore diverso da zero è true.
 
### stdio.h
All’interno di questa libreria sono contenute le istruzioni standard per l’Input e l’Output.

### Funzione test
```c
#include <stdio.h>

int sum(int a, int b) {
	return a + b;
}
```
- `int` è il tipo del valore di ritorno della funzione.
- `sum` è il nome della funzione.
- `(int a, int b)` sono gli argomenti di input, in questo caso due valori interi.

### Espressioni
In C, alcune istruzioni accettano espressioni.  
Ad esempio, `return` accetta un’espressione:
```c
return a+b;
```

Anche durante l’inizializzazione delle variabili:
```c
int a = 10 + 5;
```

### printf
Acronimo di _Print Formatted_; stampa elementi in modo formattato.  
È una funzione **variadica**, cioè accetta un numero indefinito di parametri.  
Il primo parametro è la stringa di formato, che definisce come vengono stampati i valori successivi.  
Esempio:
```c
printf("Hello World %d \n", 55);
```

### Funzioni variadiche
Sono funzioni che accettano un numero indefinito di argomenti, come ad esempio `printf()`.

### funzione main()
È una funzione speciale che non deve essere chiamata esplicitamente.  
È il punto di partenza del programma quando viene compilato.  
Deve essere presente in ogni programma, altrimenti si verifica un errore di compilazione.  
Questa funzione restituisce un valore intero (`int`), che indica al sistema operativo se il programma è terminato con successo o meno.  
Generalmente, se ritorna `0` significa che ha avuto successo, valori diversi possono indicare errori.

### Scrivere codice fuori dalle funzioni
In C non è possibile scrivere codice eseguibile all’esterno delle funzioni.  
Solo **direttive** del preprocessore e **variabili globali** sono ammesse fuori dalle funzioni.

### Warning
Sono avvertimenti che il compilatore mostra alla fine della compilazione.  
Non impediscono il funzionamento del programma, ma segnalano che potrebbero esserci pratiche non consigliate o potenziali problemi.

### C è un linguaggio fortemente tipato
Bisogna dichiarare sempre il tipo delle variabili.

### Variabili, inizializzazione e assegnazione
In C, inizializzare una variabile significa dichiararla con un tipo:
```c
int a, b, c;
```
Qui sono state dichiarate tre variabili intere. 

L’assegnazione dei valori è separata:
```c
a = 10;
b = 23;
c = 5;
```

È possibile fare entrambe le cose insieme:
```c
int z = 50;
```

### variabili locali
Le variabili sono _locali_, cioè accessibili solo all’interno dello _scope_ dove sono dichiarate:
```c
#include <stdio.h>

int sum(int a, int b) {
	int g = a + b;
    return g;
}

int main(void){
    printf("Ciao: %d\n", sum(10, 20));
    return 0;
}
```
In questo esempio, se si prova a usare la variabile `g` nella funzione `main`, si otterrà un errore perché `g` non è visibile fuori dalla funzione `sum`.  
Le variabili locali esistono solo per la durata dell’esecuzione della funzione.

#### Comportamento delle variabili nell’esempio precedente
- Quando la funzione `sum` viene chiamata nel `main`, vengono inizializzate 3 variabili: `a`, `b` e `g`.
- Ad `a` e `b` vengono assegnati i valori passati come argomenti (10 e 20).
- A `g` viene assegnato il risultato dell’espressione `a + b`.
- Quando la funzione termina, cioè restituisce `g`, tutte e tre le variabili vengono distrutte.

### Come vedere il valore in uscita da main
Per vedere l’exit status del programma nel terminale Unix, si usa:
```bash
echo $?
```
La variabile speciale `$?` contiene l’exit status dell’ultimo programma eseguito.

### Concatenazione comandi Unix
È possibile concatenare comandi nella shell Unix con i seguenti simboli:
- `&&` → esegui il secondo comando solo se il primo ha avuto successo (exit status 0)
- `||` → esegui il secondo comando solo se il primo ha fallito (exit status diverso da 0)
- `&` → esegui i comandi in parallelo (in background)
- `;` → esegui il secondo comando subito dopo il primo, indipendentemente dal successo o fallimento

Esempio:
```bash
./a.out && ls
```
In questo caso, se il programma `a.out` restituisce exit status 0 (successo), verrà stampato il contenuto della cartella corrente con `ls`.


`