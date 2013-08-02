======================================
Bsys2 FS13 Repetitionsfragen Antworten
======================================

.. contents\\:\\: Inhaltsverzeichnis


Repetitionsfragen: https://github.com/moonline/Bsys2/blob/master/RepetitionQuestions.Bsys2.tex


Sicherheit
==========

1
-
* Softwarefehler / zu hohe Komplexität
* Sicherheit ist zusätzlich Aufwand / mühsam
* das BS berücksichtigt Sicherheit zu wenig

2
-
* Information abfangen (interception)
* Information modifizieren (modifikation)
* Information unterbrechen (interruption)
* Information einspeisen (fabrication)

3
-
Eine Berechtigunggsprüfung

4
-
* Personalisierung und Authorisierung
* Identifizierung und Zugriffskontrolle

5
-
Benutzerverwaltung, Anmeldesystem, Zugrifskontrolle

6
-
* Es gibt Domänen und Objekte (Files, Drucker, ...).
* Die Rechte sind mit Tupels (Domäne, Rechte) definiert.
* z.B. (D1, r1rw2rwx4) gibt der Domäne1 leserechte für Objekt1, lese- und schreibrechte für Objekt2 und lese-, schreib- und ausführungsrechte für Objekt4.
* Die Rechte können auch als Matrix dargestellt werden.
* Benutzer melden sich als Domäne an und besitzen somit deren Rechte.

7
-
Tabelle, in welche die Objekte die Spalten und die Domänen die Zeilen bilden. Die Rechte sind in den Feldern eingetragen.

8
-
Strategie
	definiert, was geschützt werden soll (Schutzobjekte),
Mechanismus
	definiert, wie der Schutz umgesetzt werden soll (technikorientiert)

9
-
Definieren, wie weit ein Benutzer die Schutzmatrix verändern darf und z.B. einem andern Benutzer Rechte auf ein Objekt zu geben.

10
--
Kopierrecht
	Recht zum Kopieren von Rechten. 
Varianten
	Volles Kopierrecht, Rechtetransferrecht, Limitiertes Kopierrecht

11
--
Objekte besitzen Owner, der darauf volle Rechte hat (Rechte einfügen, Rechte entfernen, Besitzrecht weitergeben).

12
--
Recht zum Ändern aller Rechte einer Domäne.

13
--
Ownerkonzept
	Sämmtliche Felder in den Spalten seiner Objekte
Kontrollkonzept
	Sämmtliche Felder in den Zeilen seiner Domäne

14
--
Zugriffsliste als globale Tabelle mit Trippeln:
	* (-) verändern der Rechte bedingt durchgehen der Liste

Zugriffsliste pro File (ACL):
	* (+) Rechte schnell gefunden bei Zugriff
	* (-) Löschen der Rechte einesgelöschten Users schwierig

Zugriffsliste pro Domäne (Ticket Liste):
	* (+) Rechte einer Domäne sind zusammen abgelegt
	* (+) Löschen einer Domäne einfach
	* (-) Technisch anspruchsvoll umzusetzen

15
--
* Benutzerbestimmt: Benutzer (owner) bestimmt, wer was mit seinen Objekten macht
* Systembestimmt: System/Organisation bestimmt, wer was mit welchen Objekten macht

16
--
Der Benutzer soll zu jedem Zeitpunkt so wenig Zugriff wie möglich aber so viel wie nötig besitzen -> keine unnötigen Rechte.

17
--
Bell/Padula
	Objekte sind Sicherheitsstufen zugeordnet. Benutzer darf Objekte gleicher und schwächerer Stufen lesen, aber nur Objekte gleicher oder höherer Stufe schreiben.

18
--
Prozess sollte nur dann Rechte für ein Objekt besitzen, wenn er es gerade braucht. Da jedoch nur das Programm selbst weis, wann dies zutrifft, hat der Prozess den Grossteil der Zeit Rechte, die er gar nicht benötigt.


Unix Sicherheit
===============

19
--
* Datei besitzt Rechte für Owner, Gruppe und Andere.
* Root darf alles.
* Für Owner, Gruppe und Andere können einzeln r-, w- und ausführungsrechte gesetzt werden.

20
--
Domänen
	Owner, Group, Other
Objekte
	Files, Prozesse
	
21
--
Benutzerbestimmt

22
--
* (+) einfach zu verstehen
* (+) effizient umzusetzen
* (-) Möglichkeiten eingeschränkt
* (-) Für wikrlich komplexe Rechtevergaben werden zusätzliche Kernelmodule benötigt

23
--
* Ausführen der Datei mit Rechten den Benutzers oder der Gruppe statt mit den Rechten der Datei.
* Datei kann für jeden Benutzer mit dessen Rechten ausgeführt werden.

24
--
Rechtetemplate für neue Dateien

25
--
Benutzer kann einen einzelnen Befehl oder mehrere mit den Rechten eines andern Benutzers ausführen (minimal Priviledges).


Windows Sicherheit
==================

26
--
Dateien sind ein Owner und eine oder mehrere Groups zugeordnet. Der Owner hat das alleinige Recht die Rechte zu ändern. Die Rechteverwaltung basiert auf ACL's. Der Administrator unterliegt ebenfalls den gesetzten Rechten der Rechteverwaltung. Er kann aber Owner werden (take Ownership).
Laufwerke,  Drucker, etc. unterliegen auch den ACL's. Mittels Gruppenrichtlinien können zusätzliche Rechte gesetzt werden und auch Zugriffe auf Dienste gesteuert werden.

27
--
Domänen
	Benutzer, Gruppen
Objekte
	Dateien, Laufwerke, Drucker, Dienste, ...


