Roboter-Statusabfrage
=====================

.. toctree::
    :maxdepth: 5

Aktuelle Gelenkposition (Winkel) abrufen
+++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointPosDegree(flag=1)``"
    "Beschreibung", "Aktuelle Gelenkposition (Winkel) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``joint_pos = [j1, j2, j3, j4, j5, j6]``: Aktuelle Gelenkposition (Winkel) [°]"

Aktuelle Gelenkposition (Bogenmaß) abrufen
+++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointPosRadian(flag=1)``"
    "Beschreibung", "Aktuelle Gelenkposition (Bogenmaß) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``joint_pos = [j1, j2, j3, j4, j5, j6]``: Aktuelle Gelenkposition (rad)"

Gelenk-Rückmeldegeschwindigkeit (deg/s) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointSpeedsDegree(flag=1)``"
    "Beschreibung", "Gelenk-Rückmeldegeschwindigkeit (deg/s) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``speed = [j1, j2, j3, j4, j5, j6]``: Gelenk-Rückmeldegeschwindigkeit [°/s]"

Gelenk-Rückmeldebeschleunigung (deg/s²) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointAccDegree(flag=1)``"
    "Beschreibung", "Gelenk-Rückmeldebeschleunigung (deg/s²) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``acc = [j1, j2, j3, j4, j5, j6]``: Gelenk-Rückmeldebeschleunigung [°/s²]"

TCP-Befehlsresultierende Geschwindigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetTCPCompositeSpeed(flag=1)``"
    "Beschreibung", "TCP-Befehlsresultierende Geschwindigkeit abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[tcp_speed, ori_speed]``: tcp_speed = lineare Resultierende [mm/s], ori_speed = resultierende Orientierungsgeschwindigkeit [°/s]"

TCP-Rückmelderesultierende Geschwindigkeit abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPCompositeSpeed(flag=1)``"
    "Beschreibung", "TCP-Rückmelderesultierende Geschwindigkeit abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[tcp_speed, ori_speed]``: tcp_speed = lineare Resultierende [mm/s], ori_speed = resultierende Orientierungsgeschwindigkeit [°/s]"

TCP-Befehlsgeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetTCPSpeed(flag=1)``"
    "Beschreibung", "TCP-Befehlsgeschwindigkeit (Komponenten) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``speed = [x, y, z, rx, ry, rz]``: Befohlene TCP-Geschwindigkeit [mm/s, °/s]"

TCP-Rückmeldegeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPSpeed(flag=1)``"
    "Beschreibung", "TCP-Rückmeldegeschwindigkeit (Komponenten) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``speed = [x, y, z, rx, ry, rz]``: Tatsächliche TCP-Geschwindigkeit [mm/s, °/s]"

Aktuelle Werkzeugpose (TCP) abrufen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPPose(flag=1)``"
    "Beschreibung", "Aktuelle Werkzeugpose (TCP) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``tcp_pose = [x, y, z, rx, ry, rz]``: Aktuelle Werkzeugpose [mm, °]"

Nummer des aktuellen Werkzeugkoordinatensystems abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPNum(flag=1)``"
    "Beschreibung", "Nummer des aktuellen Werkzeugkoordinatensystems abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``tool_id``: Nummer des Werkzeugkoordinatensystems"

Nummer des aktuellen Werkstückkoordinatensystems abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualWObjNum(flag=1)``"
    "Beschreibung", "Nummer des aktuellen Werkstückkoordinatensystems abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``wobj_id``: Nummer des Werkstückkoordinatensystems"

Aktuelle Pose des Endflansches abrufen
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualToolFlangePose(flag=1)``"
    "Beschreibung", "Aktuelle Pose des Endflansches abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``flange_pose = [x, y, z, rx, ry, rz]``: Aktuelle Pose des Endflansches [mm, °]"

Aktuelle Gelenkmomente abrufen
+++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointTorques(flag=1)``"
    "Beschreibung", "Aktuelle Gelenkmomente abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``torques = [j1, j2, j3, j4, j5, j6]``: Gelenkmomente [Nm]"

Systemzeit abrufen
++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSystemClock()``"
    "Beschreibung", "Systemzeit abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``t_ms``: Systemzeit [ms]"

Abfragen, ob die Roboterbewegung abgeschlossen ist
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotMotionDone()``"
    "Beschreibung", "Abfragen, ob die Roboterbewegung abgeschlossen ist"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``state``: Bewegungsstatus: 0 = nicht abgeschlossen, 1 = abgeschlossen"

