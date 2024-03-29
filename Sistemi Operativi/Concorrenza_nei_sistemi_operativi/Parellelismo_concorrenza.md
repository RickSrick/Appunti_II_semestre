# PARALLELISMO E CONCORRENZA
Nelle [[Multiprocessore_multicore#SISTEMI MULTICORE|architetture multicore]], sono presenti diverse unità di calcolo sullo stesso chip, ognuna delle quali appare al SO come un chip separato. Su questi sistemi i [[Thread|thread]] possono essere eseguiti in parallelo, poichè il sistema li può assegnare a diverse unità di calcolo.

- ==PARALLELISMO==: eseguire più calcoli / task contemporaneamente
	- task multipli, o diverse parti dello stesso task, vengono eseguiti contemporaneamente in sistemi [[Multiprocessore_multicore#SISTEMI MULTIPROCESSORE|multi-processore]] o multi-core
	- richiedono strutture hardware apposite
	- si trasforma un flusso di esecuzione sequenziale in uno parallelo
- ==CONCORRENZA==: eseguire più calcoli / task nello stesso periodo di tempo
	- task multipli vengono eseguiti nello stesso intervallo di tempo senza un ordine specifico, dando l'apparenza che vengano eseguiti contemporaneamente
	- possibile grazie al _time slicing_ della CPU, ovvero allo [[Scheduler|scheduler]] che dedica l'unità di calcolo ai vari task per unità di tempo infinitesimali

Due tipi di parallelismo:
- ==DATA PARELLELISM==: la stessa operazione viene eseguita da più thread contemporaneamente sullo stesso insieme di dati, che viene partizionato in segmenti diversi
- ==TASK PARALLELISM==: distrubuzione di thread diversi in esecuzione nei diversi nodi di calcolo in ambienti di calcolo parallelo