# DIRECTORY
## INFORMAZIONI NELLA DIRECTORY
- _Nome_
- _Tipo
- _Indirizzo
- _Lunghezza attuale
- _Lunghezza massima
- _Data ultimo accesso
- _Data ultima modifica
- _ID del proprietario
- _Informazioni di protezione_

## OPERAZIONI SULLA DIRECTORY
- _Ricerca di un file_: possibilità di scorrere la directory per reperire l'elemento associato ad un particolare file:
	- nomi simili possono corrispondere a relazioni logiche fra i contenuti dei file
	- capacità di reperire tutti i file il cui nome soddisfi una particolare espressione
- _Creazione di un file_: aggiunta del record descrittivo del file alla directory
- _Cancellazione di un file_: rimozione del record descrittivo del file dalla directory
- _Elenco dei contenuti di una directory_: possibilità di elencare tutti i file di una directory ed il contenuto degli elementi della directory associati ai file
- _Ridenominazione di un file_: possibilità di modificare il nome di un file (che dovrebbe essere significativo del contenuto) a fronte di cambiamenti del contenuto stesso o di uso del file
- _Attraversamento del file system_: possibilità di accedere ad ogni directory e ad ogni file in essa contenuto, visitandone l'intero "organigramma"

## REALIZZAZIONE DELLA DIRECTORY
L'organizzazione della [[Struttura_directory|struttura di directory]] deve garantire:
- _efficienza_: capacità di reperire file rapidamente
- _nominazione_ convienente per gli utenti:
	- due utenti possono utilizzare nomi uguali per file diversi
	- lo stesso file può avere diversi nomi
- _grouping_: raggruppamento dei file sulla base di proprietà logiche

Implementazione della directory:
- _lista lineare_ di nomi di file con puntatori ai blocchi dati:
	- semplice da implementare, tramite array o lista concatenata
	- esecuzione onerosa dal punto di vista del tempo di ricerca (complessità lineare nel numero di elementi inclusi nella directory)
	- _lista ordinata_: migliora il tempo di ricerca, ma l'ordinamento dev'essere mantenuto ad ogni inserimento e cancellazione; utile per produrre l'elenco ordinato di tutti i file contenuti nella directory
- _tabella hash_: lista lineare con struttura hash:
	- migliora il tempo di ricerca nella directory
	- inserimento e cancellazione hanno complessità costante se non si verificano _collisioni_ (due nomi di file generano lo stesso indirizzo hash nella tabella)
	- dimensione fissa e necessità di rehash
![650](directory_hash.png)