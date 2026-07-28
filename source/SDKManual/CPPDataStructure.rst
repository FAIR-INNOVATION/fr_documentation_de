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
      uint16_t frame_head;   // Rahmenkopf, vereinbart als 0x5A5A 
      uint8_t frame_cnt;    // Rahmenzählung, zyklischer Zähler 0-255 
      uint16_t data_len;    // Länge des Dateninhalts 
      uint8_t program_state;  // Programmstatus, 1-gestoppt; 2-läuft; 3-pausiert;
      uint8_t robot_state;   // Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-ziehen 
      int   main_code;    // Hauptfehlercode 
      int   sub_code;    // Unterfehlercode 
      uint8_t robot_mode;   // Robotermodus, 1-Handmodus; 0-Automatikmodus; 
      double  jt_cur_pos[6];  // Aktuelle Gelenkpositionen von 6 Achsen, Einheit deg 
      double  tl_cur_pos[6];  // Aktuelle Werkzeugposition
            // tl_cur_pos[0], Position entlang der x-Achse, Einheit mm,
            // tl_cur_pos[1], Position entlang der y-Achse, Einheit mm,
            // tl_cur_pos[2], Position entlang der z-Achse, Einheit mm,
            // tl_cur_pos[3], Drehwinkel um die feste X-Achse, Einheit deg
            // tl_cur_pos[4], Drehwinkel um die feste Y-Achse, Einheit deg
            // tl_cur_pos[5], Drehwinkel um die feste Z-Achse, Einheit deg 
      double  flange_cur_pos[6]; // Aktuelle Endflanschposition
            // flange_cur_pos[0], Position entlang der x-Achse, Einheit mm,
            // flange_cur_pos[1], Position entlang der y-Achse, Einheit mm,
            // flange_cur_pos[2], Position entlang der z-Achse, Einheit mm,
            // flange_cur_pos[3], Drehwinkel um die feste X-Achse, Einheit deg
            // flange_cur_pos[4], Drehwinkel um die feste Y-Achse, Einheit deg
            // flange_cur_pos[5], Drehwinkel um die feste Z-Achse, Einheit deg
      double  actual_qd[6];   // Aktuelle Geschwindigkeiten von 6 Gelenken, Einheit deg/s 
      double  actual_qdd[6];   // Aktuelle Beschleunigungen von 6 Gelenken, Einheit deg/s^2 
      double  target_TCP_CmpSpeed[2]; 
            // target_TCP_CmpSpeed[0], TCP zusammengesetzte Befehlgeschwindigkeit (Position), Einheit mm/s
            // target_TCP_CmpSpeed[1], TCP zusammengesetzte Befehlgeschwindigkeit (Orientierung), Einheit deg/s */
      double  target_TCP_Speed[6];  // TCP Befehlgeschwindigkeit
              // target_TCP_Speed[0], Geschwindigkeit entlang der x-Achse, Einheit mm/s,
              // target_TCP_Speed[1], Geschwindigkeit entlang der y-Achse, Einheit mm/s,
              // target_TCP_Speed[2], Geschwindigkeit entlang der z-Achse, Einheit mm/s,
              // target_TCP_Speed[3], Winkelgeschwindigkeit um die feste X-Achse, Einheit deg/s
              // target_TCP_Speed[4], Winkelgeschwindigkeit um die feste Y-Achse, Einheit deg/s
              // target_TCP_Speed[5], Winkelgeschwindigkeit um die feste Z-Achse, Einheit deg/s */
      double  actual_TCP_CmpSpeed[2]; 
              // actual_TCP_CmpSpeed[0], TCP zusammengesetzte tatsächliche Geschwindigkeit (Position), Einheit mm/s
              // actual_TCP_CmpSpeed[1], TCP zusammengesetzte tatsächliche Geschwindigkeit (Orientierung), Einheit deg/s 
      double  actual_TCP_Speed[6];  // TCP tatsächliche Geschwindigkeit
              // actual_TCP_Speed[0], Geschwindigkeit entlang der x-Achse, Einheit mm/s,
              // actual_TCP_Speed[1], Geschwindigkeit entlang der y-Achse, Einheit mm/s,
              // actual_TCP_Speed[2], Geschwindigkeit entlang der z-Achse, Einheit mm/s,
              // actual_TCP_Speed[3], Winkelgeschwindigkeit um die feste X-Achse, Einheit deg/s
              // actual_TCP_Speed[4], Winkelgeschwindigkeit um die feste Y-Achse, Einheit deg/s
              // actual_TCP_Speed[5], Winkelgeschwindigkeit um die feste Z-Achse, Einheit deg/s 
      double  jt_cur_tor[6];   // Aktuelle Drehmomente von 6 Achsen, Einheit N·m 
      int   tool;        // Angewandtes Werkzeugkoordinatensystem Nummer 
      int   user;        // Angewandtes Werkstückkoordinatensystem Nummer 
      uint8_t cl_dgt_output_h;  // Digitaler IO-Ausgang des Steuerkastens 15-8 
      uint8_t cl_dgt_output_l;  // Digitaler IO-Ausgang des Steuerkastens 7-0 
      uint8_t tl_dgt_output_l;  // Digitaler IO-Ausgang des Werkzeugs 7-0, nur bit0-bit1 gültig 
      uint8_t cl_dgt_input_h;   // Digitaler IO-Eingang des Steuerkastens 15-8 
      uint8_t cl_dgt_input_l;   // Digitaler IO-Eingang des Steuerkastens 7-0 
      uint8_t tl_dgt_input_l;   // Digitaler IO-Eingang des Werkzeugs 7-0, nur bit0-bit1 gültig 
      uint16_t cl_analog_input[2]; // cl_analog_input[0], Analoger Eingang des Steuerkastens 0
                    //cl_analog_input[1], Analoger Eingang des Steuerkastens 1 
      uint16_t tl_anglog_input;  // Analoger Werkzeugeingang 
      double  ft_sensor_raw_data[6]; // Rohdaten des Kraft-/Drehmomentsensors
              // ft_sensor_raw_data[0], Kraft entlang der x-Achse, Einheit N
              // ft_sensor_raw_data[1], Kraft entlang der y-Achse, Einheit N
              // ft_sensor_raw_data[2], Kraft entlang der z-Achse, Einheit N
              // ft_sensor_raw_data[3], Drehmoment um die x-Achse, Einheit Nm
              // ft_sensor_raw_data[4], Drehmoment um die y-Achse, Einheit Nm
              // ft_sensor_raw_data[5], Drehmoment um die z-Achse, Einheit Nm 
      double  ft_sensor_data[6];   // Daten des Kraft-/Drehmomentsensors,
              // ft_sensor_data[0], Kraft entlang der x-Achse, Einheit N
              // ft_sensor_data[1], Kraft entlang der y-Achse, Einheit N
              // ft_sensor_data[2], Kraft entlang der z-Achse, Einheit N
              // ft_sensor_data[3], Drehmoment um die x-Achse, Einheit Nm
              // ft_sensor_data[4], Drehmoment um die y-Achse, Einheit Nm
              // ft_sensor_data[5], Drehmoment um die z-Achse, Einheit Nm 
      uint8_t ft_sensor_active;  // Aktivierungsstatus des Kraft-/Drehmomentsensors, 0-zurückgesetzt, 1-aktiviert 
      uint8_t EmergencyStop;   // Not-Halt-Flag, 0-Not-Halt nicht gedrückt, 1-Not-Halt gedrückt 
      int   motion_done;    // Bewegung-abgeschlossen-Signal, 1-abgeschlossen, 0-nicht abgeschlossen 
      uint8_t gripper_motiondone; // Greifer-Bewegungsabschluss-Signal, 0-nicht abgeschlossen, 1-abgeschlossen (kein Objekt erkannt), 2-Bewegung abgeschlossen (Objekt erkannt)
      int   mc_queue_len;    // Länge der Bewegungskommando-Warteschlange 
      uint8_t collisionState;   // Kollisionserkennung, 1-Kollision, 0-keine Kollision 
      int   trajectory_pnum;  // Bahnpunktnummer 
      uint8_t safety_stop0_state; // Sicherheitsstoppsignal SI0 
      uint8_t safety_stop1_state; // Sicherheitsstoppsignal SI1 
      uint8_t gripper_fault_id;  // Fehlerhafte Greifernummer 
      uint16_t gripper_fault;   // Greiferfehler 0-kein Fehler 1-485-Timeout 2-Befehlsfehler 3-Werkstückabfall Sonstiges-Greifer-Fehlercode 
      uint16_t gripper_active;   // Greifer-Aktivierungsstatus 
      uint8_t gripper_position;  // Greiferposition 
      int8_t  gripper_speed;   // Greifergeschwindigkeit 
      int8_t  gripper_current;  // Greiferstrom 
      int   gripper_temp;    // Greifertemperatur 
      int   gripper_voltage;  // Greiferspannung 
      robot_aux_state aux_state;  // 485 Erweiterungsachsenstatus
      EXT_AXIS_STATUS extAxisStatus[4]; // UDP Erweiterungsachsenstatus 
      uint16_t extDIState[8];    // Erweiterter DI-Eingang
      uint16_t extDOState[8];    // Erweiterter DO-Ausgang
      uint16_t extAIState[4];    // Erweiterter AI-Eingang
      uint16_t extAOState[4];    // Erweiterter AO-Ausgang
      int rbtEnableState;      // Roboter-Aktivierungsstatus
      double  jointDriverTorque[6];    // Roboter-Gelenktreiber-Drehmoment
      double  jointDriverTemperature[6];  // Roboter-Gelenktreiber-Temperatur
      RobotTime robotTime;      // Roboter-Systemzeit
      int softwareUpgradeState;   // Roboter-Software-Upgrade-Status
      uint16_t endLuaErrCode;    // End-Lua-Status
      uint16_t cl_analog_output[2]; // Analoger Ausgang des Steuerkastens
      uint16_t tl_analog_output;   // Analoger Werkzeugausgang
      float gripperRotNum;      // Aktuelle Drehzahl des rotierenden Greifers
      uint8_t gripperRotSpeed;    // Aktuelle Drehzahl-Prozentsatz des rotierenden Greifers
      uint8_t gripperRotTorque;   // Aktuelles Drehmoment-Prozentsatz des rotierenden Greifers
      WELDING_BREAKOFF_STATE weldingBreakOffState; // Schweißunterbrechungsstatus
      double jt_tgt_tor[6];         // Gelenkbefehls-Drehmoment
      int smartToolState;          // SmartTool-Griffknopfstatus
      float wideVoltageCtrlBoxTemp;     // Weitspannungs-Steuerkastentemperatur
      uint16_t wideVoltageCtrlBoxFanCurrent;// Weitspannungs-Steuerkasten-Lüfterstrom (mA)
      double toolCoord[6];    // Aktuelle Werkzeugkoordinatensystemwerte; x,y,z,rx,ry,rz
      double wobjCoord[6];    // Aktuelle Werkstückkoordinatensystemwerte; x,y,z,rx,ry,rz
      double extoolCoord[6];   // Aktuelle externe Werkzeugkoordinatensystemwerte; x,y,z,rx,ry,rz
      double exAxisCoord[6];   // Aktuelle Erweiterungsachsenkoordinatensystemwerte; x,y,z,rx,ry,rz
      double load;        // Lastmasse
      double loadCog[3];     // Lastschwerpunkt
      double lastServoTarget[6]; // Letzte ServoJ-Zielposition in der Warteschlange
      int servoJCmdNum;      // ServoJ-Befehlszähler
      double targetJointPos[6];  // 6 Gelenke Befehlsposition, Einheit °
      double targetJointVel[6];  // 6 Gelenke Befehlgeschwindigkeit, Einheit °/s
      double targetJointAcc[6];  // 6 Gelenke Befehlbeschleunigung, Einheit °/s2
      double targetJointCurrent[6]; // 6 Gelenke Befehlstrom, Einheit A
      double actualJointCurrent[6]; // 6 Gelenke aktueller Strom, Einheit A
      double actualTCPForce[6];  // Roboter-Endeffektor-Drehmoment Nm; x,y,z,rx,ry,rz
      double targetTCPPos[6];   // Roboter-TCP-Befehlsposition mm; x,y,z,rx,ry,rz
      uint8_t collisionLevel[6]; // Roboter-Kollisionsstufe
      double speedScaleManual;  // Handmodus globale Geschwindigkeitsprozentsatz
      double speedScaleAuto;   // Automatikmodus globale Geschwindigkeitsprozentsatz
      int luaLineNum;       // Aktuelle Lua-Programmzeilennummer
      uint8_t abnomalStop;    // 0-keine Abnormalität; 1-Abnormalität vorhanden
      char currentLuaFileName[256]; // Name des aktuell ausgeführten Lua-Programms
      uint8_t programTotalLine;  // Gesamtzeilen des Lua-Programms
      uint8_t safetyBoxSingal[6]; // Roboter-Tastenfeld-Tastenstatus
      double weldVoltage;     // Schweißspannung V
      double weldCurrent;     // Schweißstrom
      double weldTrackVel;    // Schweißnahtverfolgungsgeschwindigkeit mm/s
      uint8_t tpdException;    // TPD-Bahnladeanzahl überschritten, 0-nicht überschritten, 1-überschritten 
      uint8_t alarmRebootRobot;  // Warnung, 1-Not-Halt-Taste loslassen und Steuerkasten neu starten, 2-Gelenkkommunikationsstörung, Steuerkasten neu starten
      uint8_t modbusMasterConnect; // bit0-bit7 entsprechen ModbusTCP-Master 0-7 Verbindungsstatus 0-nicht verbunden 1-verbunden
      uint8_t modbusSlaveConnect;  // ModbusTCP-Slave-Verbindungsstatus 0-nicht verbunden; 1-verbunden
      uint8_t btnBoxStopSignal;   // Tastenfeld-Not-Halt-Signal, 0-Not-Halt losgelassen; 1-Not-Halt gedrückt
      uint8_t dragAlarm;      // Zieh-Warnung, aktuell im Automatikmodus, 0-keine Warnung, 1-Warnung, 2-Positionsrückmeldungsstörung, kein Wechsel
      uint8_t safetyDoorAlarm;   // Sicherheitstürwarnung; 0-Sicherheitstür geschlossen; 1-Sicherheitstür geöffnet
      uint8_t safetyPlaneAlarm;   // Eintritt in Sicherheitswand-Warnung; 0-nicht in Sicherheitswand eingetreten; 1-in Sicherheitswand eingetreten
      uint8_t motonAlarm;      // Bewegungswarnung
      uint8_t interfaceAlarm;    // Eintritt in Interferenzbereich-Warnung
      int udpCmdState;       // Port 20007 UDP-Kommunikationsverbindungsstatus
      uint8_t weldReadyState;    // Schweißgerät-Bereitschaftsstatus
      uint8_t alarmCheckEmergStopBtn; // 0-normal; 1-Kommunikationsstörung, prüfen ob Not-Halt-Taste losgelassen ist
      uint8_t tsTmCmdComError;   // 0-normal; 1-Drehmomentbefehl-Kommunikationsfehler
      uint8_t tsTmStateComError;  // 0-normal; 1-Drehmomentstatus-Kommunikationsfehler
      int ctrlBoxError;       // Steuerkastenfehler
      uint8_t safetyDataState;   // Sicherheitsdatenstatus-Flag, 0-normal, 1-abnormal
      uint8_t forceSensorErrState; // Kraftsensor-Verbindungszeitüberschreitungsfehler; bit0-bit1 entsprechen Kraftsensor ID1-ID2
      uint8_t ctrlOpenLuaErrCode[4]; // 4 Controller-Peripherieprotokoll-Fehlercodes (500 Fehlercode)
      uint8_t strangePosFlag; // Derzeit in singulärer Pose-Flag; 0-normal; 1-singuläre Pose
      uint8_t alarm;      // Warnung
      uint8_t driverAlarm;   // Treiber-Alarmachsenummer
      uint8_t aliveSlaveNumError; // Aktiver Slave-Anzahlfehler, 0: normal; 1: Anzahlfehler
      uint8_t slaveComError[8];  // Slave-Fehler, 0: normal; 1: Slave offline; 2: Slave-Status stimmt nicht mit eingestelltem Wert überein; 3: Slave nicht konfiguriert; 4: Slave-Konfigurationsfehler; 5: Slave-Initialisierungsfehler; 6: Slave-Mailbox-Kommunikationsinitialisierungsfehler
      uint8_t cmdPointError;   // Befehlspunktfehler
      uint8_t IOError;      // IO-Fehler
      uint8_t gripperError;    // Greiferfehler
      uint8_t fileError;     // Dateifehler
      uint8_t paraError;     // Parameterfehler
      uint8_t exaxisOutLimitError;  // Externe Achse Weichgrenzenüberschreitungsfehler
      uint8_t driverComError[6];   // Treiberkommunikationsfehler
      uint8_t driverError;      // Treiberkommunikationsfehler-Achsennummer
      uint8_t outSoftLimitError;   // Weichgrenzenüberschreitungsfehler
      char axleGenComData[130];   // Roboter-Endeffektor-Transparentübertragungs-Rückmeldedaten
      uint8_t socketConnTimeout;   // Socket-Verbindungszeitüberschreitung, bit0-bit4: socketID 1-4
      uint8_t socketReadTimeout;   // Socket-Lesezeitüberschreitung, bit0-bit4: socketID 1-4
      uint8_t tsWebStateComErr;   // Web-Drehmoment-Kommunikationsfehler; 0-normal; 1-fehlgeschlagen
      uint8_t exaxisCoordID;     //Kennung des erweiterten Achskoordinatensystems
      uint8_t programRunState;   // LUA-Programmausführungsstatus 0-Programm läuft nicht; 1-Programm läuft (einschließlich Programm pausiert)
      uint16_t check_sum;     // Summenprüfung
    }ROBOT_STATE_PKG;

