Versionshinweise
====================

.. toctree::
    :maxdepth: 5

.. list-table::
   :widths: 10 10 30
   :header-rows: 0
   :align: center

   * - **Version**
     - **Datum**
     - **Aktualisierungsbeschreibung**

   * - V3.9.9
     - 2026-09-01
     - | 1. Modifizierte die Parameterbeschreibung der GetGripperMotionDone()-Schnittstelle zum Abrufen des Greiferstatus, aktualisierte die Definition des Greiferstatus;
       | 2. Modifizierte GetInverseKinExaxis(), die Schnittstelle zur inversen Kinematiklösung unter Einbeziehung von Erweiterungsachsenpositionen, fügte Gelenkkonfigurationsparameter mit dem Standardwert -1 hinzu, der auf die aktuelle Gelenkkonfiguration verweist;
       | 3. Modifizierte die kraftgeregelten Schnittstellen FT_SpiralSearch(), FT_LinInsertion() und FT_FindSurface() um Parameter für die Behandlungsstrategie bei nicht erkannter Kraft/Drehmoment;
       | 4. Modifizierte die Parameterbeschreibungen der CIO-Funktionskonfigurationsschnittstellen des Robotersteuerschranks SetDIConfig(), GetDIConfig(), SetDOConfig(), GetDOConfig(), aktualisierte die neu hinzugefügten Funktionsnamen und Funktionscodes;
       | 5. Modifizierte die Codebeispiele für die grundlegende Robotersteuerung, fügte Codebeispiele für den Wechsel in den manuellen Hochgeschwindigkeitsmodus hinzu;
       | 6. Fügte den ServoJ()-Befehl für die Servo-Modus-Bewegung im Gelenkraum (Mehrpunkteingabe) und Codebeispiele hinzu;
       | 7. Fügte den GetSafetyParamsCheckSum()-Befehl zum Abrufen der Prüfsumme der Sicherheitskonfigurationsparameter, den SafetyOPPasswordCheck()-Befehl zur Sicherheitsoperations-Kennwortprüfung und Codebeispiele hinzu;
       | 8. Fügte den GripperWaitMotionDone()-Befehl zum Warten auf den Abschluss der Greiferbewegung und Codebeispiele hinzu;
       | 9. Fügte den SetRobotTime()-Befehl zur Synchronisation der Systemzeit mit dem Roboter und Codebeispiele hinzu;
       | 10. Fügte SetSafetyDIConfig() zur Sicherheits-Zweikanal-CI-Funktionskonfiguration, SetSafetyDOConfig() zur Sicherheits-Zweikanal-CO-Funktionskonfiguration und Codebeispiele hinzu;
       | 11. Fügte den HiSpeedManualSwitch()-Befehl zum Wechsel in den manuellen Hochgeschwindigkeitsmodus hinzu;
       | 12. Fügte Codebeispiele für die Überlagerung der Pendelbewegung während der Wiedergabe der Lasersensortrajektorie hinzu;

   * - V3.9.8
     - 2026-07-27
     - | 1. Aktualisierung der Roboterstatus-Rückmeldungsstruktur um den aktuellen Ausführungsstatus des LUA-Programms des Roboters: 0 - Programm läuft nicht; 1 - Programm läuft (einschließlich Programm pausiert);
       | 2. Aktualisierung der Parameterbeschreibungen für die Schnittstellen SetExToolCoord() und SetExToolList() zum Festlegen des externen Werkzeugkoordinatensystems und der Werkzeugkoordinatensystemliste. Die Nummern der externen Werkzeugkoordinatensysteme wurden auf 20-39 aktualisiert. Aktualisierung der Codebeispiele für Operationen mit externen Werkzeugkoordinatensystemen.
       | 3. Hinzufügung der Möglichkeit, Parameter für Werkzeugtyp, Installationsposition, Werkzeug-ID und Lastnummer zur GetToolCoordWithID()-Schnittstelle zum Abrufen von Werkzeugkoordinatensystemparametern abzurufen.
       | 4. Hinzufügung der Möglichkeit, Parameter für Referenzkoordinatensysteme zur GetWObjCoordWithID()-Schnittstelle zum Abrufen von Werkstückkoordinatensystemparametern abzurufen.
       | 5. Hinzufügung der Möglichkeit, Parameter für die am Roboterende montierte Werkstückkoordinatensystem-Pose zur GetExToolCoordWithID()-Schnittstelle zum Abrufen von externen Werkzeugkoordinatensystemparametern abzurufen.
       | 6. Hinzufügung der Möglichkeit, Parameter für die erweiterte Achsnummer und den Kalibrierungsflag zur GetExAxisCoordWithID()-Schnittstelle zum Abrufen von erweiterten Achsenkoordinatensystemparametern abzurufen.
       | 7. Hinzufügung von Parametereinstellungen für die Gelenksicherheitsgeschwindigkeit des Roboters zur SetVelReducePara()-Schnittstelle zum Festlegen der Robotersicherheitsgeschwindigkeit.
       | 8. Hinzufügung eines Beispiels zur Erfassung des Schweißgeräte-Steuermodus zum Codebeispiel für die Konfiguration von Schweißparametern.
       | 9. Hinzufügung von Codebeispielen zum Abrufen von erweiterten DI- und erweiterten DO-Funktionskonfigurationen zum Codebeispiel für die Konfiguration von erweiterten IO-Schweißsignalen.
       | 10. Hinzufügung eines neuen Codebeispiels zum Festlegen der Gelenksicherheitsgeschwindigkeit des Roboters;
       | 11. Hinzufügung einer neuen Schnittstelle WaitStationaryMotionDone() zum Warten auf den Abschluss einer Leerbewegung an Ort und Stelle;
       | 12. Hinzufügung einer neuen Schnittstelle SetStationaryTrackPara() zur Konfiguration von Förderband-ortsverfolgungsparametern, zusammen mit einem Codebeispiel für die Förderband-ortsverfolgung;
       | 13. Hinzufügung neuer Schnittstellen WorkPieceTrsfStart() und WorkPieceTrsfEnd() zum Starten und Beenden der Werkstückkoordinatensystemtransformation, zusammen mit einem Codebeispiel für die Werkstückkoordinatensystemtransformation.
       | 14. Hinzufügung der GetWeldMachineCtrlMode()-Schnittstelle zum Abrufen des Schweißgeräte-Steuermodus.
       | 15. Hinzufügung der GetExtDIConfig()- und GetExtDOConfig()-Schnittstellen zum Abrufen der erweiterten DI-Funktions- und erweiterten DO-Funktionskonfigurationen.

   * - V3.9.7
     - 2026-06-25
     - | 1. Robotersatus-Rückmeldungsstruktur aktualisiert: Objekterkennungsstatus zum Greiferbewegung-abgeschlossen-Signal hinzugefügt; zu Greiferfehlern hinzugefügt: 2-Befehlfehler, 3-Werkstückfall, andere-Greiferfehlercode +3;
       | 2. Codebeispiele für Ausgangs-Reset nach LUA-Programmstopp/-pause aktualisiert; Schnittstelle zum Laden von lua-Dateien optimiert, jetzt nur noch lua-Dateiname erforderlich, Pfad nicht mehr benötigt.
       | 3. Codebeispiele für photoelektrische Sensor-TCP-Kalibrierung aktualisiert; Schnittstelle zum Laden von Dateien optimiert, jetzt nur noch lua-Dateiname erforderlich, Pfad nicht mehr benötigt.
       | 4. Codebeispiele für Geschwindigkeitseinstellung während der Trajektorienausführung aktualisiert; Schnittstelle zum Laden von Trajektorien-J-Dateien optimiert, jetzt nur noch Trajektorien-J-Dateiname erforderlich, Pfad nicht mehr benötigt.
       | 5. Codebeispiele für Robotertrajektorien-J-Datei-Wiedergabe aktualisiert; Schnittstelle zum Laden von Trajektorien-J-Dateien optimiert, jetzt nur noch Trajektorien-J-Dateiname erforderlich, Pfad nicht mehr benötigt.
       | 6. Codebeispiele für Trajektorienwiedergabe (Trajektorien-Vorausschau) aktualisiert; Schnittstelle zum Laden von Trajektorien-J-Dateien optimiert, jetzt nur noch Trajektorien-J-Dateiname erforderlich, Pfad nicht mehr benötigt.
       | 7. Der Jobprogrammnamen-Parameter der LoadDefaultProgConfig()-Schnittstelle erfordert jetzt nur noch den lua-Dateinamen, Pfad nicht mehr benötigt.
       | 8. Der Jobprogrammnamen-Parameter der ProgramLoad()-Schnittstelle erfordert jetzt nur noch den lua-Dateinamen, Pfad nicht mehr benötigt.
       | 9. Der Jobprogrammnamen-Parameter der GetLoadedProgram()-Schnittstelle erfordert jetzt nur noch den lua-Dateinamen, Pfad nicht mehr benötigt.
       | 10. Codebeispiele für LUA-Programmoperationen des Roboters aktualisiert; Schnittstelle zum Laden von Dateien optimiert, jetzt nur noch lua-Dateiname erforderlich, Pfad nicht mehr benötigt.
       | 11. Aktivierungsstatus-Parameter für dreifingrige Hand zur SetAxleLuaEnableDeviceType()-Schnittstelle hinzugefügt;
       | 12. Aktivierungsstatus-Parameter für dreifingrige Hand zur GetAxleLuaEnableDeviceType()-Schnittstelle hinzugefügt;
       | 13. Statusparameter für aktivierte Gerätenummer der dreifingrigen Hand zur GetAxleLuaEnableDevice()-Schnittstelle hinzugefügt;
       | 14. Greifer-Funktionscode-Array in SetAxleLuaGripperFunc() auf 32 erweitert, Drehgreifersteuerung usw. hinzugefügt;
       | 15. Greifer-Funktionscode-Array in GetAxleLuaGripperFunc() auf 32 erweitert, Drehgreiferstatus usw. hinzugefügt;
       | 16. Fehler im Schnittstellennamen von SetCoderCompenParams() korrigiert;
       | 17. SetDexterousHandsMove()-Schnittstelle zur Steuerung der Bewegung der dreifingrigen Hand hinzugefügt.
       | 18. SetDexterousHandsAct()-Schnittstelle zur Steuerung des Resets und der Aktivierung der dreifingrigen Hand hinzugefügt.
       | 19. ClearDexterousHandsError()-Schnittstelle zum Löschen von Fehlern der dreifingrigen Hand hinzugefügt.
       | 20. SetDexterousHandsFunc()-Schnittstelle zum Festlegen der aktivierten Aktionssteuerungsfunktionen der dreifingrigen Hand hinzugefügt.
       | 21. GetDexterousHandsFunc()-Schnittstelle zum Abrufen der aktivierten Aktionssteuerungsfunktionen der dreifingrigen Hand hinzugefügt.
       | 22. SetWeaveBackCenterConfig(), GetWeaveBackCenterConfig() zum Einstellen und Abrufen der Parameter für die Rückkehr zum Zyklus-Nullpunkt nach Pendelende hinzugefügt.
       | 23. SetWeaveOffsetRT()-Schnittstelle zum Einstellen des Echtzeit-Pendeloffsets hinzugefügt;
       | 24. SetSpeedInstant()-Schnittstelle zur Echtzeit-Geschwindigkeitseinstellung hinzugefügt;

   * - V3.9.6
     - 2026-05-26
     - | 1.Roboterstatus-Rückmeldungsstruktur aktualisiert, Status der Erweiterungsachsen-Koordinatensystemnummer hinzugefügt;
       | 2.Aufzählungstyp für Roboterstatus-Rückmeldungskonfiguration aktualisiert, Konfigurationsaufzählung der Erweiterungsachsen-Koordinatensystemnummer hinzugefügt;
       | 3.ExtAxisGetParamConfig()-Schnittstelle zum Abrufen der UDP-Erweiterungsachsen-Parameterkonfiguration hinzugefügt;
       | 4.ServoJV()-Schnittstelle für Geschwindigkeitsservomodellbewegung im Roboter-Gelenkraum hinzugefügt;
       | 5.ServoMITStart()-Schnittstelle für Start der Roboter-Gelenk-MIT-Steuerung hinzugefügt;
       | 6.ServoMITEnd()-Schnittstelle für Ende der Roboter-Gelenk-MIT-Steuerung hinzugefügt;
       | 7.ServoMIT()-Schnittstelle für Roboter-Gelenk-MIT-Steuerung hinzugefügt;
       | 8.SetLaserWeldingParam()-Schnittstelle für die Konfiguration von Roboter-Laserschweißparametern hinzugefügt;
       | 9.SetLaserWeldingStartEnd()-Schnittstelle zum Einstellen des Start/Stopps des Roboter-Laserschweißens hinzugefügt;
       | 10.SetLaserWeldingEnable()-Schnittstelle zum Aktivieren/Deaktivieren des Laserschweißgeräts hinzugefügt;
       | 11.ResetLaserWeldingErr()-Schnittstelle zum Zurücksetzen von Laserschweißgerät-Fehlern hinzugefügt;
       | 12.GetLaserWeldingRunningState()-Schnittstelle zum Abrufen des Betriebszustands des Laserschweißgeräts hinzugefügt;
       | 13.GetLaserWeldingErrState()-Schnittstelle zum Abrufen des Fehlerzustands des Laserschweißgeräts hinzugefügt;
       | 14.GetLaserWeldingParamTarget()-Schnittstelle zum Abrufen der Laserschweiß-Konfigurationsparameter hinzugefügt;
       | 15.GetLaserWeldingParamActual()-Schnittstelle zum Abrufen der aktuell aktiven Konfigurationsparameter des Laserschweißgeräts hinzugefügt;
       | 16.SetLaserWeldingEnableExtDoNum()-Schnittstelle zum Konfigurieren des erweiterten IO-Aktivierungs-DO-Ports des Laserschweißgeräts hinzugefügt;
       | 17.SetLaserWeldingStartExtDoNum()-Schnittstelle zum Konfigurieren des erweiterten IO-Start-DO-Ports des Laserschweißgeräts hinzugefügt;
       | 18.SetLaserWeldingErrResetExtDoNum()-Schnittstelle zum Konfigurieren des erweiterten IO-Fehlerrücksetzungs-DO-Ports des Laserschweißgeräts hinzugefügt;
       | 19.SetLaserWeldingRunningStateExtDiNum()-Schnittstelle zum Konfigurieren des erweiterten IO-Betriebszustands (Laser an-Status) DI-Ports des Laserschweißgeräts hinzugefügt;
       | 20.SetLaserWeldingErrStateExtDiNum()-Schnittstelle zum Konfigurieren des erweiterten IO-Fehlerstatus-DI-Ports des Laserschweißgeräts hinzugefügt.

   * - V3.9.5
     - 2026-04-24
     - | 1.SetTrajectoryJSpeed()-Schnittstelle fügt die Modi Geschwindigkeitsreduzierung und direkte Umschaltung hinzu;
       | 2.FieldBusSlaveWriteAO()-Schnittstelle ändert den Schreibwerttyp in double, wobei AO0~AO15 ganzzahlig und AO16~AO31 Gleitkommazahlen sind;
       | 3.FieldBusSlaveReadAI()-Schnittstelle ändert den Lesewerttyp in double, wobei AI0~AI15 ganzzahlig und AI16~AI31 Gleitkommazahlen sind;
       | 4.Roboterstatus-Rückmeldungsstrukturtyp aktualisiert;
       | 5.Aufzählungstyp für Roboterstatus-Rückmeldungskonfiguration hinzugefügt;
       | 6.SetRobotRealtimeStateConfig()-Schnittstelle zur Konfiguration der CNDE-Statusrückmeldung des Roboters hinzugefügt;
       | 7.AddRobotRealtimeState()-Schnittstelle zum Hinzufügen eines Roboterstatus zur CNDE-Statuskonfiguration hinzugefügt;
       | 8.DeleteRobotRealtimeState()-Schnittstelle zum Löschen eines Roboterstatus aus der CNDE-Statuskonfiguration hinzugefügt;
       | 9.SetRobotRealtimeStatePeriod()-Schnittstelle zum Festlegen der CNDE-Statusrückmeldeperiode hinzugefügt;
       | 10.GetRobotRealtimeStateConfig()-Schnittstelle zum Abrufen aller aktuellen CNDE-Statusrückmelde-Zustandssätze und der Periode hinzugefügt.

   * - V3.9.4
     - 2026-03-25
     - | 1.ServoJTStart()-Schnittstelle fügt Parameter für Kommunikationstypauswahl hinzu, unterstützt XMLRPC/UDP-Kommunikation;
       | 2.ServoJTEnd()-Schnittstelle fügt Parameter für Kommunikationstypauswahl hinzu, unterstützt XMLRPC/UDP-Kommunikation;
       | 3.ServoJT()-Schnittstelle fügt Parameter für Kommunikationstypauswahl hinzu, unterstützt XMLRPC/UDP-Kommunikation;
       | 4.ServoMoveStart()-Schnittstelle fügt Parameter für Kommunikationstypauswahl hinzu, unterstützt XMLRPC/UDP-Kommunikation;
       | 5.ServoMoveEnd()-Schnittstelle fügt Parameter für Kommunikationstypauswahl hinzu, unterstützt XMLRPC/UDP-Kommunikation;
       | 6.ServoJ()-Schnittstelle fügt Parameter für Kommunikationstypauswahl hinzu, unterstützt XMLRPC/UDP-Kommunikation;
       | 7.SetWeldMachineCtrlMode()-Schnittstelle fügt Parameter für Steuerungsmodusauswahl hinzu;
       | 8.ExtDevGetUDPComParam()-Schnittstelle fügt Möglichkeit hinzu, UDP-Kommunikationsparameter abzurufen: ob nach Neustart des Steuerkastens automatisch neu verbunden wird;
       | 9.Fügt SetAxleGenComEnable()-Schnittstelle hinzu, um die allgemeine Transparentübertragungsfunktion des Endeffektors zu aktivieren;
       | 10.Fügt SndRcvAxleGenComCmdData()-Schnittstelle hinzu, um nichtperiodische Daten vom Endeffektor zu senden und auf Antwort zu warten;
       | 11.Fügt SetRobotStopOnComDisc()-Schnittstelle hinzu, um Roboterbetrieb bei getrennter Port-Kommunikation zu stoppen;
       | 12.Fügt GetRobotStopOnComDisc()-Schnittstelle hinzu, um Parameter für das Stoppen des Roboterbetriebs bei getrennter Port-Kommunikation abzurufen;
       | 13.Fügt SetDIConfig()-Schnittstelle hinzu, um konfigurierbare CI-Portfunktionen des Steuerkastens einzustellen;
       | 14.Fügt GetDIConfig()-Schnittstelle hinzu, um konfigurierbare CI-Portfunktionen des Steuerkastens abzurufen;
       | 15.Fügt SetDOConfig()-Schnittstelle hinzu, um konfigurierbare CO-Portfunktionen des Steuerkastens einzustellen;
       | 16.Fügt GetDOConfig()-Schnittstelle hinzu, um konfigurierbare CO-Portfunktionen des Steuerkastens abzurufen;
       | 17.Fügt SetToolDIConfig()-Schnittstelle hinzu, um konfigurierbare End-CI-Portfunktionen des Endeffektors einzustellen;
       | 18.Fügt GetToolDIConfig()-Schnittstelle hinzu, um konfigurierbare End-CI-Portfunktionen des Endeffektors abzurufen;
       | 19.Fügt SetDIConfigLevel()-Schnittstelle hinzu, um den aktiven Zustand konfigurierbarer CI-Ports des Steuerkastens einzustellen;
       | 20.Fügt GetDIConfigLevel()-Schnittstelle hinzu, um den aktiven Zustand konfigurierbarer CI-Ports des Steuerkastens abzurufen;
       | 21.Fügt SetDOConfigLevel()-Schnittstelle hinzu, um den aktiven Zustand konfigurierbarer CO-Ports des Steuerkastens einzustellen;
       | 22.Fügt GetDOConfigLevel()-Schnittstelle hinzu, um den aktiven Zustand konfigurierbarer CO-Ports des Steuerkastens abzurufen;
       | 23.Fügt SetToolDIConfigLevel()-Schnittstelle hinzu, um den aktiven Zustand konfigurierbarer CI-Ports des Endeffektors einzustellen;
       | 24.Fügt GetToolDIConfigLevel()-Schnittstelle hinzu, um den aktiven Zustand konfigurierbarer CI-Ports des Endeffektors abzurufen;
       | 25.Fügt SetStandardDILevel()-Schnittstelle hinzu, um den aktiven Zustand standardmäßiger DI-Ports des Steuerkastens einzustellen;
       | 26.Fügt GetStandardDILevel()-Schnittstelle hinzu, um den aktiven Zustand standardmäßiger DI-Ports des Steuerkastens abzurufen;
       | 27.Fügt SetStandardDOLevel()-Schnittstelle hinzu, um den aktiven Zustand standardmäßiger DO-Ports des Steuerkastens einzustellen;
       | 28.Fügt GetStandardDOLevel()-Schnittstelle hinzu, um den aktiven Zustand standardmäßiger DO-Ports des Steuerkastens abzurufen;
       | 29.Fügt SetExAxisCmdDoneTimeUDP()-Schnittstelle hinzu, um die Positionierungsabschlusszeit für Erweiterungsachsen einzustellen;
       | 30.Fügt OpenLuaDownload()-Schnittstelle hinzu, um Open-Protocol-Lua-Dateien herunterzuladen;
       | 31.Fügt OpenLuaDelete()-Schnittstelle hinzu, um Open-Protocol-Lua-Dateien zu löschen;
       | 32.Fügt AllOpenLuaDelete()-Schnittstelle hinzu, um Open-Protocol-Lua-Dateien zu löschen;
       | 33.Fügt SendUDPFrameUDP()-Schnittstelle hinzu, um Befehlframes zu senden;
       | 34.Fügt SetCmdRpyCallback()-Schnittstelle hinzu, um Callback-Funktion für Ausführungsergebnisse von über UDP gesendeten SDK-Befehlen einzustellen;
       | 35.Fügt SetVelReducePara()-Schnittstelle hinzu, um Sicherheitsgeschwindigkeitsparameter einzustellen;
       | 36.Fügt OriginPointWeaveStart()-Schnittstelle hinzu, um stationäres Pendeln zu starten;
       | 37.Fügt OriginPointWeaveEnd()-Schnittstelle hinzu, um stationäres Pendeln zu beenden;
       | 38.Fügt SetUserLEDColor()-Schnittstelle hinzu, um benutzerdefinierte LED-Farbe des Roboterendeffektors einzustellen;
       | 39.Fügt MoveToTPDStart()-Schnittstelle hinzu, um zum Startpunkt der TPD-Bahnaufzeichnung zu bewegen;

   * - V3.9.3
     - 2026-02-11
     - | 1. Die Schnittstelle `ServoCart()` wurde um einen Parameter für die Erweiterungsachse ergänzt.
       | 2. Die Schnittstelle `SetOutputResetCtlBoxDO()` wurde um einen Parameter erweitert, der angibt, ob der DO-Zustand vor dem Zurücksetzen nach einer Pausenfortsetzung neu geladen werden soll.
       | 3. Die Schnittstelle `SetOutputResetCtlBoxAO()` wurde um einen Parameter erweitert, der angibt, ob der AO-Zustand vor dem Zurücksetzen nach einer Pausenfortsetzung neu geladen werden soll.
       | 4. Die Schnittstelle `SetOutputResetAxleDO()` wurde um einen Parameter erweitert, der angibt, ob der DO-Zustand vor dem Zurücksetzen nach einer Pausenfortsetzung neu geladen werden soll.
       | 5. Die Schnittstelle `SetOutputResetAxleAO()` wurde um einen Parameter erweitert, der angibt, ob der AO-Zustand vor dem Zurücksetzen nach einer Pausenfortsetzung neu geladen werden soll.
       | 6. Die Schnittstelle `SetOutputResetExtDO()` wurde um einen Parameter erweitert, der angibt, ob der DO-Zustand vor dem Zurücksetzen nach einer Pausenfortsetzung neu geladen werden soll.
       | 7. Die Schnittstelle `SetOutputResetExtAO()` wurde um einen Parameter erweitert, der angibt, ob der AO-Zustand vor dem Zurücksetzen nach einer Pausenfortsetzung neu geladen werden soll.
       | 8. Die Schnittstelle `SetOutputResetSmartToolDO()` wurde um einen Parameter erweitert, der angibt, ob der DO-Zustand vor dem Zurücksetzen nach einer Pausenfortsetzung neu geladen werden soll.
       | 9. Die Schnittstelle `GetInverseKinExaxis()` zur inversen Kinematikberechnung inklusive Erweiterungsachsenposition wurde hinzugefügt.

   * - V3.9.2
     - 2026-01-26
     - | 1. Die Schnittstelle `FT_RotInsertion()` wurde um einen Parameter für die Behandlungsstrategie bei nicht erkannter Kraft/Drehmoment erweitert.
       | 2. Die Schnittstelle `LaserSensorRecordandReplay()` wurde um Parameter für das robotergestützte Punkt-Tracking ergänzt.
       | 3. Die Schnittstelle `MoveStationary()` wurde hinzugefügt.
       | 4. Die Schnittstelle `TCPComputeRPY()` wurde hinzugefügt.
       | 5. Die Schnittstelle `TCPComputeXYZ()` wurde hinzugefügt.
       | 6. Die Schnittstelle `TCPRecordFlangePosStart()` wurde hinzugefügt.
       | 7. Die Schnittstelle `TCPRecordFlangePosEnd()` wurde hinzugefügt.
       | 8. Die Schnittstelle `TCPGetRecordFlangePos()` wurde hinzugefügt.
       | 9. Die Schnittstelle `PhotoelectricSensorTCPCalibration()` wurde hinzugefügt.

   * - V3.9.1
     - 2025-12-25
     - | 1. Die Schnittstelle `MoveL()` wurde um die Parameter `oacc` (Geschwindigkeitsskalierungsfaktor / physikalische Beschleunigung) ergänzt.
       | 2. Die Schnittstelle `MoveC()` wurde um die Parameter `oacc` (Geschwindigkeitsskalierungsfaktor / physikalische Beschleunigung) ergänzt.
       | 3. Die Parameterbeschreibung für `Circle()` hinsichtlich physikalischer Geschwindigkeit und Beschleunigung wurde optimiert.
       | 4. Eine überladene Funktion `FT_Control()` mit Parametern für Startschwelle und Drehmomenteinstellkoeffizienten für rx, ry wurde hinzugefügt.
       | 5. Die Schnittstelle `SerCoderCompenParams()` wurde hinzugefügt.

   * - V3.9.0
     - 2025-11-26
     - | 1. Die Schnittstelle `JointSensitivityCalibration()` gibt jetzt zusätzlich die Linearität der Gelenke J1~J6 zurück.
       | 2. Die Schnittstelle `JointHysteresisError()` wurde hinzugefügt.
       | 3. Die Schnittstelle `JointRepeatability()` wurde hinzugefügt.
       | 4. Die Schnittstelle `SetAdmittanceParams()` wurde hinzugefügt.
       | 5. Die Schnittstelle `MoveToIntersectLineStart()` wurde hinzugefügt.
       | 6. Die Schnittstelle `MoveIntersectLine()` wurde hinzügegefügt.

   * - V3.8.7
     - 2025-10-21
     - | 1. `FT_Control()` wurde um Schnittstellen für Massen- und Dämpfungsparameter erweitert.
       | 2. Die Schnittstelle `JointSensitivityCalibration()` wurde hinzugefügt.
       | 3. Die Schnittstelle `JointSensitivityCollect()` wurde hinzugefügt.
       | 4. Die Schnittstelle `MotionQueueClear()` wurde hinzugefügt.
       | 5. Die Schnittstelle `GetSlavePortErrCounter()` wurde hinzugefügt.
       | 6. Die Schnittstelle `SlavePortErrCounterClear()` wurde hinzugefügt.
       | 7. Die Schnittstelle `SetVelFeedForwardRatio()` wurde hinzugefügt.
       | 8. Die Schnittstelle `GetVelFeedForwardRatio()` wurde hinzugefügt.
       | 9. Die Schnittstelle `RobotMCULogCollect()` wurde hinzugefügt.
       | 10. Der Statusstruktur wurden ein Zähler für ServoJ-Befehle und die Zielposition des letzten Befehls hinzugefügt.
       | 11. Der Parameterstruktur `SpiralParam` für die neue Spirale wurde ein Modus für Geschwindigkeit/Beschleunigung hinzugefügt.

   * - V3.8.6
     - 2025-09-19
     - | 1. Die Schnittstelle `SetLoadCoord()` wurde um einen Parameter für die Nutzlastnummer erweitert.
       | 2. Die Schnittstelle `LaserTrackingLaserOnOff()` wurde hinzugefügt.
       | 3. Die Schnittstelle `LaserTrackingTrackOnOff()` wurde hinzugefügt.
       | 4. Die Schnittstelle `LaserTrackingSearchStart_xyz()` wurde hinzugefügt.
       | 5. Die Schnittstelle `LaserTrackingSearchStart_point()` wurde hinzugefügt.
       | 6. Die Schnittstelle `LaserTrackingSearchStop()` wurde hinzugefügt.
       | 7. Die Schnittstelle `LaserTrackingSensorConfig()` wurde hinzugefügt.
       | 8. Die Schnittstelle `LaserTrackingSensorSamplePeriod()` wurde hinzugefügt.
       | 9. Die Schnittstelle `LoadPosSensorDriver()` wurde hinzugefügt.
       | 10. Die Schnittstelle `UnLoadPosSensorDriver()` wurde hinzugefügt.
       | 11. Die Schnittstelle `LaserSensorRecord1()` wurde hinzugefügt.
       | 12. Die Schnittstelle `LaserSensorReplay()` wurde hinzugefügt.
       | 13. Die Schnittstelle `MoveLTR()` wurde hinzugefügt.
       | 14. Die Schnittstelle `LaserSensorRecordandReplay()` wurde hinzugefügt.
       | 15. Die Schnittstelle `MoveToLaserRecordStart()` wurde hinzugefügt.
       | 16. Die Schnittstelle `MoveToLaserRecordEnd()` wurde hinzugefügt.
       | 17. Die Schnittstelle `MoveToLaserSeamPos()` wurde hinzugefügt.
       | 18. Die Schnittstelle `GetLaserSeamPos()` wurde hinzugefügt.
       | 19. Die Schnittstelle `ImpedanceControlStartStop()` wurde hinzugefügt.
       | 20. Die Schnittstelle `GetToolCoordWithID()` wurde hinzugefügt.
       | 21. Die Schnittstelle `GetWObjCoordWithID()` wurde hinzugefügt.
       | 22. Die Schnittstelle `GetExToolCoordWithID()` wurde hinzugefügt.
       | 23. Die Schnittstelle `GetExAxisCoordWithID()` wurde hinzugefügt.
       | 24. Die Schnittstelle `GetTargetPayloadWithID()` wurde hinzugefügt.
       | 25. Die Schnittstelle `GetCurToolCoord()` wurde hinzugefügt.
       | 26. Die Schnittstelle `GetCurWObjCoord()` wurde hinzugefügt.
       | 27. Die Schnittstelle `GetCurExToolCoord()` wurde hinzugefügt.
       | 28. Die Schnittstelle `GetCurExAxisCoord()` wurde hinzugefügt.
       | 29. Die Schnittstelle `KernelUpgrade()` wurde hinzugefügt.
       | 30. Die Schnittstelle `GetKernelUpgradeResult()` wurde hinzugefügt.
       | 31. Die Schnittstelle `CustomWeaveSetPara()` wurde hinzugefügt.
       | 32. Die Schnittstelle `CustomWeaveGetPara()` wurde hinzugefügt.
       | 33. Der Statusstruktur wurden Daten zu Werkzeug-, Werkstück-, externem Werkzeug-, Erweiterungsachsen-Koordinatensystem sowie Nutzlastmasse und -schwerpunkt hinzugefügt.

   * - V3.8.5
     - 2025-08-20
     - | 1. Den Befehlen `MoveL()`, `MoveC()` und `Circle()` wurde der Parameter `velAccParamMode` hinzugefügt.
       | 2. Schnittstellen für automatische Vorwärtskinematikberechnung für `MoveJ()`, `SplinePTP()` und `ExtAxisSyncMoveJ()` wurden hinzugefügt.
       | 3. `LoadTrajectoryLA()` wurde um einen Parameter zum Aktivieren des Vorausschau-Schalters bei konstanter Geschwindigkeit erweitert.
       | 4. Schnittstellen für automatische inverse Kinematikberechnung für `MoveL()`, `MoveC()`, `Circle()`, `NewSplinePoint()`, `NewSpiral()`, `ExtAxisSyncMoveL()` und `ExtAxisSyncMoveC()` wurden hinzugefügt.
       | 5. Saugnapfsteuerungsschnittstellen `SetSuckerCtrl()`, `GetSuckerState()`, `WaitSuckerState()` und die Schnittstelle für die Synchronisationsstrategie `SetExAxisRobotPlan()` wurden hinzugefügt.
       | 6. Steuerungsbefehle für den Roboterslave-Modus wie `OpenLuaUpload()`, `GetFieldBusConfig()`, `FieldBusSlaveWriteDO()`, `FieldBusSlaveWriteAO()`, `FieldBusSlaveReadDI()`, `FieldBusSlaveReadAI()`, `FieldBusSlaveWaitDI()` und `FieldBusSlaveWaitAI()` wurden hinzugefügt.

   * - V3.8.4
     - 2025-07-17
     - | 1. Die Schnittstelle `ExtAxisMove()` wurde um den Glättungsparameter `blend` erweitert.
       | 2. Die Schnittstelle `SetFocusCalibPoint()` wurde hinzugefügt.
       | 3. Die Schnittstelle `ComputeFocusCalib()` wurde hinzugefügt.
       | 4. Die Schnittstelle `SetFocusPosition()` wurde hinzugefügt.
       | 5. Die Schnittstelle `FocusStart()` wurde hinzugefügt.
       | 6. Die Schnittstelle `FocusEnd()` wurde hinzugefügt.
       | 7. Die Schnittstelle `SetJointFirmwareUpgrade()` wurde hinzugefügt.
       | 8. Die Schnittstelle `SetCtrlFirmwareUpgrade()` wurde hinzugefügt.
       | 9. Die Schnittstelle `SetEndFirmwareUpgrade()` wurde hinzugefügt.
       | 10. Die Schnittstelle `JointAllParamUpgrade()` wurde hinzugefügt.

   * - V3.8.3
     - 2025-06-24
     - | 1. Die Schnittstelle `Circle()` wurde um Parameter für Beschleunigungsprozentsatz und Glättungsradius erweitert.
       | 2. Die Schnittstelle `EndForceDragControl()` wurde um einen Parameter für die Kollisionserkennung während des unterstützten Ziehens erweitert.
       | 3. Die Schnittstelle `ServoJ()` wurde um einen Befehl-ID-Parameter erweitert.
       | 4. Die Schnittstelle `SetWideBoxTempFanMonitorParam()` wurde hinzugefügt.
       | 5. Die Schnittstelle `GetWideBoxTempFanMonitorParam()` wurde hinzugefügt.
       | 6. Der Statusstruktur wurden Daten zur Steuerschranktemperatur und zum Lüfterstrom hinzugefügt.

   * - V3.8.2
     - 2025-06-13
     - | 1. Die Schnittstelle `WeaveSetPara()` wurde um einen Parameter für den Rollwinkel der Pendelrichtung (Neigung um Pendel-X-Achse) erweitert.
       | 2. Die Schnittstelle `WeaveChangeStart()` wurde um Parameter für Pendelnummer, Schweißstartgeschwindigkeit und Schweißendgeschwindigkeit erweitert.
       | 3. Die Schnittstelle `ExtDevSetUDPComParam()` wurde um einen Parameter ergänzt, der angibt, ob nach einem Neustart automatisch eine Verbindung hergestellt werden soll.
       | 4. Die Schnittstelle `SetCollisionDetectionMethod()` wurde um eine Auswahl für die Art des Kollisionsstufen-Schwellwerts erweitert.
       | 5. Die Schnittstelle `PtpFIRPlanningStart()` wurde um einen Parameter für den maximalen einheitlichen Gelenkruck erweitert.
       | 6. Die Schnittstelle `WeldingSetVoltageGradualChangeStart()` wurde hinzugefügt.
       | 7. Die Schnittstelle `WeldingSetVoltageGradualChangeEnd()` wurde hinzugefügt.
       | 8. Die Schnittstelle `WeldingSetCurrentGradualChangeStart()` wurde hinzugefügt.
       | 9. Die Schnittstelle `WeldingSetCurrentGradualChangeEnd()` wurde hinzugefügt.
       | 10. Die Schnittstelle `ArcWeldTraceAIChannelCurrent()` wurde hinzugefügt.
       | 11. Die Schnittstelle `ArcWeldTraceAIChannelVoltage()` wurde hinzugefügt.
       | 12. Die Schnittstelle `ArcWeldTraceCurrentPara()` wurde hinzugefügt.
       | 13. Die Schnittstelle `ArcWeldTraceVoltagePara()` wurde hinzugefügt.
       | 14. Die Schnittstelle `GetSmarttoolBtnState()` wurde hinzugefügt.
       | 15. Die Schnittstelle `ExtAxisGetCoord()` wurde hinzugefügt.

   * - V3.8.1
     - 2025-04-24
     - | 1. Die Schnittstelle `ConveyorSetParam()` wurde um Parameter für den Tracking-Bewegungstyp, die Start- und die Endverfolgungsdistanz erweitert.
       | 2. Die Schnittstelle `AccSmoothStart()` wurde hinzugefügt.
       | 3. Die Schnittstelle `AccSmoothEnd()` wurde hinzugefügt.
       | 4. Die Schnittstelle `RbLogDownload()` wurde hinzugefügt.
       | 5. Die Schnittstelle `AllDataSourceDownload()` wurde hinzugefügt.
       | 6. Die Schnittstelle `DataPackageDownload()` wurde hinzugefügt.
       | 7. Die Schnittstelle `GetRobotSN()` wurde hinzugefügt.
       | 8. Die Schnittstelle `ShutDownRobotOS()` wurde hinzugefügt.
       | 9. Die Schnittstelle `ConveyorComDetect()` wurde hinzugefügt.
       | 10. Die Schnittstelle `ConveyorComDetectTrigger()` wurde hinzugefügt.

   * - V3.8.0
     - 2025-02-12
     - | 1. Die Schnittstelle `EndForceDragControl()` wurde um einen Parameter zur Singularitätsvermeidung erweitert.
       | 2. Die Schnittstelle `ArcWeldTraceControl()` wurde um einen Versatzparameter erweitert.
       | 3. Die Schnittstelle `WeaveChangeStart()` wurde hinzugefügt.
       | 4. Die Schnittstelle `WeaveChangeEnd()` wurde hinzugefügt.
       | 5. Die Schnittstelle `LoadTrajectoryLA()` wurde hinzugefügt.
       | 6. Die Schnittstelle `MoveTrajectoryLA()` wurde hinzugefügt.
       | 7. Die Schnittstelle `CustomCollisionDetectionStart()` wurde hinzugefügt.
       | 8. Die Schnittstelle `CustomCollisionDetectionEnd()` wurde hinzugefügt.