**Materia**: [[informatica]]
Data: 31-03-2025
Topics: #sql 

## Key words & Acronimi
- _SQL_: acronimo di *Structured Query Language* 
- _DataBase_: Un database è una collezione di dati che vengono memorizzati e gestiti in modo strutturato per facilitarne l’accesso, la manipolazione e l’aggiornamento
- _Query_: Una query è una richiesta fatta a un database che puo' performare diverse operazioni
- _On-Prem_: abbreviazione di On-Premises, significa che i software sono installati e gestiti localmente nei server dell'azienda
- _Serverless_: indicano dei server gestiti da provider cloud
- _NoSQL_: Acronimo di *Not Only SQL*
- _ERD_: Acronimo di *Entity Reationship Diagram*

## Informazioni
*SQL* E' un linguaggio che permette di fare delle *richieste* ad un *DataBase*.
E' un linguaggio di programmazione non *case sensitive* per quanto riguarda le *key words*, mentre e' case sensitive per i nomi dei DB e delle tabelle.
### DataBase
Esistono due tipi di database:
- _Database relazionali (RDBMS)_
- _Database non relazionali (NoSQL)_
 
La prima tipologia comprende tutti quei sistemi che si basano su *tabelle* con *righe* e *colonne*; sono i piu' comuni ed ospitano dati *strutturati*. Per operare con questa tipologia di DataBase si possono usare diversi software, i piu' comuni sono *MySQL*, *PostgreSQL* e *SQLite*

La seconda tipologia viene anche chiamata *NoSQL*, permette di gestire dati non strutturati. Ci sono diversi tipi di DataBase NoSQL, i piu' comuni sono quelli basati sui file come *.json*. I software utilizzati per lavorare con questa tipologia di DataBase sono differenti da quelli citati precedentemente, il piu' famoso e' *MongoDB*

### Dove sono salvati i DataBase
I dataBase possono essere salvati sia in *locale* che in un *server*.
Quando si fanno dei test e' consigliabile salvare in locale il database, ma la maggior parte delle volte ci si trova a lavorare con dataBase salvati su di un server; Possiamo trovarci davanti a due tipologie di server:
- *Company servers*: server privati della compagnia per cui si sta lavorando, chiamati anche **On-Prem**
- *Cloud servers*: Server hostati da compagnie molto grandi come: *AWS*, *Google Cloud* e *Azure*, vengono anche chiamati *Serverless*. Permettono allo sviluppatore di concentrarsi sul codice invece di preoccuparsi della gestione dei server
### Query
Le query permettono di eseguire diverse operazioni, racchiuse nell'acronimo *CRUD*:
- Create
- Read
- Update
- Delete

### Dove eseguire le Query
Ci sono 3 principali categorie di opzioni:
- _DataBase provider Editors_: *PostgreSQL* e *MySQL* offrono applicazioni che possono essere utilizzate come ambienti per eseguire le query.
- _Cloud Providers Editors_: Spesso offrono ambienti di sviluppo online per interagire con i DataBase
- _Code Editors_: Applicazioni generiche che permettono di scrivere ed eseguire vari linguaggi di programmazione, come SQL. Il piu' famoso e' *VSCode*
### ERD
E' la riproduzione del DataBase sotto forma di *diagramma*, e' utile per documentare e comprendere la *logica* dei dati prima della vera e propria implementazione.
![[Pasted image 20250331182332.png]]
Nell'immagine e' presente una *Fact table* chiamata *job_posting_fact*, e 3 *dimension table*.

### Differenza fra Fact & Dimension Tables
Le *Fact tables* contengono i dati piu' importanti per l'analisi, e contengono spesso *foreign key* per collegarsi alle *Dimension Tables*.
Le *Dimension Tables* contengono dati che servono per *descrivere* in modo piu' dettagliato alcuni attributi presenti nelle *Fact tables*.
## Domande