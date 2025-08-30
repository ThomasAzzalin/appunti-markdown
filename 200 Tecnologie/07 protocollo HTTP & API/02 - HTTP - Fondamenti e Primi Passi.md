## HTTP 
**HTTP** (HyperText Transfer Protocol) è il protocollo di comunicazione fondamentale del World Wide Web. 
È il "linguaggio" che permette a browser e server di scambiarsi informazioni attraverso internet.

## HTTP/0.9 (1991): I Primi Passi
Inizialmente **HTTP/0.9** era incredibilmente *semplice*. 
Era stato progettato per un web fatto solo di *documenti HTML testuali*, quindi doveva fare una cosa sola: 
permettere a un *browser* di *chiedere* una *pagina* e al *server* di *inviarla*.

La comunicazione era estremamente basilare: 
Vi era solamente un metodo *HTTP* che era il **GET**, che includeva solamente l'*indirizzo alla risorsa*.
Non esistevano ne *header* ne *status code*, e inoltre non si potevano inviare altri tipi di file oltre all'HTML.

> [!Example] Esempio client-server con HTTP/0.9
> Client -> Request
>```c
> GET /index.html
>```
>Server -> Response
>```html
><html> 
>Welcome to the example.re homepage! 
></html>
>```

Questo approccio funzionava perfettamente per il web delle origini, ma aveva limiti evidenti. 
Ogni richiesta richiedeva l'apertura di una nuova connessione [[05 - protocolli di strasporto#TCP (Transmission Control Protocol)|TCP]], il che era inefficiente e lento.
Inoltre, in caso di errore il *server* generava una pagina *html* che "spiegava" quello che era successo, ma non c'erano veri e propri *status code* per capire come fossero andate le richieste.

---

### DNS (Domain Name System)
E' un [[02 - HTTP - Fondamenti e Primi Passi#Servizio Distribuito: L'Architettura della Scalabilità Moderna|servizio distribuito]] che *traduce* i nomi di dominio leggibili dall'uomo negli indirizzi IP numerici che i computer utilizzano effettivamente per comunicare. 
Il *DNS* opera come un **database distribuito gerarchicamente organizzato**: 
al vertice ci sono i root server che conoscono i server autoritativi per ogni dominio di primo livello (.com, .org, .it), questi a loro volta conoscono i server per i domini di secondo livello (google.com, facebook.com), e così via. 
Quando il tuo browser deve risolvere un nome di dominio, interroga prima il resolver DNS locale (spesso fornito dal tuo ISP), che poi risale la gerarchia fino a trovare l'indirizzo IP corrispondente.

*DNS* utilizza prevalentemente *UDP sulla porta 53 per le query standard*, sfruttando la velocità di questo protocollo per operazioni che tipicamente richiedono un singolo scambio request-response. Tuttavia, quando la risposta supera i *512 byte* o quando è necessaria maggiore affidabilità (come per i trasferimenti di zona tra server), DNS passa automaticamente a *TCP*. 
Il sistema implementa diversi tipi di record: 
- *A record* per mappare nomi a indirizzi *IPv4* 
- *AAAA* per *IPv6* 
- *MX* per specificare i server di posta
- *CNAME* per creare *alias* 

La cache DNS a vari livelli (browser, sistema operativo, resolver ISP) è cruciale per le prestazioni: ogni record DNS ha un TTL (Time To Live) che specifica per quanto tempo può essere memorizzato in cache, bilanciando efficienza e aggiornamento delle informazioni. Questa architettura distribuita e ridondante rende DNS uno dei servizi più affidabili e scalabili di Internet.
 
### CORS (Cross-Origin Resource Sharing)
CORS è un meccanismo di sicurezza implementato dai browser web per controllare come le applicazioni web possono accedere a risorse che si trovano su domini diversi da quello che ha servito la pagina originale. Per comprendere CORS, devi prima capire il concetto di "origine" (origin): un'origine è definita dalla combinazione di protocollo, dominio e porta. Ad esempio, [https://example.com:443](https://example.com:443) e [http://example.com:80](http://example.com:80) sono origini diverse, così come [https://api.example.com](https://api.example.com) e [https://www.example.com](https://www.example.com). Il browser applica la **Same-Origin Policy** come regola di sicurezza predefinita, che impedisce agli script JavaScript di una pagina di accedere a risorse di un'origine diversa senza autorizzazione esplicita. Questo previene attacchi potenzialmente pericolosi dove un sito malevolo potrebbe tentare di accedere ai tuoi dati personali su altri siti che hai aperto contemporaneamente.

CORS risolve questo problema fornendo un meccanismo controllato per permettere l'accesso cross-origin quando è effettivamente necessario e sicuro. Funziona attraverso un sistema di header HTTP che il server deve configurare per dichiarare quali origini, metodi HTTP e header sono autorizzati ad accedere alle sue risorse. Quando JavaScript tenta di fare una richiesta cross-origin, il browser può eseguire una **preflight request** utilizzando il metodo OPTIONS per verificare se l'operazione è permessa. Il server risponde con header specifici come `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, e `Access-Control-Allow-Headers` che informano il browser sui permessi concessi. Solo se la preflight request viene approvata, il browser procede con la richiesta effettiva. Questo meccanismo è fondamentale per le moderne applicazioni web che spesso devono comunicare con API esterne o servizi distribuiti su domini diversi, mantenendo al contempo un livello di sicurezza adeguato contro attacchi cross-site.

### Proxy: Gli Intermediari della Comunicazione di Rete

### SPDY: L'Evoluzione che ha Preparato HTTP/2

### HTTPS: La Sicurezza del World Wide Web

### End-to-End: La Comunicazione Diretta tra Estremi

### TLS (Transport Layer Security): La Fondazione della Sicurezza Web

### Servizio Distribuito: L'Architettura della Scalabilità Moderna

### User-Agent: L'Identificazione del Client nel Web

### Accept: La Negoziazione del Contenuto nel Web

### Cookie: La Memoria del Web

### Stream: I Flussi Paralleli di HTTP/2 e HTTP/3