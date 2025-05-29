### vedere prime 10 righe dataframe
Per vedere le prime 10 righe del dataframe possiamo semplicemente scrivere il suo nome ed eseguire quella riga di codice:
![[Pasted image 20240729012630.png]]

### numero di righe prese casualmente
Se non ci interessa vedere l'inizio o la fine del nostro dataframe possiamo semplicemente utilizzare questa sintassi:
![[Pasted image 20240729012843.png]]
Ci restituisce il numero di righe che abbiamo inserito come parametro ma non con un ordine specifico.

## Come accedere a specifici valori?
### loc e iloc
La funzione loc ci permette di filtrare attraverso le righe e le colonne, con la seguente sintassi:
![[Pasted image 20240729013126.png]]

Se ad esempio vogliamo solo la prima riga del nostro dataframe useremmo questa sintassi:
![[Pasted image 20240729013218.png]]

Se vogliamo vedere altre righe specifiche, ad esempio la 1,2 e 5 riga dobbiamo usare questa sintassi:
![[Pasted image 20240729013348.png]]

Possiamo utilizzare lo slicing:
![[Pasted image 20240729013506.png]]

Possiamo anche far apparire solamente specifiche colonne che ci interessano:
![[Pasted image 20240729013605.png]]

Ma anche piu' di una colonna:
![[Pasted image 20240729013636.png]]

E nell'ordine che vogliamo noi:
![[Pasted image 20240729013657.png]]

La differenza con iloc e' che quest'ultimo lavora solo con gli indici, quindi per ottenere il risultato dell' esempio fatto sopra dovremmo utilizzare questa sintassi:
![[Pasted image 20240729014024.png]]
Perche' la colonna 'Day' ha indice 0, mentre la colonna 'Units Sold' ha indice 2

### Accedere ai dati senza funzioni
Per accedere tutti i valori della colonna 'Day' possiamo usare questa sintassi:
![[Pasted image 20240729014716.png]]
Se invece la nostra colonna ha un nome che utilizza degli *spazi* dobbiamo per forza utilizzare questa sintassi:
![[Pasted image 20240729014702.png]]

### Ordinare i valori
Per vedere i nostri valori ordinati utilizziamo la funzione **.sort_values('name_column')**, con questa sintassi
![[Pasted image 20240729014926.png]]
Di default sara' ordinata in modo ascendente.
Se vogliamo che venga mostrata al contrario possiamo utilizzare la seguente sintassi:
![[Pasted image 20240729015010.png]]