# NETWORK FILE SYSTEM (NFS)
==NETWORK FILE SYSTEM (NFS)==: rappresenta sia una realizzazione che una definizione di un sistema per accesso a file remoti attraverso LAN o WAN. Nasce in ambiente UNIX (_Solaris_ e _SunOS_) ed usa i protocolli _UDP/IP_ (_Unreliable Datagram Protocol_ su Ethernet) o _TCP/IP_, secondo la rete di comunicazione. È supportato da Linux.

Nel contesto dell'NFS si considera un insieme di stazioni di lavoro interconnesse come un insieme di calcolatori indipendenti con [[File_system|file system]] indipendenti. Bisogna garantire un certo grado di condivisione tra i file system, su richiesta esplicita, in modo trasparente.
Una directory remota viene [[Montaggio|montata]] su una [[Directory|directory]] del file system locale. La directory montata assume l'aspetto di un sottoalbero integrante del file system locale e sostituisce il sottoalbero che discende dalla directory locale.
La directory remota si specifica come argomento dell'operazione di montaggio in modo esplicito: occorre fornirne la locazione, o il nome del calcolatore. I file al suo interno diventano quindi accessibili in modo del tutto trasparente.
Potenzialmente, ogni file system, o ogni directory in un file system, nel rispetto dei diritti d'accesso, può essere montato in modo remoto su qualsiasi directory locale.
Esempi:
	_S1:/usr/shared_ viene montata su _U:/usr/local_
	![550](nfs.png)
	_S1:/usr/shared_ viene montata su _U:/usr/local_, dopodichè _S2:/usr/dir2_ viene montata su _U:/usr/local/dir1_
	![650](nfs2.png)

L'NFS è progettato per operare in un ambiente eterogeneo di calcolatori, sistemi operativi e architetture di rete: la sua realizzazione è indipendente dall'ambiente hardware / software che fa da substrato al file system. Tale indipendenza si ottiene utilizzando primitive _Remote Procedure Call (RPC)_ costruite su un protocollo di rappresentazione esterna dei dati, chiamato _External Data Representation (XDR)_, usato tra interfacce indipendenti.
La definizione di NFS distingue tra i servizi offerti dal meccanismo di montaggio (==PROTOCOLLO DI MONTAGGIO==) e gli effettivi servizi di accesso ai file remoti (==PROTOCOLLO NFS==).
![500](nfs3.png)

Vantaggi:
- in locale, si usa meno spazio disco, perchè i dati possono essere conservati su una singola macchina e restano accessibili a tutte le altre macchine connesse alla rete
- gli utenti non devono avere home directory separate su ogni macchina in rete: le home directory possono essere poste sul server NFS e rese disponibili attraverso la rete
- i dispositivi di archiviazione come unità CD-ROM e USB possono essere utilizzati dagli altri computer della rete: riduzione del numero di unità per supporti rimovibili presenti nella rete