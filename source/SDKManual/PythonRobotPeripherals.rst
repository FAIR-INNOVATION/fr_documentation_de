Roboter-Peripherie
==================

.. toctree::
    :maxdepth: 5

Greifer konfigurieren
+++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetGripperConfig(company, device, softversion=0, bus=0)``"
    "Beschreibung", "Greifer konfigurieren"
    "Erforderliche Parameter", "- ``company``: Greiferhersteller, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing
    - ``device``: Gerätenummer, Robotiq(0-2F-85 Serie), Huiling(0-NK Serie, 1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)"
    "Standardparameter", "- ``softversion``: Softwareversionsnummer, vorübergehend nicht verwendet, Standard = 0
    - ``bus``: Position des Geräts am Endeffektor-Bus, vorübergehend nicht verwendet, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Greiferkonfiguration abrufen
+++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperConfig()``"
    "Beschreibung", "Greiferkonfiguration abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[number, company, device, softversion]``: number = Greifernummer; company = Hersteller; device = Gerätenummer; softversion = Softwareversion"

Greifer aktivieren
++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ActGripper(index, action)``"
    "Beschreibung", "Greifer aktivieren"
    "Erforderliche Parameter", "- ``index``: Greifernummer
    - ``action``: 0 = Zurücksetzen, 1 = Aktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Greifer steuern
+++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveGripper(index, pos, vel, force, maxtime, block, type, rotNum, rotVel, rotTorque)``"
    "Beschreibung", "Greifer steuern"
    "Erforderliche Parameter", "- ``index``: Greifernummer
    - ``pos``: Positionsprozentsatz, Bereich [0~100]
    - ``vel``: Geschwindigkeitsprozentsatz, Bereich [0~100]
    - ``force``: Drehmomentprozentsatz, Bereich [0~100]
    - ``maxtime``: Maximale Wartezeit, Bereich [0~30000], [ms]
    - ``block``: 0 = blockierend, 1 = nicht blockierend
    - ``type``: Greifertyp, 0 = Parallelgreifer, 1 = Rotationsgreifer
    - ``rotNum``: Rotationsanzahl (Umdrehungen)
    - ``rotVel``: Rotationsgeschwindigkeitsprozentsatz [0-100]
    - ``rotTorque``: Rotationsdrehmomentprozentsatz [0-100]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Greifer-Bewegungsstatus abrufen
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperMotionDone()``"
    "Beschreibung", "Greifer-Bewegungsstatus abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[fault, status]``: fault = 0 = kein Fehler, 1 = Fehler; status = 0 = Bewegung nicht abgeschlossen, 1 = Bewegung abgeschlossen"

Greifer-Aktivierungsstatus abrufen
+++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperActivateStatus()``"
    "Beschreibung", "Greifer-Aktivierungsstatus abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``gripper_active``: Bit0~Bit15 entsprechen Greifernummern 0~15, Bit = 0 = nicht aktiviert, Bit = 1 = aktiviert"

Greiferposition abrufen
++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperCurPosition()``"
    "Beschreibung", "Greiferposition abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``position``: Positionsprozentsatz, Bereich 0~100%"

Greifergeschwindigkeit abrufen
+++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperCurSpeed()``"
    "Beschreibung", "Greifergeschwindigkeit abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``speed``: Geschwindigkeitsprozentsatz, Bereich 0~100%"

Greiferstrom abrufen
+++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperCurCurrent()``"
    "Beschreibung", "Greiferstrom abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``current``: Stromprozentsatz, Bereich 0~100%"

Greiferspannung abrufen
++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperVoltage()``"
    "Beschreibung", "Greiferspannung abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``voltage``: Spannung, Einheit 0.1V"

Greifertemperatur abrufen
++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperTemp()``"
    "Beschreibung", "Greifertemperatur abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``temp``: Temperatur [°C]"

Vor-Greifpunkt berechnen (visuell)
+++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputePrePick(desc_pos, zlength, zangle)``"
    "Beschreibung", "Vor-Greifpunkt berechnen (visuell)"
    "Erforderliche Parameter", "- ``desc_pos``: Kartesische Pose des Greifpunkts [x, y, z, rx, ry, rz]
    - ``zlength``: Z-Achsen-Versatz [mm]
    - ``zangle``: Rotationsversatz um die Z-Achse [°]"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``pre_pos``: Berechneter Vor-Greifpunkt [x, y, z, rx, ry, rz]"

Rückzugspunkt berechnen (visuell)
++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputePostPick(desc_pos, zlength, zangle)``"
    "Beschreibung", "Rückzugspunkt berechnen (visuell)"
    "Erforderliche Parameter", "- ``desc_pos``: Kartesische Pose des Greifpunkts [x, y, z, rx, ry, rz]
    - ``zlength``: Z-Achsen-Versatz [mm]
    - ``zangle``: Rotationsversatz um die Z-Achse [°]"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``post_pos``: Berechneter Rückzugspunkt [x, y, z, rx, ry, rz]"

Codebeispiel für Roboter-Greiferoperationen
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    company = 4
    device = 0
    softversion = 0
    bus = 2
    index = 2
    act = 0
    max_time = 30000
    block = 0
    status = 0
    fault = 0
    active_status = 0
    current_pos = 0
    current = 0
    voltage = 0
    temp = 0
    speed = 0
    robot.SetGripperConfig(company, device, softversion, bus)
    time.sleep(1)
    error, [company, device, softversion, bus] = robot.GetGripperConfig()
    print(f"gripper config: {company}, {device}, {softversion}, {bus}")
    robot.ActGripper(index, act)
    time.sleep(1)
    act = 1
    robot.ActGripper(index, act)
    time.sleep(1)
    error = robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is: {error}")
    time.sleep(1)
    error = robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is: {error}")
    error, [fault, status] = robot.GetGripperMotionDone()
    print(f"motion status: {fault}, {status}")
    error, [fault, active_status] = robot.GetGripperActivateStatus()
    print(f"gripper active fault is: {fault}, status is: {active_status}")
    error, [fault, current_pos] = robot.GetGripperCurPosition()
    print(f"fault is: {fault}, current position is: {current_pos}")
    error, [fault, current] = robot.GetGripperCurCurrent()
    print(f"fault is: {fault}, current current is: {current}")
    error, [fault, voltage] = robot.GetGripperVoltage()
    print(f"fault is: {fault}, current voltage is: {voltage}")
    error, [fault, temp] = robot.GetGripperTemp()
    print(f"fault is: {fault}, current temperature is: {temp}")
    error, [fault, speed] = robot.GetGripperCurSpeed()
    print(f"fault is: {fault}, current speed is: {speed}")
    retval = 0
    prepick_pose = [0.0] * 6
    postpick_pose = [0.0] * 6
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval, prepick_pose = robot.ComputePrePick(p1Desc, 10, 0)
    print(f"ComputePrePick retval is: {retval}")
    print(f"xyz is: {prepick_pose[0]}, {prepick_pose[1]}, {prepick_pose[2]}; rpy is: {prepick_pose[3]}, {prepick_pose[4]}, {prepick_pose[5]}")
    retval, postpick_pose = robot.ComputePostPick(p2Desc, -10, 0)
    print(f"ComputePostPick retval is: {retval}")
    print(f"xyz is: {postpick_pose[0]}, {postpick_pose[1]}, {postpick_pose[2]}; rpy is: {postpick_pose[3]}, {postpick_pose[4]}, {postpick_pose[5]}")
    robot.CloseRPC()

Rotationsanzahl des Rotationsgreifers abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperRotNum()``"
    "Beschreibung", "Rotationsanzahl des Rotationsgreifers abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``num``: Rotationsanzahl (Umdrehungen)"

