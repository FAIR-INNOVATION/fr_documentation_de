Allgemeine Roboter-Einstellungen
================================

.. toctree::
    :maxdepth: 5

Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~6]
    * @return Fehlercode
    */
    int SetToolPoint(int point_num);

Werkzeugkoordinatensystem berechnen - Sechs-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeugkoordinatensystem berechnen
    * @param [out] tcp_pose Werkzeugkoordinatensystem
    * @return Fehlercode
    */
    int ComputeTool(DescPose tcp_pose);

Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~4]
    * @return Fehlercode
    */
    int SetTcp4RefPoint(int point_num);

Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeugkoordinatensystem berechnen
    * @param [out] tcp_pose Werkzeugkoordinatensystem
    * @return Fehlercode
    */
    int ComputeTcp4(DescPose tcp_pose);

Werkzeugkoordinatensystem basierend auf Punktdaten berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeugkoordinatensystem basierend auf Punktdaten berechnen
    * @param [in] method Berechnungsmethode; 0 - Vier-Punkt-Methode, 1 - Sechs-Punkt-Methode
    * @param [in] pos Array von Gelenkpositionen, Länge 4 bei Vier-Punkt-Methode, Länge 6 bei Sechs-Punkt-Methode
    * @param [out] tool_pose Berechnetes Werkzeugkoordinatensystem
    * @return Fehlercode
    */
    int ComputeToolCoordWithPoints(int method, JointPos[] pos, DescPose tool_pose);

Werkzeugkoordinatensystem einstellen
+++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeugkoordinatensystem einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [0~14]
    * @param [in] coord Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
    * @param [in] type 0 - Werkzeugkoordinatensystem, 1 - Sensorkoordinatensystem
    * @param [in] install Einbauort, 0 - Roboterflansch, 1 - extern
    * @param [in] toolID Werkzeug-ID
    * @param [in] loadNum Lastnummer
    * @return Fehlercode
    */
    int SetToolCoord(int id, DescPose coord, int type, int install, int toolID, int loadNum);

Werkzeugkoordinatensystem in Liste einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkzeugkoordinatensystem in Liste einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [0~14]
    * @param [in] coord Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
    * @param [in] type 0 - Werkzeugkoordinatensystem, 1 - Sensorkoordinatensystem
    * @param [in] install Einbauort, 0 - Roboterflansch, 1 - extern
    * @param [in] loadNum Lastnummer
    * @return Fehlercode
    */
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);

Aktuelles Werkzeugkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelles Werkzeugkoordinatensystem abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] desc_pos Pose des Werkzeugkoordinatensystems
    * @return Fehlercode
    */
    int GetTCPOffset(int flag, DescPose desc_pos);

Codebeispiel für Roboter-Werkzeugkoordinatensystem-Operationen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTCPCompute(Robot robot)
    {
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint=new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);

        DescPose p2Desc=new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint=new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);

        DescPose p3Desc=new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint=new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);

        DescPose p4Desc=new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint=new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);

        DescPose p5Desc=new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint=new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);

        DescPose p6Desc=new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint=new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
        DescPose coordRtn =new DescPose() {};
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(4);
        robot.MoveJ(p5Joint, p5Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(5);
        robot.MoveJ(p6Joint, p6Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(coordRtn);
        robot.SetToolList(3, coordRtn, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(coordRtn);

        robot.SetToolCoord(4, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose(){};
        rtn = robot.GetTCPOffset(0, getCoord);
        return 0;
    }

Externen Werkzeug-Referenzpunkt einstellen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Externen Werkzeug-Referenzpunkt einstellen - Drei-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~3]
    * @return Fehlercode
    */
    int SetExTCPPoint(int point_num);

Externes Werkzeugkoordinatensystem berechnen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Externes Werkzeugkoordinatensystem berechnen - Drei-Punkt-Methode
    * @param [out] tcp_pose Externes Werkzeugkoordinatensystem
    * @return Fehlercode
    */
    int ComputeExTCF(DescPose tcp_pose);

Externes Werkzeugkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Externes Werkzeugkoordinatensystem einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [0~14]
    * @param [in] etcp Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
    * @param [in] etool (vorläufig unbestimmt)
    * @return Fehlercode
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool);

Externes Werkzeugkoordinatensystem in Liste einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Externes Werkzeugkoordinatensystem in Liste einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [0~14]
    * @param [in] etcp Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
    * @param [in] etool (vorläufig unbestimmt)
    * @return Fehlercode
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool);

