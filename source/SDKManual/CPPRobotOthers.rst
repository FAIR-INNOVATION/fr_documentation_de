Weitere Schnittstellen
======================

.. toctree::
    :maxdepth: 5

SSH öffentlichen Schlüssel abrufen
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief SSH öffentlichen Schlüssel abrufen
    * @param [out] keygen Öffentlicher Schlüssel
    * @return Fehlercode
    */
    errno_t GetSSHKeygen(char keygen[1024]);

SCP-Befehl senden
+++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief SCP-Befehl senden
    * @param [in] mode 0 - Hochladen (PC -> Controller), 1 - Herunterladen (Controller -> PC)
    * @param [in] sshname Benutzername auf dem PC
    * @param [in] sship IP-Adresse des PCs
    * @param [in] usr_file_url Dateipfad auf dem PC
    * @param [in] robot_file_url Dateipfad auf der Robotersteuerung
    * @return Fehlercode
    */
    errno_t SetSSHScpCmd(int mode, char sshname[32], char sship[32], char usr_file_url[128], char robot_file_url[128]);

MD5-Wert einer Datei unter einem bestimmten Pfad berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief MD5-Wert einer Datei unter einem bestimmten Pfad berechnen
    * @param [in] file_path Dateipfad inklusive Dateiname. Standard-Traj-Ordnerpfad: "/fruser/traj/", z.B. "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 MD5-Wert der Datei
    * @return Fehlercode
    */
    errno_t ComputeFileMD5(char file_path[256], char md5[256]);

Codebeispiel für SSH- und MD5-Befehle des Roboters
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSSHMd5(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      char file_path[256] = "/fruser/airlab.lua";
      char md5[256] = { 0 };
      uint8_t emerg_state = 0;
      uint8_t si0_state = 0;
      uint8_t si1_state = 0;
      int sdk_com_state = 0;
      char ssh_keygen[1024] = { 0 };
      int retval = robot.GetSSHKeygen(ssh_keygen);
      printf("GetSSHKeygen retval is: %d\n", retval);
      printf("ssh key is: %s \n", ssh_keygen);
      char ssh_name[32] = "fr";
      char ssh_ip[32] = "192.168.58.45";
      char ssh_route[128] = "/home/fr";
      char ssh_robot_url[128] = "/root/robot/dhpara.config";
      retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
      printf("SetSSHScpCmd retval is: %d\n", retval);
      printf("robot url is: %s\n", ssh_robot_url);
      robot.ComputeFileMD5(file_path, md5);
      printf("md5 is: %s \n", md5);
      robot.CloseRPC();
      return 0;
    }

Rückmeldezyklus für den Roboter-Port 20004 einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rückmeldezyklus für den Roboter-Port 20004 einstellen
    * @param [in] period Rückmeldezyklus für Port 20004 (ms)
    * @return Fehlercode
    */
    errno_t SetRobotRealtimeStateSamplePeriod(int period);

Rückmeldezyklus für den Roboter-Port 20004 abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rückmeldezyklus für den Roboter-Port 20004 abrufen
    * @param [out] period Rückmeldezyklus für Port 20004 (ms)
    * @return Fehlercode
    */
    errno_t GetRobotRealtimeStateSamplePeriod(int& period);

Codebeispiel für die Konfiguration des Statusrückmeldezyklus (Port 20004)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestRealtimePeriod(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.SetRobotRealtimeStateSamplePeriod(10);
      int getPeriod = 0;
      robot.GetRobotRealtimeStateSamplePeriod(getPeriod);
      cout << "period is " << getPeriod << endl;
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }

Roboter-Software-Upgrade
++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-Software-Upgrade
    * @param [in] filePath Vollständiger Pfad zum Software-Upgrade-Paket
    * @param [in] block Blockierend bis zum Upgrade-Abschluss? true: blockierend, false: nicht blockierend
    * @return Fehlercode
    */
    errno_t SoftwareUpgrade(std::string filePath, bool block);

