### rm
Comando utile per eliminare file
``` bash
rm hello_world.c
```

### ls
E' il comando equivalente al comando **dir** su windows.
*ls* sta per *list*, e' il modo *standard* per vedere il contenuto di una directory su sistemi *unix*.
```bash
ls
>> a.out* hello_world.c hello_world.s
```
## Varianti di LS
*source*: [geeksforgeeks](https://www.geeksforgeeks.org/ls-command-in-linux/)
E' possibile abbinare al comando base *ls* alcune opzioni che permettono di ottenre informazioni aggiuntive.
### ls -l
*List long*, mostra piu' informazioni del normale *ls*.
```bash
ls -l
>> total 24
>> -rwxr-xr-x 1 user user 14472 May 30 23:51 a.out*
>> -rw-r--r-- 1 user user    76 May 30 23:21 hello_world.c
>> -rw-r--r-- 1 user user   670 May 30 23:53 hello_world.s
```
La prima riga rappresenta il numero totale di *blocchi disco* usati dai file elencati in quella *directory*. 
(blocco disco generalmente e' uguale a 1024byte)

Ogni *riga e' un file*, mentre ogni *colonna* rappresenta delle *informazioni differenti*:
- 1 colonna -> [[002 - sistema dei permessi|permessi del file]]
- 2 colonna -> quanti [[hard link]] puntano al file
- 3 colonna -> propietario del file
- 4 colonna -> gruppo di appartenenza del file
- 5 colonna -> dimensioni in *byte*
- 6 colonna -> data e ora ultima modifica
- 7 colonna -> nome del file, se ha un * alla fine vuol dire che e' eseguibile

### ls -a
Mostra tutti i file in una directory, anche quelli *nascosti* (cioe' che iniziano con un *.*)
```bash
ls -a
>> ./ ../ a.out* hello_world.c hello_world.s
```

### ls -la
Si possono unire queste varianti, in questo caso avremo piu' informazioni su tutti i file in una directory, anche quelli nascosti.
```bash
ls -a
>> drwxr-xr-x 2 user user  4096 May 30 23:57 ./
>> drwxr-x--- 5 user user  4096 May 31 20:24 ../
>> -rwxr-xr-x 1 user user 14472 May 30 23:51 a.out*
>> -rw-r--r-- 1 user user    76 May 30 23:21 hello_world.c
>> -rw-r--r-- 1 user user   670 May 30 23:53 hello_world.s
```

### ls -lt
Restituisce i file di una directory in *ordine di ultima modifica*
```bash
ls -l
>> total 24
>> -rw-r--r-- 1 user user   670 May 30 23:53 hello_world.s
>> -rwxr-xr-x 1 user user 14472 May 30 23:51 a.out*
>> -rw-r--r-- 1 user user    76 May 30 23:21 hello_world.c
```

### ls -lh
Restituisce i file di una directory scrivendo la *dimensione* in modo piu' "*leggibile*".
```bash
ls -l
>> total 24
>> -rwxr-xr-x 1 user user 15k May 30 23:51 a.out*
>> -rw-r--r-- 1 user user  76 May 30 23:21 hello_world.c
>> -rw-r--r-- 1 user user 670 May 30 23:53 hello_world.s
```

## Vi modalita' normale
Per entrare in questa modalita':
```bash
vi hello_world.c
```

### vi nome_file.estensione
permette di *aprire* / *creare* un file. 

## Vim modalita' comando
nella modalita' normale, se si preme *:* si entra nella modalita' comando

### :q + enter
Esce da vim

### :w + enter
salva il file.

### :wq + enter
salva il file ed esce da Vim.

### i
modalita' inserimento

### a
modalita' append

### o
modalita' *open new line*


## chmod
Permette di cambiare i permessi di un file.
```bash
chmod 644 hello_world.c
```

## file
E' un comando che permette di capire la *vera natura di un file*.
```bash
file hello_world.c
>> hello_world.c: C source, ASCII text
```

> [!NOTE] approfondimento
> Non basta vedere l'estensione di un file per capire la sua vera tipologia. 
> Tutti i file contengono dei bit *invisibili* all'inizio del file che identificano la vera tipologia del file.
> Ad esempio un eseguibile potrebbe avere estensione .png, ma i suoi bit interni invece indicano che e' un file eseguibile.
> E' comunque possibile modificare questi bit, quindi non e' ugualmente una certezza al 100%

## cc
acronimo di *C Compiler*, e' spesso usato come alias per *gcc* & *clang*.
E' usato per compilare i codici scritti in C e creare un'eseguibile.
```bash
cc hello_world.c
```

## Opzioni di cc
*source*: [geeksforgeeks](https://www.geeksforgeeks.org/cc-command-in-linux-with-examples/)
E' possibile abbinare il comando *cc* con alcune opzioni, tra cui:

### cc -o
E' usato per decidere il nome da dare all'eseguibile che verra' generato.
```bash
cc hello_world.c -o nome_eseguibile
```

### cc -S
E' usato per *fermare la compilazione* alla traduzione in *assembly*.
```bash
cc -S hello_world.c
```
In questo caso verra' generato un file con estensione `.s`.

### cc -ox
E' possibile decidere anche il livello di ottimizzazione a cui vogliamo sottoporre il nostro file mentre viene compilato.
```bash
cc -ox hello_world.c
```
dove `x` e' un numero compreso fra `0` e `3`.
Piu' nel dettaglio:
- *O0*: Nessuna ottimizzazione (predefinito)
- *O1*: Ottimizza per la velocità, senza aumentare le dimensioni del codice
- *O2*: Ottimizza ulteriormente, potenzialmente aumentando le dimensioni del codice
- *O3*: Ottimizza ancor di più, potenzialmente aumentando ulteriormente le dimensioni del codice

## hexdump
*source*: [geeksforgeeks](https://www.geeksforgeeks.org/hexdump-command-in-linux-with-examples/)
E' un comando versatile, utile per mostrare il contenuto in binario dei file.
```bash
hexdump hello_world.c 
>> 0000000 6923 636e 756c 6564 3c20 7473 6964 2e6f
>> 0000010 3e68 0a0a 6e69 2074 616d 6e69 7628 696f
>> 0000020 2964 0a7b 7009 6972 746e 2866 4822 6c65
>> 0000030 6f6c 5720 726f 646c 6e5c 2922 0a3b 7209
>> 0000040 7465 7275 206e 3b30 7d0a 000a
>> 000004b
```
