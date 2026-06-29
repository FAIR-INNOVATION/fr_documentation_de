Roboter-Kraftsteuerung
================================

.. toctree::
    :maxdepth: 5

Kraftsensor konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Konfiguriert den Kraftsensor.
    * @param  config.company: Kraftsensor-Hersteller, 17-Kunwei Technology, 19-Aerospace 11th Institute, 20-ATI Sensor, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
    * @param  config.device: Gerätenummer, Kunwei(0-KWR75B), Aerospace 11th Institute(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A), NBIT(0-XLH93003ACS), Xinjingcheng XJC(0-XJC-6F-D82), NSR(0-NSR-FTSensorA)
    * @param  config.softvesion: Softwareversionsnummer, derzeit nicht verwendet, Standard 0.
    * @param  config.bus: Position des Geräts am Flanschbus, derzeit nicht verwendet, Standard 0.
    * @return  Fehlercode.
    */
    int FT_SetConfig(DeviceConfig config);

Kraftsensor-Konfiguration abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Kraftsensor-Konfiguration zurück.
    * @param [out] config company: Kraftsensor-Hersteller.
    * @param [out] config device: Gerätenummer.
    * @param [out] config softvesion: Softwareversionsnummer.
    * @param [out] config bus: Busposition.
    * @return Fehlercode.
    */
    int FT_GetConfig(DeviceConfig config);

Kraftsensor aktivieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Aktiviert den Kraftsensor.
    * @param  [in] act  0-Reset, 1-Aktivieren.
    * @return  Fehlercode.
    */
    int FT_Activate(int act);

Kraftsensor Nullpunktkorrektur
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Nullpunktkorrektur des Kraftsensors.
    * @param  [in] act  0-Nullpunkt entfernen, 1-Nullpunkt korrigieren.
    * @return  Fehlercode.
    */
    int FT_SetZero(int act);

Referenzkoordinatensystem für Kraftsensor einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Stellt das Referenzkoordinatensystem für den Kraftsensor ein.
    * @param  [in] type  0-Werkzeugkoordinatensystem, 1-Basiskoordinatensystem, 2-freies Koordinatensystem.
    * @param  [in] coord  Werte des freien Koordinatensystems (falls type=2).
    * @return  Fehlercode.
    */
    int FT_SetRCS(int type, DescPose coord);

Nutzlastgewicht unter dem Kraftsensor einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt das Nutzlastgewicht unter dem Kraftsensor ein.
    * @param [in] weight Nutzlastgewicht in kg.
    * @return Fehlercode.
    */
    int SetForceSensorPayLoad(double weight);

Nutzlastschwerpunkt unter dem Kraftsensor einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt den Nutzlastschwerpunkt unter dem Kraftsensor ein.
    * @param [in] cog Nutzlastschwerpunkt in mm.
    * @return Fehlercode.
    */
    int SetForceSensorPayLoadCog(DescTran cog);

Nutzlastgewicht unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt das Nutzlastgewicht unter dem Kraftsensor zurück.
    * @return List[0]: Fehlercode; List[1]: weight Nutzlastgewicht in kg.
    */
    List<Number> GetForceSensorPayLoad();

Nutzlastschwerpunkt unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Nutzlastschwerpunkt unter dem Kraftsensor zurück.
    * @param [out] cog Nutzlastschwerpunkt in mm.
    * @return Fehlercode.
    */
    int GetForceSensorPayLoadCog(DescTran cog);

Automatische Nullpunktkorrektur des Kraftsensors
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Automatische Nullpunktkorrektur des Kraftsensors.
    * @param [in,out] massCenter Enthält Sensormasse (kg) und Schwerpunkt (mm). Die berechneten Werte werden hier zurückgegeben.
    * @return Fehlercode.
    */
    int ForceSensorAutoComputeLoad(MassCenter massCenter);

Kraft-/Drehmomentdaten im Referenzkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt Kraft-/Drehmomentdaten im Referenzkoordinatensystem zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] ft  Kraft/Drehmoment, fx, fy, fz, tx, ty, tz.
    * @return Fehlercode.
    */
    int FT_GetForceTorqueRCS(int flag, ForceTorque ft);

Rohdaten des Kraftsensors (Kraft/Drehmoment) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die rohen Kraft-/Drehmomentdaten des Kraftsensors zurück.
    * @param [in] flag 0-blockierend, 1-nicht blockierend.
    * @param [out] ft  Kraft/Drehmoment, fx, fy, fz, tx, ty, tz.
    * @return Fehlercode.
    */
    int FT_GetForceTorqueOrigin(int flag, ForceTorque ft);

Codebeispiel für Kraftsensor-Konfiguration und automatische Nullpunktkorrektur
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestFTInit(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company,device,softversion,bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose ftCoord = new DescPose();
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayload(0.824);

        DescTran tr=new DescTran(0.778, 2.554, 48.765);
        robot.SetForceSensorPayloadCog(tr);
        List<Number> weight = new ArrayList<>();
        double x = 0, y = 0, z = 0;
        weight=robot.GetForceSensorPayload();
        robot.GetForceSensorPayloadCog(tr);
        tr.x=0;
        tr.y=0;
        tr.z=0;
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr);

        double computeWeight = 0;
        DescTran tran = new DescTran();
        MassCenter mass=new MassCenter();
        mass.weight=weight.get(1).doubleValue();
        mass.cog=tran;
        robot.ForceSensorAutoComputeLoad(mass);
        return 0;
    }

Nutzlastgewichts-Identifikation aufzeichnen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Zeichnet die Nutzlastgewichts-Identifikation auf.
    * @param  [in] id  Sensorkoordinatensystem-Nummer, Bereich [1~14].
    * @return  Fehlercode.
    */
    int FT_PdIdenRecord(int id);

Nutzlastgewichts-Identifikation berechnen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Berechnet die Nutzlastgewichts-Identifikation.
    * @return  List[0]: Fehlercode; List[1]: double weight  Nutzlastgewicht, Einheit kg.
    */
    List<Number> FT_PdIdenCompute();

Nutzlastschwerpunkt-Identifikation aufzeichnen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Zeichnet die Nutzlastschwerpunkt-Identifikation auf.
    * @param  [in] id  Sensorkoordinatensystem-Nummer, Bereich [1~14].
    * @param  [in] index Punktnummer, Bereich [1~3].
    * @return  Fehlercode.
    */
    int FT_PdCogIdenRecord(int id, int index);

Nutzlastschwerpunkt-Identifikation berechnen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Berechnet die Nutzlastschwerpunkt-Identifikation.
    * @param  [out] cog  Nutzlastschwerpunkt, Einheit mm.
    * @return  Fehlercode.
    */
    int FT_PdCogIdenCompute(DescTran cog);

