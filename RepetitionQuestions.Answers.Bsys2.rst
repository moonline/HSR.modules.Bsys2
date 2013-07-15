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