Roboter-Kraftregelung
=====================

.. toctree::
    :maxdepth: 5

Kraftsensor konfigurieren
+++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Kraftsensor konfigurieren
     * @param [in] company Kraftsensor-Hersteller, 17-Kunwei, 19-CASA, 20-ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
     * @param [in] device Gerätenummer, Kunwei(0-KWR75B), CASA(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A), NBIT(0-XLH93003ACS), Xinjingcheng XJC(0-XJC-6F-D82), NSR(0-NSR-FTSensorA)
     * @param [in] softvesion Softwareversionsnummer, vorübergehend nicht verwendet, Standard 0
     * @param [in] bus Position des Geräts am Endeffektor-Bus, vorübergehend nicht verwendet, Standard 0
     * @return Fehlercode
     */
    errno_t FT_SetConfig(int company, int device, int softvesion, int bus);

Kraftsensor-Konfiguration abrufen
+++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kraftsensor-Konfiguration abrufen
    * @param [out] company Kraftsensor-Hersteller
    * @param [out] device Gerätenummer
    * @param [out] softvesion Softwareversionsnummer
    * @param [out] bus Bus-Position
    * @return Fehlercode
    */
    errno_t FT_GetConfig(int *company, int *device, int *softvesion, int *bus);

Kraftsensor aktivieren
++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kraftsensor aktivieren
    * @param [in] act 0-Zurücksetzen, 1-Aktivieren
    * @return Fehlercode
    */
    errno_t FT_Activate(uint8_t act);

Kraftsensor Nullpunkt setzen (Tarieren)
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kraftsensor Nullpunkt setzen (Tarieren)
    * @param [in] act 0-Nullpunkt entfernen, 1-Nullpunkt korrigieren
    * @return Fehlercode
    */
    errno_t FT_SetZero(uint8_t act);

Referenzkoordinatensystem für Kraftsensor einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Referenzkoordinatensystem für Kraftsensor einstellen
    * @param [in] ref 0-Werkzeugkoordinatensystem, 1-Basiskoordinatensystem
    * @return Fehlercode
    */
    errno_t FT_SetRCS(uint8_t ref);

Lastgewicht unter dem Kraftsensor einstellen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Lastgewicht unter dem Kraftsensor einstellen
     * @param [in] weight Lastgewicht [kg]
     * @return Fehlercode
     */
    errno_t SetForceSensorPayload(double weight);

Lastschwerpunkt unter dem Kraftsensor einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Lastschwerpunkt unter dem Kraftsensor einstellen
     * @param [in] x Schwerpunkt x [mm]
     * @param [in] y Schwerpunkt y [mm]
     * @param [in] z Schwerpunkt z [mm]
     * @return Fehlercode
     */
    errno_t SetForceSensorPayloadCog(double x, double y, double z);

Lastgewicht unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Lastgewicht unter dem Kraftsensor abrufen
     * @param [out] weight Lastgewicht [kg]
     * @return Fehlercode
     */
    errno_t GetForceSensorPayload(double& weight);

Lastschwerpunkt unter dem Kraftsensor abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Lastschwerpunkt unter dem Kraftsensor abrufen
     * @param [out] x Schwerpunkt x [mm]
     * @param [out] y Schwerpunkt y [mm]
     * @param [out] z Schwerpunkt z [mm]
     * @return Fehlercode
     */
    errno_t GetForceSensorPayloadCog(double& x, double& y, double& z);

Automatische Nullpunktberechnung (Tarieren) des Kraftsensors
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Automatische Nullpunktberechnung (Tarieren) des Kraftsensors
     * @param [out] weight Sensor-eigenes Mass [kg] (oder resultierende Last?)
     * @param [out] pos Sensor-eigener Schwerpunkt [mm] (oder resultierender Schwerpunkt?)
     * @return Fehlercode
     */
    errno_t ForceSensorAutoComputeLoad(double& weight, DescTran& pos);

