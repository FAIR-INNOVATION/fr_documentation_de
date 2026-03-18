Beschreibung der Datenstrukturen
========================================

.. toctree::
    :maxdepth: 5

Rückgabewerttyp von Schnittstellenaufrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    typedef int errno_t;

Datentyp für Gelenkpositionen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Datentyp für Gelenkpositionen.
    */
    typedef struct
    {
        double jPos[6];   /* Sechs Gelenkpositionen, Einheit deg */
    } JointPos;

Datentyp für Positionen im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Datentyp für Positionen im kartesischen Raum.
    */
    typedef struct
    {
        double x;    /* x-Achsen-Koordinate, Einheit mm  */
        double y;    /* y-Achsen-Koordinate, Einheit mm  */
        double z;    /* z-Achsen-Koordinate, Einheit mm  */
    } DescTran;

Datentyp für Euler-Winkel-Ausrichtung
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Datentyp für Euler-Winkel-Ausrichtung.
    */
    typedef struct
    {
        double rx;   /* Rotationswinkel um die feste X-Achse, Einheit: deg  */
        double ry;   /* Rotationswinkel um die feste Y-Achse, Einheit: deg  */
        double rz;   /* Rotationswinkel um die feste Z-Achse, Einheit: deg  */
    } Rpy;

Datentyp für Posen im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Datentyp für Posen im kartesischen Raum.
    */
    typedef struct
    {
        DescTran tran;      /* Position im kartesischen Raum  */
        Rpy rpy;            /* Ausrichtung im kartesischen Raum  */
    } DescPose;

Datentyp für Positionen der Erweiterungsachse
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Datentyp für Positionen der Erweiterungsachse.
    */
    typedef struct
    {
        double ePos[4];   /* Positionen der vier Erweiterungsachsen, Einheit mm */
    } ExaxisPos;

Datentyp für Kraft-/Drehmomentsensor
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kraftkomponenten und Drehmomentkomponenten des Kraftsensors.
    */
    typedef struct
    {
        double fx;  /* Kraftkomponente entlang der x-Achse, Einheit N  */
        double fy;  /* Kraftkomponente entlang der y-Achse, Einheit N  */
        double fz;  /* Kraftkomponente entlang der z-Achse, Einheit N  */
        double tx;  /* Drehmomentkomponente um die x-Achse, Einheit Nm */
        double ty;  /* Drehmomentkomponente um die y-Achse, Einheit Nm */
        double tz;  /* Drehmomentkomponente um die z-Achse, Einheit Nm */
    } ForceTorque;

Datentyp für Spiralparameter
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Datentyp für Spiralparameter.
    */
    typedef struct
    {
        int    circle_num;           /* Anzahl der Windungen  */
        float  circle_angle;         /* Neigungswinkel der Spirale  */
        float  rad_init;             /* Anfangsradius der Spirale, Einheit mm  */
        float  rad_add;              /* Radiusinkrement  */
        float  rotaxis_add;          /* Inkrement in Richtung der Drehachse  */
        int    rot_direction;        /* Drehrichtung, 0-im Uhrzeigersinn, 1-gegen Uhrzeigersinn  */
        int    velAccMode;            /* Modus für Geschwindigkeit/Beschleunigung: 0-Winkelgeschwindigkeit konstant; 1-Lineargeschwindigkeit konstant */
    } SpiralParam;

