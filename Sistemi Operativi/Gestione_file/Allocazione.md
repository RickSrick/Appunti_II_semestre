# ALLOCAZIONE
La natura ad [[Accesso_file#ACCESSO DIRETTO|accesso diretto]] dei dischi garantisce flessibilità nell'implementazione dei file. Tuttavia, bisogna allocare lo spazio del disco ai file in modo da avere uno spreco di memoria minimo e una buona rapidità di accesso.
Pertanto, esistono vari ==METODI DI ALLOCAZIONE== dello spazio su disco che descrivono come i blocchi fisici del disco vengono allocati ai file.

## ==ALLOCAZIONE CONTIGUA==
Ciascun file occupa un insieme di blocchi contigui sul disco. Per reperire il file servono quindi solo la locazione iniziale e il numero di blocchi del file. Queste informazioni vengono memorizzate in ogni [[File#ATTRIBUTI DEI FILE|elemento di directory]].
L'_accesso casuale_ (il tempo per accedere ad un blocco non dipende dalla posizione del blocco) fornisce performance ottimali. Tuttavia, questa allocazione dinamica dello spazio del disco può causare [[Frammentazione#FRAMMENTAZIONE ESTERNA|frammentazione esterna]], alla quale bisogna rispondere con la compattazione dello spazio del disco. Inoltre, bisogna conoscere a priori la dimensioni dei file, i quali non possono quindi crescere.
![400](allocazione_contigua.png)
Nei SO di nuova generazione (e.g. [[File_system|file system]] _Veritas_) il disco viene allocato con una maggiore granularità della dimensione del blocco fisico. Ciascun file consiste di uno o più ==EXTENT==: porzione di spazio contiguo, di dimensione variabile eventualmente definita dall'utente.
Inizialmente, ad ogni file viene allocato un extent; se questo non è sufficientemente grande, se ne aggiunge un altro. Ciò può portare a [[Frammentazione#FRAMMENTAZIONE INTERNA|frammentazione interna]] per extent grandi. L'elemento di directory contiene l'indirizzo iniziale dell'extent, la sua dimensione e un puntatore al primo blocco dell'extent successivo.

## ==ALLOCAZIONE CONCATENATA==
Ciascun file è costituito da una lista concatenata di blocchi, i quali possono essere sparsi ovunque nel disco. Ciascuno di loro contiene un puntatore al successivo, e il file termina quando si incontra un blocco con puntatore vuoto.
Negli elementi di directory si mantengono gli indirizzi dei blocchi iniziale e finale.
Non si ha spreco di spazio, ovvero niente frammentazione esterna. Quando necessita di un nuovo blocco per far crescere il file, il SO invoca il sottosistema per la [[Gestione_spazio_libero|gestione dello spazio libero]]. L'efficienza può essere migliorata raccogliendo i blocchi in ==CLUSTER==, aumentando però la frammentazione interna.
Nota per gli esercizi: ogni blocco contiene sia il puntatore al successivo che i dati del file; quindi, una parte del blocco (e.g. 1 byte) non dovrà essere conteggiata nel calcolare quanti blocchi destinare un file.
![400](allocazione_concatenata.png)

## ==FILE ALLOCATION TABLE (FAT)==
Variante dell'allocazione concatenata implementata in MS-DOS e OS/2. Alla FAT viene riservata una porzione di disco all'inizio di ciascun [[Struttura_disco|volume]], ha un elemento per ogni blocco del disco ed è indicizzata dal numero di blocco.
L'elemento di directory contiene il numero del primo blocco del file: l'elemento della FAT indicizzata da quel blocco contiene a sua volta il numero del blocco successivo del file; l'ultimo blocco ha come elemento nella tabella un valore speciale di fine file. I blocchi inutilizzati sono contrassegnati dal valore 0.
![550](fat.png)
Il numero di bit usati per la FAT, ovvero per indirizzare i blocchi (FAT-12, FAT-16, FAT-32...), e la dimensione dei blocchi influenza la dimensione massima di una partizione. Ad esempio, con 12 bit il file system può indirizzare al massimo $2^{12}$ = 4096 blocchi, mentre con 32 bit si possono gestire $2^{32}$ = 4.294.967.296 blocchi.
![550](fat2.png)
Nota per gli esercizi: i puntatori sono tutti contenuti nella FAT; i blocchi sono interamente destinati a contenere i dati del file, quindi la loro dimensione dev'essere conteggiata per intero per calcolare quanti blocchi destinare a un file.

## ==ALLOCAZIONE INDICIZZATA==
Per ogni file, colleziona tutti i puntatori in un ==BLOCCO INDICE==, dotato di una ==TABELLA INDICE== dotata di accesso casuale.
Negli elementi di directory si memorizzano gli indirizzi dei blocchi indice.
Permette l'accesso dinamico senza frammentazione esterna, tuttavia c'è il sovraccarico temporale che deriva dall'accesso al blocco indice.
![400](allocazione_indicizzata.png)
Ci sono varie possibilità per il mapping fra indirizzi logici e indirizzi fisici (dimensione blocco: 512 byte / word):
- ==SCHEMA CONCATENATO==: si collegano blocchi della tabella indice; il primo blocco indice contiene l'indirizzo degli indirizzi dei primi 511 blocchi del file, più un puntatore al blocco indice successivo
![600](schema_concatenato.png)
- ==INDICE A PIÙ LIVELLI==
![300](indice_livelli.png)
- ==SCHEMA COMBINATO==: misto tra blocchi allocati direttamente e blocchi indice
![400](schema_combinato.png)
	Esempio: [[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|inode]] in UNIX (4KB per blocco, indirizzi a 32 bit): in un sistema UNIX-like tradizionale, gli inode hanno:
	- 10 puntatori diretti a blocchi
	- 1 blocco con indirezione singola (in totale si possono puntare $2^{10}$ = 1K blocchi)
	- 1 blocco con indirezione doppia (in totale si possono puntare $(2^{10})^2 = 2^{20}$ = 1M blocchi)
	- 1 blocco con indirezione tripla (in totale si possono puntare $(2^{10})^3 = 2^{30}$ = 1G blocchi)
![450](inode.png)

# PRESTAZIONI DELL'ALLOCAZIONE
Il miglior metodo per l'allocazione di file dipende dal [[Accesso_file|tipo di accesso]]:
- l'allocazione contigua ha ottime prestazioni per [[Accesso_file#ACCESSO SEQUENZIALE|accesso sequenziale]], casuale e [[Accesso_file#ACCESSO DIRETTO|diretto]]
- l'allocazione concatenata si presta naturalmente all'[[Accesso_file#ACCESSO SEQUENZIALE|accesso sequenziale]]
- l'allocazione indicizzata è più complessa:
	- l'accesso ai dati del file può richiedere più accessi a disco (tre accessi nel caso di un indice a due livelli)
	- tecniche di clustering possono migliorare il [[Definizioni#MISURE|throughput]], riducendo l'overhead di CPU
Pertanto, dichiarando il tipo di accesso all'atto della creazione del file, si può selezionare il metodo di allocazione più adatto.

Anche la dimensione del file influisce sulle prestazioni:
- file piccoli $\rightarrow$ allocazione contigua
- file grandi $\rightarrow$ allocazione indicizzata