Rotationsgeschwindigkeitsprozentsatz des Rotationsgreifers abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperRotSpeed()``"
    "Beschreibung", "Rotationsgeschwindigkeitsprozentsatz des Rotationsgreifers abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``speed``: Rotationsgeschwindigkeitsprozentsatz"

Rotationsdrehmomentprozentsatz des Rotationsgreifers abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperRotTorque()``"
    "Beschreibung", "Rotationsdrehmomentprozentsatz des Rotationsgreifers abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``fault``: 0 = kein Fehler, 1 = Fehler
    - ``torque``: Rotationsdrehmomentprozentsatz"

Codebeispiel zum Abrufen des Status eines Rotationsgreifers
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    fault = 0
    rotNum = 0.0
    rotSpeed = 0
    rotTorque = 0
    error,fault, rotNum = robot.GetGripperRotNum()
    error,fault, rotSpeed = robot.GetGripperRotSpeed()
    error,fault, rotTorque = robot.GetGripperRotTorque()
    print(f"gripper rot num:{rotNum},gripper rotSpeed:{rotSpeed},gripper rotTorque:{rotTorque}")
    robot.CloseRPC()

Förderband starten/stoppen
++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorStartEnd(status)``"
    "Beschreibung", "Förderband starten/stoppen"
    "Erforderliche Parameter", "- ``status``: Förderbandstatus, 1 = starten, 0 = stoppen"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

IO-Erkennungspunkt aufzeichnen
+++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorPointIORecord()``"
    "Beschreibung", "IO-Erkennungspunkt aufzeichnen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Punkt A aufzeichnen
++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorPointARecord()``"
    "Beschreibung", "Punkt A aufzeichnen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Referenzpunkt aufzeichnen
++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorRefPointRecord()``"
    "Beschreibung", "Referenzpunkt aufzeichnen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Punkt B aufzeichnen
++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorPointBRecord()``"
    "Beschreibung", "Punkt B aufzeichnen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Förderband-Werkstück IO-Erkennung
++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorIODetect(max_t)``"
    "Beschreibung", "Förderband-Werkstück IO-Erkennung"
    "Erforderliche Parameter", "- ``max_t``: Maximale Erkennungszeit [ms]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Aktuelle Objektposition abrufen
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorGetTrackData(mode)``"
    "Beschreibung", "Aktuelle Objektposition abrufen"
    "Erforderliche Parameter", "- ``mode``: 1 = Tracking Greifen, 2 = Tracking Bewegung, 3 = TPD Tracking"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Förderband-Tracking starten
++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorTrackStart(status)``"
    "Beschreibung", "Förderband-Tracking starten"
    "Erforderliche Parameter", "- ``status``: Status, 1 = starten, 0 = stoppen"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Förderband-Tracking stoppen
++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorTrackEnd()``"
    "Beschreibung", "Förderband-Tracking stoppen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Förderbandparameter konfigurieren
++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorSetParam(param, followType, startDis, endDis)``"
    "Beschreibung", "Förderbandparameter konfigurieren"
    "Erforderliche Parameter", "- ``param`` = [encChannel, resolution, lead, wpAxis, vision, speedRadio]
                    - ``encChannel``: Encoderkanal 1-2
                    - ``resolution``: Encoderauflösung (Impulse pro Umdrehung)
                    - ``lead``: Mechanisches Übersetzungsverhältnis (Vorschub pro Encoderumdrehung) [mm]
                    - ``wpAxis``: Werkstückkoordinatennummer (für Tracking-Bewegung, bei Tracking-Greifen/TPD-Tracking auf 0 setzen)
                    - ``vision``: Mit Vision gekoppelt? 0 = nein, 1 = ja
                    - ``speedRadio``: Geschwindigkeitsverhältnis (für Förderband-Tracking-Greifen Bereich 1-100, für Tracking-Bewegung/TPD-Tracking auf 1 setzen)
    - ``followType``: Tracking-Bewegungstyp, 0 = Tracking-Bewegung, 1 = Nachlauf-Bewegung"
    "Standardparameter", "- ``startDis``: Für Nachlauf-Greifen erforderlich: Startabstand des Trackings. -1 = automatische Berechnung (Nachlauf startet, wenn Werkstück unter Roboter ist). Einheit mm, Standard = 0
    - ``endDis``: Für Nachlauf-Greifen erforderlich: Endabstand des Trackings. Einheit mm, Standard = 100"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Förderband-Greifpunktkompensation
++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorCatchPointComp(cmp)``"
    "Beschreibung", "Förderband-Greifpunktkompensation"
    "Erforderliche Parameter", "- ``cmp``: Kompensationsposition [x, y, z] [mm]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Linearbewegung
++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorTrackMoveL(name, tool, wobj, vel=20, acc=100, ovl=100, blendR=-1.0)``"
    "Beschreibung", "Linearbewegung"
    "Erforderliche Parameter", "- ``name``: Name des Bewegungspunkts ('cvrCatchPoint' oder 'cvrRaisePoint')
    - ``tool``: Werkzeugnummer
    - ``wobj``: Werkstücknummer"
    "Standardparameter", "- ``vel``: Geschwindigkeit [%], Standard = 20
    - ``acc``: Beschleunigung [%], Standard = 100
    - ``ovl``: Geschwindigkeitsskalierungsfaktor [%], Standard = 100
    - ``blendR``: [-1.0] = Bewegung abschließen (blockierend), [0~1000] = Glättungsradius (nicht blockierend) [mm], Standard = -1.0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Förderband-Kommunikationseingangserkennung
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorComDetect(timeout)``"
    "Beschreibung", "Förderband-Kommunikationseingangserkennung"
    "Erforderliche Parameter", "- ``timeout``: Warte-Timeout [ms]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Förderband-Kommunikationseingangserkennung auslösen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorComDetectTrigger()``"
    "Beschreibung", "Förderband-Kommunikationseingangserkennung auslösen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Förderbandoperationen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    retval = robot.ConveyorStartEnd(1)
    print(f"ConveyorStartEnd retval is: {retval}")
    retval = robot.ConveyorPointIORecord()
    print(f"ConveyorPointIORecord retval is: {retval}")
    retval = robot.ConveyorPointARecord()
    print(f"ConveyorPointARecord retval is: {retval}")
    retval = robot.ConveyorRefPointRecord()
    print(f"ConveyorRefPointRecord retval is: {retval}")
    retval = robot.ConveyorPointBRecord()
    print(f"ConveyorPointBRecord retval is: {retval}")
    retval = robot.ConveyorStartEnd(0)
    print(f"ConveyorStartEnd retval is: {retval}")
    param = [1.0, 10000.0, 200.0, 0.0, 0.0, 20.0]
    retval = robot.ConveyorSetParam(param, 0)
    print(f"ConveyorSetParam retval is: {retval}")
    cmp = [0.0, 0.0, 0.0]
    retval = robot.ConveyorCatchPointComp(cmp)
    print(f"ConveyorCatchPointComp retval is: {retval}")
    index = 1
    max_time = 30000
    block = 0
    retval = 0
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval = robot.MoveCart(p1Desc, 1, 0, 100.0)
    print(f"MoveCart retval is: {retval}")
    retval = robot.WaitMs(1)
    print(f"WaitMs retval is: {retval}")
    retval = robot.ConveyorIODetect(10000)
    print(f"ConveyorIODetect retval is: {retval}")
    retval = robot.ConveyorGetTrackData(1)
    print(f"ConveyorGetTrackData retval is: {retval}")
    retval = robot.ConveyorTrackStart(1)
    print(f"ConveyorTrackStart retval is: {retval}")
    retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100)
    print(f"TrackMoveL retval is: {retval}")
    retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is: {retval}")
    retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100)
    print(f"TrackMoveL retval is: {retval}")
    retval = robot.ConveyorTrackEnd()
    print(f"ConveyorTrackEnd retval is: {retval}")
    robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0)
    retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is: {retval}")
    robot.CloseRPC()

