Roboter-Peripherie
==================

.. toctree::
    :maxdepth: 5

Greifer konfigurieren
+++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifer konfigurieren
    * @param [in] company Greiferhersteller (zur Festlegung)
    * @param [in] device Gerätenummer, vorübergehend nicht verwendet, Standard 0
    * @param [in] softvesion Softwareversionsnummer, vorübergehend nicht verwendet, Standard 0
    * @param [in] bus Position des Geräts am Endeffektor-Bus, vorübergehend nicht verwendet, Standard 0
    * @return Fehlercode
    */
    int SetGripperConfig(int company, int device, int softvesion, int bus);

Greiferkonfiguration abrufen
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greiferkonfiguration abrufen
    * @param [out] company Greiferhersteller (zur Festlegung)
    * @param [out] device Gerätenummer, vorübergehend nicht verwendet, Standard 0
    * @param [out] softvesion Softwareversionsnummer, vorübergehend nicht verwendet, Standard 0
    * @param [out] bus Position des Geräts am Endeffektor-Bus, vorübergehend nicht verwendet, Standard 0
    * @return Fehlercode
    */
    int GetGripperConfig(ref int company, ref int device, ref int softvesion, ref int bus);

Greifer aktivieren
++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifer aktivieren
    * @param [in] index Greifernummer
    * @param [in] act 0-Zurücksetzen, 1-Aktivieren
    * @return Fehlercode
    */
    int ActGripper(int index, byte act);

Greifer steuern
+++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifer steuern
    * @param [in] index Greifernummer
    * @param [in] pos Positionsprozentsatz, Bereich [0~100]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] force Drehmomentprozentsatz, Bereich [0~100]
    * @param [in] max_time Maximale Wartezeit, Bereich [0~30000], [ms]
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @param [in] type Greifertyp: 0-Parallelgreifer; 1-Rotationsgreifer
    * @param [in] rotNum Rotationsanzahl (Umdrehungen)
    * @param [in] rotVel Rotationsgeschwindigkeitsprozentsatz [0-100]
    * @param [in] rotTorque Rotationsdrehmomentprozentsatz [0-100]
    * @return Fehlercode
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, byte block, int type, double rotNum, int rotVel, int rotTorque);

Greifer-Bewegungsstatus abrufen
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifer-Bewegungsstatus abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] status 0-Bewegung nicht abgeschlossen, 1-Bewegung abgeschlossen
    * @return Fehlercode
    */
    int GetGripperMotionDone(ref int fault, ref int status);

Greifer-Aktivierungsstatus abrufen
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifer-Aktivierungsstatus abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] status Bit0~Bit15 entsprechen Greifernummern 0~15, Bit=0 nicht aktiviert, Bit=1 aktiviert
    * @return Fehlercode
    */
    int GetGripperActivateStatus(ref int fault, ref int status);

Greiferposition abrufen
++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greiferposition abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] position Positionsprozentsatz, Bereich 0~100%
    * @return Fehlercode
    */
    int GetGripperCurPosition(ref int fault, ref int position);

Greifergeschwindigkeit abrufen
+++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifergeschwindigkeit abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] speed Geschwindigkeitsprozentsatz, Bereich 0~100%
    * @return Fehlercode
    */
    int GetGripperCurSpeed(ref int fault, ref int speed);

Greiferstrom abrufen
+++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greiferstrom abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] current Stromprozentsatz, Bereich 0~100%
    * @return Fehlercode
    */
    int GetGripperCurCurrent(ref int fault, ref int current);

Greiferspannung abrufen
++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greiferspannung abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] voltage Spannung, Einheit 0.1V
    * @return Fehlercode
    */
    int GetGripperVoltage(ref int fault, ref int voltage);

Greifertemperatur abrufen
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifertemperatur abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] temp Temperatur [°C]
    * @return Fehlercode
    */
    int GetGripperTemp(ref int fault, ref int temp);

Vor-Greifpunkt berechnen (visuell)
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Vor-Greifpunkt berechnen (visuell)
    * @param [in] desc_pos Kartesische Pose des Greifpunkts
    * @param [in] zlength Z-Achsen-Versatz
    * @param [in] zangle Rotationsversatz um die Z-Achse
    * @param [out] pre_pos Vor-Greifpunkt
    * @return Fehlercode
    */
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, ref DescPose pre_pos);

Rückzugspunkt berechnen (visuell)
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rückzugspunkt berechnen (visuell)
    * @param [in] desc_pos Kartesische Pose des Rückzugspunkts
    * @param [in] zlength Z-Achsen-Versatz
    * @param [in] zangle Rotationsversatz um die Z-Achse
    * @param [out] post_pos Rückzugspunkt
    * @return Fehlercode
    */
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, ref DescPose post_pos);

Codebeispiel für Roboter-Greiferoperationen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button36_Click(object sender, EventArgs e)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        byte act = 0;
        int max_time = 30000;
        byte block = 0;
        int status=0;
        int fault=0;
        int active_status = 0;
        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        robot.SetGripperConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.GetGripperConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine("gripper config:{0},{1},{2},{3}\n", company, device, softversion, bus);

        robot.ActGripper(index, act);
        Thread.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        Thread.Sleep(1000);

        robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0);
        Thread.Sleep(1000);
        robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0);

        robot.GetGripperMotionDone(ref fault, ref status);
        Console.WriteLine("motion status:{0},{1}\n", fault, status);

        robot.GetGripperActivateStatus(ref fault, ref active_status);
        Console.WriteLine("gripper active fault is: {0}, status is: {1}\n", fault, active_status);

        robot.GetGripperCurPosition(ref fault, ref current_pos);
        Console.WriteLine("fault is:{0}, current position is: {1}\n", fault, current_pos);

        robot.GetGripperCurCurrent(ref fault, ref current);
        Console.WriteLine("fault is:{0}, current current is: {1}\n", fault, current);

        robot.GetGripperVoltage(ref fault, ref voltage);
        Console.WriteLine("fault is:{0}, current voltage is: {1} \n", fault, voltage);

        robot.GetGripperTemp(ref fault, ref temp);
        Console.WriteLine("fault is:{0}, current temperature is: {1}\n", fault, temp);

        robot.GetGripperCurSpeed(ref fault, ref speed);
        Console.WriteLine("fault is:{0}, current speed is: {1}\n", fault, speed);

        int retval = 0;
        DescPose prepick_pose = new DescPose();
        DescPose postpick_pose = new DescPose();

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        retval = robot.ComputePrePick(p1Desc, 10, 0, ref prepick_pose);
        Console.WriteLine("ComputePrePick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z,
            prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);

        retval = robot.ComputePostPick( p2Desc, -10, 0, ref postpick_pose);
        Console.WriteLine("ComputePostPick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z,
            postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);
    }

