link: [youtube video](https://youtu.be/mJ_5qeqGOaI?si=PK4yjU1ZCTYwUHsb)

## La nostra rete di casa
Ipotizziamo che il nostro ip di casa sia:
$$192.168.5.0/24$$
e la *default net mask* di conseguenza sara'
*decimale*:
$$255.255.255.0$$
*binario*:
$$11111111.11111111.11111111.00000000$$

Quindi gli indirizzi di *host* utilizzabili avranno come range:
$$[1; 254]$$

## Se la nostra net mask e' sufficiente per contenere tutti i dispositivi perche' modificarla?
Avere tutti i dispositivi connessi nella stessa sotto rete non e' *sicuro* ed *efficiente*, quindi divideremo la nostra rete in $4$ *sotto reti*, creando una *subnet mask*.

## Come creare una subnet mask da un'indirizzo di classe C?

Per creare $4$ *sotto reti* da una rete di *classe C* dobbiamo cambiare $2$ *bit* dalla parte di *host*.

Generalmente se necessitiamo di creare delle *sotto reti* partendo da un'*indirizzo IP* dovremo sottrarre dei *bit* con valore di *$0$* e trasformarli in *bit* con valore di *$1$* dalla *net mask*.

Ora la nostra *subnet mask* in *binario* sara':
$$11111111.11111111.11111111.11000000$$

quindi da $24$ *bit* assegnati per il *net ID* passeremo a *26*.

Mentre in *decimale* si presentera' cosi:
$$255.255.255.192$$

## Quali sono i prossimi passaggi dopo aver calcolato la subnet mask?
Ora che abbiamo calcolato che la *subnet mask* che dovremo utilizzare e' la seguente:
$$255.255.255.192$$
$$11111111.11111111.11111111.11000000$$

Bisogna *calcolare* quanti *host* ci sono in ogni *sotto rete*:
La formula generale e':
$$2^{n} - 2$$
$n=numero$ $di$ $0$ $nella$ $subnet$ $mask$

Seguendo l'esempio iniziato prima il nostro calcolo risulterebbe cosi:
$$2^6-2=62$$

Ora che abbiamo calcolato quanti *host* possiamo mettere in ogni *sotto rete* possiamo scrivere i vari *range* delle *sotto reti*.

| sotto rete       | range (inizio)  | range(fine)     | indirizzo di rete | indirizzo broadcast |
| ---------------- | --------------- | --------------- | ----------------- | ------------------- |
| sotto rete *$1$* | $192.168.5.0$   | $192.168.5.63$  | $192.168.5.0$     | $192.168.5.63$      |
| sotto rete *$2$* | $192.168.5.64$  | $192.168.5.127$ | $192.168.5.64$    | $192.168.5.127$     |
| sotto rete *$3$* | $192.168.5.128$ | $192.168.5.191$ | $192.168.5.128$   | $192.168.5.191$     |
| sotto rete *$4$* | $192.168.5.192$ | $192.168.5.255$ | $192.168.5.192$   | $192.168.5.255$     |

> [!warning]- perche' la prima sotto rete ha range x.y.z.0-63?
> ricorda che il conteggio degli indirizzi parte da *$0$* quindi la fine del range del primo, come di quelli successivi, deve tenere in considerazione questa caratteristica.

## Regola generale per generare sotto reti da una rete
In generale, se dobbiamo creare *$n$* *sotto reti* a partire da una rete di *classe generica*, dobbiamo trovare il valore, *$m$*, che messo ad esponente di *$2$* mi restituisca un valore **uguale o piu' grande** di *$n$* (numero di *sotto reti* da creare).

 $2^m \ge n$

una volta trovato *$m$*, sappiamo quanti *bit* dobbiamo trasformare da *$0$* a *$1$*.

#### Esempio precedente
Nell'esempio precedente *$m$* e' uguale a *$2$* perche' *$n$* era uguale a *$4$*.
Quindi: $2^2 \ge 4$
Di conseguenza abbiamo trasformato due *bit* da *$0$* a *$1$*:
$$11111111.11111111.11111111.00000000$$
$$11111111.11111111.11111111.11000000$$
## Passaggi per suddividere una rete in sotto reti
1. Calcolare quanti *bit* di *host* dobbiamo trasformare in *bit* di *net ID* nella *subnet mask*
2. Cambiamo i *bit* della *subnet mask*
3. Calcolare quanti *host* potranno ospitare le nostre *sotto reti*.
4. Crea le *sotto reti*:
	1. *range* (inizio-fine)
	2. *indirizzo di rete*
	3. *indirizzo di broadcast*
