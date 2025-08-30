## TCP (Transmission Control Protocol)
E' un *protocollo* fondamentale che opera al livello 4 del modello [[09 - OSI|OSI]], e' uno dei *pilasti* su cui si basa l'intera comunicazione *internet*.
E' detto **Connection Oriented**, perché prima di trasmettere qualsiasi dato, stabilisce una connessione affidabile tra mittente e destinatario attraverso un processo chiamato [[02 - HTTP - Fondamenti e Primi Passi#three-way handshake|three-way handshake]].

La caratteristica più importante di *TCP* è la sua **affidabilità**, che viene messa in atto attraverso diversi step: 
- Ogni segmento di dati inviato deve essere confermato dal ricevente attraverso un messaggio di *acknowledgment*; se il mittente non riceve questa conferma entro un timeout prestabilito, ritrasmette automaticamente il segmento. 
- Implementa anche il **controllo di flusso** attraverso il meccanismo della [[02 - HTTP - Fondamenti e Primi Passi#sliding window|sliding window]]. 
- Inoltre gestisce il **controllo di congestione**, rallentando automaticamente la trasmissione quando rileva che la rete è congestionata, contribuendo così alla stabilità complessiva di Internet. 

Questo insieme di caratteristiche rende *TCP* ideale per applicazioni come HTTP, dove l'integrità dei dati è fondamentale, anche se comporta un **overhead maggiore** (in questo caso si riferisce al costo aggiuntivo in termini di risorse) rispetto a protocolli più semplici come [[02 - HTTP - Fondamenti e Primi Passi#UDP (User Datagram Protocol)|UDP]].

### three-way handshake
Durante questo processo, il *client* invia un segmento **SYN (synchronize)**, il *server* risponde con **SYN-ACK (synchronize-acknowledge)**, e infine il *client* conferma con **ACK (acknowledge)**.
Questo meccanismo garantisce che entrambe le parti siano pronte a comunicare e sincronizzino i numeri di sequenza che serviranno per ordinare i dati.

### sliding window
E' un processo che permette al ricevente di comunicare al mittente quanti dati può ancora accettare nel suo buffer, evitando sovraccarichi. 

## UDP (User Datagram Protocol)
E' un *protocollo* di trasporto che rappresenta l'approccio opposto a [[02 - HTTP - Fondamenti e Primi Passi#TCP (Transmission Control Protocol)|TCP]] in termini di *filosofia progettuale*. 
Dove [[02 - HTTP - Fondamenti e Primi Passi#TCP (Transmission Control Protocol)|TCP]] privilegia l'*affidabilità e il controllo*, **UDP** privilegia la *velocità e la semplicità*.
È definito **connectionless** perché non stabilisce alcuna connessione prima di inviare i dati: semplicemente impacchetta le informazioni in *datagrammi* e li invia verso la destinazione: 
senza alcuna garanzia che *arrivino*, che arrivino nell'*ordine* corretto, o che non si *duplichino*. 
L'**header** UDP è estremamente minimale con soli *8 byte* che rappresentano:
- Le porte di origine e destinazione, 
- la lunghezza del datagramma 
- Un checksum opzionale per il controllo di integrità. 

Questa semplicità si traduce in un **overhead** drasticamente ridotto rispetto a [[02 - HTTP - Fondamenti e Primi Passi#TCP (Transmission Control Protocol)|TCP]].

*UDP* e' ideale per le applicazioni real-time come: 
streaming video, gaming online e VoIP (Voice over IP).
Queste applicazione beneficiano enormemente di *UDP* perché possono tollerare la perdita occasionale di alcuni pacchetti, ma non possono permettersi ritardi causati da ritrasmissioni. 
Il [[02 - HTTP - Fondamenti e Primi Passi#DNS (Domain Name System)|DNS]] (Domain Name System) utilizza *UDP* per le *query standard* perché una richiesta *DNS* è tipicamente contenuta in un singolo pacchetto, e se si perde è più efficiente fare una nuova richiesta piuttosto che implementare meccanismi di affidabilità complessi. 
Tuttavia, quando si utilizza UDP, è responsabilità dell'applicazione implementare eventuali meccanismi di controllo che ritiene necessari, come:
- Gestione dei *timeout*
- *Ritrasmissione selettiva* 
- *Ordinamento* dei dati

## QUIC: Il Futuro dei Protocolli di Trasporto