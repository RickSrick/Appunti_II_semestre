# SEMAFORI
==SEMAFORI==: strumenti di sincronizzazione composti da una variabile intera, ai quali si può accedere solo attraverso due operazioni indivisibili e atomiche, $wait(S)$ e $signal(S)$ ($S$: nome del semaforo).
Due tipi principali di semafori:
- ==SEMAFORO MUTEX==: la variabile intera può assumere solamente i valori 0 e 1
	il funzionamento è simile a quello del [[Lock|lock mutex]]
- ==SEMAFORO CONTATORE==: la variabile intera può assumere qualsiasi valore in un dominio non limitato

Il semaforo contatore può essere utilizzato quando bisogna gestire l'accesso a risorse presenti in un numero finito di esemplari:
- il semaforo è inizialmente impostato al numero di esemplari della risorsa disponibili
- un processo che vuole acquisire un'istanza della risorsa effettua una chiamata a $wait(S)$, decrementandone il valore
- un processo che vuole rilasciare un'istanza della risorsa effettua una chiamata a $signal(S)$, incrementandone il valore
- se il semaforo è uguale a 0, tutte le istanze della risorsa sono allocate, e i processi che ne richiedono una devono sospendersi sul semaforo
![450](semafori.png)
Tutte le modifiche al valore del semaforo contenute nei metodi $wait(S)$ e $signal(S)$ devono essere eseguite in modo indivisibile. Inoltre, il valore del semaforo non può essere modificato da più processi contemporaneamente. Nel caso di $wait(S)$, devono essere effettuate atomicamente sia la verifica del valore che il suo decremento.

## SEMAFORI E BUSY WAITING
Dato che occorre garantire che due processi non eseguano $wait(S)$ e $signal(S)$ sullo stesso semaforo allo stesso istante, queste chiamate devono essere effettuate all'interno della sezione critica. Si può quindi nuovamente creare una situazione di _attesa attiva / busy waiting_ dei processi in attesa ad un semaforo: questi si trovano nel ciclo del codice della entry section. Questo può costituire un problema per i sistemi multiprogrammati, in quanto così vengono sprecati cicli di CPU che altri processi potrebbero usare in modo più produttivo.
(link a sistemi multiprogrammati?)
Per evitare questa situazione si può definire il semaforo in modo un po' diverso, in modo tale che ogni struttura semaforo contenga:
- un valore intero (numero di processi in attesa)
- un puntatore alla testa di una lista dei processi in attesa (formata dai [[Processi#STATO DI UN PROCESSO|PCB]])
![450](semafori2.png)
Con questo semaforo, si usano due metodi, forniti dal SO come [[Chiamate_di_sistema|system call]]:
- $block()$: posiziona il processo che richiede di essere bloccato nell'oppurtuna d'attesa, ovvero sospende il processo che invoca il metodo (chiamato all'interno di $wait(S)$)
- $wakeup()$: rimuove un processo dalla coda d'attesa e lo sposta nella ready queue (chiamato all'interno di $signal(S)$)
![700](semafori3.png)
Mentre la definizione classica di semaforo ad attesa attiva implica che il valore del semaforo non può mai essere negativo, in questo nuovo semaforo il valore può essere negativo: se è negativo, il modulo del valore fornisce il numero di processi in attesa al semaforo.
Inoltre, questo nuovo tipo di semaforo può condurre a situazioni in cui ciascun processo attende l'esecuzione di un'istruzione $signal(S)$, che solo uno degli altri processi in coda può chiamare; se ciò avviene, si verifica un [[Deadlock|deadlock]].
Inoltre, un processo può attendere al semaforo per un tempo indefinito senza venir mai rimosso dalla coda d'attesa, causando un fenomeno di _starvation_. In particolare, può avvenire se la rimozione dei processi dalla coda avviene in modalità _LIFO (Last In First Out)_, mentre si può garantire che ciò non avvenga usando la modalità _FIFO (First In First Out)_.

## SEMAFORI PRIVATI
In problemi reali la condizione per cui un processo può continuare a lavorare non dipende solo da una variabili, ma da diversi fattori chiamati ==CONDIZIONI DI SINCRONIZZAZIONE==.
Esempio:
	abbiamo un processo che produce risorse consumabili e altri _N_ processi che consumano una certa quantità di risorse non prevedibile a priori. Supponiamo politica FIFO: i processi consumano le risorse nell'ordine della loro richiesta (chi prima ordina prima consuma)
Per implementare complessi problemi di sincronizzazione, si introduce il ==SEMAFORO PRIVATO==: solo un processo può chiamare $wait(S)$, mentre $signal(S)$ può essere chiamato da qualsiasi processo.