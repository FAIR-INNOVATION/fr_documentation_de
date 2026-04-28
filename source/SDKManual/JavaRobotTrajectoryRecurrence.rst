Roboter-Trajektorienwiedergabe
==============================

.. toctree::
    :maxdepth: 5

TPD-Trajektorienaufzeichnungsparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
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
    int SetTPDParam(int type, String name, int period_ms, int di_choose, int do_choose);

TPD-Trajektorienaufzeichnung starten
+++++++++++++++++++++++++++++++++++++
.. code-block:: Java
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
    int SetTPDStart(int type, String name, int period_ms, int di_choose, int do_choose);

TPD-Trajektorienaufzeichnung stoppen
+++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TPD-Trajektorienaufzeichnung stoppen
    * @return Fehlercode
    */
    int SetWebTPDStop();

TPD-Trajektoriendatei löschen
++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TPD-Trajektoriendatei löschen
    * @param [in] name Name der Trajektoriendatei
    * @return Fehlercode
    */
    int SetTPDDelete(String name);

TPD-Trajektorie vorladen
++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TPD-Trajektorie vorladen
    * @param [in] name Name der Trajektoriendatei
    * @return Fehlercode
    */
    int LoadTPD(String name);

TPD-Trajektorie wiedergeben
++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief TPD-Trajektorie wiedergeben
    * @param [in] name Name der Trajektoriendatei
    * @param [in] blend 0 - keine Glättung, 1 - Glättung
    * @param [in] ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]
    * @return Fehlercode
    */
    int MoveTPD(String name, int blend, double ovl);

Startpose einer TPD-Trajektorie abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Startpose einer TPD-Trajektorie abrufen
    * @param [in] name TPD-Dateiname (ohne Dateiendung)
    * @param [out] desc_pose Startpose der Trajektorie
    * @return Fehlercode
    */
    int GetTPDStartPose(String name, DescPose desc_pose);

Codebeispiel für Roboter-TPD-Trajektorienaufzeichnung
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTPD(Robot robot)
    {
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        double ovl = 100.0;
        int blend = 0;

        DescPose start_pose =new DescPose() {};

        int rtn = robot.LoadTPD(name);
        System.out.println("LoadTPD rtn is:"+ rtn);

        robot.GetTPDStartPose(name, start_pose);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        robot.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.println("MoveTPD rtn is: "+ rtn);
        robot.Sleep(5000);

        robot.SetTPDDelete(name);
        return 0;
    }

Trajektorie vorverarbeiten
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Externe Trajektoriendatei vorverarbeiten
    * @param [in] name Name der Trajektoriendatei
    * @param [in] ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]
    * @param [in] opt 1 - Kontrollpunkt, Standard = 1
    * @return Fehlercode
    */
    int LoadTrajectoryJ(String name, double ovl, int opt);

Trajektorie wiedergeben (für MoveTrajectoryJ)
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Externe Trajektoriendatei wiedergeben (für MoveTrajectoryJ)
    * @return Fehlercode
    */
    int MoveTrajectoryJ();

Startpose einer Trajektorie abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Startpose einer Trajektorie abrufen
    * @param [in] name Name der Trajektoriendatei
    * @param [out] desc_pose Startpose der Trajektorie
    * @return Fehlercode
    */
    int GetTrajectoryStartPose(String name, DescPose desc_pose);

Nummer des aktuellen Trajektorienpunkts abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Nummer des aktuellen Trajektorienpunkts abrufen
    * @param [out] pnum Punktnummer (als Array der Länge 1 übergeben)
    * @return Fehlercode
    */
    public int GetTrajectoryPointNum(int[] pnum);

Geschwindigkeit während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /*
    * @brief Geschwindigkeit während der Trajektorienausführung einstellen
    * @param ovl Geschwindigkeitsprozentsatz
    * @param mode Modus; 0-Verzögerungsmodus; 1-Direkte Umschaltung
    * @return Fehlercode
    */
    public int SetTrajectoryJSpeed(double ovl, int mode)

Kraft und Drehmoment während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kraft und Drehmoment während der Trajektorienausführung einstellen
    * @param [in] ft Objekt der Klasse ForceTorque mit Kräften und Momenten in drei Richtungen (N und Nm)
    * @return Fehlercode
    */
    public int SetTrajectoryJForceTorque(ForceTorque ft);

