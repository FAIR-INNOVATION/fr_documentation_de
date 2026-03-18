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