Endeffektor-Sensor konfigurieren
++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorConfig(idCompany, idDevice, idSoftware, idBus)``"
    "Beschreibung", "Endeffektor-Sensor konfigurieren"
    "Erforderliche Parameter", "- ``idCompany``: Hersteller, 18 = JUNKONG, 25 = HUIDE
    - ``idDevice``: Typ, 0 = JUNKONG/RYR6T.V1.0
    - ``idSoftware``: Softwareversion, 0 = J1.0/HuiDe1.0 (vorübergehend nicht freigegeben)
    - ``idBus``: Anschlussposition, 1 = Endeffektor Port 1, 2 = Port 2, ... 8 = Port 8 (vorübergehend nicht freigegeben)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Endeffektor-Sensorkonfiguration abrufen
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorConfigGet()``"
    "Beschreibung", "Endeffektor-Sensorkonfiguration abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``idCompany``: Hersteller, 18 = JUNKONG, 25 = HUIDE
    - ``idDevice``: Typ, 0 = JUNKONG/RYR6T.V1.0"

Endeffektor-Sensor aktivieren
++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorActivate(actFlag)``"
    "Beschreibung", "Endeffektor-Sensor aktivieren"
    "Erforderliche Parameter", "- ``actFlag``: 0 = Zurücksetzen, 1 = Aktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Koordinatenwerte [x, y, z, rx, ry, rz] (Bedeutung unklar)"

In Endeffektor-Sensorregister schreiben
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorRegWrite(devAddr, regHAddr, regLAddr, regNum, data1, data2, isNoBlock)``"
    "Beschreibung", "In Endeffektor-Sensorregister schreiben"
    "Erforderliche Parameter", "- ``devAddr``: Geräteadresse 0-255
    - ``regHAddr``: Registeradresse hohes Byte
    - ``regLAddr``: Registeradresse niedriges Byte
    - ``regNum``: Anzahl der Register 0-255
    - ``data1``: Zu schreibender Registerwert 1
    - ``data2``: Zu schreibender Registerwert 2
    - ``isNoBlock``: Blockierungs-Flag, 0 = blockierend, 1 = nicht blockierend"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Endeffektor-Sensor
+++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.AxleSensorConfig(18, 0, 0, 1)
    error, company, type = robot.AxleSensorConfigGet()
    print(f"company is: {company}, type is: {type}")
    rtn = robot.AxleSensorActivate(1)
    print(f"AxleSensorActivate rtn is: {rtn}")
    time.sleep(1)
    rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0)
    print(f"AxleSensorRegWrite rtn is: {rtn}")
    robot.CloseRPC()

Roboter-Peripherieprotokoll abrufen
++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExDevProtocol()``"
    "Beschreibung", "Roboter-Peripherieprotokoll abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``protocol``: Peripherieprotokollnummer: 4096 = Erweiterungsachsen-Steuerkarte, 4097 = ModbusSlave, 4098 = ModbusMaster"

Roboter-Peripherieprotokoll einstellen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExDevProtocol(protocol)``"
    "Beschreibung", "Roboter-Peripherieprotokoll einstellen"
    "Erforderliche Parameter", "- ``protocol``: Peripherieprotokollnummer: 4096 = Erweiterungsachsen-Steuerkarte, 4097 = ModbusSlave, 4098 = ModbusMaster"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Einstellen des Roboter-Peripherieprotokolls
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    protocol = 4096
    rtn = robot.SetExDevProtocol(protocol)
    print(f"SetExDevProtocol rtn: {rtn}")
    rtn, protocol = robot.GetExDevProtocol()
    print(f"GetExDevProtocol rtn: {rtn}, protocol is: {protocol}")
    robot.CloseRPC()

Endeffektor-Kommunikationsparameter abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleCommunicationParam()``"
    "Beschreibung", "Endeffektor-Kommunikationsparameter abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``baudRate``: Baudrate: 1=9600, 2=14400, 3=19200, 4=38400, 5=56000, 6=67600, 7=115200, 8=128000
    - ``dataBit``: Datenbits: unterstützt 8, 9; üblich 8
    - ``stopBit``: Stoppbits: 1=1, 2=0.5, 3=2, 4=1.5; üblich 1
    - ``verify``: Parität: 0=None, 1=Odd, 2=Even; üblich 0
    - ``timeout``: Timeout: 1~1000 ms
    - ``timeoutTimes``: Anzahl Timeout-Wiederholungen: 1~10
    - ``period``: Zykluszeit für periodische Befehle: 1~1000 ms"

Endeffektor-Kommunikationsparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleCommunicationParam(baudRate, dataBit, stopBit, verify, timeout, timeoutTimes, period)``"
    "Beschreibung", "Endeffektor-Kommunikationsparameter einstellen"
    "Erforderliche Parameter", "- ``baudRate``: Baudrate: 1=9600, 2=14400, 3=19200, 4=38400, 5=56000, 6=67600, 7=115200, 8=128000
    - ``dataBit``: Datenbits: unterstützt 8, 9; üblich 8
    - ``stopBit``: Stoppbits: 1=1, 2=0.5, 3=2, 4=1.5; üblich 1
    - ``verify``: Parität: 0=None, 1=Odd, 2=Even; üblich 0
    - ``timeout``: Timeout: 1~1000 ms
    - ``timeoutTimes``: Anzahl Timeout-Wiederholungen: 1~10
    - ``period``: Zykluszeit für periodische Befehle: 1~1000 ms"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Endeffektor-Dateiübertragungstyp einstellen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleFileType(type)``"
    "Beschreibung", "Endeffektor-Dateiübertragungstyp einstellen"
    "Erforderliche Parameter", "- ``type``: 1 = MCU Upgrade-Datei, 2 = LUA-Datei"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Endeffektor-LUA-Ausführung aktivieren
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleLuaEnable(enable)``"
    "Beschreibung", "Endeffektor-LUA-Ausführung aktivieren"
    "Erforderliche Parameter", "- ``enable``: 0 = nicht aktivieren, 1 = aktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Fehlerbehebung bei anomaler Endeffektor-LUA-Datei
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRecoverAxleLuaErr(enable)``"
    "Beschreibung", "Fehlerbehebung bei anomaler Endeffektor-LUA-Datei"
    "Erforderliche Parameter", "- ``status``: 0 = nicht beheben, 1 = beheben"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Aktivierungsstatus der Endeffektor-LUA-Ausführung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaEnableStatus()``"
    "Beschreibung", "Aktivierungsstatus der Endeffektor-LUA-Ausführung abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``enable``: 0 = nicht aktiviert, 1 = aktiviert"

Festlegen der aktivierten Endeffektor-Gerätetypen für LUA
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleLuaEnableDeviceType(self, forceSensorEnable, gripperEnable, IOEnable, dexhandEnable)``"
    "Beschreibung", "Legt die aktivierten Endeffektor-Gerätetypen für LUA fest"
    "Erforderliche Parameter", "
    - ``forceSensorEnable``: Aktivierungsstatus Kraftsensor, 0-deaktiviert; 1-aktiviert
    - ``gripperEnable``: Aktivierungsstatus Greifer, 0-deaktiviert; 1-aktiviert
    - ``IOEnable``: Aktivierungsstatus IO-Gerät, 0-deaktiviert; 1-aktiviert
    - ``dexhandEnable``: Aktivierungsstatus dreifingrige Hand, 0-deaktiviert; 1-aktiviert"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode, 0-Erfolg; ungleich Null-Fehler"