Rotationsanzahl des Rotationsgreifers abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rotationsanzahl des Rotationsgreifers abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] num Rotationsanzahl (Umdrehungen)
    * @return Fehlercode
    */
    int GetGripperRotNum(ref ushort fault, ref double num);

Rotationsgeschwindigkeitsprozentsatz des Rotationsgreifers abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rotationsgeschwindigkeitsprozentsatz des Rotationsgreifers abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] speed Rotationsgeschwindigkeitsprozentsatz
    * @return Fehlercode
    */
    int GetGripperRotSpeed(ref ushort fault, ref int speed);

Rotationsdrehmomentprozentsatz des Rotationsgreifers abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rotationsdrehmomentprozentsatz des Rotationsgreifers abrufen
    * @param [out] fault 0-kein Fehler, 1-Fehler
    * @param [out] torque Rotationsdrehmomentprozentsatz
    * @return Fehlercode
    */
    int GetGripperRotTorque(ref ushort fault, ref int torque);

Codebeispiel zum Abrufen des Status eines Rotationsgreifers
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    int MoveRotGripper(int pos, double rotPos)
    {
        robot.ResetAllError();
        robot.ActGripper(1, 1);
        Thread.Sleep(1000);
        int rtn = robot.MoveGripper(1, pos, 50, 50, 5000, 1, 1, rotPos, 50, 100);
        Console.WriteLine($"move gripper rtn is {rtn}" );
        UInt16 fault = 0;
        double rotNum = 0.0;
        int rotSpeed = 0;
        int rotTorque = 0;
        robot.GetGripperRotNum(ref fault, ref rotNum);
        robot.GetGripperRotSpeed(ref fault, ref rotSpeed);
        robot.GetGripperRotTorque(ref fault, ref rotTorque);
        Console.WriteLine($"gripper rot num :{ rotNum}, gripper rotSpeed :{rotSpeed}, gripper rotTorque : { rotTorque}");
        return 0;
    }

Förderband starten/stoppen
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband starten/stoppen
    * @param [in] status Status, 1-starten, 0-stoppen
    * @return Fehlercode
    */
    int ConveyorStartEnd(byte status);

IO-Erkennungspunkt aufzeichnen
+++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO-Erkennungspunkt aufzeichnen
    * @return Fehlercode
    */
    int ConveyorPointIORecord();

Punkt A aufzeichnen
++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Punkt A aufzeichnen
    * @return Fehlercode
    */
    int ConveyorPointARecord();

Referenzpunkt aufzeichnen
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Referenzpunkt aufzeichnen
    * @return Fehlercode
    */
    int ConveyorRefPointRecord();

Punkt B aufzeichnen
++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Punkt B aufzeichnen
    * @return Fehlercode
    */
    int ConveyorPointBRecord();

Förderband-Werkstück IO-Erkennung
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband-Werkstück IO-Erkennung
    * @param [in] max_t Maximale Erkennungszeit [ms]
    * @return Fehlercode
    */
    int ConveyorIODetect(int max_t);

Aktuelle Objektposition abrufen
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktuelle Objektposition abrufen
    * @param [in] mode 1-Tracking Greifen, 2-Tracking Bewegung, 3-TPD-Tracking
    * @return Fehlercode
    */
    int ConveyorGetTrackData(int mode);

Förderband-Tracking starten
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband-Tracking starten
    * @param [in] status Status, 1-starten, 0-stoppen
    * @return Fehlercode
    */
    int ConveyorTrackStart(byte status);

Förderband-Tracking stoppen
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband-Tracking stoppen
    * @return Fehlercode
    */
    int ConveyorTrackEnd();

Förderbandparameter konfigurieren
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderbandparameter konfigurieren
    * @param [in] encChannel Encoderkanal 1~2
    * @param [in] resolution Impulse pro Encoderumdrehung
    * @param [in] lead Vorschubweg des Förderbands pro Encoderumdrehung [mm]
    * @param [in] wpAxis Werkstückkoordinatennummer (für Tracking-Bewegung, bei Tracking-Greifen/TPD-Tracking auf 0 setzen)
    * @param [in] vision Mit Vision gekoppelt? 0 nein, 1 ja
    * @param [in] speedRadio Geschwindigkeitsverhältnis (für Förderband-Tracking-Greifen Option (1-100)), Standard 1 für andere Optionen
    * @param [in] followType Tracking-Bewegungstyp: 0-Tracking-Bewegung; 1-Nachlauf-Bewegung
    * @param [in] startDis Für Nachlauf-Greifen erforderlich: Startabstand des Trackings. -1: automatische Berechnung (Nachlauf startet, wenn Werkstück unter Roboter ist). Einheit mm, Standard 0
    * @param [in] endDis Für Nachlauf-Greifen erforderlich: Endabstand des Trackings. Einheit mm, Standard 100
    * @return Fehlercode
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis = 0, int endDis = 100);

Förderband-Greifpunktkompensation einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband-Greifpunktkompensation einstellen
    * @param [in] cmp Kompensationsposition double[3]{x, y, z}
    * @return Fehlercode
    */
    int ConveyorCatchPointComp(double[] cmp);

Förderband-Tracking-Linearbewegung
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband-Tracking-Linearbewegung
    * @param [in] name Name des Bewegungspunkts
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] wobj Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @return Fehlercode
    */
    int ConveyorTrackMoveL(string name, int tool, int wobj, float vel, float acc, float ovl, float blendR);

Förderband-Kommunikationseingangserkennung
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband-Kommunikationseingangserkennung
    * @param [in] timeout Warte-Timeout [ms]
    * @return Fehlercode
    */
    int ConveyorComDetect(int timeout);

Förderband-Kommunikationseingangserkennung auslösen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Förderband-Kommunikationseingangserkennung auslösen
    * @return Fehlercode
    */
    int ConveyorComDetectTrigger();

