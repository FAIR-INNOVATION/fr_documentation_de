Roboter-Trajektorienwiedergabe
==============================

.. toctree::
    :maxdepth: 5

TPD-Trajektorienaufzeichnungsparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTPDParam(name, period_ms, type=1, di_choose=0, do_choose=0)``"
    "Beschreibung", "TPD-Trajektorienaufzeichnungsparameter einstellen"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei
    - ``period_ms``: Datenabtastperiode, feste Werte: 2ms, 4ms oder 8ms"
    "Standardparameter", "- ``type``: Datentyp für die Aufzeichnung, 1 = Gelenkpositionen, Standard = 1
    - ``di_choose``: DI-Auswahl, Bit0~Bit7 für Steuerkasten DI0~DI7, Bit8~Bit9 für Endeffektor DI0~DI1, 0 = nicht ausgewählt, 1 = ausgewählt, Standard = 0
    - ``do_choose``: DO-Auswahl, Bit0~Bit7 für Steuerkasten DO0~DO7, Bit8~Bit9 für Endeffektor DO0~DO1, 0 = nicht ausgewählt, 1 = ausgewählt, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

TPD-Trajektorienaufzeichnung starten
+++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTPDStart(name, period_ms, type=1, di_choose=0, do_choose=0)``"
    "Beschreibung", "TPD-Trajektorienaufzeichnung starten"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei
    - ``period_ms``: Datenabtastperiode, feste Werte: 2ms, 4ms oder 8ms"
    "Standardparameter", "- ``type``: Datentyp für die Aufzeichnung, 1 = Gelenkpositionen, Standard = 1
    - ``di_choose``: DI-Auswahl, Bit0~Bit7 für Steuerkasten DI0~DI7, Bit8~Bit9 für Endeffektor DI0~DI1, 0 = nicht ausgewählt, 1 = ausgewählt, Standard = 0
    - ``do_choose``: DO-Auswahl, Bit0~Bit7 für Steuerkasten DO0~DO7, Bit8~Bit9 für Endeffektor DO0~DO1, 0 = nicht ausgewählt, 1 = ausgewählt, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

TPD-Trajektorienaufzeichnung stoppen
+++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWebTPDStop()``"
    "Beschreibung", "TPD-Trajektorienaufzeichnung stoppen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

TPD-Trajektoriendatei löschen
++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTPDDelete(name)``"
    "Beschreibung", "TPD-Trajektoriendatei löschen"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für TPD-Trajektorienaufzeichnung
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    robot.SetTPDParam(name, period_ms)
    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(1)
    robot.SetTPDStart(name, period_ms)
    print("SetTPDStart")
    time.sleep(10)
    robot.SetWebTPDStop()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

TPD-Trajektorie vorladen
++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadTPD(name)``"
    "Beschreibung", "TPD-Trajektorie vorladen"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

TPD-Trajektorie wiedergeben
++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveTPD(name, blend, ovl)``"
    "Beschreibung", "TPD-Trajektorie wiedergeben"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei
    - ``blend``: Glättung, 0 = nein, 1 = ja
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, Bereich [0~100]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Startpose einer TPD-Trajektorie abrufen
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTPDStartPose(name)``"
    "Beschreibung", "Startpose einer TPD-Trajektorie abrufen"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``desc_pose = [x, y, z, rx, ry, rz]``: Startpose der Trajektorie [mm, °]"

Codebeispiel für Roboter-TPD-Trajektorienwiedergabe
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    ovl = 100.0
    blend = 0
    rtn = robot.LoadTPD(name)
    print(f"LoadTPD rtn is: {rtn}")
    error,start_pose = robot.GetTPDStartPose(name)
    print(f"start pose, xyz is: {start_pose[0]},{start_pose[1]},{start_pose[2]}. "
          f"rpy is: {start_pose[3]},{start_pose[4]},{start_pose[5]}")
    robot.MoveCart(start_pose, 0, 0, 100, 100)
    time.sleep(1)
    rtn = robot.MoveTPD(name, blend, ovl)
    print(f"MoveTPD rtn is: {rtn}")
    time.sleep(5)
    robot.SetTPDDelete(name)
    robot.CloseRPC()

Trajektorie vorverarbeiten (für MoveTrajectoryJ)
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadTrajectoryJ(name, ovl, opt=1)``"
    "Beschreibung", "Externe Trajektoriendatei vorverarbeiten (für MoveTrajectoryJ)"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei, z.B.: /fruser/traj/trajHelix_aima_1.txt
    - ``ovl``: Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]"
    "Standardparameter", "- ``opt``: 1 = Kontrollpunkt, Standard = 1"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Trajektorie wiedergeben (für MoveTrajectoryJ)
++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveTrajectoryJ()``"
    "Beschreibung", "Externe Trajektoriendatei wiedergeben (für MoveTrajectoryJ)"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Startpose einer Trajektorie abrufen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTrajectoryStartPose(name)``"
    "Beschreibung", "Startpose einer Trajektorie abrufen"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``desc_pose = [x, y, z, rx, ry, rz]``: Startpose der Trajektorie [mm, °]"

Nummer des aktuellen Trajektorienpunkts abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTrajectoryPointNum()``"
    "Beschreibung", "Nummer des aktuellen Trajektorienpunkts abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``pnum``: Aktuelle Trajektorienpunktnummer"

