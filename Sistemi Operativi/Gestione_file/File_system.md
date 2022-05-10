# FILE SYSTEM
==FILE SYSTEM==: struttura logica con cui il SO gestisce i [[File|file]].
Tutti i moderni SO gestiscono l'archiviazione di file in _modo gerarchico_: ==HIERARCHICAL FILE SYSTEM (HFS)==; questa organizzazione non ha alcun legame con l'effettiva posizione dei file nella memoria di massa.
![650](file_system.png)
Più in dettaglio, il file system è responsabile della gestione dei file nella memoria di massa:
- struttura i dati in file
- organizza i file in [[Directory|cartelle / directory]]
- fornisce all'utente funzioni di alto livello per agire sui file, nascondendo le operazioni effettive di allocazione della memoria e di accesso in lettura e scrittura
Il file system garantisce pertanto una gestione dei file indipendente dalle caratteristiche fisiche dei dispositivi che costituiscono la memoria di massa, un'astrazione utile sia per i programmi che per gli utenti.

- File system _per l'utente_: definizione dell'aspetto di file e directory e loro operazioni
- File system _per il SO_: scelta di algoritmi e strutture dati che mettano in corrispondenza il file system logico con i dispositivi fisici di memorizzazione 

## TIPI DI FILE SYSTEM
Esistono diversi tipi di file system e non è raro che i sistemi operativi ne prevedano più di uno.
- CD-ROM: _ISO 9660_
- UNIX: _UNIX File System (UFS)_ che si fonda sul _File System Berkeley Fast (FFS)_
- Windows: _FAT, FAT32, FAT64, NTFS_
- Linux: _extended file system (ext2, ext3, ext4...)_, ne supporta più di quaranta tipi diversi
- _File system in USErspace (FUSE)_: progetto open source, rilasciato sotto la licenza GPL e LGPL, volto alla realizzazione di un modulo per il kernel Linux che permetta agli utenti non privilegiati di creare un proprio file system senza scrivere codice a livello kernel

## REALIZZAZIONE DEL FILE SYSTEM
Il file system risiede nella memoria secondaria:
- fornisce una semplice interfaccia verso i dispositivi di memorizzazione secondaria, realizzando il mapping fra indirizzi logici e fisici
- fornisce la possibilità di accedere al disco in maniera efficiente, per memorizzare e recuperare rapidamente le informazioni
I dischi sono un mezzo conveniente per la memorizzazione di file, in quanto:
- si possono riscrivere localmente
- è possibile accedere direttamente a qualsiasi blocco di informazione del disco, ovvero a qualsiasi file, sia in modo [[Accesso_file#ACCESSO SEQUENZIALE|sequenziale]] che [[Accesso_file#ACCESSO DIRETTO|diretto]]
Le operazioni di I/O su disco avvengono con _granularità di blocco_: ciascun blocco è composto da uno o più settori. I dispositivi fisici vengono controllati per mezzo di _device driver_.

## STRATIFICAZIONE DEL FILE SYSTEM
Il file system è ==STRATIFICATO==, cioè organizzato in livelli, ognuno dei quali si serve esclusivamente delle funzioni dei livelli inferiori per crearne di nuove. Questa struttura è utile per ridurre la complessità e la ridondanza, ma aggiunge overhead e può diminuire le performance.
![250](file_system_strati.png)
- ==CONTROLLO DELL'I/O / DRIVER DEI DISPOSITIVI==: traducono istruzioni di alto livello in specifiche sequenze di bit, scritte in specifiche locazioni di memoria del controllore, che guidano l'hardware di I/O nel compiere una specifica operazione in una data locazione
- ==FILE SYSTEM DI BASE==: invia comandi generici ai driver di dispositivo per leggere / scrivere blocchi fisici su disco, gestisce il buffer del dispositivo e la cache che conserva i metadati
- ==MODULO DI ORGANIZZAZIONE DEI FILE==: traduce gli indirizzi logici di blocco e contiene il modulo per la [[Gestione_spazio_libero|gestione dello spazio libero]]
- ==FILE SYSTEM LOGICO==: gestisce i ==METADATI==, ovvero tutte le strutture del file system eccetto i dati veri e propri memorizzati nei file:
	- mantiene le strutture di file tramite i [[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|File Control Block]]
	- gestisce le directory
	- gestisce protezione e sicurezza

