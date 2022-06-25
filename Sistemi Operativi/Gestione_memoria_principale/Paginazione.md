# PAGINAZIONE
Si divide la memoria fisica in blocchi di dimensione fissa (potenza di 2, nei processori attuali compresi nell'intervallo 8 KB - 4 MB): ==FRAME/PAGINE FISICHE==.
Si divide la memoria logica in blocchi della stessa dimensione: ==PAGINE==.
![500](paginazione_1.png)
![500](paginazione_2.png)

Si ottiene così uno spazio degli [[Indirizzi_logici_fisici|indirizzi logici]] totalmente separato da quello degli [[Indirizzi_logici_fisici|indirizzi fisici]].
Per eseguire un processo che impiega _n_ pagine, serve trovare _n_ frame liberi prima di caricarlo, anche non contigui.
Si impiega una ==[[Tabella_delle_pagine|TABELLA DELLE PAGINE]]== per tradurre gli indirizzi logici negli indirizzi fisici corrispondenti.

## INDIRIZZI LOGICI NELLA PAGINAZIONE
Gli indirizzi logici generati dalla CPU vengono divisi in due parti:
- ==NUMERO DI PAGINA (p)==: viene impiegato come indice nella tabella delle pagine per ricavarne l'indirizzo base del frame nella memoria fisica
- ==OFFSET NELLA PAGINA (d)==: viene combinato con l'indirizzo base del frame per ricavare l'indirizzo fisico corrispondente

## PAGINAZIONE E FRAMMENTAZIONE
Con questo metodo si elimina la [[Frammentazione#FRAMMENTAZIONE ESTERNA|frammentazione esterna]], rimanendo con solo quella [[Frammentazione#FRAMMENTAZIONE INTERNA|interna]] (relativa all'ultimo frame assegnato).
Esempio:
	Dimensione della pagina: 2048 byte
	Dimensione del processo: 72766 byte
	Spazio da assegnare dal processo: 35 pagine + 1086 byte
	Frammentazione interna di (2048 - 1086) = 962 byte
Nel caso peggiore frammentazione interna di 1 byte (contenuto in 1 frame), nel caso medio di mezzo frame
Nonostante ciò, frame piccoli non sono sempre preferibili:
- la tabella delle pagine consuma memoria
- I/O più efficiente per pagine/frame grandi (la loro dimensione cresce nella storia dei SO)

## ==PAGE FAULT==
Situazione in cui un processo fa riferimento ad una pagina non presente in memoria principale. Il SO risponde al page fault trasferendo la pagina richiesta in memoria, sospendendo il processo nel mentre.
Se la memoria fisica è piena, bisogna scaricare una pagina della memoria. Per decidere quali, si implementano ==[[Algoritmi_sostituzione_pagina|ALGORITMI DI SOSTITUZIONE PAGINA]]== basati su alcuni parametri. Le informazioni necessarie a questi algoritmi sono memorizzati in alcuni bit presenti in ogni elemento della tabella delle pagine.

## DIMENSIONE DELLE PAGINE
Criteri per determinare la dimensione delle pagine:
- dimensione della tabella delle pagine
- sovraccarico (overhead) di I/O
- numero di page fault
- dimensione ed efficienza della [[Tabella_delle_pagine#REGISTRI ASSOCIATIVI|TLB]]
- frammentazione
==TLB REACH==: quantità di memoria accessibile via TLB
Idealmente, il _[[Algoritmi_allocazione_frame#WORKING-SET|working-set]]_ di ogni processo dovrebbe essere contenuto nella TLB, altrimenti si verificano molti page fault e il tempo di esecuzione diventa proibitivo.

Aumentare le dimensioni delle pagine potrebbe portare ad un incremento della frammentazione.
Si possono prevedere pagine di diverse dimensioni e permettere l'utilizzo di quelle più grandi ai processi che le richiedono, senza aumentare la frammentazione.

## PAGINAZIONE E MEMORIA VIRTUALE
Non sempre un processo necessita della presenza di tutti i suoi frame in memoria; questo consente di implementare meccanismi di ==[[Memoria_virtuale#MEMORIA VIRTUALE|MEMORIA VIRTUALE]]==: si scrivono su disco blocchi di memoria (pagine) da caricare in memoria principale solo quando servono.