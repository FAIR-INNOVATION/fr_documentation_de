Roboter-Grundlagen
===========================

.. toctree::
    :maxdepth: 5

Roboter instanziieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Konstruktor der Roboter-Schnittstellenklasse.
    */
    Robot robot = new Robot();

Kommunikation mit der Steuerung herstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Stellt die Kommunikation mit der Robotersteuerung her.
    * @param  [in] ip  IP-Adresse der Steuerung, werkseitig Standard 192.168.58.2.
    * @return Fehlercode.
    */
    int RPC(String ip);

Kommunikation mit dem Roboter schließen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schließt die Kommunikation mit dem Roboter.
    * @return Fehlercode.
    */
    int CloseRPC();

SDK-Version abfragen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Fragt die SDK-Versionsnummer ab.
    * @return Versionsnummer als String.
    */
    String GetSDKVersion();

Controller-IP abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Controller-IP zurück.
    * @param [out] ip String-Array zur Aufnahme der Controller-IP (erwartet Array der Länge 1).
    * @return Fehlercode.
    */
    int GetControllerIP(String[] ip);

Roboter in den Ziehe-Teaching-Modus schalten oder daraus zurückkehren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schaltet den Roboter in den Ziehe-Teaching-Modus oder zurück.
    * @param [in] state 0-Ziehe-Teaching-Modus verlassen, 1-Ziehe-Teaching-Modus betreten.
    * @return Fehlercode.
    */
    int DragTeachSwitch(int state);

Abfragen, ob sich der Roboter im Ziehe-Teaching-Modus befindet
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Fragt ab, ob sich der Roboter im Ziehe-Teaching-Modus befindet.
    * @param [out] state Liste mit einem Element: 0-nicht im Ziehe-Teaching-Modus, 1-im Ziehe-Teaching-Modus.
    * @return Fehlercode.
    */
    int IsInDragTeach(List<Number> state);

Roboter aktivieren (Enable) oder deaktivieren (Disable)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Aktiviert oder deaktiviert den Roboter. Nach dem Einschalten ist der Roboter standardmäßig automatisch aktiviert.
    * @param [in] state 0-deaktivieren (Disable), 1-aktivieren (Enable).
    * @return Fehlercode.
    */
    int RobotEnable(int state);

Umschalten zwischen Hand- und Automatikmodus
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schaltet zwischen Hand- und Automatikmodus um.
    * @param [in] mode 0-Automatikmodus, 1-Handmodus.
    * @return Fehlercode.
    */
    int Mode(int mode);

Roboter-Betriebssystem herunterfahren
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: java
    :linenos:

    /**
    * @brief Fährt das Roboter-Betriebssystem herunter.
    * @return Fehlercode.
    */
    int ShutDownRobotOS();

Parameter für die automatische Wiederverbindung mit dem Roboter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Parameter für die automatische Wiederverbindung mit dem Roboter ein.
    * @param [in] enable Aktivieren? true-aktivieren, false-deaktivieren.
    * @param [in] times Anzahl der Wiederverbindungsversuche.
    * @param [in] period Zeitintervall zwischen den Wiederverbindungsversuchen (Millisekunden).
    * @return Fehlercode.
    */
    int SetReconnectParam(boolean enable, int times, int period);

Logging-Parameter initialisieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Initialisiert die Logging-Parameter.
    * @param [in] logType Ausgabemodus, DIRECT-direkte Ausgabe; BUFFER-gepufferte Ausgabe; ASYNC-asynchrone Ausgabe.
    * @param [in] logLevel Log-Filterstufe, ERROR-Fehler; WARNING-Warnung; INFO-Information; DEBUG-Debug.
    * @param [in] filePath Pfad zum Speichern der Dateien, z.B. "D://Log/".
    * @param [in] saveFileNum Maximale Anzahl der zu speichernden Dateien. Dateien, die sowohl die maximale Anzahl als auch die maximale Aufbewahrungsdauer überschreiten, werden gelöscht.
    * @param [in] saveDays Maximale Aufbewahrungsdauer in Tagen. Dateien, die sowohl die maximale Anzahl als auch die maximale Aufbewahrungsdauer überschreiten, werden gelöscht.
    * @return Fehlercode.
    */
    int LoggerInit(FrLogType logType, FrLogLevel logLevel, String filePath, int saveFileNum, int saveDays);

