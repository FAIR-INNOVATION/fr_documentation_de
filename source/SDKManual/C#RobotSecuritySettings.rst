Roboter-Sicherheitseinstellungen
=========================================

.. toctree::
    :maxdepth: 5

Kollisionsstufe einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Kollisionsstufe ein.
    * @param  [in] mode  0-Stufe, 1-Prozentsatz.
    * @param  [in] level Kollisionsschwellwert, bei mode 0 Bereich [], bei mode 1 Bereich [0~1].
    * @param  [in] config 0-Konfigurationsdatei nicht aktualisieren, 1-Konfigurationsdatei aktualisieren.
    * @return  Fehlercode.
    */
    int SetAnticollision(int mode, double[] level, int config);

Strategie nach Kollision einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Strategie nach einer Kollision ein.
    * @param  [in] strategy  0-Fehler und Pause; 1-Fortsetzen; 2-Fehler und Stopp; 3-Schwerkraftmoment-Modus; 4-Schwingungsmodus; 5-Rückprallmodus.
    * @param  [in] safeTime  Sichere Stoppzeit [1000 - 2000] ms.
    * @param  [in] safeDistance  Sicherer Stoppabstand [1-150] mm.
    * @param  [in] safeVel  TCP-sichere Stoppgeschwindigkeit [50-250] mm/s.
    * @param  [in] safetyMargin  Sicherheitsfaktoren für J1-J6 [1-10].
    * @return  Fehlercode.
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safeVel, int[] safetyMargin);

Benutzerdefinierte Kollisionserkennungsschwelle starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Startet die Funktion für benutzerdefinierte Kollisionserkennungsschwellen. Legt Schwellen für Gelenk und TCP fest.
    * @param  [in] flag 1-nur Gelenkerkennung aktivieren; 2-nur TCP-Erkennung aktivieren; 3-Gelenk- und TCP-Erkennung gleichzeitig aktivieren.
    * @param  [in] jointDetectionThreshould Gelenk-Kollisionserkennungsschwellen für J1-J6.
    * @param  [in] tcpDetectionThreshould TCP-Kollisionserkennungsschwellen für XYZABC.
    * @param  [in] block 0-nicht blockierend; 1-blockierend.
    * @return  Fehlercode.
    */
    int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Benutzerdefinierte Kollisionserkennungsschwelle deaktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Deaktiviert die Funktion für benutzerdefinierte Kollisionserkennungsschwellen.
    * @return  Fehlercode.
    */
    int CustomCollisionDetectionEnd();

Codebeispiel für Roboter-Kollisionsstufeneinstellungen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button24_Click(object sender, EventArgs e)
    {
        int mode = 0;
        int config = 1;
        double[] level1 = { 1.0f, 2.0f, 3.0f, 4.0f, 5.0f, 6.0f };
        double[] level2 = { 50.0f, 20.0f, 30.0f, 40.0f, 50.0f, 60.0f };

        int rtn = robot.SetAnticollision(mode, level1, config);
        Console.WriteLine($"SetAnticollision mode 0 rtn is {rtn}");
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        Console.WriteLine($"SetAnticollision mode 1 rtn is {rtn}");

        JointPos p1Joint = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos p2Joint = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0.0f, 0.0f, 0.0f, 0.0f);
        DescPose offdese = new DescPose(0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, 2,  exaxisPos, 0, 0,  offdese);
        robot.ResetAllError();
        int[] safety = { 5, 5, 5, 5, 5, 5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        Console.WriteLine($"SetCollisionStrategy rtn is {rtn}");

        double[] jointDetectionThreshould = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould = { 60, 60, 60, 60, 60, 60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        Console.WriteLine($"CustomCollisionDetectionStart rtn is {rtn}");

        robot.MoveL( p1Joint,  p1Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        rtn = robot.CustomCollisionDetectionEnd();
        Console.WriteLine($"CustomCollisionDetectionEnd rtn is {rtn}");
    }

Positive Endlage einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die positive Endlage (Software-Endschalter) ein.
    * @param  [in] limit Positionen der sechs Gelenke, Einheit deg.
    * @return  Fehlercode.
    */
    int SetLimitPositive(double[] limit);

Negative Endlage einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die negative Endlage (Software-Endschalter) ein.
    * @param  [in] limit Positionen der sechs Gelenke, Einheit deg.
    * @return  Fehlercode.
    */
    int SetLimitNegative(double[] limit);

Gelenk-Software-Endschalter-Winkel abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Winkel der Gelenk-Software-Endschalter zurück.
    * @param  [in] flag 0-blockierend, 1-nicht blockierend.
    * @param  [out] negative  Negative Endlagenwinkel, Einheit deg.
    * @param  [out] positive  Positive Endlagenwinkel, Einheit deg.
    * @return  Fehlercode.
    */
    int GetJointSoftLimitDeg(byte flag, ref double[] negative, ref double[] positive);

Codebeispiel für Roboter-Endlageneinstellungen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] plimit = { 170.0f, 80.0f, 150.0f, 80.0f, 170.0f, 160.0f };
        robot.SetLimitPositive(plimit);
        double[] nlimit = { -170.0f, -260.0f, -150.0f, -260.0f, -170.0f, -160.0f };
        robot.SetLimitNegative(nlimit);

        double[] neg_deg = new double[6] {0,0,0,0,0,0 };
        double[] pos_deg = new double[6] { 0, 0, 0, 0, 0, 0 };
        robot.GetJointSoftLimitDeg(0, ref neg_deg,ref pos_deg);
        Console.WriteLine($"neg limit deg:{neg_deg[0]},{neg_deg[1]},{neg_deg[2]},{neg_deg[3]},{neg_deg[4]},{neg_deg[5]}");
        Console.WriteLine($"pos limit deg:{pos_deg[0]},{pos_deg[1]},{pos_deg[2]},{pos_deg[3]},{pos_deg[4]},{pos_deg[5]}");
    }