Status-Rückmeldungspaket der Steuerung
+++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Status-Rückmeldungspaket der Steuerung.
     */
    typedef struct _ROBOT_STATE_PKG
    {
        uint16_t frame_head;      // Frame-Header, vereinbart als 0x5A5A
        uint8_t  frame_cnt;       // Frame-Zähler, zyklisch 0-255
        uint16_t data_len;        // Länge des Dateninhalts
        uint8_t  program_state;   // Programmausführungsstatus, 1-gestoppt; 2-läuft; 3-pausiert;
        uint8_t  robot_state;     // Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-Ziehemodus (Drag)
        int      main_code;       // Hauptfehlercode
        int      sub_code;        // Unterfehlercode
        uint8_t  robot_mode;      // Robotermodus, 1-Handmodus; 0-Automatikmodus;
        double   jt_cur_pos[6];   // Aktuelle Gelenkpositionen der 6 Achsen, Einheit deg
        double   tl_cur_pos[6];   // Aktuelle Werkzeugpose
                                  // tl_cur_pos[0], Position entlang x-Achse, Einheit mm,
                                  // tl_cur_pos[1], Position entlang y-Achse, Einheit mm,
                                  // tl_cur_pos[2], Position entlang z-Achse, Einheit mm,
                                  // tl_cur_pos[3], Rotationswinkel um die feste X-Achse, Einheit deg
                                  // tl_cur_pos[4], Rotationswinkel um die feste Y-Achse, Einheit deg
                                  // tl_cur_pos[5], Rotationswinkel um die feste Z-Achse, Einheit deg
        double   flange_cur_pos[6]; // Aktuelle Pose des Endflansches
                                    // flange_cur_pos[0], Position entlang x-Achse, Einheit mm,
                                    // flange_cur_pos[1], Position entlang y-Achse, Einheit mm,
                                    // flange_cur_pos[2], Position entlang z-Achse, Einheit mm,
                                    // flange_cur_pos[3], Rotationswinkel um die feste X-Achse, Einheit deg
                                    // flange_cur_pos[4], Rotationswinkel um die feste Y-Achse, Einheit deg
                                    // flange_cur_pos[5], Rotationswinkel um die feste Z-Achse, Einheit deg
        double   actual_qd[6];      // Aktuelle Geschwindigkeiten der 6 Gelenke, Einheit deg/s
        double   actual_qdd[6];     // Aktuelle Beschleunigungen der 6 Gelenke, Einheit deg/s^2
        double   target_TCP_CmpSpeed[2];
                                    // target_TCP_CmpSpeed[0], TCP-resultierende Sollgeschwindigkeit (Position), Einheit mm/s
                                    // target_TCP_CmpSpeed[1], TCP-resultierende Sollgeschwindigkeit (Ausrichtung), Einheit deg/s
        double   target_TCP_Speed[6];    // TCP-Sollgeschwindigkeit (Komponenten)
                                         // target_TCP_Speed[0], Geschwindigkeit entlang x-Achse, Einheit mm/s,
                                         // target_TCP_Speed[1], Geschwindigkeit entlang y-Achse, Einheit mm/s,
                                         // target_TCP_Speed[2], Geschwindigkeit entlang z-Achse, Einheit mm/s,
                                         // target_TCP_Speed[3], Rotationsgeschwindigkeit um die feste X-Achse, Einheit deg/s
                                         // target_TCP_Speed[4], Rotationsgeschwindigkeit um die feste Y-Achse, Einheit deg/s
                                         // target_TCP_Speed[5], Rotationsgeschwindigkeit um die feste Z-Achse, Einheit deg/s
        double   actual_TCP_CmpSpeed[2];
                                    // actual_TCP_CmpSpeed[0], TCP-resultierende Istgeschwindigkeit (Position), Einheit mm/s
                                    // actual_TCP_CmpSpeed[1], TCP-resultierende Istgeschwindigkeit (Ausrichtung), Einheit deg/s
        double   actual_TCP_Speed[6];    // TCP-Istgeschwindigkeit (Komponenten)
                                         // actual_TCP_Speed[0], Geschwindigkeit entlang x-Achse, Einheit mm/s,
                                         // actual_TCP_Speed[1], Geschwindigkeit entlang y-Achse, Einheit mm/s,
                                         // actual_TCP_Speed[2], Geschwindigkeit entlang z-Achse, Einheit mm/s,
                                         // actual_TCP_Speed[3], Rotationsgeschwindigkeit um die feste X-Achse, Einheit deg/s
                                         // actual_TCP_Speed[4], Rotationsgeschwindigkeit um die feste Y-Achse, Einheit deg/s
                                         // actual_TCP_Speed[5], Rotationsgeschwindigkeit um die feste Z-Achse, Einheit deg/s
        double   jt_cur_tor[6];      // Aktuelle Drehmomente der 6 Achsen, Einheit N·m
        int      tool;               // Nummer des angewendeten Werkzeugkoordinatensystems
        int      user;               // Nummer des angewendeten Werkstückkoordinatensystems
        uint8_t  cl_dgt_output_h;    // Digitale IO-Ausgänge des Steuerschranks 15-8
        uint8_t  cl_dgt_output_l;    // Digitale IO-Ausgänge des Steuerschranks 7-0
        uint8_t  tl_dgt_output_l;    // Digitale IO-Ausgänge des Werkzeugs 7-0, nur bit0-bit1 gültig
        uint8_t  cl_dgt_input_h;     // Digitale IO-Eingänge des Steuerschranks 15-8
        uint8_t  cl_dgt_input_l;     // Digitale IO-Eingänge des Steuerschranks 7-0
        uint8_t  tl_dgt_input_l;     // Digitale IO-Eingänge des Werkzeugs 7-0, nur bit0-bit1 gültig
        uint16_t cl_analog_input[2]; // cl_analog_input[0], Analogeingang 0 des Steuerschranks
                                     // cl_analog_input[1], Analogeingang 1 des Steuerschranks
        uint16_t tl_anglog_input;    // Analogeingang des Werkzeugs
        double   ft_sensor_raw_data[6]; // Rohdaten des Kraft-/Drehmomentsensors
                                      // ft_sensor_raw_data[0], Kraft entlang x-Achse, Einheit N
                                      // ft_sensor_raw_data[1], Kraft entlang y-Achse, Einheit N
                                      // ft_sensor_raw_data[2], Kraft entlang z-Achse, Einheit N
                                      // ft_sensor_raw_data[3], Drehmoment um x-Achse, Einheit Nm
                                      // ft_sensor_raw_data[4], Drehmoment um y-Achse, Einheit Nm
                                      // ft_sensor_raw_data[5], Drehmoment um z-Achse, Einheit Nm
        double   ft_sensor_data[6];     // Verarbeitete Daten des Kraft-/Drehmomentsensors
                                        // ft_sensor_data[0], Kraft entlang x-Achse, Einheit N
                                        // ft_sensor_data[1], Kraft entlang y-Achse, Einheit N
                                        // ft_sensor_data[2], Kraft entlang z-Achse, Einheit N
                                        // ft_sensor_data[3], Drehmoment um x-Achse, Einheit Nm
                                        // ft_sensor_data[4], Drehmoment um y-Achse, Einheit Nm
                                        // ft_sensor_data[5], Drehmoment um z-Achse, Einheit Nm
        uint8_t  ft_sensor_active;   // Aktivierungsstatus des Kraft-/Drehmomentsensors, 0-Reset, 1-aktiviert
        uint8_t  EmergencyStop;      // Not-Halt-Flag, 0-Not-Halt nicht gedrückt, 1-Not-Halt gedrückt
        int      motion_done;        // In-Position-Signal, 1-in Position, 0-nicht in Position
        uint8_t  gripper_motiondone; // Greifer-Bewegungsabschluss-Signal, 1-abgeschlossen, 0-nicht abgeschlossen
        int      mc_queue_len;       // Länge der Bewegungswarteschlange
        uint8_t  collisionState;     // Kollisionserkennung, 1-Kollision, 0-keine Kollision
        int      trajectory_pnum;    // Trajektorienpunktnummer
        uint8_t  safety_stop0_state; // Sicherheitsstopp-Signal SI0
        uint8_t  safety_stop1_state; // Sicherheitsstopp-Signal SI1
        uint8_t  gripper_fault_id;   // Fehlerhafte Greifernummer
        uint16_t gripper_fault;      // Greiferfehler
        uint16_t gripper_active;     // Greifer-Aktivierungsstatus
        uint8_t  gripper_position;   // Greiferposition
        int8_t   gripper_speed;      // Greifergeschwindigkeit
        int8_t   gripper_current;    // Greiferstrom
        int      gripper_temp;       // Greifertemperatur
        int      gripper_voltage;    // Greiferspannung
        robot_aux_state aux_state;   // Status der 485-Erweiterungsachse
        EXT_AXIS_STATUS extAxisStatus[4];  // Status der UDP-Erweiterungsachsen
        uint16_t extDIState[8];        // Erweiterte DI-Eingänge
        uint16_t extDOState[8];        // Erweiterte DO-Ausgänge
        uint16_t extAIState[4];        // Erweiterte AI-Eingänge
        uint16_t extAOState[4];        // Erweiterte AO-Ausgänge
        int rbtEnableState;            // Roboter-Aktivierungsstatus (Enable)
        double   jointDriverTorque[6];        // Drehmoment der Gelenkantriebe
        double   jointDriverTemperature[6];   // Temperatur der Gelenkantriebe
        RobotTime robotTime;           // Roboter-Systemzeit
        int softwareUpgradeState;      // Roboter-Software-Upgrade-Status
        uint16_t endLuaErrCode;        // LUA-Ausführungsstatus am Endeffektor
        uint16_t cl_analog_output[2];  // Analogausgänge des Steuerschranks
        uint16_t tl_analog_output;     // Analogausgang des Werkzeugs
        float gripperRotNum;           // Aktuelle Umdrehungszahl des Drehgreifers
        uint8_t gripperRotSpeed;       // Aktueller Rotationsgeschwindigkeitsprozentsatz des Drehgreifers
        uint8_t gripperRotTorque;      // Aktueller Rotationskraftprozentsatz des Drehgreifers
        WELDING_BREAKOFF_STATE weldingBreakOffState;  // Schweißunterbrechungsstatus
        double jt_tgt_tor[6];                 // Gelenk-Solldrehmomente
        int smartToolState;                   // SmartTool-Griff-Tastenstatus
        float wideVoltageCtrlBoxTemp;         // Temperatur des Weitbereichs-Steuerschranks
        uint16_t wideVoltageCtrlBoxFanCurrent;// Lüfterstrom des Weitbereichs-Steuerschranks (mA)
        double toolCoord[6];        // Werkzeugkoordinatensystem
        double wobjCoord[6];        // Werkstückkoordinatensystem
        double extoolCoord[6];      // Externes Werkzeugkoordinatensystem
        double exAxisCoord[6];      // Erweiterungsachsen-Koordinatensystem
        double load;                // Nutzlastmasse
        double loadCog[3];          // Nutzlastschwerpunkt
        double lastServoTarget[6];  // Letzte ServoJ-Zielposition in der Warteschlange
        int servoJCmdNum;           // ServoJ-Befehlszähler
        uint16_t check_sum;         // Summenprüfung
    } ROBOT_STATE_PKG;