# TABELLA DEI [[Segmentazione|SEGMENTI]]
==TABELLA DEI SEGMENTI==: mappa [[Indirizzi_logici_fisici|gli indirizzi logici in indirizzi fisici]] nella segmentazione.
Ogni elemento della tabella contiene:
- ==BASE==: indirizzo fisico iniziale della memoria contenente il segmento
- ==LIMITE==: lunghezza del segmento
==SEGMENT-TABLE BASE REGISTER (STBR)==: punta alla locazione in memoria della tabella dei segmenti.
==SEGMENT-TABLE LENGTH REGISTER (STLR)==: indica il numero di segmenti usati dal programma; un numero di segmento _s_ è legale se _s_ < STLR.
Anche in questo caso si usa una [[Tabella_delle_pagine#REGISTRI ASSOCIATIVI TRANSLATION LOOK-ASIDE BUFFER TLB|memoria associativa]] come hardware.
![550](segmentazione2.png)