Beispielprogramm zum Auslösen der Förderband-Kommunikationseingangserkennung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button3_Click(object sender, EventArgs e)
    {

        // Schaltfläche deaktivieren, um wiederholtes Klicken zu verhindern
        button3.Enabled = false;

        // Zeitintensive Operation im Hintergrundthread ausführen
        Thread conveyorThread = new Thread(ConveyorTest);
        conveyorThread.IsBackground = true;
        conveyorThread.Start();
    }

    private void button4_Click(object sender, EventArgs e)
    {
        // Benutzereingabe abrufen
        string input = texBox.Text;
        Console.WriteLine($"please input a number to trigger:{input}");

        int rtn = robot.ConveyorComDetectTrigger();
        Console.WriteLine($"ConveyorComDetectTrigger return value: {rtn}");

    }

    private void ConveyorTest()
    {
        // Invoke verwenden, um Steuerelemente im UI-Thread zu aktualisieren
        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("Starte Förderbandtest...");
        });

        int retval = 0;
        int index = 1;
        int max_time = 30000;
        bool block = false;
        retval = 0;

        /* Förderband-Greifprozess */
        DescPose startdescPose = new DescPose(139.176f, 4.717f, 9.088f, -179.999f, -0.004f, -179.990f);
        JointPos startjointPos = new JointPos(-34.129f, -88.062f, 97.839f, -99.780f, -90.003f, -34.140f);

        DescPose homePose = new DescPose(139.177f, 4.717f, 69.084f, -180.000f, -0.004f, -179.989f);
        JointPos homejointPos = new JointPos(-34.129f, -88.618f, 84.039f, -85.423f, -90.003f, -34.140f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        // In Sicherheitsposition bewegen
        retval = robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        Console.WriteLine($"MoveL to safe position return value: {retval}");

        // Förderbanderkennung
        retval = robot.ConveyorComDetect(1000 * 10);
        Console.WriteLine($"ConveyorComDetect return value: {retval}");

        // Tracking-Daten abrufen
        retval = robot.ConveyorGetTrackData(2);
        Console.WriteLine($"ConveyorGetTrackData return value: {retval}");

        // Tracking starten
        retval = robot.ConveyorTrackStart(2);
        Console.WriteLine($"ConveyorTrackStart return value: {retval}");

        // In Startposition bewegen
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        // Tracking beenden
        retval = robot.ConveyorTrackEnd();
        Console.WriteLine($"ConveyorTrackEnd return value: {retval}");

        // In Sicherheitsposition zurückkehren
        robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("Förderbandtest abgeschlossen!");
            button3.Enabled = true;
        });
    }

Beispielprogramm für Roboter-Förderbandoperationen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnConvert_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");
        DescPose pos1 = new DescPose(0, 0, 0, 0 ,0 ,0);
        DescPose pos2 = new DescPose(0, 0, 0, 0, 0, 0);

        pos1.tran.x = -351.175;
        pos1.tran.y = 3.389;
        pos1.tran.z = 431.172;
        pos1.rpy.rx = -179.111;
        pos1.rpy.ry = -0.241;
        pos1.rpy.rz = 90.388;

        pos2.tran.x = -333.654;
        pos2.tran.y = -229.003;
        pos2.tran.z = 404.335;
        pos2.rpy.rx = -179.139;
        pos2.rpy.ry = -0.779;
        pos2.rpy.rz = 91.269;
        int rtn = -1;

        double[] cmp = new double[3] { 0, 9.99, 0 };
        rtn = robot.ConveyorCatchPointComp(cmp);
        if (rtn != 0)
        {
            return;
        }
        Console.WriteLine($"ConveyorCatchPointComp: rtn {rtn}");

        rtn = robot.MoveCart(pos1, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, -1);
        Console.WriteLine($"MoveCart: rtn {rtn}");

        rtn = robot.ConveyorIODetect(10000);
        Console.WriteLine($"ConveyorIODetect: rtn {rtn}");

        robot.ConveyorGetTrackData(1);
        rtn = robot.ConveyorTrackStart(1);
        Console.WriteLine($"ConveyorTrackStart: rtn {rtn}");

        rtn = robot.ConveyorTrackMoveL("cvrCatchPoint", 0, 0, 100.0f, 0.0f, 100.0f, -1.0f);
        Console.WriteLine($"ConveyorTrackMoveL: rtn {rtn}");

        rtn = robot.MoveGripper(1, 59, 43, 21, 30000, 0, 0, 0, 0, 0);
        Console.WriteLine($"MoveGripper: rtn {rtn}");

        rtn = robot.ConveyorTrackMoveL("cvrRaisePoint", 0, 0, 100.0f, 0.0f, 100.0f, -1.0f);
        Console.WriteLine($"ConveyorTrackMoveL: rtn {rtn}");

        rtn = robot.ConveyorTrackEnd();
        Console.WriteLine($"ConveyorTrackEnd: rtn {rtn}");

        rtn = robot.MoveCart(pos2, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, -1);
        Console.WriteLine($"MoveCart: rtn {rtn}");

        rtn = robot.MoveGripper(1, 100, 43, 21, 30000, 0, 0, 0, 0, 0);
        Console.WriteLine($"MoveGripper: rtn {rtn}");
    }

Endeffektor-Sensor konfigurieren
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-Sensor konfigurieren
    * @param [in] idCompany Hersteller, 18-JUNKONG; 25-HUIDE
    * @param [in] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @param [in] idSoftware Softwareversion, 0-J1.0/HuiDe1.0 (vorübergehend nicht freigegeben)
    * @param [in] idBus Anschlussposition, 1-Endeffektor Port 1; 2-Endeffektor Port 2...8-Endeffektor Port 8 (vorübergehend nicht freigegeben)
    * @return Fehlercode
    */
    int AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Endeffektor-Sensorkonfiguration abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-Sensorkonfiguration abrufen
    * @param [out] idCompany Hersteller, 18-JUNKONG; 25-HUIDE
    * @param [out] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @return Fehlercode
    */
    int AxleSensorConfigGet(ref int idCompany, ref int idDevice);

Endeffektor-Sensor aktivieren
++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-Sensor aktivieren
    * @param [in] actFlag 0-Zurücksetzen; 1-Aktivieren
    * @return Fehlercode
    */
    int AxleSensorActivate(int actFlag);

In Endeffektor-Sensorregister schreiben
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief In Endeffektor-Sensorregister schreiben
    * @param [in] devAddr Geräteadresse 0-255
    * @param [in] regHAddr Registeradresse hohes Byte
    * @param [in] regLAddr Registeradresse niedriges Byte
    * @param [in] regNum Anzahl der Register 0-255
    * @param [in] data1 Zu schreibender Registerwert 1
    * @param [in] data2 Zu schreibender Registerwert 2
    * @param [in] isNoBlock 0-blockierend; 1-nicht blockierend
    * @return Fehlercode
    */
    int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Codebeispiel für Endeffektor-Sensor
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button2_Click_1(object sender, EventArgs e)
    {
        robot.AxleSensorConfig(18, 0, 0, 1);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(ref company, ref type);
        Console.WriteLine("company is " + company + ", type is " + type);

        int rtn = robot.AxleSensorActivate(1);
        Console.WriteLine("AxleSensorActivate rtn is " + rtn);

        Thread.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        Console.WriteLine("AxleSensorRegWrite rtn is " + rtn);   
    }

