Roboter-Statusabfrage
=====================

.. toctree::
    :maxdepth: 5

Aktuelle Gelenkposition (Winkel) abrufen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelle Gelenkposition (Winkel) abrufen
    * @param [out] jPos Objekt der Klasse JointPos zum Befüllen mit den sechs Gelenkpositionen, Einheit [°]
    * @return Fehlercode
    */
    int GetActualJointPosDegree(JointPos jPos);

Gelenk-Rückmeldegeschwindigkeit (deg/s) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Rückmeldegeschwindigkeit (deg/s) abrufen
    * @param [out] speed Array (Länge 6) für die Geschwindigkeiten der sechs Gelenke
    * @return Fehlercode
    */
    int GetActualJointSpeedsDegree(Object[] speed);

Gelenk-Rückmeldebeschleunigung (deg/s²) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Rückmeldebeschleunigung (deg/s²) abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] acc Array (Länge 6) für die Beschleunigungen der sechs Gelenke
    * @return Fehlercode
    */
    public int GetActualJointAccDegree(int flag, Object[] acc)

TCP-Befehlsresultierende Geschwindigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TCP-Befehlsresultierende Geschwindigkeit abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] tcp_speed Lineargeschwindigkeit (mm/s)
    * @param [out] ori_speed Orientierungsgeschwindigkeit (°/s)
    * @return Fehlercode
    */
    public int GetTargetTCPCompositeSpeed(int flag, double[] tcp_speed, double[] ori_speed) // Hinweis: double[] als Referenz

TCP-Rückmelderesultierende Geschwindigkeit abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TCP-Rückmelderesultierende Geschwindigkeit abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] tcp_speed Lineargeschwindigkeit (mm/s)
    * @param [out] ori_speed Orientierungsgeschwindigkeit (°/s)
    * @return Fehlercode
    */
    public int GetActualTCPCompositeSpeed(int flag, double[] tcp_speed, double[] ori_speed)

TCP-Befehlsgeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TCP-Befehlsgeschwindigkeit (Komponenten) abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] speed Array (Länge 6) für die Geschwindigkeiten [x, y, z, rx, ry, rz]
    * @return Fehlercode
    */
    public int GetTargetTCPSpeed(int flag, Object[] speed)

TCP-Rückmeldegeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TCP-Rückmeldegeschwindigkeit (Komponenten) abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] speed Array (Länge 6) für die Geschwindigkeiten [x, y, z, rx, ry, rz]
    * @return Fehlercode
    */
    public int GetActualTCPSpeed(int flag, Object[] speed)

Aktuelle Werkzeugpose (TCP) abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelle Werkzeugpose (TCP) abrufen
    * @param [out] desc_pos Objekt der Klasse DescPose zum Befüllen mit der Werkzeugpose
    * @return Fehlercode
    */
    int GetActualTCPPose(DescPose desc_pos);

Nummer des aktuellen Werkzeugkoordinatensystems abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Nummer des aktuellen Werkzeugkoordinatensystems abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] id Array (Länge 1) für die Werkzeugkoordinatensystem-Nummer
    * @return Fehlercode
    */
    int GetActualTCPNum(int flag, int[] id)

Nummer des aktuellen Werkstückkoordinatensystems abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Nummer des aktuellen Werkstückkoordinatensystems abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] id Array (Länge 1) für die Werkstückkoordinatensystem-Nummer
    * @return Fehlercode
    */
    public int GetActualWObjNum(int flag, int[] id)

Aktuelle Pose des Endflansches abrufen
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelle Pose des Endflansches abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] desc_pos Objekt der Klasse DescPose zum Befüllen mit der Flanschpose
    * @return Fehlercode
    */
    public int GetActualToolFlangePose(int flag, DescPose desc_pos)

Aktuelle Gelenkmomente abrufen
+++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelle Gelenkmomente abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] torques Array (Länge 6) für die Gelenkmomente
    * @return Fehlercode
    */
    int GetJointTorques(int flag, Object[] torques);

Systemzeit abrufen
++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Systemzeit abrufen
    * @return List[0]: int Fehlercode; List[1]: double t_ms Zeit in ms
    */
    List<Number> GetSystemClock();

Abfragen, ob die Roboterbewegung abgeschlossen ist
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Abfragen, ob die Roboterbewegung abgeschlossen ist
    * @param [out] state Array (Länge 1) für den Zustand: 0 - nicht abgeschlossen, 1 - abgeschlossen
    * @return Fehlercode
    */
    public int GetRobotMotionDone(int[] state)

