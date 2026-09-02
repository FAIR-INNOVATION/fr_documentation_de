Roboterbewegung
===============

.. toctree::
    :maxdepth: 5

JOG-Tippbetrieb
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief JOG-Tippbetrieb
    * @param [in] refType Tippbetrieb-Typ: 0-Gelenk-JOG, 2-JOG im Basiskoordinatensystem, 4-JOG im Werkzeugkoordinatensystem, 8-JOG im Werkstückkoordinatensystem
    * @param [in] nb 1-Gelenk 1 (oder x-Achse), 2-Gelenk 2 (oder y-Achse), 3-Gelenk 3 (oder z-Achse), 4-Gelenk 4 (oder Rotation um x-Achse), 5-Gelenk 5 (oder Rotation um y-Achse), 6-Gelenk 6 (oder Rotation um z-Achse)
    * @param [in] dir 0-negative Richtung, 1-positive Richtung
    * @param [in] vel Geschwindigkeitsprozentsatz, [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, [0~100]
    * @param [in] max_dis Maximaler Winkel pro Tippbewegung [°] oder Distanz [mm]
    * @return Fehlercode
    */
    int StartJOG(byte refType, byte nb, byte dir, float vel, float acc, float max_dis);

JOG-Tippbetrieb mit Verzögerung stoppen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief JOG-Tippbetrieb mit Verzögerung stoppen
    * @param [in] stopType 1-Gelenk-JOG stoppen, 3-JOG im Basiskoordinatensystem stoppen, 5-JOG im Werkzeugkoordinatensystem stoppen, 9-JOG im Werkstückkoordinatensystem stoppen
    * @return Fehlercode
    */
    int StopJOG(byte stopType);

JOG-Tippbetrieb sofort stoppen
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief JOG-Tippbetrieb sofort stoppen
    * @return Fehlercode
    */
    int ImmStopJOG();

Codebeispiel für Roboter-JOG-Steuerung
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnJOG_Click(object sender, EventArgs e)
    {
        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(0, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.ImmStopJOG();
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(2, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.ImmStopJOG();
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(4, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.StopJOG(5);
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(8, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.StopJOG(9);
            Thread.Sleep(1000);
        }
    }

Bewegung im Gelenkraum
++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegung im Gelenkraum
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend) [ms]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    int MoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Bewegung im Gelenkraum (automatische Vorwärtskinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegung im Gelenkraum (automatische Vorwärtskinematik)
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend) [ms]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    int MoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)

Linearbewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Linearbewegung im kartesischen Raum
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0~100] / physikalische Geschwindigkeit [mm/s]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] blendMode Übergangsmodus; 0-Innenliegender Übergang; 1-Eckpunktübergang
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] search 0-keine Schweißdrahtsuche, 1-Schweißdrahtsuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] oacc Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung [mm/s²]
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @param [in] overSpeedStrategy Strategie bei Übergeschwindigkeit, 1-Standard; 2-Fehlerstopp bei Übergeschwindigkeit; 3-adaptive Geschwindigkeitsreduzierung, Standard = 0
    * @param [in] speedPercent Erlaubter Schwellwert für Geschwindigkeitsreduzierung in Prozent [0-100], Standard 10%
    * @return Fehlercode
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, float oacc, int velAccParamMode, int overSpeedStrategy = 0, int speedPercent = 10)

Linearbewegung im kartesischen Raum (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Linearbewegung im kartesischen Raum (automatische inverse Kinematik)
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] user Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] blendMode Übergangsmodus; 0-Innenliegender Übergang; 1-Eckpunktübergang
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] search 0-keine Schweißdrahtsuche, 1-Schweißdrahtsuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @param [in] overSpeedStrategy Strategie bei Übergeschwindigkeit, 1-Standard; 2-Fehlerstopp bei Übergeschwindigkeit; 3-adaptive Geschwindigkeitsreduzierung, Standard = 0
    * @param [in] speedPercent Erlaubter Schwellwert für Geschwindigkeitsreduzierung in Prozent [0-100], Standard 10%
    * @return Fehlercode
    */
    int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int overSpeedStrategy, int speedPercent)

Linearbewegung im kartesischen Raum (mit Parameter velAccParamMode)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Linearbewegung im kartesischen Raum (mit Parameter velAccParamMode)
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] user Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] search 0-keine Schweißdrahtsuche, 1-Schweißdrahtsuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @param [in] overSpeedStrategy Strategie bei Übergeschwindigkeit, 1-Standard; 2-Fehlerstopp bei Übergeschwindigkeit; 3-adaptive Geschwindigkeitsreduzierung, Standard = 0
    * @param [in] speedPercent Erlaubter Schwellwert für Geschwindigkeitsreduzierung in Prozent [0-100], Standard 10%
    * @return Fehlercode
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Linearbewegung im kartesischen Raum (Überladung 1 mit blendMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Linearbewegung im kartesischen Raum (Überladung 1 mit blendMode)
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] user Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] blendMode Übergangsmodus; 0-Innenliegender Übergang; 1-Eckpunktübergang
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] search 0-keine Schweißdrahtsuche, 1-Schweißdrahtsuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @param [in] overSpeedStrategy Strategie bei Übergeschwindigkeit, 1-Standard; 2-Fehlerstopp bei Übergeschwindigkeit; 3-adaptive Geschwindigkeitsreduzierung, Standard = 0
    * @param [in] speedPercent Erlaubter Schwellwert für Geschwindigkeitsreduzierung in Prozent [0-100], Standard 10%
    * @return Fehlercode
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Linearbewegung im kartesischen Raum (Überladung 2 ohne Gelenkposition)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Linearbewegung im kartesischen Raum (Überladung 2 ohne Gelenkposition)
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] user Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] blendMode Übergangsmodus; 0-Innenliegender Übergang; 1-Eckpunktübergang
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] search 0-keine Schweißdrahtsuche, 1-Schweißdrahtsuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @param [in] overSpeedStrategy Strategie bei Übergeschwindigkeit, 1-Standard; 2-Fehlerstopp bei Übergeschwindigkeit; 3-adaptive Geschwindigkeitsreduzierung, Standard = 0
    * @param [in] speedPercent Erlaubter Schwellwert für Geschwindigkeitsreduzierung in Prozent [0-100], Standard 10%
    * @return Fehlercode
    */
    public int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Kreisbogenbewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kreisbogenbewegung im kartesischen Raum
    * @param [in] joint_pos_p Gelenkposition des Zwischenpunkts [°]
    * @param [in] desc_pos_p Kartesische Pose des Zwischenpunkts
    * @param [in] ptool Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] puser Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] pvel Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt [mm]
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zwischenpunkt)
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt
    * @param [in] joint_pos_t Gelenkposition des Zielpunkts [°]
    * @param [in] desc_pos_t Kartesische Pose des Zielpunkts
    * @param [in] ttool Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tuser Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tvel Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt [mm]
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zielpunkt)
    * @param [in] offset_pos_t Posenversatz für Zielpunkt
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0~100] / physikalische Geschwindigkeit [mm/s]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] oacc Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung [mm/s²]
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @return Fehlercode
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR, float oacc, int velAccParamMode)

