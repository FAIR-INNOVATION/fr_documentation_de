Roboter-Statusabfrage
===============================

.. toctree::
    :maxdepth: 5

Aktuelle Gelenkposition (Winkel) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die aktuelle Gelenkposition (Winkel) zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] jPos Positionen der sechs Gelenke, Einheit deg.
    * @return  Fehlercode.
    */
    int GetActualJointPosDegree(byte flag, ref JointPos jPos);

Aktuelle Gelenkposition (Bogenmaß) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die aktuelle Gelenkposition (Bogenmaß) zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] jPos Positionen der sechs Gelenke, Einheit rad.
    * @return  Fehlercode.
    */
    int GetActualJointPosRadian(byte flag, ref JointPos jPos);

Gelenk-Rückmeldegeschwindigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Gelenk-Rückmeldegeschwindigkeit in deg/s zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] speed Geschwindigkeiten der sechs Gelenke.
    * @return Fehlercode.
    */
    int GetActualJointSpeedsDegree(byte flag, ref double[] speed);

Gelenk-Rückmeldebeschleunigung abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Gelenk-Rückmeldebeschleunigung in deg/s² zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] acc Beschleunigungen der sechs Gelenke.
    * @return Fehlercode.
    */
    int GetActualJointAccDegree(byte flag, ref double[] acc);

TCP-Sollgeschwindigkeit (resultierend) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die resultierende TCP-Sollgeschwindigkeit zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] tcp_speed Lineare Geschwindigkeit.
    * @param [out] ori_speed Ausrichtungsgeschwindigkeit.
    * @return Fehlercode.
    */
    int GetTargetTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed);

TCP-Istgeschwindigkeit (resultierend) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die resultierende TCP-Istgeschwindigkeit zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] tcp_speed Lineare Geschwindigkeit.
    * @param [out] ori_speed Ausrichtungsgeschwindigkeit.
    * @return Fehlercode.
    */
    int GetActualTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed);

TCP-Sollgeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die TCP-Sollgeschwindigkeit als Komponenten zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] speed Geschwindigkeiten [x, y, z, rx, ry, rz].
    * @return Fehlercode.
    */
    int GetTargetTCPSpeed(byte flag, ref double[] speed);

TCP-Istgeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die TCP-Istgeschwindigkeit als Komponenten zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] speed Geschwindigkeiten [x, y, z, rx, ry, rz].
    * @return Fehlercode.
    */
    int GetActualTCPSpeed(byte flag, ref double[] speed);

Aktuelle Werkzeugpose abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die aktuelle Werkzeugpose zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] desc_pos Werkzeugpose.
    * @return  Fehlercode.
    */
    int GetActualTCPPose(byte flag, ref DescPose desc_pos);

Nummer des aktuellen Werkzeugkoordinatensystems abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die Nummer des aktuellen Werkzeugkoordinatensystems zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] id Nummer des Werkzeugkoordinatensystems.
    * @return  Fehlercode.
    */
    int GetActualTCPNum(byte flag, ref int id);

Nummer des aktuellen Werkstückkoordinatensystems abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die Nummer des aktuellen Werkstückkoordinatensystems zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] id Nummer des Werkstückkoordinatensystems.
    * @return  Fehlercode.
    */
    int GetActualWObjNum(byte flag, ref int id);

Aktuelle Pose des Endflansches abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die aktuelle Pose des Endflansches zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] desc_pos Flanschpose.
    * @return  Fehlercode.
    */
    int GetActualToolFlangePose(byte flag, ref DescPose desc_pos);

Aktuelles Gelenkdrehmoment abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt das aktuelle Gelenkdrehmoment zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] torques Gelenkdrehmomente.
    * @return  Fehlercode.
    */
    int GetJointTorques(byte flag, float[] torques);

Systemzeit abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Systemzeit abrufen
    * @param  [out] t_ms Einheit ms, kann gemäß UTC-Zeit konvertiert werden. Im Fehlerzustand des Roboters gibt GetSystemClock 0 zurück und einen Fehlercode.
    * @return  Fehlercode
    */
    public int GetSystemClock(ref double t_ms)

