# MEMORIA SECONDARIA
I dischi, che possono essere rimovibili, sono connessi al calcolatore per via del _bus di I/O_:
- _Enhanced Integrated Drive Electronics (EIDE)_
- _Advanced Technology Attachment (ATA)_
- _Serial ATA (SATA)_
- _Universal Series Bus (USB)_
- _Fiber Channel_
- _Small Computer System Interface (SCSI)_
Il trasferimento di dati in un bus è eseguito da speciali unità di elaborazione, dette ==CONTROLLORI==:
- ==ADATTATORI==: controllori posti all'estremità del bus relativa al calcolatore
- ==CONTROLLORI DEI DISCHI==: incorporati in ciascuna unità a disco

Per eseguire un operazione di I/O, si inserisce il comando opportuno nell'adattatore, generalmente tramite porte di I/O mappate in memoria. L'adattatore invia il comando al controllore del disco, che agisce sugli elementi elettromeccanici dell'unità per portare a termine il lavoro richiesto.
Il trasferimento dei dati nell'unità a disco avviene tra la superficie del disco e la cache incorporata nel controllore. Il trasferimento dei dati tra la cache e l'adattatore avviene alla velocità propria dei dispositivi elettronici.