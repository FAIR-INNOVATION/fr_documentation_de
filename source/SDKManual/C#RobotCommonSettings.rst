Allgemeine Roboter-Einstellungen
=========================================

.. toctree::
    :maxdepth: 5

Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Legt den Werkzeug-Referenzpunkt fest - Sechs-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~6]
    * @return Fehlercode
    */
    int SetToolPoint(int point_num);

Werkzeugkoordinatensystem berechnen - Sechs-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Berechnet das Werkzeugkoordinatensystem
    * @param [out] tcp_pose Werkzeugkoordinatensystem
    * @return Fehlercode
    */
    int ComputeTool(ref DescPose tcp_pose);

Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Legt den Werkzeug-Referenzpunkt fest - Vier-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~4]
    * @return Fehlercode
    */
    int SetTcp4RefPoint(int point_num);

Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Berechnet das Werkzeugkoordinatensystem
    * @param [out] tcp_pose Werkzeugkoordinatensystem
    * @return Fehlercode
    */
    int ComputeTcp4(ref DescPose tcp_pose);

Werkzeugkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt das Werkzeugkoordinatensystem ein
    * @param  [in] id Koordinatensystem-Nummer, Bereich [0~14]
    * @param  [in] coord  Pose des Werkzeugmittelpunkts relativ zur Flanschmitte
    * @param  [in] type  0-Werkzeugkoordinatensystem, 1-Sensorkoordinatensystem
    * @param  [in] install Einbauort, 0-Roboterflansch, 1-außerhalb des Roboters
    * @param  [in] toolID Werkzeug-ID
    * @param  [in] loadNum Nutzlastnummer
    * @return  Fehlercode
    */
    int SetToolCoord(int id, DescPose coord, int type, int install, int toolID, int loadNum);

Werkzeugkoordinatensystem basierend auf Punkten berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Berechnet das Werkzeugkoordinatensystem basierend auf Punkten
    * @param [in] method Berechnungsmethode; 0-Vier-Punkt-Methode; 1-Sechs-Punkt-Methode
    * @param [in] pos Array von Gelenkpositionen, Länge 4 für Vier-Punkt, Länge 6 für Sechs-Punkt
    * @return Fehlercode
    */

    int ComputeToolCoordWithPoints(int method, JointPos[] pos, ref DescPose coordRtn);

Liste der Werkzeugkoordinatensysteme einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Liste der Werkzeugkoordinatensysteme ein
    * @param  [in] id Koordinatensystem-Nummer, Bereich [0~14]
    * @param  [in] coord  Pose des Werkzeugmittelpunkts relativ zur Flanschmitte
    * @param  [in] type  0-Werkzeugkoordinatensystem, 1-Sensorkoordinatensystem
    * @param  [in] install Einbauort, 0-Roboterflansch, 1-außerhalb des Roboters
    * @param  [in] loadNum Nutzlastnummer
    * @return  Fehlercode
    */
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);

Aktuelles Werkzeugkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt das aktuelle Werkzeugkoordinatensystem zurück
    * @param  [in] flag 0-blockierend, 1-nicht blockierend
    * @param  [out] desc_pos Pose des Werkzeugkoordinatensystems
    * @return  Fehlercode
    */
    int GetTCPOffset(byte flag, ref DescPose desc_pos);

