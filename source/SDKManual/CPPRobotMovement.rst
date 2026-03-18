Roboterbewegung
====================

.. toctree::
    :maxdepth: 5


Jog-Tippbetrieb
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Jog-Tippbetrieb (Punkt-für-Punkt-Bewegung)
    * @param  [in]  ref 0-Jog im Gelenkraum, 2-Jog im Basiskoordinatensystem, 4-Jog im Werkzeugkoordinatensystem, 8-Jog im Werkstückkoordinatensystem
    * @param  [in]  nb 1-Achse 1 (oder X-Achse), 2-Achse 2 (oder Y-Achse), 3-Achse 3 (oder Z-Achse), 4-Achse 4 (oder Rotation um X-Achse), 5-Achse 5 (oder Rotation um Y-Achse), 6-Achse 6 (oder Rotation um Z-Achse)
    * @param  [in]  dir 0-negative Richtung, 1-positive Richtung
    * @param  [in]  vel Geschwindigkeitsprozentsatz, [0~100]
    * @param  [in]  acc Beschleunigungsprozentsatz, [0~100]
    * @param  [in]  max_dis Maximaler Winkel pro Tippbewegung [°] oder maximale Distanz [mm]
    * @return  Fehlercode
    */
    errno_t  StartJOG(uint8_t ref, uint8_t nb, uint8_t dir, float vel, float acc, float max_dis);

Jog-Tippbetrieb mit Verzögerung stoppen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Jog-Tippbetrieb mit Verzögerung stoppen
    * @param  [in]  ref  1-Jog im Gelenkraum stoppen, 3-Jog im Basiskoordinatensystem stoppen, 5-Jog im Werkzeugkoordinatensystem stoppen, 9-Jog im Werkstückkoordinatensystem stoppen
    * @return  Fehlercode
    */
    errno_t  StopJOG(uint8_t ref);

Jog-Tippbetrieb sofort stoppen
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Jog-Tippbetrieb sofort stoppen
    * @return  Fehlercode
    */
    errno_t  ImmStopJOG();

