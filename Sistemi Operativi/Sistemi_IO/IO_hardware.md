# I/O HARDWARE
Esiste un'incredibile varietà di dispositivi I/O:
- memorizzazione (e.g. [[Hard_disk_drive|HDD]])
- trasmissione (e.g. schede di rete)
- human-interface (e.g. tastiera, mouse)
Tra questi dispositivi e il computer esiste un'interfaccia:
- ==PORTA==: punto di connessione del dispositivo
- ==BUS==: ==DAISY CHAIN== o accesso diritto condiviso
	- ==PCI==: bus diffuso in computer e server (e.g. _PCI Express (PCIe)_)
	- ==BUS DI ESPANSIONE==: connette dispositivi relativamente lenti
- ==CONTROLLORE==: unità di elaborazione che gestisce porta / bus / dispositivo:
	- a volte è integrato nel dispositivo, a volte è un circuito separato (==HOST ADAPTER==)
	- contiene processori, microcodice, memoria dedicata, bus controller, etc.
	- può esserci comunicazione tra il controllore del dispositivo e quello del bus
- ==DEVICE DRIVER==:  "SO" del controllore; presente uno per ciascun controllore di device, ne guida le operazioni di I/O e garantisce un'interfaccia comune fra kernel e controllore.
![500](io_hardware.png)

Tipi di controllori:
- _Enhanced Integrated Drive Electronics (EIDE)_
- _Advanced Technology Attachment (ATA)_
- _Serial ATA (SATA)_
	con interfaccia ATA o SATA, al più due unità per ciascun bus di I/O
- _Universal Series Bus (USB)_
- _Fiber Channel_
	architettura seriale ad alta velocità: può gestire uno spazio di indirizzi a 24 bit, che è alla base della [[Connessione_dispositivi_memoria#MEMORIA SECONDARIA CONNESSA ALLA RETE|SAN]]; ha un controllore complesso, normalmente con un circuito separato (_host-bus adapter (HBA)_) collegato al bus
- _Small Computer System Interface (SCSI)_
	interfaccia standard progettata per realizzare il trasferimento di dati, che permette la connessione di un massimo di 16 device
- _Serial-Attached SCSI (SAS)_
	diffuso come interfaccia dischi