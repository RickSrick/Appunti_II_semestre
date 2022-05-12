# MEMORIA PRINCIPALE E PROCESSI
Per poter essere eseguiti, i programmi devono essere trasferiti, almeno in parte, nella memoria principale, così da "diventare" processi. Per ottenere l'aumento delle prestazioni fornito dallo [[Scheduling|scheduling]], tale memoria dev'essere condivisa.
La scelta del sistema di gestione della memoria dipende dall'architettura del sistema di calcolo del sistema.

La _memoria principale_ e i _registri_ sono gli unici dispositivi di memoria a cui la CPU può accedere direttamente:
- gli accessi ai registri richiedono un ciclo di clock
- gli accessi alla memoria principale possono richiedere più cicli, si può presentare uno stallo del processore in attesa di dati (soluzione: [[Dispositivi_di_memoria#CACHING|memoria cache]])

Le librerie dinamiche richiedono che il programma in esecuzione ne richieda il caricamento _on-the-fly_ in memoria quando serve; se il modulo della libreria è già presente in memoria non serve ricaricarlo.

Se il prossimo processo da eseguire non è in memoria e non c'è spazio sufficiente, bisogna sostituirlo ad un altro processo presente in memoria, effettuando un [[Processi#CONTEXT SWITCH|context switch]]. Può richiedere molto tempo, ma può essere ridotto se si conosce a priori la memoria necessaria.

## INPUT QUEUE
I programmi risiedono su disco sotto forma di file binari eseguibili.
==INPUT QUEUE==: insieme dei programmi che attendono di essere caricati in memoria principale per essere eseguiti:
- si seleziona uno dei programmi per il caricamento e l'esecuzione
- durante l'esecuzione, si può accedere ai suoi dati e alle sue istruzioni in memoria principale
- una volta completato, il processo libera la memoria ad esso allocata