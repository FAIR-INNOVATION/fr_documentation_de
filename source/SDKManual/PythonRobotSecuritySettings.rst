Roboter-Sicherheitseinstellungen
================================

.. toctree::
    :maxdepth: 5

Kollisionsstufe einstellen
++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAnticollision(mode, level, config)``"
    "Beschreibung", "Kollisionsstufe einstellen"
    "Erforderliche Parameter", "- ``mode``: 0 = Stufe, 1 = Prozent
    - ``level = [j1, j2, j3, j4, j5, j6]``: Kollisionsschwellwert
    - ``config``: 0 = Konfigurationsdatei nicht aktualisieren, 1 = Konfigurationsdatei aktualisieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Strategie nach Kollision einstellen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetCollisionStrategy(strategy, safeTime, safeDistance, safeVel, safetyMargin)``"
    "Beschreibung", "Strategie nach Kollision einstellen"
    "Erforderliche Parameter", "- ``strategy``: 0 = Fehler melden und pausieren, 1 = Weiterlaufen, 2 = Fehler melden und anhalten, 3 = Schwerkraftmomentmodus, 4 = Schwingungsantwortmodus, 5 = Kollisionsrückprallmodus"
    "Standardparameter", "- ``safeTime``: Sicherheitsstopp-Zeit [1000-2000] ms, Standard = 1000
    - ``safeDistance``: Sicherheitsstopp-Distanz [1-150] mm, Standard = 100
    - ``safeVel``: Sicherheitsstopp-Geschwindigkeit [50-250] mm/s, Standard = 250
    - ``safetyMargin[6]``: Sicherheitsfaktoren [1-10], Standard = [10, 10, 10, 10, 10, 10]"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Benutzerdefinierte Kollisionserkennungsschwellwerte starten, Schwellwerte für Gelenk und TCP setzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.0

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomCollisionDetectionStart(flag, jointDetectionThreshould, tcpDetectionThreshould, block)``"
    "Beschreibung", "Benutzerdefinierte Kollisionserkennungsschwellwerte starten, Schwellwerte für Gelenk und TCP setzen"
    "Erforderliche Parameter", "- ``flag``: 1 = Nur Gelenkerkennung aktivieren, 2 = Nur TCP-Erkennung aktivieren, 3 = Gelenk- und TCP-Erkennung gleichzeitig aktivieren
    - ``jointDetectionThreshould``: Gelenk-Kollisionserkennungsschwellwerte j1-j6
    - ``tcpDetectionThreshould``: TCP-Kollisionserkennungsschwellwerte, xyzabc
    - ``block``: 0 = nicht blockierend, 1 = blockierend"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode"

Benutzerdefinierte Kollisionserkennungsschwellwerte stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.0

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomCollisionDetectionEnd()``"
    "Beschreibung", "Benutzerdefinierte Kollisionserkennungsschwellwerte stoppen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Einstellen der Roboter-Kollisionsstufe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    mode = 0
    config = 1
    level1 = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0]
    level2 = [50.0, 20.0, 30.0, 40.0, 50.0, 60.0]
    rtn = robot.SetAnticollision(mode, level1, config)
    print(f"SetAnticollision mode 0 rtn is {rtn}")
    mode = 1
    rtn = robot.SetAnticollision(mode, level2, config)
    print(f"SetAnticollision mode 1 rtn is {rtn}")
    p1Joint = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    p2Joint = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100, blendR=2)
    robot.ResetAllError()
    safety = [5, 5, 5, 5, 5, 5]
    rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety)
    print(f"SetCollisionStrategy rtn is {rtn}")
    jointDetectionThreshould = [0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
    tcpDetectionThreshould = [60, 60, 60, 60, 60, 60]
    rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0)
    print(f"CustomCollisionDetectionStart rtn is {rtn}")
    robot.MoveL(desc_pos=p1Desc, tool=0, user=0, vel=100)
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100)
    rtn = robot.CustomCollisionDetectionEnd()
    print(f"CustomCollisionDetectionEnd rtn is {rtn}")
    robot.CloseRPC()

Positiven Endanschlag einstellen
+++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLimitPositive(p_limit)``"
    "Beschreibung", "Positiven Endanschlag (weiche Grenze) einstellen"
    "Erforderliche Parameter", "- ``p_limit = [j1, j2, j3, j4, j5, j6]``: Positionen der sechs Gelenke"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Negativen Endanschlag einstellen
+++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLimitNegative(n_limit)``"
    "Beschreibung", "Negativen Endanschlag (weiche Grenze) einstellen"
    "Erforderliche Parameter", "- ``n_limit = [j1, j2, j3, j4, j5, j6]``: Positionen der sechs Gelenke"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Weiche Gelenk-Endanschläge (Winkel) abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointSoftLimitDeg(flag=1)``"
    "Beschreibung", "Weiche Gelenk-Endanschläge (Winkel) abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``flag``: 0 = blockierend, 1 = nicht blockierend, Standard = 1"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[j1min, j1max, j2min, j2max, j3min, j3max, j4min, j4max, j5min, j5max, j6min, j6max]``: Achse 1~6, negative und positive weiche Endanschläge, Einheit [°]"

