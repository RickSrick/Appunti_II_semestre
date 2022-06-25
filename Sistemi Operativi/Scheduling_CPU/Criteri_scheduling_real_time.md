# CRITERI PER LO [[Scheduling|SCHEDULING]] PER [[Sistemi_real-time|SISTEMI REAL-TIME]]
## ==RATE-MONOTONIC SCHEDULING / PRIORITÀ PROPORZIONALE ALLA FREQUENZA==
Modello statico di attribuzione delle priorità con [[Risorse#PREEMPTION PRELAZIONE|prelazione]]:
- la priorità è inversamente proporzionale al periodo; si assegnano priorità più elevate ai processi che fanno uso della CPU più frequentemente
- se arriva un processo con una priorità maggiore di quella del processo attualmente in esecuzione, la CPU viene prelazionata al processo in esecuzione e assegnata al nuovo processo
È un ==ALGORITMO OTTIMALE==: se non è in grado di pianificare l'esecuzione di una serie di processi rispettando i vincoli temporali, nessun altro algoritmo che assegna priorità statiche ci riuscirà.
Esempio con processi $\text{P}_{1}$ e $\text{P}_{2}$, periodi $\text{T}_{1}$ = 50 e $\text{T}_{2}$ = 100, tempi di elaborazione $\text{C}_{1}$ = 20 e $\text{C}_{2}$ = 35:
![600](rms.png)
Nel caso di eventi periodici, se esistono $m$ eventi e se l'evento $i$ arriva con periodo $\text{P}_{1}$ e richiede $\text{C}_{i}$ secondi di tempo di CPU, il carico può essere gestito solo se:
$$
\begin{equation}
\sum_{i=1}^{m} \frac{C_{i}}{P_{i}} \leq 1
\end{equation}
$$
Un sistema real-time che rispetta questo criterio è detto ==SCHEDULABILE==.
Tuttavia, è possibile dimostrare che, per ogni sistema con processi periodici, il funzionamento dello scheduling con priorità proporzionale alla frequenza è garantito se:
$$
\sum_{i=1}^{m} \frac{C_{i}}{P_{i}} \leq m \cdot\left(2^{1 / m}-1\right)
$$
Esempio: per $m=2$, il carico della CPU non può superare I'83%.

## ==EARLIEST-DEADLINE-FIRST (EDF)==
Schedula i processi assegnando dinamicamente le priorità a seconda delle scadenze, usando anche la prelazione.
Quando un processo diventa eseguibile:
- deve annunciare la sua prossima scadenza allo scheduler
- la priorità viene calcolata dinamicamente in base alla scadenza; più vicina la scadenza, più alta la priorità
- la priorità di altri processi già presenti nel sistema viene modificata per riflettere la scadenza del nuovo processo
Si applica anche a processi non periodici e con tempo di elaborazione variabile.
È un algoritmo ottimale, e porta idealmente ad un utilizzo della CPU pari al 100%.
Esempio con processi $\text{P}_{1}$ e $\text{P}_{2}$, periodi $\text{T}_{1}$ = 50 e $\text{T}_{2}$ = 80, tempi di elaborazione $\text{C}_{1}$ = 20 e $\text{C}_{2}$ = 35:
![600](edf.png)