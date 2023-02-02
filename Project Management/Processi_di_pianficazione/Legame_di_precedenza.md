# LEGAME DI PRECEDENZA
==VINCOLO / LEGAME DI PRECEDENZA==: dipendenza / relazione logica tra due attività in un modello di schedulazione.

In ogni legame di precedenza sono presenti:
- ==ATTIVITÀ PREDECESSORE== (B): attività che precede l'altra
- ==ATTIVITÀ SUCCESSORE== (A): attività che segue l'altra

Ne esistono 4 tipi:
- ==FINISH TO START (FS)==: B non può iniziare prima che sia stata finita A
	- la tecnica più comunemente usata
	- es: l'installazione del SO in un PC non può iniziare prima che sia finita l'installazione dell'hardware
	- ![600](fs.png)
- ==START TO START (SS)==: B non può iniziare prima che sia stata iniziata A
	- usata per porre attività in parallelo all'inizio
	- es: il livellamento del cemento non può iniziare prima che sia partita la gettata delle fondamenta
	- ![300](ss.png)
- ==FINISH TO FINISH (FF)==: B non può finire prima che sia stata finita A
	- usata per porre attività in parallelo alla fine
	- ![300](ff.png)
- ==FINISH TO START (FS)==: B non può finire prima che sia stata iniziata A
	- modalità meno usata
	- es: deve essere avviato un nuovo sistema di contabilità fornitori prima che il vecchio sistema possa essere dismesso
	- ![600](fs.png)

Inoltre, ad ogni legame di precedenza può essere associato:
- ==RITARDO / LAG== (+n): quantità di tempo di cui B sarà ritardata rispetto ad A
- ==ANTICIPO / LEAD== (-n): quantità di tempo di cui B sarà anticipata rispetto ad A
![500](lead.png)