Codebeispiel für Roboter-externes Werkzeugkoordinatensystem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestExtCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = { p1Desc , p2Desc , p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(coordRtn);

        robot.SetExToolCoord(1, coordRtn, offdese);
        robot.SetExToolList(1, coordRtn, offdese);
        return 0;
    }

Werkstück-Referenzpunkt einstellen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkstück-Referenzpunkt einstellen - Drei-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~3]
    * @return Fehlercode
    */
    int SetWObjCoordPoint(int point_num);

Werkstückkoordinatensystem berechnen
+++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkstückkoordinatensystem berechnen
    * @param [in] method Berechnungsmethode: 0 - Ursprung-x-Achse-z-Achse, 1 - Ursprung-x-Achse-xy-Ebene
    * @param [in] refFrame Referenzkoordinatensystem
    * @param [out] wobj_pose Werkstückkoordinatensystem
    * @return Fehlercode
    */
    int ComputeWObjCoord(int method, int refFrame, DescPose wobj_pose);

Werkstückkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkstückkoordinatensystem einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [1~15]
    * @param [in] coord Pose des Werkstückkoordinatensystems relativ zum Flanschmittelpunkt
    * @param [in] refFrame Referenzkoordinatensystem
    * @return Fehlercode
    */
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Werkstückkoordinatensystem in Liste einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkstückkoordinatensystem in Liste einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [1~15]
    * @param [in] coord Pose des Werkstückkoordinatensystems relativ zum Flanschmittelpunkt
    * @param [in] refFrame Referenzkoordinatensystem
    * @return Fehlercode
    */
    int SetWObjList(int id, DescPose coord, int refFrame);

Werkstückkoordinatensystem basierend auf Punktdaten berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Werkstückkoordinatensystem basierend auf Punktdaten berechnen
    * @param [in] method Berechnungsmethode: 0 - Ursprung-x-Achse-z-Achse, 1 - Ursprung-x-Achse-xy-Ebene
    * @param [in] pos Array von drei TCP-Positionen (kartesisch)
    * @param [in] refFrame Referenzkoordinatensystem
    * @param [out] tcp_pose Berechnetes Werkstückkoordinatensystem
    * @return Fehlercode
    */
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame, DescPose tcp_pose);

Aktuelles Werkstückkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelles Werkstückkoordinatensystem abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] desc_pos Pose des Werkstückkoordinatensystems
    * @return Fehlercode
    */
    int GetWObjOffset(int flag, DescPose desc_pos);

Codebeispiel für Roboter-Werkstückkoordinatensystem-Operationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWobjCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP =new DescPose[]{p1Desc , p2Desc , p3Desc };
        DescPose coordRtn =new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, coordRtn);

        robot.SetWObjCoord(1, coordRtn, 0);
        robot.SetWObjList(1, coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, getWobjDesc);
        return 0;
    }

Globale Geschwindigkeit einstellen
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Globale Geschwindigkeit einstellen
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @return Fehlercode
    */
    int SetSpeed(int vel);

Roboter-Beschleunigung einstellen
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-Beschleunigung einstellen
    * @param [in] acc Roboter-Beschleunigungsprozentsatz
    * @return Fehlercode
    */
    int SetOaccScale(double acc);

Standard-Roboter-Geschwindigkeit abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Standard-Roboter-Geschwindigkeit abrufen
    * @return List[0]: int Fehlercode; List[1]: double vel Geschwindigkeit (mm/s)
    */
    List<Number> GetDefaultTransVel();

Endeffektor-Lastgewicht einstellen
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Endeffektor-Lastgewicht einstellen
    * @param [in] loadNum Lastnummer
    * @param [in] weight Lastgewicht (kg)
    * @return Fehlercode
    */
    int SetLoadWeight(int loadNum, double weight);

Endeffektor-Lastschwerpunkt einstellen
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Endeffektor-Lastschwerpunkt einstellen
    * @param [in] coord Schwerpunktkoordinaten (mm)
    * @return Fehlercode
    */
    int SetLoadCoord(DescTran coord);

