Roboter-Peripherie
==================

.. toctree::
    :maxdepth: 5

Greifer konfigurieren
+++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Greifer konfigurieren
    * @param [in] company Greiferhersteller (zur Festlegung)
    * @param [in] device Gerätenummer, vorübergehend nicht verwendet, Standard 0
    * @param [in] softvesion Softwareversionsnummer, vorübergehend nicht verwendet, Standard 0
    * @param [in] bus Position des Geräts am Endeffektor-Bus, vorübergehend nicht verwendet, Standard 0
    * @return Fehlercode
    */
    errno_t SetGripperConfig(int company, int device, int softvesion, int bus);

Greiferkonfiguration abrufen
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Greiferkonfiguration abrufen
    * @param [in] company Greiferhersteller (zur Festlegung)
    * @param [in] device Gerätenummer, vorübergehend nicht verwendet, Standard 0
    * @param [in] softvesion Softwareversionsnummer, vorübergehend nicht verwendet, Standard 0
    * @param [in] bus Position des Geräts am Endeffektor-Bus, vorübergehend nicht verwendet, Standard 0
    * @return Fehlercode
    */
    errno_t GetGripperConfig(int *company, int *device, int *softvesion, int *bus);

Greifer aktivieren
++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Greifer aktivieren
    * @param [in] index Greifernummer
    * @param [in] act 0-Zurücksetzen, 1-Aktivieren
    * @return Fehlercode
    */
    errno_t ActGripper(int index, uint8_t act);

Greifer steuern
+++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Greifer steuern
     * @param [in] index Greifernummer
     * @param [in] pos Positionsprozentsatz, Bereich [0~100]
     * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
     * @param [in] force Drehmomentprozentsatz, Bereich [0~100]
     * @param [in] max_time Maximale Wartezeit, Bereich [0~30000], [ms]
     * @param [in] block 0-blockierend, 1-nicht blockierend
     * @param [in] type Greifertyp: 0-Parallelgreifer; 1-Rotationsgreifer
     * @param [in] rotNum Rotationsanzahl (Umdrehungen)
     * @param [in] rotVel Rotationsgeschwindigkeitsprozentsatz [0-100]
     * @param [in] rotTorque Rotationsdrehmomentprozentsatz [0-100]
     * @return Fehlercode
     */
    errno_t MoveGripper(int index, int pos, int vel, int force, int max_time, uint8_t block, int type, double rotNum, int rotVel, int rotTorque);

Greifer-Bewegungsstatus abrufen
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Greifer-Bewegungsstatus abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] status 0-Bewegung nicht abgeschlossen, 1-Bewegung abgeschlossen
     * @return Fehlercode
     */
    errno_t GetGripperMotionDone(uint16_t *fault, uint8_t *status);

Greifer-Aktivierungsstatus abrufen
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Greifer-Aktivierungsstatus abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] status Bit0~Bit15 entsprechen Greifernummern 0~15, Bit=0 nicht aktiviert, Bit=1 aktiviert
     * @return Fehlercode
     */
    errno_t GetGripperActivateStatus(uint16_t *fault, uint16_t *status);

Greiferposition abrufen
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Greiferposition abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] position Positionsprozentsatz, Bereich 0~100%
     * @return Fehlercode
     */
    errno_t GetGripperCurPosition(uint16_t *fault, uint8_t *position);

Greifergeschwindigkeit abrufen
+++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Greifergeschwindigkeit abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] speed Geschwindigkeitsprozentsatz, Bereich 0~100%
     * @return Fehlercode
     */
    errno_t GetGripperCurSpeed(uint16_t *fault, int8_t *speed);

Greiferstrom abrufen
+++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Greiferstrom abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] current Stromprozentsatz, Bereich 0~100%
     * @return Fehlercode
     */
    errno_t GetGripperCurCurrent(uint16_t *fault, int8_t *current);

Greiferspannung abrufen
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Greiferspannung abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] voltage Spannung, Einheit 0.1V
     * @return Fehlercode
     */
    errno_t GetGripperVoltage(uint16_t *fault, int *voltage);

Greifertemperatur abrufen
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Greifertemperatur abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] temp Temperatur [°C]
     * @return Fehlercode
     */
    errno_t GetGripperTemp(uint16_t *fault, int *temp);

Vor-Greifpunkt berechnen (visuell)
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Vor-Greifpunkt berechnen (visuell)
     * @param [in] desc_pos Kartesische Pose des Greifpunkts
     * @param [in] zlength Z-Achsen-Versatz [mm]
     * @param [in] zangle Rotationsversatz um die Z-Achse [°]
     * @param [out] pre_pos Berechneter Vor-Greifpunkt
     * @return Fehlercode
     */
    errno_t ComputePrePick(DescPose *desc_pos, double zlength, double zangle, DescPose *pre_pos);

Rückzugspunkt berechnen (visuell)
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Rückzugspunkt berechnen (visuell)
     * @param [in] desc_pos Kartesische Pose des Rückzugspunkts
     * @param [in] zlength Z-Achsen-Versatz [mm]
     * @param [in] zangle Rotationsversatz um die Z-Achse [°]
     * @param [out] post_pos Berechneter Rückzugspunkt
     * @return Fehlercode
     */
    errno_t ComputePostPick(DescPose *desc_pos, double zlength, double zangle, DescPose *post_pos);

