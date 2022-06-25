# FRAMMENTAZIONE
## ==FRAMMENTAZIONE INTERNA==
La memoria allocata ad un processo è leggermente maggiore di quella effettivamente necessaria per la sua esecuzione; la memoria in eccesso resta inutilizzata.
![300](frammentazione_interna.png)

## ==FRAMMENTAZIONE ESTERNA==
La memoria necessaria ad un processo è disponibile, ma non è contigua.
![500](frammentazione_esterna.png)
Come risolvere la frammentazione esterna:
- consentire la non continuità degli indirizzi fisici, allocando la memoria ovunque sia disponibile
- ==COMPATTAZIONE==
![500](compattazione.png)