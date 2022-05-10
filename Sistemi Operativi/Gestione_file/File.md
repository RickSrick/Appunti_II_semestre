# FILE
==FILE==: spazio di indirizzi logici contigui, insieme di informazione correlate e registate in memoria secondaria a cui è stato assegnato un nome.
Dal punto di vista dell'utente, è la più piccola porzione di memoria secondaria indirizzabile logicamente; i dati possono essere scritti in memoria secondaria solo all'interno di un file.
Dal punto di vista del SO, i file vengono mappati su dispositivi fisici di memorizzazione non volatili.

## STRUTTURA DEL FILE
- Unità di memorizzazione logica
- Collezione di informazioni correlate
- ==[[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|FILE CONTROL BLOCK]]==: struttura dati del kernel che "descrive" il file

## ATTRIBUTI DEI FILE
- ==NOME==: identificativo del file per l'utente
- ==IDENTIFICATIVO==: etichetta unica, sotto forma di numero progressivo, che identifica il file all'interno del [[File_system|file system]]
- ==[[Tipi_struttura_file|TIPO]]== (necessario per sistemi che supportano tipi differenti)
- ==LOCAZIONE==: puntatore al dispositivo di memorizzazione e alla posizione dei dati sul dispositivo
- ==DIMENSIONE== attuale del file
- ==PROTEZIONE==: parametri di controllo per l'accesso in lettura, scrittura ed esecuzione del file
- ==ORA, DATE E IDENTIFICAZIONE DELL'UTENTE== (dati necessari alla sicurezza del sistema e per il controllo dell'uso)
Alcuni file system più recenti supportano anche gli ==ATTRIBUTI ESTESI== dei file, tra cui la codifica dei caratteri del file e le funzioni di sicurezza come la _checksum_. Non sono parte del file a cui vengono associati, ma sono gestiti separatamente dal file system. Ognuno di essi viene infatti identificato da una coppia (nome, valore) per permettere il reperimento delle informazioni.
Le informazioni sui file sono conservate nella struttura di _[[Directory|directory]]_, che risiede sulla memoria secondaria. Un elemento di directory consiste di un nome di file e di un identificatore unico, che a sua volta individua gli altri attributi. Un elemento di directory può avere una dimensione maggiore di 1 KB.

## OPERAZIONI SUI FILE
- ==CREAZIONE==
	- reperire lo spazio per memorizzare il file all'interno del file system
	- creare un nuovo elemento nella directory in cui registrare le informazioni del file
- ==SCRITTURA==
	- chiamata al sistema con nome del file e puntatore ai dati da scrivere come parametri
	- reperimento del file nel file system
	- scrittura dei dati nella posizione indicata dal _puntatore di scrittura_ e aggiornamento del puntatore
- ==LETTURA==
	- chiamata al sistema con nome del file e indirizzo di memoria dove trascrivere i dati letti come parametri
	- reperimento del file nel file system
	- lettura dei dati nella posizione indicata dal _puntatore di lettura_ e aggiornamento del puntatore
- ==POSIZIONAMENTO NEL FILE / FILE SEEK==
	- reperimento del file nel file system
	- aggiornamento del puntatore alla posizione corrente
	- nessuna operazione di I/O
- ==CANCELLAZIONE==
	- reperimento del file nel file system
	- si rilascia lo spazio allocato al file e si elimina il corrispondente elemento della directory
- ==TRONCAMENTO==
	- cancellazione del contenuto del file, che mantiene immutati tutti gli attributi (esclusa la dimensione)
	- si rilascia lo spazio allocato al file
- ==IMPOSTAZIONE DEGLI ATTRIBUTI
	- reperimento / aggiornamento del relativo elemento di directory
Altre operazioni sui file si ottengono mediante combinazione delle operazioni di base. Esempio: operazione di copia:
- creazione di un nuovo file
- lettura del file da copiare
- scrittura nel nuovo file
Quasi tutte le operazione richiedono una ricerca dell'elemento associato al file all'interno della struttura della directory. Il SO mantiene in memoria centrale una tabella contenente informazioni su tutti i file aperti, ovvero la _[[Tabelle_file_aperti|tabella dei file aperti]]_.

## SALVAGUARDIA DELLE INFORMAZIONI
La salvaguardia delle informazioni contenute in un sistema di calcolo è fondamentale per l'integrità e l'usabilità del sistema:
- ==AFFIDABILITÀ==: salvaguardia dai danni fisici, assicurata dalla _ridondanza_
- ==PROTEZIONE==: salvaguardia da accessi impropri, ottenute mediante il _controllo degli accessi_
Il proprietario / creatore del file dev'essere in grado di controllare chi può accedere al file e quali ==TIPI DI ACCESSO== siano leciti:
- lettura
- scrittura
- esecuzione
- append
- cancellazione
- elencazione degli attributi