Codebeispiel für Operationen mit Roboter-Werkzeugkoordinatensystemen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button18_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(186.331f, 487.913f, 209.850f, 149.030f, 0.688f, -114.347f);
        JointPos p1Joint = new JointPos(-127.876f, -75.341f, 115.417f, -122.741f, -59.820f, 74.300f);

        DescPose p2Desc = new DescPose(69.721f, 535.073f, 202.882f, -144.406f, -14.775f, -89.012f);
        JointPos p2Joint = new JointPos(-101.780f, -69.828f, 110.917f, -125.740f, -127.841f, 74.300f);

        DescPose p3Desc = new DescPose(146.861f, 578.426f, 205.598f, 175.997f, -36.178f, -93.437f);
        JointPos p3Joint = new JointPos(-112.851f, -60.191f, 86.566f, -80.676f, -97.463f, 74.300f);

        DescPose p4Desc = new DescPose(136.284f, 509.876f, 225.613f, 178.987f, 1.372f, -100.696f);
        JointPos p4Joint = new JointPos(-116.397f, -76.281f, 113.845f, -128.611f, -88.654f, 74.299f);

        DescPose p5Desc = new DescPose(138.395f, 505.972f, 298.016f, 179.134f, 2.147f, -101.110f);
        JointPos p5Joint = new JointPos(-116.814f, -82.333f, 109.162f, -118.662f, -88.585f, 74.302f);

        DescPose p6Desc = new DescPose(105.553f, 454.325f, 232.017f, -179.426f, 0.444f, -99.952f);
        JointPos p6Joint = new JointPos(-115.649f, -84.367f, 122.447f, -128.663f, -90.432f, 74.303f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = new JointPos[] { p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, ref coordRtn);
        Console.WriteLine($"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(4);
        robot.MoveJ( p5Joint,  p5Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(5);
        robot.MoveJ( p6Joint,  p6Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(ref coordRtn);
        Console.WriteLine($"6 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
        robot.SetToolList(1,  coordRtn, 0, 0, 0);

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose();
        rtn = robot.GetTCPOffset(0, ref getCoord);
        Console.WriteLine($"GetTCPOffset    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
    }

Externen Werkzeug-Referenzpunkt einstellen - Drei-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Legt den externen Werkzeug-Referenzpunkt fest - Drei-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~3]
    * @return Fehlercode
    */
    int SetExTCPPoint(int point_num);

Externes Werkzeugkoordinatensystem berechnen - Drei-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Berechnet das externe Werkzeugkoordinatensystem - Drei-Punkt-Methode
    * @param [out] tcp_pose Externes Werkzeugkoordinatensystem
    * @return Fehlercode
    */
    int ComputeExTCF(ref DescPose tcp_pose);

Externes Werkzeugkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt das externe Werkzeugkoordinatensystem ein
    * @param [in] id Koordinatensystem-Nummer, 20-39 entsprechen den externen Werkzeugkoordinatensystemen 0-19
    * @param [in] etcp Pose des Werkzeugmittelpunkts relativ zur Flanschmitte
    * @param [in] etool Unbestimmt
    * @return Fehlercode
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool);

Liste der externen Werkzeugkoordinatensysteme einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Liste der externen Werkzeugkoordinatensysteme ein
    * @param  [in] id Koordinatensystem-Nummer, 20-39 entsprechen den externen Werkzeugkoordinatensystemen 0-19
    * @param  [in] etcp  Pose des Werkzeugmittelpunkts relativ zur Flanschmitte
    * @param  [in] etool  Unbestimmt
    * @return  Fehlercode
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool);

Werkstückkoordinatensystem basierend auf Punkten berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Berechnet das Werkstückkoordinatensystem basierend auf Punkten
    * @param [in] method Berechnungsmethode; 0: Ursprung - X-Achse - Z-Achse  1: Ursprung - X-Achse - XY-Ebene
    * @param [in] pos Array von drei TCP-Positionen
    * @param [in] refFrame Referenzkoordinatensystem
    * @return Fehlercode
    */
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame, ref DescPose coordRtn);

Codebeispiel für Operationen mit externen Roboter-Werkzeugkoordinatensystemen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button20_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606f, 779.517f, 193.516f, 178.000f, 0.476f, -92.484f);
        JointPos p1Joint = new JointPos(-108.145f, -50.137f, 85.818f, -125.599f, -87.946f, 74.329f);

        DescPose p2Desc = new DescPose(-24.656f, 850.384f, 191.361f, 177.079f, -2.058f, -95.355f);
        JointPos p2Joint = new JointPos(-111.024f, -41.538f, 69.222f, -114.913f, -87.743f, 74.329f);

        DescPose p3Desc = new DescPose(-99.813f, 766.661f, 241.878f, -176.817f, 1.917f, -91.604f);
        JointPos p3Joint = new JointPos(-107.266f, -56.116f, 85.971f, -122.560f, -92.548f, 74.331f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(ref coordRtn);
        Console.WriteLine($"ComputeExTCF                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetExToolCoord(1,  coordRtn,  offdese);
        robot.SetExToolList(1,  coordRtn,  offdese);
    }

Werkstück-Referenzpunkt einstellen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Legt den Werkstück-Referenzpunkt fest - Drei-Punkt-Methode
    * @param [in] point_num Punktnummer, Bereich [1~3]
    * @return Fehlercode
    */
    int SetWObjCoordPoint(int point_num);

Werkstückkoordinatensystem berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Berechnet das Werkstückkoordinatensystem
    * @param [in] method Berechnungsmethode 0: Ursprung - X-Achse - Z-Achse  1: Ursprung - X-Achse - XY-Ebene
    * @param [in] refFrame Referenzkoordinatensystem
    * @param [out] wobj_pose Werkstückkoordinatensystem
    * @return Fehlercode
    */
    int ComputeWObjCoord(int method, int refFrame, ref DescPose wobj_pose);

Werkstückkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt das Werkstückkoordinatensystem ein
    * @param  [in] id Koordinatensystem-Nummer, Bereich [1~15]
    * @param  [in] coord  Pose des Werkstückkoordinatensystems relativ zur Flanschmitte
    * @param  [in] refFrame Referenzkoordinatensystem
    * @return  Fehlercode
    */
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Liste der Werkstückkoordinatensysteme einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Liste der Werkstückkoordinatensysteme ein
    * @param  [in] id Koordinatensystem-Nummer, Bereich [0~14]
    * @param  [in] coord  Pose des Werkstückkoordinatensystems relativ zur Flanschmitte
    * @param  [in] refFrame Referenzkoordinatensystem
    * @return  Fehlercode
    */
    int SetWObjList(int id, DescPose coord, int refFrame);

Aktuelles Werkstückkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt das aktuelle Werkstückkoordinatensystem zurück
    * @param  [in] flag 0-blockierend, 1-nicht blockierend
    * @param  [out] desc_pos Pose des Werkstückkoordinatensystems
    * @return  Fehlercode
    */
    int GetWObjOffset(byte flag, ref DescPose desc_pos);

Codebeispiel für Operationen mit Roboter-Werkstückkoordinatensystemen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button19_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint = new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc = new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint = new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc = new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint = new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint,ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoord                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetWObjCoord(1,  coordRtn, 0);
        robot.SetWObjList(1,  coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, ref getWobjDesc);
        Console.WriteLine($"GetWObjOffset                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
    }

Globale Geschwindigkeit einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die globale Geschwindigkeit ein
    * @param  [in]  vel  Geschwindigkeit in Prozent, Bereich [0~100]
    * @return  Fehlercode
    */
    int SetSpeed(int vel);

Roboter-Beschleunigung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Roboter-Beschleunigung ein
    * @param [in] acc Roboter-Beschleunigung in Prozent
    * @return Fehlercode
    */
    int SetOaccScale(double acc);

Standardgeschwindigkeit des Roboters abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die Standardgeschwindigkeit des Roboters zurück
    * @param  [out]  vel  Geschwindigkeit, Einheit mm/s
    * @return  Fehlercode
    */
    int GetDefaultTransVel(ref double vel);

Endnutzlastgewicht einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt das Endnutzlastgewicht ein
    * @param  [in] loadNum Nutzlastnummer
    * @param  [in] weight  Nutzlastgewicht, Einheit kg
    * @return  Fehlercode
    */
    int SetLoadWeight(int loadNum, float weight);

Endnutzlast-Schwerpunktkoordinaten einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Endnutzlast-Schwerpunktkoordinaten ein
    * @param  [in] coord Schwerpunktkoordinaten, Einheit mm
    * @return  Fehlercode
    */
    int SetLoadCoord(DescTran coord);

Aktuelles Nutzlastgewicht abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt das Gewicht der aktuellen Nutzlast zurück
    * @param  [in] flag 0-blockierend, 1-nicht blockierend
    * @param  [out] weight Nutzlastgewicht, Einheit kg
    * @return  Fehlercode
    */
    int GetTargetPayload(byte flag, ref double weight);

Aktuellen Nutzlast-Schwerpunkt abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt den Schwerpunkt der aktuellen Nutzlast zurück
    * @param  [in] flag 0-blockierend, 1-nicht blockierend
    * @param  [out] cog Nutzlast-Schwerpunkt, Einheit mm
    * @return  Fehlercode
    */
    int GetTargetPayloadCog(byte flag, ref DescTran cog);

Roboter-Installationsart einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Installationsart des Roboters ein
    * @param  [in] install  Installationsart, 0-normal, 1-Seitenmontage, 2-Überkopfmontage
    * @return  Fehlercode
    */
    int SetRobotInstallPos(byte install);

Roboter-Installationswinkel einstellen (freie Installation)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Installationswinkel des Roboters ein (freie Installation)
    * @param  [in] yangle  Neigungswinkel
    * @param  [in] zangle  Rotationswinkel
    * @return  Fehlercode
    */
    int SetRobotInstallAngle(double yangle, double zangle);

Roboter-Installationswinkel abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt die Installationswinkel des Roboters zurück
    * @param  [out] yangle Neigungswinkel
    * @param  [out] zangle Rotationswinkel
    * @return  Fehlercode
    */
    int GetRobotInstallAngle(ref double yangle, ref double zangle);

Systemvariablenwert setzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Setzt den Wert einer Systemvariablen
    * @param  [in]  id  Variablen-Nummer, Bereich [1~20]
    * @param  [in]  value Variablenwert
    * @return  Fehlercode
    */
    int SetSysVarValue(int id, double value);

Systemvariablenwert abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Gibt den Wert einer Systemvariablen zurück
    * @param  [in] id Systemvariablen-Nummer, Bereich [1~20]
    * @param  [out] value  Systemvariablenwert
    * @return  Fehlercode
    */
    int GetSysVarValue(int id, ref double value);

Codebeispiel für allgemeine Roboter-Einstellungen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void button21_Click(object sender, EventArgs e)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            Thread.Sleep(30);
        }

        double defaultVel = 0.0f;
        robot.GetDefaultTransVel(ref defaultVel);
        Console.WriteLine($"GetDefaultTransVel is {defaultVel}");

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5f);
            Thread.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            double value = 0;
            robot.GetSysVarValue(i, ref value);
            Console.WriteLine($"sys value  {i} is :{value}");
            Thread.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5f);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0f;
        loadCoord.y = 4.0f;
        loadCoord.z = 5.0f;
        robot.SetLoadCoord( loadCoord);

        Thread.Sleep(1000);

        double getLoad = 0.0f;
        robot.GetTargetPayload(0, ref getLoad);

        DescTran getLoadTran = new DescTran();
        robot.GetTargetPayloadCog(0, ref getLoadTran);
        Console.WriteLine($"get load is {getLoad}; get load cog is {getLoadTran.x} {getLoadTran.y} {getLoadTran.z}");

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0f, 25.0f);

        double anglex = 0.0f;
        double angley = 0.0f;
        robot.GetRobotInstallAngle(ref anglex, ref angley);
        Console.WriteLine($"GetRobotInstallAngle x:  {anglex};  y:  {angley}");
    }

