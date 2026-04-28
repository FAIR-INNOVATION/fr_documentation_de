Roboterperipherie
================================

.. toctree::
    :maxdepth: 5

Greifer konfigurieren
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den Greifer.
    * @param [in] config.company Greiferhersteller, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing.
    * @param [in] config.device Gerätenummer, Robotiq(0-2F-85 Serie), Huiling(0-NK Serie, 1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20).
    * @param [in] config.softvesion Softwareversionsnummer, derzeit nicht verwendet, Standard 0.
    * @param [in] config.bus Position des Geräts am Flanschbus, derzeit nicht verwendet, Standard 0.
    * @return Fehlercode.
    */
    int SetGripperConfig(DeviceConfig config);

Greiferkonfiguration abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Greiferkonfiguration zurück.
    * @param [out] config.company Greiferhersteller.
    * @param [out] config.device Gerätenummer.
    * @param [out] config.softvesion Softwareversionsnummer.
    * @param [out] config.bus Busposition.
    * @return Fehlercode.
    */
    int GetGripperConfig(DeviceConfig config);

Greifer aktivieren
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Aktiviert/Deaktiviert den Greifer.
    * @param [in] index Greifernummer.
    * @param [in] act 0-Reset, 1-Aktivieren.
    * @return Fehlercode.
    */
    int ActGripper(int index, int act);

Greifer steuern
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Steuert den Greifer.
    * @param [in] index Greifernummer.
    * @param [in] pos Positionsprozentsatz, Bereich [0~100].
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100].
    * @param [in] force Kraftprozentsatz, Bereich [0~100].
    * @param [in] max_time Maximale Wartezeit, Bereich [0~30000], Einheit ms.
    * @param [in] block 0-blockierend, 1-nicht blockierend.
    * @param [in] type Greifertyp, 0-Parallelgreifer; 1-Drehgreifer.
    * @param [in] rotNum Anzahl der Umdrehungen.
    * @param [in] rotVel Rotationsgeschwindigkeitsprozentsatz [0-100].
    * @param [in] rotTorque Rotationskraftprozentsatz [0-100].
    * @return Fehlercode.
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, int block, int type, double rotNum, int rotVel, int rotTorque);

Greiferbewegungsstatus abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Bewegungsstatus des Greifers zurück.
    * @return List[0]: Fehlercode; List[1]: fault 0-kein Fehler, 1-Fehler; List[2]: status 0-Bewegung nicht abgeschlossen, 1-Bewegung abgeschlossen.
    */
    List<Integer> GetGripperMotionDone();

Aktivierungsstatus des Greifers abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Aktivierungsstatus des Greifers zurück.
    * @return List[0]: Fehlercode; List[1]: fault 0-kein Fehler, 1-Fehler; List[2]: status Bit0~Bit15 entsprechen Greifernummern 0~15, bit=0 für nicht aktiviert, bit=1 für aktiviert.
    */
    List<Number> GetGripperActivateStatus();

Greiferposition abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Position des Greifers zurück.
    * @return List[0]: Fehlercode; List[1]: fault 0-kein Fehler, 1-Fehler; List[2]: position Positionsprozentsatz, Bereich 0~100%.
    */
    List<Number> GetGripperCurPosition();

Greifergeschwindigkeit abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Geschwindigkeit des Greifers zurück.
    * @return List[0]: Fehlercode; List[1]: fault 0-kein Fehler, 1-Fehler; List[2]: speed Geschwindigkeitsprozentsatz, Bereich 0~100%.
    */
    List<Number> GetGripperCurSpeed();

Greiferstrom abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Strom des Greifers zurück.
    * @return List[0]: Fehlercode; List[1]: fault 0-kein Fehler, 1-Fehler; List[2]: current Stromprozentsatz, Bereich 0~100%.
    */
    List<Number> GetGripperCurCurrent();

Greiferspannung abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Spannung des Greifers zurück.
    * @return List[0]: Fehlercode; List[1]: fault 0-kein Fehler, 1-Fehler; List[2]: voltage Spannung, Einheit 0.1V.
    */
    List<Number> GetGripperVoltage();

Greifertemperatur abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Temperatur des Greifers zurück.
    * @return List[0]: Fehlercode; List[1]: fault 0-kein Fehler, 1-Fehler; List[2]: temp Temperatur, Einheit °C.
    */
    List<Number> GetGripperTemp();

Vorab-Greifpunkt berechnen (Vision)
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Berechnet den Vorab-Greifpunkt (Vision).
    * @param [in] desc_pos Kartesische Pose des Greifpunkts.
    * @param [in] zlength Z-Achsen-Versatz.
    * @param [in] zangle Rotationsversatz um die Z-Achse.
    * @param [out] pre_pos Vorab-Greifpunkt.
    * @return Fehlercode.
    */
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, DescPose pre_pos);

Rückzugspunkt berechnen (Vision)
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Berechnet den Rückzugspunkt (Vision).
    * @param [in] desc_pos Kartesische Pose des Greifpunkts.
    * @param [in] zlength Z-Achsen-Versatz.
    * @param [in] zangle Rotationsversatz um die Z-Achse.
    * @param [out] post_pos Rückzugspunkt.
    * @return Fehlercode.
    */
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, DescPose post_pos);

Codebeispiel für Roboter-Greiferoperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestGripper(Robot robot)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        int act = 0;
        int max_time = 30000;
        int block = 0;

        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        DeviceConfig cnn=new DeviceConfig(company,device,softversion,bus);
        robot.SetGripperConfig(cnn);
        robot.GetGripperConfig(cnn);

        robot.ActGripper(index, act);
        robot.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        robot.Sleep(1000);

        robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
        robot.Sleep(1000);
        robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);

        List<Integer> stat = new ArrayList<>();
        stat = robot.GetGripperMotionDone();

        List<Number> list = new ArrayList<>();
        list = robot.GetGripperActivateStatus();

        list = robot.GetGripperCurPosition();

        list = robot.GetGripperCurCurrent();

        list = robot.GetGripperVoltage();

        list = robot.GetGripperTemp();

        list = robot.GetGripperCurSpeed();

        int retval = 0;
        DescPose prepick_pose = new DescPose();
        DescPose postpick_pose = new DescPose();

        DescPose p1Desc = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        retval = robot.ComputePrePick(p1Desc, 10, 0, prepick_pose);

        retval = robot.ComputePostPick(p2Desc, -10, 0, postpick_pose);
        return 0;
    }

