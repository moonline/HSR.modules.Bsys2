======================================
Bsys2 FS13 Repetitionsfragen Antworten
======================================

Repetitionsfragen: https://github.com/moonline/Bsys2/blob/master/RepetitionQuestions.Bsys2.tex


Sicherheit
==========
1)
	* Softwarefehler / zu hohe Komplexität
	* Sicherheit ist zusätzlich Aufwand / mühsam
	* das BS berücksichtigt Sicherheit zu wenig

2)
	* Information abfangen (interception)
	* Information modifizieren (modifikation)
	* Information unterbrechen (interruption)
	* Information einspeisen (fabrication)

3) Eine Berechtigunggsprüfung

4)
	* Personalisierung und Authorisierung
	* Identifizierung und Zugriffskontrolle

5) Benutzerverwaltung, Anmeldesystem, Zugrifskontrolle

6) 	Es gibt Domänen und Objekte (Files, Drucker, ...).
	Die Rechte sind mit Tupels (Domäne, Rechte) definiert.
	z.B. (D1, r1rw2rwx4) gibt der Domäne1 leserechte für Objekt1, lese- und schreibrechte für Objekt2 und lese-, schreib- und ausführungsrechte für Objekt4.
	Die Rechte können auch als Matrix dargestellt werden.
	Benutzer melden sich als Domäne an und besitzen somit deren Rechte.

7) Tabelle, in welche die Objekte die Spalten und die Domänen die Zeilen bilden. Die Rechte sind in den Feldern eingetragen.

8)
	Strategie
		definiert, was geschützt werden soll (Schutzobjekte),
	Mechanismus
		definiert, wie der Schutz umgesetzt werden soll (technikorientiert)

9) Definieren, wie weit ein Benutzer die Schutzmatrix verändern darf und z.B. einem andern Benutzer Rechte auf ein Objekt zu geben.

10) 
	Kopierrecht
		Recht zum Kopieren von Rechten. Varianten: Volles Kopierrecht, Rechtetransferrecht, Limitiertes Kopierrecht

11) Objekte besitzen Owner, der darauf volle Rechte hat (Rechte einfügen, Rechte entfernen, Besitzrecht weitergeben).

12) Recht zum Ändern aller Rechte einer Domäne.

13)
	Ownerkonzept
		Sämmtliche Felder in den Spalten seiner Objekte
	Kontrollkonzept
		Sämmtliche Felder in den Zeilen seiner Domäne

14)
	Zugriffsliste als globale Tabelle mit Trippeln:
		- (-) verändern der Rechte bedingt durchgehen der Liste
	Zugriffsliste pro File (ACL):
		- (+) Rechte schnell gefunden bei Zugriff
		- (-) Löschen der Rechte einesgelöschten Users schwierig
	Zugriffsliste pro Domäne (Ticket Liste):
		- (+) Rechte einer Domäne sind zusammen abgelegt
		- (+) Löschen einer Domäne einfach
		- (-) Technisch anspruchsvoll umzusetzen

15)
	* Benutzerbestimmt: Benutzer (owner) bestimmt, wer was mit seinen Objekten macht
	* Systembestimmt: System/Organisation bestimmt, wer was mit welchen Objekten macht

16) Der Benutzer soll zu jedem Zeitpunkt so wenig Zugriff wie möglich aber so viel wie nötig besitzen -> keine unnötigen Rechte.

17) Bell/Padula: Objekte sind Sicherheitsstufen zugeordnet. Benutzer darf Objekte gleicher und schwächerer Stufen lesen, aber nur Objekte gleicher oder höherer Stufe schreiben.

18) Prozess sollte nur dann Rechte für ein Objekt besitzen, wenn er es gerade braucht. Da jedoch nur das Programm selbst weis, wann dies zutrifft, hat der Prozess den Grossteil der Zeit Rechte, die er gar nicht benötigt.


Unix Sicherheit
===============
19)
	* Datei besitzt Rechte für Owner, Gruppe und Andere.
	* Root darf alles.
	* Für Owner, Gruppe und Andere können einzeln r-, w- und ausführungsrechte gesetzt werden.

20)
	* Domänen: Owner, Group, Other
	* Objekte: Files, Prozesse
	
21) Benutzerbestimmt

22)