Länge der Roboter-Bewegungsbefehlswarteschlange abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Länge der Roboter-Bewegungsbefehlswarteschlange abrufen
    * @param [out] len Array (Länge 1) für die aktuelle Warteschlangenlänge
    * @return Fehlercode
    */
    public int GetMotionQueueLength(int[] len)

Roboter-Not-Halt-Status abrufen
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-Not-Halt-Status abrufen
    * @param [out] state Array (Länge 1) für den Not-Halt-Status: 0 - kein Not-Halt, 1 - Not-Halt aktiv
    * @return Fehlercode
    */
    public int GetRobotEmergencyStopState(int[] state)

Kommunikationsstatus zwischen SDK und Roboter abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kommunikationsstatus zwischen SDK und Roboter abrufen
    * @return int state: 0 - Kommunikation normal, 1 - Kommunikationsstörung
    */
    public int GetSDKComState()

Sicherheitsstopp-Signal abrufen
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Sicherheitsstopp-Signal abrufen
    * @param [out] si0_state Array (Länge 1) für Signal SI0: 0 - inaktiv, 1 - aktiv
    * @param [out] si1_state Array (Länge 1) für Signal SI1: 0 - inaktiv, 1 - aktiv
    * @return Fehlercode
    */
    public int GetSafetyStopState(int[] si0_state, int[] si1_state)

Temperatur der Roboter-Gelenkantriebe (°C) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Temperatur der Roboter-Gelenkantriebe (°C) abrufen
    * @param [out] temperature Array (Länge 6) für die Temperaturen der sechs Antriebe
    * @return Fehlercode
    */
    public int GetJointDriverTemperature(double[] temperature)

Drehmoment der Roboter-Gelenkantriebe (Nm) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Drehmoment der Roboter-Gelenkantriebe (Nm) abrufen
    * @param [out] torque Array (Länge 6) für die Drehmomente der sechs Antriebe
    * @return Fehlercode
    */
    public int GetJointDriverTorque(double[] torque)

Roboter-Echtzeitstatus-Struktur abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-Echtzeitstatus-Struktur abrufen
    * @return ROBOT_STATE_PKG Objekt mit den Echtzeitstatusdaten
    */
    public ROBOT_STATE_PKG GetRobotRealTimeState()

Codebeispiel für Roboter-Statusabfrage
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetStatus(Robot robot)
    {
        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("yangle:"+angle.get(1)+",zangle:"+angle.get(2));

        JointPos j_deg =new JointPos(){};
        robot.GetActualJointPosDegree( j_deg);

        Object[] jointSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetActualJointSpeedsDegree(jointSpeed);

        Object[] jointAcc = new Object[]{0,0,0,0,0,0 };
        robot.GetActualJointAccDegree(0, jointAcc);

        double tcp_speed = 0.0;
        double ori_speed = 0.0;
        robot.GetTargetTCPCompositeSpeed(0, tcp_speed, ori_speed);

        robot.GetActualTCPCompositeSpeed(0, tcp_speed, ori_speed);

        Object[] targetSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetTargetTCPSpeed(0, targetSpeed);

        Object[] actualSpeed =new Object[] {0,0,0,0,0,0 };
        robot.GetActualTCPSpeed(0, actualSpeed);

        DescPose tcp = new DescPose(){};
        robot.GetActualTCPPose(tcp);

        DescPose flange = new DescPose(){};
        robot.GetActualToolFlangePose(0, flange);

        int[] id = {};
        robot.GetActualTCPNum(0, id);

        robot.GetActualWObjNum(0, id);

        List<Number> jtorque=new ArrayList<>();
        jtorque=robot.GetJointTorques(0);

        List<Number> t_ms = new ArrayList<>();
        t_ms=robot.GetSystemClock();

        List<Integer> config = new ArrayList<>();
        config=robot.GetRobotCurJointsConfig();

        int motionDone = 0;
        robot.GetRobotMotionDone(motionDone);

        int[] len ={0 };
        robot.GetMotionQueueLength(len);

        int[] emergState = {0};
        robot.GetRobotEmergencyStopState(emergState);

        int comstate = 0;
        comstate=robot.GetSDKComState();

        int[] si0_state=new int[]{0}, si1_state=new int[]{0};
        robot.GetSafetyStopState(si0_state, si1_state);

        double[] temp =new double[] { 0,0,0,0,0,0 };
        robot.GetJointDriverTemperature(temp);

        double[] torque = new double[]{ 0,0,0,0,0,0 };
        robot.GetJointDriverTorque(torque);

        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        pkg=robot.GetRobotRealTimeState();

        return 0;
    }

