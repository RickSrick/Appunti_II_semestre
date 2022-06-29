# ALGORITMI DI [[Scheduling_disco|SCHEDULING DEL DISCO]]
Tutt gli ==ALGORITMI DI SCHEDULING DEL DISCO== presenti verranno testati sulla coda di richieste per i cilindri (0-199): _98, 183, 37, 122, 14, 124, 65, 67_, con la [[Hard_disk_drive|testina]] inizialmente posizionata sul cilindro _53_.

## ==FIRST COME FIRST SERVED (FCFS)==
Viene soddisfatta la prima richiesta che arriva. È un algoritmo intrinsecamente equo, ma possono verificarsi grandi oscillazioni.
Test: movimento totale della testina pari a 640 cilindri:
![450](fcfs_disco.png)

## ==SHORTEST [[Hard_disk_drive#MISURE|SEEK TIME]] FIRST (SSTF)==
Seleziona la richiesta di accesso con seek time minimo in relazione alla posizione corrente della testina. È una forma di [[Criteri_scheduling#PRIORITÀ SHORTEST JOB FIRST SJF SHORTEST PROCESS NEXT SPN|SJF]]; può causare l'attesa indefinita di alcune richieste. Inoltre, non è un algoritmo ottimo.
Test: movimento totale della testina pari a 236 cilindri:
![450](sstf.png)
	spostandosi dal cilindro 53 al 37, e poi al 14, prima di invertire la marcia per servire le altre richieste, si riduce la distanza a 208 cilindri: non è un algoritmo ottimo.

## ==SCAN / ALGORITMO DELL'ASCENSORE==
Il braccio della testina si muove da un estremo all'altro del disco, servendo sequenzialmente le richieste; giunto ad un estremo inverte la direzione di marcia e, conseguentemente l'ordine di servizio. Per questo è chiamato anche _algoritmo dell'ascensore_.
Se gli accessi sono distribuiti uniformemente, quando la testina inverte il proprio movimento, la maggior densità di richiesta si ha all'estremo opposto del disco, e tali richieste avranno anche i tempi più lunghi di attesa di servizio.
Test: movimento totale della testina pari a 236 cilindri:
![450](scan.png)

## ==LOOK==
Variante di SCAN che ferma la testina dopo che l'ultima richiesta è stata completata, piuttosto che raggiungere il cilindro più interno / esterno.

## ==C-SCAN==
La testina si muove da un estremo all'altro del disco servendo sequenzialmente le richieste, come lo SCAN, ma quando raggiunge l'ultimo cilindro ritorna immediatamente all'inizio del disco, senza servire alcuna richiesta durante il viaggio di ritorno.
Questo algoritmo, che considera i cilindri come organizzati seconda una lista circolare, con l'ultimo cilindro adiacente al primo, garantisce un tempo d'attesa più uniforme rispetto a SCAN.
Test: movimento totale della testina pari a 383 cilindri:
![450](c-scan.png)

## ==C-LOOK==
Il braccio della testina serve l'ultima richiesta in una direzione e poi inverte il movimento, senza necessariamente arrivare al termine del disco. Questa è una versione ottimizzata, e normalmente implementata, di C-SCAN.
Test: movimento totale della testina pari a 353 cilindri:
![450](c-look.png)

# ALGORITMI A CONFRONTO
Le prestazioni dipendono dal numero e dal tipo di richieste di I/O per l'unità a disco, le quali possono essere influenzate dal [[Allocazione|metodo di allocazione di file]] e [[Directory|directory]]. L'algoritmo di scheduling dovrebbe rappresentare un modulo separato del SO, in modo da poter essere facilmente rimpiazzato qualora le caratteristiche del sistema di calcolo dovessero cambiare.
SSTF è comune e ha un comportamento naturale, mentre LOOK e C-LOOK forniscono prestazioni migliori in sistemi che utilizzano intensamente le unità a disco, in quanto garantiscono una minor probabilità di attesa indefinita. Rappresentano entrambi scelte ragionevoli per un'implementazione standard.