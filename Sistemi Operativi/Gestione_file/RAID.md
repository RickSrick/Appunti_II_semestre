# RAID
==REDUNDANT ARRAY OF INDIPENDENT DISKS (RAID)==: tecnica di installazione raggruppata di diversi [[Hard_disk_drive|dischi rigidi]], che fa sì che nel sistema appaiano e siano utilizzabili come se fossero un unico volume di memorizzazione.
Tra gli altri benefici, garantisce l'affidabilità del sistema tramite la ridondanza, con i suoi sei livelli distinti e le loro eventuali combinazioni, aumentando così il _tempo medio di guasto_. Questi sistemi sono spessi affiancati dalla presenza di _Non-Volatile RAM (NVRAM)_ per garantire la consistenza dei dati scritti "contemporaneamente" su dischi multipli.
Inoltre, le tecniche per aumentare la velocità di accesso al disco implicano l'uso di più dischi cooperanti. Infatti, richieste multiple indipendenti possono essere servite in parallelo da dischi diversi, e una singola richiesta di un numero elevato di blocchi può essere servita da più dischi che operano in maniera coordinata.

La maggior parte delle organizzazioni può essere distinta in base a due caratteristiche:
- _granularità_ di inserimento dei dati
- metodo e struttura con cui le informazioni ridondanti vengono calcolate e distribuite sui vari dischi

## ==GRANULARITÀ==
- ==GRANA FINE==: i dati vengono inseriti in blocchi relativamente piccoli, e le richieste di I/O accedono a tutti i dischi di un gruppo
	- ad esempio, durante la lettura tutti i dischi di un gruppo agiscono in parallelo, ciascuno trasferendo una porzione dei dati richiesti
	- ciò comporta data rate elevato ma basso I/O rate
	- granularità idonea per applicazioni di _supercomputing_
![550](raid_grana_fine.png)
- ==GRANA GROSSA==: i dati vengono inseriti in blocchi relativamente grandi, e le piccole richieste vengono servite da un piccolo numero di dischi
	- molteplici letture / scritture individuali avvengono in parallelo sui vari dischi di un gruppo
	- ciò comporta data rate basso ma elevato I/O rate
	- granularità idonea per _transaction processing_
![550](raid_grana_grossa.png)

## ==SEZIONAMENTO==
_Sezionamento / striping_, i dati vengono suddivisi in sezioni di uguale lunghezza e scritti su dischi differenti.

### ==RAID 0==
Si usa il ==SEZIONAMENTO DEL DISCO / DATA STRIPING==: tratta un gruppo di dischi come un'unica unità di memorizzazione. Ogni blocco di dati è suddiviso in "sottoblocchi" memorizzati su dischi distinti. Il tempo di trasferimento per rotazioni sincronizzate diminuisce proporzionalmente al numero di dischi nella batteria.
Non è una vera architettura RAID, in quanto non mantiene ridondanza e consente solo data striping, a livello di blocco o multipli di blocco.
Vantaggi:
- minor costo tra le architetture RAID
- migliori prestazioni in scrittura
Svantaggi:
- non le migliori prestazioni in lettura
- affidabilità molto bassa
Viene utilizzata in applicazioni di supercomputing.
![350](raid_0.png)

### ==RAID 1==
Il ==MIRRORING / SHADOWING== conserva duplicati di ciascun disco. I dati sono mantenuti in duplice copia su dischi distinti.
![400](raid_1.png)

### ==RAID 2==
La struttura a ==BLOCCHI DI PARITÀ== utilizza un minor grado di ridondanza, mantenendo buone caratteristiche di affidabilità. Viene effettuato uno striping a livello di bit, e si effettua un unico movimento parallelo delle testine.
Per rilevare e correggere gli errori, si usa un metodo analogo alla [[Malfunzionamenti#DISTANZA DI HAMMING|codifica di Hamming]]. Viene fornito un numero di dischi ridondanti in un gruppo circa proporzionale al logaritmo del numero dei dischi dati nel gruppo. Nei dischi ridondanti viene inserita la parità calcolata sui diversi sottoinsiemi dell'informazione, analoga al bit di parità. Un unico disco di parità può rilevare un singolo errore, ma per correggere un errore sono necessari più dischi di parità per identificare il disco con l'errore.
Data l'ormai la diffusa inclusione della correzione tramite codifica di Hamming direttamente nel [[Connessione_dispositivi_memoria#MEMORIA SECONDARIA CONNESSA ALLA MACCHINA|controllori dei dischi]], questa architettura non è diffusa commercialmente.
![550](raid_2.png)

### ==RAID 3==
Si effettua uno striping a livello di bit, si effettua un unico movimento parallelo delle testine e si usa un solo disco di parità. Infatti, sono i controllori dei dischi ad indentificare il disco guasto, cosicchè un solo disco di parità sia sufficiente per ricostruire l'informazione di un gruppo. Le operazioni di lettura accedono a tutti i dischi dati di un gruppo, mentre quelle di scrittura accedono a tutti i dischi dati e al disco di parità.
Fornisce prestazioni in lettura inferiori agli schemi che distribuiscono la parità uniformemente sui dischi. Viene usata in applicazioni che richiedono [[Scheduling_disco|larghezza di banda]] ma non moltissime operazioni di I/O.
![400](raid_3.png)

### ==RAID 4==
Si effettua uno striping a livello di blocco, le testine sono indipendenti e si usa un solo disco di parità.
Piccole letture richiedono l'accesso a un solo disco dati, mentre piccolo scritture richiedono quattro operazioni di I/O, due per leggere il vecchio dato e la vecchia parità, e due per scrivere il nuovo dato e aggiornare la parità. In queste operazioni, il collo di bottiglia rimane il disco di parità, che ne influenza enormemente la velocità.
Presenta risultati di affidabilità, costo, capacità effettiva uguali a quelli del livello RAID 3. Il ciclo di _small read-modify-write_ è ancora troppo lento rispetto al RAID 1, e dunque non è sempre idoneo per transaction processing. Invece, è idoneo per ambienti che richiedono molte piccole letture simultanee.

### ==RAID 5==
Si effettua uno striping a livello di blocco, le testine sono indipendenti e la parità è distribuita su tutti i dischi.
Rispetto al RAID 3 si riduce il collo di bottiglia, in quanto scritture indipendenti concorrenti non sempre richiedono di accedere allo stesso disco per la parità. Presenta prestazioni migliori per grandi letture, piccole letture e grandi scritture; le piccole scritture sono inefficienti rispetto allo schema di mirroring del RAID 1, in quanto è necessario usare il ciclo lettura-modifica-scrittura per aggiornare la parità.
È idoneo per applicazioni di calcolo e per elaborazione di transazioni interattive.
![450](raid_5.png)

### ==RAID 6==
Si effettua uno striping a livello di blocco, le testine sono indipendenti e la parità è distribuita due volte su tutti i dischi. Il blocco di parità viene generato e distribuito tra due stripe di parità, su due dischi separati, usando differenti stripe di parità nelle due direzioni.
Rispetto al RAID 5, le prestazioni sono comparabili, nonostante piccole scritture richiedano sei operazioni di I/O; l'affidabilità e i costi sono superiori.

### SCHEMI ANNIDATI
- ==RAID 0+1==: si adatta uno ==STRIPE OF MIRRORS==: i dati sono distribuiti su insiemi di dischi in duplice copia
- ==RAID 1+0==: si adatta un ==MIRROR OF STRIPES==: i dati sono distribuiti su un array di dischi che viene completamente duplicato su uno o più array di dischi
![350](raid_annidati.png)
![300](raid_annidati2.png)
- ==RAID 0+3, 3+0, 0+5, 5+0==: combinano rispettivamente le tecniche di parità del RAID 3 o 5 con le tecniche di distribuzione del RAID 0; presentano costi elevati, ma beneficiano del parallelismo d'accesso ai dischi di parità.