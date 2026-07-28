Allgemeine Roboter-Einstellungen
============================================

.. toctree::
    :maxdepth: 5

Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolPoint(point_num)``"
    "Beschreibung", "Legt den Werkzeug-Referenzpunkt fest - Sechs-Punkt-Methode"
    "Erforderliche Parameter", "- ``point_num``: Punktnummer, Bereich [1~6]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Werkzeugkoordinatensystem berechnen - Sechs-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeTool()``"
    "Beschreibung", "Berechnet das Werkzeugkoordinatensystem - Sechs-Punkt-Methode (nach dem Setzen aller sechs Referenzpunkte)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Werkzeugkoordinatensystem"

Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTcp4RefPoint(point_num)``"
    "Beschreibung", "Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode"
    "Erforderliche Parameter", "``point_num``: Punktnummer, Bereich [1~4]"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Werkzeugkoordinatensystem"

Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeTcp4()``"
    "Beschreibung", "Berechnet das Werkzeugkoordinatensystem - Vier-Punkt-Methode (nach dem Setzen aller vier Referenzpunkte)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Werkzeugkoordinatensystem"

Werkzeugkoordinatensystem basierend auf Punkten berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeToolCoordWithPoints(method, pos)``"
    "Beschreibung", "Berechnet das Werkzeugkoordinatensystem basierend auf Punkten"
    "Erforderliche Parameter", "
    - ``method``: Berechnungsmethode; 0-Vier-Punkt-Methode; 1-Sechs-Punkt-Methode
    - ``pos``: Array von Gelenkpositionen, Länge 4 für Vier-Punkt, Länge 6 für Sechs-Punkt"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``tcp_offset=[x,y,z,rx,ry,rz]``: Berechnetes Werkzeugkoordinatensystem, Einheit [mm][°]"

Werkzeugkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolCoord(id, t_coord, type, install, toolID, loadNum)``"
    "Beschreibung", "Stellt das Werkzeugkoordinatensystem ein"
    "Erforderliche Parameter", "- ``id``: Koordinatensystem-Nummer, Bereich [1~15]
    - ``t_coord``: Pose des Werkzeugmittelpunkts relativ zur Flanschmitte, Einheit [mm][°]
    - ``type``: 0-Werkzeugkoordinatensystem, 1-Sensorkoordinatensystem
    - ``install``: Einbauort, 0-Roboterflansch, 1-außerhalb des Roboters
    - ``toolID``: Werkzeug-ID
    - ``loadNum``: Nutzlastnummer"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Liste der Werkzeugkoordinatensysteme einstellen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolList(id, t_coord, type, install, loadNum)``"
    "Beschreibung", "Stellt die Liste der Werkzeugkoordinatensysteme ein"
    "Erforderliche Parameter", "- ``id``: Koordinatensystem-Nummer, Bereich [1~15]
    - ``t_coord``: Pose des Werkzeugmittelpunkts relativ zur Flanschmitte, Einheit [mm][°]
    - ``type``: 0-Werkzeugkoordinatensystem, 1-Sensorkoordinatensystem
    - ``install``: Einbauort, 0-Roboterflansch, 1-außerhalb des Roboters
    - ``loadNum``: Nutzlastnummer"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Aktuelles Werkzeugkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTCPOffset(flag=1)``"
    "Beschreibung", "Gibt das aktuelle Werkzeugkoordinatensystem zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "- ``flag``: 0-blockierend, 1-nicht blockierend, Standard 1"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``tcp_offset=[x,y,z,rx,ry,rz]``: Relative Pose des aktuellen Werkzeugkoordinatensystems, Einheit [mm][°]"

