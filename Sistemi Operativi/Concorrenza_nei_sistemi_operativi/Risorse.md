# RISORSE
==RISORSA==: astrazione che rappresenta un'entità necessaria al processo per svolgere il proprio lavoro (può essere sia l'output di un altro processo che spazio di memoria).
Vari tipi di risorse:
- ==CONDIVISIBILI==: possono essere usate da più processi in parallelo (e.g. RAM)
- ==NON CONDIVISIBILI==: non possono essere usate da più processi in parallelo (e.g. stampante)
- ==CONSUMABILI==: non riutilizzabili (e.g. messaggi, segnali, interrupt, batteria)
- ==NON CONSUMABILI==: possono essere riutilizzate (e.g. core di CPU, file)

Il protocollo di accesso alle risorse da parte dei thread prevede:
- ==RICHIESTA== (se la richiesta non può essere soddisfatta subito, il processo deve attendere il rilascio della risorsa richiesta da parte del thread che la trattiene)
- ==UTILIZZO==
- ==RILASCIO==

### PREEMPTION / PRELAZIONE
==PREEMPTION / PRELAZIONE==: rimozione forzata di una risorsa (==SOTTRAIBILE==) ad un processo (e.g. CPU sottratta ad un processo a bassa priorità se uno a priorità maggiore ne ha bisogno)