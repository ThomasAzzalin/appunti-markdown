fonte: [fonte](https://sourcedaddy.com/networking/special-command-tricks.html)
## Caratteri jolly (wildcard)
I caratteri jolly sono simboli utilizzati nel cmd per rappresentare uno o piu' caratteri in un nome di un file non meglio specificati.
Ce ne sono due:
- *Asterisco \* *: Rappresenta una seguenza di caratteri di qualsiasi lunghezza, incluso nessun carattere.
	- \*.txt -> predera' in considerazione tutti i file con estensione .txt (documento.txt, file.txt ecc)
	- file\* -> tutti i file che iniziano con "file" (file.txt, file.bath, filePeppino.docs ecc)
	- \*.\* -> tutti i file in una specifica cartella, indipendentemente dal nome o dalla estensione
- *Punto Interrogativo ?*: Rappresenta un qualsiasi carattere/simbolo/numero ma solo *uno*.
	- cat?.txt -> tutti i file che iniziano con "cat" e hanno un'altro carattere prima dell'estensione txt (cat1.txt, cata.txt ecc)
	- a???.batch -> tutti i file che hanno come prima lettera a seguita da altri 3 caratteri (abcd.batch, aaaa.batch ecc)

## Caratteri di concatenamento 
I caratteri di concatenamento permettono di concatenare piu' comandi in un'unica linea.
In modo tale da eseguire piu' comandi uno subito dopo l'altro.
Ecco i piu' importanti:
- *E commerciale &*: eseguira' i comandi in seguenza (->), senza tener conto del risultato del comando precedente
	- comando1 & comando2 & comando3
- *Doppia e commerciale &&*: eseguira' i comandi in seguenza (->), ma solo se quello precedente e' andato a buon fine. Se ad esempio il primo comando fallisce tutti quelli successivi non verranno eseguiti.
	- comando1 && comando2 && comando3
- *Doppia barra verticale ||*: eseguira' i comandi in seguenza (->), am solo se quello precedente *non* e' andato a buon fine.
	- comando1 || comando2 || comando3

In oltre tutti questi caratteri si possono unire creando dei comandi piu' complessi

C:\>(copy \*.doc a: && del \*.doc) || echo Oops!
Ad esempio questo comando che viene eseguito nella memoria C:
1) copia tutti i file con estensione .doc nella memoria a:
2) se il primo comando e' andato a buon fine eliminera' tutti i file con estensione .doc
3) se una delle due operazioni precedenti fallisce allora a console verra' scritto "Oops!"

## Comandi di reindirizzamento 
il reindirizzamento viene utilizzato per controllare dove l'output di un domando va, o da dove prendere l' input.
Esistono vari simboli di reindirizzamento:
- *>*: in questo modo invieremo l'output di un comando ad un file se esiste (altrimenti verra' creato), e ne sovrascrivera' il contenuto.
	- dir > elenco_file.txt (inviera' il risultato del comando "dir" nel file "elenco_file.txt")
- *>>*: in questo modo invieremo l'output di un comando ad un file se esiste (altrimenti verra' creato), e senza sovrascrivere l'intero file aggiungera' semplicemente il testo alla fine
	- echo Nuova riga di testo >> elenco_file.txt (questo comando scrivera' la frase "Nuova riga di testo" aggiungendo una nuova riga al file "elenco_file.txt")
- *<*: specificare un file come input per un comando. Questo è utile per comandi che normalmente richiedono input interattivo.
	- sort < elenco_file.txt (Prende in input i valori all'interno del file e li restituisce nella console ordinati)

## Comando di Piping
Il comando di piping viene utilizzato per "incanalare" l'output di un comando come input di un'altro comando. L'unico carattere che esiste per il piping e' *|*.
Alcuni esempi:
- dir | find "documento" 
	- l'output del comando *dir* viene inviato come input al comando *find*, che cerca la parola "documento" nell'output di dir. In questo modo vedremo solamente tutti gli elementi che contengono quella specifica parola nel loro nome. (Il comando find e' *case sensitive*)
- ipconfig | find "IPv4"
	- Questo mostra solo le righe dell'output di ipconfig che contengono "IPv4".![[Pasted image 20241017213657.png]]
- dir | find /c "cat"
	- Questo comando ci permette di contare quanti file che hanno nel loro nome la parola "cat" sono presenti nella directory.
- dir | sort | find "testo"
	- ovviamento possiamo unire piu' di due comandi in modo piping. In questo caso ordiniamo l'output di dir per poi restituire solo i file che contengono nel loro nome la parola "testo".

