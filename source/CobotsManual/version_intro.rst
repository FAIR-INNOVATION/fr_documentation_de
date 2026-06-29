Version V3.9.7
-----------------

Datum: 2026-06-25

- **Optimiertes japanisches Sprachpaket für die Software**:

    Beschreibung: Optimierte Übersetzungsinhalte des japanischen Sprachpakets.

- **Optimierte Pfadparameter für LUA-Programme des Roboters**:

    Beschreibung: Bei der Dateieingabe ist jetzt nur noch der Name erforderlich; der Pfad wird nicht mehr benötigt.

- **Optimierte Pendelfunktion für neue Spline-Linien-Bogen-Übergänge**:
    Pfad: Hilfsanwendungen -> Prozesspaket -> Schweißexpertenbibliothek -> Neue Spline-Pendelschweißung.

    Beschreibung: Anpassung der Pendelfunktion an die neue Spline-Linien-Bogen-Übergangsfunktion.

- **Optimierte Schutzfunktion der weichen Gelenkbegrenzungen**:
    Pfad: Grundeinstellungen -> Basis -> Gelenke -> Weiche Begrenzungen.

    Beschreibung: Optimierung der Steifigkeits- und Dämpfungskoeffizienten für die weichen Begrenzungen jedes Gelenks.

- **Print-Funktion für LUA-Programme des Roboters hinzugefügt**:
    Pfad: Teach-Pendant-Programm -> Druckfunktion.

    Beschreibung: Echtzeitanzeige von benutzerdefinierten Druckinformationen aus LUA-Programmen.

- **Endeffektor-Lua-Adapter für eine dreifingrige Hand hinzugefügt**:
    Pfad: Grundeinstellungen -> Peripheriegeräte -> Sauger.

    Beschreibung: 1. Anpassung für Endeffektor-Sauger und dreifingrige Hand hinzugefügt; 2. Vorhandenes Endeffektor-Lua-Open-Protokoll optimiert.

- **Fehlermelde-Funktion bei Greiferabfall hinzugefügt**:
    Pfad: Grundeinstellungen -> Peripheriegeräte -> Greifer.

    Beschreibung: Fehlermeldung bei Werkstückabfall vom Greifer hinzugefügt; Bewegung wird nach der Meldung gestoppt.

- **Rückmeldefunktion für die 24V-Kurzschlussschutzauslösung am DO-Modul des Breitspannungs-Steuerschranks hinzugefügt**:

    Beschreibung: Kurzschlussschutz und Fehlerhinweis hinzugefügt.

Version V3.9.6
-----------------

Datum: 2026-05-26

- **Optimierte Matrixbewegungsfunktion**: 
    Pfad: Hilfsanwendungen -> Prozesspaket -> Matrixbewegung.
  
    Beschreibung: Optimierte die Funktion des Matrixbewegungs-Befehlssatzes.

- **Optimierte DI-Verzögerungsfunktion**: 
    Pfad: Anfangseinstellungen -> Basis -> I/O-Einstellungen.
  
    Beschreibung: 1. Bei Auslösung des DI-Signals ist der Geschwindigkeitsregelungsprozess sanft ohne Ruckeln oder Stocken; 2. Der Roboter-Endpfad ändert sich vor und nach der Geschwindigkeitsregelung nicht; 3. Kein Fehler oder Stillstand bei DI-ausgelöster Geschwindigkeitsregelung; 4. Sofortige Ausführung ohne Fehler bei DI-ausgelöstem Stopp.

- **Hinzugefügte Kommunikationsanpassungsfunktion für Roboter-Laserschweißgerät**: 
    Pfad: Anfangseinstellungen -> Peripheriegeräte -> Schweißgerät.
  
    Beschreibung: 1. WebAPP fügt laserschweißgerätebezogene Einstellungen, Debugging und Lua-Programmgenerierungsbefehle hinzu; 2. Laserschweißgerätebezogene Parameter hinzugefügt; 3. SPS entwickelt Anpassungsprogramme.
    
- **Hinzugefügte FRJ-PCIeN-EIP/CC/PN-RJ-V10-Karten-EIP/CClink-IE-Protokollanpassung**: 
    Pfad: Anfangseinstellungen -> Peripheriegeräte -> Kartenkommunikation.
  
    Beschreibung: 1. Unterstützt konfigurierbaren Kommunikationszyklus; 2. Unterstützt Abruf des Busverbindungsstatus; 3. Kompatibel mit EIP- und CC-Protokollen.

Version V3.9.5
-----------------

Datum: 2026-04-24

- **Optimierte Controller-Funktionen**: 
    Pfad: Allgemeine Einstellungen -> Netzwerkeinstellungen; Teach-Programm -> Programmierung.
  
    Beschreibung: 1. Validierungsfehler hinzugefügt, wenn ETH0 und ETH1 mit derselben IP-Adresse konfiguriert werden; 2. Farbanzeige der aktuell ausgeführten Programmzeile optimiert.

- **Optimierte FR30-Geschwindigkeit**: 
  
    Beschreibung: Betriebsgeschwindigkeit verbessert.

- **Optimierte Bogenschwenkfunktion**: 
    Pfad: Teach-Programm -> Programmierung -> Bogenbefehl.
  
    Beschreibung: Ermöglicht Schwenkbewegungen.

- **Optimierte SetTrajectoryJSpeed-Debugging für flüssigen Betrieb**: 
  
    Beschreibung: Während der Befehl-Geschwindigkeitsanpassung fällt die Robotergeschwindigkeit beim Geschwindigkeitswechsel nicht auf Null.

- **Optimierte Bearbeitungsmodus-Operation von Lua-Programmbefehlen im Programmiermodul**: 
    Pfad: Teach-Programm -> Programmierung.
  
    Beschreibung: Optimiert, so dass Befehlsinhalte präzise abgeglichen und angezeigt werden können.

- **Hinzugefügte FRJ-PCIeN-EC-RJ-V20 Board-Protokolladaption (PN/Ecat/EIP/cclink)**: 
    Pfad: Grundeinstellungen -> Peripheriegeräte -> Board-Kommunikation.
  
    Beschreibung: 1. Unterstützt Online-Firmware-Upgrade/-Abruf; 2. Unterstützt konfigurierbaren Kommunikationszyklus; 3. Unterstützt Abruf des Busverbindungsstatus.

- **Hinzugefügte Controller-Befehle**: 
    Pfad: Teach-Programm -> Programmierung; Grundeinstellungen -> Sicherheit -> Sicherheitsstopp.
  
    Beschreibung: 1. Option für Werkstückkoordinatensystem-Offset zu Bewegungsbefehlen hinzugefügt; 2. Sicherheitsstopp-Funktion hinzugefügt; 3. DO- und AO-Lesebefehle für Steuerkasten, Endeffektor und erweiterte E/A hinzugefügt.

- **Hinzugefügte DO-Signalkonfigurationsfunktion nach Not-Halt des Steuerkastens**: 
    Pfad: Grundeinstellungen -> Basis -> DO.
  
    Beschreibung: DO-Signalkonfigurationsfunktion nach Not-Halt des Steuerkastens hinzugefügt.

- **Hinzugefügte Anpassung des portugiesischen Sprachpakets für die Softwareversion**: 
  
    Beschreibung: Portugiesische Sprachumschaltung hinzugefügt.

Version V3.9.4
-----------------

Datum: 2026-04-08

- **Optimierte TPD-Funktion für das Einlernen und Abspielen von Roboterbahnen**: 
    Pfad: Teach-Programm -> Programmierung -> TPD-Befehl.
  
    Beschreibung: 1. Automatische Generierung von Lua-Befehlen für den Startpunkt 2. Fehlersichere Ausführung des Startknopfs.

- **Optimierte Webapp-Datensicherungsfunktion**: 
  
    Beschreibung: Die Datensicherungsfunktion wurde verbessert und optimiert.

- **Optimierte FR3WML-Weichgrenzen und Verpackungspose**: 
  
    Beschreibung: Weichgrenzbereich für Gelenk 3 auf ±163° eingestellt.

- **Optimierte DH-Vollparameterkompensationsfunktion und schnelle Verifizierung**: 
  
    Beschreibung: Kompensation des Vollparametermodells.
 
