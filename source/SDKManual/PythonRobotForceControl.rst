Roboter-Kraftregelung
=====================

.. toctree::
    :maxdepth: 5

Kraftsensor konfigurieren
+++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_SetConfig(company, device, softversion=0, bus=0)``"
    "Beschreibung", "Kraftsensor konfigurieren"
    "Erforderliche Parameter", "- ``company``: Hersteller des Sensors, 17-Kunwei, 19-CASA, 20-ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
    - ``device``: Gerätenummer, Kunwei(0-KWR75B), CASA(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A), NBIT(0-XLH93003ACS), Xinjingcheng XJC(0-XJC-6F-D82), NSR(0-NSR-FTSensorA)"
    "Standardparameter", "- ``softversion``: Softwareversionsnummer, vorübergehend nicht verwendet, Standard = 0
    - ``bus``: Position des Geräts am Endeffektor-Bus, vorübergehend nicht verwendet, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kraftsensor-Konfiguration abrufen
+++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_GetConfig()``"
    "Beschreibung", "Kraftsensor-Konfiguration abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``[number, company, device, softversion, bus]``: number = Sensornummer; company = Hersteller, device = Gerätenummer, softversion = Softwareversion, bus = Busposition"

Kraftsensor aktivieren
++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_Activate(state)``"
    "Beschreibung", "Kraftsensor aktivieren"
    "Erforderliche Parameter", "- ``state``: 0 = Zurücksetzen, 1 = Aktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kraftsensor Nullpunkt setzen (Tarieren)
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_SetZero(state)``"
    "Beschreibung", "Kraftsensor Nullpunkt setzen (Tarieren)"
    "Erforderliche Parameter", "- ``state``: 0 = Nullpunkt entfernen, 1 = Nullpunkt korrigieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Referenzkoordinatensystem für Kraftsensor einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_SetRCS(ref, coord=[0,0,0,0,0,0])``"
    "Beschreibung", "Referenzkoordinatensystem für Kraftsensor einstellen"
    "Erforderliche Parameter", "- ``ref``: 0 = Werkzeugkoordinatensystem, 1 = Basiskoordinatensystem"
    "Standardparameter", "- ``coord``: [x, y, z, rx, ry, rz] Werte für benutzerdefiniertes Koordinatensystem, Standard = [0,0,0,0,0,0]"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastgewicht unter dem Kraftsensor einstellen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetForceSensorPayload(weight)``"
    "Beschreibung", "Lastgewicht unter dem Kraftsensor einstellen"
    "Erforderliche Parameter", "- ``weight``: Lastgewicht [kg]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastschwerpunkt unter dem Kraftsensor einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetForceSensorPayloadCog(x, y, z)``"
    "Beschreibung", "Lastschwerpunkt unter dem Kraftsensor einstellen"
    "Erforderliche Parameter", "
    - ``x``: Schwerpunkt x [mm]
    - ``y``: Schwerpunkt y [mm]
    - ``z``: Schwerpunkt z [mm]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastgewicht unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetForceSensorPayload()``"
    "Beschreibung", "Lastgewicht unter dem Kraftsensor abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``weight``: Lastgewicht [kg]"

Lastschwerpunkt unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetForceSensorPayloadCog()``"
    "Beschreibung", "Lastschwerpunkt unter dem Kraftsensor abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``x``: Schwerpunkt x [mm]
    - ``y``: Schwerpunkt y [mm]
    - ``z``: Schwerpunkt z [mm]"

Automatische Nullpunktberechnung (Tarieren) des Kraftsensors
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ForceSensorAutoComputeLoad()``"
    "Beschreibung", "Automatische Nullpunktberechnung (Tarieren) des Kraftsensors"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``weight``: Sensoreigengewicht [kg] (oder resultierende Last?)
    - ``pos = [x, y, z]``: Sensor-Schwerpunkt [mm] (oder resultierender Schwerpunkt?)"

Kraft-/Drehmomentdaten im Referenzkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_GetForceTorqueRCS()``"
    "Beschreibung", "Kraft-/Drehmomentdaten im Referenzkoordinatensystem abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``data = [fx, fy, fz, tx, ty, tz]``: Kraft-/Drehmomentdaten im Referenzkoordinatensystem"

Rohe Kraft-/Drehmomentdaten des Sensors abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_GetForceTorqueOrigin()``"
    "Beschreibung", "Rohe Kraft-/Drehmomentdaten des Sensors abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``data = [fx, fy, fz, tx, ty, tz]``: Rohe Kraft-/Drehmomentdaten des Sensors"

