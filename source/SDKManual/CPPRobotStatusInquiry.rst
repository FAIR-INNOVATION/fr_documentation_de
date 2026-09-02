Roboter-Statusabfrage
===============================

.. toctree::
    :maxdepth: 5

Aktuelle Gelenkposition (Winkel) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt die aktuelle Gelenkposition (Winkel) zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] jPos Positionen der sechs Gelenke, Einheit deg.
    * @return  Fehlercode.
    */
    errno_t GetActualJointPosDegree(uint8_t flag, JointPos *jPos);

Gelenk-Rückmeldegeschwindigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die Gelenk-Rückmeldegeschwindigkeit in deg/s zurück.
     * @param  [in] flag 0-blockierend, 1-nicht blockierend.
     * @param  [out] speed Geschwindigkeiten der sechs Gelenke.
     * @return  Fehlercode.
     */
    errno_t GetActualJointSpeedsDegree(uint8_t flag, float speed[6]);

Gelenk-Rückmeldebeschleunigung abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die Gelenk-Rückmeldebeschleunigung in deg/s² zurück.
     * @param  [in] flag 0-blockierend, 1-nicht blockierend.
     * @param  [out] acc Beschleunigungen der sechs Gelenke.
     * @return  Fehlercode.
     */
    errno_t GetActualJointAccDegree(uint8_t flag, float acc[6]);

TCP-Soll-Resultierendegeschwindigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die resultierende TCP-Sollgeschwindigkeit zurück.
     * @param  [in] flag 0-blockierend, 1-nicht blockierend.
     * @param  [out] tcp_speed Lineare Geschwindigkeit.
     * @param  [out] ori_speed Ausrichtungsgeschwindigkeit.
     * @return  Fehlercode.
     */
    errno_t GetTargetTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

TCP-Ist-Resultierendegeschwindigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die resultierende TCP-Istgeschwindigkeit zurück.
     * @param  [in] flag 0-blockierend, 1-nicht blockierend.
     * @param  [out] tcp_speed Lineare Geschwindigkeit.
     * @param  [out] ori_speed Ausrichtungsgeschwindigkeit.
     * @return  Fehlercode.
     */
    errno_t GetActualTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

TCP-Sollgeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die TCP-Sollgeschwindigkeit als Komponenten zurück.
     * @param  [in] flag 0-blockierend, 1-nicht blockierend.
     * @param  [out] speed Geschwindigkeiten [x, y, z, rx, ry, rz].
     * @return  Fehlercode.
     */
    errno_t GetTargetTCPSpeed(uint8_t flag, float speed[6]);

TCP-Istgeschwindigkeit (Komponenten) abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die TCP-Istgeschwindigkeit als Komponenten zurück.
     * @param  [in] flag 0-blockierend, 1-nicht blockierend.
     * @param  [out] speed Geschwindigkeiten [x, y, z, rx, ry, rz].
     * @return  Fehlercode.
     */
    errno_t GetActualTCPSpeed(uint8_t flag, float speed[6]);

Aktuelle Werkzeugpose abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt die aktuelle Werkzeugpose zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] desc_pos Werkzeugpose.
    * @return  Fehlercode.
    */
    errno_t GetActualTCPPose(uint8_t flag, DescPose *desc_pos);

Nummer des aktuellen Werkzeugkoordinatensystems abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt die Nummer des aktuellen Werkzeugkoordinatensystems zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] id Nummer des Werkzeugkoordinatensystems.
    * @return  Fehlercode.
    */
    errno_t GetActualTCPNum(uint8_t flag, int *id);

Nummer des aktuellen Werkstückkoordinatensystems abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt die Nummer des aktuellen Werkstückkoordinatensystems zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] id Nummer des Werkstückkoordinatensystems.
    * @return  Fehlercode.
    */
    errno_t GetActualWObjNum(uint8_t flag, int *id);

Aktuelle Pose des Endflansches abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt die aktuelle Pose des Endflansches zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] desc_pos Flanschpose.
    * @return  Fehlercode.
    */
    errno_t GetActualToolFlangePose(uint8_t flag, DescPose *desc_pos);