Umdrehungen des Drehgreifers abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Anzahl der Umdrehungen des Drehgreifers zurück.
    * @return List[0]: Fehlercode; List[1]: 0-kein Fehler, 1-Fehler; List[2]: Anzahl der Umdrehungen.
    */
    List<Number> GetGripperRotNum();

Rotationsgeschwindigkeit des Drehgreifers (Prozent) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Rotationsgeschwindigkeitsprozentsatz des Drehgreifers zurück.
    * @return List[0]: Fehlercode; List[1]: 0-kein Fehler, 1-Fehler; List[2]: Rotationsgeschwindigkeitsprozentsatz.
    */
    List<Number> GetGripperRotSpeed();

Rotationskraft des Drehgreifers (Prozent) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Rotationskraftprozentsatz des Drehgreifers zurück.
    * @return List[0]: Fehlercode; List[1]: 0-kein Fehler, 1-Fehler; List[2]: Rotationskraftprozentsatz.
    */
    List<Number> GetGripperRotTorque();

Codebeispiel zum Abrufen des Drehgreiferstatus
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestRotGripperState(Robot robot)
    {
        int fault = 0;
        List<Number> rotNum=new ArrayList<>();
        List<Number> rotSpeed=new ArrayList<>();
        List<Number> rotTorque=new ArrayList<>();

        rotNum=robot.GetGripperRotNum();
        rotSpeed=robot.GetGripperRotSpeed();
        rotTorque=robot.GetGripperRotTorque();
        System.out.println("gripper rot num :"+rotNum.get(2)+ ", gripper rotSpeed :"+rotSpeed.get(2)+",gripper rotTorque : "+rotTorque.get(2));

        return 0;
    }

Förderband starten/stoppen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet oder stoppt das Förderband.
    * @param [in] status Status, 1-starten, 0-stoppen.
    * @return Fehlercode.
    */
    int ConveyorStartEnd(int status);

IO-Erkennungspunkt aufzeichnen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Zeichnet einen IO-Erkennungspunkt auf.
    * @return Fehlercode.
    */
    int ConveyorPointIORecord();

Punkt A aufzeichnen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Zeichnet Punkt A auf.
    * @return Fehlercode.
    */
    int ConveyorPointARecord();

Referenzpunkt aufzeichnen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Zeichnet einen Referenzpunkt auf.
    * @return Fehlercode.
    */
    int ConveyorRefPointRecord();

Punkt B aufzeichnen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Zeichnet Punkt B auf.
    * @return Fehlercode.
    */
    int ConveyorPointBRecord();

Werkstückerkennung über IO am Förderband
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Werkstückerkennung über IO am Förderband.
    * @param [in] max_t Maximale Erkennungszeit, Einheit ms.
    * @return Fehlercode.
    */
    int ConveyorIODetect(int max_t);

Aktuelle Position des Objekts abrufen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die aktuelle Position des Objekts zurück.
    * @param [in] mode 1-Tracking Greifen, 2-Tracking Bewegung, 3-TPD Tracking.
    * @return Fehlercode.
    */
    int ConveyorGetTrackData(int mode);

Förderband-Tracking starten
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet das Förderband-Tracking.
    * @param [in] status Status, 1-starten, 0-stoppen.
    * @return Fehlercode.
    */
    int ConveyorTrackStart(int status);

Förderband-Tracking stoppen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stoppt das Förderband-Tracking.
    * @return Fehlercode.
    */
    int ConveyorTrackEnd();

Förderbandparameter konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.4-3.8.1

.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert die Parameter des Förderbands.
    * @param [in] encChannel Encoderkanal 1~2.
    * @param [in] resolution Impulse pro Encoderumdrehung.
    * @param [in] lead Vorschub pro Encoderumdrehung.
    * @param [in] wpAxis Werkstückkoordinatensystem-Nummer (für Tracking-Bewegung), für Tracking-Greifen und TPD-Tracking auf 0 setzen.
    * @param [in] vision Vision vorhanden? 0-nein, 1-ja.
    * @param [in] speedRadio Geschwindigkeitsverhältnis (für Tracking-Greifen 1-100), sonst Standard 1.
    * @param [in] followType Tracking-Bewegungstyp, 0-Tracking-Bewegung; 1-Nachverfolgungsbewegung.
    * @param [in] startDis Startabstand für Nachverfolgung (mm), -1: automatische Berechnung, Standard 0.
    * @param [in] endDis Endabstand für Nachverfolgung (mm), Standard 100.
    * @return Fehlercode.
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis, int endDis);

Greifpunktkompensation für Förderband einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Kompensation für den Greifpunkt am Förderband ein.
    * @param [in] cmp Kompensationsposition double[3]{x, y, z}.
    * @return Fehlercode.
    */
    int ConveyorCatchPointComp(Object[] cmp);

Linearbewegung mit Förderband-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Linearbewegung mit Förderband-Tracking.
    * @param [in] name Punktbeschreibung.
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14].
    * @param [in] wobj Werkstückkoordinatennummer, Bereich [0~14].
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100].
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm.
    * @return Fehlercode.
    */
    int ConveyorTrackMoveL(String name, int tool, int wobj, double vel, double acc, double ovl, double blendR);

Förderband-Kommunikationseingang prüfen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: java
    :linenos:

    /**
    * @brief Prüft den Kommunikationseingang des Förderbands.
    * @param [in] timeout Warte-Timeout (ms).
    * @return Fehlercode.
    */
    int ConveyorComDetect(int timeout);

