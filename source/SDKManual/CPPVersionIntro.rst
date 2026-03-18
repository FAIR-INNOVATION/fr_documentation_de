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