## Video
[link](https://www.youtube.com/watch?v=HjXBXBgfKyk&t)
data pubblicazione: 18.05.2025
data visione: 30.05.2025
voto: 8.5
Topics: #IT #C 

## Riassunto
Il video introduce il linguaggio C partendo dalla sua natura storica e strutturale. Spiega come, nonostante sia un linguaggio "vecchio", sia ancora oggi fondamentale per capire come funzionano davvero i linguaggi di programmazione e i computer.  
Viene mostrato un semplice esempio di _Hello World_ e si passa all’analisi dell’output assembly del programma, per evidenziare come i compilatori ottimizzano il codice.  
Si riflette anche sull'importanza della _forma mentis_ che il C aiuta a costruire per affrontare problemi in altri linguaggi.

## Contenuto
### Informazioni riguardo il linguaggio C
È un _linguaggio vecchio_, ma la sua _sintassi_ e la _libreria di base_ non si sono evolute molto nel tempo; al contrario, c'è stata una grande _evoluzione nei compilatori_ e nelle _assunzioni_ che essi possono fare sulla macchina su cui il programma verrà eseguito (es. modello di memoria, dimensioni dei tipi, endianess, ecc).

È un _linguaggio semplice da imparare_, ma _complesso da applicare_.  
Le idee vanno assorbite completamente; va allenata la mente per riuscire, dato un problema, a costruire uno schema mentale per risolverlo. Questa abilità è trasferibile anche ad altri linguaggi.

È un linguaggio _compilato_.  
Ha come estensione _.c_
### Hello world
> [!Example] Esempio
> Esempio di un programma molto semplice
>```c
>#include <stdio.h>
>
>int main(void) {
>	printf("Hello world\n");
>	return 0;
>}
>```

Per eseguire il programma è necessario prima compilarlo, utilizzando un compilatore (spesso scritto in C). Uno dei più famosi è il **GCC**.  
Una volta compilato, il programma viene trasformato in un file eseguibile con estensione _.out_

```bash
cc hello_world.c
```

### Assembly
Scrivendo:
```bash
cc -S hello_world.c
```
fermiamo la compilazione alla traduzione in _linguaggio assembly_.

Questo perché in base a come viene chiamato il comando `cc` (che spesso è un alias per `gcc`) vengono applicati diversi livelli di ottimizzazione, e possiamo vedere la differenza analizzando l'output assembly.

Ad esempio:
```bash
cc -o2 -S hello_world.c
```
Nel file assembly generato si può notare che non viene più chiamata la funzione _printf_, ma bensì _puts_.  
Questo perché, grazie al livello di ottimizzazione `-O2`, il compilatore ha capito che non aveva senso usare una funzione complessa come _printf_ (che fa il parsing della stringa) per un caso semplice, dove _puts_ è sufficiente.

### Scomponiamo il programma
```c
#include <stdio.h>

int main(void) {
	printf("Hello world\n");
	return 0;
}
```

Le _direttive_ del preprocessore iniziano con `#`.  
Ad esempio `#include` significa: _prendi il contenuto del file stdio.h (file di libreria) e inseriscilo prima del contenuto del programma stesso_.  
L'estensione `.h` sta per _header_.
## Parole chiave
- linguaggio compilato
- direttive del preprocessore
- `#include`
- `stdio.h`
- `main(void)`
- `printf` / `puts`
- compilatore (`gcc`, `cc`)
- `.c` / `.out`
- ottimizzazione (`-O2`)
- assembly (`.s`)