Codebeispiel für Roboter-Greiferoperationen
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGripper(void)
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
      int company = 4;
      int device = 0;
      int softversion = 0;
      int bus = 2;
      int index = 2;
      int act = 0;
      int max_time = 30000;
      uint8_t block = 0;
      uint8_t status;
      uint16_t fault;
      uint16_t active_status = 0;
      uint8_t current_pos = 0;
      int8_t current = 0;
      int voltage = 0;
      int temp = 0;
      int8_t speed = 0;
      robot.SetGripperConfig(company, device, softversion, bus);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.GetGripperConfig(&company, &device, &softversion, &bus);
      printf("gripper config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      act = 1;
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);
      robot.GetGripperMotionDone(&fault, &status);
      printf("motion status:%u,%u\n", fault, status);
      robot.GetGripperActivateStatus(&fault, &active_status);
      printf("gripper active fault is: %u, status is: %u\n", fault, active_status);
      robot.GetGripperCurPosition(&fault, &current_pos);
      printf("fault is:%u, current position is: %u\n", fault, current_pos);
      robot.GetGripperCurCurrent(&fault, &current);
      printf("fault is:%u, current current is: %d\n", fault, current);
      robot.GetGripperVoltage(&fault, &voltage);
      printf("fault is:%u, current voltage is: %d \n", fault, voltage);
      robot.GetGripperTemp(&fault, &temp);
      printf("fault is:%u, current temperature is: %d\n", fault, temp);
      robot.GetGripperCurSpeed(&fault, &speed);
      printf("fault is:%u, current speed is: %d\n", fault, speed);
      int retval = 0;
      DescPose prepick_pose = {};
      DescPose postpick_pose = {};
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.ComputePrePick(&p1Desc, 10, 0, &prepick_pose);
      printf("ComputePrePick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z, prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);
      retval = robot.ComputePostPick(&p2Desc, -10, 0, &postpick_pose);
      printf("ComputePostPick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z, postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Rotationsanzahl des Rotationsgreifers abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: 3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Rotationsanzahl des Rotationsgreifers abrufen
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] num Rotationsanzahl (Umdrehungen)
     * @return Fehlercode
     */
    errno_t GetGripperRotNum(uint16_t* fault, double* num);

Rotationsgeschwindigkeit des Rotationsgreifers abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Rotationsgeschwindigkeit des Rotationsgreifers abrufen (Prozentsatz)
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] speed Rotationsgeschwindigkeitsprozentsatz
     * @return Fehlercode
     */
    errno_t GetGripperRotSpeed(uint16_t* fault, int* speed);

Rotationsdrehmoment des Rotationsgreifers abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Rotationsdrehmoment des Rotationsgreifers abrufen (Prozentsatz)
     * @param [out] fault 0-kein Fehler, 1-Fehler
     * @param [out] torque Rotationsdrehmomentprozentsatz
     * @return Fehlercode
     */
    errno_t GetGripperRotTorque(uint16_t* fault, int* torque);

Codebeispiel zum Abrufen des Status eines Rotationsgreifers
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestRotGripperState(void)
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
      uint16_t fault = 0;
      double rotNum = 0.0;
      int rotSpeed = 0;
      int rotTorque = 0;
      robot.GetGripperRotNum(&fault, &rotNum);
      robot.GetGripperRotSpeed(&fault, &rotSpeed);
      robot.GetGripperRotTorque(&fault, &rotTorque);
      printf("gripper rot num : %lf, gripper rotSpeed : %d, gripper rotTorque : %d\n", rotNum, rotSpeed, rotTorque);
      robot.CloseRPC();
      return 0;
    }


Förderband starten/stoppen
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Förderband starten/stoppen
    * @param [in] status Status, 1-starten, 0-stoppen
    * @return Fehlercode
    */
    errno_t ConveyorStartEnd(uint8_t status);

IO-Erkennungspunkt aufzeichnen
+++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief IO-Erkennungspunkt aufzeichnen
    * @return Fehlercode
    */
    errno_t ConveyorPointIORecord();

Punkt A aufzeichnen
++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punkt A aufzeichnen
    * @return Fehlercode
    */
    errno_t ConveyorPointARecord();

Referenzpunkt aufzeichnen
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Referenzpunkt aufzeichnen
    * @return Fehlercode
    */
    errno_t ConveyorRefPointRecord();

Punkt B aufzeichnen
++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punkt B aufzeichnen
    * @return Fehlercode
    */
    errno_t ConveyorPointBRecord();

Förderband-Werkstück IO-Erkennung
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Förderband-Werkstück IO-Erkennung
    * @param [in] max_t Maximale Erkennungszeit [ms]
    * @return Fehlercode
    */
    errno_t ConveyorIODetect(int max_t);

Aktuelle Objektposition abrufen
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Aktuelle Objektposition abrufen
    * @param [in] mode Modus (z.B. 1-Tracking Greifen, 2-Tracking Bewegung)
    * @return Fehlercode
    */
    errno_t ConveyorGetTrackData(int mode);

Förderband-Tracking starten
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Förderband-Tracking starten
    * @param [in] status Status, 1-starten, 0-stoppen
    * @return Fehlercode
    */
    errno_t ConveyorTrackStart(uint8_t status);

Förderband-Tracking stoppen
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Förderband-Tracking stoppen
    * @return Fehlercode
    */
    errno_t ConveyorTrackEnd();

Förderbandparameter konfigurieren
++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Förderbandparameter konfigurieren
    * @param [in] para[0] Encoderkanal 1~2
    * @param [in] para[1] Impulse pro Encoderumdrehung
    * @param [in] para[2] Vorschubweg des Förderbands pro Encoderumdrehung [mm]
    * @param [in] para[3] Werkstückkoordinatennummer (für Tracking-Bewegung, bei Tracking-Greifen/TPD-Tracking auf 0 setzen)
    * @param [in] para[4] Mit Vision gekoppelt? 0 nein, 1 ja
    * @param [in] para[5] Geschwindigkeitsverhältnis (für Förderband-Tracking-Greifen Option (1-100)), Standard 1 für andere Optionen
    * @param [in] followType Tracking-Bewegungstyp: 0-Tracking-Bewegung; 1-Nachlauf-Bewegung
    * @param [in] startDis Für Nachlauf-Greifen erforderlich: Startabstand des Trackings. -1: automatische Berechnung (Nachlauf startet, wenn Werkstück unter Roboter ist). Einheit mm, Standard 0
    * @param [in] endDis Für Nachlauf-Greifen erforderlich: Endabstand des Trackings. Einheit mm, Standard 100
    * @return Fehlercode
    */
    errno_t ConveyorSetParam(float para[6], int followType = 0, int startDis = 0, int endDis = 100);

Förderband-Greifpunktkompensation
++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Förderband-Greifpunktkompensation einstellen
     * @param [in] cmp Kompensationsposition double[3]{x, y, z} [mm]
     * @return Fehlercode
     */
    errno_t ConveyorCatchPointComp(double cmp[3]);

Förderband-Linearbewegung (Tracking)
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Förderband-Linearbewegung (Tracking)
    * @param [in] name Name des Bewegungspunkts (z.B. "cvrCatchPoint")
    * @param [in] tool Werkzeugkoordinatennummer
    * @param [in] wobj Werkstückkoordinatennummer
    * @param [in] vel Geschwindigkeitsprozentsatz [0~100]
    * @param [in] acc Beschleunigungsprozentsatz [0~100] (vorübergehend nicht freigegeben)
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0~100]
    * @param [in] blendR Glättungsradius [mm] (-1 für blockierend)
    * @param [in] flag Status-Flag
    * @param [in] type Typ-Flag
    * @return Fehlercode
    */
    errno_t TrackMoveL(char name[32], int tool, int wobj, float vel, float acc, float ovl, float blendR, uint8_t flag, uint8_t type);

