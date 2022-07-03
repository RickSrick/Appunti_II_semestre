# BUFFER CACHE
==BUFFER CACHE==: area della memoria principale che contiene una copia dei [[Hard_disk_drive|blocchi del disco]] usati più di recente.
==CACHE DELLE PAGINE / PAGE CACHE==: una parte della RAM usata dal SO in cui si copiano dall'[[Hard_disk_drive|hard disk]] i dati correntemente in uso. Questi vengono modificati nella cache, poi spostati nel buffer per essere scritti nell'hard disk.
Impiega tecniche di [[Memoria_virtuale|memoria virtuale]] per la gestione dei dati del file, trattandoli come pagine anzichè come blocchi del disco. L'[[Mappatura#MAPPATURA IN MEMORIA DELL'I O|I/O mappato in memoria]] impiega una cache delle pagine, mentre l'I/O da file system utilizza la buffer cache del disco, memorizzata in memoria centrale.
![400](buffer_cache.png)
Una ==BUFFER CACHE UNIFICATA==, invece, è un'unica cache delle pagine usata per memorizzare sia i file mappati in memoria che i blocchi trasferiti per operazioni di I/O ordinario da file system, evitando il _double caching_.
![400](buffer_cache2.png)

L'algoritmo [[Algoritmi_sostituzione_pagina#LEAST RECENTLY USED LRU|LRU]] è in generale ragionevole per la sostituizione delle e pagine e dei blocchi; tuttavia, non si dovrebbe usare questo algoritmo con le pagine relative ad un file da leggere o scrivere in [[Accesso_file#ACCESSO SEQUENZIALE|modo sequenziale]], dato che la pagina letta più di recente non verrà probabilmente più utilizzata.
==RILASCIO INDIETRO / FREE-BEHIND==: rimuove una pagina della cache non appena si verifica una richiesta della pagina successiva.
==LETTURA ANTICIPATA / READ-AHEAD==: si leggono e si copiano nella cache la pagina richiesta e diverse pagine successive, che verranno probabilmente accedute in sequenza.