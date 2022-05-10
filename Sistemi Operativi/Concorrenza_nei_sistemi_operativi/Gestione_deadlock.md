# GESTIONE DEL [[Deadlock|DEADLOCK]]
Quando e quanto spesso richiamare l'algoritmo di rilevamento dipende da:
- frequenza (presunta) con la quale si verificano i deadlock
- numero di [[Thread|thread]] che vengono eventualmente influenzati dal deadlock, e sui quali occorre effettuare un _roll back_

Se l'algoritmo viene richiamato con frequenza casuale, possono essere presenti molti cicli nel [[Grafo_delle_risorse|grafo delle risorse]], e quindi non si può stabilire quale dei thread coinvolti nel ciclo abbia "causato" il deadlock.
Alternativamente, l'algoritmo può essere richiamato ogni volta che una richiesta non può essere soddisfatta immediatamente, a intervalli regolari, o quando I'utilizzo della CPU scende al di sotto del 40%.
Se i deadlock avvengono molto raramente, è meglio lasciarli avvenire e riavviare il sistema, o in generale risolverli, quando necessario; l'overhead costante e i costi in performance dell'algoritmo di rilevamento del deadlock non sono più convenienti.

# RIPRISTINO DEL [[Deadlock|DEADLOCK]]
Per ripristinare un deadlock bisogna terminare in _abort_ tutti i thread in deadlock uno alla volta, fino ad eliminare il ciclo di deadlock. L'ordine con cui terminare i thread, ovvero l'==ORDINE DI [[Risorse#PREEMPTION PRELAZIONE|PRELAZIONE]]==, viene determinato in base ad alcuni fattori fondamentali:
- priorità del thread
- tempo di computazione trascorso e tempo rimanente al completamento del thread
- quantità e tipo di risorse impiegate (se sono non oppure facilmente prelazionabili)
- risorse ulteriori necessarie al thread per il completamento
- numero di thread da eliminare

Se vengono prelazionate le risorse a un thread, questo deve tornare ad uno stato sicuro da cui ripartire: operazione di ==ROLL BACK==.
==STARVATION==: alcuni thread possono essere sempre selezionati come vittime della prelazione, e quindi potrebbero non venire mai completati.