Unix Scripting
==============
28
--
Die Shell selbst ist nur eine Anwendung, genauso wie alle andern auch. Die bekanntesten sind die Bourne Shell und die Bash.

29
--
Das Kapseln von mehreren Befehlen in ein Skript zur Administration des Systems und zur Automation von Aufgaben. 

Bsp: ein Backup-Skript überprüft Dateien auf das Änderungsdatum, packt geänderte in ein tar Archiv und kopiert das Archiv auf eine Backup Platte, wo sie wieder entpackt werden.

30
--
* Einrichten des Systems
* Wartungsaufgaben
* Automatisierungsaufgaben, für die UI nicht notwendig ist (z.B. File konvertierung, Backup)
* Security

31
--
Das Auflösen und Einsetzen von Variablen und Ausdrücken in einer Befehlszeile vor dem eigentlichen Ausführen.

32
--
Sie teilt dem System mit, mit welcher Shell das Skript ausgeführt werden soll.


Ein-/Ausgabe
============
33
--
Über den Prozessor
	* Die Daten werden von der Eingabe eingelesen, durch den Prozessor verarbeitet und auf die Ausgabe geschrieben.
	* (-) Belastet den Prozessor während des gesammten Vorgangs.

Interrupt gesteuert
	* Der Prozessor wird durch Interrupts unterrbochen und steuert jeweils den Transfer. Die Daten laufen nicht über den Prozessor.
	* Prozessor wird jeweils nur für die Initialisierung des Vorgangs belastet, wenn durch Interrupt ein zur I/O bereiter Block gemeldet wird..
	* (+) Belastet den Prozessor wesentlich weniger als wenn der gesammte Transfer über den Prozessor laufen würde
	* (-) Prozessor wird gegenüber DMA Kontroller bei jedem Interrupt unterbrochen und belastet für die Initialisierung des Transferprozesses

DMA Kontroller
	* Der Prozessor initiert den Prozess, anschliessend läuft er über den DMA Kontroller. Der Prozessor wird erst wieder gestört, um die Fertigstellung mitzuteilen.
	* Der DMA Kontroller übernimmt das Interrupt handling, das ansonsten der Prozessor übernehmen würde.
	* (+) Belastet den Prozessor praktisch nicht

34
--
siehe 33

35
--
Stellt die Kommunikation zwischen der Hardware und der I/O-Verwaltung sicher. Abstrahiert die Hardware und verhindert, das jede Software Hardwareunterstützung für jede Hardware mitbringen muss.

36
--
* keine
* einfach Buffer
* doppelter (paralleler) Buffer
* Zirkulärer Buffer


X Window System
===============
37
--
Es wurde ein verteiltes, Hardwareunabhängiges, netzwerktransparentes System zur UI Anzeige benötigt.

38
--
Hardwareunabhängigkeit (Austauschbar, setzt auf Unix auf), Netzwerktransparent durch die Client/Server Architektur, alle Programme und Frameworks sind kompatibel, nur installierbar wenn wirklich notwendig, Legt die Oberfläche nicht fest, sondern verwaltet nur die Ansteuerung der Toolkits.

39
--
Textbasierte Schnittstelle::

	[Terminal]----Serielle Verbindung----[Serieschnittstellentreiber | BS Funktion für Zeichen Ein- und Ausgabe | Applikation]

40
--
* Verwaltung der eingehenden Events (Keyboard, Mouse, Touch, ...)
* Weiterleitung an die Applikation und Verarbeitung der Applikationevents
* Eventausgabe (Monitor). 
* Im Unterschied zu Wailand oder Mir besitzt X11 kein Compositor, sonder lagert das Zusammenführen der einzelnen GUI Elemente zu einem Ausgabebild an einen externen Compositor aus.

41
--
::

	[Ausgabegeräte, Eingabegeräte] <-> [X-Server] <-> [X-Client, Event Queue]
	
	
* Eingaben von Eingabegeräten landen direkt beim X-Server. Dieser stellt die Events in die EventQueue der betreffenden Applikationen (X-Clients). 
* Applikationen teilen dem X-Server mit, wenn sie etwas dargestellt möchten. Dieser lässt durch den Compositor die Ausgabe rendern und gibt Sie an das Ausgabegerät.
* Ein- und Ausgabegeräte sind somit nicht gekoppelt. So weiss z.B. Das Touchpanel des Bildschirms nichts von der Ausgabe und kann bei einer Rotation der Ausgabe nicht automatisch die Eingabe umkehren. Diese Aufgabe muss der X-Server übernehmen. Dies führt zu dem Problem, dass der X-Server über Jahre für neue Eingabegeräte erweitert werden musste, für die er ursprünglich nicht gedacht war.

42
--
* Verwaltet die Fenster. 
* Technisch nur ein weiterer X-Client neben den Applikationen.
* Bestimmt, wie Fenster auf dem Bildschirm dargestellt werden und verwaltet Fensterbewegungen.
* Stattet die Fensterleiste mit den entsprechenden Knöpfen aus.

43
--
Library, die dem Programmierer eine komfortablere Nutzung der X-Funktionalität ermöglicht.

44
--
Stellen eine elementare Benutzeroberfläche mit Grundfunktionen basierend auf dem X-Toolkit.

45
--
Definiert das Nachrichtenformat, mit dem X-Server und X-Clients über das Netzwerk kommunizieren.

46
--
* Die Pufferung dient der Traficminimierung zwischen Client und Server.
* Requestpuffer (Dienstanforderungen): Der Server leert seinen Puffer (und senden an den Client) wenn
	* der Client blockiert und auf ein Ereignis wartet
	* der Client eine Anfrage mit zwingender sofortiger Antwort an den Server gestellt hat
	* der Client eine Leerung explzit verlangt
