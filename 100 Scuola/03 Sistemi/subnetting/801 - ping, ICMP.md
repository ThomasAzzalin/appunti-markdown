## Cosa vuol dire pingare?
Pingare vuol dire utilizzare un *comando di rete*: **ping** 

## A cosa serve il comando di rete "ping"?
Questo comando verifica se un *host* o un *server* e' raggiungibile dal *dispositivo* che ha utilizzato il comando.
Inoltre restituisce altre informazioni come:
- *Tempo di trasmissione* tra i due dispositivi.
- Percentuale di *perdita di pacchetti*.

## Cosa succede in pratica?
Durante un ping l'*host* da cui parte il comando esegue le seguenti operazini:
1) L'*host* **x** invia un pacchetto di richiesta di **echo** (*[[#ICMP]] echo request*) al dispotivo **y**.
2) Il dispositivo **y** *se raggiungibile e configurato per rispondere* restituisce al mittente una risposta di *echo* (*[[#ICMP]] echo reply*).
3) Il *tempo* che passa tra l'invio della *richiesta* e la ricezione della *risposta* e' misurato e riportato come **latenza**.

Se il dispositivo non risponde ci potrebbero essere diverse cause:
- **Iraggiungibile**.
- Non essere stato configurato per **rispondere**.
- **Problemi** di rete.

## Che cosa e' l'ICMP?
L'**ICMP (Internet Control Message Protocol)** e' un *protocollo*.

## Per cosa e' utilizzato l'ICMP?
il protocollo *ICMP*  e' utilizzato per la *diagnostica di problemi di rete* e per *gestire errori*.

## Qual'e' il suo ruolo durante un comando di ping?
Quando viene utilizzato il *comando di rete ping* i messaggi di *richiesta* e di *risposta* utilizzano questo *protocollo*.

## Altre funzionalita' importanti?
Altre funzionalita' importanti del protocollo ICMP:
- *segnalazione di errori*:
	- Destinazione irraggiungibile (*Destination Unreachable*):
		- Il dispositivo di destinazione *non puo' essere raggiunto*.
	- Tempo superato (*Tie Exceeded*):
		- Viene inviato quando il **TTL (Time-To-Live)** di un *pacchetto* scade, impedendogli di raggiungere la destinazione.
	- *Redirect message*:
		- Utilizzato per indicare ad un dispositivo di utilizzare un *percorso migliore* per raggiungere una destinazione
- *Gestione della rete*: 
	- *ICMP* *aiuta i dispositivi di rete*, come i [[router]] a comunicare tra loro. 
	- Ad esempio se un *router* e' *sovraccarico* puo' inviare un *messaggio ICMP* per *segnalare il problema*.


> [!warning]- attenzione!
> Il protocollo *ICMP* **non trasferisce dati** ma e' essenziale per monitorare e gestire le comunicazioni di rete.
