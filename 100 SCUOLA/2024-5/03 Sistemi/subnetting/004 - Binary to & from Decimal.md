link: [youtube video](https://youtu.be/2-i5x8KCfII?si=7KFyzLP8Yn1KUUBC)

## Trasformare un'indirizzo IP da binario a decimale
indirizzo IP *decimale*:
$$192.168.1.21$$

indirizzo IP *binario*:
$$11000000.10101000.00000001.00010101$$

Traformando l'*indirizzo IP* in binario possiamo notare come ogni numerro e' in realta' composto da $8$ **bit**. Per questo ogni numero degli indirizzi IP vengono chiamti *ottetti*. 

Quindi sappiamo che ogni *indirizzo IP* contiene *$32$* bits.

#### Cosa sono i bit?
Nel sistema *binario*, i bit, sono dei numeri che possono assumere solo il valore di *$1$* oppure *$0$*

## Come si converte un numero da decimale a binario?
Per convertire un *numero decimane* in *binario* dobbiamo:
- **Dividerlo per $2$** il numero e segnarci il **resto**.
- Dividere nuovamente il nuovo numero per due.
- Ripetere il passaggio finche' il numero da dividere diventera' $0$.

#### Esempio di conversione
Ad esempio per convertire il numero $8$ da *decimale* a *binario* dobbiamo eseguire questi passaggi:
![[Pasted image 20241022173750.png]]
Il nostro valore in binario sara' composto dai *resti* **letti al contrario** rispetto a quando li abbiamo calcolati.
Nel nostro caso il numero binario sara':  
**$1000$**

## Come si converte un numero da binario a decimale?
Per convertire un numero *binario* in *decimale* ci dobbiamo ricordare che stiamo lavorando in **base due**, e  quindi dovremo utilizzare le **potenze del due**.
Ecco i passaggi da seguire:
1. **Numerare** i *bit* **partendo da destra**, partendo da **zero**.
2. **Moltiplicare** ogni *bit* per $2$ con esponente la posizione del *bit* che stiamo moltiplicando.
3. **Sommiamo** tutti i valori delle *moltiplicazioni*.

#### Esempio di conversione
Vogliamo riconvertire il *numero binario* $1000$.
1. Prima di tutto *numeriamo* i vari *bit*, e otteniamo questa tabella:

| bit 3 | bit 2 | bit 1 | bit 0 |
| ----- | ----- | ----- | ----- |
| 1     | 0     | 0     | 0     |

2. Ora *moltiplichiamo* i *bit* per $2$ con esponente la posizione di quel *bit*.
2^3 x 1 + 2^2 x0 + 2^1 x 0 + 2^0 x 0

3. Ed infine *sommiamo* i vari valori che ci sono usciti
$$8 + 0 + 0 + 0 = 8$$

Come possiamo osservare, il risultato che ci esce e' uguale al numero in *decimale* che avevamo convertito prima.