Schalter für Gelenk-Reibungskompensation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Schalter für Gelenk-Reibungskompensation
    * @param [in] state 0-Aus, 1-Ein
    * @return Fehlercode
    */
    int FrictionCompensationOnOff(byte state);

Koeffizienten für Gelenk-Reibungskompensation einstellen - Normalmontage
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - Normalmontage
    * @param  [in]  coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return  Fehlercode
    */
    int SetFrictionValue_level(double[] coeff);

Koeffizienten für Gelenk-Reibungskompensation einstellen - Seitenmontage
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - Seitenmontage
    * @param  [in]  coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return  Fehlercode
    */
    int SetFrictionValue_wall(double[] coeff);

Koeffizienten für Gelenk-Reibungskompensation einstellen - Überkopfmontage
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - Überkopfmontage
    * @param  [in]  coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return  Fehlercode
    */
    int SetFrictionValue_ceiling(double[] coeff);

Koeffizienten für Gelenk-Reibungskompensation einstellen - freie Installation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Stellt die Koeffizienten für Gelenk-Reibungskompensation ein - freie Installation
    * @param  [in]  coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return  Fehlercode
    */
    int SetFrictionValue_freedom(double[] coeff);

Codebeispiel für Roboter-Joint-Friction-Compensation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] lcoeff = { 0.9f, 0.9f, 0.9f, 0.9f, 0.9f, 0.9f };
        double[] wcoeff = { 0.4f, 0.4f, 0.4f, 0.4f, 0.4f, 0.4f };
        double[] ccoeff = { 0.6f, 0.6f, 0.6f, 0.6f, 0.6f, 0.6f };
        double[] fcoeff = { 0.5f, 0.5f, 0.5f, 0.5f, 0.5f, 0.5f };

        int rtn = robot.FrictionCompensationOnOff(1);
        Console.WriteLine($"FrictionCompensationOnOff rtn is{rtn}");

        rtn = robot.SetFrictionValue_level(lcoeff);
        Console.WriteLine($"SetFrictionValue_level rtn is {rtn}");

        rtn = robot.SetFrictionValue_wall(wcoeff);
        Console.WriteLine($"SetFrictionValue_wall rtn is{rtn}");

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        Console.WriteLine($"SetFrictionValue_ceiling rtn is {rtn}");

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        Console.WriteLine($"SetFrictionValue_freedom rtn is {rtn}");
    }

