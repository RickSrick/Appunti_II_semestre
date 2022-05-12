# SISTEMI  MULTIPROCESSORE E MULTICORE
Fino a qualche anno fa molti sistemi utilizzavano un singolo processore general-purpose, pur inglobando molti microprocessori special-purpose. Da qualche anno, invece, i _sistemi multiprocessore_ e _multicore_ hanno iniziato a dominare il mondo della computazione, in quanto garantiscono:
- maggiore [[Definizioni#MISURE|throughput]]
- migliore economia di scala (prezzi più bassi rispetto a più sistemi monoprocessore)
- incremento dell'affidabilità (i guasti non bloccano il sistema)

## ==SISTEMI MULTIPROCESSORE==
Sistemi a ==MEMORIA CONDIVISA==, ossia sistemi in cui tutte le CPU condividono una memoria fisica comune.
![350](multiprocessore.png)
I sistemi multiprocessore attualmente in uso permettono la [[Scheduling_multiprocessore#MULTIELABORAZIONE ASIMMETRICA|multielaborazione asimmetrica]] e la [[Scheduling_multiprocessore#MULTIELABORAZIONE SIMMETRICA SYMMETRIC MULTI-PROCESSING SMP|multielaborazione simmetrica]].

## ==SISTEMI MULTICORE==
Si raggruppano diverse unità di calcolo core in un singolo chip.
Sono più efficienti, perché le comunicazioni, sul singolo chip, sono più veloci. Di conseguenza, un chip multicore usa molta meno potenza di diversi chip single-core.
![400](multicore.png)

## ==CLUSTER==
Sono simili ai sistemi multiprocessore, ma sono composti da due o più calcolatori completi, detti ==NODI==, collegati ad una memoria secondaria condivisa tramite una [[Connessione_dispositivi_memoria#MEMORIA SECONDARIA CONNESSA ALLA RETE|SAN]].
Presentano una notevole _tolleranza ai guasti / fault tolerance_. I cluster vengono impiegati nell'_high performance computing (HPC)_. Le applicazioni devono essere parallelizzate, cioè scritte per trarre vantaggio dall'architettura.
- ==CLUSTERING ASIMMETRICO==: un calcolatore rimane nello stato di attesa attiva mentre gli altri eseguono le applicazioni; il calcolatore in stand-by controlla gli altri nodi e si attiva nel caso di malfunzionamenti
- ==CLUSTERING SIMMETRICO==: tutti i nodi eseguono le applicazioni e si controllano reciprocamente.
![450](cluster.png)