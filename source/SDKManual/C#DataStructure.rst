Beschreibung der Datenstrukturen
========================================

.. toctree::
    :maxdepth: 5

Datentyp für Gelenkpositionen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Datentyp für Gelenkpositionen.
    */
    struct JointPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jPos;   /* Sechs Gelenkpositionen, Einheit deg */
    }

Datentyp für Positionen im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Datentyp für Positionen im kartesischen Raum.
    */
    struct DescTran
    {
        public double x;    /* x-Achsen-Koordinate, Einheit mm  */
        public double y;    /* y-Achsen-Koordinate, Einheit mm  */
        public double z;    /* z-Achsen-Koordinate, Einheit mm  */
    }

Datentyp für Euler-Winkel-Ausrichtung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Datentyp für Euler-Winkel-Ausrichtung.
    */
    struct Rpy
    {
        public double rx;   /* Rotationswinkel um die feste X-Achse, Einheit: deg  */
        public double ry;   /* Rotationswinkel um die feste Y-Achse, Einheit: deg  */
        public double rz;   /* Rotationswinkel um die feste Z-Achse, Einheit: deg  */
    }

Datentyp für Posen im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Datentyp für Posen im kartesischen Raum.
    */
    struct DescPose
    {
        public DescTran tran;     /* Position im kartesischen Raum  */
        public Rpy rpy;           /* Ausrichtung im kartesischen Raum  */
    }

Datentyp für Positionen der Erweiterungsachse
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Datentyp für Positionen der Erweiterungsachse.
    */
    struct ExaxisPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public double[] ePos;   /* Positionen der vier Erweiterungsachsen, Einheit mm */
    }

Datentyp für Kraft-/Drehmomentsensor
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    /**
    * @brief Kraftkomponenten und Drehmomentkomponenten des Kraftsensors.
    */
    struct ForceTorque
    {
        public double fx;  /* Kraftkomponente entlang der x-Achse, Einheit N  */
        public double fy;  /* Kraftkomponente entlang der y-Achse, Einheit N  */
        public double fz;  /* Kraftkomponente entlang der z-Achse, Einheit N  */
        public double tx;  /* Drehmomentkomponente um die x-Achse, Einheit Nm */
        public double ty;  /* Drehmomentkomponente um die y-Achse, Einheit Nm */
        public double tz;  /* Drehmomentkomponente um die z-Achse, Einheit Nm */
    }

Datentyp für Spiralparameter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    public struct SpiralParam
    {
        public int circle_num;           /* Anzahl der Windungen  */
        public float circle_angle;       /* Neigungswinkel der Spirale  */
        public float rad_init;            /* Anfangsradius der Spirale, Einheit mm  */
        public float rad_add;             /* Radiusinkrement  */
        public float rotaxis_add;         /* Inkrement in Richtung der Drehachse  */
        public uint rot_direction;        /* Drehrichtung, 0-im Uhrzeigersinn, 1-gegen Uhrzeigersinn  */
        public int velAccMode;            // Modus für Geschwindigkeit/Beschleunigung: 0-Winkelgeschwindigkeit konstant; 1-Lineargeschwindigkeit konstant
        public SpiralParam(int num, float angle, float initRad, float addRad, float axisAdd, uint direction, int mode)
        {
            circle_num = num;
            circle_angle = angle;
            rad_init = initRad;
            rad_add = addRad;
            rotaxis_add = axisAdd;
            rot_direction = direction;
            velAccMode = mode;
        }
    }

