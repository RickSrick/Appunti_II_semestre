# ALGORITMI PER L'ALLOCAZIONE DEI FRAME
Algoritmi per l'==ALLOCAZIONE DEI FRAME==: determinano quanti frame vengono assegnati a ciascun processo
Ciascun processo richiede un numero minimo di frame, determinato dall'architettura, mentre il numero massimo è determinato dalla disponibilità di memoria.

## ALLOCAZIONE UNIFORME
Assegnare ad ogni processo la stessa quantità di frame (possibile implementarla mantenando un _pool di frame liberi_)
![[Algoritmi_sostituzione_pagina#POOL DI FRAME LIBERI]]

## ALLOCAZIONE PROPORZIONALE
Si allocano frame sulla base di:
- dimensione del processo
- priorità del processo (==ALLOCAZIONE CON PRIORITÀ==): se un processo genera page fault, si seleziona per la sostituzione uno dei suoi frame oppure un frame di un processo con priorità minore

# SOSTITUZIONE DEI FRAME
- ==SOSTITUZIONE GLOBALE==: il SO seleziona il frame da sostituire dall'insieme di tutti i frame
	- può selezionare frame di altri processi
	- un processo non può controllare la propria frequenza di page fault
	- il tempo di esecuzione di ogni processo può variare in modo significativo
- ==SOSTITUZIONE LOCALE==: il SO, per ogni processo, seleziona il frame da sostituire solo dal relativo insieme di frame allocati
	- non rende disponibili a processi che ne facciano richiesta pagine di altri processi scarsamente utilizzate
	- possibile un sottoutilizzo della memoria
La sostituzione globale garantisce un maggiore throughput, ed è implementata nei SO più diffusi.
(link a definizione throughput)

# THRASHING
Se un processo non ha abbastanza frame a disposizione, la frequenza di page fault è abbastanza alta.
==THRASHING==: un processo è costantemente occupato a spostare pagine dal disco alla memoria e viceversa.
![500](thrashing.png)

# WORKING-SET
- ==LOCALITÀ==: insieme di pagine che vengono accedute insieme e che sono contemporaneamente in uso attivo (connotazione spazio temporale)
- $\Delta$: finestra di working-set; un numero fissato di riferimenti a pagina
- $\text{WSS}_{i}$: ==WORKING-SET== del processo $\text{P}_{i}$; insieme di pagine diverse referenziate da $\text{P}_{i}$ nel più recente $\Delta$:
	- se $\Delta$ è troppo piccolo non comprende tutta la località
	- se $\Delta$ è troppo grande comprende più località
	- se $\Delta \rightarrow \infty$ comprende l'intero programma
- $D = \sum \text{WSS}_{i} \equiv$ numero totale di pagine richieste
Politica: se $D > m$ presente thrashing; occorre sospendere un processo o sottoporlo a _swapping_
![550](working-set.png)
![[Swapping#SWAPPING]]
Problema: la finestra di working-set è mobile, con riferimenti che entrano ed escono. Si approssima con un interrupt del timer e un bit di riferimento.
Esempio:
	- il timer emette un interrupt ogni 5000 unità di tempo
	- si tengono in memoria i bit per ogni pagina
	- quando si ha un interrupt del timer, si copiano i valori di tutti i bit di riferimento e si pongono a 0
	- se uno dei bit in memoria è 1, pagina nel working-set

# FREQUENZA DI PAGE FAULT
Si stabilisce una frequenza di page fault "accettabile" e si utilizza una politica di sostituzione locale; tuttavia:
- se la frequenza effettiva è troppo bassa, il processo rilascia dei frame
- se la frequenza effettiva è troppo alta, il processo acquisisce dei frame
Costituisce un approccio più diretto e intuitivo rispetto al working-set, ma hanno comunque una relazione diretta:
- il working-set cambia nel tempo
- quando si verifica un cambio di località del processo si ha un picco della frequenza di page fault
![550](frequenza_page_fault.png)

# PREPAGING
Utilizzato per ridurre il numero di page fault necessari allo startup del processo in regime di paginazione a richiesta pura.
![[Paginazione_a_richiesta#PAGINAZIONE A RICHIESTA PURA]]
==PREPAGING==: si portano in memoria tutte o alcune delle pagine necessarie al processo, prima che vengano referenziate (ad esempio, memorizzare il working-set al momento della sospensione per I/O per poi riprendere tutte le pagine che gli appartengono).
Se le pagine precaricate non vengono usate, si sprecano I/O e memoria:
- il costo dei page fault evitati è maggiore o minore del costo di prepaging relativo al caricamento delle pagine inutilizzate?
- se la percentuale delle pagine inutilizzate rispetto a quelle precaricate tende a 0, il prepaging non conviene