Förderband-Kommunikationseingang prüfen (Trigger)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: java
    :linenos:

    /**
    * @brief Löst die Prüfung des Kommunikationseingangs des Förderbands aus.
    * @param [in] timeout Warte-Timeout (ms).
    * @return Fehlercode.
    */
    int ConveyorComDetectTrigger();

Beispielprogramm für Roboter-Förderbandoperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestConveyor(Robot robot)
    {
        int retval = 0;

        retval = robot.ConveyorStartEnd(1);

        retval = robot.ConveyorPointIORecord();

        retval = robot.ConveyorPointARecord();

        retval = robot.ConveyorRefPointRecord();

        retval = robot.ConveyorPointBRecord();

        retval = robot.ConveyorStartEnd(0);

        retval = 0;

        retval = robot.ConveyorSetParam(1,10000,200,0,0,20,0,0,100);

        Object[] cmp = new Object[]{ 0.0, 0.0, 0.0 };
        retval = robot.ConveyorCatchPointComp(cmp);

        int index = 1;
        int max_time = 30000;
        int block = 0;
        retval = 0;

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);


        retval = robot.MoveCart(p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.WaitMs(1);

        retval = robot.ConveyorTrackStart(1);

        retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);

        retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.ConveyorTrackEnd();

        robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);

        return 0;
    }

Endeffektor-Sensor konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den Sensor am Endeffektor.
    * @param [in] config.idCompany Hersteller, 18-JUNKONG; 25-HUIDE.
    * @param [in] config.idDevice Typ, 0-JUNKONG/RYR6T.V1.0.
    * @param [in] config.idSoftware Softwareversion, 0-J1.0/HuiDe1.0 (noch nicht verfügbar).
    * @param [in] config.idBus Montageposition, 1-Endeffektor Port 1; 2-Port 2...8-Port 8 (noch nicht verfügbar).
    * @return Fehlercode.
    */
    int AxleSensorConfig(DeviceConfig config);

Endeffektor-Sensorkonfiguration abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Konfiguration des Endeffektor-Sensors zurück.
    * @param [out] config.idCompany Hersteller.
    * @param [out] config.idDevice Typ.
    * @return Fehlercode.
    */
    int AxleSensorConfigGet(DeviceConfig config);

Endeffektor-Sensor aktivieren
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Aktiviert/Deaktiviert den Endeffektor-Sensor.
    * @param [in] actFlag 0-Reset; 1-Aktivieren.
    * @return Fehlercode.
    */
    int AxleSensorActivate(int actFlag);

In Endeffektor-Sensorregister schreiben
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schreibt in die Register des Endeffektor-Sensors.
    * @param [in] devAddr Geräteadresse 0-255.
    * @param [in] regHAddr Registeradresse höherwertiges Byte.
    * @param [in] regLAddr Registeradresse niederwertiges Byte.
    * @param [in] regNum Anzahl der Register 0-255.
    * @param [in] data1 Zu schreibender Wert 1.
    * @param [in] data2 Zu schreibender Wert 2.
    * @param [in] isNoBlock 0-blockierend; 1-nicht blockierend.
    * @return Fehlercode.
    */
    int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Codebeispiel für Endeffektor-Sensor
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestAxleSensor(Robot robot)
    {
        DeviceConfig con=new DeviceConfig(18,0,0,1);
        robot.AxleSensorConfig(con);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(con);

        int rtn = robot.AxleSensorActivate(1);

        robot.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        return 0;
    }

Roboter-Peripherieprotokoll abrufen
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt das Roboter-Peripherieprotokoll zurück.
    * @return List[0]: Fehlercode; List[1]: int protocol Robot-Peripherieprotokollnummer 4096-Erweiterungsachsen-Steuerkarte; 4097-ModbusSlave; 4098-ModbusMaster.
    */
    List<Integer> GetExDevProtocol();

Roboter-Peripherieprotokoll einstellen
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt das Roboter-Peripherieprotokoll ein.
    * @param [in] protocol Robot-Peripherieprotokollnummer 4096-Erweiterungsachsen-Steuerkarte; 4097-ModbusSlave; 4098-ModbusMaster.
    * @return Fehlercode.
    */
    int SetExDevProtocol(int protocol);

Beispielprogramm zum Einstellen des Roboter-Peripherieprotokolls
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestExDevProtocol(Robot robot)
    {
        int protocol = 4096;
        int rtn = robot.SetExDevProtocol(protocol);
        List<Integer> integer=new ArrayList<>();
        integer = robot.GetExDevProtocol();

        return 0;
    }

Endeffektor-Kommunikationsparameter abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Kommunikationsparameter des Endeffektors zurück.
    * @param [out] param Endeffektor-Kommunikationsparameter.
    * @return Fehlercode.
    */
    int GetAxleCommunicationParam(AxleComParam param);

Endeffektor-Kommunikationsparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Kommunikationsparameter des Endeffektors ein.
    * @param [in] param Endeffektor-Kommunikationsparameter.
    * @return Fehlercode.
    */
    int SetAxleCommunicationParam(AxleComParam param);

Endeffektor-Dateiübertragungstyp einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt den Dateiübertragungstyp für den Endeffektor ein.
    * @param [in] type 1-MCU Upgrade Datei; 2-LUA Datei.
    * @return Fehlercode.
    */
    public int SetAxleFileType(int type);

Endeffektor-LUA-Ausführung aktivieren/deaktivieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Aktiviert/deaktiviert die LUA-Ausführung am Endeffektor.
    * @param [in] enable 0-deaktivieren; 1-aktivieren.
    * @return Fehlercode.
    */
    public int SetAxleLuaEnable(int enable);

