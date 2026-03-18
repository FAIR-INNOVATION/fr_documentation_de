Sonstige Schnittstellen
================================

.. toctree::
    :maxdepth: 5

SSH-Öffentlichen Schlüssel abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt den öffentlichen SSH-Schlüssel zurück.
    * @param [out] keygen Öffentlicher Schlüssel.
    * @return Fehlercode.
    */
    int GetSSHKeygen(ref string keygen);

SCP-Befehl senden
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: csharp
    :linenos:

    /**
    * @brief Sendet einen SCP-Befehl.
    * @param [in] mode 0-Upload (PC->Controller), 1-Download (Controller->PC).
    * @param [in] sshname Benutzername auf dem PC.
    * @param [in] sship IP-Adresse des PCs.
    * @param [in] usr_file_url Dateipfad auf dem PC.
    * @param [in] robot_file_url Dateipfad im Robotercontroller.
    * @return Fehlercode.
    */
    int SetSSHScpCmd(int mode, string sshname, string sship, string usr_file_url, string robot_file_url);

MD5-Wert einer Datei unter einem bestimmten Pfad berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Berechnet den MD5-Wert einer Datei unter einem bestimmten Pfad.
    * @param [in] file_path Dateipfad inklusive Dateiname. Standard-Traj-Ordnerpfad: "/fruser/traj/", z.B. "/fruser/traj/trajHelix_aima_1.txt".
    * @param [out] md5 MD5-Wert der Datei.
    * @return Fehlercode.
    */
    int ComputeFileMD5(string file_path, ref string md5);

Codebeispiel für Roboter-SSH- und MD5-Befehle
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: csharp
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        string file_path = "/fruser/airlab.lua";
        string md5 = "";
        byte emerg_state = 0;
        byte si0_state = 0;
        byte si1_state = 0;
        int sdk_com_state = 0;

        string ssh_keygen = "";
        int retval = robot.GetSSHKeygen(ref ssh_keygen);
        Console.WriteLine("GetSSHKeygen retval is: {0}", retval);
        Console.WriteLine("ssh key is: {0}", ssh_keygen);

        string ssh_name = "fr";
        string ssh_ip = "192.168.58.45";
        string ssh_route = "/home/fr";
        string ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        Console.WriteLine("SetSSHScpCmd retval is: {0}", retval);
        Console.WriteLine("robot url is: {0}", ssh_robot_url);

        robot.ComputeFileMD5(file_path, ref md5);
        Console.WriteLine("md5 is: {0}", md5);
    }

Feedback-Periode für den Roboter-Port 20004 einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Feedback-Periode für den Roboter-Port 20004 ein.
    * @param [in] period Feedback-Periode für Port 20004 (ms).
    * @return Fehlercode.
    */
    int SetRobotRealtimeStateSamplePeriod(int period);

Feedback-Periode für den Roboter-Port 20004 abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Feedback-Periode für den Roboter-Port 20004 zurück.
    * @param [out] period Feedback-Periode für Port 20004 (ms).
    * @return Fehlercode.
    */
    int GetRobotRealtimeStateSamplePeriod(ref int period);

Codebeispiel für die Konfiguration der Feedback-Periode von Port 20004
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button47_Click(object sender, EventArgs e)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        int getPeriod = 0;
        robot.GetRobotRealtimeStateSamplePeriod(ref getPeriod);
        Console.WriteLine("period is {0}", getPeriod);
        Thread.Sleep(1000);
    }

Roboter-Software-Upgrade
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Führt ein Software-Upgrade des Roboters durch.
    * @param [in] filePath Vollständiger Pfad zum Software-Upgrade-Paket.
    * @param [in] block Blockierend bis zum Abschluss des Upgrades warten? true: blockierend; false: nicht blockierend.
    * @return Fehlercode.
    */
    int SoftwareUpgrade(string filePath, bool block);

