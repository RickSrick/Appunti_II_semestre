# TIPI DI [[File|FILE]]
==TIPO==: attributo di un file che ne indica la struttura logica interna e ne permette la corretta interpretazione.
Alcuni SO gestiscono diversi tipi di file, ovvero li riconoscono in modo da manipolare i file in maniera ragionevole.
Esistono tre tecniche principali per identificare i tipi di file:
- ==ESTENSIONI==: il tipo è indicato da un suffisso del nome (DOS)
- ==ATTRIBUTO== "tipo" associato al file nella directory (Mac OS X)
- ==MAGIC NUMBER==: il tipo è indicato da un valore posto all'inizio del file (UNIX)
UNIX, oltre a usare il magic number, usa le estensioni solo come suggerimento; non vengono imposte né dipendono dal SO.
![400](tipi_file.png)

La struttura di un file può essere:
- _nessuna_: sequenza di parole o byte
- ==STRUTTURA A RECORD SEMPLICE==:
	- linee
	- record a lunghezza fissa
	- record a lunghezza variabile
- ==STRUTTURA COMPLESSA==:
	- documento formattato
	- file eseguibile rilocabile
La struttura del file viene decisa dal SO e dall'applicativo che ha creato il file.
Il tipo di un file e la corrispondente struttura logica possono essere riconosciuti e gestiti in modi diversi nei diversi SO; se il SO gestisce molti formati:
- codice di sistema più ingombrante
- incompatibilità di programmi con file di formato differente
- gestione efficiente per i formati supportati
Altrimenti, se il SO ne gestisce pochi:
- codice di sistema più snello
- formati gestiti dal programmatore