Inverse Kinematik berechnen
+++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inverse Kinematik berechnen
    * @param [in] type 0 - absolute Pose (Basiskoordinatensystem), 1 - inkrementelle Pose (Basiskoordinatensystem), 2 - inkrementelle Pose (Werkzeugkoordinatensystem)
    * @param [in] desc_pos Kartesische Pose (DescPose)
    * @param [in] config Gelenkraum-Konfiguration, [-1] - Berechnung basierend auf aktueller Gelenkposition, [0~7] - Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @param [out] joint_pos Objekt der Klasse JointPos zum Befüllen mit den berechneten Gelenkpositionen
    * @return Fehlercode
    */
    int GetInverseKin(int type, DescPose desc_pos, int config, JointPos joint_pos);

Inverse Kinematik mit Referenzposition berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inverse Kinematik unter Verwendung einer Referenz-Gelenkposition berechnen
    * @param [in] posMode 0 - absolute Pose, 1 - relative Pose (Basiskoordinatensystem), 2 - relative Pose (Werkzeugkoordinatensystem)
    * @param [in] desc_pos Kartesische Pose (DescPose)
    * @param [in] joint_pos_ref Referenz-Gelenkposition (JointPos)
    * @param [out] joint_pos Objekt der Klasse JointPos zum Befüllen mit den berechneten Gelenkpositionen
    * @return Fehlercode
    */
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, JointPos joint_pos);

Inverse Kinematik im kartesischen Raum inklusive Erweiterungsachsenposition
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inverse Kinematik im kartesischen Raum inklusive Erweiterungsachsenposition
    * @param [in] type 0 - absolute Pose (Basiskoordinatensystem), 1 - inkrementelle Pose (Basiskoordinatensystem), 2 - inkrementelle Pose (Werkzeugkoordinatensystem)
    * @param [in] desc_pos Kartesische Pose (DescPose)
    * @param [in] exaxis Position der Erweiterungsachse (ExaxisPos)
    * @param [in] tool Werkzeugnummer
    * @param [in] workPiece Werkstücknummer
    * @param [out] joint_pos Objekt der Klasse JointPos zum Befüllen mit den berechneten Gelenkpositionen
    * @return Fehlercode
    */
    public int GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos joint_pos)

Codebeispiel für inverse Kinematik mit Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void  TestInverseKinExaxis(Robot robot)
    {
        DescPose desc=new DescPose(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis=new ExaxisPos(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos =new JointPos();
        DescPose offsetPos =new DescPose();
        ROBOT_STATE_PKG pkg=robot.GetRobotRealTimeState();
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos);
        System.out.printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.J1, jointPos.J2, jointPos.J3, jointPos.J4, jointPos.J5, jointPos.J6);
        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(jointPos, desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, exaxis, -1, 0, offsetPos);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }

Prüfen, ob die inverse Kinematik eine Lösung hat
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Prüfen, ob die inverse Kinematik für eine gegebene Pose eine Lösung hat
    * @param [in] posMode 0 - absolute Pose, 1 - relative Pose (Basiskoordinatensystem), 2 - relative Pose (Werkzeugkoordinatensystem)
    * @param [in] desc_pos Kartesische Pose (DescPose)
    * @param [in] joint_pos_ref Referenz-Gelenkposition (JointPos)
    * @return List<Integer> List[0]: Fehlercode; List[1]: int hasResult 0 - keine Lösung, 1 - Lösung vorhanden
    */
    List<Integer> GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref);

Vorwärtskinematik berechnen
++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Vorwärtskinematik berechnen
    * @param [in] joint_pos Gelenkposition (JointPos)
    * @param [out] desc_pos Objekt der Klasse DescPose zum Befüllen mit der berechneten kartesischen Pose
    * @return Fehlercode
    */
    int GetForwardKin(JointPos joint_pos, DescPose desc_pos);

Codebeispiel für Vorwärts- und inverse Kinematik
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestInverseKin(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        JointPos inverseRtn = new JointPos(){};

        robot.GetInverseKin(0, desc_pos1, -1, inverseRtn);
        robot.GetInverseKinRef(0, desc_pos1, j1, inverseRtn);

        int hasResut = 0;
        robot.GetInverseKinHasSolution(0, desc_pos1, j1);

        DescPose forwordResult = new DescPose(){};
        robot.GetForwardKin(j1, forwordResult);

        return 0;
    }

