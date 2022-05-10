# STATO DI UN PROCESSO
==STATO DI UN PROCESSO==: tutte le informazioni modificabile contenuti nei registri condivisi nel sistema che sono accessibili da P.
I processi vengono rappresentati da un ==DESCRITTORE DI PROCESSO / STRUTTURA DI CONTROLLO / PROCESS CONTROL BLOCK (PCB) / VETTORE DI STATO==, il quale contiene tutte le informazioni relative ad un processo.
Il PCB viene chiamato anche ==TCB== in Linux (nel gergo di Linux si parla di _task_).
Ogni descrittore di processo è collegato ad una struttura di processi, che consiste in una lista concatenata lineare.
![550](descrittore_processo.png)
Il supporto alla sincronizzazione dei processi è implementato nel kernel dalle primitive _wait_ e _signal_; in questo modo:
- sono utilizzabili da tutti i processi
- _wait_ può accedere al [[Dispatcher|dispatcher]] e causarne l'attivazione

I processi possono trovarsi in tre stati:
- ==RUNNING==: in esecuzione
- ==READY / RUNNABLE==: pronto per essere eseguito, in attesa di un core della CPU
- ==WAITING / UNRUNNABLE==: non può essere eseguito (e.g. non ha le risorse necessarie)
![450](processo_stati.png)
Operazioni per spostarsi tra stati:
- ==ASSIGN==: dispatcher assegna processo a CPU (da waiting a running)
- ==RESIGN==: dispatcher sottrae processa a CPU (da running a waiting)
- ==SUSPEND==: mette processo in attesa, e.g. _wait_ su un [[Semafori|semaforo]] (da running a ready)
- ==RESUME==: risveglia processo sospeso, e.g. _signal_ su un semaforo (da ready a waiting)

# STRUTTURA DI UN PROCESSO
Ogni processo include:
- _sezione di testo_: codice del programma da eseguire
- _program counter_ e il contenuto dei registri della CPU
- _stack_: dati temporanei (parametri per sottoprogrammi, indirizzi di ritorno), variabili locali
- _sezione dati_: variabili globali
- _heap_: memoria allocata dinamicamente durante il processo
![300](processo.png)

# PROCESSO E PROGRAMMA
Un programma è un'_entità passiva_ memorizzata su disco, mentre un processo è un'_entità attiva_:
- un programma diventa processo quando viene caricato in memoria principale
- un programma può corrispondere a vari processi
- un programma descrive un insieme di processi (_istanze del programma_)

# COMUNICAZIONE TRA PROCESSI
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