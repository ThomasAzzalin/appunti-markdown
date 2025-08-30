**Materia**: [[sistemi]]
Data: 08-04-2025
Topics: #ipv4 #livelloRete

## I compiti del livello rete
Serve per stabilire il percorso che i dati devono percorrere, serve quando due host si trovano su reti differenti.
L'apparecchio incaricato di far comunicare host che si trovano su reti differenti e' il *router*, che utilizza i *protocolli di routing* per determinare il percorso piu' veloce

## Commutazione
E' la tecnica utile alla creazione e gestione dei percorsi necessari per collegare due nodi in una rete. Possono essere *fisici* o *logici*.
### Commutazione di circuito
E' la tipologia fisica, viene creato un collegamento fisico fra i due dispositivi che devono comunicare e tutti i dati passeranno attraverso di esso; i punti principali:
- L'intera linea e' riservata ai due dispositivi anche quando non comunicano dati
- Se c'e' un guasto tutta la comunicazione viene persa

### Commutazione di pacchetto
In questo caso i *router* indicano ai pacchetti la strada da seguire. 
L'intero *messaggio* viene diviso in *pacchetti*. ad ogni livello il pacchetto viene inbustato in un **PDU (Protocol, Data, Unit)**, che prendera' un nome diverso a seconda del livello.
Esistono due sottocategorie della commutazione di pacchetto:
- Connection Oriented
- Connectionless
#### Connection Oriented
Questa implementazione della *commutazione di pacchetto* ricalca la commutazione di circuito.
All'inizio della comunicazione viene *generato* un percorso virtuale che i pacchetti dovranno seguire per raggiungere la destinazione, ed esso rimarra' invariato fino alla fine della comunicazione.
I punti principali sono:
- Ogni *pacchetto* ha un *identificatore*.
- Garantisce l'arrivo *ordinato* e la *correttezza* dei pacchetti.
#### Connectionless
E' un'implementazione della commutazione di pacchetto che *non e' affidabile*, cioe' che *non garastisce l'ordine* e la *correttezza* dei pacchetti. Il protocollo *IP* si basa su questa tecnica.
I suoi punti di forza sono pero':
- l'*efficienza* perche' il canale e' riservato solo per il tempo necessario per far transitare i pacchetti.
- La *tollerenza ai guasti* perche' ogni *pacchetto* viene inviato dal router in modo *autonomo* e seguira' quindi probabilmente una strada diversa dagli altri.
- La *dimensione massima* **MTU (Maximum Transmission Unit)** di ogni pacchetto viene decisa al livello del *collegamento dati*.
- Il percorso di ogni *pacchetto* e' deciso di volta in volta, dai *router* attraversati.
- Ogni *router* analizza l'*indirizzo* di destinazione e valuta il percorso piu' veloce per raggiungerlo.

## Internet Protocol (IP)
Principale *protocollo* del livello rete.
E' nato per assicurare la connessione fra *nodi*. 
E' un protocollo *connectionless*, per arrivare a destinazione un *pacchetto* deve fare dei *salti* da un *router* all'altro; e non si cura di recuperare eventuali pacchetti persi, o correggere errori di trasmissione.
I principali compiti di questo protocollo sono:
- *Assegnazione indirizzo ai dispositivi*
- *Inbustamento* 
- *Routing*, determinare il percorso migliore
- *Spacchettamento*

## Intestazione
L' *inbustamento* e lo *spacchettamento* consistono nell'aggiungere e nel togliere l' *intestazione* che contiene tutte le informazioni utili al funzionamento del protocollo *IP*; tra cui l'*indirizzo IP del mittente* e del *destinatario*.
I dati veri e propri sono inseriti nel campo *payload*, alla fine dell'intestazione.

## La frammentazione
Un *pacchetto* attraversa diversi router e collegamenti durante il suo viaggio.
Ma ogni tratto di rete presenta un *limite di grandezza* **MTU** per ogni pacchetto, essi devono quindi essere *divisi* in *frammenti* di dimensioni adeguata.
Essa e' attuata dal protocollo *IP* in questo modo:
- A tutti i *frammenti* di uno stesso pacchetto sono assegnati due valori:
	- Un valore identico per tutti i frammenti, *Identification*
	- Un valore univoco per ogni frammento che serve a tenere l'ordine, il *Fragment Offset*. L'ultimo frammento deve avere il *flag MF = 0*

## Tipi di indirizzamento IPv4
In base al *destinatario del pacchetto* gli indirizzi *IPv4* possono appartenere a 3 categorie:
- *Unicast*, identifica in modo univoco un'interfaccia di rete.
- *Broadcast*, Idendifica tutti i nodi di una rete. Quando un dispositivo invia un messaggio a tutti i dispositivi presenti in rete.
- *Multicast*, identifica un gruppo di host.