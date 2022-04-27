### I/O / CPU BOUND
==PROCESSO I/O BOUND==: processo con lunghe fasi di attesa I/O e fasi di esecuzioni brevi
==PROCESSO CPU BOUND==: processo che utilizzano in modo intensivo le risorse CPU e poche o nulle risorse I/O

### CPU / I/O BURST
==CPU BURST==: cicli di esecuzione della nella CPU
==I/O BURST==: cicli di attesa ai dispositivi di I/O
I CPU burst si susseguono agli I/O burst per tutta la vita di un processo.
![200](burst.png)

### MISURE
==THROUGHPUT / PRODUTTIVITÀ==: numero di processi che completano la loro esecuzione nell'unità di tempo
==TEMPO DI ATTESA==: tempo passato dal processo in attesa nella ready queue
==TEMPO DI BURST==: tempo speso nei cicli di CPU e I/O burst
==TEMPO DI TURNAROUND==: tempo impiegato per l'esecuzione di un processo = tempo di attesa + tempo di burst
==TEMPO DI RISPOSTA==: tempo che intercorre tra la sottomissione di una richiesta e la prima risposta prodotta

### DIAGRAMMA DI GANTT
==DIAGRAMMA DI GANTT==: istogramma che illustra una data pianificazione di processi, includendo i tempi di inizio e fine di ognuno di loro
Esempio:
![600](gantt_esempio.png)