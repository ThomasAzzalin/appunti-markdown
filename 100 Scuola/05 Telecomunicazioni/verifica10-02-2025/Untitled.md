## Descrivi le tensioni in ingresso negli integrati
Non possiamo assegnare lo 0 logico a 0V e l'1 logico al Vcc perche' basterebbe un piccolo disturbo per provocare il malfunzionamento della porta.
Per questo si utilizzano dei *range di tensione* per riconoscere lo 0 e l'1 logico.
### Range -> ingresso TTL compatibile
#### Range di tensione per 1 logico
Il range di tensione che viene riconosciuto come *1 logico* e' compreso fra Vcc e ViHmin.
cio' va dal Vcc al 2V .

#### Range di tensione per 0 logico
Il range di tensione che viene riconosciuto come *0 logico* e' compreso fra 0V e Vilmax.
cio' va da 0V a 0.8V .

#### Range di tensione tra VilMax & ViHmin
In questo range di tensione il costruttore non garantisce l'esatto valore che verra' rilevato.

## Classificazioni porte logiche
### Numero di porte logiche:
- IC SSI (Small Scale Integration) < 12 porte
- IC MSI (Medium Scale Integration) < 100 porte
- IC LSI (Large Scale Integration) < 1000 porte
- IC VLSI (Very Large Scale Integration) > 1000 porte

### Tecnologia utilizzata
- integrati Bipolari:
	- TTL (Transistor-Transistor Logic) -> 
- integrati Monopolari:
	- CMOS (Complementary MOS) -> maggiore immunita' al rumore, meno consumo


## Ingresso a Trigger
Alcune porte hanno un'ingresso dotato di *isteria*, cioe' e' in grado di capire se il segnale in ingresso sta *aumentando* oppure *diminuendo*.
Cioe' il suo *1 logico* e' presente quando il segnale in ingresso si trova nel *fronte di salita*, e lo *0 logico* quando e' nel *fronte di discesa*.

## Differenza reti combinatorie & sequenziali
Le reti *combinatorie* sono reti che per produrre un output prendono in considerazione solo l'input che viene rilevato in un preciso momento.
Le piu' famose *reti combinatorie* sono:
- *multiplexer*
- *demultiplexer*
- *encoder*
- *decoder*

Le reti *sequenziali* utilizzano sia gli input correnti che lo stato precedente del sistema, si dice quindi che hanno una *memoria* interna.
Le piu' famose *reti sequenziali* sono:
- *Latch*
- *Flip-flop*

## Multiplexer
Il *multiplexer* e' una *rete combinatoria*, cioe' non ha una memoria interna.
Ha *piu' ingressi* e permette di far arrivare all'uscita solo il segnale presente sull'ingresso selezionato, utilizzando una *combinazione binaria* applicata agli *ingressi di selezione*
### Funzionamento multiplexer 4/1
![[Pasted image 20250209164834.png]]
Questo multiplexer ha:
- *4 ingressi di segnale (In)*
- *2 ingressi di selezione (Sn)*
- *1 uscita (Y)*

![[Pasted image 20250209165007.png]]
![[Pasted image 20250209165030.png]]

### Demultiplexer
Questa *rete combinatoria* e' il contrario del *multiplexer*, presenta un solo *ingresso* e piu *uscite*, in base alla combinazione binaria che generiamo inserendo i valori negli *ingressi di selezione* decidiamo in quale uscita mandare il segnale.

 ![[Pasted image 20250209165242.png]]
 
 ![[Pasted image 20250209165248.png]]
### Encoder
Per passare da un codice ad un'altro.
Hanno *piu' ingressi* che generano in uscita il codice relativo all'ingresso attivo.
Se il numero di ingressi e' *N* il numero di uscite sara' *M*, per cui *$2^M>=N*
![[Pasted image 20250209165606.png]]