Roboter-Kollisionserkennungsmethode einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Methode zur Kollisionserkennung des Roboters ein.
    * @param  [in] method Kollisionserkennungsmethode: 0-Strommodus; 1-Doppel-Encoder; 2-Strom und Doppel-Encoder gleichzeitig aktivieren.
    * @param [in] thresholdMode Art des Kollisionsstufen-Schwellwerts; 0-Fester Schwellwert für Kollisionsstufe; 1-Benutzerdefinierter Kollisionserkennungsschwellwert.
    * @return  Fehlercode.
    */
    int SetCollisionDetectionMethod(int method, int thresholdMode = 0);

Statische Kollisionserkennung ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Schaltet die statische Kollisionserkennung ein oder aus.
    * @param  [in] status 0-aus; 1-ein.
    * @return  Fehlercode.
    */
    int SetStaticCollisionOnOff(int status);

Codebeispiel für Roboter-Kollisionserkennungsmethode
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        int rtn = robot.SetCollisionDetectionMethod(0, 0);

        rtn = robot.SetStaticCollisionOnOff(1);
        Console.WriteLine($"SetStaticCollisionOnOff On rtn is {rtn}");
        Thread.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        Console.WriteLine($"SetStaticCollisionOnOff Off rtn is {rtn}");
    }

Gelenk-Drehmoment-/Leistungserkennung
++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gelenk-Drehmoment-/Leistungserkennung.
    * @param  [in] status 0-aus; 1-ein.
    * @param  [in] power  Maximale Leistungseinstellung (W).
    * @return  Fehlercode.
    */
    int SetPowerLimit(int status, double power);

Codebeispiel für Gelenk-Drehmoment-/Leistungserkennung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }

Sicherheitsgeschwindigkeitsparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Sicherheitsgeschwindigkeitsparameter einstellen
    * @param [in] enable 0-aus; 1-im manuellen Modus aktiviert; 2-in allen Modi aktiviert (automatische Geschwindigkeitsbegrenzung nicht unterstützt)
    * @param [in] maxTCPVel Maximale TCP-Geschwindigkeitsbegrenzung; [0-1000] mm/s
    * @param [in] strategy Strategie nach Überschreitung; 0-Stopp mit Alarm; 1-automatische Geschwindigkeitsbegrenzung; 2-Stopp mit Alarm und Deaktivierung
    * @param [in] maxJointVel Maximale Geschwindigkeit für 6 Gelenke (°/s), Standard 45°/s
    * @return Fehlercode
    */
    public int SetVelReducePara(int enable, double maxTCPVel, int strategy, double[] maxJointVel = null)
    
SDK-Codebeispiel zum Einstellen der Sicherheitsgeschwindigkeitsparameter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestSetVelReducePara()
    {
        int rtn = 0;
        JointPos j1 = new JointPos(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2 = new JointPos(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        double[] maxJointVel = new double[] { 100.0, 100.0, 100.0, 100.0, 100.0, 100.0 };

        robot.SetSpeed(20);
        rtn = robot.SetVelReducePara(0, 200, 0, maxJointVel);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        // 1st
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel);
        Console.WriteLine($"SetVelReduceParaA param error rtn is {rtn}");
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        // 2rd
        maxJointVel = new double[] { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel);
        Console.WriteLine($"SetVelReduceParaB reduce vel rtn is {rtn}");
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        return 0; 
    }