Aufzählungstyp für Roboterstatus-Rückmeldungskonfiguration
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    enum class RobotState
    {
        ProgramState = 3,           // Programmstatus, 1-gestoppt; 2-läuft; 3-pausiert
        RobotState = 4,             // Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-ziehen
        MainCode = 5,               // Hauptfehlercode
        SubCode = 6,                // Unterfehlercode
        RobotMode = 7,              // Robotermodus, 1-Handmodus; 0-Automatikmodus
        JointCurPos = 8,            // Aktuelle Gelenkpositionen von 6 Achsen, Einheit deg
        ToolCurPos = 9,             // Aktuelle Werkzeugposition: [0] entlang x-Achse (mm), [1] entlang y-Achse (mm), [2] entlang z-Achse (mm), [3] Drehung um feste X-Achse (deg), [4] um feste Y-Achse (deg), [5] um feste Z-Achse (deg)
        FlangeCurPos = 10,          // Aktuelle Endflanschposition: [0] entlang x-Achse (mm), [1] entlang y-Achse (mm), [2] entlang z-Achse (mm), [3] Drehung um feste X-Achse (deg), [4] um feste Y-Achse (deg), [5] um feste Z-Achse (deg)
        ActualJointVel = 11,        // Aktuelle Geschwindigkeiten von 6 Gelenken, Einheit deg/s
        ActualJointAcc = 12,        // Aktuelle Beschleunigungen von 6 Gelenken, Einheit deg/s^2
        TargetTCPCmpSpeed = 13,     // TCP zusammengesetzte Befehlgeschwindigkeit: [0] Position (mm/s), [1] Orientierung (deg/s)
        TargetTCPSpeed = 14,        // TCP Befehlgeschwindigkeit: [0] entlang x-Achse (mm/s), [1] entlang y-Achse (mm/s), [2] entlang z-Achse (mm/s), [3] Winkelgeschwindigkeit um X-Achse (deg/s), [4] um Y-Achse (deg/s), [5] um Z-Achse (deg/s)
        ActualTCPCmpSpeed = 15,     // TCP zusammengesetzte tatsächliche Geschwindigkeit: [0] Position (mm/s), [1] Orientierung (deg/s)
        ActualTCPSpeed = 16,        // TCP tatsächliche Geschwindigkeit: [0] entlang x-Achse (mm/s), [1] entlang y-Achse (mm/s), [2] entlang z-Achse (mm/s), [3] Winkelgeschwindigkeit um X-Achse (deg/s), [4] um Y-Achse (deg/s), [5] um Z-Achse (deg/s)
        ActualJointTorque = 17,     // Aktuelle Drehmomente von 6 Achsen, Einheit N·m
        Tool = 18,                  // Angewandtes Werkzeugkoordinatensystem Nummer
        User = 19,                  // Angewandtes Werkstückkoordinatensystem Nummer
        ClDgtOutputH = 20,          // Digitaler IO-Ausgang des Steuerkastens 15-8
        ClDgtOutputL = 21,          // Digitaler IO-Ausgang des Steuerkastens 7-0
        TlDgtOutputL = 22,          // Digitaler IO-Ausgang des Werkzeugs 7-0, nur bit0-bit1 gültig
        ClDgtInputH = 23,           // Digitaler IO-Eingang des Steuerkastens 15-8
        ClDgtInputL = 24,           // Digitaler IO-Eingang des Steuerkastens 7-0
        TlDgtInputL = 25,           // Digitaler IO-Eingang des Werkzeugs 7-0, nur bit0-bit1 gültig
        ClAnalogInput = 26,         // Analoger Eingang des Steuerkastens: [0] Kanal 0, [1] Kanal 1
        TlAnalogInput = 27,         // Analoger Werkzeugeingang
        FtSensorRawData = 28,       // Rohdaten des Kraft-/Drehmomentsensors: [0] Kraft entlang x-Achse (N), [1] entlang y-Achse (N), [2] entlang z-Achse (N), [3] Drehmoment um x-Achse (Nm), [4] um y-Achse (Nm), [5] um z-Achse (Nm)
        FtSensorData = 29,          // Daten des Kraft-/Drehmomentsensors (verarbeitet): [0] Kraft entlang x-Achse (N), [1] entlang y-Achse (N), [2] entlang z-Achse (N), [3] Drehmoment um x-Achse (Nm), [4] um y-Achse (Nm), [5] um z-Achse (Nm)
        FtSensorActive = 30,        // Aktivierungsstatus des Kraft-/Drehmomentsensors, 0-zurückgesetzt, 1-aktiviert
        EmergencyStop = 31,         // Not-Halt-Flag, 0-Not-Halt nicht gedrückt, 1-Not-Halt gedrückt
        MotionDone = 32,            // Bewegung-abgeschlossen-Signal, 1-abgeschlossen, 0-nicht abgeschlossen
        GripperMotiondone = 33,     // Greiferbewegung-abgeschlossen-Signal, 1-abgeschlossen, 0-nicht abgeschlossen
        McQueueLen = 34,            // Länge der Bewegungskommando-Warteschlange
        CollisionState = 35,        // Kollisionserkennung, 1-Kollision, 0-keine Kollision
        TrajectoryPnum = 36,        // Bahnpunktnummer
        SafetyStop0State = 37,      // Sicherheitsstoppsignal SI0
        SafetyStop1State = 38,      // Sicherheitsstoppsignal SI1
        GripperFaultId = 39,        // Fehlerhafte Greifernummer
        GripperFault = 40,          // Greiferfehler
        GripperActive = 41,         // Greifer-Aktivierungsstatus
        GripperPosition = 42,       // Greiferposition
        GripperSpeed = 43,          // Greifergeschwindigkeit
        GripperCurrent = 44,        // Greiferstrom
        GripperTemp = 45,           // Greifertemperatur
        GripperVoltage = 46,        // Greiferspannung
        AuxState = 47,              // 485 Erweiterungsachsenstatus
        ExtAxisStatus = 48,         // UDP Erweiterungsachsenstatus (4 Achsen)
        ExtDIState = 49,            // Erweiterter DI-Eingang (8)
        ExtDOState = 50,            // Erweiterter DO-Ausgang (8)
        ExtAIState = 51,            // Erweiterter AI-Eingang (4)
        ExtAOState = 52,            // Erweiterter AO-Ausgang (4)
        RbtEnableState = 53,        // Roboter-Aktivierungsstatus
        JointDriverTorque = 54,     // Roboter-Gelenktreiber-Drehmoment (6 Gelenke)
        JointDriverTemperature = 55,// Roboter-Gelenktreiber-Temperatur (6 Gelenke)
        RobotTime = 56,             // Roboter-Systemzeit
        SoftwareUpgradeState = 57,  // Roboter-Software-Upgrade-Status
        EndLuaErrCode = 58,         // End-Lua-Status
        ClAnalogOutput = 59,        // Analoger Ausgang des Steuerkastens (2)
        TlAnalogOutput = 60,        // Analoger Werkzeugausgang
        GripperRotNum = 61,         // Aktuelle Drehzahl des rotierenden Greifers
        GripperRotSpeed = 62,       // Aktuelle Drehzahl-Prozentsatz des rotierenden Greifers
        GripperRotTorque = 63,      // Aktuelles Drehmoment-Prozentsatz des rotierenden Greifers
        WeldingBreakOffState = 64,  // Schweißunterbrechungsstatus
        TargetJointTorque = 65,     // Gelenkbefehls-Drehmoment (6 Gelenke)
        SmartToolState = 66,        // SmartTool-Griffknopfstatus
        WideVoltageCtrlBoxTemp = 67,// Weitspannungs-Steuerkastentemperatur
        WideVoltageCtrlBoxFanCurrent = 68, // Weitspannungs-Steuerkasten-Lüfterstrom (mA)
        ToolCoord = 69,             // Aktuelle Werkzeugkoordinatensystemwerte: x,y,z,rx,ry,rz
        WobjCoord = 70,             // Aktuelle Werkstückkoordinatensystemwerte: x,y,z,rx,ry,rz
        ExtoolCoord = 71,           // Aktuelle externe Werkzeugkoordinatensystemwerte: x,y,z,rx,ry,rz
        ExAxisCoord = 72,           // Aktuelle Erweiterungsachsenkoordinatensystemwerte: x,y,z,rx,ry,rz
        Load = 73,                  // Lastmasse
        LoadCog = 74,               // Lastschwerpunkt: x,y,z
        LastServoTarget = 75,       // Letzte ServoJ-Zielposition in der Warteschlange (6 Gelenke)
        ServoJCmdNum = 76,          // ServoJ-Befehlszähler
        TargetJointPos = 77,        // 6 Gelenke Befehlsposition, Einheit °
        TargetJointVel = 78,        // 6 Gelenke Befehlgeschwindigkeit, Einheit °/s
        TargetJointAcc = 79,        // 6 Gelenke Befehlbeschleunigung, Einheit °/s²
        TargetJointCurrent = 80,    // 6 Gelenke Befehlstrom, Einheit A
        ActualJointCurrent = 81,    // 6 Gelenke aktueller Strom, Einheit A
        ActualTCPForce = 82,        // Roboter-Endeffektor-Drehmoment: x,y,z,rx,ry,rz, Einheit Nm
        TargetTCPPos = 83,          // Roboter-TCP-Befehlsposition: x,y,z,rx,ry,rz, Einheit mm
        CollisionLevel = 84,        // Roboter-Kollisionsstufe (6)
        SpeedScaleManual = 85,      // Handmodus globale Geschwindigkeitsprozentsatz
        SpeedScaleAuto = 86,        // Automatikmodus globale Geschwindigkeitsprozentsatz
        LuaLineNum = 87,            // Aktuelle Lua-Programmzeilennummer
        AbnomalStop = 88,           // 0-keine Abnormalität; 1-Abnormalität vorhanden
        CurrentLuaFileName = 89,    // Name des aktuell ausgeführten Lua-Programms
        ProgramTotalLine = 90,      // Gesamtzeilen des Lua-Programms
        SafetyBoxSingal = 91,       // Roboter-Tastenfeld-Tastenstatus (6)
        WeldVoltage = 92,           // Schweißspannung V
        WeldCurrent = 93,           // Schweißstrom
        WeldTrackVel = 94,          // Schweißnahtverfolgungsgeschwindigkeit mm/s
        TpdException = 95,          // TPD-Bahnladeanzahl überschritten, 0-nicht überschritten, 1-überschritten
        AlarmRebootRobot = 96,      // Warnung: 1-Not-Halt-Taste loslassen und Steuerkasten neu starten, 2-Gelenkkommunikationsstörung, Steuerkasten neu starten
        ModbusMasterConnect = 97,   // bit0-7 entsprechen ModbusTCP-Master 0-7 Verbindungsstatus, 0-nicht verbunden, 1-verbunden
        ModbusSlaveConnect = 98,    // ModbusTCP-Slave-Verbindungsstatus, 0-nicht verbunden, 1-verbunden
        BtnBoxStopSignal = 99,      // Tastenfeld-Not-Halt-Signal, 0-Not-Halt losgelassen, 1-Not-Halt gedrückt
        DragAlarm = 100,            // Zieh-Warnung: 0-keine Warnung, 1-Warnung, 2-Positionsrückmeldungsstörung, kein Wechsel
        SafetyDoorAlarm = 101,      // Sicherheitstürwarnung: 0-geschlossen, 1-geöffnet
        SafetyPlaneAlarm = 102,     // Sicherheitswandwarnung: 0-nicht eingetreten, 1-eingetreten
        MotonAlarm = 103,           // Bewegungswarnung
        InterfaceAlarm = 104,       // Eintritt in Interferenzbereich-Warnung
        UdpCmdState = 105,          // Port 20007 UDP-Kommunikationsverbindungsstatus
        WeldReadyState = 106,       // Schweißgerät-Bereitschaftsstatus
        AlarmCheckEmergStopBtn = 107, // 0-normal; 1-Kommunikationsstörung, prüfen ob Not-Halt-Taste losgelassen ist
        TsTmCmdComError = 108,      // 0-normal; 1-Drehmomentbefehl-Kommunikationsfehler
        TsTmStateComError = 109,    // 0-normal; 1-Drehmomentstatus-Kommunikationsfehler
        CtrlBoxError = 110,         // Steuerkastenfehler
        SafetyDataState = 111,      // Sicherheitsdatenstatus, 0-normal, 1-abnormal
        ForceSensorErrState = 112,  // Kraftsensor-Verbindungszeitüberschreitung, bit0-bit1 entsprechen ID1-ID2
        CtrlOpenLuaErrCode = 113,   // 4 Controller-Peripherieprotokoll-Fehlercodes (500 Fehlercode)
        StrangePosFlag = 114,       // Singuläre Posenkennzeichnung: 0-normal, 1-singuläre Pose
        Alarm = 115,                // Warnung
        DriverAlarm = 116,          // Treiber-Alarmachsenummer
        AliveSlaveNumError = 117,   // Aktiver Slave-Anzahlfehler: 0-normal, 1-Anzahlfehler
        SlaveComError = 118,        // Slave-Fehler: 0-normal, 1-offline, 2-Status inkonsistent, 3-nicht konfiguriert, 4-Konfigurationsfehler, 5-Initialisierungsfehler, 6-Mailbox-Kommunikationsinitialisierungsfehler
        CmdPointError = 119,        // Befehlspunktfehler
        IOError = 120,              // IO-Fehler
        GripperError = 121,         // Greiferfehler
        FileError = 122,            // Dateifehler
        ParaError = 123,            // Parameterfehler
        ExaxisOutLimitError = 124,  // Externe Achse Weichgrenzenüberschreitungsfehler
        DriverComError = 125,       // Treiberkommunikationsfehler (6 Achsen)
        DriverError = 126,          // Treiberkommunikationsfehler-Achsennummer
        OutSoftLimitError = 127,    // Weichgrenzenüberschreitungsfehler
        AxleGenComData = 128,       // Roboter-Endeffektor-Transparentübertragungs-Rückmeldedaten
        SocketConnTimeout = 129,    // Socket-Verbindungszeitüberschreitung, bit0-bit4 entsprechen socketID 1-4
        SocketReadTimeout = 130,    // Socket-Lesezeitüberschreitung, bit0-bit4 entsprechen socketID 1-4
        TsWebStateComErr = 131,     // Web-Drehmoment-Kommunikationsfehler: 0-normal, 1-fehlgeschlagen
        ExaxisCoordID = 132          //Kennung des erweiterten Achskoordinatensystems
        programRunState = 133       //LUA-Programmausführungsstatus 0-Programm läuft nicht; 1-Programm läuft (einschließlich Programm pausiert)
    };