Status des Roboter-Software-Upgrades abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Status des Roboter-Software-Upgrades abrufen
    * @param [out] state Status des Softwarepaket-Upgrades (0 - inaktiv oder Upload läuft; 1~100 - Upgrade-Fortschritt in Prozent; -1: Upgrade fehlgeschlagen; -2: Prüfsummenfehler; -3: Versionsprüfung fehlgeschlagen; -4: Entpacken fehlgeschlagen; -5: Upgrade der Benutzerkonfiguration fehlgeschlagen; -6: Upgrade der Peripheriekonfiguration fehlgeschlagen; -7: Upgrade der Erweiterungsachsenkonfiguration fehlgeschlagen; -8: Upgrade der Roboterko nfiguration fehlgeschlagen; -9: Upgrade der DH-Parameterkonfiguration fehlgeschlagen)
    * @return Fehlercode
    */
    errno_t GetSoftwareUpgradeState(int &state);

Codebeispiel für Roboter-Software-Upgrade
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestUpgrade(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(3);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.SoftwareUpgrade("D://zUP/QNX/software.tar.gz", false);
      while (true)
      {
        int curState = -1;
        robot.GetSoftwareUpgradeState(curState);
        printf("upgrade state is %d\n", curState);
        robot.Sleep(300);
      }
      robot.CloseRPC();
      return 0;
    }

Punktetabellen-Datenbank herunterladen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Punktetabellen-Datenbank herunterladen
    * @param [in] pointTableName Name der herunterzuladenden Punktetabelle, z.B. "pointTable1.db"
    * @param [in] saveFilePath Speicherpfad für die heruntergeladene Punktetabelle, z.B. "C://test/"
    * @return Fehlercode
    */
    errno_t PointTableDownLoad(const std::string &pointTableName, const std::string &saveFilePath);

Punktetabellen-Datenbank hochladen
+++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Punktetabellen-Datenbank hochladen
    * @param [in] pointTableFilePath Vollständiger Pfad zur hochzuladenden Punktetabelle, z.B. "C://test/pointTable1.db"
    * @return Fehlercode
    */
    errno_t PointTableUpLoad(const std::string &pointTableFilePath);

Lua-Datei mit Punktetabelle aktualisieren
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Lua-Datei mit Punktetabelle aktualisieren
    * @param [in] pointTableName Name der zu verwendenden Punktetabelle, z.B. "pointTable1.db". Wenn der Name leer ist (""), wird das Lua-Programm auf das ursprüngliche Programm ohne Punktetabelle zurückgesetzt.
    * @param [in] luaFileName Name der zu aktualisierenden Lua-Datei, z.B. "testPointTable.lua"
    * @param [out] errorStr Fehlermeldung beim Wechsel der Punktetabelle
    * @return Fehlercode
    */
    errno_t PointTableUpdateLua(const std::string &pointTableName, const std::string &luaFileName);

