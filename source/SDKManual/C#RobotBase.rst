Roboter-Grundlagen
=============================

.. toctree::
    :maxdepth: 5

Roboter instanziieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Konstruktor der Roboter-Schnittstellenklasse.
    */
    Robot();

Kommunikation mit der Steuerung herstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Kommunikation mit der Robotersteuerung her.
    * @param  [in] ip  IP-Adresse der Steuerung, werkseitig Standard 192.168.58.2.
    * @return Fehlercode.
    */
    int RPC(string ip);

Kommunikation mit dem Roboter trennen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Trennt die Kommunikation mit der Robotersteuerung.
    * @return Fehlercode.
    */
    int CloseRPC();

SDK-Version abfragen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Fragt die SDK-Versionsnummer ab.
    * @param [out] version SDK-Versionsnummer.
    * @return Fehlercode.
    */
    int GetSDKVersion(ref string version);

Controller-IP abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Controller-IP zurück.
    * @param [out] ip Controller-IP.
    * @return Fehlercode.
    */
    int GetControllerIP(ref string ip);

Roboter in den Ziehe-Teaching-Modus schalten oder daraus zurückkehren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Schaltet den Roboter in den Ziehe-Teaching-Modus oder zurück.
    * @param [in] state 0-Ziehe-Teaching-Modus verlassen, 1-Ziehe-Teaching-Modus betreten.
    * @return Fehlercode.
    */
    int DragTeachSwitch(byte state);

Abfragen, ob sich der Roboter im Ziehemodus befindet
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Fragt ab, ob sich der Roboter im Ziehe-Teaching-Modus befindet.
    * @param [out] state 0-nicht im Ziehe-Teaching-Modus, 1-im Ziehe-Teaching-Modus.
    * @return Fehlercode.
    */
    int IsInDragTeach(ref byte state);

Roboter aktivieren (Enable) oder deaktivieren (Disable)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Aktiviert oder deaktiviert den Roboter. Nach dem Einschalten ist der Roboter standardmäßig automatisch aktiviert.
    * @param [in] state 0-deaktivieren (Disable), 1-aktivieren (Enable).
    * @return Fehlercode.
    */
    int RobotEnable(byte state);

Umschalten zwischen Hand- und Automatikmodus
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Schaltet zwischen Hand- und Automatikmodus um.
    * @param [in] mode 0-Automatikmodus, 1-Handmodus.
    * @return Fehlercode.
    */
    int Mode(int mode);

Roboter-Betriebssystem herunterfahren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Fährt das Roboter-Betriebssystem herunter.
    * @return Fehlercode.
    */
    int ShutDownRobotOS();

Codebeispiel
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button6_Click(object sender, EventArgs e)
    {
        int rtn = robot.ShutDownRobotOS();
        Console.WriteLine($"ShutDownRobotOS rtn is {rtn}");
    }

Parameter für die automatische Wiederverbindung mit dem Roboter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Parameter für die automatische Wiederverbindung mit dem Roboter ein.
    * @param [in] enable Aktivieren? true-aktivieren, false-deaktivieren.
    * @param [in] times Anzahl der Wiederverbindungsversuche.
    * @param [in] period Zeitintervall zwischen den Wiederverbindungsversuchen (Millisekunden).
    */
    void SetReconnectParam(bool enable, int times, int period);

Codebeispiel
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnStandard_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 20000); // Parameter für Wiederverbindung bei Verbindungsabbruch
        robot.RPC("192.168.58.2");

        string ip = "";
        string version = "";
        byte state = 0;

        robot.GetSDKVersion(ref version);
        Console.WriteLine($"SDK version : {version}");
        robot.GetControllerIP(ref ip);
        Console.WriteLine($"controller ip : {ip}");

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        int rtn = robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.DragTeachSwitch(0);
        Thread.Sleep(1000);
        robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.RobotEnable(0);
        Thread.Sleep(3000);
        robot.RobotEnable(1);

        robot.Mode(0);
        Thread.Sleep(1000);
        robot.Mode(1);
    }