Endeffektor-Lastschwerpunkt einstellen (mit Lastnummer)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Endeffektor-Lastschwerpunkt einstellen (mit Lastnummer)
     * @param [in] loadNum Lastnummer
     * @param [in] coord Schwerpunktkoordinaten (mm)
     * @return Fehlercode
     */
    public int SetLoadCoord(int loadNum, DescTran coord)

Aktuelles Lastgewicht abrufen
++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelles Lastgewicht abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @return List[0]: int Fehlercode; List[1]: double weight Lastgewicht (kg)
    */
    List<Number> GetTargetPayload(int flag);

Aktuellen Lastschwerpunkt abrufen
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuellen Lastschwerpunkt abrufen
    * @param [in] flag 0 - blockierend, 1 - nicht blockierend
    * @param [out] cog Lastschwerpunkt (mm)
    * @return Fehlercode
    */
    int GetTargetPayloadCog(int flag, DescTran cog);

Roboter-Einbauart einstellen
++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-Einbauart einstellen
    * @param [in] install Einbauart, 0 - Boden, 1 - Wand, 2 - Decke
    * @return Fehlercode
    */
    int SetRobotInstallPos(int install);

Roboter-Einbauwinkel einstellen (freie Montage)
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-Einbauwinkel einstellen (freie Montage)
    * @param [in] yangle Neigungswinkel
    * @param [in] zangle Rotationswinkel
    * @return Fehlercode
    */
    int SetRobotInstallAngle(double yangle, double zangle);

Roboter-Einbauwinkel abrufen
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboter-Einbauwinkel abrufen
    * @return List[0]: Fehlercode; List[1]: double yangle Neigungswinkel; List[2]: double zangle Rotationswinkel
    */
    public List<Number> GetRobotInstallAngle()

Systemvariablenwert einstellen
++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Systemvariablenwert einstellen
    * @param [in] id Variablennummer, Bereich [1~20]
    * @param [in] value Variablenwert
    * @return Fehlercode
    */
    int SetSysVarValue(int id, double value);

Systemvariablenwert abrufen
++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Systemvariablenwert abrufen
    * @param [in] id Systemvariablennummer, Bereich [1~20]
    * @return List[0]: Fehlercode; List[1]: double value Systemvariablenwert
    */
    List<Number> GetSysVarValue(int id);

Codebeispiel für allgemeine Roboter-Einstellungen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLoadInstall(Robot robot)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            robot.Sleep(30);
        }

        List<Number> defaultVel=new ArrayList<>();

        defaultVel=robot.GetDefaultTransVel();
        System.out.println("GetDefaultTransVel is:"+ defaultVel.get(1));

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5);
            robot.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            float value = 0;
            defaultVel=robot.GetSysVarValue(i);
            System.out.println("sys value :"+i+", is :"+defaultVel.get(1));
            robot.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0;
        loadCoord.y = 4.0;
        loadCoord.z = 5.0;
        robot.SetLoadCoord(loadCoord);

        robot.Sleep(1000);

        List<Number> getLoad = new ArrayList<>();

        getLoad=robot.GetTargetPayload(0);

        DescTran getLoadTran =new DescTran();
        robot.GetTargetPayloadCog(0, getLoadTran);
        System.out.println("get load is:"+getLoad.get(1)+", get load cog is: "+getLoadTran.x+","+getLoadTran.y+","+getLoadTran.z);

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0, 25.0);

        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("GetRobotInstallAngle x:"+angle.get(1)+";  y:"+angle.get(2));

        robot.CloseRPC();
        return 0;
    }

Gelenk-Reibungskompensation ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensation ein-/ausschalten
    * @param [in] state 0 - aus, 1 - an
    * @return Fehlercode
    */
    int FrictionCompensationOnOff(int state);

Gelenk-Reibungskompensationskoeffizienten einstellen - Bodenmontage
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - Bodenmontage
    * @param [in] coeff Array von sechs Gelenkkompensationskoeffizienten, Bereich [0~1]
    * @return Fehlercode
    */
    int SetFrictionValue_level(Object[] coeff);

Gelenk-Reibungskompensationskoeffizienten einstellen - Wandmontage
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - Wandmontage
    * @param [in] coeff Array von sechs Gelenkkompensationskoeffizienten, Bereich [0~1]
    * @return Fehlercode
    */
    int SetFrictionValue_wall(Object[] coeff);