Aktuelles Gelenkdrehmoment abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt das aktuelle Gelenkdrehmoment zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] torques Gelenkdrehmomente.
    * @return  Fehlercode.
    */
    errno_t GetJointTorques(uint8_t flag, float torques[6]);

Systemzeit abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt die Systemzeit zurück.
    * @param  [out] t_ms Zeit in Millisekunden.
    * @return  Fehlercode.
    */
    errno_t GetSystemClock(float *t_ms);

Abfragen, ob die Roboterbewegung abgeschlossen ist
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fragt ab, ob die Roboterbewegung abgeschlossen ist.
    * @param  [out] state 0-nicht abgeschlossen, 1-abgeschlossen.
    * @return  Fehlercode.
    */
    errno_t GetRobotMotionDone(uint8_t *state);

Länge der Roboter-Bewegungswarteschlange abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die Länge der Roboter-Bewegungswarteschlange zurück.
     * @param  [out] len Länge der Warteschlange.
     * @return  Fehlercode.
     */
    errno_t GetMotionQueueLength(int *len);

Roboter-Not-Halt-Status abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt den Roboter-Not-Halt-Status zurück.
    * @param [out] state Not-Halt-Status, 0-nicht aktiv, 1-aktiv.
    * @return Fehlercode.
    */
    errno_t GetRobotEmergencyStopState(uint8_t *state);

Kommunikationsstatus zwischen SDK und Roboter abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt den Kommunikationsstatus zwischen SDK und Roboter zurück.
    * @param [out] state Kommunikationsstatus, 0-normal, 1-gestört.
    */
    errno_t GetSDKComState(int *state);

Sicherheitsstopp-Signale abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Sicherheitsstopp-Signale zurück.
    * @param [out] si0_state Sicherheitsstopp-Signal SI0, 0-inaktiv, 1-aktiv.
    * @param [out] si1_state Sicherheitsstopp-Signal SI1, 0-inaktiv, 1-aktiv.
    */
    errno_t GetSafetyStopState(uint8_t *si0_state, uint8_t *si1_state);

Temperatur der Roboter-Gelenkantriebe (°C) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Temperatur der Roboter-Gelenkantriebe in °C zurück.
    * @param [out] temperature Array der Gelenktemperaturen.
    * @return Fehlercode.
    */
    errno_t GetJointDriverTemperature(double temperature[]);

Drehmoment der Roboter-Gelenkantriebe (Nm) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt das Drehmoment der Roboter-Gelenkantriebe in Nm zurück.
    * @param [out] torque Array der Gelenkdrehmomente.
    * @return Fehlercode.
    */
    errno_t GetJointDriverTorque(double torque[]);

Roboter-Echtzeitstatus-Struktur abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Roboter-Echtzeitstatus-Struktur zurück.
    * @param [out] pkg Roboter-Echtzeitstatus-Struktur.
    * @return Fehlercode.
    */
    errno_t GetRobotRealTimeState(ROBOT_STATE_PKG *pkg);