Daten eines Roboter-Teachingpunkts abfragen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Daten eines Roboter-Teachingpunkts abfragen
    * @param [in] name Name des Punkts (String)
    * @return List<Number> List[0]: Fehlercode; List[1] - List[20]: Punktdaten als double[20] {x, y, z, rx, ry, rz, j1, j2, j3, j4, j5, j6, tool, wobj, speed, acc, e1, e2, e3, e4}
    */
    List<Number> GetRobotTeachingPoint(String name);

DH-Parameter-Kompensationswerte des Roboters abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief DH-Parameter-Kompensationswerte des Roboters abrufen
    * @param dhCompensation Array (Länge 6) zum Befüllen mit den Kompensationswerten (mm) [cmpstD1, cmpstA2, cmpstA3, cmpstD4, cmpstD5, cmpstD6]
    * @return Fehlercode
    */
    public int GetDHCompensation(Object[] dhCompensation)

SN-Code des Steuerkastens abrufen
++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief SN-Code des Steuerkastens abrufen
    * @param [out] SNCode Array (Länge 1) zum Befüllen mit dem SN-Code
    * @return Fehlercode
    */
    int GetRobotSN(String[] SNCode);

Codebeispiel für Teachingpunkt-Abfrage
++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetTeachPoint(Robot robot)
    {
        String name = "P1";
        List<Number> data=new ArrayList<>();
        data = robot.GetRobotTeachingPoint(name);
        System.out.println(name+" name is: "+data.get(0));
        for (int i = 0; i < 20; i++)
        {
            System.out.println("data is: "+ data.get(i+1));
        }

        int[] que_len = {0};
        int rtn = robot.GetMotionQueueLength(que_len);
        System.out.println("GetMotionQueueLength rtn is:"+rtn+", queue length is:"+ que_len[0]);

        Object[] dh = new Object[]{ 0,0,0,0,0,0 };
        int retval = 0;
        retval = robot.GetDHCompensation(dh);
        System.out.println("retval is: "+retval);

        String[] SN = new String[]{""};
        robot.GetRobotSN(SN);
        System.out.println("robot SN is "+SN[0]);
        return 0;
    }

Werkzeugkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeugkoordinatensystem nach ID abrufen
    * @param [in] id Werkzeugkoordinatensystem-Nummer
    * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
    * @return Fehlercode
    */
    int GetToolCoordWithID(int id, DescPose coord)

Werkstückkoordinatensystem nach ID abrufen
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
    * @brief Werkstückkoordinatensystem nach ID abrufen
    * @param [in] id Werkstückkoordinatensystem-Nummer
    * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
    * @return Fehlercode
    */
    public int GetWObjCoordWithID(int id, DescPose coord)

Externes Werkzeugkoordinatensystem nach ID abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
    * @brief Externes Werkzeugkoordinatensystem nach ID abrufen
    * @param [in] id Externes Werkzeugkoordinatensystem-Nummer
    * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
    * @return Fehlercode
    */
    public int GetExToolCoordWithID(int id, DescPose coord)

Erweiterungsachsen-Koordinatensystem nach ID abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
    * @brief Erweiterungsachsen-Koordinatensystem nach ID abrufen
    * @param [in] id Erweiterungsachsen-Koordinatensystem-Nummer
    * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
    * @return Fehlercode
    */
    public int GetExAxisCoordWithID(int id, DescPose coord)

Aktuelles Werkzeugkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Aktuelles Werkzeugkoordinatensystem abrufen
     * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
     * @return Fehlercode
     */
    public int GetCurToolCoord(DescPose coord)

Aktuelles Werkstückkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Aktuelles Werkstückkoordinatensystem abrufen
     * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
     * @return Fehlercode
     */
    public int GetCurWObjCoord(DescPose coord)

Aktuelles externes Werkzeugkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Aktuelles externes Werkzeugkoordinatensystem abrufen
     * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
     * @return Fehlercode
     */
    public int GetCurExToolCoord(DescPose coord)

Aktuelles Erweiterungsachsen-Koordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Aktuelles Erweiterungsachsen-Koordinatensystem abrufen
     * @param [out] coord Objekt der Klasse DescPose zum Befüllen mit den Koordinatenwerten
     * @return Fehlercode
     */
    public int GetCurExAxisCoord(DescPose coord)

