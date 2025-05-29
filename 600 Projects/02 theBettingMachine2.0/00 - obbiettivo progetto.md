## Obbiettivo
Dopo il primo progetto di [[00 - obbiettivi progetto|predizione]] dei risultati mi e' venuto in mente di implementare l'intelligenza artificiale per provare a fare un' analisi ancora piu' approfondita delle partite.

Con questo progetto voglio riuscire a vedere il livello di predizione che posso riuscire a raggiungere, vedere se esiste una correlazione tra livello del team ecc.

#### Problematiche
1. Recupero dei dati
	2. dati di training
	3. dati di test
	4. dati delle partite da predirre effettivamente
3. pulizia dei dati
	1. capire quali dati servono effettivamente
	2. capire come togliere certi dati in determinate situazioni
4. creazione del modello

### Recupero dei dati
Prima di tutto bisogna capire come recuperare i dati da vlr, un compito che non dovrebbe essere troppo difficile in quanto l'ho gia' fatto nel progetto 1.0, anche se questa volta dovro' prendere molti piu' dati.

### Recupero dei dati, dati di training/test
Questi tipi di dati saranno i piu' complessi da prendere.
Un'idea sarebbe quella di prendere il link dei torneo di base in cui ci sono tutti i match, creare un file che contenga i link di tutte le partite e la data in cui sono avvenute, in questo modo posso prendere le informazioni dei team in un determinato periodo e basta.

dividere il dataset in 80% per il training e 20% per il test.

Per il recupero dei dati utilizzerei questi tornei qui:
- TIER 1:
	1. INTERNATIONAL
		1. https://www.vlr.gg/event/1921/champions-tour-2024-masters-madrid
		2. https://www.vlr.gg/event/1999/champions-tour-2024-masters-shanghai
		3. https://www.vlr.gg/event/2097/valorant-champions-2024
	2. EMEA
		1. https://www.vlr.gg/event/1998/champions-tour-2024-emea-stage-1
		2. https://www.vlr.gg/event/2094/champions-tour-2024-emea-stage-2
	3. PACIFIC
		1. https://www.vlr.gg/event/2002/champions-tour-2024-pacific-stage-1
		2. https://www.vlr.gg/event/2005/champions-tour-2024-pacific-stage-2
	4. AMERICA
		1. https://www.vlr.gg/event/2004/champions-tour-2024-americas-stage-1
		2. https://www.vlr.gg/event/2095/champions-tour-2024-americas-stage-2
- TIER 2:
	1. EMEA
https://www.vlr.gg/event/1943/challengers-league-2024-northern-europe-polaris-split-1
https://www.vlr.gg/event/2065/challengers-league-2024-north-polaris-split-2
https://www.vlr.gg/event/1942/challengers-league-2024-france-revolution-split-1
https://www.vlr.gg/event/2060/challengers-league-2024-france-revolution-split-2
https://www.vlr.gg/event/1939/challengers-league-2024-spain-rising-split-1
https://www.vlr.gg/event/2067/challengers-league-2024-spain-rising-split-2
https://www.vlr.gg/event/1945/challengers-league-2024-portugal-tempest-split-1
https://www.vlr.gg/event/2092/challengers-league-2024-portugal-tempest-split-2
https://www.vlr.gg/event/1893/challengers-league-2024-t-rkiye-birlik-split-1
https://www.vlr.gg/event/2085/challengers-league-2024-t-rkiye-birlik-split-2
https://www.vlr.gg/event/1932/challengers-league-2024-east-surge-split-1
https://www.vlr.gg/event/2077/challengers-league-2024-east-surge-split-2
https://www.vlr.gg/event/1947/challengers-league-2024-italy-rinascimento-split-1
https://www.vlr.gg/event/2082/challengers-league-2024-italy-rinascimento-split-2
https://www.vlr.gg/event/1948/challengers-league-2024-dach-evolution-split-1
https://www.vlr.gg/event/2072/challengers-league-2024-dach-evolution-split-2

potremmo pure prendere i dati dei player ma per ora mi limitero' a prendere i dati delle squadre nel loro complesso e basta.


