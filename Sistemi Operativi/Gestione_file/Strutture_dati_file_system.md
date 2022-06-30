# STRUTTURE DATI DEL [[File_system|FILE SYSTEM]]
Le funzioni del file system vengono realizzate tramite [[Chiamate_di_sistema|chiamate di sistema]] invocate attraverso l'API, che utilizzano dati, gestiti dal kernel, residenti sia su disco che su memoria.

## STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO
- ==[[Avviamento_so_memoria#BOOT BLOCK|BLOCCO DI CONTROLLO DI AVVIAMENTO]]==: contiene le informazioni per l'[[Avviamento_so_memoria|avviamento di un SO]] da quel [[Struttura_disco|volume]]; necessario se il volume contiene un SO, normalmente è il primo blocco del volume
- ==BLOCCHI DI CONTROLLO DEI VOLUMI==: contengono dettagli riguardanti la [[Struttura_disco|partizione]], quali numero totale dei blocchi e loro dimensione, contatore dei blocchi liberi e relativi puntatori
	_superblocco_ in UFS, _master file table (MFT)_ nell'[[File_system#TIPI DI FILE SYSTEM|NTFS]]
- ==[[Struttura_directory|STRUTTURE DELLA DIRECTORY]]==: usate per organizzare i file
	in UFS comprendono i nomi dei file e i numeri di [[File_system#STRATIFICAZIONE DEL FILE SYSTEM|inode]] associati
- ==FILE CONTROL BLOCK / BLOCCHI DI CONTROLLO DEI FILE (FCB)== (==INODE== in Linux): contengono informazioni sui file, quali proprietario, permessi, posizione del contenuto
	- numero di inode, permessi, dimensione, data di creazione / ultimo accesso / ultima modifica, puntatori ai blocchi di dati
	- NTFS memorizza i dati nella _master file table_ utilizzando una struttura in stile database relazionale
![400](fcb.png)

## STRUTTURE DATI DEL FILE SYSTEM RESIDENTI IN MEMORIA PRINCIPALE
- ==TABELLA DI [[Montaggio|MONTAGGIO]]==: contiene le informazioni relative a ciascun volume montato 
- ==STRUTTURA DELLE DIRECTORY==: contiene informazioni relative a tutte le directory cui i processi hanno avuto accessi di recente
- ==[[Tabelle_file_aperti|TABELLA DEI FILE APERTI]]==
- ==[[Tabelle_file_aperti|TABELLA DEI FILE APERTI PER CIASCUN PROCESSO]]==
![450](tabella_file.png)