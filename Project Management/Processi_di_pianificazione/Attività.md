# ATTIVITÀ
==ATTIVITÀ==: componenti del lavoro da eseguire per realizzare un certo deliverable, assegnate ad una o più persone, con una durata ed un effort previsti.
Nella [[Work_breakdown_structure|WBS]] le attività devono essere descritte in modo da essere:
- _controllabili_: devono essere assegnate ad un responsabile
- _gestibili_: devono tipicamente avere una durata breve (_buono_: dal giorno ad un mese; _male_: 3 mesi o più)
- _misurabili_: devono generare un output tale da essere misurato (_buono_: rilascio di 10 disegni, rilascio di un documento, consegna di due unità (elementi fisici); _male_: completare la progettazione)
- _significative_: devono essere chiari i requisiti di ciò che si vuole ottenere (_buono_: assemblare il prototipo hardware, eseguire il test; _male_: emettere un report di avanzamento)

## ==ATTRIBUTI== DELLE ATTIVITÀ
- nome / etichetta
- identificativo (ID)
- identificativo della WBS
- descrizione
- durata (_duration_)
- durata complessiva, incluse ferie e giorni non lavorativi (_elapsed duration_)
- vincoli
- anticipo (_lead_) e ritardo (_lag_)
- requisiti di risorse
- tipo di impegno richiesto (_effort_)
Questi attributi sono molto utili per lo sviluppo della [[Diagrammi_di_schedulazione|schedulazione]] e per il calendario di Progetto a cui è assegnata l’attività

## ==DURATA== DELL'ATTIVITÀ
Numero di periodi di lavoro necessari per completarla (espresso in ore, giorni o settimane lavorativi), tempo espresso in unità temporali che intercorrono tra l’inizio e la fine dell’attività.
![500](durata_attività.png)

Ci sono vari metodi per stimare la durata di un'attività:
- ==STIMA PER ANALOGIA==: tecnica che usa dati storici provenienti da un’attività o progetto simile
	  - stima approssimativa e meno accurata, usata quando vi sono poche informazioni dettagliate
	  - di solito meno costosa e richiede tempi minori rispetto ad altre tecniche
- ==STIMA PARAMETRICA==: determina quantitativamente la durata
	  - moltiplica la quantità di lavoro da eseguire per il numero di ore di lavoro richieste da ciascuna attività
	  - e.g. progettazione tecnica: numeri di disegni per il numero di ore di lavoro per disegno
- ==STIMA BOTTOM-UP==: stima che aggrega le stime dei componenti di livello inferiore della WBS
	  - il lavoro viene scomposto nel dettaglio, le durate dettagliate sono stimate, le stime sono poi aggregate
	  - viene usata quando la durata non può essere stimata con un ragionevole grado di affidabilità
- ==STIMA A TRE VALORI==: si basa sulle durate dell’attività (==THREE-POINT ESTIMATES==):
	- _più probabile / most likely ($t_{M}$)_: sulla base delle risorse probabilmente assegnate
	- _ottimistica / optimistic ($t_{O}$)_: basata sullo scenario migliore
	- _pessimistica / pessimistic ($t_{P}$)_: basata sullo scenario peggiore
	- con queste durate, si calcola la ==DURATA ATTESA / EXPECTED DURATION== ($t_{E}$) con la formula della _distribuzione triangolare_: $t_{E} = (t_{M} + t_{O} + t_{P}) / 3$
	- si usa quando non ci sono dati storici sufficienti o quando si usano dati discrezionali
- ==PROGRAM EVALUATION AND REVIEW TECHNIQUE (PERT)==: tecnica di stima che applica una media ponderata (_weighted average_) tra la stima ottimistica, pessimistica e più probabile quando vi è incertezza sulla stima di durata di una attività
	![450](pert.png)