Förderband-Kommunikationseingangserkennung
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Förderband-Kommunikationseingangserkennung
    * @param [in] timeout Warte-Timeout [ms]
    * @return Fehlercode
    */
    errno_t ConveyorComDetect(int timeout);

Förderband-Kommunikationseingangserkennung auslösen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Förderband-Kommunikationseingangserkennung auslösen
    * @return Fehlercode
    */
    errno_t ConveyorComDetectTrigger();

Beispielprogramm für Roboter-Förderbandoperationen
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestConveyor(void)
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
      retval = robot.ConveyorStartEnd(1);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = robot.ConveyorPointIORecord();
      printf("ConveyorPointIORecord retval is: %d\n", retval);
      retval = robot.ConveyorPointARecord();
      printf("ConveyorPointARecord retval is: %d\n", retval);
      retval = robot.ConveyorRefPointRecord();
      printf("ConveyorRefPointRecord retval is: %d\n", retval);
      retval = robot.ConveyorPointBRecord();
      printf("ConveyorPointBRecord retval is: %d\n", retval);
      retval = robot.ConveyorStartEnd(0);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = 0;
      float param[6] = { 1,10000,200,0,0,20 };
      retval = robot.ConveyorSetParam(param);
      printf("ConveyorSetParam retval is: %d\n", retval);
      double cmp[3] = { 0.0, 0.0, 0.0 };
      retval = robot.ConveyorCatchPointComp(cmp);
      printf("ConveyorCatchPointComp retval is: %d\n", retval);
      int index = 1;
      int max_time = 30000;
      uint8_t block = 0;
      retval = 0;
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.MoveCart(&p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      printf("MoveCart retval is: %d\n", retval);
      retval = robot.WaitMs(1);
      printf("WaitMs retval is: %d\n", retval);
      retval = robot.ConveyorIODetect(10000);
      printf("ConveyorIODetect retval is: %d\n", retval);
      retval = robot.ConveyorGetTrackData(1);
      printf("ConveyorGetTrackData retval is: %d\n", retval);
      retval = robot.ConveyorTrackStart(1);
      printf("ConveyorTrackStart retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.ConveyorTrackEnd();
      printf("ConveyorTrackEnd retval is: %d\n", retval);
      robot.MoveCart(&p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      rtn = robot.ConveyorComDetect(1000 * 10);
      printf("ConveyorComDetect rtn is: %d\n", rtn);
      robot.Sleep(2000);
      rtn = robot.ConveyorComDetectTrigger();
      printf("ConveyorComDetectTrigger rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }


Endeffektor-Sensor konfigurieren
++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Sensor konfigurieren
    * @param [in] idCompany Hersteller, 18-JUNKONG; 25-HUIDE
    * @param [in] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @param [in] idSoftware Softwareversion, 0-J1.0/HuiDe1.0 (vorübergehend nicht freigegeben)
    * @param [in] idBus Anschlussposition, 1-Endeffektor Port 1; 2-Endeffektor Port 2...8-Endeffektor Port 8 (vorübergehend nicht freigegeben)
    * @return Fehlercode
    */
    errno_t AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Endeffektor-Sensorkonfiguration abrufen
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Endeffektor-Sensorkonfiguration abrufen
     * @param [out] idCompany Hersteller, 18-JUNKONG; 25-HUIDE
     * @param [out] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
     * @return Fehlercode
     */
    errno_t AxleSensorConfigGet(int& idCompany, int& idDevice);

Endeffektor-Sensor aktivieren
++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Endeffektor-Sensor aktivieren
     * @param [in] actFlag 0-Zurücksetzen; 1-Aktivieren
     * @return Fehlercode
     */
    errno_t AxleSensorActivate(int actFlag);

In Endeffektor-Sensorregister schreiben
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief In Endeffektor-Sensorregister schreiben
     * @param [in] devAddr Geräteadresse 0-255
     * @param [in] regHAddr Registeradresse hohes Byte
     * @param [in] regLAddr Registeradresse niedriges Byte
     * @param [in] regNum Anzahl der Register 0-255
     * @param [in] data1 Zu schreibender Registerwert 1
     * @param [in] data2 Zu schreibender Registerwert 2
     * @param [in] isNoBlock 0-blockierend; 1-nicht blockierend
     * @return Fehlercode
     */
    errno_t AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Codebeispiel für Endeffektor-Sensor
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAxleSensor(void)
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
      robot.AxleSensorConfig(18, 0, 0, 1);
      int company = -1;
      int type = -1;
      robot.AxleSensorConfigGet(company, type);
      printf("company is %d, type is %d\n", company, type);
      rtn = robot.AxleSensorActivate(1);
      printf("AxleSensorActivate rtn is %d\n", rtn);
      robot.Sleep(1000);
      rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
      printf("AxleSensorRegWrite rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Roboter-Peripherieprotokoll abrufen
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-Peripherieprotokoll abrufen
    * @param [out] protocol Roboter-Peripherieprotokollnummer: 4096-Erweiterungsachsen-Steuerkarte; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Fehlercode
    */
    errno_t GetExDevProtocol(int *protocol);

Roboter-Peripherieprotokoll einstellen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Roboter-Peripherieprotokoll einstellen
    * @param [in] protocol Roboter-Peripherieprotokollnummer: 4096-Erweiterungsachsen-Steuerkarte; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Fehlercode
    */
    errno_t SetExDevProtocol(int protocol);

Beispielprogramm zum Einstellen des Roboter-Peripherieprotokolls
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    int TestExDevProtocol(void)
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
      int protocol = 4096;
      rtn = robot.SetExDevProtocol(protocol);
      std::cout << "SetExDevProtocol rtn " << rtn << std::endl;
      rtn = robot.GetExDevProtocol(&protocol);
      std::cout << "GetExDevProtocol rtn " << rtn << " protocol is: " << protocol << std::endl;
      robot.CloseRPC();
      return 0;
    }

Endeffektor-Kommunikationsparameter abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Kommunikationsparameter abrufen
    * @param [out] param Struktur mit Kommunikationsparametern
    * @return Fehlercode
    */
    errno_t GetAxleCommunicationParam(AxleComParam* param);

Endeffektor-Kommunikationsparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Kommunikationsparameter einstellen
    * @param [in] param Struktur mit Kommunikationsparametern
    * @return Fehlercode
    */
    errno_t SetAxleCommunicationParam(AxleComParam param);

Endeffektor-Dateiübertragungstyp einstellen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Dateiübertragungstyp einstellen
    * @param [in] type 1-MCU Upgrade-Datei; 2-LUA-Datei
    * @return Fehlercode
    */
    errno_t SetAxleFileType(int type);

Endeffektor-LUA-Ausführung aktivieren
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-LUA-Ausführung aktivieren
    * @param [in] enable 0-nicht aktivieren; 1-aktivieren
    * @return Fehlercode
    */
    errno_t SetAxleLuaEnable(int enable);

Fehlerbehebung bei anomaler Endeffektor-LUA-Datei
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Fehlerbehebung bei anomaler Endeffektor-LUA-Datei
    * @param [in] status 0-nicht beheben; 1-beheben
    * @return Fehlercode
    */
    errno_t SetRecoverAxleLuaErr(int status);

Aktivierungsstatus der Endeffektor-LUA-Ausführung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktivierungsstatus der Endeffektor-LUA-Ausführung abrufen
    * @param [out] status status[0]: 0-nicht aktiviert; 1-aktiviert
    * @return Fehlercode
    */
    errno_t GetAxleLuaEnableStatus(int status[]);

Aktivierungstyp der Endeffektor-LUA-Endgeräte einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktivierungstyp der Endeffektor-LUA-Endgeräte einstellen
    * @param [in] forceSensorEnable Kraftsensor-Aktivierungsstatus, 0-nicht aktivieren; 1-aktivieren
    * @param [in] gripperEnable Greifer-Aktivierungsstatus, 0-nicht aktivieren; 1-aktivieren
    * @param [in] IOEnable IO-Geräte-Aktivierungsstatus, 0-nicht aktivieren; 1-aktivieren
    * @return Fehlercode
    */
    errno_t SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable);

Aktivierungstyp der Endeffektor-LUA-Endgeräte abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktivierungstyp der Endeffektor-LUA-Endgeräte abrufen
    * @param [out] forceSensorEnable Kraftsensor-Aktivierungsstatus, 0-nicht aktiviert; 1-aktiviert
    * @param [out] gripperEnable Greifer-Aktivierungsstatus, 0-nicht aktiviert; 1-aktiviert
    * @param [out] IOEnable IO-Geräte-Aktivierungsstatus, 0-nicht aktiviert; 1-aktiviert
    * @return Fehlercode
    */
    errno_t GetAxleLuaEnableDeviceType(int* forceSensorEnable, int* gripperEnable, int* IOEnable);

Aktuell konfigurierte Endgeräte abrufen
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktuell konfigurierte Endgeräte (über LUA) abrufen
    * @param [out] forceSensorEnable Array aktivierter Kraftsensornummern (Indikator)
    * @param [out] gripperEnable Array aktivierter Greifernummern (Indikator)
    * @param [out] IODeviceEnable Array aktivierter IO-Gerätenummern (Indikator)
    * @return Fehlercode
    */
    errno_t GetAxleLuaEnableDevice(int forceSensorEnable[], int gripperEnable[], int IODeviceEnable[]);

Greifer-Aktionssteuerungsfunktion aktivieren (für LUA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Greifer-Aktionssteuerungsfunktion aktivieren (für LUA-Skript)
    * @param [in] id Greifer-Gerätenummer
    * @param [in] func Funktions-Array: func[0]-Greifer aktivieren; func[1]-Greifer initialisieren; 2-Position einstellen; 3-Geschwindigkeit einstellen; 4-Drehmoment einstellen; 6-Greiferstatus lesen; 7-Initialisierungsstatus lesen; 8-Fehlercode lesen; 9-Position lesen; 10-Geschwindigkeit lesen; 11-Drehmoment lesen
    * @return Fehlercode
    */
    errno_t SetAxleLuaGripperFunc(int id, int func[]);

Aktivierte Greifer-Aktionssteuerungsfunktion abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktivierte Greifer-Aktionssteuerungsfunktion abrufen
    * @param [in] id Greifer-Gerätenummer
    * @param [out] func Funktions-Array (wie oben)
    * @return Fehlercode
    */
    errno_t GetAxleLuaGripperFunc(int id, int func[]);

In Ethercat-Slave-Datei des Roboters schreiben
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief In Ethercat-Slave-Datei des Roboters schreiben (Firmware/Konfiguration updaten)
    * @param [in] type Slave-Dateityp: 1-Upgrade Slave-Datei; 2-Upgrade Slave-Konfigurationsdatei
    * @param [in] slaveID Slave-Nummer
    * @param [in] fileName Name der hochzuladenden Datei (Pfad auf dem Roboter?)
    * @return Fehlercode
    */
    errno_t SlaveFileWrite(int type, int slaveID, std::string fileName);

Endeffektor-Lua-Open-Protocol-Datei hochladen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Lua-Open-Protocol-Datei hochladen
    * @param [in] filePath Lokaler Pfad zur Lua-Datei ".../AXLE_LUA_End_DaHuan.lua"
    * @return Fehlercode
    */
    errno_t AxleLuaUpload(std::string filePath);

Ethercat-Slave des Roboters in den Boot-Modus versetzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ethercat-Slave des Roboters in den Boot-Modus versetzen (für Firmware-Update)
    * @return Fehlercode
    */
    errno_t SetSysServoBootMode();

Codebeispiel für Roboter-Endeffektor-LUA-Dateioperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAxleLua(void)
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
      robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");
      AxleComParam param(7, 8, 1, 0, 5, 3, 1);
      robot.SetAxleCommunicationParam(param);
      AxleComParam getParam;
      robot.GetAxleCommunicationParam(&getParam);
      printf("GetAxleCommunicationParam param is %d %d %d %d %d %d %d\n", getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify, getParam.timeout, getParam.timeoutTimes, getParam.period);
      robot.SetAxleLuaEnable(1);
      int luaEnableStatus[1] = {0};
      robot.GetAxleLuaEnableStatus(luaEnableStatus);
      robot.SetAxleLuaEnableDeviceType(0, 1, 0);
      int forceEnable = 0;
      int gripperEnable = 0;
      int ioEnable = 0;
      robot.GetAxleLuaEnableDeviceType(&forceEnable, &gripperEnable, &ioEnable);
      printf("GetAxleLuaEnableDeviceType param is %d %d %d\n", forceEnable, gripperEnable, ioEnable);
      int func[16] = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
      robot.SetAxleLuaGripperFunc(1, func);
      int getFunc[16] = { 0 };
      robot.GetAxleLuaGripperFunc(1, getFunc);
      int getforceEnable[16] = { 0 };
      int getgripperEnable[16] = { 0 };
      int getioEnable[16] = { 0 };
      robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable);
      printf("\ngetforceEnable status : ");
      for (int i = 0; i < 16; i++)
      {
        printf("%d,", getforceEnable[i]);
      }
      printf("\ngetgripperEnable status : ");
      for (int i = 0; i < 16; i++)
      {
        printf("%d,", getgripperEnable[i]);
      }
      printf("\ngetioEnable status : ");
      for (int i = 0; i < 16; i++)
      {
        printf("%d,", getioEnable[i]);
      }
      printf("\n");
      robot.ActGripper(1, 0);
      robot.Sleep(2000);
      robot.ActGripper(1, 1);
      robot.Sleep(2000);
      robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
      int pos = 0;
      while (true)
      {
        robot.GetRobotRealTimeState(&pkg);
        printf("gripper pos is %u\n", pkg.gripper_position);
        robot.Sleep(100);
      }
      robot.CloseRPC();
      return 0;
    }

SmartTool-Tastenstatus abrufen
+++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief SmartTool-Tastenstatus abrufen
    * @param [out] state SmartTool-Griff Tastenstatus (Bit0: 0-Kommunikation normal; 1-Kommunikation unterbrochen; Bit1-Rückgängig; Bit2-Programm löschen;
        Bit3-Taste A; Bit4-Taste B; Bit5-Taste C; Bit6-Taste D; Bit7-Taste E; Bit8-IO-Taste; Bit9-Hand/Automatik; Bit10-Start)
    * @return Fehlercode
    */
    errno_t GetSmarttoolBtnState(int& state);

Codebeispiel für SmartTool-Tasten
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int main(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;

      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      robot.SetReConnectParam(true, 30000, 500);

      while (true)
      {
        int btn = 0;
        robot.GetSmarttoolBtnState(btn);
        // Ausgabe als Binärstring
        cout << "smarttool " << bitset<sizeof(btn) * 8>(btn) << endl;

        Sleep(100);
      }
    }

Array-Sauggreifer steuern
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Array-Sauggreifer steuern
    * @param [in] slaveID Slave-Nummer (0 für Broadcast)
    * @param [in] len Anzahl der zu steuernden Sauger (Länge des ctrlValue-Arrays)
    * @param [in] ctrlValue Steuerwerte-Array: 1-mit maximalem Vakuum ansaugen; 2-mit eingestelltem Vakuum ansaugen; 3-Ansaugen stoppen
    * @return Fehlercode
    */
    errno_t SetSuckerCtrl(uint8_t slaveID, uint8_t len, uint8_t ctrlValue[20]);

Status des Array-Sauggreifers abrufen
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Status des Array-Sauggreifers abrufen
    * @param [in] slaveID Slave-Nummer
    * @param [out] state Saugzustand: 0-Objekt losgelassen; 1-Werkstück erfolgreich angesaugt; 2-kein Objekt angesaugt; 3-Objekt abgelöst
    * @param [out] pressValue Aktuelles Vakuum [kPa]
    * @param [out] error Aktueller Fehlercode des Saugers
    * @return Fehlercode
    */
    errno_t GetSuckerState(uint8_t slaveID, uint8_t* state, int* pressValue, int* error);

Auf Saugerstatus warten
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Auf Saugerstatus warten
    * @param [in] slaveID Slave-Nummer
    * @param [in] state Erwarteter Saugzustand (siehe GetSuckerState)
    * @param [in] ms Maximale Wartezeit [ms]
    * @return Fehlercode (0 bei Erfolg, Fehlercode bei Timeout/Fehler)
    */
    errno_t WaitSuckerState(uint8_t slaveID, uint8_t state, int ms);

Codebeispiel für Array-Sauggreifer-Steuerung
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    void testSucker()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;

        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("E://Projekt/PeripherieSDK/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(1, "CtrlDev_sucker.lua");
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);

        // Sauger im Broadcast-Modus mit maximaler Saugkraft steuern
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);

        // Zustände von Sauger 1 und Sauger 12 in einer Schleife überwachen
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, &state, &pressVlaue, &error);
            printf("sucker1 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.GetSuckerState(12, &state, &pressVlaue, &error);
            printf("sucker12 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.Sleep(100);
        }

        // Auf angesaugten Zustand von Sauger 1 warten, Timeout 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        printf("WaitSuckerState result is  %d\n", ret);

        // Unicast-Modus: Sauger 1 und 12 ausschalten (Wert 3)
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);

        robot.CloseRPC();
    }

