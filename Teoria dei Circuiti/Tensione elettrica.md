# TENSIONE ELETTRICA
Consideriamo una linea $l$ orientata secondo $\vec{t}$ 

![CONDUTTORE FILIFORME|350](Tensione_Elettrica_1.png)

Si definisce tensione elettrica:
$$V(t) = \int_l{\vec{E}(p,t)~\cdot~\vec{t}~dl}\qquad[V] = V$$
Il verso di percorrenza della corrende è detto ==riferimento della tensione==.

In quanto la tensione include in $\vec{E}(p,t)$ anche il campo indotto, la tensione non è conservativa [[Campo Elettrico|{...}]], quindi ==dipende dal percorso==.
$$V_{AB}(t)~=~\int_{A,l}^B\vec{E}(p,t)~\cdot~\vec{t}~dl$$
Esistono varie notazioni che indicano il riferimento della tensione:
- Al posto dei pedici, si mette un segno $+$ in corrispondenza del punto di inizio e un $-$ in corrispondenza al punto di fine

![TENSIONE ELETTRICA NOTAZIONE 1|400](Tensione_Elettrica_2.png)
- Riferimento dato da una freccia con vertice diretto verso il punto d'inizio

![TENSIONE ELETTRICA NOTAZIONE 2|400](Tensione_Elettrica_3.png)

Cambiare il riferimento della tensione equivale a cambiare il segno dle suo valore:
$$V_{BA}(t)~=~\int_{B,l}^A~\vec{E}(p,t)~\cdot~\vec{t^*}~ds~=$$$$\qquad\qquad\qquad=~\int_B^A~\vec{E}(p,t)~\cdot(-\vec{t})~(-dl)~=$$$$\qquad\quad=~\int_B^A~\vec{E}(p,t)~\cdot~\vec{t}~dl~=$$$$=~-V_{AB}\qquad\quad$$
$V_{AB}$ considerata sempre sullo stesso percorso.


### REGIME STAZIONARIO

Nel caso ci si trovi a regime stazionario, otteniamo che il campo elettrico indotto è nullo, pertanto il campo elettrico è uguale al campo elettrostatico e quindi, a regime stazionario, la tensione è una differenza di potenziale [[Campo Elettrico#CAMPO ELETTROSTATICO|{...}]]:
$$V_{AB}~=~V(A)-V(B)$$


### LEGAME TENSIONE - LAVORO
$$V~=~\int_l{\vec{E}~\cdot~\vec{t}~dl}~=$$$$\qquad=~\int_l~\frac{d\vec{F}}{dt}~\cdot~\vec{t}~dl~=$$$$\qquad\quad=~\frac{d}{dt}~\int_l~\vec{F}~\cdot~\vec{t}~dl~=$$$$=~\frac{d}{dt}(L)\qquad$$
