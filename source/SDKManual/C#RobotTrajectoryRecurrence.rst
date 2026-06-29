Roboter-Trajektorienreproduktion
============================================

.. toctree::
    :maxdepth: 5

TPD-Trajektorienaufzeichnungsparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Stellt die Parameter für die TPD-Trajektorienaufzeichnung ein.
    * @param  [in] type  Aufzuzeichnender Datentyp, 1-Gelenkpositionen.
    * @param  [in] name  Name der Trajektoriendatei.
    * @param  [in] period_ms  Datenabtastperiode, feste Werte: 2ms, 4ms oder 8ms.
    * @param  [in] di_choose  DI-Auswahl, Bits 0-7 für Steuerschrank DI0-DI7, Bits 8-9 für Endeffektor DI0-DI1. 0-nicht ausgewählt, 1-ausgewählt.
    * @param  [in] do_choose  DO-Auswahl, Bits 0-7 für Steuerschrank DO0-DO7, Bits 8-9 für Endeffektor DO0-DO1. 0-nicht ausgewählt, 1-ausgewählt.
    * @return  Fehlercode.
    */
    int SetTPDParam(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose);

TPD-Trajektorienaufzeichnung starten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Startet die TPD-Trajektorienaufzeichnung.
    * @param  [in] type  Aufzuzeichnender Datentyp, 1-Gelenkpositionen.
    * @param  [in] name  Name der Trajektoriendatei.
    * @param  [in] period_ms  Datenabtastperiode, feste Werte: 2ms, 4ms oder 8ms.
    * @param  [in] di_choose  DI-Auswahl, Bits 0-7 für Steuerschrank DI0-DI7, Bits 8-9 für Endeffektor DI0-DI1. 0-nicht ausgewählt, 1-ausgewählt.
    * @param  [in] do_choose  DO-Auswahl, Bits 0-7 für Steuerschrank DO0-DO7, Bits 8-9 für Endeffektor DO0-DO1. 0-nicht ausgewählt, 1-ausgewählt.
    * @return  Fehlercode.
    */
    int SetTPDStart(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose);

TPD-Trajektorienaufzeichnung stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Stoppt die TPD-Trajektorienaufzeichnung.
    * @return  Fehlercode.
    */
    int SetWebTPDStop();

TPD-Trajektorienaufzeichnung löschen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Löscht eine TPD-Trajektorienaufzeichnung.
    * @param  [in] name  Name der Trajektoriendatei.
    * @return  Fehlercode.
    */
    int SetTPDDelete(string name);

TPD-Trajektorie vorladen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Lädt eine Trajektorie vor.
    * @param  [in] name  Name der Trajektoriendatei.
    * @return  Fehlercode.
    */
    int LoadTPD(string name);

Startpose einer TPD-Trajektorie abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gibt die Startpose einer Trajektorie zurück.
    * @param [in] name  Name der Trajektoriendatei.
    * @param [out] desc_pose Startpose der Trajektorie.
    * @return Fehlercode.
    */
    int GetTPDStartPose(string name, ref DescPose desc_pose);

TPD-Trajektorie reproduzieren
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Reproduziert eine Trajektorie.
    * @param  [in] name  Name der Trajektoriendatei.
    * @param  [in] blend 0-nicht glätten, 1-glätten.
    * @param  [in] ovl  Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100].
    * @return  Fehlercode.
    */
    int MoveTPD(string name, byte blend, float ovl);

Codebeispiel für Roboter-TPD-Trajektorienaufzeichnung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnTPDMove_Click(object sender, EventArgs e)
    {
        int type = 1;
        string name = "tpd2025";
        int period_ms = 4;
        ushort di_choose = 0;
        ushort do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        Thread.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        float ovl = 100.0f;
        byte blend = 0;

        DescPose start_pose = new DescPose();

        int rtn = robot.LoadTPD(name);
        Console.WriteLine("LoadTPD rtn is: {0}\n", rtn);

        robot.GetTPDStartPose(name, ref start_pose);
        Console.WriteLine("start pose, xyz is: {0} {1} {2}. rpy is: {3} {4} {5} \n",
            start_pose.tran.x, start_pose.tran.y, start_pose.tran.z,
            start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        Thread.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        Console.WriteLine("MoveTPD rtn is: {0}\n", rtn);
        Thread.Sleep(5000);

        robot.SetTPDDelete(name);
    }

Externe Trajektoriendatei vorverarbeiten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Vorverarbeitung einer externen Trajektoriendatei (TrajectoryJ).
    * @param [in] name Name der Trajektoriendatei.
    * @param [in] ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100].
    * @param [in] opt 1-Kontrollpunkte, Standard 1.
    * @return Fehlercode.
    */
    int LoadTrajectoryJ(string name, float ovl, int opt);

