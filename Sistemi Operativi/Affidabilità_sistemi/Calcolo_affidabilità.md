# CALCOLO DELL'[[Affidabilità|AFFIDABILITÀ]]
Si effettua un test di 10 dispositivi dello stesso tipo misurando, per ciascuno di essi, il tempo in cui si verifica un [[Guasti|guasto]].
- $\text{n}_{prod}(t)$: numero di dispositivi funzionanti al tempo $t$ (se $t = \text{t}_{0}$, numero di dispositivi al tempo iniziale $\text{t}_{0}$)
- $\text{t}_{k}$: tempo di funzionamento del dispositivo $k$ prima di un guasto
- $R(t)$: affidabilità di un dispositivo garantita per un tempo $t$
- $Q(t)$: probabilità di guasto al tempo $t$
$$
\begin{equation}
R(t) = \frac{\text{n}_{prod}(t)}{\text{n}_{prod}(\text{t}_{0})}; \quad Q(t) = 1 - R(t) = 1 - \frac{\text{n}_{prod}(t)}{\text{n}_{prod}(\text{t}_{0})}; \quad MTTF = \frac{\sum_{k} t_{k}}{10}
\end{equation}
$$
![500](calcolo_affidabilità.png)

Nel caso di sistemi riparabili è necessario considerare anche le riparazioni / sostituizioni. Per migliorare la [[Affidabilità#ALTRE DEFINIZIONI|disponibilità]] di un sistema si deve agire sia sull'affidabilità che sui tempi di riparazione.
- $\text{r}_{k}$: tempo di riparazione del dispositivo $k$
- $A$: disponiblità
$$
\begin{equation}
MTTR = \frac{\sum_{k} r_{k}}{10}; \quad A = \frac{MTTF}{MTTF + MTTR}
\end{equation}
$$
![650](calcolo_affidabilità2.png)