- **Hinzugefügte PTP-Bewegungs-Impedanzregelungsfunktion**: 
  
    Beschreibung: Verbesserte Sicherheit während der Mensch-Roboter-Interaktion.

- **Hinzugefügte Kommunikationsprotokollfunktion für Moxibustion-Kopf-Endeffektors**: 
    Pfad: Grundeinstellungen -> Peripheriegeräte -> Endeffektor-Transparentübertragung.
  
    Beschreibung: Neue Anpassung des Kommunikationsprotokolls für Endeffektors.

- **Hinzugefügte Anpassung des deutschen Sprachpakets für die Softwareversion**: 
  
    Beschreibung: Deutsche Sprachumschaltung hinzugefügt.

- **Hinzugefügte Funktion, dass Sicherheitsgeschwindigkeitseinstellungen auf Servo-Bewegungsbefehle wirken**: 
    Pfad: Grundeinstellungen -> Sicherheit -> Sicherheitsgeschwindigkeit.
  
    Beschreibung: Sicherheitsstrategieoption hinzugefügt: Stopp mit Fehlermeldung und Deaktivierung nach Überschreitung.

- **Hinzugefügte LA-Anpassung für TP-LINK AX3000 WLAN-Router**: 
  
    Beschreibung: Behebung des Problems, dass nach einem Stromausfall und Neustart kein direkter drahtloser Zugriff auf das webApp möglich war.
    
- **Hinzugefügte Funktion für stationäres Pendeln**: 
    Pfad: Teach-Programm -> Programmierung -> Weave-Befehl.
  
    Beschreibung: Durchführung der Funktion für stationäres Pendeln in Verbindung mit einem externen Lasersensor.

Version V3.9.3
-----------------

Datum: 2026-02-11

- **Optimierung der Geschwindigkeitseinstellung für SmartTool-Bewegungsbefehle**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgriff.

    Beschreibung: Der Einstellbereich für die Geschwindigkeit von PTP-, LIN- und ARC-Befehlen wurde auf 0-100 % angepasst (bisheriges Geschwindigkeitslimit war 30 %).

- **Optimierung der externen Krafterkennung ohne Kraftsensor und Verbesserung des Führungserlebnisses**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre.

    Beschreibung: Die Genauigkeit der externen Krafterkennung wurde auf ±0,5 N verbessert.

- **Optimierung des Wiederverbindungsmechanismus für Modbus TCP-Master**:
    Pfad: Teachprogramm -> Programmierung -> Modbus TCP.

    Beschreibung: Eine Pausenlogik wurde hinzugefügt.

- **Hinzufügen von Debug-Befehlsfunktionen für externe Achsen**:
    Pfad: Grundeinstellungen -> Peripherie -> Externe Achsen.

    Beschreibung: Implementierung der inversen Kinematik des Roboters im Koordinatensystem externer Achsen sowie ServoCart-Servobewegungen mit externen Achsen.

- **Hinzufügen einer konfigurierbaren Funktion für den DO-Reset-Status bei Pausenfortsetzung**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgriff.

    Beschreibung: Es kann optional eingestellt werden, ob der DO-Ausgabestatus nach Bewegungsfortsetzung mit dem Status vor der Pause übereinstimmt.

Version V3.9.2
-----------------

Datum: 2026-01-26

- **Optimierung des Führungsteachens mit Positionsregelung basierend auf Gelenkmomentensensoren**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre.

    Beschreibung: Behebung des Problems unzureichender Punktgenauigkeit innerhalb von 2s bei Führung zwischen Gelenken.

- **Optimierung der Erweiterungskarte**:

    Beschreibung: Optimierung des Synchronisationsmechanismus für erweiterte DO-Daten.

- **Optimierung der Lichtbogenverfolgungsfunktion**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgerät.

    Beschreibung: Hinzufügen der Echtzeiterfassung des Schweißstroms über das offene Peripherieprotokoll ModbusTCP.

- **Optimierung der IP-Reset-Funktion für Controller und physisches Teachpendant**:
    Pfad: Systemeinstellungen -> Netzwerk.

    Beschreibung: ① In webrecovery wurde eine neue Funktion zum Zurücksetzen der Controller-IP hinzugefügt, die eine zweite Bestätigung erfordert. ② Dem physischen Teachpendant wurde eine IP-Reset-Funktion hinzugefügt. ③ Das physische Teachpendant kann im nicht verbundenen Zustand über eine physische Taste zurückgesetzt werden. Die IP-Adresse des Teachpendants lautet dann 192.168.58.77.

- **Neue Roboter-Konfiguration FR3C hinzugefügt**:

    Beschreibung: Der Gelenkbewegungsbereich ist identisch mit der FR3-Serie. Ober- und Unterarm sind identisch mit WMS. Die Nennlast beträgt 3 kg.

- **Neue Quader-Interferenzfunktion hinzugefügt**:
    Pfad: Grundeinstellungen -> Sicherheit -> Interferenzbereiche -> Quader-Interferenz.

    Beschreibung: Ermöglicht die gleichzeitige Interferenzprüfung von mindestens 4 Quadern und konfigurierbare CO-Ausgabe entsprechender Interferenzsignale.

- **Neue Funktionserweiterung des slave_interpret-Moduls (PROFINET-Protokoll) und Web-Volllast-I/O-Anzeigefunktion**:
    Pfad: Grundeinstellungen -> Peripherie -> Kartenkommunikation -> Karten-Upgrade.

    Beschreibung: Hinzufügen von EtherCAT-Firmware-Updates für Jiyuan-Karten, PLC-Kommunikationsprüfung, konfigurierbarer Zyklus und Web-Volllast-I/O-Anzeige (PROFINET-Protokoll).

- **Neue SmartTool-Open-Protokoll-Funktion hinzugefügt**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgriff.

    Beschreibung: ① Hinzufügen der SmartTool-Programmerstellung und -Analyse basierend auf offenen Protokollen sowie der Verarbeitung von Erkennungssignalen. Hinzufügen einer "Rückgängig/Löschen"-Tastenfunktion zur Fehlervermeidung. ② Die Tastenkonfiguration für das SmartTool-Open-Protokoll wurde um eine automatische Generierungsfunktion erweitert.

- **Neue gegenseitige Kompatibilität der Sicherungsdateien von QX- und LA-Softwareversionen**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Datensicherung.

    Beschreibung: ① QX unterstützt den vollständigen Import von LA-Sicherungsdateien, und LA unterstützt den vollständigen Import von QX-Sicherungsdateien. ② Kompatibel mit Sicherungsdateien ab Version v3.8.7.

- **Neue konfigurierbare Parameter für Endeffektor-CI und Controller-CI**:
    Pfad: Grundeinstellungen -> Basis -> I/O-Einstellungen -> DI.

    Beschreibung: Ermöglicht die Konfiguration von Bewegungsunterbrechungen durch den Endeffektor-CI und die teilweise Synchronisation des Endeffektor-CI mit dem Controller-CI.

- **Neue Servo-Tracking-Funktion für Roboter-Laserdaten**:
    Pfad: Grundeinstellungen -> Peripherie -> Linienlasersensor.

    Beschreibung: Ermöglicht dem Roboter die direkte Verfolgung basierend auf Lasersensordaten.

- **Neue Konfigurationsfunktionen für das Teachpendant**:

    Beschreibung: ① Die Tasten F1-F4 am Teachpendant unterstützen die Konfiguration benutzerdefinierter Funktionen über die WEB-Oberfläche. ② Der Schlüsselschalter im benutzerdefinierten Modus kann als Führungsmodus konfiguriert werden.

Version V3.9.1
-----------------

Datum: 2025-12-30

- **Funktion zur Aufzeichnung von Fehlern und Alarmereignissen im Roboterhintergrund**:

    Beschreibung: Fehler- und Alarminformationen können während der Abmeldung von der Benutzeroberfläche aufgezeichnet und nach erneuter Anmeldung eingesehen werden.

