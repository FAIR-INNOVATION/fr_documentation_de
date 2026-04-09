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

Roboter bei getrennter Port-Kommunikation stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter bei getrennter Port-Kommunikation stoppen
    * @param portID Portnummer 0-8080; 1-8083; 2-20002; 3-20004
    * @param enable 0-deaktiviert; 1-aktiviert
    * @param confirmTime Bestätigungsdauer der Kommunikationsunterbrechung (ms)[0-5000]
    * @return Fehlercode
    */
    public int SetRobotStopOnComDisc(int portID, bool enable, int confirmTime)
    
Parameter für Roboterstopp bei Kommunikationsunterbrechung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Parameter für Roboterstopp bei Kommunikationsunterbrechung abrufen
    * @param portID Portnummer 0-8080; 1-8083; 2-20002; 3-20004
    * @param enable Ergebnisarray, Index 0: 0-deaktiviert; 1-aktiviert
    * @param confirmTime Ergebnisarray, Index 0: Bestätigungsdauer der Kommunikationsunterbrechung (ms)[0-5000]
    * @return Fehlercode
    */
    public int GetRobotStopOnComDisc(int portID, int[] enable, int[] confirmTime)

Codebeispiel für Parameter Roboterstopp bei Kommunikationsunterbrechung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    void TestRobotStopOnComDisc(Robot robot)
    {
        int[] enable = {0};
        int[] confirmTime = {0};
        int rtn = 0;
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        System.out.printf("SetRobotStopOnComDisc %d\n", rtn);

        robot.GetRobotStopOnComDisc(0, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 8080 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(1, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 8083 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(2, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 20002 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(3, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 20004 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);

        return;
    }

UDP-Befehlframe senden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief UDP-Befehlframe senden
    * @param frame Befehlframe
    * @return Fehlercode
    */
    public int SendUDPFrame(String frame)
    
SDK-Codebeispiel für UDP-Kommunikation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestRobotUDP (Robot robot) {
        robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Roboter-UDP-Antwort erhalten]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("Inhalt: " + content);
            return 0;
        });
        // Frame senden
        String frameToSend = "/f/bIII52III236III7IIIMode(1)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII52III236III7IIIMode(0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII41III201III153IIIMoveJ(53.857,-89.441,119.453,-22.664,61.059,3.369,-54.249,-491.930,375.396,96.474,-6.896,-7.783,0,0,100,100,100,0.000,0.000,0.000,0.000,-1,0,0,0,0,0,0,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII42III203III163IIIMoveL(81.736,-85.284,114.974,-23.261,88.746,6.799,125.744,-506.570,375.396,96.474,-6.896,-7.783,0,0,100,100,100,-1,0,0.000,0.000,0.000,0.000,0,0,0,0,0,0,0,0,100,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII47III400III15IIIGetMCVersion(1)III/b/f/f/bIII48III424III21IIIGetSlaveFirmVersion()III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
    }
        
Benutzerdefinierte LED-Farbe des Roboterendeffektors einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Benutzerdefinierte LED-Farbe des Roboterendeffektors einstellen
    * @param r End-Rot-LED-Steuerung; 0-aus; 1-ein
    * @param g End-Grün-LED-Steuerung; 0-aus; 1-ein
    * @param b End-Blau-LED-Steuerung; 0-aus; 1-ein
    * @return Fehlercode
    */
    public int SetUserLEDColor(bool r, bool g, bool b)
            
SDK-Codebeispiel zum Einstellen der benutzerdefinierten LED-Farbe des Roboterendeffektors
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public void testled(robot)
    {
        robot.SetUserLEDColor(true, true, true);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(true, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, true, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, true);
    }