23)
	* Ausführen der Datei mit Rechten der Benutzers oder der Gruppe statt mit den Rechten der Datei.
	* Datei kann für jeden Benutzer mit dessen Rechten ausgeführt werden.

24) Rechtetemplate für neue Dateien

25) Benutzer kann einen einzelnen Befehl oder mehrere mit den Rechten eines andern Benutzers ausführen (minimal Priviledges).


Windows Sicherheit
==================
26) Dateien sind ein Owner und eine oder mehrere Groups zugeordnet. Der Owner hat das alleinige Recht die Rechte zu ändern. Die Rechteverwaltung basiert auf ACL's. Der Administrator unterliegt ebenfalls den gesetzten Rechten der Rechteverwaltung. Er kann aber Owner werden (take Ownership).
Laufwerke,  Drucker, etc. unterliegen auch den ACL's. Mittels Gruppenrichtlinien können zusätzliche Rechte gesetzt werden und auch Zugriffe auf Dienste gesteuert werden.

27) 
	* Domänen: Benutzer, Gruppen
	* Objekte: Dateien, Laufwerke, Drucker, Dienste, ...


Unix Scripting
==============
28) Die Shell selbst ist nur eine Anwendung, genauso wie alle andern auch. Die bekanntesten sind die Bourne Shell und die Bash.

29) Das Kapseln von mehreren Befehlen in ein Skript zur Administration des Systems und zur Automation von Aufgaben. Bsp: ein Backup-Skript überprüft Dateien auf das Änderungsdatum, packt geänderte in ein tar Archiv und legt kopiert das Archiv auf eine Backup Platte, wo sie wieder entpackt werden.

30)
	* Einrichten des Systems
	* Wartungsaufgaben
	* Aufgaben, für die UI notwendig ist (z.B. File konvertierung, Backup)

31) Das Auflösen und Einsetzen von Variablen und Ausdrücken in einer Befehlszeile vor dem eigentlichen Ausführen.

32) Sie teilt dem System mit, mit welcher Shell das Skript ausgeführt werden soll.


Ein-/Ausgabe
============
33)
	Über den Prozessor
		Die Daten werden von der Eingabe eingelesen, durch den Prozessor verarbeitet und auf die Ausgabe geschrieben.
			- (-) Belastet den Prozessor unnötig stark.
	Interrupt gesteuert
		Der Prozessor wird durch Interrupts unterrbochen und steuert jeweils den Transfer. Die Daten laufen nicht über den Prozessor.
			- Prozessor wird weniger belastet als oben, aber mehr als bei DMA K.
	DMA Kontroller
		Der Prozessor initiert den Prozess, anschliessend läuft er über den DMA Kontroller. Der Prozessor wird erst wieder gestört, um die Fertigstellung mitzuteilen.
			- (+) Belastet den Prozessor praktisch nicht

34) siehe 33

35) Stellt die Kommunikation zwischen der Hardware und der I/O-Verwaltung sicher. Abstrahiert die Hardware und verhindert, das jede Software Hardwareunterstützung für jede Hardware mitbringen muss.

36) 
	* keine
	* einfach Buffer
	* doppelter (paralleler) Buffer
	* Zirkulärer Buffer


X Window System
===============
37) Es wurde ein verteiltes, Hardwareunabhängiges, netzwerktransparentes System zur UI Anzeige benötigt.

38) Hardwareunabhängigkeit (Austauschbar, setzt auf Unix auf), Netzwerktransparent durch die Client/Server Architektur, alle Programme und Frameworks sind kompatibel, nur installierbar wenn wirklich notwendig, Legt die Oberfläche nicht fest, sondern verwaltet nur die Ansteuerung der Toolkits.

39) [Terminal]----Serielle Verbindung----[Serieschnittstellentreiber | BS Funktion für Zeichen Ein- und Ausgabe | Applikation]

40) Verwaltung der eingehenden Events (Keyboard, Mouse, Touch, ...), Weiterleitung an die Applikation und Verarbeitung der Applikationevents, Eventausgabe (Monitor). Im Unterschied zu Wailand oder Mir besitzt X11 kein Compositor, sonder lagert das Zusammenführen der einzelnen GUI Elemente zu einem Ausgabebild aus.