Systemzeit mit dem Roboter synchronisieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ruft die aktuelle Systemzeit des Hosts ab und sendet sie an den Roboter, um die Systemzeit zu synchronisieren (aufgrund von QNX-Systemeinschränkungen ist die Synchronisationsgenauigkeit auf Minutenebene)
    * @return Fehlercode
    */
    public int SetRobottime()

Codebeispiel zum Synchronisieren der Systemzeit mit dem Roboter
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void testSetAndGetRobotTime()
    {
        double t_ms = 0.0;

        int ret = robot.GetSystemClock(ref t_ms);
        if (ret == 0)
        {
            Console.WriteLine($"system clock : {t_ms}");
            // Millisekunden-Zeitstempel in DateTime (UTC-Zeit) umwandeln
            DateTime utcTime = new DateTime(1970, 1, 1, 0, 0, 0, DateTimeKind.Utc).AddMilliseconds(t_ms);
            Console.WriteLine($"BEFORE UTC Time   : {utcTime:yyyy-MM-dd HH:mm:ss}");
        }
        else
        {
            Console.WriteLine($"GetSystemClock failed,ret:{ret}");
        }

        robot.SetRobottime();

        // Roboterzeit nach der Einstellung abrufen
        double t_ms_after = 0;
        ret = robot.GetSystemClock(ref t_ms_after);
        if (ret == 0)
        {
            Console.WriteLine($"system clock : {t_ms}");
            DateTime robotTimeAfter = DateTimeOffset.FromUnixTimeMilliseconds((long)t_ms_after).UtcDateTime;

            // PC-Zeit vor der Einstellung abrufen (als erwarteter Wert)
            DateTime pcTimeBefore = DateTime.Now;

            // Sowohl die erwartete Zeit (PC-Zeit) als auch die Roboterzeit auf Minuten kürzen
            DateTime pcMinute = new DateTime(pcTimeBefore.Year, pcTimeBefore.Month, pcTimeBefore.Day,
                                                pcTimeBefore.Hour, pcTimeBefore.Minute, 0, DateTimeKind.Utc);
            DateTime robotMinute = new DateTime(robotTimeAfter.Year, robotTimeAfter.Month, robotTimeAfter.Day,
                                                robotTimeAfter.Hour, robotTimeAfter.Minute, 0, DateTimeKind.Utc);

            // Konsistenz vergleichen
            bool isConsistent = (pcMinute == robotMinute);
            if (isConsistent)
            {
                Console.WriteLine($"Consistent     | PC time: {pcMinute:yyyy-MM-dd HH:mm}  | Robot time: {robotMinute:yyyy-MM-dd HH:mm}");
            }
            else
            {
                Console.WriteLine($"[Inconsistent | PC time: {pcMinute:yyyy-MM-dd HH:mm}  | Robot time: {robotMinute:yyyy-MM-dd HH:mm}");
            }
        }
        else
        {
            Console.WriteLine($"GetSystemClock failed,ret:{ret}");
        }
    }    

Abfragen, ob die Roboterbewegung abgeschlossen ist
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Fragt ab, ob die Roboterbewegung abgeschlossen ist.
    * @param  [out] state 0-nicht abgeschlossen, 1-abgeschlossen.
    * @return  Fehlercode.
    */
    int GetRobotMotionDone(ref byte state);

Länge der Roboter-Bewegungswarteschlange abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Länge der Roboter-Bewegungswarteschlange zurück.
    * @param [out] len Länge der Warteschlange.
    * @return Fehlercode.
    */
    int GetMotionQueueLength(ref int len);

Roboter-Not-Halt-Status abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt den Roboter-Not-Halt-Status zurück.
    * @param [out] state Not-Halt-Status, 0-nicht aktiv, 1-aktiv.
    * @return Fehlercode.
    */
    int GetRobotEmergencyStopState(ref byte state);

Kommunikationsstatus zwischen SDK und Roboter abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt den Kommunikationsstatus zwischen SDK und Roboter zurück.
    * @param [out] state Kommunikationsstatus, 0-normal, 1-gestört.
    */
    int GetSDKComState(ref int state);

