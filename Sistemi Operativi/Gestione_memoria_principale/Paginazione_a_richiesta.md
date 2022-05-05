# [[Paginazione|PAGINAZIONE]] SU RICHIESTA

## PAGER
I processi possono essere caricati per intero su RAM durante il loading oppure si può caricare una certa pagina in memoria solo quando è necessaria.
==PAGER==: modulo del SO che si occupa della paginazione su richiesta

## PAGE DEMANDING
Quando un processo sta per essere caricato in memoria, il pager ipotizza quali pagine saranno usate prima che il processo venga di nuovo rimosso dalla memoria.
Così, anzichè caricare in memoria tutto il processo, il pager trasferisce in memoria solo le pagine che ritiene necessarie.
Serve quindi una _MMU_ con ulteriori funzionalità.
![[MMU#MMU]]

## BIT DI VALIDITÀ
- Se la pagina è già presente in memoria, si prosegue l'esecuzione normalmente
- altrimenti, dev'essere localizzata in memoria secondaria e caricata in memoria principale senza alterare il flusso del programma e senza che il programmatore debba cambiare il codice
Serve un meccanismo per distinguere le pagine presenti in memoria da quelle residenti su disco: aggiungere alla tabella delle pagine un ==BIT DI VALIDITÀ==:
- _v_: pagina in memoria
- _i_: pagina non valida o non residente in memoria
[[Tabella_delle_pagine]]
![500](bit_di_validita1.png)
Inizialmente posto a _i_ per tutte le pagine; durante la traduzione degli indirizzi, se il bit di validità vale _i_ viene generata una trap al SO: ==PAGE FAULT==.
Il SO consulta una tabella interna delle pagine (conservata con il ==TCB==) per decidere se si tratta di riferimento non valido (abort) o pagina non in memoria.
![[Processi#STATO DI UN PROCESSO]]
Nel secondo caso:
- si individua la pagina richiesta su disco
- si seleziona un frame libero: se esiste lo si usa, altrimenti si applica un _algoritmo di sostituzione_ per selezionare un _frame vittima_
- si sposta la pagina nel frame (schedulando un operazione di I/O) e si scrive la pagina vittima su disco
- aggiorna la tabella delle pagine (impostando il bit a _v_ / _i_ ) e dei frame (marcando come occupato il frame utilizzato)
- riavvia l'operazione interrotta
![500](bit_di_validita2.png)

## PAGINAZIONE A RICHIESTA PURA
==PAGINAZIONE A RICHIESTA PURA==: avviare l'esecuzione di un processo senza pagine in memoria:
- quando il SO carica nel contatore di programma l'indirizzo della prima istruzione, si verifica un page fault
- il processo prosegue generando page fault finchè vengono caricate in memoria tutte le pagine necessarie

## SOVRALLOCAZIONE
==SOVRALLOCAZIONE==: durante l'esecuzione di un processo utente si verifica un page fault, ma non vi sono frame liberi per caricare la pagina richiesta in memoria.
Soluzione: ==SOSTITUZIONE DI PAGINA==: si trova una pagina in memoria che non risulta attualemente utilizzata e si sposta sul disco.
Bisogna scegliere un _algoritmo di sostituzione_ che scelega un frame _vittima_ e che provochi il minor numero possibile di page fault.
![[Algoritmi_sostituzione_pagina]]

La sovrallocazione si verifica quando è richiesta più memoria di quella effettivamente disponibile; la si può prevenire modificando la routine di servizio del page fault, includendo la sostituzione delle pagine.
Si impiega un ==BIT DI MODIFICA/DIRTY BIT== per ridurre il sovraccarico dei trasferimenti di pagine: solo le pagine modificate vengono riscritte su disco.