## Tags
#metaBase
#sql 
#Charlie

## Details
*Date start task:* 29.04.2025
*Death line:* 12.05.2025
*Actual date end task:* 02.05.2025
*Estimated total hours:* ??
*Actual total hours:* 2.5

## Goal
Devo ricreare una dashboard modificando tutte le query, migrandole dallo schema *Dbo* allo schema *Analytics Staging* (STG).

## Suddivisione dei compiti
### Variables
Ogni query presenta una sezione chiamata *Variables*, devo modificare per ogni query da dove le variabili attingono le informazioni.
Ho 4 variabili:
- *Timestamp*: PARTNERJOBS.PartnerJobs -> Stg Partner Jobs.CallStatusTimestamp
- *country*: ServiceProviders.Country -> ServiceProviders.*404*
- *contract*: AssistanceRequests.ContractCode -> Stg Assistance Requests.ContractCode
- *count_interventions*: Eliminato

**queries**:
- [x] Interventions Count 
- [x] Average ABC Distance 
- [x] Average AB Distance 
- [x] Average Minutes to Vehicle
- [x] Average Partner Price
- [x] App Usage Score (0 --> 1)
- [x] % Departed
- [x] % Arrived
- [x] % Completed
- [x] Network Insight Details
- [x] Interventions Count Map
- [x] Interventions Count By Hour of Day
- [x] Interventions Count By Day of Week
- [x] Interventions Count By Day of Month


### Queries
- [x] Interventions Count 
- [x] Average ABC Distance 
- [x] Average AB Distance 
- [x] Average Minutes to Vehicle
- [x] Average Partner Price
- [x] App Usage Score (0 --> 1)
- [x] % Departed
- [x] % Arrived
- [x] % Completed
- [x] Network Insight Details
- [x] Interventions Count Map
- [x] Interventions Count By Hour of Day
- [x] Interventions Count By Day of Week
- [x] Interventions Count By Day of Month

## Problemi
- La *variabile* **country** non presenta una contro parte nel nuovo schema.
- nella *query* *Average Partner Price* manca la controparte della colonna **PartnerJobs.PartnerEstimatedNetPrice** nella tabella *stg__partner_jobs*, ho utilizzato la colonna *PartnerActualNetPrice* come rimpiazio per il momento.
![[Pasted image 20250429225420.png]]

- Nella *Query* *Network Insight Details* manca la controparte della colonna **ServiceProviders.LegalName** nella tabella *stg__service_providers*, ho utilizzato la colonna *Name* come rimpiazio per il momento.
![[Pasted image 20250429231539.png]]

## Post work 
Ho trovato questo lavoro molto ripetitivo e facile, direi che e' il piu' facile che ho dovuto fare fino ad ora, ma anche il piu' noioso.
Non ho riscontrato nessun problema, ci ho impiegato 2.5h ma avrei potuto fare piu' veloce secondo me.