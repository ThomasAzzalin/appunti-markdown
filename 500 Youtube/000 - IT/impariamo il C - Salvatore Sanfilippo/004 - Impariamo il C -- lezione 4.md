## Video
[link](https://www.youtube.com/watch?v=YNsXyasn4R4)
data pubblicazione: 07.06.2025
data visione: 30.06.2025
voto: ??
Topics: #IT #C

---

```table-of-contents
style: inlineFirstLevel # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
```

---

## I tipi in C
In *C* i tipi numeri **Non sono consistenti** tra i vari sistemi
Ad esempio per la tipologia *int* non viene specificato se sara' un numero a 32/16/64 bit, questo dipende da sistema a sistema.

### Come fare a capire la grandezza?
Se vogliamo capire nel nostro sistema quanto e' grande il valore rappresentabile con un tipo numerico utilizzeremo la funzione **sizeof(name_var)**.
```c
int z = 5;
printf("In this system int is %lu bytes", sizeof(z));
```

### Perche?
Perche' *C* nasceva con l'intenzione di essere compatibile con qualsiasi sistema; ad esempio esistevano compilatori anche per processori ad **8 bit**.
Ovviamente processori che hanno meno potenza computazionale andrebbero  in *tilt* se la grandezza delle varie variabili numeriche fosse stata decisa a priori nella documentazione.

### Oggi giorno
Anche se *C*, come abbiamo detto, non garantisce una grandezza "sicura" per i vari tipi, oggi giorno esistono degli **standard** che vengono rispettati nel 99% dei casi nei sistemi a *32* e *64* bit.
Alcune tipologie di dati e la oro grandezza comune:

- char -> 8 bit/1byte
- short  -> 16bit/2bytes
- int -> 32bit/4bytes
- long -> situazione particolare, ha la grandezza delle *word* che il processore usa

## Parsing
Mettendo tra parentesi un *tipo* prima di qualsiasi espressione converte quello che e' a destra nella tipologia specificata tra parentesi.
```c
(int) sizeof(z);
```
Normalmente la funzone *sizeof()* restituisce un *int lungo unsigned* (lu).

## <limits.h>
La libreria  `<limits.h>` importa delle variabili che contengono i valori massimi che le variabili possono contenere in quel determinato sistema.
```c
printf("int min: %d int max: %d\n",INT_MIN, INT_MAX);
```
> int min: -2147483648 int max: 2147483647 

## <stdint.h>
Il linguaggio C, a partire dallo standard **C99**, ha introdotto una libreria chiamata `<stdint.h>`, che definisce tipi interi con **dimensioni garantite e comportamenti portabili** tra architetture diverse.
```c
#include <stdint.h>
```

### int8_t, int16_t, int32_t, int64_t
Sono tipi **interi con segno** a larghezza fissa.  
Garantiscono di avere esattamente 8, 16, 32 o 64 bit, ovunque il codice venga compilato.

### uint8_t, uint16_t, uint32_t, uint64_t
Sono la **versione senza segno** dei precedenti.  
Vengono usati quando si vuole sfruttare **tutto il range positivo** dei bit.

### intptr_t
Tipo intero **con segno** in grado di contenere un **puntatore**.  
Serve per **convertire puntatori in interi** in modo sicuro.
È garantito che `intptr_t` sia **abbastanza grande** per contenere l'indirizzo di memoria di qualsiasi puntatore.

### uintptr_t
Stessa cosa di `intptr_t`, ma **senza segno**.  
Utile quando si vuole fare aritmetica sugli indirizzi in modo _modulare_ e **senza segni negativi**.

## Parole chiave
>

## Domande
>