Abrufen der aktivierten Endeffektor-Gerätetypen für LUA
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaEnableDeviceType()``"
    "Beschreibung", "Ruft die aktivierten Endeffektor-Gerätetypen für LUA ab"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode, 0-Erfolg; ungleich Null-Fehler
    - ``forceSensorEnable``: Aktivierungsstatus Kraftsensor, 0-deaktiviert; 1-aktiviert
    - ``gripperEnable``: Aktivierungsstatus Greifer, 0-deaktiviert; 1-aktiviert
    - ``IOEnable``: Aktivierungsstatus IO-Gerät, 0-deaktiviert; 1-aktiviert
    - ``dexhandEnable``: Aktivierungsstatus dreifingrige Hand, 0-deaktiviert; 1-aktiviert"

Abrufen der aktuell konfigurierten Endeffektor-Geräte
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaEnableDevice()``"
    "Beschreibung", "Ruft die aktuell konfigurierten Endeffektor-Geräte ab"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode, 0-Erfolg; ungleich Null-Fehler
    - ``forceSensorEnable[8]``: Aktivierungsstatus Kraftsensor, 0-deaktiviert; 1-aktiviert
    - ``gripperEnable[8]``: Aktivierungsstatus Greifer, 0-deaktiviert; 1-aktiviert
    - ``IOEnable[8]``: Aktivierungsstatus IO-Gerät, 0-deaktiviert; 1-aktiviert
    - ``dexhandEnable``: Aktivierungsstatus dreifingrige Hand, 0-deaktiviert; 1-aktiviert"

Festlegen der aktivierten Greifer-Aktionssteuerungsfunktionen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleLuaGripperFunc(id, func)``"
    "Beschreibung", "Legt die aktivierten Greifer-Aktionssteuerungsfunktionen fest"
    "Erforderliche Parameter", "
    - ``id``: Greifer-Gerätenummer
    - ``func``: 0-Greifer aktivieren; 1-Greifer initialisieren; 2-Position einstellen; 3-Geschwindigkeit einstellen; 4-Drehmoment einstellen; 6-Greiferstatus lesen; 7-Initialisierungsstatus lesen; 8-Fehlercode lesen; 9-Position lesen; 10-Geschwindigkeit lesen; 11-Drehmoment lesen; 12-Drehzahl für Drehgreifer einstellen; 13-Drehgeschwindigkeit für Drehgreifer einstellen; 14-Drehmoment für Drehgreifer einstellen; 15-Drehgreiferstatus lesen; 16-Initialisierungsstatus Drehgreifer lesen; 17-Drehzahl Drehgreifer lesen; 18-Drehgeschwindigkeit Drehgreifer lesen; 19-Drehmoment Drehgreifer lesen; 20-Mehrachs-Synchronbewegung einstellen; 21-Fehlerlöschbefehl; 22-Einzelachsen-Betriebsstatus; 23-Alle-Achsen-Betriebsstatus;"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode, 0-Erfolg; ungleich Null-Fehler"

Abrufen der aktivierten Greifer-Aktionssteuerungsfunktionen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaGripperFunc(id)``"
    "Beschreibung", "Ruft die aktivierten Greifer-Aktionssteuerungsfunktionen ab"
    "Erforderliche Parameter", "- ``id``: Greifer-Gerätenummer"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode, 0-Erfolg; ungleich Null-Fehler
    - ``func``: 0-Greifer aktivieren; 1-Greifer initialisieren; 2-Position einstellen; 3-Geschwindigkeit einstellen; 4-Drehmoment einstellen; 6-Greiferstatus lesen; 7-Initialisierungsstatus lesen; 8-Fehlercode lesen; 9-Position lesen; 10-Geschwindigkeit lesen; 11-Drehmoment lesen; 12-Drehzahl für Drehgreifer einstellen; 13-Drehgeschwindigkeit für Drehgreifer einstellen; 14-Drehmoment für Drehgreifer einstellen; 15-Drehgreiferstatus lesen; 16-Initialisierungsstatus Drehgreifer lesen; 17-Drehzahl Drehgreifer lesen; 18-Drehgeschwindigkeit Drehgreifer lesen; 19-Drehmoment Drehgreifer lesen; 20-Mehrachs-Synchronbewegung einstellen; 21-Fehlerlöschbefehl; 22-Einzelachsen-Betriebsstatus; 23-Alle-Achsen-Betriebsstatus;"

In Ethercat-Slave-Datei des Roboters schreiben
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SlaveFileWrite(type, slaveID, fileName)``"
    "Beschreibung", "In Ethercat-Slave-Datei des Roboters schreiben (Firmware/Konfiguration updaten)"
    "Erforderliche Parameter", "- ``type``: Slave-Dateityp, 1 = Upgrade Slave-Datei, 2 = Upgrade Slave-Konfigurationsdatei
    - ``slaveID``: Slave-Nummer
    - ``fileName``: Name der hochzuladenden Datei (auf dem Roboter?)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Endeffektor-Lua-Open-Protocol-Datei hochladen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleLuaUpload(filePath)``"
    "Beschreibung", "Endeffektor-Lua-Open-Protocol-Datei hochladen"
    "Erforderliche Parameter", "- ``filePath``: Lokaler Pfad zur Lua-Datei (z.B. .../AXLE_LUA_End_DaHuan.lua)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Ethercat-Slave des Roboters in den Boot-Modus versetzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSysServoBootMode()``"
    "Beschreibung", "Ethercat-Slave des Roboters in den Boot-Modus versetzen (für Firmware-Update)"
    "Erforderliche Parameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Endeffektor-LUA-Dateioperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua")
    param = [7, 8, 1, 0, 5, 3, 1]  # AxleComParam
    robot.SetAxleCommunicationParam(7, 8, 1, 0, 5, 3, 1)
    error,getParam0,getParam1,getParam2,getParam3,getParam4,getParam5,getParam6 = robot.GetAxleCommunicationParam()
    print(f"GetAxleCommunicationParam param is:{getParam0} {getParam1} {getParam2} {getParam3} {getParam4} {getParam5} {getParam6}")
    robot.SetAxleLuaEnable(1)
    error,luaEnableStatus = robot.GetAxleLuaEnableStatus()
    robot.SetAxleLuaEnableDeviceType(0, 1, 0)
    error, forceEnable, gripperEnable, ioEnable = robot.GetAxleLuaEnableDeviceType()
    print(f"GetAxleLuaEnableDeviceType param is: {forceEnable} {gripperEnable} {ioEnable}")
    func = [1] * 16  # Alle Funktionen aktivieren
    robot.SetAxleLuaGripperFunc(1, func)
    error,getFunc = robot.GetAxleLuaGripperFunc(1)
    error,getforceEnable, getgripperEnable, getioEnable = robot.GetAxleLuaEnableDevice()
    print("\ngetforceEnable status:", end=" ")
    for i in range(8):
        print(f"{getforceEnable[i]},", end="")
    print("\ngetgripperEnable status:", end=" ")
    for i in range(8):
        print(f"{getgripperEnable[i]},", end="")
    print("\ngetioEnable status:", end=" ")
    for i in range(8):
        print(f"{getioEnable[i]},", end="")
    print()
    robot.ActGripper(1, 0)
    time.sleep(2)
    robot.ActGripper(1, 1)
    time.sleep(2)
    robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0)
    while True:
        error,pkg = robot.GetRobotRealTimeState()
        print(f"gripper pos is:{pkg.gripper_position}")
        time.sleep(0.1)
    robot.CloseRPC()

SmartTool-Tastenstatus abrufen
+++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSmarttoolBtnState()``"
    "Beschreibung", "SmartTool-Tastenstatus abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``state``: SmartTool-Griff Tastenstatus (Bit0: 0 = Kommunikation normal, 1 = Kommunikation unterbrochen; Bit1 = Rückgängig; Bit2 = Programm löschen; Bit3 = Taste A; Bit4 = Taste B; Bit5 = Taste C; Bit6 = Taste D; Bit7 = Taste E; Bit8 = IO-Taste; Bit9 = Hand/Automatik; Bit10 = Start)"

