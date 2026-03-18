Roboter-Grundlagen
==================

.. toctree::
    :maxdepth: 5

Roboter instanziieren
+++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RPC(ip)``"
    "Beschreibung", "Instanziiert ein Roboterobjekt"
    "Erforderliche Parameter", "- ``ip``: IP-Adresse des Roboters, Standard-IP ab Werk ist 192.168.58.2"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Erfolg: Gibt ein Roboterobjekt zurück
    - Fehlschlag: Das erstellte Objekt wird zerstört"

RPC-Verbindung schließen
++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CloseRPC()``"
    "Beschreibung", "Schließt die RPC-Verbindung"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Kein Rückgabewert"

SDK-Version abfragen
++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSDKVersion()``"
    "Beschreibung", "Fragt die SDK-Version ab"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``sdk``: SDK-Versionsnummer, Controller-Versionsnummer"

Controller-IP abrufen
+++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetControllerIP()``"
    "Beschreibung", "Fragt die Controller-IP ab"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``ip``: Controller-IP"

Roboter in den oder aus dem Drag&Teach-Modus schalten
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``DragTeachSwitch(state)``"
    "Beschreibung", "Schaltet den Roboter in den oder aus dem Drag&Teach-Modus"
    "Erforderliche Parameter", "- ``state``: 1 = Drag&Teach-Modus betreten, 0 = Drag&Teach-Modus verlassen"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Abfragen, ob sich der Roboter im Drag-Modus befindet
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``IsInDragTeach()``"
    "Beschreibung", "Fragt ab, ob sich der Roboter im Drag&Teach-Modus befindet"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``state``: 0 = nicht im Drag&Teach-Modus, 1 = im Drag&Teach-Modus"

Roboter aktivieren (Enable) oder deaktivieren (Disable)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RobotEnable(state)``"
    "Beschreibung", "Aktiviert (Enable) oder deaktiviert (Disable) den Roboter"
    "Erforderliche Parameter", "- ``state``: 1 = aktivieren, 0 = deaktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"


Umschalten zwischen Hand- und Automatikmodus
++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``Mode(state)``"
    "Beschreibung", "Schaltet zwischen Hand- und Automatikmodus des Roboters um"
    "Erforderliche Parameter", "- ``state``: 0 = Automatikmodus, 1 = Handmodus"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Roboter-Betriebssystem herunterfahren
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ShutDownRobotOS()``"
    "Beschreibung", "Fährt das Roboter-Betriebssystem herunter"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Logging-Parameter initialisieren
++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoggerInit(output_model=1, file_path="", file_num=5)``"
    "Beschreibung", "Initialisiert die Logging-Parameter"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``output_model``: Ausgabemodus, 0 = direkte Ausgabe, 1 = gepufferte Ausgabe, 2 = asynchrone Ausgabe, Standard = 1
    - ``file_path``: Pfad und Name der Logdatei, Name muss die Form xxx.log haben, z.B. /home/fr/linux/fairino.log. Standardmäßig wird die Datei im Ausführungsverzeichnis mit dem Namen fairino_Jahr_Monat_Tag.log erstellt (z.B. fairino_2024_03_13.log).
    - ``file_num``: Anzahl der rollierenden Logdateien, 1~20, Standard = 5. Einzeldateigröße max. 50 MB."
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Logging-Filterstufe einstellen
+++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLoggerLevel(lvl=1)``"
    "Beschreibung", "Stellt die Logging-Filterstufe ein"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "- ``lvl``: Filterstufe. Je kleiner der Wert, desto weniger Logs werden ausgegeben. 1 = error, 2 = warning, 3 = info, 4 = debug. Standard = 1"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für grundlegende Robotersteuerung
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    error,version = robot.GetSDKVersion()
    print(f"SDK version: {version}")
    error,ip = robot.GetControllerIP()
    print(f"controller ip: {ip}")
    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(state=1)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.DragTeachSwitch(state=0)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.RobotEnable(0)
    time.sleep(3)
    robot.RobotEnable(1)
    robot.Mode(0)
    time.sleep(1)
    robot.Mode(1)
    robot.CloseRPC()

Softwareversion des Roboters abrufen
++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSoftwareVersion()``"
    "Beschreibung", "Ruft die Softwareversion des Roboters ab"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``robotModel``: Robotermodell
    - ``webVersion``: Web-Version
    - ``controllerVersion``: Controller-Version"

Hardwareversionsinformationen des Roboters abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSlaveHardVersion()``"
    "Beschreibung", "Ruft die Hardwareversionsinformationen des Roboters ab"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``ctrlBoxBoardVersion``: Version der Steuerkastenplatine
    - ``driver1Version``: Version Antrieb 1
    - ``driver2Version``: Version Antrieb 2
    - ``driver3Version``: Version Antrieb 3
    - ``driver4Version``: Version Antrieb 4
    - ``driver5Version``: Version Antrieb 5
    - ``driver6Version``: Version Antrieb 6
    - ``endBoardVersion``: Version der Endeffektorplatine"

Firmwareversionsinformationen des Roboters abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSlaveFirmVersion()``"
    "Beschreibung", "Ruft die Firmwareversionsinformationen des Roboters ab"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``ctrlBoxBoardVersion``: Version der Steuerkasten-Firmware
    - ``driver1Version``: Firmware-Version Antrieb 1
    - ``driver2Version``: Firmware-Version Antrieb 2
    - ``driver3Version``: Firmware-Version Antrieb 3
    - ``driver4Version``: Firmware-Version Antrieb 4
    - ``driver5Version``: Firmware-Version Antrieb 5
    - ``driver6Version``: Firmware-Version Antrieb 6
    - ``endBoardVersion``: Firmware-Version der Endeffektorplatine"

Codebeispiel zum Abrufen der Software- und Firmwareversionen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn,robotModel, webversion, controllerVersion = robot.GetSoftwareVersion()
    print(f"Getsoftwareversion rtn is: {rtn}")
    print(f"robotmodel is: {robotModel}, webversion is: {webversion}, controllerVersion is: {controllerVersion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetHardwareversion()
    print(f"GetHardwareversion rtn is: {rtn}")
    print(f"GetHardwareversion get hardware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetFirmwareVersion()
    print(f"GetFirmwareversion rtn is: {rtn}")
    print(f"GetFirmwareversion get firmware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    robot.CloseRPC()