Gelenk-Reibungskompensationskoeffizienten einstellen - Deckenmontage
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - Deckenmontage
    * @param [in] coeff Array von sechs Gelenkkompensationskoeffizienten, Bereich [0~1]
    * @return Fehlercode
    */
    int SetFrictionValue_ceiling(Object[] coeff);

Gelenk-Reibungskompensationskoeffizienten einstellen - freie Montage
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - freie Montage
    * @param [in] coeff Array von sechs Gelenkkompensationskoeffizienten, Bereich [0~1]
    * @return Fehlercode
    */
    int SetFrictionValue_freedom(Object[] coeff);

Codebeispiel zum Einstellen der Gelenk-Reibungskompensation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFriction(Robot robot)
    {

        Object[] lcoeff = { 0.9,0.9,0.9,0.9,0.9,0.9 };
        Object[] wcoeff = { 0.4,0.4,0.4,0.4,0.4,0.4 };
        Object[] ccoeff = { 0.6,0.6,0.6,0.6,0.6,0.6 };
        Object[] fcoeff = { 0.5,0.5,0.5,0.5,0.5,0.5 };

        int rtn = robot.FrictionCompensationOnOff(1);
        System.out.println("FrictionCompensationOnOff rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_level(lcoeff);
        System.out.println("SetFrictionValue_level rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_wall(wcoeff);
        System.out.println("SetFrictionValue_wall rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        System.out.println("SetFrictionValue_ceiling rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        System.out.println("SetFrictionValue_freedom rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Roboter-Fehlercode abfragen
++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Roboter-Fehlercode abfragen
     * @param [out] maincode Hauptfehlercode (als Array der Länge 1 übergeben)
     * @param [out] subcode Unterfehlercode (als Array der Länge 1 übergeben)
     * @return Fehlercode
     */
    int GetRobotErrorCode(int[] maincode, int[] subcode);

Fehlerstatus löschen
++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fehlerstatus löschen
    * @return Fehlercode
    */
    int ResetAllError();

Codebeispiel zum Abrufen und Löschen von Roboter-Fehlerstatus
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetError(Robot robot)
    {
        int[] maincode={0}, subcode={0};
        robot.GetRobotErrorCode(maincode, subcode);

        robot.ResetAllError();

        robot.Sleep(1000);

        robot.GetRobotErrorCode(maincode, subcode);
        return 0;
    }

Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens einstellen
    * @param [in] enable 0 - Überwachung deaktivieren, 1 - Überwachung aktivieren
    * @param [in] period Überwachungszyklus (s), Bereich 1-100
    * @return Fehlercode
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens abrufen
    * @return List[0] - Fehlercode, List[1] - enable (0/1), List[2] - period (s)
    */
    List<Number> GetWideBoxTempFanMonitorParam()

Codebeispiel zum Abrufen von Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestWideVoltageCtrlBoxtemp(Robot robot)
    {
        robot.SetWideBoxTempFanMonitorParam(1, 2);
        List<Number> list=robot.GetWideBoxTempFanMonitorParam();
        System.out.println("GetWideBoxTempFanMonitorParam enable is:"+list.get(1)+", period is:"+list.get(2));
        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+",fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);

        list=robot.GetWideBoxTempFanMonitorParam();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+" ,fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        robot.CloseRPC();
        robot.Sleep(2000);
        return 0;
    }

Fokus-Kalibrierungspunkt setzen
++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Fokus-Kalibrierungspunkt setzen
    * @param [in] pointNum Kalibrierungspunktnummer (1-8)
    * @param [in] point Koordinaten des Kalibrierungspunkts (Pose)
    * @return Fehlercode
    */
    int SetFocusCalibPoint(int pointNum, DescPose point)

Fokus-Kalibrierungsergebnis berechnen
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Fokus-Kalibrierungsergebnis berechnen
    * @param [in] pointNum Anzahl der Kalibrierungspunkte
    * @param [in] resultPos Kalibriertes XYZ-Ergebnis (als Objekt zum Befüllen)
    * @param [out] accuracy Kalibriergenauigkeit (Fehler) als double[1]
    * @return Fehlercode
    */
    int ComputeFocusCalib(int pointNum, DescTran resultPos, double[] accuracy)

Fokusverfolgung starten
++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Fokusverfolgung starten
    * @param [in] kp Proportionalparameter, Standard 50.0
    * @param [in] kpredict Vorsteuerungsparameter, Standard 19.0
    * @param [in] aMax Maximale Winkelbeschleunigungsbegrenzung [°/s²], Standard 1440
    * @param [in] vMax Maximale Winkelgeschwindigkeitsbegrenzung [°/s], Standard 180
    * @param [in] type Ausrichtung der X-Achse (0 - Referenzeingangsvektor, 1 - horizontal, 2 - vertikal)
    * @return Fehlercode
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type)

Fokusverfolgung stoppen
++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Fokusverfolgung stoppen
    * @return Fehlercode
    */
    int FocusEnd()

Fokuskoordinaten einstellen
++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Fokuskoordinaten einstellen
    * @param pos Fokuskoordinaten XYZ
    * @return Fehlercode
    */
    public int SetFocusPosition(DescTran pos)

Codebeispiel für Fokusverfolgung
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFocus(Robot robot){
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint = new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
        DescPose p2Desc = new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint = new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
        DescPose p3Desc = new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint = new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
        DescPose p4Desc = new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint = new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
        DescPose p5Desc = new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint = new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
        DescPose p6Desc = new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint = new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 100, 0, 0, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint,  p2Desc);
        robot.GetForwardKin(p3Joint,  p3Desc);
        robot.GetForwardKin(p4Joint,  p4Desc);
        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);

        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4( coordRtn);

        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint, p2Desc);
        robot.GetForwardKin(p3Joint, p3Desc);

        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);

        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double[] accuracy = {0.0};
        rtn = robot.ComputeFocusCalib(3,  resultPos,  accuracy);
        rtn = robot.SetFocusPosition(resultPos);

        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);

        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.FocusEnd();
    }

Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung aktivieren
    * @param status 0 - deaktivieren, 1 - aktivieren
    * @return Fehlercode
    */
    public int JointSensitivityEnable(int status)