Fehlerbehebung bei fehlerhafter Endeffektor-LUA-Datei
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Fehlerbehebung bei fehlerhafter Endeffektor-LUA-Datei.
    * @param [in] status 0-nicht beheben; 1-beheben.
    * @return Fehlercode.
    */
    public int SetRecoverAxleLuaErr(int status);

Aktivierungsstatus der Endeffektor-LUA-Ausführung abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Aktivierungsstatus der Endeffektor-LUA-Ausführung zurück.
    * @param [out] status[0]: 0-nicht aktiviert; 1-aktiviert.
    * @return Fehlercode.
    */
    int GetAxleLuaEnableStatus(int[] status);

Aktivierungstypen für Endeffektor-LUA-Geräte einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Aktivierungstypen für Endeffektor-LUA-Geräte ein.
    * @param forceSensorEnable Aktivierungsstatus Kraftsensor, 0-deaktivieren; 1-aktivieren.
    * @param gripperEnable Aktivierungsstatus Greifer, 0-deaktivieren; 1-aktivieren.
    * @param IOEnable Aktivierungsstatus IO-Gerät, 0-deaktivieren; 1-aktivieren.
    * @return Fehlercode.
    */
    public int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable);

Aktivierungstypen für Endeffektor-LUA-Geräte abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
     * @brief Gibt die Aktivierungstypen für Endeffektor-LUA-Geräte zurück.
     * @param enable enable[0]: forceSensorEnable Aktivierungsstatus Kraftsensor, 0-deaktivieren; 1-aktivieren.
     * @param enable enable[1]: gripperEnable Aktivierungsstatus Greifer, 0-deaktivieren; 1-aktivieren.
     * @param enable enable[2]: IOEnable Aktivierungsstatus IO-Gerät, 0-deaktivieren; 1-aktivieren.
     * @return Fehlercode.
     */
    public int GetAxleLuaEnableDeviceType(int[] enable);

Aktuell konfigurierte Endeffektor-Geräte abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
     * @brief Gibt die aktuell konfigurierten Endeffektor-Geräte zurück.
     * @param forceSensorEnable Aktivierte Kraftsensor-Gerätenummern (Array).
     * @param gripperEnable Aktivierte Greifer-Gerätenummern (Array).
     * @param IODeviceEnable Aktivierte IO-Gerätenummern (Array).
     * @return Fehlercode.
     */
    public int GetAxleLuaEnableDevice(int[] forceSensorEnable, int[] gripperEnable, int[] IODeviceEnable);

Greifer-Aktionssteuerungsfunktionen aktivieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
     * @brief Aktiviert die Greifer-Aktionssteuerungsfunktionen für LUA.
     * @param id Greifer-Gerätenummer.
     * @param func func[0]-Greifer aktivieren; func[1]-Greifer initialisieren; 2-Position setzen; 3-Geschwindigkeit setzen; 4-Kraft setzen; 6-Greiferstatus lesen; 7-Initialisierungsstatus lesen; 8-Fehlercode lesen; 9-Position lesen; 10-Geschwindigkeit lesen; 11-Kraft lesen.
     * @return Fehlercode.
     */
    public int SetAxleLuaGripperFunc(int id, int[] func);

Aktivierte Greifer-Aktionssteuerungsfunktionen abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
     * @brief Gibt die aktivierten Greifer-Aktionssteuerungsfunktionen für LUA zurück.
     * @param id Greifer-Gerätenummer.
     * @param func func[0]-Greifer aktivieren; func[1]-Greifer initialisieren; 2-Position setzen; 3-Geschwindigkeit setzen; 4-Kraft setzen; 6-Greiferstatus lesen; 7-Initialisierungsstatus lesen; 8-Fehlercode lesen; 9-Position lesen; 10-Geschwindigkeit lesen; 11-Kraft lesen.
     * @return Fehlercode.
     */
    public int GetAxleLuaGripperFunc(int id, int[] func);

Roboter-Ethercat-Slave-Datei schreiben
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
     * @brief Schreibt eine Datei in einen Roboter-Ethercat-Slave.
     * @param type Slave-Dateityp, 1-Slave-Upgrade-Datei; 2-Slave-Konfigurationsdatei-Upgrade.
     * @param slaveID Slave-Nummer.
     * @param fileName Name der hochzuladenden Datei.
     * @return Fehlercode.
     */
    public int SlaveFileWrite(int type, int slaveID, String fileName);

Endeffektor-Lua-Open-Protocol-Datei hochladen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
     * @brief Lädt eine Endeffektor-Lua-Open-Protocol-Datei hoch.
     * @param filePath Lokaler Pfad der Lua-Datei ".../AXLE_LUA_End_DaHuan.lua".
     * @return Fehlercode.
     */
    public int AxleLuaUpload(String filePath);

Roboter-Ethercat-Slave in den Boot-Modus versetzen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
     * @brief Versetzt den Roboter-Ethercat-Slave in den Boot-Modus.
     * @return Fehlercode.
     */
    public int SetSysServoBootMode();

Codebeispiel für Roboter-Endeffektor-LUA-Dateioperationen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestAxleLua(Robot robot)
    {
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");

        AxleComParam param=new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        robot.GetAxleCommunicationParam(param);

        robot.SetAxleLuaEnable(1);
        int[] luaEnableStatus = new int[]{0};
        robot.GetAxleLuaEnableStatus(luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int [] enable=new int[]{0,0,0};
        robot.GetAxleLuaEnableDeviceType(enable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
        robot.SetAxleLuaGripperFunc(1, func);
        int[] getFunc = { 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0};
        robot.GetAxleLuaGripperFunc(1, getFunc);
        int[] getforceEnable = { 0,0,0,0,0,0,0,0};
        int[] getgripperEnable = { 0,0,0,0,0,0,0,0};
        int[] getioEnable = { 0,0,0,0,0,0,0,0};
        robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable);
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getforceEnable[i]);
        }
        System.out.println("getgripperEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getgripperEnable[i]);
        }
        System.out.println("getioEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getioEnable[i]);
        }
        robot.ActGripper(1, 0);
        robot.Sleep(2000);
        robot.ActGripper(1, 1);
        robot.Sleep(2000);
        robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
            pkg=robot.GetRobotRealTimeState();
            System.out.println("gripper pos is:"+pkg.gripper_position);
            robot.Sleep(100);
        }

    }