Open-Protocol-LUA-Datei hochladen
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Open-Protocol-LUA-Datei hochladen (für Peripheriegeräte)
     * @param [in] filePath Lokaler Pfad zur LUA-Datei
     * @return Fehlercode
     */
    errno_t OpenLuaUpload(std::string filePath);

Slave-Kartenparameter abrufen (Feldbus)
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Slave-Kartenparameter (Feldbus) abrufen
    * @param [out] type Protokolltyp: 0-Ethercat, 1-CClink, 3-Ethercat (Dopplung?), 4-EIP
    * @param [out] version Protokollversion
    * @param [out] connState Verbindungsstatus: 0-nicht verbunden, 1-verbunden
    * @return Fehlercode
    */
    errno_t GetFieldBusConfig(uint8_t* type, uint8_t* version, uint8_t* connState);

In Slave-DO schreiben (Feldbus)
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief In Slave-DO (Digitalausgang) schreiben (Feldbus)
    * @param [in] DOIndex DO-Nummer (Startadresse)
    * @param [in] writeNum Anzahl der zu schreibenden Werte
    * @param [in] status[8] Array mit den zu schreibenden Werten (0/1), max. 8
    * @return Fehlercode
    */
    errno_t FieldBusSlaveWriteDO(uint8_t DOIndex, uint8_t writeNum, uint8_t status[8]);