Codebeispiel für Kraftsensor-Konfiguration und automatische Nullpunktberechnung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    error,ft = robot.FT_GetForceTorqueOrigin()
    print(f"ft origin:{ft[0]},{ft[1]},{ft[2]},{ft[3]},{ft[4]},{ft[5]}")
    robot.FT_SetZero(1)
    time.sleep(1)
    ftCoord = [0, 0, 0, 0, 0, 0]
    robot.FT_SetRCS(0, ftCoord)
    robot.SetForceSensorPayload(0.824)
    robot.SetForceSensorPayloadCog(0.778, 2.554, 48.765)
    error,weight = robot.GetForceSensorPayload()
    error,x, y, z = robot.GetForceSensorPayloadCog()
    print(f"the FT load is  {weight}, {x} {y} {z}")
    robot.SetForceSensorPayload(0)
    robot.SetForceSensorPayloadCog(0, 0, 0)
    error,computeWeight, tran = robot.ForceSensorAutoComputeLoad()
    print(f"the result is weight {computeWeight} pos is {tran[0]} {tran[1]} {tran[2]}")
    robot.CloseRPC()

Lastgewichtserkennung aufzeichnen
+++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_PdIdenRecord(tool_id)``"
    "Beschreibung", "Lastgewichtserkennung aufzeichnen"
    "Erforderliche Parameter", "- ``tool_id``: Sensorkoordinatensystem-Nummer, Bereich [0~14]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastgewichtserkennung berechnen
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_PdIdenCompute()``"
    "Beschreibung", "Lastgewichtserkennung berechnen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``weight``: Berechnetes Lastgewicht [kg]"

Lastschwerpunkt-Erkennung aufzeichnen
++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_PdCogIdenRecord(tool_id, index)``"
    "Beschreibung", "Lastschwerpunkt-Erkennung aufzeichnen"
    "Erforderliche Parameter", "- ``tool_id``: Sensorkoordinatensystem-Nummer, Bereich [0~14]
    - ``index``: Punktnummer [1~3]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastschwerpunkt-Erkennung berechnen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_PdCogIdenCompute()``"
    "Beschreibung", "Lastschwerpunkt-Erkennung berechnen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``cog = [cogx, cogy, cogz]``: Berechneter Lastschwerpunkt [mm]"

Codebeispiel für Lastidentifikation mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    error,ft = robot.FT_GetForceTorqueOrigin()
    print(f"ft origin:{ft[0]},{ft[1]},{ft[2]},{ft[3]},{ft[4]},{ft[5]}")
    robot.FT_SetZero(1)
    time.sleep(1)
    tcoord = [0, 0, 35.0, 0, 0, 0]
    robot.SetToolCoord(10, tcoord, 1, 0, 0, 0)
    robot.FT_PdIdenRecord(10)
    time.sleep(1)
    error,weight = robot.FT_PdIdenCompute()
    print(f"payload weight:{weight}")
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_p3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    robot.MoveCart(desc_p1, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 1)
    robot.MoveCart(desc_p2, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 2)
    robot.MoveCart(desc_p3, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 3)
    time.sleep(1)
    error,cog = robot.FT_PdCogIdenCompute()
    print(f"FT_PdCogIdenCompute return {error}")
    print(f"cog:{cog[0]},{cog[1]},{cog[2]}")
    robot.CloseRPC()

Kollisionsüberwachung (Force Guard)
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_Guard(flag, sensor_num, select, force_torque, max_threshold, min_threshold)``"
    "Beschreibung", "Kollisionsüberwachung (Force Guard)"
    "Erforderliche Parameter", "- ``flag``: 0 = deaktivieren, 1 = aktivieren
    - ``sensor_num``: Kraftsensor-Nummer
    - ``select``: Auswahl der sechs Freiheitsgrade für die Kollisionserkennung [fx, fy, fz, mx, my, mz], 0 = nicht prüfen, 1 = prüfen
    - ``force_torque``: Soll-Kollisionskraft/-moment (Mitte) [N oder Nm]
    - ``max_threshold``: Maximaler Schwellwert (obere Toleranz) [N oder Nm]
    - ``min_threshold``: Minimaler Schwellwert (untere Toleranz) [N oder Nm]
    - Hinweis: Erkennungsbereich: (force_torque - min_threshold, force_torque + max_threshold)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Kollisionsüberwachung
