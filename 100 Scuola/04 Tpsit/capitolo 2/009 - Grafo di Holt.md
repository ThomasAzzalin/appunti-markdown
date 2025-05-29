## Cos'e' il grafo di Holt (o grafo delle attese)
Il **grafo di Holt** e' un sistema di rappresentazione dell'allocazione delle risorse ai processi.
Viene anche chiamato **grafo delle attesse**. Esso permette di rappresentare tutte le situazioni in cui un *processo* e le sue *richieste* di *risorsa* si possono trovare.

### A cosa e' utile il grafo di Holt
Il *grafo di Holt* e' molto utile per scovare *situazioni critiche* che si possono venire a creare fra *processi* e *risorse*

### Gli elementi di un grafo di Holt
Un *grafo di Holt* e' composto da *2 insieme*, rappresentati da *nodi*, e da *archi orientati*. Piu' nello specifico:
- I *nodi* di forma *circolare* rappresentano i *processi*
- I *nodi* di forma *quadrata* rappresentano le *risorse* 
	- mentre i *nodi* di forma *rettangolare* rappresentano una *classe di risorsa*, oppure per *piu' istanze* della medesima classe. In questo caso, per *ogni istanza* aggiungeremo *un pallino nero* all'interno del rettangolo
- Gli *archi* invece sono *orientati*; possono *collegare* solo elementi che fanno parte di *2 sottoinsieme differenti*:
	- Se un arco *parte da una risorsa e finisce su un processo*, vuol dire che quella *risorsa* e' **assegnata** al *processo*.
	- Se invece un arco *parte da un processo e finisce su una risorsa*, allora la *risorsa* e' stata solamente **richiesta** dal *processo*, ma *non e'* ancora *assegnata*.

#### Esempio di grafo con immagine
![[Pasted image 20241216212522.png#center]]
Ad esempio in questa immagine abbiamo:
- Una risorsa *R1* con una sola istanza 
- Una risorsa *R2* con due istanze
- Un processo *P1*
- Un processo *P2*

Le interazioni tra questi elementi sono:
- La risorsa *R1* e' **assegnata** al procesos *P1*
- Un'istanze della classe *R2* viene **assegnata** a *P1*
- Un'istanza della classe *R2* e' **assegnata** al processo *P2*
- Il processo *P2* **richiede** la risorsa *R1* che pero' *non e' disponibile* (arco rosso)


### Caratteristiche di un grafo di Holt
Grazie agli elementi che caratterizzano un *grafo di Holt* di cui abbiamo parlato precedentemente possiamo determinare alcune caratteristiche che ogni grafo delle attese ha:
- **Grafo orientato diretto (directed graph)**, cioe' gli archi hanno una sola direzione
- **Grafo partito**, perche' gli archi non possono collegare elementi dello stesso sottoinsieme (risorsa con risorsa & processo con processo)

## Riducibilita' di un grafo di Holt
Spesso abbiamo bisogno di vedere la situazione tra processi e risorse spostata in avanti nel tempo; per fare cio' ci basta trasformare il *grafo di Holt* in un *grafo ridotto*.
### Grafo ridotto
In un *grafo ridotto* vengono *tolte* tutte le situazioni in cui un *processo* e' gia' *in grado di evolvere* perche' tutte le *risorse* che gli servono gli sono gia' state assegnate. 

### Concetto alla base dei grafi ridotti
Possiamo creare i *grafi ridotti* perche' supponiamo che il *processo* che ha gia' tutte le *risorse* che necessita per *evolvere*, prima o poi *terminera'* e quando questo succedera' *rilesciera' le risorse* che stava utilizzando.
E quindi non rappresenta un'ostacolo per i *processi* che **necessitano** di quelle *risorse* e le stanno **aspettando**.

### Differenze fra grafo di Holt e grafo ridotto graficamente
Graficamente parlando, per creare un *grafo ridotto* partendo da un *grafo di Holt* ci basta togliere qualsiasi *processo* che *presenta SOLO archi entranti*, e nessun arco uscente.

> [!NOTE] Definizione grafo riducibile
> Un *grafo di Holt* si dice *riducibile* se esiste almeno un *nodo* di tipo *processo* con *solo archi entranti*

#### Esempio di riduzione di un grafico
![[Pasted image 20241216221018.png#center]]