Codebeispiel für Roboter-Statusabfragen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetStatus(void)
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
      float yangle, zangle;
      robot.GetRobotInstallAngle(&yangle, &zangle);
      printf("yangle:%f,zangle:%f\n", yangle, zangle);
      JointPos j_deg = {};
      robot.GetActualJointPosDegree(0, &j_deg);
      printf("joint pos deg:%f,%f,%f,%f,%f,%f\n", j_deg.jPos[0], j_deg.jPos[1], j_deg.jPos[2], j_deg.jPos[3], j_deg.jPos[4], j_deg.jPos[5]);
      float jointSpeed[6] = { 0.0 };
      robot.GetActualJointSpeedsDegree(0, jointSpeed);
      printf("joint speeds deg:%f,%f,%f,%f,%f,%f\n", jointSpeed[0], jointSpeed[1], jointSpeed[2], jointSpeed[3], jointSpeed[4], jointSpeed[5]);
      float jointAcc[6] = { 0.0 };
      robot.GetActualJointAccDegree(0, jointAcc);
      printf("joint acc deg:%f,%f,%f,%f,%f,%f\n", jointAcc[0], jointAcc[1], jointAcc[2], jointAcc[3], jointAcc[4], jointAcc[5]);
      float tcp_speed = 0.0;
      float ori_speed = 0.0;
      robot.GetTargetTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetTargetTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      robot.GetActualTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetActualTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      float targetSpeed[6] = { 0.0 };
      robot.GetTargetTCPSpeed(0, targetSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", targetSpeed[0], targetSpeed[1], targetSpeed[2], targetSpeed[3], targetSpeed[4], targetSpeed[5]);
      float actualSpeed[6] = { 0.0 };
      robot.GetActualTCPSpeed(0, actualSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", actualSpeed[0], actualSpeed[1], actualSpeed[2], actualSpeed[3], actualSpeed[4], actualSpeed[5]);
      DescPose tcp = {};
      robot.GetActualTCPPose(0, &tcp);
      printf("tcp pose:%f,%f,%f,%f,%f,%f\n", tcp.tran.x, tcp.tran.y, tcp.tran.z, tcp.rpy.rx, tcp.rpy.ry, tcp.rpy.rz);
      DescPose flange = {};
      robot.GetActualToolFlangePose(0, &flange);
      printf("flange pose:%f,%f,%f,%f,%f,%f\n", flange.tran.x, flange.tran.y, flange.tran.z, flange.rpy.rx, flange.rpy.ry, flange.rpy.rz);
      int id = 0;
      robot.GetActualTCPNum(0, &id);
      printf("tcp num:%d\n", id);
      robot.GetActualWObjNum(0, &id);
      printf("wobj num:%d\n", id);
      float jtorque[6] = { 0.0 };
      robot.GetJointTorques(0, jtorque);
      printf("torques:%f,%f,%f,%f,%f,%f\n", jtorque[0], jtorque[1], jtorque[2], jtorque[3], jtorque[4], jtorque[5]);
      float t_ms = 0.0;
      robot.GetSystemClock(&t_ms);
      printf("system clock:%f\n", t_ms);
      int config = 0;
      robot.GetRobotCurJointsConfig(&config);
      printf("joint config:%d\n", config);
      uint8_t motionDone = 0;
      robot.GetRobotMotionDone(&motionDone);
      printf("GetRobotMotionDone :%d\n", motionDone);
      int len = 0;
      robot.GetMotionQueueLength(&len);
      printf("GetMotionQueueLength :%d\n", len);
      uint8_t emergState = 0;
      robot.GetRobotEmergencyStopState(&emergState);
      printf("GetRobotEmergencyStopState :%d\n", emergState);
      int comstate = 0;
      robot.GetSDKComState(&comstate);
      printf("GetSDKComState :%d\n", comstate);
      uint8_t si0_state, si1_state;
      robot.GetSafetyStopState(&si0_state, &si1_state);
      printf("GetSafetyStopState :%d %d\n", si0_state, si1_state);
      double temp[6] = { 0.0 };
      robot.GetJointDriverTemperature(temp);
      printf("Temperature:%f,%f,%f,%f,%f,%f\n", temp[0], temp[1], temp[2], temp[3], temp[4], temp[5]);
      double torque[6] = { 0.0 };
      robot.GetJointDriverTorque(torque);
      printf("torque:%f,%f,%f,%f,%f,%f\n", torque[0], torque[1], torque[2], torque[3], torque[4], torque[5]);
      robot.GetRobotRealTimeState(&pkg);
      robot.CloseRPC();
      return 0;
    }

Inverse Kinematik berechnen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Berechnet die inverse Kinematik.
    * @param  [in] type 0-absolute Pose (Basiskoordinatensystem), 1-inkrementelle Pose (Basiskoordinatensystem), 2-inkrementelle Pose (Werkzeugkoordinatensystem).
    * @param  [in] desc_pos Kartesische Pose.
    * @param  [in] config Gelenkraumkonfiguration, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen.
    * @param  [out] joint_pos Gelenkposition.
    * @return  Fehlercode.
    */
    errno_t GetInverseKin(int type, DescPose *desc_pos, int config, JointPos *joint_pos);

Inverse Kinematik berechnen (mit Referenzposition)
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Berechnet die inverse Kinematik unter Verwendung einer Referenz-Gelenkposition.
    * @param  [in] type 0-absolute Pose (Basiskoordinatensystem), 1-inkrementelle Pose (Basiskoordinatensystem), 2-inkrementelle Pose (Werkzeugkoordinatensystem).
    * @param  [in] desc_pos Kartesische Pose.
    * @param  [in] joint_pos_ref Referenz-Gelenkposition.
    * @param  [out] joint_pos Berechnete Gelenkposition.
    * @return  Fehlercode.
    */
    errno_t GetInverseKinRef(int type, DescPose *desc_pos, JointPos *joint_pos_ref, JointPos *joint_pos);

Inverse Kinematik (mit Erweiterungsachsenposition) berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Berechnet die inverse Kinematik, einschließlich der Erweiterungsachsenposition im kartesischen Raum.
    * @param [in] type 0-absolute Pose (Basiskoordinatensystem), 1-inkrementelle Pose (Basiskoordinatensystem), 2-inkrementelle Pose (Werkzeugkoordinatensystem).
    * @param [in] desc_pos Kartesische Pose.
    * @param [in] exaxis Position der Erweiterungsachse.
    * @param [in] tool Werkzeugnummer.
    * @param [in] workPiece Werkstücknummer.
    * @param [out] joint_pos Gelenkposition.
    * @param [in] config Gelenkraumkonfiguration, [-1] - Lösung basierend auf der aktuellen Gelenkposition als Referenz, [0~7] - Lösung gemäß einer bestimmten Gelenkraumkonfiguration
    * @return Fehlercode.
    */
    errno_t GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos& joint_pos, int config = -1);