Kraft-/Drehmomentdaten im Referenzkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kraft-/Drehmomentdaten im Referenzkoordinatensystem abrufen
    * @param [out] ft Kraft/Drehmoment, fx, fy, fz, tx, ty, tz
    * @return Fehlercode
    */
    errno_t FT_GetForceTorqueRCS(ForceTorque *ft);

Rohe Kraft-/Drehmomentdaten des Sensors abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rohe Kraft-/Drehmomentdaten des Sensors abrufen
    * @param [out] ft Kraft/Drehmoment, fx, fy, fz, tx, ty, tz
    * @return Fehlercode
    */
    errno_t FT_GetForceTorqueOrigin(ForceTorque *ft);

Codebeispiel für Kraftsensor-Konfiguration und automatische Nullpunktberechnung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTInit(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose ftCoord = {};
      robot.FT_SetRCS(0, ftCoord);
      robot.SetForceSensorPayload(0.824);
      robot.SetForceSensorPayloadCog(0.778, 2.554, 48.765);
      double weight = 0;
      double x = 0, y = 0, z = 0;
      robot.GetForceSensorPayload(weight);
      robot.GetForceSensorPayloadCog(x, y, z);
      printf("the FT load is %lf, %lf %lf %lf\n", weight, x, y, z);
      robot.SetForceSensorPayload(0);
      robot.SetForceSensorPayloadCog(0, 0, 0);
      double computeWeight = 0;
      DescTran tran = {};
      robot.ForceSensorAutoComputeLoad(weight, tran);
      cout << "the result is weight " << weight << " pos is " << tran.x << " " << tran.y << " " << tran.z << endl;
      robot.CloseRPC();
      return 0;
    }


Lastgewichtserkennung aufzeichnen
+++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastgewichtserkennung aufzeichnen
    * @param [in] id Sensorkoordinatensystem-Nummer, Bereich [1~14]
    * @return Fehlercode
    */
    errno_t FT_PdIdenRecord(int id);

Lastgewichtserkennung berechnen
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastgewichtserkennung berechnen
    * @param [out] weight Lastgewicht [kg]
    * @return Fehlercode
    */
    errno_t FT_PdIdenCompute(float *weight);

Lastschwerpunkt-Erkennung aufzeichnen
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastschwerpunkt-Erkennung aufzeichnen
    * @param [in] id Sensorkoordinatensystem-Nummer, Bereich [1~14]
    * @param [in] index Punktnummer, Bereich [1~3]
    * @return Fehlercode
    */
    errno_t FT_PdCogIdenRecord(int id, int index);

Lastschwerpunkt-Erkennung berechnen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastschwerpunkt-Erkennung berechnen
    * @param [out] cog Lastschwerpunkt [mm]
    * @return Fehlercode
    */
    errno_t FT_PdCogIdenCompute(DescTran *cog);

Codebeispiel für Lastidentifikation mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTLoadCompute(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose tcoord = {};
      tcoord.tran.z = 35.0;
      robot.SetToolCoord(10, &tcoord, 1, 0, 0, 0);
      robot.FT_PdIdenRecord(10);
      robot.Sleep(1000);
      float weight = 0.0;
      robot.FT_PdIdenCompute(&weight);
      printf("payload weight:%f\n", weight);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 2);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 3);
      robot.Sleep(1000);
      DescTran cog;
      memset(&cog, 0, sizeof(DescTran));
      robot.FT_PdCogIdenCompute(&cog);
      printf("cog:%f,%f,%f\n", cog.x, cog.y, cog.z);
      robot.CloseRPC();
      return 0;
    }

Kollisionsüberwachung (Force Guard)
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kollisionsüberwachung (Force Guard)
    * @param [in] flag 0-deaktivieren, 1-aktivieren
    * @param [in] sensor_id Kraftsensor-Nummer
    * @param [in] select Auswahl der sechs Freiheitsgrade für die Kollisionserkennung, 0-nicht prüfen, 1-prüfen
    * @param [in] ft Kollisionskraft/-moment Schwellwerte (Mitte), fx,fy,fz,tx,ty,tz
    * @param [in] max_threshold Maximaler Schwellwert (obere Toleranz)
    * @param [in] min_threshold Minimaler Schwellwert (untere Toleranz)
    * @note Erkennungsbereich: (ft - min_threshold, ft + max_threshold)
    * @return Fehlercode
    */
    errno_t FT_Guard(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque *ft, float max_threshold[6], float min_threshold[6]);

