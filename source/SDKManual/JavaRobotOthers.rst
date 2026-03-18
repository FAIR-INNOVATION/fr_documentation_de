Weitere Schnittstellen
======================

.. toctree::
    :maxdepth: 5

SSH öffentlichen Schlüssel abrufen
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief SSH öffentlichen Schlüssel abrufen
    * @param [out] keygen Öffentlicher Schlüssel (als String-Array der Länge 1 übergeben)
    * @return Fehlercode
    */
    int GetSSHKeygen(String[] keygen)

SCP-Befehl senden
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
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
    int SetSSHScpCmd(int mode, String sshname, String sship, String usr_file_url, String robot_file_url)

MD5-Wert einer Datei unter einem bestimmten Pfad berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief MD5-Wert einer Datei unter einem bestimmten Pfad berechnen
    * @param [in] file_path Dateipfad inklusive Dateiname. Standard-Traj-Ordnerpfad: "/fruser/traj/", z.B. "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 MD5-Wert der Datei (als String-Array der Länge 1 übergeben)
    * @return Fehlercode
    */
    int ComputeFileMD5(String file_path, String[] md5)

Codebeispiel für SSH- und MD5-Befehle des Roboters
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSSHMd5(Robot robot)
    {
        String file_path= "/fruser/airlab.lua";
        String[] md5 =new String[]{""};

        String[] ssh_keygen=new String[]{""};
        int retval = robot.GetSSHKeygen(ssh_keygen);
        System.out.println(ssh_keygen[0]);

        String ssh_name = "fr";
        String ssh_ip = "192.168.58.45";
        String ssh_route = "/home/fr";
        String ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        System.out.println("SetSSHScpCmd retval is:"+ retval);
        System.out.println("robot url is:"+ ssh_robot_url);

        robot.ComputeFileMD5(file_path, md5);
        System.out.println("md5 is:+"+ md5[0]);
        return 0;
    }

Rückmeldezyklus für den Roboter-Port 20004 einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Rückmeldezyklus für den Roboter-Port 20004 einstellen
    * @param [in] period Rückmeldezyklus für Port 20004 (ms)
    * @return Fehlercode
    */
    public int SetRobotRealtimeStateSamplePeriod(int period)

Rückmeldezyklus für den Roboter-Port 20004 abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Rückmeldezyklus für den Roboter-Port 20004 abrufen
    * @return List[0]: Fehlercode; List[1]: Rückmeldezyklus für Port 20004 (ms)
    */
    public List<Integer> GetRobotRealtimeStateSamplePeriod()

Codebeispiel für die Konfiguration des Statusrückmeldezyklus (Port 20004)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestRealtimePeriod(Robot robot)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        List<Integer> getPeriod = new ArrayList<>();
        getPeriod=robot.GetRobotRealtimeStateSamplePeriod();
        robot.Sleep(1000);

        return 0;
    }

Roboter-Software-Upgrade
++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Roboter-Software-Upgrade
     * @param [in] filePath Vollständiger Pfad zum Software-Upgrade-Paket
     * @param [in] block Blockierend bis zum Upgrade-Abschluss? true: blockierend, false: nicht blockierend
     * @return Fehlercode
     */
    public int SoftwareUpgrade(String filePath, boolean block)

Status des Roboter-Software-Upgrades abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Status des Roboter-Software-Upgrades abrufen
    * @return List[0]: Fehlercode; List[1]: Status (0 - inaktiv oder Upload läuft; 1~100 - Fortschritt in %; -1: Upgrade fehlgeschlagen; -2: Prüfsummenfehler; -3: Versionsprüfung fehlgeschlagen; -4: Entpacken fehlgeschlagen; -5: Upgrade der Benutzerkonfiguration fehlgeschlagen; -6: Upgrade der Peripheriekonfiguration fehlgeschlagen; -7: Upgrade der Erweiterungsachsenkonfiguration fehlgeschlagen; -8: Upgrade der Roboterko nfiguration fehlgeschlagen; -9: Upgrade der DH-Parameterkonfiguration fehlgeschlagen)
    */
    public List<Integer> GetSoftwareUpgradeState()

Codebeispiel für Roboter-Software-Upgrade
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUpgrade(Robot robot)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            List<Integer> inter=new ArrayList<>();
            inter=robot.GetSoftwareUpgradeState();
            System.out.println("upgrade state is:"+ inter.get(1));
            robot.Sleep(300);
        }
    }

Punktetabellen-Datenbank herunterladen
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Punktetabellen-Datenbank herunterladen
    * @param [in] pointTableName Name der herunterzuladenden Punktetabelle, z.B. "pointTable1.db"
    * @param [in] saveFilePath Speicherpfad für die heruntergeladene Punktetabelle, z.B. "C://test/"
    * @return Fehlercode
    */
    int PointTableDownLoad(String pointTableName, String saveFilePath);

Punktetabellen-Datenbank hochladen
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Punktetabellen-Datenbank hochladen
    * @param [in] pointTableFilePath Vollständiger Pfad zur hochzuladenden Punktetabelle, z.B. "C://test/pointTable1.db"
    * @return Fehlercode
    */
    int PointTableUpLoad(String pointTableFilePath);

