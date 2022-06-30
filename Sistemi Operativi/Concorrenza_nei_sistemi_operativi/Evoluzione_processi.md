# DIAGRAMMA TEMPORALE
Un [[Processo|processo]] descrive un'entità attiva con un suo sviluppo. È importante quindi rappresentare la sua evoluzione temporale.
Si utilizza un ==DIAGRAMMA TEMPORALE==:
- ascissa: tempo ($\text{t}_{0}$: istante iniziale, $\text{t}_{f}$: istante finale)
- ordinata: stato del processo ($\text{S}_{0}$: stato iniziale, $\text{S}_{f}$: stato finale)
![400](diagramma_temporale.png)
I plateau indicano che il processo non sta proseguendo, dunque tale diagramma permette di rappresentare processi in attesa di dati esterni.

A meno che il processo non sia indipendente da fattori esterni, è impossibile prevedere perfettamente i tempi; si preferisce quindi una rappresentazione che evidenzi solo gli stati più significativi del processo.
Inoltre, è conveniente scomporre il processo in sottoprocessi, anche se la suddivisione può non essere univoca.
Esempio:
	espressione $f = (a + b) \cdot (c + d) + e$:
	![450](scomposizione1.png)
	somme $(a + b)$ e $(c + d)$ possono essere eseguite in parallelo:
	![450](scomposizione2.png)
	questa scomposizione riduce il tempo totale di esecuzione

# EVOLUZIONE DI DUE PROCESSI
Nel caso semplice di due processi la loro evoluzione è rappresentabile con un sistema di assi cartesiani:
- un punto nel piano rappresenta lo stato dei processi
- punto P: terminazione del sistema (entrambi i processi completati)
- segmento orizzontale / verticale: un processo in esecuzione, l'altro in attesa

Esempio 1:
![450](evoluzione_processi.png)
($\text{R}_{1}$, $\text{R}_{2}$: risorse non condivisibili)
In questo caso non possono esserci [[Deadlock|deadlock]], in quanto ogni processo usa [[Risorse|risorse]] non condivisibili separate.

Esempio 2:
![450](evoluzione_processi2.png)
In questo esempio, entrambi i processi richiedono la stessa risorsa non condivisibile $\text{R}_{1}$. Pertanto, tutte le traiettorie che passano per la ==REGIONE VIETATA== sono impossibili (entrambi i processi usano la stessa risorsa).
Se sono presenti più risorse non condivisibili, la regione vietata sarà l'unione delle varie regioni vietate.