41) [Ausgabegeräte, Eingabegeräte] <-> [X-Server] <-> [X-Client, Event Queue]
	Eingaben von Eingabegeräten landen direkt beim X-Server. Dieser stellt die Events in die EventQueue der betreffenden Applikationen (X-Clients). Applikationen teilen dem X-Server mit, wenn sie etwas dargestellt möchten. Dieser lässt durch den Compositor die Ausgaberendern und gibt Sie an das Ausgabegerät.
	Ein- und Ausgabegeräte sind somit nicht gekoppelt. So weiss z.B. Das Touchpanel des Bildschirms nichts von der Ausgabe und kann bei einer Rotation der Ausgabe nicht automatisch die Eingabe umkehren. Diese Aufgabe muss der X-Server übernehmen. Dies führt zu dem Problem, dass der X-Server über Jahre für neue Eingabegeräte erweitert werden musste, für die er ursprünglich nicht gedacht war.

42) 
	* Verwaltet die Fenster. 
	* Technisch nur ein weiterer X-Client neben den Applikationen.
	* Bestimmt, wie Fenster auf dem Bildschirm dargestellt werden und verwaltet Fensterbewegungen.
	* Stattet die Fensterleiste mit den entsprechenden Knöpfen aus.

43) Library, die dem Programmierer eine komfortablere Nutzung der X-Funktionalität ermöglicht.

44) Stellen eine elementare Benutzeroberfläche mit Grundfunktionen basierend auf dem X-Toolkit.

45) Definiert das Nachrichtenformat, mit dem X-Server und X-Clients über das Netzwerk kommunizieren.

46) Die Pufferung dient der Traficminimierung zwischen Client und Server.
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
	
47) X-Ressourcen speichern auf dem X-Server Infomationen im Auftrag des Clients (zur Traficreduktion). Beispiele:
	* Window preferences
	* Rastergrafiken
	* Farbtabellen
	* Schriften
	* Eigenschaften von Grafikelementen

48) Die Fenster sind wie in einem Baum dem Hautfenster (Root window) untergegliedert. Wiederum sind deren Fensterinhalte Blätter der Fenster.

49) Einfache Formen und Linien

50) Die Farbtabelle stellt Shortcuts für die aktuell verwendeten Farben bereit. Dadurch wird der Trafic massiv verringert gegenüber einer direkten Nutzung von z.B. RGB

51) Ereignisse (Benutzereingaben (Keyboard, Maus, Touch, ...), Systemereignisse (Fenster anzeigen, ...)) werden an das Element unterhalb der Maus gesendet, das sich zu unterst im Baum befindet (an oberster Stelle auf dem Display befindet). Interessiert sich das Element nicht für das Ereignis, wird es an das Elternwindow weitergereicht, allenfalls bis hoch zum root window.


Windows GUI
-----------
52) 
	* Programmgesteuerter Ablauf: Programmierung legt fest, in welcher Reihenfolge Programmteile ablaufen
		Beispiel: Stapelverarbeitung/Commandline (Stapelverarbeitungsregel legt Reihenfolge fest, Events können nicht in Ablauf eingreifen)
	* Ereignisgesteuerter Ablauf: Reihenfolge der Ereignisse (Benutzerinteraktionen, Systemevents, Hardwareevents, ...) bestimmt, in welcher Reihenfolge die Programmteile ablaufen
		Beispiel: GUI (Programmteile werden anhand von Benutzerinteraktionen mit dem GUI aufgerufen. Die Reihenfolge wird durch die Eventreihenfolge bestimmt.)

53) Windows messages sind Ereignisse des Betriebsystems, die an die Applikationen weitergereicht werden.
	* Aufbau: 
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

54)
	* GUI-Thread: Besitzen einen ereignisgesteuerten Programmablauf und jeweils eine eigene Ereigniswarteschlange. Von der Applikation nicht behandelte Ereignisse erfahren eine Standardbehandlung durch das BS.
	* Konsolen-Thread: Besitzen einen programmgesteuerten Ablauf und haben keine eigene Ereigniswarteschlange. Können im Vordergrund oder im Hintergrund ablaufen.
	
55) 
	* Mausklicke
	* Fenstergrössenänderung, neu Zeichnen, schliessen
	* Timer abgelaufen
	* Tastatur Tasten events
	
56) Rechteckiges Fenster, bestehend aus:
	* Systembereich (Titelleiste mit Fensterschaltflächen, Menuleiste)
	* Anwendungsbereich mit Scrollbar
	