Codebeispiel für Roboter-Jog-Steuerung
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestJOG(void)
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
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(0, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.ImmStopJOG();
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(2, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.ImmStopJOG();
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(4, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.StopJOG(5);
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(8, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.StopJOG(9);
             robot.Sleep(1000);
         }
         robot.CloseRPC();
         return 0;
     }

Bewegung im Gelenkraum
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Bewegung im Gelenkraum (MoveJ)
    * @param  [in] joint_pos  Ziel-Gelenkposition, Einheit deg
    * @param  [in] desc_pos   Ziel-Kartesische Pose
    * @param  [in] tool  Werkzeugkoordinatennummer, Bereich [0~14]
    * @param  [in] user  Werkstückkoordinatennummer, Bereich [0~14]
    * @param  [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param  [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] ovl  Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param  [in] epos  Position der Erweiterungsachse, Einheit mm
    * @param  [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit ms
    * @param  [in] offset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param  [in] offset_pos  Posenversatz
    * @return  Fehlercode
    */
    errno_t  MoveJ(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos *epos, float blendT, uint8_t offset_flag, DescPose *offset_pos);

Bewegung im Gelenkraum (automatische Vorwärtskinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung im Gelenkraum (automatische Vorwärtskinematik)
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] epos Position der Erweiterungsachse, Einheit mm
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit ms
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    errno_t MoveJ(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos* epos, float blendT, uint8_t offset_flag, DescPose* offset_pos);

Linearbewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Linearbewegung im kartesischen Raum (MoveL)
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0~100] / physikalische Geschwindigkeit (mm/s)
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param [in] blendMode Übergangsart; 0-Innenkreisübergang; 1-Eckpunktübergang
    * @param [in] epos Position der Erweiterungsachse, Einheit mm
    * @param [in] search 0-keine Schweißdraht-Positionssuche, 1-Schweißdraht-Positionssuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] oacc Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung (mm/s2)
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit (mm/s) und Beschleunigung (mm/s2)
    * @param [in] overSpeedStrategy Strategie bei Geschwindigkeitsüberschreitung, 1-Standard; 2-Fehler und Stopp bei Überschreitung; 3-adaptive Geschwindigkeitsreduzierung, Standard 0
    * @param [in] speedPercent Zulässiger Geschwindigkeitsreduzierungsschwellwert in Prozent [0-100], Standard 10%
    * @return Fehlercode
    */
    errno_t MoveL(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos, float oacc = 100.0, int velAccParamMode = 0, int overSpeedStrategy = 0, int speedPercent = 10);

Linearbewegung im kartesischen Raum (automatische inverse Kinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Linearbewegung im kartesischen Raum (automatische inverse Kinematik)
    * @param [in] desc_pos  Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param [in] blendMode Übergangsart; 0-Innenkreisübergang; 1-Eckpunktübergang
    * @param [in] epos Position der Erweiterungsachse, Einheit mm
    * @param [in] search 0-keine Schweißdraht-Positionssuche, 1-Schweißdraht-Positionssuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen
    * @param [in] overSpeedStrategy Strategie bei Geschwindigkeitsüberschreitung, 1-Standard; 2-Fehler und Stopp bei Überschreitung; 3-adaptive Geschwindigkeitsreduzierung, Standard 0
    * @param [in] speedPercent Zulässiger Geschwindigkeitsreduzierungsschwellwert in Prozent [0-100], Standard 10%
    * @return Fehlercode
    */
    errno_t MoveL(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos* epos, uint8_t search, uint8_t offset_flag, DescPose* offset_pos, int config = -1, int overSpeedStrategy = 0, int speedPercent = 10);

Kreisbogenbewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Kreisbogenbewegung im kartesischen Raum (MoveC)
    * @param  [in] joint_pos_p  Gelenkposition des Zwischenpunkts, Einheit deg
    * @param  [in] desc_pos_p   Kartesische Pose des Zwischenpunkts
    * @param  [in] ptool  Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param  [in] puser  Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param  [in] pvel  Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100]
    * @param  [in] pacc  Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] epos_p  Position der Erweiterungsachse am Zwischenpunkt, Einheit mm
    * @param  [in] poffset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zwischenpunkt
    * @param  [in] offset_pos_p  Posenversatz für Zwischenpunkt
    * @param  [in] joint_pos_t  Gelenkposition des Zielpunkts, Einheit deg
    * @param  [in] desc_pos_t   Kartesische Pose des Zielpunkts
    * @param  [in] ttool  Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param  [in] tuser  Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param  [in] tvel  Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100]
    * @param  [in] tacc  Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] epos_t  Position der Erweiterungsachse am Zielpunkt, Einheit mm
    * @param  [in] toffset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zielpunkt
    * @param  [in] offset_pos_t  Posenversatz für Zielpunkt
    * @param  [in] ovl  Geschwindigkeitsskalierungsfaktor [0~100] / physikalische Geschwindigkeit (mm/s)
    * @param  [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param  [in] oacc Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung (mm/s2)
    * @param  [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit (mm/s) und Beschleunigung (mm/s2)
    * @return  Fehlercode
    */
    errno_t MoveC(JointPos *joint_pos_p, DescPose *desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos *epos_p, uint8_t poffset_flag, DescPose *offset_pos_p, JointPos *joint_pos_t, DescPose *desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos *epos_t, uint8_t toffset_flag, DescPose *offset_pos_t, float ovl, float blendR, float oacc = 100.0, int velAccParamMode = 0);

Kreisbogenbewegung im kartesischen Raum (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kreisbogenbewegung im kartesischen Raum (automatische inverse Kinematik)
    * @param [in] desc_pos_p  Kartesische Pose des Zwischenpunkts
    * @param [in] ptool Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] puser Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] pvel Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt, Einheit mm
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zwischenpunkt
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt
    * @param [in] desc_pos_t  Kartesische Pose des Zielpunkts
    * @param [in] ttool Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tuser Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tvel Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt, Einheit mm
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zielpunkt
    * @param [in] offset_pos_t Posenversatz für Zielpunkt
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen
    * @return Fehlercode
    */
    errno_t MoveC(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, uint8_t poffset_flag, DescPose* offset_pos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, uint8_t toffset_flag, DescPose* offset_pos_t, float ovl, float blendR, int config = -1);

Vollkreisbewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Vollkreisbewegung im kartesischen Raum (Circle)
    * @param  [in] joint_pos_p  Gelenkposition von Zwischenpunkt 1, Einheit deg
    * @param  [in] desc_pos_p   Kartesische Pose von Zwischenpunkt 1
    * @param  [in] ptool  Werkzeugkoordinatennummer für Zwischenpunkt 1, Bereich [0~14]
    * @param  [in] puser  Werkstückkoordinatennummer für Zwischenpunkt 1, Bereich [0~14]
    * @param  [in] pvel  Geschwindigkeitsprozentsatz für Zwischenpunkt 1, Bereich [0~100]
    * @param  [in] pacc  Beschleunigungsprozentsatz für Zwischenpunkt 1, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] epos_p  Position der Erweiterungsachse an Zwischenpunkt 1, Einheit mm
    * @param  [in] joint_pos_t  Gelenkposition von Zwischenpunkt 2, Einheit deg
    * @param  [in] desc_pos_t   Kartesische Pose von Zwischenpunkt 2
    * @param  [in] ttool  Werkzeugkoordinatennummer für Zwischenpunkt 2, Bereich [0~14]
    * @param  [in] tuser  Werkstückkoordinatennummer für Zwischenpunkt 2, Bereich [0~14]
    * @param  [in] tvel  Geschwindigkeitsprozentsatz für Zwischenpunkt 2, Bereich [0~100]
    * @param  [in] tacc  Beschleunigungsprozentsatz für Zwischenpunkt 2, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] epos_t  Position der Erweiterungsachse an Zwischenpunkt 2, Einheit mm
    * @param  [in] ovl  Geschwindigkeitsskalierungsfaktor [0~100] / physikalische Geschwindigkeit (mm/s)
    * @param  [in] offset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param  [in] offset_pos  Posenversatz
    * @param  [in] oacc Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung (mm/s2)
    * @param  [in] blendR -1: blockierend; 0~1000: Glättungsradius
    * @param  [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit (mm/s) und Beschleunigung (mm/s2)
    * @return  Fehlercode
    */
    errno_t Circle(JointPos* joint_pos_p, DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, JointPos* joint_pos_t, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int velAccParamMode = 0);

Vollkreisbewegung im kartesischen Raum (automatische inverse Kinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Vollkreisbewegung im kartesischen Raum (automatische inverse Kinematik)
    * @param [in] desc_pos_p  Kartesische Pose von Zwischenpunkt 1
    * @param [in] ptool Werkzeugkoordinatennummer für Zwischenpunkt 1, Bereich [0~14]
    * @param [in] puser Werkstückkoordinatennummer für Zwischenpunkt 1, Bereich [0~14]
    * @param [in] pvel Geschwindigkeitsprozentsatz für Zwischenpunkt 1, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz für Zwischenpunkt 1, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_p Position der Erweiterungsachse an Zwischenpunkt 1, Einheit mm
    * @param [in] desc_pos_t  Kartesische Pose von Zwischenpunkt 2
    * @param [in] ttool Werkzeugkoordinatennummer für Zwischenpunkt 2, Bereich [0~14]
    * @param [in] tuser Werkstückkoordinatennummer für Zwischenpunkt 2, Bereich [0~14]
    * @param [in] tvel Geschwindigkeitsprozentsatz für Zwischenpunkt 2, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz für Zwischenpunkt 2, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_t Position der Erweiterungsachse an Zwischenpunkt 2, Einheit mm
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] oacc Beschleunigungsprozentsatz
    * @param [in] blendR -1: blockierend; 0~1000: Glättungsradius
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen
    * @return Fehlercode
    */
    errno_t Circle(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int config = -1);

Punkt-zu-Punkt-Bewegung im kartesischen Raum (MoveCart)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Punkt-zu-Punkt-Bewegung im kartesischen Raum (MoveCart)
    * @param  [in]  desc_pos  Ziel-Kartesische Pose oder Poseninkrement
    * @param  [in] tool  Werkzeugkoordinatennummer, Bereich [0~14]
    * @param  [in] user  Werkstückkoordinatennummer, Bereich [0~14]
    * @param  [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param  [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] ovl  Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param  [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit ms
    * @param  [in] config  Konfiguration des Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen, Standard -1
    * @return  Fehlercode
    */
    errno_t  MoveCart(DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Codebeispiel für grundlegende Roboter-Bewegungsbefehle
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
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

Spiralbewegung im kartesischen Raum (NewSpiral)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Spiralbewegung im kartesischen Raum (NewSpiral)
    * @param  [in] joint_pos  Ziel-Gelenkposition, Einheit deg
    * @param  [in] desc_pos   Ziel-Kartesische Pose
    * @param  [in] tool  Werkzeugkoordinatennummer, Bereich [0~14]
    * @param  [in] user  Werkstückkoordinatennummer, Bereich [0~14]
    * @param  [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param  [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] epos  Position der Erweiterungsachse, Einheit mm
    * @param  [in] ovl  Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param  [in] offset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param  [in] offset_pos  Posenversatz
    * @param  [in] spiral_param  Spiralparameter
    * @return  Fehlercode
    */
    errno_t  NewSpiral(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, ExaxisPos *epos, float ovl, uint8_t offset_flag, DescPose *offset_pos, SpiralParam spiral_param);

Spiralbewegung im kartesischen Raum (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Spiralbewegung im kartesischen Raum (automatische inverse Kinematik)
    * @param [in] desc_pos  Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos Position der Erweiterungsachse, Einheit mm
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] spiral_param Spiralparameter
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen
    * @return Fehlercode
    */
    errno_t NewSpiral(DescPose* desc_pos, int tool, int user, float vel, float acc, ExaxisPos* epos, float ovl, uint8_t offset_flag, DescPose* offset_pos, SpiralParam spiral_param, int config = -1);

Codebeispiel für Spiralbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpiral(void)
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
      JointPos j(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose offset_pos1(50, 0, 0, -30, 0, 0);
      DescPose offset_pos2(50, 0, 0, -5, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      SpiralParam sp;
      sp.circle_num = 5;
      sp.circle_angle = 5.0;
      sp.rad_init = 50.0;
      sp.rad_add = 10.0;
      sp.rotaxis_add = 10.0;
      sp.rot_direction = 0;
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = 0.0;
      uint8_t flag = 2;
      robot.SetSpeed(20);
      rtn = robot.MoveJ(&j, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos1);
      printf("movej errcode:%d\n", rtn);
      rtn = robot.NewSpiral(&desc_pos, tool, user, vel, acc, &epos, ovl, flag, &offset_pos2, sp);
      printf("newspiral errcode:%d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Servo-Modus Bewegung starten
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Servo-Modus Bewegung starten (in Verbindung mit ServoJ, ServoCart)
    * @return Fehlercode
    */
    errno_t ServoMoveStart();

Servo-Modus Bewegung beenden
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Servo-Modus Bewegung beenden (in Verbindung mit ServoJ, ServoCart)
    * @return Fehlercode
    */
    errno_t ServoMoveEnd();

Servo-Modus Bewegung im Gelenkraum (ServoJ)
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Servo-Modus Bewegung im Gelenkraum (ServoJ)
    * @param  [in] joint_pos  Ziel-Gelenkposition, Einheit deg
    * @param  [in] axisPos  Position der externen Achse, Einheit mm
    * @param  [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar, Standard 0
    * @param  [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100], vorerst nicht verfügbar, Standard 0
    * @param  [in] cmdT  Befehlsübermittlungszyklus, Einheit s, empfohlen [0.001~0.0016]
    * @param  [in] filterT Filterzeit, Einheit s, vorerst nicht verfügbar, Standard 0
    * @param  [in] gain  Proportionalverstärkung für Zielposition, vorerst nicht verfügbar, Standard 0
    * @param  [in] id servoJ Befehls-ID, Standard 0
    * @return  Fehlercode
    */
    errno_t ServoJ(JointPos *joint_pos, ExaxisPos* axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0);

Beispielprogramm für Servo-Modus Bewegung im Gelenkraum (ServoJ)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoJ(void)
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
        JointPos j(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        float vel = 0.0;
        float acc = 0.0;
        float cmdT = 0.008;
        float filterT = 0.0;
        float gain = 0.0;
        uint8_t flag = 0;
        int count = 500;
        float dt = 0.1;
        int cmdID = 0;
        int ret = robot.GetActualJointPosDegree(flag, &j);
        if (ret == 0)
        {
            robot.ServoMoveStart();
            while (count)
            {
                robot.ServoJ(&j, &epos, acc, vel, cmdT, filterT, gain, cmdID);
                j.jPos[0] += dt;
                count -= 1;
                robot.WaitMs(cmdT * 1000);
            }
            robot.ServoMoveEnd();
        }
        else
        {
            printf("GetActualJointPosDegree errcode:%d\n", ret);
        }
        robot.CloseRPC();
        return 0;
    }

Gelenk-Drehmomentregelung starten (ServoJT)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Drehmomentregelung starten (ServoJT)
    * @return Fehlercode
    */
    errno_t ServoJTStart();

Gelenk-Drehmomentregelung (ServoJT)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Drehmomentregelung (ServoJT)
    * @param  [in] torque j1~j6 Gelenkdrehmomente, Einheit Nm
    * @param  [in] interval Befehlszyklus, Einheit s, Bereich [0.001~0.008]
    * @param  [in] checkFlag Erkennungsstrategie 0-keine Einschränkung; 1-Leistungsbegrenzung; 2-Geschwindigkeitsbegrenzung; 3-Leistungs- und Geschwindigkeitsbegrenzung gleichzeitig
    * @param  [in] jPowerLimit Maximale Gelenkleistungsbegrenzung (W)
    * @param  [in] jVelLimit Maximale Gelenkgeschwindigkeit (°/s)
    * @return  Fehlercode
    */
    errno_t ServoJT(float torque[], double interval, int checkFlag, double jPowerLimit[6], double jVelLimit[6]);

Gelenk-Drehmomentregelung beenden (ServoJT)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gelenk-Drehmomentregelung beenden (ServoJT)
    * @return Fehlercode
    */
    errno_t ServoJTEnd();

Codebeispiel für Gelenk-Drehmomentregelung (ServoJT)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestServoJT(void)
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
         float torques[] = { 0, 0, 0, 0, 0, 0 };
         robot.GetJointTorques(1, torques);
         int count = 100;
         robot.ServoJTStart(); 
         int error = 0;
         while (count > 0)
         {
             error = robot.ServoJT(torques, 0.001);
             count = count - 1;
             robot.Sleep(1);
         }
         error = robot.ServoJTEnd();
         robot.DragTeachSwitch(0);
         robot.CloseRPC();
         return 0;
     }

Codebeispiel für Gelenk-Drehmomentregelung mit Überdrehzahlschutz
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int ServoJTWithSafety(FRRobot* robot)
    {
        robot->ResetAllError();
        robot->Sleep(500);
        float torques[] = { 0, 0, 0, 0, 0, 0 };
        robot->GetJointTorques(1, torques);
        robot->ServoJTStart(); 
        ROBOT_STATE_PKG pkg = {};
        robot->DragTeachSwitch(1);
        int checkFlag = 3;
        //double jPowerLimit[6] = {1, 1, 1, 1, 1, 1}; 
        double jPowerLimit[6] = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double jVelLimit[6] = { 181, 80, 80, 80, 80, 80 };
        int count = 800000;
        int error = 0;
        while (count > 0)
        {
            torques[2] = torques[2] + 0.01;
            error = robot->ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit); 
            if (error != 0)
            {
                robot->ServoJTEnd();
            }
            printf("ServoJT rtn is %d\n", error);
            count = count - 1;
            robot->Sleep(1);
            robot->GetRobotRealTimeState(&pkg);
            printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
        }
        robot->DragTeachSwitch(0);
        error = robot->ServoJTEnd();  
        return 0;
    }

Servo-Modus Bewegung im kartesischen Raum (ServoCart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Servo-Modus Bewegung im kartesischen Raum (ServoCart)
    * @param [in] mode 0-Absolutbewegung (Basiskoordinatensystem), 1-Inkrementalbewegung (Basiskoordinatensystem), 2-Inkrementalbewegung (Werkzeugkoordinatensystem)
    * @param [in] desc_pos Ziel-Kartesische Pose oder Poseninkrement
    * @param [in] exaxis Position der Erweiterungsachse
    * @param [in] pos_gain Proportionalbeiwert für Poseninkrement, nur bei inkrementaler Bewegung wirksam, Bereich [0~1]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar, Standard 0
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100], vorerst nicht verfügbar, Standard 0
    * @param [in] cmdT Befehlsübermittlungszyklus, Einheit s, empfohlen [0.001~0.016]
    * @param [in] filterT Filterzeit, Einheit s, vorerst nicht verfügbar, Standard 0
    * @param [in] gain Proportionalverstärkung für Zielposition, vorerst nicht verfügbar, Standard 0
    * @return Fehlercode
    */
    errno_t ServoCart(int mode, DescPose *desc_pose, ExaxisPos exaxis, float pos_gain[6], float acc, float vel, float cmdT, float filterT, float gain);

Codebeispiel für Servo-Modus Bewegung im kartesischen Raum (ServoCart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoCart(void)
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
        DescPose desc_pos_dt = { 83.00800, 50.525000 , 29.246 , 179.629 , -7.138 , -166.975 };
        ExaxisPos exaxis = { 100.0, 0.0, 0.0, 0.0 };
        float pos_gain[6] = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int mode = 0;
        float vel = 0.0;
        float acc = 0.0;
        float cmdT = 0.001;
        float filterT = 0.0;
        float gain = 0.0;
        uint8_t flag = 0;
        int count = 5000;
        robot.SetSpeed(20);
        while (count)
        {
            rtn = robot.ServoCart(mode, &desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            printf("ServoCart rtn is %d\n", rtn);
            count -= 1;
            desc_pos_dt.tran.x += 0.01;
            exaxis.ePos[0] += 0.01;
        }
        robot.CloseRPC();
        return 0;
    }

Spline-Bewegung starten
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Spline-Bewegung starten
    * @return  Fehlercode
    */
    errno_t  SplineStart();

Spline-Bewegung im Gelenkraum (automatische Vorwärtskinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Spline-Bewegung im Gelenkraum (automatische Vorwärtskinematik)
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @return Fehlercode
    */
    errno_t SplinePTP(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl);

Spline-PTP-Bewegung
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Spline-PTP-Bewegung im Gelenkraum
    * @param  [in] joint_pos  Ziel-Gelenkposition, Einheit deg
    * @param  [in] desc_pos   Ziel-Kartesische Pose
    * @param  [in] tool  Werkzeugkoordinatennummer, Bereich [0~14]
    * @param  [in] user  Werkstückkoordinatennummer, Bereich [0~14]
    * @param  [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param  [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param  [in] ovl  Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @return  Fehlercode
    */
    errno_t  SplinePTP(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl);

Spline-Bewegung beenden
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Spline-Bewegung beenden
    * @return  Fehlercode
    */
    errno_t  SplineEnd();

Codebeispiel für Spline-Bewegung
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpline(void)
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
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, &desc_pos1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, &desc_pos2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, &desc_pos3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, &desc_pos4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      robot.CloseRPC();
      return 0;
    }

Neue Spline-Bewegung starten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Neue Spline-Bewegung starten (NewSpline)
    * @param [in] type  0-Kreisbogenübergang, 1-gegebene Punkte sind Bahnpunkte
    * @param [in] averageTime Globale durchschnittliche Übergangszeit (ms) (10 ~ ), Standard 2000
    * @return Fehlercode
    */
    errno_t NewSplineStart(int type, int averageTime=2000);

Neuer Spline-Befehlspunkt
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Neuer Spline-Befehlspunkt
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg
    * @param [in] desc_pos  Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param  [in] lastFlag Ist dies der letzte Punkt? 0-nein, 1-ja
    * @return Fehlercode
    */
    errno_t NewSplinePoint(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Neuer Spline-Befehlspunkt (automatische inverse Kinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Neuer Spline-Befehlspunkt (automatische inverse Kinematik)
    * @param [in] desc_pos  Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param [in] lastFlag Ist dies der letzte Punkt? 0-nein, 1-ja
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen
    * @return Fehlercode
    */
    errno_t NewSplinePoint(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag, int config = -1);

Neue Spline-Bewegung beenden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Neue Spline-Bewegung beenden
    * @return Fehlercode
    */
    errno_t NewSplineEnd();

Codebeispiel für neue Spline-Bewegung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestNewSpline(void)
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
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&j1, &desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j2, &desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j3, &desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j4, &desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j5, &desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      robot.CloseRPC();
      return 0;
    }

Bewegung abbrechen (StopMotion)
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung abbrechen
    * @return  Fehlercode
    */
    errno_t  StopMotion();

Bewegung pausieren (PauseMotion)
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung pausieren
    * @return Fehlercode
    */
    errno_t PauseMotion();

Bewegung fortsetzen (ResumeMotion)
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung fortsetzen
    * @return Fehlercode
    */
    errno_t ResumeMotion();

Codebeispiel für Bewegung pausieren, fortsetzen, abbrechen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestPause(void)
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
         JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         rtn = robot.MoveJ(&j5, &desc_pos5, tool, user, vel, acc, ovl, &epos, 1, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PauseMotion();
         robot.Sleep(1000);
         robot.ResumeMotion();
         robot.Sleep(1000);
         robot.StopMotion();
         robot.Sleep(1000);
         robot.CloseRPC();
         return 0;
     }

Globalen Punktversatz aktivieren
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Globalen Punktversatz aktivieren
    * @param  [in]  flag  0-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param  [in] offset_pos  Posenversatz
    * @return  Fehlercode
    */
    errno_t  PointsOffsetEnable(int flag, DescPose *offset_pos);

Globalen Punktversatz deaktivieren
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Globalen Punktversatz deaktivieren
    * @return  Fehlercode
    */
    errno_t  PointsOffsetDisable();

Codebeispiel für Punktversatz
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestOffset(void)
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
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PointsOffsetEnable(0, &offset_pos1);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.PointsOffsetDisable();
         robot.CloseRPC();
         return 0;
     }

Steuerschrank AO High-Speed-Ausgabe starten (MoveAOStart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Steuerschrank AO High-Speed-Ausgabe starten
    * @param [in] AONum Steuerschrank AO-Nummer
    * @param [in] maxTCPSpeed Maximaler TCP-Geschwindigkeitswert [1-5000 mm/s], Standard 1000
    * @param [in] maxAOPercent AO-Prozentsatz für maximale TCP-Geschwindigkeit, Standard 100%
    * @param [in] zeroZoneCmp AO-Prozentsatz für Totzonenkompensation, Ganzzahl, Standard 20%, Bereich [0-100]
    * @return Fehlercode
    */
    errno_t MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Steuerschrank AO High-Speed-Ausgabe stoppen (MoveAOStop)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Steuerschrank AO High-Speed-Ausgabe stoppen
    * @return Fehlercode
    */
    errno_t MoveAOStop();

Endeffektor AO High-Speed-Ausgabe starten (MoveToolAOStart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor AO High-Speed-Ausgabe starten
    * @param [in] AONum Endeffektor AO-Nummer
    * @param [in] maxTCPSpeed Maximaler TCP-Geschwindigkeitswert [1-5000 mm/s], Standard 1000
    * @param [in] maxAOPercent AO-Prozentsatz für maximale TCP-Geschwindigkeit, Standard 100%
    * @param [in] zeroZoneCmp AO-Prozentsatz für Totzonenkompensation, Ganzzahl, Standard 20%, Bereich [0-100]
    * @return Fehlercode
    */
    errno_t MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Endeffektor AO High-Speed-Ausgabe stoppen (MoveToolAOStop)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Endeffektor AO High-Speed-Ausgabe stoppen
    * @return Fehlercode
    */
    errno_t MoveToolAOStop();

Codebeispiel für AO High-Speed-Ausgabe (MoveAO)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestMoveAO(void)
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
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 20.0;
         float acc = 20.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveAOStop();
         robot.Sleep(1000);
         robot.MoveToolAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveToolAOStop();
         robot.CloseRPC();
         return 0;
     }

PTP-Bewegung mit FIR-Filterung starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
    * @brief PTP-Bewegung mit FIR-Filterung starten
    * @param [in] maxAcc Maximale Beschleunigung (deg/s²)
    * @param [in] maxJek Maximale einheitliche Gelenkruck (deg/s³)
    * @return Fehlercode
    */
    errno_t PtpFIRPlanningStart(double maxAcc, double maxJek = 1000);

PTP-Bewegung mit FIR-Filterung beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
    * @brief PTP-Bewegung mit FIR-Filterung beenden
    * @return Fehlercode
    */
    errno_t PtpFIRPlanningEnd();

LIN-/ARC-Bewegung mit FIR-Filterung starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
    * @brief LIN-/ARC-Bewegung mit FIR-Filterung starten
    * @param [in] maxAccLin Maximale Linearbeschleunigung (mm/s²)
    * @param [in] maxAccDeg Maximale Winkelbeschleunigung (deg/s²)
    * @param [in] maxJerkLin Maximaler Linearruck (mm/s³)
    * @param [in] maxJerkDeg Maximaler Winkelruck (deg/s³)
    * @return Fehlercode
    */
    errno_t LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

LIN-/ARC-Bewegung mit FIR-Filterung beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
    * @brief LIN-/ARC-Bewegung mit FIR-Filterung beenden
    * @return Fehlercode
    */
    errno_t LinArcFIRPlanningEnd();

Codebeispiel für FIR-Filterung
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

     int TestFIR(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos midjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         JointPos endjointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose middescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose enddescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.PtpFIRPlanningStart(1000, 1000);
         cout << "PtpFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.PtpFIRPlanningEnd();
         cout << "PtpFIRPlanningEnd rtn is " << rtn << endl;
         robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
         cout << "LinArcFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveL(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
         robot.MoveC(&midjointPos, &middescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, &endjointPos, &enddescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, 100, -1);
         robot.LinArcFIRPlanningEnd();
         cout << "LinArcFIRPlanningEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Beschleunigungsglättung aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Beschleunigungsglättung aktivieren
    * @param [in] saveFlag Bei Stromausfall speichern? (0-nein, 1-ja)
    * @return Fehlercode
    */
    errno_t AccSmoothStart(bool saveFlag);

Beschleunigungsglättung deaktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Beschleunigungsglättung deaktivieren
    * @param [in] saveFlag Bei Stromausfall speichern? (0-nein, 1-ja)
    * @return Fehlercode
    */
    errno_t AccSmoothEnd(bool saveFlag);

Codebeispiel für Beschleunigungsglättung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAccSmooth(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AccSmoothStart(0);
         cout << "AccSmoothStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AccSmoothEnd(0);
         cout << "AccSmoothEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Spezifische Ausrichtungsgeschwindigkeit aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Spezifische Ausrichtungsgeschwindigkeit aktivieren
    * @param [in] ratio Ausrichtungsgeschwindigkeitsprozentsatz [0-300]
    * @return Fehlercode
    */
    errno_t AngularSpeedStart(int ratio);

Spezifische Ausrichtungsgeschwindigkeit deaktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Spezifische Ausrichtungsgeschwindigkeit deaktivieren
    * @return Fehlercode
    */
    errno_t AngularSpeedEnd();

Codebeispiel für spezifische Ausrichtungsgeschwindigkeit
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAngularSpeed(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AngularSpeedStart(50);
         cout << "AngularSpeedStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AngularSpeedEnd();
         cout << "AngularSpeedEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Singularitätsschutz starten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Singularitätsschutz starten
    * @param [in] protectMode Singularitätsschutzmodus, 0: Gelenkmodus; 1: Kartesischer Modus
    * @param [in] minShoulderPos Einstellbereich für Schulter-Singularität (mm), Standard 100
    * @param [in] minElbowPos Einstellbereich für Ellenbogen-Singularität (mm), Standard 50
    * @param [in] minWristPos Einstellbereich für Handgelenks-Singularität (°), Standard 10
    * @return Fehlercode
    */
    errno_t SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Singularitätsschutz stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Singularitätsschutz stoppen
    * @return Fehlercode
    */
    errno_t SingularAvoidEnd();

Codebeispiel für Roboter-Singularitätsschutz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestSingularAvoid(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.SingularAvoidStart(2, 10, 5, 5);
         cout << "SingularAvoidStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.SingularAvoidEnd();
         cout << "SingularAvoidEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Bewegungsbefehlswarteschlange leeren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegungsbefehlswarteschlange leeren
    * @return Fehlercode
    */
    errno_t MotionQueueClear();

Zum Startpunkt einer Durchdringungskurve bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zum Startpunkt einer Durchdringungskurve bewegen
    * @param [in] mainPoint Kartesische Posen der 6 Teach-Punkte des Hauptrohrs
    * @param [in] mainExaxisPos Positionen der Erweiterungsachse für die 6 Teach-Punkte des Hauptrohrs
    * @param [in] piecePoint Kartesische Posen der 6 Teach-Punkte des Nebenrohrs
    * @param [in] pieceExaxisPos Positionen der Erweiterungsachse für die 6 Teach-Punkte des Nebenrohrs
    * @param [in] extAxisFlag Erweiterungsachse verwenden? 0-nein; 1-ja
    * @param [in] exaxisPos Startposition der Erweiterungsachse
    * @param [in] tool Werkzeugkoordinatensystem-Nummer
    * @param [in] wobj Werkstückkoordinatensystem-Nummer
    * @param [in] vel Geschwindigkeitsprozentsatz
    * @param [in] acc Beschleunigungsprozentsatz
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor
    * @param [in] oacc Beschleunigungsskalierungsfaktor
    * @param [in] moveType Bewegungstyp; 0-PTP; 1-LIN
    * @param [in] moveDirection Bewegungsrichtung; 0-im Uhrzeigersinn; 1-gegen Uhrzeigersinn
    * @param [in] offset Versatz
    * @return Fehlercode
    */
    errno_t MoveToIntersectLineStart(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);

Bewegung entlang einer Durchdringungskurve
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung entlang einer Durchdringungskurve
    * @param [in] mainPoint Kartesische Posen der 6 Teach-Punkte des Hauptrohrs
    * @param [in] mainExaxisPos Positionen der Erweiterungsachse für die 6 Teach-Punkte des Hauptrohrs
    * @param [in] piecePoint Kartesische Posen der 6 Teach-Punkte des Nebenrohrs
    * @param [in] pieceExaxisPos Positionen der Erweiterungsachse für die 6 Teach-Punkte des Nebenrohrs
    * @param [in] extAxisFlag Erweiterungsachse verwenden? 0-nein; 1-ja
    * @param [in] exaxisPos Positionen der Erweiterungsachse (Array der Länge 4)
    * @param [in] tool Werkzeugkoordinatensystem-Nummer
    * @param [in] wobj Werkstückkoordinatensystem-Nummer
    * @param [in] vel Geschwindigkeitsprozentsatz
    * @param [in] acc Beschleunigungsprozentsatz
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor
    * @param [in] oacc Beschleunigungsskalierungsfaktor
    * @param [in] moveDirection Bewegungsrichtung; 0-im Uhrzeigersinn; 1-gegen Uhrzeigersinn
    * @param [in] offset Versatz
    * @return Fehlercode
    */
    errno_t MoveIntersectLine(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos[4], int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);

Codebeispiel für Bewegung entlang einer Durchdringungskurve
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void TestIntersectLineMove()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(3);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return ;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose mainPoint[6] = {};
        DescPose piecePoint[6] = {};
        ExaxisPos mainExaxisPos[6] = {};
        ExaxisPos pieceExaxisPos[6] = {};
        int extAxisFlag = 1;
        ExaxisPos exaxisPos[4] = {};
        DescPose offset = { 0.0, 2.0 ,30.0, -2.0, 0.0, 0.0 };
        mainPoint[0] = {490.004, -383.194, 402.735, -9.332, -1.528, 69.594};
        mainPoint[1] = {444.950, -407.117, 389.011, -5.546, -2.196, 65.279};
        mainPoint[2] = {445.168, -463.605, 355.759, -1.544, -10.886, 57.104};
        mainPoint[3] = {507.529, -485.385, 343.013, -0.786, -4.834, 61.799};
        mainPoint[4] = {554.390, -442.647, 367.701, -4.761, -10.181, 64.925};
        mainPoint[5] = {532.552, -394.003, 396.467, -13.732, -13.592, 67.411};
        mainExaxisPos[0] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[1] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[2] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[3] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[4] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[5] = { -29.996, 0.000, 0.000, 0.000 };
        piecePoint[0] = { 505.571, -192.408, 316.759, 38.098, 37.051, 139.447 };
        piecePoint[1] = {533.837, -201.558, 332.340, 34.644, 42.339, 137.748};
        piecePoint[2] = {530.386, -225.085, 373.808, 35.431, 45.111, 137.560};
        piecePoint[3] = {485.646, -229.195, 383.778, 33.870, 45.173, 137.064};
        piecePoint[4] = {460.551, -212.161, 354.256, 28.856, 45.602, 135.930};
        piecePoint[5] = {474.217, -197.124, 324.611, 42.469, 41.133, 148.167};
        pieceExaxisPos[0] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[1] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[2] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[3] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[4] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[5] = { -29.996, -0.000, 0.000, 0.000 };
        exaxisPos[0] = {-29.996, -0.000, 0.000, 0.000};
        exaxisPos[1] = {-44.994, 90.000, 0.000, 0.000};
        exaxisPos[2] = {-59.992, 0.002, 0.000, 0.000};
        exaxisPos[3] = {-44.994, -89.997, 0.000, 0.000};
        int tool = 2;
        int wobj = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 12.0;
        double oacc = 12.0; 
        int moveType = 1;
        int moveDirection = 1;
        rtn = robot.MoveToIntersectLineStart(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos[0], tool, wobj, vel, acc, ovl, oacc, moveType, moveDirection, offset);
        printf("MoveToIntersectLineStart rtn is %d\n", rtn);
        rtn = robot.MoveIntersectLine(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos, tool, wobj, vel, acc, 5.0, 5.0, moveDirection, offset);
        printf("MoveIntersectLine rtn is %d\n", rtn);
        robot.CloseRPC();
        return ;
    }

Bewegung auf der Stelle (ohne Positionsänderung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung auf der Stelle (ohne Positionsänderung)
    * @return Fehlercode
    */
    errno_t MoveStationary();

Codebeispiel für Bewegung auf der Stelle
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLaserStationary(void)
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
        rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 0, 10, 100);
        printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        rtn = robot.MoveStationary();
        printf("MoveStationary rtn is %d\n", rtn);
        rtn = robot.LaserSensorRecord1(0, 10);
        printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }