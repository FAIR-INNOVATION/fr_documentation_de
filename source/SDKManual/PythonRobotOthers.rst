Weitere Schnittstellen
======================

.. toctree::
    :maxdepth: 5

SSH öffentlichen Schlüssel abrufen
+++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSSHKeygen()``"
    "Beschreibung", "SSH öffentlichen Schlüssel abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``keygen``: Öffentlicher Schlüssel"

SCP-Befehl senden
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSSHScpCmd(mode, sshname, sship, usr_file_url, robot_file_url)``"
    "Beschreibung", "SCP-Befehl senden"
    "Erforderliche Parameter", "- ``mode``: 0 = Hochladen (PC -> Controller), 1 = Herunterladen (Controller -> PC)
    - ``sshname``: Benutzername auf dem PC
    - ``sship``: IP-Adresse des PCs
    - ``usr_file_url``: Dateipfad auf dem PC
    - ``robot_file_url``: Dateipfad auf der Robotersteuerung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

MD5-Wert einer Datei unter einem bestimmten Pfad berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeFileMD5(file_path)``"
    "Beschreibung", "MD5-Wert einer Datei unter einem bestimmten Pfad berechnen"
    "Erforderliche Parameter", "- ``file_path``: Dateipfad inklusive Dateiname. Standard-Traj-Ordnerpfad: /fruser/traj/, z.B. /fruser/traj/trajHelix_aima_1.txt"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``md5``: MD5-Wert der Datei"

Codebeispiel für SSH- und MD5-Befehle des Roboters
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    file_path = "/fruser/airlab.lua"
    md5 = ""
    emerg_state = 0
    si0_state = 0
    si1_state = 0
    sdk_com_state = 0
    ssh_keygen = ""
    retval,ssh_keygen = robot.GetSSHKeygen()
    print(f"GetSSHKeygen retval is: {retval}")
    print(f"ssh key is: {ssh_keygen}")
    ssh_name = "fr"
    ssh_ip = "192.168.58.45"
    ssh_route = "/home/fr"
    ssh_robot_url = "/root/robot/dhpara.config"
    retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url)
    print(f"SetSSHScpCmd retval is: {retval}")
    print(f"robot url is: {ssh_robot_url}")
    error, md5 = robot.ComputeFileMD5(file_path)
    print(f"md5 is: {md5}")
    robot.CloseRPC()

Rückmeldezyklus für den Roboter-Port 20004 einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotRealtimeStateSamplePeriod(period)``"
    "Beschreibung", "Rückmeldezyklus für den Roboter-Port 20004 einstellen"
    "Erforderliche Parameter", "- ``period``: Rückmeldezyklus für Port 20004 (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Rückmeldezyklus für den Roboter-Port 20004 abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotRealtimeStateSamplePeriod()``"
    "Beschreibung", "Rückmeldezyklus für den Roboter-Port 20004 abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``period``: Rückmeldezyklus für Port 20004 (ms)"

Codebeispiel für die Konfiguration des Statusrückmeldezyklus (Port 20004)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    robot.SetRobotRealtimeStateSamplePeriod(10)
    error,getPeriod = robot.GetRobotRealtimeStateSamplePeriod()
    print(f"period is {getPeriod}")
    time.sleep(1)
    robot.CloseRPC()

Roboter-Software-Upgrade
++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SoftwareUpgrade(filePath, block)``"
    "Beschreibung", "Roboter-Software-Upgrade"
    "Erforderliche Parameter", "- ``filePath``: Vollständiger Pfad zum Software-Upgrade-Paket
    - ``block``: Blockierend bis zum Upgrade-Abschluss? True = blockierend, False = nicht blockierend"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Status des Roboter-Software-Upgrades abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSoftwareUpgradeState()``"
    "Beschreibung", "Status des Roboter-Software-Upgrades abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``state``: Status des Softwarepaket-Upgrades: 0 = inaktiv oder Upload läuft; 1~100 = Fortschritt in %; -1 = Upgrade fehlgeschlagen; -2 = Prüfsummenfehler; -3 = Versionsprüfung fehlgeschlagen; -4 = Entpacken fehlgeschlagen; -5 = Upgrade der Benutzerkonfiguration fehlgeschlagen; -6 = Upgrade der Peripheriekonfiguration fehlgeschlagen; -7 = Upgrade der Erweiterungsachsenkonfiguration fehlgeschlagen; -8 = Upgrade der Roboterko nfiguration fehlgeschlagen; -9 = Upgrade der DH-Parameterkonfiguration fehlgeschlagen"