57) createWindow(...Fenstereigenschaften...); ShowWindow(Fenster); UpdateWindow(Fenster); // Anwendungsbereich neu zeichnen

58)
	Gepuffert
		Vorteile: Meldungen landen in Warteschlange, Fenster wird mit DispatchMessage benachrichtigt
		Anwendung: Usereingaben, Mausmeldungen, Window-Paint, Window-Timer, Window-Close
	Direkt (Warteschlange wird umgangen)
		Vorteile: direkter Aufruf der Fensterprozedur durch das BS
		Nachteile: Warteschlange wird umgangen
		Anwendung: Alle andern Events
		
59)
	* System: Behandlung durch DefWindowProc(), gepuffert/ungepuffert
	* User-Thread: Direkte Übertragung durch SendMessage() (ungepuffert, Sender blockiert bis Empfänger Nachricht verarbeitet hat) oder PostMessage() (gepuffert)
	
60) Das Virtuel Keyboard ist Tastaturunabhängig und und besitzt alle erforderlichen Zeichen. Der Tastaturtreiber wandelt die Positionsangabe des Keyboardevents mittels des konfigurierten Tastaturtyps in den virtuellen Tastencode um.

61) Fenster stehen entweder in einer Eltern-Kind beziehung (Child Window wird auf Fläche des Eltern Window begrenzt und über diesem angezeigt) oder in einer Besitzer-Besitz Beziehung (Fenster, das einem andern Fenster gehört und immer vor diesem angezeigt wird). Die Z-Order definiert die Fensterreihenfolge, wobei Eltern Fenster immer zuunterst sind und neu erzeigte Fenster immer zu oberst.

62) Das Kindfenster erzeugt für relevante Ereignisse eine Meldung und sendet diese an das Elternfenster.

63) Elternfenster können Kindfenster nur über Meldungen beeinflussen.


Speichersystem
==============
64)
	Primärspeicher
		Dient der kurzzeitigen Ablage von Daten, ist direkt adressierbar und besitzt eine physische Datenorganisation mit nummerierten Speicherplätzen. (Hauptspeicher / Arbeitsspeicher)
	Sekundärspeicher
		Dient der längerfristigen Lagerung von Daten, ist indirekt adressierbar über eine Schnittstellenhardware und/Software und besitzt eine logische Datenorganisation. (Platten, Bänder)
		
65)
	Direkt adressierbarer Speicher
		Über die Adresse wird direkt die gewünschte Speicherstelle angesprochen. Es kann auf beliebige Speicherstellen zugegriffen werden.
		Hauptanwendung: RAM/ROM
	Mehrportspeicher
		Speicher mit mehreren Zugriffspfaden. Mehrere Elemente können damit gleichzeitig auf den Speicher (sogar auf die gleiche Speicherzelle) zugreifen.
	Schieberegister
		Ein Bitmuster wird durch eine Kette von 1-Bit Speicherstellen geschoben, die Speicherstellen werden dabei nach bestimmten Regeln verknüpft. 
		Hauptanwendung: Umwandlung von Daten
	Fifo Speicher
		Daten werden wie in einer Schlange abgelegt. Daten werden hinten in die Schlange eingefügt und vorne entnommen. Es kann immer nur das vorderste Element zugegriffen werden.
		Hauptanwendung: Warteschlangen
	Stack
		Daten werden auf einen Stapel gelegt. Es kann immer nur das oberste (und damit zuletzt auf den Stapel gelegte) Element entnommen werden.
		Hauptanwendung: Programmstack
	Assoziationsspeicher (Content addressable memory CAM)
		Daten werden über Teilinformationen abgerufen, analog Key/Value Storages
		
66)	Die Maske definiert die Spalten des Musters, die mit dem Inhalt matchen müssen. In diesem Falle die Spalten 4 und 8

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
	
67) Ein sehr kleiner Teil der Daten werden immer wieder gebraucht, der Grossteil der Daten (95%) selten. Diesen Lokalitätseffekt kann man nutzen, um mit einen Cache Speicher zu realisieren, der 5% der Grösse des Hauptspeichers beträgt und doch einen Grossteil der Anfragen abdecken kann. -> Kosten- und Geschwindigkeitsoptimierung