Codebeispiel für SmartTool-Tasten
++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    while True:
        error,state = robot.GetSmarttoolBtnState()
        print(f"{state:016b}")
        time.sleep(0.1)

Krafterkennung vor dem Führen einstellen
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTorqueDetectionSwitch(flag)``"
    "Beschreibung", "Krafterkennung vor dem Führen einstellen (Lastprüfung)"
    "Erforderliche Parameter", "- ``flag``: 0 = aus, 1 = an"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Peripherie Ein-/Ausschalten
++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingLaserOnOff(OnOff, weldId)``"
    "Beschreibung", "Laser-Peripherie Ein-/Ausschalten"
    "Erforderliche Parameter", "- ``OnOff``: 0 = aus, 1 = ein"
    "Standardparameter", "- ``weldId``: Schweißnaht-ID, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Tracking Start/Stopp
+++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingTrackOnOff(OnOff, coordId)``"
    "Beschreibung", "Laser-Tracking Start/Stopp"
    "Erforderliche Parameter", "- ``OnOff``: 0 = stopp, 1 = start
    - ``coordId``: Werkzeugkoordinatennummer des Laser-Peripheriegeräts"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lasernahtsuche starten - feste Richtung
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSearchStart_xyz(direction, vel, distance, timeout, posSensorNum)``"
    "Beschreibung", "Lasernahtsuche starten - feste Richtung"
    "Erforderliche Parameter", "- ``direction``: 0 = x+, 1 = x-, 2 = y+, 3 = y-, 4 = z+, 5 = z-
    - ``vel``: Geschwindigkeit [%]
    - ``distance``: Maximale Suchdistanz [mm]
    - ``timeout``: Such-Timeout [ms]
    - ``posSensorNum``: Nummer des kalibrierten Laser-Werkzeugkoordinatensystems"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lasernahtsuche starten - Richtung durch Punkt vorgegeben
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSearchStart_point(directionPoint, vel, distance, timeout, posSensorNum)``"
    "Beschreibung", "Lasernahtsuche starten - Richtung durch Punkt vorgegeben"
    "Erforderliche Parameter", "- ``directionPoint``: XYZ-Koordinaten des Richtungspunkts [x, y, z] (relativ)
    - ``vel``: Geschwindigkeit [%]
    - ``distance``: Maximale Suchdistanz [mm]
    - ``timeout``: Such-Timeout [ms]
    - ``posSensorNum``: Nummer des kalibrierten Laser-Werkzeugkoordinatensystems"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-IP-Konfiguration
++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSensorConfig(ip, port)``"
    "Beschreibung", "Laser-IP-Konfiguration"
    "Erforderliche Parameter", "- ``ip``: IP-Adresse des Laser-Peripheriegeräts
    - ``port``: Portnummer des Laser-Peripheriegeräts"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Peripherie-Abtastperiode konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSensorSamplePeriod(period)``"
    "Beschreibung", "Laser-Peripherie-Abtastperiode konfigurieren"
    "Erforderliche Parameter", "- ``period``: Abtastperiode [ms]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Peripherie-Treiber laden
+++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadPosSensorDriver(type)``"
    "Beschreibung", "Laser-Peripherie-Treiber laden"
    "Erforderliche Parameter", "- ``type``: Protokolltyp des Laser-Peripherietreibers: 101 = RuiNiu, 102 = ChuangXiang, 103 = QuanShi, 104 = TongZhou, 105 = AoTai"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Peripherie-Treiber entladen
++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``UnLoadPosSensorDriver()``"
    "Beschreibung", "Laser-Peripherie-Treiber entladen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Schweißnaht-Trajektorie aufzeichnen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserSensorRecord1(status, delayTime)``"
    "Beschreibung", "Laser-Schweißnaht-Trajektorie aufzeichnen"
    "Erforderliche Parameter", "- ``status``: 0 = Aufzeichnung stoppen, 1 = Echtzeit-Tracking, 2 = Aufzeichnung starten
    - ``delayTime``: Verzögerungszeit [ms]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Schweißnaht-Trajektorie wiedergeben
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserSensorReplay(delayTime, speed)``"
    "Beschreibung", "Laser-Schweißnaht-Trajektorie wiedergeben"
    "Erforderliche Parameter", "- ``delayTime``: Verzögerungszeit [ms]
    - ``speed``: Geschwindigkeit [%]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Tracking-Wiedergabe (MoveLTR)
++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveLTR()``"
    "Beschreibung", "Laser-Tracking-Wiedergabe (Bewegung entlang der aufgezeichneten Trajektorie)"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Laser-Schweißnaht-Trajektorie aufzeichnen und wiedergeben (erweitert)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserSensorRecordandReplay(delayMode, delayTime, delayDisExAxisNum, delayDis, sensitivePara, trackMode, triggerMode, runTime, speed)``"
    "Beschreibung", "Laser-Schweißnaht-Trajektorie aufzeichnen und wiedergeben (erweiterte Funktion)"
    "Erforderliche Parameter", "- ``delayMode``: Modus, 0 = Verzögerungszeit, 1 = Verzögerungsdistanz
    - ``delayTime``: Verzögerungszeit [ms] (wenn delayMode=0)
    - ``delayDisExAxisNum``: Erweiterungsachsennummer für Distanzverzögerung
    - ``delayDis``: Verzögerungsdistanz [mm] (wenn delayMode=1)
    - ``sensitivePara``: Kompensations-Empfindlichkeitskoeffizient
    - ``trackMode``: Punkt-Tracking-Typ: 0 = Erweiterungsachse asynchron, 1 = Roboter (synchron?)
    - ``triggerMode``: Punkt-Tracking-Auslösemodus: 0 = Tracking-Dauer, 1 = IO
    - ``runTime``: Dauer des Roboter-Punkt-Trackings [s]
    - ``speed``: Geschwindigkeit [%]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Zum aufgezeichneten Startpunkt der Schweißnaht bewegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToLaserRecordStart(moveType, ovl)``"
    "Beschreibung", "Zum aufgezeichneten Startpunkt der Schweißnaht bewegen"
    "Erforderliche Parameter", "- ``moveType``: 0 = PTP, 1 = LIN
    - ``ovl``: Geschwindigkeit [%]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Zum aufgezeichneten Endpunkt der Schweißnaht bewegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToLaserRecordEnd(moveType, ovl)``"
    "Beschreibung", "Zum aufgezeichneten Endpunkt der Schweißnaht bewegen"
    "Erforderliche Parameter", "- ``moveType``: 0 = PTP, 1 = LIN
    - ``ovl``: Geschwindigkeit [%]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Zum vom Laser-Sensor gefundenen Nahtpunkt bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToLaserSeamPos(moveFlag, ovl, dataFlag, plateType, trackOffectType, offset)``"
    "Beschreibung", "Zum vom Laser-Sensor gefundenen Nahtpunkt bewegen"
    "Erforderliche Parameter", "- ``moveFlag``: Bewegungstyp, 0 = PTP, 1 = LIN
    - ``ovl``: Geschwindigkeitsskalierungsfaktor [0-100]
    - ``dataFlag``: Auswahl der Schweißnaht-Cache-Daten: 0 = Planungsdaten ausführen, 1 = Aufgezeichnete Daten ausführen
    - ``plateType``: Plattenmaterial-Typ: 0 = Wellenplatte, 1 = Wellpappe, 2 = Zaunplatte, 3 = Ölfass, 4 = Wellenpanzerstahl
    - ``trackOffectType``: Laser-Sensor-Versatztyp: 0 = kein Versatz, 1 = Versatz im Basiskoordinatensystem, 2 = Versatz im Werkzeugkoordinatensystem, 3 = Versatz basierend auf Laser-Sensor-Rohdaten
    - ``offset``: Versatzwert [x, y, z, rx, ry, rz]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Koordinaten des vom Laser-Sensor gefundenen Nahtpunkts abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserSeamPos(trackOffectType, offset)``"
    "Beschreibung", "Koordinaten des vom Laser-Sensor gefundenen Nahtpunkts abrufen"
    "Erforderliche Parameter", "- ``trackOffectType``: Laser-Sensor-Versatztyp (siehe MoveToLaserSeamPos)
    - ``offset``: Versatzwert [x, y, z, rx, ry, rz]"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``jPos``: Gelenkposition [°] (Liste von 6 Werten)
    - ``descPos``: Kartesische Position [mm, °] (Liste von 6 Werten)
    - ``tool``: Verwendetes Werkzeugkoordinatensystem
    - ``user``: Verwendetes Werkstückkoordinatensystem
    - ``exaxis``: Position der Erweiterungsachse [mm] (Liste von 4 Werten)"

