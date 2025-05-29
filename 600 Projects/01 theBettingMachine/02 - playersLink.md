### Premessa, obbiettivo
Per questo script abbiamo solo bisogno di estrapolare la prima riga dal file *00_info.txt*, cioe' quella associata alla regione.

In questo script dobbiamo estrapolare gli url di ogni player per ogni team in una specifica regione e salvarli in un file
## Struttura
- Estrarre regione dal file *00_info.txt*
- In base alla regione estratta scegliere da file di testo dobbiamo estrarre gli url dei vari team
- Fare una richiesta HTTP a tutti i siti
- Estrapolare il contenuto html delle risposte
- Estrarre gli url di ogni player per ogni team
- Salvare gli url dei player del team_n nel file team_n

## Import
![[Pasted image 20240726020614.png]]
## Funzioni
##### extract_the_region
[[01 - teamsLink#^c755c9|extract_the_region]]

##### get_teams_links_for_region
![[Pasted image 20240728093308.png]]
**Parametri:**
- region: E' la regione che utilizziamo per sapere a quale file accedere per estrarre tutti i link dei team di quella regione

**Obbiettivo:**
Restituire una lista, con ogni elemento della suddetta che equivale ad un link di un team di quella regione

##### get_player_links_from_team_page
![[Pasted image 20240728093815.png]]
**Parametri:**
- team_url: Url del team da cui vogliamo estrarre tutti i player

**Obbiettivo:**
- Fa una richiesta web all'Url interessato
- Estrae il testo di suddetta richiesta
- crea un'oggetto beautifulSoup con il parser lxml
- isola nella variabile players_div il contenuto del div con uno specifico stile
- SE ha trovato quello specifico div crea la lista list_link_players che contiene tutti i tag ==a== che si trovavano nel tag ==div== 
- Restituisce infine una lista di tutti gli url che erano dentro i vari tag ==a==

##### save_in_file
![[Pasted image 20240728095233.png]]
**Parametri:**
- players_url: Una lista che contiene gli url di tutti i player di uno specifico team
- region: Contiene la regione su cui stiamo operando
- team_name: Contiene il nome del team a cui gli url sono associati

**Obbiettivo:**
Creare un file nella directory grazie ai parametri 'region' e 'team_name'.
per ogni url contenuta nella lista scrive una riga nuova nel file.


#### MAIN
![[Pasted image 20240728095925.png]]
- Estrae la regione
- Crea una lista con tutti gli url dei team di quella regione
- Per ogni url della lista esegue le varie funzioni