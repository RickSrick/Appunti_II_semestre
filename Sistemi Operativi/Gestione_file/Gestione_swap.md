# GESTIONE SWAP
==AREA DI SWAP==: area di memoria su [[Hard_disk_drive|disco]] usata dai meccanismi di [[Memoria_virtuale|memoria virtuale]] come estensione della memoria centrale. L'obiettivo principale nella sua progettazione e realizzazione è fornire la migliore produttività per il sistema di memoria virtuale.
Lo spazio di swap può essere ricavato all'interno del normale [[File_system|file system]] o, più comunemente, si può trovare in una [[Struttura_disco|partizione]] separata del disco.

## AREA DI SWAP IN LINUX
L'area di swap, in Linux, è utilizzata solo per la ==MEMORIA ANONIMA==: dati che non corrispondono a file.
Linux permette l'istituzione di una o più ==AREE DI AVVICENDAMENTO==: serie di moduli di 4 KB, detti ==SLOT DELLE PAGINE==, la cui funzione è quella di conservare le pagine avvicendate. Queste aree possono essere istituite sia in file che in una [[Struttura_disco|partizione raw]].
Ogni area dispone di una ==MAPPA DI AVVICENDAMENTO==: array di contatori interi, ciascuno dei quali corrisponde ad uno slot dell'area:
- se un contatore vale 0, la pagina che gli corrisponde è disponibile
- se un contatore vale _n_ diverso da 0, la pagina che gli corrisponde fa parte dello spazio degli indirizzi virtuali di _n_ processi
![500](area_swap.png)