Codebeispiel zum Einstellen der Roboter-Endanschläge
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    plimit = [170.0, 80.0, 150.0, 80.0, 170.0, 160.0]
    robot.SetLimitPositive(plimit)
    nlimit = [-170.0, -260.0, -150.0, -260.0, -170.0, -160.0]
    robot.SetLimitNegative(nlimit)
    error,neg_deg = robot.GetJointSoftLimitDeg(0)
    print(f"pos limit deg: {neg_deg[1]}, {neg_deg[3]}, {neg_deg[5]}, {neg_deg[7]}, {neg_deg[9]}, {neg_deg[11]}")
    print(f"neg limit deg: {neg_deg[0]}, {neg_deg[2]}, {neg_deg[4]}, {neg_deg[6]}, {neg_deg[8]}, {neg_deg[10]}")
    robot.CloseRPC()

Roboter-Kollisionserkennungsmethode einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetCollisionDetectionMethod(method, thresholdMode)``"
    "Beschreibung", "Roboter-Kollisionserkennungsmethode einstellen"
    "Erforderliche Parameter", "- ``method``: Kollisionserkennungsmethode: 0 = Strommodus, 1 = Doppel-Encoder, 2 = Strom und Doppel-Encoder gleichzeitig aktiviert
    - ``thresholdMode``: Art des Kollisionsstufen-Schwellwerts: 0 = Fester Schwellwert der Kollisionsstufe, 1 = Benutzerdefinierter Kollisionserkennungsschwellwert"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kollisionserkennung im Stillstand ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetStaticCollisionOnOff(status)``"
    "Beschreibung", "Kollisionserkennung im Stillstand ein-/ausschalten"
    "Erforderliche Parameter", "- ``status``: 0 = aus, 1 = ein"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Einstellen der Roboter-Kollisionserkennungsmethode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetCollisionDetectionMethod(0,0)
    rtn = robot.SetStaticCollisionOnOff(1)
    print(f"SetStaticCollisionOnOff On rtn is {rtn}")
    time.sleep(5)
    rtn = robot.SetStaticCollisionOnOff(0)
    print(f"SetStaticCollisionOnOff Aus rtn ist {rtn}")
    robot.CloseRPC()

Gelenk-Drehmoment-/Leistungsüberwachung
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetPowerLimit(status, power)``"
    "Beschreibung", "Gelenk-Drehmoment-/Leistungsüberwachung"
    "Erforderliche Parameter", "- ``status``: 0 = aus, 1 = ein
    - ``power``: Maximale eingestellte Leistung (W)"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Gelenk-Drehmoment-/Leistungsüberwachung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    robot.SetPowerLimit(1, 200)
    error,torques = robot.GetJointTorques(1)
    count = 100
    robot.ServoJTStart()
    while count > 0:
        error = robot.ServoJT(torques, 0.001)
        count -= 1
        time.sleep(0.001)  # 1ms Verzögerung
    error = robot.ServoJTEnd()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Sicherheitsgeschwindigkeitsparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetVelReducePara(enable, maxTCPVel, strategy)``"
    "Beschreibung", "Sicherheitsgeschwindigkeitsparameter einstellen"
    "Erforderliche Parameter", "
    - ``enable``: 0-aus; 1-im manuellen Modus aktiviert; 2-in allen Modi aktiviert (automatische Geschwindigkeitsbegrenzung nicht unterstützt)
    - ``maxTCPVel``: Maximale TCP-Geschwindigkeitsbegrenzung; [0-1000] mm/s
    - ``strategy``: Strategie nach Überschreitung; 0-Stopp mit Alarm; 1-automatische Geschwindigkeitsbegrenzung; 2-Stopp mit Alarm und Deaktivierung
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode"

SDK-Codebeispiel zum Einstellen der Sicherheitsgeschwindigkeitsparameter
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    def TestSetVelReducePara(self):
        # Gelenkposition, externe Achse und Offset initialisieren
        j1 = [0, -90, 90, 0, 0, 0]
        j2 = [90, -90, 90, 0, 0, 0]
        epos = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]

        # Basisgeschwindigkeit einstellen
        robot.SetSpeed(80)

        # Test Parameterfehler (mode=2 ungültig?)
        rtn = robot.SetVelReducePara(2, 30, 1)
        print(f"SetVelReducePara param error rtn is {rtn}")

        # Geschwindigkeitsreduzierung deaktivieren (mode=0, action=1 deaktiviert)
        rtn = robot.SetVelReducePara(0, 30, 1)
        print(f"SetVelReducePara disable reduce vel rtn is {rtn}")
        robot.MoveJ(joint_pos=j1, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Geschwindigkeitsreduzierung aktivieren (mode=1, action=1)
        rtn = robot.SetVelReducePara(1, 30, 1)
        print(f"SetVelReducePara reduce vel rtn is {rtn}")
        robot.MoveJ(joint_pos=j1, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Test action=2 (kann Not-Halt oder Deaktivierung bedeuten)
        rtn = robot.SetVelReducePara(2, 30, 2)
        print(f"SetVelReducePara disable robot rtn is {rtn}")
        robot.MoveJ(joint_pos=j1, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Warten, Fehler zurücksetzen und Roboter wieder aktivieren
        time.sleep(2)
        robot.ResetAllError()
        robot.RobotEnable(1)
        time.sleep(1)

        # Test action=0 (kann nur Fehler melden, keine Aktion bedeuten)
        rtn = robot.SetVelReducePara(2, 30, 0)
        print(f"SetVelReducePara report error rtn is {rtn}")
        robot.MoveJ(joint_pos=j1, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=0, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Verbindung schließen
        robot.CloseRPC()

    TestSetVelReducePara(robot)