Codebeispiel für Laser-Peripherie-Sensorparametrierung und -Debugging
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.LaserTrackingSensorConfig("192.168.58.20", 5020)
    robot.LaserTrackingSensorSamplePeriod(20)
    robot.LoadPosSensorDriver(101)
    robot.LaserTrackingLaserOnOff(0, 0)
    time.sleep(3)
    robot.LaserTrackingLaserOnOff(1, 0)
    robot.CloseRPC()

Codebeispiel für Laser-Trajektorienscan und -wiedergabe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    i = 0
    while i<10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(2, 10)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose,tool= 1,user= 0,vel= 50,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(0, 10)
        robot.MoveToLaserRecordStart(1, 30)
        robot.LaserSensorReplay(10, 100)
        robot.MoveLTR()
        robot.LaserSensorRecord1(0, 10)
        i = i+1
    robot.CloseRPC()

Codebeispiel für Lasernahtsuche und Echtzeit-Tracking
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    time.sleep(8)
    i = 0
    while i < 10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        directionPoint = [0.0] * 3
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3)
        robot.LaserTrackingSearchStop()
        robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese)
        robot.LaserTrackingTrackOnOff(1, 3)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=20, acc=100, ovl=100, blendR=-1, exaxis_pos=exaxisPos, search=0, offset_flag=0, offset_pos=offdese, overSpeedStrategy=1, speedPercent=1)
        robot.LaserTrackingTrackOnOff(0, 3)  # Tracking stoppen
        print(f"Durchlauf {i+1} abgeschlossen")
    robot.CloseRPC()