* Ereignisse werden beim Server und beim Client gepuffert
	* der Server puffert zur Zusammenfassung von Events
	* der Client puffert eingehende Events (Meldungsschleife), bis er Zeit hat, diese abzuarbeiten
* Arten von Nachrichten:
	* Requests (client -> server)
	* replies (server -> client)
	* events (client -> server)
	* errors (server -> client)

47
--
X-Ressourcen speichern auf dem X-Server Infomationen im Auftrag des Clients (zur Traficreduktion). Beispiele:
* Window preferences
* Rastergrafiken
* Farbtabellen
* Schriften
* Eigenschaften von Grafikelementen

48
--
Die Fenster sind wie in einem Baum dem Hautfenster (Root window) untergegliedert. Wiederum sind deren Fensterinhalte Blätter der Fenster.

49
--
Einfache Formen und Linien

50
--
Die Farbtabelle stellt Shortcuts für die aktuell verwendeten Farben bereit. Dadurch wird der Trafic massiv verringert gegenüber einer direkten Nutzung von z.B. RGB

51
--
Ereignisse (Benutzereingaben (Keyboard, Maus, Touch, ...), Systemereignisse (Fenster anzeigen, ...)) werden an das Element unterhalb der Maus gesendet, das sich zu unterst im Baum befindet (an oberster Stelle auf dem Display befindet). Interessiert sich das Element nicht für das Ereignis, wird es an das Elternwindow weitergereicht, allenfalls bis hoch zum root window.


Windows GUI
-----------
52
--
* Programmgesteuerter Ablauf: Programmierung legt fest, in welcher Reihenfolge Programmteile ablaufen
	Beispiel: Stapelverarbeitung/Commandline (Stapelverarbeitungsregel legt Reihenfolge fest, Events können nicht in Ablauf eingreifen)
* Ereignisgesteuerter Ablauf: Reihenfolge der Ereignisse (Benutzerinteraktionen, Systemevents, Hardwareevents, ...) bestimmt, in welcher Reihenfolge die Programmteile ablaufen
	Beispiel: GUI (Programmteile werden anhand von Benutzerinteraktionen mit dem GUI aufgerufen. Die Reihenfolge wird durch die Eventreihenfolge bestimmt.)

53
--
Windows messages sind Ereignisse des Betriebsystems, die an die Applikationen weitergereicht werden.

**Aufbau** 
.. code-block:: c

	typedef struct tagMsg {
	    HWND hWnd; 	// windows handle
	    UINT message; 	// message type
	    WPARAM wParam; 	// 1. msg parameter
	    LPARAM lparam; 	// 2. msg parameter
	    DWORD time;	// time of event
	    POINT pt;	// actual position
	}


* Die Messages werden in die Message Queue eingereiht, dabei wird dynamisch Speicher alloziert. Beim Entnehmen der Messages aus der Queue wird der Speicher wieder freigegeben.

54
--
GUI-Thread
	Besitzen einen ereignisgesteuerten Programmablauf und jeweils eine eigene Ereigniswarteschlange. Von der Applikation nicht behandelte Ereignisse erfahren eine Standardbehandlung durch das BS.
Konsolen-Thread
	Besitzen einen programmgesteuerten Ablauf und haben keine eigene Ereigniswarteschlange. Können im Vordergrund oder im Hintergrund ablaufen.

55
--
* Mausklicke
* Fenstergrössenänderung, neu Zeichnen, schliessen
* Timer abgelaufen
* Tastatur Tasten events

56
--
Rechteckiges Fenster, bestehend aus:
	* Systembereich (Titelleiste mit Fensterschaltflächen, Menuleiste)
	* Anwendungsbereich mit Scrollbar
	
57
--
createWindow(...Fenstereigenschaften...); ShowWindow(Fenster); UpdateWindow(Fenster); // Anwendungsbereich neu zeichnen

58
--
Gepuffert
	* Vorteile: Meldungen landen in Warteschlange, Fenster wird mit DispatchMessage benachrichtigt
	* Anwendung: Usereingaben, Mausmeldungen, Window-Paint, Window-Timer, Window-Close

Direkt (Warteschlange wird umgangen)
	* Vorteile: direkter Aufruf der Fensterprozedur durch das BS
	* Nachteile: Warteschlange wird umgangen
	* Anwendung: Alle andern Events
	
59
--
* System: Behandlung durch DefWindowProc(), gepuffert/ungepuffert
* User-Thread: Direkte Übertragung durch SendMessage() (ungepuffert, Sender blockiert bis Empfänger Nachricht verarbeitet hat) oder PostMessage() (gepuffert)

60
--
Das Virtuel Keyboard ist Tastaturunabhängig und und besitzt alle erforderlichen Zeichen. Der Tastaturtreiber wandelt die Positionsangabe des Keyboardevents mittels des konfigurierten Tastaturtyps in den virtuellen Tastencode um.

61
--
Fenster stehen entweder in einer Eltern-Kind beziehung (Child Window wird auf Fläche des Eltern Window begrenzt und über diesem angezeigt) oder in einer Besitzer-Besitz Beziehung (Fenster, das einem andern Fenster gehört und immer vor diesem angezeigt wird). Die Z-Order definiert die Fensterreihenfolge, wobei Eltern Fenster immer zuunterst sind und neu erzeigte Fenster immer zu oberst.

62
--
Das Kindfenster erzeugt für relevante Ereignisse eine Meldung und sendet diese an das Elternfenster.