Roboter-Peripherieprotokoll abrufen
++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Roboter-Peripherieprotokoll abrufen
    * @param [out] protocol Roboter-Peripherieprotokollnummer: 4096-Erweiterungsachsen-Steuerkarte; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Fehlercode
    */
    int GetExDevProtocol(ref int protocol);

Roboter-Peripherieprotokoll einstellen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Roboter-Peripherieprotokoll einstellen
    * @param [in] protocol Roboter-Peripherieprotokollnummer: 4096-Erweiterungsachsen-Steuerkarte; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Fehlercode
    */
    int SetExDevProtocol(int protocol);

Beispielprogramm zum Einstellen des Roboter-Peripherieprotokolls
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSetProto_Click(object sender, EventArgs e)
    {
        int protocol = 4096;
        int rtn = robot.SetExDevProtocol(protocol);
        Console.WriteLine("SetExDevProtocol rtn " + rtn);
        rtn = robot.GetExDevProtocol(ref protocol);
        Console.WriteLine("GetExDevProtocol rtn " + rtn + " protocol is: " + protocol);
    }

Endeffektor-Kommunikationsparameter abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-Kommunikationsparameter abrufen
    * @param [out] param Endeffektor-Kommunikationsparameter
    * @return Fehlercode
    */
    int GetAxleCommunicationParam(ref AxleComParam param);

Endeffektor-Kommunikationsparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-Kommunikationsparameter einstellen
    * @param [in] param Endeffektor-Kommunikationsparameter
    * @return Fehlercode
    */
    int SetAxleCommunicationParam(AxleComParam param);

Endeffektor-Dateiübertragungstyp einstellen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-Dateiübertragungstyp einstellen
    * @param [in] type 1-MCU Upgrade-Datei; 2-LUA-Datei
    * @return Fehlercode
    */
    int SetAxleFileType(int type);

Endeffektor-LUA-Ausführung aktivieren
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-LUA-Ausführung aktivieren
    * @param [in] enable 0-nicht aktivieren; 1-aktivieren
    * @return Fehlercode
    */
    int SetAxleLuaEnable(int enable);

Fehlerbehebung bei anomaler Endeffektor-LUA-Datei
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fehlerbehebung bei anomaler Endeffektor-LUA-Datei
    * @param [in] status 0-nicht beheben; 1-beheben
    * @return Fehlercode
    */
    int SetRecoverAxleLuaErr(int status);

Aktivierungsstatus der Endeffektor-LUA-Ausführung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktivierungsstatus der Endeffektor-LUA-Ausführung abrufen
    * @param [out] status 0-nicht aktiviert; 1-aktiviert
    * @return Fehlercode
    */
    int GetAxleLuaEnableStatus(ref int status);

Aktivierungstyp der Endeffektor-LUA-Endgeräte einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktivierungstyp der Endeffektor-LUA-Endgeräte einstellen
    * @param [in] forceSensorEnable Kraftsensor-Aktivierungsstatus, 0-nicht aktivieren; 1-aktivieren
    * @param [in] gripperEnable Greifer-Aktivierungsstatus, 0-nicht aktivieren; 1-aktivieren
    * @param [in] IOEnable IO-Geräte-Aktivierungsstatus, 0-nicht aktivieren; 1-aktivieren
    * @return Fehlercode
    */
    int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable);

Aktivierungstyp der Endeffektor-LUA-Endgeräte abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktivierungstyp der Endeffektor-LUA-Endgeräte abrufen
    * @param [out] forceSensorEnable Kraftsensor-Aktivierungsstatus, 0-nicht aktiviert; 1-aktiviert
    * @param [out] gripperEnable Greifer-Aktivierungsstatus, 0-nicht aktiviert; 1-aktiviert
    * @param [out] IOEnable IO-Geräte-Aktivierungsstatus, 0-nicht aktiviert; 1-aktiviert
    * @return Fehlercode
    */
    int GetAxleLuaEnableDeviceType(ref int forceSensorEnable, ref int gripperEnable, ref int IOEnable);

Aktuell konfigurierte Endgeräte abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktuell konfigurierte Endgeräte abrufen
    * @param [out] forceSensorEnable Aktivierte Kraftsensornummern-Array (0-nicht aktiviert; 1-aktiviert) - Implementierung abhängig
    * @param [out] gripperEnable Aktivierte Greifernummern-Array (0-nicht aktiviert; 1-aktiviert) - Implementierung abhängig
    * @param [out] IODeviceEnable Aktivierte IO-Gerätenummern-Array (0-nicht aktiviert; 1-aktiviert) - Implementierung abhängig
    * @return Fehlercode
    */
    int GetAxleLuaEnableDevice(ref int[] forceSensorEnable, ref int[] gripperEnable, ref int[] IODeviceEnable); // Hinweis: Array-Parameter möglicherweise anders zu handhaben

Greifer-Aktionssteuerungsfunktion aktivieren
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Greifer-Aktionssteuerungsfunktion aktivieren (für LUA-Skript)
    * @param [in] id Greifer-Gerätenummer
    * @param [in] func Funktions-Array: func[0]-Greifer aktivieren; func[1]-Greifer initialisieren; 2-Position einstellen; 3-Geschwindigkeit einstellen; 4-Drehmoment einstellen; 6-Greiferstatus lesen; 7-Initialisierungsstatus lesen; 8-Fehlercode lesen; 9-Position lesen; 10-Geschwindigkeit lesen; 11-Drehmoment lesen
    * @return Fehlercode
    */
    int SetAxleLuaGripperFunc(int id, int[] func);

Aktivierte Greifer-Aktionssteuerungsfunktion abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktivierte Greifer-Aktionssteuerungsfunktion abrufen
    * @param [in] id Greifer-Gerätenummer
    * @param [out] func Funktions-Array (wie oben)
    * @return Fehlercode
    */
    int GetAxleLuaGripperFunc(int id, ref int[] func); // Hinweis: Array-Parameter möglicherweise anders zu handhaben

In Ethercat-Slave-Datei des Roboters schreiben
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief In Ethercat-Slave-Datei des Roboters schreiben
    * @param [in] type Slave-Dateityp: 1-Upgrade Slave-Datei; 2-Upgrade Slave-Konfigurationsdatei
    * @param [in] slaveID Slave-Nummer
    * @param [in] fileName Name der hochzuladenden Datei
    * @return Fehlercode
    */
    int SlaveFileWrite(int type, int slaveID, string fileName);