Codebeispiel für Roboter-Punktetabellen-Operationen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestPointTable(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      string save_path = "D://zDOWN/";
      string point_table_name = "point_table_FR5.db";
      rtn = robot.PointTableDownLoad(point_table_name, save_path);
      cout << "download : " << point_table_name << " fail: " << rtn << endl;
      string upload_path = "D://zUP/point_table_FR5.db";
      rtn = robot.PointTableUpLoad(upload_path);
      cout << "retval is: " << rtn << endl;
      string point_tablename = "point_table_FR5.db";
      string lua_name = "airlab.lua";
      rtn = robot.PointTableUpdateLua(point_tablename, lua_name);
      cout << "retval is: " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Controller-Protokolle herunterladen
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Controller-Protokolle herunterladen
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/"
    * @return Fehlercode
    */
    errno_t RbLogDownload(std::string savePath);

Alle Datenquellen herunterladen
++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Alle Datenquellen herunterladen
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/"
    * @return Fehlercode
    */
    errno_t AllDataSourceDownload(std::string savePath);

Daten-Backup-Paket herunterladen
+++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Daten-Backup-Paket herunterladen
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/"
    * @return Fehlercode
    */
    errno_t DataPackageDownload(std::string savePath);

Codebeispiel zum Herunterladen von Controller-Daten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestDownLoadRobotData(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      rtn = robot.RbLogDownload("D://zDOWN/");
      cout << "RbLogDownload rtn is " << rtn << endl;
      rtn = robot.AllDataSourceDownload("D://zDOWN/");
      cout << "AllDataSourceDownload rtn is " << rtn << endl;
      rtn = robot.DataPackageDownload("D://zDOWN/");
      cout << "DataPackageDownload rtn is " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Gelenk-Firmware-Upgrade einstellen
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Firmware-Upgrade einstellen
    * @param [in] type Dateityp für das Upgrade: 1 - Firmware-Upgrade (vor Verwendung muss der Roboter in den Boot-Modus versetzt werden); 2 - Upgrade der Slave-Konfigurationsdatei (vor Verwendung muss der Roboter deaktiviert werden)
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    errno_t SetJointFirmwareUpgrade(int type, std::string path);

Steuerkasten-Firmware-Upgrade einstellen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Steuerkasten-Firmware-Upgrade einstellen
    * @param [in] type Dateityp für das Upgrade: 1 - Firmware-Upgrade (vor Verwendung muss der Roboter in den Boot-Modus versetzt werden); 2 - Upgrade der Slave-Konfigurationsdatei (vor Verwendung muss der Roboter deaktiviert werden)
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    errno_t SetCtrlFirmwareUpgrade(int type, std::string path);

Endeffektor-Firmware-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Firmware-Upgrade einstellen
    * @param [in] type Dateityp für das Upgrade: 1 - Firmware-Upgrade (vor Verwendung muss der Roboter in den Boot-Modus versetzt werden); 2 - Upgrade der Slave-Konfigurationsdatei (vor Verwendung muss der Roboter deaktiviert werden)
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    errno_t SetEndFirmwareUpgrade(int type, std::string path);

Upgrade der vollständigen Gelenkparameter-Konfigurationsdatei
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Upgrade der vollständigen Gelenkparameter-Konfigurationsdatei (vor Verwendung muss der Roboter deaktiviert werden)
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    errno_t JointAllParamUpgrade(std::string path);

Codebeispiel für Roboter-Slave-Firmware-Upgrade
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFirmWareUpgrade()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.RobotEnable(0);
      robot.Sleep(200);
      rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
      printf("robot JointAllParamUpgrade rtn ist %d\n", rtn);
      rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
      printf("robot SetCtrlFirmwareUpgrade (Konfiguration) rtn ist %d\n", rtn);
      rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
      printf("robot SetEndFirmwareUpgrade (Konfiguration) rtn ist %d\n", rtn);
      robot.SetSysServoBootMode();
      rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
      printf("robot SetCtrlFirmwareUpgrade (Firmware) rtn ist %d\n", rtn);
      rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
      printf("robot SetEndFirmwareUpgrade (Firmware) rtn ist %d\n", rtn);
      rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
      printf("robot SetJointFirmwareUpgrade (Firmware) rtn ist %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Upgrade des Roboter-Betriebssystems (LA-Steuerkasten)
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Upgrade des Roboter-Betriebssystems (LA-Steuerkasten)
    * @param [in] filePath Vollständiger Pfad zum Betriebssystem-Upgrade-Paket
    * @return Fehlercode
    */
    errno_t KernelUpgrade(std::string filePath);

Ergebnis des Roboter-Betriebssystem-Upgrades abrufen (LA-Steuerkasten)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Ergebnis des Roboter-Betriebssystem-Upgrades abrufen (LA-Steuerkasten)
    * @param [out] result Upgrade-Ergebnis: 0 = Erfolg, -1 = Fehlschlag
    * @return Fehlercode
    */
    errno_t GetKernelUpgradeResult(int& result);

Roboter-MCU-Protokoll generieren
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-MCU-Protokoll generieren
    * @return Fehlercode
    */
    errno_t RobotMCULogCollect();