63
--
Elternfenster können Kindfenster nur über Meldungen beeinflussen.


Speichersystem
==============
64
--
Primärspeicher
	Dient der kurzzeitigen Ablage von Daten, ist direkt adressierbar und besitzt eine physische Datenorganisation mit nummerierten Speicherplätzen. (Hauptspeicher / Arbeitsspeicher)
Sekundärspeicher
	Dient der längerfristigen Lagerung von Daten, ist indirekt adressierbar über eine Schnittstellenhardware und/Software und besitzt eine logische Datenorganisation. (Platten, Bänder)
	
65
--
Direkt adressierbarer Speicher
	* Über die Adresse wird direkt die gewünschte Speicherstelle angesprochen. Es kann auf beliebige Speicherstellen zugegriffen werden.
	* Hauptanwendung: RAM/ROM

Mehrportspeicher
	* Speicher mit mehreren Zugriffspfaden. Mehrere Elemente können damit gleichzeitig auf den Speicher (sogar auf die gleiche Speicherzelle) zugreifen.
	
Schieberegister
	* Ein Bitmuster wird durch eine Kette von 1-Bit Speicherstellen geschoben, die Speicherstellen werden dabei nach bestimmten Regeln verknüpft. 
	* Hauptanwendung: Umwandlung von Daten
	
Fifo Speicher
	* Daten werden wie in einer Schlange abgelegt. Daten werden hinten in die Schlange eingefügt und vorne entnommen. Es kann immer nur das vorderste Element zugegriffen werden.
	* Hauptanwendung: Warteschlangen
	
Stack
	* Daten werden auf einen Stapel gelegt. Es kann immer nur das oberste (und damit zuletzt auf den Stapel gelegte) Element entnommen werden.
	* Hauptanwendung: Programmstack
	
Assoziationsspeicher (Content addressable memory CAM)
	* Daten werden über Teilinformationen abgerufen, analog Key/Value Storages
	
66
--
Die Maske definiert die Spalten des Musters, die mit dem Inhalt matchen müssen. In diesem Falle die Spalten 4 und 8

+------------+-----------------+---------+
| Suchmuster | 0 1 0 0 0 1 0 1 | Treffer |
+------------+-----------------+ -       |
| Maske      | 0 0 0 1 0 0 0 1 | Bit     |
+============+=================+=========+
| Speicher   | 0 1 0 0 0 0 0 1 | 1       |
| Inhalt     +-----------------+---------+
|            | 1 1 1 1 0 0 0 0 | 0       |
|            +-----------------+---------+
|            | 1 1 0 0 1 0 1 0 | 0       |
|            +-----------------+---------+
|            | 0 0 1 0 0 0 0 0 | 0       |
|            +-----------------+---------+
|            | 1 1 1 1 1 1 1 0 | 0       |
|            +-----------------+---------+
|            | 1 0 0 0 0 0 0 1 | 1       |
|            +-----------------+---------+
|            | 1 0 0 1 1 1 1 0 | 0       |
|            +-----------------+---------+
|            | 1 0 1 1 0 0 1 1 | 0       |
+------------+-----------------+---------+
| Resultate  | 0 1 0 0 0 0 0 1 |         |
| Zeilen 1,6 +-----------------+         |
|            | 1 0 0 0 0 0 0 1 |         |
+------------+-----------------+---------+
	
67
--
Ein sehr kleiner Teil der Daten werden immer wieder gebraucht, der Grossteil der Daten (95%) selten. Diesen Lokalitätseffekt kann man nutzen, um mit einen Cache Speicher zu realisieren, der 5% der Grösse des Hauptspeichers beträgt und doch einen Grossteil der Anfragen abdecken kann. -> Kosten- und Geschwindigkeitsoptimierung

68
--
::

	[CPU] -- [L1] -- [L2] -- [L3] -- [Hauptspeicher] <-> [HDD]


* Lx: Cache Speicher
* Prozessornahe Stufen sind schnell und teuer, prozessorferne gross und billig
* Daten, die der Prozessor benötigt, müssen zuerst in Prozessornahe Speicher transferiert werden


Cache Speicher
--------------

69
..
Verringerung der Zugriffszeit auf häufig gebrauchte Daten

70
..
.. code-block:: formula
	
	Geg: tc 1.1ns, tm 10.5ns, h 88%
	Ges: mittlere Zugriffszeit teff
	Lös:
	teff = h*tc+(1-h)*tm = 0.88*1.1ns+0.12*10.5ns = 2.2ns
		
	
71
..
Der Cache enthält Ausschnitte des Hauptspeichers. Möchte der Prozessor auf Inhalte zugreifen, die nicht im Cache sind, so müssen diese zuerst in den Cache geladen werden (Wird automatisch von der Cache Logik erledigt). Die Cache Steuerlogik ist in Hardware implementiert.

72
..
Arbeiten mehrere Prozessoren mit dem Cache, so ist nicht klar, ob die Daten im Cache noch aktuell sind oder nicht. Eine Möglichkeit zur Umgehung des Problems ist die Löschung (Markieren als ungültig) aller Caches bei einem Schreibzugriff (sehr langsam) oder ein Write through (Schreibzugriffe gehen immer in Cache+HS) (auch langsam).

73
..
* Erst wenn der Prozessor auf eine nicht im Cache vorhandene Adresse zugreifen will, kann der Inhalt aus dem HS nachgeladen werden -> Langsam
* Bei der Adressierung werden mehrere Byte zu einer Cache Zeile zusammengefasst werden. Müssen Inhalte in den Cache geladen werden, so muss immer die ganze Zeile geladen werden.
* Der Cache bringt nur lesenden Zugriffen eine Beschleunigung
* Peripherieadressräume dürfen NIE über den Cache angebungen werden, wegen den Hardwarestatuswerten
* Der Cache beschleunigt nur den HS, nicht aber Register oder logische Operationen
	
