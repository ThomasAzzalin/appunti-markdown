Data: 14/09/2022

## Cosa sono i prodotti notevoli?
I **prodotti notevoli** sono *formule di calcolo* che permettono di *sviluppare* velocemente determinate potenze e prodotti tra polinomi, e viceversa, di *scomporre* certi tipi di polinomi.

## Somma per differenza
### Definizione
*Differenza* dei *quadrati* dei due monomi.
### Formula
$$(a+b)(a-b) = a^2 - b^2$$
### Esempio
$$(3+2x)(3-2x) = 9 - 4x^2$$

## Quadrato di binomio
### Definizione
Primo monomio al *quadrato* piu' *doppio prodotto* tra i due monomi piu' secondo monomio al *quadrato*
### Formula
$$(a+b)^2 = a^2 + b^2 - 2ab$$
### Esempio
$$(3+4x)^2 = 9 + 16x^2 -24x$$

## Quadrato di un trinomio
### Definizione
La somma tra i quadrati dei monomi e il doppio prodotto dei monomi presi a coppie
### Formula
$$(a+b+c)^2 = a^2+b^2+c^2+2ab+2ac+2bc$$
### Esempio
$$(2x+3+5x)^2 = 4x^2+9+25x^2+12x+20x^2+30x$$

## Cubo di un binomio
### Definizione
Primo monomio al cubo, piu' il triplo prodotto del primo monomio al quadrato per il secondo, piu' il triplo prodotto del primo monomio per il secondo al quadrato, piu' secondo monomio al cubo
### Formula
$$(a+b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$$
### Esempio
$$(2 + 3x)^3 = 8 + 36x + 54x^2 + 27x^3$$
## Triangolo di tartaglia
### A cosa serve?
Serve per calcolare una qualsiasi potenza di un binomio.
$$(a + b)^n$$
### Che cosa e'?
E' una tabella di forma triangolare composta da numeri naturali, ogni numero e' un coefficiente binomiale.
La tabella ha infiniti elementi, ciascuna riga si forma dalla precedente disponendo 1 agli estremi e sommando le coppie di termini della riga sovrastante.
Riga $n$ del triangolo di Tartaglia <--> $(a+b)^{n-1}$
Ad esempio la prima riga corrispondera' al seguente binomio -> $(a+b)^0$
### Prime 6 righe del triangolo
![[Pasted image 20250119204445.png]]

#### Schema per la costruzione
![[Pasted image 20250119204516.png]]

### Applicazione del triangolo ad un binomio
Per questo esempio utilizzeremo il binomio $(a+b)$.
Ipotizziamo di voler calcolare 
$$(a+b)^5$$
prima di tutto scriviamo la parte letterale di ogni monomio
$$a^5b^0 + a^4b^1 + a^3b^2 + a^2b^3 + a^1b^4 + a^0b^5$$
Ordiniamolo:
$$a^5 + a^4b + a^3b^2 + a^2b^3 + ab^4 + b^5$$
Ora prendiamo in esame la 6 riga del triangolo di Tartaglia:
![[Pasted image 20250119205625.png]]
E moltiplichiamo per i coefficienti:
$$1a^5 + 5a^4b + 10a^3b^2 + 10a^2b^3 + 5ab^4 + 1b^5$$
Ripuliamola ed otteremo il nostro risultato:
$$(a+b)^5 = a^5 + 5a^4b + 10a^3b^2 + 10a^2b^3 + 5ab^4 + b^5$$

