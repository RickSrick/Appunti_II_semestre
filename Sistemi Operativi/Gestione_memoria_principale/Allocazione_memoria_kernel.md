# ALLOCAZIONE DELLA MEMORIA AL [[Sistema_operativo#STRUTTURA DEL SISTEMA DI CALCOLO|KERNEL]]
Il kernel, per allocare la propria memoria, attinge ad una riserva di memoria libera diversa dalla lista dei [[Paginazione|frame]] usata per i processi utente:
- il kernel richiede memoria per strutture dati dalle dimensioni variabili (serve un uso oculato della memoria per evitare sprechi: in molti SO, codice e dati del kernel non sono soggetti a [[Paginazione|paginazione]])
- parti della memoria del kernel devono essere contigue perchè alcuni dispositivi accedono direttamente alla memoria fisica senza l'interfaccia della [[Memoria_virtuale|memoria virtuale]], come i dispositivi di I/O

## ==ALLOCATORE-POTENZA-DI-2==
Utilizza un segmento di dimensione fissa, composto da pagine fisicamente contigue: ==BUDDY SYSTEM==. Alloca memoria in blocchi di dimensioni pari a potenze di 2; la quantità richiesta viene arrotondata alla più piccola potenza di 2 che la contiene.
Quando si richiede meno memoria di quella che costituisce il segmento corrente, questo viene diviso in due segmenti gemelli di identica dimensione.
Esempio:
	si ha a disposizione un segmento da 256 KB, ma il kernel richiede 21 KB:
	- si divide il segmento in due segmenti $A_{L}$ e $A_{R}$, ciascuno di 128 KB
	- si divide uno dei due segmenti in $B_{L}$ e $B_{R}$, ciascuno di 64 KB
	- si divide uno dei due segmenti in $C_{L}$ e $C_{R}$, ciascuno da 32 KB, uno dei quali viene utilizzato per soddisfare la richiesta
![400](allocatore_potenza_2.png)

## ==ALLOCAZIONE A LASTRA==
==LASTRA/SLAB==: insieme di uno o più frame fisicamente contigui.
==CACHE==: insieme di una o più lastre contigue (contiguità non richiesta nelle nuove versioni di Linux).
Ciascuna categoria di strutture dati del kernel ([[Processo#STATO DI UN PROCESSO|PCB]], [[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|descrittori di file]], [[Semafori|semafori]], etc.) è dotata di una sola cache, e ciascuna cache è popolata da istanze della relativa struttura dati. Le istanze vengono create in anticipo, nelle varie lastre associate alla loro cache, per poi essere assegnate ad un processo / file / etc. e successivamente rilasciate quando non servono più.
![400](allocazione_lastra.png)
Stati di una lastra:
- _piena_: tutti gli oggetti contrassegnati come usati
- _vuota_: tutti gli oggetti contrassegnati come liberi
- _parzialmente occupata_: la lastra contiene oggetti sia usati che liberi
Quando una lastra diventa piena, un nuovo oggetto viene allocato in una lastra completamente vuota; se non ci sono lastre vuote, si alloca una nuova lastra e la si appende in fondo alla cache opportuna (==CACHE GROW==).

Questo metodo offre due benefici principali:
- non si provoca [[Frammentazione|frammentazione]], in quanto si può calcolare la dimensione di ogni lastra in base a quella degli oggetti rappresentati
- le richieste di memoria possono essere soddisfatte velocemente, in quanto gli oggetti sono creati in anticipo per poi essere allocati dalla cache e restituiti alla cache velocemente