- **Hinzufügen relativer Bewegungsfunktionen basierend auf der aktuellen Position zu PTP- und LIN-Befehlen, Hinzufügen von ServoJ-Befehlen in der WebApp**:
    Pfad: Teachprogramm -> Programmierung -> PTP/LIN-Befehle.

    Beschreibung: Behebt das Problem komplexer Befehlsoperationen, wenn der Roboterarm keinen Teachpunkt hat, aber eine Verschiebung basierend auf der aktuellen Position benötigt wird. Dies kann nun mit einem einzigen Befehl realisiert werden.

- **Debug-Schalter und Syntaxprüfungsfunktion für das offene Lua-Protokoll am Endeffektor**:
    Pfad: Grundeinstellungen -> Peripherie -> Greifer, Kraftsensor, Schweißgriff.

    Beschreibung: Die aktuelle Controller-Integration ist an Endeffektor-Protokolle angepasst (Greifer, Kraftsensor, Schweißgriff). Diese Optimierung ermöglicht die direkte Auswahl und Anwendung auf den Endeffektor in der WebApp. Der webServer verfügt über eine neue Syntaxprüfung für Lua-Protokolle; bei Fehlschlag wird direkt ein Fehler gemeldet. Die WebApp hat einen neuen Debug-Schalter für offene Lua-Protokolle; im Debug-Modus wird bei der Ausführung von Endeffektor-Lua die Zeitüberschreitungsmeldung des Sensor-Kommunikationsfehlers unterdrückt.

- **Optimierung der FRCap-Palettierszenenfunktion**:
    Pfad: Zusatzanwendungen -> Prozesspakete -> Palettieren.

    Beschreibung: Palettieren unterstützt zwei Entnahmepunkte – nach der Anlieferung von zwei Fließbändern greift der Roboter sequenziell Material von den Entnahmepunkten der beiden Bänder und legt es auf zwei entsprechende Paletten.

- **Optimierung der Funktionen des physischen Teachpendants**:
    Pfad: Systemeinstellungen -> Allgemeine Einstellungen -> Netzwerk.

    Beschreibung: Bisher mussten Kunden beim Verwenden des Teachpendants zuerst in die WebApp wechseln, um dann in ihre eigene HMI-Oberfläche zu gelangen, was umständlich war. Nach der Optimierung kann der Roboter durch Drehen des physischen Schlüsselschalters zwischen Hand- und Automatikmodus wechseln, ohne sich an der Teach-Oberfläche anmelden zu müssen.

- **Optimierung der Kollisionsfunktion**:
    Pfad: Grundeinstellungen -> Basis -> Gelenke -> Kollisionsstufe -> Fehlalarmerkennung.

    Beschreibung: Auch bei Kollisionsstufe 1 kann mit beliebiger Geschwindigkeit gefahren werden, ohne dass aufgrund hoher Geschwindigkeit Fehlalarme ausgelöst werden. Bei einer tatsächlichen Kollision oder Quetschung wird ein Fehler gemeldet und angehalten.

- **Photoelektrische Sensor-TCP-Kalibrierungsfunktion**:
    Pfad: Grundeinstellungen -> Basis -> Werkzeugkoordinaten -> Photoelektrische automatische Kalibrierung.

    Beschreibung: Unterstützt die automatische Kalibrierung von geraden und gebogenen Schweißbrennern.

Version V3.9.0
-----------------

Datum: 2025-11-27

- **Anwendung des Daru DFC kraftgeregelten Schleifkopfs**:
    Pfad: Grundeinstellungen -> Peripherie -> Schleifen -> Daru DFC kraftgeregelter Schleifkopf.

    Beschreibung: Softwareanpassung und Tests für das DFC intelligente, flexible, kraftgeregelte Schleifperipheriegerät. Erfüllt die Anpassungsanforderungen des DFC-Schleifsystems.

- **Parameterkalibrierung von Gelenkmomentsensoren am Gesamtroboter**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre -> Gelenkmomentsensor-Gesamtroboterführung.

    Beschreibung: Durchlaufen einer vorgegebenen Trajektorie zur Kalibrierung der Parameter Empfindlichkeit, Linearität, Hysteresefehler und Wiederholgenauigkeit der Gelenkmomentsensoren.

- **Neue Funktion zur Vermeidung von Überschwingern bei der führungsbasierten Teacheinweisung mit Gelenkmomentsensoren**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre -> Gelenkmomentsensor-Gesamtroboterführung.

    Beschreibung: Mildert das Überschwingen bei der Führung im Stromregelkreis ab. Nach Aktivierung dieser Funktion kann die Führungspunktoperation bequemer durchgeführt werden.

- **Funktion zum Schweißen von Rohrverschneidungen**:
    Pfad: Teachprogramm -> Programmierung -> Rohrverschneidungsbefehl.

    Beschreibung: Durch Aufzeichnen von 6 Teachpunkten auf den Querschnitten des Hauptrohrs und des angeschweißten Rohrs sowie Eingabe von Parametern wie Bewegungsrichtung, Geschwindigkeit, Beschleunigung und Offset kann der Roboter die durch die Überschneidung der beiden Rohre entstehende Verschneidungskurve generieren und schweißen.

- **Hinzufügen einer Gleich-Funktion zu den Modbus-Warteeinstellungen für analoge Eingänge**:
    Pfad: Teachprogramm -> Programmierung -> Modbus-Befehl.

    Beschreibung: Dem Wartestatus für das Warten auf analoge Eingänge vom Slave wurde eine Gleich-Funktion hinzugefügt.

- **Teachpunkt-Update mit einem Klick & Lin-Einzelpunktausführung**:
    Pfad: Teachprogramm -> Teachpunkte -> Teachpunktverwaltung.

    Beschreibung: Auf der Teachpunkt-Oberfläche kann die aktuelle Roboterpose über die Roboter-Bedienleiste auf den entsprechenden Punkt aktualisiert werden, mit der Option, das Teachprogramm zu synchronisieren. Eine neue Lin-Einzelpunktausführungsmethode wurde hinzugefügt.

- **Optimierung der Punktaufzeichnungsfunktion im Punktabellenmodus**:
    Pfad: Teachprogramm -> Teachpunkte -> Teachpunktverwaltung.

    Beschreibung: Im Punktabellenmodus kann eine erneute Punktaufzeichnung das Lua-Programm synchron aktualisieren. Optimierte Lösung für gelegentliche Überschreitungen im PTP-Reduktionsmodus und Bewegungsstopps nach Erreichen der Position im LIN-Geschwindigkeitsregelungsmodus.

- **Benutzerkonfigurationsdatei (user config)**:
    Beschreibung: Optimierung des Problems fehlgeschlagener Ladevorgänge der Benutzerkonfigurationsdatei. Hinzufügen einer Funktion zum automatischen Neustart der Backup-Konfigurationsdatei und zum Zurücksetzen auf die Backup-Konfigurationsdatei.

- **Web-Oberflächenversion**:
    Beschreibung: Die Version der Weboberfläche wurde auf 2.0 aktualisiert. Die Software-Benutzeroberfläche wurde überarbeitet und optimiert.

- **Neue Robotermodelle V6.5 hinzugefügt**:
    Beschreibung: Durch Optimierungen an Hardware (Getriebe) und Algorithmen wird die Vibration des Roboters reduziert und die Bahngenauigkeit verbessert. Neue Modelle: FR3, FR5, FR10, FR16, FR20.

- **Neue Robotermodellkonfiguration FR5C hinzugefügt**:
    Beschreibung: Der LA-Softwareversion wurde die Konfigurationsmöglichkeit für das Robotermodell FR5C hinzugefügt.

Version V3.8.7
-----------------

Datum: 2025-10-21

- **Kollisionserkennungsfunktion für Roboter auf Linearzahnstangenführungen**:
    Pfad: Grundeinstellungen -> Basis -> Gelenke -> Kollisionsstufe -> Kollisionserkennung für Roboter auf Linearzahnstangenführungen.

    Beschreibung: Ermöglicht einen Notstopp der Führung bei einer Kollision während der Bewegung, was die Betriebssicherheit erhöht.

- **Neue Funktion zur Einstellung der tatsächlichen physikalischen Geschwindigkeit für neue Spiralbewegungen**:
    Pfad: Teachprogramm -> Programmierung -> Neuer Spiralbefehl N-Spiral.

    Beschreibung: Sorgt dafür, dass die konstante Lineargeschwindigkeit des Roboter-Endeffektors mit dem eingestellten Wert übereinstimmt.

