# CODE MULTIPLE
Si può dividere la [[Scheduling|ready queue]] in più code separate, ognuna con il proprio criterio di scheduling:
- ==FOREGROUND / INTERATTIVA==: [[Criteri_scheduling#ROUND ROBIN|RR]]
- ==BACKGROUND / BATCH==: [[Criteri_scheduling#FIRST COME FIRST SERVED FCFS|FCFS]]

È necessario effettuare lo [[Scheduling|scheduling]] tra code:
- ==SCHEDULING A PRIORITÀ FISSA==: si servono tutti i processi in foreground, poi quelli in background (rischio di _starvation_)
- ==TIME SLICE==: ciascuna coda occupa un certo tempo di CPU da dividere tra i propri processi (e.g. 80% per foreground e 20% per background)

I processi possono essere assegnati ad una coda in modo permanente secondo qualche caratteristica invariante del processo.
![450](code_multiple.png)

In alternativa, ==CODE MULTIPLE CON FEEDBACK==: un processo si può spostare tra le varie code (si può implementare l'aging). Gli spostamenti vengono effettuati secondo vari parametri:
- numero di code
- algoritmo di scheduling per ciascuna coda
- metodo impiegato per determinare quando spostare un processo in una coda a priorità maggiore / minore
- metodo impiegato per determinare in quale coda deve essere posto un processo quando entra nel sistema
Esempio:
![400](feedback.png)