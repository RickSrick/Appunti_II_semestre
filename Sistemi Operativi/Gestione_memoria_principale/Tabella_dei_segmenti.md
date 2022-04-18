# TABELLA DEI SEGMENTI
==TABELLA DEI SEGMENTI==: mappa gli indirizzi logici in indirizzi fisici.
Ogni elemento della tabella contiene:
- ==BASE==: indirizzo fisico iniziale della memoria contenente il segmento
- ==LIMITE==: lunghezza del segmento
==SEGMENT-TABLE BASE REGISTER (STBR)==: punta alla locazione in memoria della tabella dei segmenti
==SEGMENT-TABLE LENGTH REGISTER (STLR)==: indica il numero di segmenti usati dal programma; un numero di segmento _s_ è legale se _s_ < STLR.
Anche in questo caso si usa una memoria associativa come hardware.
![[Tabella_delle_pagine#REGISTRI ASSOCIATIVI]]
![550](segmentazione2.png)