# AVVIAMENTO DEL SO
==BOOTSTRAP==: insieme dei processi che vengono eseguiti per caricare il SO nella fase d'avvio.

All'accensione del computer il programma di bootstrap (==BOOTLOADER==) viene caricato dal ==BIOS==. Viene eseguito dall'accensione fino al completo caricamento del kernel del SO in memoria principale; dopodichè il controllo della macchina passa al SO. Normalmente il bootloader è memorizzato su disco fisso, nel Master Boot Record (MBR).

Il BIOS è tipicamente memorizzato nella ROM e viene identificato col nome di ==FIRMWARE==. È un insieme di routine software che fornisce una serie di funzioni base per l'accesso base all'hardware:
- inizializza e controlla tutte le componenti di sistema
- procede al caricamento del kernel del SO e ne lancia l'esecuzione
- 
Recentemente, il BIOS sta lasciando il posto a un nuovo firmware, ==UEFI==, che si trova nella cartella _efi_ nella relativa partizione di sistema.