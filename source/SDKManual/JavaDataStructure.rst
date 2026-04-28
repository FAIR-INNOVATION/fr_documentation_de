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
        public int gripper_motiondone;              // Greiferbewegung abgeschlossen
        public int mc_queue_len;                    // Bewegungswarteschlangenlänge
        public int collisionState;                  // Kollisionsstatus
        public int trajectory_pnum;                 // Bahnpunkt-Sequenznummer
        public int safety_stop0_state;              // Sicherheitsstopp 0 Status
        public int safety_stop1_state;              // Sicherheitsstopp 1 Status
        public int gripper_fault_id;                // Greiferfehler-ID
        public int gripper_fault;                   // Greiferfehler
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
    public enum RobotState {
        ProgramState,
        RobotState,
        MainCode,
        SubCode,
        RobotMode,
        JointCurPos,
        ToolCurPos,
        FlangeCurPos,
        ActualJointVel,
        ActualJointAcc,
        TargetTCPCmpSpeed,
        TargetTCPSpeed,
        ActualTCPCmpSpeed,
        ActualTCPSpeed,
        ActualJointTorque,
        Tool,
        User,
        ClDgtOutputH,
        ClDgtOutputL,
        TlDgtOutputL,
        ClDgtInputH,
        ClDgtInputL,
        TlDgtInputL,
        ClAnalogInput,
        TlAnglogInput,
        FtSensorRawData,
        FtSensorData,
        FtSensorActive,
        EmergencyStop,
        MotionDone,
        GripperMotiondone,
        McQueueLen,
        CollisionState,
        TrajectoryPnum,
        SafetyStop0State,
        SafetyStop1State,
        GripperFaultId,
        GripperFault,
        GripperActive,
        GripperPosition,
        GripperSpeed,
        GripperCurrent,
        GripperTemp,
        GripperVoltage,
        AuxState,
        ExtAxisStatus,
        ExtDIState,
        ExtDOState,
        ExtAIState,
        ExtAOState,
        RbtEnableState,
        JointDriverTorque,
        JointDriverTemperature,
        RobotTime,
        SoftwareUpgradeState,
        EndLuaErrCode,
        ClAnalogOutput,
        TlAnalogOutput,
        GripperRotNum,
        GripperRotSpeed,
        GripperRotTorque,
        WeldingBreakOffState,
        TargetJointTorque,
        SmartToolState,
        WideVoltageCtrlBoxTemp,
        WideVoltageCtrlBoxFanCurrent,
        ToolCoord,
        WobjCoord,
        ExtoolCoord,
        ExAxisCoord,
        Load,
        LoadCog,
        LastServoTarget,
        ServoJCmdNum,
        TargetJointPos,
        TargetJointVel,
        TargetJointAcc,
        TargetJointCurrent,
        ActualJointCurrent,
        ActualTCPForce,
        TargetTCPPos,
        CollisionLevel,
        SpeedScaleManual,
        SpeedScaleAuto,
        LuaLineNum,
        AbnomalStop,
        CurrentLuaFileName,
        ProgramTotalLine,
        SafetyBoxSingal,
        WeldVoltage,
        WeldCurrent,
        WeldTrackVel,
        TpdException,
        AlarmRebootRobot,
        ModbusMasterConnect,
        ModbusSlaveConnect,
        BtnBoxStopSignal,
        DragAlarm,
        SafetyDoorAlarm,
        SafetyPlaneAlarm,
        MotonAlarm,
        InterfaceAlarm,
        UdpCmdState,
        WeldReadyState,
        AlarmCheckEmergStopBtn,
        TsTmCmdComError,
        TsTmStateComError,
        SocketConnTimeout,
        SocketReadTimeout,
        TsWebStateComErr,
        CtrlBoxError,
        SafetyDataState,
        ForceSensorErrState,
        CtrlOpenLuaErrCode,
        StrangePosFlag,
        Alarm,
        DriverAlarm,
        AliveSlaveNumError,
        SlaveComError,
        CmdPointError,
        IOError,
        GripperError,
        FileError,
        ParaError,
        ExaxisOutLimitError,
        DriverComError,
        DriverError,
        OutSoftLimitError,
        AxleGenComData;
    }