Log-Filterstufe einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Log-Filterstufe ein.
    * @param [in] logLevel Log-Filterstufe, ERROR-Fehler; WARNING-Warnung; INFO-Information; DEBUG-Debug.
    * @return Fehlercode.
    */
    int SetLoggerLevel(FrLogLevel logLevel);

Codebeispiel für grundlegende Robotersteuerung
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("RPC-Verbindung erfolgreich");
        }
        else
        {
            System.out.println("RPC-Verbindung fehlgeschlagen");
            return;
        }
        String[] ip={""};
        String version = "";
        version=robot.GetSDKVersion();
        System.out.println("SDK version : " + version);
        int rtn = robot.GetControllerIP(ip);
        System.out.println("controller ip : " +  ip[0] + "  " + rtn);
        robot.Mode(1); // 1-Handmodus, 0-Automatikmodus
        robot.Sleep(1000);
        robot.DragTeachSwitch(1); // In Ziehemodus wechseln
        robot.Sleep(1000);
        ROBOT_STATE_PKG pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);
        robot.Sleep(1000);
        robot.DragTeachSwitch(0); // Ziehemodus verlassen
        robot.Sleep(1000);
        pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);

        if (pkg.robot_state == 4){
           System.out.println("Im Ziehemodus");
        }else {
           System.out.println("Nicht im Ziehemodus");
        }
    }

Roboter-Softwareversion abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Roboter-Softwareversionsinformationen zurück.
    * @param [out] robotModel Robotermodell (String).
    * @param [out] webVersion Web-Version (String).
    * @param [out] controllerVersion Controller-Version (String).
    * @return Fehlercode.
    */
    int GetSoftwareVersion(String robotModel, String webVersion, String controllerVersion);

Roboter-Hardwareversion abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Roboter-Hardwareversionsinformationen zurück.
    * @param [out] ctrlBoxBoardVersion Hardwareversion der Steuerschrankplatine.
    * @param [out] driver1Version Hardwareversion von Antrieb 1.
    * @param [out] driver2Version Hardwareversion von Antrieb 2.
    * @param [out] driver3Version Hardwareversion von Antrieb 3.
    * @param [out] driver4Version Hardwareversion von Antrieb 4.
    * @param [out] driver5Version Hardwareversion von Antrieb 5.
    * @param [out] driver6Version Hardwareversion von Antrieb 6.
    * @param [out] endBoardVersion Hardwareversion der Endeffektorplatine.
    * @return Fehlercode.
    */
    int GetHardwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Roboter-Firmwareversion abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Roboter-Firmwareversionsinformationen zurück.
    * @param [out] ctrlBoxBoardVersion Firmwareversion der Steuerschrankplatine.
    * @param [out] driver1Version Firmwareversion von Antrieb 1.
    * @param [out] driver2Version Firmwareversion von Antrieb 2.
    * @param [out] driver3Version Firmwareversion von Antrieb 3.
    * @param [out] driver4Version Firmwareversion von Antrieb 4.
    * @param [out] driver5Version Firmwareversion von Antrieb 5.
    * @param [out] driver6Version Firmwareversion von Antrieb 6.
    * @param [out] endBoardVersion Firmwareversion der Endeffektorplatine.
    * @return Fehlercode.
    */
    int GetFirmwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Codebeispiel zum Abrufen von Roboter-Soft-/Firmware-Versionen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//设置重连次数、间隔
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("RPC-Verbindung erfolgreich");
        }
        else
        {
            System.out.println("RPC-Verbindung fehlgeschlagen");
            return;
        }
        String ctrlBoxBoardVersion = "";
        String driver1Version = "";
        String driver2Version = "";
        String driver3Version = "";
        String driver4Version = "";
        String driver5Version = "";
        String driver6Version = "";
        String endBoardVersion = "";
        robot.GetHardwareVersion(ctrlBoxBoardVersion ,driver1Version,  driver2Version,  driver3Version,
                 driver4Version,  driver5Version,  driver6Version,  endBoardVersion);

        robot.GetFirmwareVersion(ctrlBoxBoardVersion, driver1Version, driver2Version, driver3Version,
                driver4Version, driver5Version, driver6Version, endBoardVersion);
    }