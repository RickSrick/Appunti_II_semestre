# THREAD
==THREAD==: suddivisione di un processo in due o più sottoprocessi; unità base d'uso della CPU.
Ogni thread comprende un ==IDENTIFICATORE DI THREAD (TID)==, un contatore di programma, un insieme di registri e uno stack. Condivide con gli altri thread del processo a cui appartiene le sezioni del codice, dei dati e le altre risorse allocate al processo.

==HEAVYWEIGHT PROCESS==: processo tradizionale, composto da un solo thread (un processo è pesante in riferimento al contesto che lo definisce)
==LIGHTWEIGHT PROCESS==: thread; hanno un contesto ridotto, condividono lo spazio degli indirizzi

Poichè i thread appartenenti ad uno stesso processo condividono codice, dati e risorse:
- se un thread modifica una variabile non locale al thread, anche gli altri thread possono vedere la modifica
- se un thread apre un file, anche gli altri thread possono usarlo

Un ==PROCESSO MULTITHREAD== può eseguire più compiti in maniera indipendente. Possiede un program counter per ogni thread, a differenza dei processi single thread, che hanno un unico program counter.
La programmazione multithread può quindi produrre codice più semplice ed efficiente. I kernel attuali sono normalmente multithread, in quanto il multithreading si adatta perfettamente alla programmazione nei [[Multiprocessore_multicore#SISTEMI MULTICORE|sistemi multicore]].