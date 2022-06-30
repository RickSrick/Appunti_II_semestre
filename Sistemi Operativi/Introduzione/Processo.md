# PROCESSO
==PROCESSO==: programma in esecuzione; unità di lavoro del sistema di calcolo.
Il programma è un'entità passiva, il processo un'entità attiva. Infatti, un programma diventa processo quando viene caricato in [[Memoria_principale_processi|memoria principale]], e può quindi corrispondere a vari processi. In casi come questi, un programma descrive un insieme di processi (_istanze del programma_).
Un processo necessita di alcune [[Risorse|risorse]] per assolvere al proprio compito, le quali vengono rilasciate all'atto della sua terminazione.
Ogni processo è suddiviso in [[Thread|thread]].
Normalmente, in un sistema, vi sono molti processi di uno o più utenti, e alcuni processi del SO, che vengono eseguiti in concorrenza su una o più CPU.

Il SO è responsabile delle seguenti attività relative alla gestione dei processi:
- creazione e cancellazione di processi, utente e di sistema
- sospensione e riattivazione di processi
- fornire meccanismi per la sincronizzazione di processi, la comunicazione fra processi e la gestione del [[Deadlock|deadlock]]
Per prevenire processi che eseguono cicli infiniti senza più restituire il controllo al SO si ha un timer, realizzato mediante un clock e un contatore. Il SO inizializza il contatore al tempo massimo stimato di esecuzione del processo e lo decrementa ad ogni impulso. Quando il contatore ha valore zero, si genera un [[Interrupt|interrupt]], che restituisce il controllo al SO. Questo timer viene impostato ogni volta che un processo accede alla CPU.

