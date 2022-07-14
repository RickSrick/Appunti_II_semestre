# AVVIAMENTO DEL SO
Una volta creato, il [[Sistema_operativo#STRUTTURA DEL SISTEMA DI CALCOLO|kernel]] del SO dev'essere caricato dal computer durante la fase di ==AVVIO / BOOTING==, nella quale viene eseguito l'insieme di processi necessari per l'avvio, detto ==BOOTSTRAP==:
- un piccolo programma (==BOOTSTRAP LOADER / BOOT LOADER==) identifica la posizione del kernel
- il kernel viene caricato in memoria e avviato
- iI kernel inizializza l'hardware
- il ==ROOT [[File_system|FILE SYSTEM]]==, la [[Struttura_disco|partizione]] dove risiedono i restanti file del SO, viene attivato

Nei computer più datati, il boot loader è parte del ==BIOS==: insieme di routine software che fornisce una serie di funzioni di base per l'accesso all'hardware. È tipicamente memorizzato nella ROM e viene identificato con il termine di ==FIRMWARE==.
Questo piccolo boot loader carica un secondo boot loader memorizzato in una predeterminata posizione del disco, detta [[Avviamento_so_memoria#BOOT BLOCK|boot block]]. Quest'ultimo può completare la parte restante e caricare / avviare il kernel, oppure richiamare un altro programma di bootstrap su disco.

Recentemente, il vecchio processo multi-stage e il BIOS hanno lasciato il posto a un più efficiente metodo single-stage e al firmware ==UNIFIED EXTENSIBLE FIRMWARE INTERFACE (UEFI)==. Con il suo avvento, il funzionamento del boot loader è cambiato sostanzialmente, a cominciare dal fatto che si trova, fisicamente, nella cartella _efi_ contenuta nella relativa partizione di sistema.

## ESEMPI SPECIFICI NEI SO
- _UNIX / Linux_:
	il boot loader più conosciuto è ==GRAND UNFIED BOOTLOADER (GRAND)==:
	- inizialmente, un piccolo file system viene caricato in memoria principale per contenere driver e altri moduli del kernel necessari a far partire il vero root file system
	- una volta che il kernel è avviato e il root file system avviato, Linux crea il primo processo, _systemd_, e poi tutti gli altri man mano
- _Android_:
	il boot loader è il ==LITTLE KERNEL (LK)==
- _Windows_:
	il firmware di sistema esegue il codice nel [[Avviamento_so_memoria#BOOT BLOCK|Master Boot Record (MBR)]], che, con l'ausilio di una tabella delle partizioni, identifica quella dove si trovano kernel e driver