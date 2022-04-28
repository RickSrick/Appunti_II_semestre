# CHIAMATE DI SISTEMA
Le ==SYSTEM CALL / CHIAMATE DI SISTEMA== forniscono l'interfaccia tra i processi e i servizi offerti dal SO. Sono realizzate con linguaggi di alto livello (e.g. C o C++). Normalmente, vengono richiamate dai processi attraverso le ==APPLICATION PROGRAMMING INTERFACE (API)== piuttosto che per invocazione diretta. Alcuni API molto diffuse sono la _Win64 API_ per Windows, la _POSIX API_ per i sistemi POSIX-based (POSIX: Portable Operating System Interface per UNIX), la _Java API_ per la Java Virtual Machine.
![450](system_call.png)

Normalmente, ad ogni system call è associato un numero; l'interfaccia alle chiamate di sistema mantiene una tabella indicizzata dal numero, effettua la chiamata e ritorna lo stato del sistema dopo l'esecuzione (ed eventuali valori restituiti). L'utente non deve conoscere i dettagli implementativi delle system call, ma solo la modalità di funzionamento dell'API ed eventualmente il compito svolto dalle chiamate. Questa intermediazione delle API garantisce anche la portabilità delle applicazioni.

Spesso l'informazione necessaria alla chiamata di sistema include dei parametri. Esistono tre metodi per passarli:
- passaggio di parametri nei registri
- salvare i parametri in un blocco di memoria e passare l'indirizzo del blocco in un registro come parametro (approccio seguito da Linux, per più di 5 parametri, e Solaris)
- _push_ dei parametri nello stack da parte del programma, recuperati dal SO con un _pop_
![450](system_call3.png)

Esempi di funzioni assolte dalle system call:
- controllo dei processi
- gestione delle informazioni
- comunicazione
- protezione
- gestione dei file
- gestione dei dispositivi di I/O