Kreisbogenbewegung im kartesischen Raum (automatische inverse Kinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Kreisbogenbewegung im kartesischen Raum (automatische inverse Kinematik)
    * @param [in] desc_pos_p Kartesische Pose des Zwischenpunkts
    * @param [in] ptool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] puser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] pvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt [mm]
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zwischenpunkt)
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt
    * @param [in] desc_pos_t Kartesische Pose des Zielpunkts
    * @param [in] ttool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] tuser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] tvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt [mm]
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zielpunkt)
    * @param [in] offset_pos_t Posenversatz für Zielpunkt
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @return Fehlercode
    */
    int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config)

Kreisbogenbewegung im kartesischen Raum (mit Parameter velAccParamMode)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Kreisbogenbewegung im kartesischen Raum (mit Parameter velAccParamMode)
    * @param [in] joint_pos_p Gelenkposition des Zwischenpunkts [°]
    * @param [in] desc_pos_p Kartesische Pose des Zwischenpunkts
    * @param [in] ptool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] puser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] pvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt [mm]
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zwischenpunkt)
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt
    * @param [in] joint_pos_t Gelenkposition des Zielpunkts [°]
    * @param [in] desc_pos_t Kartesische Pose des Zielpunkts
    * @param [in] ttool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] tuser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] tvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt [mm]
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zielpunkt)
    * @param [in] offset_pos_t Posenversatz für Zielpunkt
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @return Fehlercode
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int velAccParamMode)

Kreisbogenbewegung im kartesischen Raum (Überladung 1 ohne Gelenkposition)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Kreisbogenbewegung im kartesischen Raum (Überladung 1 ohne Gelenkposition)
    * @param [in] desc_pos_p Kartesische Pose des Zwischenpunkts
    * @param [in] ptool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] puser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] pvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt [mm]
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zwischenpunkt)
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt
    * @param [in] desc_pos_t Kartesische Pose des Zielpunkts
    * @param [in] ttool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] tuser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] tvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt [mm]
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zielpunkt)
    * @param [in] offset_pos_t Posenversatz für Zielpunkt
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @return Fehlercode
    */
    public int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config, int velAccParamMode)

Punkt-zu-Punkt-Bewegung im kartesischen Raum
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Punkt-zu-Punkt-Bewegung im kartesischen Raum
    * @param [in] desc_pos Ziel-Kartesische Pose im Basiskoordinatensystem
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend) [ms]
    * @param [in] config Konfiguration des Gelenkraums, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration, Standard = -1
    * @return Fehlercode
    */
    int MoveCart(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Vollkreisbewegung im kartesischen Raum
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4 Web-3.8.3

.. code-block:: c#
    :linenos:

    /**
    * @brief Vollkreisbewegung im kartesischen Raum
    * @param [in] joint_pos_p Gelenkposition des ersten Pfadpunkts [°]
    * @param [in] desc_pos_p Kartesische Pose des ersten Pfadpunkts
    * @param [in] ptool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] puser Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] pvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am ersten Pfadpunkt [mm]
    * @param [in] joint_pos_t Gelenkposition des zweiten Pfadpunkts [°]
    * @param [in] desc_pos_t Kartesische Pose des zweiten Pfadpunkts
    * @param [in] ttool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] tuser Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] tvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am zweiten Pfadpunkt [mm]
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0~100] / physikalische Geschwindigkeit [mm/s]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] oacc Beschleunigungsskalierungsfaktor [0-100] / physikalische Beschleunigung [mm/s²]
    * @param [in] blendR -1: blockierend; 0~1000: Glättungsradius
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @return Fehlercode
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, float ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Vollkreisbewegung im kartesischen Raum (automatische inverse Kinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
     * @brief Vollkreisbewegung im kartesischen Raum (automatische inverse Kinematik)
     * @param [in] desc_pos_p Kartesische Pose des ersten Pfadpunkts
     * @param [in] ptool Werkzeugkoordinatennummer, Bereich [0~14]
     * @param [in] puser Werkstückkoordinatennummer, Bereich [0~14]
     * @param [in] pvel Geschwindigkeitsprozentsatz, Bereich [0~100]
     * @param [in] pacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
     * @param [in] epos_p Position der Erweiterungsachse am ersten Pfadpunkt [mm]
     * @param [in] desc_pos_t Kartesische Pose des zweiten Pfadpunkts
     * @param [in] ttool Werkzeugkoordinatennummer, Bereich [0~14]
     * @param [in] tuser Werkstückkoordinatennummer, Bereich [0~14]
     * @param [in] tvel Geschwindigkeitsprozentsatz, Bereich [0~100]
     * @param [in] tacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
     * @param [in] epos_t Position der Erweiterungsachse am zweiten Pfadpunkt [mm]
     * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
     * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
     * @param [in] offset_pos Posenversatz
     * @param [in] oacc Beschleunigungsprozentsatz
     * @param [in] blendR -1: blockierend; 0~1000: Glättungsradius
     * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
     * @return Fehlercode
     */
    int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config)