SmartTool-Tastenstatus abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Status der SmartTool-Tasten zurück.
    * @param [out] state SmartTool-Griff-Tastenstatus; (bit0:0-Kommunikation normal; 1-Kommunikation unterbrochen; bit1-Widerrufen; bit2-Programm löschen; bit3-Taste A; bit4-Taste B; bit5-Taste C; bit6-Taste D; bit7-Taste E; bit8-IO-Taste; bit9-Hand/Auto; bit10-Start).
    * @return Fehlercode.
    */
    int GetSmarttoolBtnState(int[] state);

Codebeispiel für SmartTool-Tasten
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 500);
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn == 0) {
            System.out.println("rpc Verbindung erfolgreich");
        } else {
            System.out.println("rpc Verbindung fehlgeschlagen");
            return;
        }

        int[] state = {0};
        while (true)
        {
            robot.GetSmarttoolBtnState(state);

            String binaryString = String.format("%32s", Integer.toBinaryString(state[0])).replace(' ', '0');
            System.out.println("GetSmarttoolBtnState:"+binaryString);
            robot.Sleep(100);
        }
    }

Open-Protocol-Lua-Datei hochladen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Lädt eine Open-Protocol-Lua-Datei hoch.
    * @param filePath Lokaler Pfad der Open-Protocol-Lua-Datei.
    * @return Fehlercode.
    */
    public int OpenLuaUpload(String filePath);

Feldbus-Slave-Kartenparameter abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Parameter der Feldbus-Slave-Karte zurück.
    * @param type 0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP.
    * @param version Protokollversion.
    * @param connState 0-nicht verbunden, 1-verbunden.
    * @return Fehlercode.
    */
    public int GetFieldBusConfig(int[] type, int[] version, int[] connState);

In Slave-DO schreiben
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Schreibt in die digitalen Ausgänge des Slaves.
    * @param DOIndex DO-Index.
    * @param writeNum Anzahl der zu schreibenden Werte.
    * @param status Array der zu schreibenden Werte (max. 8).
    * @return Fehlercode.
    */
    public int FieldBusSlaveWriteDO(int DOIndex, int writeNum, int[] status);

In Slave-AO schreiben
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /*
    * @brief  In Slave-AO schreiben
    * @param  AOIndex AO-Nummer
    * @param  writeNum Anzahl der zu schreibenden Werte
    * @param  status Array der zu schreibenden Werte (maximal 8), AO0~AO15 sind ganzzahlig, AO16~AO31 sind Gleitkommawerte
    * @return  Fehlercode
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int writeNum, double[] status)

Slave-DI lesen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Liest die digitalen Eingänge des Slaves.
    * @param DOIndex DI-Index.
    * @param readNum Anzahl der zu lesenden Werte.
    * @param status Array zum Speichern der gelesenen Werte (max. 8).
    * @return Fehlercode.
    */
    public int FieldBusSlaveReadDI(int DOIndex, int readNum, int[] status);

Slave-AI lesen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Liest die analogen Eingänge des Slaves.
    * @param AIIndex AI-Index.
    * @param readNum Anzahl der zu lesenden Werte.
    * @param status Array zum Speichern der gelesenen Werte (max. 8).
    * @return Fehlercode.
    */
    public int FieldBusSlaveReadAI(int AIIndex, int readNum, double[] status);

Auf Slave-DI warten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen digitalen Eingang des Slaves.
    * @param DIIndex DI-Index.
    * @param status 0-niedriger Pegel; 1-hoher Pegel.
    * @param waitMs Maximale Wartezeit (ms).
    * @return Fehlercode.
    */
    public int FieldBusSlaveWaitDI(int DIIndex, int status, int waitMs);

Auf Slave-AI warten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen analogen Eingang des Slaves.
    * @param AIIndex AI-Index.
    * @param waitType 0-größer als; 1-kleiner als.
    * @param value AI-Wert.
    * @param waitMs Maximale Wartezeit (ms).
    * @return Fehlercode.
    */
    public int FieldBusSlaveWaitAI(int AIIndex, int waitType, double value, int waitMs);

Codebeispiel für Feldbus-Slave-Kartenoperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void testFieldBusBoard(Robot robot)
    {
        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("D://zUP/1111/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);
        int[] type = new int[1];
        int[] version = new int[1];
        int[] connState = new int[1];
        // Protokolltyp, Softwareversion und Verbindungsstatus der Slave-Karte abrufen
        robot.GetFieldBusConfig(type, version, connState);
        System.out.println("type is: "+type[0]+", version is : "+version[0]+", connState is : "+connState[0]);
        //DO0 = 1、DO1 = 0、DO2 = 1
        int[] ctrl =new int[8];
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);
        //AO2 = 0x1000
        int[] ctrlAO =new int[8];
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);
        int[] DI = new int[4];
        double[] AI = new double[3];
        // DI0~DI3 und AI0~AI2 zyklisch überwachen
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            System.out.println("DI0 is: "+DI[0]+", DI1 is: "+DI[1]+",DI2 is: "+DI[2]+",DI3 is: "+DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            System.out.println("AI0 is: "+AI[0]+ ",AI1 is: "+AI[1]+",AI2 is: "+AI[2]);
            robot.Sleep(10);
        }
        // Auf DI0 = 1 warten, maximal 100 ms warten, Ergebnis ausgeben
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        System.out.println("FieldBusSlaveWaitDI result is: " + ret);
        // Auf AI0 > 400 warten, maximal 100 ms warten, Ergebnis ausgeben
        ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00, 100);
        System.out.println("FieldBusSlaveWaitAI result is: " + ret);
        robot.CloseRPC();
    }

