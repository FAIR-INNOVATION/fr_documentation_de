Roboter-Sicherheitseinstellungen
================================

.. toctree::
    :maxdepth: 5

Kollisionsstufe einstellen
++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kollisionsstufe einstellen
    * @param [in] mode 0 - Stufe, 1 - Prozent
    * @param [in] level Kollisionsschwellwert, Stufenbereich [1 - 10 entspricht Stufe 1-10, 100 - aus], Prozentbereich [0~10 entspricht 0% - 100%]
    * @param [in] config 0 - Konfigurationsdatei nicht aktualisieren, 1 - Konfigurationsdatei aktualisieren
    * @return Fehlercode
    */
    int SetAnticollision(int mode, Object[] level, int config);

Strategie nach Kollision einstellen
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Strategie nach Kollision einstellen
    * @param [in] strategy 0 - Fehler melden und anhalten, 1 - Weiterlaufen
    * @param [in] safeTime Sicherheitsstopp-Zeit [1000 - 2000] ms
    * @param [in] safeDistance Sicherheitsstopp-Distanz [1-150] mm
    * @param [in] safetyMargin Sicherheitsfaktoren für J1-J6 [1-10]
    * @return Fehlercode
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int[] safetyMargin);

Benutzerdefinierte Kollisionserkennungsschwellwerte starten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief Benutzerdefinierte Kollisionserkennungsschwellwerte starten, Schwellwerte für Gelenk und TCP setzen
    * @param [in] flag 1 - Nur Gelenkerkennung aktivieren; 2 - Nur TCP-Erkennung aktivieren; 3 - Gelenk- und TCP-Erkennung gleichzeitig aktivieren
    * @param [in] jointDetectionThreshould Gelenk-Kollisionserkennungsschwellwerte J1-J6
    * @param [in] tcpDetectionThreshould TCP-Kollisionserkennungsschwellwerte, xyzabc
    * @param [in] block 0 - nicht blockierend; 1 - blockierend
    * @return Fehlercode
    */
    public int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Benutzerdefinierte Kollisionserkennungsschwellwerte stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief Benutzerdefinierte Kollisionserkennungsschwellwerte stoppen
    * @return Fehlercode
    */
    public int CustomCollisionDetectionEnd();

Codebeispiel zum Einstellen der Roboter-Kollisionsstufe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCollision(Robot robot)
    {
        int mode = 0;
        int config = 1;
        Object[] level1 = new Object[]{ 1.0,2.0,3.0,4.0,5.0,6.0 };
        Object[] level2 = new Object[]{ 50.0,20.0,30.0,40.0,50.0,60.0 };

        int rtn = robot.SetAnticollision(mode, level1, config);
        System.out.println("SetAnticollision mode 0 rtn is: "+ rtn);
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        System.out.println("SetAnticollision mode 1 rtn is :"+ rtn);

        JointPos p1Joint=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos p2Joint=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offdese=new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, 2,0, exaxisPos, 0, 0, offdese,0,10);
        robot.ResetAllError();
        int[] safety = new int[]{ 5,5,5,5,5,5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        System.out.println("SetCollisionStrategy rtn is:"+ rtn);

        double[] jointDetectionThreshould = new double[]{ 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould =new double[] { 60,60,60,60,60,60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        System.out.println("CustomCollisionDetectionStart rtn is :"+ rtn);

        robot.MoveL(p1Joint, p1Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        rtn = robot.CustomCollisionDetectionEnd();
        System.out.println("CustomCollisionDetectionEnd rtn is: "+ rtn);
        return 0;
    }

Positiven Endanschlag einstellen
+++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Positiven Endanschlag (weiche Grenze) einstellen
    * @param [in] limit Positionen der sechs Gelenke, Einheit [°]
    * @return Fehlercode
    */
    int SetLimitPositive(Object[] limit);

Negativen Endanschlag einstellen
+++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Negativen Endanschlag (weiche Grenze) einstellen
    * @param [in] limit Positionen der sechs Gelenke, Einheit [°]
    * @return Fehlercode
    */
    int SetLimitNegative(Object[] limit);

Weiche Gelenk-Endanschläge (Winkel) abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Weiche Gelenk-Endanschläge (Winkel) abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] negative Winkel der negativen Endanschläge [°]
    * @param [out] positive Winkel der positiven Endanschläge [°]
    * @return Fehlercode
    */
    int GetJointSoftLimitDeg(int flag, Object[] negative, Object[] positive);

Codebeispiel zum Einstellen der Roboter-Endanschläge
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLimit(Robot robot)
    {
        Object[] plimit =new Object[] { 170.0,80.0,150.0,80.0,170.0,160.0 };
        robot.SetLimitPositive(plimit);
        Object[] nlimit =new Object[] { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
        robot.SetLimitNegative(nlimit);

        Object[] neg_deg =new Object[] {0, 0 , 0, 0, 0, 0}, pos_deg = new Object[]{0, 0 , 0, 0, 0, 0};
        robot.GetJointSoftLimitDeg(1,  neg_deg,  pos_deg);
        System.out.println("neg limit deg:"+ neg_deg[0]+","+ neg_deg[1]+","+ neg_deg[2]+","+ neg_deg[3]+","+ neg_deg[4]+","+ neg_deg[5]);
        System.out.println("pos limit deg:"+pos_deg[0]+","+ pos_deg[1]+","+ pos_deg[2]+","+ pos_deg[3]+","+ pos_deg[4]+","+pos_deg[5]);
        return 0;
    }

Roboter-Kollisionserkennungsmethode einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-Kollisionserkennungsmethode einstellen
    * @param [in] method Kollisionserkennungsmethode: 0 - Strommodus; 1 - Doppel-Encoder; 2 - Strom und Doppel-Encoder gleichzeitig aktiviert
    * @param [in] thresholdMode Art des Kollisionsstufen-Schwellwerts: 0 - Fester Schwellwert der Kollisionsstufe; 1 - Benutzerdefinierter Kollisionserkennungsschwellwert
    * @return Fehlercode
    */
    int SetCollisionDetectionMethod(int method, int thresholdMode)

Kollisionserkennung im Stillstand ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kollisionserkennung im Stillstand ein-/ausschalten
    * @param [in] status 0 - aus; 1 - ein
    * @return Fehlercode
    */
    public int SetStaticCollisionOnOff(int status)

Codebeispiel zum Einstellen der Roboter-Kollisionserkennungsmethode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCollisionMethod(Robot robot)
    {
        int rtn = robot.SetCollisionDetectionMethod(0);

        rtn = robot.SetStaticCollisionOnOff(1);
        System.out.println("SetStaticCollisionOnOff On rtn is:"+ rtn);
        robot.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        System.out.println("SetStaticCollisionOnOff Off rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Gelenk-Drehmoment-/Leistungsüberwachung
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Drehmoment-/Leistungsüberwachung
    * @param [in] status 0 - aus; 1 - ein
    * @param [in] power Maximale eingestellte Leistung (W)
    * @return Fehlercode
    */
    public int SetPowerLimit(int status, double power)

Codebeispiel für Gelenk-Drehmoment-/Leistungsüberwachung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPowerLimit(Robot robot)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        List<Number> joint_toq=new ArrayList<>();
        joint_toq=robot.GetJointTorques(1);

        int count = 100;
        robot.ServoJTStart(); // ServoJT starten
        int error = 0;
        while (count > 0)
        {
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
.. code-block:: Java
    :linenos:

    /**
    * @brief Sicherheitsgeschwindigkeitsparameter einstellen
    * @param enable 0-aus; 1-im manuellen Modus aktiviert; 2-in allen Modi aktiviert (automatische Geschwindigkeitsbegrenzung nicht unterstützt)
    * @param maxTCPVel Maximale TCP-Geschwindigkeitsbegrenzung; [0-1000] mm/s
    * @param strategy Strategie nach Überschreitung; 0-Stopp mit Alarm; 1-automatische Geschwindigkeitsbegrenzung; 2-Stopp mit Alarm und Deaktivierung
    * @return Fehlercode
    */
    public int SetVelReducePara(int enable, double maxTCPVel, int strategy)
        
SDK-Codebeispiel zum Einstellen der Sicherheitsgeschwindigkeitsparameter
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSetVelReducePara(Robot robot) {
        int rtn = 0;

        JointPos j1 = new JointPos(0, -90, 90, 0, 0, 0);
        JointPos j2 = new JointPos(90, -90, 90, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        System.out.printf("SetVelReducePara param error rtn is %d\n", rtn);

        rtn = robot.SetVelReducePara(0, 30, 1);
        System.out.printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(1, 30, 1);
        System.out.printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(2, 30, 2);
        System.out.printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);

        rtn = robot.SetVelReducePara(2, 30, 0);
        System.out.printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(1000);
        return 0;
    }