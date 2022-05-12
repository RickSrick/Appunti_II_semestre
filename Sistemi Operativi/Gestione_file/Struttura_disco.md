# STRUTTURA DEL DISCO
Il disco è suddiviso in ==PARTIZIONI / MINIDISCHI==. La suddivisione in partizioni è utile per limitare la dimensione dei [[File_system|file system]], per installarne di diverso tipo e per dedicare ad altri scopi parti del dispositivo, come:
- _[[Gestione_swap|aree di swap]]_
- ==AREE RAW==: aree dotate solo della [[Formattazione#FORMATTAZIONE FISICA DI BASSO LIVELLO|formattazione di basso livello]], una sequenza "non strutturata" di blocchi
- ==AREE COOKED==: aree contenenti SO

==VOLUME==: ciascuna partizione con un file system. Ogni volume ha una ==[[Directory|DIRECTORY]] DI DISPOSITIVO==, che contiene informazioni su tutti i file in esso cotenuti. Un volume può essere:
- un "pezzetto" di un dispositivo di memorizzazione
- un dispositivo intero
- dispositivi multipli collegati in [[RAID]]
- dispositivi suddivisi e, al contempo, assemblati in RAID
![550](partizioni.png)