Codebeispiel für inverse Kinematik mit Erweiterungsachsen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKinExaxis()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose desc(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos = {};
        DescPose offsetPos = {};
        robot.GetRobotRealTimeState(&pkg);
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos);
        printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.jPos[0], jointPos.jPos[1], jointPos.jPos[2], jointPos.jPos[3], jointPos.jPos[4], jointPos.jPos[5]);
        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(&jointPos, &desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, &exaxis, -1, 0, &offsetPos);
        robot.CloseRPC();
        return 0;
    }

Lösbarkeit der inversen Kinematik prüfen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Prüft, ob die inverse Kinematik für eine gegebene Referenz-Gelenkposition lösbar ist.
    * @param  [in] type 0-absolute Pose (Basiskoordinatensystem), 1-inkrementelle Pose (Basiskoordinatensystem), 2-inkrementelle Pose (Werkzeugkoordinatensystem).
    * @param  [in] desc_pos Kartesische Pose.
    * @param  [in] joint_pos_ref Referenz-Gelenkposition.
    * @param  [out] result 0-keine Lösung, 1-Lösung vorhanden.
    * @return  Fehlercode.
    */
    errno_t GetInverseKinHasSolution(int type, DescPose *desc_pos, JointPos *joint_pos_ref, uint8_t *result);

Vorwärtskinematik berechnen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Berechnet die Vorwärtskinematik.
    * @param  [in] joint_pos Gelenkposition.
    * @param  [out] desc_pos Kartesische Pose.
    * @return  Fehlercode.
    */
    errno_t GetForwardKin(JointPos *joint_pos, DescPose *desc_pos);