Codebeispiel für Roboter-Software-Upgrade
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    error = robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", False)
    print(f"SoftwareUpgrade error is {error}")
    while True:
        curState = robot.GetSoftwareUpgradeState()
        print(f"upgrade state is {curState}")
        time.sleep(3)
    robot.CloseRPC()

Punktetabellen-Datenbank herunterladen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointTableDownLoad(point_table_name, save_file_path)``"
    "Beschreibung", "Punktetabellen-Datenbank herunterladen"
    "Erforderliche Parameter", "- ``point_table_name``: Name der herunterzuladenden Punktetabelle, z.B. pointTable1.db
    - ``save_file_path``: Speicherpfad für die heruntergeladene Punktetabelle, z.B. C://test/"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Punktetabellen-Datenbank hochladen
+++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointTableUpLoad(point_table_file_path)``"
    "Beschreibung", "Punktetabellen-Datenbank hochladen"
    "Erforderliche Parameter", "- ``point_table_file_path``: Vollständiger Pfad zur hochzuladenden Punktetabelle, z.B. C://test/pointTable1.db"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lua-Datei mit Punktetabelle aktualisieren
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointTableUpdateLua(point_table_name, lua_file_name)``"
    "Beschreibung", "Lua-Datei mit Punktetabelle aktualisieren"
    "Erforderliche Parameter", "- ``point_table_name``: Name der zu verwendenden Punktetabelle, z.B. pointTable1.db. Wenn der Name leer ist (""), wird das Lua-Programm auf das ursprüngliche Programm ohne Punktetabelle zurückgesetzt.
    - ``lua_file_name``: Name der zu aktualisierenden Lua-Datei, z.B. testPointTable.lua"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Punktetabellen-Operationen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    save_path = "D://zDOWN/"
    point_table_name = "point_table_FR5.db"
    rtn = robot.PointTableDownLoad(point_table_name, save_path)
    print(f"download : {point_table_name} fail: {rtn}")
    upload_path = "D://zDOWN/point_table_FR5.db"
    rtn = robot.PointTableUpLoad(upload_path)
    print(f"retval is: {rtn}")
    point_tablename = "point_table_FR5.db"
    lua_name = "test0610.lua"
    rtn,error = robot.PointTableUpdateLua(point_tablename, lua_name)
    print(f"retval is: {rtn}")
    robot.CloseRPC()

Controller-Protokolle herunterladen
++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RbLogDownload(savePath)``"
    "Beschreibung", "Controller-Protokolle herunterladen"
    "Erforderliche Parameter", "- ``savePath``: Pfad zum Speichern der Datei, z.B. D://zDown/"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Alle Datenquellen herunterladen
++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AllDataSourceDownload(savePath)``"
    "Beschreibung", "Alle Datenquellen herunterladen"
    "Erforderliche Parameter", "- ``savePath``: Pfad zum Speichern der Datei, z.B. D://zDown/"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Daten-Backup-Paket herunterladen
+++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``DataPackageDownload(savePath)``"
    "Beschreibung", "Daten-Backup-Paket herunterladen"
    "Erforderliche Parameter", "- ``savePath``: Pfad zum Speichern der Datei, z.B. D://zDown/"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Herunterladen von Controller-Daten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.RbLogDownload("D://zDOWN/")
    print(f"RbLogDownload rtn is {rtn}")
    rtn = robot.AllDataSourceDownload("D://zDOWN/")
    print(f"AllDataSourceDownload rtn is {rtn}")
    rtn = robot.DataPackageDownload("D://zDOWN/")
    print(f"DataPackageDownload rtn is {rtn}")
    robot.CloseRPC()