In Slave-AO schreiben (Feldbus)
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief In Slave-AO (Analogausgang) schreiben (Feldbus)
    * @param [in] AOIndex AO-Nummer (Startadresse)
    * @param [in] writeNum Anzahl der zu schreibenden Werte
    * @param [in] status[8] Array mit den zu schreibenden Werten (int), max. 8
    * @return Fehlercode
    */
    errno_t FieldBusSlaveWriteAO(uint8_t AOIndex, uint8_t writeNum, int status[8]);

Slave-DI lesen (Feldbus)
+++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Slave-DI (Digitaleingang) lesen (Feldbus)
    * @param [in] DIIndex DI-Nummer (Startadresse)
    * @param [in] readNum Anzahl der zu lesenden Werte
    * @param [out] status[8] Array mit den gelesenen Werten (0/1), max. 8
    * @return Fehlercode
    */
    errno_t FieldBusSlaveReadDI(uint8_t DIIndex, uint8_t readNum, uint8_t status[8]);

Slave-AI lesen (Feldbus)
+++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Slave-AI (Analogeingang) lesen (Feldbus)
    * @param [in] AIIndex AI-Nummer (Startadresse)
    * @param [in] readNum Anzahl der zu lesenden Werte
    * @param [out] status[8] Array mit den gelesenen Werten (int), max. 8
    * @return Fehlercode
    */
    errno_t FieldBusSlaveReadAI(uint8_t AIIndex, uint8_t readNum, int status[8]);

