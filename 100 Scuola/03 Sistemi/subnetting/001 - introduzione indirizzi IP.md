link: [youtube video](https://youtu.be/5WfiTHiU4x8?si=Dhxs9E2ksb4x-RcF)
## Cos'e' un' indirizzo IP?
Un' **indirizzo IP** (Internet Protocol) e' una combinazione di numeri che identifica i dispositivi all'interno di una **rete**. 
Esistono due versioni di indirizzi IP:
- [[800 - IPv4|IPv4]] -> 192.168.1.1
- [[IPv6|IPv6]] -> 2001:0db8:85a3:0000:0000:8a2e:0370:7334

## A cosa servono gli indirizzi IP?
- Indicano la "*strada*" da percorrere per raggiungere quel dispositivo
- *Identificano* uno specifico dispositivo.
- Permettono la *comunicazione* fra i vari dispositivi.

## Da cosa e' composto un indirizzo IPv4?
Un indirizzo IP e' composto da 4 **ottetti** di bit divisi da 3 *punti*.
$$00000000.00000000.00000000.00000000$$
Ogni ottetto ha quindi il seguente range:
- da $0$ a $255$ -> *decimale*
- da $00000000$ a $11111111$ -> *binario*

Il numero di combinazioni e' $2^{32}$, circa $4$ *miliardi* di valori.

Ogni *ottetto* ha un suo "*compito*", infatti non possiamo usare tutte e *4* le miliardi di combinazioni liberamente, ma dobbiamo seguire delle *regole*.

## Come si vede l'indirizzo IP di un dispositivo windows?
Per vedere l'*indirizzo IP* che e' stato assegnato al nostro dispositivo su windows, dobbiamo seguere dei passaggi molto semplici:
1) Aprire il **CMD**
2) Scrivere: **ipconfig**
![[Pasted image 20241016151823.png]]

## Chi assegna gli indirizzi IP ai dispositivi?
Il **[[router]]** assegna ad ogni dispositivo che gli si collega un *indirizzo IP* che lo identifica all'interno *di una specifica rete*.
#### Quale protocollo regola questa assegnazione?
Questo processo e' regolato dal [[DHCP]] (Dynamic Host Configuration Protocol)

## Qual'e' la correlazione fra indirizzi IP e Net Mask?
![[Pasted image 20241016154536.png]]
Come possiamo notare, la *composizione* dell'*indirizzo IPv4* e della **Net Mask** *sono uguali*.
Entrambi sono formate da 4 *ottetti* divisi da 3 *punti*.

La *Net Mask* ci dice cosa rappresenta ogni *ottetto* presente nell'*indirizzo IPv4*
Questo perche' ogni *ottetto* nelle due seguenze numeriche e' *associato all'altro*.

| Tipo     | ottetto 1 | ottetto 2 | ottetto 3 | ottetto 4 |
| -------- | --------- | --------- | --------- | --------- |
| IPv4 1   | 192       | 168       | 1         | 11        |
| IPv4 2   | 192       | 168       | 1         | 44        |
| Net Mask | 255       | 255       | 255       | 0         |


Quando un ottetto della *Net Mask* ha valore di *$255$* tutti gli **host** per dire di appartenere alla stessa *rete* devono avere gli *ottetti* associati ai valori *$255$* uguali tra di loro.
Mentre se l'*ottetto* della *Net Mask* ha valore *$0$*, l'*ottetto* corrispondende nell'*indirizzo IPv4* potra' assumere, *quasi*, tutti i valori tra $0$ e $255$.

Gli *ottetti* associati agli ottetti nella *Net Mask* con valore $255$ vengono chiamati: **ottetti di Net ID**
Gli *ottetti* associati agli ottetti nella *Net Mask* con valore $0$ vengono chiamati: **ottetti di Host**

In realta' questa divisione degli *ottetti* e' decisa dalle [[classi di indirizzo]], e non e' sempre cosi.
#### Esempio di host appartenenti alla stessa rete

| Tipo             | ottetto 1 | ottetto 2 | ottetto 3 | ottetto 4 |
| ---------------- | --------- | --------- | --------- | --------- |
| indirizzo IPv4 1 | 192       | 168       | 1         | 11        |
| indirizzo IPv4 1 | 192       | 168       | 1         | 44        |
| Net Mask      | 255       | 255       | 255       | 0         |
Entrambi gli *indirizzi IPv4* fanno parte della stessa *rete* perche' nella *net Mask* i primi 3 *ottetti* hanno valore $255$ quindi due *host* per poter essere all'interno della stessa *rete* devono avere i primi 3 *ottetti* uguali, mentre l'ultimo *ottetto* puo' assumere qualsiasi valore tra $0$ e $255$.

## Cos'e' l'indirizzo di Default Gateway?
![[Pasted image 20241016161123.png]]
Il **Default Gateway** e' l'indirizzo associato al *[[router]]* di quella *rete*.
Abbiamo due tipi di *indirizzi* assiciati al *router* [[IPv6|IPv6]] & [[800 - IPv4|IPv4]].

## A cosa serve avere un Default Gateway?
Il *Default Gateway* serve quando un *host* **$A$**, appartenente alla *rete* **$X$**, vuole comunicare con un *host* **$B$**, appartenente alla *rete* **$Y$**.

#### Esempio di utilizzo del Default Gateway
Seguendo la tabella che abbiamo visto prima, che utilizzava la *Net mask*: $255.255.255.0$ ci potremmo trovare in questa situazione:
- *Host* **$A$** che ha indirizzo: $192.168.$*$0$*$.9$
	- vuole comunicare con 
- *Host* **$B$** che ha indirizzo: $192.168.$*$1$*$.9$

I due *host* si trovano in due reti differenti, e quindi devono passare per un [[router]] per poter comunicare. Quindi il messaggio prima viene inviato al *Default Gateway* che poi lo trasferira' all'altra *rete*.

## Quali indirizzi sono inutilizzabili?
Prima abbiamo detto che se l'*ottetto* della *Net Mask* ha valore $0$ allora nell'*indirizzo IPv4* quell'*ottetto* puo' assumere qualsiasi valore compreso fra $0$ e $255$.
In realta' dobbiamo tenere a mente che vi sono degli **indirizzi riservati** e che quindi non possiamo utilizzarli tutti.
Gli *indirizzi riservati* sono:
- Il *primo indirizzo* di una *rete*:
	- viene chiamato: **Indirizzo di Rete (Network Address)**
- L' *ultimo indirizzo* di una *rete*:
	- viene chiamato: **Indirizzo di Broadcast (Broadcast Address)**
	- Se si inviano messaggi a questo indirizzo, tutti gli *host* della rete lo riceveranno
- Se presente, L' *indirizzo associato al router (Default Gateway)*

#### Esempi di indirizzi riservati in una rete
Seguendo la tabella che abbiamo visto prima, che utilizzava la *Net mask*: $255.255.255.0$ gli indirizzi riservati della rete *$192.168.5.0$* sarebbero:
- *192.168.5.0* -> **Network Address**
- *192.168.5.255* -> **Broadcast Address**
- *192.168.5.1*: -> **Indirizzo del Router**
	- Di solito l'indirizzo per il *Default Gateway* e' il primo indirizzo libero nella rete. (Queste *non e'* una regola!)

Dopo tutte queste limitazioni, possiamo capire bene che il numero di indirizzi utilizzabili all'interno di una *rete* e' calcolabile facendo:
$$n - 2$$
$n = Numero$ $Indirizzi$

