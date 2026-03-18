Roboter-Kraftsteuerung
============================

.. toctree::
    :maxdepth: 5

Kraftsensor konfigurieren
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Konfiguriert den Kraftsensor
    * @param  [in] company  Kraftsensor-Hersteller, 17-Kunwei Technology
    * @param  [in] device  Gerätenummer, derzeit nicht verwendet, Standard 0
    * @param  [in] softvesion  Softwareversionsnummer, derzeit nicht verwendet, Standard 0
    * @param  [in] bus  Position des Geräts am Flanschbus, derzeit nicht verwendet, Standard 0
    * @return  Fehlercode
    */
    int FT_SetConfig(int company, int device, int softvesion, int bus);

Kraftsensor-Konfiguration abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Kraftsensor-Konfiguration zurück
    * @param [out] deviceID Kraftsensor-Nummer
    * @param [out] company Kraftsensor-Hersteller, 17-Kunwei Technology, 19-Aerospace 11th Institute, 20-ATI Sensor, 21-Zhongke Midian, 22-Weihang Minxin
    * @param [out] device  Gerätenummer, Kunwei(0-KWR75B), Aerospace 11th Institute(0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A)
    * @param [out] softvesion Softwareversionsnummer, derzeit nicht verwendet, Standard 0
    * @return Fehlercode
    */
    int FT_GetConfig(ref int deviceID, ref int company, ref int device, ref int softvesion);

Kraftsensor aktivieren
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Aktiviert den Kraftsensor
    * @param  [in] act  0-Reset, 1-Aktivieren
    * @return  Fehlercode
    */
    int FT_Activate(byte act);

Kraftsensor Nullpunktkorrektur
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Nullpunktkorrektur des Kraftsensors
    * @param  [in] act  0-Nullpunkt entfernen, 1-Nullpunkt korrigieren
    * @return  Fehlercode
    */
    int FT_SetZero(byte act);

Referenzkoordinatensystem für Kraftsensor einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt das Referenzkoordinatensystem für den Kraftsensor ein
    * @param  [in] ref  0-Werkzeugkoordinatensystem, 1-Basiskoordinatensystem
    * @return  Fehlercode
    */
    int FT_SetRCS(byte type);

Nutzlastgewicht unter dem Kraftsensor einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt das Nutzlastgewicht unter dem Kraftsensor ein
    * @param  [in] weight Nutzlastgewicht in kg
    * @return  Fehlercode
    */
    int SetForceSensorPayLoad(double weight);

Nutzlastschwerpunkt unter dem Kraftsensor einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt den Nutzlastschwerpunkt unter dem Kraftsensor ein
    * @param  [in] x Nutzlastschwerpunkt x in mm
    * @param  [in] y Nutzlastschwerpunkt y in mm
    * @param  [in] z Nutzlastschwerpunkt z in mm
    * @return  Fehlercode
    */
    int SetForceSensorPayLoadCog(double x, double y, double z);

Nutzlastgewicht unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt das Nutzlastgewicht unter dem Kraftsensor zurück
    * @param  [out] weight Nutzlastgewicht in kg
    * @return  Fehlercode
    */
    int GetForceSensorPayLoad(ref double weight);

Nutzlastschwerpunkt unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt den Nutzlastschwerpunkt unter dem Kraftsensor zurück
    * @param  [out] x Nutzlastschwerpunkt x in mm
    * @param  [out] y Nutzlastschwerpunkt y in mm
    * @param  [out] z Nutzlastschwerpunkt z in mm
    * @return  Fehlercode
    */
    int GetForceSensorPayLoadCog(ref double x, ref double y, ref double z);

Automatische Nullpunktkorrektur des Kraftsensors
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Automatische Nullpunktkorrektur des Kraftsensors
    * @param  [out] weight Sensormasse in kg
    * @param  [out] pos Sensorsschwerpunkt in mm
    * @return  Fehlercode
    */
    int ForceSensorAutoComputeLoad(ref double weight, ref DescTran pos);

Kraft-/Drehmomentdaten im Referenzkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt Kraft-/Drehmomentdaten im Referenzkoordinatensystem zurück
    * @param  [out] ft  Kraft/Drehmoment, fx, fy, fz, tx, ty, tz
    * @return  Fehlercode
    */
    int FT_GetForceTorqueRCS(byte flag, ref ForceTorque ft);

