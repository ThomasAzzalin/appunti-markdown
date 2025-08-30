**Materia**: [[sistemi]]
Data: 08-04-2025
Topics: #ipv4 #livelloRete

## IPv6
E' stato introdotto perche' gli indirizzi dell'*IPv4* non bastavano piu'.
Ha 128 bit.

## Rappresentazione degli indirizzi IPv6
Sono codificati come una stringa di valori esadecimali, ogni cifra e' composta da 4 bit.
Un indirizzo completo e' composto da 8 hextet, cioe' un gruppo di 16bit.

## Tipi di indirizzamento
Gli indirizzi *IPv6* possono appartenere a 3 categorie:
- *Unicast*, identifica in modo univoco un'interfaccia di rete.
- *Anycast*, e' un indirizzo *unicast* che pero' puo' essere assegnato alle interfacce di diversi dispositivi, con lo scopo di poter raggiungere *almeno una tra queste interfacce*
- *Multicast*, identifica un gruppo di host.

## Indirizzi Unicast
Possono essere utilizzati in due diversi contesti:
- In ambito *globale* in *internet* 
- In rete *locale*