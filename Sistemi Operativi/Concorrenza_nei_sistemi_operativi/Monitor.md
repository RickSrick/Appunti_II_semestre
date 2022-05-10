# MONITOR
Nonostante i semafori rappresentino un meccanismo pratico ed efficace per sincronizzare i processi, il loro uso scorretto può generare problemi difficili da individuare, in quanto si manifestano solo in presenza di particolari sequenze di esecuzione. Per semplificare la gestione della mutua esclusione, si definiscono i ==MONITOR==:
- per effettuare l'allocazione di risorse tramite monitor, un processo deve richiamare una routine interna al monitor
- la mutua esclusione è rigidamente forzata ai confini del monitor stesso, al quale può accedere solo un processo alla volta

Tuttavia, tale definizione di monitor non è sufficientemente potente per modellare alcuni schemi di sincronizzazione per permettere ad un processo di attendere, causa occupazione della risorsa richiesta, dopo l'ingresso al monitor.
Per questo si dichiarano apposite _variabili condition_.
(link a processo)
![400](monitor.png)
![400](monitor2.png)

## ==VARIABILE CONDITION==
Variabile $x$ che può essere usata solo in relazione alle operazioni $x.wait()$ e $x.signal()$, e dotata di una coda di processi:
- $x.wait()$: il processo chiamante si mette nella coda d'attesa di $x$, rimanendo al di fuori del monitor, e vi rimane finchè un altro processo non chiama $x.signal()$
- $x.signal()$: il processo chiamante attiva un processo sospeso della coda di $x$, in modo tale che possa accedere al monitor

Un processo utilizza una variabile condition interna al monitor per attendere il verificarsi di una certa condizione, uscendo dal monitor nel frattempo. Pertanto, il monitor ne associa una per ogni situazione che potrebbe portare un processo a mettersi in attesa. Un processo può quindi uscire dal monitor mettendosi in attesa su una variabile monitor oppure completando il codice protetto dal monitor.
In particolare, se il processo $P$ invoca $x.signal()$ sulla variabile condition $x$ ed esiste un processo $Q$ in coda a quella variabile:
- ==SEGNALARE E ATTENDERE / SIGNAL AND WAIT==: $Q$ entra nel monitor e $P$ attende fuori dal monitor che $Q$ abbia terminato o si metta in attesa su una variabile condition
- ==SEGNALARE E PROSEGUIRE / SIGNAL AND CONTINUE==: $Q$ attende che $P$ lasci il monitor o si metta in attesa ($wait()$) su una condition
Dato che $P$ era già in esecuzione nel monitor, segnalare e proseguire sembra più ragionevole, però quando $P$ termina, la condizione attesa da $\mathrm{Q}$ potrebbe non essere più valida. Una terza alternativa di compromesso potrebbe essere che $P$ lascia il monitor volontariamente subito dopo aver invocato $signal()$.
![350](monitor3.png)