Questa fu la seconda versione del protocollo, vennero implementate diverse tecnologie che permisero alle richieste e alle risposte **HTTP** di essere piu' flessibili ed efficienti:

- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#protocol specification information|Specificazione del protocollo]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#estensione dei metodi HTTP|estensione dei metodi HTTP]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#status code|status code]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#headers|headers]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#different filetypes|differenti tipi di file]]

### protocol specification information

Permetteva di specificare la versione del protocollo _HTTP_ che il _client_ voleva utilizzare. Era inserita all'interno della richiesta, sulla stessa riga della tipologia della richiesta.

> [!Example] Esempio
> Client -> Request
> 
> c
> 
> ```c
> GET /index.html HTTP/1.1
> ```

### estensione dei metodi HTTP

Con questa versione del protocollo HTTP vennero estesi i metodi utilizzabili, aggiungendo:

#### POST

Questo nuovo metodo fu introdotto per poter mandare un messaggio dal _client_ al _server_; mentre prima la comunicazione era uni-direzionale.

#### HEAD

E' uguale ad una richiesta **post**, ma il server quando la riceve invia solamente l'_header_ della risposta e interrompe la comunicazione subito dopo. E' utile nel caso si vogliano conoscere solamente i [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#metadata|metadata]] di una risorsa, senza consumare bandwidth necessaria per scaricare anche il body.

### status code

Fu aggiunta una riga di stato, che indicava il risultato della richiesta **HTTP**; invece che avere il server che inviava una pagina html in caso di errore. Questo lascio' piu' responsabilita' hai _browser_. Inoltre i codici di errore erano standardizzati.

### headers

L'aggiunta degli _headers_ permise di avere messaggi piu' flessibili e ricchi di informazioni, sia se si parli di dirichieste **HTTP** che di risposte. L'implementazione degli _headers_ permise l'aggiunta anche di altre informazioni come:

- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#Caching|Caching]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#Authorization|Authorization]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#different filetypes|Supporto di diversi tipi di file]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#Metadata|Metadata]]

#### Caching

E' una tecnica utilizzata per migliorare le performance dei siti.

Grazie all'header **Last-Modified** quando un server inviava una risorsa poteva includere una riga come: `Last-Modified: Wed, 21 Oct 2015 07:28:00 GMT` e il client salvava la risorsa legata a questa data. Quando il client faceva nuovamente richiesta al server per la stessa pagina, includeva l'header **If-Modified-Since** in una riga come: `If-Modified-Since: Wed, 21 Oct 2015 07:28:00 GMT`; in questo modo il server rispondeva con la risorsa solamente se era stata modificata successivamente alla data specificata.

Piu' nello specifico, se la risorsa era stata modificata rispondenva con lo status code **200**(Ok), altrimenti con **304** (Not Modified).

Vi erano anche altri _header_ utilizzati per il caching.

#### Authorization

E' un header che viene inviato insieme ad una richiesta dal _clienti_. Specificava se un'user era autorizzato ad interagire con una risorsa protetta.

#### Metadata

In questo caso per metadata intendiamo le informazioni riguardo il _user-client_ e il _server_.

### different filetypes

Questa seconda versione permetteva l'invio di file diversi da quelli _html_, venne creato il **Content-Type** dove veniva specificato la tipologia del file che stava venendo inviata.

### Esempio

> [!Example] Esempio
> Client -> Initial Request
> 
> bash
> 
> ```bash
> GET /index.html HTTP/1.0 
> User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)
> ```
> 
> Server -> response
> 
> bash
> 
> ```bash
> 200 OK 
> Date: Sun, 01 Jan 1995 12:01:00 GMT 
> Server: CERN/3.0 libwww/2.17 
> Content-Type: text/html 
> 
> <html> 
> Welcome to the <img src="/logo.gif"> example.re homepage! 
> </html>
> ```
> 
> Client -> Second connection request (to fetch the image)
> 
> bash
> 
> ```bash
> GET /logo.gif HTTP/1.0
> User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)
> ```
> 
> bash
> 
> ```bash
> 200 OK 
> Date: Sun, 01 Jan 1995 12:01:01 GMT 
> Server: CERN/3.0 libwww/2.17 
> Content-Type: text/gif 
> 
> Encoded data of logo.gif
> ```