Endeffektor-Lua-Open-Protocol-Datei hochladen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor-Lua-Open-Protocol-Datei hochladen
    * @param [in] filePath Lokaler Pfad zur Lua-Datei ".../AXLE_LUA_End_DaHuan.lua"
    * @return Fehlercode
    */
    int AxleLuaUpload(string filePath);

Ethercat-Slave des Roboters in den Boot-Modus versetzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ethercat-Slave des Roboters in den Boot-Modus versetzen
    * @return Fehlercode
    */
    int SetSysServoBootMode();

Codebeispiel für Roboter-Endeffektor-LUA-Dateioperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button41_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_JunDuo_Xinjingcheng.lua");

        AxleComParam param = new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        AxleComParam getParam = new AxleComParam();
        robot.GetAxleCommunicationParam(ref getParam);
        Console.WriteLine("GetAxleCommunicationParam param is {0} {1} {2} {3} {4} {5} {6}",
            getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify,
            getParam.timeout, getParam.timeoutTimes, getParam.period);

        robot.SetAxleLuaEnable(1);
        int luaEnableStatus = 0;
        robot.GetAxleLuaEnableStatus(ref luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        robot.GetAxleLuaEnableDeviceType(ref forceEnable, ref gripperEnable, ref ioEnable);
        Console.WriteLine("GetAxleLuaEnableDeviceType param is {0} {1} {2}", forceEnable, gripperEnable, ioEnable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
        robot.SetAxleLuaGripperFunc(1, func);
        int[] getFunc = new int[16];
        robot.GetAxleLuaGripperFunc(1, ref getFunc);
        int[] getforceEnable = new int[16];
        int[] getgripperEnable = new int[16];
        int[] getioEnable = new int[16];
        robot.GetAxleLuaEnableDevice(ref getforceEnable, ref getgripperEnable, ref getioEnable);
        Console.WriteLine("\ngetforceEnable status : ");
        foreach (int i in getforceEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetgripperEnable status : ");
        foreach (int i in getgripperEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetioEnable status : ");
        foreach (int i in getioEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine();
        robot.ActGripper(1, 0);
        Thread.Sleep(2000);
        robot.ActGripper(1, 1);
        Thread.Sleep(2000);
        robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("gripper pos is " + pkg.gripper_position);
            Thread.Sleep(100);
        }
    }

SmartTool-Tastenstatus abrufen
+++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief SmartTool-Tastenstatus abrufen
    * @param [out] state SmartTool-Griff Tastenstatus (Bit0: 0-Kommunikation normal; 1-Kommunikation unterbrochen; Bit1-Rückgängig; Bit2-Programm löschen;
        Bit3-Taste A; Bit4-Taste B; Bit5-Taste C; Bit6-Taste D; Bit7-Taste E; Bit8-IO-Taste; Bit9-Hand/Automatik; Bit10-Start)
    * @return Fehlercode
    */
    int GetSmarttoolBtnState(ref int state);

Codebeispiel
++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button11_Click(object sender, EventArgs e)
    {

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int state = 0;
        while (true)
        {
            int rtn = robot.GetSmarttoolBtnState(ref state);
            string binaryString = Convert.ToString(state, 2).PadLeft(32, '0');
            Console.WriteLine($"GetSmarttoolBtnState rtn (binary): {binaryString}");
            Thread.Sleep(100);
        }
    }

Open-Protocol-Lua-Datei hochladen
++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Open-Protocol-Lua-Datei hochladen
    * @param filePath Lokaler Pfad zur Open-Protocol-Lua-Datei
    * @return Fehlercode
    */
    int OpenLuaUpload(string filePath)

Slave-Kartenparameter abrufen
+++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Slave-Kartenparameter abrufen
    * @param type Protokolltyp: 0-Ethercat, 1-CClink, 3-Ethercat (Dopplung?), 4-EIP
    * @param version Protokollversion
    * @param connState Verbindungsstatus: 0-nicht verbunden, 1-verbunden
    * @return Fehlercode
    */
    int GetFieldBusConfig(ref int type, ref int version, ref int connState) // Hinweis: Array-Parameter in C# SDK möglicherweise anders

In Slave-DO schreiben
++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief In Slave-DO schreiben
    * @param DOIndex DO-Nummer
    * @param writeNum Anzahl der zu schreibenden Werte
    * @param status Zu schreibende Werte (max. 8)
    * @return Fehlercode
    */
    int FieldBusSlaveWriteDO(int DOIndex, int writeNum, int[] status)

In Slave-AO schreiben
++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  AO der Slave-Station schreiben
    * @param [in] AOIndex AO-Nummer
    * @param [in] writeNum Anzahl der zu schreibenden Werte
    * @param [in] status Array der zu schreibenden Werte (maximal 8), AO0~AO15 sind ganzzahlig, AO16~AO31 sind Gleitkommazahlen
    * @return Fehlercode
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int writeNum, double[] status)

Slave-DI lesen
+++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Slave-DI lesen
    * @param DIIndex DI-Nummer
    * @param readNum Anzahl der zu lesenden Werte
    * @param status Gelesene Werte (max. 8)
    * @return Fehlercode
    */
    int FieldBusSlaveReadDI(int DIIndex, int readNum, ref int[] status)

Slave-AI lesen
+++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Slave-AI lesen
    * @param AIIndex AI-Nummer
    * @param readNum Anzahl der zu lesenden Werte
    * @param status Gelesene Werte (max. 8)
    * @return Fehlercode
    */
    int FieldBusSlaveReadAI(int AIIndex, int readNum, ref double[] status)

Auf erweiterten DI-Eingang warten (Slave)
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Auf erweiterten DI-Eingang (Slave) warten
    * @param DIIndex DI-Nummer
    * @param status Erwarteter Zustand: 0-niedrig; 1-hoch
    * @param waitMs Maximale Wartezeit [ms]
    * @return Fehlercode
    */
    int FieldBusSlaveWaitDI(int DIIndex, int status, int waitMs)

Auf erweiterten AI-Eingang warten (Slave)
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Auf erweiterten AI-Eingang (Slave) warten
    * @param AIIndex AI-Nummer
    * @param waitType Bedingung: 0-größer als; 1-kleiner als
    * @param value Vergleichswert
    * @param waitMs Maximale Wartezeit [ms]
    * @return Fehlercode
    */
    int FieldBusSlaveWaitAI(int AIIndex, int waitType, double value, int waitMs)

Codebeispiel für Slave-Modus-Befehle
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button101_Click(object sender, EventArgs e)
    {
        int rtn = 0;

        int type = 0, version = 0, connState = 0;
        int[] ctrl = new int[8];
        double[] ctrlAO = new double[8];
        int[] DI = new int[8];
        double[] AI = new double[8];
        // if (rtn != 0) // Ursprünglicher Code, wahrscheinlich überflüssig
        // {
        //     return;
        // }
        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("E://temp/CtrlDev_field.lua");
        Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        Thread.Sleep(8000);

        // Protokolltyp, Softwareversion und Verbindungsstatus mit SPS abrufen
        robot.GetFieldBusConfig(ref type, ref version, ref connState);
        Console.WriteLine($"type is {type}, version is {version}, connState is {connState}");

        // DO0 = 1, DO1 = 0, DO2 = 1 schreiben
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);

        // AO2 = 0x1000 schreiben
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);

        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, ref DI);
            Console.WriteLine($"DI0 is {DI[0]}, DI1 is {DI[1]}, DI2 is {DI[2]}, DI3 is {DI[3]}");
            robot.FieldBusSlaveReadAI(0, 3, ref AI);
            Console.WriteLine($"AI0 is {AI[0]}, AI1 is {AI[1]}, AI2 is {AI[2]}");
            Thread.Sleep(10);
        }
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        Console.WriteLine($"FieldBusSlaveWaitDI result is {ret}");

        ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00f, 100);
        Console.WriteLine($"FieldBusSlaveWaitAI result is {ret}");
    }

