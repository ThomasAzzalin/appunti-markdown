## Dataframes
I dataframes sono la base di pandas, essi possono essere considerati come delle tabelle con delle colonne e delle righe.
![[Pasted image 20240729000343.png]]
Ad esempio questa riga di codice genera questo dataframe:
![[Pasted image 20240729000407.png]]
**.head()** permette di vedere a schermo le prime 5 righe di default, e tutte le colonne che compongono il nostro dataframe. Se inseriamo un numero all'interno delle parentesi ci fara' vedere la quantita' da noi desiderata.
La funzione direttamente contraria e' invece **.tail()** che ha le stesse propieta' e caratteristiche della sua controparte.

Come possiamo vedere dall'immagine ci sono degli elementi in piu' che non sono stati aggiunti da noi, ma in automatico da pandas. Questo concetto e' definito *popolamento* automatico:
- la *prima colonna* equivale agli **indici** di ogni riga
- ![[Pasted image 20240729000647.png]]
- la *prima riga* equivale al **nome** che ogni colonna ha, viene anche definita **HEADER**
- ![[Pasted image 20240729000703.png]]

Per impostare il nome di ogni colonna dobbiamo inserirli con questa sintassi durante la creazione del dataframe:
![[Pasted image 20240729000815.png]]
Il nuovo dataframe che otterremo sara' cosi:
![[Pasted image 20240729000831.png]]

**.columns** Permette di vedere solamente gli *header* del dataframe, ed il loro rispettivo tipo
![[Pasted image 20240729001334.png]]

Per impostare degli *indici* a nostro piaciamento durante la creazione di un dataframe dobbiamo utilizzare questa sintassi:
![[Pasted image 20240729001814.png]]
Il nuovo dataframe che otterremo sara' cosi:
![[Pasted image 20240729001836.png]]

**.index** Permette di vedere gli indici che compongono il nostro dataframe
![[Pasted image 20240729001517.png]]
Per avere questa informazione come una lista aggiungiamo: **tolist()**
![[Pasted image 20240729001553.png]]

### df.info()
Un'operazione molto comoda quando operiamo con i dataframes e' sapere il loro aspetto generale, per questo possiamo utizzare la funzione **.info()**, che ci restituisce le seguenti informazioni: 
![[Pasted image 20240729002034.png]]
- La *classe* del nostro oggetto: **DataFrame**
- il *numero* dei nostri **index**, il *primo* e l'*ultimo*
- *quante* colonne abbiamo: **3**
- per ogni colonna ci indica:
	- *index*
	- *nome colonna*
	- *quanti valori NON null abbiamo*
	- *il type dei dati dentro la colonna*
- Generalmente ci indica *quanti* e *quali* tipi di dato popolano il nostro DataFrame
- E la *memoria* occupata dal dataframe

### df.describe()
Per ottenere altre informazioni che potrebbero essere utili quando si inizia a lavorare con un nuovo dataframe possiamo usare la funzione **.describe()**, che ci restituisce le seguenti informazioni: 
![[Pasted image 20240729002607.png]]
- *count*: numero di valori non nulli
- *mean*: media dei valori
- *std*: standard deviation 
- *min*: valore minimo
- *max*: valore massimo

### df.nunique()
**.nunique()** restituisce per ogni colonna quanti sono i valori unici
![[Pasted image 20240729004023.png]]

### df\['name_column'].unique()
Possiamo inoltre utilizzare la seguente sintassi per sapere nella colonna specificata quali sono questi valori unici:
![[Pasted image 20240729004139.png]]
E questo e' quello che ci restituira'
![[Pasted image 20240729004144.png]]

### df.shape
Per saperela forma del nostro dataframe potrebbe essere utile usare la funzione **.shape**:
![[Pasted image 20240729004416.png]]
Che ci restituisce questo:
![[Pasted image 20240729004430.png]]
*righe* x *colonne*

### df.size
Per sapere quanti valori ci sono in totale nel nostro dataframe utilizziamo la funzione **.size** con la seguente sintassi:
![[Pasted image 20240729004717.png]]
Che ci restituira' la moltiplicazione tra *righe* e *colonne*, considerando anche i valori null
