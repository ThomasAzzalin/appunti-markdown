## Video
[link](https://www.youtube.com/watch?v=mw4gUqsGPZw)
data pubblicazione: 31.05.2025
data visione: 09.06.2025
voto: ?
Topics: #IT #C 

---

```table-of-contents
style: inlineFirstLevel # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
```

---

## Variabili globali
Le variabili globali vengono dichiarate **fuori da ogni funzione**.  
Restano in memoria per **tutta la durata del programma** e sono accessibili da **qualsiasi punto del codice**.
```c
#include <stdio.h>

int x = 0;

void incr(void){
    x = x + 1;
    printf("%d\n", x);
}
int main(void){
    incr();
    incr();
    return 0;
}
```
Stamperà prima _1_, poi _2_.

## Variabili globali static
Le variabili dichiarate con `static` **fuori da ogni funzione** sono **globali per durata**, ma **locali per visibilità**:  
non sono visibili al di fuori del file in cui sono definite.

Una variabile dichiarata `static` **dentro una funzione** mantiene il suo valore **tra chiamate successive**, ma **non è visibile all'esterno**.
```c
#include <stdio.h>

void incr(void){
    static int x = 0;
	x = x + 1;
	printf("%d\n", x);
}
int main(void){
	incr();
	incr();
	return 0;
}
```
La variabile `x` non è accessibile da `main`, ma **mantiene il suo valore** tra una chiamata e l’altra.  
Stampa 1 e poi 2.

## Problemi con le variabili globali
Non sono sicure in ambienti **multithreading**, perché possono essere modificate da più thread contemporaneamente.  
Questo può causare **problemi di sincronizzazione**.

## Passaggio per valore
In C, **le variabili vengono passate per valore**: la funzione lavora su una **copia** della variabile.
```c
#include <stdio.h>

int incr(int x){
	x = x + 1;
	return x;
}
int main(void){
	int a = 10;
	incr(a);
	printf("%d\n", a)
	return 0;
}
```
Stampa 10, perché la funzione ha modificato **solo una copia**, non la variabile `a` originale.

## Argomenti passati per riferimento
In C, il **passaggio per riferimento** si ottiene **solo tramite puntatori**.  
Permette di modificare direttamente il valore della variabile passata.

---

## Tipi primitivi -> Float
È un tipo a virgola mobile **a 32 bit**.
```c
float f = 23.56;

printf("%f\n", f);
```

## Tipi primitivi -> double
È un tipo a virgola mobile **a 64 bit**, quindi più preciso di `float`.

## Tipi primitivi -> char
Rappresenta 1 byte e può contenere **valori ASCII**.
```c
char c = 'g';
```

### Varianti:
- `unsigned char`: da 0 a 255
- `signed char`: da -128 a 127

## Tipi primitivi -> short
Occupa 2 byte.  
Utile per risparmiare memoria quando si lavora con **numeri piccoli**.

## Tipi primitivi -> int
Tipo intero **con segno**, il tipo intero standard in C.
```c
int x = 5;
printf("%d\n", x);
```

## Tipi primitivi -> unsigned int
Rappresenta **solo numeri positivi**.
```c
unsigned int i = 14;
```

## Sistema di promozione automatica
In alcune situazioni, i tipi vengono **convertiti automaticamente** dal compilatore.  
Succede in:
- espressioni aritmetiche
- ritorni di funzione
- parametri di funzioni variadiche (es. `printf`)

Esempi:
- `float → double`
- `short → int`

## C è pericoloso #1
```c
int x = 4;
float fl = 13.58;
printf("%d %f\n", fl, x);
```
L'ordine tra variabili e specificatori è **sbagliato**.  
Il compilatore mostra **solo un warning**, ma il comportamento è imprevedibile.

## C e' pericoloso #2
```c
short x = 128;
printf("%d\n", x);
```
Uscita: `-128`.  
Perché? Il valore massimo per uno `short` signed è 127.  
Oltre quel limite si verifica **Undefined Behavior (UB)**.

## Undefined Behavior
Con tipi **signed**, l’overflow porta a **comportamenti imprevedibili**.  
Con tipi **unsigned**, invece, il comportamento è definito: il valore **riparte da 0**.

## Perché tanti tipi?
Negli anni '60 la memoria era **molto costosa**.  
Il C è stato progettato per offrire **tipi di dimensioni diverse** per **evitare sprechi**.

## Domande
>Cosa succede se dichiaro una variabile `static` dentro una funzione?  
Perché in C i parametri vengono passati per valore?  
Cosa significa "undefined behavior"?  
Qual è la differenza tra `float` e `double`?  
Perché servono tanti tipi primitivi in C?  
Come si fa il passaggio per riferimento in C?

## Parole chiave
>variabili globali  
static  
puntatori  
passaggio per valore  
float  
signed / unsigned  
overflow  
undefined behavior  
promozione automatica