Lua-Datei mit Punktetabelle aktualisieren
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Lua-Datei mit Punktetabelle aktualisieren
    * @param [in] pointTableName Name der zu verwendenden Punktetabelle, z.B. "pointTable1.db". Wenn der Name leer ist (""), wird das Lua-Programm auf das ursprüngliche Programm ohne Punktetabelle zurückgesetzt.
    * @param [in] luaFileName Name der zu aktualisierenden Lua-Datei, z.B. "testPointTable.lua"
    * @param [out] errorStr Fehlermeldung beim Wechsel der Punktetabelle (als String-Array der Länge 1 übergeben)
    * @return Fehlercode
    */
    int PointTableUpdateLua(String pointTableName, String luaFileName, String[] errorStr);

Codebeispiel für Roboter-Punktetabellen-Operationen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPointTable(Robot robot)
    {
        String save_path = "D://zDOWN/";
        String point_table_name = "point_table_FR5.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);

        String upload_path = "D://zUP/point_table_FR5.db";
        rtn = robot.PointTableUpLoad(upload_path);

        String point_tablename = "point_table_FR5.db";
        String lua_name = "airlab.lua";
        String err="";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name,err);

        robot.CloseRPC();
        return 0;
    }

Controller-Protokolle herunterladen
++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Controller-Protokolle herunterladen
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/"
    * @return Fehlercode
    */
    int RbLogDownload(String savePath);

Alle Datenquellen herunterladen
++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Alle Datenquellen herunterladen
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/"
    * @return Fehlercode
    */
    int AllDataSourceDownload(String savePath);

Daten-Backup-Paket herunterladen
+++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Daten-Backup-Paket herunterladen
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/"
    * @return Fehlercode
    */
    int DataPackageDownload(String savePath);

Codebeispiel zum Herunterladen von Controller-Daten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestDownLoadRobotData(Robot robot)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");

        rtn = robot.AllDataSourceDownload("D://zDOWN/");

        rtn = robot.DataPackageDownload("D://zDOWN/");
        return 0;
    }

Encoder-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Encoder-Upgrade einstellen
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    int SetEncoderUpgrade(String path)

Gelenk-Firmware-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Firmware-Upgrade einstellen
    * @param [in] type Dateityp für das Upgrade: 1 - Firmware-Upgrade, 2 - Upgrade der Slave-Konfigurationsdatei
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    public int SetJointFirmwareUpgrade(int type, String path)

Steuerkasten-Firmware-Upgrade einstellen
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Steuerkasten-Firmware-Upgrade einstellen
    * @param [in] type Dateityp für das Upgrade: 1 - Firmware-Upgrade, 2 - Upgrade der Slave-Konfigurationsdatei
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    public int SetCtrlFirmwareUpgrade(int type, String path)

Endeffektor-Firmware-Upgrade einstellen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Endeffektor-Firmware-Upgrade einstellen
    * @param [in] type Dateityp für das Upgrade: 1 - Firmware-Upgrade, 2 - Upgrade der Slave-Konfigurationsdatei
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    public int SetEndFirmwareUpgrade(int type, String path)

Upgrade der vollständigen Gelenkparameter-Konfigurationsdatei
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Upgrade der vollständigen Gelenkparameter-Konfigurationsdatei
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (z.B. D://zUP/XXXXX.bin)
    * @return Fehlercode
    */
    public int JointAllParamUpgrade(String path)

Codebeispiel für Roboter-Slave-Firmware-Upgrade
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFirmWareUpgrade(Robot robot)
    {
        robot.RobotEnable(0);
        robot.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/standardQX/jointallparametersFR56.0.db");
        System.out.println("robot JointAllParamUpgrade rtn is:"+ rtn);

        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade config param rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        System.out.println("robot SetEndFirmwareUpgrade config param rtn is:"+ rtn);

        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/standardQX/FR_CTRL_PRIMCU_FV201010_MAIN_U4_T01_20240529.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/standardQX/FR_END_FV201010_MAIN_U01_T01_20250522.bin");
        System.out.println("robot SetEndFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/standardQX/FR_SERVO_FV502211_MAIN_U7_T07_20250217.bin");
        System.out.println("robot SetJointFirmwareUpgrade rtn is:"+ rtn);

        robot.CloseRPC();
    }

Upgrade des Roboter-Betriebssystems (LA-Steuerkasten)
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Upgrade des Roboter-Betriebssystems (LA-Steuerkasten)
     * @param [in] filePath Vollständiger Pfad zum Betriebssystem-Upgrade-Paket
     * @return Fehlercode
     */
    public int KernelUpgrade(String filePath)

Ergebnis des Roboter-Betriebssystem-Upgrades abrufen (LA-Steuerkasten)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ergebnis des Roboter-Betriebssystem-Upgrades abrufen (LA-Steuerkasten)
     * @param [out] result Upgrade-Ergebnis (als int-Array der Länge 1 übergeben): 0 = Erfolg, -1 = Fehlschlag
     * @return Fehlercode
     */
    public int GetKernelUpgradeResult(int[] result)

Roboter-MCU-Protokoll generieren
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-MCU-Protokoll generieren
    * @return Fehlercode
    */
    public int RobotMCULogCollect()