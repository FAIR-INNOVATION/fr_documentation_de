Beschreibung der Datenstrukturen
=====================================

.. toctree::
    :maxdepth: 5

Datentyp für Gelenkpositionen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Datentyp für Gelenkpositionen.
    */
    public class JointPos
    {
      double J1;
      double J2;
      double J3;
      double J4;
      double J5;
      double J6;

      public JointPos(double j1, double j2, double j3, double j4, double j5, double j6)
      {
        J1 = j1;
        J2 = j2;
        J3 = j3;
        J4 = j4;
        J5 = j5;
        J6 = j6;
      }

      public JointPos()
      {

      }
    }

Datentyp für Positionen im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Datentyp für Positionen im kartesischen Raum.
    */
    public class DescTran
    {
      public double x = 0.0;    /* x-Achsen-Koordinate, Einheit mm  */
      public double y = 0.0;    /* y-Achsen-Koordinate, Einheit mm  */
      public double z = 0.0;    /* z-Achsen-Koordinate, Einheit mm  */
      public DescTran(double posX, double posY, double posZ)
      {
        x = posX;
        y = posY;
        z = posZ;
      }

      public DescTran()
      {

      }

    }

Datentyp für Euler-Winkel-Ausrichtung
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Datentyp für Euler-Winkel-Ausrichtung.
    */
    public class Rpy
    {
      public double rx = 0.0;   /* Rotationswinkel um die feste X-Achse, Einheit: deg  */
      public double ry = 0.0;   /* Rotationswinkel um die feste Y-Achse, Einheit: deg  */
      public double rz = 0.0;   /* Rotationswinkel um die feste Z-Achse, Einheit: deg  */
      public Rpy(double rotateX, double rotateY, double rotateZ)
      {
        rx = rotateX;
        ry = rotateY;
        rz = rotateZ;
      }
    }

Datentyp für Posen im kartesischen Raum
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Datentyp für Posen im kartesischen Raum.
    */
    public class DescPose
    {
      public DescTran tran = new DescTran(0.0, 0.0, 0.0);      /* Position im kartesischen Raum  */
      public Rpy rpy = new Rpy(0.0, 0.0, 0.0);                  /* Ausrichtung im kartesischen Raum  */

      public DescPose()
      {

      }

      public DescPose(DescTran descTran, Rpy rotateRpy)
      {
        tran = descTran;
        rpy = rotateRpy;
      }

      public DescPose(double tranX, double tranY, double tranZ, double rX, double ry, double rz)
      {
        tran.x = tranX;
        tran.y = tranY;
        tran.z = tranZ;
        rpy.rx = rX;
        rpy.ry = ry;
        rpy.rz = rz;
      }

      public String toString()
      {
        return String.valueOf(tran.x) + "," +  String.valueOf(tran.y) + "," +String.valueOf(tran.z) + "," +String.valueOf(rpy.rx) + "," +String.valueOf(rpy.ry) + "," +String.valueOf(rpy.rz);
      }
    }

Datentyp für Positionen der Erweiterungsachse
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Datentyp für Positionen der Erweiterungsachse.
    */
    public class ExaxisPos
    {
      public double axis1 = 0.0;
      public double axis2 = 0.0;
      public double axis3 = 0.0;
      public double axis4 = 0.0;

      public ExaxisPos()
      {

      }
      public ExaxisPos(double[] exaxisPos)
      {
        axis1 = exaxisPos[0];
        axis2 = exaxisPos[1];
        axis3 = exaxisPos[2];
        axis4 = exaxisPos[3];
      }

      public ExaxisPos(double pos1, double pos2, double pos3, double pos4)
      {
        axis1 = pos1;
        axis2 = pos2;
        axis3 = pos3;
        axis4 = pos4;
      }
    }

Datentyp für Kraft-/Drehmomentsensor
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Kraftkomponenten und Drehmomentkomponenten des Kraftsensors.
    */
    public class ForceTorque
    {
      public double fx;  /* Kraftkomponente entlang der x-Achse, Einheit N  */
      public double fy;  /* Kraftkomponente entlang der y-Achse, Einheit N  */
      public double fz;  /* Kraftkomponente entlang der z-Achse, Einheit N  */
      public double tx;  /* Drehmomentkomponente um die x-Achse, Einheit Nm */
      public double ty;  /* Drehmomentkomponente um die y-Achse, Einheit Nm */
      public double tz;  /* Drehmomentkomponente um die z-Achse, Einheit Nm */
      public ForceTorque(double fX, double fY, double fZ, double tX, double tY, double tZ)
      {
        fx = fX;
        fy = fY;
        fz = fZ;
        tx = tX;
        ty = tY;
        tz = tZ;
      }
    }

