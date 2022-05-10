# MONTAGGIO
Un [[File_system|file system]] dev'essere ==MONTATO== prima di poter essere acceduto dai processi di un sistema. Un file system _unmounted_ può essere montato in un _mount point_ prescelto.
Alcuni SO richiedono un file system prefissato; altri ne supportano diversi e sondano le strutture dei dispositivi per determinare i tipi di file system presenti, eventualmente montandoli automaticamente in fase di boot.

Per montare un file system, si fornisce al SO il nome del dispositivo da montare, sotto forma di [[Struttura_disco|volume]] e pathname, e la locazione che dovrà assumere nella struttura del file system (_mount point_).
Una volta montato, il file system risulta accessibile a programmi e utenti in modo trasparente e diventa parte integrante del [[Struttura_directory|grafo delle directory]]. La directory su cui viene montato un file system può non essere vuota, ma dal momento in cui si effettua il montaggio i dati contenuti in essa diventano inaccessibili fino all'operazione di _unmount_.
![650](montaggio.png)

I sistemi MAC e Windows rilevano tutti i dispositivi all'avvio della macchina e montano automaticamente tutti i file system in essi contenuti. Nei sistemi UNIX-like, invece, i file system devono essere montati esplicitamente.
In Linux: $/etc/fstab$ è il file di configurazione di sistema per la descrizione statica dei dispositivi di memoria collegati al computer il cui mount deve essere effettuato all'avvio. Nelle ultime versioni si effettuano anche montaggi automatici.