Codebeispiel für Operationen mit Roboter-Werkzeugkoordinatensystemen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posJ = [p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint]
    rtn, coordRtn = robot.ComputeToolCoordWithPoints(1, posJ)
    print(f"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint, tool=0, user=0, vel=100)
    robot.SetToolPoint(1)
    robot.MoveJ(joint_pos=p2Joint, tool=0, user=0, vel=100)
    robot.SetToolPoint(2)
    robot.MoveJ(joint_pos=p3Joint, tool=0, user=0, vel=100)
    robot.SetToolPoint(3)
    robot.MoveJ(joint_pos=p4Joint, tool=0, user=0, vel=100)
    robot.SetToolPoint(4)
    robot.MoveJ(joint_pos=p5Joint, tool=0, user=0, vel=100)
    robot.SetToolPoint(5)
    robot.MoveJ(joint_pos=p6Joint, tool=0, user=0, vel=100)
    robot.SetToolPoint(6)
    rtn, coordRtn = robot.ComputeTool()
    print(f"6 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolList(1, coordRtn, 0, 0, 0)
    robot.MoveJ(joint_pos=p1Joint, tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint, tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint, tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint, tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(4)
    rtn, coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0)
    rtn, getCoord = robot.GetTCPOffset(0)
    print(f"GetTCPOffset    {rtn}  coord is {getCoord[0]} {getCoord[1]} {getCoord[2]} {getCoord[3]} {getCoord[4]} {getCoord[5]}")
    robot.CloseRPC()

Externen Werkzeug-Referenzpunkt einstellen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExTCPPoint(point_num)``"
    "Beschreibung", "Legt den externen Werkzeug-Referenzpunkt fest - Drei-Punkt-Methode"
    "Erforderliche Parameter", "- ``point_num``: Punktnummer, Bereich [1~3]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Externes Werkzeugkoordinatensystem berechnen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeExTCF()``"
    "Beschreibung", "Berechnet das externe Werkzeugkoordinatensystem - Drei-Punkt-Methode (nach dem Setzen aller drei Referenzpunkte)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``etcp=[x,y,z,rx,ry,rz]``: Externes Werkzeugkoordinatensystem"

Externes Werkzeugkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExToolCoord(id, etcp, etool)``"
    "Beschreibung", "Stellt das externe Werkzeugkoordinatensystem ein"
    "Erforderliche Parameter", "- ``id``: Koordinatensystem-Nummer, 20-39 entsprechen den externen Werkzeugkoordinatensystemen 0-19
    - ``etcp``: [x,y,z,rx,ry,rz] Externes Werkzeugkoordinatensystem, Einheit [mm][°]
    - ``etool``: [x,y,z,rx,ry,rz] Endeffektor-Werkzeugkoordinatensystem, Einheit [mm][°]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Liste der externen Werkzeugkoordinatensysteme einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExToolList(id, etcp, etool)``"
    "Beschreibung", "Stellt die Liste der externen Werkzeugkoordinatensysteme ein"
    "Erforderliche Parameter", "- ``id``: Koordinatensystem-Nummer, 20-39 entsprechen den externen Werkzeugkoordinatensystemen 0-19
    - ``etcp``: Externes Werkzeugkoordinatensystem, Einheit [mm][°]
    - ``etool``: Endeffektor-Werkzeugkoordinatensystem, Einheit [mm][°]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Operationen mit externen Roboter-Werkzeugkoordinatensystemen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    robot = Robot.RPC('192.168.58.2')

    def TestExtCoord(self):
        p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
        p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]

        p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
        p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]

        p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
        p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]

        exaxisPos = [0, 0, 0, 0]
        offdese = [0, 0, 0, 0, 0, 0]

        posTCP = [p1Desc, p2Desc, p3Desc]
        # coordRtn = DescPose()

        robot.MoveJ(joint_pos=p1Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(1)
        robot.MoveJ(joint_pos=p2Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(2)
        robot.MoveJ(joint_pos=p3Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(3)
        rtn,coordRtn = robot.ComputeExTCF()
        print(f"ComputeExTCF {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")

        robot.SetExToolCoord(21, coordRtn, offdese)
        robot.SetExToolList(21, coordRtn, offdese)

        robot.CloseRPC()
    TestExtCoord(robot)

Werkstück-Referenzpunkt einstellen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWObjCoordPoint(point_num)``"
    "Beschreibung", "Legt den Werkstück-Referenzpunkt fest - Drei-Punkt-Methode"
    "Erforderliche Parameter", "- ``point_num``: Punktnummer, Bereich [1~3]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Werkstückkoordinatensystem berechnen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeWObjCoord(method, refFrame)``"
    "Beschreibung", "Berechnet das Werkstückkoordinatensystem - Drei-Punkt-Methode (nach dem Setzen aller drei Referenzpunkte)"
    "Erforderliche Parameter", "- ``method``: Berechnungsmethode 0: Ursprung - X-Achse - Z-Achse, 1: Ursprung - X-Achse - XY-Ebene
    - ``refFrame``: Referenzkoordinatensystem"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``wobj_pose=[x,y,z,rx,ry,rz]``: Werkstückkoordinatensystem"

Werkstückkoordinatensystem einstellen
+++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWObjCoord(id, coord, refFrame)``"
    "Beschreibung", "Stellt das Werkstückkoordinatensystem ein"
    "Erforderliche Parameter", "- ``id``: Koordinatensystem-Nummer, Bereich [0~14]
    - ``coord``: Pose des Werkstückkoordinatensystems relativ zur Flanschmitte, Einheit [mm][°]
    - ``refFrame``: Referenzkoordinatensystem"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Liste der Werkstückkoordinatensysteme einstellen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWObjList(id, coord, refFrame)``"
    "Beschreibung", "Stellt die Liste der Werkstückkoordinatensysteme ein"
    "Erforderliche Parameter", "- ``id``: Koordinatensystem-Nummer, Bereich [0~14]
    - ``coord``: Pose des Werkstückkoordinatensystems relativ zur Flanschmitte, Einheit [mm][°]
    - ``refFrame``: Referenzkoordinatensystem"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Werkstückkoordinatensystem basierend auf Punkten berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeWObjCoordWithPoints(method, pos, refFrame)``"
    "Beschreibung", "Berechnet das Werkstückkoordinatensystem basierend auf Punkten"
    "Erforderliche Parameter", "- ``method``: Berechnungsmethode; 0: Ursprung - X-Achse - Z-Achse, 1: Ursprung - X-Achse - XY-Ebene
    - ``pos``: Array von drei TCP-Positionen
    - ``refFrame``: Referenzkoordinatensystem"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``wobj_offset=[x,y,z,rx,ry,rz]``: Berechnetes Werkstückkoordinatensystem, Einheit [mm][°]"

Aktuelles Werkstückkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWObjOffset(flag=1)``"
    "Beschreibung", "Gibt das aktuelle Werkstückkoordinatensystem zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "- ``flag``: 0-blockierend, 1-nicht blockierend, Standard 1"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``wobj_offset=[x,y,z,rx,ry,rz]``: Relative Pose des aktuellen Werkstückkoordinatensystems, Einheit [mm][°]"

Codebeispiel für Operationen mit Roboter-Werkstückkoordinatensystemen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
    p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
    p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]
    p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posTCP = [p1Desc, p2Desc, p3Desc]
    rtn, coordRtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0)
    print(f"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint, tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(1)
    robot.MoveJ(joint_pos=p2Joint, tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(2)
    robot.MoveJ(joint_pos=p3Joint, tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(3)
    rtn, coordRtn = robot.ComputeWObjCoord(1, 0)
    print(f"ComputeWObjCoord   {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetWObjCoord(1, coordRtn, 0)
    robot.SetWObjList(1, coordRtn, 0)
    rtn, getWobjDesc = robot.GetWObjOffset(0)
    print(f"GetWObjOffset    {rtn}  coord is {getWobjDesc[0]} {getWobjDesc[1]} {getWobjDesc[2]} {getWobjDesc[3]} {getWobjDesc[4]} {getWobjDesc[5]}")
    robot.CloseRPC()

Globale Geschwindigkeit einstellen
++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSpeed(vel)``"
    "Beschreibung", "Stellt die globale Geschwindigkeit ein"
    "Erforderliche Parameter", "- ``vel``: Geschwindigkeitsprozentsatz, Bereich [0~100]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Roboter-Beschleunigung einstellen
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOaccScale(acc)``"
    "Beschreibung", "Stellt die Roboter-Beschleunigung ein"
    "Erforderliche Parameter", "- ``acc``: Roboter-Beschleunigungsprozentsatz"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Standardgeschwindigkeit abrufen
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDefaultTransVel()``"
    "Beschreibung", "Gibt die Standardgeschwindigkeit zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``vel``: Standardgeschwindigkeit, Einheit [mm/s]"

Endnutzlastgewicht einstellen
+++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLoadWeight(loadNum, weight)``"
    "Beschreibung", "Stellt das Endnutzlastgewicht ein. Eine falsche Einstellung kann zu unkontrolliertem Roboter im Ziehemodus führen."
    "Erforderliche Parameter", "- ``loadNum``: Nutzlastnummer
    - ``weight``: Einheit [kg]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Endnutzlast-Schwerpunktkoordinaten einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLoadCoord(x, y, z, loadNum=0)``"
    "Beschreibung", "Stellt die Endnutzlast-Schwerpunktkoordinaten ein. Eine falsche Einstellung kann zu unkontrolliertem Roboter im Ziehemodus führen."
    "Erforderliche Parameter", "- ``x``: Schwerpunktkoordinate, Einheit [mm]
    - ``y``: Schwerpunktkoordinate, Einheit [mm]
    - ``z``: Schwerpunktkoordinate, Einheit [mm]"
    "Optionale Parameter", "- ``loadNum``: Nutzlastnummer, Standard 0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Aktuelles Nutzlastgewicht abrufen
++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetPayload(flag=1)``"
    "Beschreibung", "Gibt das Gewicht der aktuellen Nutzlast zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "- ``flag``: 0-blockierend, 1-nicht blockierend, Standard 1"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``weight``: Aktuelles Nutzlastgewicht, Einheit [kg]"

Aktuellen Nutzlast-Schwerpunkt abrufen
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetPayloadCog(flag=1)``"
    "Beschreibung", "Gibt den Schwerpunkt der aktuellen Nutzlast zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "- ``flag``: 0-blockierend, 1-nicht blockierend, Standard 1"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``cog=[x,y,z]``: Aktuelle Schwerpunktkoordinaten, Einheit [mm]"

Roboter-Installationsart einstellen (feste Installation)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotInstallPos(method)``"
    "Beschreibung", "Stellt die Installationsart des Roboters ein (feste Installation). Eine falsche Einstellung kann zu unkontrolliertem Roboter im Ziehemodus führen."
    "Erforderliche Parameter", "- ``method``: 0-normal, 1-Seitenmontage, 2-Überkopfmontage"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Roboter-Installationswinkel einstellen (freie Installation)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotInstallAngle(yangle, zangle)``"
    "Beschreibung", "Stellt die Installationswinkel des Roboters ein (freie Installation). Eine falsche Einstellung kann zu unkontrolliertem Roboter im Ziehemodus führen."
    "Erforderliche Parameter", "- ``yangle``: Neigungswinkel
    - ``zangle``: Rotationswinkel"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Roboter-Installationswinkel abrufen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotInstallAngle()``"
    "Beschreibung", "Gibt die Installationswinkel des Roboters zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``[yangle, zangle]``: yangle-Neigungswinkel, zangle-Rotationswinkel"

Systemvariablenwert setzen
+++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSysVarValue(id, value)``"
    "Beschreibung", "Setzt den Wert einer Systemvariablen"
    "Erforderliche Parameter", "- ``id``: Variablen-Nummer, Bereich [1~20]
    - ``value``: Variablenwert"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Systemvariablenwert abrufen
++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSysVarValue(id)``"
    "Beschreibung", "Gibt den Wert einer Systemvariablen zurück"
    "Erforderliche Parameter", "- ``id``: Systemvariablen-Nummer, Bereich [1~20]"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``var_value``: Systemvariablenwert"

Codebeispiel für allgemeine Roboter-Einstellungen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    for i in range(1, 100):
        robot.SetSpeed(i)
        robot.SetOaccScale(i)
        time.sleep(0.03)
    error,defaultVel = robot.GetDefaultTransVel()
    print(f"GetDefaultTransVel is {defaultVel}")
    for i in range(1, 21):
        robot.SetSysVarValue(i, i + 0.5)
        time.sleep(0.1)
    for i in range(1, 21):
        value = robot.GetSysVarValue(i)
        print(f"sys value {i} is: {value}")
        time.sleep(0.1)
    robot.SetLoadWeight(0, 2.5)
    robot.SetLoadCoord(3.0,4.0,5.0)
    time.sleep(1)
    error,getLoad = robot.GetTargetPayload(0)
    error,getLoadTran = robot.GetTargetPayloadCog(0)
    print(f"get load is {getLoad}; get load cog is {getLoadTran[0]} {getLoadTran[1]} {getLoadTran[2]}")
    robot.SetRobotInstallPos(0)
    robot.SetRobotInstallAngle(15.0, 25.0)
    error,[anglex, angley] = robot.GetRobotInstallAngle()
    print(f"GetRobotInstallAngle x: {anglex}; y: {angley}")
    robot.CloseRPC()

Schalter für Gelenk-Reibungskompensation
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FrictionCompensationOnOff(state)``"
    "Beschreibung", "Schaltet die Gelenk-Reibungskompensation ein oder aus"
    "Erforderliche Parameter", "- ``state``: 0-aus, 1-ein"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Koeffizienten für Gelenk-Reibungskompensation einstellen - Normalmontage
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_level(coeff)``"
    "Beschreibung", "Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - feste Installation, Normalmontage"
    "Erforderliche Parameter", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Kompensationskoeffizienten für sechs Gelenke"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Koeffizienten für Gelenk-Reibungskompensation einstellen - Seitenmontage
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_wall(coeff)``"
    "Beschreibung", "Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - feste Installation, Seitenmontage"
    "Erforderliche Parameter", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Kompensationskoeffizienten für sechs Gelenke"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Koeffizienten für Gelenk-Reibungskompensation einstellen - Überkopfmontage
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_ceiling(coeff)``"
    "Beschreibung", "Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - feste Installation, Überkopfmontage"
    "Erforderliche Parameter", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Kompensationskoeffizienten für sechs Gelenke"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Koeffizienten für Gelenk-Reibungskompensation einstellen - freie Installation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_freedom(coeff)``"
    "Beschreibung", "Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - freie Installation"
    "Erforderliche Parameter", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Kompensationskoeffizienten für sechs Gelenke"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Gelenk-Reibungskompensation
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    lcoeff = [0.9, 0.9, 0.9, 0.9, 0.9, 0.9]
    wcoeff = [0.4, 0.4, 0.4, 0.4, 0.4, 0.4]
    ccoeff = [0.6, 0.6, 0.6, 0.6, 0.6, 0.6]
    fcoeff = [0.5, 0.5, 0.5, 0.5, 0.5, 0.5]
    rtn = robot.FrictionCompensationOnOff(1)
    print(f"FrictionCompensationOnOff rtn is {rtn}")
    rtn = robot.SetFrictionValue_level(lcoeff)
    print(f"SetFrictionValue_level rtn is {rtn}")
    rtn = robot.SetFrictionValue_wall(wcoeff)
    print(f"SetFrictionValue_wall rtn is {rtn}")
    rtn = robot.SetFrictionValue_ceiling(ccoeff)
    print(f"SetFrictionValue_ceiling rtn is {rtn}")
    rtn = robot.SetFrictionValue_freedom(fcoeff)
    print(f"SetFrictionValue_freedom rtn is {rtn}")
    robot.CloseRPC()

Roboter-Fehlercode abfragen
++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotErrorCode()``"
    "Beschreibung", "Fragt den Roboter-Fehlercode ab"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``[maincode, subcode]``: Roboter-Fehlercode, maincode-Hauptfehlercode, subcode-Unterfehlercode"

Fehlerzustand löschen
++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ResetAllError()``"
    "Beschreibung", "Löscht den Fehlerzustand (nur zurücksetzbare Fehler)"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Fehlerstatusabfrage und -löschung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    robot.MoveJ(joint_pos=p1Joint, tool=5, user=2, vel=50)
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    time.sleep(1)
    robot.ResetAllError()
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    robot.CloseRPC()

Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWideBoxTempFanMonitorParam(enable, period)``"
    "Beschreibung", "Stellt die Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks ein"
    "Erforderliche Parameter", "
    - ``enable``: 0-Überwachung deaktivieren; 1-Überwachung aktivieren
    - ``period``: Überwachungsperiode (s), Bereich 1-100"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWideBoxTempFanMonitorParam()``"
    "Beschreibung", "Gibt die Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``enable``: 0-Überwachung deaktiviert; 1-Überwachung aktiviert
    - ``period``: Überwachungsperiode (s)"

Codebeispiel für das Abrufen von Temperatur und Lüfterstrom des Weitbereichs-Steuerschranks
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    robot.SetWideBoxTempFanMonitorParam(1, 2)
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    rtn = robot.SetWideBoxTempFanMonitorParam(0, 2)
    print(f"SetWideBoxTempFanMonitorParam rtn is:{rtn}")
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    robot.CloseRPC()

Fokus-Kalibrierpunkt setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFocusCalibPoint(pointNum, point)``"
    "Beschreibung", "Setzt einen Fokus-Kalibrierpunkt"
    "Erforderliche Parameter", "- ``pointNum``: Fokus-Kalibrierpunktnummer 1-8
    - ``point``: Koordinaten des Kalibrierpunkts"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Fokus-Kalibrierungsergebnis berechnen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeFocusCalib(pointNum)``"
    "Beschreibung", "Berechnet das Ergebnis der Fokus-Kalibrierung"
    "Erforderliche Parameter", "- ``pointNum``: Anzahl der Kalibrierpunkte"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``resultPos``: Kalibrierungsergebnis XYZ
    - ``accuracy``: Kalibriergenauigkeitsfehler"

Fokus-Verfolgung starten
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FocusStart(kp=50.0, kpredic=19.0, aMax=1440, vMax=180, type=0)``"
    "Beschreibung", "Startet die Fokus-Verfolgung"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "- ``kp``: Proportionalparameter, Standard 50.0
    - ``kpredic``: Vorsteuerungsparameter, Standard 19.0
    - ``aMax``: Maximale Winkelbeschleunigungsbegrenzung, Standard 1440°/s^2
    - ``vMax``: Maximale Winkelgeschwindigkeitsbegrenzung, Standard 180°/s
    - ``type``: Sperren der X-Achsen-Ausrichtung (0-Referenz-Eingabevektor; 1-horizontal; 2-vertikal), Standard 0"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Fokus-Verfolgung stoppen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FocusEnd()``"
    "Beschreibung", "Stoppt die Fokus-Verfolgung"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Fokus-Koordinaten setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFocusPosition(pos)``"
    "Beschreibung", "Setzt die Fokus-Koordinaten"
    "Erforderliche Parameter", "- ``pos``: Fokus-Koordinaten XYZ"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Fokus-Verfolgung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 100, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1, offset_flag=0, offset_pos=offdese)
    robot.SetTcp4RefPoint(4)
    rtn,coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool {rtn} coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} "
          f"{coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0)
    error, p1Desc = robot.GetForwardKin(p1Joint)
    error, p2Desc = robot.GetForwardKin(p2Joint)
    error, p3Desc = robot.GetForwardKin(p3Joint)
    robot.SetFocusCalibPoint(1, p1Desc)
    robot.SetFocusCalibPoint(2, p2Desc)
    robot.SetFocusCalibPoint(3, p3Desc)
    rtn, resultPos, accuracy = robot.ComputeFocusCalib(pointNum=3)
    print(f"ComputeFocusCalib coord is {rtn} {resultPos[0]} {resultPos[1]} {resultPos[2]} accuracy is {accuracy}")
    rtn = robot.SetFocusPosition(resultPos)
    error, p5Desc = robot.GetForwardKin(p5Joint)
    error, p6Desc = robot.GetForwardKin(p6Joint)
    robot.MoveL(desc_pos=p5Desc, tool=1, user=0, vel=10, acc=100, ovl=100, blendR=-1, blendMode=0, exaxis_pos=exaxisPos, search=0, offset_flag=1, offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc, tool=1, user=0, vel=10, acc=100, ovl=100, blendR=-1, blendMode=0, exaxis_pos=exaxisPos, search=0, offset_flag=1, offset_pos=offdese)
    robot.FocusStart(50, 19, 710, 90, 0)
    robot.MoveL(desc_pos=p5Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.FocusEnd()
    robot.CloseRPC()

Aktivierung der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityEnable(status)``"
    "Beschreibung", "Aktiviert die Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung"
    "Erforderliche Parameter", "- ``status``: 0-deaktivieren; 1-aktivieren"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Datenerfassung für Gelenk-Drehmomentsensor-Empfindlichkeit
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityCollect()``"
    "Beschreibung", "Erfasst Daten für die Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityCalibration()``"
    "Beschreibung", "Gibt das Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``calibResult``: J1~J6 Gelenkempfindlichkeit [0-1]
    - ``linearity``: J1~J6 Gelenklinearität [0-1]"

Gelenk-Drehmomentsensor-Hysteresefehler abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointHysteresisError()``"
    "Beschreibung", "Gibt den Hysteresefehler des Gelenk-Drehmomentsensors zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``hysteresisError``: J1~J6 Hysteresefehler"

Gelenk-Drehmomentsensor-Wiederholgenauigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointRepeatability()``"
    "Beschreibung", "Gibt die Wiederholgenauigkeit des Gelenk-Drehmomentsensors zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``repeatability``: J1~J6 Wiederholgenauigkeit"

Gelenk-Kraftsensor-Parameter einstellen
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAdmittanceParams(M, B, K, threshold, sensitivity, setZeroFlag)``"
    "Beschreibung", "Stellt die Gelenk-Kraftsensor-Parameter ein"
    "Erforderliche Parameter", "
    - ``M``: J1-J6 Massenkoeffizient [0.001 ~ 10]
    - ``B``: J1-J6 Dämpfungskoeffizient [0.001 ~ 10]
    - ``K``: J1-J6 Steifigkeitskoeffizient [0.001 ~ 10]
    - ``threshold``: Kraftregelungsschwelle, Nm
    - ``sensitivity``: Empfindlichkeit, Nm/V, [0 ~ 10]
    - ``setZeroFlag``: Funktionsaktivierungs-Flag; 0-deaktivieren; 1-aktivieren; 2-Position 1 Nullpunkt aufzeichnen; 3-Position 2 Nullpunkt aufzeichnen"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für automatische Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.JointSensitivityEnable(0)
    rtn = robot.JointSensitivityEnable(1)
    print(f"JointSensitivityEnable rtn is {rtn}")
    curJPos = [0.0] * 6
    rtn, curJPos = robot.GetActualJointPosDegree(0)
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    jointPos1 = [curJPos[0], 0.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos1 = [0.0] * 6
    rtn, descPos1 = robot.GetForwardKin(jointPos1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 1 rtn is {rtn}")
    time.sleep(0.1)
    jointPos2 = [curJPos[0], -30.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos2 = [0.0] * 6
    rtn, descPos2 = robot.GetForwardKin(jointPos2)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 2 rtn is {rtn}")
    time.sleep(0.1)
    jointPos3 = [curJPos[0], -60.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos3 = [0.0] * 6
    rtn, descPos3 = robot.GetForwardKin(jointPos3)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 3 rtn is {rtn}")
    time.sleep(0.1)
    jointPos4 = [curJPos[0], -90.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos4 = [0.0] * 6
    rtn, descPos4 = robot.GetForwardKin(jointPos4)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 4 rtn is {rtn}")
    time.sleep(0.1)
    jointPos5 = [curJPos[0], -120.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos5 = [0.0] * 6
    rtn, descPos5 = robot.GetForwardKin(jointPos5)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 5 rtn is {rtn}")
    time.sleep(0.1)
    jointPos6 = [curJPos[0], -150.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos6 = [0.0] * 6
    rtn, descPos6 = robot.GetForwardKin(jointPos6)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 6 rtn is {rtn}")
    time.sleep(0.1)
    jointPos7 = [curJPos[0], -180.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos7 = [0.0] * 6
    rtn, descPos7 = robot.GetForwardKin(jointPos7)
    robot.MoveJ(joint_pos=jointPos7, desc_pos=descPos7, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 7 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 8 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 9 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 10 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 11 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 12 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 13 rtn is {rtn}")
    time.sleep(0.1)
    calibResult = [0.0] * 6
    linearity = [0.0] * 6
    rtn,calibResult, linearity = robot.JointSensitivityCalibration()
    print(f"JointSensitivityCalibration rtn is {rtn}")
    rtn = robot.JointSensitivityEnable(0)
    print(f"JointSensitivityEnable rtn is {rtn}")
    print(f"jointSensor Calib result is {calibResult[0]},{calibResult[1]},{calibResult[2]},{calibResult[3]},{calibResult[4]},{calibResult[5]}")
    print( f"jointSensor linearity is {linearity[0]},{linearity[1]},{linearity[2]},{linearity[3]},{linearity[4]},{linearity[5]}")
    hysteresisError = [0.0] * 6
    rtn,hysteresisError = robot.JointHysteresisError()
    print(f"JointHysteresisError result is {hysteresisError[0]},{hysteresisError[1]},{hysteresisError[2]},{hysteresisError[3]},{hysteresisError[4]},{hysteresisError[5]}")
    repeatability = [0.0] * 6
    rtn, repeatability = robot.JointRepeatability()
    print(f"JointRepeatability result is {repeatability[0]},{repeatability[1]},{repeatability[2]},{repeatability[3]},{repeatability[4]},{repeatability[5]}")
    M = [1.0] * 6
    B = [1.0] * 6
    K = [0.0] * 6
    threshold = [1.0] * 6
    setZeroFlag = 1
    rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag)
    print(f"SetAdmittanceParams rtn is {rtn}")
    robot.CloseRPC()

Fehlerzähler der 8 Slave-Ports des Roboters abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSlavePortErrCounter()``"
    "Beschreibung", "Gibt die Fehlerzähler der 8 Slave-Ports des Roboters zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``inRecvErr``: Eingang Empfangsfehlerzähler
    - ``inCRCErr``: Eingang CRC-Fehlerzähler
    - ``inTransmitErr``: Eingang Übertragungsfehlerzähler
    - ``inLinkErr``: Eingang Verbindungsfehlerzähler
    - ``outRecvErr``: Ausgang Empfangsfehlerzähler
    - ``outCRCErr``: Ausgang CRC-Fehlerzähler
    - ``outTransmitErr``: Ausgang Übertragungsfehlerzähler
    - ``outLinkErr``: Ausgang Verbindungsfehlerzähler"

Slave-Port-Fehlerzähler zurücksetzen
++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityEnable(slaveID)``"
    "Beschreibung", "Setzt den Fehlerzähler eines Slave-Ports zurück"
    "Erforderliche Parameter", "- ``slaveID``: Slave-Nummer 0~7"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Codebeispiel für Slave-Port-Fehlerzähler
++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    inRecvErr = [0] * 8
    inCRCErr = [0] * 8
    inTransmitErr = [0] * 8
    inLinkErr = [0] * 8
    outRecvErr = [0] * 8
    outCRCErr = [0] * 8
    outTransmitErr = [0] * 8
    outLinkErr = [0] * 8
    rtn,inRecvErr, inCRCErr, inTransmitErr, inLinkErr, outRecvErr, outCRCErr, outTransmitErr, outLinkErr = robot.GetSlavePortErrCounter()
    for i in range(8):
        if inRecvErr[i] != 0:
            print(f"inRecvErr {i} is {inRecvErr[i]}")
        if inCRCErr[i] != 0:
            print(f"inCRCErr {i} is {inCRCErr[i]}")
        if inTransmitErr[i] != 0:
            print(f"inTransmitErr {i} is {inTransmitErr[i]}")
        if inLinkErr[i] != 0:
            print(f"inLinkErr {i} is {inLinkErr[i]}")
        if outRecvErr[i] != 0:
            print(f"outRecvErr {i} is {outRecvErr[i]}")
        if outCRCErr[i] != 0:
            print(f"outCRCErr {i} is {outCRCErr[i]}")
        if outTransmitErr[i] != 0:
            print(f"outTransmitErr {i} is {outTransmitErr[i]}")
        if outLinkErr[i] != 0:
            print(f"outLinkErr {i} is {outLinkErr[i]}")
    print("others has no err!")
    for i in range(8):
        robot.SlavePortErrCounterClear(i)
    robot.CloseRPC()

Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetVelFeedForwardRatio(radio)``"
    "Beschreibung", "Stellt die Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse ein"
    "Erforderliche Parameter", "- ``radio``: Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetVelFeedForwardRatio()``"
    "Beschreibung", "Gibt die Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse zurück"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - ``radio``: Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse"

Codebeispiel für Roboter-Geschwindigkeits-Vorsteuerung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zum Robotercontroller herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    setRadio = [1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
    robot.SetVelFeedForwardRatio(setRadio)
    getRadio = [0.0] * 6
    rtn,getRadio = robot.GetVelFeedForwardRatio()
    print(f"{getRadio[0]},{getRadio[1]},{getRadio[2]},{getRadio[3]},{getRadio[4]},{getRadio[5]}")
    robot.CloseRPC()

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPComputeRPY(Btool, Etool, sensor, radius, dz)``"
    "Beschreibung", "Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen"
    "Erforderliche Parameter", "- ``Btool``: Roboter-kartesische Position
    - ``Etool``: Aktueller Werkzeugkoordinatenwert
    - ``sensor``: Aktueller Sensorkoordinatenwert (noch nicht freigegeben)
    - ``radius``: Radius der Kreisbewegung (mm) (noch nicht freigegeben)
    - ``dz``: Bewegungsabstand entlang der negativen Z-Achse des Basiskoordinatensystems; wenn dz = 10000, gibt die Funktion direkt das Werkzeug-RPY zurück"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPComputeXYZ(select, originDirection, pos1, pos2, pos3, pos4)``"
    "Beschreibung", "Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen"
    "Erforderliche Parameter", "- ``select``: 0-Werkzeug-TCP berechnen; 1-Sensorursprung berechnen; 2-Sensorausrichtung berechnen; 3-Werkzeug-TCP direkt zurückgeben; 4-Aktuelles Werkstück- und Werkzeugkoordinatensystem aufzeichnen
    - ``originDirection``: 0-X-Richtung; 1-Y-Richtung; 2-Z-Richtung
    - ``pos1``: Roboter-kartesische Position 1
    - ``pos2``: Roboter-kartesische Position 2
    - ``pos3``: Roboter-kartesische Position 3
    - ``pos4``: Roboter-kartesische Position 4"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "
    - Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - TCP: Werkzeug-XYZ-Wert (bei erfolgreichem Aufruf)"

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition starten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPRecordFlangePosStart()``"
    "Beschreibung", "Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition starten"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPRecordFlangePosEnd()``"
    "Beschreibung", "Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition stoppen"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode"

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeugmittelpunktposition abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPGetRecordFlangePos()``"
    "Beschreibung", "Photoelektrischer Sensor TCP-Kalibrierung - Werkzeugmittelpunktposition abrufen"
    "Erforderliche Parameter", "Keine"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "
    - Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - TCP: Werkzeugmittelpunktposition (x, y, z) (bei erfolgreichem Aufruf)"

Photoelektrischer Sensor TCP-Kalibrierung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PhotoelectricSensorTCPCalibration(self, luaFile, offsetX)``"
    "Beschreibung", "Photoelektrischer Sensor TCP-Kalibrierung"
    "Erforderliche Parameter", "
    - ``luaFile``: Pfad zum automatischen Kalibrierungs-Lua-Programm: - 'FR_CalibrateTheToolTcp.lua';
    - ``offsetX``: Teachpunktversatz (x, y, z) mm"
    "Optionale Parameter", "Keine"
    "Rückgabewerte", "- Fehlercode: 0 bei Erfolg, sonst Fehlercode
    - TCP: Werkzeug-XYZ-Wert (bei erfolgreichem Aufruf)"

Codebeispiel für Photoelektrische Sensor TCP-Kalibrierung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    offset = [10.0, 10.0, 3.0]
    TCP = [0.0] * 6
    rtn, TCP = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset)
    print(f"PhotoelectricSensorTCPCalibration rtn is {rtn},{TCP[0]},{TCP[1]},{TCP[2]},{TCP[3]},{TCP[4]},{TCP[5]}")
    robot.CloseRPC()
    return 0

Echtzeit-Geschwindigkeitseinstellung (Befehlsframe, niedrige Latenz)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSpeedInstant(self, vel)``"
    "Beschreibung", "Echtzeit-Geschwindigkeitseinstellung (Befehlsframe, niedrige Latenz)"
    "Erforderliche Parameter", "
    - ``vel``: Geschwindigkeitsprozent, Bereich [0~100]"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode, 0-Erfolg; ungleich Null-Fehler"

Echtzeit-Pendeloffset einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeaveOffsetRT(self, offset)``"
    "Beschreibung", "Stellt den Echtzeit-Pendeloffset ein"
    "Erforderliche Parameter", "
    - ``offset``: Echtzeit-Offset [x,y,z,rx,ry,rz], Einheit [mm, °]"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode, 0-Erfolg; ungleich Null-Fehler"

Codebeispiel für Pendelgeschwindigkeit und Echtzeit-Offset-Test    
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    import threading


    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        j1 = [5.027, -84.331, -75.139, -103.690, 86.379, 20.794]
        d1 = [324.752, -83.339, 366.314, -172.321, -0.936, -106.047]

        j2 = [-35.335, -117.598, -57.174, -95.234, 90.001, -19.560]
        d2 = [324.999, -355.439, 260.000, 179.995, 0.003, -105.775]

        j3 = [59.787, -117.594, -57.183, -95.222, 90.006, 75.562]
        d3 = [324.998, 355.441, 260.002, 179.995, 0.003, -105.775]

        rtn = 0

        print("\nStep 1: MoveJ to start point")
        rtn = robot.MoveJ(joint_pos=j1, desc_pos=d1, tool=1, user=0, vel=100, acc=100, ovl=50,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        print(f"  MoveJ(j1) rtn={rtn}")
        time.sleep(0.5)

        print("\nStep 2: MoveJ to weave entry point")
        rtn = robot.MoveJ(joint_pos=j2, desc_pos=d2, tool=1, user=0, vel=100, acc=100, ovl=50,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        print(f"  MoveJ(j2) rtn={rtn}")
        time.sleep(0.5)

        print("\nStep 3: WeaveStart + MoveL in background thread")
        robot.WeaveStart(0)

        weave_running = True
        move_rtn = [0]  

        def weave_move_thread():
            rtn_val = robot.MoveL(joint_pos=j3, desc_pos=d3, tool=1, user=0, vel=100, acc=100, ovl=5,
                                blendR=-1, offset_flag=0, exaxis_pos=epos, search=0,
                                offset_pos=offset_pos, config=5, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
            print(f"  MoveL(weave) thread finished, rtn={rtn_val}")
            move_rtn[0] = rtn_val
            nonlocal weave_running
            weave_running = False

        weave_thread = threading.Thread(target=weave_move_thread)
        weave_thread.daemon = True
        weave_thread.start()
        time.sleep(0.5)  

        print("\nStep 4: SetSpeed test during weaving")
        speed_values = [20, 50, 80, 30, 60, 10]
        for speed in speed_values:
            if not weave_running:
                break
            rtn = robot.SetSpeedInstant(speed)
            print(f"  SetSpeed({speed}) -> rtn={rtn}")
            # rtn, pkg = robot.GetRobotRealTimeState()
            # print(f"target_TCP_CmpSpeed: [{', '.join([f'{x:.3f}' for x in pkg.target_TCP_CmpSpeed])}]")
            time.sleep(5)

        time.sleep(5)

        print("\nStep 5: SetWeaveOffsetRT test (50 iterations, delta=0.1)")
        accum_offset = 0.0
        for i in range(50):
            if not weave_running:
                break
            accum_offset += 1
            weave_offset = [0.0, 0.0, accum_offset, 0.0, 0.0, 0.0]
            rtn = robot.SetWeaveOffsetRT(weave_offset)
            rtn, pkg = robot.GetRobotRealTimeState()
            print(f"  [{i+1}/50] SetWeaveOffsetRT(x={accum_offset:.1f}) -> rtn={rtn}, "
                f"TCP_pos=({pkg.tl_cur_pos[0]:.2f},{pkg.tl_cur_pos[1]:.2f},{pkg.tl_cur_pos[2]:.2f})")
            time.sleep(0.1)

        print("\nStep 6: Wait for weave MoveL, then WeaveEnd")
        weave_thread.join()
        robot.WeaveEnd(0)
        time.sleep(0.5)

        print("\nStep 7: MoveL back to start")
        rtn = robot.MoveL(joint_pos=j1, desc_pos=d1, tool=1, user=0, vel=100, acc=100, ovl=50,
                        blendR=-1, offset_flag=0, exaxis_pos=epos, search=0,
                        offset_pos=offset_pos, config=50, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
        print(f"  MoveL(back) rtn={rtn}")

        rtn, pkg = robot.GetRobotRealTimeState()
        print(f"\n  Final robot state: main_code={pkg.main_code}, sub_code={pkg.sub_code}")
        
        robot.CloseRPC()


    if __name__ == "__main__":
        main()    