Encoder-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetEncoderUpgrade(path)``"
    "Beschreibung", "Encoder-Upgrade einstellen"
    "Erforderliche Parameter", "- ``path``: Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Gelenk-Firmware-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetJointFirmwareUpgrade(type, path)``"
    "Beschreibung", "Gelenk-Firmware-Upgrade einstellen"
    "Erforderliche Parameter", "- ``type``: Dateityp für das Upgrade: 1 = Firmware-Upgrade, 2 = Upgrade der Slave-Konfigurationsdatei
    - ``path``: Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Steuerkasten-Firmware-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetCtrlFirmwareUpgrade(type, path)``"
    "Beschreibung", "Steuerkasten-Firmware-Upgrade einstellen"
    "Erforderliche Parameter", "- ``type``: Dateityp für das Upgrade: 1 = Firmware-Upgrade, 2 = Upgrade der Slave-Konfigurationsdatei
    - ``path``: Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Endeffektor-Firmware-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetEndFirmwareUpgrade(type, path)``"
    "Beschreibung", "Endeffektor-Firmware-Upgrade einstellen"
    "Erforderliche Parameter", "- ``type``: Dateityp für das Upgrade: 1 = Firmware-Upgrade, 2 = Upgrade der Slave-Konfigurationsdatei
    - ``path``: Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Upgrade der vollständigen Gelenkparameter-Konfigurationsdatei
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointAllParamUpgrade(path)``"
    "Beschreibung", "Upgrade der vollständigen Gelenkparameter-Konfigurationsdatei"
    "Erforderliche Parameter", "- ``path``: Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Slave-Firmware-Upgrade
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    robot.RobotEnable(0)
    time.sleep(0.2)
    rtn = robot.JointAllParamUpgrade("D://zUP/MT/joint0603/jointallparameters.db")
    print(f"robot JointAllParamUpgrade rtn is {rtn}")
    rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Cbd_Asix_V2.0.bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Axle_Asix_V2.4.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    robot.SetSysServoBootMode()
    time.sleep(0.2)
    rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/MT/FR_CTRL_PRIMCU_FV201412_MAIN_U4_T01_20250630(MT).bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/MT/FR_END_FV2010010_MAIN_U1_T01_20250603.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/MT/FR_SERVO_FV504215_MAIN_U7_T07_20250603.bin")
    print(f"robot SetJointFirmwareUpgrade rtn is {rtn}")
    robot.CloseRPC()

Upgrade des Roboter-Betriebssystems (LA-Steuerkasten)
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``KernelUpgrade(filePath)``"
    "Beschreibung", "Upgrade des Roboter-Betriebssystems (LA-Steuerkasten)"
    "Erforderliche Parameter", "- ``filePath``: Vollständiger Pfad zum Betriebssystem-Upgrade-Paket"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Ergebnis des Roboter-Betriebssystem-Upgrades abrufen (LA-Steuerkasten)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetKernelUpgradeResult()``"
    "Beschreibung", "Ergebnis des Roboter-Betriebssystem-Upgrades abrufen (LA-Steuerkasten)"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Roboter-MCU-Protokoll generieren
++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RobotMCULogCollect()``"
    "Beschreibung", "Roboter-MCU-Protokoll generieren"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Roboter bei getrennter Port-Kommunikation stoppen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotStopOnComDisc(portID, enable, confirmTime)``"
    "Beschreibung", "Roboter bei getrennter Port-Kommunikation stoppen"
    "Erforderliche Parameter", "
    - ``portID``: Portnummer 0-8080; 1-8083; 2-20002; 3-20004
    - ``enable``: 0-deaktiviert; 1-aktiviert
    - ``confirmTime``: Bestätigungsdauer der Kommunikationsunterbrechung (ms)[0-5000]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
           
