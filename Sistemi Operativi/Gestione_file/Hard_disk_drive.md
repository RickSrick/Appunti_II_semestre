# HARD DISK DRIVE (HDD)
I ==DISCHI MAGNETICI== rappresentano il mezzo fondamentale per la memorizzazione di massa negli attuali sistemi di calcolo.
![400](hdd.png)
- ==PIATTO==: ognuna delle superfici dei dischi paralleli, identificata da un numero univoco e destinata alla memorizzazione dei dati
- ==TRACCIA==: anelli concentrici presenti su ogni piatto, ciascuno identificato da un numero univoco
- ==SETTORE==: settori circolari che compongono le tracce, ciascuno identificato da un numero univoco
- ==CILINDRO==: insieme delle tracce poste alla stessa distanza dal centro e relative a tutti i dischi; corrisponde a tutte le tracce con lo stesso numero, ma giacenti su piatti diversi
- ==BLOCCO==: insieme dei settori posti nella stessa posizione in tutti i piatti
- ==TESTINA==: testina di lettura e scrittura presente su ogni piatto; la posizione di ogni testina è solidale con tutte le altre sui diversi piatti: se una testina è posizionata su una traccia, le altre tracce si posizionano sul cilindro a cui la traccia appartiene
![400](hdd2.png)
- ==VELOCITÀ DI TRASFERIMENTO==: velocità con cui i dati fluiscono dall'unità a disco alla RAM
- ==TEMPO DI POSIZIONAMENTO==: _seek time_ + _latenza di rotazione_:
	- ==SEEK TIME==: tempo necessario a spostare il braccio del disco in corrispondenza del cilindro desiderato
	- ==LATENZA DI ROTAZIONE==: tempo necessario affinchè il settore desiderato si porti sotto la testina
- ==TEMPO DI ACCESSO MEDIO==: seek time medio + latenza media
- ==TEMPO MEDIO DI I/O==: tempo medio di accesso + (quantità di dati da trasferire / velocità di trasferimento) + overhead
Il crollo della testina, normalmente sospesa su un cuscinetto d'aria di pochi micron ($10^-6$ m), corrisponde all'impatto della stessa sulla superficie del disco.