Gelenk-Drehmomentsensor-Empfindlichkeitsdaten erfassen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Empfindlichkeitsdaten erfassen
    * @return Fehlercode
    */
    public int JointSensitivityCollect()

Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung abrufen
    * @param calibResult Array (Länge 6) für die Empfindlichkeit j1~j6 [0-1]
    * @param linearity Array (Länge 6) für die Linearität j1~j6 [0-1]
    * @return Fehlercode
    */
    public int JointSensitivityCalibration(double[] calibResult, double[] linearity)

Gelenk-Drehmomentsensor-Hysteresefehler abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Hysteresefehler abrufen
    * @param hysteresisError Array (Länge 6) für die Hysteresefehler j1~j6
    * @return Fehlercode
    */
    public int JointHysteresisError(double[] hysteresisError);

Gelenk-Drehmomentsensor-Wiederholgenauigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Wiederholgenauigkeit abrufen
    * @param repeatability Array (Länge 6) für die Wiederholgenauigkeit j1~j6
    * @return Fehlercode
    */
    public int JointRepeatability(double[] repeatability);

Gelenk-Kraftsensor-Parameter einstellen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Gelenk-Kraftsensor-Parameter einstellen (für Impedanzregelung)
    * @param M Array (Länge 6) der Massenkoeffizienten J1-J6
    * @param B Array (Länge 6) der Dämpfungskoeffizienten J1-J6
    * @param K Array (Länge 6) der Steifigkeitskoeffizienten J1-J6
    * @param threshold Array (Länge 6) der Kraftregelungsschwellwerte [Nm]
    * @param sensitivity Array (Länge 6) der Empfindlichkeit [Nm/V]
    * @param setZeroFlag Funktionsaktivierungs-Flag; 0 - deaktivieren, 1 - aktivieren, 2 - Nullpunkt an Position 1 aufzeichnen, 3 - Nullpunkt an Position 2 aufzeichnen
    * @return Fehlercode
    */
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Codebeispiel für automatische Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSensitivityCalib(Robot robot)
    {
        int rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = new JointPos();
        robot.GetActualJointPosDegree(curJPos);
        ExaxisPos epos = new ExaxisPos(0,0,0,0);
        DescPose offset_pos =new DescPose(0,0,0,0,0,0 );
        JointPos jointPos1 = new JointPos(curJPos.J1, 0, 0, -90, 0.02, curJPos.J6);
        DescPose descPos1 = new DescPose();
        robot.GetForwardKin(jointPos1, descPos1);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 =new JointPos( curJPos.J1, -30, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos2 =new DescPose();
        robot.GetForwardKin(jointPos2, descPos2);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = new JointPos( curJPos.J1, -60, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos3 =new DescPose();
        robot.GetForwardKin(jointPos3, descPos3);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = new JointPos(curJPos.J1, -90, 0, -90, 0.02, curJPos.J6);
        DescPose descPos4 = new DescPose();
        robot.GetForwardKin(jointPos4, descPos4);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = new JointPos(curJPos.J1, -120, 0, -90, 0.02, curJPos.J6);
        DescPose descPos5 = new DescPose();
        robot.GetForwardKin(jointPos5, descPos5);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = new JointPos(curJPos.J1, -150, 0, -90, 0.02, curJPos.J6);
        DescPose descPos6 = new DescPose();
        robot.GetForwardKin(jointPos6, descPos6);
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = new JointPos(curJPos.J1, -180, 0, -90, 0.02, curJPos.J6);
        DescPose descPos7 = new DescPose();
        robot.GetForwardKin(jointPos7, descPos7);
        robot.MoveJ(jointPos7, descPos7, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //Rückwärtshub
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double[] calibResult =new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        System.out.printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        System.out.printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n",
                calibResult[0], calibResult[1], calibResult[2],
                calibResult[3], calibResult[4], calibResult[5],
                linearity[0], linearity[1], linearity[2],
                linearity[3], linearity[4], linearity[5]);
        double[] hysteresisError = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointHysteresisError(hysteresisError);
        System.out.printf("JointHysteresisError result is %f %f %f %f %f %f\n",
                hysteresisError[0], hysteresisError[1], hysteresisError[2],
                hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double[] repeatability = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointRepeatability(repeatability);
        System.out.printf("JointRepeatability result is %f %f %f %f %f %f\n",
                repeatability[0], repeatability[1], repeatability[2],
                repeatability[3], repeatability[4], repeatability[5]);
        double[] M = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] B = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] K = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        double[] threshold = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        System.out.printf("SetAdmittanceParams rtn is %d\n", rtn);
    }

Fehlerzähler der 8 Slave-Ports abrufen
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fehlerzähler der 8 Slave-Ports abrufen
    * @param inRecvErr Array (Länge 8) für Empfangsfehler (Eingang)
    * @param inCRCErr Array (Länge 8) für CRC-Fehler (Eingang)
    * @param inTransmitErr Array (Länge 8) für Übertragungsfehler (Eingang)
    * @param inLinkErr Array (Länge 8) für Link-Fehler (Eingang)
    * @param outRecvErr Array (Länge 8) für Empfangsfehler (Ausgang)
    * @param outCRCErr Array (Länge 8) für CRC-Fehler (Ausgang)
    * @param outTransmitErr Array (Länge 8) für Übertragungsfehler (Ausgang)
    * @param outLinkErr Array (Länge 8) für Link-Fehler (Ausgang)
    * @return Fehlercode
    */
    public int GetSlavePortErrCounter(int[] inRecvErr, int[] inCRCErr, int[] inTransmitErr, int[] inLinkErr, int[] outRecvErr, int[] outCRCErr, int[] outTransmitErr, int[] outLinkErr)

Slave-Port-Fehlerzähler zurücksetzen
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Slave-Port-Fehlerzähler zurücksetzen
    * @param slaveID Slave-Nummer 0~7
    * @return Fehlercode
    */
    public int SlavePortErrCounterClear(int slaveID)

Codebeispiel zum Abrufen der Slave-Port-Fehlerzähler
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSlavePortErr(Robot robot)
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        int[] inRecvErr =new int[8];
        int[] inCRCErr =new int[8];
        int[] inTransmitErr =new int[8];
        int[] inLinkErr =new int[8];
        int[] outRecvErr =new int[8];
        int[] outCRCErr =new int[8];
        int[] outTransmitErr =new int[8];
        int[] outLinkErr =new int[8];
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
                outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                System.out.printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                System.out.printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                System.out.printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                System.out.printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        System.out.printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
    }

Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse einstellen
    * @param radio Array (Länge 6) der Geschwindigkeits-Vorsteuerkoeffizienten
    * @return Fehlercode
    */
    public int SetVelFeedForwardRatio(double[] radio)

Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse abrufen
    * @param radio Array (Länge 6) zum Befüllen mit den Koeffizienten
    * @return Fehlercode
    */
    public int GetVelFeedForwardRatio(double[] radio)

Codebeispiel für Geschwindigkeits-Vorsteuerkoeffizienten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestVelFeedForwardRatio(Robot robot)
    {
        double[] setRadio =new double[] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[]{ 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        System.out.printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
    }

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen
    * @param Btool Roboter-Kartesische Position (Pose)
    * @param Etool Aktueller Wert des Werkzeugkoordinatensystems (Pose)
    * @param sensor Aktueller Wert des Sensorkoordinatensystems (Pose, vorübergehend nicht freigegeben)
    * @param radius Radius der Kreisbewegung [mm] (vorübergehend nicht freigegeben)
    * @param dz Bewegungsdistanz entlang der negativen Z-Achse des Basiskoordinatensystems; wenn dz = 10000, gibt die Funktion direkt das Werkzeug-RPY zurück
    * @param TCPRPY Ausgabe-Objekt für die berechneten Werkzeug-RPY-Werte
    * @return Fehlercode
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, Rpy TCPRPY)

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen
    * @param select 0 - Werkzeug-TCP berechnen, 1 - Sensorursprung berechnen, 2 - Sensorausrichtung berechnen, 3 - Werkzeug-TCP direkt zurückgeben, 4 - Aktuelles Werkstück- und Werkzeugkoordinatensystem aufzeichnen
    * @param originDirection 0 - X-Richtung, 1 - Y-Richtung, 2 - Z-Richtung
    * @param pos1 Roboter-Kartesische Position 1 (nur Translation)
    * @param pos2 Roboter-Kartesische Position 2 (nur Translation)
    * @param pos3 Roboter-Kartesische Position 3 (nur Translation)
    * @param pos4 Roboter-Kartesische Position 4 (nur Translation)
    * @param TCP Ausgabe-Objekt für die berechneten Werkzeug-XYZ-Werte
    * @return Fehlercode
    */
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2, DescTran pos3, DescTran pos4, DescTran TCP)

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position starten
    * @return Fehlercode
    */
    public int TCPRecordFlangePosStart()

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position stoppen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position stoppen
    * @return Fehlercode
    */
    public int TCPRecordFlangePosEnd()