Datentyp für Spiralparameter
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Datentyp für Spiralparameter.
    */
    public class SpiralParam
    {
        public int circle_num;           /* Anzahl der Windungen  */
        public double circle_angle;      /* Neigungswinkel der Spirale  */
        public double rad_init;          /* Anfangsradius der Spirale, Einheit mm  */
        public double rad_add;           /* Radiusinkrement  */
        public double rotaxis_add;       /* Inkrement in Richtung der Drehachse  */
        public int rot_direction;        /* Drehrichtung, 0-im Uhrzeigersinn, 1-gegen Uhrzeigersinn  */
        public int velAccMode;           /* Modus für Geschwindigkeit/Beschleunigung: 0-Winkelgeschwindigkeit konstant; 1-Lineargeschwindigkeit konstant */
        public SpiralParam(int circleNum, double circleAngle, double radInit, double radAdd, double rotaxisAdd, int rotDirection, int vel_AccMode)
        {
            circle_num = circleNum;
            circle_angle = circleAngle;
            rad_init = radInit;
            rad_add = radAdd;
            rotaxis_add = rotaxisAdd;
            rot_direction = rotDirection;
            velAccMode = vel_AccMode;
        }
    }

Datentyp für Erweiterungsachsen-Status
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Datentyp für den Status der Erweiterungsachse.
    */
    public class EXT_AXIS_STATUS
    {
     public double pos = 0;        // Erweiterungsachsenposition
     public double vel = 0;        // Erweiterungsachsengeschwindigkeit
     public int errorCode = 0;     // Fehlercode der Erweiterungsachse
     public int ready = 0;         // Servo bereit
     public int inPos = 0;         // Servo in Position
     public int alarm = 0;         // Servoalarm
     public int flerr = 0;         // Folgefehler
     public int nlimit = 0;        // Negative Endlage erreicht
     public int pLimit = 0;        // Positive Endlage erreicht
     public int mdbsOffLine = 0;   // Antriebs-485-Bus offline
     public int mdbsTimeout = 0;   // Kommunikationstimeout zwischen Steuerkarte und Steuerschrank (485)
     public int homingStatus = 0;  // Referenzpunktfahrt-Status der Erweiterungsachse
    }

Sensortyp
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Sensortyp.
    */
    public class DeviceConfig
    {
      int company = 0;          // Hersteller
      int device = 0;           // Typ / Gerätenummer
      int softwareVersion = 0;  // Softwareversion
      int bus = 0;              // Montageposition (Bus)

      public DeviceConfig()
      {

      }

      public DeviceConfig(int company, int device, int softwareVersion, int bus)
      {
        this.company = company;
        this.device = device;
        this.softwareVersion = softwareVersion;
        this.bus = bus;
      }
    }

485-Erweiterungsachsen-Konfiguration
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief 485-Erweiterungsachsen-Konfiguration.
    */
    public class Axis485Param
    {
      int servoCompany;           // Hersteller des Servoantriebs, 1-DYNATEC
      int servoModel;             // Modell des Servoantriebs, 1-FD100-750C
      int servoSoftVersion;       // Softwareversion des Servoantriebs, 1-V1.0
      int servoResolution;        // Encoderauflösung
      double axisMechTransRatio;  // Mechanisches Übersetzungsverhältnis

      public Axis485Param(int company, int model, int softVersion, int resolution, double mechTransRatio)
      {
        servoCompany = company;
        servoModel = model;
        servoSoftVersion = softVersion;
        servoResolution = resolution;
        axisMechTransRatio = mechTransRatio;
      }

      public Axis485Param()
      {

      }
    }

Servocontroller-Status
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Servocontroller-Status.
    */
    public class ROBOT_AUX_STATE
    {
      public int servoId = 0;           // Servoantriebs-ID-Nummer
      public int servoErrCode = 0;      // Fehlercode des Servoantriebs
      public int servoState = 0;        // Status des Servoantriebs
      public double servoPos = 0;       // Aktuelle Position des Servos
      public float servoVel = 0;        // Aktuelle Geschwindigkeit des Servos
      public float servoTorque = 0;     // Aktuelles Drehmoment des Servos
    }

Schweißunterbrechungsstatus
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schweißunterbrechungsstatus.
    */
    public class WELDING_BREAKOFF_STATE
    {
      public int breakOffState = 0;  // Schweißunterbrechungsstatus
      public int weldArcState = 0;   // Lichtbogenunterbrechungsstatus beim Schweißen
    }

