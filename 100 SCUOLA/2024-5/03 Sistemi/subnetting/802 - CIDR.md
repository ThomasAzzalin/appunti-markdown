## Cos'e' il "CIDR"?
Il **CIDR (Classless Inter-Domain Routing)** è un metodo per suddividere gli *indirizzi IP*.

## Cosa c'era prima del "CIDR"?
Prima di iniziare ad utilizzare questa strategia di suddivisione di *indirizzi IP*, si utilizzava un metodo chiamato *classful*. 
Cioe' avevano delle *classi* (dalla **$A$** alla **$E$**) che avevano un numero fisso e prestabilito di *bit* assegnati al *net id* e uno per gli *host*.

## Perche' siamo passati dal metodo classful al CIDR?
Il metodo *classful* creava molti sprechi in termini di *indirizzi*.

#### Esempio di spreco
Se ci serviva avere una rete con $500$ *host* dovevamo passare dalla *classe C* a quella *B*, avendo uno spreco di $(2^16 - 2)-500$ circa $65$ mila *indirizzi inutilizzati*.

## Quando entra in azione il CIDR?
Il sistema *CIDR* entra in azione nel *1993*.