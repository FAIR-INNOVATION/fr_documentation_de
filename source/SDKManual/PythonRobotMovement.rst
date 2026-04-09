Roboterbewegung
===================

.. toctree::
    :maxdepth: 5

Jog-Tippbetrieb
+++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``StartJOG(ref, nb, dir, max_dis, vel=20.0, acc=100.0)``"
    "Beschreibung", "Jog-Tippbetrieb (Punkt-für-Punkt-Bewegung)"
    "Erforderliche Parameter", "- ``ref``: 0-Jog im Gelenkraum, 2-Jog im Basiskoordinatensystem, 4-Jog im Werkzeugkoordinatensystem, 8-Jog im Werkstückkoordinatensystem
    - ``nb``: 1-Achse 1 (X-Achse), 2-Achse 2 (Y-Achse), 3-Achse 3 (Z-Achse), 4-Achse 4 (rx), 5-Achse 5 (ry), 6-Achse 6 (rz)
    - ``dir``: 0-negative Richtung, 1-positive Richtung
    - ``max_dis``: Maximaler Winkel pro Tippbewegung [°] oder maximale Distanz [mm]"
    "Optionale Parameter", "- ``vel``: Geschwindigkeitsprozentsatz, [0~100] Standard 20.0
    - ``acc``: Beschleunigungsprozentsatz, [0~100] Standard 100.0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Jog-Tippbetrieb mit Verzögerung stoppen
++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``StopJOG(ref)``"
    "Beschreibung", "Jog-Tippbetrieb mit Verzögerung stoppen"
    "Erforderliche Parameter", "- ``ref``: 1-Jog im Gelenkraum stoppen, 3-Jog im Basiskoordinatensystem stoppen, 5-Jog im Werkzeugkoordinatensystem stoppen, 9-Jog im Werkstückkoordinatensystem stoppen"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Jog-Tippbetrieb sofort stoppen
+++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ImmStopJOG()``"
    "Beschreibung", "Jog-Tippbetrieb sofort stoppen"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Jog-Steuerung
