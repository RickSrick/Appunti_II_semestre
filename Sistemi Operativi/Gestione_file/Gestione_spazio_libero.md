# GESTIONE DELLO SPAZIO LIBERO
Per tener traccia dello spazio libero su disco, il sistema conserva una ==LISTA DELLO SPAZIO LIBERO==. Per creare un file occorre:
- cercare nella lista dello spazio libero la quantità di spazio necessaria ed allocarla al nuovo file
- aggiornare al contenuto della lista
Quando si cancella un file, si aggiungono allo lista dello spazio libero i blocchi di disco precedentemente assegnati al file.
La lista dello spazio libero può non essere realizzata come una lista.

## IMPLEMENTAZIONE DELLA LISTA DELLO SPAZIO LIBERO
### ==VETTORE DI BIT / BITMAP==
Se il bit $[i]$ è uguale a 1 il blocco $[i]$ è libero, se è uguale a 0 il blocco è occupato:
- per calcolare il numero del primo blocco libero si scorre il vettore, cercando il primo bit diverso da 0
- buone prestazioni se il vettore è conservato in memoria centrale
- è adatta per gestire file contigui
![500](bitmap.png)
### ==LISTA CONCATENATA==
Si collegano tutti i blocchi liberi mediante puntatori e si mantiene un puntatore alla testa della lista in memoria centrale:
- non si spreca spazio, in quanto si conserva solo un puntatore
- non è necessario attraverso tutta la lista, poichè di solito la richiesta è relativa ad un singolo blocco
- non facile da usare per ottenere spazio contiguo
- nella [[Allocazione#FILE ALLOCATION TABLE FAT|FAT]], il conteggio dei blocchi liberi è incluso nella struttura dati per l'allocazione e non richiede quindi un metodo di gestione separato
![300](spazio_libero.png)
### GROUPING / CONTEGGIO
- ==GROUPING==: realizzazione di una lista di blocchi
	il primo blocco contiene gli indirizzi di _n_ blocchi liberi, dei quali _n-1_ sono effettivamente liberi e l'_n_-esimo contiene gli indirizzi di altri _n_ blocchi, e così via
- ==CONTEGGIO==: si mantiene una lista contenente un indirizzo del disco, che indica un blocco libero, e un contatore, che indica da quanti altri blocchi liberi contigui è seguito
	utile in quanto lo spazio viene spesso allocato e liberato in modo contiguo (e.g. [[Allocazione#ALLOCAZIONE CONTIGUA|allocazione contigua, extent]] e [[Allocazione#ALLOCAZIONE CONCATENATA|clustering]])
![600](schema_concatenato.png)
### ==TRIM==
Comando ==ADVANCED TECHNOLOGY ATTACHMENT (ATA)== che consente al SO di informare un SSD su quali blocchi di dati può cancellare in quanto non sono in uso. (link a SSD) Il TRIM è complementare al [[Struttura_directory#DIRECTORY A GRAFO GENERALE|garbage collection]]:
- elimina la copiatura di pagine di dati scartate o non valide durante il processo di garbage collection per risparmiare tempo e migliorare le prestazioni dell'unità SSD
- l'SSD ha un minor numero di pagine da spostare durante la garbage collecition, il che riduce il numero totale di cicli di programmazione / cancellazione sul supporto flash NAND e prolunga la vita dell'SSD
(link a flash NAND?)

## PRESTAZIONI
Se, nell'elemento di directory, si mantiene la data di ultimo accesso ad un file per consentire all'utente di risalire all'ultima volta che un file è stato letto, ogni volta che si apre un file per la lettura. si deve leggere e scrivere anche l'elemento della directory ad esso associato.
Se si aumenta la dimensione dei puntatori, si aumenta la dimensione della memoria gestibile via file system, ma si aumenta anche la dimensione delle strutture dati necessarie per I'allocazione e la gestione dello spazio libero.

Le prestazioni dipendono da:
- mantenere dati e metadati "vicini" nel disco
- disporre di una [[Buffer_cache|buffer cache]]
- scritture _sincrone_, talvolta richieste dalle applicazioni oppure necessarie al SO:
	- impossibilità di buffering / caching: l'operazione di scrittura su disco deve essere completata prima di proseguire l'esecuzione
	- le scritture _asincrone_, che sono le più comuni, sono invece bufferizzabili e più veloci
- utilizzo di svuotamento / riempimento delle cache per ottimizzare l'[[Accesso_file#ACCESSO SEQUENZIALE|accesso sequenziale]]