Rohdaten des Kraftsensors (Kraft/Drehmoment) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die rohen Kraft-/Drehmomentdaten des Kraftsensors zurück
    * @param  [out] ft  Kraft/Drehmoment, fx, fy, fz, tx, ty, tz
    * @return  Fehlercode
    */
    int FT_GetForceTorqueOrigin(byte flag, ref ForceTorque ft);

Codebeispiel für Kraftsensor-Konfiguration und automatische Nullpunktkorrektur
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button54_Click(object sender, EventArgs e)
    {
        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0, 0, 0, 0, 0, 0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin:{ft.fx},{ft.fy},{ft.fz},{ft.tx},{ft.ty},{ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose ftCoord = new DescPose(0, 0, 0, 0, 0, 0);
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayLoad(0.824);
        robot.SetForceSensorPayLoadCog(0.778, 2.554, 48.765);
        double weight = 0;
        double x = 0, y = 0, z = 0;
        robot.GetForceSensorPayLoad(ref weight);
        robot.GetForceSensorPayLoadCog(ref x, ref y, ref z);
        Console.WriteLine($"the FT load is {weight}, {x} {y} {z}");

        robot.SetForceSensorPayLoad(0);
        robot.SetForceSensorPayLoadCog(0, 0, 0);

        double computeWeight = 0;
        DescTran tran = new DescTran(0, 0, 0);
        robot.ForceSensorAutoComputeLoad(ref weight, ref tran);
        Console.WriteLine($"the result is weight {weight} pos is {tran.x} {tran.y} {tran.z}");

    }

Nutzlastgewichts-Identifikation aufzeichnen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Zeichnet die Nutzlastgewichts-Identifikation auf
    * @param  [in] id  Sensorkoordinatensystem-Nummer, Bereich [1~14]
    * @return  Fehlercode
    */
    int FT_PdIdenRecord(int id);

Nutzlastgewichts-Identifikation berechnen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Berechnet die Nutzlastgewichts-Identifikation
    * @param  [out] weight  Nutzlastgewicht, Einheit kg
    * @return  Fehlercode
    */
    int FT_PdIdenCompute(ref double weight);

Nutzlastschwerpunkt-Identifikation aufzeichnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Zeichnet die Nutzlastschwerpunkt-Identifikation auf
    * @param  [in] id  Sensorkoordinatensystem-Nummer, Bereich [1~14]
    * @param  [in] index Punktnummer, Bereich [1~3]
    * @return  Fehlercode
    */
    int FT_PdCogIdenRecord(int id, int index);

Nutzlastschwerpunkt-Identifikation berechnen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Berechnet die Nutzlastschwerpunkt-Identifikation
    * @param  [out] cog  Nutzlastschwerpunkt, Einheit mm
    * @return  Fehlercode
    */
    int FT_PdCogIdenCompute(ref DescTran cog);

Codebeispiel für Kraftsensor-Nutzlastidentifikation
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnFTPdCog_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin: {ft.fx}, {ft.fy}, {ft.fz}, {ft.tx}, {ft.ty}, {ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose tcoord = new DescPose(0, 0, 35.0, 0, 0, 0);
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        Thread.Sleep(1000);

        double weight = 0.0f;
        robot.FT_PdIdenCompute(ref weight);
        Console.WriteLine($"payload weight: {weight}");

        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);

        DescTran cog = new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(ref cog);
        Console.WriteLine($"cog: {cog.x}, {cog.y}, {cog.z}");
    }

Kollisionsschutz
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Kollisionsschutz
    * @param  [in] flag 0-Kollisionsschutz deaktivieren, 1-Kollisionsschutz aktivieren
    * @param  [in] sensor_id Kraftsensor-Nummer
    * @param  [in] select  Auswahl der sechs Freiheitsgrade für die Kollisionserkennung, 0-nicht erkennen, 1-erkennen
    * @param  [in] ft  Kollisionskraft/-drehmoment, fx, fy, fz, tx, ty, tz
    * @param  [in] max_threshold Maximalschwelle
    * @param  [in] min_threshold Minimalschwelle
    * @note   Erkennungsbereich für Kraft/Drehmoment: (ft - min_threshold, ft + max_threshold)
    * @return  Fehlercode
    */
    int FT_Guard(int flag, int sensor_id, int[] select, ForceTorque ft, double[] max_threshold, double[] min_threshold);

