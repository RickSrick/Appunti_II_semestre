# RACE CONDITION
==RACE CONDITION / CORSA CRITICA==: più [[Processo|processi]] accedono in concorrenza e modificano dati condivisi; l'esito dell'esecuzione dipende dall'ordine di esecuzione di questi processi.
Tali situazioni si verificano spesso nei SO, nei quali diversi componenti agiscono su [[Risorse|risorse]] condivise, soprattutto nei [[Multiprocessore_multicore#SISTEMI MULTICORE|sistemi multicore]], in cui diversi [[Thread|thread]] vengono eseguiti in parallelo su unità di calcolo distinte.
Per evitare le corse critiche occorre che i processi siano ==SINCRONIZZATI==. A questo scopo, alcune operazioni devono essere ==ATOMICHE==: vengono completate senza subire interruzioni. Se due processi tentano di accedere agli stessi dati contemporaneamente, le istruzioni in linguaggio macchina possono risultare ==INTERFOGLIATE==, e la sequenza effettiva di esecuzione dipende da come i processi vengono schedulati.

Esempio:
	Processo produttore:
	![400](race_condition.png)
	Processo consumatore:
	![400](race_condition2.png)
	Questi processi sono corretti se considerati separatamente, ma potrebbero non funzionare correttamente se eseguiti in concorrenza, in particolare le operazioni $contatore ++$ e $contatore --$.

## SEZIONE CRITICA
==SEZIONE CRITICA==: segmento di codice in cui un processo accede a dati condivisi.
Bisogna assicurarsi che, ogni volta che un processo entra in una sezione critica, a nessun altro processo sia concesso l'ingresso in una sezione critica analoga, che accede agli stessi dati. Bisogna quindi progettare un protocollo di cooperazione tra i processi, dove ogni processo chieda l'accesso alla sezione critica tramite una ==ENTRY SECTION== e tale sezione critica sia seguita da una ==EXIT SECTION==.
==SEZIONI CRITICHE CONDIZIONALI==: sezioni critiche per le quali esistono condizioni di sincronizzazione.

L'accesso alle sezioni critiche dovrà quindi avere le seguenti caratteristiche:
- ==MUTUA ESCLUSIONE==: se un processo entra nella sua sezione critica, nessun altro processo può eseguire la propria sezioni critica
- ==PROGRESSO==: se nessun processo è in esecuzione nella sua sezione e un processo richiede di accedervi, la scelta del prossimo processo che entrerà prossimamente nella sua sezione critica non può essere rimandata indefinitamente
- ==ATTESA LIMITATA==: se un processo ha richiesto di entrare nella sua sezione critica, bisogna porre un limite al numero di volte in cui si consente ad altri processi di entrare nella propria sezione critica prima che venga soddisfatta la richiesta del primo processo (politica equa per evitare la _starvation_)

Molti sistemi forniscono soluzioni hardware per risolvere problemi legati alle sezioni critiche:
- in un sistema monoprocessore è sufficiente interdire le [[Interrupt|interruzioni]] mentre si modificano le variabili condivise, eseguendo quindi il processo senza possibilità di [[Risorse#PREEMPTION PRELAZIONE|prelazione]] (soluzione inefficiente nei sistemi multiprocessore)
- molte architetture attuali forniscono speciali istruzioni atomiche implementate in hardware
Tuttavia, queste soluzioni sono complicate e generalmente inaccessibili ai programmatori di applicazioni. I progettisti di SO hanno quindi implementato soluzioni software per risolvere questi problemi:
- [[Lock|lock]]
- [[Semafori|semafori]]
- [[Monitor|monitor]]

## SEZIONI CRITICHE E KERNEL
In particolare, il codice del kernel dovrà regolare l'accesso ai dati condivisi, nel caso in cui più processi utente richiedano servizi al SO.
A questo proposito, esistono due tipi di kernel:
- ==KERNEL SENZA DIRITTO DI PRELAZIONE==: i processi vengono eseguiti finchè non escono dalla [[Modalità|modalità kernel]], si bloccano o restituiscono volontariamente la CPU
	- immuni dai problemi legati all'ordine degli accessi alle strutture dati del kernel: non si consente l'interruzione forzata di processi attivi in modalità di sistema
- ==KERNEL CON DIRITTO DI PRELAZIONE==: si consente la prelazione di processi in esecuzione in modalità kernel
	- critici per [[Scheduling_multiprocessore#MULTIELABORAZIONE SIMMETRICA SYMMETRIC MULTI-PROCESSING SMP|sistemi SMP]], in cui due processi in modalità kernel possono essere eseguiti su processori distinti
	- necessari in ambito [[Sistemi_real-time|real-time]]: permettono ai processi in tempo reale di far valere il loro diritto di precedenza
	- utili nei sistemi [[Multiprogrammazione|time-sharing]]: diminuiscono il [[Definizioni#MISURE|tempo medio di risposta]]