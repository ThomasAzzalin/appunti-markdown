link: [youtube video](https://youtu.be/oZGZRtaGyG8?si=T-XBCZ2LN2vNle0m)

## Cos'e' una subnet mask?
La **net mask** e' composta da 4 *ottetti* e 3 *punti*.
Ogni ottetto della *net mask* e' legato ad un'*ottetto* dell' *indirizzo IP*.

Ad esempio un'*indirizzo IPv4* in *classe C* avra' la seguente *net mask*
In *decimale*:

| ottetto 1 | ottetto 2 | ottetto 3 | ottetto 4 |
| --------- | --------- | --------- | --------- |
| 192       | 168       | 1         | 21        |
| 255       | 255       | 255       | 0         | 

In *binario*:

| ottetto 1 | ottetto 2 | ottetto 3 | ottetto 4 |
| --------- | --------- | --------- | --------- |
| 11000000  | 10101000  | 00000001  | 00010101  |
| 11111111  | 11111111  | 11111111  | 00000000  | 

Quando l'ottetto della *net mask* e' composto da *$11111111$* vuol dire che l'*ottetto* corrispondente nell' *indirizzo IP* e' un' ottetto di **net id (network)**.

Invece gli *ottetti* dell'*indirizzo IP* associati agli *ottetti* della *net mask* che contengono solo *$0$*, vengono chiamati *ottetto* di **host**. 

> [!warning]-
> Piu' avanti vedremo che in realta' non tutto l'*ottetto* nell'*indirizzo IP* e' occupato da  *host* *bit* o da *net id* *bit*. 

## Perche' e' importante conoscere questa cosa?
Per ora abbiamo utilizzato una classificazione di *indirizzi IP* per *classi*, chiamata anche **classful**.
In questa situazione sapere che i *bit* con valore *$1$* sono associati ai *net id* e che i *bit* con valore di *$0$* sono associati agli *host* non ci serve quasi nulla.

Ma adesso spiegeremo un altro metodo di classificazione chiamato **classless**, e queste nozioni ci torneranno indispensabili.
 

## Perche' passare dal metodo classful a quello classless?
Ipotizziamo di avere un' *indirizzo IP* di *classe C*, ma vorremmo avere $500$ *host* in ogni rete.
Seguendo la classificazione *classful* dovremmo passare alla classe successiva, cioe' la *classe B*.
Ma sappiamo che in questa classe il numero di *host* per ogni rete e' *$65$* mila, quindi vi sarebbe uno *spreco* enorme di indirizzi.

Per questo la cosa migliore da fare e' utilizzare la classificazione *classless*.

Se necessitiamo di piu *host* per ogni sottorete dovremo sottrarre dei *bit* con valore di *$1$* e trasformarli in *bit* con valore di *$0$* dalla *net mask*.

#### Esempio con 500 host per sottorete
Nell'esempio presentato prima la nostra *default net mask* e' la seguente:
$$255.255.255.0$$
in *binario*:
$$11111111.11111111.11111111.00000000$$

**Trasformando** un *bit* con valore di *$1$* in un *bit* con valore di *$0$* ci troveremmo in questa situazione:
$$11111111.11111111.11111110.00000000$$

Ora ci basta **contare** quanti *$0$* abbiamo nella nostra *net mask* e utilizzare questo numero come *esponente* da mettere al numero $2$, il risultato di questo calcolo sara' il numero di *host* disponibili per ogni *rete*.
Nel nostro caso:
$$2^9 = 512$$
Quindi abbiamo $512$ *host* disponibili per ogni rete, che e' maggiore del numero che serviva a noi. 
Ma e' un margine di eccesso ammissibile.

Adesso ritrasformiamo la nostra *net mask* in *decimale*:
$$255.255.254.0$$

## Cosa abbiamo appena fatto?
ABBIAMO APPENA ESEGUITO IL NOSTRO PRIMO **SUBNETTING**!

Inoltre siamo passati dalla struttura a [[002 - Abbiamo finito le combinazioni#Problemi con le classi di indirizzi|classi]] detta anche **classful** a quella che non prende in sonsiderazione le classi, detta **classless**, o [[802 - CIDR|CIDR]].

Per far capire agli altri che *subnet mask* abbiamo utilizzato dobbiamo aggiungere uno *slash* (/) alla fine del nostro *indirizzo IP*.
$$192.168.254/23$$
il numero dopo lo slash sta ad indicare i *bit* di *net ID*. (cioe' quanti bit con valore di *$0$* ci sono nella nostra *subnet mask*).

