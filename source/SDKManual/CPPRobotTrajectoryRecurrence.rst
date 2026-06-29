Roboter-Trajektorienwiedergabe
==============================

.. toctree::
    :maxdepth: 5

TPD-Trajektorienaufzeichnungsparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief TPD-Trajektorienaufzeichnungsparameter einstellen
    * @param [in] type Datentyp für die Aufzeichnung, 1 - Gelenkpositionen
    * @param [in] name Name der Trajektoriendatei
    * @param [in] period_ms Datenabtastperiode, feste Werte: 2ms, 4ms oder 8ms
    * @param [in] di_choose DI-Auswahl, Bit0~Bit7 für Steuerkasten DI0~DI7, Bit8~Bit9 für Endeffektor DI0~DI1, 0 - nicht ausgewählt, 1 - ausgewählt
    * @param [in] do_choose DO-Auswahl, Bit0~Bit7 für Steuerkasten DO0~DO7, Bit8~Bit9 für Endeffektor DO0~DO1, 0 - nicht ausgewählt, 1 - ausgewählt
    * @return Fehlercode
    */
    errno_t SetTPDParam(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose);

TPD-Trajektorienaufzeichnung starten
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief TPD-Trajektorienaufzeichnung starten
    * @param [in] type Datentyp für die Aufzeichnung, 1 - Gelenkpositionen
    * @param [in] name Name der Trajektoriendatei
    * @param [in] period_ms Datenabtastperiode, feste Werte: 2ms, 4ms oder 8ms
    * @param [in] di_choose DI-Auswahl, Bit0~Bit7 für Steuerkasten DI0~DI7, Bit8~Bit9 für Endeffektor DI0~DI1, 0 - nicht ausgewählt, 1 - ausgewählt
    * @param [in] do_choose DO-Auswahl, Bit0~Bit7 für Steuerkasten DO0~DO7, Bit8~Bit9 für Endeffektor DO0~DO1, 0 - nicht ausgewählt, 1 - ausgewählt
    * @return Fehlercode
    */
    errno_t SetTPDStart(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose);

TPD-Trajektorienaufzeichnung stoppen
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief TPD-Trajektorienaufzeichnung stoppen
    * @return Fehlercode
    */
    errno_t SetWebTPDStop();

TPD-Trajektoriendatei löschen
++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief TPD-Trajektoriendatei löschen
    * @param [in] name Name der Trajektoriendatei
    * @return Fehlercode
    */
    errno_t SetTPDDelete(char name[30]);

TPD-Trajektorie vorladen
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief TPD-Trajektorie vorladen
    * @param [in] name Name der Trajektoriendatei
    * @return Fehlercode
    */
    errno_t LoadTPD(char name[30]);

TPD-Trajektorie wiedergeben
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief TPD-Trajektorie wiedergeben
    * @param [in] name Name der Trajektoriendatei
    * @param [in] blend 0 - keine Glättung, 1 - Glättung
    * @param [in] ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]
    * @return Fehlercode
    */
    errno_t MoveTPD(char name[30], uint8_t blend, float ovl);

Startpose einer TPD-Trajektorie abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Startpose einer TPD-Trajektorie abrufen
     * @param [in] name TPD-Dateiname (ohne Dateiendung)
     * @param [out] desc_pose Startpose der Trajektorie
     * @return Fehlercode
     */
    errno_t GetTPDStartPose(char name[30], DescPose *desc_pose);

Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
    * @param [in] name Bahndateiname
    * @param [in] moveType Bewegungstyp; 0-PTP; 1-LIN
    * @param [in] ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]
    * @return Fehlercode
    */
    errno_t MoveToTPDStart(char name[30], uint8_t moveType, float ovl);
    
Codebeispiel für Roboter-TPD-Bahnaufzeichnung
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTPD(void)
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
    int type = 1;
    char name[30] = "tpd2025";
    int period_ms = 4;
    uint16_t di_choose = 0;
    uint16_t do_choose = 0;
    robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);
    robot.Mode(1);
    robot.Sleep(1000);
    robot.DragTeachSwitch(1);
    robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
    robot.Sleep(3000);
    robot.SetWebTPDStop();
    robot.DragTeachSwitch(0);
    robot.Sleep(1000);
    float ovl = 100.0;
    uint8_t blend = 0;
    DescPose start_pose = {};
    rtn = robot.LoadTPD(name);
    printf("LoadTPD rtn is: %d\n", rtn);
    robot.GetTPDStartPose(name, &start_pose);
    printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
    rtn = robot.MoveToTPDStart(name, 0, 100);
    printf("MoveToTPDStart rtn is: %d\n", rtn);
    rtn = robot.MoveTPD(name, blend, ovl);
    printf("MoveTPD rtn is: %d\n", rtn);
    std::this_thread::sleep_for(std::chrono::milliseconds(5000));
    robot.SetTPDDelete(name);
    robot.CloseRPC();
    return 0;
    }

