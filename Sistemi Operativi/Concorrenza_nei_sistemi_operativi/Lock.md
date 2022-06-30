# LOCK
==LOCK==: strumento più semplice per gestire gli accessi alle [[Race_condition#SEZIONE CRITICA|sezioni critiche]]: il [[Processo|processo]] che vuole accedere alla propria sezione critica deve acquisire il possesso del lock, per poi restituirlo al momento dell'uscita.
![400](lock.png)
==LOCK MUTEX== (_mutex_ da _mutual exclusion_, mutua esclusione):
- metodo per acquisire: $acquire()$
- metodo per rilasciare: $release()$
	le chiamate a questi metodi devono essere atomiche
- variabile booleana per indicare se il lock è disponibile o meno
![600](lock2.png)

Usare i lock impone l'==ATTESA ATTIVA / BUSY WAITING==: mentre un processo si trova nella propria sezione critica, gli altri processi che vogliono accedere alla propria devono ciclare effettuando la chiamata ad $acquire()$.