Datentyp für Erweiterungsachsen-Status
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: csharp
    :linenos:

    /**
    * @brief Datentyp für den Status der Erweiterungsachse.
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct ROBOT_AUX_STATE
    {
        public byte servoId;           // Servoantriebs-ID-Nummer
        public int servoErrCode;       // Fehlercode des Servoantriebs
        public int servoState;         // Status des Servoantriebs
        public double servoPos;        // Aktuelle Position des Servos
        public float servoVel;         // Aktuelle Geschwindigkeit des Servos
        public float servoTorque;      // Aktuelles Drehmoment des Servos
    }

Schweißunterbrechungsstatus
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: csharp
    :linenos:

    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct WELDING_BREAKOFF_STATE
    {
        public byte breakOffState;  // Schweißunterbrechungsstatus
        public byte weldArcState;   // Lichtbogenunterbrechungsstatus beim Schweißen
    }

Roboterstatus-Feedback-Strukturtyp
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: c#
    :linenos:

    /**
    * @brief  Roboterstatus-Feedback-Strukturtyp
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public class ROBOT_STATE_PKG
    {
        public UInt16 frame_head;           // Rahmenkopf 0x5A5A
        public byte frame_cnt;              // Rahmenzählung
        public UInt16 data_len;             // Datenlänge 5
        public byte program_state;          // Programmausführungsstatus, 1-gestoppt; 2-läuft; 3-pausiert;
        public byte robot_state;            // Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-Ziehen
        public int main_code;               // Hauptfehlercode
        public int sub_code;                // Unterfehlercode
        public byte robot_mode;             // Robotermodus, 1-Handmodus; 0-Automatikmodus;

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_pos;         // Aktuelle Gelenkpositionen von 6 Achsen, Einheit deg
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] tl_cur_pos;         // Aktuelle Werkzeugposition (TCP)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] flange_cur_pos;     // Aktuelle Position des Endflansches
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qd;          // Aktuelle Geschwindigkeiten von 6 Gelenken, Einheit deg/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qdd;         // Aktuelle Beschleunigungen von 6 Gelenken, Einheit deg/s^2
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] target_TCP_CmpSpeed;// TCP-Synthese-Sollgeschwindigkeit (Position, Orientierung)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] target_TCP_Speed;   // TCP-Sollgeschwindigkeit
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] actual_TCP_CmpSpeed;// TCP-Synthese-Istgeschwindigkeit
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_TCP_Speed;   // TCP-Istgeschwindigkeit
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_tor;         // Aktuelle Drehmomente von 6 Achsen, Einheit N·m

        public int tool;                    // Angewandte Werkzeugkoordinatensystem-Nummer
        public int user;                    // Angewandte Werkstückkoordinatensystem-Nummer
        public byte cl_dgt_output_h;        // Digitale IO-Ausgabe des Steuerkastens 15-8
        public byte cl_dgt_output_l;        // Digitale IO-Ausgabe des Steuerkastens 7-0
        public byte tl_dgt_output_l;        // Digitale IO-Ausgabe des Werkzeugs 7-0, nur Bits 0-1 gültig
        public byte cl_dgt_input_h;         // Digitale IO-Eingabe des Steuerkastens 15-8
        public byte cl_dgt_input_l;         // Digitale IO-Eingabe des Steuerkastens 7-0
        public byte tl_dgt_input_l;         // Digitale IO-Eingabe des Werkzeugs 7-0, nur Bits 0-1 gültig

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public UInt16[] cl_analog_input;        // Analogeingänge des Steuerkastens
        public UInt16 tl_anglog_input;          // Analogeingang des Werkzeugs

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_raw_data; // Rohdaten des Drehmomentsensors
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_data;     // Daten des Drehmomentsensors
        public byte ft_sensor_active;       // Aktivierungsstatus des Drehmomentsensors, 0-Zurücksetzen, 1-aktiviert

        public byte EmergencyStop;          // Not-Halt-Flag, 0-nicht gedrückt, 1-gedrückt
        public int motion_done;             // Bewegungsabschluss-Signal, 1-abgeschlossen, 0-nicht abgeschlossen
        public byte gripper_motiondone;     // Greifer-Bewegungsabschluss-Signal, 0-nicht abgeschlossen, 1-abgeschlossen (kein Objekt erkannt), 2-Bewegung abgeschlossen (Objekt erkannt)
        public int mc_queue_len;            // Länge der Bewegungskommando-Warteschlange
        public byte collisionState;         // Kollisionserkennung, 1-Kollision, 0-keine Kollision
        public int trajectory_pnum;         // Trajektorienpunktnummer
        public byte safety_stop0_state;     // Sicherheitsstoppsignal SI0
        public byte safety_stop1_state;     // Sicherheitsstoppsignal SI1
        public byte gripper_fault_id;       // ID des fehlerhaften Greifers
        public UInt16 gripper_fault;     /* Greiferfehler 0-kein Fehler 1-485-Timeout 2-Befehlsfehler 3-Werkstückabfall Sonstiges-Greifer-Fehlercode */
        public UInt16 gripper_active;    /* Greiferaktivierungsstatus */
        public byte gripper_position;       // Greiferposition
        public byte gripper_speed;       /* Greifergeschwindigkeit */
        public byte gripper_current;     /* Greiferstrom */
        public int gripper_temp;            // Greifertemperatur
        public int gripper_voltage;         // Greiferspannung

        public ROBOT_AUX_STATE auxState;   // 485 Erweiterungsachsenstatus

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public EXT_AXIS_STATUS[] extAxisStatus; // UDP Erweiterungsachsenstatus

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDIState;        // Erweiterte DI-Eingänge
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDOState;        // Erweiterte DO-Ausgänge
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAIState;        // Erweiterte AI-Eingänge
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAOState;        // Erweiterte AO-Ausgänge

        public int rbtEnableState;          // Roboter-Freigabestatus

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTorque;      // Roboter-Gelenktreiber-Drehmomente
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTemperature; // Roboter-Gelenktreiber-Temperaturen

        public ROBOT_TIME robotTime;        // Roboter-Systemzeit
        public int softwareUpgradeState;    // Roboter-Software-Upgrade-Status
        public UInt16 endLuaErrCode;    // End-LUA-Ausführungsstatus

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public  UInt16[] cl_analog_output;  // Analogausgänge des Steuerkastens
        public UInt16 tl_analog_output;     // Analogausgang des Werkzeugs

        public float gripperRotNum;         // Aktuelle Umdrehungszahl des rotierenden Greifers
        public byte gripperRotSpeed;        // Aktuelle Geschwindigkeitsprozent des rotierenden Greifers
        public byte gripperRotTorque;       // Aktuelles Drehmomentprozent des rotierenden Greifers

        public WELDING_BREAKOFF_STATE weldingBreakOffState; // Schweißunterbrechungsstatus

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_tgt_tor;         // Gelenk-Solldrehmomente
        public int smartToolState;          // SmartTool-Griffknopfstatus
        public float wideVoltageCtrlBoxTemp; // Temperatur des Weitspannungs-Steuerkastens
        public UInt16 wideVoltageCtrlBoxFanVel;   // Lüfterstrom des Weitspannungs-Steuerkastens (mA)

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] toolCoord;          // Aktuelle Werkzeugkoordinatenwerte; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] wobjCoord;          // Aktuelle Werkstückkoordinatenwerte; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] extoolCoord;        // Aktuelle externe Werkzeugkoordinatenwerte; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] exAxisCoord;        // Aktuelle Erweiterungsachsen-Koordinatenwerte; x,y,z,rx,ry,rz

        public double load;                 // Lastmasse
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 3)]
        public double[] loadCog;            // Lastschwerpunkt
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] lastServoTarget;    // Letzte ServoJ-Zielposition in der Warteschlange
        public int servoJCmdNum;            // servoJ-Kommandozähler

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointPos;     // Sollpositionen von 6 Gelenken, Einheit °
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointVel;     // Sollgeschwindigkeiten von 6 Gelenken, Einheit °/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointAcc;     // Sollbeschleunigungen von 6 Gelenken, Einheit °/s²
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointCurrent; // Sollströme von 6 Gelenken, Einheit A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualJointCurrent; // Istströme von 6 Gelenken, Einheit A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualTCPForce;     // Roboters-Endeffektor-Drehmoment Nm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetTCPPos;       // Roboter-TCP-Sollposition mm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] collisionLevel;       // Roboter-Kollisionsstufen

        public double speedScaleManual;     // Globale Geschwindigkeitsprozent im Handmodus
        public double speedScaleAuto;       // Globale Geschwindigkeitsprozent im Automatikmodus
        public int luaLineNum;              // Aktuelle Zeilennummer des laufenden Lua-Programms
        public byte abnomalStop;            // 0-keine Anomalie; 1-Anomalie vorhanden

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 256)]
        public byte[] currentLuaFileName;   // Name des aktuell laufenden Lua-Programms
        public byte programTotalLine;       // Gesamtzeilen des Lua-Programms
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] safetyBoxSingal;      // Roboter-Tastenbox-Knopfstatus

        public double weldVoltage;          // Schweißspannung V
        public double weldCurrent;          // Schweißstrom
        public double weldTrackVel;         // Schweißnahtverfolgungsgeschwindigkeit mm/s

        public byte tpdException;           // TPD-Trajektorienladungsüberschreitung, 0-nicht überschritten, 1-überschritten
        public byte alarmRebootRobot;       // Warnung, 1-Not-Halt-Taste loslassen und Steuerkasten neu starten, 2-Gelenkkommunikationsanomalie, Steuerkasten neu starten
        public byte modbusMasterConnect;    // Bits 0-7 entsprechen ModbusTCP-Master 0-7 Verbindungsstatus 0-nicht verbunden 1-verbunden
        public byte modbusSlaveConnect;     // ModbusTCP-Slave-Verbindungsstatus 0-nicht verbunden; 1-verbunden
        public byte btnBoxStopSignal;       // Not-Halt-Signal der Tastenbox, 0-Not-Halt gelöst; 1-Not-Halt gedrückt
        public byte dragAlarm;              // Zieh-Warnung, aktuell im Automatikmodus, 0-kein Alarm, 1-Alarm, 2-Positionsrückmeldeanomalie, keine Umschaltung
        public byte safetyDoorAlarm;        // Sicherheitstür-Warnung; 0-Sicherheitstür geschlossen; 1-Sicherheitstür offen
        public byte safetyPlaneAlarm;       // Sicherheitswand-Eintrittswarnung; 0-nicht in Sicherheitswand eingetreten; 1-in Sicherheitswand eingetreten
        public byte motonAlarm;             // Bewegungswarnung
        public byte interfaceAlarm;         // Interferenzbereich-Eintrittswarnung
        public int udpCmdState;             // UDP-Kommunikationsverbindungsstatus auf Port 20007
        public byte weldReadyState;         // Schweißgerät-Bereitschaftsstatus
        public byte alarmCheckEmergStopBtn; // 0-normal; 1-Kommunikationsanomalie, prüfen, ob Not-Halt-Taste gelöst ist
        public byte tsTmCmdComError;        // 0-normal; 1-Drehmomentbefehl-Kommunikationsfehler
        public byte tsTmStateComError;      // 0-normal; 1-Drehmomentstatus-Kommunikationsfehler
        public int ctrlBoxError;            // Steuerkastenfehler
        public byte safetyDataState;        // Sicherheitsdatenstatus-Flag, 0-normal, 1-anomal
        public byte forceSensorErrState;    // Kraftsensor-Verbindungszeitüberschreitungsfehler; Bits 0-1 entsprechen Kraftsensor-ID1-ID2

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public byte[] ctrlOpenLuaErrCode;   // 4 Controller-Peripherieprotokoll-Fehlercodes (500-Fehlercode)

        public byte strangePosFlag;         // Aktuelle singuläre Pose-Flag; 0-normal; 1-singuläre Pose
        public byte alarm;                  // Warnung
        public byte driverAlarm;            // Treiberalarm-Achsennummer
        public byte aliveSlaveNumError;     // Fehler in der Anzahl aktiver Slaves, 0: normal; 1: Anzahlfehler

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public byte[] slaveComError;        // Slave-Fehler, 0: normal; 1: Slave offline; 2: Slave-Status stimmt nicht mit eingestelltem Wert überein; 3: Slave nicht konfiguriert; 4: Slave-Konfigurationsfehler; 5: Slave-Initialisierungsfehler; 6: Slave-Mailbox-Kommunikationsinitialisierungsfehler

        public byte cmdPointError;          // Befehlspunktfehler
        public byte IOError;                // IO-Fehler
        public byte gripperError;           // Greiferfehler
        public byte fileError;              // Dateifehler
        public byte paraError;              // Parameterfehler
        public byte exaxisOutLimitError;    // Externe Achse außerhalb der Weichgrenze

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] driverComError;       // Kommunikationsfehler mit Treiber
        public byte driverError;            // Achsennummer des Treiberkommunikationsfehlers
        public byte outSoftLimitError;      // Weichgrenzenüberschreitungsfehler

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 130)]
        public byte[] axleGenComData;       // Roboter-Endeffektor-Transparentübertragungs-Feedbackdaten

        public byte socketConnTimeout;     // Socket-Verbindungszeitüberschreitungs-Flag
        public byte socketReadTimeout;     // Socket-Lesezeitüberschreitungs-Flag
        public byte tsWebStateComErr;      // ts_web_state_com_err
        public byte exaxisCoordID;         // Nummer des Erweiterungsachsen-Koordinatensystems
        public UInt16 check_sum;         /* Checksumme */

        // Konstruktor: Initialisiert alle Array-Felder
        public ROBOT_STATE_PKG()
        {
            jt_cur_pos = new double[6];
            tl_cur_pos = new double[6];
            flange_cur_pos = new double[6];
            actual_qd = new double[6];
            actual_qdd = new double[6];
            target_TCP_CmpSpeed = new double[2];
            target_TCP_Speed = new double[6];
            actual_TCP_CmpSpeed = new double[2];
            actual_TCP_Speed = new double[6];
            jt_cur_tor = new double[6];
            cl_analog_input = new ushort[2];
            ft_sensor_raw_data = new double[6];
            ft_sensor_data = new double[6];
            extAxisStatus = new EXT_AXIS_STATUS[4];
            extDIState = new ushort[8];
            extDOState = new ushort[8];
            extAIState = new ushort[4];
            extAOState = new ushort[4];
            jointDriverTorque = new double[6];
            jointDriverTemperature = new double[6];
            cl_analog_output = new ushort[2];
            jt_tgt_tor = new double[6];
            toolCoord = new double[6];
            wobjCoord = new double[6];
            extoolCoord = new double[6];
            exAxisCoord = new double[6];
            loadCog = new double[3];
            lastServoTarget = new double[6];
            targetJointPos = new double[6];
            targetJointVel = new double[6];
            targetJointAcc = new double[6];
            targetJointCurrent = new double[6];
            actualJointCurrent = new double[6];
            actualTCPForce = new double[6];
            targetTCPPos = new double[6];
            collisionLevel = new byte[6];
            currentLuaFileName = new byte[256];
            safetyBoxSingal = new byte[6];
            ctrlOpenLuaErrCode = new byte[4];
            slaveComError = new byte[8];
            driverComError = new byte[6];
            axleGenComData = new byte[130];
        }
    }

