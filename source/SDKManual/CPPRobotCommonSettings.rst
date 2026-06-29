Allgemeine Roboter-Einstellungen
================================

.. toctree::
    :maxdepth: 5

Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
     * @param [in] point_num Punktnummer, Bereich [1~6]
     * @return Fehlercode
     */
    errno_t SetToolPoint(int point_num);

Werkzeugkoordinatensystem berechnen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Werkzeugkoordinatensystem berechnen
     * @param [out] tcp_pose Werkzeugkoordinatensystem
     * @return Fehlercode
     */
    errno_t ComputeTool(DescPose *tcp_pose);

Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
     * @param [in] point_num Punktnummer, Bereich [1~4]
     * @return Fehlercode
     */
    errno_t SetTcp4RefPoint(int point_num);

Werkzeugkoordinatensystem berechnen (Vier-Punkt-Methode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Werkzeugkoordinatensystem berechnen (Vier-Punkt-Methode)
     * @param [out] tcp_pose Werkzeugkoordinatensystem
     * @return Fehlercode
     */
    errno_t ComputeTcp4(DescPose *tcp_pose);

Werkzeugkoordinatensystem basierend auf Punktdaten berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Werkzeugkoordinatensystem basierend auf Punktdaten berechnen
     * @param [in] method Berechnungsmethode; 0-Vier-Punkt-Methode; 1-Sechs-Punkt-Methode
     * @param [in] pos Array von Gelenkpositionen, Länge 4 bei Vier-Punkt-Methode, Länge 6 bei Sechs-Punkt-Methode
     * @param [out] coord Ergebnis des Werkzeugkoordinatensystems
     * @return Fehlercode
     */
    errno_t ComputeToolCoordWithPoints(int method, JointPos pos[], DescPose& coord);

Werkzeugkoordinatensystem einstellen
+++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Werkzeugkoordinatensystem einstellen
     * @param [in] id Koordinatensystemnummer, Bereich [0~14]
     * @param [in] coord Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
     * @param [in] type 0-Werkzeugkoordinatensystem, 1-Sensorkoordinatensystem
     * @param [in] install Einbauort, 0-Roboterflansch, 1-extern
     * @param [in] toolID Werkzeug-ID
     * @param [in] loadNum Lastnummer
     * @return Fehlercode
     */
    errno_t SetToolCoord(int id, DescPose *coord, int type, int install, int toolID, int loadNum);

Werkzeugkoordinatensystem in Liste einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Werkzeugkoordinatensystem in Liste einstellen
     * @param [in] id Koordinatensystemnummer, Bereich [0~14]
     * @param [in] coord Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
     * @param [in] type 0-Werkzeugkoordinatensystem, 1-Sensorkoordinatensystem
     * @param [in] install Einbauort, 0-Roboterflansch, 1-extern
     * @param [in] loadNum Lastnummer
     * @return Fehlercode
     */
    errno_t SetToolList(int id, DescPose *coord, int type, int install, int loadNum);

Aktuelles Werkzeugkoordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Aktuelles Werkzeugkoordinatensystem abrufen
    * @param [in] flag 0-blockierend, 1-nicht blockierend
    * @param [out] desc_pos Pose des Werkzeugkoordinatensystems
    * @return Fehlercode
    */
    errno_t GetTCPOffset(uint8_t flag, DescPose *desc_pos);

Codebeispiel für Roboter-Werkzeugkoordinatensystem-Operationen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestTCPCompute(void)
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
         DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
         JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
         DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
         JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
         DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
         JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
         DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
         JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
         DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
         JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
         DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
         JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         JointPos posJ[6] = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
         DescPose coordRtn = {};
         rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);
         printf("ComputeToolCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(3);
         robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(4);
         robot.MoveJ(&p5Joint, &p5Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(5);
         robot.MoveJ(&p6Joint, &p6Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(6);
         rtn = robot.ComputeTool(&coordRtn);
         printf("6 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetToolList(1, &coordRtn, 0, 0, 0);
         robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(3);
         robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(4);
         rtn = robot.ComputeTcp4(&coordRtn);
         printf("4 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetToolCoord(2, &coordRtn, 0, 0, 1, 0);
         DescPose getCoord = {};
         rtn = robot.GetTCPOffset(0, &getCoord);
         printf("GetTCPOffset    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.CloseRPC();
         return 0;
     }

Externen Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Externen Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
     * @param [in] point_num Punktnummer, Bereich [1~4]
     * @return Fehlercode
     */
    errno_t SetExTCPPoint(int point_num);

Externes Werkzeugkoordinatensystem berechnen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Externes Werkzeugkoordinatensystem berechnen
     * @param [out] tcp_pose Externes Werkzeugkoordinatensystem
     * @return Fehlercode
     */
    errno_t ComputeExTCF(DescPose *tcp_pose);

Externes Werkzeugkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Externes Werkzeugkoordinatensystem einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [0~14]
    * @param [in] etcp Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
    * @param [in] etool (vorläufig unbestimmt)
    * @return Fehlercode
    */
    errno_t SetExToolCoord(int id, DescPose *etcp, DescPose *etool);

Externes Werkzeugkoordinatensystem in Liste einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Externes Werkzeugkoordinatensystem in Liste einstellen
    * @param [in] id Koordinatensystemnummer, Bereich [0~14]
    * @param [in] etcp Pose des Werkzeugmittelpunkts relativ zum Flanschmittelpunkt
    * @param [in] etool (vorläufig unbestimmt)
    * @return Fehlercode
    */
    errno_t SetExToolList(int id, DescPose *etcp, DescPose *etool);

Codebeispiel für Roboter-externes Werkzeugkoordinatensystem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestExtCoord(void)
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
       DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
       JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
       DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
       JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
       DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
       JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
       ExaxisPos exaxisPos(0, 0, 0, 0);
       DescPose offdese(0, 0, 0, 0, 0, 0);
       DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
       DescPose coordRtn = {};
       robot.MoveJ(&p1Joint, &p1Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.SetExTCPPoint(1);
       robot.MoveJ(&p2Joint, &p2Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.SetExTCPPoint(2);
       robot.MoveJ(&p3Joint, &p3Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.SetExTCPPoint(3);
       rtn = robot.ComputeExTCF(&coordRtn);
       printf("ComputeExTCF          %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
       robot.SetExToolCoord(1, &coordRtn, &offdese);
       robot.SetExToolList(1, &coordRtn, &offdese);
       robot.CloseRPC();
       return 0;
    }

Werkstück-Referenzpunkt einstellen - Drei-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Werkstück-Referenzpunkt einstellen - Drei-Punkt-Methode
     * @param [in] point_num Punktnummer, Bereich [1~3]
     * @return Fehlercode
     */
    errno_t SetWObjCoordPoint(int point_num);

Werkstückkoordinatensystem berechnen
+++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Werkstückkoordinatensystem berechnen
     * @param [in] method Berechnungsmethode 0: Ursprung-x-Achse-z-Achse  1: Ursprung-x-Achse-xy-Ebene
     * @param [in] refFrame Referenzkoordinatensystem
     * @param [out] wobj_pose Werkstückkoordinatensystem
     * @return Fehlercode
     */
    errno_t ComputeWObjCoord(int method, int refFrame, DescPose *wobj_pose);

Werkstückkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Werkstückkoordinatensystem einstellen
     * @param [in] id Koordinatensystemnummer, Bereich [0~14]
     * @param [in] coord Pose des Werkstückkoordinatensystems relativ zum Flanschmittelpunkt
     * @param [in] refFrame Referenzkoordinatensystem
     * @return Fehlercode
     */
    errno_t SetWObjCoord(int id, DescPose *coord, int refFrame);

Werkstückkoordinatensystem in Liste einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Werkstückkoordinatensystem in Liste einstellen
     * @param [in] id Koordinatensystemnummer, Bereich [0~14]
     * @param [in] coord Pose des Werkstückkoordinatensystems relativ zum Flanschmittelpunkt
     * @param [in] refFrame Referenzkoordinatensystem
     * @return Fehlercode
     */
    errno_t SetWObjList(int id, DescPose *coord, int refFrame);

Werkstückkoordinatensystem basierend auf Punktdaten berechnen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Werkstückkoordinatensystem basierend auf Punktdaten berechnen
     * @param [in] method Berechnungsmethode; 0: Ursprung-x-Achse-z-Achse  1: Ursprung-x-Achse-xy-Ebene
     * @param [in] pos Array von drei TCP-Positionen (kartesisch)
     * @param [in] refFrame Referenzkoordinatensystem
     * @param [out] coord Ergebnis des Werkzeugkoordinatensystems (hier Werkstückkoordinatensystem)
     * @return Fehlercode
     */
    errno_t ComputeWObjCoordWithPoints(int method, DescPose pos[], int refFrame, DescPose& coord);

Aktuelles Werkstückkoordinatensystem abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Aktuelles Werkstückkoordinatensystem abrufen
    * @param [in] flag 0-blockierend, 1-nicht blockierend
    * @param [out] desc_pos Pose des Werkstückkoordinatensystems
    * @return Fehlercode
    */
    errno_t GetWObjOffset(uint8_t flag, DescPose *desc_pos);

Codebeispiel für Roboter-Werkstückkoordinatensystem-Operationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestWobjCoord(void)
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
         DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
         JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
         DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
         JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
         DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
         JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
         DescPose coordRtn = {};
         rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);
         printf("ComputeWObjCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.MoveJ(&p1Joint, &p1Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(3);
         rtn = robot.ComputeWObjCoord(1, 0, &coordRtn);
         printf("ComputeWObjCoord                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetWObjCoord(1, &coordRtn, 0);
         robot.SetWObjList(1, &coordRtn, 0);
         DescPose getWobjDesc = {};
         rtn = robot.GetWObjOffset(0, &getWobjDesc);
         printf("GetWObjOffset                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.CloseRPC();
         return 0;
     }

Globale Geschwindigkeit einstellen
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Globale Geschwindigkeit einstellen
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @return Fehlercode
    */
    errno_t SetSpeed(int vel);

Roboter-Beschleunigung einstellen
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Roboter-Beschleunigung einstellen
     * @param [in] acc Roboter-Beschleunigungsprozentsatz
     * @return Fehlercode
     */
    errno_t SetOaccScale(double acc);

Standard-Roboter-Geschwindigkeit abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Standard-Roboter-Geschwindigkeit abrufen
    * @param [out] vel Geschwindigkeit [mm/s]
    * @return Fehlercode
    */
    errno_t GetDefaultTransVel(float *vel);

Endeffektor-Lastgewicht einstellen
+++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Endeffektor-Lastgewicht einstellen
     * @param [in] loadNum Lastnummer
     * @param [in] weight Lastgewicht [kg]
     * @return Fehlercode
     */
    errno_t SetLoadWeight(int loadNum = 0, float weight);

Endeffektor-Lastschwerpunkt einstellen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Lastschwerpunkt einstellen
    * @param [in] loadNum Lastnummer
    * @param [in] coord Schwerpunktkoordinaten [mm]
    * @return Fehlercode
    */
    errno_t SetLoadCoord(int loadNum, DescTran* coord);

Aktuelles Lastgewicht abrufen
++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Aktuelles Lastgewicht abrufen
    * @param [in] flag 0-blockierend, 1-nicht blockierend
    * @param [out] weight Lastgewicht [kg]
    * @return Fehlercode
    */
    errno_t GetTargetPayload(uint8_t flag, float *weight);

Aktuellen Lastschwerpunkt abrufen
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Aktuellen Lastschwerpunkt abrufen
    * @param [in] flag 0-blockierend, 1-nicht blockierend
    * @param [out] cog Lastschwerpunkt [mm]
    * @return Fehlercode
    */
    errno_t GetTargetPayloadCog(uint8_t flag, DescTran *cog);

Roboter-Einbauart einstellen
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-Einbauart einstellen
    * @param [in] install Einbauart, 0-Boden, 1-Wand, 2-Decke
    * @return Fehlercode
    */
    errno_t SetRobotInstallPos(uint8_t install);

Roboter-Einbauwinkel einstellen (freie Montage)
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-Einbauwinkel einstellen (freie Montage)
    * @param [in] yangle Neigungswinkel
    * @param [in] zangle Rotationswinkel
    * @return Fehlercode
    */
    errno_t SetRobotInstallAngle(double yangle, double zangle);

Roboter-Einbauwinkel abrufen
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-Einbauwinkel abrufen
    * @param [out] yangle Neigungswinkel
    * @param [out] zangle Rotationswinkel
    * @return Fehlercode
    */
    errno_t GetRobotInstallAngle(float *yangle, float *zangle);

Systemvariablenwert einstellen
++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Systemvariablenwert einstellen
    * @param [in] id Variablennummer, Bereich [1~20]
    * @param [in] value Variablenwert
    * @return Fehlercode
    */
    errno_t SetSysVarValue(int id, float value);

Systemvariablenwert abrufen
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Systemvariablenwert abrufen
    * @param [in] id Systemvariablennummer, Bereich [1~20]
    * @param [out] value Systemvariablenwert
    * @return Fehlercode
    */
    errno_t GetSysVarValue(int id, float *value);

Codebeispiel für allgemeine Roboter-Einstellungen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestLoadInstall(void)
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
         for (int i = 1; i < 100; i++)
         {
             robot.SetSpeed(i);
             robot.SetOaccScale(i);
             robot.Sleep(30);
         }
         float defaultVel = 0.0;
         robot.GetDefaultTransVel(&defaultVel);
         printf("GetDefaultTransVel is %f\n", defaultVel);
         for (int i = 1; i < 21; i++)
         {
             robot.SetSysVarValue(i, i + 0.5);
             robot.Sleep(100);
         }
         for (int i = 1; i < 21; i++)
         {
             float value = 0;
             robot.GetSysVarValue(i, &value);
             printf("sys value  %d is :%f\n", i, value);
             robot.Sleep(100);
         }
         robot.SetLoadWeight(0, 2.5);
         DescTran loadCoord = {};
         loadCoord.x = 3.0;
         loadCoord.y = 4.0;
         loadCoord.z = 5.0;
         robot.SetLoadCoord(&loadCoord);
         robot.Sleep(1000);
         float getLoad = 0.0;
         robot.GetTargetPayload(0, &getLoad);
         DescTran getLoadTran = {};
         robot.GetTargetPayloadCog(0, &getLoadTran);
         printf("get load is %f; get load cog is %f %f %f\n", getLoad, getLoadTran.x, getLoadTran.y, getLoadTran.z);
         robot.SetRobotInstallPos(0);
         robot.SetRobotInstallAngle(15.0, 25.0);
         float anglex = 0.0;
         float angley = 0.0;
         robot.GetRobotInstallAngle(&anglex, &angley);
         printf("GetRobotInstallAngle x:  %f;  y:  %f\n", anglex, angley);
         robot.CloseRPC();
         return 0;
     }

Gelenk-Reibungskompensation ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensation ein-/ausschalten
    * @param [in] state 0-aus, 1-an
    * @return Fehlercode
    */
    errno_t FrictionCompensationOnOff(uint8_t state);

Gelenk-Reibungskompensationskoeffizienten einstellen - Bodenmontage
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - Bodenmontage
    * @param [in] coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return Fehlercode
    */
    errno_t SetFrictionValue_level(float coeff[6]);

Gelenk-Reibungskompensationskoeffizienten einstellen - Wandmontage
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - Wandmontage
    * @param [in] coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return Fehlercode
    */
    errno_t SetFrictionValue_wall(float coeff[6]);

Gelenk-Reibungskompensationskoeffizienten einstellen - Deckenmontage
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - Deckenmontage
    * @param [in] coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return Fehlercode
    */
    errno_t SetFrictionValue_ceiling(float coeff[6]);

Gelenk-Reibungskompensationskoeffizienten einstellen - freie Montage
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Reibungskompensationskoeffizienten einstellen - freie Montage
    * @param [in] coeff Kompensationskoeffizienten für sechs Gelenke, Bereich [0~1]
    * @return Fehlercode
    */
    errno_t SetFrictionValue_freedom(float coeff[6]);

Codebeispiel zum Einstellen der Gelenk-Reibungskompensation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFriction(void)
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
       float lcoeff[6] = { 0.9,0.9,0.9,0.9,0.9,0.9 };
       float wcoeff[6] = { 0.4,0.4,0.4,0.4,0.4,0.4 };
       float ccoeff[6] = { 0.6,0.6,0.6,0.6,0.6,0.6 };
       float fcoeff[6] = { 0.5,0.5,0.5,0.5,0.5,0.5 };
       rtn = robot.FrictionCompensationOnOff(1);
       printf("FrictionCompensationOnOff rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_level(lcoeff);
       printf("SetFrictionValue_level rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_wall(wcoeff);
       printf("SetFrictionValue_wall rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_ceiling(ccoeff);
       printf("SetFrictionValue_ceiling rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_freedom(fcoeff);
       printf("SetFrictionValue_freedom rtn is %d\n", rtn);
       robot.CloseRPC();
       return 0;
    }

Roboter-Fehlercode abfragen
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Roboter-Fehlercode abfragen
     * @param [out] maincode Hauptfehlercode
     * @param [out] subcode Unterfehlercode
     * @return Fehlercode
     */
    errno_t GetRobotErrorCode(int *maincode, int *subcode);

Fehlerstatus löschen
++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fehlerstatus löschen
    * @return Fehlercode
    */
    errno_t ResetAllError();

Codebeispiel zum Abrufen und Löschen von Roboter-Fehlerstatus
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetError(void)
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
       int maincode, subcode;
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.ResetAllError();
       robot.Sleep(1000);
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.CloseRPC();
       return 0;
    }

Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens einstellen
    * @param [in] enable 0-Überwachung deaktivieren; 1-Überwachung aktivieren
    * @param [in] period Überwachungszyklus (s), Bereich 1-100
    * @return Fehlercode
    */
    errno_t SetWideBoxTempFanMonitorParam(int enable, int period);

Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Überwachungsparameter für Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens abrufen
    * @param [out] enable 0-Überwachung deaktiviert; 1-Überwachung aktiviert
    * @param [out] period Überwachungszyklus (s), Bereich 1-100
    * @return Fehlercode
    */
    errno_t GetWideBoxTempFanMonitorParam(int &enable, int &period);

Codebeispiel zum Abrufen von Temperatur und Lüfterstrom des Weitspannungs-Steuerkastens
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestWideVoltageCtrlBoxtemp(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         printf("robot rpc rtn is %d\n", rtn);
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         robot.SetWideBoxTempFanMonitorParam(1, 2);
         int enable = 0;
         int period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
         printf("SetWideBoxTempFanMonitorParam rtn is %d\n", rtn);
         enable = 0;
         period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         robot.CloseRPC();
         robot.Sleep(2000);
         return 0;
     }

Fokus-Kalibrierungsergebnis berechnen
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fokus-Kalibrierungsergebnis berechnen
    * @param [in] pointNum Anzahl der Kalibrierungspunkte
    * @param [out] resultPos Kalibriertes XYZ-Ergebnis
    * @param [out] accuracy Kalibriergenauigkeit (Fehler)
    * @return Fehlercode
    */
    errno_t ComputeFocusCalib(int pointNum, DescTran& resultPos, float& accuracy);

Fokuskoordinaten einstellen
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fokuskoordinaten einstellen
    * @param [in] pos Fokuskoordinaten XYZ
    * @return Fehlercode
    */
    errno_t SetFocusPosition(DescTran pos);

Fokusverfolgung starten
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fokusverfolgung starten
    * @param [in] kp Proportionalparameter, Standard 50.0
    * @param [in] kpredict Vorsteuerungsparameter, Standard 19.0
    * @param [in] aMax Maximale Winkelbeschleunigungsbegrenzung [°/s²], Standard 1440
    * @param [in] vMax Maximale Winkelgeschwindigkeitsbegrenzung [°/s], Standard 180
    * @param [in] type Ausrichtung der X-Achse (0-Referenzeingangsvektor; 1-horizontal; 2-vertikal)
    * @return Fehlercode
    */
    errno_t FocusStart(double kp, double kpredict, double aMax, double vMax, int type);

Fokusverfolgung stoppen
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fokusverfolgung stoppen
    * @return Fehlercode
    */
    errno_t FocusEnd();

Codebeispiel für Roboter-Fokusverfolgung
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFocus()
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
      DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
      JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
      DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
      JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
      DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
      JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
      DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
      JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
      DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
      JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
      DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
      JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 100, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(1);
      robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(2);
      robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(3);
      robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(4);
      DescPose coordRtn = {};
      rtn = robot.ComputeTcp4(&coordRtn);
      printf("4 Point ComputeTool    %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
      robot.SetToolCoord(1, &coordRtn, 0, 0, 1, 0);
      robot.GetForwardKin(&p1Joint, &p1Desc);
      robot.GetForwardKin(&p2Joint, &p2Desc);
      robot.GetForwardKin(&p3Joint, &p3Desc);
      robot.SetFocusCalibPoint(1, p1Desc);
      robot.SetFocusCalibPoint(2, p2Desc);
      robot.SetFocusCalibPoint(3, p3Desc);
      DescTran resultPos = {};
      float accuracy = 0.0;
      rtn = robot.ComputeFocusCalib(3, resultPos, accuracy);
      printf("ComputeFocusCalib coord is %d %f %f %f accuracy is %f\n", rtn, resultPos.x, resultPos.y, resultPos.z, accuracy);
      rtn = robot.SetFocusPosition(resultPos);
      robot.GetForwardKin(&p5Joint, &p5Desc);
      robot.GetForwardKin(&p6Joint, &p6Desc);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusStart(50, 19, 710, 90, 0);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusEnd();
      robot.CloseRPC();
      return 0;
    }

Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung aktivieren
    * @param [in] status 0-deaktivieren; 1-aktivieren
    * @return Fehlercode
    */
    errno_t JointSensitivityEnable(int status);

Gelenk-Drehmomentsensor-Empfindlichkeitsdaten erfassen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Empfindlichkeitsdaten erfassen
    * @return Fehlercode
    */
    errno_t JointSensitivityCollect();

Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ergebnis der Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung abrufen
    * @param [out] calibResult Empfindlichkeit j1~j6 [0-1]
    * @param [out] linearity Linearität j1~j6 [0-1]
    * @return Fehlercode
    */
    errno_t JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Gelenk-Drehmomentsensor-Hysteresefehler abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Hysteresefehler abrufen
    * @param [out] hysteresisError Hysteresefehler j1~j6
    * @return Fehlercode
    */
    errno_t JointHysteresisError(double hysteresisError[6]);

Gelenk-Drehmomentsensor-Wiederholgenauigkeit abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Drehmomentsensor-Wiederholgenauigkeit abrufen
    * @param [out] repeatability Wiederholgenauigkeit j1~j6
    * @return Fehlercode
    */
    errno_t JointRepeatability(double repeatability[6]);

Gelenk-Kraftsensor-Parameter einstellen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Kraftsensor-Parameter einstellen (für Impedanzregelung)
    * @param [in] M Massenkoeffizienten J1-J6 [0.001 ~ 10]
    * @param [in] B Dämpfungskoeffizienten J1-J6 [0.001 ~ 10]
    * @param [in] K Steifigkeitskoeffizienten J1-J6 [0.001 ~ 10]
    * @param [in] threshold Kraftregelungsschwellwerte [Nm]
    * @param [in] sensitivity Empfindlichkeit [Nm/V], [0 ~ 10]
    * @param [in] setZeroFlag Funktionsaktivierungs-Flag; 0-deaktivieren; 1-aktivieren; 2-Nullpunkt an Position 1 aufzeichnen; 3-Nullpunkt an Position 2 aufzeichnen
    * @return Fehlercode
    */
    errno_t SetAdmittanceParams(double M[6], double B[6], double K[6], double threshold[6], double sensitivity[6], int setZeroFlag);

Codebeispiel für automatische Gelenk-Drehmomentsensor-Empfindlichkeitskalibrierung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSensitivityCalib()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = {};
        robot.GetActualJointPosDegree(0, &curJPos);
        ExaxisPos epos = { 0,0,0,0 };
        DescPose offset_pos = { 0,0,0,0,0,0 };
        JointPos jointPos1 = { curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos1 = {};
        robot.GetForwardKin(&jointPos1, &descPos1);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 = { curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos2 = {};
        robot.GetForwardKin(&jointPos2, &descPos2);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = { curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos3 = {};
        robot.GetForwardKin(&jointPos3, &descPos3);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = { curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos4 = {};
        robot.GetForwardKin(&jointPos4, &descPos4);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = { curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos5 = {};
        robot.GetForwardKin(&jointPos5, &descPos5);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = { curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos6 = {};
        robot.GetForwardKin(&jointPos6, &descPos6);
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = { curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos7 = {};
        robot.GetForwardKin(&jointPos7, &descPos7);
        robot.MoveJ(&jointPos7, &descPos7, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //-------------------
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double calibResult[6] = { 0.0 };
        double linearity[6] = { 0.0 };
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n", 
            calibResult[0], calibResult[1], calibResult[2], 
            calibResult[3], calibResult[4], calibResult[5], 
            linearity[0], linearity[1], linearity[2],
            linearity[3], linearity[4], linearity[5]);
        double hysteresisError[6] = { 0.0 };
        rtn = robot.JointHysteresisError(hysteresisError);
        printf("JointHysteresisError result is %f %f %f %f %f %f\n",
            hysteresisError[0], hysteresisError[1], hysteresisError[2],
            hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double repeatability[6] = { 0.0 };
        rtn = robot.JointRepeatability(repeatability);
        printf("JointRepeatability result is %f %f %f %f %f %f\n",
            repeatability[0], repeatability[1], repeatability[2],
            repeatability[3], repeatability[4], repeatability[5]);
        double M[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double B[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double K[6] = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double threshold[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        printf("SetAdmittanceParams rtn is %d\n", rtn);
        robot.CloseRPC();
    }

Fehlerzähler der 8 Slave-Ports abrufen
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fehlerzähler der 8 Slave-Ports abrufen
    * @param [out] inRecvErr Empfangsfehler (Eingang) für 8 Ports
    * @param [out] inCRCErr CRC-Fehler (Eingang) für 8 Ports
    * @param [out] inTransmitErr Übertragungsfehler (Eingang) für 8 Ports
    * @param [out] inLinkErr Link-Fehler (Eingang) für 8 Ports
    * @param [out] outRecvErr Empfangsfehler (Ausgang) für 8 Ports
    * @param [out] outCRCErr CRC-Fehler (Ausgang) für 8 Ports
    * @param [out] outTransmitErr Übertragungsfehler (Ausgang) für 8 Ports
    * @param [out] outLinkErr Link-Fehler (Ausgang) für 8 Ports
    * @return Fehlercode
    */
    errno_t GetSlavePortErrCounter(int inRecvErr[8], int inCRCErr[8], int inTransmitErr[8], int inLinkErr[8], int outRecvErr[8], int outCRCErr[8], int outTransmitErr[8], int outLinkErr[8]);

Slave-Port-Fehlerzähler zurücksetzen
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Slave-Port-Fehlerzähler zurücksetzen
    * @param [in] slaveID Slave-Nummer 0~7
    * @return Fehlercode
    */
    errno_t SlavePortErrCounterClear(int slaveID);

Codebeispiel zum Abrufen der Slave-Port-Fehlerzähler
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSlavePortErr()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        int inRecvErr[8] = {0.0}; 
        int inCRCErr[8] = { 0.0 };
        int inTransmitErr[8] = { 0.0 };
        int inLinkErr[8] = { 0.0 };
        int outRecvErr[8] = { 0.0 };
        int outCRCErr[8] = { 0.0 };
        int outTransmitErr[8] = { 0.0 };
        int outLinkErr[8] = { 0.0 };
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
            outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
        return 0;
    }

Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse einstellen
    * @param [in] radio Geschwindigkeits-Vorsteuerkoeffizienten für 6 Achsen
    * @return Fehlercode
    */
    errno_t SetVelFeedForwardRatio(double radio[6]);

Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Geschwindigkeits-Vorsteuerkoeffizienten für jede Achse abrufen
    * @param [out] radio Geschwindigkeits-Vorsteuerkoeffizienten für 6 Achsen
    * @return Fehlercode
    */
    errno_t GetVelFeedForwardRatio(double radio[6]);

Codebeispiel für Geschwindigkeits-Vorsteuerkoeffizienten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestVelFeedForwardRatio()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        double setRadio[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double getRadio[6] = { 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
        return 0;
    }

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-RPY berechnen
    * @param [in] Btool Roboter-Kartesische Position (Pose)
    * @param [in] Etool Aktueller Wert des Werkzeugkoordinatensystems
    * @param [in] sensor Aktueller Wert des Sensorkoordinatensystems (vorübergehend nicht freigegeben)
    * @param [in] radius Radius der Kreisbewegung [mm] (vorübergehend nicht freigegeben)
    * @param [in] dz Bewegungsdistanz entlang der negativen Z-Achse des Basiskoordinatensystems; wenn dz = 10000, gibt die Funktion direkt das Werkzeug-RPY zurück
    * @param [out] TCPRPY Berechnete Werkzeug-RPY-Werte
    * @return Fehlercode
    */
    errno_t TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, Rpy& TCPRPY);

Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Werkzeug-XYZ berechnen
    * @param [in] select 0-Werkzeug-TCP berechnen; 1-Sensorursprung berechnen; 2-Sensorausrichtung berechnen; 3-Werkzeug-TCP direkt zurückgeben; 4-Aktuelles Werkstück- und Werkzeugkoordinatensystem aufzeichnen
    * @param [in] originDirection 0-X-Richtung; 1-Y-Richtung; 2-Z-Richtung
    * @param [in] pos1 Roboter-Kartesische Position 1
    * @param [in] pos2 Roboter-Kartesische Position 2
    * @param [in] pos3 Roboter-Kartesische Position 3
    * @param [in] pos4 Roboter-Kartesische Position 4
    * @param [out] TCP Berechnete Werkzeug-XYZ-Werte
    * @return Fehlercode
    */
    errno_t TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2, DescTran pos3, DescTran pos4, DescTran& TCP);

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position starten
    * @return Fehlercode
    */
    errno_t TCPRecordFlangePosStart();

Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position stoppen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Aufzeichnung der Flanschmittelpunkt-Position stoppen
    * @return Fehlercode
    */
    errno_t TCPRecordFlangePosEnd();

Photoelektrischer Sensor TCP-Kalibrierung - Position des Werkzeugmittelpunkts abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung - Position des Werkzeugmittelpunkts abrufen
    * @param [out] TCP Position des Werkzeugmittelpunkts (x,y,z)
    * @return Fehlercode
    */
    errno_t TCPGetRecordFlangePos(DescTran& TCP);

Photoelektrischer Sensor TCP-Kalibrierung (automatisiert)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Photoelektrischer Sensor TCP-Kalibrierung (automatisiert)
    * @param [in] luaPath Pfad zum automatischen Kalibrierungs-Lua-Programm: "FR_CalibrateTheToolTcp.lua"; 
    * @param [in] offset Versatz der Teachpunkte (x,y,z) [mm]
    * @param [out] TCP Kalibriertes Werkzeugkoordinatensystem (x,y,z,rx,ry,rz)
    * @return Fehlercode
    */
    errno_t PhotoelectricSensorTCPCalibration(std::string luaPath, DescTran offset, DescPose& TCP);

Codebeispiel für photoelektrische Sensor TCP-Kalibrierung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestPhotoelectricSensorTCPCalib(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescTran offset = { 10.0, 10.0, 3.0 };
        DescPose TCP = {};
        rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, TCP);
        printf("PhotoelectricSensorTCPCalibration rtn is  %d %f %f %f %f %f %f \n", rtn, TCP.tran.x, TCP.tran.y, TCP.tran.z, TCP.rpy.rx, TCP.rpy.ry, TCP.rpy.rz);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
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
    errno_t SetSpeedInstant(int vel);    