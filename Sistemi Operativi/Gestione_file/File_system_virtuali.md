# FILE SYSTEM VIRTUALI
==FILE SYSTEM VIRTUALI (VFS)==: presenti in UNIX, forniscono una modalità di implementazione del [[File_system|file system]] object-oriented. Il VFS gestisce un'interfaccia omogenea alle [[Chiamate_di_sistema|chiamate di sistema]] (una API) da usare in corrispondenza di tutti i tipi di file system:
- separa le operazioni standard dalla loro realizzazione su un particolare file system
- le implementazioni possono essere relative a diversi file system locali o distribuiti
- permette la rappresentazione univoca di un file su tutta la rete, tramite ==VNODE==, che corrispondono a [[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|inode]] o alle informazioni necessarie a gestire file remoti.
L'API interagisce così con l'interfaccia del file system virtuale, piuttosto che con i diversi file system reali.
![450](vfs.png)