Kraft in X-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kraft in X-Richtung während der Trajektorienausführung einstellen
    * @param [in] fx Kraft in X-Richtung (N)
    * @return Fehlercode
    */
    int SetTrajectoryJForceFx(double fx);

Kraft in Y-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kraft in Y-Richtung während der Trajektorienausführung einstellen
    * @param [in] fy Kraft in Y-Richtung (N)
    * @return Fehlercode
    */
    int SetTrajectoryJForceFy(double fy);

Kraft in Z-Richtung während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kraft in Z-Richtung während der Trajektorienausführung einstellen
    * @param [in] fz Kraft in Z-Richtung (N)
    * @return Fehlercode
    */
    int SetTrajectoryJForceFz(double fz);

Drehmoment um die X-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Drehmoment um die X-Achse während der Trajektorienausführung einstellen
    * @param [in] tx Drehmoment um die X-Achse (Nm)
    * @return Fehlercode
    */
    int SetTrajectoryJTorqueTx(double tx);

Drehmoment um die Y-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Drehmoment um die Y-Achse während der Trajektorienausführung einstellen
    * @param [in] ty Drehmoment um die Y-Achse (Nm)
    * @return Fehlercode
    */
    int SetTrajectoryJTorqueTy(double ty);

Drehmoment um die Z-Achse während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Drehmoment um die Z-Achse während der Trajektorienausführung einstellen
    * @param [in] tz Drehmoment um die Z-Achse (Nm)
    * @return Fehlercode
    */
    int SetTrajectoryJTorqueTz(double tz);

Trajektorien-J-Datei hochladen
+++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Trajektorien-J-Datei hochladen
    * @param [in] filePath Vollständiger Pfad zur hochzuladenden Trajektoriendatei, z.B. "C://test/testJ.txt"
    * @return Fehlercode
    */
    int TrajectoryJUpLoad(String filePath);

Trajektorien-J-Datei löschen
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Trajektorien-J-Datei löschen
    * @param [in] fileName Name der Datei, z.B. "testJ.txt"
    * @return Fehlercode
    */
    int TrajectoryJDelete(String fileName);