Länge der Roboter-Bewegungsbefehlswarteschlange abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetMotionQueueLength()``"
    "Beschreibung", "Länge der Roboter-Bewegungsbefehlswarteschlange abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``len``: Aktuelle Warteschlangenlänge"

Roboter-Not-Halt-Status abrufen
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotEmergencyStopState()``"
    "Beschreibung", "Roboter-Not-Halt-Status abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``state``: Not-Halt-Status: 0 = kein Not-Halt, 1 = Not-Halt aktiv"

Kommunikationsstatus zwischen SDK und Roboter abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSDKComState()``"
    "Beschreibung", "Kommunikationsstatus zwischen SDK und Roboter abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``state``: Kommunikationsstatus: 0 = normal, 1 = gestört"

Sicherheitsstopp-Signal abrufen
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSafetyStopState()``"
    "Beschreibung", "Sicherheitsstopp-Signal abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[si0_state, si1_state]``: si0_state = Signal SI0 (0 = inaktiv, 1 = aktiv), si1_state = Signal SI1 (0 = inaktiv, 1 = aktiv)"

Aktuelle Temperatur der Gelenkantriebe (°C) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointDriverTemperature()``"
    "Beschreibung", "Aktuelle Temperatur der Gelenkantriebe (°C) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``data = [t1, t2, t3, t4, t5, t6]``: Aktuelle Temperaturen der sechs Antriebe [°C]"

Aktuelles Drehmoment der Gelenkantriebe (Nm) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointDriverTorque()``"
    "Beschreibung", "Aktuelles Drehmoment der Gelenkantriebe (Nm) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``data = [j1, j2, j3, j4, j5, j6]``: Aktuelle Drehmomente der sechs Antriebe [Nm]"

Roboter-Echtzeitstatus abrufen
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotRealTimeState()``"
    "Beschreibung", "Roboter-Echtzeitstatus abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``robot_state_pkg``: Struktur mit den Echtzeitstatusdaten des Roboters"