UDP-Erweiterungsachsen-Kommunikationsparameter
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief UDP-Erweiterungsachsen-Kommunikationsparameter.
    */
    public class UDPComParam
    {
      public String ip = "192.168.58.88";// IP-Adresse
      public int port = 2021;            // Portnummer
      public int period = 2;             // Kommunikationszyklus (ms, Standard 2, diesen Parameter nicht ändern)
      public int lossPkgTime = 50;       // Paketverlust-Erkennungszeit (ms)
      public int lossPkgNum = 2;         // Anzahl der Paketverluste
      public int disconnectTime = 100;   // Bestätigungsdauer für Kommunikationsunterbrechung
      public int reconnectEnable = 0;    // Automatische Wiederverbindung bei Kommunikationsunterbrechung aktivieren? 0-deaktivieren, 1-aktivieren
      public int reconnectPeriod = 100;  // Wiederverbindungsintervall (ms)
      public int reconnectNum = 3;       // Anzahl der Wiederverbindungsversuche
      public int selfConnect = 0;        // Automatische Verbindung nach Neustart? 0-keine Verbindung; 1-Verbindung herstellen
    }

Strukturtyp für Roboterstatus-Rückmeldung
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Roboterstatus-Rückmeldungsstrukturtyp
    */
    public class ROBOT_STATE_PKG {
        public int frame_head;                      // Rahmenkopf
        public int frame_cnt;                       // Rahmenzählung
        public int data_len;                        // Datenlänge
        public int program_state;                   // Programmstatus - 1-gestoppt; 2-läuft; 3-pausiert
        public int robot_state;                     // Roboterbewegungsstatus - 1-gestoppt; 2-läuft; 3-pausiert; 4-ziehen
        public int main_code;                       // Hauptfehlercode
        public int sub_code;                        // Unterfehlercode
        public int robot_mode;                      // Robotermodus - 1-Handmodus; 0-Automatikmodus
        public double[] jt_cur_pos = new double[6]; // Aktuelle Gelenkpositionen von 6 Achsen, Einheit deg
        public double[] tl_cur_pos = new double[6]; // Aktuelle Werkzeugposition - [x,y,z,rx,ry,rz]
        public double[] flange_cur_pos = new double[6]; // Aktuelle Endflanschposition - [x,y,z,rx,ry,rz]
        public double[] actual_qd = new double[6];  // Aktuelle Geschwindigkeiten von 6 Gelenken, Einheit deg/s
        public double[] actual_qdd = new double[6]; // Aktuelle Beschleunigungen von 6 Gelenken, Einheit deg/s^2
        public double[] target_TCP_CmpSpeed = new double[2]; // TCP zusammengesetzte Befehlgeschwindigkeit - [Position mm/s, Orientierung deg/s]
        public double[] target_TCP_Speed = new double[6]; // TCP Befehlgeschwindigkeit - [vx,vy,vz,wx,wy,wz]
        public double[] actual_TCP_CmpSpeed = new double[2]; // TCP zusammengesetzte tatsächliche Geschwindigkeit - [Position mm/s, Orientierung deg/s]
        public double[] actual_TCP_Speed = new double[6]; // TCP tatsächliche Geschwindigkeit - [vx,vy,vz,wx,wy,wz]
        public double[] jt_cur_tor = new double[6]; // Aktuelles Gelenkmoment
        public int tool;                            // Werkzeug-ID
        public int user;                            // Werkstück-ID
        public int cl_dgt_output_h;                 // Digitaler Ausgang des Schaltschranks High-Byte
        public int cl_dgt_output_l;                 // Digitaler Ausgang des Schaltschranks Low-Byte
        public int tl_dgt_output_l;                 // Digitaler Werkzeugausgang Low-Byte
        public int cl_dgt_input_h;                  // Digitaler Eingang des Schaltschranks High-Byte
        public int cl_dgt_input_l;                  // Digitaler Eingang des Schaltschranks Low-Byte
        public int tl_dgt_input_l;                  // Digitaler Werkzeugeingang Low-Byte
        public int[] cl_analog_input = new int[2];  // Analoger Eingang des Schaltschranks
        public int tl_anglog_input;                 // Analoger Werkzeugeingang
        public double[] ft_sensor_raw_data = new double[6]; // Rohdaten des Kraftsensors
        public double[] ft_sensor_data = new double[6]; // Daten des Kraftsensors
        public int ft_sensor_active;                // Aktivierungsstatus des Kraftsensors
        public int EmergencyStop;                   // Not-Halt-Status
        public int motion_done;                     // Bewegung abgeschlossen
        public int gripper_motiondone;              // Greifer-Bewegungsabschluss-Signal, 0-nicht abgeschlossen, 1-abgeschlossen (kein Objekt erkannt), 2-Bewegung abgeschlossen (Objekt erkannt)
        public int mc_queue_len;                    // Bewegungswarteschlangenlänge
        public int collisionState;                  // Kollisionsstatus
        public int trajectory_pnum;                 // Bahnpunkt-Sequenznummer
        public int safety_stop0_state;              // Sicherheitsstopp 0 Status
        public int safety_stop1_state;              // Sicherheitsstopp 1 Status
        public int gripper_fault_id;                // Greiferfehler-ID
        public int gripper_fault;                   // Greiferfehler 0-kein Fehler 1-485-Timeout 2-Befehlsfehler 3-Werkstückabfall Sonstiges-Greifer-Fehlercode
        public int gripper_active;                  // Greiferaktivierung
        public int gripper_position;                // Greiferposition
        public int gripper_speed;                   // Greifergeschwindigkeit
        public int gripper_current;                 // Greiferstrom
        public int gripper_temp;                    // Greifertemperatur
        public int gripper_voltage;                 // Greiferspannung
        public AuxState aux_state = new AuxState(); // Interner Hilfsachsenstatus
        public EXT_AXIS_STATUS[] extAxisStatus = new EXT_AXIS_STATUS[4]; // Erweiterungsachsenstatus-Array
        public short[] extDIState = new short[8];   // Erweiterte E/A
        public short[] extDOState = new short[8];   // Erweiterte E/A
        public short[] extAIState = new short[4];   // Erweiterte E/A
        public short[] extAOState = new short[4];   // Erweiterte E/A
        public int rbtEnableState;                  // Roboter-Aktivierungsstatus
        public double[] jointDriverTorque = new double[6]; // Gelenktreibermoment
        public double[] jointDriverTemperature = new double[6]; // Gelenktreibertemperatur
        public ROBOT_TIME robotTime = new ROBOT_TIME(); // Roboterzeitobjekt
        public int softwareUpgradeState;            // Software-Upgrade-Status
        public int endLuaErrCode;                   // End-Lua-Fehlercode
        public int[] cl_analog_output = new int[2]; // Analoger Ausgang des Schaltschranks
        public int tl_analog_output;                // Analoger Werkzeugausgang
        public float gripperRotNum;                 // Drehzahl des rotierenden Greifers
        public int gripperRotSpeed;                 // Geschwindigkeit des rotierenden Greifers
        public int gripperRotTorque;                // Drehmoment des rotierenden Greifers
        public WELDING_BREAKOFF_STATE weldingBreakOffState = new WELDING_BREAKOFF_STATE(); // Schweißunterbrechungsstatus
        public double[] jt_tgt_tor = new double[6]; // Soll-Gelenkmoment
        public int smartToolState;                  // Smart-Tool-Status
        public float wideVoltageCtrlBoxTemp;        // Weitspannungs-Steuerkastentemperatur
        public int wideVoltageCtrlBoxFanCurrent;    // Weitspannungs-Steuerkasten-Lüfterstrom
        public double[] toolCoord = new double[6];  // Werkzeugkoordinatensystem
        public double[] wobjCoord = new double[6];  // Werkstückkoordinatensystem
        public double[] extoolCoord = new double[6]; // Externes Werkzeugkoordinatensystem
        public double[] exAxisCoord = new double[6]; // Erweiterungsachsenkoordinatensystem
        public double load;                         // Last
        public double[] loadCog = new double[3];    // Lastschwerpunkt
        public double[] lastServoTarget = new double[6]; // Letzte Servo-J-Sollposition
        public int servoJCmdNum;                    // Servo-J-Befehlszähler
        public double[] targetJointPos = new double[6]; // Soll-Gelenkposition
        public double[] targetJointVel = new double[6]; // Soll-Gelenkgeschwindigkeit
        public double[] targetJointAcc = new double[6]; // Soll-Gelenkbeschleunigung
        public double[] targetJointCurrent = new double[6]; // Soll-Gelenkstrom
        public double[] actualJointCurrent = new double[6]; // Tatsächlicher Gelenkstrom
        public double[] actualTCPForce = new double[6]; // Tatsächliche TCP-Kraft
        public double[] targetTCPPos = new double[6]; // Soll-TCP-Position
        public int[] collisionLevel = new int[6];   // Kollisionsstufe
        public double speedScaleManual;              // Manueller Geschwindigkeitsmaßstab
        public double speedScaleAuto;                // Automatischer Geschwindigkeitsmaßstab
        public int luaLineNum;                       // Lua-Zeilennummer
        public int abnomalStop;                      // Abnormaler Stopp
        public String currentLuaFileName;            // Aktueller Lua-Dateiname
        public int programTotalLine;                 // Programmgesamtzeilen
        public int[] safetyBoxSingal = new int[6];   // Sicherheitskastensignal
        public double weldVoltage;                   // Schweißspannung
        public double weldCurrent;                   // Schweißstrom
        public double weldTrackVel;                  // Schweißnahtverfolgungsgeschwindigkeit
        public int tpdException;                     // TPD-Ausnahme
        public int alarmRebootRobot;                 // Alarm-Roboter-Neustart
        public int modbusMasterConnect;              // Modbus-Master-Verbindung
        public int modbusSlaveConnect;               // Modbus-Slave-Verbindung
        public int btnBoxStopSignal;                 // Tastenfeld-Stoppsignal
        public int dragAlarm;                        // Ziehalarm
        public int safetyDoorAlarm;                  // Sicherheitstüralarm
        public int safetyPlaneAlarm;                 // Sicherheitsebenenalarm
        public int motonAlarm;                       // Bewegungsalarm
        public int interfaceAlarm;                   // Interferenzalarm
        public int udpCmdState;                      // UDP-Befehlsstatus
        public int weldReadyState;                   // Schweißbereitschaftsstatus
        public int alarmCheckEmergStopBtn;           // Alarmprüfung Not-Halt-Taste
        public int tsTmCmdComError;                  // Befehlskommunikationsfehler
        public int tsTmStateComError;                // Statuskommunikationsfehler
        public int ctrlBoxError;                     // Steuerkastenfehler
        public int safetyDataState;                  // Sicherheitsdatenstatus
        public int forceSensorErrState;              // Kraftsensorfehlerstatus
        public int[] ctrlOpenLuaErrCode = new int[4]; // Steuerungs-Open-Lua-Fehlercode
        public int strangePosFlag;                   // Singuläre Positionskennzeichnung
        public int alarm;                            // Alarm
        public int driverAlarm;                      // Treiberalarm
        public int aliveSlaveNumError;               // Fehler bei Anzahl aktiver Slaves
        public int[] slaveComError = new int[8];     // Slave-Kommunikationsfehler
        public int cmdPointError;                    // Befehlspunktfehler
        public int IOError;                          // IO-Fehler
        public int gripperError;                     // Greiferfehler
        public int fileError;                        // Dateifehler
        public int paraError;                        // Parameterfehler
        public int exaxisOutLimitError;              // Fehler bei Überschreitung der Weichgrenze der Erweiterungsachse
        public int[] driverComError = new int[6];    // Treiberkommunikationsfehler
        public int driverError;                      // Treiberfehler
        public int outSoftLimitError;                // Fehler bei Überschreitung der Weichgrenze
        public byte[] axleGenComData = new byte[130]; // Allgemeine Achskommunikationsdaten
        public int check_sum;                        // Prüfsumme
        public int socketConnTimeout;                // Socket-Verbindungszeitüberschreitung
        public int socketReadTimeout;                // Socket-Lesezeitüberschreitung
        public int tsWebStateComErr;                 // TS-Web-Zustandskommunikationsfehler
        public int exaxisCoordID;                  // Kennung des erweiterten Achskoordinatensystems
        public int programRunState;                  // LUA-Programmausführungsstatus 0-Programm läuft nicht; 1-Programm läuft (einschließlich Programm pausiert)
    }

