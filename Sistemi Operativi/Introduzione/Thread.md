# THREAD
==THREAD==: suddivisione di un [[Processo|processo]] in due o più sottoprocessi; unità base d'uso della CPU.
Alla base del concetto di thread sta la constatazione che la definizione di processo è basata su due aspetti: possesso delle [[Risorse|risorse]] ed esecuzione. I due aspetti sono indipendenti, e come tali possono essere gestiti dal SO. L'elemento che viene eseguito è il thread, mentre l'elemento che possiede le risorse è il processo.

==HEAVYWEIGHT PROCESS==: processo tradizionale, composto da un solo thread (un processo è pesante in riferimento al contesto che lo definisce)
==LIGHTWEIGHT PROCESS==: thread; hanno un contesto ridotto, condividono lo spazio degli indirizzi

## ==MULTITHREADING==
Più thread associati ad un processo. Può quindi eseguire più compiti in maniera indipendente.
Ognuno dei thread condivide con gli altri il codice, i dati e le altre risorse allocate al processo. Pertanto:
- se un thread modifica una variabile non locale al thread, anche gli altri thread possono vedere la modifica
- se un thread apre un [[File|file]], anche gli altri thread possono usarlo

Ad ogni thread è associato:
- un descrittore: ==IDENTIFICATORE DI THREAD (TID)==
- un contatore di programma
- un insieme di registri
- uno stack
- uno stato d'esecuzione
- uno spazio di memoria per le variabili locali
Dato che le informazioni associate al thread sono poche, le operazioni di [[Processo#CONTEXT SWITCH|cambio di contesto]], di [[Processo#STATO DI UN PROCESSO|creazione e terminazione]] sono più semplici.

La programmazione multithread può quindi produrre codice più semplice ed efficiente. I kernel attuali sono normalmente multithread, in quanto il multithreading si adatta perfettamente alla programmazione nei [[Multiprocessore_multicore#SISTEMI MULTICORE|sistemi multicore]].