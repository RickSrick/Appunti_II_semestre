# FAULT TOLERANCE
Il concetto di ==FAULT TOLERANCE== fa riferimento all’abilità di un sistema o componente di continuare il normale funzionamento nonostante la presenza di [[Guasti|guasti]] hardware o software. Tipicamente include qualche forma di _ridondanza_:
- ==RIDONDANZA SPAZIALE / FISICA==: si usano più componenti che eseguono la stessa funzione contemporaneamente, oppure che sono configurati in modo che un componente sia disponibile come backup nel caso un altro componente abbia un guasto (e.g. [[RAID]])
- ==RIDONDANZA TEMPORALE==: si ripete una funzione / operazione quando viene rilevato un errore; risulta efficace con [[Guasti|guasti temporanei]] ma non con quelli [[Guasti|permanenti]]
- ==RIDONDANZA DI INFORMAZIONE==: si replicano o si programmano dati in modo che gli errori a livello di bit possano essere rilevati e corretti (e.g. [[Malfunzionamenti#DISTANZA DI HAMMING|codifica di Hamming]])
Lo scopo è di incrementare l'[[Affidabilità|affidabilità]] del sistema, e tipicamente questo comporta dei costi in termini economici o di prestazioni. Il livello di misure da implementare per la fault tolerance è legata all’importanza delle [[Risorse|risorse]] da proteggere.

Un certo numero di soluzioni possono essere implementate nel SO per renderlo fault tolerant:
- isolamento dei [[Processo|processi]]
- controllo della concorrenza
- virtual machines
- checkpoints e rollbacks