# HARD DISK DRIVE (HDD)
I ==DISCHI MAGNETICI== rappresentano il mezzo fondamentale per la memorizzazione di massa negli attuali sistemi di calcolo.
![400](hdd.png)
- ==PIATTO==: ognuna delle superfici dei dischi paralleli, identificata da un numero univoco e destinata alla memorizzazione dei dati
- ==TRACCIA==: ognuno degli anelli concentrici presenti su ogni piatto, ciascuno identificato da un numero univoco
- ==SETTORE==: ognuno dei settori circolari che compongono le tracce, ciascuno identificato da un numero univoco
- ==CILINDRO==: insieme delle tracce poste alla stessa distanza dal centro e relative a tutti i dischi; corrisponde a tutte le tracce con lo stesso numero, ma giacenti su piatti diversi
- ==BLOCCO==: insieme dei settori posti nella stessa posizione in tutti i piatti
- ==TESTINA==: testina di lettura e scrittura presente su ogni piatto; la posizione di ogni testina è solidale con tutte le altre sui diversi piatti: se una testina è posizionata su una traccia, le altre tracce si posizionano sul cilindro a cui la traccia appartiene
![400](hdd2.png)

## MISURE
- ==VELOCITÀ DI TRASFERIMENTO==: velocità con cui i dati fluiscono dall'unità a disco alla RAM
- ==TEMPO DI POSIZIONAMENTO==: _seek time_ + _latenza di rotazione_:
	- ==SEEK TIME==: tempo necessario a spostare il braccio del disco in corrispondenza del cilindro desiderato
	- ==LATENZA DI ROTAZIONE==: tempo necessario affinchè il settore desiderato si porti sotto la testina, ruotando il disco
- ==TEMPO DI ACCESSO MEDIO==: seek time medio + _latenza media_ (tempo per compiere una mezza rotazione del disco)
- ==TEMPO MEDIO DI I/O==: tempo medio di accesso + (quantità di dati da trasferire / velocità di trasferimento) + overhead
Il crollo della testina, normalmente sospesa su un cuscinetto d'aria di pochi micron ($10^{-6}$ m), corrisponde all'impatto della stessa sulla superficie del disco.
Nota per gli esercizi: quando non si sa la posizione precisa a cui accedere, si considera la latenza media.

## ==BLOCCHI LOGICI==
Le unità a disco vengono indirizzate come giganteschi vettori monodimensionali di _blocchi logici_, che rappresentano le minime unità di trasferimento e che sono creati all'atto della formattazione di basso livello.
L'array di blocchi logici viene mappato sequenzialmente nei settori del disco:
- il settore 0 è il primo settore della prima traccia del cilindro più esterno
- la corrispondenza prosegue ordinatamente lungo la prima traccia, poi lungo le tracce rimanenti nel primo cilindro, e così via, di cilindro in cilindro, dall'esterno verso l'interno
- il mapping fra [[Indirizzi_logici_fisici|indirizzi logici e fisici]] si realizza in maniera diretta
- i settori danneggiati vanno esclusi dall'operazione di mappatura

## VELOCITÀ
- ==CONSTANT LINEAR VELOCITY (CLV)==: densità dei bit per traccia uniforme
	- tracce più lontane dal centro del disco sono più lunghe e contengono un maggior numero di settori, fino al 40% in più rispetto alle tracce vicine al centro di rotazione
	- la velocità di rotazione aumenta spostandosi verso l'interno ($v = \omega r$) per mantenere costante la velocità lineare, e quindi la quantità di dati che passano sotto le testine nell'unità di tempo
	- usata soprattutto in CD e DVD
	- talvolta si ha un'unica traccia a spirale
- ==CONSTANT ANGULAR VELOCITY (CAV)==: velocità di rotazione costante
	- la densità dei bit decresce dalle tracce più interne a quelle esterne per mantenere costante la quantità di dati che passano sotto le testine nell'unità di tempo
![450](clv_cav.png)