Array-Sauggreifer steuern
++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Array-Sauggreifer steuern
    * @param [in] slaveID Slave-Nummer
    * @param [in] len Länge des Steuerarrays (Anzahl der zu steuernden Sauger)
    * @param [in] ctrlValue Steuerwerte: 1-mit maximalem Vakuum ansaugen; 2-mit eingestelltem Vakuum ansaugen; 3-Ansaugen stoppen
    * @return Fehlercode
    */
    int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue)

Status des Array-Sauggreifers abrufen
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Status des Array-Sauggreifers abrufen
    * @param [in] slaveID Slave-Nummer
    * @param [out] state Saugzustand: 0-Objekt losgelassen; 1-Werkstück erfolgreich angesaugt; 2-kein Objekt angesaugt; 3-Objekt abgelöst
    * @param [out] pressValue Aktuelles Vakuum [kPa]
    * @param [out] error Aktueller Fehlercode des Saugers
    * @return Fehlercode
    */
    int GetSuckerState(int slaveID, ref int[] state, ref int[] pressValue, ref int[] error) // Hinweis: Array-Parameter

Auf Saugerstatus warten
++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Auf Saugerstatus warten
    * @param [in] slaveID Slave-Nummer
    * @param [in] state Erwarteter Saugzustand: 0-Objekt losgelassen; 1-Werkstück erfolgreich angesaugt; 2-kein Objekt angesaugt; 3-Objekt abgelöst
    * @param [in] ms Maximale Wartezeit [ms]
    * @return Fehlercode
    */
    int WaitSuckerState(int slaveID, int state, int ms)

Codebeispiel für Array-Sauggreifer-Steuerung
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void TestSucker(Robot robot)
    {

        int[] ctrl = new int[20];
        int state=0;
        int pressValue=0;
        int error=0;
        int rtn;

        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload(@"C:\SDK\CtrlDev_sucker.lua");
        Thread.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        Thread.Sleep(1000);

        // Sauger im Broadcast-Modus mit maximaler Saugkraft steuern
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);

        // Zustände von Sauger 1 und Sauger 12 in einer Schleife überwachen
        for (int i = 0; i < 100; i++)
        {
            // Hinweis: GetSuckerState erwartet Arrays, die Übergabe von Einzelvariablen ist hier problematisch.
            // Dies ist eine konzeptionelle Darstellung. Die tatsächliche Implementierung muss die Array-Parameter korrekt behandeln.
            // robot.GetSuckerState(1, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker1 state is {state}, pressValue is {pressValue}, error num is {error}");
            // robot.GetSuckerState(12, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker12 state is {state}, pressValue is {pressValue}, error num is {error}");
            Thread.Sleep(100);
        }
        // Auf angesaugten Zustand von Sauger 1 warten, Timeout 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        Console.WriteLine($"WaitSuckerState result is {ret}");

        // Unicast-Modus: Sauger 1 und 12 ausschalten
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);

        robot.CloseRPC();
    }

Laser-Peripherie Ein-/Ausschaltfunktion
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Peripherie Ein-/Ausschaltfunktion
     * @param [in] OnOff 0-ausschalten, 1-einschalten
     * @param [in] weldId Schweißnaht-ID, Standard 0
     * @return Fehlercode
     */
    int LaserTrackingLaserOnOff(int OnOff, int weldId)

Laser-Tracking Start-/Endfunktion
++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Tracking Start-/Endfunktion
     * @param [in] OnOff 0-beenden, 1-starten
     * @param [in] coordId Werkzeugkoordinatennummer des Laser-Peripheriegeräts
     * @return Fehlercode
     */
    int LaserTrackingTrackOnOff(int OnOff, int coordId)

Lasernahtsuche - feste Richtung
++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Lasernahtsuche - feste Richtung
     * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
     * @param [in] vel Geschwindigkeit [%]
     * @param [in] distance Maximale Suchdistanz [mm]
     * @param [in] timeout Such-Timeout [ms]
     * @param [in] posSensorNum Nummer des kalibrierten Laser-Werkzeugkoordinatensystems
     * @return Fehlercode
     */
    int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum)

Lasernahtsuche - beliebige Richtung
++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Lasernahtsuche - beliebige Richtung
     * @param [in] directionPoint XYZ-Koordinaten des Eingabepunkts für die Suchrichtung
     * @param [in] vel Geschwindigkeit [%]
     * @param [in] distance Maximale Suchdistanz [mm]
     * @param [in] timeout Such-Timeout [ms]
     * @param [in] posSensorNum Nummer des kalibrierten Laser-Werkzeugkoordinatensystems
     * @return Fehlercode
     */
    int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum)

Lasernahtsuche beenden
++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Lasernahtsuche beenden
    * @return Fehlercode
    */
    int LaserTrackingSearchStop()

Laser-IP-Konfiguration
++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-IP-Konfiguration
     * @param [in] ip IP-Adresse des Laser-Peripheriegeräts
     * @param [in] port Portnummer des Laser-Peripheriegeräts
     * @return Fehlercode
     */
    int LaserTrackingSensorConfig(string ip, int port)