Roboterstatus-Feedback-Konfigurationsergebnisklasse
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * Roboterstatus-Feedback-Konfigurationsergebnisklasse, enthält Statusliste und Periode
    */
    public static class StateConfigResult {
      public final List<RobotState> stateList;
      public final int period;
    }

Roboterstatus-Feedback-Konfigurationsaufzählungstyp
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * Roboterstatus-Aufzählungstyp
    * Wird für die Echtzeitstatus-Feedback-Konfiguration verwendet
    */
    enum class RobotState
    {
        ProgramState,           // Programmstatus, 1-gestoppt; 2-läuft; 3-pausiert
        RobotState,             // Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-Ziehen
        MainCode,               // Hauptfehlercode
        SubCode,                // Unterfehlercode
        RobotMode,              // Robotermodus, 1-Manualmodus; 0-Automatikmodus
        JointCurPos,            // Aktuelle Gelenkpositionen von 6 Achsen, Einheit deg
        ToolCurPos,             // Aktuelle Werkzeugposition: [0]Position entlang x-Achse(mm), [1]entlang y-Achse(mm), [2]entlang z-Achse(mm), [3]Rotation um festes X(deg), [4]um festes Y(deg), [5]um festes Z(deg)
        FlangeCurPos,           // Aktuelle Endflanschposition: [0]entlang x-Achse(mm), [1]entlang y-Achse(mm), [2]entlang z-Achse(mm), [3]Rotation um festes X(deg), [4]um festes Y(deg), [5]um festes Z(deg)
        ActualJointVel,         // Aktuelle 6 Gelenkgeschwindigkeiten, Einheit deg/s
        ActualJointAcc,         // Aktuelle 6 Gelenkbeschleunigungen, Einheit deg/s²
        TargetTCPCmpSpeed,      // TCP-Zusammengesetzte Befehlgeschwindigkeit: [0]Position(mm/s), [1]Orientierung(deg/s)
        TargetTCPSpeed,         // TCP-Befehlgeschwindigkeit: [0]entlang x-Achse(mm/s), [1]entlang y-Achse(mm/s), [2]entlang z-Achse(mm/s), [3]Winkelgeschwindigkeit um X(deg/s), [4]um Y(deg/s), [5]um Z(deg/s)
        ActualTCPCmpSpeed,      // TCP-Zusammengesetzte Istgeschwindigkeit: [0]Position(mm/s), [1]Orientierung(deg/s)
        ActualTCPSpeed,         // TCP-Istgeschwindigkeit: [0]entlang x-Achse(mm/s), [1]entlang y-Achse(mm/s), [2]entlang z-Achse(mm/s), [3]Winkelgeschwindigkeit um X(deg/s), [4]um Y(deg/s), [5]um Z(deg/s)
        ActualJointTorque,      // Aktuelle 6 Gelenkdrehmomente, Einheit N·m
        Tool,                   // Angewandte Werkzeugkoordinatensystemnummer
        User,                   // Angewandte Werkstückkoordinatensystemnummer
        ClDgtOutputH,           // Digitaler IO-Ausgang des Steuerschranks 15-8
        ClDgtOutputL,           // Digitaler IO-Ausgang des Steuerschranks 7-0
        TlDgtOutputL,           // Digitaler Werkzeug-IO-Ausgang 7-0, nur bit0-bit1 gültig
        ClDgtInputH,            // Digitaler IO-Eingang des Steuerschranks 15-8
        ClDgtInputL,            // Digitaler IO-Eingang des Steuerschranks 7-0
        TlDgtInputL,            // Digitaler Werkzeug-IO-Eingang 7-0, nur bit0-bit1 gültig
        ClAnalogInput,          // Analoger Eingang des Steuerschranks: [0]Kanal 0, [1]Kanal 1
        TlAnalogInput,          // Analoger Werkzeugeingang
        FtSensorRawData,        // Rohdaten des Kraft-Drehmoment-Sensors: [0]Kraft entlang x-Achse(N), [1]entlang y-Achse(N), [2]entlang z-Achse(N), [3]Drehmoment um x-Achse(Nm), [4]um y-Achse(Nm), [5]um z-Achse(Nm)
        FtSensorData,           // Daten des Kraft-Drehmoment-Sensors (verarbeitet): [0]Kraft entlang x-Achse(N), [1]entlang y-Achse(N), [2]entlang z-Achse(N), [3]Drehmoment um x-Achse(Nm), [4]um y-Achse(Nm), [5]um z-Achse(Nm)
        FtSensorActive,         // Aktivierungsstatus des Kraft-Drehmoment-Sensors, 0-Reset, 1-aktiv
        EmergencyStop,          // Not-Halt-Flag, 0-Not-Halt nicht gedrückt, 1-Not-Halt gedrückt
        MotionDone,             // Bewegungs-abgeschlossen-Signal, 1-abgeschlossen, 0-nicht abgeschlossen
        GripperMotiondone,      // Greiferbewegung-abgeschlossen-Signal, 1-abgeschlossen, 0-nicht abgeschlossen
        McQueueLen,             // Länge der Bewegungskommandowarteschlange
        CollisionState,         // Kollisionserkennung, 1-Kollision, 0-keine Kollision
        TrajectoryPnum,         // Trajektorienpunktnummer
        SafetyStop0State,       // Sicherheitsstoppsignal SI0
        SafetyStop1State,       // Sicherheitsstoppsignal SI1
        GripperFaultId,         // Fehlerhafte Greifernummer
        GripperFault,           // Greiferfehler
        GripperActive,          // Greiferaktivierungsstatus
        GripperPosition,        // Greiferposition
        GripperSpeed,           // Greifergeschwindigkeit
        GripperCurrent,         // Greiferstrom
        GripperTemp,            // Greifertemperatur
        GripperVoltage,         // Greiferspannung
        AuxState,               // 485 Erweiterter Achsenstatus
        ExtAxisStatus,          // UDP-Erweiterte Achsenstatus (4 Achsen)
        ExtDIState,             // Erweiterter DI-Eingang (8)
        ExtDOState,             // Erweiterter DO-Ausgang (8)
        ExtAIState,             // Erweiterter AI-Eingang (4)
        ExtAOState,             // Erweiterter AO-Ausgang (4)
        RbtEnableState,         // Roboter-Freigabestatus
        JointDriverTorque,      // Roboter-Gelenktreiber-Drehmoment (6 Gelenke)
        JointDriverTemperature, // Roboter-Gelenktreiber-Temperatur (6 Gelenke)
        RobotTime,              // Roboter-Systemzeit
        SoftwareUpgradeState,   // Roboter-Software-Upgrade-Status
        EndLuaErrCode,          // End-LUA-Ausführungsstatus
        ClAnalogOutput,         // Analoger Ausgang des Steuerschranks (2)
        TlAnalogOutput,         // Analoger Werkzeugausgang
        GripperRotNum,          // Aktuelle Rotationsumdrehungen des Drehgreifers
        GripperRotSpeed,        // Aktuelle Rotationsgeschwindigkeitsprozent des Drehgreifers
        GripperRotTorque,       // Aktuelles Rotationsdrehmomentprozent des Drehgreifers
        WeldingBreakOffState,   // Schweißunterbrechungsstatus
        TargetJointTorque,      // Gelenkbefehlsdrehmoment (6 Gelenke)
        SmartToolState,         // SmartTool-Griffknopfstatus
        WideVoltageCtrlBoxTemp, // Temperatur des Weitspannungs-Steuerschranks
        WideVoltageCtrlBoxFanCurrent, // Lüfterstrom des Weitspannungs-Steuerschranks (mA)
        ToolCoord,              // Aktuelle Werkzeugkoordinatenwerte: x,y,z,rx,ry,rz
        WobjCoord,              // Aktuelle Werkstückkoordinatenwerte: x,y,z,rx,ry,rz
        ExtoolCoord,            // Aktuelle externe Werkzeugkoordinatenwerte: x,y,z,rx,ry,rz
        ExAxisCoord,            // Aktuelle erweiterte Achsenkoordinatenwerte: x,y,z,rx,ry,rz
        Load,                   // Lastmasse
        LoadCog,                // Lastschwerpunkt: x,y,z
        LastServoTarget,        // Letzte ServoJ-Zielposition in Warteschlange (6 Gelenke)
        ServoJCmdNum,           // servoJ-Befehlszähler
        TargetJointPos,         // 6 Gelenkbefehlspositionen, Einheit °
        TargetJointVel,         // 6 Gelenkbefehlsgeschwindigkeiten, Einheit °/s
        TargetJointAcc,         // 6 Gelenkbefehlsbeschleunigungen, Einheit °/s²
        TargetJointCurrent,     // 6 Gelenkbefehlsströme, Einheit A
        ActualJointCurrent,     // 6 Gelenkistströme, Einheit A
        ActualTCPForce,         // Roboter-Enddrehmoment: x,y,z,rx,ry,rz, Einheit Nm
        TargetTCPPos,           // Roboter-TCP-Befehlsposition: x,y,z,rx,ry,rz, Einheit mm
        CollisionLevel,         // Roboter-Kollisionsstufe (6)
        SpeedScaleManual,       // Globale Geschwindigkeitsprozent im Handmodus
        SpeedScaleAuto,         // Globale Geschwindigkeitsprozent im Automatikmodus
        LuaLineNum,             // Aktuelle laufende Zeilennummer des Lua-Programms
        AbnomalStop,            // 0-keine Anomalie; 1-Anomalie vorhanden
        CurrentLuaFileName,     // Aktueller laufender Lua-Programmname
        ProgramTotalLine,       // Lua-Programm-Gesamtzeilen
        SafetyBoxSingal,        // Roboter-Tastenfeld-Tastenstatus (6)
        WeldVoltage,            // Schweißspannung V
        WeldCurrent,            // Schweißstrom
        WeldTrackVel,           // Nahtverfolgungsgeschwindigkeit mm/s
        TpdException,           // TPD-Trajektorien-Ladeanzahl überschritten, 0-nicht überschritten, 1-überschritten
        AlarmRebootRobot,       // Warnung: 1-Stromzyklus nach Loslassen des Not-Halts erforderlich, 2-Gelenkkommunikationsanomalie erfordert Stromzyklus
        ModbusMasterConnect,    // bit0-7 entsprechen ModbusTCP-Master 0-7 Verbindungsstatus, 0-nicht verbunden, 1-verbunden
        ModbusSlaveConnect,     // ModbusTCP-Slave-Verbindungsstatus, 0-nicht verbunden, 1-verbunden
        BtnBoxStopSignal,       // Not-Halt-Signal des Tastenfelds, 0-Not-Halt losgelassen, 1-Not-Halt gedrückt
        DragAlarm,              // Ziehwarnung: 0-kein Alarm, 1-Alarm, 2-Positionsrückmeldungsanomalie kein Wechsel
        SafetyDoorAlarm,        // Sicherheitstürwarnung: 0-geschlossen, 1-geöffnet
        SafetyPlaneAlarm,       // Sicherheitswandwarnung: 0-nicht betreten, 1-betreten
        MotonAlarm,             // Bewegungswarnung
        InterfaceAlarm,         // Warnung beim Eintritt in Interferenzzone
        UdpCmdState,            // UDP-Kommunikationsverbindungsstatus von Port 20007
        WeldReadyState,         // Schweißgerät-Bereitschaftsstatus
        AlarmCheckEmergStopBtn, // 0-normal; 1-Kommunikationsanomalie, Not-Halt-Knopf prüfen
        TsTmCmdComError,        // 0-normal; 1-Drehmomentbefehlskommunikationsfehler
        TsTmStateComError,      // 0-normal; 1-Drehmomentstatuskommunikationsfehler
        CtrlBoxError,           // Steuerschrankfehler
        SafetyDataState,        // Sicherheitsdatenstatus, 0-normal, 1-anomal
        ForceSensorErrState,    // Kraftsensor-Verbindungszeitüberschreitung, bit0-bit1 entsprechen ID1-ID2
        CtrlOpenLuaErrCode,     // 4 Controller-Peripherieprotokoll-Fehlercodes (500-Fehlercode)
        StrangePosFlag,         // Singuläre-Pose-Flag: 0-normal, 1-singuläre Pose
        Alarm,                  // Alarm
        DriverAlarm,            // Treiber-Alarmachsenummer
        AliveSlaveNumError,     // Aktive-Slave-Anzahlfehler: 0-normal, 1-Anzahlfehler
        SlaveComError,          // Slave-Fehler: 0-normal, 1-offline, 2-Zustandsinkonsistenz, 3-nicht konfiguriert, 4-Konfigurationsfehler, 5-Initialisierungsfehler, 6-Mailbox-Kommunikationsinitialisierungsfehler
        CmdPointError,          // Befehlspunktfehler
        IOError,                // IO-Fehler
        GripperError,           // Greiferfehler
        FileError,              // Dateifehler
        ParaError,              // Parameterfehler
        ExaxisOutLimitError,    // Fehler wegen Überschreitung der weichen Grenze der externen Achse
        DriverComError,         // Treiberkommunikationsfehler (6 Achsen)
        DriverError,            // Achsnummer des Treiberkommunikationsfehlers
        OutSoftLimitError,      // Fehler wegen Überschreitung der weichen Grenze
        AxleGenComData,         // Roboter-End-Durchsatz-Feedbackdaten
        SocketConnTimeout,      // Socket-Verbindungszeitüberschreitung, bit0-bit4 entsprechen socketID 1-4
        SocketReadTimeout,      // Socket-Lesezeitüberschreitung, bit0-bit4 entsprechen socketID 1-4
        TsWebStateComErr,       // web-Drehmomentkommunikationsfehler: 0-normal, 1-Fehler
        ExaxisCoordID           // Kennung des erweiterten Achskoordinatensystems
        programRunState         //LUA-Programmausführungsstatus 0-Programm läuft nicht; 1-Programm läuft (einschließlich Programm pausiert)
    };