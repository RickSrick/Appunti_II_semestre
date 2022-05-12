# PREVENZIONE DEL [[Deadlock|DEADLOCK]]
- ==ALLOCAZIONE GLOBALE==: richiede tutte le [[Risorse|risorse]] che il [[Processi|processo]] necessita per il suo completamento:
	- realizzabile quando sono note esattamente le risorse utilizzate dai processi
	- permette di evitare il deadlock in un sistema di più processi, al costo di un cattivo utilizzo delle risorse
- ==ALLOCAZIONE GERARCHICA==: stabilire ordinamento delle risorse in base alla loro importanza:
	- un processo che sta usando risorse può acquisirne di più importanti
	- se vuole acquisire una risorsa meno importante rispetto a quella usata, deve prima rilasciare quest'ultima prima di richiedere quella meno importante
- ==ALGORITMO DEL BANCHIERE==

## ALGORITMO DEL BANCHIERE
Dati _n_ processi:
- ==SEQUENZA SICURA==: ordinamento dei processi tali che le richieste del processo $\text{P}_{i}$ siano soddisfacibili dalle risorse disponibili al sistema più quelle allocate ai processi $\text{P}_{j}$ con _j_ < _i_
- ==STATO SICURO==: assegnazione di risorse che ammette almeno una sequenza sicura
Le risorse vengono allocate solo se:
- la concessione non rende possibile uno stallo
- le risorse residue sono sufficienti alla terminazione del processo richiedente

Data una serie di processi $\text{P}_{i}$ e una serie di risorse $\text{R}_{j}$, si rappresenta il sistema con tre tabelle:
- risorse massime richieste dai processi
- risorse assegnate ai processi nella situazione iniziale
- risorse richieste da ogni processo
Definiamo:
- $\text{M}_{i}$: numero massimo di risorse che $\text{P}_{i}$ necessita
- $D$: risorse totali disponibili
- $\text{A}_{ij}$: numero di risorse assegnate al processo $\text{P}_{i}$ durante la fase $j$
- $\text{R}_{ij}$: numero di risorse richieste dal processo $\text{P}_{i}$ durante la fase $j$
- $\text{D}_{j}$: risorse disponibili durante la fase $j$: $\text{D}_{j} = D - \sum_i^{} \text{A}_{ij}$
Avranno concesse le risorse richieste solo i processi che possono portare a termine la propria esecuzione, ovvero quelli per cui è soddisfatta la condizione di terminazione di $\text{P}_{i}$: $\text{M}_{i} - \text{A}_{ij} = \text{R}_{ij} \le \text{D}_{j}$
Se vengono allocate le risorse richieste da $\text{P}_{i}$, questo viene eseguito fino alla sua terminazione; allora, le righe $\text{P}_{i}$ delle tabelle vengono eliminate, e le risorse che gli erano state assegnate all'inizio (riga $\text{P}_{i}$ della tabella delle risorse assegnate) si aggiungono alle richieste disponibili al sistema, $\text{D}_{j}$.
Se tutte le righe delle tabelle vengono eliminate, la riduzione è completa e il sistema non è in deadlock.

Esempio:
	![400](banchiere.png)
	![450](banchiere2.png)
	(Riga S: risorse massime del sistema / assegnate dal sistema / disponibili al sistema)
	Chiamiamo la situazione iniziale del sistema _fase 0_:
	- fase 0:
		- processo $\text{P}_{4}$ può terminare: $\text{M}_{4} - \text{A}_{4,0} = \text{R}_{4,0} \le \text{D}_{0} \rightarrow [1 1 1] - [1 1 0] = [0 0 1] \le [1 0 1]$
		- viene soddisfatta la richiesta di $\text{P}_{4}$: viene eseguito, termina e rilascia le risorse: $\text{D}_{1} = [1 0 1] + [1 1 0] = [2 1 1]$
	- fase 1:
		- processo $\text{P}_{1}$ può terminare: $\text{M}_{1} - \text{A}_{1,1} = \text{R}_{1,1} \le \text{D}_{1} \rightarrow [2 1 0] - [0 1 0] = [2 0 0] \le [2 1 1]$
		- viene soddisfatta la richiesta di $\text{P}_{1}$: viene eseguito, termina e rilascia le risorse: $\text{D}_{2} = [2 1 1] + [0 1 0] = [2 2 1]$
	- fase 2:
		- processo $\text{P}_{2}$ può terminare: $\text{M}_{2} - \text{A}_{2,2} = \text{R}_{2,2} \le \text{D}_{2} \rightarrow [2 1 1] - [1 0 0] = [1 1 1] \le [2 2 1]$
		- viene soddisfatta la richiesta di $\text{P}_{4}$: viene eseguito, termina e rilascia le risorse: $\text{D}_{3} = [2 2 1] + [1 0 0] = [3 2 1]$
	- fase 3:
		- processo $\text{P}_{3}$ può terminare: $\text{M}_{3} - \text{A}_{3,3} = \text{R}_{3,3} \le \text{D}_{3} \rightarrow [0 2 1] - [0 1 0] = [0 1 1] \le [3 2 1]$
		- viene soddisfatta la richiesta di $\text{P}_{3}$: viene eseguito, termina e rilascia le risorse: $\text{D}_{4} = [3 2 1] + [0 1 0] = [3 3 1] = D$
	Esiste una sequenza sicura, pertanto il sistema è in uno stato sicuro: non sono presenti deadlock.