Codebeispiel zum Abrufen von Roboter-Koordinatensystemen und Lastdaten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestCoord(Robot robot)
    {
        int id = 1;
        int rtn = 0;
        DescPose toolCoord = new DescPose();
        DescPose extoolCoord = new DescPose();
        DescPose wobjCoord = new DescPose();
        DescPose exAxisCoord = new DescPose();


        robot.GetCurToolCoord(toolCoord);//Werkzeug
        System.out.println("GetToolCoord:"+id+","+
                toolCoord.tran.x+","+ toolCoord.tran.y+","+ toolCoord.tran.z+","+
                toolCoord.rpy.rx+","+ toolCoord.rpy.ry+","+ toolCoord.rpy.rz);


        robot.GetCurWObjCoord(toolCoord);//Werkstück
        System.out.println("GetCurWObjCoord:"+id+","+
                toolCoord.tran.x+","+ toolCoord.tran.y+","+ toolCoord.tran.z+","+
                toolCoord.rpy.rx+","+ toolCoord.rpy.ry+","+ toolCoord.rpy.rz);

        robot.GetCurExToolCoord(toolCoord);//Externes Werkzeug
        System.out.println("GetCurExToolCoord:"+id+","+
                toolCoord.tran.x+","+ toolCoord.tran.y+","+ toolCoord.tran.z+","+
                toolCoord.rpy.rx+","+ toolCoord.rpy.ry+","+ toolCoord.rpy.rz);


        robot.GetCurExAxisCoord(toolCoord);//Erweiterungsachse
        System.out.println("GetCurExToolCoord:"+id+","+
                toolCoord.tran.x+","+ toolCoord.tran.y+","+ toolCoord.tran.z+","+
                toolCoord.rpy.rx+","+ toolCoord.rpy.ry+","+ toolCoord.rpy.rz);


        List<Number> weightT = new ArrayList<>();//Schwerpunkt
        DescTran cogT=new DescTran();
        weightT=robot.GetTargetPayload(0);
        robot.GetTargetPayloadCog(0,cogT);
        System.out.println("GetTargetPayload :"+weightT.get(1).doubleValue()+", "+
                cogT.x+", "+cogT.y+", "+cogT.z);


        robot.GetToolCoordWithID(id, toolCoord);
        System.out.println("GetToolCoordWithID:"+id+","+
                toolCoord.tran.x+","+ toolCoord.tran.y+","+ toolCoord.tran.z+","+
                toolCoord.rpy.rx+","+ toolCoord.rpy.ry+","+ toolCoord.rpy.rz);

        robot.GetWObjCoordWithID(id, wobjCoord);
        System.out.println("GetWObjCoordWithID "+id+", "+
                wobjCoord.tran.x+","+ wobjCoord.tran.y+","+ wobjCoord.tran.z+","+
                wobjCoord.rpy.rx+","+ wobjCoord.rpy.ry+","+ wobjCoord.rpy.rz);


        robot.GetExToolCoordWithID(id, extoolCoord);//Externes Werkzeug
        System.out.println("GetExToolCoordWithID :"+ id+","+
                extoolCoord.tran.x+","+ extoolCoord.tran.y+","+ extoolCoord.tran.z+","+
                extoolCoord.rpy.rx+","+ extoolCoord.rpy.ry+","+ extoolCoord.rpy.rz);

        robot.GetExAxisCoordWithID(id, exAxisCoord);//Erweiterungsachse
        System.out.println("GetExAxisCoordWithID "+id+","+
                exAxisCoord.tran.x+","+ exAxisCoord.tran.y+","+ exAxisCoord.tran.z+","+
                exAxisCoord.rpy.rx+","+ exAxisCoord.rpy.ry+","+ exAxisCoord.rpy.rz);


        double[] weight = new double[1];//Lastschwerpunkt
        DescTran getCog = new DescTran();
        robot.GetTargetPayloadWithID(id, weight, getCog);
        System.out.println("GetTargetPayloadWithID :"+ id+","+ weight[0]+","+
                getCog.x+","+ getCog.y+","+ getCog.z);

        DescPose coordSet0 = new DescPose(0, 0, 0, 0, 0, 0);
        DescPose coordSet = new DescPose(1, 2, 3, 4, 5, 6);
        DescPose etcp = new DescPose(10, 20, 30, 40, 50, 60);
        DescPose etool = new DescPose(0.1, 0.2, 0.3, 0.4, 0.5, 0.6);
        DescTran cog = new DescTran(1, 2, 3);

        robot.SetToolCoord(id, coordSet, 0, 0, 1, 0);
        robot.Sleep(100);
        robot.SetWObjCoord(id, coordSet, 0);
        robot.Sleep(100);
        robot.ExtAxisActiveECoordSys(id, 1, coordSet, 1); //Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden
        robot.Sleep(100);
        rtn = robot.SetExToolCoord(id, etcp, etool);
        robot.Sleep(100);
        rtn = robot.SetLoadWeight(id, 1.5);
        robot.Sleep(500);
        rtn = robot.SetLoadCoord(id, cog);
        robot.Sleep(100);
    }