74
..
Cache-Speicher Grösse, Cache-Zeilen Grösse und die Organisationsform des Caches beeinflussen dessen Einflussfaktor auf die Leistung. Damit der Cache die Leistung positiv beeinflussen kann, muss er eine hohe Trefferrate aufweisen.

75
..
Grund dafür ist der SSD-Cache, der Schreibvorgänge Cached und dem System damit eine hohe Schreibgeschwindigkeit vorgaukelt. Ist die zu schreibende Datei grösser als der Cache, so muss die Datei direkt auf die Platte geschrieben werden und damit kommt die Geschwindigkeit der SSD und nicht die Geschindigkeit des Caches zum tragen.

76
..
Der gesammte Kopiervorgang läuft über den Prozessor. Die Daten werden von Speicher zu Speicher verschoben, bis sie den Prozessor erreicht haben und anschliessend wieder von Speicher zu Speicher verschoben (oder in die Caches und den HS durchgeschrieben (write through) bis sie auf der Platte angelangt sind.

Der Cache nutzt in diesem Fall überhaupt nichts. Im Gegenteil, die Kopiererei verlangsamt den Vorgang sogar.

Datenfluss::
	
	    +-- [L1] <-- [L2] <-- [L3] <-- [HS] <-- [HDD]
	    v
	[Prozessor]
	    |
	    +-- Write trough --> [HS] --> [HDD]

	
Heap
----

77
..
Der Heap ist ein Speicherbereich, indem Prozesse dynamisch Speicher allozieren können. Die Programme sind selbst dafür verantwortlich, dass der Speicher wieder freigegeben wird.

Schematische Darstellung::

	+------------------------+
	|                        |
	+------------------------+   ""\
	| arguments              |     |
	+------------------------+     |
	| environment            |     |
	+------------------------+     |
	| code                   |      \
	+------------------------+       } Application stuff
	| data                   |      /
	+------------------------+     |
	| stack                  |     |
	+------------------------+     |
	| heap                   |     |
	+------------------------+   ../
	|                        |
	|                        |
	+------------------------+   ""\
	| code                   |     |
	+------------------------+     |
	| daten                  |      \
	+------------------------+       } OS stuff
	| stack                  |      /
	+------------------------+     |
	| heap                   |     |
	+------------------------+   ../
	|                        |
	+------------------------+


78
..
Der Stack legt die neusten Daten zu oberst auf den Stapel. Wird die aktuelle Funktion beendet, wird dieser Bereich vom Stack abgeräumt und de Daten sind weg. Auf dem Heap verbleiben die Daten bis sie gelöscht werden.

Heap
	* Mit new angelegte Elemente
Stack
	* Methodenaufrufparameter
	* Rücksrungadresse
	* Framepointer
	* lokale Variablen

79
..
Daten, deren Gültigkeit über die Laufzeit der Funktion hinausgehen, in der sie erzeugt werden, müssen zwingend auf dem Heap abgelegt werden, damit sie weiterhin verfügbar sind.

80
..
C
	* malloc(size)
	* free(pointer)
	* nicht freigegebener Speicher bleibt reserviert, bis der Prozess beendet wird
	
C++
	* new type
	* delete pointer
	* nicht freigegebener Speicher bleibt reserviert, bis der Prozess beendet wird
	
Java
	* new
	* durch Garbage Collection
	* Garbage Collection räumt nicht mehr referenzierte Objekt automatisch irgendwann ab
	
Desktop / Server
	Server laufen unter umständen Jahre. Entsprechend laufen einige Serverprozesse auch Jahre. Würde ein Programm vergessen Speicher dreizugeben, wäre der Speicher irgendwann voll. Bei Desktops ist dies weniger ein Problem, da die Prozesse meist beendet werden, bevor der Speicher volllaufen kann.

81
..
* systeminterne Meldungen
* systeminterne Tabellen und Objekte
* Sprachübergreifende Speicherbereitstellung

82
..
variable Zuordnungsgrösse
	System
		Es können beliebige Bereich belegt werden
	Vorteile
		keine interne Fragmentierung
	Probleme
		Externe Fragmentierung
	Schema
		::

			    |--A--|--F--|     |----E----|---G---|  |-H-|


	Verwaltungsdaten (Freiliste beginnend bei 1000)
		::

			[1000|40| -]-->[1140|50| -]-->[1350|20| -]-->


	Suchalgorithmen
		* first fit: List durchgehen, erste Lücke die ausreichend gross ist, wird genommen
		* next fit: List durchgehen, beginnen an der zuletzt aufgehörten Stelle bis eine Lücke ausreichender Grösse gefunden wurde
		* best fit: Gesammte Liste wird nach optimaler Lücke durchsucht
		* Worst fit: Ganze Liste nach der grössten Lücke durchsuchen

Feste Grössenklassen
	System
		Es gibt verschieden Grössenklassen. Bei der Belegung wird auf die nächste aufgerundet.
	Vorteile
		effiziente Suche, Kleine Blöcke können kombiniert und grosse rekombiniert werden
	Problem
		Interne Fragmentierung
	Schema
		::

			     |-A-  |---B---   |     |-C-  |          |----D---- |


	Verwaltungsdaten
		::

			50er: [1000| -]-->[1200| -]-->
			100er:[1300| -]-->
	
	
	Suchalgorithmen
		* Quick Fit: Getrennte Listen für die verschiedenen Lückengrössen -> es kann jeweils die erste freie Lücke gewählt werden