++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    sensor_id = 1
    select = [1, 1, 1, 1, 1, 1]
    max_threshold = [10.0, 10.0, 10.0, 10.0, 10.0, 10.0]
    min_threshold = [5.0, 5.0, 5.0, 5.0, 5.0, 5.0]
    ft = None 
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_p3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    error = robot.FT_Guard(1, sensor_id, select,[0.0,0.0,0.0,0.0,0.0,0.0], max_threshold, min_threshold)
    robot.MoveCart(desc_p1, 0, 0, 100.0)
    robot.MoveCart(desc_p2, 0, 0, 100.0)
    robot.MoveCart(desc_p3, 0, 0, 100.0)
    robot.FT_Guard(0, sensor_id, select,[0.0,0.0,0.0,0.0,0.0,0.0], max_threshold, min_threshold)
    robot.CloseRPC()

Kraftregelung (Constant Force Control)
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M=None, B=None, threshold=[0.2,0.2], adjustCoeff=[1.0,1.0], polishRadio=0, filter_Sign=0, posAdapt_sign=0, isNoBlock=0)``"
    "Beschreibung", "Kraftregelung (Constant Force Control)"
    "Erforderliche Parameter", "- ``flag``: Kraftregelung aktivieren: 0 = aus, 1 = an
    - ``sensor_id``: Kraftsensor-Nummer
    - ``select``: Auswahl der sechs Freiheitsgrade für die Kraftregelung [fx, fy, fz, mx, my, mz], 0 = nicht regeln, 1 = regeln
    - ``ft``: Soll-Kraft/-Moment [fx, fy, fz, tx, ty, tz] [N oder Nm]
    - ``ft_pid``: PID-Parameter für Kraftregelung [f_p, f_i, f_d, m_p, m_i, m_d] (P, I, D für Kraft und Moment)
    - ``adj_sign``: Adaptive Regelung: 0 = deaktivieren, 1 = aktivieren
    - ``ILC_sign``: ILC (Iterative Learning Control): 0 = stop, 1 = training, 2 = practice
    - ``max_dis``: Maximale Anpassungsdistanz [mm]
    - ``max_ang``: Maximaler Anpassungswinkel [°]"
    "Standardparameter", "- ``M``: Massenparameter (für rx, ry) [0.1-10], Standard intern festgelegt? (im Code als None)
    - ``B``: Dämpfungsparameter (für rx, ry) [0.1-50], Standard intern festgelegt? (im Code als None)
    - ``threshold``: Startschwellen für rx, ry [0-10], Standard = [0.2, 0.2]
    - ``adjustCoeff``: Momenten-Anpassungskoeffizient für rx, ry [0-1], Standard = [1.0, 1.0]
    - ``polishRadio``: Schleifscheibenradius [mm], Standard = 0
    - ``filter_Sign``: Filter aktivieren: 0 = aus, 1 = an, Standard = 0
    - ``posAdapt_sign``: Posennachgiebigkeit aktivieren: 0 = aus, 1 = an, Standard = 0
    - ``isNoBlock``: Blockierungs-Flag: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Kraftregelung mit Dämpfung
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    sensor_id = 10
    select = [0, 0, 1, 0, 0, 0]
    ft_pid = [0.0008, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 1000.0
    max_ang = 20.0
    ft = [0.0] * 6 
    epos = [0.0] * 4
    j1 = [80.765, -98.795, 106.548, -97.734, -89.999, 94.842]
    j2 = [43.067, -84.429, 92.620, -98.175, -90.011, 57.144]
    desc_p1 = [5.009, -547.463, 262.053, -179.999, -0.019, 75.923]
    desc_p2 = [-347.966, -547.463, 262.048, -180.000, -0.019, 75.923]
    offset_pos = [0.0] * 6
    M = [2.0, 2.0]
    B = [15.0, 15.0]
    threshold = [1.0, 1.0]
    adjustCoeff = [1.0, 0.8]
    polishRadio = 0.0
    filter_Sign = 0
    posAdapt_sign = 1
    isNoBlock = 0
    ft[2] = -10.0 
    while True:
        rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold,adjustCoeff, 0, 0, 1, 0)
        print(f"FT_Control start rtn is {rtn}")
        rtn = robot.MoveL(desc_pos=desc_p1, tool=1, user=0, vel=100, acc=100, ovl=100, blendR=-1, blendMode = 0, exaxis_pos=epos, search=0, offset_flag=0, offset_pos=offset_pos)
        rtn = robot.MoveL(desc_pos=desc_p2, tool=1, user=0, vel=100, acc=100, ovl=100, blendR=-1, blendMode = 0, exaxis_pos=epos, search=0, offset_flag=0, offset_pos=offset_pos)
        rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold,adjustCoeff, 0, 0, 1, 0)
        print(f"FT_Control end rtn is {rtn}")
    robot.CloseRPC()
    return 0

