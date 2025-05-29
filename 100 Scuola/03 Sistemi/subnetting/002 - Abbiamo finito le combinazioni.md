link: [youtube video](https://youtu.be/tcae4TSSMo8?si=4CMILbfu4_6QnWl_)

## Struttura degli indirizzi IPv4, Classi
Come abbiamo gia' detto, gli *indirizzi IPv4* sono formati da 4 *ottetti* divisi da 3 *punti*.

Pero' vi e' anche un'altra caratteristica che abbiamo solo accennato e cioe' che vi e' una procedura che regola il compito dei vari *ottetti*, utlizzando una suddivione in **classi** delle *Net Mask*.

## Come nasce la suddivisione in classi? Quante classi esistono?
Quando nacque il *protocollo IPv4* i loro creatori pensarono che sarebbe stato piu' intelligente creare una *suddivisione* che avrebbe semplificato la *creazione di reti*, e l'*assegnazione di indirizzi* alle varie aziende.
Nacquero quindi le **Classi di Indirizzo**:
Dalla *classe* **A** alla *classe* **E**. 
$5$ classi.

## Che cosa differenzia una classe da un'altra?
La differenza tra due *classi*, e' il numero di *host* che si possono avere in ogni *rete*, ed il range dei vari *ottetti* che si possono utilizzare.
Maggiore e' il numero di *host* che puo' contenere una singola rete, minori saranno le reti che si potranno creare utilizzando quella specifica *classe*.

Adesso potrebbe sembrare complicato capire, ma piu' avanti con gli esempi risultera' tutto piu' semplice.

## I range di indirizzi e le Net Mask delle varie classi
| classe | range decimale              | Net Mask      | 
| ------ | --------------------------- | ------------- |
| A      | 1.0.0.0 - 126.255.255.255   | 255.0.0.0     |
| B      | 128.0.0.0 - 191.255.0.0     | 255.255.0.0   |
| C      | 192.0.0.0 - 223.255.255.0   | 255.255.255.0 |
| D      | 224.0.0.0 - 239.255.255.255 |               |
| E      | 240.0.0.0 - 255.255.255.255 |               |

## Entriamo piu' nello specifico delle varie classi!
### Classe A
Gli indirizzi di Classe A sono progettati per *reti molto grandi*. 
In un indirizzo di Classe A, il primo *ottetto* dell'indirizzo indica il *Net ID* e i restanti tre *ottetti* sono per gli *host*. 

Inoltre, anche se non lo vediamo dalla tabella sopra, in questa classe il primo **bit** del primo *ottetto* deve essere per forza *zero*, per indicare che l'indirizzo IPv4 e' di classe A.

| Range binario                                                             | Classe   |
| ------------------------------------------------------------------------- | -------- |
| 00000000.00000000.00000000.00000000 - *0*1111111.11111111.11111111.11111111 | Classe A | 

Quindi il numero di reti di *classe A* che possono esistere all'interno di tutto *internet* e' *$126$* .
Mentre in ogni *rete* di *classe A* possono esistere *$16$ $milioni$*  di *host*.


### Tra classe A e classe B, gli indirizzi di loopback
Tra la *classe A* e la *classe B* notiamo che saltiamo dall' indirizzo *$126$*.x.y.z al *$128$*.x.y.z
gli indirizzi che iniziano con **$127$** sono i cosiddetti **indirizzi di loopback**. 

Cio' significa che ogni *host* ha al suo interno *$16$ $milioni$*  di **indirizzi virtuali**, che vengono utilizzati per:
- *test locali*: Per verificare che i vari servizi locali funzionino
- *Isolamento*: I pacchetti inviati ad indirizzi che cominciano con *127* non escono dall'*host*
- *Sviluppo & Debug*: Si possono simulare server e servizi in locale sugli *host*.

Sono tutte funzioni importanti, ma non servivano *$16$ $milioni$*  di indirizzi per fare cio'. Ne sarebbero bastati anche solo un centinaio, esagerando.

Ad esempio [[801 - ping, ICMP|pingando]] l' indirizzo *$127$*$.0.0.1$ riceveremmo la seguente risposta:
![[Pasted image 20241018173323.png]]
Che e' la stessa che riceveremmo anche se utilizzassimo un qualsiasi altro indirizzo che inizia con 127:
![[Pasted image 20241018173359.png]]

### Classe B
Gli indirizzi di *Classe B* sono progettati per *reti mediamente grandi*.
In un indirizzo di *Classe B*, i primi due *ottetti* dell'indirizzo servono per il *Net ID*e i restanti due *ottetti* sono per gli *host*. 

### Classe C
Gli indirizzi di *Classe C* sono progettati per *reti piccole*.
In un indirizzo di *Classe C*, i primi tre *ottetti* dell'indirizzo servono per il *Net ID* e solo l'ultimo *ottetto* indica gli *host*. 

### Classe D
Gli indirizzi di *Classe D* sono progettati per il *multi-casting*.

### Classe E
Gli indirizzi di *Classe E* sono progettati per *usi sperimentali*.