++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    for i in range(6):
        robot.StartJOG(0, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.ImmStopJOG()
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(2, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.ImmStopJOG()
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(4, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.StopJOG(5)
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(8, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.StopJOG(9)
        time.sleep(1)
    robot.CloseRPC()

Bewegung im Gelenkraum (MoveJ)
+++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveJ(joint_pos, tool, user, desc_pos = [0.0,0.0,0.0,0.0,0.0,0.0], vel = 20.0, acc = 0.0, ovl = 100.0, exaxis_pos = [0.0,0.0,0.0,0.0], blendT = -1.0, offset_flag = 0, offset_pos = [0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Beschreibung", "Bewegung im Gelenkraum (MoveJ)"
    "Erforderliche Parameter", "- ``joint_pos``: Ziel-Gelenkposition, Einheit [°]
    - ``tool``: Werkzeugnummer, [0~14]
    - ``user``: Werkstücknummer, [0~14]"
    "Optionale Parameter", "- ``desc_pos``: Ziel-Kartesische Pose, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch Vorwärtskinematik berechnet)
    - ``vel``: Geschwindigkeitsprozentsatz, [0~100], Standard 20.0
    - ``acc``: Beschleunigungsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0
    - ``exaxis_pos``: Position der externen Achsen 1-4, Standard [0.0,0.0,0.0,0.0]
    - ``blendT``: [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit [ms], Standard -1.0
    - ``offset_flag``: [0]-kein Versatz, [1]-Versatz im Werkstück-/Basiskoordinatensystem, [2]-Versatz im Werkzeugkoordinatensystem, Standard 0
    - ``offset_pos``: Posenversatz, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0]"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Linearbewegung im kartesischen Raum (MoveL)
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveL(desc_pos, tool, user, joint_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0, blendMode=0, exaxis_pos=[0.0, 0.0, 0.0, 0.0], search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], oacc=100.0, config=-1, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)``"
    "Beschreibung", "Linearbewegung im kartesischen Raum (MoveL)"
    "Erforderliche Parameter", "- ``desc_pos``: Ziel-Kartesische Pose, Einheit [mm][°]
    - ``tool``: Werkzeugnummer, [0~14]
    - ``user``: Werkstücknummer, [0~14]"
    "Optionale Parameter", "- ``joint_pos``: Ziel-Gelenkposition, Einheit [°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch inverse Kinematik berechnet)
    - ``vel``: Geschwindigkeitsprozentsatz, [0~100], Standard 20.0
    - ``acc``: Beschleunigungsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0
    - ``blendR``: [-1.0]-Bewegung abschließen (blockierend), [0~1000]-Glättungsradius (nicht blockierend), Einheit [mm], Standard -1.0
    - ``blendMode``: Übergangsart; 0-Innenkreisübergang; 1-Eckpunktübergang, Standard 0
    - ``exaxis_pos``: Position der externen Achsen 1-4, Standard [0.0,0.0,0.0,0.0]
    - ``search``: [0]-keine Schweißdraht-Positionssuche, [1]-Schweißdraht-Positionssuche, Standard 0
    - ``offset_flag``: [0]-kein Versatz, [1]-Versatz im Werkstück-/Basiskoordinatensystem, [2]-Versatz im Werkzeugkoordinatensystem, Standard 0
    - ``offset_pos``: Posenversatz, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``oacc``: Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung (mm/s2), Standard 100
    - ``config``: Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen, Standard -1
    - ``velAccParamMode``: Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit (mm/s) und Beschleunigung (mm/s2), Standard 0
    - ``overSpeedStrategy``: Strategie bei Geschwindigkeitsüberschreitung, 0-Strategie aus; 1-Standard; 2-Fehler und Stopp bei Überschreitung; 3-adaptive Geschwindigkeitsreduzierung, Standard 0
    - ``speedPercent``: Zulässiger Geschwindigkeitsreduzierungsschwellwert in Prozent [0-100], Standard 10%"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Kreisbogenbewegung im kartesischen Raum (MoveC)
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveC(desc_pos_p, tool_p, user_p, desc_pos_t, tool_t, user_t, joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_p=20.0, acc_p=100.0, exaxis_pos_p=[0.0, 0.0, 0.0, 0.0], offset_flag_p=0, offset_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=100.0, exaxis_pos_t=[0.0, 0.0, 0.0, 0.0], offset_flag_t=0, offset_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], ovl=100.0, blendR=-1.0, oacc=100.0, config=-1, velAccParamMode=0)``"
    "Beschreibung", "Kreisbogenbewegung im kartesischen Raum (MoveC)"
    "Erforderliche Parameter", "- ``desc_pos_p``: Kartesische Pose des Zwischenpunkts, Einheit [mm][°]
    - ``tool_p``: Werkzeugnummer für Zwischenpunkt, [0~14]
    - ``user_p``: Werkstücknummer für Zwischenpunkt, [0~14]
    - ``desc_pos_t``: Kartesische Pose des Zielpunkts, Einheit [mm][°]
    - ``tool_t``: Werkzeugnummer für Zielpunkt, [0~14]
    - ``user_t``: Werkstücknummer für Zielpunkt, [0~14]"
    "Optionale Parameter", "- ``joint_pos_p``: Gelenkposition des Zwischenpunkts, Einheit [°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch inverse Kinematik berechnet)
    - ``joint_pos_t``: Gelenkposition des Zielpunkts, Einheit [°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch inverse Kinematik berechnet)
    - ``vel_p``: Geschwindigkeitsprozentsatz für Zwischenpunkt, [0~100], Standard 20.0
    - ``acc_p``: Beschleunigungsprozentsatz für Zwischenpunkt, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``exaxis_pos_p``: Position der externen Achsen am Zwischenpunkt, Standard [0.0,0.0,0.0,0.0]
    - ``offset_flag_p``: Versatz für Zwischenpunkt? [0]-kein Versatz, [1]-Versatz, Standard 0
    - ``offset_pos_p``: Posenversatz für Zwischenpunkt, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``vel_t``: Geschwindigkeitsprozentsatz für Zielpunkt, [0~100], Standard 20.0
    - ``acc_t``: Beschleunigungsprozentsatz für Zielpunkt, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``exaxis_pos_t``: Position der externen Achsen am Zielpunkt, Standard [0.0,0.0,0.0,0.0]
    - ``offset_flag_t``: Versatz für Zielpunkt? [0]-kein Versatz, [1]-Versatz, Standard 0
    - ``offset_pos_t``: Posenversatz für Zielpunkt, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0
    - ``blendR``: [-1.0]-Bewegung abschließen (blockierend), [0~1000]-Glättungsradius (nicht blockierend), Einheit [mm], Standard -1.0
    - ``oacc``: Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung (mm/s2), Standard 100
    - ``config``: Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen, Standard -1
    - ``velAccParamMode``: Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit (mm/s) und Beschleunigung (mm/s2), Standard 0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Vollkreisbewegung im kartesischen Raum (Circle)
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``Circle(desc_pos_p, tool_p, user_p, desc_pos_t, tool_t, user_t, joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_p=20.0, acc_p=0.0, exaxis_pos_p=[0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=0.0, exaxis_pos_t=[0.0, 0.0, 0.0, 0.0], ovl=100.0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], oacc=100.0, blendR=-1, config=-1, velAccParamMode=0)``"
    "Beschreibung", "Vollkreisbewegung im kartesischen Raum (Circle)"
    "Erforderliche Parameter", "- ``desc_pos_p``: Kartesische Pose von Zwischenpunkt 1, Einheit [mm][°]
    - ``tool_p``: Werkzeugnummer für Zwischenpunkt 1, [0~14]
    - ``user_p``: Werkstücknummer für Zwischenpunkt 1, [0~14]
    - ``desc_pos_t``: Kartesische Pose von Zwischenpunkt 2, Einheit [mm][°]
    - ``tool_t``: Werkzeugnummer für Zwischenpunkt 2, [0~14]
    - ``user_t``: Werkstücknummer für Zwischenpunkt 2, [0~14]"
    "Optionale Parameter", "- ``joint_pos_p``: Gelenkposition von Zwischenpunkt 1, Einheit [°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch inverse Kinematik berechnet)
    - ``joint_pos_t``: Gelenkposition von Zwischenpunkt 2, Einheit [°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch inverse Kinematik berechnet)
    - ``vel_p``: Geschwindigkeitsprozentsatz für Zwischenpunkt 1, [0~100], Standard 20.0
    - ``acc_p``: Beschleunigungsprozentsatz für Zwischenpunkt 1, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``exaxis_pos_p``: Position der externen Achsen an Zwischenpunkt 1, Standard [0.0,0.0,0.0,0.0]
    - ``vel_t``: Geschwindigkeitsprozentsatz für Zwischenpunkt 2, [0~100], Standard 20.0
    - ``acc_t``: Beschleunigungsprozentsatz für Zwischenpunkt 2, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``exaxis_pos_t``: Position der externen Achsen an Zwischenpunkt 2, Standard [0.0,0.0,0.0,0.0]
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0
    - ``offset_flag``: [0]-kein Versatz, [1]-Versatz im Werkstück-/Basiskoordinatensystem, [2]-Versatz im Werkzeugkoordinatensystem, Standard 0
    - ``offset_pos``: Posenversatz, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``oacc``: Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung (mm/s2), Standard 100
    - ``blendR``: -1: blockierend; 0~1000: Glättungsradius, Standard -1
    - ``config``: Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen, Standard -1
    - ``velAccParamMode``: Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit (mm/s) und Beschleunigung (mm/s2), Standard 0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Punkt-zu-Punkt-Bewegung im kartesischen Raum (MoveCart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveCart(desc_pos, tool, user, vel=20.0, acc=0.0, ovl=100.0, blendT=-1.0, config=-1)``"
    "Beschreibung", "Punkt-zu-Punkt-Bewegung im kartesischen Raum (MoveCart)"
    "Erforderliche Parameter", "- ``desc_pos``: Ziel-Kartesische Pose
    - ``tool``: Werkzeugnummer, [0~14]
    - ``user``: Werkstücknummer, [0~14]"
    "Optionale Parameter", "- ``vel``: Geschwindigkeitsprozentsatz, [0~100], Standard 20.0
    - ``acc``: Beschleunigungsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0
    - ``blendT``: [-1.0]-Bewegung abschließen (blockierend), [0~500]-Glättungszeit (nicht blockierend), Einheit [ms], Standard -1.0
    - ``config``: Gelenkraumkonfiguration, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen, Standard -1"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für grundlegende Roboter-Bewegungsbefehle
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    j3 = [-29.777, -84.536, 109.275, -114.075, -86.655, 74.257]
    j4 = [-31.154, -95.317, 94.276, -88.079, -89.740, 74.256]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_pos3 = [-487.434, 154.362, 308.576, 176.600, 0.268, -14.061]
    desc_pos4 = [-443.165, 147.881, 480.951, 179.511, -0.775, -15.409]
    offset_pos = [0.0] * 6
    epos = [0.0] * 4
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    oacc = 100.0
    blendT = 0.0
    blendR = 0.0
    flag = 0
    search = 0
    blendMode = 0
    velAccMode = 0
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, blendR=blendR, blendMode=blendMode, exaxis_pos=epos, search=search, offset_flag=flag, offset_pos=offset_pos, oacc=oacc, velAccParamMode=velAccMode)
    print(f"movel errcode:{rtn}")
    rtn = robot.MoveC(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, offset_flag_p=flag, offset_pos_p=offset_pos, desc_pos_t=desc_pos4, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, offset_flag_t=flag, offset_pos_t=offset_pos, ovl=ovl, blendR=blendR, oacc=oacc, velAccParamMode=velAccMode)
    print(f"movec errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.Circle(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, desc_pos_t=desc_pos1, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, ovl=ovl, offset_flag=flag, offset_pos=offset_pos, oacc=oacc, blendR=-1, velAccParamMode=velAccMode)
    print(f"circle errcode:{rtn}")
    rtn = robot.MoveCart(desc_pos=desc_pos4, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, blendT=blendT, config=-1)
    print(f"MoveCart errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, blendR=blendR, blendMode=blendMode, exaxis_pos=epos, search=search, offset_flag=flag, offset_pos=offset_pos, config=-1, velAccParamMode=velAccMode)
    print(f"movel errcode:{rtn}")
    rtn = robot.MoveC(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, offset_flag_p=flag, offset_pos_p=offset_pos, desc_pos_t=desc_pos4, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, offset_flag_t=flag, offset_pos_t=offset_pos, ovl=ovl, blendR=blendR, config=-1, velAccParamMode=velAccMode)
    print(f"movec errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.Circle(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, desc_pos_t=desc_pos1, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, ovl=ovl, offset_flag=flag, offset_pos=offset_pos, oacc=oacc, blendR=-1, velAccParamMode=velAccMode)
    print(f"circle errcode:{rtn}")
    robot.CloseRPC()
    return 0

Spiralbewegung im kartesischen Raum (NewSpiral)
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``NewSpiral(desc_pos, tool, user, param, joint_pos=[0.0,0.0,0.0,0.0,0.0,0.0], vel=20.0, acc=0.0, exaxis_pos=[0.0,0.0,0.0,0.0], ovl=100.0, offset_flag=0, offset_pos=[0.0,0.0,0.0,0.0,0.0,0.0], config=-1)``"
    "Beschreibung", "Spiralbewegung im kartesischen Raum (NewSpiral)"
    "Erforderliche Parameter", "- ``desc_pos``: Ziel-Kartesische Pose, Einheit [mm][°]
    - ``tool``: Werkzeugnummer, [0~14]
    - ``user``: Werkstücknummer, [0~14]
    - ``param=[circle_num, circle_angle, rad_init, rad_add, rotaxis_add, rot_direction, velAccMode]``: circle_num: Anzahl der Windungen; circle_angle: Neigungswinkel der Spirale; rad_init: Anfangsradius; rad_add: Radiusinkrement; rotaxis_add: Inkrement in Richtung der Drehachse; rot_direction: Drehrichtung, 0-im Uhrzeigersinn, 1-gegen Uhrzeigersinn; velAccMode: Modus für Geschwindigkeit/Beschleunigung, 0-Winkelgeschwindigkeit konstant, 1-Lineargeschwindigkeit konstant"
    "Optionale Parameter", "- ``joint_pos``: Ziel-Gelenkposition, Einheit [°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch inverse Kinematik berechnet)
    - ``vel``: Geschwindigkeitsprozentsatz, [0~100], Standard 20.0
    - ``acc``: Beschleunigungsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``exaxis_pos``: Position der externen Achsen 1-4, Standard [0.0,0.0,0.0,0.0]
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0
    - ``offset_flag``: [0]-kein Versatz, [1]-Versatz im Werkstück-/Basiskoordinatensystem, [2]-Versatz im Werkzeugkoordinatensystem, Standard 0
    - ``offset_pos``: Posenversatz, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``config``: Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen, Standard -1"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Spiralbewegung
+++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    j = [67.957, -81.482, 87.595, -95.691, -94.899, -9.727]
    desc_pos = [-123.142, -551.735, 430.549, 178.753, -4.757, 167.754]
    offset_pos1 = [50.0, 0.0, 0.0, -30.0, 0.0, 0.0]
    offset_pos2 = [50.0, 0.0, 0.0, -30.0, 0.0, 0.0]
    epos = [0.0] * 4
    sp = [2, 30.0, 50.0, 10.0, 10.0, 0, 1]  # [circle_num, circle_angle, rad_init, rad_add, rotaxis_add, rot_direction, velAccMode]
    tool = 0
    user = 0
    vel = 30.0
    acc = 60.0
    ovl = 100.0
    blendT = -1.0
    flag = 2
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos1)
    print(f"movej errcode:{rtn}")
    rtn = robot.NewSpiral(desc_pos=desc_pos, tool=tool, user=user, vel=vel, acc=acc, exaxis_pos=epos, ovl=ovl, offset_flag=flag, offset_pos=offset_pos2, param=sp)
    print(f"newspiral errcode:{rtn}")
    robot.CloseRPC()
    return 0

Servobewegung Start
++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ServoMoveStart(cmdType=0)``"
    "Beschreibung", "Start der Servobewegung, wird mit ServoJ- und ServoCart-Befehlen verwendet"
    "Erforderliche Parameter", "- ``cmdType``: Befehlssendetyp, 0=XML-RPC, 1=UDP-Transparentübertragung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Servobewegung Ende
++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ServoMoveEnd(cmdType=0)``"
    "Beschreibung", "Ende der Servobewegung, wird mit ServoJ- und ServoCart-Befehlen verwendet"
    "Erforderliche Parameter", "- ``cmdType``: Befehlssendetyp, 0=XML-RPC, 1=UDP-Transparentübertragung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Gelenkraum-Servomodellbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ServoJ(joint_pos, axisPos, acc = 0.0, vel = 0.0, cmdT = 0.008, filterT = 0.0, gain = 0.0, id=0, cmdType=0)``"
    "Beschreibung", "Gelenkraum-Servomodellbewegung"
    "Erforderliche Parameter", "- ``joint_pos``: Zielgelenkposition, Einheit [°];
    - ``axisPos``: Externe Achsenposition, Einheit mm;"
    "Standardparameter", "- ``acc``: Beschleunigung, Bereich [0~100], vorübergehend nicht geöffnet, Standard ist 0.0;
    - ``vel``: Geschwindigkeit, Bereich [0~100], vorübergehend nicht geöffnet, Standard ist 0.0;
    - ``cmdT``: Befehlssendezyklus, Einheit s, empfohlener Bereich [0.001~0.0016], Standard ist 0.008;
    - ``filterT``: Filterzeit, Einheit [s], vorübergehend nicht geöffnet, Standard ist 0.0;
    - ``gain``: Proportionalverstärker für Zielposition, vorübergehend nicht geöffnet, Standard ist 0.0;
    - ``id``: ServoJ-Befehls-ID, Standard ist 0;
    - ``cmdType``: Befehlssendetyp, 0=XML-RPC, 1=UDP-Transparentübertragung;"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

SDK-Codebeispiel für ServoJ, ServoMoveStart, ServoMoveEnd basierend auf UDP-Kommunikation
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    def TestServoJUDP(self):
        # Callback einstellen
        def callback(src_type, count, cmd_id, data_len, content):
            print("Callback-Funktion: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0

        robot.SetUDPCmdRpyCallback(callback)
        # # Gelenkposition und externe Achsenposition initialisieren
        j= [105, -108, 74, -66, -88.893, -1.621]
        offset_pos = [0, 0, 0, 0, 0, 0]
        epos = [0, 0, 0, 0]
        # # In die Ausgangsposition bewegen
        result=robot.MoveJ(joint_pos=j, tool=0, user=0, vel=100, acc=100, ovl=100,exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        print("MoveJ Rückgabe: {}".format(result))
        vel = 0.0
        acc = 0.0
        cmdT = 0.016
        filterT = 0.0
        gain = 0.0
        flag = 0
        dt = 0.1
        cmdID = 0

        # Aktuelle Gelenkposition abrufen
        ret, j = robot.GetActualJointPosDegree(flag)
        if ret != 0:
            print(f"GetActualJointPosDegree errcode:{ret}")
        while 1:
            count = 300
            result = robot.ServoMoveStart(cmdType=1)
            print("ServoMoveStart Rückgabe: {}".format(result))
            while count > 0:
                result = robot.ServoJ(joint_pos=j, axisPos=epos, acc=acc, vel=vel, cmdT=cmdT,filterT=filterT, gain=gain, id=cmdID, cmdType=1)
                j[0] += dt
                j[1] += dt
                j[2] += dt
                j[3] += dt
                j[4] += dt
                j[5] += dt
                count -= 1
                time.sleep(0.01)
            result = robot.ServoMoveEnd(cmdType=1)
            print("ServoMoveEnd Rückgabe: {}".format(result))

            count = 300
            result = robot.ServoMoveStart(cmdType=1)
            print("ServoMoveStart Rückgabe: {}".format(result))
            while count > 0:
                result = robot.ServoJ(joint_pos=j, axisPos=epos, acc=acc, vel=vel, cmdT=cmdT,filterT=filterT, gain=gain, id=cmdID, cmdType=1)
                j[0] -= dt
                j[1] -= dt
                j[2] -= dt
                j[3] -= dt
                j[4] -= dt
                j[5] -= dt
                count -= 1
                time.sleep(0.01)
            result = robot.ServoMoveEnd(cmdType=1)
            print("ServoMoveEnd Rückgabe: {}".format(result))
        robot.CloseRPC()
        return 0
    TestServoJUDP(robot)

Codebeispiel für Servo-Modus Bewegung im Gelenkraum (ServoJ)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    j = [0.0] * 6
    epos = [0.0] * 4
    vel = 0.0
    acc = 0.0
    cmdT = 0.008
    filterT = 0.0
    gain = 0.0
    flag = 0
    count = 500
    dt = 0.1
    cmdID = 0
    ret, j = robot.GetActualJointPosDegree(flag)
    if ret == 0:
        cmdID += 1
        robot.ServoMoveStart()
        while count:
            robot.ServoJ(joint_pos=j, axisPos=epos, acc=acc, vel=vel, cmdT=cmdT, filterT=filterT, gain=gain, id=cmdID)
            j[4] += dt
            count -= 1
            time.sleep(cmdT)
            rtn, pkg = robot.GetRobotRealTimeState()
            print(f"Servoj Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]},{pkg.lastServoTarget[1]},{pkg.lastServoTarget[2]},{pkg.lastServoTarget[3]},{pkg.lastServoTarget[4]},{pkg.lastServoTarget[5]}")

            if count < 50:
                robot.MotionQueueClear()
                print(f"After queue clear, Servoj Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]},{pkg.lastServoTarget[1]},{pkg.lastServoTarget[2]},{pkg.lastServoTarget[3]},{pkg.lastServoTarget[4]},{pkg.lastServoTarget[5]}")
                break
        robot.ServoMoveEnd()
    else:
        print(f"GetActualJointPosDegree errcode:{ret}")
    robot.CloseRPC()

Start der Gelenkmomentsteuerung
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ServoJTStart(cmdType=0)``"
    "Beschreibung", "Start der Gelenkmomentsteuerung"
    "Erforderliche Parameter", "- ``cmdType``: Befehlssendetyp, 0=XML-RPC, 1=UDP-Transparentübertragung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Gelenkmomentsteuerung
+++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ServoJT(torque, interval, checkFlag=0, jPowerLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],jVelLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], cmdType=0)``"
    "Beschreibung", "Gelenkmomentsteuerung"
    "Erforderliche Parameter", "- ``torque``: j1~j6 Gelenkmoment, Einheit Nm
                - ``interval``: Befehlsperiode, Einheit s, Bereich [0.001~0.008]
                - ``checkFlag``: Erkennungsstrategie 0-keine Einschränkung; 1-Leistungsbegrenzung; 2-Geschwindigkeitsbegrenzung; 3-sowohl Leistungs- als auch Geschwindigkeitsbegrenzung, Standard 0
                - ``jPowerLimit``: Maximale Gelenkleistungsbegrenzung (W), Standard [0.0,0.0,0.0,0.0,0.0,0.0]
                - ``jVelLimit``: Maximale Gelenkgeschwindigkeit (°/s), Standard [0.0,0.0,0.0,0.0,0.0,0.0]
                - ``cmdType``: Befehlssendetyp, 0=XML-RPC, 1=UDP-Transparentübertragung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Ende der Gelenkmomentsteuerung
+++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ServoJTEnd(cmdType=0)``"
    "Beschreibung", "Ende der Gelenkmomentsteuerung"
    "Erforderliche Parameter", "- ``cmdType``: Befehlssendetyp, 0=XML-RPC, 1=UDP-Transparentübertragung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

SDK-Codebeispiel für ServoJT, ServoJTStart, ServoJTEnd basierend auf UDP-Kommunikation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    def TestServoJTUDP(self):
        # Callback einstellen
        def callback(src_type, count, cmd_id, data_len, content):
            print("Callback-Funktion: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0

        robot.SetUDPCmdRpyCallback(callback)
        while True:
            # Gelenkposition und externe Achsenposition initialisieren
            j = [0, -90, 90, 0, 0, 0]
            epos = [0, 0, 0, 0]
            offset_pos = [0, 0, 0, 0, 0, 0]

            # In die Ausgangsposition bewegen
            robot.MoveJ(joint_pos=j, tool=0, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
            time.sleep(3)
            # Zieh-Teaching aktivieren
            result=robot.DragTeachSwitch(1)
            print("DragTeachSwitch Rückgabe: {}".format(result))
            torques = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

            # Gelenkmomente abrufen
            ret, torques = robot.GetJointTorques(flag=1)
            if ret != 0:
                print(f"GetJointTorques errcode:{ret}")

            count = 100
            result = robot.ServoJTStart(cmdType=1)
            print("ServoJTStart Rückgabe: {}".format(result))
            # Vorwärtsmomentsteuerung
            while True:
                torques[0] = 0.03
                result = robot.ServoJT(
                    torque=torques,
                    interval=0.001,
                    checkFlag=0,
                    jPowerLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                    jVelLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                    cmdType=1
                )
                print("Rückgabe: {}".format(result))
                time.sleep(1)

                ret, pkg = robot.GetRobotRealTimeState()
                if pkg.jt_cur_pos[0] > 30:
                    break

            # Rückwärtsmomentsteuerung
            while True:
                torques[0] = -0.03
                result = robot.ServoJT(
                        torque=torques,
                        interval=0.001,
                        checkFlag=0,
                        jPowerLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                        jVelLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                        cmdType=1
                    )
                print("Rückgabe: {}".format(result))
                time.sleep(1)

                ret, pkg = robot.GetRobotRealTimeState()
                if pkg.jt_cur_pos[0] < 0:
                    break

            # Momentsteuerung beenden und Zieh-Teaching deaktivieren
            result = robot.ServoJTEnd(cmdType=1)
            print("ServoJTEnd Rückgabe: {}".format(result))
            result = robot.DragTeachSwitch(0)
            print("DragTeachSwitch Rückgabe: {}".format(result))

        robot.CloseRPC()
        return 0
    TestServoJTUDP(robot)

Codebeispiel für Gelenk-Drehmomentregelung (ServoJT)
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    error, torques = robot.GetJointTorques(1)
    robot.ServoJTStart()
    count = 100
    while count > 0:
        error = robot.ServoJT(torques, 0.001)
        count -= 1
        time.sleep(0.001)
    error = robot.ServoJTEnd()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Servo-Modus Bewegung im kartesischen Raum (ServoCart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ServoCart(mode, desc_pos, exaxis, pos_gain=[1.0, 1.0, 1.0, 1.0, 1.0, 1.0], acc=0.0, vel=0.0, cmdT=0.008, filterT=0.0, gain=0.0)``"
    "Beschreibung", "Servo-Modus Bewegung im kartesischen Raum (ServoCart)"
    "Erforderliche Parameter", "- ``mode``: [0]-Absolutbewegung (Basiskoordinatensystem), [1]-Inkrementalbewegung (Basiskoordinatensystem), [2]-Inkrementalbewegung (Werkzeugkoordinatensystem)
    - ``desc_pos``: Ziel-Kartesische Pose oder Poseninkrement
    - ``exaxis``: Position der Erweiterungsachse"
    "Optionale Parameter", "- ``pos_gain``: Proportionalbeiwert für Poseninkrement, nur bei inkrementaler Bewegung wirksam, Bereich [0~1], Standard [1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
    - ``acc``: Beschleunigungsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``vel``: Geschwindigkeitsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``cmdT``: Befehlsübermittlungszyklus, Einheit s, empfohlen [0.001~0.0016], Standard 0.008
    - ``filterT``: Filterzeit, Einheit s (vorerst nicht verfügbar), Standard 0.0
    - ``gain``: Proportionalverstärkung für Zielposition (vorerst nicht verfügbar), Standard 0.0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Servo-Modus Bewegung im kartesischen Raum (ServoCart)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    desc_pos_dt = [83.00800, 50.525000, 29.246, 179.629, -7.138, -166.975]
    exaxis = [100.0, 0.0, 0.0, 0.0]
    pos_gain = [0.0] * 6
    mode = 0
    vel = 0.0
    acc = 0.0
    cmdT = 0.001
    filterT = 0.0
    gain = 0.0
    flag = 0
    count = 5000
    robot.SetSpeed(20)
    while count:
        rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain)
        print(f"ServoCart rtn is {rtn}")
        count -= 1
        desc_pos_dt[0] += 0.01
        exaxis[0] += 0.01
    robot.CloseRPC()
    return 0

Spline-Bewegung starten
+++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SplineStart()``"
    "Beschreibung", "Spline-Bewegung starten"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Spline-PTP-Bewegung
++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SplinePTP(joint_pos, tool, user, desc_pos=[0.0,0.0,0.0,0.0,0.0,0.0], vel=20.0, acc=100.0, ovl=100.0)``"
    "Beschreibung", "Spline-PTP-Bewegung im Gelenkraum"
    "Erforderliche Parameter", "- ``joint_pos``: Ziel-Gelenkposition, Einheit [°]
    - ``tool``: Werkzeugnummer, [0~14]
    - ``user``: Werkstücknummer, [0~14]"
    "Optionale Parameter", "- ``desc_pos``: Ziel-Kartesische Pose, Einheit [mm][°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch Vorwärtskinematik berechnet)
    - ``vel``: Geschwindigkeitsprozentsatz, [0~100], Standard 20.0
    - ``acc``: Beschleunigungsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 100.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Spline-Bewegung beenden
+++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SplineEnd()``"
    "Beschreibung", "Spline-Bewegung beenden"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Spline-Bewegung
++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    joint_points = [
        [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256],  # j1
        [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255],  # j2
        [-61.954, -84.409, 108.153, -116.316, -91.283, 74.260],  # j3
        [-89.575, -80.276, 102.713, -116.302, -91.284, 74.267]  # j4
    ]
    cart_points = [
        [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833],  # desc_pos1
        [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869],  # desc_pos2
        [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207],  # desc_pos3
        [-104.066, 544.321, 327.023, -177.715, 3.371, -73.818]  # desc_pos4
    ]
    offset_pos = [0] * 6 
    epos = [0] * 4 
    tool = user = 0
    vel = acc = ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    err1 = robot.MoveJ(joint_pos=joint_points[0], tool=tool, user=user, vel=vel)
    print(f"MoveJ Fehlercode: {err1}")
    robot.SplineStart()
    robot.SplinePTP(joint_pos=joint_points[0], tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[1], tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[2], tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[3], tool=tool, user=user)
    robot.SplineEnd()
    robot.CloseRPC()

Neue Spline-Bewegung starten (NewSpline)
+++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``NewSplineStart(type, averageTime=2000)``"
    "Beschreibung", "Neue Spline-Bewegung starten (NewSpline)"
    "Erforderliche Parameter", "- ``type``: 0-Kreisbogenübergang, 1-gegebene Punkte sind Bahnpunkte"
    "Optionale Parameter", "- ``averageTime``: Globale durchschnittliche Übergangszeit (ms), Standard 2000"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Neuer Spline-Befehlspunkt
+++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``NewSplinePoint(desc_pos, tool, user, lastFlag, joint_pos=[0.0,0.0,0.0,0.0,0.0,0.0], vel=0.0, acc=0.0, ovl=100.0, blendR=0.0)``"
    "Beschreibung", "Einen Punkt zu einer neuen Spline-Bewegung hinzufügen"
    "Erforderliche Parameter", "- ``desc_pos``: Ziel-Kartesische Pose, Einheit [mm][°]
    - ``tool``: Werkzeugnummer, [0~14]
    - ``user``: Werkstücknummer, [0~14]
    - ``lastFlag``: Ist dies der letzte Punkt? 0-nein, 1-ja"
    "Optionale Parameter", "- ``joint_pos``: Ziel-Gelenkposition, Einheit [°], Standard [0.0,0.0,0.0,0.0,0.0,0.0] (wird durch inverse Kinematik berechnet)
    - ``vel``: Geschwindigkeitsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``acc``: Beschleunigungsprozentsatz, [0~100] (vorerst nicht verfügbar), Standard 0.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor, [0~100], Standard 100.0
    - ``blendR``: [0~1000]-Glättungsradius (nicht blockierend), Einheit [mm], Standard 0.0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Neue Spline-Bewegung beenden
++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``NewSplineEnd()``"
    "Beschreibung", "Neue Spline-Bewegung beenden"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für neue Spline-Bewegung
+++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    j3 = [-61.954, -84.409, 108.153, -116.316, -91.283, 74.260]
    j4 = [-89.575, -80.276, 102.713, -116.302, -91.284, 74.267]
    j5 = [-95.228, -54.621, 73.691, -112.245, -91.280, 74.268]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_pos3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    desc_pos4 = [-104.066, 544.321, 327.023, -177.715, 3.371, -73.818]
    desc_pos5 = [-33.421, 732.572, 275.103, -177.907, 2.709, -79.482]
    offset_pos = [0, 0, 0, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    err1 = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    print(f"movej errcode:{err1}")
    robot.NewSplineStart(1, 2000)
    robot.NewSplinePoint(desc_pos=desc_pos1, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos3, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos4, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos5, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplineEnd()
    robot.CloseRPC()

Roboterbewegung abbrechen (StopMotion)
++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``StopMotion()``"
    "Beschreibung", "Bewegung abbrechen (erfordert nicht-blockierende Bewegungsbefehle)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Roboterbewegung pausieren (PauseMotion)
++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PauseMotion()``"
    "Beschreibung", "Bewegung pausieren (erfordert nicht-blockierende Bewegungsbefehle)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Roboterbewegung fortsetzen (ResumeMotion)
+++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ResumeMotion()``"
    "Beschreibung", "Bewegung fortsetzen (erfordert nicht-blockierende Bewegungsbefehle)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Bewegung pausieren, fortsetzen, abbrechen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    j1 =[-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j5 =[-95.228, -54.621, 73.691, -112.245, -91.280, 74.268]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos5 = [-33.421, 732.572, 275.103, -177.907, 2.709, -79.482]
    offset_pos = [0, 0, 0, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    rtn = robot.MoveJ(joint_pos=j5, tool=tool, user=user, vel=vel, blendT=1)
    time.sleep(1)
    robot.PauseMotion()
    time.sleep(1)
    robot.ResumeMotion()
    time.sleep(1)
    robot.StopMotion()
    time.sleep(1)
    robot.CloseRPC()

Globalen Punktversatz aktivieren
++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointsOffsetEnable(flag, offset_pos)``"
    "Beschreibung", "Globalen Punktversatz aktivieren"
    "Erforderliche Parameter", "- ``flag``: 0-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    - ``offset_pos``: Versatz, Einheit [mm][°]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Globalen Punktversatz deaktivieren
+++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointsOffsetDisable()``"
    "Beschreibung", "Globalen Punktversatz deaktivieren"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Punktversatz
+++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    offset_pos = [0, 0, 0, 0, 0, 0]
    offset_pos1 = [0, 0, 50, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    time.sleep(1)
    robot.PointsOffsetEnable(flag=0, offset_pos=offset_pos1)
    robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.PointsOffsetDisable()
    robot.CloseRPC()

Steuerschrank AO High-Speed-Ausgabe starten (MoveAOStart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveAOStart(AONum, maxTCPSpeed=1000, maxAOPercent=100, zeroZoneCmp=20)``"
    "Beschreibung", "Steuerschrank AO High-Speed-Ausgabe starten"
    "Erforderliche Parameter", "- ``AONum``: Steuerschrank AO-Nummer"
    "Optionale Parameter", "- ``maxTCPSpeed``: Maximaler TCP-Geschwindigkeitswert [1-5000 mm/s], Standard 1000
    - ``maxAOPercent``: AO-Prozentsatz für maximale TCP-Geschwindigkeit, Standard 100%
    - ``zeroZoneCmp``: AO-Prozentsatz für Totzonenkompensation, Ganzzahl, Standard 20, Bereich [0-100]"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Steuerschrank AO High-Speed-Ausgabe stoppen (MoveAOStop)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveAOStop()``"
    "Beschreibung", "Steuerschrank AO High-Speed-Ausgabe stoppen"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Endeffektor AO High-Speed-Ausgabe starten (MoveToolAOStart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToolAOStart(AONum, maxTCPSpeed=1000, maxAOPercent=100, zeroZoneCmp=20)``"
    "Beschreibung", "Endeffektor AO High-Speed-Ausgabe starten"
    "Erforderliche Parameter", "- ``AONum``: Endeffektor AO-Nummer"
    "Optionale Parameter", "- ``maxTCPSpeed``: Maximaler TCP-Geschwindigkeitswert [1-5000 mm/s], Standard 1000
    - ``maxAOPercent``: AO-Prozentsatz für maximale TCP-Geschwindigkeit, Standard 100%
    - ``zeroZoneCmp``: AO-Prozentsatz für Totzonenkompensation, Ganzzahl, Standard 20, Bereich [0-100]"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Endeffektor AO High-Speed-Ausgabe stoppen (MoveToolAOStop)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToolAOStop()``"
    "Beschreibung", "Endeffektor AO High-Speed-Ausgabe stoppen"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für AO High-Speed-Ausgabe (MoveAO)
++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    offset_pos = [0, 0, 0, 0, 0, 0]
    offset_pos1 = [0, 0, 50, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 20.0
    acc = 20.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    robot.MoveAOStart(0, 100, 100, 20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.MoveAOStop()
    time.sleep(1)
    robot.MoveToolAOStart(0, 100, 100, 20)
    robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.MoveToolAOStop()
    robot.CloseRPC()

PTP-Bewegung mit FIR-Filterung starten
++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PtpFIRPlanningStart(maxAcc, maxJek)``"
    "Beschreibung", "PTP-Bewegung mit FIR-Filterung starten"
    "Erforderliche Parameter", "- ``maxAcc``: Maximale Beschleunigung (deg/s²)
    - ``maxJek``: Maximale einheitliche Gelenkruck (deg/s³)"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

PTP-Bewegung mit FIR-Filterung beenden
++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PtpFIRPlanningEnd()``"
    "Beschreibung", "PTP-Bewegung mit FIR-Filterung beenden"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

LIN-/ARC-Bewegung mit FIR-Filterung starten
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LinArcFIRPlanningStart(maxAccLin, maxAccDeg, maxJerkLin, maxJerkDeg)``"
    "Beschreibung", "LIN-/ARC-Bewegung mit FIR-Filterung starten"
    "Erforderliche Parameter", "- ``maxAccLin``: Maximale Linearbeschleunigung (mm/s²)
    - ``maxAccDeg``: Maximale Winkelbeschleunigung (deg/s²)
    - ``maxJerkLin``: Maximaler Linearruck (mm/s³)
    - ``maxJerkDeg``: Maximaler Winkelruck (deg/s³)"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

LIN-/ARC-Bewegung mit FIR-Filterung beenden
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LinArcFIRPlanningEnd()``"
    "Beschreibung", "LIN-/ARC-Bewegung mit FIR-Filterung beenden"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für FIR-Filterung
++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    midjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    endjointPos = [-29.777, -84.536, 109.275, -114.075, -86.655, 74.257]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    middescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    enddescPose = [-487.434, 154.362, 308.576, 176.600, 0.268, -14.061]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.PtpFIRPlanningStart(1000.0, 1000.0)
    print(f"PtpFIRPlanningStart rtn is {rtn}")
    error = robot.MoveJ(joint_pos=startjointPos,tool= 0,user= 0,desc_pos=startdescPose,vel= 100,acc=100,ovl=100, blendT=-1.0, offset_flag=0)
    print(f"MoveJ rtn is {rtn}")
    error = robot.MoveJ(joint_pos=endjointPos,tool= 0,user= 0,desc_pos=enddescPose,vel= 100,acc=100,ovl=100, blendT=-1.0, offset_flag=0)
    print(f"MoveJ rtn is {rtn}")
    robot.PtpFIRPlanningEnd()
    print(f"PtpFIRPlanningEnd rtn is {rtn}")
    rtn = robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000)
    print(f"LinArcFIRPlanningStart rtn is {rtn}")
    error = robot.MoveL(desc_pos=startdescPose,tool= 0,user= 0, joint_pos=startjointPos,vel= 100,overSpeedStrategy=1,speedPercent=1)
    print(f"MoveL rtn is {rtn}")
    error = robot.MoveC(desc_pos_p=middescPose,tool_p= 0,user_p= 0, joint_pos_p=midjointPos,vel_p= 100,desc_pos_t=enddescPose,tool_t= 0,user_t= 0,joint_pos_t=endjointPos,vel_t= 100)
    print(f"MoveC rtn is {rtn}")
    robot.LinArcFIRPlanningEnd()
    print(f"LinArcFIRPlanningEnd rtn is {rtn}")
    robot.CloseRPC()

Beschleunigungsglättung aktivieren
+++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AccSmoothStart(saveFlag)``"
    "Beschreibung", "Beschleunigungsglättung aktivieren"
    "Erforderliche Parameter", "- ``saveFlag``: Bei Stromausfall speichern? (0-nein, 1-ja)"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Beschleunigungsglättung deaktivieren
++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AccSmoothEnd(saveFlag)``"
    "Beschreibung", "Beschleunigungsglättung deaktivieren"
    "Erforderliche Parameter", "- ``saveFlag``: Bei Stromausfall speichern? (0-nein, 1-ja)"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Beschleunigungsglättung
++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.AccSmoothStart(0)
    print(f"AccSmoothStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos,tool= 0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos,tool= 0,user= 0,vel= 100)
    rtn = robot.AccSmoothEnd(0)
    print(f"AccSmoothEnd rtn is {rtn}")
    robot.CloseRPC()

Spezifische Ausrichtungsgeschwindigkeit aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AngularSpeedStart(ratio)``"
    "Beschreibung", "Spezifische Ausrichtungsgeschwindigkeit aktivieren"
    "Erforderliche Parameter", "- ``ratio``: Ausrichtungsgeschwindigkeitsprozentsatz [0-300]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Spezifische Ausrichtungsgeschwindigkeit deaktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AngularSpeedEnd()``"
    "Beschreibung", "Spezifische Ausrichtungsgeschwindigkeit deaktivieren"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für spezifische Ausrichtungsgeschwindigkeit
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.AngularSpeedStart(50)
    print(f"AngularSpeedStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos, tool=0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos, tool=0,user= 0,vel= 100)
    rtn = robot.AngularSpeedEnd()
    print(f"AngularSpeedEnd rtn is {rtn}")
    robot.CloseRPC()

Singularitätsschutz starten
++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SingularAvoidStart(protectMode, minShoulderPos=100, minElbowPos=50, minWristPos=10)``"
    "Beschreibung", "Singularitätsschutz starten"
    "Erforderliche Parameter", "- ``protectMode``: Singularitätsschutzmodus, 0: Gelenkmodus; 1: Kartesischer Modus"
    "Optionale Parameter", "- ``minShoulderPos``: Einstellbereich für Schulter-Singularität (mm), Standard 100.0
    - ``minElbowPos``: Einstellbereich für Ellenbogen-Singularität (mm), Standard 50.0
    - ``minWristPos``: Einstellbereich für Handgelenks-Singularität (°), Standard 10.0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Singularitätsschutz stoppen
++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SingularAvoidEnd()``"
    "Beschreibung", "Singularitätsschutz stoppen"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Singularitätsschutz
++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.SingularAvoidStart(2, 10, 5, 5)
    print(f"SingularAvoidStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos, tool=0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos, tool=0,user= 0,vel= 100)
    rtn = robot.SingularAvoidEnd()
    print(f"SingularAvoidEnd rtn is {rtn}")
    robot.CloseRPC()

Bewegungsbefehlswarteschlange leeren
+++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MotionQueueClear()``"
    "Beschreibung", "Bewegungsbefehlswarteschlange leeren"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Bewegung zum Startpunkt einer Durchdringungskurve
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToIntersectLineStart(mainPoint, piecePoint, tool, wobj, vel, acc, ovl, oacc, moveType, mainExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]], pieceExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]], extAxisFlag=0, exaxisPos=[0.0,0.0,0.0,0.0], moveDirection=0, offset=[0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Beschreibung", "Bewegung zum Startpunkt einer Durchdringungskurve"
    "Erforderliche Parameter", "- ``mainPoint``: Kartesische Posen der 6 Teach-Punkte des Hauptrohrs
    - ``piecePoint``: Kartesische Posen der 6 Teach-Punkte des Nebenrohrs
    - ``tool``: Werkzeugkoordinatensystem-Nummer
    - ``wobj``: Werkstückkoordinatensystem-Nummer
    - ``vel``: Geschwindigkeitsprozentsatz
    - ``acc``: Beschleunigungsprozentsatz
    - ``ovl``: Geschwindigkeitsskalierungsfaktor
    - ``oacc``: Beschleunigungsskalierungsfaktor
    - ``moveType``: Bewegungstyp; 0-PTP; 1-LIN"
    "Optionale Parameter", "- ``mainExaxisPos``: Positionen der Erweiterungsachse für die 6 Teach-Punkte des Hauptrohrs, Standard [[0.0,0.0,0.0,0.0], ...]
    - ``pieceExaxisPos``: Positionen der Erweiterungsachse für die 6 Teach-Punkte des Nebenrohrs, Standard [[0.0,0.0,0.0,0.0], ...]
    - ``extAxisFlag``: Erweiterungsachse verwenden? 0-nein; 1-ja, Standard 0
    - ``exaxisPos``: Startposition der Erweiterungsachse [0.0,0.0,0.0,0.0], Standard [0.0,0.0,0.0,0.0]
    - ``moveDirection``: Bewegungsrichtung; 0-im Uhrzeigersinn; 1-gegen Uhrzeigersinn, Standard 0
    - ``offset``: Versatz [x,y,z,rx,ry,rz], Standard [0.0,0.0,0.0,0.0,0.0,0.0]"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Bewegung entlang einer Durchdringungskurve
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveIntersectLine(mainPoint, piecePoint, tool, wobj, vel, acc, ovl, oacc, moveDirection, mainExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]], pieceExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]], extAxisFlag=0, exaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]], offset=[0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Beschreibung", "Bewegung entlang einer Durchdringungskurve"
    "Erforderliche Parameter", "- ``mainPoint``: Kartesische Posen der 6 Teach-Punkte des Hauptrohrs
    - ``piecePoint``: Kartesische Posen der 6 Teach-Punkte des Nebenrohrs
    - ``tool``: Werkzeugkoordinatensystem-Nummer
    - ``wobj``: Werkstückkoordinatensystem-Nummer
    - ``vel``: Geschwindigkeitsprozentsatz
    - ``acc``: Beschleunigungsprozentsatz
    - ``ovl``: Geschwindigkeitsskalierungsfaktor
    - ``oacc``: Beschleunigungsskalierungsfaktor
    - ``moveDirection``: Bewegungsrichtung; 0-im Uhrzeigersinn; 1-gegen Uhrzeigersinn"
    "Optionale Parameter", "- ``mainExaxisPos``: Positionen der Erweiterungsachse für die 6 Teach-Punkte des Hauptrohrs, Standard [[0.0,0.0,0.0,0.0], ...]
    - ``pieceExaxisPos``: Positionen der Erweiterungsachse für die 6 Teach-Punkte des Nebenrohrs, Standard [[0.0,0.0,0.0,0.0], ...]
    - ``extAxisFlag``: Erweiterungsachse verwenden? 0-nein; 1-ja, Standard 0
    - ``exaxisPos``: Positionen der Erweiterungsachse (Array der Länge 4), Standard [[0.0,0.0,0.0,0.0], ...]
    - ``offset``: Versatz [x,y,z,rx,ry,rz], Standard [0.0,0.0,0.0,0.0,0.0,0.0]"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Bewegung entlang einer Durchdringungskurve
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    mainPoint = [[0.0] * 6 for _ in range(6)]
    piecePoint = [[0.0] * 6 for _ in range(6)]
    mainExaxisPos = [[0.0] * 4 for _ in range(6)]
    pieceExaxisPos = [[0.0] * 4 for _ in range(6)]
    extAxisFlag = 1
    exaxisPos = [[0.0] * 4 for _ in range(4)]
    offset = [0.0, 2.0, 30.0, -2.0, 0.0, 0.0]
    mainPoint[0] = [490.004, -383.194, 402.735, -9.332, -1.528, 69.594]
    mainPoint[1] = [444.950, -407.117, 389.011, -5.546, -2.196, 65.279]
    mainPoint[2] = [445.168, -463.605, 355.759, -1.544, -10.886, 57.104]
    mainPoint[3] = [507.529, -485.385, 343.013, -0.786, -4.834, 61.799]
    mainPoint[4] = [554.390, -442.647, 367.701, -4.761, -10.181, 64.925]
    mainPoint[5] = [532.552, -394.003, 396.467, -13.732, -13.592, 67.411]
    mainExaxisPos[0] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[1] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[2] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[3] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[4] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[5] = [-29.996, 0.000, 0.000, 0.000]
    piecePoint[0] = [505.571, -192.408, 316.759, 38.098, 37.051, 139.447]
    piecePoint[1] = [533.837, -201.558, 332.340, 34.644, 42.339, 137.748]
    piecePoint[2] = [530.386, -225.085, 373.808, 35.431, 45.111, 137.560]
    piecePoint[3] = [485.646, -229.195, 383.778, 33.870, 45.173, 137.064]
    piecePoint[4] = [460.551, -212.161, 354.256, 28.856, 45.602, 135.930]
    piecePoint[5] = [474.217, -197.124, 324.611, 42.469, 41.133, 148.167]
    pieceExaxisPos[0] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[1] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[2] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[3] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[4] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[5] = [-29.996, -0.000, 0.000, 0.000]
    exaxisPos[0] = [-29.996, -0.000, 0.000, 0.000]
    exaxisPos[1] = [-44.994, 90.000, 0.000, 0.000]
    exaxisPos[2] = [-59.992, 0.002, 0.000, 0.000]
    exaxisPos[3] = [-44.994, -89.997, 0.000, 0.000]
    tool = 2
    wobj = 0
    vel = 100.0
    acc = 100.0
    ovl = 12.0
    oacc = 12.0
    moveType = 1
    moveDirection = 1
    rtn = robot.MoveToIntersectLineStart(mainPoint=mainPoint, mainExaxisPos=mainExaxisPos, piecePoint=piecePoint, pieceExaxisPos=pieceExaxisPos, extAxisFlag=extAxisFlag,exaxisPos=exaxisPos[0], tool=tool, wobj=wobj, vel=vel, acc=acc, ovl=ovl, oacc=oacc, moveType=moveType, moveDirection=moveDirection, offset=offset)
    print(f"MoveToIntersectLineStart rtn is {rtn}")
    rtn = robot.MoveIntersectLine(mainPoint=mainPoint, mainExaxisPos=mainExaxisPos, piecePoint=piecePoint, pieceExaxisPos=pieceExaxisPos, extAxisFlag=extAxisFlag, exaxisPos=exaxisPos, tool=tool,wobj=wobj, vel=vel, acc=acc, ovl=5.0, oacc=5.0, moveDirection=moveDirection, offset=offset)
    print(f"MoveIntersectLine rtn is {rtn}")
    robot.CloseRPC()

Bewegung auf der Stelle (ohne Positionsänderung)
++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveStationary()``"
    "Beschreibung", "Bewegung auf der Stelle (ohne Positionsänderung)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Bewegung auf der Stelle
++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 0, 10, 100)
    print(f"LaserSensorRecordandReplay rtn is {rtn}")
    rtn = robot.MoveStationary()
    print(f"MoveStationary rtn is {rtn}")
    rtn = robot.LaserSensorRecord1(0, 10)
    print(f"LaserSensorRecordandReplay rtn is {rtn}")
    robot.CloseRPC()
    return 0

Stationäres Pendeln Start
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OriginPointWeaveStart(weaveNum, mode, refPoint, weaveTime)``"
    "Beschreibung", "Start des stationären Pendelns"
    "Erforderliche Parameter", "
    - ``weaveNum``: Pendelnummer [0-7]
    - ``mode``: 0-Werkzeugkoordinatensystem; 1-Referenzpunkt
    - ``refPoint``: Referenzpunkt-Koordinaten im kartesischen Koordinatensystem [x,y,z,a,b,c]
    - ``weaveTime``: Pendelzeit [s]
    - "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Stationäres Pendeln Ende
+++++++++++++++++++++++++++++++++
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OriginPointWeaveEnd()``"
    "Beschreibung", "Ende des stationären Pendelns"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode"

SDK-Codebeispiel für stationäres Pendeln
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    def TestOriginPointWeave(self):
        time.sleep(2)
        # Gelenkposition, externe Achse und Offset initialisieren
        j = [39.886, -98.580, -124.032, -47.393, 90.000, 40.842]
        epos = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]

        # Referenzpunktposition [x, y, z, rx, ry, rz]
        refPoint = [400.021, 300.022, 299.996, 179.997, -0.003, -90.956]

        # In die Startposition bewegen
        robot.MoveJ(joint_pos=j, tool=1, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Erstes Pendeln: Absolutes Koordinatensystem (tool=0), Modus 0
        robot.OriginPointWeaveStart(0, 0, refPoint, 3)
        robot.MoveStationary()
        robot.OriginPointWeaveEnd()

        time.sleep(2)

        # Erneut in die Startposition bewegen
        robot.MoveJ(joint_pos=j, tool=1, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Zweites Pendeln: Absolutes Koordinatensystem (tool=0), Modus 1
        robot.OriginPointWeaveStart(0, 1, refPoint, 3)
        robot.MoveStationary()
        robot.OriginPointWeaveEnd()

        # Verbindung schließen
        robot.CloseRPC()
        time.sleep(1)

    TestOriginPointWeave(robot)

SDK-Codebeispiel für stationäres Pendeln (mit Laser und Erweiterungsachse)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    def TestOriginPointWeave(self):
        time.sleep(2)
        # Gelenkposition, externe Achse und Offset initialisieren
        j = [39.886, -98.580, -124.032, -47.393, 90.000, 40.842]
        epos1 = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]
        epos2 = [5, 0.000, 0.000, 0.000]
        # Referenzpunktposition [x, y, z, rx, ry, rz]
        refPoint = [400.021, 300.022, 299.996, 179.997, -0.003, -90.956]

        rtn = 0
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020)
        robot.LaserTrackingSensorSamplePeriod(20)
        robot.LoadPosSensorDriver(101)

        # UDP-Treiber laden
        robot.ExtDevLoadUDPDriver()

        # Positionierungsabschlusszeit für Erweiterungsachse einstellen
        rtn = robot.SetExAxisCmdDoneTime(5000.0)
        print(f"SetExAxisCmdDoneTime rtn is {rtn}")

        # Erweiterungsachsen 1 und 2 aktivieren
        rtn = robot.ExtAxisServoOn(1, 1)
        print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
        rtn = robot.ExtAxisServoOn(2, 1)
        print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
        time.sleep(2)

        # Referenzfahrt für Erweiterungsachse einstellen
        robot.ExtAxisSetHoming(1, 0, 10, 2)
        robot.LaserTrackingLaserOnOff(1)

        # 1---Ohne Erweiterungsachse
        robot.LaserTrackingTrackOnOff(1, 4)
        time.sleep(0.2)
        # Stationäres Pendeln starten
        robot.OriginPointWeaveStart(0, 0, refPoint, 10)
        robot.MoveStationary()  # Stationäre Bewegung ausführen (vorausgesetzt, diese Methode existiert)
        robot.OriginPointWeaveEnd()
        robot.LaserTrackingTrackOnOff(0, 4)

        time.sleep(2)  # 2 Sekunden warten

        # 2----Mit Erweiterungsachse
        robot.ExtAxisMove(epos1, 100, -1)
        robot.LaserTrackingTrackOnOff(1, 4)
        # Stationäres Pendeln starten
        robot.OriginPointWeaveStart(0, 0, refPoint, 20)
        robot.ExtAxisMove(epos2, 100, -1)
        robot.OriginPointWeaveEnd()
        robot.LaserTrackingTrackOnOff(0, 4)

        # Verbindung schließen
        robot.CloseRPC()
        time.sleep(1)

    TestOriginPointWeave(robot)