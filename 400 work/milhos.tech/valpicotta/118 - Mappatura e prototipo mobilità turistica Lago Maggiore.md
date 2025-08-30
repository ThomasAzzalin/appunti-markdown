## Tags
#SVELTE 
#DB
#SQLITE
#python 
#GEMINI
#LLM 
#API 
#GRAFO

## Details
*Date start task:* 02.08.2025
*Death line:* 31.08.2025
*Actual date end task:* ??
*Estimated total hours:* 50
*Actual total hours:* ??
*Invoice:* Invoice #009 / #010 / #011 / #012

## Goal

## Suddivisione dei compiti
### 14.08.2025
Per ogni provider creiamo un **JSON dedicato**, che si adatta alla sua logica e ai suoi orari.
Partire dalle autolinee varesine.
- Creare cartella apposta con i vari prompt in base alla tipologia di orari
- Creare nuova struttura per contenere gli archi in base alla compagnia
- Controllare il file per trovare le coordinate delle stazioni, e creare il formato per contenere i nodi in formato .json
- Creare un video che mostra come viene eseguito il vario processo
- Per ora fare solo con le autolinee varesine
Autolinee Varesine → [Linea N15 (HTML dinamico)](https://www.varesine.it/IT/Linea/N15)

### 17.08.2025
Lavorare solo con autolinee varesine:
- Trovare un modo per evitare di considerare le fermate che riguardano altri metodi di trasporto come treni e/o batteli (30m) [20min]
- Trovare il modo di aggiungere anche il percorso al contrario se presente e quindi trovare il modo di gestirlo (1h) [30]
- Trovare formato per i nodi (stazioni)  e di conseguenza lo script che lo genera (1h)[1h]
- Lavorare con lo script per trovare le coordinate delle fermate (30m)[1h]
- Trovare il modo di creare il DB a grafo e come aggiungere modificare ed elimanare dati (2h)
- Registrare video demo (30m)

### 19.08.2025
- [x] Salvare API key in un file .env
- [x] Revisionare il file prompts.json e come salvo i prompt, per renderli piu' leggibili. Modificato il nome in providers.json e aggiunto nuovo file "prompts.toml"
- [x] creare suddivisione in subdirectory per i vari provider
- [x] Modificare come vengono salvati gli orari e il range attivo dell'orario 
- [x] Modificato il formato del file "elaborated_data_arches.json"
- [x] Aggiustato codice qua e la

### 25.08.2025
Iniziare a lavorare con il DB a grafo:
- [x] Modificare la struttura degli archi (guardare claude code)
- [x] Creazione del DB nel pc, e poi le varie interazioni con python
- [x] Creazione delle due strutture principali: 
	- [x] Nodi
	- [x] Archi
- [x] Iniziare a creare qualche query per vedere il funzionamento

### 28.08.2025
Modificare architettura da neo4j a postgreSQL, cercare di ottenere stesso risultato che avevo con neo4j!
Ottenuto stesso risultato ma ci sono ancora diversi problemi.
1) il fase di analisi dei dati dall'LLM non prende ancora tutto
2) modificare dove viene stampato l'errore in fase di parsing da img a json
3) modificare creazione dei percorsi, se c'e' un trattino skippare quella stazione:
   st1 -> st2 -> st3 ma se st2 non ferma diventa st1 -> st3

### 29.08.2025
Modificata l'architettura dell'intero programma all'interno del file test_main.py, adesso prima estraggo la tabella con una libreria a parte, la ripulisco a mano in formato .csv e poi genero i vari file, gemini viene utilizzata per pochi dettagli da estrarre dalle varie immagini.
 
## Problemi
03.08.2025 -> non riesco a lavorare come vorrei con gemini, ottengo degli output non al 100% corretti. Problemi anche per quanto riguarda i vari formati delle varie aziende (figli di puttana)

15.08.2025 -> trovare il modo di gestire al meglio gli screen che comprendono anche il ritorno e non solo l'andata. 
## Post work 

## Time Track

| giorno     | tempo (min) | informazioni                                                                                                                                                                   | invoice |
| ---------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- |
| 02.08.2025 | 60          | iniziato ad esplorare il progetto cercando delle tecniche buone per fare scraping dei dati                                                                                     | #009    |
| 03.08.2025 | 120         | creato file per scaricare immagine, creato file per inviare immagine a gemini ed estrarre dati di input che poi andranno elaborati, creato file per elaborare i dati di input  | #009    |
| 05.08.2025 | 210         | aggiunto il main.py, creato varie funzioni nelle utils, creato e concretizzato workflow con intervento umano in 2 avvenimanti (Immagine ridimensionamento, giorni degli orari) | #009    |
| 08.08.2025 | 120         | pensato alla logica finale dei nodi e degli archi e le informazioni necessarie da immagazzinare, e il modo in cui farlo.                                                       | #009    |
| 11.08.2025 | 30          | scritto messaggio su linear                                                                                                                                                    | #009    |
| 12.08.2025 | 120         | migliorato leggibilita' codice, modificato formato dei due file json.                                                                                                          | #010    |
| 14.08.2025 | 210         | Modificato flow per gestire diversi tipi di provider, prompt diversi e formato dei file json.                                                                                  | #010    |
| 17.08.2025 | 180         | Aggiunti file per lavorare con i nodi, generazioni di coordinate e del file. Registrata demo.                                                                                  | #010    |
| 19.08.2025 | 120         | C'e' scritto sopra                                                                                                                                                             | #011    |
| 25.08.2025 | 120         | C'e' scritto sopra                                                                                                                                                             | #012    |
| 28.08.2025 | 90          | c'e' scritto sopra                                                                                                                                                             | #012    |
| 29.08.2025 | 180         | c'e' scritto sopra                                                                                                                                                             | #012    | 

