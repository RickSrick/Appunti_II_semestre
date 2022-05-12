# SCHEDULING IN [[Multiprocessore_multicore#SISTEMI MULTIPROCESSORE|SISTEMI MULTIPROCESSORE]]
Lo scheduling diventa più complesso quando sono presenti più CPU nel sistema di calcolo. Si assume come ipotesi che le unità di elaborazione siano identiche nelle loro funzioni: ==SISTEMI OMOGENEI==.
Bisogna ripartire il carico di lavoro.

## ==MULTIELABORAZIONE ASIMMETRICA==
Lo scheduling, l'elaborazione dell'I/O e le altre attività del sistema sono affidate ad un solo processore (==MASTER SERVER==). Si riduce così la necessità di condividere dati.

## ==MULTIELABORAZIONE SIMMETRICA / SYMMETRIC  MULTI-PROCESSING (SMP)==
I processi pronti formano una coda comune oppure vi è una coda per ogni processore, e ciascun processore ha un proprio scheduler che seleziona la coda migliore da cui prelevare il prossimo processo da eseguire. Questo metodo viene adottato da molti SO attuali, come Windwos, Mac OS X e Linux.
L'accesso concorrente di più processori ad una struttura dati comune rende delicata la programmazione degli scheduler:
- devono evitare di scegliere contemporaneamente lo stesso processo
- devono evitare che qualche processo vada "perso"
![450](smp.png)

Ci sono due possibilità per implementare le code di attesa:
- ==COMMON READY QUEUE==: comune a tutti i processore; l'accesso alla coda deve essere gestito tramite [[Lock|lock]] per evitare le possibili [[Race_condition|race condition]]
- ==PER-CORE RUN QUEUES==: una per ogni processore; serve un uso più efficiente della cache per compensare il possibile sbilanciamento del carico di lavoro
![450](smp_code.png)

Tradizionalmente i sistemi SMP hanno reso possibile la concorrenza fra [[Thread|thread]] con l'utilizzo di diversi processori fisici; questi sistemi su processori multicore sono più veloci e consumano meno energia.
Quando un processore accede alla memoria, una quantità significativa di tempo (fino al 50%) è trascorsa in attesa della disponibilità di dati: ==STALLO DELLA MEMORIA==. Progetti hardware recenti di _hyperthreading_ implementano unità di calcolo multithread in cui due o più thread hardware sono assegnati ad una singola CPU.

Due versioni del SMP:
- ==BILANCIAMENTO DEL CARICO==: ripartire uniformemente il carico di lavoro sui vari processori (è automatico in sistemi con ready queue comune)
	- ==MIGRAZIONE GUIDATA (PUSH MIGRATION)==: un processo dedicato controlla periodicamente il carico dei processori per effettuare eventuali riequilibri
	- ==MIGRAZIONE SPONTANEA (PULL MIGRATION)==: un processore inattivo sottrae ad uno sovraccarico un processo in attesa
	- Linux le implementa entrambe: esegue il proprio algoritmo di bilanciamento ad intervalli regolari e ogniqualvolta si svuota la coda di attesa di un processore
- ==PREDILEZIONE PER IL PROCESSORE==: mantenere un processo in esecuzione sempre sullo stesso processore, per poter riutilizzare il contenuto della cache per burst successivi
	- ==PREDILEZIONE FORTE (HARD AFFINITY)==: si specifica che un processo non può abbandonare un dato processore
	- ==PREDILEZIONE DEBOLE (SOFT AFFINITY)==: non si garantisce che, per particolari condizioni di carico, i processi non subiscano spostamenti
	- Linux le implementa entrambe, Solaris solo la predilezione debole
	- l'architettura della memoria influenza la predilezione
		in caso di ==NON UNIFORM MEMORY ACCESS (NUMA)==, situazione standard in sistemi costituiti da diverse schede ognuna con una o più CPU e memoria, le CPU di una scheda accedono più velocemente alla memoria locale rispetto alle memorie residenti sulle altre schede; pertanto, ogni thread dovrebbe risiedere nella memoria locale al processore su cui viene eseguito