Aufzählungstyp der Roboterstatus-Rückmeldungskonfiguration
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Roboter konfigurierbare Statusaufzählung, Bereich 0~132
    */
    public enum RobotState
    {
        FrameHead = 0,
        FrameCnt = 1,
        DataLen = 2,
        ProgramState = 3,
        RobotState = 4,
        MainCode = 5,
        SubCode = 6,
        RobotMode = 7,
        JointCurPos = 8,
        ToolCurPos = 9,
        FlangeCurPos = 10,
        ActualJointVel = 11,
        ActualJointAcc = 12,
        TargetTCPCmpSpeed = 13,
        TargetTCPSpeed = 14,
        ActualTCPCmpSpeed = 15,
        ActualTCPSpeed = 16,
        ActualJointTorque = 17,
        Tool = 18,
        User = 19,
        ClDgtOutputH = 20,
        ClDgtOutputL = 21,
        TlDgtOutputL = 22,
        ClDgtInputH = 23,
        ClDgtInputL = 24,
        TlDgtInputL = 25,
        ClAnalogInput = 26,
        TlAnglogInput = 27,
        FtSensorRawData = 28,
        FtSensorData = 29,
        FtSensorActive = 30,
        EmergencyStop = 31,
        MotionDone = 32,
        GripperMotiondone = 33,
        McQueueLen = 34,
        CollisionState = 35,
        TrajectoryPnum = 36,
        SafetyStop0State = 37,
        SafetyStop1State = 38,
        GripperFaultId = 39,
        GripperFault = 40,
        GripperActive = 41,
        GripperPosition = 42,
        GripperSpeed = 43,
        GripperCurrent = 44,
        GripperTemp = 45,
        GripperVoltage = 46,
        AuxState = 47,
        ExtAxisStatus = 48,
        ExtDIState = 49,
        ExtDOState = 50,
        ExtAIState = 51,
        ExtAOState = 52,
        RbtEnableState = 53,
        JointDriverTorque = 54,
        JointDriverTemperature = 55,
        RobotTime = 56,
        SoftwareUpgradeState = 57,
        EndLuaErrCode = 58,
        ClAnalogOutput = 59,
        TlAnalogOutput = 60,
        GripperRotNum = 61,
        GripperRotSpeed = 62,
        GripperRotTorque = 63,
        WeldingBreakOffState = 64,
        TargetJointTorque = 65,
        SmartToolState = 66,
        WideVoltageCtrlBoxTemp = 67,
        WideVoltageCtrlBoxFanCurrent = 68,
        ToolCoord = 69,
        WobjCoord = 70,
        ExtoolCoord = 71,
        ExAxisCoord = 72,
        Load = 73,
        LoadCog = 74,
        LastServoTarget = 75,
        ServoJCmdNum = 76,
        TargetJointPos = 77,
        TargetJointVel = 78,
        TargetJointAcc = 79,
        TargetJointCurrent = 80,
        ActualJointCurrent = 81,
        ActualTCPForce = 82,
        TargetTCPPos = 83,
        CollisionLevel = 84,
        SpeedScaleManual = 85,
        SpeedScaleAuto = 86,
        LuaLineNum = 87,
        AbnomalStop = 88,
        CurrentLuaFileName = 89,
        ProgramTotalLine = 90,
        SafetyBoxSingal = 91,
        WeldVoltage = 92,
        WeldCurrent = 93,
        WeldTrackVel = 94,
        TpdException = 95,
        AlarmRebootRobot = 96,
        ModbusMasterConnect = 97,
        ModbusSlaveConnect = 98,
        BtnBoxStopSignal = 99,
        DragAlarm = 100,
        SafetyDoorAlarm = 101,
        SafetyPlaneAlarm = 102,
        MotonAlarm = 103,
        InterfaceAlarm = 104,
        UdpCmdState = 105,
        WeldReadyState = 106,
        AlarmCheckEmergStopBtn = 107,
        TsTmCmdComError = 108,
        TsTmStateComError = 109,
        CtrlBoxError = 110,
        SafetyDataState = 111,
        ForceSensorErrState = 112,
        CtrlOpenLuaErrCode = 113,
        StrangePosFlag = 114,
        Alarm = 115,
        DriverAlarm = 116,
        AliveSlaveNumError = 117,
        SlaveComError = 118,
        CmdPointError = 119,
        IOError = 120,
        GripperError = 121,
        FileError = 122,
        ParaError = 123,
        ExaxisOutLimitError = 124,
        DriverComError = 125,
        DriverError = 126,
        OutSoftLimitError = 127,
        AxleGenComData = 128,
        SocketConnTimeout = 129,     // Socket-Verbindungszeitüberschreitung, bit0-bit4: socketID 1-4
        SocketReadTimeout = 130,     // Socket-Lesezeitüberschreitung, bit0-bit4: socketID 1-4
        TsWebStateComErr = 131,     // Web-Drehmoment-Kommunikationsfehler; 0-normal; 1-fehlgeschlagen
        ExaxisCoordID = 132          // Nummer des Erweiterungsachsen-Koordinatensystems
    }