- **Optionale automatische Aktivierung nach Sicherheitsstopp-Wiederherstellung**:
    Pfad: Grundeinstellungen -> Sicherheit -> Not-Halt.

    Beschreibung: Neue Konfigurationsmöglichkeit für die Aktivierungsstrategie nach Not-Halt-Reset in Kategorie 1b.

- **Lastkalibrierung für Kraftsensoren und Freigabe der Nachgiebigkeitsparameter für die Positionsanpassung**:
    Pfad: Grundeinstellungen -> Basis -> Last, Teachprogramm -> Programmierung -> F/T Control-Befehl.

    Beschreibung: Neue Freigabe der Nachgiebigkeitsparameter für die Positionsanpassung.

- **Laser-Tracking-Funktion für Kreisbögen und Vollkreise**:

    Beschreibung: Ermöglicht die Echtzeit-Laser-Tracking-Funktion für Kreisbögen und Vollkreise. Die Pose ändert sich während der Bewegung mit. Ermöglicht die Laserscan-Reproduktionsfunktion für Kreisbögen und Vollkreise.

- **Tasterfeld-Funktion**:

    Beschreibung: Optimierung der IP-Reset-Funktion für die Tasterfeld-Version 1.0.

Version V3.8.6
-----------------

Datum: 2025-09-19

- **Neue Impedanzregelungsfunktion für Roboter**:
    Pfad: Teachprogramm -> Programmierung -> F/T-Befehl.

    Beschreibung: Durch Echtzeiterfassung externer Kräfte wird bei Erreichen eines Schwellwerts aktiv der externen Kraft nachgegeben und von der Bewegungsbahn abgewichen. Sinkt die Kraft unter den Schwellwert, wird zur Bewegungsbahn zurückgekehrt. Dies verbessert die Mensch-Roboter-Interaktion.

- **Neue Drehmomenterkennungsfunktion vor dem Führungsmodus**:
    Pfad: Grundeinstellungen -> Basis -> Kollisionsstufe.

    Beschreibung: Vor dem Eintritt in den Führungsmodus wird die Differenz zwischen Soll- und Ist-Drehmoment für jedes Gelenk berechnet. Bei falsch konfigurierter Last oder Montageart kann die Differenz den Schwellwert überschreiten, was den Eintritt in den Führungsmodus verhindert und so Kontrollverlust vermeidet.

- **Neue benutzerdefinierte Pendelschweißfunktion**:
    Pfad: Teachprogramm -> Programmierung -> Weave-Befehl.

    Beschreibung: Benutzer können ihr eigenes Pendelschweißmuster entwerfen und ausführen.

- **ModbusTCP**:
    Pfad: Teachprogramm -> Programmierung -> ModbusTCP.

    Beschreibung: Optimierung der Timeout-Erkennungsfunktion für ModbusTCP-Master.

- **Pneumatischer Sauggreifer**:
    Pfad: Grundeinstellungen -> Peripherie -> Array-Sauggreifer.

    Beschreibung: Optimierung der Webseiten-Anpassungsfunktion für pneumatische Sauggreifer.

- **Fehlermeldung bei fehlgeschlagener Schweißdrahtsuche**:

    Beschreibung: Optimierung der Fehlermeldung in der WebApp bei fehlgeschlagener Schweißdrahtsuche; Fehler kann zurückgesetzt werden.

- **Konfigurierbare I/O-Funktionen**:

    Beschreibung: Neue konfigurierbare I/O-Funktionen für FR3C-FR3MT. Eingänge können als CI0-CI4 konfiguriert werden, Ausgänge als CO0-CO4.

Version V3.8.5
-----------------

Datum: 2025-08-19

- **Socket-Netzwerkdebugging**:
    Pfad: Teachprogramm -> Programmierung -> Socket-Netzwerkdebugging.

    Beschreibung: Socket-Verbindungen können neu angelegt, konfiguriert und gelöscht werden. Es werden maximal 4 Socket-Verbindungen unterstützt. Über das Befehlsmodul können Teachprogramme zum Öffnen/Schließen von Verbindungen sowie zum Senden/Empfangen von Daten generiert werden.

- **Funktion zur Umwandlung von CAD-generiertem G-Code in Roboterbahnen**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> G-Code-Konvertierung.

    Beschreibung: In Software mit CAM-Funktionalität (wie Solidworks, FUSION360) werden Bearbeitungsbahnen (Linien, Bögen, Kreise, Splines) als G-Code-Datei generiert. Diese G-Code-Datei kann dann in das Web-End importiert werden.

- **Hinzufügen der tatsächlichen physikalischen Geschwindigkeit zu Linien-, Bogen- und Kreisbewegungsbefehlen**:
    Pfad: Teachprogramm -> Programmierung, Grundeinstellungen -> Peripherie -> Schweißgriff.

    Beschreibung: Die tatsächliche physikalische Ausführungsgeschwindigkeit des aktuellen Bewegungsbefehls kann direkt definiert werden.

- **Optimierung der PTP-Geschwindigkeitsregelungsfunktion**:

    Beschreibung: Sorgt für einen flüssigen Geschwindigkeitsregelungsprozess und reduziert Geschwindigkeitsschwankungen an den Übergängen.

- **Roboter-Modellkonfiguration**:

    Beschreibung: Neue Konfigurationsoption für das Robotermodell FR30L hinzugefügt.

- **Steuerungsgehäuse-Anpassung**:

    Beschreibung: Neue Anpassung des Steuerungsgehäuses für die ETMP03E-Karte (EtherCAT-Protokoll).

Version V3.8.4.1
-----------------

Datum: 2025-07-30

- **Anpassung des Steuerungsgehäuses an Ethernet-Transparentmodul und Steuerung von Sauggreifern**:
    Pfad: Grundeinstellungen -> Peripherie -> Array-Sauggreifer.

    Beschreibung: Ermöglicht die Steuerung von Array-Sauggreifern (max. 20) über ein Ethernet-zu-485-Transparentmodul basierend auf der Webseite und offenen Peripherieprotokollen.

- **Vorausschauende Roboter-Bahnplanung (gleichförmige Vorausschau)**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Ein Ein-/Ausschalter für gleichförmige Bewegung wurde hinzugefügt. Wenn aktiviert, führt der Roboter die Vorausschaubewegung mit gleichförmiger Geschwindigkeit aus.

- **Optimierungsfunktion für den Slave-Modus des Steuerungsgehäuses**:
    Pfad: Grundeinstellungen -> Peripherie -> Kartenkommunikation, Fernmodus.

    Beschreibung: Neue Anpassung des Steuerungsgehäuses an die Jiyuan ETMP03E-Karte (EtherCAT-Protokoll).

- **Funktion zum Abrufen der Position von Laser-Suchpunkten**:
    Pfad: Grundeinstellungen -> Peripherie -> Linienlasersensor.

    Beschreibung: Nach erfolgreicher Lasernahtsuche können die Positionsdaten, die in "seamPos" gespeichert sind, über SDK- oder TCP-Protokollbefehle abgerufen werden.

- **Geschwindigkeitsfreigabefunktion für FR5 und FR10**:

    Beschreibung: Die Lineargeschwindigkeit des FR5 wurde von 1,0 m/s auf 1,7 m/s erhöht; die des FR10 von 1,5 m/s auf 2,0 m/s.

- **Roboter-Modellkonfiguration**:

    Beschreibung: Neue Konfigurationsoption für das Robotermodell FR5-WML (lange Reichweite) hinzugefügt.

- **Optimierung des Software-Upgrades**:

    Beschreibung: Verkürzung der Upgrade-Zeit. Kompatibilität für Downgrade von höheren auf beliebige niedrigere Versionen (3.7.6-3.8.4) wurde verbessert.

- **Optimierung der Wiederherstellung der Werkseinstellungen**:

    Beschreibung: Bei der Wiederherstellung der Werkseinstellungen werden nun Robotermodell, Steifigkeit, Dynamikeinstellungen, Tasterfeldversion usw. beibehalten.