Geschwindigkeit während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJSpeed(ovl)``"
    "Beschreibung", "Geschwindigkeit während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``ovl``: Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kraft und Drehmoment während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceTorque(ft)``"
    "Beschreibung", "Kraft und Drehmoment während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``ft = [fx, fy, fz, tx, ty, tz]``: Kräfte [N] und Momente [Nm]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kraft in X-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceFx(fx)``"
    "Beschreibung", "Kraft in X-Richtung während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``fx``: Kraft in X-Richtung [N]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kraft in Y-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceFy(fy)``"
    "Beschreibung", "Kraft in Y-Richtung während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``fy``: Kraft in Y-Richtung [N]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kraft in Z-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceFz(fz)``"
    "Beschreibung", "Kraft in Z-Richtung während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``fz``: Kraft in Z-Richtung [N]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Drehmoment um die X-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJTorqueTx(tx)``"
    "Beschreibung", "Drehmoment um die X-Achse während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``tx``: Drehmoment um die X-Achse [Nm]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Drehmoment um die Y-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJTorqueTy(ty)``"
    "Beschreibung", "Drehmoment um die Y-Achse während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``ty``: Drehmoment um die Y-Achse [Nm]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Drehmoment um die Z-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJTorqueTz(tz)``"
    "Beschreibung", "Drehmoment um die Z-Achse während der Trajektorienausführung einstellen"
    "Erforderliche Parameter", "- ``tz``: Drehmoment um die Z-Achse [Nm]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Trajektorien-J-Datei hochladen
+++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TrajectoryJUpLoad(filePath)``"
    "Beschreibung", "Trajektorien-J-Datei hochladen"
    "Erforderliche Parameter", "- ``filePath``: Vollständiger Pfad zur hochzuladenden Trajektoriendatei, z.B. C://test/testJ.txt"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Trajektorien-J-Datei löschen
+++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TrajectoryJDelete(filePath)``"
    "Beschreibung", "Trajektorien-J-Datei löschen"
    "Erforderliche Parameter", "- ``filePath``: Vollständiger Pfad zur zu löschenden Trajektoriendatei, z.B. C://test/testJ.txt"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Trajektorien-J-Wiedergabe
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "/fruser/traj/traj.txt"
    rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1)
    print(f"LoadTrajectoryJ {traj_file_name}, rtn is: {rtn}")
    rtn,traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos:{traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},"
          f"{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 50, 100, 100)
    rtn,traj_num = robot.GetTrajectoryPointNum()
    print(f"GetTrajectoryStartPose rtn is: {rtn}, traj num is: {traj_num}")
    rtn = robot.SetTrajectoryJSpeed(50.0)
    print(f"SetTrajectoryJSpeed is: {rtn}")
    traj_force = [0.0,0.0,0.0,0.0,0.0,0.0]
    traj_force[0] = 10  # fx = 10
    rtn = robot.SetTrajectoryJForceTorque(traj_force)
    print(f"SetTrajectoryJForceTorque rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFx(10.0)
    print(f"SetTrajectoryJForceFx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFy(0.0)
    print(f"SetTrajectoryJForceFy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFz(0.0)
    print(f"SetTrajectoryJForceFz rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTx(10.0)
    print(f"SetTrajectoryJTorqueTx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTy(10.0)
    print(f"SetTrajectoryJTorqueTy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTz(10.0)
    print(f"SetTrajectoryJTorqueTz rtn is: {rtn}")
    rtn = robot.MoveTrajectoryJ()
    print(f"MoveTrajectoryJ rtn is: {rtn}")
    robot.CloseRPC()

Trajektorie vorverarbeiten (Vorausschauende Planung für TrajectoryLA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadTrajectoryLA(name, mode, errorLim, type, precision, vamx, amax, jmax, flag)``"
    "Beschreibung", "Trajektorie vorverarbeiten (Vorausschauende Planung für TrajectoryLA)"
    "Erforderliche Parameter", "- ``name``: Name der Trajektoriendatei
    - ``mode``: Abtastmodus, 0 = keine Abtastung, 1 = Abtastung mit konstantem Datenintervall, 2 = Abtastung mit Fehlergrenze
    - ``errorLim``: Fehlergrenze (wirksam bei Verwendung linearer Approximation)
    - ``type``: Glättungsmethode, 0 = Bezier-Glättung
    - ``precision``: Glättungsgenauigkeit (wirksam bei Verwendung von Bezier-Glättung)
    - ``vamx``: Eingestellte maximale Geschwindigkeit [mm/s]
    - ``amax``: Eingestellte maximale Beschleunigung [mm/s²]
    - ``jmax``: Eingestellter maximaler Ruck [mm/s³]
    - ``flag``: Schalter für konstante Vorausschau-Geschwindigkeit: 0 = deaktiviert, 1 = aktiviert"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Trajektorie wiedergeben (Vorausschauende Planung für TrajectoryLA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.0

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveTrajectoryLA()``"
    "Beschreibung", "Trajektorie wiedergeben (Vorausschauende Planung für TrajectoryLA)"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Trajektorienwiedergabe (Vorausschauende Planung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "/fruser/traj/traj.txt"
    rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 50, 200, 1000, 0)
    print(f"LoadTrajectoryLA {traj_file_name}, rtn is: {rtn}")
    rtn, traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos: {traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100)
    rtn = robot.MoveTrajectoryLA()
    print(f"MoveTrajectoryLA rtn is: {rtn}")
    robot.CloseRPC()