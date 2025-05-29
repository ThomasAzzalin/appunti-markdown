## cosa possiamo importare?
Con *pandas* abbiamo la possibilita di importare tantissime tipologie di file e trasformarle in *dataframe*, tra cui:
### csv files
possiamo importare file csv (comma separated values), che si trovano in locale, con la seguente sintassi
![[Pasted image 20240729005423.png]]
Se invece il file si trova su un server possiamo usare la sintassi che fa uso dell'url, come in questo caso:
![[Pasted image 20240729005815.png]]

In questa parte del tutorial utilizzeremo questo file come esempio:
![[Pasted image 20240729005532.png]]
Che una volta importato in un dataframe con pandas avra' questo aspetto:
![[Pasted image 20240729005608.png]]

#### Problema dei file csv
Il problema principale dei file csv sono le dimensioni, adesso compareremo diversi formati che contengono le stesse informazioni:
**CSV:**
![[Pasted image 20240729010134.png]]
**FEATHER:**
![[Pasted image 20240729010203.png]]
**PARQUET:**
![[Pasted image 20240729010226.png]] 