Codebeispiel für Roboter-Vorwärts-/Inverskinematik
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKin(void)
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
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      JointPos inverseRtn = {};
      robot.GetInverseKin(0, &desc_pos1, -1, &inverseRtn);
      printf("dcs1 GetInverseKin rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      robot.GetInverseKinRef(0, &desc_pos1, &j1, &inverseRtn);
      printf("dcs1 GetInverseKinRef rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      uint8_t hasResut = 0;
      robot.GetInverseKinHasSolution(0, &desc_pos1, &j1, &hasResut);
      printf("dcs1 GetInverseKinRef result %d\n", hasResut);
      DescPose forwordResult = {};
      robot.GetForwardKin(&j1, &forwordResult);
      printf("jpos1 forwordResult rtn is %f %f %f %f %f %f \n", forwordResult.tran.x, forwordResult.tran.y, forwordResult.tran.z, forwordResult.rpy.rx, forwordResult.rpy.ry, forwordResult.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Teachpunkt-Daten abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die Daten eines Robot-Teachpunkts zurück.
     * @param  [in] name Punktname.
     * @param  [out] data Punktdaten (Array der Länge 20).
     * @return  Fehlercode.
     */
    errno_t GetRobotTeachingPoint(char name[64], float data[20]);

DH-Parameter-Kompensationswerte abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Kompensationswerte der Roboter-DH-Parameter zurück.
    * @param [out] dhCompensation DH-Parameter-Kompensationswerte in mm [cmpstD1, cmpstA2, cmpstA3, cmpstD4, cmpstD5, cmpstD6].
    * @return Fehlercode.
    */
    errno_t GetDHCompensation(double dhCompensation[6]);

SN-Code des Steuerschranks abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt den SN-Code des Steuerschranks zurück.
    * @param [out] SNCode SN-Code des Steuerschranks.
    * @return Fehlercode.
    */
    errno_t GetRobotSN(std::string& SNCode);

Codebeispiel für das Abrufen von Teachpunkt-Daten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetTeachPoint(void)
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
      char name[64] = "P1";
      float data[20] = { 0 };
      rtn = robot.GetRobotTeachingPoint(name, data);
      printf(" %d name is: %s \n", rtn, name);
      for (int i = 0; i < 20; i++)
      {
        printf("data is: %f \n", data[i]);
      }
      int que_len = 0;
      rtn = robot.GetMotionQueueLength(&que_len);
      printf("GetMotionQueueLength rtn is: %d, queue length is: %d \n", rtn, que_len);
      double dh[6] = { 0 };
      int retval = 0;
      retval = robot.GetDHCompensation(dh);
      cout << "retval is: " << retval << endl;
      cout << "dh is: " << dh[0] << " " << dh[1] << " " << dh[2] << " " << dh[3] << " " << dh[4] << " " << dh[5] << endl;
      string SN = "";
      robot.GetRobotSN(SN);
      cout << "robot SN is " << SN << endl;
      robot.CloseRPC();
      return 0;
    }

Werkzeugkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
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
    errno_t GetToolCoordWithID(int id, DescPose& coord, int& type, int& install, int& toolID, int& loadNo);

Werkstückkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruft das Werkstückkoordinatensystem nach ID ab
    * @param [in] id Nummer des Werkstückkoordinatensystems
    * @param [out] coord Werte des Koordinatensystems
    * @param [out] refFrame Referenzkoordinatensystem
    * @return Fehlercode
    */
    errno_t GetWObjCoordWithID(int id, DescPose& coord, int& refFrame);
    
Externes Werkzeugkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruft das externe Werkzeugkoordinatensystem nach ID ab
    * @param [in] id Nummer des externen Werkzeugkoordinatensystems, 20-39 entsprechen den externen Werkzeugkoordinatensystemen 0-19
    * @param [out] coord TCP-Pose des festen externen Werkzeugs am Roboter
    * @param [out] tcoord Pose des am Roboterende montierten Werkstückkoordinatensystems
    * @return Fehlercode
    */
    errno_t GetExToolCoordWithID(int id, DescPose& coord, DescPose& tcoord);
    
Erweitertes Achsenkoordinatensystem nach ID abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruft das erweiterte Achsenkoordinatensystem nach ID ab
    * @param [in] id Nummer des externen Werkzeugkoordinatensystems
    * @param [out] coord Werte des Koordinatensystems
    * @param [out] axisCoordNum Erweiterte Achsnummer; bit0-bit3 entsprechen den erweiterten Achsen 1-4; z.B. entspricht axisCoordNum-Wert 3 den erweiterten Achsen [1, 2]
    * @param [out] calibFlag Kalibrierungsflag; 0-nicht kalibriert; 1-kalibriert
    * @return Fehlercode
    */
    errno_t GetExAxisCoordWithID(int id, DescPose& coord, int& axisCoordNum, int& calibFlag);

Nutzlastmasse und -schwerpunkt anhand der ID abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Nutzlastmasse und den -schwerpunkt anhand der ID zurück.
    * @param [in] id Nutzlastnummer.
    * @param [out] weight Nutzlastmasse.
    * @param [out] cog Nutzlastschwerpunkt.
    * @return Fehlercode.
    */
    errno_t GetTargetPayloadWithID(int id, double& weight, DescTran& cog);

Aktuelles Werkzeugkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt das aktuelle Werkzeugkoordinatensystem zurück.
    * @param [out] coord Koordinatenwerte.
    * @return Fehlercode.
    */
    errno_t GetCurToolCoord(DescPose& coord);

Aktuelles Werkstückkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt das aktuelle Werkstückkoordinatensystem zurück.
    * @param [out] coord Koordinatenwerte.
    * @return Fehlercode.
    */
    errno_t GetCurWObjCoord(DescPose& coord);

Aktuelles externes Werkzeugkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt das aktuelle externe Werkzeugkoordinatensystem zurück.
    * @param [out] coord Koordinatenwerte.
    * @return Fehlercode.
    */
    errno_t GetCurExToolCoord(DescPose& coord);

Aktuelles Erweiterungsachsen-Koordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt das aktuelle Erweiterungsachsen-Koordinatensystem zurück.
    * @param [out] coord Koordinatenwerte.
    * @return Fehlercode.
    */
    errno_t GetCurExAxisCoord(DescPose& coord);

Codebeispiel für Roboter-Koordinatensysteme und Nutzlast
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    int TestCoord()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        robot.Sleep(2000);
        int id = 1;
        DescPose toolCoord = {};
        DescPose extoolCoord = {};
        DescPose exworkpieceCoord = {};
        DescPose wobjCoord = {};
        DescPose exAxisCoord = {};
        int type = 0, install = 0, toolID = 0, loadNo = 0;
        robot.GetToolCoordWithID(id, toolCoord, type, install, toolID, loadNo);
        printf("GetToolCoordWithID %d, %f %f %f %f %f %f,  type = %d, install = %d, toolID = %d, loadNo = %d\n", id,
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type, install, toolID, loadNo);
        int refFrame = 0;
        robot.GetWObjCoordWithID(id, wobjCoord, refFrame);
        printf("GetWObjCoordWithID %d, %f %f %f %f %f %f, refFrame = %d\n", id,
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame);
        robot.GetExToolCoordWithID(21, extoolCoord, exworkpieceCoord);
        printf("GetExToolCoordWithID %d, %f %f %f %f %f %f\n", id,
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz,
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);
        int axisCoordNum = 0, calibFlag = 0;
        robot.GetExAxisCoordWithID(id, exAxisCoord, axisCoordNum, calibFlag);
        printf("GetExAxisCoordWithID %d, %f %f %f %f %f %f, axisCoordNum = %d, calibFlag = %d\n", id,
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum, calibFlag);
        double weight = 0.0;
        DescTran cog = {};
        robot.GetTargetPayloadWithID(id, weight, cog);
        printf("GetTargetPayloadWithID %d, %f %f %f %f\n", id, weight,
            cog.x, cog.y, cog.z);
        robot.GetCurToolCoord(toolCoord);
        printf("GetCurToolCoord %f %f %f %f %f %f\n",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);
        robot.GetCurWObjCoord(wobjCoord);
        printf("GetCurWObjCoord %f %f %f %f %f %f\n",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);
        robot.GetCurExToolCoord(extoolCoord);
        printf("GetExToolCoordWithID %f %f %f %f %f %f\n",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        robot.GetCurExAxisCoord(exAxisCoord);
        printf("GetCurExAxisCoord %f %f %f %f %f %f\n",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);
        float weightT = 0.0;
        DescTran cogT = {};
        robot.GetTargetPayload(0, &weightT);
        robot.GetTargetPayloadCog(0, &cogT);
        printf("GetTargetPayload %f %f %f %f\n", weightT,
            cogT.x, cogT.y, cogT.z);
        DescPose coordSet(0, 1, 2, 3, 4, 5);
        robot.SetToolCoord(1, &coordSet, 0, 0, 1, 0);
        robot.SetWObjCoord(1, &coordSet, 0);
        robot.SetLoadWeight(1, 1.3);
        //DescTran cog = {};
        cog.x = 10;
        cog.y = 20;
        cog.z = 30;
        robot.SetLoadCoord(1, &cog);
        DescPose etcp(0, 0, 100, 0, 0, 0);
        DescPose etool(0, 0, 50, 0, 0, 0);
        rtn = robot.SetExToolCoord(21, &etcp, &etool);
        printf("SetExToolCoord rtn is %d\n", rtn);
        robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        robot.CloseRPC();
        return 0;
    }
