## HTTP/2 (2015): La Rivoluzione del Multiplexing
HTTP/2 rappresentò la prima revisione maggiore del protocollo HTTP in quasi vent'anni. 
Fu sviluppato basandosi su [[04 - HTTP 2 e HTTP 3 - Le Rivoluzioni Moderne#SPDY|SPDY]], un protocollo sperimentale creato da Google che aveva dimostrato come si potesse rendere il web molto più veloce.

La caratteristica rivoluzionaria di HTTP/2 fu il **multiplexing binario**. Invece di inviare richieste come testo leggibile, HTTP/2 divide tutto in piccoli frame binari che possono essere inviati in qualsiasi ordine su una singola connessione. Il server può rispondere alle richieste non appena è pronto, indipendentemente dall'ordine in cui sono arrivate.
Inoltre introdusse anche molte altre diverse tecnologie:
- [[02 - HTTP - Fondamenti e Primi Passi#HPACK|HPACK]]
- [[02 - HTTP - Fondamenti e Primi Passi#server push|server push]]
- [[02 - HTTP - Fondamenti e Primi Passi#prioritizzazione delle richieste|prioritizzazione delle richieste]]

### HPACK
La compressione delle intestazioni fu un'altra innovazione importante. HTTP/1.1 ripeteva molte intestazioni identiche in ogni richiesta - [[02 - HTTP - Fondamenti e Primi Passi#User-Agent: L'Identificazione del Client nel Web|User-Agent]], [[02 - HTTP - Fondamenti e Primi Passi#Accept: La Negoziazione del Contenuto nel Web|Accept]], [[02 - HTTP - Fondamenti e Primi Passi#Cookie: La Memoria del Web|Cookie]] spesso erano gli stessi per tutte le richieste di una pagina. 
HTTP/2 usa un algoritmo chiamato **HPACK** che mantiene una tabella delle intestazioni già inviate e trasmette solo le differenze.

### server push
Fu la feature più ambiziosa di HTTP/2. Il server poteva inviare risorse al browser prima che questo le richiedesse. Se il server sapeva che una pagina HTML avrebbe avuto bisogno di un certo file CSS, poteva inviarlo immediatamente insieme alla pagina. Nella pratica, questa feature si rivelò più complessa da implementare correttamente di quanto inizialmente previsto.

### prioritizzazione delle richieste
Permise ai browser di dire al server quali risorse erano più importanti; una richiesta per il CSS critico poteva avere priorità più alta rispetto a un'immagine decorativa, permettendo di ottimizzare l'ordine di caricamento.

## HTTP/3 (2022): Il Salto a QUIC
HTTP/3 rappresenta un cambio di paradigma ancora più radicale. Invece di usare [[02 - HTTP - Fondamenti e Primi Passi#TCP (Transmission Control Protocol)|TCP]] come protocollo di trasporto sottostante, HTTP/3 usa [[02 - HTTP - Fondamenti e Primi Passi#QUIC: Il Futuro dei Protocolli di Trasporto|QUIC]] (Quick UDP Internet Connections), un protocollo sviluppato da Google che gira sopra [[02 - HTTP - Fondamenti e Primi Passi#UDP (User Datagram Protocol)|UDP]].

Questa scelta risolve alcuni problemi fondamentali che affliggevano anche HTTP/2. 
[[02 - HTTP - Fondamenti e Primi Passi#TCP (Transmission Control Protocol)|TCP]], per quanto affidabile, ha il problema del [[02 - HTTP - Fondamenti e Primi Passi#Il Problema del Head-of-Line Blocking: Il Collo di Bottiglia delle Performance|Head-of-Line Blocking]] a livello di trasporto. 
Se un pacchetto TCP si perde, tutti i pacchetti successivi devono aspettare che quello perso venga ritrasmesso, anche se appartengono a [[02 - HTTP - Fondamenti e Primi Passi#Stream: I Flussi Paralleli di HTTP/2 e HTTP/3|stream]] HTTP/2 completamente indipendenti.

QUIC elimina questo problema implementando il **multiplexing** direttamente a livello di trasporto. Ogni [[02 - HTTP - Fondamenti e Primi Passi#Stream: I Flussi Paralleli di HTTP/2 e HTTP/3|stream]] HTTP/3 è *indipendente* dagli altri anche a livello di rete. 
La perdita di pacchetti di uno stream non influenza gli altri.

Un altro vantaggio enorme di HTTP/3 è la **riduzione della latenza di connessione**.
TCP richiede un "[[02 - HTTP - Fondamenti e Primi Passi#three-way handshake|three-way handshake]]" per stabilire una connessione, e se usi [[02 - HTTP - Fondamenti e Primi Passi#HTTPS: La Sicurezza del World Wide Web|HTTPS]] (cosa ormai obbligatoria), serve anche un handshake [[02 - HTTP - Fondamenti e Primi Passi#TLS (Transport Layer Security): La Fondazione della Sicurezza Web|TLS]] separato.
QUIC combina l'establishment della connessione con la negoziazione crittografica, riducendo il numero di **round-trip** necessari per iniziare a trasferire dati.

QUIC include anche la **migrazione della connessione**. 
Se ti sposti dalla WiFi alla rete mobile, una connessione TCP tradizionale si interrompe perché cambia il tuo indirizzo IP. QUIC può mantenere la stessa connessione logica anche quando l'indirizzo IP cambia, rendendo la navigazione mobile molto più fluida.
