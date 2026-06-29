Versionshinweise
================

.. toctree::
    :maxdepth: 5

.. list-table::
   :widths: 10 10 30
   :header-rows: 0
   :align: center

   * - **Version**
     - **Datum**
     - **Aktualisierungsbeschreibung**

   * - V3.9.7
     - 2026-06-25
     - | 1. PhotoelectricSensorTCPCalibration()-Parameter können sich jetzt an Dateinamen ohne Pfad anpassen;
       | 2. LoadTrajectoryJ()-Parameter können sich jetzt an Dateinamen ohne Pfad anpassen;
       | 3. LoadTrajectoryLA()-Parameter können sich jetzt an Dateinamen ohne Pfad anpassen;
       | 4. LoadDefaultProgConfig()-Parameter können sich jetzt an Dateinamen ohne Pfad anpassen;
       | 5. ProgramLoad()-Parameter können sich jetzt an Dateinamen ohne Pfad anpassen;
       | 6. Aktivierungsstatus-Parameter für dreifingrige Hand zur SetAxleLuaEnableDeviceType()-Schnittstelle hinzugefügt;
       | 7. Aktivierungsstatus-Parameter für dreifingrige Hand zur GetAxleLuaEnableDeviceType()-Schnittstelle hinzugefügt;
       | 8. Schnittstellen zum Abrufen der aktuell konfigurierten Endeffektor-Geräteaktivierungstypen und der Greifer-Aktionssteuerung modifiziert;
       | 9. Aktivierung und Funktionscodes für dreifingrige Hand hinzugefügt;
       | 10. SetDexterousHandsMove()-Schnittstelle zur Steuerung der Bewegung der dreifingrigen Hand hinzugefügt;
       | 11. SetDexterousHandsAct()-Schnittstelle zur Steuerung des Resets und der Aktivierung der dreifingrigen Hand hinzugefügt;
       | 12. ClearDexterousHandsError()-Schnittstelle zum Löschen von Fehlern der dreifingrigen Hand hinzugefügt;
       | 13. SetDexterousHandsFunc()-Schnittstelle zum Festlegen der aktivierten Aktionssteuerungsfunktionen der dreifingrigen Hand hinzugefügt;
       | 14. GetDexterousHandsFunc()-Schnittstelle zum Abrufen der aktivierten Aktionssteuerungsfunktionen der dreifingrigen Hand hinzugefügt;
       | 15. Schnittstellen zum Einstellen und Abrufen der Parameter für die Rückkehr zum Zyklus-Nullpunkt nach Pendelende hinzugefügt;
       | 16. SetWeaveOffsetRT()-Schnittstelle zum Einstellen des Echtzeit-Pendeloffsets und SetSpeedInstant()-Schnittstelle zur Echtzeit-Geschwindigkeitseinstellung hinzugefügt.

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
       | 2.Roboterstatus-Rückmeldungsstrukturtyp aktualisiert;
       | 3.Aufzählungstyp für Roboterstatus-Rückmeldungskonfiguration hinzugefügt;
       | 4.Klasse für Roboterstatus-Rückmeldungskonfigurationsergebnis hinzugefügt;
       | 5.SetRobotRealtimeStateConfig()-Schnittstelle zur Konfiguration der CNDE-Statusrückmeldung des Roboters hinzugefügt;
       | 6.AddRobotRealtimeState()-Schnittstelle zum Hinzufügen eines Roboterstatus zur CNDE-Statuskonfiguration hinzugefügt;
       | 7.DeleteRobotRealtimeState()-Schnittstelle zum Löschen eines Roboterstatus aus der CNDE-Statuskonfiguration hinzugefügt;
       | 8.SetRobotRealtimeStatePeriod()-Schnittstelle zum Festlegen der CNDE-Statusrückmeldeperiode hinzugefügt;
       | 9.GetRobotRealtimeStateConfig()-Schnittstelle zum Abrufen aller aktuellen CNDE-Statusrückmelde-Zustandssätze und der Periode hinzugefügt.

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
     - | 1. Der Schnittstelle ServoCart() wurde ein Parameter für Erweiterungsachsen hinzugefügt.
       | 2. Der Schnittstelle SetOutputResetCtlBoxDO() wurde ein Parameter hinzugefügt, der angibt, ob der DO-Status vor dem Zurücksetzen nach einer Pausenfortsetzung wiederhergestellt werden soll.
       | 3. Der Schnittstelle SetOutputResetCtlBoxAO() wurde ein Parameter hinzugefügt, der angibt, ob der AO-Status vor dem Zurücksetzen nach einer Pausenfortsetzung wiederhergestellt werden soll.
       | 4. Der Schnittstelle SetOutputResetAxleDO() wurde ein Parameter hinzugefügt, der angibt, ob der DO-Status vor dem Zurücksetzen nach einer Pausenfortsetzung wiederhergestellt werden soll.
       | 5. Der Schnittstelle SetOutputResetAxleAO() wurde ein Parameter hinzugefügt, der angibt, ob der AO-Status vor dem Zurücksetzen nach einer Pausenfortsetzung wiederhergestellt werden soll.
       | 6. Der Schnittstelle SetOutputResetExtDO() wurde ein Parameter hinzugefügt, der angibt, ob der DO-Status vor dem Zurücksetzen nach einer Pausenfortsetzung wiederhergestellt werden soll.
       | 7. Der Schnittstelle SetOutputResetExtAO() wurde ein Parameter hinzugefügt, der angibt, ob der AO-Status vor dem Zurücksetzen nach einer Pausenfortsetzung wiederhergestellt werden soll.
       | 8. Der Schnittstelle SetOutputResetSmartToolDO() wurde ein Parameter hinzugefügt, der angibt, ob der DO-Status vor dem Zurücksetzen nach einer Pausenfortsetzung wiederhergestellt werden soll.
       | 9. Die Schnittstelle GetInverseKinExaxis() zur Lösung der inversen Kinematik unter Einbeziehung der Position von Erweiterungsachsen wurde hinzugefügt.
       
   * - V3.9.2
     - 2026-01-26
     - | 1. Der Schnittstelle FT_RotInsertion() wurde ein Parameter für die Strategie bei fehlender Kraft-/Momentenerkennung hinzugefügt.
       | 2. Der Schnittstelle LaserSensorRecordandReplay() wurden Parameter für das robotergestützte Punkt-Tracking hinzugefügt.
       | 3. Die Schnittstelle MoveStationary() wurde hinzugefügt.
       | 4. Die Schnittstelle TCPComputeRPY() wurde hinzugefügt.
       | 5. Die Schnittstelle TCPComputeXYZ() wurde hinzugefügt.
       | 6. Die Schnittstelle TCPRecordFlangePosStart() wurde hinzugefügt.
       | 7. Die Schnittstelle TCPRecordFlangePosEnd() wurde hinzugefügt.
       | 8. Die Schnittstelle TCPGetRecordFlangePos() wurde hinzugefügt.
       | 9. Die Schnittstelle PhotoelectricSensorTCPCalibration() wurde hinzugefügt.

   * - V3.9.1
     - 2025-12-25
     - | 1. Der Schnittstelle MoveL() wurden Parameter für den Beschleunigungsskalierungsfaktor (oacc) und die physikalische Beschleunigung hinzugefügt.
       | 2. Der Schnittstelle MoveC() wurden Parameter für den Beschleunigungsskalierungsfaktor (oacc) und die physikalische Beschleunigung hinzugefügt.
       | 3. Die Parameterbeschreibung für physikalische Geschwindigkeit und Beschleunigung in der Circle()-Schnittstelle wurde optimiert.
       | 4. Eine überladene FT_Control()-Funktion mit Parametern für den Startschwellwert von rx, ry und den Momentenanpassungskoeffizienten wurde hinzugefügt.
       | 5. Die Schnittstelle SerCoderCompenParams() wurde hinzugefügt.
       
   * - V3.9.0
     - 2025-11-26
     - | 1. Der Schnittstelle JointSensitivityCalibration() wurde die Rückgabe der Linearität der Gelenke J1~J6 hinzugefügt.
       | 2. Die Schnittstelle JointHysteresisError() wurde hinzugefügt.
       | 3. Die Schnittstelle JointRepeatability() wurde hinzugefügt.
       | 4. Die Schnittstelle SetAdmittanceParams() wurde hinzugefügt.
       | 5. Die Schnittstelle MoveToIntersectLineStart() wurde hinzugefügt.
       | 6. Die Schnittstelle MoveIntersectLine() wurde hinzugefügt.
       
   * - V3.8.7
     - 2025-10-21
     - | 1. Der Schnittstelle FT_Control() wurden Schnittstellen für Massen- und Dämpfungsparameter hinzugefügt.
       | 2. Die Schnittstelle JointSensitivityCalibration() wurde hinzugefügt.
       | 3. Die Schnittstelle JointSensitivityCollect() wurde hinzugefügt.
       | 4. Die Schnittstelle MotionQueueClear() wurde hinzugefügt.
       | 5. Die Schnittstelle GetSlavePortErrCounter() wurde hinzugefügt.
       | 6. Die Schnittstelle SlavePortErrCounterClear() wurde hinzugefügt.
       | 7. Die Schnittstelle SetVelFeedForwardRatio() wurde hinzugefügt.
       | 8. Die Schnittstelle GetVelFeedForwardRatio() wurde hinzugefügt.
       | 9. Die Schnittstelle RobotMCULogCollect() wurde hinzugefügt.
       | 10. Dem Statusstruktur wurden der ServoJ-Befehlszähler und die Daten der letzten Zielposition eines Befehls hinzugefügt.
       | 11. Der SpiralParam-Struktur für neue Spiralbewegungen wurde ein Modus für Geschwindigkeits-/Beschleunigungsparameter hinzugefügt.

   * - V3.8.6
     - 2025-09-19
     - | 1. Der Schnittstelle SetLoadCoord() wurde ein Parameter für die Lastnummer hinzugefügt.
       | 2. Die Schnittstelle LaserTrackingLaserOnOff() wurde hinzugefügt.
       | 3. Die Schnittstelle LaserTrackingTrackOnOff() wurde hinzugefügt.
       | 4. Die Schnittstelle LaserTrackingSearchStart_xyz() wurde hinzugefügt.
       | 5. Die Schnittstelle LaserTrackingSearchStart_point() wurde hinzugefügt.
       | 6. Die Schnittstelle LaserTrackingSearchStop() wurde hinzugefügt.
       | 7. Die Schnittstelle LaserTrackingSensorConfig() wurde hinzugefügt.
       | 8. Die Schnittstelle LaserTrackingSensorSamplePeriod() wurde hinzugefügt.
       | 9. Die Schnittstelle LoadPosSensorDriver() wurde hinzugefügt.
       | 10. Die Schnittstelle UnLoadPosSensorDriver() wurde hinzugefügt.
       | 11. Die Schnittstelle LaserSensorRecord1() wurde hinzugefügt.
       | 12. Die Schnittstelle LaserSensorReplay() wurde hinzugefügt.
       | 13. Die Schnittstelle MoveLTR() wurde hinzugefügt.
       | 14. Die Schnittstelle LaserSensorRecordandReplay() wurde hinzugefügt.
       | 15. Die Schnittstelle MoveToLaserRecordStart() wurde hinzugefügt.
       | 16. Die Schnittstelle MoveToLaserRecordEnd() wurde hinzugefügt.
       | 17. Die Schnittstelle MoveToLaserSeamPos() wurde hinzugefügt.
       | 18. Die Schnittstelle GetLaserSeamPos() wurde hinzugefügt.
       | 19. Die Schnittstelle ImpedanceControlStartStop() wurde hinzugefügt.
       | 20. Die Schnittstelle GetToolCoordWithID() wurde hinzugefügt.
       | 21. Die Schnittstelle GetWObjCoordWithID() wurde hinzugefügt.
       | 22. Die Schnittstelle GetExToolCoordWithID() wurde hinzugefügt.
       | 23. Die Schnittstelle GetExAxisCoordWithID() wurde hinzugefügt.
       | 24. Die Schnittstelle GetTargetPayloadWithID() wurde hinzugefügt.
       | 25. Die Schnittstelle GetExAxisCoordWithID() (doppelt) wurde hinzugefügt.
       | 26. Die Schnittstelle GetCurWObjCoord() wurde hinzugefügt.
       | 27. Die Schnittstelle GetCurExToolCoord() wurde hinzugefügt.
       | 28. Die Schnittstelle GetCurExToolCoord() (doppelt) wurde hinzugefügt.
       | 29. Die Schnittstelle KernelUpgrade() wurde hinzugefügt.
       | 30. Die Schnittstelle GetKernelUpgradeResult() wurde hinzugefügt.
       | 31. Die Schnittstelle CustomWeaveSetPara() wurde hinzugefügt.
       | 32. Die Schnittstelle CustomWeaveGetPara() wurde hinzugefügt.
       | 33. Dem Statusstruktur wurden Daten zu Werkzeug-, Werkstück-, externen Werkzeug- und Erweiterungsachsen-Koordinatensystemen sowie zu Lastmasse und -schwerpunkt hinzugefügt.

   * - V3.8.5
     - 2025-08-20
     - | 1. Die Schnittstelle OpenLuaUpload() wurde hinzugefügt.
       | 2. Die Schnittstelle GetFieldBusConfig() wurde hinzugefügt.
       | 3. Die Schnittstelle FieldBusSlaveWriteDO() wurde hinzugefügt.
       | 4. Die Schnittstelle FieldBusSlaveWriteAO() wurde hinzugefügt.
       | 5. Die Schnittstelle FieldBusSlaveReadDI() wurde hinzugefügt.
       | 6. Die Schnittstelle FieldBusSlaveReadAI() wurde hinzugefügt.
       | 7. Die Schnittstelle FieldBusSlaveWaitDI() wurde hinzugefügt.
       | 8. Die Schnittstelle FieldBusSlaveWaitAI() wurde hinzugefügt.
       | 9. Die Schnittstelle SetSuckerCtrl() wurde hinzugefügt.
       | 10. Die Schnittstelle GetSuckerState() wurde hinzugefügt.
       | 11. Die Schnittstelle WaitSuckerState() wurde hinzugefügt.
       | 12. Der Schnittstelle MoveL() wurde ein Modus für Geschwindigkeits-/Beschleunigungsparameter (velAccParamMode) hinzugefügt.
       | 13. Eine überladene Funktion MoveL() (Überladung 1) wurde hinzugefügt.
       | 14. Eine überladene Funktion MoveL() (Überladung 2) wurde hinzugefügt.
       | 15. Der Schnittstelle MoveC() wurde ein Modus für Geschwindigkeits-/Beschleunigungsparameter (velAccParamMode) hinzugefügt.
       | 16. Eine überladene Funktion MoveC() (Überladung 1) wurde hinzugefügt.
       | 17. Der Schnittstelle Circle() wurde ein Modus für Geschwindigkeits-/Beschleunigungsparameter (velAccParamMode) hinzugefügt.
       | 18. Eine überladene Funktion Circle() (Überladung 1) wurde hinzugefügt.
       | 19. Die Schnittstelle SetExAxisRobotPlan() wurde hinzugefügt.

   * - V3.8.4
     - 2025-07-17
     - | 1. Der Schnittstelle ExtAxisMove() wurde der Glättungsparameter 'blend' hinzugefügt.
       | 2. Die Schnittstelle SetFocusCalibPoint() wurde hinzugefügt.
       | 3. Die Schnittstelle ComputeFocusCalib() wurde hinzugefügt.
       | 4. Die Schnittstelle FocusStart() wurde hinzugefügt.
       | 5. Die Schnittstelle FocusEnd() wurde hinzugefügt.
       | 6. Die Schnittstelle SetFocusPosition() wurde hinzugefügt.
       | 7. Die Schnittstelle SetEncoderUpgrade() wurde hinzugefügt.
       | 8. Die Schnittstelle SetJointFirmwareUpgrade() wurde hinzugefügt.
       | 9. Die Schnittstelle SetCtrlFirmwareUpgrade() wurde hinzugefügt.
       | 10. Die Schnittstelle SetEndFirmwareUpgrade() wurde hinzugefügt.
       | 11. Die Schnittstelle JointAllParamUpgrade() wurde hinzugefügt.
       
   * - V3.8.3
     - 2025-06-24
     - | 1. Der Schnittstelle Circle() wurden Parameter für den Beschleunigungsprozentsatz und den Glättungsradius hinzugefügt.
       | 2. Der Schnittstelle EndForceDragControl() wurde ein Parameter für die Kollisionserkennung während der unterstützten Führung hinzugefügt.
       | 3. Der Schnittstelle ServoJ() wurde ein Parameter für die Befehls-ID hinzugefügt.
       | 4. Die Schnittstelle SetSSHScpCmd() wurde hinzugefügt.
       | 5. Die Schnittstelle SetWideBoxTempFanMonitorParam() wurde hinzugefügt.
       | 6. Die Schnittstelle GetWideBoxTempFanMonitorParam() wurde hinzugefügt.
       | 7. Dem Statusstruktur wurden Daten zur Steuerkastentemperatur und zum Lüfterstrom hinzugefügt.
              
   * - V3.8.2
     - 2025-06-13
     - | 1. Der Schnittstelle WeaveSetPara() wurde ein Parameter für den Seitneigungswinkel der Pendelrichtung (Rotation um die Pendel-X-Achse) hinzugefügt.
       | 2. Der Schnittstelle WeaveChangeStart() wurden Parameter für die Pendelnummer, die Start-Schweißgeschwindigkeit und die End-Schweißgeschwindigkeit hinzugefügt.
       | 3. Der Schnittstelle ExtDevSetUDPComParam() wurde ein Parameter für den automatischen Verbindungsaufbau nach einem Neustart hinzugefügt.
       | 4. Der Schnittstelle SetCollisionDetectionMethod() wurde eine Auswahl für die Art des Kollisionsstufen-Schwellwerts hinzugefügt.
       | 5. Der Schnittstelle PtpFIRPlanningStart() wurde ein Parameter für den maximalen Gelenkruck hinzugefügt.
       | 6. Die Schnittstelle WeldingSetVoltageGradualChangeStart() wurde hinzugefügt.
       | 7. Die Schnittstelle WeldingSetVoltageGradualChangeEnd() wurde hinzugefügt.
       | 8. Die Schnittstelle WeldingSetCurrentGradualChangeStart() wurde hinzugefügt.
       | 9. Die Schnittstelle WeldingSetCurrentGradualChangeEnd() wurde hinzugefügt.
       | 10. Die Schnittstelle ArcWeldTraceAIChannelCurrent() wurde hinzugefügt.
       | 11. Die Schnittstelle ArcWeldTraceAIChannelVoltage() wurde hinzugefügt.
       | 12. Die Schnittstelle ArcWeldTraceCurrentPara() wurde hinzugefügt.
       | 13. Die Schnittstelle ArcWeldTraceVoltagePara() wurde hinzugefügt.
       | 14. Die Schnittstelle GetSmarttoolBtnState() wurde hinzugefügt.
       | 15. Die Schnittstelle ExtAxisGetCoord() wurde hinzugefügt.
                     
   * - V3.8.1
     - 2025-04-24
     - | 1. Der Schnittstelle ConveyorSetParam() wurden Parameter für den Tracking-Bewegungstyp, den Startabstand und den Endabstand des Trackings hinzugefügt.
       | 2. Die Schnittstelle AccSmoothStart() wurde hinzugefügt.
       | 3. Die Schnittstelle AccSmoothEnd() wurde hinzugefügt.
       | 4. Die Schnittstelle RbLogDownload() wurde hinzugefügt.
       | 5. Die Schnittstelle AllDataSourceDownload() wurde hinzugefügt.
       | 6. Die Schnittstelle DataPackageDownload() wurde hinzugefügt.
       | 7. Die Schnittstelle GetRobotSN() wurde hinzugefügt.
       | 8. Die Schnittstelle ShutDownRobotOS() wurde hinzugefügt.
       | 9. Die Schnittstelle ConveyorComDetect() wurde hinzugefügt.
       | 10. Die Schnittstelle ConveyorComDetectTrigger() wurde hinzugefügt.