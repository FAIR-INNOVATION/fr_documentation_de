Roboter-Grundlagen
==================

.. toctree::
    :maxdepth: 5

Roboter instanziieren
+++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Konstruktor der Roboter-Schnittstellenklasse
    */
    FRRobot();

Kommunikation mit der Steuerung aufbauen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kommunikation mit der Robotersteuerung aufbauen
    * @param [in] ip IP-Adresse der Steuerung, werkseitig standardmäßig 192.168.58.2
    * @return Fehlercode
    */
    errno_t RPC(const char *ip);

Kommunikation mit der Steuerung schließen
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Kommunikation mit der Robotersteuerung schließen
     * @return Fehlercode
     */
    errno_t CloseRPC();

SDK-Version abfragen
++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief SDK-Version abfragen
    * @param [out] version SDK-Versionsnummer
    * @return Fehlercode
    */
    errno_t GetSDKVersion(char *version);

Controller-IP abrufen
+++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Controller-IP abrufen
    * @param [out] ip Controller-IP
    * @return Fehlercode
    */
    errno_t GetControllerIP(char *ip);

Roboter in den oder aus dem Drag&Teach-Modus schalten
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter in den oder aus dem Drag&Teach-Modus schalten
    * @param [in] state 0 - Drag&Teach-Modus verlassen, 1 - Drag&Teach-Modus betreten
    * @return Fehlercode
    */
    errno_t DragTeachSwitch(uint8_t state);

Abfragen, ob sich der Roboter im Drag-Modus befindet
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Abfragen, ob sich der Roboter im Drag&Teach-Modus befindet
    * @param [out] state 0 - nicht im Drag&Teach-Modus, 1 - im Drag&Teach-Modus
    * @return Fehlercode
    */
    errno_t IsInDragTeach(uint8_t *state);

Roboter aktivieren (Enable) oder deaktivieren (Disable)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter aktivieren (Enable) oder deaktivieren (Disable). Nach dem Einschalten ist der Roboter standardmäßig automatisch aktiviert.
    * @param [in] state 0 - deaktivieren, 1 - aktivieren
    * @return Fehlercode
    */
    errno_t RobotEnable(uint8_t state);

Umschalten zwischen Hand- und Automatikmodus
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Umschalten zwischen Hand- und Automatikmodus des Roboters
    * @param [in] mode 0 - Automatikmodus, 1 - Handmodus
    * @return Fehlercode
    */
    errno_t Mode(int mode);

Roboter-Betriebssystem herunterfahren
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-Betriebssystem herunterfahren
    * @return Fehlercode
    */
    errno_t ShutDownRobotOS();

Parameter für die Wiederverbindung mit der Robotersteuerung einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Parameter für die Wiederverbindung mit der Robotersteuerung einstellen
    * @param [in] enable Wiederverbindung bei Netzwerkfehler aktivieren: true - aktivieren, false - deaktivieren
    * @param [in] reconnectTime Wiederverbindungszeit (ms)
    * @param [in] period Wiederverbindungszyklus (ms)
    * @return Fehlercode
    */
    errno_t SetReConnectParam(bool enable, int reconnectTime = 30000, int period = 50);