Roboter-Fehlercode abfragen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Fragt den Roboter-Fehlercode ab
    * @param [out] maincode   Hauptfehlercode
    * @param [out] subcode    Unterfehlercode
    * @return Fehlercode
    */
    int GetRobotErrorCode(ref int maincode, ref int subcode);

Fehlerzustand löschen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief  Löscht den Fehlerzustand
    * @return  Fehlercode
    */
    int ResetAllError();

Codebeispiel für Roboter-Fehlerstatusabfrage und -löschung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        int maincode=0, subcode=0;
        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is {subcode}" );

        robot.ResetAllError();

        Thread.Sleep(1000);

        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is{subcode}");
    }

Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks ein
    * @param [in] enable 0-Überwachung deaktivieren; 1-Überwachung aktivieren
    * @param [in] period Überwachungsperiode (s), Bereich 1-100
    * @return Fehlercode
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Parameter für die Überwachung der Temperatur und Lüfterdrehzahl des Weitbereichs-Steuerschranks zurück
    * @param [out] enable 0-Überwachung deaktiviert; 1-Überwachung aktiviert
    * @param [out] period Überwachungsperiode (s), Bereich 1-100
    * @return Fehlercode
    */
    int GetWideBoxTempFanMonitorParam(ref int enable, ref int period);

