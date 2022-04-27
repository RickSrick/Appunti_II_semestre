## INTERRUPT
==INTERRUPT==: meccanismo dell'elaboratore per salvare il contatore di programma del processo interrotto per poi trasferire il controllo ad una locazione di memoria usata come inizio di un segmento di programma per determinare la causa dell'interruzione e agire di conseguenza (==INTERRUPT HANDLER==).
![[Interrupt]]

## ISTRUZIONI PRIVILEGIATE
==ISTRUZIONI PRIVILEGIATE==: sottoinsieme di istruzioni utilizzabili esclusivamente dal sistema operativo:
- abilitare/disabilitare interruzioni
- accedere ai registri di protezione della memoria
- gestire eccezioni
- arrestare la CPU

## USER / KERNEL MODE
Gli elaboratori possono agire in ==MODO UTENTE / USER MODE== oppure in ==MODO SUPERVISORE / KERNEL MODE==:
- le istruzioni privilegiate possono essere eseguite solo in kernel mode-
- anche il passaggio da kernel mode a user mode viene gestito tramite istruzioni privilegiate
- il passaggio da user mode a kernel mode può avvenire solo in circostanze particolari senza normali istruzioni, per motivi di sicurezza

## STRUTTURA KERNEL
Il ==KERNEL== è composto da tre sezioni, implementate direttamente in hardware e scritte almeno in parte in linguaggio Assembly:
- ==FIRST INTERRUPT HANDLER (FLIH)==: gestione iniziale di tutte le interruzioni
	funzioni del FLIH:
	- determinare l'origine dell'interruzione
	- attivare il segmento di codice specifico per l'interruzione identificata
- ==DISPATCHER==: assegna i CPU core ai vari processi
- terza sezione: implementa i costrutti per la sincronizzazione dei processi (e.g. semafori)
	![[Semafori]]
Ogni sistem è anche dotato di un orologio in tempo reale (==REAL-TIME CLOCK (RTC)==) per misurare gli intervalli di tempo.