Status des Roboter-Software-Upgrades abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt den Status des Roboter-Software-Upgrades zurück.
    * @param [out] state Status des Software-Paket-Upgrades. 0-im Leerlauf oder Upgrade-Paket wird hochgeladen; 1~100: Upgrade-Fortschritt in Prozent; -1: Upgrade fehlgeschlagen; -2: Prüfsummenfehler; -3: Versionsprüfung fehlgeschlagen; -4: Entpacken fehlgeschlagen; -5: Benutzerkonfigurations-Upgrade fehlgeschlagen; -6: Peripherie-Konfigurations-Upgrade fehlgeschlagen; -7: Erweiterungsachsen-Konfigurations-Upgrade fehlgeschlagen; -8: Roboter-Konfigurations-Upgrade fehlgeschlagen; -9: DH-Parameter-Konfigurations-Upgrade fehlgeschlagen.
    * @return Fehlercode.
    */
    int GetSoftwareUpgradeState(ref int state);

Codebeispiel für Roboter-Software-Upgrade
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button48_Click(object sender, EventArgs e)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            int curState = -1;
            robot.GetSoftwareUpgradeState(ref curState);
            Console.WriteLine("upgrade state is {0}", curState);
            Thread.Sleep(300);
        }
    }

Punktetabelle herunterladen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Lädt eine Punktetabelle vom Robotercontroller auf den lokalen Computer herunter.
    * @param [in] pointTableName Name der Punktetabelle im Controller: pointTable1.db.
    * @param [in] saveFilePath Pfad, unter dem die Punktetabelle auf dem Computer gespeichert werden soll, z.B. C://test/.
    * @return Fehlercode.
    */
    int PointTableDownLoad(string pointTableName, string saveFilePath);

Punktetabelle hochladen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Lädt eine Punktetabelle vom lokalen Computer in den Robotercontroller hoch.
    * @param [in] pointTableFilePath Absoluter Pfad der Punktetabelle auf dem lokalen Computer, z.B. C://test/pointTable1.db.
    * @return Fehlercode.
    */
    int PointTableUpLoad(string pointTableFilePath);

Lua-Programm mit Punktetabelle aktualisieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Aktualisiert Punkte in einem Lua-Programm mit einer gegebenen Punktetabelle.
    * @param [in] pointTableName Name der Punktetabelle im Controller: "pointTable1.db". Wenn die Punktetabelle leer ist, d.h. "", wird das Lua-Programm auf das ursprüngliche Programm ohne Anwendung der Punktetabelle zurückgesetzt.
    * @param [in] luaFileName Name der zu aktualisierenden Lua-Datei, z.B. "test.lua".
    * @param [out] errorStr Fehlermeldung bei der Aktualisierung des Lua-Programms mit der Punktetabelle.
    * @return Fehlercode.
    */
    int PointTableUpdateLua(string pointTableName, string luaFileName, ref string errorStr);

Punktetabelle wechseln und anwenden
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Wechselt die Punktetabelle und wendet sie an.
    * @param [in] pointTableName Name der zu wechselnden Punktetabelle, z.B. "pointTable1.db".
    * @param [out] errorStr Fehlermeldung beim Wechseln der Punktetabelle.
    * @return Fehlercode.
    */
    int PointTableSwitch(string pointTableName, ref string errorStr);

Codebeispiel für Roboter-Punktetabellen-Operationen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnUpload_Click(object sender, EventArgs e)
    {
        string save_path = "D://zDOWN/";
        string point_table_name = "test_point_A.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);
        Console.WriteLine("download : {0} fail: {1}", point_table_name, rtn);

        string upload_path = "D://zUP/test_point_A.db";
        rtn = robot.PointTableUpLoad(upload_path);
        Console.WriteLine("retval is: {0}", rtn);

        string point_tablename = "test_point_A.db";
        string lua_name = "Text1.lua";

        string errorStr = "";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name, ref errorStr);
        Console.WriteLine("retval is: {0}", rtn);
    }

Controller-Protokolle herunterladen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Lädt Controller-Protokolle herunter.
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/".
    * @return Fehlercode.
    */
    int RbLogDownload(string savePath);