Roboter-Betriebssystem herunterfahren (C#)
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Roboter-Betriebssystem herunterfahren
    * @return Fehlercode
    */
    int ShutDownRobotOS();

Logging-Parameter initialisieren
++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Logging-Parameter initialisieren
    * @param output_model: Ausgabemodus, 0 - direkte Ausgabe, 1 - gepufferte Ausgabe, 2 - asynchrone Ausgabe
    * @param file_path: Pfad und Name der Logdatei, maximale Länge 256, Name muss die Form xxx.log haben, z.B. /home/fr/linux/fairino.log
    * @param file_num: Anzahl der rollierenden Logdateien, 1~20. Einzeldateigröße max. 50 MB
    * @return Fehlercode
    */
    errno_t LoggerInit(int output_model = 0, std::string file_path = "", int file_num = 5);

Logging-Filterstufe einstellen
+++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Logging-Filterstufe einstellen
    * @param lvl: Filterstufe. Je kleiner der Wert, desto weniger Logs werden ausgegeben. Standardwert ist 1. 1 = error, 2 = warning, 3 = info, 4 = debug
    */
    void SetLoggerLevel(int lvl = 1);

Codebeispiel für grundlegende Robotersteuerung
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestRobotCtrl(void)
    {
            ROBOT_STATE_PKG pkg = {};
            FRRobot robot;
            robot.LoggerInit();
            robot.SetLoggerLevel(1);
            int rtn = robot.RPC("192.168.58.2");
            robot.SetReConnectParam(true, 30000, 500);
            char ip[64] = "";
            char version[64] = "";
            uint8_t state;
            robot.GetSDKVersion(version);
            printf("SDK version:%s\n", version);
            robot.GetControllerIP(ip);
            printf("controller ip:%s\n", ip);
            robot.Mode(1);
            robot.Sleep(1000);
            robot.DragTeachSwitch(1);
            robot.Sleep(1000);
            robot.IsInDragTeach(&state);
            printf("drag state :%u\n", state);
            robot.Sleep(3000);
            robot.DragTeachSwitch(0);
            robot.Sleep(1000);
            robot.IsInDragTeach(&state);
            printf("drag state :%u\n", state);
            robot.Sleep(3000);
            robot.RobotEnable(0);
            robot.Sleep(3000);
            robot.RobotEnable(1);
            robot.Mode(0);
            robot.Sleep(1000);
            robot.Mode(1);
            robot.Sleep(3000);
            robot.ShutDownRobotOS();
            robot.CloseRPC();
            return 0;
    }

Codebeispiel zum Abrufen der Softwareversion des Roboters
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Softwareversion des Roboters abrufen
    * @param[out] robotModel Robotermodell
    * @param[out] webVersion Web-Version
    * @param[out] controllerVersion Controller-Version
    * @return Fehlercode
    */
    errno_t GetSoftwareVersion(char robotModel[64], char webVersion[64], char controllerVersion[64]);

Hardwareversion des Roboters abrufen
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Hardwareversion des Roboters abrufen
    * @param[out] ctrlBoxBoardversion Hardwareversion der Steuerkasten-Trägerplatine
    * @param[out] driver1version Hardwareversion von Antrieb 1
    * @param[out] driver2version Hardwareversion von Antrieb 2
    * @param[out] driver3version Hardwareversion von Antrieb 3
    * @param[out] driver4version Hardwareversion von Antrieb 4
    * @param[out] driver5version Hardwareversion von Antrieb 5
    * @param[out] driver6version Hardwareversion von Antrieb 6
    * @param[out] endBoardversion Hardwareversion der Endeffektorplatine
    */
    errno_t GetHardwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Firmwareversion des Roboters abrufen
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Firmwareversion des Roboters abrufen
    * @param[out] ctrlBoxBoardversion Firmwareversion der Steuerkasten-Trägerplatine
    * @param[out] driver1version Firmwareversion von Antrieb 1
    * @param[out] driver2version Firmwareversion von Antrieb 2
    * @param[out] driver3version Firmwareversion von Antrieb 3
    * @param[out] driver4version Firmwareversion von Antrieb 4
    * @param[out] driver5version Firmwareversion von Antrieb 5
    * @param[out] driver6version Firmwareversion von Antrieb 6
    * @param[out] endBoardversion Firmwareversion der Endeffektorplatine
    */
    errno_t GetFirmwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Codebeispiel zum Abrufen der Software- und Firmwareversionen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetVersions(void)
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
         char robotModel[64] = { 0 };
         char webversion[64] = { 0 };
         char controllerVersion[64] = { 0 };
         char ctrlBoxBoardversion[128] = { 0 };
         char driver1version[128] = { 0 };
         char driver2version[128] = { 0 };
         char driver3version[128] = { 0 };
         char driver4version[128] = { 0 };
         char driver5version[128] = { 0 };
         char driver6version[128] = { 0 };
         char endBoardversion[128] = { 0 };
         rtn = robot.GetSoftwareVersion(robotModel, webversion, controllerVersion);
         printf("Getsoftwareversion rtn is: %d\n", rtn);
         printf("robotmodel is: %s, webversion is: %s, controllerVersion is: %s \n\n", robotModel, webversion, controllerVersion);
         rtn = robot.GetHardwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetHardwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         rtn = robot.GetFirmwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetFirmwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         robot.CloseRPC();
         return 0;
     }