Allozierung in mehrfachen von festen Blöcken
	System
		Es gibt eine Blockgrösse, es können mehrere aufs Mal belegt werden. Eine Bit-Blockzuordnung listet zusammengehörige auf.
	Vorteile
		keine externe Fragmentierung, wenig interne Fragmentierung
	Probleme
		interne Fragmentierung, u.U. lange Suchzeiten bis freie Blöcke gefunden
	Schema
		::

			|  |  |--|--|--|  |--|--|--|  |  |  |


	Verwaltungsdaten
		::

			Bit-Block-Belegung: 0 0 1 1 1 0 1 1 1 0 0 0
			[L|0|2| -]-->[P|3|3| -]-->[L|5|1| -]-->[P|6|3| -]-->[L|9|3|  ]


	Suchalgorithmen
		* Liste durchsuchen

Buddy System
	System:
		Es können Blöcke beliebiger von der Grösse beliebiger 2er Potenzen belegt werden, die Blöcke sind nach Grösse sortiert. Blöcke werden durch aufteilen eines Grösseren in zwei Teile (Buddies) geschaffen. Freie Buddies können rekombiniert werden. Es werden einzelne Freilisten geführt pro Grösse.
	Vorteile
		Schnelles Auffinden von freien Lücken, einfache Rekombination
	Probleme
		interne Fragmentierung
	Schema
		::

			|----|    |        |----------------|                                |


	Verwaltungsdaten
		::

			64er: [64| -]-->
			128er: [128| -]-->
			256:
			512er: [512| -]-->


	Suchalgorithmen
		* Wenn sich in Freigabelist der benötigten Grösse kein freies Feld mehr befindet -> grössere Felder solange zweiteilen (Buddies), bis ein freies Feld vorliegt

83
..
Nur indirekt über die Allozierung und Freigabe von Elementen kann zusammenhängender Speicher freigegeben werden in der Hoffnung, das Betriebsystem kann die Bereiche rekombinieren.

84
..
Die Metadaten der Heap Verwaltung beinhalten sämmtliche Angaben über den Aufbau des Heaps, die Freigabelisten, etc. Sie werden entweder

direkt beim betreffenden Heap Bereich gespeichert
	* Vorteil: einfach zum freigeben beim Prozessende
	* Nachteil: über den HS verstreut
in einem zentralen Bereich für Heap Metadaten
	* Vorteil: effiziente Adressierung für das BS
	* Nachteil: aufwändiger, Bereiche freizugeben
		
85
.. 
interne Fragmentierung
	Es werden grössere Blöcke (nach Grössenklassen oder festen Grössen) als effektiv benötigt alloziert. Dadurch gibt es innerhalb des Blockes Verschnitt.
externe Fragmentierung
	Im HS gibt es Bereiche, die zu klein sind um sie zu belegen oder eine Belegung füllt nicht die Gesammte Lücke und es gibt Rest.
	
86
..
Lückenelliminierung durch Verschieben belegter Bereiche (Defragmentierung)

87
..
Master Pointer zeigen auf die Startadresse des Heap. Die Applikation greift mittels MP zu. So kann die Heap Verwaltung den Heap umkopieren, ohne dass die Applpikation etwas davon merkt.

88
..
Es gibt keine garantierte Zugriffszeit bei den Suchalgorithen für freie Lücken. Daher ist diese Heapordnung nicht für Echtzeit Systeme geeignet.

89
..

Prozessadressräume
==================
90
--
.bss
	uninitialisierte Daten
.data
	initialisierte Daten
.text
	Programmcode
		
91
--
Die Sektionen werden in den Hauptspeicher vor den Heap Bereich kopiert.

92
--
Eine HS Sektion, die 1:1 Teile eines Files abbilden

93
--
Eine Region beschreibt einen belegten Bereich im Prozessadressraum (z.B. Startaddr. des belegten Bereichs, Grösse, Schutzattribute, zugehöriger Hintergrundspeicher).


Programmübersetzung
===================
94
--
* Der Programmcode wird übersetzt und zusammen mit Libraries gebunden.
* Compilation: Programmcode wird in Assemblerquellcode übersetzt
* Assemblierung: Assembler Quellprogramm wird ins Objektformat (Maschinencode+Zusatzinformationen) übersetzt
* Linkage: Objektformatdateien werden zusammen mit Bibliotheksobjektformatdateien gebunden und erneut als lad- und ausführbares Objektformat abgelegt.

Darstellung::

	[preprocessor]->[compiler]->[assembler]->[linker]->Objektformat

	
95
--
Einschritt-Übersetzung
	Der Quellcode wird in einem Schritt kompiliert und Bibliotheken gebunden.
Mehrweg Übersetzung
	Der Quellcode wird einzeln (jede Datei einzeln) kompiliert und in weiteren Schritten mit den andern Dateien und Libraries gebunden.
	
96
--
Der Compiler besitzt verschiedene Ausgabemodule für verschiedene Plattformen. Die IR abstrahiert die compilierung von der Ausgabe. Der Src-Code wird Plattformunabhängig in die IR umgewandelt und dann erst durch das spezifische Ausgabemodul für die Plattform erzeugt.

97
--
siehe 95.

Vorteil der Mehrweg Übersetzung: Wenn eine einzelne Klasse geändert wurde, muss nur diese neu kompiliert und anschliessend alles gebunden werden (effizienter, schneller).

98
--
preprocessing & compilation
	Die Dateien werden einzeln in Assembler Quellcode übersetzt
assembling
	Aus dem Assembler Quellcode werden ungebundene Objektdateien erzeugt.
