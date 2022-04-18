## ANALISI DI UNA RETE LINEARE A REGIME STAZIONARIO
Se si considera una rete di generatori ideali o resistori ideali, è una rete di $l$ bipoli con $2l$ equazioni e $2l$ incognite.
Si ottiene quindi in seguente sistema:
$$
\begin{equation}
\begin{cases}
	\sum_{maglia}{\pm V=0}\\\\\sum_{insieme~di~taglio}{\pm I}=0\\\\V=E\\\\I=J\\\\V-RI=0
\end{cases}
\end{equation}
$$
Si tratta di un sistema di $2l$ equazioni lineari a coefficienti costanti.
Tale rete è detta ==rete lineare==.

Il sistema può essere scritto in forma matriciale:
$$
[A]
\begin{bmatrix}
V\\
I
\end{bmatrix}
=[B]
$$
I termini della matrice $A$ sono i coefficienti $+1,0,-1,-R$ del sistema di $2l$ equazioni.
I termini del vettore colonna $B$ sono i valori $0,E,J$

Se le equazioni della matrice $A$ sono indipendenti, la matrice è invertibile e la soluzione esiste ed è unica.
$$
\begin{bmatrix}
V\\
I
\end{bmatrix}
=[A]^{-1}[B]
$$
Si può quindi scrivere ogni tensione e corrente della rete come combinazione lineare mediante i coefficienti che dipendono dai termini di A:
$$
\begin{equation}
\begin{cases}
	V_h=\sum_{k=1}^{r}{a_{hk}E_k}+\sum_{k=1}^{s}{R_{hk}J_k}\\\\
	I_h=\sum_{k=1}^r{G_{hk}E_k}+\sum_{k=1}^{s}{\beta_{hk}J_k}
\end{cases}
\end{equation}
$$
ovvero, secondo la teoria della ==sovrapposizione degli effetti==:
$$
\begin{equation}
\begin{cases}
	V_h=\sum_{k=1}^{r}{V_{hE_k}}+\sum_{k=1}^{s}{V_{hJ_k}}\\\\
	I_h=\sum_{k=1}^r{I_{hE_k}}+\sum_{k=1}^{s}{I_{hJ_k}}
\end{cases}
\end{equation}
$$
Pertanto, per calcolare la tensione o corrente su un generico lato h della rete:
- Si calcola la tensione o corrente su tale lato facendo agire un solo generatore ideale (azzerando tutti gli altri)
- Si ripete il calcolo per tutti gli altri generatori ideali (uno alla volta)
- Si sommano tutti i valori così calcolati di tensione o corrente.

La sovrapposizione degli effetti non vale per il calcolo della potenza scambiata.