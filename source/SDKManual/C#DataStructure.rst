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

Strukturtyp für Roboterstatus-Rückmeldung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: csharp
    :linenos:

    /**
    * @brief Strukturtyp für die Roboterstatus-Rückmeldung.
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct ROBOT_STATE_PKG
    {
        public UInt16 frame_head;           // Frame-Header 0x5A5A
        public byte frame_cnt;              // Frame-Zähler
        public UInt16 data_len;             // Datenlänge  5
        public byte program_state;          // Programmausführungsstatus, 1-gestoppt; 2-läuft; 3-pausiert
        public byte robot_state;            // Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-Ziehemodus (Drag) 7
        public int main_code;                // Hauptfehlercode
        public int sub_code;                 // Unterfehlercode
        public byte robot_mode;              // Robotermodus, 0-Automatikmodus; 1-Handmodus 16

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_pos;                             // Aktuelle Gelenkpositionen
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] tl_cur_pos;                             // Aktuelle Werkzeugpose
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] flange_cur_pos;                         // Aktuelle Pose des Endflansches
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qd;                              // Aktuelle Gelenkgeschwindigkeiten des Roboters
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qdd;                             // Aktuelle Gelenkbeschleunigungen des Roboters 16 + 8 * 6 * 5 = 256
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] target_TCP_CmpSpeed;                    // Resultierende TCP-Sollgeschwindigkeit des Roboters
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] target_TCP_Speed;                       // TCP-Sollgeschwindigkeit des Roboters (Komponenten)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] actual_TCP_CmpSpeed;                    // Resultierende TCP-Istgeschwindigkeit des Roboters
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_TCP_Speed;                       // TCP-Istgeschwindigkeit des Roboters (Komponenten)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_tor;                             // Aktuelle Drehmomente
        public int tool;                        // Werkzeugnummer
        public int user;                        // Werkstücknummer
        public byte cl_dgt_output_h;            // Digitalausgänge 15-8
        public byte cl_dgt_output_l;            // Digitalausgänge 7-0
        public byte tl_dgt_output_l;            // Werkzeug-Digitalausgänge 7-0 (nur bit0-bit1 gültig)
        public byte cl_dgt_input_h;             // Digitaleingänge 15-8
        public byte cl_dgt_input_l;             // Digitaleingänge 7-0
        public byte tl_dgt_input_l;             // Werkzeug-Digitaleingänge 7-0 (nur bit0-bit1 gültig)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public UInt16[] cl_analog_input;        // Analogeingänge des Steuerschranks
        public UInt16 tl_anglog_input;          // Analogeingang des Werkzeugs
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_raw_data;     // Rohdaten des Kraft-/Drehmomentsensors
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_data;         // Verarbeitete Daten des Kraft-/Drehmomentsensors
        public byte ft_sensor_active;           // Aktivierungsstatus des Kraft-/Drehmomentsensors, 0-Reset, 1-aktiviert
        public byte EmergencyStop;              // Not-Halt-Flag
        public int motion_done;                 // In-Position-Signal
        public byte gripper_motiondone;         // Greifer-Bewegungsabschluss-Signal
        public int mc_queue_len;                // Länge der Bewegungswarteschlange
        public byte collisionState;             // Kollisionserkennung, 1-Kollision; 0-keine Kollision
        public int trajectory_pnum;             // Bahnpunktnummer
        public byte safety_stop0_state;         /* Sicherheitsstopp-Signal SI0 */
        public byte safety_stop1_state;         /* Sicherheitsstopp-Signal SI1 */
        public byte gripper_fault_id;           /* Fehlerhafte Greifernummer */
        public UInt16 gripper_fault;            /* Greiferfehler */
        public UInt16 gripper_active;           /* Greifer-Aktivierungsstatus */
        public byte gripper_position;            /* Greiferposition */
        public byte gripper_speed;               /* Greifergeschwindigkeit */
        public byte gripper_current;             /* Greiferstrom */
        public int gripper_tmp;                   /* Greifertemperatur */
        public int gripper_voltage;               /* Greiferspannung */
        public ROBOT_AUX_STATE auxState;          /* Status der 485-Erweiterungsachse */
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public EXT_AXIS_STATUS[] extAxisStatus;   /* Status der UDP-Erweiterungsachsen */
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDIState;                // Erweiterte DI-Eingänge
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDOState;                // Erweiterte DO-Ausgänge
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAIState;                // Erweiterte AI-Eingänge
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAOState;                // Erweiterte AO-Ausgänge
        public int rbtEnableState;                  // Roboter-Aktivierungsstatus (Enable)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTorque;          // Drehmoment der Gelenkantriebe
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTemperature;     // Temperatur der Gelenkantriebe
        public ROBOT_TIME robotTime;                 // Roboter-Systemzeit
        public int softwareUpgradeState;             // Software-Upgrade-Status 0-im Leerlauf oder Upgrade-Paket wird hochgeladen; 1~100: Upgrade-Fortschritt in Prozent; -1: Software-Upgrade fehlgeschlagen; -2: Prüfsummenfehler; -3: Versionsprüfung fehlgeschlagen; -4: Entpacken fehlgeschlagen; -5: Benutzerkonfigurations-Upgrade fehlgeschlagen; -6: Peripherie-Konfigurations-Upgrade fehlgeschlagen; -7: Erweiterungsachsen-Konfigurations-Upgrade fehlgeschlagen; -8: Roboter-Konfigurations-Upgrade fehlgeschlagen; -9: DH-Parameter-Konfigurations-Upgrade fehlgeschlagen
        public UInt16 endLuaErrCode;                 // LUA-Ausführungsstatus am Endeffektor
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public UInt16[] cl_analog_output;            // Analogausgänge des Steuerschranks
        public UInt16 tl_analog_output;               // Analogausgang des Werkzeugs
        public float gripperRotNum;                   // Aktuelle Umdrehungszahl des Drehgreifers
        public byte gripperRotSpeed;                   // Aktueller Rotationsgeschwindigkeitsprozentsatz des Drehgreifers
        public byte gripperRotTorque;                  // Aktueller Rotationskraftprozentsatz des Drehgreifers
        public WELDING_BREAKOFF_STATE weldingBreakOffState;// Schweißunterbrechungsstatus

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_tgt_tor;                     // Gelenk-Solldrehmomente
        public int smartToolState;                       // SmartTool-Griff-Tastenstatus
        public float wideVoltageCtrlBoxTemp;             // Temperatur des Weitbereichs-Steuerschranks
        public UInt16 wideVoltageCtrlBoxFanVel;          // Lüfterstrom des Weitbereichs-Steuerschranks (mA)

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] toolCoord;                       // Werkzeugkoordinatensystem
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] wobjCoord;                       // Werkstückkoordinatensystem
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] extoolCoord;                     // Externes Werkzeugkoordinatensystem
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] exAxisCoord;                     // Erweiterungsachsen-Koordinatensystem
        public double load;                               // Nutzlastmasse

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 3)]
        public double[] loadCog;                          // Nutzlastschwerpunkt
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] lastServoTarget;                  // Letzte servoJ-Zielposition in der Warteschlange

        public int servoJCmdNum;                           // servoJ-Befehlszähler
        public UInt16 check_sum;                           /* Summenprüfung */
    }