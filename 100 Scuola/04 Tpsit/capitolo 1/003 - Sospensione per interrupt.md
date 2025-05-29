## Interrupt
un'**interrupt** e' un blocco di un processo.
Questo blocco puo' essere un **Interrupt Software** se viene generato dallo *scheduler* che interrompe un processo se ha esaurito il suo *time-slice di CPU* che gli era stato assegnato o un' **Interrupt Hardware (esterno)** se viene generato da un dispositivo *I/O*.

### Interrupt Software
Quando un processo termina il suo *time-slice di CPU* si verifica un'*interrupt software*, in questo caso il *SO* esegue delle operazioni di **Context Switching**

#### Context Switching
Con questo termine sono indicate tutte le azioni che il *SO* esegue all'*interruzione* di un processo, salvando:
- **Registri della CPU**: Instruction Pointer (IP), Program Counter (PC).
- **Stato del processore**: Flag di stao e altre informazioni
- **Stack del kernel**: Il puntatore dello stack del kernel associato al processo.

Tutte queste informazioni vengono salvate nel **PCB (Process Control Block)** 
### Interrupt Hardware
Invece gli *interrupt hardware* sono generati dai dispositivi di *I/O*, ed essendo molti sono classificati seguendo una divisione in *classi*, ad ogni classe e' associata una *locazione di memoria* chiamata **Interrupt Vector** che contiene i vari *indirizzi* che puntano alla procedura che il *SO* deve eseguire per maneggiare adeguatamente l'interrupt che si sta verificando.

### Cosa succede dopo un'interrupt generico
Dopo un generico *interrupt* (software o hardware), viene sempre richiamato lo **scheduler**, che decide quale sara' il prossimo processo ad essere mandato in *esecuzione*.
Successivamente un *programma assembler* carica i *registri* e la *mappa di memoria* che serviranno al *nuovo processo corrente*.