Externe Trajektoriendatei reproduzieren
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Reproduziert eine externe Trajektoriendatei (TrajectoryJ).
    * @return Fehlercode.
    */
    int MoveTrajectoryJ();

Startpose einer Trajektoriendatei abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gibt die Startpose einer Trajektoriendatei zurück.
    * @param [in] name Name der Trajektoriendatei.
    * @param [out] desc_pose Startpose der Trajektorie.
    * @return Fehlercode.
    */
    int GetTrajectoryStartPose(string name, ref DescPose desc_pose);

Punktnummer einer Trajektoriendatei abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gibt die Nummer des Trajektorienpunkts zurück.
    * @param [out] pnum Trajektorienpunktnummer.
    * @return Fehlercode.
    */
    int GetTrajectoryPointNum(ref int pnum);

Geschwindigkeit während der Trajektorienausführung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
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

Kraft und Drehmoment während der Trajektorienreproduktion einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt die Kraft und das Drehmoment während der Trajektorienreproduktion ein (TrajectoryJ).
    * @param [in] ft Kräfte und Drehmomente in drei Richtungen, Einheiten N und Nm.
    * @return Fehlercode.
    */
    int SetTrajectoryJForceTorque(ForceTorque ft);

Kraft in x-Richtung während der Trajektorienreproduktion einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt die Kraft in x-Richtung während der Trajektorienreproduktion ein (TrajectoryJ).
    * @param [in] fx Kraft in x-Richtung, Einheit N.
    * @return Fehlercode.
    */
    int SetTrajectoryJForceFx(double fx);

Kraft in y-Richtung während der Trajektorienreproduktion einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt die Kraft in y-Richtung während der Trajektorienreproduktion ein (TrajectoryJ).
    * @param [in] fy Kraft in y-Richtung, Einheit N.
    * @return Fehlercode.
    */
    int SetTrajectoryJForceFy(double fy);

Kraft in z-Richtung während der Trajektorienreproduktion einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt die Kraft in z-Richtung während der Trajektorienreproduktion ein (TrajectoryJ).
    * @param [in] fz Kraft in z-Richtung, Einheit N.
    * @return Fehlercode.
    */
    int SetTrajectoryJForceFz(double fz);

Drehmoment um die x-Achse während der Trajektorienreproduktion einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt das Drehmoment um die x-Achse während der Trajektorienreproduktion ein (TrajectoryJ).
    * @param [in] tx Drehmoment um die x-Achse, Einheit Nm.
    * @return Fehlercode.
    */
    int SetTrajectoryJTorqueTx(double tx);

Drehmoment um die y-Achse während der Trajektorienreproduktion einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt das Drehmoment um die y-Achse während der Trajektorienreproduktion ein (TrajectoryJ).
    * @param [in] ty Drehmoment um die y-Achse, Einheit Nm.
    * @return Fehlercode.
    */
    int SetTrajectoryJTorqueTy(double ty);

Drehmoment um die z-Achse während der Trajektorienreproduktion einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt das Drehmoment um die z-Achse während der Trajektorienreproduktion ein (TrajectoryJ).
    * @param [in] tz Drehmoment um die z-Achse, Einheit Nm.
    * @return Fehlercode.
    */
    int SetTrajectoryJTorqueTz(double tz);

TrajectoryJ-Datei hochladen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Lädt eine TrajectoryJ-Datei hoch.
    * @param [in] filePath Vollständiger Pfad zur hochzuladenden Trajektoriendatei, z.B. C://test/testJ.txt.
    * @return Fehlercode.
    */
    int TrajectoryJUpLoad(string filePath);

TrajectoryJ-Datei löschen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Löscht eine TrajectoryJ-Datei.
    * @param [in] fileName Dateiname, z.B. testJ.txt.
    * @return Fehlercode.
    */
    int TrajectoryJDelete(string fileName);

