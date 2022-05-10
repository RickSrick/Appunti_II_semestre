# ALGORITMI PER LA SOSTITUZIONE DELLE [[Paginazione|PAGINE]]
Algoritmi per la ==SOSTITUZIONE DELLE PAGINE==: scelgono quali [[Paginazione|frame]] sostituire in caso di necessità per minimizzare la quantità di [[Paginazione#PAGE FAULT|page fault]].
Gli algoritmi per la sostituzione delle pagine vengono valutati eseguendoli su una particolare stringa di riferimenti a memoria (==REFERENCE STRING==) e contando il numero di page fault provocati su quella stringa:
	- stringa costituita dai soli numeri di pagina, non indirizzi completi
	- accessi multipli alla stessa pagina non provocano page fault
	- i risultati dipendono significativamente dal numero di frame a disposizione
Esempio di stringa _s_: _7 0 1 2 0 3 0 4 2 3 0 3 0 3 2 1 2 0 1 7 0 1_

## FIRST IN - FIRST OUT (FIFO)
Implementato mediante una coda FIFO relativa alle pagine residenti in memoria: si sostituisce la pagina in testa alla coda.
Esempio con stringa _s_ e 3 frame disponibili per processo:
![550](fifo.png)

## ANOMALIA DI BELADY
Esempio di FIFO con stringa _1 2 3 4 1 2 5 1 2 3 4 5_, 3 frame:
![400](belady1.png)
Esempio di FIFO con stringa _1 2 3 4 1 2 5 1 2 3 4 5_, 4 frame:
![400](belady2.png)
==ANOMALIA DI BELADY==: aumentando il numero di frame aumenta il numero di page fault
Perchè accade con il FIFO?
- un processo richiede consecutivamente un insieme di pagine in maniera ciclica
- l'insieme delle pagine richieste ciclicamente ha una dimensione uguale o maggiore del numero di frame fisici liberi
- le sequenze cicliche sono distanziate in modo tale che FIFO "perda memoria" delle pagine accedute in precedenza
- può capitare che FIFO stronchi di continuo le pagine accedute al passo successivo
- con il numero di frame può aumentare anche il numero di page fault

## ALGORITMO OTTIMO (OPT)
Sostituire la pagina che non verrà usata per il periodo di tempo più lungo.
Esempio con stringa _s_ e 3 frame disponibili per processo:
![550](opt.png)
È il minimo possibile per la stringa _s_, ma come si può conoscere l'identità delle pagine richieste se non si conosce il futuro? Non si può; infatti questo algoritmo è di solo interesse teorico: viene usato per misurare le prestazioni comparative di algoritrmi implementabili.

## LEAST RECENTLY USED (LRU)
Si rimpiazza la pagina che non è stata usata per più tempo (occorre associare ad ogni pagina il momento dell'ultimo accesso).
Esempio con stringa _s_ e 3 frame disponibili per processo:
![550](lru.png)
(prestazioni migliori del FIFO ma peggiori dell'OPT)
OPT e LRU sono ==ALGORITMI "A PILA"==, che non soffrono dell'anomalia di Belady. Tuttavia, LRU pressuppone la presenza di hardware dedicato, e rimane comunque un algoritmo lento.

## VARIANTI DELL'LRU
- ==IMPLEMENTAZIONE CON CONTATORE==:
	- ciascuna pagine ha un contatore
	- ogni volta che si fa riferimento ad una pagina si copia il momento in cui è stato effettuato il riferimento nel contatore
	- quando si deve rimuovere una pagina si analizzano i contatori per scegliere quale pagine rimuovere (necessaria la ricerca lineare sulla tabella delle pagine)
- ==IMPLEMENTAZIONE CON STACK==:
	- si mantiene uno stack di numeri di pagina tramite lista doppiamente concatenata
	- ogni volta che si fa riferimento ad un pagina si sposta la pagina in cima allo stack (non serve più fare ricerche per scegliere la pagina da rimuovere, ma mantenere lo stack aggiornato ha un costo)
- ==BIT DI RIFERIMENTO==:
	- si associa un bit ad ogni pagina, inizialmente a 0
	- ogni volta che si fa riferimento ad una pagina si pone il bit a 1
	- si rimpiazza la pagina il cui bit di riferimento vale 0, se zero (non si conosce l'ordine di accesso alle pagine)
	- possibile registrare i bit di riferimento ad intervalli regolari in un registro a scorrimento ($\mathrm{p}_{i}$ con registro di scorrimento _11000100_ acceduta più recentemente di $\mathrm{p}_{j}$ con valore 01100101)

## SECONDA CHANCE (CLOCK ALGORITHM)
Si basa sul FIFO, con l'aggiunta di un bit di riferimento.
Quando la pagina riceve una seconda chance, il bit di riferimento viene azzerato ed il tempo di arrivo viene aggiornato al tempo attuale:
- se la pagina da rimpiazzare in ordine di clock ha il bit di riferimento a 0 viene rimpiazzata
- se la pagina da rimpiazzare in ordine di clock ha il bit di riferimento a 1:
	- si pone il bit a 0
	- si lascia la pagina in memoria
	- si rimpiazza la pagina successiva in ordine di clock in base alle stesse regole
![550](clock.png)

## VARIANTI DELLA SECONDA CHANCE
- ==ALGORITMO SECONDA CHANCE MIGLIORATO==:
	- si considera la coppia (_bit_riferimento_, _bit_modifica_)
	- possibili 4 casi:
		- (0,0): non recentemente usata né modificata; è la scelta migliore per la sostituzione
		- (0,1): non usata recentemente ma modificata; dev'essere salvata su disco
		- (1,0): usata recentemente ma non modificata; probabilmente verrà acceduta di nuovo a breve
		- (1,1): usata recentemente e modificata; probabilmente verrà acceduta di nuovo a breve e dev'essere salvata su disco prima di essere sostituita
	- si sostituisce la prima pagina che si trova nella classe (0,0)
	- azzera sempre il bit di riferimento nella ricerca della pagina da sostituire

## ALGORITMI CON CONTEGGIO
Si mantiene un contatore del numero di riferimenti effettuati ad ogni pagina.
- ==LEAST FREQUENTLY USED (LFU)==: si rimpiazza la pagina col valore minimo del contatore
- ==MOST FREQUENTLY USED (MFU)==: si rimpiazza la pagina col valore massimo del contatore (presuppone che la pagina col valore minimo del contatore sia stata spostata recentemente in memoria e quindi deve essere ancora impiegata)
L'implementazione è costosa e le prestazioni sono scadenti.

## POOL DI FRAME LIBERI
Si mantiene un pool di frame liberi; ci sono due modi di gestire un page fault:
- si seleziona un frame vittima, ma prima di trascriverlo su disco si procede alla copia della pagina richiesta in un frame del pool (il processo può essere riavviato rapidamente senza attendere la fine del salvataggio su memoria di massa del frame vittima)
- prima di accedere alla memoria di massa si controlla se la pagina richiesta è ancora presente nel pool dei frame liberi (non serve alcuna operazione di I/O)

In generale, possibile _ottimizzare le scritture_: si mantiene una lista delle pagine modificate e, ogni volta che il dispositivo di paginazione è inattivo, si sceglie una pagina modificata, la si salva su disco e si reimposta il suo bit di modifica. Aumenta la probabilità che, al momento della selezione della vittima, questa non abbia subito modifiche e non debba essere trascritta su disco.