Codebeispiel für Kollisionsüberwachung
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTGuard(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t sensor_id = 1;
      uint8_t select[6] = { 1,1,1,1,1,1 };
      float max_threshold[6] = { 10.0,10.0,10.0,10.0,10.0,10.0 };
      float min_threshold[6] = { 5.0,5.0,5.0,5.0,5.0,5.0 };
      ForceTorque ft;
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.FT_Guard(1, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_Guard(0, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.CloseRPC();
      return 0;
    }

Kraftregelung (Constant Force Control)
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kraftregelung (Constant Force Control)
    * @param [in] flag 0-deaktivieren, 1-aktivieren
    * @param [in] sensor_id Kraftsensor-Nummer
    * @param [in] select Auswahl der sechs Freiheitsgrade für die Kraftregelung, 0-nicht regeln, 1-regeln
    * @param [in] ft Soll-Kraft/-Moment, fx,fy,fz,tx,ty,tz
    * @param [in] ft_pid PID-Parameter für Kraftregelung [6] (Reihenfolge: fx,fy,fz,tx,ty,tz P-Anteil? I,D=0?)
    * @param [in] adj_sign Adaptive Regelung, 0-deaktivieren, 1-aktivieren
    * @param [in] ILC_sign ILC (Iterative Learning Control), 0-stopp, 1-Training, 2-Praxis
    * @param [in] max_dis Maximale Anpassungsdistanz [mm]
    * @param [in] max_ang Maximaler Anpassungswinkel [°]
    * @param [in] M Massenparameter für rx, ry [0.1-10], Standard 2
    * @param [in] B Dämpfungsparameter für rx, ry [0.1-50], Standard 8
    * @param [in] threshold Startschwellen für rx, ry [0-10], Standard 0.2
    * @param [in] adjustCoeff Momenten-Anpassungskoeffizient für rx, ry [0-1], Standard 1
    * @param [in] polishRadio Schleifscheibenradius [mm], für spezielle Anwendungen
    * @param [in] filter_Sign Filter aktivieren, 0-aus; 1-an, Standard aus
    * @param [in] posAdapt_sign Posennachgiebigkeit aktivieren, 0-aus; 1-an, Standard aus
    * @param [in] isNoBlock Blockierungs-Flag, 0-blockierend; 1-nicht blockierend
    * @return Fehlercode
    */
    errno_t FT_Control(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque* ft, float ft_pid[6], uint8_t adj_sign,
    uint8_t ILC_sign, float max_dis, float max_ang, double M[2], double B[2], double threshold[2], double adjustCoeff[2], double polishRadio = 0.0, int filter_Sign = 0, int posAdapt_sign = 0, int isNoBlock = 0);

Codebeispiel für Kraftregelung mit Dämpfung
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTControlWithAdjustCoeff(void)
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
      uint8_t sensor_id = 10;
      uint8_t select[6] = { 0,0,1,0,0,0 };
      float ft_pid[6] = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 1000.0;
      float max_ang = 20;
      ForceTorque ft = {0.0};
      ExaxisPos epos(0, 0, 0, 0);
      JointPos j1(80.765, -98.795, 106.548, -97.734, -89.999, 94.842);
      JointPos j2(43.067, -84.429, 92.620, -98.175, -90.011, 57.144);
      DescPose desc_p1(5.009, -547.463, 262.053, -179.999, -0.019, 75.923);
      DescPose desc_p2(-347.966, -547.463, 262.048, -180.000, -0.019, 75.923);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      double M[2] = { 2.0, 2.0 };
      double B[2] = { 15.0, 15.0 };
      double threshold[2] = {1.0, 1.0};
      double adjustCoeff[2] = {1.0, 0.8};
      double polishRadio = 0.0;
      int filter_Sign = 0;
      int posAdapt_sign = 1;
      int isNoBlock;
      ft.fz = -10.0;
      while(true)
      {
        rtn = robot.FT_Control(1, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
        printf("FT_Control start rtn is %d\n", rtn);
        robot.MoveL(&j1, &desc_p1, 1, 0, 100, 100, 100, -1, 0, &epos, 0, 0, &offset_pos, 200.0, 0);
        robot.MoveL(&j2, &desc_p2, 1, 0, 100, 100, 100, -1, 0, &epos, 0, 0, &offset_pos, 200.0, 0);
        rtn = robot.FT_Control(0, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
        printf("FT_Control end rtn is %d\n", rtn);
      }
      robot.CloseRPC();
      return 0;
    }

Spiralförmige Suche
++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Spiralförmige Suche (nach Kontakt)
    * @param [in] rcs Referenzkoordinatensystem, 0-Werkzeug, 1-Basis
    * @param [in] dr Radiuszunahme pro Umdrehung [mm]
    * @param [in] ft Kraft-/Momentenschwellwert für Abbruch [N] oder [Nm]
    * @param [in] max_t_ms Maximale Suchzeit [ms]
    * @param [in] max_vel Maximale Lineargeschwindigkeit [mm/s]
    * @return Fehlercode
    */
    errno_t FT_SpiralSearch(int rcs, float dr, float ft, float max_t_ms, float max_vel);

Rotatorisches Einführen
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rotatorisches Einführen (mit Kraftsuche)
    * @param [in] rcs Referenzkoordinatensystem, 0-Werkzeug, 1-Basis
    * @param [in] angVelRot Rotationsgeschwindigkeit [°/s]
    * @param [in] ft Kraft-/Momentenschwellwert für Abbruch [N] oder [Nm]
    * @param [in] max_angle Maximaler Rotationswinkel [°]
    * @param [in] orn Kraft-/Momentenrichtung, 1-entlang Z-Achse, 2-um Z-Achse
    * @param [in] max_angAcc Maximale Rotationsbeschleunigung [°/s²], vorübergehend nicht verwendet, Standard 0
    * @param [in] rotorn Rotationsrichtung, 1-im Uhrzeigersinn, 2-gegen Uhrzeigersinn
    * @param [in] strategy Strategie bei fehlender Kraft-/Momentenerkennung, 0-Fehler; 1-Warnung, Bewegung fortsetzen
    * @return Fehlercode
    */
    errno_t FT_RotInsertion(int rcs, float angVelRot, float ft, float max_angle, uint8_t orn, float max_angAcc, uint8_t rotorn, int strategy = 0);

Codebeispiel für rotatorisches Einführen mit Kraftsensor
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestMove(void)
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
        JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0;
        float acc = 100.0;
        float ovl = 100.0;
        float oacc = 100.0;
        float blendT = 0.0;
        float blendR = 0.0;
        uint8_t flag = 0;
        uint8_t search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&j2, &desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, oacc, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&j3, &desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &j4, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, oacc, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&j3, &desc_pos3, tool, user, vel, acc, &epos, &j1, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(&desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, -1, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, -1, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&desc_pos3, tool, user, vel, acc, &epos, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, blendR, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        robot.CloseRPC();
        return 0;
    }

Lineares Einführen
+++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lineares Einführen (mit Kraftsuche)
    * @param [in] rcs Referenzkoordinatensystem, 0-Werkzeug, 1-Basis
    * @param [in] ft Kraft-/Momentenschwellwert für Abbruch [N] oder [Nm]
    * @param [in] lin_v Lineare Suchgeschwindigkeit [mm/s]
    * @param [in] lin_a Lineare Suchbeschleunigung [mm/s²], vorübergehend nicht verwendet
    * @param [in] max_dis Maximale Einführdistanz [mm]
    * @param [in] linorn Einführrichtung, 0-negative Richtung, 1-positive Richtung
    * @return Fehlercode
    */
    errno_t FT_LinInsertion(int rcs, float ft, float lin_v, float lin_a, float max_dis, uint8_t linorn);

Codebeispiel für Spiral-Suche, Lineares Einführen etc.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTSearch(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t status = 1; 
      int sensor_num = 1; 
      float gain[6] = { 0.0001,0.0,0.0,0.0,0.0,0.0 }; 
      uint8_t adj_sign = 0; 
      uint8_t ILC_sign = 0; 
      float max_dis = 100.0; 
      float max_ang = 5.0; 
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      int rcs = 0; 
      float dr = 0.7; 
      float fFinish = 1.0; 
      float t = 60000.0;
      float vmax = 3.0;
      float force_goal = 20.0; 
      float lin_v = 0.0;
      float lin_a = 0.0;
      float disMax = 100.0;
      uint8_t linorn = 1; 
      float angVelRot = 2.0; 
      float forceInsertion = 1.0; 
      int angleMax = 45; 
      uint8_t orn = 1;
      float angAccmax = 0.0; 
      uint8_t rotorn = 1; 
      uint8_t select1[6] = { 0,0,1,1,1,0 }; 
      ft.fz = -10.0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_SpiralSearch(rcs, dr, fFinish, t, vmax);
      printf("FT_SpiralSearch rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select2[6] = { 1,1,1,0,0,0 }; 
      gain[0] = 0.00005;
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select3[6] = { 0,0,1,1,1,0 }; 
      ft.fz = -10.0;
      gain[0] = 0.0001;
      status = 1;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn);
      printf("FT_RotInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select4[6] = { 1,1,1,0,0,0 }; 
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Oberflächenlokalisierung
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oberflächenlokalisierung (FindSurface)
    * @param [in] rcs Referenzkoordinatensystem, 0-Werkzeug, 1-Basis
    * @param [in] dir Bewegungsrichtung, 1-positive Richtung, 2-negative Richtung
    * @param [in] axis Bewegungsachse, 1-x-Achse, 2-y-Achse, 3-z-Achse
    * @param [in] lin_v Lineare Suchgeschwindigkeit [mm/s]
    * @param [in] lin_a Lineare Suchbeschleunigung [mm/s²], vorübergehend nicht verwendet, Standard 0
    * @param [in] max_dis Maximale Suchdistanz [mm]
    * @param [in] ft Kraftschwellwert für Aktionsabbruch [N] (einzelner Wert für die gewählte Achse)
    * @return Fehlercode
    */
    errno_t FT_FindSurface(int rcs, uint8_t dir, uint8_t axis, float lin_v, float lin_a, float max_dis, float ft);

Berechnung der mittleren Ebene starten
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Berechnung der mittleren Ebene starten (für Zentrierung)
    * @return Fehlercode
    */
    errno_t FT_CalCenterStart();

Berechnung der mittleren Ebene beenden
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Berechnung der mittleren Ebene beenden
    * @param [out] pos Pose der mittleren Ebene (Zentrumsposition)
    * @return Fehlercode
    */
    errno_t FT_CalCenterEnd(DescPose *pos);

Codebeispiel für Oberflächenlokalisierung
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSurface(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      int rcs = 0;
      uint8_t dir = 1;
      uint8_t axis = 1;
      float lin_v = 3.0;
      float lin_a = 0.0;
      float maxdis = 50.0;
      float ft_goal = 2.0;
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose xcenter(0, 0, 0, 0, 0, 0);
      DescPose ycenter(0, 0, 0, 0, 0, 0);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      ft.fx = -2.0;
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_CalCenterStart();
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&xcenter);
      printf("xcenter:%f,%f,%f,%f,%f,%f\n", xcenter.tran.x, xcenter.tran.y, xcenter.tran.z, xcenter.rpy.rx, xcenter.rpy.ry, xcenter.rpy.rz);
      robot.MoveCart(&xcenter, 9, 0, 60.0, 50.0, 50.0, -1.0, -1);
      robot.FT_CalCenterStart();
      dir = 1;
      axis = 2;
      lin_v = 6.0;
      maxdis = 150.0;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&ycenter);
      printf("ycenter:%f,%f,%f,%f,%f,%f\n", ycenter.tran.x, ycenter.tran.y, ycenter.tran.z, ycenter.rpy.rx, ycenter.rpy.ry, ycenter.rpy.rz);
      robot.MoveCart(&ycenter, 9, 0, 60.0, 50.0, 50.0, 0.0, -1);
      robot.CloseRPC();
      return 0;
    }

Nachgiebigkeitsregelung (Compliance) starten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Nachgiebigkeitsregelung (Compliance) starten
    * @param [in] p Positionsregelungsfaktor oder Nachgiebigkeitskoeffizient
    * @param [in] force Kraftschwellwert für Aktivierung [N]
    * @return Fehlercode
    */
    errno_t FT_ComplianceStart(float p, float force);

Nachgiebigkeitsregelung (Compliance) stoppen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Nachgiebigkeitsregelung (Compliance) stoppen
    * @return Fehlercode
    */
    errno_t FT_ComplianceStop();

Codebeispiel für Nachgiebigkeitsregelung
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestCompliance(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t flag = 1;
      int sensor_id = 1;
      uint8_t select[6] = { 1,1,1,0,0,0 };
      float ft_pid[6] = { 0.0005,0.0,0.0,0.0,0.0,0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 100.0;
      float max_ang = 0.0;
      ForceTorque ft;
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      memset(&ft, 0, sizeof(ForceTorque));
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      ft.fx = -10.0;
      ft.fy = -10.0;
      ft.fz = -10.0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      float p = 0.00005;
      float force = 30.0;
      rtn = robot.FT_ComplianceStart(p, force);
      printf("FT_ComplianceStart rtn is %d\n", rtn);
      int count = 15;
      while (count)
      {
        robot.MoveL(&j1, &desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 1, &offset_pos);
        robot.MoveL(&j2, &desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 0, &offset_pos);
        count -= 1;
      }
      robot.FT_ComplianceStop();
      printf("FT_ComplianceStop rtn is %d\n", rtn);
      flag = 0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Lastidentifikation - Dynamikfilter initialisieren
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastidentifikation - Dynamikfilter initialisieren
    * @return Fehlercode
    */
    errno_t LoadIdentifyDynFilterInit();

Lastidentifikation - Variablen initialisieren
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastidentifikation - Variablen initialisieren
    * @return Fehlercode
    */
    errno_t LoadIdentifyDynVarInit();

Lastidentifikation - Hauptprogramm
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastidentifikation - Hauptprogramm
    * @param [in] joint_torque Gemessene Gelenkmomente [Nm]
    * @param [in] joint_pos Gemessene Gelenkpositionen [rad] oder [°]?
    * @param [in] t Abtastperiode [s]
    * @return Fehlercode
    */
    errno_t LoadIdentifyMain(double joint_torque[6], double joint_pos[6], double t);

Lastidentifikationsergebnis abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Lastidentifikationsergebnis abrufen
    * @param [in] gain Verstärkungsfaktor (für Filter?)
    * @param [out] weight Berechnetes Lastgewicht [kg]
    * @param [out] cog Berechneter Lastschwerpunkt [mm]
    * @return Fehlercode
    */
    errno_t LoadIdentifyGetResult(double gain[12], double *weight, DescTran *cog);

Codebeispiel für Roboter-Lastidentifikation
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestIdentify(void)
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
      int retval = 0;
      retval = robot.LoadIdentifyDynFilterInit();
      printf("LoadIdentifyDynFilterInit retval is: %d \n", retval);
      retval = robot.LoadIdentifyDynVarInit();
      printf("LoadIdentifyDynVarInit retval is: %d \n", retval);
      JointPos posJ = {};
      DescPose posDec = {};
      float joint_toq[6] = { 0.0 };
      robot.GetActualJointPosDegree(0, &posJ);
      posJ.jPos[1] = posJ.jPos[1] + 10;
      robot.GetJointTorques(0, joint_toq);
      joint_toq[1] = joint_toq[1] + 2;
      double tmpTorque[6] = { 0.0 };
      for (int i = 0; i < 6; i++)
      {
        tmpTorque[i] = joint_toq[i];
      }
      retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
      printf("LoadIdentifyMain retval is: %d \n", retval);
      double gain[12] = { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
      double weight = 0;
      DescTran load_pos;
      memset(&load_pos, 0, sizeof(DescTran));
      retval = robot.LoadIdentifyGetResult(gain, &weight, &load_pos);
      printf("LoadIdentifyGetResult retval is: %d ; weight is %f cog is %f %f %f \n", retval, weight, load_pos.x, load_pos.y, load_pos.z);
      robot.CloseRPC();
      return 0;
    }

Kraftsensor-unterstütztes Führen (Drag & Teach)
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Kraftsensor-unterstütztes Führen (Drag & Teach)
    * @param [in] status Steuerstatus, 0-aus; 1-an
    * @param [in] asaptiveFlag Adaptive Regelung aktivieren, 0-aus; 1-an
    * @param [in] interfereDragFlag Führen in Interferenzbereichen, 0-aus; 1-an
    * @param [in] ingularityConstraintsFlag Strategie bei Singularität, 0-vermeiden; 1-durchqueren
    * @param [in] forceCollisionFlag Kollisionserkennung während Führung, 0-aus; 1-an
    * @param [in] M Trägheitskoeffizienten (Vektor der Länge 6)
    * @param [in] B Dämpfungskoeffizienten (Vektor der Länge 6)
    * @param [in] K Steifigkeitskoeffizienten (Vektor der Länge 6)
    * @param [in] F Kraftschwellwerte für sechs Achsen (Vektor der Länge 6)
    * @param [in] Fmax Maximale Kraftbegrenzung
    * @param [in] Vmax Maximale Geschwindigkeitsbegrenzung
    * @return Fehlercode
    */
    errno_t EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag, int ingularityConstraintsFlag, int forceCollisionFlag, std::vector<double> M, std::vector<double> B, std::vector<double> K, std::vector<double> F, double Fmax, double Vmax);

Kraftsensor-Führungsstatus abrufen
++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Kraftsensor-Führungsstatus abrufen
     * @param [out] dragState Kraftsensor-unterstützter Führungsstatus, 0-aus; 1-an
     * @param [out] sixDimensionalDragState 6D-Kraftführungsstatus, 0-aus; 1-an (möglicherweise identisch)
     * @return Fehlercode
     */
    errno_t GetForceAndTorqueDragState(int& dragState, int& sixDimensionalDragState);

Automatische Aktivierung des Kraftsensors nach Fehlerlöschung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Automatische Aktivierung des Kraftsensors nach Fehlerlöschung
     * @param [in] status Steuerstatus, 0-aus; 1-an
     * @return Fehlercode
     */
    errno_t SetForceSensorDragAutoFlag(int status);

Codebeispiel für Kraftsensor-unterstütztes Führen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestEndForceDragCtrl(void)
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
         robot.SetForceSensorDragAutoFlag(1);
         vector <double> M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
         vector <double> B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
         vector <double> K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
         vector <double> F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
         robot.EndForceDragControl(1, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.Sleep(5000);
         int dragState = 0;
         int sixDimensionalDragState = 0;
         robot.GetForceAndTorqueDragState(dragState, sixDimensionalDragState);
         printf("the drag state is %d %d \n", dragState, sixDimensionalDragState);
         robot.EndForceDragControl(0, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.CloseRPC();
         return 0;
     }

Gemischte 6D-Kraft- und Gelenkimpedanz-Führung ein-/ausschalten und Parameter setzen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Gemischte 6D-Kraft- und Gelenkimpedanz-Führung ein-/ausschalten und Parameter setzen
     * @param [in] status Steuerstatus, 0-aus; 1-an
     * @param [in] impedanceFlag Impedanz aktivieren, 0-aus; 1-an
     * @param [in] lamdeDain Führungsverstärkung (Vektor der Länge 6)
     * @param [in] KGain Steifigkeitsverstärkung (Vektor der Länge 6)
     * @param [in] BGain Dämpfungsverstärkung (Vektor der Länge 6)
     * @param [in] dragMaxTcpVel Maximale Endeffektor-Lineargeschwindigkeit während Führung [mm/s]
     * @param [in] dragMaxTcpOriVel Maximale Endeffektor-Winkelgeschwindigkeit während Führung [°/s]
     * @return Fehlercode
     */
    errno_t ForceAndJointImpedanceStartStop(int status, int impedanceFlag, std::vector<double> lamdeDain, std::vector<double> KGain, std::vector<double> BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Codebeispiel für gemischte 6D-Kraft- und Gelenkimpedanz-Führung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestForceAndJointImpedance(void)
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
      vector <double> lamdeDain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
      vector <double> KGain = { 0, 0, 0, 0, 0, 0 };
      vector <double> BGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
      rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.Sleep(5000);
      robot.DragTeachSwitch(0);
      rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Impedanzregelung Start/Stopp
++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Impedanzregelung Start/Stopp
    * @param [in] status 0: aus; 1-an
    * @param [in] workSpace 0-Gelenkraum; 1-Kartesischer Raum
    * @param [in] forceThreshold Kraftschwellwert für Auslösung [N] (Vektor der Länge 6)
    * @param [in] m Massenparameter (Vektor der Länge 6)
    * @param [in] b Dämpfungsparameter (Vektor der Länge 6)
    * @param [in] k Steifigkeitsparameter (Vektor der Länge 6)
    * @param [in] maxV Maximale Lineargeschwindigkeit [mm/s]
    * @param [in] maxVA Maximale Linearbeschleunigung [mm/s²]
    * @param [in] maxW Maximale Winkelgeschwindigkeit [°/s]
    * @param [in] maxWA Maximale Winkelbeschleunigung [°/s²]
    * @return Fehlercode
    */
    errno_t ImpedanceControlStartStop(int status, int workSpace, double forceThreshold[6], double m[6], double b[6], double k[6], double maxV, double maxVA, double maxW, double maxWA);

Codebeispiel für Roboter-Impedanzregelung
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    int TestImpedanceControl()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      uint8_t ctrl[20];
      uint8_t state;
      int pressVlaue;
      int error;
      robot.CloseRPC();
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return 0;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j1(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
      JointPos j2(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
      DescPose desc_pos1(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
      DescPose desc_pos2(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 200.0;
      float ovl = 100.0;
      float blendT = -1.0;
      float blendR = -1.0;
      uint8_t flag = 0;
      uint8_t search = 0;
      robot.SetSpeed(20);
      int company = 17;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
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
      double forceThreshold[6] = { 30,30,30,5,5,5 };
      double m[6] = { 0.1,0.1,0.1,0.02,0.02,0.02 };
      double b[6] = { 1,1,1,0.08,0.08,0.08 };
      double k[6] = { 0,0,0,0,0,0 };
      rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
      printf("ImpedanceControlStartStop errcode:%d\n", rtn);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      printf("movel errcode:%d\n", rtn);
      robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);    
      robot.CloseRPC();
      return 0;
    }

Momentenkompensation aktivieren und Koeffizienten setzen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Momentenkompensation aktivieren und Koeffizienten setzen (für Gelenke)
    * @param [in] status Schalter, 0-aus; 1-an
    * @param [in] torqueCoeff Momentenkompensationskoeffizienten J1-J6 [0-1]
    * @return Fehlercode
    */
    errno_t SerCoderCompenParams(int status, double torqueCoeff[6]);