Vollkreisbewegung im kartesischen Raum (mit Parameter velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Vollkreisbewegung im kartesischen Raum (mit Parameter velAccParamMode)
    * @param [in] joint_pos_p Gelenkposition des ersten Pfadpunkts [°]
    * @param [in] desc_pos_p Kartesische Pose des ersten Pfadpunkts
    * @param [in] ptool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] puser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] pvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am ersten Pfadpunkt [mm]
    * @param [in] joint_pos_t Gelenkposition des zweiten Pfadpunkts [°]
    * @param [in] desc_pos_t Kartesische Pose des zweiten Pfadpunkts
    * @param [in] ttool Werkzeugkoordinatennummer, Bereich [1~15]
    * @param [in] tuser Werkstückkoordinatennummer, Bereich [1~15]
    * @param [in] tvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am zweiten Pfadpunkt [mm]
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] oacc Beschleunigungsprozentsatz
    * @param [in] blendR -1: blockierend; 0~1000: Glättungsradius
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @return Fehlercode
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Vollkreisbewegung im kartesischen Raum (Überladung 1 ohne Gelenkposition)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Vollkreisbewegung im kartesischen Raum (Überladung 1 ohne Gelenkposition)
    * @param [in] desc_pos_p Kartesische Pose des ersten Pfadpunkts
    * @param [in] ptool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] puser Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] pvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am ersten Pfadpunkt [mm]
    * @param [in] desc_pos_t Kartesische Pose des zweiten Pfadpunkts
    * @param [in] ttool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] tuser Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] tvel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am zweiten Pfadpunkt [mm]
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] oacc Beschleunigungsprozentsatz
    * @param [in] blendR -1: blockierend; 0~1000: Glättungsradius
    * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @param [in] velAccParamMode Modus für Geschwindigkeits-/Beschleunigungsparameter; 0-Prozentsatz; 1-physikalische Geschwindigkeit [mm/s] / Beschleunigung [mm/s²]
    * @return Fehlercode
    */
    public int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config, int velAccParamMode)

Codebeispiel für grundlegende Roboterbewegungsbefehle
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
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
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode,0,10);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,desc_pos4, tool, user, vel, acc, epos, flag, offset_pos,ovl, blendR, -1, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
    }

Spiralbewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Spiralbewegung im kartesischen Raum
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] spiral_param Spiralparameter
    * @return Fehlercode
    */
    int NewSpiral(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, ExaxisPos epos, float ovl, byte offset_flag, DescPose offset_pos, SpiralParam spiral_param);

Spiralbewegung im kartesischen Raum (automatische inverse Kinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Spiralbewegung im kartesischen Raum (automatische inverse Kinematik)
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] spiral_param Spiralparameter
    * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @return Fehlercode
    */
    int NewSpiral(DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param, int config)

Codebeispiel für Spiralbewegung
+++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public static int TestSpiral(Robot robot)
    {
        int rtn=-1;
        JointPos j=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose offset_pos1=new DescPose(50, 0, 0, -30, 0, 0);
        DescPose offset_pos2=new DescPose(50, 0, 0, -5, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        SpiralParam sp=new SpiralParam(1,5.0,50.0,10.0,10.0,0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = 0.0;
        int flag = 2;

        rtn = robot.MoveJ(j, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos1);
         Console.WriteLine("movej errcode:"+ rtn);

        rtn = robot.NewSpiral(desc_pos, tool, user, vel, acc, epos, ovl, flag, offset_pos2, sp,-1);
        Console.WriteLine("newspiral errcode:"+ rtn);

        return 0;
    }

Servobewegung Start
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Start der Servobewegung, wird mit ServoJ- und ServoCart-Befehlen verwendet
    * @param[in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoMoveStart (int comType = 0)

Servobewegung Ende
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ende der Servobewegung, wird mit ServoJ- und ServoCart-Befehlen verwendet
    * @param[in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoMoveEnd (int comType = 0)

Gelenkraum-Servomodellbewegung
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Gelenkraum-Servomodellbewegung
    * @param  [in] joint_pos  Zielgelenkposition, Einheit deg
    * @param  [in] axisPos  Externe Achsenposition, Einheit mm
    * @param  [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100], vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] cmdT  Befehlssendezyklus, Einheit s, empfohlener Bereich [0.001~0.0016]
    * @param  [in] filterT Filterzeit, Einheit s, vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] gain  Proportionalverstärker für Zielposition, vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] id ServoJ-Befehls-ID, Standard ist 0
    * @param  [in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return  Fehlercode
    */
    public int ServoJ(JointPos joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

SDK-Codebeispiel für ServoJ, ServoMoveStart, ServoMoveEnd basierend auf UDP-Kommunikation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    public void TestServoJUDP()
    {
        // Callback abonnieren
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 300;
        float dt = 0.1f;
        int cmdID = 0;

        while (true)
        {
            JointPos j = new JointPos(0, -90, 90, 0, 0, 0);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(0, -90, 90, 0, 0, 0);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            int ret = robot.GetActualJointPosDegree(flag, ref j);
            if (ret == 0)
            {
                count = 300;
                cmdID += 1;
                robot.ServoMoveStart(1);

                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] += dt;
                    j.jPos[1] += dt;
                    j.jPos[3] += dt;
                    j.jPos[4] += dt;
                    j.jPos[5] += dt;
                    epos.ePos[0] += dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);

                Thread.Sleep(1000);
                count = 300;
                robot.ServoMoveStart(1);
                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] -= dt;
                    j.jPos[1] -= dt;
                    j.jPos[3] -= dt;
                    j.jPos[4] -= dt;
                    j.jPos[5] -= dt;
                    epos.ePos[0] -= dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);
            }
            else
            {
                Console.WriteLine($"GetActualJointPosDegree errcode:{ret}");
            }
        }
    }

Codebeispiel für Servobewegung im Gelenkraum
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4 Web-3.8.3

.. code-block:: c#
    :linenos:

    private void btnJointServoMove_Click(object sender, EventArgs e)
    {
        JointPos j = new JointPos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 500;
        float dt = 0.1f;
        int cmdID = 0;
        int ret = robot.GetActualJointPosDegree(flag, ref j);
        if (ret == 0)
        {
            robot.ServoMoveStart();

            try
            {
                while (count > 0)
                {

                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID);

                    j.jPos[0] += dt;
                    count--;

                    robot.WaitMs((int)(cmdT * 1000));
                }
            }
            finally
            {

                robot.ServoMoveEnd();
            }
        }
        else
        {
            Console.WriteLine($"GetActualJointPosDegree error code: {ret}");
        }
    }

Start der Gelenkmomentsteuerung
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Start der Gelenkmomentsteuerung
    * @param [in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoJTStart (int comType = 0)

Servo-Modus-Bewegung im Gelenkraum (Unterstützt Mehrfacheingabe auf Einmal)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Servo-Modus-Bewegung im Gelenkraum (unterstützt Mehrfacheingabe auf einmal)
    * @param [in] joint_pos Ziel-Gelenkpositionssatz (unterstützt bis zu 10 Gruppen), Einheit deg
    * @param [in] axisPos Externe Achsenposition, Einheit mm
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], noch nicht verfügbar, Standard 0
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100], noch nicht verfügbar, Standard 0
    * @param [in] cmdT Befehlssendezyklus, Einheit s, empfohlener Bereich [0.001~0.0016]
    * @param [in] filterT Filterzeit, Einheit s, noch nicht verfügbar, Standard 0
    * @param [in] gain Proportionalverstärker der Zielposition, noch nicht verfügbar, Standard 0
    * @param [out] servoJCmdCount ServoJ-Befehlspunktzähler [0-10000]
    * @param [in] id ServoJ-Befehls-ID, Standard 0
    * @param [in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboterschleuse 20007)
    * @return Fehlercode
    */
    public int ServoJ(List<JointPos> joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, ref int servoJCmdCount, int id = 0, int comType = 0)
    