Photoelektrischer Sensor TCP-Kalibrierung - Position des Werkzeugmittelpunkts abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Position des Werkzeugmittelpunkts abrufen
    * @param TCP Ausgabe-Objekt für die Position (x,y,z)
    * @return Fehlercode
    */
    public int TCPGetRecordFlangePos(DescTran TCP)

Photoelektrischer Sensor TCP-Kalibrierung (automatisiert)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung (automatisiert)
    * @param luaPath Pfad zum automatischen Kalibrierungs-Lua-Programm: QX-Roboter - "/fruser/FR_CalibrateTheToolTcp.lua"; LA-Roboter - "/usr/local/etc/controller/lua/FR_CalibrateTheToolTcp.lua"
    * @param offset Versatz der Teachpunkte (x, y, z) [mm]
    * @param TCP Ausgabe-Objekt für das kalibrierte Werkzeugkoordinatensystem (x, y, z, rx, ry, rz)
    * @return Fehlercode
    */
    public int PhotoelectricSensorTCPCalibration(String luaPath, DescTran offset, DescPose TCP)

Codebeispiel für photoelektrische Sensor TCP-Kalibrierung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestPhotoelectricSensorTCPCalib(Robot robot)
    {
        DescTran offset = new DescTran(10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("/fruser/FR_CalibrateTheToolTcp.lua", offset, TCP);
        System.out.printf("PhotoelectricSensorTCPCalibration rtn is %d %f %f %f %f %f %f \n", rtn, TCP.tran.x, TCP.tran.y, TCP.tran.z, TCP.rpy.rx, TCP.rpy.ry, TCP.rpy.rz);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }