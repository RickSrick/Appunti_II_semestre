# TABELLA DELLE PAGINE
==TABELLA DELLE PAGINE==: traduce gli indirizzi logici negli indirizzi fisici corrispondenti.
![500](tabella_delle_pagine.png)
Risiede nella memoria centrale; di norma, presenete una tabella per processo.
==PAGE-TABLE BASE REGISTER==: punta all'inizio della tabella
==PAGE-TABLE LENGTH REGISTER==: indica la dimensione della tabella
Così ogni accesso a dati o istruzioni richiede due accessi in memoria, uno per la tabella e uno per i dati cercati; per risolvere il problema, ==REGISTRI ASSOCIATIVI==.

Associare una tabella delle pagine ad ogni processo può occupare troppa memoria.
Possibili soluzioni:
- [[Paginazione_gerarchica|paginazione gerarchica]]
- [[Tabella_delle_pagine_hash|tabella delle pagine hash]]
- [[Tabella_delle_pagine_invertita|tabella delle pagine invertita]]

# REGISTRI ASSOCIATIVI
==REGISTRI ASSOCIATIVI / TRANSLATION LOOK-ASIDE BUFFER (TLB)==: si effettua una ricerca parallela veloce su una piccola tabella.
Dato l'indirizzo (p,d), se p è nel registro associativo, si recupera il numero del frame dal registro, altrimenti lo si recupera dalla tabella delle pagine in memoria.

==ADDRESS SPACE IDENTIFIER (ASID)==: dato memorizzato per ciascun elemento da alcune TLB per identificare univocamente il processo a cui appartiene la pagina:
- prima di calcolare l'indirizzo fisico, si confronta l'ASID del processo in esecuzione e quello della pagina virtuale richiesta; se non c'è corrispondenza, ==TLB-MISS==
- permette alla TLB di contenere pagine di processi diversi contemporaneamente; altrimenti, la TLB dev'essere svuotata (==FLUSH==) ad ogni context switch, per contenere le pagine del processo in esecuzione
In occasione di un TLB-miss, la pagina dev'essere spostata nella TLB per poi accedervi:
- bisognerà applicare politiche di sostituizione per gli elementi della TLB
- alcuni elementi possono essere vincolati

Nelle architetture hardware attuali, le ricerche nella TLB fanno parte della pipeline di istruzioni:
- nessuna penalizzazione nelle prestazioni
- la TLB dev'essere piccola
- presenti TLB separate per dati e istruzioni

# PROTEZIONE DELLA MEMORIA
- ==BIT DI PROTEZIONE==: uno o più bit associati a ciascun frame per determinare in che modalità si può accedere alla pagina (lettura/scrittura/esecuzione)
	mentre si mappa l'indirizzo logico all'indirizzo fisico, si verifica la modalità di accesso a tale pagina; se l'accesso viola le modalità codificate nei bit di protezione si causa una trap al SO
- ==BIT DI VALIDITÀ==: un bit associato a ciascun frame:
	- valore valido: pagina presente nello spazio degli indirizzi logici del processo, pagina legale
	- valore non valido: pagina assente dallo spazio degli indirizzi logici del processo, pagina illegale