Codebeispiel für Servo-Modus-Bewegung im Gelenkraum (Unterstützt Mehrfacheingabe auf Einmal)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoJPath()
    {
        // ServoJ-Pfaddatei lesen, Spalten 2~7 jeder Zeile als 6 Gelenkpositionen nehmen
        string filePath = "D://zUP/ServoJPath.txt";
        List<JointPos> allJointData = new List<JointPos>();
        using (StreamReader reader = new StreamReader(filePath))
        {
            string line;
            while ((line = reader.ReadLine()) != null)
            {
                string[] cols = line.Split(new[] { ' ', '\t' }, StringSplitOptions.RemoveEmptyEntries);
                if (cols.Length < 7)
                    continue;
                JointPos pose = new JointPos(0, 0, 0, 0, 0, 0);
                pose.jPos[0] = double.Parse(cols[1]);
                pose.jPos[1] = double.Parse(cols[2]);
                pose.jPos[2] = double.Parse(cols[3]);
                pose.jPos[3] = double.Parse(cols[4]);
                pose.jPos[4] = double.Parse(cols[5]);
                pose.jPos[5] = double.Parse(cols[6]);
                allJointData.Add(pose);
            }
        }
        Console.WriteLine($"Total {allJointData.Count} joint position sets read");
        if (allJointData.Count == 0)
            return;

        // Hin- und Rückweg erstellen: Vorwärtsreihenfolge + Rückwärtsreihenfolge
        List<JointPos> backForthPath = new List<JointPos>(allJointData);
        for (int i = allJointData.Count - 2; i >= 0; i--)
        {
            backForthPath.Add(allJointData[i]);
        }

        ExaxisPos epos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offsetPos = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        robot.MoveJ(allJointData[0], 0, 0, 100, 100, 100, epos, -1, 0, offsetPos);

        robot.Sleep(1000);

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        while (true)
        {
            robot.ResetAllError();
            robot.MoveJ(allJointData[0], 0, 0, 100, 100, 100, epos, -1, 0, offsetPos);
            int moveCount = 0;
            while (moveCount < backForthPath.Count - 10)
            {
                robot.GetRobotRealTimeState(ref pkg);

                int singleServoJCount = 50 - pkg.mc_queue_len;
                if (singleServoJCount <= 0)
                {
                    robot.Sleep(100);
                    continue;
                }
                if (singleServoJCount > 10)
                {
                    singleServoJCount = 10;
                }

                List<JointPos> jointPos = new List<JointPos>();
                for (int j = 0; j < singleServoJCount; j++)
                {
                    jointPos.Add(backForthPath[moveCount]);
                    moveCount++;
                }

                Console.WriteLine($"Sending {singleServoJCount} waypoints, moveCount={moveCount}");

                ExaxisPos axisPos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
                int servoJCmdCount = 0;
                int rtn = robot.ServoJ(jointPos, axisPos, 100.0f, 100.0f, 0.008f, 0.008f, 1.0f, ref servoJCmdCount);
                if (rtn != 0)
                {
                    Console.WriteLine($"ServoJ failed: {rtn}");
                    break;
                }
            }
            robot.Sleep(4000);
        }
    }    

Gelenkmomentsteuerung
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gelenkmomentsteuerung
    * @param [in] torque j1~j6 Gelenkmoment, Einheit Nm
    * @param [in] interval Befehlsperiode, Einheit s, Bereich [0.001~0.008]
    * @param [in] checkFlag Erkennungsstrategie 0-keine Einschränkung; 1-Leistungsbegrenzung; 2-Geschwindigkeitsbegrenzung; 3-sowohl Leistungs- als auch Geschwindigkeitsbegrenzung
    * @param [in] jPowerLimit Maximale Gelenkleistungsbegrenzung (W)
    * @param [in] jVelLimit Maximale Gelenkgeschwindigkeit (°/s)
    * @param [in]  comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoJT(double[] torque, double interval, int checkFlag, double[] jPowerLimit, double[] jVelLimit, int comType = 0)

Ende der Gelenkmomentsteuerung
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ende der Gelenkmomentsteuerung
    * @param[in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoJTEnd (int comType = 0)

SDK-Codebeispiel für ServoJT, ServoJTStart, ServoJTEnd basierend auf UDP-Kommunikation
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafetyUDP()
    {
        // Callback abonnieren
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP-Antwort] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            JointPos j = new JointPos(7.053, -89.699, 156.141, -72.751, 7.829, 1.889);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(-151.288, -321.186, 221.989, 89.140, 4.361, -0.795);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);

            robot.ServoJTStart(1);
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);

            int checkFlag = 0;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[0] = 0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[0] = -0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoJTEnd(1);
        }
        return 0;
    }

Codebeispiel für Gelenkmomentsteuerung
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button27_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }

Codebeispiel für Gelenkmomentsteuerung mit Übergeschwindigkeitsschutz
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafety()
    {
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            JointPos j = new JointPos(7.053, -89.699, 156.141, -72.751, 7.829, 1.889);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(-151.288, -321.186, 221.989, 89.140, 4.361, -0.795);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);

            robot.ServoJTStart(0);
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);

            int checkFlag = 0;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[0] = 0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 0);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[0] = -0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 0);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoJTEnd(0);
        }
    }

Servobewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Servobewegung im kartesischen Raum
    * @param [in] mode 0-Absolutbewegung (Basiskoordinatensystem), 1-Inkrementalbewegung (Basiskoordinatensystem), 2-Inkrementalbewegung (Werkzeugkoordinatensystem)
    * @param [in] desc_pose Ziel-Kartesische Pose oder Poseninkrement
    * @param [in] exaxis Position der Erweiterungsachse
    * @param [in] pos_gain Proportionalitätsfaktor für das Poseninkrement, nur bei inkrementeller Bewegung wirksam, Bereich [0~1]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben, Standard = 0
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben, Standard = 0
    * @param [in] cmdT Befehlszyklus [s], empfohlener Bereich [0.001~0.016]
    * @param [in] filterT Filterzeit [s], vorübergehend nicht freigegeben, Standard = 0
    * @param [in] gain Proportionalverstärkung der Zielposition, vorübergehend nicht freigegeben, Standard = 0
    * @return Fehlercode
    */
    public int ServoCart(int mode, DescPose desc_pose, ExaxisPos exaxis, double[] pos_gain, double acc, double vel, double cmdT, double filterT, double gain);

