# AVVIAMENTO DEL SO
==BOOTSTRAP==: insieme dei processi che vengono eseguiti da un computer durante la fase di avvio, in particolare dall'accensione fino al completo caricamento in memoria primaria del kernel del sistema operativo a partire dalla memoria secondaria.
==BIOS==: insieme di routine software che fornisce una serie di funzioni di base per l'accesso all'hardware. È tipicamente memorizzato nella ROM e viene identificato con il termine di ==FIRMWARE==. 
==BOOTSTRAP LOADER==: inizializza e controlla tutte le componenti del sistema, Procede al caricamento del kernel del SO e ne lancia l'esecuzione. Normalmente è memorizzato su [[Hard_disk_drive|disco fisso]], nel [[Avviamento_so_memoria#BOOT BLOCK|Master Boot Record]].

Quando si accende un elaboratore, occorre attendere alcuni istanti per poter iniziare a lavorare: durante questa pausa il computer carica il kernel e i programmi di sistema, che garantiscono i servizi fondamentali per l'esecuzione dei programmi utente.

Recentemente il BIOS ha lasciato il posto a un nuovo firmware: ==UEFI==. Con il suo avvanto, il funzionamento del boot loader è cambiato sostanzialmente, a cominciare dal fatto che si trova, fisicamente, nella cartella _efi_ contenuta nella relativa [[Struttura_disco|partizione]] di sistema.