Array-Saugnapf steuern
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Steuert einen Array-Saugnapf.
    * @param slaveID Slave-Adresse.
    * @param len Länge des Steuerarrays.
    * @param ctrlValue Steuerwerte: 1-Saugen mit maximalem Vakuum; 2-Saugen mit eingestelltem Vakuum; 3-Saugen stoppen.
    * @return Fehlercode.
    */
    public int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue);

Array-Saugnapfstatus abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Status eines Array-Saugnapfs zurück.
    * @param slaveID Slave-Adresse.
    * @param state [out] Saugstatus: 0-Objekt losgelassen; 1-Werkstück erkannt, angesaugt; 2-kein Objekt angesaugt; 3-Objekt abgelöst.
    * @param pressValue [out] Aktuelles Vakuum (kPa).
    * @param error [out] Fehlercode des Saugnapfs.
    * @return Fehlercode.
    */
    public int GetSuckerState(int slaveID, int[] state, int[] pressValue, int[] error);

Auf Saugnapfstatus warten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen bestimmten Saugnapfstatus.
    * @param slaveID Slave-Adresse.
    * @param state Erwarteter Saugstatus.
    * @param ms Maximale Wartezeit (ms).
    * @return Fehlercode.
    */
    public int WaitSuckerState(int slaveID, int state, int ms);

Codebeispiel für Array-Saugnapf-Steuerung
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void testSucker(Robot robot)
    {
        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("C：//Projekt/Peripherie-SDK/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);
        // Alle Saugnäpfe im Broadcast-Modus mit maximaler Kraft saugen lassen
        int[] ctrl = {1};
        robot.SetSuckerCtrl(0, 1, ctrl);
        int[] state = new int[1];
        int[] pressValue = new int[1];
        int[] error = new int[1];
        // Status von Saugnapf 1 und 12 überwachen
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, state,pressVlaue, error);
            System.out.println("sucker1 state is:"+state[0]+",pressVlaue is:"+pressVlaue[0]+",error num is"+error[0]);
            robot.GetSuckerState(12, state, pressVlaue, error);
            System.out.println("sucker12 state is :"+state[0]+", pressVlaue is:"+pressVlaue[0]+",error num is:"+error[0]);
            robot.Sleep(100);
        }
        // Auf Status "angesaugt" (1) von Saugnapf 1 warten, maximal 100 ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        System.out.println("WaitSuckerState result is:" + ret);
        // Saugnäpfe 1 und 12 im Unicast-Modus ausschalten
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);
        robot.CloseRPC();
    }

Laserperipherie ein-/ausschalten
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Schaltet die Laserperipherie ein oder aus.
     * @param [in] OnOff 0-ausschalten, 1-einschalten.
     * @param [in] weldId Schweißnaht-ID, Standard 0.
     * @return Fehlercode.
     */
    public int LaserTrackingLaserOnOff(int OnOff, int weldId);

Laser-Tracking starten/beenden
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Startet oder beendet das Laser-Tracking.
     * @param [in] OnOff 0-beenden, 1-starten.
     * @param [in] coordId Werkzeugkoordinaten-Nummer der Laserperipherie.
     * @return Fehlercode.
     */
    public int LaserTrackingTrackOnOff(int OnOff, int coordId);

Laser-Positionssuche - feste Richtung
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Laser-Positionssuche in einer festen Richtung.
     * @param [in] direction 0-x+, 1-x-, 2-y+, 3-y-, 4-z+, 5-z-.
     * @param [in] vel Geschwindigkeit (%).
     * @param [in] distance Maximale Suchstrecke (mm).
     * @param [in] timeout Such-Timeout (ms).
     * @param [in] posSensorNum Nummer des kalibrierten Lasersensor-Werkzeugs.
     * @return Fehlercode.
     */
    public int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum);

Laser-Positionssuche - beliebige Richtung
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Laser-Positionssuche in einer beliebigen Richtung.
     * @param [in] directionPoint XYZ-Koordinaten des Richtungspunkts.
     * @param [in] vel Geschwindigkeit (%).
     * @param [in] distance Maximale Suchstrecke (mm).
     * @param [in] timeout Such-Timeout (ms).
     * @param [in] posSensorNum Nummer des kalibrierten Lasersensor-Werkzeugs.
     * @return Fehlercode.
     */
    public int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum);

Laser-Positionssuche beenden
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
   :linenos:

   /**
    * @brief Beendet die Laser-Positionssuche.
    * @return Fehlercode.
    */
    public int LaserTrackingSearchStop();

Laser-IP konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
   :linenos:

    /**
     * @brief Konfiguriert die IP-Adresse des Lasersensors.
     * @param [in] ip IP-Adresse des Lasersensors.
     * @param [in] port Portnummer des Lasersensors.
     * @return Fehlercode.
     */
    public int LaserTrackingSensorConfig(String ip, int port);

Abtastperiode des Lasersensors konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Konfiguriert die Abtastperiode des Lasersensors.
     * @param [in] period Abtastperiode (ms).
     * @return Fehlercode.
     */
    public int LaserTrackingSensorSamplePeriod(int period);

Lasersensor-Treiber laden
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Lädt den Treiber für den Lasersensor.
     * @param [in] type Protokolltyp des Treibers: 101-Ruiniu, 102-Chuangxiang, 103-Quanshi, 104-Tongzhou, 105-Aotai.
     * @return Fehlercode.
     */
    public int LoadPosSensorDriver(int type);

Lasersensor-Treiber entladen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Entlädt den Treiber für den Lasersensor.
     * @return Fehlercode.
     */
    public int UnLoadPosSensorDriver();

Laser-Schweißnaht-Trajektorie aufzeichnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Zeichnet die Laser-Schweißnaht-Trajektorie auf.
     * @param [in] status 0-Aufzeichnung stoppen, 1-Echtzeit-Tracking, 2-Aufzeichnung starten.
     * @param [in] delayTime Verzögerungszeit (ms).
     * @return Fehlercode.
     */
    public int LaserSensorRecord1(int status, int delayTime);