Laser-Peripherie-Abtastperiode konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Peripherie-Abtastperiode konfigurieren
     * @param [in] period Abtastperiode [ms]
     * @return Fehlercode
     */
    int LaserTrackingSensorSamplePeriod(int period)

Laser-Peripherie-Treiber laden
+++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Peripherie-Treiber laden
     * @param [in] type Protokolltyp des Laser-Peripherietreibers: 101-RuiNiu; 102-ChuangXiang; 103-QuanShi; 104-TongZhou; 105-AoTai
     * @return Fehlercode
     */
    int LoadPosSensorDriver(int type)

Laser-Peripherie-Treiber entladen
++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Peripherie-Treiber entladen
     * @return Fehlercode
     */
    int UnLoadPosSensorDriver()

Laser-Schweißnaht-Trajektorie aufzeichnen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Schweißnaht-Trajektorie aufzeichnen
     * @param [in] status 0-Aufzeichnung stoppen; 1-Echtzeit-Tracking; 2-Aufzeichnung starten
     * @param [in] delayTime Verzögerungszeit [ms]
     * @return Fehlercode
     */
    int LaserSensorRecord1(int status, int delayTime)

Laser-Schweißnaht-Trajektorie wiedergeben
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Schweißnaht-Trajektorie wiedergeben
     * @param [in] delayTime Verzögerungszeit [ms]
     * @param [in] speed Geschwindigkeit [%]
     * @return Fehlercode
     */
    int LaserSensorReplay(int delayTime, double speed)

Laser-Tracking-Wiedergabe
+++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Laser-Tracking-Wiedergabe (Bewegung entlang der aufgezeichneten Trajektorie)
     * @return Fehlercode
     */
    int MoveLTR()

Laser-Schweißnaht-Trajektorie aufzeichnen und wiedergeben
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Laser-Schweißnaht-Trajektorie aufzeichnen und wiedergeben (erweiterte Funktion)
    * @param [in] delayMode Modus: 0-Verzögerungszeit; 1-Verzögerungsdistanz
    * @param [in] delayTime Verzögerungszeit [ms] (wenn delayMode=0)
    * @param [in] delayDisExAxisNum Erweiterungsachsennummer für Distanzverzögerung
    * @param [in] delayDis Verzögerungsdistanz [mm] (wenn delayMode=1)
    * @param [in] sensitivePara Kompensations-Empfindlichkeitskoeffizient
    * @param [in] trackMode Punkt-Tracking-Typ: 0-Erweiterungsachse asynchron; 1-Roboter (synchron?)
    * @param [in] triggerMode Punkt-Tracking-Auslösemodus: 0-Tracking-Dauer; 1-IO
    * @param [in] runTime Dauer des Roboter-Punkt-Trackings [s]
    * @param [in] speed Geschwindigkeit [%]
    * @return Fehlercode
    */
    int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed)

Zum aufgezeichneten Startpunkt der Schweißnaht bewegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Zum aufgezeichneten Startpunkt der Schweißnaht bewegen
     * @param [in] moveType 0-PTP, 1-LIN
     * @param [in] ovl Geschwindigkeit [%]
     * @return Fehlercode
     */
    int MoveToLaserRecordStart(int moveType, double ovl)

Zum aufgezeichneten Endpunkt der Schweißnaht bewegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Zum aufgezeichneten Endpunkt der Schweißnaht bewegen
     * @param [in] moveType 0-PTP, 1-LIN
     * @param [in] ovl Geschwindigkeit [%]
     * @return Fehlercode
     */
    int MoveToLaserRecordEnd(int moveType, double ovl)

Zum vom Laser-Sensor gefundenen Nahtpunkt bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Zum vom Laser-Sensor gefundenen Nahtpunkt bewegen
     * @param [in] moveFlag Bewegungstyp: 0-PTP; 1-LIN
     * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0-100]
     * @param [in] dataFlag Auswahl der Schweißnaht-Cache-Daten: 0-Planungsdaten ausführen; 1-Aufgezeichnete Daten ausführen
     * @param [in] plateType Plattenmaterial-Typ: 0-Wellenplatte; 1-Wellpappe; 2-Zaunplatte; 3-Ölfass; 4-Wellenpanzerstahl
     * @param [in] trackOffectType Laser-Sensor-Versatztyp: 0-kein Versatz; 1-Versatz im Basiskoordinatensystem; 2-Versatz im Werkzeugkoordinatensystem; 3-Versatz basierend auf Laser-Sensor-Rohdaten
     * @param [in] offset Versatzwert (Pose)
     * @return Fehlercode
     */
    int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset)

Koordinateninformationen des vom Laser-Sensor gefundenen Nahtpunkts abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Koordinateninformationen des vom Laser-Sensor gefundenen Nahtpunkts abrufen
     * @param [in] trackOffectType Laser-Sensor-Versatztyp (siehe oben)
     * @param [in] offset Versatzwert (Pose)
     * @param [out] jPos Gelenkposition [°]
     * @param [out] descPos Kartesische Position [mm]
     * @param [out] tool Verwendetes Werkzeugkoordinatensystem
     * @param [out] user Verwendetes Werkstückkoordinatensystem
     * @param [out] exaxis Position der Erweiterungsachse [mm]
     * @return Fehlercode
     */
    int GetLaserSeamPos(int trackOffectType, DescPose offset, ref JointPos jPos, ref DescPose descPos, ref int tool, ref int user, ref ExaxisPos exaxis)

Codebeispiel für Laser-Peripherie-Sensorparametrierung und -Debugging
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    void testLaserConfig()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0, 0);
        System.Threading.Thread.Sleep(3000);
        robot.LaserTrackingLaserOnOff(1, 0);
    }

Codebeispiel für Laser-Trajektorienscan und -wiedergabe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    void testLaserRecordAndReplay()
    { 
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i=0;i<10;++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);

            robot.LaserSensorRecord1(0, 10);
            robot.MoveToLaserRecordStart(1, 30);
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            robot.LaserSensorRecord1(0, 10);
            Console.WriteLine($"Number of completions : {i+1} ");
        }
    }

Codebeispiel für Lasernahtsuche und Echtzeit-Tracking
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    public static void testLasertrack()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i = 0; i < 10; ++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint = new DescTran();

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();
            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);

            robot.LaserTrackingTrackOnOff(1, 3);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingTrackOnOff(0, 3);
            Console.WriteLine($"Number of completions : {i + 1} ");
        }
    }

