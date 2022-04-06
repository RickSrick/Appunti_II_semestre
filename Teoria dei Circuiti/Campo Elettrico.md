# CAMPO ELETTRICO
Se osservo delle cariche sorgenti in moto dovuto a una Forza di Coulomb [[Legge di Coulomb|{...}]], ottengo un campo elettrico:
$$\vec{E}(p,t)~=~\frac{d\vec{F}(p,t)}{dq}~=~\frac{1}{4\pi\epsilon_0}~\frac{q(Q)}{r^2_{QP}}~\vec{u}_{QP}$$
![LEGGE DI COULOMB|400](Legge_Di_Coulomb_1.png)

## CAMPO ELETTROSTATICO
Considero un circuito orientato chiuso qualsiasi.
La circuitazione di un campo elettrostatico su questo circuito è 0:
$$\oint_l{~\vec{E_c}~\cdot~\vec{t}~dl} = 0$$

Il ==campo elettrostatico== è quindi ==conservativo==, e che il risultato dipende solo dal punto iniziale e finale del circuito:
$$\int_{A,l}^B{\vec{E_c}(p,t)~\cdot~\vec{t}~dl} = V(A)~-~V(B)$$
$V(...)$ è detto ==potenziale elettrostatico== [[Tensione elettrica#REGIME STAZIONARIO|{...}]].

## CAMPO ELETTRICO
Quando provo a verificare se il campo elettrostatico coincide con quello elettrico, si ottiene che
$$\vec{E}(p,t)~=~\vec{E_c}(p,t)~+~\vec{E_i}(p,t)$$
$\vec{E_i}(p,t)$ rappresenta il campo elettrico indotto.

- ==Condizione elettrostatica==:
	- cariche elettriche statiche (in quiete e costanti)
	- $\vec{E}~=~\vec{E_c}$
- ==Regime stazionario==:
	- fenomeni elettromagnetici non variano nel tempo
	- $\vec{E}~=~\vec{E_c}$
- ==Condizioni variabili generiche==:
	- densità di carica e campo di corrente variabili nel tempo
	- $\vec{E}(p,t)~=~\vec{E_c}(p,t)~+~\vec{E_i}(p,t)$
	- $\vec{E_i}(p,t)$ non è conservativo