## Tags
#metaBase
#sql 
#Charlie

## Informazioni
*Date start task:* 8.05.2025
*Death line:* 18.05.2025
*Actual date end task:* 16.05.2025
*Estimated total hours:* 4
*Actual total hours:* 3.5h

## Analisi
Devo ricreare una dashboard modificando tutte le query, migrandole dallo schema *Dbo* allo schema *Analytics Staging* (STG).
[schema db](https://metabase.charlie24.com/browse/databases/3/schema/analytics_staging)

## Dashboards
### B2B Analytics
[old](https://metabase.charlie24.com/dashboard/30-b2b-analytics?contract=&country=&status=CallCenterAssigned&status=Completed&status=PartnerArrivedAtDepot&status=PartnerCompleted&status=PartnerEnrouteToTowingDestination&status=PartnerArrivingAtTowingDestination&status=PaymentAuthorized&status=HomeAssistanceCompanyAssigned&status=PartnerOnSite&status=PartnerArriving&status=DispatchAuthorized&status=PartnerDelayed&status=CustomerCompleted&status=AbroadAssistanceCompanyAssigned&status=Dispatching&status=PartnerEnroute&status=PartnerArrivedAtTowingDestination&status=PartnerEnrouteToDepot&status=VehicleRepairedOnTheSpot&status=AssistanceCompanyAssigned&status=PartnerAssigned&tab=17-high-level&timestamp=thisyear)
[new](https://metabase.charlie24.com/dashboard/44-b2b-analytics-temp-migration?contract=&country=&status=CallCenterAssigned&status=Completed&status=PartnerArrivedAtDepot&status=PartnerCompleted&status=PartnerEnrouteToTowingDestination&status=PartnerArrivingAtTowingDestination&status=PaymentAuthorized&status=HomeAssistanceCompanyAssigned&status=PartnerOnSite&status=PartnerArriving&status=DispatchAuthorized&status=PartnerDelayed&status=CustomerCompleted&status=AbroadAssistanceCompanyAssigned&status=Dispatching&status=PartnerEnroute&status=PartnerArrivedAtTowingDestination&status=PartnerEnrouteToDepot&status=VehicleRepairedOnTheSpot&status=AssistanceCompanyAssigned&status=PartnerAssigned&tab=27-high-level&timestamp=thisyear)
#### Variables
Ogni query presenta una sezione chiamata *Variables*, devo modificare per ogni query da dove le variabili attingono le informazioni.
Ho 4 variabili:
- *country*: AssistanceRequests.Country -> stg__assistance_requests.Country
- *Timestamp*: AssistanceRequests.CreateTimeStamp -> stg__assistance_requests.CreateTimestamp
- *contract*: AssistanceRequests.ContractCode -> stg__assistance_requests.ContractCode
- *Status*: AssistanceRequests.Status -> stg__assistance_requests.Status

*Variables Queries*:
- [x] Request Count
- [x] Avg ABC
- [x] Contract Performance Analysis - Total Turnover
- [x] Service Provider Cost 
- [x] Contract Performance Analysis - Net Revenues
- [x] Contract Performance Analysis - Avg Margin
- [x] Actual vs Expected (Based on Daily Average YTD) 
- [x] B2B Growth Trends
- [x] Contract Performance 
- [x] Country Performance
- [x] Map Performance
- [x] Locality Performance



#### Queries
- [ ] Request Count
- [ ] Avg ABC
- [ ] Contract Performance Analysis - Total Turnover
- [ ] Service Provider Cost 
- [ ] Contract Performance Analysis - Net Revenues
- [ ] Contract Performance Analysis - Avg Margin
- [ ] Actual vs Expected (Based on Daily Average YTD) 
- [ ] B2B Growth Trends
- [ ] Contract Performance 
- [ ] Country Performance
- [ ] Map Performance
- [ ] Locality Performance

#### Problemi

- Nella tabella *stg__partner_jobs* manca la colonna *Order*. 
	- Serve per tutte le query

- Nella tabella *stg__partner_jobs* (controparte della tabella *PartnerJobs*) manca la colonna *CustomerActualGrossPrice*. 
	- Serve per la query *Contract Performance Analysis - Total Turnover* & *Actual vs Expected (Based on Daily Average YTD)*.

- Nella tabella *stg__partner_jobs* (controparte della tabella  *PartnerJobs*) manca la colonna *C24ActualNetRevenue*. 
	- Serve per la query *Contract Performance Analysis - Net Revenues* & *Contract Performance Analysis - Avg Margin* & *Actual vs Expected (Based on Daily Average YTD)* & *B2B Growth Trends* & *Contract Performance*

- Nella tabella *stg__partner_jobs* (controparte della tabella  *PartnerJobs*) manca la colonna *CustomerActualGrossPrice*. 
	- Serve per la query *Contract Performance Analysis - Avg Margin* & *Contract Performance* & *Contract Performance Analysis - Total Turnover* & *Actual vs Expected (Based on Daily Average YTD)*.

- Ho anche notato che la colonna *CustomerPrice* nella tabella *stg__partner_jobs* e' di tipo text. Se lo modifichi da db posso evitare di fare il casting direttamente nella query e questo velocizzerebbe un pochino il processo.

Nella tabella *stg__partner_jobs* mancano le colonne:
- Order
- CustomerActualGrossPrice
- C24ActualNetRevenue
- CustomerActualGrossPrice
E ho anche notato che la colonna *CustomerPrice* sempre nella tabella *[stg__partner_job]()s* e' di tipo text. Se lo modifichi da db posso evitare di fare il casting direttamente nella query e questo velocizzerebbe un pochino il processo.

### Traffic Analytics
[old](https://metabase.charlie24.com/dashboard/32-traffic-analytics?all_options=past365days&country=)
[new](https://metabase.charlie24.com/dashboard/45-traffic-analytics-temp?country=&timestamp=past365days)

#### Variables
Ogni query presenta una sezione chiamata *Variables*, devo modificare per ogni query da dove le variabili attingono le informazioni.
Ho 2 variabili:
- *Timestamp*: AnalyticsSessions.Timestamp -> Stg__Analyitics_Sessions.Timestamp
- *country*: AssistanceRequests.Country -> 

*Variables Queries*:
- [x] Google Ads Monthly Net Revenues
- [ ] Organic Monthly Net Revenues
- [ ] Google Ads Sessions Completion Rate
- [ ] Organic Sessions Completion Rate
- [ ] Google Ads Details 
- [ ] Organic Details
- [ ] Traffic Distribution by Source and Medium
- [ ] Top Referrers by Session Volume 
- [ ] Most Frequent Organic Queries (UtmContent)
- [ ] Analytics Session Generated by UrmReferer "charlie24"





#### Queries
- [x] Google Ads Monthly Net Revenues
- [x] Organic Monthly Net Revenues
- [x] Google Ads Sessions Completion Rate
- [x] Organic Sessions Completion Rate
- [x] Google Ads Details 
- [x] Organic Details
- [x] Traffic Distribution by Source and Medium
- [x] Top Referrers by Session Volume 
- [x] Most Frequent Organic Queries (UtmContent)
- [x] Analytics Session Generated by UrmReferer "charlie24"


#### Problemi
Manca tutta la tabella corrispondente a *dbo.AnalyticsSessions*

Manca la colonna *SessionId* nella tabella *stg__assistance_requests*.
## Post work 

## Time Track
9.05.2025 90min
10.05.2025 30min
11.05.2025 30min
12.05.2025 60min
tot = 210