Alle Datenquellen herunterladen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Lädt alle Datenquellen herunter.
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/".
    * @return Fehlercode.
    */
    int AllDataSourceDownload(string savePath);

Datensicherungspaket herunterladen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Lädt das Datensicherungspaket herunter.
    * @param [in] savePath Pfad zum Speichern der Datei, z.B. "D://zDown/".
    * @return Fehlercode.
    */
    int DataPackageDownload(string savePath);

Codebeispiel für das Herunterladen von Controller-Daten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button50_Click(object sender, EventArgs e)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");
        Console.WriteLine("RbLogDownload rtn is {0}", rtn);

        rtn = robot.AllDataSourceDownload("D://zDOWN/");
        Console.WriteLine("AllDataSourceDownload rtn is {0}", rtn);

        rtn = robot.DataPackageDownload("D://zDOWN/");
        Console.WriteLine("DataPackageDownload rtn is {0}", rtn);
    }

Roboter-Betriebssystem-Upgrade (LA-Steuerschrank)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    /**
     * @brief Führt ein Upgrade des Roboter-Betriebssystems durch (LA-Steuerschrank).
     * @param [in] filePath Vollständiger Pfad zum Betriebssystem-Upgrade-Paket.
     * @return Fehlercode.
     */
    public int KernelUpgrade(string filePath);

Ergebnis des Roboter-Betriebssystem-Upgrades abrufen (LA-Steuerschrank)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    /**
     * @brief Gibt das Ergebnis des Roboter-Betriebssystem-Upgrades zurück (LA-Steuerschrank).
     * @param [out] result Upgrade-Ergebnis: 0: Erfolg; -1: Fehler.
     * @return Fehlercode.
     */
    public int GetKernelUpgradeResult(ref int[] result);

Encoder-Upgrade einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt ein Encoder-Upgrade ein.
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin).
    * @return Fehlercode.
    */
    int SetEncoderUpgrade(string path);

Gelenk-Firmware-Upgrade einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt ein Gelenk-Firmware-Upgrade ein.
    * @param [in] type Dateityp für das Upgrade; 1-Firmware-Upgrade; 2-Slave-Konfigurationsdatei-Upgrade.
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin).
    * @return Fehlercode.
    */
    int SetJointFirmwareUpgrade(int type, string path);

Steuerschrank-Firmware-Upgrade einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt ein Steuerschrank-Firmware-Upgrade ein.
    * @param [in] type Dateityp für das Upgrade; 1-Firmware-Upgrade; 2-Slave-Konfigurationsdatei-Upgrade.
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin).
    * @return Fehlercode.
    */
    int SetCtrlFirmwareUpgrade(int type, string path);

Endeffektor-Firmware-Upgrade einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt ein Endeffektor-Firmware-Upgrade ein.
    * @param [in] type Dateityp für das Upgrade; 1-Firmware-Upgrade; 2-Slave-Konfigurationsdatei-Upgrade.
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin).
    * @return Fehlercode.
    */
    int SetEndFirmwareUpgrade(int type, string path);

Upgrade der Gelenk-Gesamtparameter-Konfigurationsdatei
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Führt ein Upgrade der Gelenk-Gesamtparameter-Konfigurationsdatei durch.
    * @param [in] path Vollständiger Pfad zum lokalen Upgrade-Paket (D://zUP/XXXXX.bin).
    * @return Fehlercode.
    */
    int JointAllParamUpgrade(string path);

Codebeispiel für Roboter-Slave-Firmware-Upgrade
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    private void button83_Click(object sender, EventArgs e)
    {
        robot.RobotEnable(0);
        Thread.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
        Console.WriteLine($"robot JointAllParamUpgrade rtn is{rtn}");
        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
        Console.WriteLine($"robot SetJointFirmwareUpgrade rtn is{rtn}");
    }

Roboter-MCU-Protokoll generieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Generiert ein Roboter-MCU-Protokoll.
    * @return Fehlercode.
    */
    public int RobotMCULogCollect();