Codebeispiel für Roboter-TrajectoryJ-Reproduktion
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button33_Click(object sender, EventArgs e)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/spray_traj1.txt");
        Console.WriteLine("Upload TrajectoryJ A {0}\n", rtn);

        string traj_file_name = "/fruser/traj/spray_traj1.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        Console.WriteLine("LoadTrajectoryJ {0}, rtn is: {1}\n", traj_file_name, rtn);

        DescPose traj_start_pose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(traj_file_name, ref traj_start_pose);
        Console.WriteLine("GetTrajectoryStartPose is: {0}\n", rtn);
        Console.WriteLine("desc_pos:{0},{1},{2},{3},{4},{5}\n",
            traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z,
            traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);

        Thread.Sleep(1000);

        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(ref traj_num);
        Console.WriteLine("GetTrajectoryStartPose rtn is: {0}, traj num is: {1}\n", rtn, traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0f);
        Console.WriteLine("SetTrajectoryJSpeed is: {0}\n", rtn);

        ForceTorque traj_force = new ForceTorque();
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        Console.WriteLine("SetTrajectoryJForceTorque rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0f);
        Console.WriteLine("SetTrajectoryJForceFx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0f);
        Console.WriteLine("SetTrajectoryJForceFy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0f);
        Console.WriteLine("SetTrajectoryJForceFz rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTz rtn is: {0}\n", rtn);

        rtn = robot.MoveTrajectoryJ();
        Console.WriteLine("MoveTrajectoryJ rtn is: {0}\n", rtn);
    }

Trajektorienvorverarbeitung (Trajektorienvorausschau)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Trajektorienvorverarbeitung (Trajektorienvorausschau).
    * @param  [in] name  Name der Trajektoriendatei.
    * @param  [in] mode  Abtastmodus, 0-keine Abtastung; 1-Abtastung in gleichen Datenabständen; 2-Abtastung mit Fehlerbegrenzung.
    * @param  [in] errorLim  Fehlergrenze, wirksam bei Verwendung von linearer Approximation.
    * @param  [in] type  Glättungsart, 0-Bézier-Glättung.
    * @param  [in] precision  Glättungsgenauigkeit, wirksam bei Verwendung von Bézier-Glättung.
    * @param  [in] vmax  Eingestellte maximale Geschwindigkeit, mm/s.
    * @param  [in] amax  Eingestellte maximale Beschleunigung, mm/s².
    * @param  [in] jmax  Eingestellte maximale Ruck (Jerk), mm/s³.
    * @return  Fehlercode.
    */
    int LoadTrajectoryLA(string name, int mode, double errorLim, int type, double precision, double vmax, double amax, double jmax);

Trajektorienreproduktion (Trajektorienvorausschau)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Trajektorienreproduktion (Trajektorienvorausschau).
    * @return  Fehlercode.
    */
    int MoveTrajectoryLA();

Codebeispiel für Trajektorienreproduktion (Trajektorienvorausschau)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button87_Click(object sender, EventArgs e)
    {
        // Upload trajectory file
        int rtn = robot.TrajectoryJUpLoad(@"D:\zUP\horse.txt");
        Console.WriteLine($"Upload TrajectoryJ A {rtn}");

        string trajFileName = "horse.txt";
        rtn = robot.LoadTrajectoryLA(trajFileName, 2, 0, 0, 1, 40, 100, 100, 1);
        Console.WriteLine($"LoadTrajectoryLA {trajFileName}, rtn is: {rtn}");

        DescPose trajStartPose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(trajFileName, ref trajStartPose);
        Console.WriteLine($"GetTrajectoryStartPose is: {rtn}");
        Console.WriteLine($"desc_pos: {trajStartPose.tran.x},{trajStartPose.tran.y},{trajStartPose.tran.z},{trajStartPose.rpy.rx},{trajStartPose.rpy.ry},{trajStartPose.rpy.rz}");

        Thread.Sleep(1000);

        robot.SetSpeed(50);
        robot.MoveCart(trajStartPose, 0, 0, 100, 100, 100, -1, -1);

        rtn = robot.MoveTrajectoryLA();
        Console.WriteLine($"MoveTrajectoryLA rtn is: {rtn}");
    }

Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
    * @param [in] name Bahndateiname
    * @param [in] moveType Bewegungstyp; 0-PTP; 1-LIN
    * @param [in] ovl Geschwindigkeitsskalierungsprozentsatz, Bereich [0~100]
    * @return Fehlercode
    */
    public int MoveToTPDStart(string name, int moveType, double ovl)

SDK-Codebeispiel für die Bewegung zum Startpunkt der TPD-Bahnaufzeichnung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void testTPDmove()
    {
        string name = "tpd2025";
        int type = 1;
        int period_ms = 4;
        int rtn = 0;
        UInt16 di_choose = 0;
        UInt16 do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        Thread.Sleep(3000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        Thread.Sleep(3000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        Thread.Sleep(1000);
        float ovl = 100.0f;
        byte blend = 0;
        DescPose start_pose = new DescPose();
        rtn = robot.LoadTPD(name);
        Console.WriteLine($"LoadTPD rtn is:{rtn}\n");

        robot.GetTPDStartPose(name, ref start_pose);
        Console.WriteLine($"start pose, xyz is: %f %f %f. rpy is: {start_pose.tran.x},{start_pose.tran.y}, {start_pose.tran.z}, {start_pose.rpy.rx}, {start_pose.rpy.ry}, {start_pose.rpy.rz}");

        rtn = robot.MoveToTPDStart(name, 0, 100.0);

        rtn = robot.MoveTPD(name, blend, ovl);
        Thread.Sleep(5000*5);

        robot.SetTPDDelete(name);
    }