## HTTP/1.1 (1997): L'Ottimizzazione

HTTP/1.1 risolse il problema principale della versione precedente introducendo le **connessioni persistenti**. Ora il browser poteva mantenere aperta la connessione [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#TCP (Transmission Control Protocol)|TCP]] e inviare molteplici richieste sulla stessa connessione. Questo _ridusse i tempi di caricamento delle pagine web_. Inoltre introdusse anche molte altre diverse tecnologie:

- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#content negotiation|content negotiation]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#estensione dei metodi HTTP V2|estensione dei metodi HTTP]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#pipelining|pipelining]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#hosting virtuale: La Democratizzazione del Web|hosting virtuale]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#chunked encoding: Lo Streaming dei Contenuti Dinamici|chunked encoding]]

### content negotiation

Questa funzionalita' permise al client ed al server di mettersi d'accordo per la lingua e altre informazioni riguardo alla risorsa che voleva ricevere il client. Ad esempio, il server poteva avere due documenti chiamati word.txt ma uno aveva il contentuo in inglese mentre l'altro era in tedesco, in questo modo il client poteva dare la sua preferenza sulla lingua.

### estensione dei metodi HTTP V2

con **HTTP/1.1** vennero aggiunti 5 nuovi metodi:

- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#PUT - Il Metodo di Sostituzione Completa|PUT]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#DELETE - Il Metodo di Rimozione|DELETE]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#OPTIONS - Il Metodo di Negoziazione|OPTIONS]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#TRACE - Il Metodo di Diagnostica|TRACE]]
- [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#CONNECT - Il Metodo per i Tunnel|CONNECT]]

#### PUT - Il Metodo di Sostituzione Completa

**PUT** è progettato per sostituire completamente una risorsa esistente o crearne una nuova a un URL specifico. Un'operazione PUT include sempre un **payload** che descrive una definizione di risorsa completamente nuova da salvare dal server. PUT è **idempotente**, il che significa che fare la stessa richiesta più volte produce sempre lo stesso risultato - una caratteristica fondamentale per la robustezza delle applicazioni web.

#### DELETE - Il Metodo di Rimozione

Il metodo **DELETE** elimina la risorsa specificata.  
È il complemento naturale di _PUT_ - mentre _PUT_ crea o sostituisce, **DELETE** rimuove. È anch'esso **idempotente**: eliminare la stessa risorsa più volte ha lo stesso effetto di eliminarla una volta sola.

#### OPTIONS - Il Metodo di Negoziazione

Il metodo **OPTIONS** descrive le opzioni di comunicazione per la risorsa target. Il server rispondere elencando quali _metodi HTTP_ supporta per quella specifica risorsa, quali _header_ accetta, e altre informazioni sulla capacità del server. **OPTIONS** è fondamentale per il meccanismo [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#CORS (Cross-Origin Resource Sharing)|CORS]](Cross-Origin Resource Sharing) moderno.

#### TRACE - Il Metodo di Diagnostica

Il metodo **TRACE** viene utilizzato per invocare un **loop-back remoto** a livello applicativo del messaggio di richiesta. È essenzialmente uno strumento di debugging che permette di vedere come una richiesta viene modificata mentre passa attraverso [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#Proxy: Gli Intermediari della Comunicazione di Rete|proxy]]e altri intermediari di rete. Il server che riceve una richiesta **TRACE** dovrebbe restituire esattamente quello che ha ricevuto, permettendo al client di vedere se e come la richiesta è stata alterata lungo il percorso.

#### CONNECT - Il Metodo per i Tunnel

Il metodo **CONNECT** stabilisce un tunnel verso il server identificato dalla risorsa target. Questo metodo è principalmente utilizzato per creare tunnel sicuri attraverso [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#Proxy: Gli Intermediari della Comunicazione di Rete|proxy]] HTTP, specialmente per connessioni [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#HTTPS: La Sicurezza del World Wide Web|HTTPS]]. Quando usi [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#HTTPS: La Sicurezza del World Wide Web|HTTPS]] attraverso un [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#Proxy: Gli Intermediari della Comunicazione di Rete|proxy]], il tuo browser spesso usa **CONNECT** per stabilire un tunnel _crittografato_ [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#End-to-End: La Comunicazione Diretta tra Estremi|end-to-end]].

### pipelining

Fu un'altra innovazione importante, anche se poco utilizzata nella pratica. Il browser poteva inviare molteplici richieste senza aspettare le risposte, e il server doveva rispondere nello stesso ordine. Questo avrebbe dovuto velocizzare ulteriormente il web, ma creava problemi quando una richiesta lenta bloccava tutte quelle successive, questo problema era chiamato [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#Il Problema del Head-of-Line Blocking: Il Collo di Bottiglia delle Performance|Head-of-Line Blocking]]

### hosting virtuale: La Democratizzazione del Web

Prima di questa versione, _ogni sito web_ doveva avere il _proprio indirizzo IP univoco_ mentre adesso con l'**intestazione Host**, un singolo server poteva ospitare centinaia di siti web diversi, ciascuno identificato dal nome del dominio. Ora quando il browser faceva una richiesta, includeva sempre una riga come `Host: www.miosito.com`. Il server, ricevendo la richiesta, poteva guardare questa intestazione e decidere quale sito web servire, anche se centinaia di siti diversi "vivevano" sullo stesso indirizzo IP. Questa fu una rivoluzione economica che rese possibile l'hosting condiviso e abbassò enormemente i costi per avere un sito web.

### chunked encoding: Lo Streaming dei Contenuti Dinamici

Questa tecnologia permetteva al server di iniziare a inviare una risposta prima di sapere quanto sarebbe stata lunga; prima invece il server doveva specificare la lunghezza esatta nella risorsa nell'header **Content-Length** prima di inviarla. Questo fu particolarmente utile per contenuti generati dinamicamente.

> [!Example] Esempio 
> Se consideriamo una pagina web che mostra i risultati di una ricerca nel database. Il server deve:
> 
> 1. Eseguire la query nel database
> 2. Processare i risultati
> 3. Generare l'HTML dinamicamente
> 4. Solo a questo punto sapere quanto è lunga la risposta completa

Con l'aggiunta di questa tecnologia, il server poteva dire che non sapeva la lunghezza a priori ma avrebbe inviato la risorsa a "pezzi", usando l'header **Transfer-Encoding: chunked**

### Il Problema del Head-of-Line Blocking: Il Collo di Bottiglia delle Performance

Vi era ancora un problema architetturale fondamentale chiamato **head-of-line blocking**. Anche se una connessione poteva gestire multiple richieste, queste dovevano essere processate in ordine. Se la prima richiesta era lenta, tutte le successive dovevano aspettare, anche se il server avrebbe potuto rispondere immediatamente.

#### Domain sharding: risoluzione creativa

Per risolvere tale problema gli sviluppatori web iniziarono a usare trucchi per aggirare questo limite. Uno dei più comuni era il **domain sharding**, dividere le risorse di un sito web su più domini diversi per poter aprire più connessioni parallele.

> [!Explaination] Spiegazione
> I browser limitavano il numero di connessioni simultanee per dominio, ma se avevi immagini su images.miosito.com, CSS su styles.miosito.com e JavaScript su scripts.miosito.com, potevi aggirare questo limite.

Questa tecnica pero' aveva dei costi nascosti molto significativi: Ogni nuovo dominio richiedeva una risoluzione [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#DNS (Domain Name System)|DNS]] separata, il che aggiungeva latenza. Inoltre, il browser doveva stabilire connessioni [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#TCP (Transmission Control Protocol)|TCP]] e handshake [[03 - HTTP 1.0 e HTTP 1.1 - L'Era della Maturazione#TLS (Transport Layer Security): La Fondazione della Sicurezza Web|TLS]] separati per ogni dominio, il che ironicamente poteva rallentare il caricamento iniziale delle pagine.