## STATO DI UN PROCESSO
==STATO DI UN PROCESSO==: tutte le informazioni modificabili contenuti nei registri condivisi nel sistema che sono accessibili dal processo.
I processi vengono rappresentati da un ==PROCESS CONTROL BLOCK (PCB) / DESCRITTORE DI PROCESSO / STRUTTURA DI CONTROLLO / VETTORE DI STATO==, il quale contiene tutte le informazioni relative ad un processo.
Il PCB viene chiamato anche ==TCB== in Linux (nel gergo di Linux si parla di _task_).
Le informazioni associate ad ogni processo e conservate nel PCB sono:
- stato del processo
- nome (numero) del processo
- contesto del processo: program counter, registri della CPU (accumulatori, registri indice, stack pointer, registri di controllo)
- informazioni sullo [[Scheduling|scheduling]] della CPU (priorità, puntatori alle code di scheduling)
- informazioni sulla [[Memoria_principale_processi|gestione della memoria]] ([[Registri_base_limite|registri base e limite]], [[Tabella_delle_pagine|tabella delle pagine]] o [[Tabella_dei_segmenti|dei segmenti]])
- informazioni di contabilizzazione delle risorse: tempo di utilizzo della CPU, tempo trascorso dall'inizio dell'esecuzione, etc.
- informazioni sull'I/O: elenco dispositivi assegnati al processo, [[Tabelle_file_aperti|file aperti]], etc.
![175](pcb.png)
Ogni descrittore di processo è collegato ad una struttura di processi, che consiste in una lista concatenata lineare.
![550](descrittore_processo.png)
Il supporto alla sincronizzazione dei processi è implementato nel [[Sistema_operativo#STRUTTURA DEL SISTEMA DI CALCOLO|kernel]] dalle primitive _wait_ e _signal_; in questo modo:
- sono utilizzabili da tutti i processi
- _wait_ può accedere al [[Dispatcher|dispatcher]] e causarne l'attivazione

I processi possono trovarsi in cinque stati:
- ==NEW==: il processo viene creato
- ==RUNNING==: in esecuzione
- ==READY / RUNNABLE==: pronto per essere eseguito, in attesa di un core della CPU
- ==WAITING / UNRUNNABLE==: non può essere eseguito, è in attesa di un evento (e.g. non ha le risorse necessarie)
- ==TERMINATED==: il processo ha terminato la propria esecuzione

Transizioni tra stati:
- _raggiunto stato new_: creazione di un nuovo processo
- _da new a ready_: il SO ([[Scheduler|scheduler]] a lungo/medio termine) ammette il nuovo processo alla contesa attiva per la CPU (inclusione nella [[Scheduling|ready queue]])
- _da ready a running_: in seguito al blocco del processo in esecuzione, il processo viene scelto dal dispatcher, fra tutti i processi pronti, per essere eseguito
- _da running a ready_ (==REVOCA / PRE-RILASCIO==):
	- [[Criteri_scheduling#PRIORITÀ SHORTEST JOB FIRST SJF SHORTEST PROCESS NEXT SPN|scheduling a priorità]], quando arriva al sistema un processo con priorità maggiore
	- nei [[Criteri_scheduling#ROUND ROBIN|sistemi a partizione di tempo]], per esaurimento del quanto di tempo
	- al verificarsi di un interrupt esterno (asincrono)
- _da running a waiting_: richiesta di un servizio di I/O al SO, o per l’attesa di un qualche evento
- _da waiting a ready_: il servizio richiesto viene completato, oppure l'evento si è verificato
- _raggiunto stato terminated_:
	- terminazione normale, con chiamata al SO per indicare il completamento delle attività
	- terminazione anomala
	- uso scorretto delle risorse (e.g. superamento dei limiti di memoria, superamento del tempo massimo di utilizzo della CPU)
	- esecuzione di istruzioni non consentite o non valide ([[Interrupt|trap]]).
	![550](stati_processo.png)

In particolare, considerando gli stati _ready_, _running_ e _waiting_, definiamo operazioni per spostarsi tra gli stati:
- ==ASSIGN==: dispatcher assegna processo a CPU (da waiting a running)
- ==RESIGN==: dispatcher sottrae processa a CPU (da running a waiting)
- ==SUSPEND==: mette processo in attesa, e.g. _wait_ su un [[Semafori|semaforo]] (da running a ready)
- ==RESUME==: risveglia processo sospeso, e.g. _signal_ su un semaforo (da ready a waiting)
![450](processo_stati.png)

## ==CONTEXT SWITCH==
Quando si sospende un processo e se ne conserva lo stato per attivarne un altro, si effettua un _context switch_:
- salvare le informazioni di A (da interrompere)
- ripristinare o inizializzare le informazioni di B
![400](context_switch.png)

## STRUTTURA DI UN PROCESSO
Ogni processo include:
- _sezione di testo_: codice del programma da eseguire
- _program counter_ e il contenuto dei registri della CPU
- _stack_: dati temporanei (parametri per sottoprogrammi, indirizzi di ritorno), variabili locali
- _sezione dati_: variabili globali
- _heap_: memoria allocata dinamicamente durante il processo
![300](processo.png)

## COMUNICAZIONE TRA PROCESSI
La comunicazione tra processi può essere necessaria per:
- condividere informazioni
- velocità computazionale (e.g. task diviso in sotto-task da eseguire in parallelo tra diversi core)
- modularità del codice
Questo richiede un meccanismo di ==INTER-PROCESS COMMUNICATION (IPC)==:
- ==SCAMBIO DI MESSAGGI==
	- utile per scambiare piccole quantità di dati
	- semplice da gestire e nessuna conflittualità: è tutto gestito dal kernel tramite system call
	- non adatto a scambi frequenti (le [[Chiamate_di_sistema|system call]] continue rallentano)
- ==MEMORIA CONDIVISA==
	- massima efficienza nella comunicazione e velocità maggiore: richiede l'intervento del kernel solo per allocare la memoria, non richiede system call, gli accessi sono gestiti dai processi
	- fornisce prestazioni migliori nei [[Multiprocessore_multicore#SISTEMI MULTICORE|multicore]]
	- più difficile da gestire: problemi di coerenza dovuti alla migrazione di dati condivisi tra varie [[Dispositivi_di_memoria#CACHING|cache]]
![500](comunicazione_processi.png)