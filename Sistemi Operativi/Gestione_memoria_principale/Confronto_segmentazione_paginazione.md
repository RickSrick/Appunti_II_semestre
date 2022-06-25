# VANTAGGI DELLA [[Paginazione|PAGINAZIONE]]
- elimina la [[Frammentazione#FRAMMENTAZIONE ESTERNA|frammentazione esterna]] (tuttavia può portare a [[Frammentazione#FRAMMENTAZIONE INTERNA|frammentazione interna]], in quanto le pagine sono di dimensioni fisse e il processo può non occupare tutta la memoria del suo ultimo frame)
- facilita l'implementazione di complesse tecniche di ottimizzazione (come i meccanismi di [[Memoria_virtuale|memoria virtuale]])

# VANTAGGI DELLA [[Segmentazione|SEGMENTAZIONE]]
- elimina la frammentazione interna (tuttavia può portare a frammentazione esterna, in quanto la memoria viene riempita con segmenti a dimensione variabile, possibilmente troppo piccoli per nuovi segmenti)
- la natura dei segmenti permette di rappresentare più fedelmente la struttura logica del programma
- uso dinamico della memoria
- prestazioni migliori, in quanto ogni segmento è contiguo

Possibile anche combinare segmentazione e paginazione.
![550](fusione.png)