## Come aggiungere una colonna?
Per aggiungere una colonna nuova basta scrivere:
name_dataframe\['new_column_name'] = list_of_new_values
Il numero dei nuovi elementi aggiunti deve combaciare con il numero di righe del dataframe, oppure si puo' scrivere anche un solo valore che popolera' tutta la colonna.
![[Pasted image 20240729024805.png]]

Se vogliamo ad esempio associare ad ogni 'coffee type' uno specifico prezzo possiamo farlo importando la libreria numpy, e utilizzando questa sintassi:
![[Pasted image 20240729025656.png]]
quindi dove l'elemento della colonna 'coffee type' e' uguale a 'Espresso' il valore della nuova colonna sara' 3.99, in tutti gli altri casi sara' 5.99
La nostra nuova tabella risultera' cosi:
![[Pasted image 20240729025805.png]]

Possiamo inoltre utilizzare una comoda sintassi per creare una nuova colonna, basandosi su elementi gia' esistenti:

## Come eliminare una colonna?
Per eliminare una colonna, ed applicare il cambiamento al dataframe su cui stiamo lavorando dobbiamo utilizzare la seguente sintassi:
![[Pasted image 20240729030118.png]]

Con la seguente sintassi possiamo eliminare anche una sola riga:
![[Pasted image 20240729030334.png]]

## Come rinominare le colonne
Possiamo anche rinominare le colonne con la seguente sintassi:
![[Pasted image 20240729030732.png]]
Il nostro nuovo dataset sarebbe:
![[Pasted image 20240729030748.png]]