Codebeispiel für Roboter-TPD-Trajektorienaufzeichnung
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestTPD(void)
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
      int type = 1;
      char name[30] = "tpd2025";
      int period_ms = 4;
      uint16_t di_choose = 0;
      uint16_t do_choose = 0;
      robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);
      robot.Mode(1);
      robot.Sleep(1000);
      robot.DragTeachSwitch(1);
      robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
      robot.Sleep(10000);
      robot.SetWebTPDStop();
      robot.DragTeachSwitch(0);
      float ovl = 100.0;
      uint8_t blend = 0;
      DescPose start_pose = {};
      rtn = robot.LoadTPD(name);
      printf("LoadTPD rtn is: %d\n", rtn);
      robot.GetTPDStartPose(name, &start_pose);
      printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
      robot.MoveCart(&start_pose, 0, 0, 100, 100, ovl, -1, -1);
      robot.Sleep(1000);
      rtn = robot.MoveTPD(name, blend, ovl);
      printf("MoveTPD rtn is: %d\n", rtn);
      std::this_thread::sleep_for(std::chrono::milliseconds(5000));
      robot.SetTPDDelete(name);
      robot.CloseRPC();
      return 0;
    }

Trajektorie vorverarbeiten
+++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Trajektorie vorverarbeiten (für MoveTrajectoryJ)
     * @param [in] name Name der Trajektoriendatei
     * @param [in] ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]
     * @param [in] opt 1 - Kontrollpunkt, Standard = 1
     * @return Fehlercode
     */
    errno_t LoadTrajectoryJ(char name[30], float ovl, int opt);

Trajektorie wiedergeben (für MoveTrajectoryJ)
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Trajektorie wiedergeben (für MoveTrajectoryJ)
     * @return Fehlercode
     */
    errno_t MoveTrajectoryJ();

Startpose einer Trajektorie abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Startpose einer Trajektorie abrufen
     * @param [in] name Name der Trajektoriendatei
     * @param [out] desc_pose Startpose der Trajektorie
     * @return Fehlercode
     */
    errno_t GetTrajectoryStartPose(char name[30], DescPose *desc_pose);

Nummer des Trajektorienpunkts abrufen
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Nummer des aktuellen Trajektorienpunkts abrufen
     * @param [out] pnum Punktnummer
     * @return Fehlercode
     */
    errno_t GetTrajectoryPointNum(int *pnum);

Geschwindigkeit während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Geschwindigkeit während der Trajektorienausführung einstellen
    * @param [in] ovl Geschwindigkeitsprozentsatz [0-100.0]
    * @param [in] mode Modus; 0-Geschwindigkeitsreduzierungsmodus; 1-direkte Umschaltung
    * @return Fehlercode
    */
    errno_t SetTrajectoryJSpeed(float ovl, int mode = 0);

