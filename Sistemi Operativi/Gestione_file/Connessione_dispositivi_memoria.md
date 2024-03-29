# CONNESSIONE DEI DISPOSITIVI DI MEMORIA
I calcolatori accedono alla memoria secondaria in tre modi:
- tramite un dispositivo connesso alla macchina
- tramite un dispositivo connesso alla rete
- in cloud

## MEMORIA SECONDARIA CONNESSA ALLA MACCHINA
Alla memoria secondaria connessa alla macchina si accede dalle _porte locali di I/O_ che sono collegate al _bus di I/O_, al quale sono connessi i dischi, che possono anche essere rimovibili.
Il trasferimento di dati in un bus è eseguito da vari tipi di [[Input_output|controllori]]:
- ==ADATTATORI==: controllori posti all'estremità del bus relativa al calcolatore
- ==CONTROLLORI DEI DISCHI==: incorporati in ciascuna unità a disco

Per eseguire un'operazione di I/O, si inserisce il comando opportuno nell'adattatore, generalmente tramite porte di [[Mappatura#MAPPATURA IN MEMORIA DELL'I O|I/O mappate in memoria]]. L'adattatore invia il comando al controllore del disco, che agisce sugli elementi elettromeccanici dell'unità per portare a termine il lavoro richiesto.
Il trasferimento dei dati nell'unità a disco avviene tra la superficie del disco e la [[Dispositivi_di_memoria#CACHING|cache]] incorporata nel controllore. Il trasferimento dei dati tra la cache e l'adattatore avviene alla velocità propria dei dispositivi elettronici.

Esempi di controllori:
- _Enhanced Integrated Drive Electronics (EIDE)_
- _Advanced Technology Attachment (ATA)_
- _Serial ATA (SATA)_
	con interfaccia ATA o SATA, al più due unità per ciascun bus di I/O
- _Universal Series Bus (USB)_
- _Fiber Channel_
	architettura seriale ad alta velocità: può gestire uno spazio di indirizzi a 24 bit, che è alla base della _storage area network (SAN)_, nella quale molti host sono connessi con altrettante unità di memorizzazione
- _Small Computer System Interface (SCSI)_
	interfaccia standard progettata per realizzare il trasferimento di dati, che permette la connessione di un massimo di 16 device

## MEMORIA SECONDARIA CONNESSA ALLA RETE
==NETWORK-ATTACHED STORAGE (NAS)==: dispositivo di memoria connesso alla rete; sistema di memoria specializzato al quale si accede in modo remoto attraverso la rete di trasmissione di dati.
Il NAS si presenta come un altro [[File_system|file system]]. I client accedono alla memoria connessa alla rete tramite un'_interfaccia RPC_, supportata da protocolli quali [[Network_file_system|NFS]] su UNIX e _CIFS_ su Windows. Le chiamate di procedura remota sono implementate per mezzo di TCP o UDP, sopra una rete IP, di solito la stessa rete che supporta tutto il traffico di dati fra client e server.
![450](nas.png)
==STORAGE AREA NETWORK (SAN)==: reti private tra server e unità di memoria secondaria, che impiegano protocolli specifici per la memorizzazione. Garantiscono flessibilità, in quanto si possono connettere alla stessa SAN molti calcolatori e molti storage array.
![550](san.png)

## MEMORIA SECONDARIA IN CLOUD
Lo ==STORAGE CLOUD== è basato su API, con programmi che le utilizzano per fornire accesso. Si impiegano le API per bilanciare le lunghe latenze e i numerosi scenari di errore.
Esempi: _Dropbox_, _Amazon S3_, _Microsoft OneDrive_, _Apple iCloud_, _Google Drive_.
![450](cloud_storage.png)