Codebeispiel für Kollisionsschutz
++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnFTGuard_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte sensor_id = 1;
        int[] select = { 1, 1, 1, 1, 1, 1 };
        double[] max_threshold = { 10.0f, 10.0f, 10.0f, 10.0f, 10.0f, 10.0f };
        double[] min_threshold = { 5.0f, 5.0f, 5.0f, 5.0f, 5.0f, 5.0f };

        ForceTorque ft = new ForceTorque();
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.FT_Guard(1, sensor_id, select,  ft, max_threshold, min_threshold);
        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);

        robot.FT_Guard(0, sensor_id, select, ft, max_threshold, min_threshold);
    }

Konstantkraftregelung
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Konstantkraftregelung
    * @param  [in] flag 0-Konstantkraftregelung deaktivieren, 1-Konstantkraftregelung aktivieren
    * @param  [in] sensor_id Kraftsensor-Nummer
    * @param  [in] select  Auswahl der sechs Freiheitsgrade für die Erkennung, 0-nicht erkennen, 1-erkennen
    * @param  [in] ft  Kraft-/Drehmoment-Sollwerte, fx, fy, fz, tx, ty, tz
    * @param  [in] ft_pid Kraft-PID-Parameter, Drehmoment-PID-Parameter
    * @param  [in] adj_sign Adaptive Start/Stopp-Steuerung, 0-deaktivieren, 1-aktivieren
    * @param  [in] ILC_sign ILC Start/Stopp, 0-stopp, 1-Training, 2-Praxis
    * @param  [in] max_dis Maximale Anpassungsstrecke, Einheit mm
    * @param  [in] max_ang Maximaler Anpassungswinkel, Einheit deg
    * @param  [in] M rx, ry Massenparameter [0.1-10], Standard 2
    * @param  [in] B rx, ry Dämpfungsparameter [0.1-50], Standard 8
    * @param  [in] threshold rx, ry Startschwelle [0-10], Standard 0.2
    * @param  [in] adjustCoeff rx, ry Drehmoment-Einstellkoeffizient [0-1], Standard 1
    * @param  [in] polishRadio Schleifradius, Einheit mm
    * @param  [in] filter_Sign Filteraktivierungsflag 0-aus; 1-ein, Standard aus
    * @param  [in] posAdapt_sign Pose-Anpassungsaktivierungsflag 0-aus; 1-ein, Standard aus
    * @param  [in] isNoBlock Blockierungsflag, 0-blockierend; 1-nicht blockierend
    * @return  Fehlercode
    */
    public int FT_Control(byte flag, int sensor_id, byte[] select, ForceTorque ft, float[] ft_pid, byte adj_sign, byte ILC_sign, float max_dis, float max_ang, double[] M, double[] B, double[] threshold, double[] adjustCoeff, double polishRadio, int filter_Sign, int posAdapt_sign, int isNoBlock)