bindung
	1) Die Objektdateien werden gebunden, ebenfalls die Objektdateien der Bibliotheken
	2) Die gebundenen Objektdateien und die gebundenen Bibliotheken werden zusammengebunden
		
99
-- 
Funktion
	Die T-Notation stellt die Übersetzung und Ausführung in Bezug auf die Plattform dar.

Symbole::

	| zz | Maschine mit zz Prozessor

	| P | Programm p mit Logik x
	| x |

	| E | Eingabe

	| A | Ausgabe

	| A --> B | Übersetzer von A nach B in der Form X
	   | X |


Direkte Ausführung::

	| E | calc | A | Ausführung auf der gleichen Maschine (68k auf 68k)
	    |_68k__|
	    | 68k  |


Interpretation::

	| E | calc | A | Ausführung über Java Virtual Machine auf k68 Prozessor
	    |_java_|
	    | Java |
	    |_68k__|
	    | 68k  |


Resident Compiler::

	| calc |             | calc | Programm in c++, das auf einer k68er Plattform für einen k68er Prozessor übersetzt wird
	| c++  | c++ --> 68k | 68k  |
	           |_68k_|
	           | 68k |


Cross Compiler::

	| calc |             | calc | Programm in c++, das auf einer k68er Plattform für einen x86er Prozessor übersetzt wird
	| c++  | c++ --> x86 | x86  |
	           |_68k_|
	           | 68k |


Cross Assembler::

	| num  |              | num  | Programm in 68k Assembler, das auf einer pentium Plattform für einen 68k Prozessor übersetzt wird
	| A68k | A68k -> O68k | O68k |
	           |_pent_|
	           | pent |

	           
100
---
Crosscompiler
	Erzeugt Code für eine andere Plattform, als die auf der der Compiler läuft
Crossassembler
	Erzeugt Objektdateien für eine Plattform x aus Assemblerquellcode für die Plattform x auf der Plattform y
Resident Compiler
	Erzeugt Aus Quellcode Maschinencode für die aktuelle Plattform. Aus einem Crosscompiler kann ein Residentcompiler erzeugt werden.
		
101
---
Liegt bereits ein Crosscompiler für die Plattform vor, kann der Residentcompiler aus dieser compiled weren.

102
---
Linkt Objektdateien und Objektbibliotheksdateien für eine Andere Plattform als die, auf der er selber läuft.

103
---
Direkte Ausführung
	Der Quellcode wird direkt in Maschinencode für die entsprechende Hardware übersetzt und auf der Hardware ausgeführt
Interpretierte Ausführung
	Der Quellcode wird in Bytecode übersetzt, der in einer virtuellen Maschine erneut interpretiert und für die aktuelle Plattform in Maschinencode umgewandelt wird. (1 Zwischenschritt)
	
104
---
* Ausführbarer Maschinencode
* Daten
* Zusatzinformationen über Extern und Public Elemente

105
---
Noch nicht ladbare Objektdatei mit vorläufigen Adressen für Code und Daten, die beim binden umplatziert (reloziert).

106
---
Bei 0.

107
---
Diese Information steht in der Relozierungstabelle in der Objektdatei.


Realer Speicher
===============

108
---
Beim Realen Speicher verwenden die Programme physische Adressen (die ev. Basisversetzt sind). Den Speicher, den die Programme brauchen, muss auch physisch vorhanden sein.

Die Progamme belegen den Speicher als Blöcke oder Partitionen. Im Unterschied zum virtuellen Speicher kommt es nicht vor, das das Programm über den Speicher verstreut wird.

109
---
* Monoprogrammierung bedeutet, das nur ein Programm gleichzeitig laufen kann.
* Da der Speicher somit jeweils nur für ein Programm Platz bereits stellen muss, kann gut mit Realem Speicher gearbeitet werden.
* Das Programm hat jedoch nur soviel Speicher zur Verfügung, wie effektiv vorhanden ist.

110
---
Vorteile
	* Es ist einfach, es braucht kein Partitionsmanagement
	* Die Anzahl Partitionen ist von Anfang an festgelegt und bestimmt die Anzahl paralleler Prozesse
Nachteile
	* Eine Partition belegt unter Umständen mehr Platz als der Prozess effektiv benötigt
	* Braucht ein Prozess mehr Speicher als die grösste Partition bieten kann, kann er nicht ablaufen

111
---
Gemeinsame Warteschlange
	* Keine Prozesse warten unnötig, weil sie drankommen, sobald eine Partition frei wird
	* Partitionen werden nicht optimal benutzt, viel nicht gebrauchter Speicher ist frei, kann aber nicht genutzt werden
Einzelne Warteschlange
	* Prozesse tragen sich immer beim kleinstmöglichen Prozess ein -> optimale Speicherausnutzung
	* Prozesse warten unnötig, obwohl es freie Partitionen geben würde

112
---
Jedes Programm kann auf jede Adresse zugreifen. Dadurch kann es in eine für ihn gar nicht bestimmten Bereich schreiben.

Gelöst werden kann dies durch einen Schlüssel, der die Partition freigibt und vom BS vergeben wird oder durch Basisversetzte Adressen

113
---
Die CPU enthält zwei Register, ein Basisregister und ein Limitregister. Das Basisregister wird zur Adresse hinzugezählt. Dadurch beginnt jede Adresse automatisch frühestens am Partitionsbeginn.

Die Basisversetzte Adresse wird mit dem Limitregister verglichen. Ist sie grösser, so überschreitet die Adresse die obere Partitionsgrenze und eine Speicherverletzung liegt vor.