Auf erweiterten DI-Eingang warten (Feldbus)
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Auf erweiterten DI-Eingang (Feldbus) warten
    * @param [in] DIIndex DI-Nummer
    * @param [in] status Erwarteter Zustand: false (0) für niedrig, true (1) für hoch
    * @param [in] waitMs Maximale Wartezeit [ms]
    * @return Fehlercode (0 bei Erfolg, Fehlercode bei Timeout)
    */
    errno_t FieldBusSlaveWaitDI(uint8_t DIIndex, bool status, int waitMs);

Auf erweiterten AI-Eingang warten (Feldbus)
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Auf erweiterten AI-Eingang (Feldbus) warten
    * @param [in] AIIndex AI-Nummer
    * @param [in] waitType Bedingung: 0-größer als; 1-kleiner als
    * @param [in] value Vergleichswert (double)
    * @param [in] waitMs Maximale Wartezeit [ms]
    * @return Fehlercode (0 bei Erfolg, Fehlercode bei Timeout)
    */
    errno_t FieldBusSlaveWaitAI(uint8_t AIIndex, uint8_t waitType, double value, int waitMs);

Codebeispiel für Slave-Modus-Befehle (Feldbus-Karte)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    void testFieldBusBoard()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t type = 0, version = 0, connState = 0;
        uint8_t ctrl[8];
        int ctrlAO[8];
        static uint8_t DI[8];
        static int AI[8];

        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("E://Projekt/PeripherieSDK/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);

        // Protokolltyp, Softwareversion und Verbindungsstatus der Slave-Karte abrufen
        robot.GetFieldBusConfig(&type, &version, &connState);
        printf("type is %d, version is %d, connState is %d\n", type, version, connState);

        // DO0 = 1, DO1 = 0, DO2 = 1 schreiben
        ctrl[0] = 0; // Wert für DO0? Ursprünglich ctrl[0]=0, aber Kommentar sagt DO0=1, möglicherweise Index-Verschiebung
        ctrl[1] = 1;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);

        // AO2 = 0x1000 (4096) schreiben
        ctrlAO[0] = 0x1005; // Beispielwert 0x1005
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO); // Schreibt ab AO2 den Wert aus ctrlAO[0]

        // DI0..DI3 und AI0..AI2 in einer Schleife überwachen
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            printf("DI0 is %d, DI1 is %d, DI2 is %d, DI3 is %d\n", DI[0], DI[1], DI[2], DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            printf("AI0 is %d, AI1 is %d, AI2 is %d\n", AI[0], AI[1], AI[2]);
            robot.Sleep(10);
        }

        // Auf DI0 = 1 warten, Timeout 100ms
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        printf("FieldBusSlaveWaitDI result is  %d\n", ret);

        // Auf AI0 > 400 warten, Timeout 100ms
        ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00, 100);
        printf("FieldBusSlaveWaitAI result is  %d\n", ret);

        robot.CloseRPC();
    }

Laser-Peripherie Ein-/Ausschalten
++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Laser-Peripherie Ein-/Ausschaltfunktion
     * @param [in] OnOff 0-ausschalten, 1-einschalten
     * @param [in] weldId Schweißnaht-ID (Standard 0)
     * @return Fehlercode
     */
    errno_t LaserTrackingLaserOnOff(int OnOff, int weldId);

Laser-Tracking Start/Stopp
+++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Laser-Tracking Start/Stopp
     * @param [in] OnOff 0-stoppen, 1-starten
     * @param [in] coordId Werkzeugkoordinatennummer des Laser-Peripheriegeräts
     * @return Fehlercode
     */
    errno_t LaserTrackingTrackOnOff(int OnOff, int coordId);

Lasernahtsuche starten - feste Richtung
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Lasernahtsuche starten - feste Richtung
    * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
    * @param [in] vel Geschwindigkeit [%]
    * @param [in] distance Maximale Suchdistanz [mm]
    * @param [in] timeout Such-Timeout [ms]
    * @param [in] posSensorNum Nummer des kalibrierten Laser-Werkzeugkoordinatensystems
    * @return Fehlercode
    */
    errno_t LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum);

Lasernahtsuche starten - Richtung durch Punkt vorgegeben
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Lasernahtsuche starten - Richtung durch Punkt vorgegeben
     * @param [in] directionPoint XYZ-Koordinaten des Richtungspunkts (relativ)
     * @param [in] vel Geschwindigkeit [%]
     * @param [in] distance Maximale Suchdistanz [mm]
     * @param [in] timeout Such-Timeout [ms]
     * @param [in] posSensorNum Nummer des kalibrierten Laser-Werkzeugkoordinatensystems
     * @return Fehlercode
     */
    errno_t LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum);

Lasernahtsuche beenden
++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Lasernahtsuche beenden
     * @return Fehlercode
     */
    errno_t LaserTrackingSearchStop();

Laser-Netzwerkparameter konfigurieren
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Laser-Netzwerkparameter konfigurieren
     * @param [in] ip IP-Adresse des Laser-Peripheriegeräts
     * @param [in] port Portnummer des Laser-Peripheriegeräts
     * @return Fehlercode
     */
    errno_t LaserTrackingSensorConfig(std::string ip, int port);

Laser-Peripherie-Abtastperiode konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Laser-Peripherie-Abtastperiode konfigurieren
    * @param [in] period Abtastperiode [ms]
    * @return Fehlercode
    */
    errno_t LaserTrackingSensorSamplePeriod(int period);

Laser-Peripherie-Treiber laden
+++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Laser-Peripherie-Treiber laden
     * @param [in] type Protokolltyp des Laser-Peripherietreibers: 101-RuiNiu; 102-ChuangXiang; 103-QuanShi; 104-TongZhou; 105-AoTai
     * @return Fehlercode
     */
    errno_t LoadPosSensorDriver(int type);

Laser-Peripherie-Treiber entladen
++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Laser-Peripherie-Treiber entladen
     * @return Fehlercode
     */
    errno_t UnLoadPosSensorDriver();