Codebeispiel
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: csharp
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        var pkg = new ROBOT_STATE_PKG();
        robot.SetWideBoxTempFanMonitorParam(1, 2);
        int enable = 0;
        int period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }
        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
        Console.WriteLine($"SetWideBoxTempFanMonitorParam rtn is {rtn}");
        enable = 0;
        period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($" robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }
    }

Fokus-Kalibrierpunkt setzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Setzt einen Fokus-Kalibrierpunkt
    * @param [in] pointNum Fokus-Kalibrierpunktnummer 1-8
    * @param [in] point Koordinaten des Kalibrierpunkts
    * @return Fehlercode
    */
    int SetFocusCalibPoint(int pointNum, DescPose point);

Fokus-Koordinaten setzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Setzt die Fokus-Koordinaten
    * @param [in] pos Fokus-Koordinaten XYZ
    * @return Fehlercode
    */
    int SetFocusPosition(DescTran pos);

Fokus-Verfolgung starten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Startet die Fokus-Verfolgung
    * @param [in] kp Proportionalparameter, Standard 50.0
    * @param [in] kpredict Vorsteuerungsparameter, Standard 19.0
    * @param [in] aMax Maximale Winkelbeschleunigungsbegrenzung, Standard 1440°/s^2
    * @param [in] vMax Maximale Winkelgeschwindigkeitsbegrenzung, Standard 180°/s
    * @param [in] type Sperren der X-Achsen-Ausrichtung (0-Referenz-Eingabevektor; 1-horizontal; 2-vertikal)
    * @return Fehlercode
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type);

Fokus-Verfolgung stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stoppt die Fokus-Verfolgung
    * @return Fehlercode
    */
    int FocusEnd();

Codebeispiel für Fokus-Verfolgung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: csharp
    :linenos:

    private void button81_Click(object sender, EventArgs e)
    {
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
        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.GetForwardKin(p4Joint, ref p4Desc);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool      {rtn} coord is {coordRtn.tran.x} ,{coordRtn.tran.y} ,{coordRtn.tran.z} ,{coordRtn.rpy.rx} ,{coordRtn.rpy.ry} ,{coordRtn.rpy.rz} ");
        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);
        robot.GetForwardKin(p1Joint, ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);
        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double accuracy = 0.0;
        rtn = robot.ComputeFocusCalib(3, ref resultPos, ref accuracy);
        Console.WriteLine($"ComputeFocusCalib coord is  {rtn},{ resultPos.x} ,{ resultPos.y}, { resultPos.z}, accuracy is {accuracy} ");
        rtn = robot.SetFocusPosition(resultPos);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusEnd();
    }