Sicherheitsstopp-Signale abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Sicherheitsstopp-Signale zurück.
    * @param [out] si0_state Sicherheitsstopp-Signal SI0, 0-inaktiv, 1-aktiv.
    * @param [out] si1_state Sicherheitsstopp-Signal SI1, 0-inaktiv, 1-aktiv.
    */
    int GetSafetyStopState(ref byte si0_state, ref byte si1_state);

Temperatur der Roboter-Gelenkantriebe (°C) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Temperatur der Roboter-Gelenkantriebe in °C zurück.
    * @param [out] temperature Array der Gelenktemperaturen.
    * @return Fehlercode.
    */
    int GetJointDriverTemperature(double[] temperature);

Drehmoment der Roboter-Gelenkantriebe (Nm) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt das Drehmoment der Roboter-Gelenkantriebe in Nm zurück.
    * @param [out] torque Array der Gelenkdrehmomente.
    * @return Fehlercode.
    */
    int GetJointDriverTorque(double[] torque);

Die neuesten Echtzeit-Roboterstatusdaten abrufen (Interne Mechanismusänderung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Die neuesten Echtzeit-Roboterstatusdaten abrufen (interner Thread aktualisiert kontinuierlich, diese Schnittstelle gibt direkt zwischengespeicherte Daten zurück)
    * @param [out] pkg Referenzparameter zum Empfangen der Roboterstatusdaten (ROBOT_STATE_PKG-Struktur)
    * @return Gibt bei Erfolg 0 zurück; bei Fehler einen negativen Fehlercode (z. B. Netzwerkkommunikationsfehler)
    */
    public int GetRobotRealTimeState(ref ROBOT_STATE_PKG pkg)

Codebeispiel für Roboter-Statusabfragen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button29_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        double yangle = 0, zangle = 0;
        robot.GetRobotInstallAngle(ref yangle, ref zangle);
        Console.WriteLine($"yangle:{yangle},zangle:{zangle}");

        JointPos j_deg = new JointPos(0,0,0,0,0,0);
        robot.GetActualJointPosDegree(0, ref j_deg);
        Console.WriteLine($"joint pos deg:{j_deg.jPos[0]},{j_deg.jPos[1]},{j_deg.jPos[2]},{j_deg.jPos[3]},{j_deg.jPos[4]},{j_deg.jPos[5]}");

        double[] jointSpeed = new double[6];
        robot.GetActualJointSpeedsDegree(0, ref jointSpeed);
        Console.WriteLine($"joint speeds deg:{jointSpeed[0]},{jointSpeed[1]},{jointSpeed[2]},{jointSpeed[3]},{jointSpeed[4]},{jointSpeed[5]}");

        double[] jointAcc = new double[6];
        robot.GetActualJointAccDegree(0, ref jointAcc);
        Console.WriteLine($"joint acc deg:{jointAcc[0]},{jointAcc[1]},{jointAcc[2]},{jointAcc[3]},{jointAcc[4]},{jointAcc[5]}");

        double tcp_speed = 0, ori_speed = 0;
        robot.GetTargetTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        robot.GetActualTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        double[] targetSpeed = new double[6];
        robot.GetTargetTCPSpeed(0,ref targetSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {targetSpeed[0]},{targetSpeed[1]},{targetSpeed[2]},{targetSpeed[3]},{targetSpeed[4]},{targetSpeed[5]}");

        double[] actualSpeed = new double[6];
        robot.GetActualTCPSpeed(0, ref actualSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {actualSpeed[0]},{actualSpeed[1]},{actualSpeed[2]},{actualSpeed[3]},{actualSpeed[4]},{actualSpeed[5]}");

        DescPose tcp = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualTCPPose(0, ref tcp);
        Console.WriteLine($"tcp pose:{tcp.tran.x},{tcp.tran.y},{tcp.tran.z},{tcp.rpy.rx},{tcp.rpy.ry},{tcp.rpy.rz}");

        DescPose flange = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualToolFlangePose(0, ref flange);
        Console.WriteLine($"flange pose:{flange.tran.x},{flange.tran.y},{flange.tran.z},{flange.rpy.rx},{flange.rpy.ry},{flange.rpy.rz}");

        int id = 0;
        robot.GetActualTCPNum(0, ref id);
        Console.WriteLine($"tcp num:{id}");

        robot.GetActualWObjNum(0, ref id);
        Console.WriteLine($"wobj num:{id}");

        double[] jtorque = new double[6];
        robot.GetJointTorques(0, jtorque);
        Console.WriteLine($"torques:{jtorque[0]},{jtorque[1]},{jtorque[2]},{jtorque[3]},{jtorque[4]},{jtorque[5]}");

        double t_ms = 0;
        robot.GetSystemClock(ref t_ms);
        Console.WriteLine($"system clock:{t_ms}");

        int config = 0;
        robot.GetRobotCurJointsConfig(ref config);
        Console.WriteLine($"joint config:{config}");

        byte motionDone = 0;
        robot.GetRobotMotionDone(ref motionDone);
        Console.WriteLine($"GetRobotMotionDone :{motionDone}");

        int len = 0;
        robot.GetMotionQueueLength(ref len);
        Console.WriteLine($"GetMotionQueueLength :{len}");

        byte emergState = 0;
        robot.GetRobotEmergencyStopState(ref emergState);
        Console.WriteLine($"GetRobotEmergencyStopState :{emergState}");

        int comstate = 0;
        robot.GetSDKComState(ref comstate);
        Console.WriteLine($"GetSDKComState :{comstate}");

        byte si0_state = 0, si1_state = 0;
        robot.GetSafetyStopState(ref si0_state, ref si1_state);
        Console.WriteLine($"GetSafetyStopState :{si0_state} {si1_state}");

        double[] temp = new double[6];
        robot.GetJointDriverTemperature(temp);
        Console.WriteLine($"Temperature:{temp[0]},{temp[1]},{temp[2]},{temp[3]},{temp[4]},{temp[5]}");

        double[] torque = new double[6];
        robot.GetJointDriverTorque(torque);
        Console.WriteLine($"torque:{torque[0]},{torque[1]},{torque[2]},{torque[3]},{torque[4]},{torque[5]}");

        robot.GetRobotRealTimeState(ref pkg);
    }

Inverse Kinematik berechnen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Berechnet die inverse Kinematik.
    * @param  [in] type 0-absolute Pose (Basiskoordinatensystem), 1-inkrementelle Pose (Basiskoordinatensystem), 2-inkrementelle Pose (Werkzeugkoordinatensystem).
    * @param  [in] desc_pos Kartesische Pose.
    * @param  [in] config Gelenkraumkonfiguration, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen.
    * @param  [out] joint_pos Gelenkposition.
    * @return  Fehlercode.
    */
    int GetInverseKin(int type, DescPose desc_pos, int config, ref JointPos joint_pos);

Inverse Kinematik berechnen (mit Referenzposition)
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Berechnet die inverse Kinematik unter Verwendung einer Referenz-Gelenkposition, um die Lösbarkeit zu prüfen.
    * @param  [in] type 0-absolute Pose (Basiskoordinatensystem), 1-inkrementelle Pose (Basiskoordinatensystem), 2-inkrementelle Pose (Werkzeugkoordinatensystem).
    * @param  [in] desc_pos Kartesische Pose.
    * @param  [in] joint_pos_ref Referenz-Gelenkposition.
    * @param  [out] joint_pos Berechnete Gelenkposition (falls lösbar).
    * @return  Fehlercode.
    */
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref JointPos joint_pos);

Inverse Kinematik (mit Erweiterungsachsenposition) berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Berechnet die inverse Kinematik, einschließlich der Erweiterungsachsenposition im kartesischen Raum.
    * @param [in] type 0-absolute Pose (Basiskoordinatensystem), 1-inkrementelle Pose (Basiskoordinatensystem), 2-inkrementelle Pose (Werkzeugkoordinatensystem).
    * @param [in] desc_pos Kartesische Pose.
    * @param [in] exaxis Position der Erweiterungsachse.
    * @param [in] tool Werkzeugnummer.
    * @param [in] workPiece Werkstücknummer.
    * @param [out] joint_pos Gelenkposition.
    * @param [in] config -1: automatische Lösung, 0-7 entsprechen acht Lösungssätzen
    * @return Fehlercode.
    */
    public int GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, ref JointPos joint_pos, int config = -1);

