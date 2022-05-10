# CRITERI PER LO SCHEDULING
Normalmente si ottimizzano i valori medi, ma talvolta è più opportuno privilegiare i valori massimi/minimi (e.g. ridurre il [[Definizioni#MISURE|tempo massimo di risposta]] per garantire che tutti gli utenti ricevano un buon servizio).
Per i sistemi time-sharing invece è più significativo ridurre la varianza dei tempi di risposta rispetto al valore medio: un sistema con un tempo di risposta prevedibile è migliore di un sistema mediamente più rapido ma molto variabile.

## FIRST COME FIRST SERVED (FCFS)
La CPU viene assegnata al primo processo che la richiede.
La realizzazione di questo criterio si basa sull'implementazione della ready queue con una coda FIFO:
- quando un processo entra nella ready queue, si collega il suo [[Processi#STATO DI UN PROCESSO|PCB]] all'ultimo elemento della coda
- quando la CPU è libera, viene assegnata al processo che si trova in testa alla ready queue, rimuovendolo da essa
Si rischia un ==EFFETTO CONVOGLIO==: processi breve devono aspettare che processi lunghi liberino la CPU.
Esempio (processi arrivano nell'ordine indicato):
![300](fcfs.png)
![600](gantt_esempio.png)

## PRIORITÀ / SHORTEST JOB FIRST (SJF) / SHORTEST PROCESS NEXT (SPN)
Un valore intero di priorità viene associato ad ogni processo, e la CPU viene allocata al processo con la priorità più alta.
==SHORTEST JOB FIRST (SJF) / SHORTEST PROCESS NEXT (SPN)==: la priorità è rappresentata dal tempo di burst; a parità di tempo di burst, si segue il FCFS.
Può presentarsi un problema di ==STARVATION==: i processi a bassa priorità non vengono mai eseguiti. Si può risolvere tramite l'==AGING==: aumento graduale della priorità per processi che attendono da molto tempo.
Esempio con processi:
![350](priorità1.png)
Usando le priorità indicate:
![600](priorità2.png)
Usando il tempo di burst come priorità:
![600](sjf.png)

## ROUND ROBIN
A ciascun processo viene associata una piccola quantità di tempo di CPU, detta ==QUANTO DI TEMPO== e indicata con _q_ (di solito 10-100 millisecondi); dopo un quanto di tempo, il processo è obbligato a rilasciare la CPU e a tornare nella ready queue.
Se _q_ diventa grande, il Round Robin diventa simile al FCFS. Inoltre, _q_ deve rimanere grande rispetto al tempo di [[Scheduler#CONTEXT SWITCH|context switch]] (di solito inferiore a 10 microsecondi), altrimenti l'overhead diventa troppo alto.
In media si ha un tempo medio di attesa e di turnaround maggiore rispetto a SJF, ma anche un miglior tempo medio di risposta.
Esempio con processi:
![300](rr1.png)
![600](rr2.png)

## SHORTEST REMAINING TIME (SRT)
Versione preemptive di SJF: ogni volta che arriva un nuovo processo in ready queue, si individua il processo con il tempo di esecuzione rimanente più breve; se tale processo è diverso da quello attualmente in esecuzione, la CPU viene prelazionata al processo in esecuzione e assegnata al nuovo processo.
Esempio con processi:
![250](srthrrn.png)
![400](srt.png)

## HIGHEST RESPONSE RATIO NEXT
Ad ogni processo $\text{P}_{i}$ viene associato un ==FATTORE DI RISPOSTA==:
$$
\begin{equation}
\text{Fr}_{i} = \frac{\text{a}_{i} + \text{e}_{i}}{\text{e}_{i}}
\end{equation}
$$
- $\text{a}_{i}$: tempo di attesa di $\text{P}_{i}$ nella ready queue
- $\text{e}_{i}$: tempo di esecuzione stimato di $\text{P}_{i}$
Lo scheduler attiva i processi con il fattore più elevato, ovvero i processi più corti che attendono da molto.
Esempio con processi:
![250](srthrrn.png)
![650](hrrn.png)