Codebeispiel für synchrones Laser-Tracking mit Erweiterungsachse und Roboter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestLaserTrackAndExitAxis()
    {   
        ExaxisPos startexaxisPos = new ExaxisPos(0, 0, 0, 0);
        ExaxisPos seamexaxisPos = new ExaxisPos(-10, 0, 0, 0);
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);      
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);     
        JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
        DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
        for (int i=0;i<10;++i)
        {
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);
            Console.WriteLine("11111");
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            Console.WriteLine("2222");
            int tool = 0;
            int user = 0;
            JointPos seamjointPos = new JointPos();
            DescPose seamdescPose = new DescPose();
            robot.GetLaserSeamPos(0, offdese, ref seamjointPos, ref seamdescPose, ref tool, ref user, ref startexaxisPos);
            Console.WriteLine($"{seamjointPos.jPos[0]}, {seamjointPos.jPos[1]}, {seamjointPos.jPos[2]}, " +
                            $"{seamjointPos.jPos[3]}, {seamjointPos.jPos[4]}, {seamjointPos.jPos[5]}, " +
                            $"{seamdescPose.tran.x}, {seamdescPose.tran.y}, {seamdescPose.tran.z}, " +
                            $"{seamdescPose.rpy.rx}, {seamdescPose.rpy.ry}, {seamdescPose.rpy.rz}");
            if (ret == 0)
            {
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);
                Console.WriteLine("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            Console.WriteLine($"Number of completions : {i + 1} ");
        }     
    }

Endeffektor-Transparentübertragungsfunktion ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Aktiviert die allgemeine Transparentübertragungsfunktion des Endeffektors
    * @param [in] Aktivierung, 0-deaktiviert, 1-aktiviert
    * @return Fehlercode
    */
    public int SetAxleGenComEnable(int mode)

Endeffektor-Transparentübertragungsfunktion für azyklische Datenübertragung und -empfang
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Endeffektor sendet azyklische Daten und wartet auf Antwort
    * @param [in] len_snd, Länge der zu sendenden Daten
    * @param [in] sndBuff[], zu sendende Daten
    * @param [in] len_rcv, Länge der zu empfangenden Daten
    * @param [out] rcvBuff[], Antwortdaten
    * @return Fehlercode
    */
    public int SndRcvAxleGenComCmdData(int len_snd, int[] sndBuff, int len_rcv, ref int[] rcvdata)

Codebeispiel für azyklische Datenkommunikation des DIO Health Care Moxibustion-Kopfs basierend auf der Endeffektor-Transparentübertragungsfunktion
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    void testAxleGenCom()
    {
        int[] led_on = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
        int[] led_off = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
        int[] version = new int[5]{ 0xAB, 0xBA, 0x11, 0x00, 0x76 };
        int[] state = new int[6] { 0xAB, 0xBA, 0x1B,0x01, 0xAA, 0x2B };
        int[] cycleState = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };

        int[] rcvdata = new int[16];
        int ret = 0;
        int cnt = 1;

        JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
        DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

        JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
        DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        //Endeffektor-Transparentübertragungsfunktion aktivieren
        robot.SetAxleGenComEnable(1);
        robot.SetAxleLuaEnable(1);

        while(cnt<=10)
        { 
            //Versionsnummer auslesen
            ret = robot.SndRcvAxleGenComCmdData(5, version, 10, ref rcvdata);
            Console.WriteLine($" hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}");
            if (ret != 0)
            {
                break;
            }
            Thread.Sleep(1000);
            //Präsenzstatus des Moxibustion-Kopfs auslesen
            ret = robot.SndRcvAxleGenComCmdData(6, state, 6, ref rcvdata);
            Console.WriteLine($" state : {rcvdata[4]}");
            Thread.Sleep(1000);
            //Laser des Moxibustion-Kopfs einschalten
            ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, ref rcvdata);
            Console.WriteLine($"led on rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(4000);
            //Laser des Moxibustion-Kopfs ausschalten
            ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, ref rcvdata);
            Console.WriteLine($"led off rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(1000);
            Console.WriteLine($"***********************complate No. {cnt}  SDK test*****************************");
            cnt++;
        }

    }

Open-Protocol-Lua-Datei herunterladen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Open-Protocol-Lua-Datei herunterladen
    * @param [in] fileName Name der Open-Protocol-Datei "CtrlDev_XXX.lua"
    * @param [in] savePath Pfad zum Speichern der Open-Protocol-Datei
    * @return Fehlercode
    */
    public int OpenLuaDownload(string fileName, string savePath)
    
Open-Protocol-Lua-Datei löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Open-Protocol-Lua-Datei löschen
    * @param [in] fileName Name der zu löschenden Open-Protocol-Lua-Datei "CtrlDev_XXX.lua"
    * @return Fehlercode
    */
    public int OpenLuaDelete(string fileName)
        
Alle Open-Protocol-Lua-Dateien löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Alle Open-Protocol-Lua-Dateien löschen
    * @return Fehlercode
    */
    public int AllOpenLuaDelete()

SDK-Codebeispiel für Open-Protocol-Lua-Dateioperationen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public int TestCtrlOpenLuaOperate()
    {
        int rtn;

        // Lua-Datei auf Roboter hochladen
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        Console.WriteLine($"OpenLuaUpload rtn is {rtn}");
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        Console.WriteLine($"OpenLuaUpload rtn is {rtn}");

        // Lua-Datei von Roboter herunterladen
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        Console.WriteLine($"OpenLuaDownload rtn is {rtn}");
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        Console.WriteLine($"OpenLuaDownload rtn is {rtn}");

        // Steuerungs-Open-Protocol-Lua-Name festlegen
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        Console.WriteLine($"SetCtrlOpenLUAName rtn is {rtn}");
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        Console.WriteLine($"SetCtrlOpenLUAName rtn is {rtn}");

        // Steuerungs-Open-Protocol-Lua-Name abrufen
        string[] name = new string[4];
        rtn = robot.GetCtrlOpenLUAName(ref name);
        Console.WriteLine($"ctrl open lua names : {name[0]}, {name[1]}, {name[2]}, {name[3]}");

        // Open-Protocol-Lua laden und entladen
        rtn = robot.LoadCtrlOpenLUA(1);
        Console.WriteLine($"LoadCtrlOpenLUA rtn is {rtn}");
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        Console.WriteLine($"UnloadCtrlOpenLUA rtn is {rtn}");

        // Bestimmte Lua-Datei und alle Lua-Dateien löschen
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        Console.WriteLine($"OpenLuaDelete rtn is {rtn}");
        rtn = robot.AllOpenLuaDelete();
        Console.WriteLine($"AllOpenLuaDelete rtn is {rtn}");

        return 0;
    }