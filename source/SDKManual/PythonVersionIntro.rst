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
     - | 1. Der Schnittstelle NewSpiral() wurde der Parameter velAccMode hinzugefügt.
       | 2. Der Schnittstelle FT_Control() wurden Schnittstellen für Massen- und Dämpfungsparameter hinzugefügt.
       | 3. Die Schnittstelle JointSensitivityCalibration() wurde hinzugefügt.
       | 4. Die Schnittstelle JointSensitivityCollect() wurde hinzugefügt.
       | 5. Die Schnittstelle MotionQueueClear() wurde hinzugefügt.
       | 6. Die Schnittstelle GetSlavePortErrCounter() wurde hinzugefügt.
       | 7. Die Schnittstelle SlavePortErrCounterClear() wurde hinzugefügt.
       | 8. Die Schnittstelle SetVelFeedForwardRatio() wurde hinzugefügt.
       | 9. Die Schnittstelle GetVelFeedForwardRatio() wurde hinzugefügt.
       | 10. Die Schnittstelle RobotMCULogCollect() wurde hinzugefügt.
       | 11. Dem Statusstruktur wurden die letzte ServoJ-Zielposition in der Warteschlange und der ServoJ-Befehlszähler hinzugefügt.

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
     - | 1. Der Schnittstelle MoveL() wurden der inverse Kinematik-Parameter 'config' und der Parameter 'velAccParamMode' hinzugefügt.
       | 2. Der Schnittstelle MoveC() wurden der inverse Kinematik-Parameter 'config' und der Parameter 'velAccParamMode' hinzugefügt.
       | 3. Der Schnittstelle Circle() wurden der inverse Kinematik-Parameter 'config' und der Parameter 'velAccParamMode' hinzugefügt.
       | 4. Der Schnittstelle NewSpiral() wurde der inverse Kinematik-Parameter 'config' hinzugefügt.
       | 5. Der Schnittstelle NewSplinePoint() wurde der inverse Kinematik-Parameter 'config' hinzugefügt.
       | 6. Der Schnittstelle ExtAxisSyncMoveJ() wurde der inverse Kinematik-Parameter 'config' hinzugefügt.
       | 7. Der Schnittstelle ExtAxisSyncMoveL() wurde der inverse Kinematik-Parameter 'config' hinzugefügt.
       | 8. Der Schnittstelle ExtAxisSyncMoveC() wurde der inverse Kinematik-Parameter 'config' hinzugefügt.
       | 9. Die neue Schnittstelle LaserRecordPoint(coordID) wurde hinzugefügt.
       | 10. Die neue Schnittstelle SetExAxisRobotPlan(strategy) wurde hinzugefügt.
       | 11. Die neue Schnittstelle OpenLuaUpload(filePath) wurde hinzugefügt.
       | 12. Die neue Schnittstelle GetFieldBusConfig() wurde hinzugefügt.
       | 13. Die neue Schnittstelle FieldBusSlaveWriteDO(DOIndex, wirteNum, status) wurde hinzugefügt.
       | 14. Die neue Schnittstelle FieldBusSlaveWriteAO(AOIndex, wirteNum, status) wurde hinzugefügt.
       | 15. Die neue Schnittstelle FieldBusSlaveReadDI(DOIndex, readeNum) wurde hinzugefügt.
       | 16. Die neue Schnittstelle FieldBusSlaveReadAI(AOIndex, readeNum) wurde hinzugefügt.
       | 17. Die neue Schnittstelle FieldBusSlaveWaitDI(DIIndex, status, waitMs) wurde hinzugefügt.
       | 18. Die neue Schnittstelle FieldBusSlaveWaitAI(AIIndex, waitType, value, waitMs) wurde hinzugefügt.
       | 19. Die neue Schnittstelle SetSuckerCtrl(slaveID, len, ctrlValue) wurde hinzugefügt.
       | 20. Die neue Schnittstelle GetSuckerState(slaveID) wurde hinzugefügt.
       | 21. Die neue Schnittstelle WaitSuckerState(slaveID, state, ms) wurde hinzugefügt.

   * - V3.8.4
     - 2025-07-17
     - | 1. Der Schnittstelle ExtAxisMove() wurde der Glättungsparameter 'blend' hinzugefügt.
       | 2. Die Schnittstelle SetFocusCalibPoint(pointNum, point) wurde hinzugefügt.
       | 3. Die Schnittstelle ComputeFocusCalib(pointNum) wurde hinzugefügt.
       | 4. Die Schnittstelle FocusStart(kp, kpredic, aMax, vMax, type) wurde hinzugefügt.
       | 5. Die Schnittstelle FocusEnd() wurde hinzugefügt.
       | 6. Die Schnittstelle SetFocusPosition(pos) wurde hinzugefügt.
       | 7. Die Schnittstelle SetEncoderUpgrade(path) wurde hinzugefügt.
       | 8. Die Schnittstelle SetJointFirmwareUpgrade(type, path) wurde hinzugefügt.
       | 9. Die Schnittstelle SetCtrlFirmwareUpgrade(type, path) wurde hinzugefügt.
       | 10. Die Schnittstelle SetEndFirmwareUpgrade(type, path) wurde hinzugefügt.
       | 11. Die Schnittstelle JointAllParamUpgrade(path) wurde hinzugefügt.
       
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
                     
   * - V3.8.0
     - 2025-02-12
     - | 1. Der Schnittstelle EndForceDragControl() wurde ein Parameter für die Singularitätsstrategie hinzugefügt.
       | 2. Der Schnittstelle ArcWeldTraceControl() wurden Versatzparameter hinzugefügt.
       | 3. Die Schnittstelle WeaveChangeStart() wurde hinzugefügt.
       | 4. Die Schnittstelle WeaveChangeEnd() wurde hinzugefügt.
       | 5. Die Schnittstelle LoadTrajectoryLA() wurde hinzugefügt.
       | 6. Die Schnittstelle MoveTrajectoryLA() wurde hinzugefügt.
       | 7. Die Schnittstelle CustomCollisionDetectionStart() wurde hinzugefügt.
       | 8. Die Schnittstelle CustomCollisionDetectionEnd() wurde hinzugefügt.