Codebeispiel für Servobewegung im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void TestServoCart()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        int rtn;
        DescPose desc_pos_dt = new DescPose(83.00800f, 50.525000f, 29.246f, 179.629f, -7.138f, -166.975f);
        ExaxisPos exaxis = new ExaxisPos(100.0f, 0.0f, 0.0f, 0.0f);
        double[] pos_gain = { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        int mode = 0;
        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.001f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 5000;

        robot.SetSpeed(20);

        while (count > 0)
        {
            rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoCart rtn is {rtn}");
            count -= 1;
            desc_pos_dt.tran.x += 0.01f;
            exaxis.ePos[0] += 0.01f;
        }
    }

Spline-Bewegung starten
+++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Spline-Bewegung starten
    * @return Fehlercode
    */
    int SplineStart();

Spline-PTP-Bewegung
++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Spline-Bewegung im Gelenkraum
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @return Fehlercode
    */
    int SplinePTP(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl);

Spline-PTP-Bewegung im Gelenkraum (automatische Vorwärtskinematik)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Spline-Bewegung im Gelenkraum (automatische Vorwärtskinematik)
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @return Fehlercode
    */
    int SplinePTP(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl)

Spline-Bewegung beenden
+++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Spline-Bewegung beenden
    * @return Fehlercode
    */
    int SplineEnd();

Codebeispiel für Spline-Bewegung
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSplineMove_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.SplineStart();
        robot.SplinePTP(j1, desc_pos1, tool, user, vel, acc, ovl);
        robot.SplinePTP(j2, desc_pos2, tool, user, vel, acc, ovl);
        robot.SplinePTP(j3, desc_pos3, tool, user, vel, acc, ovl);
        robot.SplinePTP(j4, desc_pos4, tool, user, vel, acc, ovl);
        robot.SplineEnd();
    }

Neue Spline-Bewegung starten
++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Neue Spline-Bewegung starten
    * @param [in] type 0-Kreisbogenübergang, 1-Vorgegebene Punkte sind Pfadpunkte
    * @param [in] averageTime Globale durchschnittliche Verbindungszeit [ms] (10 ~ ), Standard 2000
    * @return Fehlercode
    */
    int NewSplineStart(int type, int averageTime=2000);

