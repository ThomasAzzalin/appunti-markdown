Adesso lavoreremo con il file contenente le informazioni biografiche di oltre 100 mila atleti che hanno partecipato alle olimpiadi.
Ecco una panoramica di questo dataframe:
![[Pasted image 20240729015726.png]]
![[Pasted image 20240729015802.png]]

### filtrare i dati
Se vogliamo vedere quali e quanti atleti sono piu' alti di 215 cm possiamo utilizzare questa sintassi:
![[Pasted image 20240729020106.png]]
E ci verrebbe restituita questa tabella:
![[Pasted image 20240729020129.png]]

Se vogliamo sapere solo il nome e l'altezza dell'atleta possiamo "complicare" la sintassi in questo modo:
![[Pasted image 20240729020213.png]]
E verrebbe stampata questa tabella:
![[Pasted image 20240729020234.png]]

Inoltre se volessimo avere gli atleti ordinati dal piu' alto al piu' basso dovremmo aggiungere la funzione: **sort_values()** in questo modo:
![[Pasted image 20240729020338.png]]
Per ricevere la seguente tabella:
![[Pasted image 20240729020353.png]]

Se non vogliamo utilizzare la funzione loc possiamo usare questa sintassi:
![[Pasted image 20240729020513.png]]
Ed otterremmo lo stesso risultato

Se volessimo combinare piu' parametri potremmo farlo con le parentesi tonde in questo modo:
![[Pasted image 20240729020736.png]]
In questo modo abbiamo filtrato tutti gli atleti piu' alti di 215 cm e che sono nati in Francia, questa e' la tabella che riceviamo:
![[Pasted image 20240729020811.png]]

Se vogliamo trovare tutti gli atleti che nel proprio nome contengono una parola specifica possiamo utilizzare la seguente sintassi:
![[Pasted image 20240729021138.png]]
In questo caso la tabella che verrebbe stampata sarebbe la seguente:
![[Pasted image 20240729021158.png]]

### query
Un' altro modo di filtrare i nostri dati e' utilizzare la funzione **.query()**, in questo modo ad esempio:
![[Pasted image 20240729023701.png]]
ci restituira' tutti gli atleti che sono nati negli USA, come possiamo vedere da questa tabella:![[Pasted image 20240729023725.png]]
 