Codebeispiel für Roboter-Trajektorien-J-Wiedergabe
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTraj(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");
        System.out.println("Upload TrajectoryJ A :"+ rtn);

        String traj_file_name = "/fruser/traj/traj.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        System.out.println("LoadTrajectoryJ:"+traj_file_name+", rtn is:"+ rtn);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);


        ExaxisPos epos=new ExaxisPos(0,0,0,0);
        DescPose po=new DescPose(0,0,0,0,0,0);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0);
        System.out.println("SetTrajectoryJSpeed is:"+ rtn);

        ForceTorque traj_force=new ForceTorque(0,0,0,0,0,0);
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        System.out.println("SetTrajectoryJForceTorque rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0);
        System.out.println("SetTrajectoryJForceFx rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0);
        System.out.println("SetTrajectoryJForceFy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0);
        System.out.println("SetTrajectoryJForceFz rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0);
        System.out.println("SetTrajectoryJTorqueTx rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0);
        System.out.println("SetTrajectoryJTorqueTy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0);
        System.out.println("SetTrajectoryJTorqueTz rtn is:"+ rtn);

        rtn = robot.MoveTrajectoryJ();
        System.out.println("MoveTrajectoryJ rtn is: "+ rtn);

        return 0;
    }


Codebeispiel zum Einstellen der Geschwindigkeit während der Roboterbahnbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public int TestSetTrajectoryJSpeed(Robot robot) {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int rtn;

        robot.SetReconnectParam(true, 30000, 500);
        rtn = robot.TrajectoryJUpLoad("D://zUP/trajHelix_aima_1.txt");
        System.out.printf("Upload TrajectoryJ A %d%n", rtn);
        String trajFileName = "/fruser/traj/trajHelix_aima_1.txt";
        rtn = robot.LoadTrajectoryJ(trajFileName, 100, 1);
        System.out.printf("LoadTrajectoryJ %s, rtn is: %d%n", trajFileName, rtn);
        DescPose trajStartPose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(trajFileName, trajStartPose);
        System.out.printf("GetTrajectoryStartPose is: %d%n", rtn);
        System.out.printf("desc_pos:%f,%f,%f,%f,%f,%f%n", trajStartPose.tran.x, trajStartPose.tran.y, trajStartPose.tran.z, trajStartPose.rpy.rx, trajStartPose.rpy.ry, trajStartPose.rpy.rz);
        robot.Sleep(1000);
        robot.SetSpeed(50);
        robot.MoveCart(trajStartPose, 0, 0, 100, 100, 100, -1, -1);
        rtn = robot.GetTrajectoryPointNum(0);
        pkg = robot.GetRobotRealTimeState();
        int trajNum = pkg.trajectory_pnum;
        System.out.printf("GetTrajectoryPointNum rtn is: %d, traj num is: %d%n", rtn, trajNum);

        rtn = robot.MoveTrajectoryJ();
        System.out.printf("MoveTrajectoryJ rtn is: %d%n", rtn);

        robot.Sleep(1000);

        pkg = robot.GetRobotRealTimeState();
        int trajspeedMode = 1;
        while (pkg.motion_done == 0)
        {
            pkg = robot.GetRobotRealTimeState();

            rtn = robot.SetTrajectoryJSpeed(10.0, trajspeedMode);
            System.out.printf("SetTrajectoryJSpeed is: %d%n", rtn);

            robot.Sleep(1000);

            rtn = robot.SetTrajectoryJSpeed(80.0, trajspeedMode);
            System.out.printf("SetTrajectoryJSpeed is: %d%n", rtn);

            robot.Sleep(1000);
        }

        return 0;
    }

Trajektorie vorverarbeiten (Vorausschauende Planung für TrajectoryLA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief Trajektorie vorverarbeiten (Vorausschauende Planung für TrajectoryLA)
    * @param [in] name Name der Trajektoriendatei
    * @param [in] mode Abtastmodus, 0 - keine Abtastung, 1 - Abtastung mit konstantem Datenintervall, 2 - Abtastung mit Fehlergrenze
    * @param [in] errorLim Fehlergrenze (wirksam bei Verwendung linearer Approximation)
    * @param [in] type Glättungsmethode, 0 - Bezier-Glättung
    * @param [in] precision Glättungsgenauigkeit (wirksam bei Verwendung von Bezier-Glättung)
    * @param [in] vamx Eingestellte maximale Geschwindigkeit (mm/s)
    * @param [in] amax Eingestellte maximale Beschleunigung (mm/s²)
    * @param [in] jmax Eingestellter maximaler Ruck (mm/s³)
    * @return Fehlercode
    */
    int LoadTrajectoryLA(String name, int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax);

Trajektorie wiedergeben (Vorausschauende Planung für TrajectoryLA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief Trajektorie wiedergeben (Vorausschauende Planung für TrajectoryLA)
    * @return Fehlercode
    */
    int MoveTrajectoryLA();

Codebeispiel für Trajektorienwiedergabe (Vorausschauende Planung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLoadTrajLA(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");

        String traj_file_name = "/fruser/traj/traj.txt";
        rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        rtn = robot.MoveTrajectoryLA();

        robot.CloseRPC();
        return 0;
    }

Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
    * @param name Bahndateiname
    * @param moveType Bewegungstyp; 0-PTP; 1-LIN
    * @param ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]
    * @return Fehlercode
    */
    public int MoveToTPDStart(string name, int moveType, double ovl)

SDK-Codebeispiel für die Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testTPDmove (Robot robot)
    {
        int rtn = 0;
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(3000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        robot.Sleep(1000);
        double ovl = 100.0;
        int blend = 0;
        DescPose start_pose = new DescPose();
        rtn = robot.LoadTPD(name);
        System.out.printf("LoadTPD rtn is: %d\n", rtn);

        robot.GetTPDStartPose(name, start_pose);
        System.out.printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        //robot.MoveCart(&start_pose, 0, 0, 100, 100, ovl, -1, -1);
        //robot.Sleep(1000);

        rtn = robot.MoveToTPDStart(name, 0, 100);
        System.out.printf("MoveToTPDStart rtn is: %d\n", rtn);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.printf("MoveTPD rtn is: %d\n", rtn);

        robot.Sleep(5000);

        robot.SetTPDDelete(name);

        return ;
    }