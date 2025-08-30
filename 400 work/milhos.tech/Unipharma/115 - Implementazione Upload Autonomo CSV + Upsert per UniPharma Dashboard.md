## Tags
#SVELTE
#CSV 
#DB
#SQLITE

## Details
*Date start task:* 21.07.2025
*Death line:* 04.08.2025
*Actual date end task:* 27.07.2025
*Estimated total hours:* 6
*Actual total hours:* 7.5
*Invoice:* Invoice #008

## Goal

## Suddivisione dei compiti
In ordine devo fare le seguente cose:
- Creare una nuova pagina /upload
- Capire come fare area drag and drop per file
- area di conferma con informazioni prima di modifica DB (controllare pop up aggiunti nella pagina web Etiql)
- creazione nuovo script per importazioni dati (simile a quello presente nel file `src/lib/db/import.js`)
- Creazione nuovo script di check del csv se controlli non sono gia' presenti nel file.
- 
## Problemi

## Post work 

## Time Track
21.07.2025 -> 15min -> copiata repository, avviato progetto, letto e capita task
21.07.2025 -> 60min -> Fanculo ho buttato un'ora e non ci ho capito un cazzo (valuto se inserirla comunque nella fattura)
21.07.2025 -> 120min -> modificato sidebar, creata nuova pagina, creato componente che permette il drag&drop del file, iniziata logica di elaborazione file.
24.07.2025 -> 90min -> HO FORSE CAPITO LA LOGICA CHE MI PERMETTERA' DOMANI DI FARE TUTTO PORCA 
24.07.2025 -> 60min -> ok avevo effettivamente capito la logica. Ho fatto l'API che mi va a prendere tutti gli ordini, la funzione che li confronta con quelli nel file e restituisce il numero di righe gia' esistenti e di quelle nuove. Devo ancora fare il pop up di conferma con il numero di righe da modificare e da aggiungere e l'API che mi permette di caricare le nuove righe, e quella che me le aggiunge. ipotizzo un 3h massimo. (obbiettivo finire entro il 28)
25.07.2025 -> 105min -> Finito tutto, aggiunta API POST modificato file update.js e aggiunto pop up.

totale -> 450min -> 7.5h