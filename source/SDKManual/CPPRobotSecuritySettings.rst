Roboter-Sicherheitseinstellungen
=========================================

.. toctree::
    :maxdepth: 5

Kollisionsstufe einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Kollisionsstufe ein.
    * @param  [in] mode  0-Stufe, 1-Prozentsatz.
    * @param  [in] level  Kollisionsschwellwerte, bei mode 0 Bereich [], bei mode 1 Bereich [0~1].
    * @param  [in] config 0-Konfigurationsdatei nicht aktualisieren, 1-Konfigurationsdatei aktualisieren.
    * @return  Fehlercode.
    */
    errno_t SetAnticollision(int mode, float level[6], int config);

Strategie nach Kollision einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Stellt die Strategie nach einer Kollision ein.
     * @param  [in] strategy  0-Fehler und Pause; 1-Fortsetzen; 2-Fehler und Stopp; 3-Schwerkraftmoment-Modus; 4-Schwingungsmodus; 5-Rückprallmodus.
     * @param  [in] safeTime  Sichere Stoppzeit [1000 - 2000] ms.
     * @param  [in] safeDistance  Sicherer Stoppabstand [1-150] mm.
     * @param  [in] safetyMargin  Sicherheitsfaktoren für J1-J6 [1-10].
     * @return  Fehlercode.
     */
    errno_t SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safetyMargin[]);

Benutzerdefinierte Kollisionserkennungsschwelle starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Startet die Funktion für benutzerdefinierte Kollisionserkennungsschwellen. Legt Schwellen für Gelenk und TCP fest.
     * @param  [in] flag 1-nur Gelenkerkennung aktivieren; 2-nur TCP-Erkennung aktivieren; 3-Gelenk- und TCP-Erkennung gleichzeitig aktivieren.
     * @param  [in] jointDetectionThreshould Gelenk-Kollisionserkennungsschwellen für J1-J6.
     * @param  [in] tcpDetectionThreshould TCP-Kollisionserkennungsschwellen für XYZABC.
     * @param  [in] block 0-nicht blockierend; 1-blockierend.
     * @return  Fehlercode.
     */
    errno_t CustomCollisionDetectionStart(int flag, double jointDetectionThreshould[6], double tcpDetectionThreshould[6], int block);

Benutzerdefinierte Kollisionserkennungsschwelle beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Beendet die Funktion für benutzerdefinierte Kollisionserkennungsschwellen.
     * @return  Fehlercode.
     */
    errno_t CustomCollisionDetectionEnd();

