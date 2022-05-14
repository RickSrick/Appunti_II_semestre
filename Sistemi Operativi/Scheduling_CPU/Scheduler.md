# SCHEDULER
==SCHEDULER (AD ALTO LIVELLO)==: implementa l'algoritmo di [[Scheduling|scheduling]] che assegna priorità ai processi in [[Processo#STATO DI UN PROCESSO|stato ready]], possibilmente in modo dinamico.
==SCHEDULER A MEDIO TERMINE==: rimozione temporanea, in caso di sovraccarico, della memoria di un processo attivo ([[Swapping|swapping]])
==SCHEDULER A BASSO LIVELLO==: [[Dispatcher|dispatcher]]

I processi sono memorizzati in una struttura dati (e.g. heap) da cui viene estratto il processo con priorità minore.
In genere si introduce anche un processo _idle_, con la priorità più bassa e sempre in stato _ready_, utile per lanciare programmi di test della CPU.
Lo scheduler deve prendere decisioni in quattro casi:
1. passa da _running_ a _waiting_ (e.g. richiesta di I/O, attesa terminazione di processo figlio)
2. passa da _runing_ a _ready_ (e.g. [[Interrupt|interrupt]])
3. passa da _waiting_ a _ready_ (e.g. completamento di I/O)
4. termina
==NON [[Risorse#PREEMPTION PRELAZIONE|PREEMPTIVE]] / COOPERATIVO==: scheduling effettuato solo nei casi 1 e 4, non possiede diritto di prelazione
Altrimenti, ==PREEMPTIVE==

In caso di scheduler preemptive, bisogna tenere in considerazione:
- accesso a dati condivisi (prelazione durante la modifica di dati con risultati imprevedibili)
- possibilità di prelazione di processi del kernel (normalmente modificano dati vitali per il sistema)
- interruzione di operazioni cruciali effettuate dal SO
- gestione del [[Processo#CONTEXT SWITCH|context switch]] tra i processi A e B