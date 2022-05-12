# PROCESSI
==PROCESSO==: programma in esecuzione; unità di lavoro del sistema di calcolo.
Il programma è un'entità passiva, il processo un'entità attiva. Infatti, un programma diventa processo quando viene caricato in memoria principale, e può quindi corrispondere a vari processi. In casi come questi, un programma descrive un insieme di processi (_istanze del programma_).
Un processo necessita di alcune [[Risorse|risorse]] per assolvere al proprio compito, le quali vengono rilasciate all'atto della sua terminazione.
Ogni processo è suddiviso in [[Thread|thread]].
Normalmente, in un sistema, vi sono molti processi di uno o più utenti, e alcuni processi del SO, che vengono eseguiti in concorrenza su una o più CPU.

Il SO è responsabile delle seguenti attività relative alla gestione dei processi:
- creazione e cancellazione di processi, utente e di sistema
- sospensione e riattivazione di processi
- fornire meccanismi per la sincronizzazione di processi, la comunicazione fra processi e la gestione del [[Deadlock|deadlock]]
Per prevenire processi che eseguono cicli infiniti senza più restituire il controllo al SO si ha un timer, realizzato mediante un clock e un contatore. Il SO inizializza il contatore al tempo massimo stimato di esecuzione del processo e lo decrementa ad ogni impulso. Quando il contatore ha valore zero, si genera un [[Interrupt|interrupt]], che restituisce il controllo al SO. Questo timer viene impostato ogni volta che un processo accede alla CPU.

## ==CONTEXT SWITCH==
Quando si sospende un processo e se ne conserva lo stato per attivarne un altro, si effettua un _context switch_:
- salvare le informazioni di A (da interrompere)
- ripristinare o inizializzare le informazioni di B
![400](context_switch.png)

## STATO DI UN PROCESSO
==STATO DI UN PROCESSO==: tutte le informazioni modificabile contenuti nei registri condivisi nel sistema che sono accessibili da P.
I processi vengono rappresentati da un ==DESCRITTORE DI PROCESSO / STRUTTURA DI CONTROLLO / PROCESS CONTROL BLOCK (PCB) / VETTORE DI STATO==, il quale contiene tutte le informazioni relative ad un processo.
Il PCB viene chiamato anche ==TCB== in Linux (nel gergo di Linux si parla di _task_).
Ogni descrittore di processo è collegato ad una struttura di processi, che consiste in una lista concatenata lineare.
![550](descrittore_processo.png)
Il supporto alla sincronizzazione dei processi è implementato nel kernel dalle primitive _wait_ e _signal_; in questo modo:
- sono utilizzabili da tutti i processi
- _wait_ può accedere al [[Dispatcher|dispatcher]] e causarne l'attivazione

I processi possono trovarsi in cinque stati:
- ==NEW==: il processo viene creato
- ==RUNNING==: in esecuzione
- ==READY / RUNNABLE==: pronto per essere eseguito, in attesa di un core della CPU
- ==WAITING / UNRUNNABLE==: non può essere eseguito, è in attesa di un evento (e.g. non ha le risorse necessarie)
- ==TERMINATED==: il processo ha terminato la propria esecuzione
![550](stati_processo.png)

In particolare, considerando gli stati _ready_, _running_ e _waiting_, definiamo operazioni per spostarsi tra gli stati:
- ==ASSIGN==: dispatcher assegna processo a CPU (da waiting a running)
- ==RESIGN==: dispatcher sottrae processa a CPU (da running a waiting)
- ==SUSPEND==: mette processo in attesa, e.g. _wait_ su un [[Semafori|semaforo]] (da running a ready)
- ==RESUME==: risveglia processo sospeso, e.g. _signal_ su un semaforo (da ready a waiting) ![450](processo_stati.png)

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
	- non adatto a scambi frequenti (le system call continue rallentano)
- ==MEMORIA CONDIVISA==
	- massima efficienza nella comunicazione e velocità maggiore: richiede l'intervento del kernel solo per allocare la memoria, non richiede system call, gli accessi sono gestiti dai processi
	- fornisce prestazioni migliori nei multicore
	- più difficile da gestire: problemi di coerenza dovuti alla migrazione di dati condivisi tra varie cache
![500](comunicazione_processi.png)