Codebeispiel für Roboter-Kollisionsstufeneinstellungen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestCollision(void)
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
         int mode = 0;
         int config = 1;
         float level1[6] = { 1.0,2.0,3.0,4.0,5.0,6.0 };
         float level2[6] = { 50.0,20.0,30.0,40.0,50.0,60.0 };
         rtn = robot.SetAnticollision(mode, level1, config);
         printf("SetAnticollision mode 0 rtn is %d\n", rtn);
         mode = 1;
         rtn = robot.SetAnticollision(mode, level2, config);
         printf("SetAnticollision mode 1 rtn is %d\n", rtn);
         JointPos p1Joint(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos p2Joint(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0.0, 0.0, 0.0, 0.0);
         DescPose offdese(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, 2, &exaxisPos, 0, 0, &offdese);
         robot.ResetAllError();
         int safety[6] = { 5,5,5,5,5,5 };
         rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
         printf("SetCollisionStrategy rtn is %d\n", rtn);
         double jointDetectionThreshould[6] = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
         double tcpDetectionThreshould[6] = { 60,60,60,60,60,60 };
         rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
         cout << "CustomCollisionDetectionStart rtn is " << rtn << endl;
         robot.MoveL(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         rtn = robot.CustomCollisionDetectionEnd();
         cout << "CustomCollisionDetectionEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Positive Endlage einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die positive Endlage (Software-Endschalter) ein.
    * @param  [in] limit Positionen der sechs Gelenke, Einheit deg.
    * @return  Fehlercode.
    */
    errno_t SetLimitPositive(float limit[6]);

Negative Endlage einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die negative Endlage (Software-Endschalter) ein.
    * @param  [in] limit Positionen der sechs Gelenke, Einheit deg.
    * @return  Fehlercode.
    */
    errno_t SetLimitNegative(float limit[6]);

Gelenk-Software-Endschalter-Winkel abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Winkel der Gelenk-Software-Endschalter zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] negative  Negative Endlagenwinkel, Einheit deg.
    * @param  [out] positive  Positive Endlagenwinkel, Einheit deg.
    * @return  Fehlercode.
    */
    errno_t GetJointSoftLimitDeg(uint8_t flag, float negative[6], float positive[6]);

Codebeispiel für Roboter-Endlageneinstellungen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLimit(void)
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
      float plimit[6] = { 170.0,80.0,150.0,80.0,170.0,160.0 };
      robot.SetLimitPositive(plimit);
      float nlimit[6] = { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
      robot.SetLimitNegative(nlimit);
      float neg_deg[6] = { 0.0 }, pos_deg[6] = { 0.0 };
      robot.GetJointSoftLimitDeg(0, neg_deg, pos_deg);
      printf("neg limit deg:%f,%f,%f,%f,%f,%f\n", neg_deg[0], neg_deg[1], neg_deg[2], neg_deg[3], neg_deg[4], neg_deg[5]);
      printf("pos limit deg:%f,%f,%f,%f,%f,%f\n", pos_deg[0], pos_deg[1], pos_deg[2], pos_deg[3], pos_deg[4], pos_deg[5]);
      robot.CloseRPC();
      return 0;
    }

Roboter-Kollisionserkennungsmethode einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Methode zur Kollisionserkennung des Roboters ein.
    * @param [in] method Kollisionserkennungsmethode: 0-Strommodus; 1-Doppel-Encoder; 2-Strom und Doppel-Encoder gleichzeitig aktivieren.
    * @param [in] thresholdMode Art des Kollisionsstufen-Schwellwerts; 0-Fester Schwellwert für Kollisionsstufe; 1-Benutzerdefinierter Kollisionserkennungsschwellwert.
    * @return  Fehlercode.
    */
    errno_t SetCollisionDetectionMethod(int method, int thresholdMode = 0);

Statische Kollisionserkennung ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Schaltet die statische Kollisionserkennung ein oder aus.
     * @param [in] status 0-aus; 1-ein.
     * @return Fehlercode.
     */
    errno_t SetStaticCollisionOnOff(int status);

Codebeispiel für Roboter-Kollisionserkennungsmethode
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestCollisionMethod(void)
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
      rtn = robot.SetCollisionDetectionMethod(0, 0);
      printf("SetCollisionDetectionMethod rtn is %d\n", rtn);
      rtn = robot.SetStaticCollisionOnOff(1);
      printf("SetStaticCollisionOnOff On rtn is %d\n", rtn);
      rtn = robot.Sleep(5000);
      rtn = robot.SetStaticCollisionOnOff(0);
      printf("SetStaticCollisionOnOff Off rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Gelenk-Drehmoment-/Leistungserkennung
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Gelenk-Drehmoment-/Leistungserkennung.
     * @param [in] status 0-aus; 1-ein.
     * @param [in] power  Maximale Leistungseinstellung (W).
     * @return Fehlercode.
     */
    errno_t SetPowerLimit(int status, double power);

Codebeispiel für Gelenk-Drehmoment-/Leistungserkennung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestPowerLimit(void)
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
       robot.DragTeachSwitch(1);
       robot.SetPowerLimit(1, 200);
       float torques[] = { 0, 0, 0, 0, 0, 0 };
       robot.GetJointTorques(1, torques);
       int count = 100;
       robot.ServoJTStart(); 
       int error = 0;
       while (count > 0)
       {
          error = robot.ServoJT(torques, 0.001);
          count = count - 1;
          robot.Sleep(1);
       }
       error = robot.ServoJTEnd();
       robot.DragTeachSwitch(0);
       robot.CloseRPC();
       return 0;
    }

Sicherheitsgeschwindigkeitsparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Legt die Sicherheitsgeschwindigkeitsparameter fest
    * @param [in] enable 0-deaktiviert; 1-im Handmodus aktiviert; 2-in allen Modi aktiviert
    * @param [in] maxTCPVel Maximale TCP-Geschwindigkeitsbegrenzung; [0-1000] mm/s
    * @param [in] strategy Strategie nach Geschwindigkeitsüberschreitung; 0-Stopp mit Alarm; 1-automatische Geschwindigkeitsbegrenzung; 2-Stopp mit Alarm und Deaktivierung
    * @param [in] maxJointVel Maximale Geschwindigkeit für 6 Gelenke (°/s), Standard 45°/s
    * @return Fehlercode
    */
    errno_t SetVelReducePara(int enable, double maxTCPVel, int strategy, std::vector<double> maxJointVel = {45.0, 45.0, 45.0, 45.0, 45.0, 45.0});
        
SDK-Codebeispiel zum Einstellen der Sicherheitsgeschwindigkeitsparameter
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSetVelReducePara()
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
        JointPos j1(0, -90, 90, 0, 0, 0);
        JointPos j2(90, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        rtn = robot.SetVelReducePara(0, 30, 1);
        printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(1, 30, 1);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(2, 30, 2);
        printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);
        rtn = robot.SetVelReducePara(2, 30, 0);
        printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Codebeispiel zum Festlegen der Gelenksicherheitsgeschwindigkeit des Roboters
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:    

    int TestSetJointVelReducePara()
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
        JointPos j1(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(20);

        std::vector<double> maxJointVelA = {100.0, 100.0, 100.0, 100.0, 100.0, 100.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelA);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        std::vector<double> maxJointVelB = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelB);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.CloseRPC();
        return 0;
    }    