Codebeispiel für Roboter-Statusabfrage
+++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    error, [yangle, zangle] = robot.GetRobotInstallAngle()
    print(f"yangle: {yangle}, zangle: {zangle}")
    error, j_deg = robot.GetActualJointPosDegree(0)
    print(f"joint pos deg: {j_deg[0]}, {j_deg[1]}, {j_deg[2]}, {j_deg[3]}, {j_deg[4]}, {j_deg[5]}")
    error, jointSpeed = robot.GetActualJointSpeedsDegree(0)
    print(f"joint speeds deg: {jointSpeed[0]}, {jointSpeed[1]}, {jointSpeed[2]}, {jointSpeed[3]}, {jointSpeed[4]}, {jointSpeed[5]}")
    error, jointAcc = robot.GetActualJointAccDegree(0)
    print(f"joint acc deg: {jointAcc[0]}, {jointAcc[1]}, {jointAcc[2]}, {jointAcc[3]}, {jointAcc[4]}, {jointAcc[5]}")
    error, [tcp_speed, ori_speed] = robot.GetTargetTCPCompositeSpeed(0)
    print(f"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error, [tcp_speed, ori_speed] = robot.GetActualTCPCompositeSpeed(0)
    print(f"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error, targetSpeed = robot.GetTargetTCPSpeed(0)
    print(f"GetTargetTCPSpeed {targetSpeed[0]}, {targetSpeed[1]}, {targetSpeed[2]}, {targetSpeed[3]}, {targetSpeed[4]}, {targetSpeed[5]}")
    error, actualSpeed = robot.GetActualTCPSpeed(0)
    print(f"GetActualTCPSpeed {actualSpeed[0]}, {actualSpeed[1]}, {actualSpeed[2]}, {actualSpeed[3]}, {actualSpeed[4]}, {actualSpeed[5]}")
    error, tcp = robot.GetActualTCPPose(0)
    print(f"tcp pose: {tcp[0]}, {tcp[1]}, {tcp[2]}, {tcp[3]}, {tcp[4]}, {tcp[5]}")
    error, flange = robot.GetActualToolFlangePose(0)
    print(f"flange pose: {flange[0]}, {flange[1]}, {flange[2]}, {flange[3]}, {flange[4]}, {flange[5]}")
    error, id = robot.GetActualTCPNum(0)
    print(f"tcp num: {id}")
    error, id = robot.GetActualWObjNum(0)
    print(f"wobj num: {id}")
    error, jtorque = robot.GetJointTorques(0)
    print(f"torques: {jtorque[0]}, {jtorque[1]}, {jtorque[2]}, {jtorque[3]}, {jtorque[4]}, {jtorque[5]}")
    error, t_ms = robot.GetSystemClock()
    print(f"system clock: {t_ms}")
    error, config = robot.GetRobotCurJointsConfig()
    print(f"joint config: {config}")
    error, motionDone = robot.GetRobotMotionDone()
    print(f"GetRobotMotionDone: {motionDone}")
    error, len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength: {len}")
    error, emergState = robot.GetRobotEmergencyStopState()
    print(f"GetRobotEmergencyStopState: {emergState}")
    error, comstate = robot.GetSDKComState()
    print(f"GetSDKComState: {comstate}")
    error, [si0_state, si1_state] = robot.GetSafetyStopState()
    print(f"GetSafetyStopState: {si0_state} {si1_state}")
    error, temp = robot.GetJointDriverTemperature()
    print(f"Temperature: {temp[0]}, {temp[1]}, {temp[2]}, {temp[3]}, {temp[4]}, {temp[5]}")
    error, torque = robot.GetJointDriverTorque()
    print(f"torque: {torque[0]}, {torque[1]}, {torque[2]}, {torque[3]}, {torque[4]}, {torque[5]}")
    error, pkg = robot.GetRobotRealTimeState()
    robot.CloseRPC()

Inverse Kinematik berechnen
+++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKin(type, desc_pos, config=-1)``"
    "Beschreibung", "Inverse Kinematik: Berechnet Gelenkpositionen aus einer kartesischen Pose"
    "Erforderliche Parameter", "- ``type``: 0 = absolute Pose (Basiskoordinatensystem), 1 = relative Pose (Basiskoordinatensystem), 2 = relative Pose (Werkzeugkoordinatensystem)
    - ``desc_pose``: [x, y, z, rx, ry, rz], Werkzeugpose [mm, °]"
    "Standardparameter", "- ``config``: Gelenk-Konfiguration: [-1] = Berechnung basierend auf aktueller Gelenkposition, [0~7] = Berechnung basierend auf spezifischer Konfiguration. Standard = -1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``joint_pos = [j1, j2, j3, j4, j5, j6]``: Berechnete Gelenkpositionen [°]"

Inverse Kinematik mit Referenzposition berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKinRef(type, desc_pos, joint_pos_ref)``"
    "Beschreibung", "Inverse Kinematik unter Verwendung einer Referenz-Gelenkposition"
    "Erforderliche Parameter", "- ``type``: 0 = absolute Pose (Basiskoordinatensystem), 1 = relative Pose (Basiskoordinatensystem), 2 = relative Pose (Werkzeugkoordinatensystem)
    - ``desc_pos``: [x, y, z, rx, ry, rz], Werkzeugpose [mm, °]
    - ``joint_pos_ref``: [j1, j2, j3, j4, j5, j6], Referenz-Gelenkposition [°]"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``joint_pos = [j1, j2, j3, j4, j5, j6]``: Berechnete Gelenkpositionen [°]"

Inverse Kinematik im kartesischen Raum inklusive Erweiterungsachsenposition
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKinExaxis(type, desc_pos, exaxis, tool, workPiece, config = -1)``"
    "Beschreibung", "Inverse Kinematik im kartesischen Raum inklusive Erweiterungsachsenposition"
    "Erforderliche Parameter", "- ``type``: 0 = absolute Pose (Basiskoordinatensystem), 1 = inkrementelle Pose (Basiskoordinatensystem), 2 = inkrementelle Pose (Werkzeugkoordinatensystem)
    - ``desc_pos``: Kartesische Pose [mm, °]
    - ``exaxis``: Position der Erweiterungsachse(n) [mm]
    - ``tool``: Werkzeugnummer
    - ``workPiece``: Werkstücknummer
    - ``config -1``: automatische Lösung, 0-7 entsprechen acht Lösungssätzen"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``joint_pos``: Berechnete Gelenkpositionen [°]"

Codebeispiel für inverse Kinematik mit Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    desc = [99.957, -0.002, 29.994, -176.569, -6.757, -167.462]
    exaxis = [100.0, 0.0, 0.0, 0.0]
    jointPos = [0.0] * 6
    offsetPos = [0.0] * 6
    rtn,pkg = robot.GetRobotRealTimeState()
    toolnum = pkg.tool
    workPcsNum = pkg.user
    rtn, jointPos = robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum)
    print(f"GetInverseKinExaxis joint is {jointPos[0]},{jointPos[1]},{jointPos[2]},{jointPos[3]},{jointPos[4]},{jointPos[5]}")
    robot.ExtAxisMove(exaxis, 100, -1)
    robot.MoveJ(joint_pos=jointPos, desc_pos=desc, tool=toolnum, user=workPcsNum, vel=100.0, acc=100.0, ovl=100.0, exaxis_pos=exaxis, blendT=-1, offset_flag=0, offset_pos=offsetPos)
    robot.CloseRPC()
    return 0

Prüfen, ob die inverse Kinematik eine Lösung hat
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKinHasSolution(type, desc_pos, joint_pos_ref)``"
    "Beschreibung", "Prüfen, ob die inverse Kinematik für eine gegebene Pose eine Lösung hat"
    "Erforderliche Parameter", "- ``type``: 0 = absolute Pose (Basiskoordinatensystem), 1 = relative Pose (Basiskoordinatensystem), 2 = relative Pose (Werkzeugkoordinatensystem)
    - ``desc_pos``: [x, y, z, rx, ry, rz], Werkzeugpose [mm, °]
    - ``joint_pos_ref``: [j1, j2, j3, j4, j5, j6], Referenz-Gelenkposition [°]"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``result``: True = Lösung vorhanden, False = keine Lösung"

Vorwärtskinematik berechnen
++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetForwardKin(joint_pos)``"
    "Beschreibung", "Vorwärtskinematik: Berechnet Werkzeugpose aus Gelenkpositionen"
    "Erforderliche Parameter", "- ``joint_pos``: [j1, j2, j3, j4, j5, j6], Gelenkpositionen [°]"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``desc_pos = [x, y, z, rx, ry, rz]``: Berechnete Werkzeugpose [mm, °]"

Codebeispiel für Vorwärts- und inverse Kinematik
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    error, inverseRtn = robot.GetInverseKin(0, desc_pos=desc_pos1, config=-1)
    print(f"dcs1 GetInverseKin rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, inverseRtn = robot.GetInverseKinRef(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, hasResult = robot.GetInverseKinHasSolution(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef result {hasResult}")
    error, forwordResult = robot.GetForwardKin(j1)
    print(f"jpos1 forwordResult rtn is {forwordResult[0]}, {forwordResult[1]}, {forwordResult[2]}, "
          f"{forwordResult[3]}, {forwordResult[4]}, {forwordResult[5]}")
    robot.CloseRPC()

Daten eines Roboter-Teachingpunkts abfragen
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotTeachingPoint(name)``"
    "Beschreibung", "Daten eines Roboter-Teachingpunkts abfragen"
    "Erforderliche Parameter", "- ``name``: Name des Punkts"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[x, y, z, rx, ry, rz, j1, j2, j3, j4, j5, j6, tool, wobj, speed, acc, e1, e2, e3, e4]``: Punktdaten"

DH-Parameter-Kompensationswerte abrufen
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDHCompensation()``"
    "Beschreibung", "DH-Parameter-Kompensationswerte abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``dhCompensation = [cmpstD1, cmpstA2, cmpstA3, cmpstD4, cmpstD5, cmpstD6]``: DH-Parameter-Kompensationswerte [mm]"

SN-Code des Steuerkastens abrufen
++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotSN()``"
    "Beschreibung", "SN-Code des Steuerkastens abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``SNCode``: SN-Code des Steuerkastens"

Codebeispiel für Teachingpunkt-Abfrage
++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    name = "P1"
    rtn, data = robot.GetRobotTeachingPoint(name)
    print(f"{rtn} name is: {name}")
    for i in range(20):
        print(f"data is: {data[i]}")
    rtn,que_len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength rtn is: {rtn}, queue length is: {que_len}")
    retval,dh = robot.GetDHCompensation()
    print(f"retval is: {retval}")
    print(f"dh is: {dh[0]} {dh[1]} {dh[2]} {dh[3]} {dh[4]} {dh[5]}")
    error,sn = robot.GetRobotSN()
    print(f"robot SN is {sn[0]}")
    robot.CloseRPC()

Werkzeugkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolCoordWithID(id)``"
    "Beschreibung", "Ruft das Werkzeugkoordinatensystem nach ID ab"
    "Erforderliche Parameter", "- ``id``: Nummer des Werkzeugkoordinatensystems"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode, 0-Erfolg; ungleich Null-Fehler
    - ``coord``: Werte des Koordinatensystems
    - ``type``: Werkzeugtyp (optional) 0-Werkzeug; 1-Sensor
    - ``install``: Installationsposition (optional) 0-Roboterende; 1-außerhalb des Roboters
    - ``toolID``: Werkzeug-ID
    - ``loadNo``: Lastnummer
    "

Werkstückkoordinatensystem nach ID abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWObjCoordWithID(id)``"
    "Beschreibung", "Ruft das Werkstückkoordinatensystem nach ID ab"
    "Erforderliche Parameter", "- ``id``: Nummer des Werkstückkoordinatensystems"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode, 0-Erfolg; ungleich Null-Fehler
    - ``coord``: Werte des Koordinatensystems
    - ``refFrame``: Referenzkoordinatensystem
    "

Externes Werkzeugkoordinatensystem nach ID abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExToolCoordWithID(id)``"
    "Beschreibung", "Ruft das externe Werkzeugkoordinatensystem nach ID ab"
    "Erforderliche Parameter", "- ``id``: Nummer des externen Werkzeugkoordinatensystems"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode, 0-Erfolg; ungleich Null-Fehler
    - ``coord``: Werte des Koordinatensystems
    - ``tcoord``: Pose des am Roboterende montierten Werkstückkoordinatensystems (6 Werte: [x, y, z, rx, ry, rz])
    "

Erweitertes Achsenkoordinatensystem nach ID abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExAxisCoordWithID(id)``"
    "Beschreibung", "Ruft das erweiterte Achsenkoordinatensystem nach ID ab"
    "Erforderliche Parameter", "- ``id``: Nummer des erweiterten Achsenkoordinatensystems"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode, 0-Erfolg; ungleich Null-Fehler
    - ``coord``: Werte des Koordinatensystems
    - ``axisCoordNum``: Erweiterte Achsnummer (optional) bit0-bit3 entsprechen den erweiterten Achsen 1-4; z.B. entspricht Wert 3 den erweiterten Achsen [1,2]
    - ``calibFlag``: Kalibrierungsflag (optional) 0-nicht kalibriert; 1-kalibriert
    "

Lastmasse und -schwerpunkt nach ID abrufen
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetPayloadWithID(id)``"
    "Beschreibung", "Lastmasse und -schwerpunkt nach ID abrufen"
    "Erforderliche Parameter", "- ``id``: Lastnummer (Erweiterungsachsen-Koordinatensystem-Nummer?)"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``weight``: Lastmasse [kg]
    - ``cog``: Lastschwerpunkt [x, y, z] [mm]"

Aktuelles Werkzeugkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurToolCoord()``"
    "Beschreibung", "Aktuelles Werkzeugkoordinatensystem abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Koordinatenwerte [x, y, z, rx, ry, rz]"

Aktuelles Werkstückkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurWObjCoord()``"
    "Beschreibung", "Aktuelles Werkstückkoordinatensystem abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Koordinatenwerte [x, y, z, rx, ry, rz]"

Aktuelles externes Werkzeugkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurExToolCoord()``"
    "Beschreibung", "Aktuelles externes Werkzeugkoordinatensystem abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Koordinatenwerte [x, y, z, rx, ry, rz]"

Aktuelles Erweiterungsachsen-Koordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurExAxisCoord()``"
    "Beschreibung", "Aktuelles Erweiterungsachsen-Koordinatensystem abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Koordinatenwerte [x, y, z, rx, ry, rz]"

Codebeispiel zum Abrufen von Roboter-Koordinatensystemen und Lastdaten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        time.sleep(2)

        id = 1
        rtn, toolCoord, type_val, install, toolID, loadNo = robot.GetToolCoordWithID(id)
        print(f"GetToolCoordWithID {id}, {toolCoord[0]:.6f} {toolCoord[1]:.6f} {toolCoord[2]:.6f} {toolCoord[3]:.6f} {toolCoord[4]:.6f} {toolCoord[5]:.6f},  type = {type_val}, install = {install}, toolID = {toolID}, loadNo = {loadNo}")
        rtn, wobjCoord, refFrame = robot.GetWObjCoordWithID(id)
        print(f"GetWObjCoordWithID {id}, {wobjCoord[0]:.6f} {wobjCoord[1]:.6f} {wobjCoord[2]:.6f} {wobjCoord[3]:.6f} {wobjCoord[4]:.6f} {wobjCoord[5]:.6f}, refFrame = {refFrame}")
        rtn, extoolCoord, exworkpieceCoord = robot.GetExToolCoordWithID(21)
        print(f"GetExToolCoordWithID {id}, {extoolCoord[0]:.6f} {extoolCoord[1]:.6f} {extoolCoord[2]:.6f} {extoolCoord[3]:.6f} {extoolCoord[4]:.6f} {extoolCoord[5]:.6f}, {exworkpieceCoord[0]:.6f} {exworkpieceCoord[1]:.6f} {exworkpieceCoord[2]:.6f} {exworkpieceCoord[3]:.6f} {exworkpieceCoord[4]:.6f} {exworkpieceCoord[5]:.6f}")
        rtn, exAxisCoord, axisCoordNum, calibFlag = robot.GetExAxisCoordWithID(id)
        print(f"GetExAxisCoordWithID {id}, {exAxisCoord[0]:.6f} {exAxisCoord[1]:.6f} {exAxisCoord[2]:.6f} {exAxisCoord[3]:.6f} {exAxisCoord[4]:.6f} {exAxisCoord[5]:.6f}, axisCoordNum = {axisCoordNum}, calibFlag = {calibFlag}")
        rtn, weight, cog = robot.GetTargetPayloadWithID(id)
        print(f"GetTargetPayloadWithID {id}, {weight:.6f} {cog[0]:.6f} {cog[1]:.6f} {cog[2]:.6f}")
        rtn, toolCoord = robot.GetCurToolCoord()
        print(f"GetCurToolCoord {toolCoord[0]:.6f} {toolCoord[1]:.6f} {toolCoord[2]:.6f} {toolCoord[3]:.6f} {toolCoord[4]:.6f} {toolCoord[5]:.6f}")
        rtn, wobjCoord = robot.GetCurWObjCoord()
        print(f"GetCurWObjCoord {wobjCoord[0]:.6f} {wobjCoord[1]:.6f} {wobjCoord[2]:.6f} {wobjCoord[3]:.6f} {wobjCoord[4]:.6f} {wobjCoord[5]:.6f}")
        rtn, extoolCoord = robot.GetCurExToolCoord()
        print(f"GetCurExToolCoord {extoolCoord[0]:.6f} {extoolCoord[1]:.6f} {extoolCoord[2]:.6f} {extoolCoord[3]:.6f} {extoolCoord[4]:.6f} {extoolCoord[5]:.6f}")

        rtn, exAxisCoord = robot.GetCurExAxisCoord()
        print(f"GetCurExAxisCoord {exAxisCoord[0]:.6f} {exAxisCoord[1]:.6f} {exAxisCoord[2]:.6f} {exAxisCoord[3]:.6f} {exAxisCoord[4]:.6f} {exAxisCoord[5]:.6f}")
        rtn, weightT = robot.GetTargetPayload(0)
        rtn, cogT = robot.GetTargetPayloadCog(0)
        print(f"GetTargetPayload {weightT:.6f} {cogT[0]:.6f} {cogT[1]:.6f} {cogT[2]:.6f}")
        coordSet = [0.0, 1.0, 2.0, 3.0, 4.0, 5.0]

        rtn = robot.SetToolCoord(1, coordSet, 0, 0, 1, 0)
        print(f"SetToolCoord rtn is {rtn}")

        rtn = robot.SetWObjCoord(1, coordSet, 0)
        print(f"SetWObjCoord rtn is {rtn}")

        rtn = robot.SetLoadWeight(1, 1.3)
        print(f"SetLoadWeight rtn is {rtn}")

        rtn = robot.SetLoadCoord(10.0, 20.0, 30.0,1)
        print(f"SetLoadCoord rtn is {rtn}")

        etcp = [0.0, 0.0, 100.0, 0.0, 0.0, 0.0]
        etool = [0.0, 0.0, 50.0, 0.0, 0.0, 0.0]
        rtn = robot.SetExToolCoord(21, etcp, etool)
        print(f"SetExToolCoord rtn is {rtn}")

        rtn = robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1)
        print(f"ExtAxisActiveECoordSys rtn is {rtn}")

        robot.CloseRPC()

    if __name__ == "__main__":
        main()