Parameter für Roboterstopp bei Kommunikationsunterbrechung abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotStopOnComDisc(portID)``"
    "Beschreibung", "Parameter für Roboterstopp bei Kommunikationsunterbrechung abrufen"
    "Erforderliche Parameter", "
    - ``portID``: Portnummer 0-8080; 1-8083; 2-20002; 3-20004
    - ``enable``: 0-deaktiviert; 1-aktiviert
    - ``confirmTime``: Bestätigungsdauer der Kommunikationsunterbrechung (ms)[0-5000]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Codebeispiel für Parameter Roboterstopp bei Kommunikationsunterbrechung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot
    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    def test_robot_stop_on_com_disc(self):
        # Parameter initialisieren
        enable = False
        confirm_time = 0

        # Roboterstopp bei Kommunikationsunterbrechung einstellen
        rtn = robot.SetRobotStopOnComDisc(0, True, 330)
        print(f"SetRobotStopOnComDisc index0: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(1, True, 550)
        print(f"SetRobotStopOnComDisc index1: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(2, True, 110)
        print(f"SetRobotStopOnComDisc index2: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(3, True, 220)
        print(f"SetRobotStopOnComDisc index3: {rtn}")

        # Roboterstopp bei Kommunikationsunterbrechung abrufen
        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(0)
        print(f"GetRobotStopOnComDisc 8080 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(1)
        print(f"GetRobotStopOnComDisc 80803 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(2)
        print(f"GetRobotStopOnComDisc 20002 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(3)
        print(f"GetRobotStopOnComDisc 20004 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        # RPC-Verbindung schließen
        robot.CloseRPC()
        return 0

    test_robot_stop_on_com_disc(robot)

UDP-Befehlframe senden
+++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SendUDPFrame(frame)``"
    "Beschreibung", "UDP-Befehlframe senden"
    "Erforderliche Parameter", "
    - ``frame``: UDP-Daten zum Senden, transparente Übertragung, keine Kapselung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

SDK-Codebeispiel für UDP-Kommunikation
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    def TestSendUDPFrame(self):
        # Callback einstellen
        def callback(src_type, count, cmd_id, data_len, content):
            print("Antwort erhalten: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0
        robot.SetUDPCmdRpyCallback(callback)

        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame Mode(0) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame("/f/bIII21III303III7IIIMode(1)III/b/f")
        print(f"SendUDPFrame Mode(1) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame(
            "/f/bIII49III201III184IIIMoveJ(-15.625, -82.680, 101.654, -110.950, -88.290, 0.017, -383.012, -2.325, 242.655, -178.024, 1.710, 74.416, 0, 0, 100, 100, 100, 0.000, 0.000, 0.000, 0.000, -1, 0, 0, 0, 0, 0, 0, 0)III/b/f")
        print(f"SendUDPFrame MoveJ(-15.625) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame(
            "/f/bIII48III203III199IIIMoveL(-75.622, -82.680, 101.654, -110.950, -88.290, 0.017, -193.537, 330.525, 242.657, -178.024, 1.710, 14.420, 0, 0, 100, 100, 100, -1, 0, 0.000, 0.000, 0.000, 0.000, 0, 0, 0, 0, 0, 0, 0, 0, 100, 0)III/b/f")
        print(f"SendUDPFrame MoveL(-75.622) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame("/f/bIII4III905III20IIIGetSoftwareVersion()III/b/f")
        print(f"SendUDPFrame GetSoftwareVersion() rtn is {rtn}")

        time.sleep(1)

        # UDP-Frame-Datenvalidierungstest
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("III20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bIII20III303III6IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/b|||20|||303|||7|||Mode(0)|||/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bII20II303II7IIMode(0)II/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        robot.CloseRPC()
        time.sleep(1)

    TestSendUDPFrame(robot)
    
Benutzerdefinierte LED-Farbe des Roboterendeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetUserLEDColor(r, g, b)``"
    "Beschreibung", "Benutzerdefinierte LED-Farbe des Roboterendeffektors einstellen"
    "Erforderliche Parameter", "
    - ``r``: End-Rot-LED-Steuerung; 0-aus; 1-ein
    - ``g``: End-Grün-LED-Steuerung; 0-aus; 1-ein
    - ``b``: End-Blau-LED-Steuerung; 0-aus; 1-ein
    - "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

SDK-Codebeispiel zum Einstellen der benutzerdefinierten LED-Farbe des Roboterendeffektors
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')


    def testled(self):
        # Benutzerdefinierte LED-Farbe einstellen
        # Parameterreihenfolge: R, G, B (Rot, Grün, Blau)

        # Weiß (alle Lichter an)
        robot.SetUserLEDColor(True, True, True)
        time.sleep(1)

        # Alle Lichter ausschalten
        robot.SetUserLEDColor(False, False, False)
        time.sleep(1)

        # Rot (nur rotes Licht)
        robot.SetUserLEDColor(True, False, False)
        time.sleep(1)

        # Grün (nur grünes Licht)
        robot.SetUserLEDColor(False, True, False)
        time.sleep(1)

        # Blau (nur blaues Licht)
        robot.SetUserLEDColor(False, False, True)

        # Verbindung schließen
        robot.CloseRPC()

    testled(robot)