Version V3.8.4
-----------------

Datum: 2025-07-18

- **Implementierung der Blending-Glättungsfunktion für externe Achsen**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Ermöglicht sanfte Übergänge zwischen Bewegungen externer Achsen und verbessert die Arbeitseffizienz.

- **Optimierungsfunktion für den Slave-Modus des Steuerungsgehäuses**:
    Pfad: Grundeinstellungen -> Peripherie -> Kartenkommunikation, Fernmodus.

    Beschreibung: Hinzufügen der Karten-IP-Konfiguration und des Versendens von LUA-Befehlen über die Oberfläche. Hinzufügen einer automatischen Startfunktion für das Slave-Protokoll des Controllers im Fernmodus.

- **QX-Anpassung der N2L-Karte für Steuerungsgehäuse (EtherCAT)**:
    Beschreibung: FA-IR Industrial-Echtzeitbus-Kommunikationskarte, miniPCIe-Karte, unterstützt EtherCAT-Protokollkommunikation.

- **Roboter-JOG-Bewegung**:
    Beschreibung: Hinzufügen einer CO-Statusausgabefunktion für die Roboter-JOG-Bewegung.

Version V3.8.3
-----------------

Datum: 2025-06-27

- **Slave-Modus-Funktion für Steuerungsgehäuse**:
    Pfad: Grundeinstellungen -> Peripherie -> Kartenkommunikation.

    Beschreibung: Auf der Roboter-Peripherieoberfläche wurde ein neues Konfigurationsmodul für die Kartenkommunikation hinzugefügt. Basierend auf nationalen Erweiterungskarten können die Protokolle EIP, CClink, PN für die Interaktion mit dem Roboterslave realisiert werden.

- **Hinzufügen einer Kollisionserkennungsfunktion für kraftsensorgestütztes Führen im Handmodus**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre -> Kraftsensor-gestützte Sperre.

    Beschreibung: Wenn die kraftsensorgestützte Führungsfunktion aktiviert ist, wird die Kollisionserkennung auch im Handmodus des Roboters ausgelöst, um Schäden an der Endeffektorausrüstung zu vermeiden.

- **Hinzufügen einer T-förmigen Geschwindigkeitscharakteristik-Bahnplanung + Blending-Glättungsfunktion**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Ermöglicht sanfte Übergänge zwischen verschiedenen Bewegungsbefehlen und verbessert die Arbeitseffizienz.

- **Optimierung der Statusabfrage-Oberfläche in der WebApp**:
    Pfad: Statusinformationen -> Statusabfrage.

    Beschreibung: Optimierung der Statusabfrage: Anzahl der Parameter auf 6 erhöht, maximale Wellenformzeit 30s, Hinzufügen einer Datenansicht mit Kopierfunktion für Daten, Hinzufügen der Umbenennung von Diagrammtiteln.

- **Optimierung der Führungskraft für die gesamte FR-Roboterserie**:
    Pfad: Grundeinstellungen -> Basis -> Gelenke -> Reibungskompensation -> Führungskraftkompensation.

    Beschreibung: Durch Bereitstellung eines Kompensationsdrehmoments während des Führungsvorgangs wird die Führung kraftsparender gestaltet.

- **Optimierung der Speicherfunktion für Websystemprotokolle**:
    Beschreibung: Behebung von Problemen mit Systemprotokolldateien. Standardmäßige Aufbewahrungsdauer für Protokolle auf 7 Tage eingestellt.

Version V3.8.2
-----------------

Datum: 2025-05-29

- **Anpassung des offenen Lua-Endeffektorprotokolls an die Schweißgriff-Funktion**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgriff.

    Beschreibung: Das offene Protokoll kann verwendet werden, um den SmartTool-Schweißgriff anzupassen. Alle Parameter sind konfigurierbar.

- **Hinzufügen eines offenen Schweißgerätprotokolls zu den offenen Peripherieprotokollen des Controllers**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgerät.

    Beschreibung: Kommunikation mit dem Schweißgerät über das offene Peripherieprotokoll des Controllers (ModbusTCP) zur Schweißgerätesteuerung.

- **Hinzufügen einer Pausenfunktion für LUA-Programme**:
    Pfad: Teachprogramm -> Programmierung.

    Beschreibung: Während der Ausführung eines Teachprogramms kann in jeder beliebigen Zeile eine Pause eingefügt werden, einschließlich Wartebefehlen und Kommunikationsbefehlen. Die Pause verbraucht keine Timeout-Zeit.

- **Hinzufügen einer T-förmigen Geschwindigkeitsanpassung + Blending-Funktion**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Nach Aktivieren des Schalters für T-förmige Geschwindigkeitsanpassung wird die Geschwindigkeitskurve geglättet. Derzeit werden Blending-Typen unterstützt (PTP-PTP, LIN-LIN, ARC-ARC, LIN-ARC, ARC-LIN).

- **FIR-adaptive Parameterfunktion + FIR-Pausen-Wiederherstellungsfunktion**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung, Grundeinstellungen -> Sicherheit -> Bewegungskonfiguration.

    Beschreibung: Der FIR-Funktion wurde ein globaler Schalter für FIR- und adaptive Parameter hinzugefügt. Nach Aktivierung werden normale PTP/LIN/ARC-Befehle automatisch in FIR-Planung umgewandelt (nicht mit Blend-Radius kombinierbar).

- **Optimierung der Modbus RTU-Funktion**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung, Teachprogramm -> Programmierung -> Modbus RTU-Einstellung.

    Beschreibung: Konfiguration von ModbusRTU-Master, Baudrate, Parität, Stationsnummer usw. in der WebApp möglich. Echtzeitwerte der ModbusRTU-Register können überwacht werden.

- **Schutzfunktion durch weiche Gelenk-Endanschläge**:
    Pfad: Grundeinstellungen -> Gelenke -> Weiche Endanschläge.

    Beschreibung: Im Führungsmodus ist ein Dämpfungsmoment spürbar, wenn sich ein Gelenk den in der Oberfläche eingestellten weichen Endanschlägen nähert. Nach Aufheben des externen Drehmoments kann das Gelenk in den Bereich der weichen Endanschläge zurückkehren.

- **Funktion des Roboter-Seitneigungswinkels beim Pendeln**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Unterstützt die benutzerdefinierte Einstellung des Pendelwinkels des Roboter-Endeffektors um die Rx-Richtung des Pendelkoordinatensystems während der Pendelbewegung.

- **Funktion für allmähliche Änderung von Prozessparametern beim Schweißen**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Ermöglicht die allmähliche Änderung der Vorschubgeschwindigkeit und der Strom-/Spannungswerte während des Schweißprozesses.

- **Analoge Lichtbogenverfolgungsfunktion**:
    Pfad: Grundeinstellungen -> Basis -> I/O-Einstellungen -> AI.

    Beschreibung: Direkte Verbindung der DI, DO, AI und AO des Steuerungsgehäuses mit den I/O-Anschlüssen des Schweißgeräts zur Realisierung einer Lichtbogenverfolgung basierend auf analoger Stromrückmeldung.

- **FRCap-Plugin-System + Palettierer-Plugin-Paket-Funktion**:

    Beschreibung: Anpassung des FRCap-Plugin-Systems und des Palettierer-Plugin-Pakets für die QX x86-Version. FRCap kann über die bereitgestellten offiziellen Schnittstellen mit der Robotersteuerung interagieren, oder Kunden können basierend auf tatsächlichen Anforderungen benutzerdefinierte Schnittstellenbefehle und Verarbeitungslogiken für individuelle Entwicklungen schreiben.

- **Robotermodelle und -typen**:

    Beschreibung: Hinzufügen der Robotermodell- und Konfiguration FR3-C.

Version V3.8.1
-----------------

Datum: 2025-04-14

- **Optimierung der T-förmigen Geschwindigkeitsfunktion**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung, Grundeinstellungen -> Basismodul.

    Beschreibung: In der Bewegungskonfiguration wurde ein neuer Optimierungsmodus für trapezförmige Geschwindigkeit hinzugefügt. Dieser optimiert den Ruck in der Start-Stopp-Phase und erhöht die Beschleunigung in der Beschleunigungsphase. Hauptsächlich anwendbar in Situationen, in denen in der Start-Stopp-Phase leicht Kollisionsalarme ausgelöst werden oder in dieser Phase deutliche Restvibrationen auftreten.