Logging-Parameter initialisieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Initialisiert die Logging-Parameter.
    * @param [in] logType: Ausgabemodus, DIRECT-direkte Ausgabe; BUFFER-gepufferte Ausgabe; ASYNC-asynchrone Ausgabe.
    * @param [in] logLevel: Log-Filterstufe, ERROR-Fehler; WARNING-Warnung; INFO-Information; DEBUG-Debug.
    * @param [in] filePath: Pfad zum Speichern der Dateien, z.B. "D://Log/".
    * @param [in] saveFileNum: Maximale Anzahl der zu speichernden Dateien. Dateien, die sowohl die maximale Anzahl als auch die maximale Aufbewahrungsdauer überschreiten, werden gelöscht.
    * @param [in] saveDays: Maximale Aufbewahrungsdauer in Tagen. Dateien, die sowohl die maximale Anzahl als auch die maximale Aufbewahrungsdauer überschreiten, werden gelöscht.
    * @return Fehlercode.
    */
    int LoggerInit(FrLogType logType = FrLogType.DIRECT, FrLogLevel logLevel = FrLogLevel.INFO, string filePath = "", int saveFileNum = 10, int saveDays = 10);

Log-Filterstufe einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Log-Filterstufe ein.
    * @param [in] logLevel: Log-Filterstufe, ERROR-Fehler; WARNING-Warnung; INFO-Information; DEBUG-Debug.
    * @return Fehlercode.
    */
    int SetLoggerLevel(FrLogLevel logLevel);

Roboter-Softwareversion abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Roboter-Softwareversionsinformationen zurück.
    * @param [out] robotModel Robotermodell.
    * @param [out] webVersion Web-Version.
    * @param [out] controllerVersion Controller-Version.
    * @return Fehlercode.
    */
    int GetSoftwareVersion(ref string robotModel, ref string webVersion, ref string controllerVersion);

Roboter-Hardwareversion abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
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
    int GetHardwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version, ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Roboter-Firmwareversion abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
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
    int GetFirmwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version, ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Codebeispiel
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnGetVersions_Click(object sender, EventArgs e)
    {
        string[] ver = new string[20];
        int rtn = 0;
        rtn = robot.GetSoftwareVersion(ref ver[0], ref ver[1], ref ver[2]);
        rtn = robot.GetHardwareVersion(ref ver[3], ref ver[4], ref ver[5], ref ver[6], ref ver[7], ref ver[8], ref ver[9], ref ver[10]);
        rtn = robot.GetFirmwareVersion(ref ver[11], ref ver[12], ref ver[13], ref ver[14], ref ver[15], ref ver[16], ref ver[17], ref ver[18]);
        Console.WriteLine($"robotmodel  is: {ver[0]}");
        Console.WriteLine($"webVersion  is: {ver[1]}");
        Console.WriteLine($"controllerVersion  is: {ver[2]}");
        Console.WriteLine($"Hard ctrlBox Version  is: {ver[3]}");
        Console.WriteLine($"Hard driver1 Version  is: {ver[4]}");
        Console.WriteLine($"Hard driver2 Version  is: {ver[5]}");
        Console.WriteLine($"Hard driver3 Version  is: {ver[6]}");
        Console.WriteLine($"Hard driver4 Version  is: {ver[7]}");
        Console.WriteLine($"Hard driver5 Version  is: {ver[8]}");
        Console.WriteLine($"Hard driver6 Version  is: {ver[9]}");
        Console.WriteLine($"Hard end Version  is: {ver[10]}");
        Console.WriteLine($"Firm ctrlBox Version  is: {ver[11]}");
        Console.WriteLine($"Firm driver1 Version  is: {ver[12]}");
        Console.WriteLine($"Firm driver2 Version  is: {ver[13]}");
        Console.WriteLine($"Firm driver3 Version  is: {ver[14]}");
        Console.WriteLine($"Firm driver4 Version  is: {ver[15]}");
        Console.WriteLine($"Firm driver5 Version  is: {ver[16]}");
        Console.WriteLine($"Firm driver6 Version  is: {ver[17]}");
        Console.WriteLine($"Firm end Version  is: {ver[18]}");
    }