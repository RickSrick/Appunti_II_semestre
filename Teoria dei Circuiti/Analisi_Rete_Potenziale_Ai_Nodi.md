## METODO DEI POTENZIALI AI NODI
Si prenda una rete di GLC (o casi particolari)
Se nella rete sono presenti GLT, si calcoli l'equivalente GLC.
Si tratta di una rete lineare:
$$
\begin{equation}
\begin{cases}
	\sum_{maglia}{\pm V}=0\qquad(m=l-n+1\quad LKT)\\\\
	\sum_{insieme~di~taglio}{\pm I}=0\qquad(n-1\quad LKC)\\\\
	I=J-GV\qquad (l~equazioni~dei~GLC)
\end{cases}
\end{equation}
$$
Le tensioni si possono esprimere ricorrendo a $n-1$ potenziali ai nodi, preso un nodo come riferimento a potenziale nullo (==nodo di massa==).
$$V_n=0$$
Si esprimano le tensioni dei lati come idifferenze di potenziale:
$$V_h=\pm(V_{Nr}-V_{Ns})$$

Scartando il nodo di massa, si scrivono le LKC sugli $n-1$ nodi a cui si sono associati i potenziali. Si ottiene:
$$\sum_{insieme~di~taglio}{\pm J}=\sum_{insieme~di~taglio}{\pm G(V_{Nr}-V_{Ns})}\qquad(n-1\quad LKC)$$
Riordinando la scrittura:
$$G_{N_{kk}}V_{N_k}-\sum_{h\neq k}{G_{N_{kh}}V_{N_h}}=J_{N_k}$$
- $G_{N_{kk}}$ è la somma delle conduttanze dei lati che hanno un morsetto collegato al nodo k (==autoconduttanza di nodo==)
- $G_{N_{kh}}$ è la conduttanza fra i nodi k e h (==mutua conduttanza tra i nodi==)
- $J_{N_k}$ è la somma algebrica delle correnti impresse dei GIC collegati al nodo k