- **Optimierung der Förderband-Tracking-Funktion**:
    Pfad: Zusatzanwendungen -> Prozesspakete -> Förderband-Tracking.

    Beschreibung: Im Förderband-Tracking-Bewegungsmodus wurde eine neue Nachführbewegungsfunktion hinzugefügt. Eine Bewegungsteachung im Werkstückkoordinatensystem ist nicht erforderlich. Eine benutzerdefinierte Auslöseverzögerungsdistanz kann eingestellt werden.

- **Hinzufügen einer Impedanz-Rückruffunktion für Achs-Interferenzbereiche**:
    Pfad: Grundeinstellungen -> Sicherheit -> Interferenzbereiche.

    Beschreibung: Bei kraftsensorgestütztem Führen kann das Betreten eines Interferenzbereichs eine Impedanz-Rückruffunktion auslösen.

- **Anpassungsfunktion für Schweißgriffe**:
    Beschreibung: Neue Anpassung für Schweißgriffe: Ein am Roboterende montierter Schweißgriff ermöglicht das Schreiben von Schweißprogrammen sowie die Steuerung von Roboterstart/-stopp, Hand-/Automatikumschaltung, Führung usw.

- **Hinzufügen einer Anzeige für Gelenkbegrenzungsringe auf der WEB-Seite**:
    Beschreibung: Aktivieren der Anzeigefunktion für Begrenzungsringe zur Echtzeitanzeige der Gelenkpositionen.

- **Neue SDK-Funktionen**:
    Beschreibung: Dem SDK wurden Funktionen zum Herunterladen von Controller-Protokollen, aller Datenquellen und Datensicherungspakete hinzugefügt.

- **Funktion zur Aufzeichnung von Gelenkinformationen vor und nach einer Kollision**:
    Beschreibung: Aufzeichnung von Gelenkpositionen, -geschwindigkeiten, -beschleunigungen und Drehmomentinformationen vor und nach einer Kollision. Erleichtert die direkte Analyse der Kollisionsursache beim Kunden vor Ort.

Version V3.8.0
-----------------

Datum: 2025-03-03

- **Lichtbogenverfolgungsfunktion mit monotoner Änderung von Offset und Pendelamplitude**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Die Pendelbreite als Pendelparameter kann sich während einer Schweißbewegung allmählich ändern. Der Pendelamplitudenparameter am Anfang des Segments geht allmählich in den Parameter am Ende des Segments über. Das Schweißzentrum kann aktiv aus der Schweißnahtmitte verschoben werden.

- **Benutzerdefinierte Schwellwertfunktion für das Kollisionserkennungsmoment**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Während des Betriebs kann der Schwellwert für das Kollisionserkennungsmoment eingestellt werden. Es kann zwischen Gelenkmoment-Schwellwert oder TCP-seitigem Momentschwellwert gewählt werden. Nach einer Kollision werden Informationen wie Gelenkgeschwindigkeit, -beschleunigung und -moment in einer Protokolldatei ausgegeben.

- **Echtzeit-Vorausschau-Bahnplanungsmethodenfunktion**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Realisiert die geglättete Anpassung und Verbindung mehrerer Bahnpunkte. Die Betriebsgeschwindigkeit passt sich adaptiv an die Bahnkrümmung an.

- **Zeichnung der Lastkurven für die gesamte FR-Roboterserie**:
    Beschreibung: Aktualisierung der Lastkurvendiagramme für die gesamte FR-Roboterserie.

- **Optimierung der Geschwindigkeitsumschaltlogik im Reduktionsmodus**:
    Beschreibung: Behebung und Optimierung des Problems, dass bei Auslösung des Reduktionsmodus gelegentlich Bewegungen mit deutlich geringerer Geschwindigkeit als der Reduktionsmodus-Geschwindigkeit auftraten.

- **Optimierung der Teachpunkte**:
    Beschreibung: Optimierung der Hinweismeldungen beim Setzen von Teachpunkten.

- **Funktion des CNC-Funktionspakets basierend auf FOCAS**:
    Beschreibung: Hinzufügen der CNC-Funktionalität basierend auf FOCAS.

- **Anpassung von Slave-Befehlen an Karten**:
    Beschreibung: Anpassung von Slave-Befehlen an die EnTalk miniPCIe-Karte (Profinet-Protokoll, Ethernet/IP-Protokoll, CC-Link IEF Basic-Protokoll). Anpassung an die CIFX 9OE-RE/F/PNS miniPCIe-Karte (Profinet-Protokoll, Ethernet/IP-Protokoll, Ethercat-Protokoll, CC-Link IEF Basic-Protokoll).

- **Checkpoint-Zeitstempel-Rückmeldungsfunktion**:
    Beschreibung: Bei ServoJ-Bewegungen können Zeitstempelergebnisse empfangen werden, einschließlich Befehlsnummer und Zeitstempel für Versand, Warteschlangeneintritt, Warteschlangenaustritt und Ausführung.

- **Anpassung des Lasersensors an das offene Peripherieprotokoll des Controllers**:
    Beschreibung: Hinzufügen einer Kommunikationsfunktion für das offene Laserperipherieprotokoll.

Version V3.7.8
-----------------

Datum: 2025-01-20

- **Funktion zur verzerrungsfreien Punktverfolgung mit externen Achsen und Laserdaten**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung, Grundeinstellungen -> Peripherie -> Linienlasersensor.

    Beschreibung: Hauptsächlich für die Echtzeit-Punktverfolgung von Positionierern gedacht. Ermöglicht, dass während der Bewegung externer Achsen die durch den Laser erfassten Werkstückabweichungen am Roboter-Endeffektor kompensiert werden.

- **Neue und optimierte Roboter-CI-Konfigurationsfunktionen**:
    Pfad: Grundeinstellungen -> Basis -> I/O-Einstellungen -> DI, Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: 1. Den konfigurierbaren CI-Eingängen wurde die Funktion "Hand-/Automatikumschaltung (High/Low-Pegel)" hinzugefügt. Wenn das Signal an diesem Port aktiv ist, wechselt der Roboter automatisch in den Automatikmodus; wenn das Signal inaktiv ist, wechselt er in den Handmodus. 2. Nach dem Öffnen eines LUA-Programms in der WebApp wird durch einen konfigurierbaren CI-Start das aktuell geöffnete LUA-Programm automatisch ausgeführt, nicht das zuletzt gespeicherte Programm.

- **Optimierung der WebApp-Statusabfragefunktion**:
    Pfad: Statusinformationen -> Statusabfrage.

    Beschreibung: Die Dateninteraktionsmethode zwischen Frontend und Backend wurde von Frontend-Polling auf WebSocket umgestellt, um die CPU-Auslastung zu senken.

- **Konfigurierbare Funktion für DO-Pegel nach dem Einschalten der Steuerungsgehäuse-Firmware**:
    Pfad: Grundeinstellungen -> Basis -> I/O-Einstellungen -> DO.

    Beschreibung: Eine neue Konfiguration "Steuerungsgehäuse DO-Ausgabe während des Einschaltens" wurde hinzugefügt. Vor der Roboteraktivierung können die DOs des Steuerungsgehäuses je nach Anwendungsszenario auf den gewünschten High/Low-Pegel konfiguriert werden.

- **Echtzeit-Vorausschau-Bahnplanungsmethodenfunktion**:
    Pfad: Teachprogramm -> Programmierung, grafische Programmierung, Knotenpunktprogrammierung.

    Beschreibung: Neuer "TrajectoryLA"-Befehl hinzugefügt.

- **Strategiefunktion nach kraftsensorbasierter Kollision**:
    Pfad: Grundeinstellungen -> Gelenke -> Kollisionsstufe.

    Beschreibung: Dem Kollisionsrückprallmodus wurde ein Parameter "Sicherheitsgeschwindigkeit" hinzugefügt.