Laser-Schweißnaht-Trajektorie wiedergeben
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Gibt die aufgezeichnete Laser-Schweißnaht-Trajektorie wieder.
     * @param [in] delayTime Verzögerungszeit (ms).
     * @param [in] speed Geschwindigkeit (%).
     * @return Fehlercode.
     */
    public int LaserSensorReplay(int delayTime, double speed);

Laser-Tracking-Wiedergabe (MoveLTR)
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Führt die Laser-Tracking-Wiedergabe aus.
     * @return Fehlercode.
     */
    public int MoveLTR();

Laser-Schweißnaht-Trajektorie aufzeichnen und wiedergeben (erweitert)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
    * @brief Zeichnet eine Laser-Schweißnaht-Trajektorie auf und gibt sie wieder (erweiterte Parameter).
    * @param delayMode Modus 0-Verzögerungszeit, 1-Verzögerungsstrecke.
    * @param delayTime Verzögerungszeit (ms).
    * @param delayDisExAxisNum Nummer der Erweiterungsachse für Verzögerungsstrecke.
    * @param delayDis Verzögerungsstrecke (mm).
    * @param sensitivePara Empfindlichkeitskoeffizient für Kompensation.
    * @param trackMode Tracking-Typ. 0-Asynchrone Bewegung der Erweiterungsachse; 1-Roboter.
    * @param triggerMode Auslösemodus für Tracking. 0-Tracking-Dauer; 1-IO.
    * @param runTime Dauer des Robotertrackings (s).
    * @param speed Geschwindigkeit (%).
    * @return Fehlercode.
    */
    public int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed);

Zum Startpunkt der aufgezeichneten Laser-Schweißnaht bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Bewegt den Roboter zum Startpunkt der aufgezeichneten Laser-Schweißnaht.
     * @param [in] moveType 0-PTP, 1-LIN.
     * @param [in] ovl Geschwindigkeit (%).
     * @return Fehlercode.
     */
    public int MoveToLaserRecordStart(int moveType, double ovl);

Zum Endpunkt der aufgezeichneten Laser-Schweißnaht bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Bewegt den Roboter zum Endpunkt der aufgezeichneten Laser-Schweißnaht.
     * @param [in] moveType 0-PTP, 1-LIN.
     * @param [in] ovl Geschwindigkeit (%).
     * @return Fehlercode.
     */
    public int MoveToLaserRecordEnd(int moveType, double ovl);

Zum Laser-Suchpunkt (SeamPos) bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Bewegt den Roboter zum vom Laser gefundenen Schweißnahtpunkt (SeamPos).
     * @param [in] moveFlag Bewegungstyp: 0-PTP; 1-LIN.
     * @param [in] ovl Geschwindigkeitsskalierungsfaktor (0-100).
     * @param [in] dataFlag Auswahl der Schweißnaht-Cachedaten: 0-Planungsdaten; 1-Aufzeichnungsdaten.
     * @param [in] plateType Plattentyp: 0-Wellblech; 1-Trapezblech; 2-Zaunblech; 3-Ölfass; 4-Wellpappenstahl.
     * @param [in] trackOffectType Versatztyp für Lasersensor: 0-kein Versatz; 1-Basiskoordinaten-Versatz; 2-Werkzeugkoordinaten-Versatz; 3-Versatz basierend auf Laserrohdaten.
     * @param [in] offset Versatzwert.
     * @return Fehlercode.
     */
    public int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset);

Koordinaten des Laser-Suchpunkts (SeamPos) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
    :linenos:

    /**
     * @brief Gibt die Koordinaten des vom Laser gefundenen Schweißnahtpunkts (SeamPos) zurück.
     * @param [in] trackOffectType Versatztyp für Lasersensor: 0-kein Versatz; 1-Basiskoordinaten-Versatz; 2-Werkzeugkoordinaten-Versatz; 3-Versatz basierend auf Laserrohdaten.
     * @param [in] offset Versatzwert.
     * @param [out] jPos Gelenkposition [°].
     * @param [out] descPos Kartesische Position [mm].
     * @param [out] tool Werkzeugkoordinatensystem-Nummer.
     * @param [out] user Werkstückkoordinatensystem-Nummer.
     * @param [out] exaxis Position der Erweiterungsachse [mm].
     * @return Fehlercode.
     */
    public int GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos jPos, DescPose descPos, int[] tool, int[] user, ExaxisPos exaxis);

Codebeispiel für Lasersensor-Konfiguration und -Test
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void testLaserConfig(Robot robot)
    {
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);

        robot.LaserTrackingSensorSamplePeriod(20);

        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0,0);

        robot.Sleep(3000);

        robot.LaserTrackingLaserOnOff(1, 0);

        robot.CloseRPC();
    }

Codebeispiel für Laser-Trajektorienaufzeichnung und -wiedergabe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void testLaserRecordAndReplay(Robot robot)
    {
        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);

        for (int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos=new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose=new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1,0, exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(0, 10);

            robot.MoveToLaserRecordStart(1, 30);

            robot.LaserSensorReplay(10, 100);

            robot.MoveLTR();

            robot.LaserSensorRecord1(0, 10);
        }

        robot.CloseRPC();
    }

Codebeispiel für Laser-Positionssuche und Echtzeit-Tracking
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void testLasertrack(Robot robot)
    {
        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        for(int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint=new DescTran();
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();

            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);

            robot.LaserTrackingTrackOnOff(1, 3);
            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese, 0, 1, 1);

            robot.LaserTrackingTrackOnOff(0, 3);
            System.out.println("Durchlauf: " + (i + 1));
        }
        robot.CloseRPC();
    }

