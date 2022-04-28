# DEBUGGING
==DEBUGGING==: attività di individuazione e risoluzione di errori nel sistema (==BUG==) (comprende anche il _performance tuning_).
Il SO può generare ==FILE DI LOG== che danno informazioni sugli errori rilevati durante l'esecuzione di un processo; può anche acquisire e memorizzare in un file un'immagine del contenuto della memoria utilizzata dal processo: ==CORE DUMP==. Questa istantanea post-mortem dello stato del processo al momento della terminazione anomala può essere passata a un programma di supporto, un ==DEBUGGER==, in grado di rilevare l'errore.

==CRASH==: guasto nel sistema.
Come avviene per i processi utente, l'informazione riguardante l'errore viene salvata in un file di log, mentre lo stato della memoria viene salvato in un'immagine su memoria di massa: ==CRASH DUMP==.
La natura delle attività svolte dal kernel comportano tecniche più complesse: il salvataggio del crash dump su file potrebbe essere rischioso se il kernel è in stato inconsistente (e.g. malfunzionamento del codice kernel relativo allo stesso file system). Il dump viene quindi salvato in un'aria di memoria dedicata e da lì recuperato per non rischiare di compromettere il file system.

==LEGGE DI KERNIGHAN==: _"Il debugging è due volte più difficile rispetto alla stesura del codice. Di conseguenza, chi scrive il codice nella maniera più intelligente possibile non è, per definizione, abbastanza intelligente per eseguire il debugging."_

I problemi che condizionano le prestazioni sono anch'essi considerati bug.
==PERFORMANCE TUNING==: insieme delle tecniche che ottimizzano le prestazioni del sistema di calcolo, eliminando i colli di bottiglia:
- esecuzione di codice che effettui misurazioni sul comportamento del sistema e salvi i dati su un file di log
- analisi dei dati salvati nel file di log, che descrive tutti gli eventi di rilievo, per identificare ostacoli ed inefficienze
- introduzione, all'interno del SO, di strumenti interattivi che permettano ad amministratore ed utenti di monitorare il sistema (e.g. istruzione _top_ di UNIX: mostra le risorse di sistema impiegate ed un elenco ordinato dei principali processi che le utilizzano)
- ==PROFILING==: campionamento periodico dell'==INSTRUCTION POINTER (IP)== per valutare, per esempio, quali chiamate di sistema siano utilizzate maggiormente
In generale, ci sono due metodi principali per monitorare le prestazioni di un SO:
- ==COUNTERS / CONTATORI==: si contano eventi quali numero di [[Chiamate_di_sistema|system calls]] effettuate da un processo, numero di accessi al disco, etc.
![650](counters.png)
- ==TRACING / TRACCIAMENTO==: si collezionano dati più specifici, come i passaggi richiesti da una system call, segnali, etc.
![650](tracing.png)