- **Automatische Anhebungsfunktion nach Kraftsensorkollision**:
    Beschreibung: Implementierung einer automatischen Roboteranhebung nach einer kraftsensorbasierten Kollisionserkennung, mit Begrenzung der Geschwindigkeit während des Anhebens.

- **Zeichnung der Lastkurven für die gesamte FR-Roboterserie**:
    Beschreibung: Aktualisierung der Lastkurvendiagramme für die gesamte FR-Roboterserie.

Version V3.7.7
-----------------

Datum: 2024-12-30

- **Echtzeit-Überwachungsfunktion für Greiferstatusdaten**:
    Pfad: Grundeinstellungen -> Peripherie -> Greifer -> Statusüberwachung.

    Beschreibung: Echtzeitanzeige von Statusinformationen wie Greifergeschwindigkeit, Drehmoment und Position.

- **Datenerfassungsfunktion für Controller-Fehler**:
    Pfad: Systemeinstellungen -> Allgemeine Einstellungen -> Fehlerdaten.

    Beschreibung: Bei Fehlern während des Roboterbetriebs (z. B. Kollisionen, Befehlspunktfehler) zeichnet der Controller automatisch die Roboterstatusinformationen (Position, Geschwindigkeit usw.) von 15 Sekunden vor bis 15 Sekunden nach dem Fehler auf. Die WebApp kann Fehlerinformationen im .csv-Format exportieren, was bei der Fehleranalyse hilft.

- **Vermeidung und Durchquerung von Singularitäten bei kraftsensorgestütztem Führen**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre -> Kraftsensor-gestützte Sperre.

    Beschreibung: 1. Auf der Oberfläche für kraftsensorgestütztes Führen kann die Strategie "Vermeiden" gewählt werden. Wenn sich der Roboter beim Führen einer Singularität nähert, wird eine virtuelle Kraft erzeugt. 2. Bei Wahl der Strategie "Durchqueren" wird in der Nähe einer Singularität in den Führungsmodus umgeschaltet; bei Entfernung von der Singularität wird zurück in den kraftsensorgestützten Führungsmodus geschaltet.

- **Anpassung alter Dynamikmodelle an 360°-freie Montage und Import von Sicherungsdateien mit Dynamikanpassung**:
    Pfad: Grundeinstellungen -> Basis -> Montage, Zusatzanwendungen -> Werkzeuganwendungen -> Datensicherung.

    Beschreibung: Beim Import von Sicherungsdateien wird eine Überprüfung von Robotertyp, Montageart, Montagewinkel und Dynamikkonfigurationstyp hinzugefügt. Bei Nichtübereinstimmung dieser Parameter wird eine Warnung ausgegeben und der Import verhindert.

- **Funktion zur Durchquerung von Singularitäten im Automatikmodus**:
    Pfad: Teachprogramm -> Peripherie -> LIN/ARC-Befehl.

    Beschreibung: Neue Bewegungsschutzkonfiguration "Singularität durchqueren" hinzugefügt.

- **Funktion zur automatischen Aktualisierung des entsprechenden Punkt-Lua-Programms nach Punkterfassung mit Endeffektor-Taste**:
    Pfad: Teachprogramm -> Programmierung -> Teachpunkte.

    Beschreibung: Neue Funktion zur automatischen Aktualisierung des entsprechenden Punkt-Lua-Programms nach Punkterfassung mit Endeffektor-Taste.

- **Optimierung der Statusabfrage-Oberfläche**:
    Pfad: Statusinformationen -> Statusabfrage.

    Beschreibung: UI- und Interaktionsoptimierungen der Statusabfrage-Oberfläche.

- **Optimierung der WebApp- und Teachpendant-Oberflächen**:
    Beschreibung: Die WebApp und das Teachpendant verfügen nun über russische und traditionell chinesische Anzeigeoberflächen.

- **Optimierungsfunktion der WebApp-Anzeigeoberfläche**:
    Beschreibung: In der unteren linken Ecke der WebApp-Oberfläche werden nun die Softwareversion und das Robotermodell angezeigt.

- **Laser-Tracking-Funktion mit externen Achsen**:
    Beschreibung: 1. Bei synchroner Bewegung von Roboter und externer Achse realisiert der Laser ein synchrones Tracking im Koordinatensystem der externen Achse. 2. Bei asynchroner Bewegung von Roboter und externer Achse kann der Laser entweder im Roboter-Basiskoordinatensystem oder im Koordinatensystem der externen Achse tracken.

- **Funktion zum Führen von Werkzeugpunkten basierend auf Kraftsensoren**:
    Beschreibung: In der Web-Oberfläche das FT-Referenzkoordinatensystem als benutzerdefiniertes Koordinatensystem einstellen. Nach Aktivieren der kraftsensorgestützten Führung bewegt sich der Roboter entlang des eingestellten Werkzeugkoordinatensystems.

- **Roboter-CNDE-Funktion**:
    Beschreibung: Der Client kann über CNDE Roboterstatusrückmeldungen erhalten und Steuerdaten an den Roboter senden (UDP-Kommunikation). Der Statusrückmeldezyklus ist konfigurierbar (1-200 ms). Der Inhalt der Roboterstatusrückmeldedaten und die vom Client eingegebenen Steuerdaten für den Roboter sind frei konfigurierbar.

Version V3.7.6
-----------------

Datum: 2024-11-18

- **Optimierung des Seitenlayouts der Grundeinstellungen**:
    Pfad: Grundeinstellungen.

    Beschreibung: Optimierung der Werkzeugeinstellungsoberfläche, der Lastkonfigurationsoberfläche und der Anzeige einiger Funktionssymbole.

- **Interaktionsoptimierung für die Konfiguration externer Peripherieachsen in der WebApp**:
    Pfad: Grundeinstellungen -> Peripherie -> Externe Achsen.

    Beschreibung: Optimierung des Layouts und der Interaktion der Oberfläche für externe Achsen.

- **Optimierung der Systemprotokollfunktion**:
    Pfad: Statusinformationen -> Systemprotokoll.

    Beschreibung: Neue seitenweise Anzeige der Protokolle und Unterscheidung detaillierter Aktionskategorien.

- **Funktion für konstante Querkraft in X/Y-Richtung beim Schleifen**:
    Pfad: Teachprogramm -> Programmierung -> Kraftregelungsset -> F/T_Control-Befehl.

    Beschreibung: Ein Parameter "Schleifscheibenradius" wurde hinzugefügt, der wiederholte lineare/kurvenförmige Bewegungen entlang der Werkstückoberfläche ermöglicht.

- **Funktion für lasergestützte Punkterfassungsbewegung**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Schnittpunkterzeugung.

    Beschreibung: Die Funktion zur Berechnung von Schnittpunktkoordinaten aus Drei-Punkt- und Vier-Punkt-Suche wurde um die Verwendung von Lua-Skriptbefehlen erweitert.

- **Externe Achskonfiguration – Zwei-Freiheitsgrad-Wagen-Funktion**:
    Pfad: Grundeinstellungen -> Peripherie -> Externe Achsen.

    Beschreibung: Hinzufügen einer externen Achslösung "Zwei-Freiheitsgrad-Wagen". Die Kommunikation zwischen Roboter und SPS erfolgt per UDP, die SPS steuert dann den Zwei-Freiheitsgrad-Wagen über EtherCat.

- **Funktion der TCP-Kalibrierungsmethode basierend auf einem Plattenwerkzeug**:
    Pfad: Grundeinstellungen -> Koordinatensysteme -> Werkzeugkoordinaten.

    Beschreibung: Neue Koordinatensystem-Kalibrierungsmethode "Plattenwerkzeug-Kalibrierung" hinzugefügt.

- **Funktion für Roboter-Hintergrundprogramme**:
    Pfad: Teachprogramm -> Programmierung.

    Beschreibung: Hintergrundprogramme können nun korrekt auf I/O-Schnittstellendaten zugreifen, einschließlich System-I/O, Modbus und erweitertem I/O.

- **Funktion zur automatischen Vermeidung von Singularitäten in Roboterbahnen**:
    Pfad: Teachprogramm -> Programmierung -> Linienbefehl Lin / Kreisbogenbefehl Arc.

    Beschreibung: Neue Bewegungsschutzkonfiguration "Singularität vermeiden" hinzugefügt.

