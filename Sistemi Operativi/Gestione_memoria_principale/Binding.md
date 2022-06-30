#  BINDING
==BINDING==: associazione di istruzioni e dati ad indirizzi di memoria.
Può avvenire in fase di:
- _compilazione_: se si conosce la posizione in memoria del processo a priori, si può generare codice ==ASSOLUTO==; se cambia la locazione iniziale dev'essere ricompilato
- _caricamento_: se non si conosce posizione in memoria del processo a priori, serve generare codice ==RILOCABILE==: il compilatore genera indirizzi relativi che vengono convertiti in indirizzi assoluti dal [[Linker_loader|loader]]; se cambia la locazione iniziale dev'essere ricaricato in memoria
- _esecuzione_: il processo può essere spostato da una locazione di memoria all'altra in run-time: codice ==DINAMICAMENTE RILOCABILE==
	- il codice contiene solo riferimenti relativi a se stesso
	- la locazione finale di un riferimento ad un indirizzo di memoria effettuato dentro il codice è sconosciuta finchè non lo si compie
	- necessita di opportuno hardware per mappare gli indirizzi: [[Registri_base_limite|registri base e limite]], [[Tabella_delle_pagine|tabella delle pagine]]

Prima di essere eseguiti, i programmi passano attraverso stadi diversi con diverse rappresentazioni degli indirizzi:
- ==SIMBOLICI==: indirizzi presenti nel codice sorgente (e.g. nomi di variabili)
- ==RILOCABILI==: indirizzi associati a quelli simbolici dal compilatore (e.g. calcolati a partire dalla locazione della prima istruzione del programma)
- ==ASSOLUTI==: indirizzi di memoria fisica associati a quelli rilocabili dal [[Linker_loader|linker/loader]]
![650](binding.png)