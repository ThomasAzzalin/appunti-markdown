#### Premessa
Ogni script, tranne quello del plot, usufruiscono di informazioni che vengono inserite esternamente in un file di testo per semplificare di molto la procedura ricerca e calcolo dei dati. 
Suddetto file si chiama: *00_info.txt* 

## Obbiettivo
L' obbiettivo del progetto e' avere a disposizione un grafico, che facesse vedere se esistesse una correlazione tra la vittoria di un team rispetto ad un altro, prendendo in considerazione un  "punteggio", assegnato da me ad ogni team.

nel grafico cartesiano:
- le *ascessi* rappresentano la *DIFFERENZA* di punteggio tra i due team
- le *ordinate* rappresentano la percentuale di *ROUND* vinti nella partita dal team che ha il vantaggio in termini di differenza di punti

### Calcolo rating dei team
per calcolare il rating dei team innanzitutto avevo bisogno di avere gli url di tutti i team, 
file: "*01_teamLink.py*".

Una volta salvati gli url dei team che competono nelle 3 regioni del VCT, dovevo salvare per ogni team l'url di ogni giocatore, 
file: "*02_playersLink.py*".

Adesso che ho le pagine "vlr.gg" di ogni giocatore salvate in file distinti, con il nome del team di appartenenza non mi resta che calcolare il rating da dare ad ogni player, e poi fare la media dei 5 player e assegnarla al team, per poi salvare tutte queste informazioni in un database, 
file: "*03_teamStatistics.py*"

### Calcolo differenza rating, percentuale vittoria 
Ora che ho i database, uno per ogni regione (3 regioni), che contengono i rating di ogni team, devo inserire i dati delle partite disputate, per fare cio' ho creato un file di testo che ha questa struttura:
![[Pasted image 20240726004550.png]]
1) Nome della regione
2) Nome del team_a
3) Nome del team_b
4) Numero di round vinti dal team_a
5) Numero di round vinti dal team_b

facendo partire il file: "*04_caculusWinRate*" calcola quale sia il team con il rating migliore, e parte dal presupposto che quello stesso team abbia vinto almeno il 50.1% dei round (statisticamente vittoria). 
Una volta calcolato la differenza di rating, quale sia il team migliore e in percentuale quanti round abbia vinto il team "migliore" salvo tutte queste informazioni in un database che mi servira' per creare il grafico.

### Creazione grafico
Il database che abbiamo creato nell'ultimo programma ha la seguente struttura:
![[Pasted image 20240726004946.png]]
Ogni punto sara' quindi collacato nel grafico grazie alla differenza di rating e la percentuale di round vinti, inoltre salvando anche le altre informazini saremo in grado di sapere ogni punto a quale partita corrispondeva,
file: "**05_plot.py"


