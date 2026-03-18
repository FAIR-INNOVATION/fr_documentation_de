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
    * @brief Strukturtyp für die Roboterstatus-Rückmeldung.
    */
    public class ROBOT_STATE_PKG
    {
      public short frame_head = 0;            // Frame-Header 0x5A5A
      public byte frame_cnt = 0;              // Frame-Zähler
      public short data_len = 0;              // Datenlänge
      public int program_state = 0;           // Programmausführungsstatus, 1-gestoppt; 2-läuft; 3-pausiert
      public int robot_state = 0;             // Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-Ziehemodus (Drag)
      public int main_code = 0;                // Hauptfehlercode
      public int sub_code = 0;                 // Unterfehlercode
      public int robot_mode = 0;               // Robotermodus, 0-Automatikmodus; 1-Handmodus
      public double[] jt_cur_pos  = new double[6];                  // Aktuelle Gelenkpositionen
      public double[] tl_cur_pos = new double[6];                  // Aktuelle Werkzeugpose
      public double[] flange_cur_pos = new double[6];              // Aktuelle Pose des Endflansches
      public double[] actual_qd = new double[6];                   // Aktuelle Gelenkgeschwindigkeiten des Roboters
      public double[] actual_qdd = new double[6];                  // Aktuelle Gelenkbeschleunigungen des Roboters
      public double[] target_TCP_CmpSpeed = new double[2];         // Resultierende TCP-Sollgeschwindigkeit des Roboters
      public double[] target_TCP_Speed = new double[6];            // TCP-Sollgeschwindigkeit des Roboters (Komponenten)
      public double[] actual_TCP_CmpSpeed = new double[2];         // Resultierende TCP-Istgeschwindigkeit des Roboters
      public double[] actual_TCP_Speed = new double[6];            // TCP-Istgeschwindigkeit des Roboters (Komponenten)
      public double[] jt_cur_tor = new double[6];                  // Aktuelle Drehmomente
      public int tool = 0;                        // Werkzeugnummer
      public int user = 0;                        // Werkstücknummer
      public int cl_dgt_output_h = 0;            // Digitalausgänge 15-8
      public int cl_dgt_output_l = 0;            // Digitalausgänge 7-0
      public int tl_dgt_output_l = 0;            // Werkzeug-Digitalausgänge 7-0 (nur bit0-bit1 gültig)
      public int cl_dgt_input_h = 0;              // Digitaleingänge 15-8
      public int cl_dgt_input_l = 0;              // Digitaleingänge 7-0
      public int tl_dgt_input_l = 0;              // Werkzeug-Digitaleingänge 7-0 (nur bit0-bit1 gültig)
      public short[] cl_analog_input = new short[2];          // Analogeingänge des Steuerschranks
      public short tl_anglog_input = 0;                       // Analogeingang des Werkzeugs
      public double[] ft_sensor_raw_data = new double[6];     // Rohdaten des Kraft-/Drehmomentsensors
      public double[] ft_sensor_data = new double[6];         // Verarbeitete Daten des Kraft-/Drehmomentsensors (im Referenzkoordinatensystem)
      public int ft_sensor_active = 0;           // Aktivierungsstatus des Kraft-/Drehmomentsensors, 0-Reset, 1-aktiviert
      public int EmergencyStop = 0;              // Not-Halt-Flag
      public int motion_done = 0;                 // In-Position-Signal
      public int gripper_motiondone = 0;         // Greifer-Bewegungsabschluss-Signal
      public int mc_queue_len = 0;                // Länge der Bewegungswarteschlange
      public int collisionState = 0;             // Kollisionserkennung, 1-Kollision; 0-keine Kollision
      public int trajectory_pnum = 0;             // Trajektorienpunktnummer
      public int safety_stop0_state = 0;          /* Sicherheitsstopp-Signal SI0 */
      public int safety_stop1_state = 0;          /* Sicherheitsstopp-Signal SI1 */
      public int gripper_fault_id = 0;             /* Fehlerhafte Greifernummer */
      public short gripper_fault = 0;              /* Greiferfehler */
      public short gripper_active = 0;             /* Greifer-Aktivierungsstatus */
      public int gripper_position = 0;             /* Greiferposition */
      public int gripper_speed = 0;                /* Greifergeschwindigkeit */
      public int gripper_current = 0;              /* Greiferstrom */
      public int gripper_tmp = 0;                   /* Greifertemperatur */
      public int gripper_voltage = 0;               /* Greiferspannung */
      public ROBOT_AUX_STATE auxState = new ROBOT_AUX_STATE(); /* Status der 485-Erweiterungsachse */
      public EXT_AXIS_STATUS extAxisStatus0 = new EXT_AXIS_STATUS();
      public EXT_AXIS_STATUS extAxisStatus1 = new EXT_AXIS_STATUS();
      public EXT_AXIS_STATUS extAxisStatus2 = new EXT_AXIS_STATUS();
      public EXT_AXIS_STATUS extAxisStatus3 = new EXT_AXIS_STATUS();
      public short[] extDIState = new short[8];        // Erweiterte DI-Eingänge
      public short[] extDOState = new short[8];        // Erweiterte DO-Ausgänge
      public short[] extAIState = new short[4];        // Erweiterte AI-Eingänge
      public short[] extAOState = new short[4];        // Erweiterte AO-Ausgänge
      public int rbtEnableState = 0;                   // Roboter-Aktivierungsstatus (Enable)
      public double[] jointDriverTorque  = new double[6];       // Aktuelles Drehmoment der Gelenkantriebe
      public double[] jointDriverTemperature = new double[6];  // Aktuelle Temperatur der Gelenkantriebe
      public ROBOT_TIME robotTime = new ROBOT_TIME();
      public int softwareUpgradeState = 0;   // Roboter-Software-Upgrade-Status 0-im Leerlauf oder Upgrade-Paket wird hochgeladen; 1~100: Upgrade-Fortschritt in Prozent; -1: Upgrade fehlgeschlagen; -2: Prüfsummenfehler; -3: Versionsprüfung fehlgeschlagen; -4: Entpacken fehlgeschlagen; -5: Benutzerkonfigurations-Upgrade fehlgeschlagen; -6: Peripherie-Konfigurations-Upgrade fehlgeschlagen; -7: Erweiterungsachsen-Konfigurations-Upgrade fehlgeschlagen; -8: Roboter-Konfigurations-Upgrade fehlgeschlagen; -9: DH-Parameter-Konfigurations-Upgrade fehlgeschlagen
      public int endLuaErrCode;                         // LUA-Ausführungsstatus am Endeffektor

      public int[] cl_analog_output = new int[2];  // Analogausgänge des Steuerschranks
      public int tl_analog_output;                  // Analogausgang des Werkzeugs
      public float gripperRotNum;                   // Aktuelle Umdrehungszahl des Drehgreifers
      public int gripperRotSpeed;                    // Aktueller Rotationsgeschwindigkeitsprozentsatz des Drehgreifers
      public int gripperRotTorque;	                 // Aktueller Rotationskraftprozentsatz des Drehgreifers

      public  WELDING_BREAKOFF_STATE weldingBreakOffstate = new WELDING_BREAKOFF_STATE(); // Schweißunterbrechungsstatus

      public double[] jt_tgt_tor = new double[6];    // Gelenk-Solldrehmomente
      public int smartToolState;                      // SmartTool-Griff-Tastenstatus

      public float wideVoltageCtrlBoxTemp;            // Temperatur des Weitbereichs-Steuerschranks
      public int wideVoltageCtrlBoxFanVel;            // Lüfterstrom des Weitbereichs-Steuerschranks (mA)

      public double[] toolCoord = new double[6];           // Werkzeugkoordinatensystem
      public double[] wobjCoord = new double[6];		   // Werkstückkoordinatensystem
      public double[] extoolCoord = new double[6];		   // Externes Werkzeugkoordinatensystem
      public double[] exAxisCoord = new double[6];		   // Erweiterungsachsen-Koordinatensystem
      public double load;                                    // Nutzlastmasse
      public double[] loadCog = new double[3];              // Nutzlastschwerpunkt

      public double[] lastServoTarget = new double[6];      // Letzte servoJ-Zielposition in der Warteschlange
      public int servoJCmdNum;                               // servoJ-Befehlszähler

      public short check_sum = 0;                             /* Summenprüfung */

      public ROBOT_STATE_PKG()
      {

      }
    }