Basisversetzte Speicheradressierung::

	                      | Grenzregister
	                      v
	Al ----> (+) --Ap--> (<) ----> Ap
	          ^           |
	Basisreg. |           v Schutzverletzung


114
---
Lösungen
	* Jedes Programm verbraucht eine so grosse Partiton, wie es effektiv Speicher verbraucht
Probleme
	* Eine Fragmentierung des Speichers führt dazu, dass Programme verschoben werden müssen, was zusäzlichen Rechenaufwand erfordert
	* Wachsen Programme während der Ausführung, muss entweder von Anfang an Reservespeicher zur Verfügung gestellt werden, oder die Programme verschoben werden

115
---
Bei gleicher I/O Wartezeit
	::

		A Auslastung
		p Zeitanteil für I/O Warten
		n Anzahl Prozesse

		A = 1 - p^n


Bei ungleicher I/O Wartezeit
	Warteschlangentheorie

116
---
Overlay Technik
	Teile des Programmcodes werden erst bei bedarf nachgeladen und überlagern (overlay) gerade nicht benötigte Programmteile. Die Übersetzungswerkzeuge müssen dazu de Code entsprechend analysieren und in Overlays einteilen, sodass kein noch gebrauchter Code überschrieben wird.
Swapping
	Inaktive Prozesse werden in die Swapping Area auf der Festplatte ausgelagert und benötigen somit keinen Speicher mehr im Hauptspeicher, bis sie wieder weterlaufen müssen.

117
---
::

	Geg:
		n = 5 Prozesse
		s = 5MB Specherbedarf
		t = 15MB/s Transferrate
		r = 200ms Rechenzeit
		w = 500ms Wartezeit
	Ges:
		z Zeitbedarf für Swapin/out in %
	Lös:
		ta = s / t = 5MB / 15MB/s = 1/3s Ein-/Auslagerungszeit
		tt = 2*ta + r = 3000ms*2+200ms = 6200ms Einlagern/Rechen/Auslagern
		ws = 6000ms/6200ms = 97% der Zeit wird für Swapping benötigt
		cpu = 1-0.97^5 = 14% CPU Auslastung


Virtueller Speicher
===================
118
---
* Jeder Prozess hat scheinbar den kompletten Speicher für sich alleine.
* Jeder Prozess kann nur die eigenen Inhalte lesen und schreiben.
* Es ist mehr Speicher vorhanden, als real in Hardware vorhanden

119
---
Virtual Memory Manager: Verwaltet den Virtuellen Speicher und Speicherzugriffe

120
---
MMU
	Memory Management Unit: übernimmt das Umsetzen der logischen Adresse in eine reale. Besteht aus der TLB und einem Zeigeregiter, das auf die Seitentabellen im Hauptspeicher zeigt.
TLB
	Translation lookaside Buffer: Buffer in der MMU, der einen Teil der Seitentabellen beinhaltet. Wird bei einem Prozesswechsel geflushed, darum sind Prozesswechsel "teuer".

121
---
Virtueller Speicher ist wesentlich aufwändiger als realer, sodass für eine vernünftige Performance die Hardware entsprechende Funktionen zur Verfügung stellen muss. Das Betriebssystem muss Virtuellen Specher unterstützen, weil es für die HS-Verwaltung verantwortlich ist.

**Speicherzugriffablauf**

	::

		Adresszugriff --> Adresse im RAM vorhanden ---------------------------------> Adressinhalte zurückgeben
		      |                                                                                 ^
		      v                                                                                 |
		Seite im RAM --> Freier Seitenrahmen vorhanden? --> Ja ---------------------> Seite in Rahmen laden 
		nicht vorhanden                |                                                  ^          ^
		      |                        v                                                  |          |
		      V                      Nein --> Zu überschreibender Seitenrahmen --> Seite unverändert |
		Page in Auslagerungs-                 wählen (Opfer)                                         |
		datei nicht vorhanden                              |                                         |
		      |                                            v                                         |
		      V                                  Seite wurde verändert --> Seiteninhalte speichern --'
		Speicherschutzverletzung                                                  (auslagern)


122
---
Segmentbasierte Umsetzung
	* Jedes Programm erhält ein Segment, so gross wie es Speicher braucht
	* Die Segmente werden als Ganzes auf den Speicher abgebildet
	* (-) Nicht Transparent
	* (-) Mögliche Externe Fragmentierung
	* (-) Teures Auslagern
	* (+) Keine Segment-Interne Fragmentierung
Seitenbasierte Umsetzung
	* Der Speicher wird in gleich grosse Blöcke (Seiten) unterteilt
	* Es können nur ganze Blöcke genutzt werden
	* (-) Verschnitt innerhalb derPages
	* (+) Einfache HS Verwaltung
	* (+) Kein externer Verschnitt
	* (+) Effizientes Auslagern
Kombinationsverfahren
	* Segmente werden im virtuellen Adressraum platziert und dieser anschliessend über Pages auf den HS abgebildet
	* (+) kaum interne Fragmentierung
	* (+) Verwendung segmentbasierter Attribute (Schreibsperre für Codesegment, ...) einfach

123
---
Segmentbasiert
	?
Seitenbasiert
	Platzbedarf = 2^(#bit der virt. Adresse) * Seitendeskriptorgrösse (B) / Seitengrösse (B)
Kombiniert
	?

124
---
* Mehrstufige Tabellen
* Grössere Seitengrösse
* Invertierte Seitentabelle (Prozessidentifikation, Seitennummer, Seitenrahmen)

125
---
Speicher, den mehrere Prozesse sehen und verwenden können.

Umsetzung: Das BS fügt die Seitendeskriptoren in die Umsetzungstabellen beider Prozesse ein.


s