Codebeispiel zum Einstellen der Robotergeschwindigkeit während der Trajektorienausführung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSetTrajectoryJSpeed() 
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        
        rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        printf("Upload TrajectoryJ A %d\n", rtn);
        char traj_file_name[90] = "horse.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
        DescPose traj_start_pose;
        memset(&traj_start_pose, 0, sizeof(DescPose));
        rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
        printf("GetTrajectoryStartPose is: %d\n", rtn);
        printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
        std::this_thread::sleep_for(std::chrono::seconds(1));
        robot.SetSpeed(50);
        robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(&traj_num);
        printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
        rtn = robot.MoveTrajectoryJ();
        printf("MoveTrajectoryJ rtn is: %d\n", rtn);
        robot.Sleep(1000);
        robot.GetRobotRealTimeState(&pkg);
        int trajspeedMode = 1;
        while (pkg.motion_done == 0)
        {
            robot.GetRobotRealTimeState(&pkg);
            rtn = robot.SetTrajectoryJSpeed(10.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
            rtn = robot.SetTrajectoryJSpeed(80.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }

Kraft und Drehmoment während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Kraft und Drehmoment während der Trajektorienausführung einstellen
     * @param [in] ft Kräfte und Momente in drei Richtungen [fx, fy, fz, tx, ty, tz] (N und Nm)
     * @return Fehlercode
     */
    errno_t SetTrajectoryJForceTorque(ForceTorque *ft);

Kraft in X-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Kraft in X-Richtung während der Trajektorienausführung einstellen
     * @param [in] fx Kraft in X-Richtung (N)
     * @return Fehlercode
     */
    errno_t SetTrajectoryJForceFx(double fx);

Kraft in Y-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Kraft in Y-Richtung während der Trajektorienausführung einstellen
     * @param [in] fy Kraft in Y-Richtung (N)
     * @return Fehlercode
     */
    errno_t SetTrajectoryJForceFy(double fy);

Kraft in Z-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Kraft in Z-Richtung während der Trajektorienausführung einstellen
     * @param [in] fz Kraft in Z-Richtung (N)
     * @return Fehlercode
     */
    errno_t SetTrajectoryJForceFz(double fz);

Drehmoment um die X-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Drehmoment um die X-Achse während der Trajektorienausführung einstellen
     * @param [in] tx Drehmoment um die X-Achse (Nm)
     * @return Fehlercode
     */
    errno_t SetTrajectoryJTorqueTx(double tx);

Drehmoment um die Y-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Drehmoment um die Y-Achse während der Trajektorienausführung einstellen
     * @param [in] ty Drehmoment um die Y-Achse (Nm)
     * @return Fehlercode
     */
    errno_t SetTrajectoryJTorqueTy(double ty);

Drehmoment um die Z-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Drehmoment um die Z-Achse während der Trajektorienausführung einstellen
     * @param [in] tz Drehmoment um die Z-Achse (Nm)
     * @return Fehlercode
     */
    errno_t SetTrajectoryJTorqueTz(double tz);

Trajektorien-J-Datei hochladen
+++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
     * @brief Trajektorien-J-Datei hochladen
     * @param [in] filePath Vollständiger Pfad zur hochzuladenden Trajektoriendatei, z.B. "C://test/testJ.txt"
     * @return Fehlercode
     */
    errno_t TrajectoryJUpLoad(const std::string& filePath);

Trajektorien-J-Datei löschen
+++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
     * @brief Trajektorien-J-Datei löschen
     * @param [in] fileName Name der Datei, z.B. "testJ.txt"
     * @return Fehlercode
     */
    errno_t TrajectoryJDelete(const std::string& fileName);

Codebeispiel für Roboter-Trajektorien-J-Wiedergabe
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestTraj(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj1.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj1.txt";
      rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
      printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      int traj_num = 0;
      rtn = robot.GetTrajectoryPointNum(&traj_num);
      printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
      rtn = robot.SetTrajectoryJSpeed(50.0);
      printf("SetTrajectoryJSpeed is: %d\n", rtn);
      ForceTorque traj_force;
      memset(&traj_force, 0, sizeof(ForceTorque));
      traj_force.fx = 10;
      rtn = robot.SetTrajectoryJForceTorque(&traj_force);
      printf("SetTrajectoryJForceTorque rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFx(10.0);
      printf("SetTrajectoryJForceFx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFy(0.0);
      printf("SetTrajectoryJForceFy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFz(0.0);
      printf("SetTrajectoryJForceFz rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTx(10.0);
      printf("SetTrajectoryJTorqueTx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTy(10.0);
      printf("SetTrajectoryJTorqueTy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTz(10.0);
      printf("SetTrajectoryJTorqueTz rtn is: %d\n", rtn);
      rtn = robot.MoveTrajectoryJ();
      printf("MoveTrajectoryJ rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Trajektorie vorverarbeiten (Vorausschauende Planung)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Trajektorie vorverarbeiten (Vorausschauende Planung für TrajectoryLA)
     * @param [in] name Name der Trajektoriendatei
     * @param [in] mode Abtastmodus, 0 - keine Abtastung, 1 - Abtastung mit konstantem Datenintervall, 2 - Abtastung mit Fehlergrenze
     * @param [in] errorLim Fehlergrenze (wirksam bei Verwendung linearer Approximation)
     * @param [in] type Glättungsmethode, 0 - Bezier-Glättung
     * @param [in] precision Glättungsgenauigkeit (wirksam bei Verwendung von Bezier-Glättung)
     * @param [in] vamax Eingestellte maximale Geschwindigkeit (mm/s)
     * @param [in] amax Eingestellte maximale Beschleunigung (mm/s²)
     * @param [in] jmax Eingestellter maximaler Ruck (mm/s³)
     * @param [in] flag Schalter für konstante Vorausschau-Geschwindigkeit, 0 - deaktiviert, 1 - aktiviert
     * @return Fehlercode
     */
    errno_t LoadTrajectoryLA(char name[30], int mode, double errorLim, int type, double precision, double vamax, double amax, double jmax, int flag = 0);

Trajektorie wiedergeben (Vorausschauende Planung)
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Trajektorie wiedergeben (Vorausschauende Planung für TrajectoryLA)
    * @return Fehlercode
    */
    errno_t MoveTrajectoryLA();

Codebeispiel für Trajektorienwiedergabe (Vorausschauende Planung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLoadTrajLA(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj.txt";
      rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);
      printf("LoadTrajectoryLA %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      rtn = robot.MoveTrajectoryLA();
      printf("MoveTrajectoryLA rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }