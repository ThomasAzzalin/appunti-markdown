## Tags
#metaBase
#sql 
#Charlie

## Informazioni
*Date start task:* 22.05.2025
*Death line:* 09.06.2025
*Actual date end task:* ??
*Estimated total hours:* 11
*Actual total hours:* ??

## Analisi
Devo lavorare sul sito *Etiql*; nello specifico:
- aggiunta filtro nella pagina *Historical Purchase Order*
- migliorare UI nella pagina *Engine*
- Aggiungere flag *Edge Sizes* in tutte le sezioni dove e' anche presente la flag *Half Sizes*

## Suddivisione dei compiti
### aggiunta filtro nella pagina Historical Purchase Order
Suddivisione il compito in sottoproblemi:
1. Assicurarsi che la lista dei fornitori disponibili per il filtro sia dinamica e popolata dai dati presenti nel database relativi agli ordini storici.
2. Nella sezione "Historical Purchase Order", aggiungere un nuovo filtro per permettere la selezione del fornitore.
3. Posizionare questo filtro nella UI **di fianco al pulsante "Export to CSV"**.
4. Il filtro deve permettere all'utente di visualizzare nella tabella solo gli ordini storici relativi al fornitore selezionato.
#### 1
Utilizzare *api* gia' esistente nel file: *src/routes/api/suppliers/+server.js*
Inserire questi dati in un vettore che saranno poi visualizzabile e selezionabili nel filtro.

#### 2/3
Copiare dal file: *src/routes/manage-skus/+page.svelte* il filtro di ricerca.
Modificarlo in base alle esigenze, e posizionarlo vicino al tasto Export to CSV

#### 4
Copiare dal file : *src/routes/manage-skus/+page.svelte* la funzione che filtra gli elementi visualizzati in base al filtro.
Modificarla in base alla struttura della tabella.

### migliorare UI nella pagina Engine
Suddivisione il compito in sottoproblemi:
1. Nella pagina *Engine* (file: *src/routes/engine/+page.svelte*), modificare l'allineamento dei valori mostrati per i campi 'Grow from last year' e 'Months Ahead'. I numeri devono essere **allineati a destra** per una migliore leggibilità.
2. Assicurarsi che le icone (frecce su/giù) associate a questi campi siano **sempre visibili**, indipendentemente dallo stato del valore (anche quando il valore è zero o non c'è variazione).
### Aggiungere flag Edge Sizes

## Problemi
Manca la colonna *Edge Sizes* nella tabella *Skus* utile per risolvere la task numero 3.
## Post work 

## Time 
22.05.2025 -> 30m -> studio del progetto ad alto livello
23.05.2025 -> 60m -> finita task 3
24.05.2025 -> 30min -> aggiustato push
26.06.2025 -> 120 min -> iniziata task 1
27.05.2025 -> 60min -> finita task 1 e task 2