Aktivierung der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Aktivierung der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung
    * @param [in] status 0-deaktivieren; 1-aktivieren
    * @return  Fehlercode
    */
    public int JointSensitivityEnable(int status);

Datenerfassung für Gelenk-Drehmomentsensor-Empfindlichkeit
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Datenerfassung für Gelenk-Drehmomentsensor-Empfindlichkeit
    * @return Fehlercode
    */
    public int JointSensitivityCollect();

Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt das Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung zurück
    * @param [out] calibResult J1~J6 Gelenkempfindlichkeit [0-1]
    * @param [out] linearity J1~J6 Gelenklinearität [0-1]
    * @return Fehlercode
    */
    public int JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Gelenk-Drehmomentsensor-Hysteresefehler abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt den Hysteresefehler des Gelenk-Drehmomentsensors zurück
    * @param [out] hysteresisError J1~J6 Hysteresefehler
    * @return Fehlercode
    */
    public int JointHysteresisError(ref double[] hysteresisError);

Gelenk-Drehmomentsensor-Wiederholgenauigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Wiederholgenauigkeit des Gelenk-Drehmomentsensors zurück
    * @param [out] repeatability J1~J6 Wiederholgenauigkeit
    * @return Fehlercode
    */
    public int JointRepeatability(ref double[] repeatability);

Gelenk-Kraftsensor-Parameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Gelenk-Kraftsensor-Parameter ein
    * @param [in] M J1-J6 Massenkoeffizient [0.001 ~ 10]
    * @param [in] B J1-J6 Dämpfungskoeffizient [0.001 ~ 10]
    * @param [in] K J1-J6 Steifigkeitskoeffizient [0.001 ~ 10]
    * @param [in] threshold Kraftregelungsschwelle, Nm
    * @param [in] sensitivity Empfindlichkeit, Nm/V, [0 ~ 10]
    * @param [in] setZeroFlag Funktionsaktivierungs-Flag; 0-deaktivieren; 1-aktivieren; 2-Position 1 Nullpunkt aufzeichnen; 3-Position 2 Nullpunkt aufzeichnen
    * @return Fehlercode
    */
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Codebeispiel für automatische Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    public int TestSensitivityCalib()
    {
        int rtn;
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");

        JointPos curJPos = new JointPos(0, 0, 0, 0, 0, 0);
        robot.GetActualJointPosDegree(0, ref curJPos);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        JointPos[] jointPoses = new JointPos[]
        {
            new JointPos(curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5])
        };
        for (int i = 0; i < jointPoses.Length; i++)
        {
            DescPose descPos = new DescPose(0, 0, 0, 0, 0, 0);
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            Thread.Sleep(i == 0 ? 200 : 100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {i + 1} rtn is {rtn}");
            Thread.Sleep(100);
        }

        for (int i = jointPoses.Length - 2; i >= 0; i--)
        {
            DescPose descPos = new DescPose();
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            Thread.Sleep(100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {jointPoses.Length + (jointPoses.Length - 1 - i)} rtn is {rtn}");
            Thread.Sleep(100);
        }
        double[] calibResult = new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(ref calibResult, ref linearity);
        Console.WriteLine($"JointSensitivityCalibration rtn is {rtn}");
        rtn = robot.JointSensitivityEnable(0);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");
        Console.WriteLine($"jointSensor Calib result is {calibResult[0]:F6} {calibResult[1]:F6} {calibResult[2]:F6} {calibResult[3]:F6} {calibResult[4]:F6} {calibResult[5]:F6}");
        Console.WriteLine($"jointSensor linearity is {linearity[0]:F6} {linearity[1]:F6} {linearity[2]:F6} {linearity[3]:F6} {linearity[4]:F6} {linearity[5]:F6}");
        double[] hysteresisError = new double[6];
        rtn = robot.JointHysteresisError(ref hysteresisError);
        Console.WriteLine($"JointHysteresisError result is {hysteresisError[0]:F6} {hysteresisError[1]:F6} {hysteresisError[2]:F6} {hysteresisError[3]:F6} {hysteresisError[4]:F6} {hysteresisError[5]:F6}");
        double[] repeatability = new double[6];
        rtn = robot.JointRepeatability(ref repeatability);
        Console.WriteLine($"JointRepeatability result is {repeatability[0]:F6} {repeatability[1]:F6} {repeatability[2]:F6} {repeatability[3]:F6} {repeatability[4]:F6} {repeatability[5]:F6}");
        double[] M = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] B = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] K = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] threshold = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        Console.WriteLine($"SetAdmittanceParams rtn is {rtn}");
        robot.CloseRPC();
        return 0;
    }

