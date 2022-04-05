# TENSIONE ELETTRICA
Consideriamo una linea $l$ orientata secondo $\vec{t}$ 

_Insert Image Here_

Si definisce tensione elettrica:
$$V(t) = \int_l{\vec{E}(p,t)~\cdot~\vec{t}~dl}\qquad[V] = V$$
Il verso di percorrenza della corrende è detto ==riferimento della tensione==.

In quanto la tensione include in $\vec{E}(p,t)$ anche il campo indotto, la tensione non è conservativa [[Campo Elettrico|{...}]], quindi ==dipende dal percorso==.
$$V_{AB}~=~\int_{A,l}^B\vec{E}(p,t)~\cdot~\vec{t}~dl$$
Esistono varie notazioni che indicano il riferimento della tensione:

_Insert Image Here_

Cambiare il riferimento della tensione equivale a cambiare il segno dle suo valore:
$$V_{BA}(t)~=~\int_{B,l}^A~\vec{E}(p,t)~\cdot~\vec{t^*}~ds~=~\int_B^A~\vec{E}(p,t)~\cdot(-\vec{t})~(-dl)~=~\int_B^A~\vec{E}(p,t)~\cdot~\vec{t}~dl~=~-V_{AB}$$
$V_{AB}$ considerata sempre sullo stesso percorso.

### LEGAME TENSIONE - LAVORO
$$V~=~\int_l{\vec{E}~\cdot~\vec{t}~dl}~=~\int_l~\frac{d\vec{F}}{dt}~\cdot~\vec{t}~dl~=~\frac{d}{dt}~\int_l~\vec{F}~\cdot~\vec{t}~dl~=~\frac{d}{dt}(L)$$