Codebeispiel für inverse Kinematik mit Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    public void TestInverseKinExaxis()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        robot.GetRobotRealTimeState(ref pkg);
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;

        DescPose desc = new DescPose(-547.469, -47.361, 184.149, 169.843, 4.579, 82.557);
        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        JointPos jointPos = new JointPos(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, ref jointPos, 0);
        Console.WriteLine($"GetInverseKinExaxis joint is {jointPos.jPos[0]}, {jointPos.jPos[1]}, {jointPos.jPos[2]}, {jointPos.jPos[3]}, {jointPos.jPos[4]}, {jointPos.jPos[5]}");
    }

Lösbarkeit der inversen Kinematik prüfen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Prüft, ob die inverse Kinematik für eine gegebene Referenz-Gelenkposition lösbar ist.
    * @param [in] posMode 0 absolute Pose, 1 relative Pose - Basiskoordinatensystem, 2 relative Pose - Werkzeugkoordinatensystem.
    * @param [in] desc_pos Kartesische Pose.
    * @param [in] joint_pos_ref Referenz-Gelenkposition.
    * @param [out] hasResult 0-keine Lösung, 1-Lösung vorhanden.
    * @return Fehlercode.
    */
    int GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref bool hasResult);

Vorwärtskinematik berechnen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Berechnet die Vorwärtskinematik.
    * @param  [in] joint_pos Gelenkposition.
    * @param  [out] desc_pos Kartesische Pose.
    * @return  Fehlercode.
    */
    int GetForwardKin(JointPos joint_pos, ref DescPose desc_pos);