Fehlerzähler der 8 Slave-Ports des Roboters abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Fehlerzähler der 8 Slave-Ports des Roboters zurück
    * @param [out] inRecvErr Eingang Empfangsfehlerzähler
    * @param [out] inCRCErr Eingang CRC-Fehlerzähler
    * @param [out] inTransmitErr Eingang Übertragungsfehlerzähler
    * @param [out] inLinkErr Eingang Verbindungsfehlerzähler
    * @param [out] outRecvErr Ausgang Empfangsfehlerzähler
    * @param [out] outCRCErr Ausgang CRC-Fehlerzähler
    * @param [out] outTransmitErr Ausgang Übertragungsfehlerzähler
    * @param [out] outLinkErr Ausgang Verbindungsfehlerzähler
    * @return Fehlercode
    */
    public int GetSlavePortErrCounter(ref int[] inRecvErr,ref int[] inCRCErr,ref int[] inTransmitErr,ref int[] inLinkErr,ref int[] outRecvErr,ref int[] outCRCErr,ref int[] outTransmitErr,ref int[] outLinkErr);

Slave-Port-Fehlerzähler zurücksetzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Setzt den Fehlerzähler eines Slave-Ports zurück
    * @param [in] slaveID Slave-Nummer 0~7
    * @return Fehlercode
    */
    public int SlavePortErrCounterClear(int slaveID);

Codebeispiel für Slave-Port-Fehlerzähler
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    public void TestSlavePortErr()
    {
        int[] inRecvErr = new int[8];
        int[] inCRCErr = new int[8];
        int[] inTransmitErr = new int[8];
        int[] inLinkErr = new int[8];
        int[] outRecvErr = new int[8];
        int[] outCRCErr = new int[8];
        int[] outTransmitErr = new int[8];
        int[] outLinkErr = new int[8];

        robot.GetSlavePortErrCounter(ref inRecvErr, ref inCRCErr, ref inTransmitErr, ref inLinkErr,
            ref outRecvErr, ref outCRCErr, ref outTransmitErr, ref outLinkErr);

        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                Console.WriteLine($"inRecvErr {i} is {inRecvErr[i]}");
            }

            if (inCRCErr[i] != 0)
            {
                Console.WriteLine($"inCRCErr {i} is {inCRCErr[i]}");
            }

            if (inTransmitErr[i] != 0)
            {
                Console.WriteLine($"inTransmitErr {i} is {inTransmitErr[i]}");
            }

            if (inLinkErr[i] != 0)
            {
                Console.WriteLine($"inLinkErr {i} is {inLinkErr[i]}");
            }

            if (outRecvErr[i] != 0)
            {
                Console.WriteLine($"outRecvErr {i} is {outRecvErr[i]}");
            }

            if (outCRCErr[i] != 0)
            {
                Console.WriteLine($"outCRCErr {i} is {outCRCErr[i]}");
            }

            if (outTransmitErr[i] != 0)
            {
                Console.WriteLine($"outTransmitErr {i} is {outTransmitErr[i]}");
            }

            if (outLinkErr[i] != 0)
            {
                Console.WriteLine($"outLinkErr {i} is {outLinkErr[i]}");
            }
        }
        Console.WriteLine("others has no err!");

        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }

        robot.CloseRPC();
    }

Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Stellt die Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse ein
    * @param [in] radio Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse
    * @return Fehlercode
    */
    public int SetVelFeedForwardRatio(double radio[6]);

Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: csharp
    :linenos:

    /**
    * @brief Gibt die Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse zurück
    * @param [out] radio Geschwindigkeits-Vorsteuerungskoeffizienten für jede Achse
    * @return Fehlercode
    */
    public int GetVelFeedForwardRatio(ref double radio[6]);