Codebeispiel für Laser-Tracking mit synchronisierter Erweiterungsachse
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void testLasertrackandExitAxis(Robot robot)
    {
        ExaxisPos startexaxisPos = new ExaxisPos(0, 0, 0, 0);
        ExaxisPos seamexaxisPos = new ExaxisPos(-10, 0, 0, 0);
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        JointPos seamjointPos = new JointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose = new DescPose(0, 0, 0, 0, 0, 0);

        for (int i = 0; i < 10; ++i) {
            // Bewegung zum Startpunkt der Positionssuche
            JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            System.out.println("11111");
            // Positionssuche in -y Richtung starten
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            System.out.println("2222");
            int[] tool = new int[1];
            int[] user = new int[1];
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            System.out.println(seamjointPos.J1 + ", " + seamjointPos.J2 + ", " +
                    seamjointPos.J3 + ", " + seamjointPos.J4 + ", " +
                    seamjointPos.J5 + ", " + seamjointPos.J6 + ", " +
                    seamdescPose.tran.x + ", " + seamdescPose.tran.y + ", " +
                    seamdescPose.tran.z + ", " + seamdescPose.rpy.rx + ", " +
                    seamdescPose.rpy.ry + ", " + seamdescPose.rpy.rz);
            // Wenn die Positionssuche erfolgreich war
            if (ret == 0) {
                // Roboter und Erweiterungsachse synchron zum Suchpunkt bewegen
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                // Laser-Tracking starten und synchron mit Erweiterungsachse bewegen
                System.out.println("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);

                // Tracking stoppen
                robot.LaserTrackingTrackOnOff(0, 2);
                System.out.println("44444");
            }
            System.out.println("Durchlauf: " + i);
        }
        robot.CloseRPC();
    }

Endeffektor-Transparentübertragungsfunktion ein-/ausschalten SDK-Schnittstelle
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktiviert die allgemeine Transparentübertragungsfunktion des Endeffektors
    * @param Aktivierung, 0-deaktiviert, 1-aktiviert
    * @return Fehlercode
    */
    public int SetAxleGenComEnable(int mode)

Endeffektor-Transparentübertragungsfunktion für azyklische Datenübertragung und -empfang SDK-Schnittstelle
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Endeffektor sendet azyklische Daten und wartet auf Antwort
    * @param lenSnd Länge der zu sendenden Daten
    * @param sndBuff Zu sendende Daten
    * @param lenRcv Länge der zu empfangenden Daten
    * @param [out] rcvData Antwortdaten
    * @return Fehlercode
    */
    public int SndRcvAxleGenComCmdData(int lenSnd, int[] sndBuff, int lenRcv, int[] rcvData)
    
Codebeispiel für azyklische Datenkommunikation des DIO Health Care Moxibustion-Kopfs basierend auf der Endeffektor-Transparentübertragungsfunktion
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testAxleGenCom(Robot robot) {
    int[] led_on = {0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79};
    int[] led_off = {0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78};
    int[] version = {0xAB, 0xBA, 0x11, 0x00, 0x76};
    int[] state = {0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B};

    int[] rcvdata = new int[16];
    int ret = 0;
    int cnt = 1;

    JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
    DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

    JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
    DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

    ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
    DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

    // Endeffektor-Transparentübertragungsfunktion aktivieren
    robot.SetAxleGenComEnable(1);
    robot.SetAxleLuaEnable(1);

    while (cnt <= 10000) {
        // Versionsnummer auslesen
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        if (ret == 0) {
            System.out.printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n",
                    rcvdata[4], rcvdata[5], rcvdata[6], rcvdata[7], rcvdata[8]);
        } else {
            System.out.println("SndRcvAxleGenComCmdData version fail: " + ret);
            break;
        }
        robot.Sleep(1000);

        // Präsenzstatus des Moxibustion-Kopfs auslesen
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        if (ret == 0) {
            System.out.printf(" state : %d \n", rcvdata[4]);
        }
        robot.Sleep(1000);

        // Laser des Moxibustion-Kopfs einschalten
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led on rcv data is: %d, %d, %d, %d, %d, %d\n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(4000);

        // Laser des Moxibustion-Kopfs ausschalten
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(1000);

        System.out.println("***********************complete No. " + cnt + " SDK test*****************************");
        cnt++;
    }
    }  
    
Open-Protocol-Lua-Datei herunterladen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Open-Protocol-Lua-Datei herunterladen
    * @param fileName Name der Open-Protocol-Datei "CtrlDev_XXX.lua"
    * @param savePath Pfad zum Speichern der Open-Protocol-Datei
    * @return Fehlercode
    */
    public int OpenLuaDownload(string fileName, string savePath)

Open-Protocol-Lua-Datei löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Open-Protocol-Lua-Datei löschen
    * @param [in] fileName Name der zu löschenden Open-Protocol-Lua-Datei "CtrlDev_XXX.lua"
    * @return Fehlercode
    */
    public int OpenLuaDelete(string fileName)
        
Alle Open-Protocol-Lua-Dateien löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Alle Open-Protocol-Lua-Dateien löschen
    * @return Fehlercode
    */
    public int AllOpenLuaDelete()

Codebeispiel für Open-Protocol-Upload, -Download und -Löschen von Controller-Peripheriegeräten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestCtrlOpenLuaOperate(Robot robot) {
        int rtn;
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);

        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);

        String[] names = new String[4];
        rtn = robot.GetCtrlOpenLUAName(names);
        System.out.println("GetCtrlOpenLUAName rtn is " + rtn + ", names: " +
                names[0] + ", " + names[1] + ", " + names[2] + ", " + names[3]);

        rtn = robot.LoadCtrlOpenLUA(1);
        System.out.println("LoadCtrlOpenLUA rtn is " + rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        System.out.println("UnloadCtrlOpenLUA rtn is " + rtn);

        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaDelete rtn is " + rtn);
        rtn = robot.AllOpenLuaDelete();
        System.out.println("AllOpenLuaDelete rtn is " + rtn);

        robot.Sleep(1000);
        return 0;
    }