- **Anpassungsfunktion für rotierende Greifer-Endeffektoren**:
    Pfad: Grundeinstellungen -> Peripherie -> Greifer.

    Beschreibung: Hinzufügen von Funktionscodes für rotierende Greifer.

- **Benutzerdefinierte Protokoll-Slave-Befehle**:
    Pfad: Fernmodus.

    Beschreibung: Neue Konfiguration "Controller-Slave-Protokoll" hinzugefügt.

- **Schweißdrahtsuchfunktion über UDP-Kommunikation**:

    Beschreibung: Der Roboter kann über erweitertes UDP-I/O die Schweißdrahtsuche starten/stoppen und das Erfolgssignal der Schweißdrahtsuche empfangen.

- **Optimierung der Sicherungsdatei-Funktion**:

    Beschreibung: Unterstützung für den Import älterer Datenpakete (QX 3.6.1 und später).

- **Optimierung der Funktion "Werkseinstellungen wiederherstellen"**:

    Beschreibung: Neue Dateiprüfung hinzugefügt, erhöht die Stabilität der Systemwiederherstellung auf Werkseinstellungen.

- **Optimierung der Upgrade-Funktion**:

    Beschreibung: Direktes Upgrade von QX3.6.9 und späteren Versionen auf QX3.7.6 möglich. Benutzerdaten der aktuellen Version bleiben nach dem Upgrade erhalten.

- **Downgrade-Funktion für die Seite**:

    Beschreibung: Die WebApp-Seite unterstützt Downgrades auf beliebige Versionen ab QX3.6.9. Benutzerdaten der aktuellen Version bleiben nach dem Downgrade erhalten.

Version V3.7.5
-----------------

Datum: 2024-09-30

- **Einstellbare Winkelgeschwindigkeit für Eckpunkt-Posenübergänge**:
    Pfad: Teachprogramm -> Programmierung -> Linienbefehl Lin.

    Beschreibung: Neue Bewegungsschutzkonfiguration "Übergangspunkt-Winkelgeschwindigkeit einstellbar" hinzugefügt.

- **Mehrlagenschweißfunktion mit Lichtbogenverfolgung**:
    Pfad: Zusatzanwendungen -> Prozesspakete -> Schweißexpertenbibliothek -> Mehrlagenschweißen.

    Beschreibung: Neue Konfigurationen für "Pendelfunktion in der ersten Lage" und "Lichtbogenverfolgungsfunktion" hinzugefügt.

- **Konfigurationsfunktion für 485-Erweiterungsachsen**:
    Pfad: Grundeinstellungen -> Peripherie -> Externe Achsen.

    Beschreibung: Konfiguration für "Beschleunigung und Not-Halt" hinzugefügt.

- **Automatische TCP-Kalibrierungsfunktion für Roboterwerkzeuge (mit selbstgebauter faseroptischer Sensorvorrichtung)**:
    Pfad: Grundeinstellungen -> Basis -> Werkzeugkoordinaten.

    Beschreibung: Neue Koordinatensystem-Kalibrierung "Photoelektrische automatische Kalibrierung" hinzugefügt.

- **Mehrsprachige Einstellungsfunktion für das Teachpendant**:
    Pfad: Anmeldeseite.

    Beschreibung: Neue Konfiguration "Sprachumschaltung" hinzugefügt.

Version V3.7.4
-----------------

Datum: 2024-08-09

- **Softwarefunktion basierend auf offenem Lua-Endeffektorprotokoll (Greiferteil)**:
    Pfad: Grundeinstellungen -> Peripherie -> Greifer.

    Beschreibung: Neue Konfiguration "Endeffektor-Protokoll aktivieren" hinzugefügt.

- **Schräg-Sägezahn-Pendelfunktion**:
    Pfad: Teachprogramm -> Programmierung -> Pendelbefehl Weave.

    Beschreibung: Parameterkonfiguration "Pendelrichtungs-Azimutwinkel" hinzugefügt.

- **Optimierungsfunktion für Roboter-Schweißprozesspakete**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgerät -> Schweißgerätekonfiguration.

    Beschreibung: Neue Konfiguration "Schweißprozessparameter" hinzugefügt.

- **Funktion zur Behandlung von Gelenkübergeschwindigkeit bei Lin-Befehlen**:
    Pfad: Teachprogramm -> Programmierung -> Linienbefehl Lin.

    Beschreibung: Neue Bewegungsschutzkonfiguration "Gelenk-Übergeschwindigkeitsschutz" hinzugefügt.

Version V3.7.3
-----------------

Datum: 2024-06-28

- **Funktion zur Robotersteuerung als Modbus-Slave**:
    Pfad: Teachprogramm -> Programmierung -> ModbusTCP.

    Beschreibung: Neue Konfiguration "Slave-Controller" hinzugefügt.

- **Funktion für Not-Halt-Typen**:
    Pfad: Grundeinstellungen -> Sicherheit -> Not-Halt.

    Beschreibung: Den Not-Halt-Typen wurden die Typen "Klasse 1a, Klasse 2a, Klasse 2" hinzugefügt.

Version V3.7.2
-----------------

Datum: 2024-06-07

- **Konfigurationsfunktion basierend auf offenem Lua-Endeffektorprotokoll**:
    Pfad: Grundeinstellungen -> Peripherie -> Endeffektorwerkzeuge -> Offenes Protokoll.

    Beschreibung: Neue Konfiguration "Offenes Protokoll" hinzugefügt.

- **Funktion für Bewegungs-AO-Steuerbefehle**:
    Pfad: Teachprogramm -> Programmierung.

    Beschreibung: Neuer "Bewegungs-AO-Befehl" hinzugefügt.

- **Gemischte Führungsfunktion mit 6-Achsen-Kraft- und Gelenkimpedanz**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre.

    Beschreibung: Neue "Gemischte Führung mit 6-Achsen-Kraft und Gelenkimpedanz" hinzugefügt.

- **Funktion für Reaktionsstrategie nach Kollision**:
    Pfad: Grundeinstellungen -> Basis -> Gelenke -> Kollisionsstufe.

    Beschreibung: Neue Konfiguration "Kollisionsstrategie" hinzugefügt.

- **Funktion zur Erstaktivierung des Roboters**:
    Pfad: Anmeldeeinstellungen.

    Beschreibung: Neue Verifikationsfunktion für die Erstaktivierung des Roboters hinzugefügt.

Version V3.7.1
-----------------

Datum: 2024-05-10

- **Sperrfunktion für die Web-Oberfläche**:
    Pfad: Systemeinstellungen -> Benutzerdefinierte Informationen.

    Beschreibung: Neue Konfiguration "Web-Oberfläche Bildschirmsperre" hinzugefügt.

- **Funktion zur Berechnung von Schnittpunktkoordinaten aus Drei- und Vier-Punkt-Suche**:
    Pfad: Zusatzanwendungen -> Werkzeuganwendungen -> Schnittpunkterzeugung.

    Beschreibung: Neue "Funktion zur Berechnung von Schnittpunktkoordinaten aus Drei- und Vier-Punkt-Suche" hinzugefügt.

- **Optimierungsfunktion für Segment-Schweißbewegungsposen**:
    Pfad: Teachprogramm -> Programmierung -> Segment-Schweißbefehl Segment.

    Beschreibung: Neue Konfiguration "Segment-Schweißmodus" hinzugefügt.

- **Funktion für virtuelle Wände basierend auf Kraftsensoren**:
    Pfad: Grundeinstellungen -> Peripherie -> Kraftsensor, Zusatzanwendungen -> Werkzeuganwendungen -> Führungssperre.

    Beschreibung: Der Endeffektor-Peripheriekonfiguration wurden "Kraftsensor"-bezogene Konfigurationsparameter hinzugefügt. Der kraftsensorgestützten Sperre wurde ein Parameter "Trägheitskoeffizient" hinzugefügt.

- **Neue Funktionen für die SmartTool- und Kraftsensor-Kombination**:
    Pfad: Grundeinstellungen -> Peripherie -> Schweißgriff.

    Beschreibung: Neue Tastenfunktionskonfigurationen hinzugefügt.