Codebeispiel zum Einstellen der Geschwindigkeitsvorsteuerung des Roboters
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    public void TestVelFeedForwardRatio()
    {

        double[] setRadio = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        robot.GetVelFeedForwardRatio(ref getRadio);
        Console.WriteLine($" {getRadio[0]:F6} {getRadio[1]:F6} {getRadio[2]:F6} {getRadio[3]:F6} {getRadio[4]:F6} {getRadio[5]:F6}");
    }

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen
    * @param [in] Btool Roboter-kartesische Position
    * @param [in] Etool Aktueller Werkzeugkoordinatenwert
    * @param [in] sensor Aktueller Sensorkoordinatenwert (noch nicht freigegeben)
    * @param [in] radius Radius der Kreisbewegung mm (noch nicht freigegeben)
    * @param [in] dz Bewegungsabstand entlang der negativen Z-Achse des Basiskoordinatensystems; wenn dz = 10000, gibt die Funktion direkt das Werkzeug-RPY zurück
    * @param [out] TCPRPY Werkzeug-RPY-Wert
    * @return Fehlercode
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, out Rpy TCPRPY);

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen
    * @param [in] select 0-Werkzeug-TCP berechnen; 1-Sensorursprung berechnen; 2-Sensorausrichtung berechnen; 3-Werkzeug-TCP direkt zurückgeben; 4-Aktuelles Werkstück- und Werkzeugkoordinatensystem aufzeichnen
    * @param [in] originDirection 0-X-Richtung; 1-Y-Richtung; 2-Z-Richtung
    * @param [in] pos1 Roboter-kartesische Position 1
    * @param [in] pos2 Roboter-kartesische Position 2
    * @param [in] pos3 Roboter-kartesische Position 3
    * @param [in] pos4 Roboter-kartesische Position 4
    * @param [out] TCP Werkzeug-XYZ-Wert
    * @return Fehlercode
    */
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2,DescTran pos3, DescTran pos4, out DescTran TCP);

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition starten
    * @return Fehlercode
    */
    errno_t TCPRecordFlangePosStart();

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition stoppen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunktposition stoppen
    * @return Fehlercode
    */
    public int TCPRecordFlangePosEnd();

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeugmittelpunktposition abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Werkzeugmittelpunktposition abrufen
    * @param [out] TCP Werkzeugmittelpunktposition (x, y, z)
    * @return Fehlercode
    */
    public int TCPGetRecordFlangePos(out DescTran TCP);

Photoelektrischer Sensor TCP-Kalibrierung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung
    * @param [in] luaPath Pfad zum automatischen Kalibrierungs-Lua-Programm: "FR_CalibrateTheToolTcp.lua"
    * @param [in] offsetX Teachpunktversatz (x, y, z) mm
    * @param [out] TCP Kalibriertes Werkzeugkoordinatensystem (x, y, z, rx, ry, rz)
    * @return Fehlercode
    */
    public int PhotoelectricSensorTCPCalibration(string luaPath, DescTran offset, out DescPose TCP);

Codebeispiel für Photoelektrische Sensor TCP-Kalibrierung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: csharp
    :linenos:

    public void TestPhotoelectricSensorTCPCalib()
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        DescTran offset = new DescTran( 10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, out TCP);
        Console.WriteLine($"PhotoelectricSensorTCPCalibration : {rtn}");
        Console.WriteLine($"Werkzeug-TCP Koordinaten: X={TCP.tran.x:F3}, Y={TCP.tran.y:F3}, Z={TCP.tran.z:F3}");
        Console.WriteLine($"Werkzeug-RPY Ausrichtung: RX={TCP.rpy.rx:F3}, RY={TCP.rpy.ry:F3}, RZ={TCP.rpy.rz:F3}");
    }

Globale Geschwindigkeit sofort einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Stellt die globale Geschwindigkeit sofort ein
    * @param [in] vel Geschwindigkeitsprozent, Bereich [0~100]
    * @return Fehlercode
    */
    public int SetWeaveOffsetRT(DescPose offset)