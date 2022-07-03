# [[Paginazione|PAGINAZIONE]] SU RICHIESTA
I processi possono essere caricati per intero su RAM durante il loading, oppure si può implementare la ==PAGINAZIONE SU RICHIESTA / PAGE DEMANDING==: si carica una certa pagina in memoria solo quando è necessaria, ovvero quando viene referenziata. Il modulo del SO che si occupa di questa tecnica viene detto ==PAGER==.

Quando un processo sta per essere caricato in memoria, il pager ipotizza quali pagine saranno usate prima che il processo venga di nuovo rimosso dalla memoria. Così, anzichè caricare in memoria tutto il processo, il pager trasferisce in memoria solo le pagine che ritiene necessarie.
Serve quindi una [[MMU]] con ulteriori funzionalità:
- se la pagina è già presente in memoria, si prosegue l'esecuzione normalmente
- altrimenti, dev'essere localizzata in memoria secondaria e caricata in memoria principale senza alterare il flusso del programma e senza che il programmatore debba cambiare il codice

## ==BIT DI VALIDITÀ==
Serve un meccanismo per distinguere le pagine presenti in memoria da quelle residenti su disco. Si aggiunge alla [[Tabella_delle_pagine|tabella delle pagine]] un _bit di validità_:
- _v_: pagina in memoria
- _i_: pagina non valida o non residente in memoria
![500](bit_di_validita1.png)
Inizialmente viene posto a _i_ per tutte le pagine; durante la traduzione degli indirizzi, se il bit di validità vale _i_ si verifica un [[Paginazione#PAGE FAULT|page fault]].
Il SO consulta una tabella interna delle pagine (conservata con il [[Processo#STATO DI UN PROCESSO|PCB]]) per decidere se si tratta di riferimento non valido (abort) o pagina non in memoria.
Nel secondo caso:
- si individua la pagina richiesta su disco
- si seleziona un frame libero: se esiste lo si usa, altrimenti si applica un [[Algoritmi_sostituzione_pagina|algoritmo di sostituzione]] per selezionare un _frame vittima_
- si sposta la pagina nel frame (schedulando un operazione di I/O) e si scrive la pagina vittima su disco
- aggiorna la tabella delle pagine (impostando il bit a _v_ / _i_ ) e dei frame (marcando come occupato il frame utilizzato)
- riavvia l'operazione interrotta
![500](bit_di_validita2.png)

## ==PAGINAZIONE A RICHIESTA PURA==
Avviare l'esecuzione di un processo senza pagine in memoria:
- quando il SO carica nel contatore di programma l'indirizzo della prima istruzione, si verifica un page fault
- il processo prosegue generando page fault finchè vengono caricate in memoria tutte le pagine necessarie

## ==SOVRALLOCAZIONE==
Fenomeno per il quale durante l'esecuzione di un processo utente si verifica un page fault, ma non vi sono frame liberi per caricare la pagina richiesta in memoria.
Soluzione: ==SOSTITUZIONE DI PAGINA==: si trova una pagina in memoria che non risulta attualmente utilizzata e si sposta sul disco.
Bisogna scegliere un [[Algoritmi_sostituzione_pagina|algoritmo di sostituzione]] che scelega un _frame vittima_ e che provochi il minor numero possibile di page fault.

La sovrallocazione si verifica quando è richiesta più memoria di quella effettivamente disponibile; la si può prevenire modificando la routine di servizio del page fault, includendo la sostituzione delle pagine.
Si impiega un ==BIT DI MODIFICA/DIRTY BIT== per ridurre il sovraccarico dei trasferimenti di pagine: solo le pagine modificate vengono riscritte su disco.