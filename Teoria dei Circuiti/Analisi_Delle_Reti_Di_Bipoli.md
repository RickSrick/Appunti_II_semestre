# ANALISI DELLE RETI DI BIPOLI
Come già visto, analizzando le equazioni topologiche della rete, abbiamo $l$ equazioni con $2l$ incognite.

Se combiniamo queste equazioni con le equazioni tipologiche, otteniamo altre $l$ equazioni indipendenti, in quanto ciascuna coivolge una tensinoe o una corrente di un lato specifico.

![](Analisi_Rete_Lineare_Regime_Stazionario)

![](Analisi_Rete_Correnti_Di_Anello)

![](Analisi_Rete_Potenziale_Ai_Nodi)

## TEOREMA DI SOSTITUZIONE
Si consideri a regime stazionario, una rete formata da GIT, GIC e resistori ideali.
Si tratta di una rete lineare.

Si consideri il generico lato $V_h$ e corrente $I_h$.
Si sostituisca tale bipolo con un GIT avente tensione impressa $V_h=E_h$ oppure un GIC avente corrente impressa $I_h=J_h$

Il teorema di sostituzione afferma che se la rete modificata ammette soluzione unica, questa coincide con quella della rete originale.

## TEOREMA DEI GENERATORI EQUIVALENTI
Si consideri una rete di bipoli a regime stazionario.
Se di tale rete sono accessibili solo due nodi $A$ e $B$, la rete può essere vista come un bipolo avente per morsetti $A$ e $B$.
Questo bipolo equivalente ha lo stesso comportamento di un generatore lineare di tensione (teorema di Thevenin) o di un generatore lineare di corrente (teorema di Norton).

![](Analisi_Rete_Teorema_Di_Thevenin)

![](Analisi_Rete_Teorema_Di_Norton)

#### MATERIALE NECESSARIO PER IL CAPITOLO:
[[Modello_Reti_Elettriche]]
[[Topologia]]
[[Leggi_Di_Kirchhoff]]


