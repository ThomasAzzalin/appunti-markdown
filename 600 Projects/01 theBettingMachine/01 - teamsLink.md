### Premessa, obbiettivo
Per questo script abbiamo solo bisogno di estrapolare la prima riga dal file *00_info.txt*, cioe' quella associata alla regione.

In questo script dobbiamo estrapolare gli url di ogni team per ogni regione e salvarli in un file di testo.
## Struttura
- Estrarre regione dal file *00_info.txt*
- In base alla regione estratta scegliere da quale pagina web estrapolare le informazioni
- Fare una richiesta HTTP al sito
- Estrapolare il contenuto html della risposta
- Estrarre gli url di ogni team
- Salvare gli url in un file

## Import
![[Pasted image 20240726020614.png]]
## Funzioni
##### extract_the_region
![[Pasted image 20240726010111.png]]
**Parametri:**
- !null

**Obbiettivo:**
Estrarre la prima riga del file *00_info.txt*, e restituirla. Essa corrisponde al nome della regione.

##### get_tournament_url
![[Pasted image 20240726013022.png]]
**Parametri:**
- region: e' la regione di cui vogliamo estrarre gli url dei team

**Obbiettivo:**
In base al nome della regione restituira' gli url della sua pagina web, se la regione non esiste tra quelle preventivate sollevera' un'errore.

##### get_response_content
![[Pasted image 20240726012115.png]]
**Parametri:**
- url: E' l'indirizzo della pagina web su cui opereremo

**Obbiettivo:**
Fare una richiesta HTTP al sito scelto, e poi restituire il contenuto della risposta sottoforma di stringa.
[[response.text]]

##### get_soup_html
![[Pasted image 20240726014103.png]]
**Parametri:** 
- content: e' il contenuto della risposta HTTP che abbiamo fatto nella funzione prima

**Obbiettivo:**
Creare un oggetto BeautifulSoup che organizza in modo migliore il contenuto HTML che stiamo utilizzando, in questo modo sara' piu' facile navigare nel codice del sito e trovare quello che ci serve.
Utilizziamo il parser *lxml* perche' e' piu' efficiente degli altri.
[[parser]]

##### get_each_link
![[Pasted image 20240726020132.png]]
**Parametri:** 
- soup: e' l'oggetto di beautifulSoup che contiene la struttura del codice HTML organizzata

**Obbiettivo:**
restituire tutti i tag ==a== che si trovano all'interno del secondo tag ==tbody==

##### save_in_file
![[Pasted image 20240726020231.png]]
**Parametri:**
- region: la regione su cui stiamo operando, in modo tale da selezionare in modo autonomo il file su cui lavorera' la funzione
- links: tutti gli url dei team che dobbiamo salvare e che abbiamo estratto con la funzione di prima

**Obbiettivo:**
salvare gli url che abbiamo trovato prima dei vari team nel file di testo giusto


#### MAIN
![[Pasted image 20240726020454.png]]
semplicemente utilizziaamo in ordine tutte le funzioni che abbiamo creato, ed infine restituiamo all'utente un feedback se le operazioni sono andate a buon fine.