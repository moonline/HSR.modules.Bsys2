Bsys2 FS13 Repetitionsfragen Antworten
======================================

Repetitionsfragen: https://github.com/moonline/Bsys2/blob/master/RepetitionQuestions.Bsys2.tex

Sicherheit
----------
1)		
	- Softwarefehler / zu hohe Komplexität
	- Sicherheit ist zusätzlich Aufwand / mühsam
	- das BS berücksichtigt Sicherheit zu wenig

2)	
	- Information abfangen (interception)
	- Information modifizieren (modifikation)
	- Information unterbrechen (interruption)
	- Information einspeisen (fabrication)

3)	Eine Berechtigunggsprüfung

4)	
	- Personalisierung und Authorisierung
	- Identifizierung und Zugriffskontrolle

5)	Benutzerverwaltung, Anmeldesystem, Zugrifskontrolle

6)	Es gibt Domänen und Objekte (Files, Drucker, ...).
	Die Rechte sind mit Tupels (Domäne, Rechte) definiert.
	z.B. (D1, r1rw2rwx4) gibt der Domäne1 leserechte für Objekt1, lese- und schreibrechte für Objekt2 und lese-, schreib- und ausführungsrechte für Objekt4.
	Die Rechte können auch als Matrix dargestellt werden.
	Benutzer melden sich als Domäne an und besitzen somit deren Rechte.

7)	Tabelle, in welche die Objekte die Spalten und die Domänen die Zeilen bilden. Die Rechte sind in den Feldern eingetragen.

8)	Strategie definiert, was geschützt werden soll (Schutzobjekte),
	Mechanismus definiert, wie der Schutz umgesetzt werden soll (technikorientiert)

9)	Definieren, wie weit ein Benutzer die Schutzmatrix verändern darf
	und z.B. einem andern Benutzer Rechte auf ein Objekt zu geben.

10)	Kopierrecht: Recht zum Kopieren von Rechten. Varianten:
	Volles Kopierrecht, Rechtetransferrecht, Limitiertes Kopierrecht

11)	Objekte besitzen Owner, der darauf volle Rechte hat (Rechte einfügen, Rechte entfernen, Besitzrecht weitergeben).

12)	Recht zum Ändern aller Rechte einer Domäne.

13)	Ownerkonzept: Sämmtliche Felder in den Spalten seiner Objekte
	Kontrollkonzept: Sämmtliche Felder in den Zeilen seiner Domäne

14)	
	- Zugriffsliste als globale Tabelle mit Trippeln:
		- (-) verändern der Rechte bedingt durchgehen der Liste

	- Zugriffsliste pro File (ACL):
		- (+) Rechte schnell gefunden bei Zugriff
		- (-) Löschen der Rechte einesgelöschten Users schwierig

	- Zugriffsliste pro Domäne (Ticket Liste):
		- (+) Rechte einer Domäne sind zusammen abgelegt
		- (+) Löschen einer Domäne einfach
		- (-) Technisch anspruchsvoll umzusetzen

15)	
	- Benutzerbestimmt: Benutzer (owner) bestimmt, wer was mit seinen Objekten macht
	- Systembestimmt: System/Organisation bestimmt, wer was mit welchen Objekten macht

16) Der Benutzer soll zu jedem Zeitpunkt so wenig Zugriff wie möglich aber so viel wie nötig besitzen -> keine unnötigen Rechte.

17) Bell/Padula: Objekte sind Sicherheitsstufen zugeordnet. Benutzer darf Objekte gleicher und schwächerer Stufen lesen, aber nur Objekte gleicher oder höherer Stufe schreiben.

18) Prozess sollte nur dann Rechte für ein Objekt besitzen, wenn er es gerade braucht. Da jedoch nur das Programm selbst weis, wann dies zutrifft, hat der Prozess den Grossteil der Zeit Rechte, die er gar nicht benötigt.


Unix Sicherheit
---------------
19)	
	- Datei besitzt Rechte für Owner, Gruppe und Andere.
	- Root darf alles.
	- Für Owner, Gruppe und Andere können einzeln r-, w- und ausführungsrechte gesetzt werden.

20)	
	- Domänen: Owner, Group, Other
	- Objekte: Files, Prozesse
	
21) Benutzerbestimmt

22)	

23)	
	- Ausführen der Datei mit Rechten der Benutzers oder der Gruppe statt mit den Rechten der Datei.
	- Datei kann für jeden Benutzer mit dessen Rechten ausgeführt werden.

24) Rechtetemplate für neue Dateien

25) Benutzer kann einen einzelnen Befehl oder mehrere mit den Rechten eines andern Benutzers ausführen (minimal Priviledges).


Windows Sicherheit
------------------
26)	

27)


Unix Scripting
--------------
28) Die Shell selbst ist nur eine Anwendung, genauso wie alle andern auch. Die bekanntesten sind die Bourne Shell und die Bash.

29) Das Kapseln von mehreren Befehlen in ein Skript zur Administration des Systems und zur Automation von Aufgaben. Bsp: ein Backup-Skript überprüft Dateien auf das Änderungsdatum, packt geänderte in ein tar Archiv und legt kopiert das Archiv auf eine Backup Platte, wo sie wieder entpackt werden.

30)
	- Einrichten des Systems
	- Wartungsaufgaben
	- Aufgaben, für die UI notwendig ist (z.B. File konvertierung, Backup)

31) Das Auflösen und Einsetzen von Variablen und Ausdrücken in einer Befehlszeile vor dem eigentlichen Ausführen.

32) Sie teilt dem System mit, mit welcher Shell das Skript ausgeführt werden soll.


Ein-/Ausgabe
------------
33)
	- Über den Prozessor: Die Daten werden von der Eingabe eingelesen, durch den Prozessor verarbeitet und auf die Ausgabe geschrieben.
		- (-) Belastet den Prozessor unnötig stark.
	- Interrupt gesteuert: Der Prozessor wird durch Interrupts unterrbochen und steuert jeweils den Transfer. Die Daten laufen nicht über den Prozessor.
		- Prozessor wird weniger belastet als oben, aber mehr als bei DMA K.
	- DMA Kontroller: Der Prozessor initiert den Prozess, anschliessend läuft er über den DMA Kontroller. Der Prozessor wird erst wieder gestört, um die Fertigstellung mitzuteilen.
		- (+) Belastet den Prozessor praktisch nicht

34) siehe 33

35) Stellt die Kommunikation zwischen der Hardware und der I/O-Verwaltung sicher. Abstrahiert die Hardware und verhindert, das jede Software Hardwareunterstützung für jede Hardware mitbringen muss.

36) 
	- keine
	- einfach Buffer
	- doppelter (paralleler) Buffer
	- Zirkulärer Buffer


X Window System
---------------
