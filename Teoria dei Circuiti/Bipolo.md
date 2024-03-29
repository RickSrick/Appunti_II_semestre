# BIPOLO

N-Polo con $n = 2$.

![](N-Poli)

![BIPOLO|500](Images/Bipolo_1.png)

In ogni istante, la corrente entrante ad un terminale è uguale alla corrente uscente all'altro terminale, pertanto il bipolo è caratterizzato da __una__ corrente e __una__ tensione.

### CONVENZIONI PER TENSIONE E CORRENTE
- ==Convenzione dell'utilizzatore== (1): corrente entrante nel bipolo al terminale con riferimento $+$ della tensione
- ==Convenzione del generatore== (2): corrente uscente dal bipolo al terminale con riferimento $+$ della tensione

![CONVENZIONI BIPOLO|500](Images/Bipolo_2.png)

### POTENZA ELETTRICA SCAMBIATA
Si consideri un bipolo con tensione $v(t)$ e corrente $i(t)$.
Definiamo come ==potenza scambiata dal bipolo==:
$$p(t)~=~v(t)~i(t)~=~\frac{dL}{dq}~\frac{dq}{dt}~=~\frac{dL}{dt}\qquad[p]~=~VA~=~\frac{J}{s}$$
La potenza è il lavoro svolto per unità di tempo.

Quando la potenza viene calcolata con la convenzione dell'utilizzatore, la potenza si dice ==entrante== (assorbita), quando viene calcolata con la convenzione del generatore, la potenza si dice ==uscente== (erogata).

Dalla definizione di potenza, si ricava la formula per calcolare il lavoro entrante/uscente:
$$L(t)~=~\int_{-\infty}^t{p(t^*)~dt^*}$$

Un bipolo si dice ==passivo== se il ==lavoro elettrico entrante== (con convenzione dell'utilizzatore) è ==non negativo==.
Se un bipolo non è passivo, si dice ==attivo==.

#### BIPOLI IDEALI PARTICOLARI
- Cortocircuito: $V=0,\forall I$
	Si ottiene dal resistore con $R=0$
- Circuito aperto: $I=0,\forall V$
	Si ottiene dal resistore, con $G=0$ o dal GIC con $J=0$

## BIPOLI IDEALI A REGIME VARIABILE QUASI STAZIONARIO
Oltre ai bipoli ideali visti precedentemente, si aggiungono anche gli ==interruttori==
- Interruttore che chiude in $t=t^*$:
	Bipolo che commuta all'istante di tempo $t^*$ passando da circuito aperto a cortocircuito
- Interruttore che apre in $t=t^*$
	Bipolo che commuta all'istante di tempo $t^*$ passando da cortocircuito a circuito aperto

#### MATERIALE NECESSARIO PER IL CAPITOLO:
[[N-Poli]]