Neuen Spline-Befehlspunkt hinzufügen
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Einen Befehlspunkt zur Spline-Bewegung hinzufügen
    * @param [in] joint_pos Ziel-Gelenkposition [°]
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] lastFlag Ob es der letzte Punkt ist, 0-nein, 1-ja
    * @return Fehlercode
    */
    int NewSplinePoint(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Neuen Spline-Befehlspunkt hinzufügen (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7 Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Neuen Spline-Befehlspunkt (automatische inverse Kinematik)
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] lastFlag Ob es der letzte Punkt ist, 0-nein, 1-ja
    * @param [in] config Konfiguration des Gelenkraums für inverse Kinematik, [-1]-Berechnung basierend auf aktueller Gelenkposition, [0~7]-Berechnung basierend auf spezifischer Gelenkraumkonfiguration
    * @return Fehlercode
    */
    int NewSplinePoint(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag, int config)

Neue Spline-Bewegung beenden
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Neue Spline-Bewegung beenden
    * @return Fehlercode
    */
    int NewSplineEnd();

Codebeispiel für neue Spline-Bewegung
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnNewSpline_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.NewSplineStart(1, 2000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j5, desc_pos5, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplineEnd();
    }

Bewegung abbrechen
++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegung abbrechen
    * @return Fehlercode
    */
    int StopMotion();

Bewegung pausieren
++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegung pausieren
    * @return Fehlercode
    */
    int PauseMotion();

Bewegung fortsetzen
+++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegung fortsetzen
    * @return Fehlercode
    */
    int ResumeMotion();

Codebeispiel für Bewegungspause, -fortsetzung und -abbruch
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMotionPause_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        rtn = robot.MoveJ(j5, desc_pos5, tool, user, vel, acc, ovl, epos, 1, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PauseMotion();

        Thread.Sleep(1000);
        robot.ResumeMotion();

        Thread.Sleep(1000);
        robot.StopMotion();

        Thread.Sleep(1000);
    }

Gesamtpunktversatz starten
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gesamtpunktversatz starten
    * @param [in] flag 0-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    int PointsOffsetEnable(int flag, DescPose offset_pos);

Gesamtpunktversatz beenden
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gesamtpunktversatz beenden
    * @return Fehlercode
    */
    int PointsOffsetDisable();

Codebeispiel für Punktversatz
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnPointOffect_Click(object sender, EventArgs e)
    {
        JointPos j1, j2;
        DescPose desc_pos1, desc_pos2, offset_pos, offset_pos1;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        offset_pos1 = new DescPose(50.0, 50.0, 50.0, 5.0, 5.0, 5.0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;
        int type = 0;

        robot.SetSpeed(20);

        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetEnable(type, offset_pos1);
        Thread.Sleep(1000);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetDisable();
    }

AO-Fliegendes-Messen (Control Box) starten
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: c#
    :linenos:

    /**
    * @brief AO-Fliegendes-Messen (Control Box) starten
    * @param [in] AONum AO-Nummer der Control Box
    * @param [in] maxTCPSpeed Maximale TCP-Geschwindigkeit [1-5000mm/s], Standard 1000
    * @param [in] maxAOPercent AO-Prozentsatz entsprechend der maximalen TCP-Geschwindigkeit, Standard 100%
    * @param [in] zeroZoneCmp Totzonenkompensationswert als AO-Prozentsatz, Ganzzahl, Standard 20%, Bereich [0-100]
    * @return Fehlercode
    */
    int MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

AO-Fliegendes-Messen (Control Box) stoppen
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: c#
    :linenos:

    /**
    * @brief AO-Fliegendes-Messen (Control Box) stoppen
    * @return Fehlercode
    */
    int MoveAOStop();

AO-Fliegendes-Messen (Endeffektor) starten
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: c#
    :linenos:

    /**
    * @brief AO-Fliegendes-Messen (Endeffektor) starten
    * @param [in] AONum AO-Nummer des Endeffektors
    * @param [in] maxTCPSpeed Maximale TCP-Geschwindigkeit [1-5000mm/s], Standard 1000
    * @param [in] maxAOPercent AO-Prozentsatz entsprechend der maximalen TCP-Geschwindigkeit, Standard 100%
    * @param [in] zeroZoneCmp Totzonenkompensationswert als AO-Prozentsatz, Ganzzahl, Standard 20%, Bereich [0-100]
    * @return Fehlercode
    */
    int MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

AO-Fliegendes-Messen (Endeffektor) stoppen
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: c#
    :linenos:

    /**
    * @brief AO-Fliegendes-Messen (Endeffektor) stoppen
    * @return Fehlercode
    */
    int MoveToolAOStop();

Codebeispiel für AO-Fliegendes-Messen
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMoveAO_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;

        robot.SetSpeed(5);

        robot.MoveAOStart(0,100,100,20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveAOStop();

        robot.MoveToolAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveToolAOStop();
    }

PTP-Bewegung mit FIR-Filterung starten
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief PTP-Bewegung mit FIR-Filterung starten
    * @param [in] maxAcc Maximale Beschleunigung [°/s²]
    * @param [in] maxJek Maximale Gelenkruck-Grenze [°/s³]
    * @return Fehlercode
    */
    int PtpFIRPlanningStart(double maxAcc, double maxJek=1000);

PTP-Bewegung mit FIR-Filterung beenden
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief PTP-Bewegung mit FIR-Filterung beenden
    * @return Fehlercode
    */
    int PtpFIRPlanningEnd();

LIN-/ARC-Bewegung mit FIR-Filterung starten
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief LIN-/ARC-Bewegung mit FIR-Filterung starten
    * @param [in] maxAccLin Maximale lineare Beschleunigung [mm/s²]
    * @param [in] maxAccDeg Maximale Winkelbeschleunigung [°/s²]
    * @param [in] maxJerkLin Maximale lineare Ruck-Grenze [mm/s³]
    * @param [in] maxJerkDeg Maximale Winkelruck-Grenze [°/s³]
    * @return Fehlercode
    */
    int LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

LIN-/ARC-Bewegung mit FIR-Filterung beenden
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief LIN-/ARC-Bewegung mit FIR-Filterung beenden
    * @return Fehlercode
    */
    int LinArcFIRPlanningEnd();

Codebeispiel für FIR-Filterung
++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button69_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos midjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos endjointPos = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose middescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose enddescPose = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.PtpFIRPlanningStart(1000, 1000);
        Console.WriteLine("PtpFIRPlanningStart rtn is " + rtn);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.PtpFIRPlanningEnd();
        Console.WriteLine("PtpFIRPlanningEnd rtn is " + rtn);

        robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
        Console.WriteLine("LinArcFIRPlanningStart rtn is " + rtn);
        robot.MoveL(startjointPos, startdescPose, 0, 0, 20, 100, 100, -1,0, exaxisPos, 0, 0, offdese, 1, 50);
        robot.MoveC(midjointPos, middescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, endjointPos, enddescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, 100, -1, 100, 0);
        robot.LinArcFIRPlanningEnd();
        Console.WriteLine("LinArcFIRPlanningEnd rtn is " + rtn);
    }

Beschleunigungsglättung aktivieren
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Beschleunigungsglättung aktivieren
    * @param [in] saveFlag Speichern bei Stromausfall (true/false)
    * @return Fehlercode
    */
    int AccSmoothStart(bool saveFlag);

Beschleunigungsglättung deaktivieren
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Beschleunigungsglättung deaktivieren
    * @param [in] saveFlag Speichern bei Stromausfall (true/false)
    * @return Fehlercode
    */
    int AccSmoothEnd(bool saveFlag);

Codebeispiel
++++++++++++
.. code-block:: c#
    :linenos:

    private void button1_Click(object sender, EventArgs e)
    {

        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AccSmoothStart(false);
        Console.WriteLine("AccSmoothStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AccSmoothEnd(false);
        Console.WriteLine("AccSmoothEnd rtn is " + rtn);
    }

Bestimmte Orientierungsgeschwindigkeit aktivieren
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bestimmte Orientierungsgeschwindigkeit aktivieren
    * @param [in] ratio Orientierungsgeschwindigkeitsprozentsatz [0-300]
    * @return Fehlercode
    */
    int AngularSpeedStart(int ratio);

Bestimmte Orientierungsgeschwindigkeit deaktivieren
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bestimmte Orientierungsgeschwindigkeit deaktivieren
    * @return Fehlercode
    */
    int AngularSpeedEnd();

Codebeispiel für Roboter mit bestimmter Orientierungsgeschwindigkeit
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button71_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AngularSpeedStart(50);
        Console.WriteLine("AngularSpeedStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AngularSpeedEnd();
        Console.WriteLine("AngularSpeedEnd rtn is " + rtn);
    }

Singularitätsschutz starten
+++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Singularitätsschutz starten
    * @param [in] protectMode Singularitätsschutzmodus, 0: Gelenkmodus; 1-Kartesischer Modus
    * @param [in] minShoulderPos Schulter-Singularitätsanpassungsbereich [mm], Standard 100
    * @param [in] minElbowPos Ellenbogen-Singularitätsanpassungsbereich [mm], Standard 50
    * @param [in] minWristPos Handgelenk-Singularitätsanpassungsbereich [°], Standard 10
    * @return Fehlercode
    */
    int SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Singularitätsschutz beenden
++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Singularitätsschutz beenden
    * @return Fehlercode
    */
    int SingularAvoidEnd();

Codebeispiel
++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    private void btnTestSingularAvoidEArc_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.SingularAvoidStart(2, 10, 5, 5);
        Console.WriteLine("SingularAvoidStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.SingularAvoidEnd();
        Console.WriteLine("SingularAvoidEnd rtn is " + rtn);
    }

Sicherheitsstopp auslösen
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Sicherheitsstopp-Signal auslösen (Code abrufen)
    * @return Fehlercode
    */
    int GetSafetyCode();

Bewegungsbefehlswarteschlange leeren
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9 Web-3.8.7

.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegungsbefehlswarteschlange leeren
    * @return Fehlercode
    */
    public int MotionQueueClear();

Zum Startpunkt einer Rohrverschneidung bewegen
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zum Startpunkt einer Rohrverschneidung bewegen
    * @param [in] mainPoint Kartesische Posen der 6 Teachpunkte des Hauptrohrs
    * @param [in] mainExaxisPos Positionen der Erweiterungsachse an den 6 Teachpunkten des Hauptrohrs
    * @param [in] piecePoint Kartesische Posen der 6 Teachpunkte des Nebenrohrs
    * @param [in] pieceExaxisPos Positionen der Erweiterungsachse an den 6 Teachpunkten des Nebenrohrs
    * @param [in] extAxisFlag Erweiterungsachse aktivieren? 0-nein; 1-ja
    * @param [in] exaxisPos Startposition der Erweiterungsachse
    * @param [in] tool Werkzeugkoordinatennummer
    * @param [in] wobj Werkstückkoordinatennummer
    * @param [in] vel Geschwindigkeitsprozentsatz
    * @param [in] acc Beschleunigungsprozentsatz
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor
    * @param [in] oacc Beschleunigungsskalierungsfaktor
    * @param [in] moveType Bewegungstyp; 0-PTP; 1-LIN
    * @param [in] moveDirection Bewegungsrichtung; 0-im Uhrzeigersinn; 1-gegen Uhrzeigersinn
    * @param [in] offset Versatzwert (Pose)
    * @return Fehlercode
    */
    public int MoveToIntersectLineStart(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);

Bewegung entlang einer Rohrverschneidung
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Bewegung entlang einer Rohrverschneidung
    * @param [in] mainPoint Kartesische Posen der 6 Teachpunkte des Hauptrohrs
    * @param [in] mainExaxisPos Positionen der Erweiterungsachse an den 6 Teachpunkten des Hauptrohrs
    * @param [in] piecePoint Kartesische Posen der 6 Teachpunkte des Nebenrohrs
    * @param [in] pieceExaxisPos Positionen der Erweiterungsachse an den 6 Teachpunkten des Nebenrohrs
    * @param [in] extAxisFlag Erweiterungsachse aktivieren? 0-nein; 1-ja
    * @param [in] exaxisPos Array von Positionen der Erweiterungsachse entlang der Bahn
    * @param [in] tool Werkzeugkoordinatennummer
    * @param [in] wobj Werkstückkoordinatennummer
    * @param [in] vel Geschwindigkeitsprozentsatz
    * @param [in] acc Beschleunigungsprozentsatz
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor
    * @param [in] oacc Beschleunigungsskalierungsfaktor
    * @param [in] moveDirection Bewegungsrichtung; 0-im Uhrzeigersinn; 1-gegen Uhrzeigersinn
    * @param [in] offset Versatzwert (Pose)
    * @return Fehlercode
    */
    public int MoveIntersectLine(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos[] exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);

Codebeispiel für Roboterbewegung entlang einer Rohrverschneidung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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

Stillstehende Leerbewegung
+++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Stillstehende Leerbewegung (Bewegung ohne Ortsveränderung)
    * @return Fehlercode
    */
    public int MoveStationary()

Codebeispiel für stillstehende Leerbewegung
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void LaserSensorRecordandReplay()
    {
        int rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 1, 10, 100);
        Console.WriteLine($"LaserSensorRecordandReplay rtn is {rtn}");
        rtn = robot.MoveStationary();
        Console.WriteLine($"MoveStationary rtn is {rtn}");
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord1 rtn is {rtn}"); 
    }

Stationäres Pendeln Start
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Start des stationären Pendelns
    * @param [in] weaveNum Pendelnummer [0-7]
    * @param [in] mode 0-Werkzeugkoordinatensystem; 1-Referenzpunkt
    * @param [in] refPoint Referenzpunkt-Koordinaten im kartesischen Koordinatensystem [x,y,z,a,b,c]
    * @param [in] weaveTime Pendelzeit [s]
    * @return Fehlercode
    */
    public int OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime);
    
