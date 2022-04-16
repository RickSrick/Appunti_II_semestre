## Cos'è?
Creator è il principio che si impone di risolvere il seguente problema:

**chi crea gli oggetti?**

Da questa domanda sono partite delle condizioni che definiscono quando una classe può crearne un'altra.

![[class_creation.png]]

**A** e **B** due classi, per decidere se A può essere creato da B almeno una di queste condizioni è vera:

- B contiene o raggruppa A
- B registra A 
- B usa strettamente A (strettamente = localmente)
- B contiene i dati per creare A

**in caso esistessero più classi valide, usare quella che sfrutta la prima  condizione**

****

#### Diagramma di Sequenza

![[seq_creation.png|600]]

****

#### Vantaggi
il vantaggio principale è:

**La creazione di un oggetto dipende da un solo "creatore"**

è ovvio che quindi, in caso di problemi o di modifiche strutturali, i cambiamenti saranno localizzati.