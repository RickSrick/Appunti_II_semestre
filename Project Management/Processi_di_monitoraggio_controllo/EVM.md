==EARNED VALUE METHOD (EVM)==: metodologia che consente l’integrazione delle misurazioni di [[Aree_di_gestione|scope]], [[Diagrammi_di_schedulazione|schedulazione]] e [[Risorse|risorse]] per valutare le prestazioni e l'avanzamento del progetto. L’Earned Value può essere monitorato in modo:
- incrementale, per determinare lo status attuale
- cumulativo, per determinare le tendenze

Questo metodo si basa su dei valori:
- _[[Avanzamento_progetto#DATI DI AVANZAMENTO|Planned Value]]_
	- il profilo del PV è talvolta definito [[Baseline|Performance Measurement Baseline]]
	- l’ammontare complessivo del valore pianificato è chiamato anche [[Avanzamento_progetto#DATI DI AVANZAMENTO|Budget at Completion]]
- _[[Avanzamento_progetto#DATI DI AVANZAMENTO|Actual Cost]]_
- ==EARNED VALUE (EV)==: 
	- misura del lavoro eseguito espressa in termini del budget autorizzato per tale lavoro
	- budget associato al lavoro che è stato completato
	- valore del budget di ciò che abbiamo realizzato (performed)

Esempio:
	Progetto: realizzare un giardino di 1.000 $m^2$ in un periodo di 10 giorni. Il budget di progetto è di 10.000€. Supponiamo che il giardino sia uniforme e che quindi ogni metro quadro abbia il valore di 10€.
	Supponiamo che dopo 5 giorni siano stati spesi €6.000 e realizzati 70 $m^2$
	![300](evm_es.png)
	- costo previsto al quinto giorno: €5.000
	- AC al quinto giorno: €6.000
	- EV: valore di lavoro realizzato = $700 m^2 \cdot \text{€}10 = \text{€} 7.000$ 

Controllando l’andamento dei tre indicatori (PV, AC, EV) è possibile evidenziare graficamente due tipi di scostamento rispetto ad una data fissata:
- ==SCHEDULE VARIANCE (SV)==: SV = EV - PV
	efficienza della pianificazione:
	- varianza positiva: in anticipo rispetto alla schedulazione
	- varianza negativa: in ritardo rispetto alla schedulazione
- ==COST VARIANCE (CV)==: CV = EV - AC
	posizione rispetto al budget:
	- varianza positiva: in difetto rispetto al budget schedulato
	- varianza negativa: in eccesso rispetto al budget schedulato
![400](evm1.png)
![400](evm2.png)
- ==SCHEDULE PERFORMANCE INDEX (SPI)==: SPI = EV / PV
	indice di efficienza della schedulazione
	- =1: progetto “on schedule”
	- >1: progetto in anticipo sui tempi, è completato un lavoro superiore a quello pianificato)
	- <1: progetto in ritardo sui tempi, è completato un lavoro inferiore a quello pianificato
- ==COST PERFORMANCE INDEX (CPI)==: CPI = EV / AC
	indice di efficienza dei costi
	- =1: progetto “on cost”
	- >1: costo inferiore al previsto (risparmio)
	- <1 costo superiore al previsto (sforamento nei costi)
- ==MATRICE SPIxCPI==: possiamo posizionare un progetto su dei quadranti, ognuno riferito a differenti situazioni di [[Reportistica|stato avanzamento]], con la dimensione della bolla proporzionale al budget globale assegnato al progetto
![500](spixcpi.png)