Codebeispiel für Roboter-Vorwärts-/Inverskinematik
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button30_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);

        JointPos inverseRtn = new JointPos(0, 0, 0, 0, 0, 0);

        robot.GetInverseKin(0, desc_pos1, -1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKin rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");
        robot.GetInverseKinRef(0,  desc_pos1, j1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKinRef rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");

        bool hasResut = false;
        robot.GetInverseKinHasSolution(0,  desc_pos1,  j1, ref hasResut);
        Console.WriteLine($"dcs1 GetInverseKinRef result {hasResut}");

        DescPose forwordResult = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetForwardKin(j1, ref forwordResult);
        Console.WriteLine($"jpos1 forwordResult rtn is {forwordResult.tran.x} {forwordResult.tran.y} {forwordResult.tran.z} {forwordResult.rpy.rx} {forwordResult.rpy.ry} {forwordResult.rpy.rz}");
    }

Teachpunkt-Daten abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Daten eines Robot-Teachpunkts zurück.
    * @param [in] name Punktname.
    * @param [out] data Punktdaten double[20] {x, y, z, rx, ry, rz, j1, j2, j3, j4, j5, j6, tool, wobj, speed, acc, e1, e2, e3, e4}.
    * @return Fehlercode.
    */
    int GetRobotTeachingPoint(string name, ref double[] data);

DH-Parameter-Kompensationswerte abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Kompensationswerte der Roboter-DH-Parameter zurück.
    * @param [out] dhCompensation DH-Parameter-Kompensationswerte in mm [cmpstD1, cmpstA2, cmpstA3, cmpstD4, cmpstD5, cmpstD6].
    * @return Fehlercode.
    */
    int GetDHCompensation(ref double[] dhCompensation);

SN-Code des Steuerschranks abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt den SN-Code des Steuerschranks zurück.
    * @param [out] SNCode SN-Code des Steuerschranks.
    * @return Fehlercode.
    */
    int GetRobotSN(ref string SNCode);

Codebeispiel für das Abrufen von Teachpunkt-Daten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button31_Click(object sender, EventArgs e)
    {
        string name = "A0";
        double[] data = new double[20];
        int rtn = robot.GetRobotTeachingPoint(name, ref data);
        Console.WriteLine(" {0} name is: {1} \n", rtn, name);
        for (int i = 0; i < 20; i++)
        {
            Console.WriteLine("data is: {0} \n", data[i]);
        }

        int que_len = 0;
        rtn = robot.GetMotionQueueLength(ref que_len);
        Console.WriteLine("GetMotionQueueLength rtn is: {0}, queue length is: {1} \n", rtn, que_len);

        double[] dh = { 0, 0, 0, 0, 0, 0 };
        int retval = 0;
        retval = robot.GetDHCompensation(ref dh);
        Console.WriteLine($"retval is  {retval}");
        Console.WriteLine($"dh is {dh[0]}, {dh[1]}, {dh[2]}, {dh[3]}, {dh[4]}, {dh[5]}");
        string SN = "";
        robot.GetRobotSN(ref SN);
        Console.WriteLine($"robot SN is  {SN}");
    }

Werkzeugkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Ruft das Werkzeugkoordinatensystem nach ID ab
    * @param [in] id Nummer des Werkzeugkoordinatensystems
    * @param [out] coord Werte des Koordinatensystems
    * @param [out] type Werkzeugtyp: 0-Werkzeug; 1-Sensor
    * @param [out] install Installationsposition: 0-Roboterende; 1-außerhalb des Roboters
    * @param [out] toolID Werkzeug-ID
    * @param [out] loadNo Lastnummer
    * @return Fehlercode
    */
    int GetToolCoordWithID(int id, ref DescPose coord, ref int type, ref int install, ref int toolID, ref int loadNo)

Werkstückkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Ruft das Werkstückkoordinatensystem nach ID ab
    * @param [in] id Nummer des Werkstückkoordinatensystems
    * @param [out] coord Werte des Koordinatensystems
    * @param [out] refFrame Referenzkoordinatensystem
    * @return Fehlercode
    */
    public int GetWObjCoordWithID(int id, ref DescPose coord, ref int refFrame)

Externes Werkzeugkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Ruft das externe Werkzeugkoordinatensystem nach ID ab
    * @param [in] id Nummer des externen Werkzeugkoordinatensystems, 20-39 entsprechen den externen Werkzeugkoordinatensystemen 0-19
    * @param [out] coord TCP-Pose des festen externen Werkzeugs am Roboter
    * @param [out] tcoord Pose des am Roboterende montierten Werkstückkoordinatensystems
    * @return Fehlercode
    */
    public int GetExToolCoordWithID(int id, ref DescPose coord, ref DescPose tcoord)

Erweitertes Achsenkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Ruft das erweiterte Achsenkoordinatensystem nach ID ab
    * @param [in] id Nummer des externen Werkzeugkoordinatensystems
    * @param [out] coord Werte des Koordinatensystems
    * @param [out] axisCoordNum Erweiterte Achsnummer; bit0-bit3 entsprechen den erweiterten Achsen 1-4; z.B. entspricht axisCoordNum-Wert 3 den erweiterten Achsen [1, 2]
    * @param [out] calibFlag Kalibrierungsflag; 0-nicht kalibriert; 1-kalibriert
    * @return Fehlercode
    */
    public int GetExAxisCoordWithID(int id, ref DescPose coord, ref int axisCoordNum, ref int calibFlag)

Aktuelles Werkzeugkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    /**
     * @brief Gibt das aktuelle Werkzeugkoordinatensystem zurück.
     * @param [out] coord Koordinatenwerte.
     * @return Fehlercode.
     */
    public int GetCurToolCoord(ref DescPose coord);

Aktuelles Werkstückkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    /**
     * @brief Gibt das aktuelle Werkstückkoordinatensystem zurück.
     * @param [out] coord Koordinatenwerte.
     * @return Fehlercode.
     */
    public int GetCurWObjCoord(ref DescPose coord);

Aktuelles externes Werkzeugkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    /**
     * @brief Gibt das aktuelle externe Werkzeugkoordinatensystem zurück.
     * @param [out] coord Koordinatenwerte.
     * @return Fehlercode.
     */
    public int GetCurExToolCoord(ref DescPose coord);

Aktuelles Erweiterungsachsen-Koordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    /**
     * @brief Gibt das aktuelle Erweiterungsachsen-Koordinatensystem zurück.
     * @param [out] coord Koordinatenwerte.
     * @return Fehlercode.
     */
    public int GetCurExAxisCoord(ref DescPose coord);

Codebeispiel zum Abrufen von Koordinaten nach ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: csharp
    :linenos:

    public int TestCoord()
    {
        int rtn;
        int id = 1;

        // GetToolCoordWithID
        DescPose toolCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int type = 0, install = 0, toolID = 0, loadNo = 0;
        rtn = robot.GetToolCoordWithID(id, ref toolCoord, ref type, ref install, ref toolID, ref loadNo);
        Console.WriteLine("GetToolCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, type={7}, install={8}, toolID={9}, loadNo={10}",
            id, toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type, install, toolID, loadNo);

        // GetWObjCoordWithID
        DescPose wobjCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int refFrame = 0;
        rtn = robot.GetWObjCoordWithID(id, ref wobjCoord, ref refFrame);
        Console.WriteLine("GetWObjCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, refFrame={7}",
            id, wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame);

        // GetExToolCoordWithID
        DescPose extoolCoord = new DescPose(0, 0, 0, 0, 0, 0);
        DescPose exworkpieceCoord = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.GetExToolCoordWithID(21, ref extoolCoord, ref exworkpieceCoord);
        Console.WriteLine("GetExToolCoordWithID 21, {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        Console.WriteLine("  tcoord: {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);

        // GetExAxisCoordWithID
        DescPose exAxisCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int axisCoordNum = 0, calibFlag = 0;
        rtn = robot.GetExAxisCoordWithID(id, ref exAxisCoord, ref axisCoordNum, ref calibFlag);
        Console.WriteLine("GetExAxisCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, axisCoordNum={7}, calibFlag={8}",
            id, exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum, calibFlag);

        // GetTargetPayloadWithID
        double weight = 0.0;
        DescTran cog = new DescTran(0, 0, 0);
        rtn = robot.GetTargetPayloadWithID(id, ref weight, ref cog);
        Console.WriteLine("GetTargetPayloadWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3}",
            id, weight, cog.x, cog.y, cog.z);

        // GetCurToolCoord
        rtn = robot.GetCurToolCoord(ref toolCoord);
        Console.WriteLine("GetCurToolCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);

        // GetCurWObjCoord
        rtn = robot.GetCurWObjCoord(ref wobjCoord);
        Console.WriteLine("GetCurWObjCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);

        // GetCurExToolCoord
        rtn = robot.GetCurExToolCoord(ref extoolCoord);
        Console.WriteLine("GetCurExToolCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);

        // GetCurExAxisCoord
        rtn = robot.GetCurExAxisCoord(ref exAxisCoord);
        Console.WriteLine("GetCurExAxisCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);

        // GetTargetPayload / GetTargetPayloadCog
        double weightT = 0.0;
        DescTran cogT = new DescTran(0, 0, 0);
        robot.GetTargetPayload(0, ref weightT);
        robot.GetTargetPayloadCog(0, ref cogT);
        Console.WriteLine("GetTargetPayload {0:F3} {1:F3} {2:F3} {3:F3}",
            weightT, cogT.x, cogT.y, cogT.z);

        // SetToolCoord
        DescPose coordSet = new DescPose(0, 1, 2, 3, 4, 5);
        rtn = robot.SetToolCoord(1, coordSet, 0, 0, 1, 0);
        Console.WriteLine("SetToolCoord(1) rtn={0}", rtn);

        // SetWObjCoord
        rtn = robot.SetWObjCoord(1, coordSet, 0);
        Console.WriteLine("SetWObjCoord(1) rtn={0}", rtn);

        // SetLoadWeight + SetLoadCoord
        rtn = robot.SetLoadWeight(1, 1.3f);
        Console.WriteLine("SetLoadWeight(1,1.3) rtn={0}", rtn);

        DescTran loadCog = new DescTran(10, 20, 30);
        rtn = robot.SetLoadCoord(1, loadCog);
        Console.WriteLine("SetLoadCoord(1,10,20,30) rtn={0}", rtn);

        // SetExToolCoord
        DescPose etcp = new DescPose(0, 0, 100, 0, 0, 0);
        DescPose etool = new DescPose(0, 0, 50, 0, 0, 0);
        rtn = robot.SetExToolCoord(21, etcp, etool);
        Console.WriteLine("SetExToolCoord(21) rtn={0}", rtn);
        // SetExToolList
        rtn = robot.SetExToolList(21, etcp, etool);
        Console.WriteLine("SetExToolList(21) rtn={0}", rtn);

        // ExtAxisActiveECoordSys
        rtn = robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        Console.WriteLine("ExtAxisActiveECoordSys(1,1,..,1) rtn={0}", rtn);

        return 0;
    }