Laser-Schweißnaht-Trajektorie aufzeichnen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Laser-Schweißnaht-Trajektorie aufzeichnen
    * @param [in] status 0-Aufzeichnung stoppen; 1-Echtzeit-Tracking; 2-Aufzeichnung starten
    * @param [in] delayTime Verzögerungszeit [ms]
    * @return Fehlercode
    */
    errno_t LaserSensorRecord1(int status, int delayTime);

Laser-Schweißnaht-Trajektorie wiedergeben
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Laser-Schweißnaht-Trajektorie wiedergeben
     * @param [in] delayTime Verzögerungszeit [ms]
     * @param [in] speed Geschwindigkeit [%]
     * @return Fehlercode
     */
    errno_t LaserSensorReplay(int delayTime, double speed);

Laser-Tracking-Wiedergabe (MoveLTR)
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Laser-Tracking-Wiedergabe (Bewegung entlang der aufgezeichneten Trajektorie)
     * @return Fehlercode
     */
    errno_t MoveLTR();

Laser-Schweißnaht-Trajektorie aufzeichnen und wiedergeben (erweitert)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Laser-Schweißnaht-Trajektorie aufzeichnen und wiedergeben (erweiterte Funktion mit verschiedenen Modi)
    * @param [in] delayMode Modus: 0-Verzögerungszeit; 1-Verzögerungsdistanz
    * @param [in] delayTime Verzögerungszeit [ms] (wenn delayMode=0)
    * @param [in] delayDisExAxisNum Erweiterungsachsennummer für Distanzverzögerung
    * @param [in] delayDis Verzögerungsdistanz [mm] (wenn delayMode=1)
    * @param [in] sensitivePara Kompensations-Empfindlichkeitskoeffizient
    * @param [in] trackMode Punkt-Tracking-Typ: 0-Erweiterungsachse asynchron; 1-Roboter (synchron?)
    * @param [in] triggerMode Punkt-Tracking-Auslösemodus: 0-Tracking-Dauer; 1-IO
    * @param [in] runTime Dauer des Roboter-Punkt-Trackings [s]
    * @param [in] speed Geschwindigkeit [%]
    * @return Fehlercode
    */
    errno_t LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed);

Zum aufgezeichneten Startpunkt der Schweißnaht bewegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Zum aufgezeichneten Startpunkt der Schweißnaht bewegen
    * @param [in] moveType 0-moveJ, 1-moveL
    * @param [in] ovl Geschwindigkeit [%]
    * @return Fehlercode
    */
    errno_t MoveToLaserRecordStart(int moveType, double ovl);

Zum aufgezeichneten Endpunkt der Schweißnaht bewegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Zum aufgezeichneten Endpunkt der Schweißnaht bewegen
    * @param [in] moveType 0-moveJ, 1-moveL
    * @param [in] ovl Geschwindigkeit [%]
    * @return Fehlercode
    */
    errno_t MoveToLaserRecordEnd(int moveType, double ovl);

Zum vom Laser-Sensor gefundenen Nahtpunkt bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Zum vom Laser-Sensor gefundenen Nahtpunkt bewegen
    * @param [in] moveFlag Bewegungstyp: 0-PTP; 1-LIN
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0-100]
    * @param [in] dataFlag Auswahl der Schweißnaht-Cache-Daten: 0-Planungsdaten ausführen; 1-Aufgezeichnete Daten ausführen
    * @param [in] plateType Plattenmaterial-Typ: 0-Wellenplatte; 1-Wellpappe; 2-Zaunplatte; 3-Ölfass; 4-Wellenpanzerstahl
    * @param [in] trackOffectType Laser-Sensor-Versatztyp: 0-kein Versatz; 1-Versatz im Basiskoordinatensystem; 2-Versatz im Werkzeugkoordinatensystem; 3-Versatz basierend auf Laser-Sensor-Rohdaten
    * @param [in] offset Versatzwert (Pose)
    * @return Fehlercode
    */
    errno_t MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset);

Koordinaten des vom Laser-Sensor gefundenen Nahtpunkts abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Koordinaten des vom Laser-Sensor gefundenen Nahtpunkts abrufen
    * @param [in] trackOffectType Laser-Sensor-Versatztyp (siehe MoveToLaserSeamPos)
    * @param [in] offset Versatzwert (Pose)
    * @param [out] jPos Gelenkposition [°]
    * @param [out] descPos Kartesische Position [mm]
    * @param [out] tool Verwendetes Werkzeugkoordinatensystem
    * @param [out] user Verwendetes Werkstückkoordinatensystem
    * @param [out] exaxis Position der Erweiterungsachse [mm]
    * @return Fehlercode
    */
    errno_t GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos& jPos, DescPose& descPos, int& tool, int& user, ExaxisPos& exaxis);

Codebeispiel für Laser-Peripherie-Sensorparametrierung und -Debugging
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLaserConfig()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        // IP-Adresse und Port konfigurieren
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        // Abtastperiode konfigurieren
        robot.LaserTrackingSensorSamplePeriod(20);
        // Treiber laden (Typ 101 = RuiNiu)
        robot.LoadPosSensorDriver(101);
        // Laser ausschalten
        robot.LaserTrackingLaserOnOff(0, 0);
        robot.Sleep(3000);
        // Laser einschalten
        robot.LaserTrackingLaserOnOff(1, 0);
        robot.CloseRPC();
    }

Codebeispiel für Laser-Trajektorienscan und -wiedergabe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLaserRecordAndReplay()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while (cnt < 31)
        {
            // Zum Startpunkt der Aufzeichnung bewegen
            JointPos startjointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            // Trajektorienaufzeichnung starten
            robot.LaserSensorRecord1(2, 10);
            // Zum Endpunkt der Aufzeichnung bewegen
            JointPos endjointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(&endjointPos, &enddescPose, 1, 0, 30, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            // Aufzeichnung stoppen
            robot.LaserSensorRecord1(0, 10);
            // Zum aufgezeichneten Startpunkt bewegen
            robot.MoveToLaserRecordStart(1, 30);
            // Trajektorienwiedergabe starten
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            // Wiedergabe stoppen (implizit durch MoveLTR?)
            robot.LaserSensorRecord1(0, 10);
            printf("Laser-Scan + Trajektorienwiedergabe Stabilitätstest Nr. %d\n", cnt);
            cnt++;
        }
        robot.CloseRPC();
    }