Codebeispiel für Kraftsensor-Nutzlastidentifikation
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestFTLoadCompute(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose tcoord = new DescPose();
        tcoord.tran.z = 35.0;
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        robot.Sleep(1000);

        List<Number> weight =new ArrayList<>();
        weight=robot.FT_PdIdenCompute();

        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3=new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart(desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart(desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart(desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);
        robot.Sleep(1000);
        DescTran cog=new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(cog);

        robot.CloseRPC();
        return 0;
    }

Kollisionsschutz
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Kollisionsschutz.
    * @param  [in] flag 0-Kollisionsschutz deaktivieren, 1-Kollisionsschutz aktivieren.
    * @param  [in] sensor_id Kraftsensor-Nummer.
    * @param  [in] select  Auswahl der sechs Freiheitsgrade für die Kollisionserkennung, 0-nicht erkennen, 1-erkennen (als Object[] erwartet, z.B. Integer[]).
    * @param  [in] ft  Kollisionskraft/-drehmoment, fx, fy, fz, tx, ty, tz.
    * @param  [in] max_threshold Maximalschwellen (als Object[] erwartet, z.B. Double[]).
    * @param  [in] min_threshold Minimalschwellen (als Object[] erwartet, z.B. Double[]).
    * @note   Erkennungsbereich für Kraft/Drehmoment: (ft - min_threshold, ft + max_threshold).
    * @return  Fehlercode.
    */
    int FT_Guard(int flag, int sensor_id, Object[] select, ForceTorque ft, Object[] max_threshold, Object[] min_threshold);

Codebeispiel für Kollisionsschutz
++++++++++++++++++++++++++++++++++++++++++++
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
        byte flag = 1;
        byte sensor_id = 8;
        Object[] select = { 1, 0, 0, 0, 0, 0 }; // Nur x-Achsen-Kollisionsschutz aktivieren
        Object[] max_threshold = { 5.0, 0.01, 0.01, 0.01, 0.01, 0.01 };
        Object[] min_threshold = { 3.0, 0.01, 0.01, 0.01, 0.01, 0.01 };

        ForceTorque ft = new ForceTorque(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        DescPose  desc_p1, desc_p2, desc_p3;
        desc_p1 = new DescPose(-14.404,-455.283,319.847,-172.935,25.141,-68.097);
        desc_p2 = new DescPose(-107.999,-599.174,285.939,153.472,12.686,-71.284);
        desc_p3 = new DescPose(6.586,-704.897,309.638,178.909,-27.759,-70.479);

        int rtn =  robot.FT_Guard(flag, sensor_id, select, ft, max_threshold, min_threshold);
        System.out.println("FT_Guard start rtn {rtn}");
        robot.MoveCart(desc_p1, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p2, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p3, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
    }

Konstantkraftregelung
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Konstantkraftregelung.
    * @param  flag 0-Konstantkraftregelung deaktivieren, 1-aktivieren.
    * @param  sensor_id Kraftsensor-Nummer.
    * @param  select  Auswahl der sechs Freiheitsgrade, 0-nicht, 1-erkennen (int[]).
    * @param  ft  Kraft-/Drehmoment-Sollwerte.
    * @param  ft_pid Kraft-PID-Parameter (double[] der Länge 6).
    * @param  adj_sign Adaptive Start/Stopp-Steuerung, 0-deaktivieren, 1-aktivieren.
    * @param  ILC_sign ILC Start/Stopp, 0-stopp, 1-Training, 2-Praxis.
    * @param  max_dis Maximale Anpassungsstrecke, Einheit mm.
    * @param  max_ang Maximaler Anpassungswinkel, Einheit deg.
    * @param  M rx, ry Massenparameter [0.1-10], Standard 2 (double[] der Länge 2).
    * @param  B rx, ry Dämpfungsparameter [0.1-50], Standard 8 (double[] der Länge 2).
    * @param  threshold rx, ry Startschwelle [0-10], Standard 0.2 (double[] der Länge 2).
    * @param  adjustCoeff rx, ry Drehmoment-Einstellkoeffizient [0-1], Standard 1 (double[] der Länge 2).
    * @param  polishRadio Schleifradius, Einheit mm.
    * @param  filter_Sign Filteraktivierungsflag 0-aus; 1-ein, Standard aus.
    * @param  posAdapt_sign Pose-Anpassungsaktivierungsflag 0-aus; 1-ein, Standard aus.
    * @param  isNoBlock Blockierungsflag, 0-blockierend; 1-nicht blockierend.
    * @return  Fehlercode.
    */
    public int FT_Control(int flag, int sensor_id, int[] select, ForceTorque ft, double[] ft_pid, int adj_sign, int ILC_sign, double max_dis, double max_ang, double[] M, double[] B, double[] threshold, double[] adjustCoeff, double polishRadio, int filter_Sign, int posAdapt_sign, int isNoBlock);

Codebeispiel für Konstantkraftregelung mit Dämpfung
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestFTControlWithAdjustCoeff(Robot robot)
    {
        int sensor_id = 10;
        int[] select = { 0,0,1,0,0,0 };
        double[] ft_pid = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 1000.0;
        double max_ang = 20;
        ForceTorque ft = new ForceTorque(0.0,0,0,0,0,0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        JointPos j1=new JointPos(80.765, -98.795, 106.548, -97.734, -89.999, 94.842);
        JointPos j2=new JointPos(43.067, -84.429, 92.620, -98.175, -90.011, 57.144);
        DescPose desc_p1=new DescPose(5.009, -547.463, 262.053, -179.999, -0.019, 75.923);
        DescPose desc_p2=new DescPose(-347.966, -547.463, 262.048, -180.000, -0.019, 75.923);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = { 2.0, 2.0 };
        double[] B = { 15.0, 15.0 };
        double[] threshold = {1.0, 1.0};
        double[] adjustCoeff = {1.0, 0.8};
        double polishRadio = 0.0;
        int filter_Sign = 0;
        int posAdapt_sign = 1;
        int isNoBlock;
        ft.fz = -10.0;
        while(true)
        {
            int rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            System.out.printf("FT_Control start rtn is %d\n", rtn);
            robot.MoveL(j1, desc_p1, 1, 0, 100.0, 100.0, 100.0, -1.0, 0, epos, 0, 0, offset_pos, 0,0, 0,10);
            robot.MoveL(j2, desc_p2, 1, 0, 100.0, 100.0, 100.0, -1.0, 0, epos, 0, 0, offset_pos, 0,0, 0,10);
            rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            System.out.printf("FT_Control end rtn is %d\n", rtn);
        }
    }

Rotationseinfügung
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Rotationseinfügung.
    * @param rcs Referenzkoordinatensystem, 0-Werkzeugkoordinatensystem, 1-Basiskoordinatensystem.
    * @param angVelRot Rotationswinkelgeschwindigkeit, Einheit deg/s.
    * @param ft  Kraft-/Drehmomentschwelle (als einzelner Wert? Im C++ Beispiel war es ein double).
    * @param max_angle Maximaler Rotationswinkel, Einheit deg.
    * @param orn Kraft-/Drehmomentrichtung, 1-entlang der z-Achse, 2-um die z-Achse.
    * @param max_angAcc Maximale Rotationsbeschleunigung, Einheit deg/s^2, derzeit nicht verwendet, Standard 0.
    * @param rotorn  Rotationsrichtung, 1-im Uhrzeigersinn, 2-gegen Uhrzeigersinn.
    * @param strategy Behandlungsstrategie bei nicht erkannter Kraft, 0-Fehler; 1-Warnung, Bewegung fortsetzen.
    * @return  Fehlercode.
    */
    public int FT_RotInsertion(int rcs, double angVelRot, double ft, double max_angle, int orn, double max_angAcc, int rotorn, int strategy);

Codebeispiel für Rotationseinfügung mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestMove(Robot robot)
    {
        int rtn=-1;
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4=new JointPos(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4=new DescPose(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double oacc = 100.0;
        double blendT = 0.0;
        double blendR = 0.0;
        int flag = 0;
        int search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos, j1, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        System.out.printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, -1, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        return 0;
    }

Nachgiebigkeitsregelung starten
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Nachgiebigkeitsregelung starten.
    * @param  [in] p Positionseinstellkoeffizient oder Nachgiebigkeitskoeffizient.
    * @param  [in] force Kraftschwelle zum Starten der Nachgiebigkeit, Einheit N.
    * @return  Fehlercode.
    */
    int FT_ComplianceStart(double p, double force);

Nachgiebigkeitsregelung stoppen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Nachgiebigkeitsregelung stoppen.
    * @return  Fehlercode.
    */
    int FT_ComplianceStop();

Codebeispiel für Nachgiebigkeitsregelung
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestCompliance(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);

        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        int flag = 1;
        int sensor_id = 1;
        Object[] select =new Object[] { 1,1,1,0,0,0 };
        Object[] ft_pid =new Object[] { 0.0005,0.0,0.0,0.0,0.0,0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 100.0;
        double max_ang = 0.0;

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        DescPose  offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);


        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ft.fx = -10.0;
        ft.fy = -10.0;
        ft.fz = -10.0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        double p = 0.00005;
        double force = 30.0;
        int rtn = robot.FT_ComplianceStart(p, force);

        int count = 15;
        while (count>0)
        {
            robot.MoveL(j1, desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 1, offset_pos,0,10);
            robot.MoveL(j2, desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 0, offset_pos,0,10);
            count -= 1;
        }
        robot.FT_ComplianceStop();
        flag = 0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        robot.CloseRPC();
        return 0;
    }

Nutzlastidentifikation initialisieren
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Initialisiert die Nutzlastidentifikation (Dynamikfilter).
    * @return Fehlercode.
    */
    int LoadIdentifyDynFilterInit();

Nutzlastidentifikations-Variablen initialisieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Initialisiert die Variablen der Nutzlastidentifikation.
    * @return Fehlercode.
    */
    int LoadIdentifyDynVarInit();

Hauptprogramm der Nutzlastidentifikation
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Hauptprogramm der Nutzlastidentifikation.
    * @param [in] joint_torque Gelenkdrehmomente (Object[] erwartet, z.B. Double[]).
    * @param [in] joint_pos Gelenkpositionen (Object[] erwartet, z.B. Double[]).
    * @param [in] t Abtastperiode.
    * @return Fehlercode.
    */
    int LoadIdentifyMain(Object[] joint_torque, Object[] joint_pos, double t);

Ergebnis der Nutzlastidentifikation abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt das Ergebnis der Nutzlastidentifikation zurück.
    * @param [in] gain Koeffizienten (Object[] erwartet, z.B. Double[]).
    * @return List[0]: Fehlercode; List[1]: double weight Nutzlastgewicht; List[2]: double x Nutzlastschwerpunkt X (mm); List[3]: double y Nutzlastschwerpunkt Y (mm); List[4]: double z Nutzlastschwerpunkt Z (mm).
    */
    List<Number> LoadIdentifyGetResult(Object[] gain);

Codebeispiel für Roboter-Nutzlastidentifikation
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestIdentify(Robot robot)
    {
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();

        retval = robot.LoadIdentifyDynVarInit();

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0,0,0,0,0,0);
        List<Number> joint_toq=new ArrayList<>();
        robot.GetActualJointPosDegree( posJ);
        posJ.J2 = posJ.J2 + 10;
        joint_toq=robot.GetJointTorques(0);

        Object[] gain =new Object[] { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
        double weight = 0;
        DescTran load_pos=new DescTran(0,0,0);
        List<Number> num=new ArrayList<>();
        num = robot.LoadIdentifyGetResult(gain);

        robot.CloseRPC();
        return 0;

    }

Unterstütztes Ziehen mit Kraftsensor
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: java
    :linenos:

    /**
    * @brief Unterstütztes Ziehen mit Kraftsensor.
    * @param [in] status Steuerungsstatus, 0-deaktivieren; 1-aktivieren.
    * @param [in] asaptiveFlag Adaptivitätsflag, 0-deaktivieren; 1-aktivieren.
    * @param [in] interfereDragFlag Interferenzbereich-Ziehflag, 0-deaktivieren; 1-aktivieren.
    * @param [in] ingularityConstraintsFlag Singularitätsstrategie, 0-vermeiden; 1-durchqueren.
    * @param [in] forceCollisionFlag Kollisionserkennungsflag beim unterstützten Ziehen; 0-deaktivieren; 1-aktivieren.
    * @param [in] M Trägheitskoeffizienten (Object[] erwartet, z.B. Double[] der Länge 6).
    * @param [in] B Dämpfungskoeffizienten (Object[] erwartet, z.B. Double[] der Länge 6).
    * @param [in] K Steifigkeitskoeffizienten (Object[] erwartet, z.B. Double[] der Länge 6).
    * @param [in] F Sechsdimensionale Kraftschwellen für das Ziehen (Object[] erwartet, z.B. Double[] der Länge 6).
    * @param [in] Fmax Maximale Zugkraftbegrenzung Nm.
    * @param [in] Vmax Maximale Gelenkgeschwindigkeitsbegrenzung °/s.
    * @return  Fehlercode.
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag, int ingularityConstraintsFlag, int forceCollisionFlag, Object[] M, Object[] B, Object[] K, Object[] F, double Fmax, double Vmax);

Schaltzustand des kraftunterstützten Ziehens abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Schaltzustand des kraftunterstützten Ziehens zurück.
    * @return List[0]: Fehlercode; List[1]: dragState Steuerungsstatus des kraftunterstützten Ziehens, 0-deaktiviert; 1-aktiviert; List[2]: sixDimensionalDragState Steuerungsstatus des 6-Achsen-kraftunterstützten Ziehens, 0-deaktiviert; 1-aktiviert.
    */
    List<Integer> GetForceAndTorqueDragState();

Automatische Aktivierung des Kraftsensors nach Fehlerlöschung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Automatische Aktivierung des Kraftsensors nach Fehlerlöschung.
    * @param [in] status Steuerungsstatus, 0-deaktivieren; 1-aktivieren.
    * @return Fehlercode.
    */
    int SetForceSensorDragAutoFlag(int status);

Codebeispiel für kraftunterstütztes Ziehen mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestEndForceDragCtrl(Robot robot)
    {
        DescTran tr1 = new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        robot.SetForceSensorDragAutoFlag(1);

        Object[] M =new Object[] { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        Object[] B =new Object[] { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        Object[] K =new Object[] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        Object[] F =new Object[] { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);

        robot.Sleep(10000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        List<Integer> state=new ArrayList<>();
        state=robot.GetForceAndTorqueDragState();

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
        return 0;
    }

Schalter und Parameter für gemischtes Ziehen mit 6-Achsen-Kraft und Gelenkimpedanz einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt Schalter und Parameter für gemischtes Ziehen mit 6-Achsen-Kraft und Gelenkimpedanz ein.
    * @param [in] status Steuerungsstatus, 0-deaktivieren; 1-aktivieren.
    * @param [in] impedanceFlag Impedanz-Aktivierungsflag, 0-deaktivieren; 1-aktivieren.
    * @param [in] lamdeGain Zugverstärkung (Object[] erwartet, z.B. Double[] der Länge 6).
    * @param [in] KGain Steifigkeitsverstärkung (Object[] erwartet, z.B. Double[] der Länge 6).
    * @param [in] BGain Dämpfungsverstärkung (Object[] erwartet, z.B. Double[] der Länge 6).
    * @param [in] dragMaxTcpVel Maximale Endlineargeschwindigkeitsbegrenzung beim Ziehen.
    * @param [in] dragMaxTcpOriVel Maximale Endwinkelgeschwindigkeitsbegrenzung beim Ziehen.
    * @return  Fehlercode.
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, Object[] lamdeGain, Object[] KGain, Object[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Codebeispiel für gemischtes Ziehen mit 6-Achsen-Kraft und Gelenkimpedanz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestForceAndJointImpedance(Robot robot)
    {
        robot.DragTeachSwitch(1);
        Object[] lamdeDain =new Object[] { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        Object[] KGain = new Object[]{ 0, 0, 0, 0, 0, 0 };
        Object[] BGain =new Object[] { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.Sleep(10000);

        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.CloseRPC();
        return 0;
    }

Impedanzregelung Start/Stopp
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Impedanzregelung Start/Stopp.
    * @param [in] status 0: deaktivieren; 1-aktivieren.
    * @param [in] workSpace 0-Gelenkraum; 1-Kartesischer Raum.
    * @param [in] forceThreshold Auslösekraftschwelle (N) (double[] der Länge 6).
    * @param [in] m Massenparameter (double[] der Länge 6).
    * @param [in] b Dämpfungsparameter (double[] der Länge 6).
    * @param [in] k Steifigkeitsparameter (double[] der Länge 6).
    * @param [in] maxV Maximale Lineargeschwindigkeit (mm/s).
    * @param [in] maxVA Maximale Linearbeschleunigung (mm/s²).
    * @param [in] maxW Maximale Winkelgeschwindigkeit (°/s).
    * @param [in] maxWA Maximale Winkelbeschleunigung (°/s²).
    * @return Fehlercode.
    */
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA);

Codebeispiel für Roboter-Impedanzregelung Start/Stopp
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestImpedanceControl(Robot robot)
    {
        JointPos j1=new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2=new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1=new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2=new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 200.0;
        double ovl = 100.0;
        double blendT = -1.0;
        double blendR = -1.0;
        int flag = 0;
        int search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        System.out.println("FT config:"+con.company+","+con.device+","+con.softwareVersion+"con"+ con.bus);
        robot.Sleep(1000);
        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);
        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);
        robot.FT_SetZero(1);
        robot.Sleep(1000);
        double[] forceThreshold = { 30,30,30,5,5,5 };
        double[] m= { 0.1,0.1,0.1,0.02,0.02,0.02 };
        double[] b = { 1,1,1,0.08,0.08,0.08 };
        double[] k = { 0,0,0,0,0,0 };
        int rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        System.out.println("ImpedanceControlStartStop errcode:"+ rtn);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        System.out.println("movel errcode:"+ rtn);
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        robot.CloseRPC();
        return 0;
    }

Drehmomentkompensationsfunktion und -koeffizienten aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Aktiviert die Drehmomentkompensationsfunktion und setzt die Koeffizienten.
    * @param  status Schalter, 0-deaktivieren; 1-aktivieren.
    * @param  torqueCoeff J1-J6 Drehmomentkompensationskoeffizienten [0-1] (double[] der Länge 6).
    * @return Fehlercode.
    */
    public int SetCoderCompenParams(int status, double[] torqueCoeff);