Stationäres Pendeln Ende
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ende des stationären Pendelns
    * @return Fehlercode
    */
    public int OriginPointWeaveEnd();
        
SDK-Codebeispiel für stationäres Pendeln
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave()
    {
        // Gelenkpositionsobjekt erstellen
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        // Referenzpunkt-Koordinaten
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        //// Erste Bewegung
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Stationäres Pendeln starten (Modus 0)
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();   // Stationäre Bewegung ausführen (vorausgesetzt, diese Methode existiert)
        robot.OriginPointWeaveEnd();

        Thread.Sleep(2000);         // 2 Sekunden warten

        // Zweite Bewegung
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Stationäres Pendeln starten (Modus 1)
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
    }

SDK-Codebeispiel für stationäres Pendeln (mit Laser und Erweiterungsachse)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave2()
    {
        // Gelenkpositionsobjekt erstellen
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1 = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2 = new ExaxisPos(5, 0.000, 0.000, 0.000);

        // Referenzpunkt-Koordinaten
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        int rtn = 0;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);

        // UDP-Treiber laden
        robot.ExtDevLoadUDPDriver();

        // Positionierungsabschlusszeit für Erweiterungsachse einstellen
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        Console.WriteLine("SetExAxisCmdDoneTime rtn is " + rtn);

        // Erweiterungsachsen 1 und 2 aktivieren
        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        // Referenzfahrt für Erweiterungsachse einstellen
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.LaserTrackingLaserOnOff(1);


        //// 1---Ohne Erweiterungsachse
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        // Stationäres Pendeln starten
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();   // Stationäre Bewegung ausführen
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        Thread.Sleep(2000);         // 2 Sekunden warten

        //// 2---Mit Erweiterungsachse
        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        // Stationäres Pendeln starten
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);
    }