Codebeispiel für Lasernahtsuche und Echtzeit-Tracking
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLasertrack()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        // Open-Protocol-Datei hochladen und laden
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while (cnt < 2)
        {
            // Zum Startpunkt der Suche bewegen
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            DescTran directionPoint; // Nicht initialisiert/verwendet
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);

            // Lasernahtsuche in -y Richtung starten (direction=3)
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            // Bei erfolgreicher Suche (ret == 0)
            if (ret == 0)
            {
                // Zum gefundenen Nahtpunkt bewegen
                robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);
                // Laser-Tracking starten
                robot.LaserTrackingTrackOnOff(1, 2);
                // Bewegung entlang der Naht (mit Tracking)
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.MoveL(&endjointPos, &enddescPose, 1, 0, 20, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
                // Tracking stoppen
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            cnt++;
        }
        robot.CloseRPC();
    }

Codebeispiel für synchrones Laser-Tracking mit Erweiterungsachse und Roboter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLasertrackandExitAxis()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        ExaxisPos startexaxisPos = { 0,0,0,0 };
        ExaxisPos seamexaxisPos = { -10,0,0,0 };
        ExaxisPos endexaxisPos = { -30, 0, 0, 0 };
        DescPose offdese = { 0, 0, 0, 0, 0, 0 };
        JointPos seamjointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose(0, 0, 0, 0, 0, 0);

        int cnt = 1;
        while (cnt < 31)
        {
            // Zum Startpunkt der Suche bewegen (synchron mit Erweiterungsachse)
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            // Lasernahtsuche in -y Richtung starten (direction=3)
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            int tool = 0;
            int user = 0;
            // Koordinaten des gefundenen Nahtpunkts abrufen
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            printf("%f, %f, %f,%f, %f, %f,%f, %f, %f,%f, %f, %f\n", seamjointPos.jPos[0], seamjointPos.jPos[1], seamjointPos.jPos[2], seamjointPos.jPos[3], seamjointPos.jPos[4], seamjointPos.jPos[5], seamdescPose.tran.x, seamdescPose.tran.y, seamdescPose.tran.z, seamdescPose.rpy.rx, seamdescPose.rpy.ry, seamdescPose.rpy.rz);

            // Bei erfolgreicher Suche (ret == 0)
            if (ret == 0)
            {
                // Synchron zum Nahtpunkt bewegen
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                // Laser-Tracking starten
                robot.LaserTrackingTrackOnOff(1, 2);
                // Synchron entlang der Naht bewegen (mit Tracking)
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                // Tracking stoppen
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            cnt++;
            printf("Synchrones Laser-Tracking mit Erweiterungsachse - Durchlauf %d\n", cnt);
        }
        robot.CloseRPC();
    }

Endeffektor-Transparentübertragungsfunktion ein-/ausschalten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor-Transparentübertragungsfunktion ein-/ausschalten
    * @param [in] Aktivierung, 0-deaktiviert, 1-aktiviert
    * @return Fehlercode
    */
    errno_t SetAxleGenComEnable(int mode);
                                                            
Endeffektor-Transparentübertragungsfunktion für azyklische Datenübertragung und -empfang
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Endeffektor-Transparentübertragungsfunktion für azyklische Datenübertragung und -empfang
    * @param [in] len_snd Länge der zu sendenden Daten
    * @param [in] sndBuff Zu sendende Daten
    * @param [in] len_rcv Länge der zu empfangenden Daten
    * @param [out] rcvBuff Antwortdaten
    * @return Fehlercode
    */
    errno_t SndRcvAxleGenComCmdData(int lenSnd, int sndBuff[130], int lenRcv, int rcvData[130]);
                                                                
Codebeispiel für azyklische Datenkommunikation des DIO Health Care Moxibustion-Kopfs basierend auf der Endeffektor-Transparentübertragungsfunktion
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int testAxleGenCom()
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
      int led_on[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
      int led_off[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int version[5] = { 0xAB, 0xBA, 0x11, 0x00, 0x76 };
      int state[6] = { 0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B };
      int cycleState[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int rcvdata[16] = {0};
      int ret = 0;
      int cnt = 1;
      JointPos p1Joint(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
      DescPose p1Desc(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);
      JointPos p2Joint(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
      DescPose p2Desc(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      //Endeffektor-Transparentübertragungsfunktion aktivieren
      robot.SetAxleGenComEnable(1);
      robot.SetAxleLuaEnable(1);
      while (cnt <= 10000)
      {
        //Versionsnummer auslesen
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n", rcvdata[4], rcvdata[5], rcvdata[6] ,rcvdata[7], rcvdata[8]);
        if (ret != 0)
        {
          break;
        }
        robot.Sleep(1000);
        //Präsenzstatus des Moxibustion-Kopfs auslesen
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        printf(" state : %d \n", rcvdata[4]);
        robot.Sleep(1000);
        //Laser des Moxibustion-Kopfs einschalten
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        printf("led on rcv data is: %d, %d, %d, %d, %d, %d  \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(4000);
        //Laser des Moxibustion-Kopfs ausschalten
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(1000);
        printf("***********************complate No. %d SDK test*****************************\n", cnt);
        cnt++;
      }
      robot.CloseRPC();
    }

Open-Protocol-Lua-Datei herunterladen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Open-Protocol-Lua-Datei herunterladen
    * @param [in] fileName Name der Open-Protocol-Datei "CtrlDev_XXX.lua"
    * @param [in] savePath Pfad zum Speichern der Open-Protocol-Datei
    * @return Fehlercode
    */
    errno_t OpenLuaDownload(std::string fileName, std::string savePath);
    
Open-Protocol-Lua-Datei löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Open-Protocol-Lua-Datei löschen
    * @param [in] fileName Name der zu löschenden Open-Protocol-Lua-Datei "CtrlDev_XXX.lua"
    * @return Fehlercode
    */
    errno_t OpenLuaDelete(std::string fileName);
        
Alle Open-Protocol-Lua-Dateien löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Alle Open-Protocol-Lua-Dateien löschen
    * @return Fehlercode
    */
    errno_t AllOpenLuaDelete();

Codebeispiel für Open-Protocol-Upload, -Download und -Löschen von Controller-Peripheriegeräten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestCtrlOpenLuaOperate()
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
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        std::string name[4] = {};
        rtn = robot.GetCtrlOpenLUAName(name);
        printf("ctrl open lua names : %s, %s, %s, %s\n", name[0].c_str(), name[1].c_str(), name[2].c_str(), name[3].c_str());
        rtn = robot.LoadCtrlOpenLUA(1);
        printf("LoadCtrlOpenLUA rtn is %d\n", rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        printf("UnloadCtrlOpenLUA rtn is %d\n", rtn);
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        printf("OpenLuaDelete rtn is %d\n", rtn);
        rtn = robot.AllOpenLuaDelete();
        printf("AllOpenLuaDelete rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }