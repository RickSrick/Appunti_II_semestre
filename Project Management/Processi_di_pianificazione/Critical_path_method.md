# CRITICAL PATH METHOD
==METODO DEL CAMMINO CRITICO / CRITICAL PATH METHOD (CPM)==: tecnica di analisi per individuare il ==CAMMINO CRITICO==: sequenza di [[Attività|attività]] che rappresenta il percorso più lungo nel [[Definizioni#==PROGETTO==|Progetto]] che determina la durata minore possibile. Questa tecnica calcola per tutte le attività, indipendemente dalle limitazioni delle [[Risorse|risorse]]:
- ==EARLY START (ES)==: il primo momento possibile in cui un’attività può cominciare in base alla sequenza logica
- ==EARLY FINISH (EF)==: il primo momento possibile in cui un’attività può finire in base alla sequenza logica
- ==LATE START (LS)==: l’ultimo momento possibile in cui un’attività può cominciare senza ritardare il completamento del Progetto
- ==LATE FINISH (LF)==: l’ultimo momento possibile in cui un’attività può finire senza ritardare il completamento del Progetto
![450](date.png)

Vengono effettuate delle analisi di calcolo:
- ==FORWARD PASS==: vengono calcolate ES ed EF (date / periodi minimi)
	- ![400](forward_pass.png)
- ==BACKFLOW PASS==: vengono calcolate LS e LF (date / periodi massimi)
	- ![400](backflow_pass.png)
Si mettono insieme i dati.
![450](forward_backflow.png)

Si calcola la ==FLESSIBILITÀ DI SCHEDULAZIONE / TOTAL FLOAT / TOTAL STACK (TF)==: lasso di tempo per cui si può ritardare o allungare un’attività schedulata rispetto alla ES senza rinviare la data di fine progetto o infrangere un [[Legame_di_precedenza|vincolo di schedulazione]]; $TF = LS - ES = LF - EF$
![450](tf.png)
Le attività con TF = 0 sono ==ATTIVITÀ CRITICHE==, e costituiscono il cammino critico.
![450](cp.png)

==FREE FLOAT (FF)==: quantità di tempo per la quale si può ritardare un’attività senza ritardare la ES di un’[[Legame_di_precedenza|attività successore]] o violare un vincolo di schedulazione; $FF = min\{ES(successore)\} - EF - 1$
![450](free_float.png)

Questo metodo è usato per:
- stimare la durata minima del Progetto calcolando il percorso critico
- determinare la flessibilità della schedulazione nel modello di schedulazione attraverso la quantità di Free Float e Total Float