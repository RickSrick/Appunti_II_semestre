## Cos'è?
Information Expert è il principio che si impone di risolvere il seguente problema:

**Come si assegnano le responsabilità agli oggetti?**

Per risolvere questo problema si parte da un concetto abbastanza intuitivo:

**L'oggetto, esegue azioni in base alle informazioni che ha**

Facile no? Quindi l'ogetto avrà responsabilità solo in base alle informazioni con cui può eseguirla.

**ESEMPIO:** Io Luca e Francesco siamo stati trascinati da Matteo a vedere un pessimo film Marvel sui vampiri: **Chi dovrà darci informazioni su orario e luogo d'incontro?** Il popi di Matteo che ci vuole portare

****

#### Come Scelgo la Classe Giusta? 

**Prima Scelta:** se hai la fortuna di avere già una classe che contiene tutte le informazioni per fare quello che vuoi, complimenti

**Seconda Scelta:** sfrutta il Domain Model e lasciati ispirare per creare una classe adatta alla tua situazione.

****

#### Domande Da Porsi:
- Di quali informazioni ho bisogno?
- Dove posso raggruppare tutte le info?
- Quale classe dovrebbe conoscere la risposta alla mia richiesta?

****

#### Note
Information Expert è usato spesso con sistemi che danno valore alle **responsabilità**. Ovviamente più oggetti che contengono informazioni parziali possono collaborare. 

****

#### Vantaggi
- Mantengo l'incapsulamento
- Codice più robusto e meno dipendente