Spiralförmige Suche
++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_SpiralSearch(rcs, ft, dr=0.7, max_t_ms=60000, max_vel=5)``"
    "Beschreibung", "Spiralförmige Suche (nach Kontakt)"
    "Erforderliche Parameter", "- ``rcs``: Referenzkoordinatensystem, 0 = Werkzeug, 1 = Basis
    - ``ft``: Kraft-/Momentenschwellwert für Abbruch [N oder Nm] (einzelner Wert)"
    "Standardparameter", "- ``dr``: Radiuszunahme pro Umdrehung [mm], Standard = 0.7
    - ``max_t_ms``: Maximale Suchzeit [ms], Standard = 60000
    - ``max_vel``: Maximale Lineargeschwindigkeit [mm/s], Standard = 5"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Rotatorisches Einführen
++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_RotInsertion(rcs, ft, orn, angVelRot=3, angleMax=45, angAccmax=0, rotorn=1, strategy=0)``"
    "Beschreibung", "Rotatorisches Einführen (mit Kraftsuche)"
    "Erforderliche Parameter", "- ``rcs``: Referenzkoordinatensystem, 0 = Werkzeug, 1 = Basis
    - ``ft``: Kraft-/Momentenschwellwert für Abbruch [N oder Nm] (einzelner Wert)
    - ``orn``: Kraft-/Momentenrichtung, 1 = entlang Z-Achse, 2 = um Z-Achse"
    "Standardparameter", "- ``angVelRot``: Rotationsgeschwindigkeit [°/s], Standard = 3
    - ``angleMax``: Maximaler Rotationswinkel [°], Standard = 45
    - ``angAccmax``: Maximale Rotationsbeschleunigung [°/s²], vorübergehend nicht verwendet, Standard = 0
    - ``rotorn``: Rotationsrichtung, 1 = im Uhrzeigersinn, 2 = gegen Uhrzeigersinn, Standard = 1
    - ``strategy``: Strategie bei fehlender Kraft-/Momentenerkennung, 0 = Fehler, 1 = Warnung, Bewegung fortsetzen, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Spiral-Suche, Lineares Einführen etc.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    j1=[-11.904,-99.669,117.473,-108.616,-91.726,74.256]
    j2=[-45.615,-106.172,124.296,-107.151,-91.282,74.255]
    j3=[-29.777,-84.536,109.275,-114.075,-86.655,74.257]
    j4=[-31.154,-95.317,94.276,-88.079,-89.740,74.256]
    desc_pos1=[-419.524,-13.000,351.569,-178.118,0.314,3.833]
    desc_pos2=[-321.222,185.189,335.520,-179.030,-1.284,-29.869]
    desc_pos3=[-487.434,154.362,308.576,176.600,0.268,-14.061]
    desc_pos4=[-443.165,147.881,480.951,179.511,-0.775,-15.409]
    offset_pos=[0.0]*6
    epos=[0.0]*4
    tool=0
    user=0
    vel=100.0
    acc=100.0
    ovl=100.0
    oacc=100.0
    blendT=0.0
    blendR=0.0
    flag=0
    search=0
    blendMode=0
    velAccMode=0
    robot.SetSpeed(20)
    rtn=robot.MoveJ(joint_pos=j1,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.MoveL(desc_pos=desc_pos2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendR=blendR,blendMode=blendMode,exaxis_pos=epos,search=search,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,velAccParamMode=velAccMode)
    print(f"movelerrcode:{rtn}")
    rtn=robot.MoveC(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,offset_flag_p=flag,offset_pos_p=offset_pos,desc_pos_t=desc_pos4,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,offset_flag_t=flag,offset_pos_t=offset_pos,ovl=ovl,blendR=blendR,oacc=oacc,velAccParamMode=velAccMode)
    print(f"movecerrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.Circle(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,desc_pos_t=desc_pos1,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,ovl=ovl,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,blendR=-1,velAccParamMode=velAccMode)
    print(f"circleerrcode:{rtn}")
    rtn=robot.MoveCart(desc_pos=desc_pos4,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendT=blendT,config=-1)
    print(f"MoveCarterrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j1,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.MoveL(desc_pos=desc_pos2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendR=blendR,blendMode=blendMode,exaxis_pos=epos,search=search,offset_flag=flag,offset_pos=offset_pos,config=-1,velAccParamMode=velAccMode)
    print(f"movelerrcode:{rtn}")
    rtn=robot.MoveC(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,offset_flag_p=flag,offset_pos_p=offset_pos,desc_pos_t=desc_pos4,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,offset_flag_t=flag,offset_pos_t=offset_pos,ovl=ovl,blendR=blendR,config=-1,velAccParamMode=velAccMode)
    print(f"movecerrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.Circle(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,desc_pos_t=desc_pos1,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,ovl=ovl,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,blendR=-1,velAccParamMode=velAccMode)
    print(f"circleerrcode:{rtn}")
    robot.CloseRPC()
    return0

Lineares Einführen
+++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_LinInsertion(rcs, ft, disMax, linorn, lin_v=1.0, lin_a=1.0)``"
    "Beschreibung", "Lineares Einführen (mit Kraftsuche)"
    "Erforderliche Parameter", "- ``rcs``: Referenzkoordinatensystem, 0 = Werkzeug, 1 = Basis
    - ``ft``: Kraft-/Momentenschwellwert für Abbruch [N oder Nm] (einzelner Wert)
    - ``disMax``: Maximale Einführdistanz [mm]
    - ``linorn``: Einführrichtung: 0 = negative Richtung, 1 = positive Richtung"
    "Standardparameter", "- ``lin_v``: Lineare Suchgeschwindigkeit [mm/s], Standard = 1.0
    - ``lin_a``: Lineare Suchbeschleunigung [mm/s²], vorübergehend nicht verwendet, Standard = 1.0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Spiral-Suche, Lineares Einführen etc.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    status = 1
    sensor_num = 1
    gain = [0.0001, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 100.0
    max_ang = 5.0
    ft = [0.0,0.0,-10.0,0.0,0.0,0.0]
    rcs = 0
    dr = 0.7
    fFinish = 1.0
    t = 60000.0
    vmax = 3.0
    force_goal = 20.0
    lin_v = 0.0
    lin_a = 0.0
    disMax = 100.0
    linorn = 1
    angVelRot = 2.0
    forceInsertion = 1.0
    angleMax = 45
    orn = 1
    angAccmax = 0.0
    rotorn = 1
    select1 = [0, 0, 1, 1, 1, 0]
    robot.FT_Control(status, sensor_num, select1, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_SpiralSearch(rcs, dr, fFinish, t, vmax)
    print(f"FT_SpiralSearch rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select1, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select2 = [1, 1, 1, 0, 0, 0]
    gain[0] = 0.00005
    ft[2] = -30.0
    robot.FT_Control(1, sensor_num, select2, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn)
    print(f"FT_LinInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select2, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select3 = [0, 0, 1, 1, 1, 0]
    ft[2] = -10.0
    gain[0] = 0.0001
    robot.FT_Control(1, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn)
    print(f"FT_RotInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select4 = [1, 1, 1, 0, 0, 0]
    ft[2] = -30.0
    robot.FT_Control(1, sensor_num, select4, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn)
    print(f"FT_LinInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select4, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    robot.CloseRPC()

Oberflächenlokalisierung
++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_FindSurface(rcs, dir, axis, disMax, ft, lin_v=3.0, lin_a=0.0)``"
    "Beschreibung", "Oberflächenlokalisierung (FindSurface)"
    "Erforderliche Parameter", "- ``rcs``: Referenzkoordinatensystem, 0 = Werkzeug, 1 = Basis
    - ``dir``: Bewegungsrichtung, 1 = positive Richtung, 2 = negative Richtung
    - ``axis``: Bewegungsachse, 1 = x, 2 = y, 3 = z
    - ``disMax``: Maximale Suchdistanz [mm]
    - ``ft``: Kraftschwellwert für Aktionsabbruch [N] (einzelner Wert für die gewählte Achse)"
    "Standardparameter", "- ``lin_v``: Lineare Suchgeschwindigkeit [mm/s], Standard = 3.0
    - ``lin_a``: Lineare Suchbeschleunigung [mm/s²], Standard = 0.0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Berechnung der mittleren Ebene starten
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_CalCenterStart()``"
    "Beschreibung", "Berechnung der mittleren Ebene starten (für Zentrierung)"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Berechnung der mittleren Ebene beenden
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_CalCenterEnd()``"
    "Beschreibung", "Berechnung der mittleren Ebene beenden"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``pos = [x, y, z, rx, ry, rz]``: Pose der mittleren Ebene (Zentrumsposition)"

Codebeispiel für Oberflächenlokalisierung
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    rcs = 0
    dir = 1
    axis = 1
    lin_v = 3.0
    lin_a = 0.0
    maxdis = 50.0
    ft_goal = 2.0
    desc_pos = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    xcenter = [0, 0, 0, 0, 0, 0]
    ycenter = [0, 0, 0, 0, 0, 0]
    ft = [-2.0, 0.0, 0.0, 0.0, 0.0, 0.0]  # Nicht direkt verwendet
    robot.MoveCart(desc_pos, 9, 0, 100.0)
    robot.FT_CalCenterStart()
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    robot.MoveCart(desc_pos, 9, 0)
    robot.WaitMs(1000)
    dir = 2
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    error,xcenter = robot.FT_CalCenterEnd()
    print(f"xcenter:{xcenter[0]},{xcenter[1]},{xcenter[2]},{xcenter[3]},{xcenter[4]},{xcenter[5]}")
    robot.MoveCart(xcenter, 9, 0, 60.0)
    robot.FT_CalCenterStart()
    dir = 1
    axis = 2
    lin_v = 6.0
    maxdis = 150.0
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    robot.MoveCart(desc_pos, 9, 0, 100.0)
    robot.WaitMs(1000)
    dir = 2
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    error,ycenter = robot.FT_CalCenterEnd()
    print(f"ycenter:{ycenter[0]},{ycenter[1]},{ycenter[2]},{ycenter[3]},{ycenter[4]},{ycenter[5]}")
    robot.MoveCart(ycenter, 9, 0, 60.0)
    robot.CloseRPC()

Nachgiebigkeitsregelung (Compliance) starten
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_ComplianceStart(p, force)``"
    "Beschreibung", "Nachgiebigkeitsregelung (Compliance) starten"
    "Erforderliche Parameter", "- ``p``: Positionsregelungsfaktor oder Nachgiebigkeitskoeffizient
    - ``force``: Kraftschwellwert für Aktivierung [N]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Nachgiebigkeitsregelung (Compliance) stoppen
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FT_ComplianceStop()``"
    "Beschreibung", "Nachgiebigkeitsregelung (Compliance) stoppen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Nachgiebigkeitsregelung
++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    flag = 1
    sensor_id = 1
    select = [1, 1, 1, 0, 0, 0]
    ft_pid = [0.0005, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 100.0
    max_ang = 0.0
    ft = [-10.0, -10.0, -10.0, 0.0, 0.0, 0.0]
    offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    epos = [0.0, 0.0, 0.0, 0.0]
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]  # DescPose
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    p = 0.00005
    force = 30.0
    rtn = robot.FT_ComplianceStart(p, force)
    print(f"FT_ComplianceStart rtn is {rtn}")
    count = 3
    while count > 0:
        robot.MoveL(desc_pos=desc_p1,tool= 0,user= 0,vel= 100.0)
        robot.MoveL(desc_pos=desc_p2,tool= 0,user= 0,vel= 100.0)
        count -= 1
    robot.FT_ComplianceStop()
    print(f"FT_ComplianceStop rtn is {rtn}")
    flag = 0
    robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    robot.CloseRPC()

Lastidentifikation - Dynamikfilter initialisieren
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadIdentifyDynFilterInit()``"
    "Beschreibung", "Lastidentifikation - Dynamikfilter initialisieren"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastidentifikation - Variablen initialisieren
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadIdentifyDynVarInit()``"
    "Beschreibung", "Lastidentifikation - Variablen initialisieren"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastidentifikation - Hauptprogramm
+++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadIdentifyMain(joint_torque, joint_pos, t)``"
    "Beschreibung", "Lastidentifikation - Hauptprogramm"
    "Erforderliche Parameter", "- ``joint_torque``: Gemessene Gelenkmomente [j1...j6] [Nm]
    - ``joint_pos``: Gemessene Gelenkpositionen [j1...j6] [°] oder [rad]?
    - ``t``: Abtastperiode [s]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lastidentifikationsergebnis abrufen
++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadIdentifyGetResult(gain)``"
    "Beschreibung", "Lastidentifikationsergebnis abrufen"
    "Erforderliche Parameter", "- ``gain``: Liste von 12 Koeffizienten (6 für Gravitationsterme, 6 für Zentrifugal-/Coriolisterme?)"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``weight``: Berechnetes Lastgewicht [kg]
    - ``cog = [x, y, z]``: Berechneter Lastschwerpunkt [mm]"

Codebeispiel für Roboter-Lastidentifikation
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    retval = robot.LoadIdentifyDynFilterInit()
    print(f"LoadIdentifyDynFilterInit retval is: {retval}")
    retval = robot.LoadIdentifyDynVarInit()
    print(f"LoadIdentifyDynVarInit retval is: {retval}")
    error, posJ = robot.GetActualJointPosDegree(0)
    posJ[1] += 10  # Gelenk 2 modifizieren (Beispiel)
    error, joint_toq = robot.GetJointTorques(0)
    joint_toq[1] += 2  # Drehmoment an Gelenk 2 modifizieren (Beispiel)
    tmpTorque = joint_toq.copy()
    retval = robot.LoadIdentifyMain(tmpTorque, posJ, 1)
    print(f"LoadIdentifyMain retval is: {retval}")
    gain = [0, 0.05, 0, 0, 0, 0, 0, 0.02, 0, 0, 0, 0]
    weight = [0.0]
    load_pos = [0.0, 0.0, 0.0]
    retval, weight, load_pos = robot.LoadIdentifyGetResult(gain)
    print(f"LoadIdentifyGetResult retval is: {retval} ; weight is {weight}  cog is {load_pos[0]} {load_pos[1]} {load_pos[2]}")
    robot.CloseRPC()

Kraftsensor-unterstütztes Führen (Drag & Teach)
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``EndForceDragControl(status, asaptiveFlag, interfereDragFlag, ingularityConstraintsFlag, M, B, K, F, Fmax, Vmax, forceCollisionFlag=0)``"
    "Beschreibung", "Kraftsensor-unterstütztes Führen (Drag & Teach)"
    "Erforderliche Parameter", "- ``status``: Steuerstatus, 0-aus; 1-an
    - ``asaptiveFlag``: Adaptive Regelung aktivieren, 0-aus; 1-an
    - ``interfereDragFlag``: Führen in Interferenzbereichen, 0-aus; 1-an
    - ``ingularityConstraintsFlag``: Strategie bei Singularität, 0-vermeiden; 1-durchqueren
    - ``forceCollisionFlag``: Kollisionserkennung während Führung, 0-aus; 1-an
    - ``M=[m1,m2,m3,m4,m5,m6]``: Trägheitskoeffizienten
    - ``B=[b1,b2,b3,b4,b5,b6]``: Dämpfungskoeffizienten
    - ``K=[k1,k2,k3,k4,k5,k6]``: Steifigkeitskoeffizienten
    - ``F=[f1,f2,f3,f4,f5,f6]``: Kraftschwellwerte für sechs Achsen
    - ``Fmax``: Maximale Kraftbegrenzung
    - ``Vmax``: Maximale Geschwindigkeitsbegrenzung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kraftsensor-Führungsstatus abrufen
++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetForceAndTorqueDragState()``"
    "Beschreibung", "Kraftsensor-Führungsstatus abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``dragState``: Kraftsensor-unterstützter Führungsstatus, 0 = aus, 1 = an
    - ``sixDimensionalDragState``: 6D-Kraftführungsstatus, 0 = aus, 1 = an (möglicherweise identisch)"

Automatische Aktivierung des Kraftsensors nach Fehlerlöschung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetForceSensorDragAutoFlag(status)``"
    "Beschreibung", "Automatische Aktivierung des Kraftsensors nach Fehlerlöschung"
    "Erforderliche Parameter", "- ``status``: Steuerstatus, 0 = aus, 1 = an"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Kraftsensor-unterstütztes Führen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.SetForceSensorDragAutoFlag(1)
    M = [15.0, 15.0, 15.0, 0.5, 0.5, 0.1]
    B = [150.0, 150.0, 150.0, 5.0, 5.0, 1.0]
    K = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    F = [10.0, 10.0, 10.0, 1.0, 1.0, 1.0]
    robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100)
    time.sleep(5)
    drag_state = 0
    six_dimensional_drag_state = 0
    error,drag_state, six_dimensional_drag_state = robot.GetForceAndTorqueDragState()
    print(f"the drag state is {drag_state} {six_dimensional_drag_state}")
    robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100)
    robot.CloseRPC()

Gemischte 6D-Kraft- und Gelenkimpedanz-Führung ein-/ausschalten und Parameter setzen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ForceAndJointImpedanceStartStop(status, impedanceFlag, lamdeDain, KGain, BGain, dragMaxTcpVel, dragMaxTcpOriVel)``"
    "Beschreibung", "Gemischte 6D-Kraft- und Gelenkimpedanz-Führung ein-/ausschalten und Parameter setzen"
    "Erforderliche Parameter", "- ``status``: Steuerstatus, 0 = aus, 1 = an
    - ``impedanceFlag``: Impedanz aktivieren, 0 = aus, 1 = an
    - ``lamdeDain``: Führungsverstärkung [D1, D2, D3, D4, D5, D6]
    - ``KGain``: Steifigkeitsverstärkung [K1, K2, K3, K4, K5, K6]
    - ``BGain``: Dämpfungsverstärkung [B1, B2, B3, B4, B5, B6]
    - ``dragMaxTcpVel``: Maximale Endeffektor-Lineargeschwindigkeit während Führung [mm/s]
    - ``dragMaxTcpOriVel``: Maximale Endeffektor-Winkelgeschwindigkeit während Führung [°/s]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für gemischte 6D-Kraft- und Gelenkimpedanz-Führung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    lamde_dain = [3.0, 2.0, 2.0, 2.0, 2.0, 3.0]
    k_gain = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    b_gain = [150.0, 150.0, 150.0, 5.0, 5.0, 1.0]
    rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamde_dain, k_gain, b_gain, 1000, 180)
    print(f"ForceAndJointImpedanceStartStop rtn is {rtn}")
    time.sleep(5)
    robot.DragTeachSwitch(0)
    rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamde_dain, k_gain, b_gain, 1000, 180)
    print(f"ForceAndJointImpedanceStartStop rtn is {rtn}")
    robot.CloseRPC()

Impedanzregelung Start/Stopp
++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ImpedanceControlStartStop(status, workSpace, forceThreshold, m, b, k, maxV, maxVA, maxW, maxWA)``"
    "Beschreibung", "Impedanzregelung Start/Stopp"
    "Erforderliche Parameter", "- ``status``: 0 = aus, 1 = an
    - ``workSpace``: 0 = Gelenkraum, 1 = Kartesischer Raum
    - ``forceThreshold``: Kraftschwellwert für Auslösung [fx, fy, fz, mx, my, mz] [N, Nm]
    - ``m``: Massenparameter [m1...m6]
    - ``b``: Dämpfungsparameter [b1...b6]
    - ``k``: Steifigkeitsparameter [k1...k6]
    - ``maxV``: Maximale Lineargeschwindigkeit [mm/s]
    - ``maxVA``: Maximale Linearbeschleunigung [mm/s²]
    - ``maxW``: Maximale Winkelgeschwindigkeit [°/s]
    - ``maxWA``: Maximale Winkelbeschleunigung [°/s²]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Impedanzregelung
+++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    j1 = [102.622, -135.990, 120.769, -73.950, -90.848, 35.507]
    j2 = [93.674, -80.062, 82.947, -92.199, -90.967, 26.559]
    desc_pos1 = [136.552, -149.799, 449.532, 179.817, -1.172, 157.123]
    desc_pos2 = [136.540, -561.048, 449.542, 179.819, -1.172, 157.122]
    offset_pos = [0.0] * 6
    epos = [0.0] * 4
    tool = 0
    user = 0
    vel = 100.0
    acc = 200.0
    ovl = 100.0
    blendT = -1.0
    blendR = -1.0
    flag = 0
    search = 0
    robot.SetSpeed(20)
    company = 17
    device = 0
    softversion = 0
    bus = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    rnt,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    robot.FT_SetZero(1)
    time.sleep(1)
    forceThreshold = [30.0, 30.0, 30.0, 5.0, 5.0, 5.0]
    m = [0.1, 0.1, 0.1, 0.02, 0.02, 0.02]
    b = [1.0, 1.0, 1.0, 0.08, 0.08, 0.08]
    k = [0.0] * 6
    rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100)
    print(f"ImpedanceControlStartStop errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    print(f"movel errcode:{rtn}")
    robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100)
    robot.CloseRPC()

Momentenkompensation aktivieren und Koeffizienten setzen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SerCoderCompenParams(status, torqueCoeff)``"
    "Beschreibung", "Momentenkompensation aktivieren und Koeffizienten setzen (für Gelenke)"
    "Erforderliche Parameter", "
    - ``status``: Schalter, 0 = aus, 1 = an
    - ``torqueCoeff``: Momentenkompensationskoeffizienten J1-J6 [0-1]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"