Gelenkraum-Geschwindigkeitsservomodellbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Gelenkraum-Geschwindigkeitsservomodellbewegung
    * @param  [in] joint_pos  6 Zielgelenkgeschwindigkeiten, Einheit deg/s
    * @param  [in] axisPos  4 externe Achsengeschwindigkeiten, Einheit deg/s
    * @param  [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100], vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] cmdT  Befehlssendezyklus, Einheit s, empfohlener Bereich [0.001~0.0016]
    * @param  [in] filterT Filterzeit, Einheit s, vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] gain  Proportionalverstärker für Zielposition, vorübergehend nicht geöffnet, Standard ist 0
    * @param  [in] id ServoJ-Befehls-ID, Standard ist 0
    * @param[in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return  Fehlercode
    */
    public int ServoJV(double[] joint_vel, double[] exis_vel, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

Codebeispiel für Gelenkraum-Geschwindigkeitsservomodellbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJVtest()
    {
        double[] joint_vel = new double[6] { 10, 0, 0, 0, 0, 0 };
        double[] exis_vel = new double[4] { 0, 0, 0, 0 };
        float acc = 0.0f; 
        float vel = 0.0f;
        float cmdT = 0.01f; 
        float filterT = 0.0f; 
        float gain = 0.0f;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoJV rtn is {error}");
            cnt++;
        }
        return 0;
    }

Gelenk-MIT-Steuerung Start
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gelenk-MIT-Steuerung Start
    * @param [in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoMITStart(int comType = 0)

Gelenk-MIT-Steuerung Ende
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gelenk-MIT-Steuerung Ende
    * @param [in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoMITEnd(int comType = 0)

Gelenk-MIT-Steuerung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Gelenk-MIT-Steuerung
    * @param [in] posGain j1~j6 Gelenkpositionsverstärkung
    * @param [in] desPos j1~j6 Gelenkpositionssollwert, Einheit: deg
    * @param [in] velGain j1~j6 Gelenkgeschwindigkeitsverstärkung
    * @param [in] desVel j1~j6 Gelenkgeschwindigkeitssollwert, Einheit: deg/s
    * @param [in] torque_ff j1~j6 Vorsteuerungsdrehmoment, Einheit: Nm
    * @param [in] interval Befehlsperiode, Einheit s, Bereich [0.001~0.008]
    * @param [in] comType Befehlssendetyp; 0-xmlrpc; 1-UDP (entspricht Roboter-Port 20007)
    * @return Fehlercode
    */
    public int ServoMIT(double[] posGain, double[] desPos, double[] velGain, double[] desVel, double[] torque_ff, double interval, int comType = 0)

Codebeispiel für Gelenk-MIT-Steuerungsbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoMITtest()
    {
        // Callback abonnieren
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP-Antwort] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            double[] posGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desPos = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] velGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desVel = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);
            Console.WriteLine($"111111");
            //robot.ServoMITEnd(0);
            robot.ServoMITStart(0);
            Console.WriteLine($"ServoMITStart");
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);
            Console.WriteLine($"DragTeachSwitch");
            double intev = 0.008;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[5] = 0.03;
                Console.WriteLine($"ServoMIT call ");
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoMIT111111 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[5] = -0.03;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoJT222222 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        return 0;
    }

Start der Werkstückkoordinatensystem-Punkttransformation
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Start der Werkstückkoordinatensystem-Punkttransformation
    * @param  [in] workpieceID Werkstücknummer [0-14]
    * @return  Fehlercode, 0 bei Erfolg
    */
    public int WorkPieceTrsfStart(int workpieceID)
    
Ende der Werkstückkoordinatensystem-Punkttransformation
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ende der Werkstückkoordinatensystem-Punkttransformation
    * @return  Fehlercode, 0 bei Erfolg
    */
    public int WorkPieceTrsfEnd()
        
Codebeispiel für die Werkstückkoordinatensystem-Punkttransformation
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestWorkPieceTrsf()
    {

        // ---- Punktdefinitionen ----
        JointPos j1 = new JointPos(-11.188, -64.165, -107.299, -76.706, 89.590, 92.983);
        DescPose d1 = new DescPose(225.986, 190.694, 394.238, -6.230, -23.797, -98.972);
        JointPos j2 = new JointPos(-38.148, -97.408, -133.704, -30.999, 89.584, 92.986);
        DescPose d2 = new DescPose(52.741, 262.917, 30.824, -5.696, -9.864, -126.092);
        JointPos j3 = new JointPos(-25.561, -123.131, -85.736, -94.911, 89.582, 93.006);
        DescPose d3 = new DescPose(70.455, 88.410, 45.299, -4.101, 31.775, -113.199);
        JointPos j4 = new JointPos(-8.013, -125.881, -79.196, -84.440, 89.564, 93.005);
        DescPose d4 = new DescPose(209.453, -73.895, 56.416, -4.727, 17.523, -95.906);
        JointPos j5 = new JointPos(-2.722, -94.518, -119.965, -54.518, 89.563, 93.005);
        DescPose d5 = new DescPose(274.800, 81.106, 102.977, -5.467, -2.980, -90.711);
        JointPos j6 = new JointPos(-2.671, -56.234, -138.914, -25.099, 95.355, 92.967);
        DescPose d6 = new DescPose(300.392, 177.281, 300.926, -1.909, -51.894, -89.703);
        JointPos j7 = new JointPos(-1.229, -121.184, -63.201, -122.331, 93.045, 93.019);
        DescPose d7 = new DescPose(296.856, -31.294, 215.698, -0.589, 34.594, -88.954);

        ExaxisPos ex = new ExaxisPos(0, 0, 0, 0);
        DescPose zeroOff = new DescPose(0, 0, 0, 0, 0, 0);

        int tool = 1;
        int workpiece = 1;
        float blend = 5.0f;

        // ===== Koordinatensystem 1 =====
        // Home
        robot.MoveJ(j1, d1, tool, workpiece, 100, 100, 100, ex, -1, 0, zeroOff);
        // PTP
        robot.MoveJ(j2, d2, tool, workpiece, 100, 100, 100, ex, blend, 0, zeroOff);
        // LIN
        robot.MoveL(j3, d3, tool, workpiece, 10, 100, 100, blend, 0, ex, 0, 1, zeroOff, 0, 90);
        // ARC
        robot.MoveC(j4, d4, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    j5, d5, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    10, blend, 100, 0);
        // CIR
        robot.Circle(j6, d6, tool, workpiece, 100, 100, ex,
                        j7, d7, tool, workpiece, 100, 100, ex,
                        10, 0, zeroOff, 100.0, blend, 0);

        // ===== WorkPieceTrsfStart(2) =====
        int rtn = robot.WorkPieceTrsfStart(2);
        Console.WriteLine("  WorkPieceTrsfStart(2) rtn={0}", rtn);

        // ===== Koordinatensystem 2 (nach Transformation) =====
        robot.MoveJ(j1, d1, tool, workpiece, 100, 100, 100, ex, -1, 0, zeroOff);
        robot.MoveJ(j2, d2, tool, workpiece, 100, 100, 100, ex, blend, 0, zeroOff);
        robot.MoveL(j3, d3, tool, workpiece, 10, 100, 100, blend, 0, ex, 0, 1, zeroOff, 0, 90);
        robot.MoveC(j4, d4, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    j5, d5, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    10, blend, 100, 0);
        robot.Circle(j6, d6, tool, workpiece, 100, 100, ex,
                        j7, d7, tool, workpiece, 100, 100, ex,
                        10, 0, zeroOff, 100.0, blend, 0);

        // ===== WorkPieceTrsfEnd =====
        rtn = robot.WorkPieceTrsfEnd();
        Console.WriteLine("  WorkPieceTrsfEnd() rtn={0}", rtn);

        return rtn;
    }    