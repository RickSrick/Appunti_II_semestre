# SEGMENTAZIONE
==SEGMENTAZIONE==: schema di gestione della memoria che asseconda la visione dell'utente (generalmente non pensa alla memoria come ad un array lineare di dati). Un programma viene considerato come una collezione di ==SEGMENTI==: unità logiche, come:
- programma principale
- procedure e funzioni
- variabili locali e globali
- metodi
- oggetti
- strutture dati

Ciascun segmento ha una lunghezza variabile, che dipende dal compito svolto dal segmento come parte del programma utente.
Ogni elemento del segmento è indentificato dall'offset al suo interno; ogni indirizzo logico è quindi formato dalla coppia <numero di segmento, offset>.
![500](segmentazione.png)
Per ogni processo si usa una [[Tabella_dei_segmenti|tabella dei segmenti]].