68)
	* [CPU] -- [L1] -- [L2] -- [L3] -- [Hauptspeicher] <-> [HDD]
	* Lx: Cache Speicher
	* Prozessornahe Stufen sind schnell und teuer, prozessorferne gross und billig
	* Daten, die der Prozessor benötigt, müssen zuerst in Prozessornahe Speicher transferiert werden
	

Cache Speicher
--------------
69) Verringerung der Zugriffszeit auf häufig gebrauchte Daten

70) .. code-block:: formula
	
		Geg: tc 1.1ns, tm 10.5ns, h 88%
		Ges: mittlere Zugriffszeit teff
		Lös:
		teff = h*tc+(1-h)*tm = 0.88*1.1ns+0.12*10.5ns = 2.2ns
	
71) Der Cache enthält Ausschnitte des Hauptspeichers. Möchte der Prozessor auf Inhalte zugreifen, die nicht im Cache sind, so müssen diese zuerst in den Cache geladen werden (Wird automatisch von der Cache Logik erledigt). Die Cache Steuerlogik ist in Hardware implementiert.

72) Arbeiten mehrere Prozessoren mit dem Cache, so ist nicht klar, ob die Daten im Cache noch aktuell sind oder nicht. Eine Möglichkeit zur Umgehung des Problems ist die Löschung (Markieren als ungültig) aller Caches bei einem Schreibzugriff (sehr langsam) oder ein Write through (Schreibzugriffe gehen immer in Cache+HS) (auch langsam).

73)
	* Erst wenn der Prozessor auf eine nicht im Cache vorhandene Adresse zugreifen will, kann der Inhalt aus dem HS nachgeladen werden -> Langsam
	* Bei der Adressierung werden mehrere Byte zu einer Cache Zeile zusammengefasst werden. Müssen Inhalte in den Cache geladen werden, so muss immer die ganze Zeile geladen werden.
	* Der Cache bringt nur lesenden Zugriffen eine Beschleunigung
	* Peripherieadressräume dürfen NIE über den Cache angebungen werden, wegen den Hardwarestatuswerten
	* Der Cache beschleunigt nur den HS, nicht aber Register oder logische Operationen
	
74) Cache-Speicher Grösse, Cache-Zeilen Grösse und die Organisationsform des Caches beeinflussen dessen Einflussfaktor auf die Leistung. Damit der Cache die Leistung positiv beeinflussen kann, muss er eine hohe Trefferrate aufweisen.

75) Grund dafür ist der SSD-Cache, der Schreibvorgänge Cached und dem System damit eine hohe Schreibgeschwindigkeit vorgaukelt. Ist die zu schreibende Datei grösser als der Cache, so muss die Datei direkt auf die Platte geschrieben werden und damit kommt die Geschwindigkeit der SSD und nicht die Geschindigkeit des Caches zum tragen.

76)	Der gesammte Kopiervorgang läuft über den Prozessor. Die Daten werden von Speicher zu Speicher verschoben, bis sie den Prozessor erreicht haben und anschliessend wieder von Speicher zu Speicher verschoben (oder in die Caches und den HS durchgeschrieben (write through) bis sie auf der Platte angelangt sind.
	Der Cache nutzt in diesem Fall überhaupt nichts. Im Gegenteil, die Kopiererei verlangsamt den Vorgang sogar.

	Datenfluss::
	
		    +-- [L1] <-- [L2] <-- [L3] <-- [HS] <-- [HDD]
		    v
		[Prozessor]
		    |
		    +-- Write trough --> [HS] --> [HDD]
	
	
Heap
----
77) Der Heap ist ein Speicherbereich, indem Prozesse dynamisch Speicher allozieren können. Die Programme sind selbst dafür verantwortlich, dass der Speicher wieder freigegeben wird.
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


78) Der Stack legt die neusten Daten zu oberst auf den Stapel. Wird die aktuelle Funktion beendet, wird dieser Bereich vom Stack abgeräumt und de Daten sind weg. Auf dem Heap verbleiben die Daten bis sie gelöscht werden.
	Heap
		* Mit new angelegte Elemente
	Stack
		* Methodenaufrufparameter
		* Rücksrungadresse
		* Framepointer
		* lokale Variablen