Codebeispiel für Konstantkraftregelung mit Dämpfung
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    public void TestFTControlWithAdjustCoeff()
    {
        int rtn;
        int sensor_id = 10;
        byte[] select = new byte[6] { 0, 0, 1, 0, 0, 0 };
        float[] ft_pid = new float[6] { 0.0008f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0;
        byte ILC_sign = 0;
        float max_dis = 1000.0f;
        float max_ang = 20.0f;
        ForceTorque ft = new ForceTorque();
        ft.fz = -10.0f;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        JointPos j1 = new JointPos(80.765f, -98.795f, 106.548f, -97.734f, -89.999f, 94.842f);
        JointPos j2 = new JointPos(43.067f, -84.429f, 92.620f, -98.175f, -90.011f, 57.144f);
        DescPose desc_p1 = new DescPose(5.009f, -547.463f, 262.053f, -179.999f, -0.019f, 75.923f);
        DescPose desc_p2 = new DescPose(-347.966f, -547.463f, 262.048f, -180.000f, -0.019f, 75.923f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = new double[2] { 2.0, 2.0 };
        double[] B = new double[2] { 15.0, 15.0 };
        double[] threshold = new double[2] { 1.0, 1.0 };
        double[] adjustCoeff = new double[2] { 1.0, 0.8 };
        double polishRadio = 0.0;
        int filter_Sign = 0;
        int posAdapt_sign = 1;
        int isNoBlock = 0;
        while (true)
        {
            rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control start rtn is {rtn}");
            robot.MoveL(j1, desc_p1, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            robot.MoveL(j2, desc_p2, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control end rtn is {rtn}");
        }
    }

Rotationseinfügung
++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Rotationseinfügung
    * @param [in] rcs Referenzkoordinatensystem, 0-Werkzeugkoordinatensystem, 1-Basiskoordinatensystem
    * @param [in] angVelRot Rotationswinkelgeschwindigkeit, Einheit deg/s
    * @param [in] ft Kraft-/Drehmomentschwelle, fx, fy, fz, tx, ty, tz, Bereich [0~100]
    * @param [in] max_angle Maximaler Rotationswinkel, Einheit deg
    * @param [in] orn Kraft-/Drehmomentrichtung, 1-entlang der z-Achse, 2-um die z-Achse
    * @param [in] max_angAcc Maximale Rotationsbeschleunigung, Einheit deg/s^2, derzeit nicht verwendet, Standard 0
    * @param [in] rotorn Rotationsrichtung, 1-im Uhrzeigersinn, 2-gegen Uhrzeigersinn
    * @param [in] strategy Behandlungsstrategie bei nicht erkannter Kraft, 0-Fehler; 1-Warnung, Bewegung fortsetzen
    * @return Fehlercode
    */
    public int FT_RotInsertion(int rcs, double angVelRot, double ft, double max_angle, int orn, double max_angAcc, int rotorn, int strategy)

Codebeispiel für Rotationseinfügung mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    public void TestMove()
    {
        int rtn;
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos j2 = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos j3 = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);
        JointPos j4 = new JointPos(-31.154f, -95.317f, 94.276f, -88.079f, -89.740f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose desc_pos2 = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose desc_pos3 = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);
        DescPose desc_pos4 = new DescPose(-443.165f, 147.881f, 480.951f, 179.511f, -0.775f, -15.409f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float oacc = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos,j1, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        Console.WriteLine($"MoveCart errcode:{rtn}");
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,desc_pos4, tool, user, vel, acc, epos, flag, offset_pos,ovl, blendR, -1, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
    }

Nachgiebigkeitsregelung starten
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Nachgiebigkeitsregelung starten
    * @param  [in] p Positionseinstellkoeffizient oder Nachgiebigkeitskoeffizient
    * @param  [in] force Kraftschwelle zum Starten der Nachgiebigkeit, Einheit N
    * @return  Fehlercode
    */
    int FT_ComplianceStart(float p, float force);

Nachgiebigkeitsregelung stoppen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Nachgiebigkeitsregelung stoppen
    * @return  Fehlercode
    */
    int FT_ComplianceStop();

Codebeispiel für Nachgiebigkeitsregelung
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnComplience_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte flag = 1;
        int sensor_id = 1;
        int[] select = { 1, 1, 1, 0, 0, 0 };
        double[] ft_pid = { 0.0005f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0, ILC_sign = 0;
        float max_dis = 100.0f, max_ang = 0.0f;

        ForceTorque ft = new ForceTorque { fx = -10.0, fy = -10.0, fz = -10.0 };
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
        float p = 0.00005f;
        float force = 30.0f;
        int rtn = robot.FT_ComplianceStart(p, force);
        Console.WriteLine($"FT_ComplianceStart rtn is {rtn}");

        int count = 5;
        while (count-- > 0)
        {
        robot.MoveL(j1, desc_p1, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 1, offset_pos);
        robot.MoveL(j2, desc_p2, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 0, offset_pos);
        }

        robot.FT_ComplianceStop();
        Console.WriteLine($"FT_ComplianceStop rtn is {rtn}");

        flag = 0;
        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
    }

Nutzlastidentifikation initialisieren
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Initialisiert die Nutzlastidentifikation (Dynamikfilter)
    * @return Fehlercode
    */
    int LoadIdentifyDynFilterInit();

Nutzlastidentifikations-Variablen initialisieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Initialisiert die Variablen der Nutzlastidentifikation
    * @return Fehlercode
    */
    int LoadIdentifyDynVarInit();

Hauptprogramm der Nutzlastidentifikation
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Hauptprogramm der Nutzlastidentifikation
    * @param [in] joint_torque Gelenkdrehmomente
    * @param [in] joint_pos Gelenkpositionen
    * @param [in] t Abtastperiode
    * @return Fehlercode
    */
    int LoadIdentifyMain(double[] joint_torque, double[] joint_pos, double t);

Ergebnis der Nutzlastidentifikation abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt das Ergebnis der Nutzlastidentifikation zurück
    * @param [in] gain  Koeffizienten für Gravitationsterme double[6], Koeffizienten für Zentrifugalterme double[6]
    * @param [out] weight Nutzlastgewicht
    * @param [out] cog Nutzlastschwerpunkt
    * @return Fehlercode
    */
    int LoadIdentifyGetResult(double[] gain, ref double weight, ref DescTran cog);

Codebeispiel für Roboter-Nutzlastidentifikation
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button74_Click(object sender, EventArgs e)
    {
        int rtn;
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();
        Console.WriteLine("LoadIdentifyDynFilterInit retval is: " + retval);

        retval = robot.LoadIdentifyDynVarInit();
        Console.WriteLine("LoadIdentifyDynVarInit retval is: " + retval);

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0, 0, 0, 0, 0, 0);
        double[] joint_toq = new double[6] { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        robot.GetActualJointPosDegree(0, ref posJ);
        posJ.jPos[1] = posJ.jPos[1] + 10;
        robot.GetJointTorques(0, joint_toq);
        joint_toq[1] = joint_toq[1] + 2;

        double[] tmpTorque = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        for (int i = 0; i < 6; i++)
        {
            tmpTorque[i] = joint_toq[i];
        }

        retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
        Console.WriteLine("LoadIdentifyMain retval is: " + retval);

        double[] gain = new double[12] { 0, 0.05, 0, 0, 0, 0, 0, 0.02, 0, 0, 0, 0 };
        double weight = 0;
        DescTran load_pos = new DescTran(0, 0, 0);
        retval = robot.LoadIdentifyGetResult(gain, ref weight, ref load_pos);
        Console.WriteLine("LoadIdentifyGetResult retval is: {0}; weight is {1} cog is {2} {3} {4}", retval, weight, load_pos.x, load_pos.y, load_pos.z);
    }

Unterstütztes Ziehen mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Unterstütztes Ziehen mit Kraftsensor
    * @param  [in] status Steuerungsstatus, 0-deaktivieren; 1-aktivieren
    * @param  [in] asaptiveFlag Adaptivitätsflag, 0-deaktivieren; 1-aktivieren
    * @param  [in] interfereDragFlag Interferenzbereich-Ziehflag, 0-deaktivieren; 1-aktivieren
    * @param  [in] ingularityConstraintsFlag Singularitätsstrategie, 0-vermeiden; 1-durchqueren
    * @param  [in] forceCollisionFlag Kollisionserkennungsflag beim unterstützten Ziehen; 0-deaktivieren; 1-aktivieren
    * @param  [in] M Trägheitskoeffizienten
    * @param  [in] B Dämpfungskoeffizienten
    * @param  [in] K Steifigkeitskoeffizienten
    * @param  [in] F Sechsdimensionale Kraftschwellen für das Ziehen
    * @param  [in] Fmax Maximale Zugkraftbegrenzung Nm
    * @param  [in] Vmax Maximale Gelenkgeschwindigkeitsbegrenzung °/s
    * @return  Fehlercode
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag, int ingularityConstraintsFlag, int forceCollisionFlag, double[] M, double[] B, double[] K, double[] F, double Fmax, double Vmax);

Schaltzustand des kraftunterstützten Ziehens abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt den Schaltzustand des kraftunterstützten Ziehens zurück
    * @param  [out] dragState Steuerungsstatus des kraftunterstützten Ziehens, 0-deaktiviert; 1-aktiviert
    * @param  [out] sixDimensionalDragState Steuerungsstatus des 6-Achsen-kraftunterstützten Ziehens, 0-deaktiviert; 1-aktiviert
    * @return  Fehlercode
    */
    int GetForceAndTorqueDragState(ref int dragState, ref int sixDimensionalDragState);

Automatische Aktivierung des Kraftsensors nach Fehlerlöschung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Automatische Aktivierung des Kraftsensors nach Fehlerlöschung
    * @param  [in] status Steuerungsstatus, 0-deaktivieren; 1-aktivieren
    * @return  Fehlercode
    */
    int SetForceSensorDragAutoFlag(int status);

Codebeispiel für kraftunterstütztes Ziehen mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button61_Click(object sender, EventArgs e)
    {
        robot.SetForceSensorDragAutoFlag(1);
        double[] M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        double[] B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        double[] K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };

        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);
        robot.WaitMs(5000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        robot.GetForceAndTorqueDragState(ref dragState, ref sixDimensionalDragState);
        Console.WriteLine($"the drag state is {dragState} {sixDimensionalDragState}");

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
    }

Schalter und Parameter für gemischtes Ziehen mit 6-Achsen-Kraft und Gelenkimpedanz einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt Schalter und Parameter für gemischtes Ziehen mit 6-Achsen-Kraft und Gelenkimpedanz ein
    * @param  [in] status Steuerungsstatus, 0-deaktivieren; 1-aktivieren
    * @param  [in] impedanceFlag Impedanz-Aktivierungsflag, 0-deaktivieren; 1-aktivieren
    * @param  [in] lamdeDain Zugverstärkung
    * @param  [in] KGain Steifigkeitsverstärkung
    * @param  [in] BGain Dämpfungsverstärkung
    * @param  [in] dragMaxTcpVel Maximale Endlineargeschwindigkeitsbegrenzung beim Ziehen
    * @param  [in] dragMaxTcpOriVel Maximale Endwinkelgeschwindigkeitsbegrenzung beim Ziehen
    * @return  Fehlercode
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, double[] lamdeDain, double[] KGain, double[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Codebeispiel für kraftunterstütztes Ziehen mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button62_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        double[] lambdaGain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        double[] kGain = { 0, 0, 0, 0, 0, 0 };
        double[] bGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
        Thread.Sleep(5000); 
        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
    }

Impedanzregelung Start/Stopp
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    /**
    * @brief Impedanzregelung Start/Stopp
    * @param [in] status 0: deaktivieren; 1-aktivieren
    * @param [in] workSpace 0-Gelenkraum; 1-Kartesischer Raum
    * @param [in] forceThreshold Auslösekraftschwelle (N)
    * @param [in] m Massenparameter
    * @param [in] b Dämpfungsparameter
    * @param [in] k Steifigkeitsparameter
    * @param [in] maxV Maximale Lineargeschwindigkeit (mm/s)
    * @param [in] maxVA Maximale Linearbeschleunigung (mm/s²)
    * @param [in] maxW Maximale Winkelgeschwindigkeit (°/s)
    * @param [in] maxWA Maximale Winkelbeschleunigung (°/s²)
    * @return Fehlercode
    */
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA)

Codebeispiel für Roboter-Impedanzregelung Start/Stopp
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: csharp
    :linenos:

    public void TestImpedanceControl()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        int rtn;
        JointPos j1 = new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2 = new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1 = new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2 = new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);

        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 200.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        float blendR = -1.0f;

        byte flag = 0;

        byte search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);
        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        double[] forceThreshold = new double[] { 30, 30, 30, 5, 5, 5 };
        double[] m = new double[] { 0.1, 0.1, 0.1, 0.02, 0.02, 0.02 };
        double[] b = new double[] { 1, 1, 1, 0.08, 0.08, 0.08 };
        double[] k = new double[] { 0, 0, 0, 0, 0, 0 };
        rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        Console.WriteLine($"ImpedanceControlStartStop errcode:{rtn}");
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        Console.WriteLine($"movel errcode:{rtn}");
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
    }

Drehmomentkompensationsfunktion und -koeffizienten aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Aktiviert die Drehmomentkompensationsfunktion und setzt die Koeffizienten
    * @param [in] status Schalter, 0-deaktivieren; 1-aktivieren
    * @param [in] torqueCoeff J1-J6 Drehmomentkompensationskoeffizienten [0-1]
    * @return Fehlercode
    */
    public int SerCoderCompenParams(int status, double[] torqueCoeff)