Codebeispiel für synchrones Laser-Tracking mit Erweiterungsachse und Roboter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    startexaxisPos = [0.0, 0.0, 0.0, 0.0]
    seamexaxisPos = [-10.0, 0.0, 0.0, 0.0]
    endexaxisPos = [-30.0, 0.0, 0.0, 0.0]
    offdese = [0.0] * 6
    seamjointPos = [0.0] * 6
    seamdescPose = [0.0] * 6
    i=0
    while i < 10:
        startjointPos = [58.337, -119.628, 146.037, -116.358, -92.224, -117.654]
        startdescPose = [-53.375, -255.363, 0.919, 178.054, 1.077, -94.026]
        robot.ExtAxisSyncMoveJ(joint_pos=startjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= startexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
        ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2)
        robot.LaserTrackingSearchStop()
        tool = 0
        user = 0
        rnte, seamjointPos, seamdescPose, tool, user, startexaxisPos = robot.GetLaserSeamPos(0, offdese)
        print(f"{seamjointPos[0]},{seamjointPos[1]},{seamjointPos[2]},{seamjointPos[3]},{seamjointPos[4]},{seamjointPos[5]},{seamdescPose[0]},{seamdescPose[1]},{seamdescPose[2]},{seamdescPose[3]},{seamdescPose[4]},{seamdescPose[5]}")
        if ret == 0:
            robot.ExtAxisSyncMoveJ(joint_pos=seamjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= seamexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(1, 2)
            endjointPos = [70.580, -90.918, 126.593, -125.154, -92.162, -105.403]
            enddescPose = [-53.375, -419.020, 0.920, 178.054, 1.076, -94.026]
            robot.ExtAxisSyncMoveL(desc_pos=enddescPose, tool=1,user= 0,vel= 20,acc= 100, ovl=100,blendR= -1,exaxis_pos= endexaxisPos,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(0, 2)
        i = i+1
        print(i)
    robot.CloseRPC()

Array-Saugnapf steuern
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSuckerCtrl(slaveID, len, ctrlValue)``"
    "Beschreibung", "Array-Saugnapf steuern"
    "Erforderliche Parameter", "- ``slaveID``: Slave-Stationsnummer
    - ``len``: Länge
    - ``ctrlValue``: Steuerwert 1-Saugen mit maximalem Vakuum 2-Saugen mit eingestelltem Vakuum 3-Saugen stoppen"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Array-Saugnapf-Status abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSuckerState(slaveID)``"
    "Beschreibung", "Array-Saugnapf-Status abrufen"
    "Erforderliche Parameter", "- ``slaveID``: Slave-Stationsnummer"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode
    - ``state``: Saugstatus 0-Objekt freigegeben 1-Werkstück erfolgreich angesaugt 2-Kein Objekt angesaugt 3-Objekt abgelöst
    - ``pressValue``: Aktueller Vakuumdruck Einheit kPa
    - ``error``: Aktueller Fehlercode des Saugnapfs"

Auf Saugnapf-Status warten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitSuckerState(slaveID, state, ms)``"
    "Beschreibung", "Auf Saugnapf-Status warten"
    "Erforderliche Parameter", "- ``slaveID``: Slave-Stationsnummer
    - ``state``: Saugstatus 0-Objekt freigegeben 1-Werkstück erfolgreich angesaugt 2-Kein Objekt angesaugt 3-Objekt abgelöst
    - ``ms``: Maximale Wartezeit"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Codebeispiel für Array-Saugnapf-Steuerbefehle
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung mit der Robotersteuerung herstellen, bei Erfolg wird ein Roboter-Objekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("C://Projekt/PeripherieSDK/CtrlDev_sucker.lua")
    time.sleep(2)
    robot.UnloadCtrlOpenLUA(1)
    robot.LoadCtrlOpenLUA(1)
    time.sleep(1)
    ctrl = bytearray(20)
    ctrl[0] = 1
    robot.SetSuckerCtrl(0, 1, ctrl)
    for i in range(100):
        rtn, state, press_value, error = robot.GetSuckerState(1)
        print(f"sucker1 state is {state}, pressValue is {press_value}, error num is {error}")
        rtn, state, press_value, error = robot.GetSuckerState(12)
        print(f"sucker12 state is {state}, pressValue is {press_value}, error num is {error}")
        time.sleep(0.1)
    ret = robot.WaitSuckerState(1, 1, 100)
    print(f"WaitSuckerState result is {ret}")
    ctrl[0] = 3
    robot.SetSuckerCtrl(1, 1, ctrl)
    robot.SetSuckerCtrl(12, 1, ctrl)
    robot.CloseRPC()

Open-Protocol-Lua-Datei hochladen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OpenLuaUpload(filePath)``"
    "Beschreibung", "Open-Protocol-Lua-Datei hochladen"
    "Erforderliche Parameter", "- ``filePath``: Lokaler Pfad der Open-Protocol-Lua-Datei"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Slave-Stationskartenparameter abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetFieldBusConfig()``"
    "Beschreibung", "Slave-Stationskartenparameter abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode
    - ``type``: 0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    - ``version``: Protokollversion
    - ``connState``: 0-Nicht verbunden 1-Verbunden"

Slave-Station DO schreiben
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWriteDO(DOIndex, writeNum, status)``"
    "Beschreibung", "Slave-Station DO schreiben"
    "Erforderliche Parameter", "- ``DOIndex``: DO-Nummer
    - ``writeNum``: Anzahl zu schreibender Werte
    - ``status``: Zu schreibende Werte, maximal 8"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Slave-Station AO schreiben
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWriteAO(AOIndex, writeNum, status)``"
    "Beschreibung", "Slave-Station AO schreiben"
    "Erforderliche Parameter", "- ``AOIndex``: AO-Nummer
    - ``writeNum``: Anzahl zu schreibender Werte
    - ``status``: Zu schreibende Werte, maximal 8"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Slave-Station DI lesen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveReadDI(DIIndex, readNum)``"
    "Beschreibung", "Slave-Station DI lesen"
    "Erforderliche Parameter", "- ``DIIndex``: DI-Nummer
    - ``readNum``: Anzahl zu lesender Werte"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode
    - ``status[8]``: Gelesene Werte, maximal 8"

Slave-Station AI lesen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveReadAI(AIIndex, readNum)``"
    "Beschreibung", "Slave-Station AI lesen"
    "Erforderliche Parameter", "- ``AIIndex``: AI-Nummer
    - ``readNum``: Anzahl zu lesender Werte"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode
    - ``status[8]``: Gelesene Werte, maximal 8"

Auf erweiterten DI-Eingang warten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWaitDI(DIIndex, status, waitMs)``"
    "Beschreibung", "Auf erweiterten DI-Eingang warten"
    "Erforderliche Parameter", "- ``DIIndex``: DI-Nummer
    - ``status``: 0-Low-Pegel; 1-High-Pegel
    - ``waitMs``: Maximale Wartezeit (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Auf erweiterten AI-Eingang warten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWaitAI(AIIndex, waitType, value, waitMs)``"
    "Beschreibung", "Auf erweiterten AI-Eingang warten"
    "Erforderliche Parameter", "- ``AIIndex``: AI-Nummer
    - ``waitType``: 0-Größer als; 1-Kleiner als
    - ``value``: AI-Wert
    - ``waitMs``: Maximale Wartezeit (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Codebeispiel für Slave-Stationsmodus-bezogene Schnittstellenbefehle
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung mit der Robotersteuerung herstellen, bei Erfolg wird ein Roboter-Objekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/Peripherie/CtrlDev_field.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(3,"CtrlDev_field.lua")
    robot.UnloadCtrlOpenLUA(3)
    robot.LoadCtrlOpenLUA(3)
    time.sleep(8)
    rtn,type, version, conn_state = robot.GetFieldBusConfig()
    print(f"type is {type}, version is {version}, connState is {conn_state}")
    # Write digital outputs
    ctrl = [1, 0, 1]  # DO0=1, DO1=0, DO2=1
    robot.FieldBusSlaveWriteDO(0, 3, ctrl)
    # Write analog output
    ctrl_ao = [0x1000]  # AO2 = 0x1000
    robot.FieldBusSlaveWriteAO(2, 1, ctrl_ao)
    for i in range(100):
        rtn,di = robot.FieldBusSlaveReadDI(0, 4)
        print(f"DI0 is {di[0]}, DI1 is {di[1]}, DI2 is {di[2]}, DI3 is {di[3]}")
        rtn, ai = robot.FieldBusSlaveReadAI(0, 3)
        print(f"AI0 is {ai[0]}, AI1 is {ai[1]}, AI2 is {ai[2]}")
        time.sleep(0.01)
    ret = robot.FieldBusSlaveWaitDI(0, 1, 100)
    print(f"FieldBusSlaveWaitDI result is {ret}")
    ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00, 100)
    print(f"FieldBusSlaveWaitAI result is {ret}")
    robot.CloseRPC()

Endeffektor-Transparentübertragungsfunktion ein-/ausschalten SDK-Schnittstelle
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleGenComEnable(mode)``"
    "Beschreibung", "Allgemeine Transparentübertragungsfunktion des Endeffektors aktivieren"
    "Erforderliche Parameter", "- ``mode``: Aktivierung, 0-deaktiviert, 1-aktiviert"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Endeffektor-Transparentübertragungsfunktion für azyklische Datenübertragung und -empfang SDK-Schnittstelle
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SndRcvAxleGenComCmdData(len_snd, sndBuff, len_rcv)``"
    "Beschreibung", "Endeffektor sendet azyklische Daten und wartet auf Antwort"
    "Erforderliche Parameter", "
    - ``len_snd``: Länge der zu sendenden Daten;
    - ``sndBuff[]``: Zu sendende Daten;
    - ``len_rcv``: Länge der zu empfangenden Daten;
    - ``rcvBuff[]``: Antwortdaten;"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Codebeispiel für azyklische Datenkommunikation des DIO Health Care Moxibustion-Kopfs basierend auf der Endeffektor-Transparentübertragungsfunktion
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    from ctypes import sizeof
    # Verbindung mit der Robotersteuerung herstellen, bei Erfolg wird ein Roboter-Objekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')

    import time


    def testAxleGenCom(self):

        led_on = [0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79]
        led_off = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        version = [0xAB, 0xBA, 0x11, 0x00, 0x76]
        state = [0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B]
        cycleState = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        cnt = 1

        p1Joint = [88.708, -86.178, 140.989, -141.825, -89.162, -49.879]
        p1Desc = [188.007, -377.850, 260.207, 178.715, 2.823, -131.466]
        p2Joint = [112.131, -75.554, 126.989, -139.027, -88.044, -26.477]
        p2Desc = [368.003, -377.848, 260.211, 178.715, 2.823, -131.465]

        exaxisPos = [0, 0, 0, 0]
        offdese = [0, 0, 0, 0, 0, 0]

        #Endeffektor-Transparentübertragungsfunktion aktivieren
        robot.SetAxleGenComEnable(1)
        robot.SetAxleLuaEnable(1)

        while cnt <= 10000:
            #Versionsnummer auslesen
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(len_snd=5, sndBuff=version, len_rcv=10)
            print(ret)
            print(rcvdata)
            print(f"hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}")
            if ret != 0:
                break
            time.sleep(1)
            # Präsenzstatus des Moxibustion-Kopfs auslesen
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, state, 6)
            print(f"state : {rcvdata[4]} ")
            time.sleep(1)
            # Laser des Moxibustion-Kopfs einschalten
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, led_on, 6)
            print(f"led on rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p1Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,
                            offset_flag=0, offset_pos=offdese)
            time.sleep(4)
            # Laser des Moxibustion-Kopfs ausschalten
            ret, rcvdata = robot.SndRcvAxleGenComCmdData(6, led_off, 6)
            print(f"led off rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p2Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,offset_flag=0, offset_pos=offdese)
            time.sleep(1)
            print(f"***********************complate No. {cnt} SDK test*****************************")
            cnt = cnt + 1

        robot.CloseRPC()
        return 0

    testAxleGenCom(robot)
    
Open-Protocol-Lua-Datei herunterladen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OpenLuaDownload(fileName, savePath)``"
    "Beschreibung", "Open-Protocol-Lua-Datei herunterladen"
    "Erforderliche Parameter", "
    - ``fileName``: Name der Open-Protocol-Datei `CtrlDev_XXX.lua`;
    - ``savePath``: Pfad zum Speichern der Open-Protocol-Datei;
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Bestimmte Open-Protocol-Lua-Datei löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OpenLuaDelete(fileName)``"
    "Beschreibung", "Bestimmte Open-Protocol-Lua-Datei löschen"
    "Erforderliche Parameter", "
    - ``fileName``: Name der zu löschenden Open-Protocol-Lua-Datei `CtrlDev_XXX.lua`
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Alle Open-Protocol-Lua-Dateien löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AllOpenLuaDelete()``"
    "Beschreibung", "Alle Open-Protocol-Lua-Dateien löschen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

SDK-Codebeispiel für Open-Protocol-Lua-Dateioperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')


    def TestCtrlOpenLuaOperate(self):
        # Lua-Datei auf Roboter hochladen
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        # Lua-Datei von Roboter herunterladen
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        # Steuerungs-Open-Protocol-Lua-Name festlegen
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        # Steuerungs-Open-Protocol-Lua-Name abrufen
        rtn, name = robot.GetCtrlOpenLUAName()
        print(f"ctrl open lua names : {name[0]}, {name[1]}, {name[2]}, {name[3]}")
        
        # Steuerungs-Open-Protocol-Lua laden
        rtn = robot.LoadCtrlOpenLUA(1)
        print(f"LoadCtrlOpenLUA rtn is {rtn}")
        time.sleep(2)
        
        # Steuerungs-Open-Protocol-Lua entladen
        rtn = robot.UnloadCtrlOpenLUA(1)
        print(f"UnloadCtrlOpenLUA rtn is {rtn}")
        
        # Bestimmte Lua-Datei löschen
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua")
        print(f"OpenLuaDelete rtn is {rtn}")
        
        # Alle Lua-Dateien löschen
        rtn = robot.AllOpenLuaDelete()
        print(f"AllOpenLuaDelete rtn is {rtn}")
        
        # Verbindung schließen
        robot.CloseRPC()
        time.sleep(1)


    # Testfunktion aufrufen
    TestCtrlOpenLuaOperate(robot)

Steuerung der Bewegung der Dreifingrigen Hand
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDexterousHandsMove(self, idstart, slaveNum, pos, speed, force, max_time)``"
    "Beschreibung", "Steuerung der Bewegung der dreifingrigen Hand"
    "Erforderliche Parameter", "
    - ``idstart``: Start-Slave-Stationsnummer;
    - ``slaveNum``: Anzahl;
    - ``pos[16]``: Position (-360~360);
    - ``speed[16]``: Geschwindigkeitsprozent, Bereich [0~100];
    - ``force[16]``: Drehmomentprozent, Bereich [0~100];
    - ``max_time``: Maximale Wartezeit, Bereich [0~30000], Einheit ms;"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode, 0-Erfolg; ungleich Null-Fehler"
        
Steuerung des Resets und der Aktivierung der Dreifingrigen Hand
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDexterousHandsAct(self, id, act)``"
    "Beschreibung", "Steuerung des Resets und der Aktivierung der dreifingrigen Hand"
    "Erforderliche Parameter", "
    - ``id``: Slave-Stationsnummer;
    - ``act``: 0-Reset 1-Aktivierung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode, 0-Erfolg; ungleich Null-Fehler"
        
Löschen von Fehlern der Dreifingrigen Hand
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ClearDexterousHandsError(self)``"
    "Beschreibung", "Löschen von Fehlern der dreifingrigen Hand"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode, 0-Erfolg; ungleich Null-Fehler"
    
Festlegen der Aktivierten Aktionssteuerungsfunktionen der Dreifingrigen Hand
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDexterousHandsFunc(self, id, func)``"
    "Beschreibung", "Legt die aktivierten Aktionssteuerungsfunktionen der dreifingrigen Hand fest"
    "Erforderliche Parameter", "
    - ``id``: Slave-Stationsnummer der dreifingrigen Hand;
    - ``func``: Funktionsarray, 32 Elemente
        0-Greifauslösung, 1-Greiferinitialisierung, 2-Positionseinstellung, 3-Geschwindigkeitseinstellung, 4-Drehmomenteinstellung,
        6-Greiferstatus lesen, 7-Initialisierungsstatus lesen, 8-Fehlercode lesen, 9-Position lesen, 10-Geschwindigkeit lesen,
        11-Drehmoment lesen, 12-Drehzahl einstellen, 13-Drehgeschwindigkeit einstellen, 14-Drehmoment einstellen,
        15-Drehgreiferstatus lesen, 16-Dreh-Initialisierungsstatus lesen, 17-Drehzahl lesen, 18-Drehgeschwindigkeit lesen,
        19-Drehmoment lesen, 20-Mehrachsen-Synchronbewegung einstellen, 21-Fehlerlöschbefehl, 22-Einzelachsen-Betriebsstatus,
        23-Alle-Achsen-Betriebsstatus"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode, 0-Erfolg; ungleich Null-Fehler"
    
Abrufen der Aktivierten Aktionssteuerungsfunktionen der Dreifingrigen Hand
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDexterousHandsFunc(self, id)``"
    "Beschreibung", "Ruft die aktivierten Aktionssteuerungsfunktionen der dreifingrigen Hand ab"
    "Erforderliche Parameter", "
    - ``id``: Slave-Stationsnummer der dreifingrigen Hand;
    - ``func``: Funktionsarray, 32 Elemente
        0-Greifauslösung, 1-Greiferinitialisierung, 2-Positionseinstellung, 3-Geschwindigkeitseinstellung, 4-Drehmomenteinstellung,
        6-Greiferstatus lesen, 7-Initialisierungsstatus lesen, 8-Fehlercode lesen, 9-Position lesen, 10-Geschwindigkeit lesen,
        11-Drehmoment lesen, 12-Drehzahl einstellen, 13-Drehgeschwindigkeit einstellen, 14-Drehmoment einstellen,
        15-Drehgreiferstatus lesen, 16-Dreh-Initialisierungsstatus lesen, 17-Drehzahl lesen, 18-Drehgeschwindigkeit lesen,
        19-Drehmoment lesen, 20-Mehrachsen-Synchronbewegung einstellen, 21-Fehlerlöschbefehl, 22-Einzelachsen-Betriebsstatus,
        23-Alle-Achsen-Betriebsstatus"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode, 0-Erfolg; ungleich Null-Fehler"

Codebeispiel für Konfiguration und Bewegung der Dreifingrigen Hand am Endeffektor  
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:  
     
    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')

    def main(self):

        id = 1                 
        slaveNum = 4         
        max_time = 8000      
        speed = [0] * 16     
        force = [0] * 16     

        for i in range(16):
            force[i] = 50 if i < 4 else 0

        def set_positions(v1, v2, v3, v4):
            pos = [0.0] * 16
            pos[0] = v1
            pos[1] = v2
            pos[2] = v3
            pos[3] = v4
            return pos

        j1 = [-53.426,-85.916,109.280,-86.236,-96.663,-28.560]
        j2 = [-91.877,-85.917,109.281,-86.236,-96.663,-28.560]
        epos = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]

        ret = robot.ClearDexterousHandsError()
        print(f"ClearDexterousHandsError -> {ret}")

        setFunc = [0] * 32
        setFunc[2] = 1   
        setFunc[4] = 1   
        setFunc[9] = 1   
        setFunc[10] = 1  
        setFunc[11] = 1  
        setFunc[22] = 1  

        ret = robot.SetDexterousHandsFunc(id, setFunc)
        print(f"SetDexterousHandsFunc(Init + Positions-/Drehmomentfunktionen aktiviert) -> {ret}")

        ret, getFunc = robot.GetDexterousHandsFunc(id)
        print(f"GetDexterousHandsFunc -> {ret}")
        if ret == 0:
            print("GetDexterousHandsFunc :")
            for i in range(len(getFunc)):
                print(f"  [{i}]={getFunc[i]}", end="")
                if (i + 1) % 8 == 0:
                    print()  
                elif i < len(getFunc) - 1:
                    print(", ", end="")
            if len(getFunc) % 8 != 0:

        ret = robot.SetDexterousHandsAct(id, 1)
        print(f"SetDexterousHandsAct() -> {ret}")
        if ret != 0:
            return
            pos = set_positions(20, 20, 20, 20)
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
        print(f"ret: {ret}")
        time.sleep(5)

        for iteration in range(1, 11):
            robot.MoveJ(joint_pos=j1, tool=1, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

            pos = set_positions(10, 10, 10, 10)
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
            time.sleep(1)

            robot.MoveJ(joint_pos=j2, tool=1, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

            pos = set_positions(50, 50, 50, 50)
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
            time.sleep(1)

    main(robot)    