79) Daten, deren Gültigkeit über die Laufzeit der Funktion hinausgehen, in der sie erzeugt werden, müssen zwingend auf dem Heap abgelegt werden, damit sie weiterhin verfügbar sind.

80)
	C
		* malloc(size)
		* free(pointer)
		* nicht freigegebener Speicher bleibt reserviert, bis der Prozess beendet wird
	C++
		* new type
		* delete pointer
		*nicht freigegebener Speicher bleibt reserviert, bis der Prozess beendet wird
	Java
		* new
		* durch Garbage Collection
		* Garbage Collection räumt nicht mehr referenzierte Objekt automatisch irgendwann ab
	Desktop / Server
		Server laufen unter umständen Jahre. Entsprechend laufen einige Serverprozesse auch Jahre. Würde ein Programm vergessen Speicher dreizugeben, wäre der Speicher irgendwann voll. Bei Desktops ist dies weniger ein Problem, da die Prozesse meist beendet werden, bevor der Speicher volllaufen kann.

81)
	* systeminterne Meldungen
	* systeminterne Tabellen und Objekte
	* Sprachübergreifende Speicherbereitstellung

82)
	variable Zuordnungsgrösse
		System
			Es können beliebige Bereich belegt werden
		Vorteile
			keine interne Fragmentierung
		Probleme
			Externe Fragmentierung
		Schema::

			    |--A--|--F--|     |----E----|---G---|  |-H-|


		Verwaltungsdaten (Freiliste beginnend bei 1000)::
		
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
		Schema::

			     |-A-  |---B---   |     |-C-  |          |----D---- |


		Verwaltungsdaten::

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
		Schema::

			|  |  |--|--|--|  |--|--|--|  |  |  |


		Verwaltungsdaten::

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
		Schema::
		
			|----|    |        |----------------|                                |

			
		Verwaltungsdaten::

			64er: [64| -]-->
			128er: [128| -]-->
			256: 
			512er: [512| -]-->
			
			
		Suchalgorithmen
			* Wenn sich in Freigabelist der benötigten Grösse kein freies Feld mehr befindet -> grössere Felder solange zweiteilen (Buddies), bis ein freies Feld vorliegt

83) Nur indirekt über die Allozierung und Freigabe von Elementen kann zusammenhängender Speicher freigegeben werden in der Hoffnung, das Betriebsystem kann die Bereiche rekombinieren.

84) Die Metadaten der Heap Verwaltung beinhalten sämmtliche Angaben über den Aufbau des Heaps, die Freigabelisten, etc. Sie werden entweder 
	direkt beim betreffenden Heap Bereich gespeichert
		* Vorteil: einfach zum freigeben beim Prozessende
		* Nachteil: über den HS verstreut
	in einem zentralen Bereich für Heap Metadaten
		* Vorteil: effiziente Adressierung für das BS
		* Nachteil: aufwändiger, Bereiche freizugeben
		
85) 
	interne Fragmentierung
		Es werden grössere Blöcke (nach Grössenklassen oder festen Grössen) als effektiv benötigt alloziert. Dadurch gibt es innerhalb des Blockes Verschnitt.
	externe Fragmentierung
		Im HS gibt es Bereiche, die zu klein sind um sie zu belegen oder eine Belegung füllt nicht die Gesammte Lücke und es gibt Rest.
		
86) Lückenelliminierung durch Verschieben belegter Bereiche (Defragmentierung)

87) Master Pointer zeigen auf die Startadresse des Heap. Die Applikation greift mittels MP zu. So kann die Heap Verwaltung den Heap umkopieren, ohne dass die Applpikation etwas davon merkt.

88) Es gibt keine garantierte Zugriffszeit bei den Suchalgorithen für freie Lücken. Daher ist diese Heapordnung nicht für Echtzeit Systeme geeignet.

89) 


Prozessadressräume
==================
90)
	.bss
		uninitialisierte Daten
	.data
		initialisierte Daten
	.text
		Programmcode
		
91) Die Sektionen werden in den Hauptspeicher vor den Heap Bereich kopiert.

92) Eine HS Sektion, die 1:1 Teile eines Files abbilden

93) Eine Region beschreibt einen belegten Bereich im Prozessadressraum (z.B. Startaddr. des belegten Bereichs, Grösse, Schutzattribute, zugehöriger Hintergrundspeicher).


