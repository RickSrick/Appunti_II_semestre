# MEMORIA PRINCIPALE E [[Processo|PROCESSI]]
La ==MEMORIA CENTRALE== è un vettore di miliardi di parole, ciascuna con un proprio indirizzo, costruito come un array. È un deposito di dati rapidamente accessibili, condiviso dalla CPU e dai dispositivi di I/O, ma è lenta rispetto alla CPU.
Per "diventare" processi ed essere eseguiti, i programmi devono essere trasferiti, almeno in parte, dalla memoria secondaria, dove risiedono sotto forma di file binari, nella memoria principale. Per ottenere l'aumento delle prestazioni fornito dallo [[Scheduling|scheduling]], tale memoria dev'essere condivisa. Serve quindi un modulo per la gestione della memoria principale che determini cosa è contenuto in essa ad un certo istante.
La scelta del sistema di gestione della memoria dipende dall'architettura del sistema di calcolo del sistema.

Il SO è quindi responsabile delle seguenti attività connesse alla gestione della memoria centrale:
- tener traccia di quali parti della memoria sono attualmente usate e da chi
- decidere quali parti di processi caricare in memoria quando vi è spazio disponibile
- allocare e deallocare lo spazio di memoria secondo necessità

La _memoria principale_ e i _registri_ sono gli unici dispositivi di memoria a cui la CPU può accedere direttamente:
- gli accessi ai registri richiedono un ciclo di clock
- gli accessi alla memoria principale possono richiedere più cicli, si può presentare uno stallo del processore in attesa di dati (soluzione: [[Dispositivi_di_memoria#CACHING|memoria cache]])

Se il prossimo processo da eseguire non è in memoria e non c'è spazio sufficiente, bisogna sostituirlo ad un altro processo presente in memoria, effettuando un [[Processo#CONTEXT SWITCH|context switch]]. Può richiedere molto tempo, ma può essere ridotto se si conosce a priori la memoria necessaria.

## ==CICLO DI FETCH-DECODE-EXECUTE==
Dinamica generale di funzionamento dei processori dei computer:
- preleva (_fetch_) un'istruzione dalla memoria primaria
- l'istruzione viene decodificata (_decode_) interpretata
- l'istruzione viene eseguita (_execute_) combinandola coi dati relativi all'istruzione stessa.
In questo modo il processore esegue sequenzialmente istruzioni che danno vita a [[Thread|thread]] e processi, sotto la supervisione del SO attraverso lo [[Scheduler|scheduler]].

## ==[[Scheduling|INPUT QUEUE]]==
Insieme dei programmi che attendono di essere caricati in memoria principale per essere eseguiti:
- si seleziona uno dei programmi per il caricamento e l'esecuzione
- durante l'esecuzione, si può accedere ai suoi dati e alle sue istruzioni in memoria principale
- una volta completato, il processo libera la memoria ad esso allocata