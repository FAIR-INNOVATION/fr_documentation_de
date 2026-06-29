Datenstrukturbeschreibung
=========================

.. toctree::
    :maxdepth: 5

Roboterstatus-Rückmeldungsstrukturtyp
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:
    
    class ROBOT_AUX_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("servoId", c_uint8),         # Servotreiber-ID-Nummer
            ("servoErrCode", c_int),     # Servotreiber-Fehlercode
            ("servoState", c_int),       # Servotreiber-Status
            ("servoPos", c_double),      # Servo aktuelle Position
            ("servoVel", c_float),       # Servo aktuelle Geschwindigkeit
            ("servoTorque", c_float),    # Servo aktuelles Drehmoment
        ]

    class EXT_AXIS_STATUS(Structure):
        _pack_ = 1
        _fields_ = [
            ("pos", c_double),        # Erweiterungsachsenposition
            ("vel", c_double),        # Erweiterungsachsengeschwindigkeit
            ("errorCode", c_int),     # Erweiterungsachsen-Fehlercode
            ("ready", c_uint8),        # Servo bereit
            ("inPos", c_uint8),        # Servo in Position
            ("alarm", c_uint8),        # Servo-Alarm
            ("flerr", c_uint8),        # Folgefehler
            ("nlimit", c_uint8),       # Negativer Grenzwert erreicht
            ("pLimit", c_uint8),       # Positiver Grenzwert erreicht
            ("mdbsOffLine", c_uint8),  # Treiber-485-Bus offline
            ("mdbsTimeout", c_uint8),  # Steuerkarte zu Steuerkasten 485-Kommunikationszeitüberschreitung
            ("homingStatus", c_uint8), # Erweiterungsachsen-Referenzierstatus
        ]

    class WELDING_BREAKOFF_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("breakOffState", c_uint8),        # Schweißunterbrechungsstatus
            ("weldArcState", c_uint8),        # Schweißlichtbogen-Unterbrechungsstatus
        ]

    # ==================== Vollständige Roboterstatusstruktur ====================
    class RobotStatePkg(Structure):
        """
        Roboterstatus-Rückmeldungsdatenpaket
        """
        _pack_ = 1
        _fields_ = [
            # Rahmenkopf-Informationen
            ("frame_head", c_uint16),           # Rahmenkopf, vereinbart als 0x5A5A
            ("frame_cnt", c_uint8),             # Rahmenzählung, zyklischer Zähler 0-255
            ("data_len", c_uint16),             # Länge des Dateninhalts
            ("program_state", c_uint8),         # Programmstatus, 1-gestoppt; 2-läuft; 3-pausiert
            ("robot_state", c_uint8),             # Roboterbewegungsstatus, 1-gestoppt; 2-läuft; 3-pausiert; 4-ziehen
            ("main_code", c_int),               # Hauptfehlercode
            ("sub_code", c_int),                # Unterfehlercode
            ("robot_mode", c_uint8),            # Robotermodus, 1-Handmodus; 0-Automatikmodus

            # Gelenkpositionen und -geschwindigkeiten
            ("jt_cur_pos", c_double * 6),       # Aktuelle Gelenkpositionen von 6 Achsen, Einheit deg
            ("tl_cur_pos", c_double * 6),       # Aktuelle Werkzeugposition [x,y,z,rx,ry,rz]
            ("flange_cur_pos", c_double * 6),   # Aktuelle Endflanschposition [x,y,z,rx,ry,rz]
            ("actual_qd", c_double * 6),        # Aktuelle Geschwindigkeiten von 6 Gelenken, Einheit deg/s
            ("actual_qdd", c_double * 6),       # Aktuelle Beschleunigungen von 6 Gelenken, Einheit deg/s^2
            ("target_TCP_CmpSpeed", c_double * 2),  # TCP zusammengesetzte Befehlgeschwindigkeit [Position mm/s, Orientierung deg/s]
            ("target_TCP_Speed", c_double * 6), # TCP Befehlgeschwindigkeit [x,y,z,rx,ry,rz]
            ("actual_TCP_CmpSpeed", c_double * 2),  # TCP zusammengesetzte tatsächliche Geschwindigkeit [Position mm/s, Orientierung deg/s]
            ("actual_TCP_Speed", c_double * 6), # TCP tatsächliche Geschwindigkeit [x,y,z,rx,ry,rz]
            ("jt_cur_tor", c_double * 6),       # Aktuelle Drehmomente von 6 Achsen, Einheit N·m

            # Werkzeug- und Werkstückkoordinatensysteme
            ("tool", c_int),                    # Angewandtes Werkzeugkoordinatensystem Nummer
            ("user", c_int),                    # Angewandtes Werkstückkoordinatensystem Nummer

            # Digitale E/A
            ("cl_dgt_output_h", c_uint8),       # Digitaler IO-Ausgang des Steuerkastens 15-8
            ("cl_dgt_output_l", c_uint8),       # Digitaler IO-Ausgang des Steuerkastens 7-0
            ("tl_dgt_output_l", c_uint8),       # Digitaler IO-Ausgang des Werkzeugs 7-0, nur bit0-bit1 gültig
            ("cl_dgt_input_h", c_uint8),        # Digitaler IO-Eingang des Steuerkastens 15-8
            ("cl_dgt_input_l", c_uint8),        # Digitaler IO-Eingang des Steuerkastens 7-0
            ("tl_dgt_input_l", c_uint8),        # Digitaler IO-Eingang des Werkzeugs 7-0, nur bit0-bit1 gültig

            # Analoge E/A
            ("cl_analog_input", c_uint16 * 2),  # Analoger Eingang des Steuerkastens [0],[1]
            ("tl_anglog_input", c_uint16),      # Analoger Werkzeugeingang

            # Kraft-/Drehmomentsensor
            ("ft_sensor_raw_data", c_double * 6),   # Rohdaten des Kraft-/Drehmomentsensors
            ("ft_sensor_data", c_double * 6),      # Daten des Kraft-/Drehmomentsensors
            ("ft_sensor_active", c_uint8),          # Aktivierungsstatus des Kraft-/Drehmomentsensors

            # Statussignale
            ("EmergencyStop", c_uint8),         # Not-Halt-Flag, 0-nicht gedrückt, 1-gedrückt
            ("motion_done", c_int),             # Bewegung-abgeschlossen-Signal, 1-abgeschlossen, 0-nicht abgeschlossen
            ("gripper_motiondone", c_uint8),    # Greifer-Bewegungsabschluss-Signal, 0-nicht abgeschlossen, 1-abgeschlossen (kein Objekt erkannt), 2-Bewegung abgeschlossen (Objekt erkannt)
            ("mc_queue_len", c_int),            # Länge der Bewegungskommando-Warteschlange
            ("collisionState", c_uint8),        # Kollisionserkennung, 1-Kollision, 0-keine Kollision
            ("trajectory_pnum", c_int),         # Bahnpunktnummer
            ("safety_stop0_state", c_uint8),    # Sicherheitsstoppsignal SI0
            ("safety_stop1_state", c_uint8),    # Sicherheitsstoppsignal SI1

            # Greiferinformationen
            ("gripper_fault_id", c_uint8),      # Fehlerhafte Greifernummer
            ("gripper_fault", c_uint16),        # Greiferfehler 0-kein Fehler 1-485-Timeout 2-Befehlsfehler 3-Werkstückabfall Sonstiges-Greifer-Fehlercode
            ("gripper_active", c_uint16),      # Greifer-Aktivierungsstatus
            ("gripper_position", c_uint8),      # Greiferposition
            ("gripper_speed", c_int8),          # Greifergeschwindigkeit
            ("gripper_current", c_int8),        # Greiferstrom
            ("gripper_temp", c_int),            # Greifertemperatur
            ("gripper_voltage", c_int),         # Greiferspannung

            # Erweiterungsachsenstatus
            ("aux_axis_state", ROBOT_AUX_STATE * 25),    # 485 Erweiterungsachsenstatus (25)
            ("extAxisStatus", EXT_AXIS_STATUS * 4), # UDP Erweiterungsachsenstatus (4)

            # Erweiterter E/A-Status
            ("extDIState", c_uint16 * 8),       # Erweiterter DI-Eingang
            ("extDOState", c_uint16 * 8),       # Erweiterter DO-Ausgang
            ("extAIState", c_uint16 * 4),        # Erweiterter AI-Eingang
            ("extAOState", c_uint16 * 4),        # Erweiterter AO-Ausgang

            # Roboter- und Gelenkstatus
            ("rbtEnableState", c_int),                  # Roboter-Aktivierungsstatus
            ("jointDriverTorque", c_double * 6),        # Roboter-Gelenktreiber-Drehmoment
            ("jointDriverTemperature", c_double * 6),   # Roboter-Gelenktreiber-Temperatur

            # Roboterzeit
            #("robotTime", c_int * 7),             # Roboter-Systemzeit [Jahr,Monat,Tag,Stunde,Minute,Sekunde,Millisekunde]
            ("year", ctypes.c_uint16),  # Jahr
            ("mouth", ctypes.c_uint8),  # Monat
            ("day", ctypes.c_uint8),   # Tag
            ("hour", ctypes.c_uint8),   # Stunde
            ("minute", ctypes.c_uint8), # Minute
            ("second", ctypes.c_uint8), # Sekunde
            ("millisecond", ctypes.c_uint16), # Millisekunde

            ("softwareUpgradeState", c_int),      # Roboter-Software-Upgrade-Status
            ("endLuaErrCode", c_uint16),          # End-Lua-Status

            # Analoger Ausgang
            ("cl_analog_output", c_uint16 * 2), # Analoger Ausgang des Steuerkastens [0],[1]
            ("tl_analog_output", c_uint16),       # Analoger Werkzeugausgang

            # Rotierender Greifer
            ("gripperRotNum", c_float),         # Aktuelle Drehzahl des rotierenden Greifers
            ("gripperRotSpeed", c_uint8),       # Aktuelle Drehzahl-Prozentsatz des rotierenden Greifers
            ("gripperRotTorque", c_uint8),      # Aktuelles Drehmoment-Prozentsatz des rotierenden Greifers

            # Schweißunterbrechungsstatus - Verwendung einer Struktur
            ("weldingBreakOffState", WELDING_BREAKOFF_STATE),  # Schweißunterbrechungsstatus

            # Zielgelenk-Drehmoment
            ("jt_tgt_tor", c_double * 6),       # Gelenkbefehls-Drehmoment

            ("smartToolState", c_int),          # SmartTool-Griffknopfstatus
            ("wideVoltageCtrlBoxTemp", c_float),        # Weitspannungs-Steuerkastentemperatur
            ("wideVoltageCtrlBoxFanCurrent", c_uint16), # Weitspannungs-Steuerkasten-Lüfterstrom (mA)

            # Koordinatensystemwerte
            ("toolCoord", c_double * 6),        # Aktuelle Werkzeugkoordinatensystemwerte; x,y,z,rx,ry,rz
            ("wobjCoord", c_double * 6),        # Aktuelle Werkstückkoordinatensystemwerte; x,y,z,rx,ry,rz
            ("extoolCoord", c_double * 6),      # Aktuelle externe Werkzeugkoordinatensystemwerte; x,y,z,rx,ry,rz
            ("exAxisCoord", c_double * 6),      # Aktuelle Erweiterungsachsenkoordinatensystemwerte; x,y,z,rx,ry,rz

            # Last
            ("load", c_double),                 # Lastmasse
            ("loadCog", c_double * 3),            # Lastschwerpunkt

            # Servobefehle
            ("lastServoTarget", c_double * 6),  # Letzte ServoJ-Zielposition in der Warteschlange
            ("servoJCmdNum", c_int),            # ServoJ-Befehlszähler

            # Zielgelenkdaten
            ("targetJointPos", c_double * 6),   # 6 Gelenke Befehlsposition, Einheit °
            ("targetJointVel", c_double * 6),   # 6 Gelenke Befehlgeschwindigkeit, Einheit °/s
            ("targetJointAcc", c_double * 6),   # 6 Gelenke Befehlbeschleunigung, Einheit °/s2
            ("targetJointCurrent", c_double * 6), # 6 Gelenke Befehlstrom, Einheit A
            ("actualJointCurrent", c_double * 6), # 6 Gelenke aktueller Strom, Einheit A
            ("actualTCPForce", c_double * 6),   # Roboter-Endeffektor-Drehmoment Nm; x,y,z,rx,ry,rz
            ("targetTCPPos", c_double * 6),     # Roboter-TCP-Befehlsposition mm; x,y,z,rx,ry,rz

            ("collisionLevel", c_uint8 * 6),    # Roboter-Kollisionsstufe
            ("speedScaleManual", c_double),     # Handmodus globale Geschwindigkeitsprozentsatz
            ("speedScaleAuto", c_double),       # Automatikmodus globale Geschwindigkeitsprozentsatz
            ("luaLineNum", c_int),              # Aktuelle Lua-Programmzeilennummer
            ("abnomalStop", c_uint8),           # 0-keine Abnormalität; 1-Abnormalität vorhanden
            ("currentLuaFileName", c_uint8 * 256),  # Name des aktuell ausgeführten Lua-Programms
            ("programTotalLine", c_uint8),      # Gesamtzeilen des Lua-Programms
            ("safetyBoxSingal", c_uint8 * 6),   # Roboter-Tastenfeld-Tastenstatus

            # Schweißdaten
            ("weldVoltage", c_double),          # Schweißspannung V
            ("weldCurrent", c_double),          # Schweißstrom
            ("weldTrackVel", c_double),         # Schweißnahtverfolgungsgeschwindigkeit mm/s

            ("tpdException", c_uint8),            # TPD-Bahnladeanzahl überschritten, 0-nicht überschritten, 1-überschritten
            ("alarmRebootRobot", c_uint8),      # Warnung, 1-Not-Halt-Taste loslassen und Steuerkasten neu starten, 2-Gelenkkommunikationsstörung, Steuerkasten neu starten
            ("modbusMasterConnect", c_uint8),   # bit0-7 entsprechen ModbusTCP-Master 0-7 Verbindungsstatus
            ("modbusSlaveConnect", c_uint8),    # ModbusTCP-Slave-Verbindungsstatus
            ("btnBoxStopSignal", c_uint8),      # Tastenfeld-Not-Halt-Signal
            ("dragAlarm", c_uint8),             # Zieh-Warnung
            ("safetyDoorAlarm", c_uint8),       # Sicherheitstürwarnung
            ("safetyPlaneAlarm", c_uint8),      # Eintritt in Sicherheitswand-Warnung
            ("motonAlarm", c_uint8),            # Bewegungswarnung
            ("interfaceAlarm", c_uint8),        # Eintritt in Interferenzbereich-Warnung
            ("udpCmdState", c_int),             # Port 20007 UDP-Kommunikationsverbindungsstatus
            ("weldReadyState", c_uint8),        # Schweißgerät-Bereitschaftsstatus
            ("alarmCheckEmergStopBtn", c_uint8),    # 0-normal; 1-Kommunikationsstörung, prüfen ob Not-Halt-Taste losgelassen ist
            ("tsTmCmdComError", c_uint8),       # 0-normal; 1-Drehmomentbefehl-Kommunikationsfehler
            ("tsTmStateComError", c_uint8),     # 0-normal; 1-Drehmomentstatus-Kommunikationsfehler
            ("ctrlBoxError", c_int),            # Steuerkastenfehler
            ("safetyDataState", c_uint8),       # Sicherheitsdatenstatus-Flag
            ("forceSensorErrState", c_uint8),   # Kraftsensor-Verbindungszeitüberschreitungsfehler
            ("ctrlOpenLuaErrCode", c_uint8 * 4),  # 4 Controller-Peripherieprotokoll-Fehlercodes
            ("strangePosFlag", c_uint8),        # Derzeit in singulärer Pose-Flag
            ("alarm", c_uint8),                 # Warnung
            ("driverAlarm", c_uint8),           # Treiber-Alarmachsenummer
            ("aliveSlaveNumError", c_uint8),    # Aktiver Slave-Anzahlfehler
            ("slaveComError", c_uint8 * 8),     # Slave-Fehlerstatus
            ("cmdPointError", c_uint8),         # Befehlspunktfehler
            ("IOError", c_uint8),               # IO-Fehler
            ("gripperError", c_uint8),          # Greiferfehler
            ("fileError", c_uint8),             # Dateifehler
            ("paraError", c_uint8),             # Parameterfehler
            ("exaxisOutLimitError", c_uint8),   # Externe Achse Weichgrenzenüberschreitungsfehler
            ("driverComError", c_uint8 * 6),    # Treiberkommunikationsfehler
            ("driverError", c_uint8),           # Treiberkommunikationsfehler-Achsennummer
            ("outSoftLimitError", c_uint8),     # Weichgrenzenüberschreitungsfehler
            ("axleGenComData", c_uint8 * 130),   # Achsen allgemeine Kommunikationsdaten (azyklisch)
            ("socketConnTimeout", c_uint8),     # Socket-Verbindungszeitüberschreitung
            ("socketReadTimeout", c_uint8),     # Socket-Lesezeitüberschreitung
            ("tsWebStateComErr", c_uint8),      # TS_WEB-Statuskommunikationsfehler
            ("exaxisCoordID", c_uint8),         # Externe erweiterte Achsen-ID
            ("check_sum", c_uint16)          # Summenprüfung
        ]

Controller-Statusrückmeldungs-Datenpaket
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: Python SDK-v2.1.7

.. csv-table::
    :header-rows: 1
    :name: Datenpaket der Controller-Statusrückmeldung
    :widths: 20 30

    "Variable", "Bedeutung"
    "program_state", "Programmausführungsstatus: 1 - gestoppt; 2 - läuft; 3 - pausiert"
    "robot_state", "Roboterbewegungsstatus: 1 - gestoppt; 2 - läuft; 3 - pausiert; 4 - Führung (Drag)"
    "main_code", "Hauptfehlercode"
    "sub_code", "Unterfehlercode"
    "robot_mode", "Robotermodus: 0 - Automatikmodus; 1 - Handmodus"
    "jt_cur_pos[i]", "Aktuelle Gelenkposition, Einheit [°], i:0~5"
    "tl_cur_pos[i]", "Aktuelle Werkzeugpose (TCP), Einheiten [° & mm], i:0~5"
    "flange_cur_pos[i]", "Aktuelle Pose des Endflansches, Einheiten [° & mm], i:0~5"
    "actual_qd[i]", "Aktuelle Gelenkgeschwindigkeit des Roboters, Einheit [°/s], i:0~5"
    "actual_qdd[i]", "Aktuelle Gelenkbeschleunigung des Roboters, Einheit [°/s²], i:0~5"
    "target_TCP_CmpSpeed[i]", "Befohlene TCP-Resultierende-Geschwindigkeit, Einheiten [mm/s & °/s], i:0~1"
    "target_TCP_Speed[i]", "Befohlene TCP-Geschwindigkeit (Komponenten), Einheiten [mm/s & °/s], i:0~5"
    "actual_TCP_CmpSpeed[i]", "Tatsächliche TCP-Resultierende-Geschwindigkeit, Einheiten [mm/s & °/s], i:0~1"
    "actual_TCP_Speed[i]", "Tatsächliche TCP-Geschwindigkeit (Komponenten), Einheiten [mm/s & °/s], i:0~5"
    "jt_cur_tor[i]", "Aktuelles Gelenkmoment, Einheit [Nm], i:0~5"
    "tool", "Nummer des verwendeten Werkzeugkoordinatensystems"
    "user", "Nummer des verwendeten Werkstückkoordinatensystems"
    "cl_dgt_output_h", "Digitalausgänge des Steuerkastens (Bits 15-8)"
    "cl_dgt_output_l", "Digitalausgänge des Steuerkastens (Bits 7-0)"
    "tl_dgt_output_l", "Digitalausgänge des Werkzeugs (Bits 7-0, nur Bit0-Bit1 gültig)"
    "dgt_input_h", "Digitaleingänge des Steuerkastens (Bits 15-8)"
    "cl_dgt_input_l", "Digitaleingänge des Steuerkastens (Bits 7-0)"
    "tl_dgt_input_l", "Digitaleingänge des Werkzeugs (Bits 7-0, nur Bit0-Bit1 gültig)"
    "cl_analog_input[i]", "Analogeingänge des Steuerkastens, i:0~2"
    "tl_anglog_input", "Analogeingang des Werkzeugs"
    "ft_sensor_raw_data", "Rohdaten des Kraft-/Momentensensors, Einheiten [N & Nm], i:0~5"
    "ft_sensor_data", "Verarbeitete Daten des Kraft-/Momentensensors, Einheiten [N & Nm], i:0~5"
    "ft_sensor_active", "Aktivierungsstatus des Kraft-/Momentensensors: 0 - zurückgesetzt, 1 - aktiviert"
    "EmergencyStop", "Not-Halt-Status: 0 - Not-Halt nicht betätigt, 1 - Not-Halt betätigt"
    "motion_done", "Bewegungsabschluss-Signal: 1 - abgeschlossen, 0 - nicht abgeschlossen"
    "gripper_motiondone", "Greifer-Bewegungsabschluss-Signal, 0-nicht abgeschlossen, 1-abgeschlossen (kein Objekt erkannt), 2-Bewegung abgeschlossen (Objekt erkannt)"
    "mc_queue_len", "Länge der Bewegungsbefehlswarteschlange"
    "collisionState", "Kollisionserkennung: 1 - Kollision, 0 - keine Kollision"
    "trajectory_pnum", "Trajektorienpunktnummer"
    "safety_stop0_state", "Sicherheitsstopp-Signal SI0"
    "safety_stop1_state", "Sicherheitsstopp-Signal SI1"
    "gripper_fault_id", "Nummer des fehlerhaften Greifers"
    "gripper_fault", "Greiferfehler 0-kein Fehler 1-485-Timeout 2-Befehlsfehler 3-Werkstückabfall Sonstiges-Greifer-Fehlercode"
    "gripper_active", "Greifer-Aktivierungsstatus: 0 - nicht aktiviert, 1 - aktiviert"
    "gripper_position", "Greiferposition (Prozent)"
    "gripper_speed", "Greifergeschwindigkeit (Prozent)"
    "gripper_current", "Greiferstrom (Prozent)"
    "gripper_tmp", "Greifertemperatur, Einheit [°C]"
    "gripper_voltage", "Greiferspannung, Einheit [V]"
    "auxState.servoId", "485-Erweiterungsachse: Servoantriebs-ID, i:0~3"
    "auxState.servoErrCode", "485-Erweiterungsachse: Fehlercode des Servoantriebs, i:0~3"
    "auxState.servoState", "485-Erweiterungsachse: Status des Servoantriebs, i:0~3"
    "auxState.servoPos", "485-Erweiterungsachse: Aktuelle Servoposition, i:0~3"
    "auxState.servoVel", "485-Erweiterungsachse: Aktuelle Servogeschwindigkeit, i:0~3"
    "auxState.servoTorque", "485-Erweiterungsachse: Aktuelles Servodrehmoment, i:0~3"
    "extAxisStatus[i].pos", "UDP-Erweiterungsachse: Position, i:0~3"
    "extAxisStatus[i].vel", "UDP-Erweiterungsachse: Geschwindigkeit, i:0~3"
    "extAxisStatus[i].errorCode", "UDP-Erweiterungsachse: Fehlercode, i:0~3"
    "extAxisStatus[i].ready", "UDP-Erweiterungsachse: Servo bereit, i:0~3"
    "extAxisStatus[i].inPos", "UDP-Erweiterungsachse: Servo in Position, i:0~3"
    "extAxisStatus[i].alarm", "UDP-Erweiterungsachse: Servo-Alarm, i:0~3"
    "extAxisStatus[i].flerr", "UDP-Erweiterungsachse: Folgefhler, i:0~3"
    "extAxisStatus[i].nlimit", "UDP-Erweiterungsachse: Negativer Endschalter erreicht, i:0~3"
    "extAxisStatus[i].pLimit", "UDP-Erweiterungsachse: Positiver Endschalter erreicht, i:0~3"
    "extAxisStatus[i].mdbsOffLine", "UDP-Erweiterungsachse: Antriebs-485-Bus offline"
    "extAxisStatus[i].mdbsTimeout", "UDP-Erweiterungsachse: 485-Kommunikation zwischen Steuerkarte und Steuerkasten Zeitüberschreitung"
    "extAxisStatus[i].homingStatus", "UDP-Erweiterungsachse: Referenzfahrt-Status"
    "extDIState", "Erweiterter Digitaleingangsstatus"
    "extDOState", "Erweiterter Digitalausgangsstatus"
    "extAIState", "Erweiterter Analogeingangsstatus"
    "extAOState", "Erweiterter Analogausgangsstatus"
    "rbtEnableState", "Roboter-Aktivierungsstatus (Enable)"
    "jointDriverTorque", "Aktuelles Drehmoment der Gelenkantriebe"
    "jointDriverTemperature", "Aktuelle Temperatur der Gelenkantriebe"
    "year", "Jahr"
    "mouth", "Monat"
    "day", "Tag"
    "hour", "Stunde"
    "minute", "Minute"
    "second", "Sekunde"
    "millisecond", "Millisekunde"
    "softwareUpgradeState", "Status des Roboter-Software-Upgrades"
    "endLuaErrCode", "Ausführungsstatus des Endeffektor-LUA-Skripts"
    "cl_analog_output[i]", "Analogausgänge des Steuerkastens, i:0~1"
    "tl_analog_output", "Analogausgang des Werkzeugs"
    "gripperRotNum", "Aktuelle Rotationsanzahl des Rotationsgreifers"
    "gripperRotSpeed", "Aktuelle Rotationsgeschwindigkeit des Rotationsgreifers (Prozent)"
    "gripperRotTorque", "Aktuelles Rotationsdrehmoment des Rotationsgreifers (Prozent)"
    "weldingBreakOffState", "Schweißunterbrechungsstatus"
    "jt_tgt_tor", "Befehls-Gelenkmoment"
    "smartToolState", "SmartTool-Griff Tastenstatus"
    "wideVoltageCtrlBoxTemp", "Temperatur des Weitspannungs-Steuerkastens"
    "wideVoltageCtrlBoxFanCurrent", "Lüfterstrom des Weitspannungs-Steuerkastens (mA)"
    "toolCoord[i]", "Werkzeugkoordinatensystem, i:0~5"
    "wobjCoord[i]", "Werkstückkoordinatensystem, i:0~5"
    "extoolCoord[i]", "Externes Werkzeugkoordinatensystem, i:0~5"
    "exAxisCoord[i]", "Erweiterungsachsen-Koordinatensystem, i:0~5"
    "load", "Lastmasse"
    "loadCog[i]", "Lastschwerpunkt, i:0~2"
    "lastServoTarget[i]", "Letzte ServoJ-Zielposition in der Warteschlange, i:0~5"
    "servoJCmdNum", "ServoJ-Befehlszähler"

Servocontroller-Status
~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: Python SDK-v2.1.3

.. csv-table::
    :header-rows: 1
    :name: Servocontroller-Status
    :widths: 20 30

    "Variable", "Bedeutung"
    "servoId", "Servoantriebs-ID-Nummer"
    "servoErrCode", "Fehlercode des Servoantriebs"
    "servoState", "Status des Servoantriebs"
    "servoPos", "Aktuelle Servoposition"
    "servoVel", "Aktuelle Servogeschwindigkeit"
    "servoTorque", "Aktuelles Servodrehmoment"

Erweiterungsachsen-Status
~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: Python SDK-v2.1.3

.. csv-table::
    :header-rows: 1
    :name: Erweiterungsachsen-Status
    :widths: 20 30

    "Variable", "Bedeutung"
    "pos", "Position der Erweiterungsachse"
    "vel", "Geschwindigkeit der Erweiterungsachse"
    "errorCode", "Fehlercode der Erweiterungsachse"
    "ready", "Servo bereit"
    "inPos", "Servo in Position"
    "alarm", "Servo-Alarm"
    "flerr", "Folgefehler"
    "nlimit", "Negativer Endschalter erreicht"
    "pLimit", "Positiver Endschalter erreicht"
    "mdbsOffLine", "Antriebs-485-Bus offline"
    "mdbsTimeout", "485-Kommunikation zwischen Steuerkarte und Steuerkasten Zeitüberschreitung"
    "homingStatus", "Status der Referenzfahrt der Erweiterungsachse"

Schweißunterbrechungsstatus
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: Python SDK-v2.1.3

.. csv-table::
    :header-rows: 1
    :name: Schweißunterbrechungsstatus
    :widths: 20 30

    "Variable", "Bedeutung"
    "breakOffState", "Schweißunterbrechungsstatus"
    "weldArcState", "Lichtbogenunterbrechungsstatus beim Schweißen"

Codebeispiel
~~~~~~~~~~~~
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    print("program_state:", robot.robot_state_pkg.program_state)
    print("robot_state:", robot.robot_state_pkg.robot_state)
    print("main_code:", robot.robot_state_pkg.main_code)
    print("sub_code:", robot.robot_state_pkg.sub_code)
    print("robot_mode:", robot.robot_state_pkg.robot_mode)
    print("jt_cur_pos0:", robot.robot_state_pkg.jt_cur_pos[0])
    print("jt_cur_pos1:", robot.robot_state_pkg.jt_cur_pos[1])
    print("jt_cur_pos2:", robot.robot_state_pkg.jt_cur_pos[2])
    print("jt_cur_pos3:", robot.robot_state_pkg.jt_cur_pos[3])
    print("jt_cur_pos4:", robot.robot_state_pkg.jt_cur_pos[4])
    print("jt_cur_pos5:", robot.robot_state_pkg.jt_cur_pos[5])
    print("tl_cur_pos0:", robot.robot_state_pkg.tl_cur_pos[0])
    print("tl_cur_pos1:", robot.robot_state_pkg.tl_cur_pos[1])
    print("tl_cur_pos2:", robot.robot_state_pkg.tl_cur_pos[2])
    print("tl_cur_pos3:", robot.robot_state_pkg.tl_cur_pos[3])
    print("tl_cur_pos4:", robot.robot_state_pkg.tl_cur_pos[4])
    print("tl_cur_pos5:", robot.robot_state_pkg.tl_cur_pos[5])
    print("flange_cur_pos0:", robot.robot_state_pkg.flange_cur_pos[0])
    print("flange_cur_pos1:", robot.robot_state_pkg.flange_cur_pos[1])
    print("flange_cur_pos2:", robot.robot_state_pkg.flange_cur_pos[2])
    print("flange_cur_pos3:", robot.robot_state_pkg.flange_cur_pos[3])
    print("flange_cur_pos4:", robot.robot_state_pkg.flange_cur_pos[4])
    print("flange_cur_pos5:", robot.robot_state_pkg.flange_cur_pos[5])
    print("actual_qd0:", robot.robot_state_pkg.actual_qd[0])
    print("actual_qd1:", robot.robot_state_pkg.actual_qd[1])
    print("actual_qd2:", robot.robot_state_pkg.actual_qd[2])
    print("actual_qd3:", robot.robot_state_pkg.actual_qd[3])
    print("actual_qd4:", robot.robot_state_pkg.actual_qd[4])
    print("actual_qd5:", robot.robot_state_pkg.actual_qd[5])
    print("actual_qdd0:", robot.robot_state_pkg.actual_qdd[0])
    print("actual_qdd1:", robot.robot_state_pkg.actual_qdd[1])
    print("actual_qdd2:", robot.robot_state_pkg.actual_qdd[2])
    print("actual_qdd3:", robot.robot_state_pkg.actual_qdd[3])
    print("actual_qdd4:", robot.robot_state_pkg.actual_qdd[4])
    print("actual_qdd5:", robot.robot_state_pkg.actual_qdd[5])
    print("target_TCP_CmpSpeed0:", robot.robot_state_pkg.target_TCP_CmpSpeed[0])
    print("target_TCP_CmpSpeed1:", robot.robot_state_pkg.target_TCP_CmpSpeed[1])
    print("target_TCP_Speed0:", robot.robot_state_pkg.target_TCP_Speed[0])
    print("target_TCP_Speed1:", robot.robot_state_pkg.target_TCP_Speed[1])
    print("target_TCP_Speed2:", robot.robot_state_pkg.target_TCP_Speed[2])
    print("target_TCP_Speed3:", robot.robot_state_pkg.target_TCP_Speed[3])
    print("target_TCP_Speed4:", robot.robot_state_pkg.target_TCP_Speed[4])
    print("target_TCP_Speed5:", robot.robot_state_pkg.target_TCP_Speed[5])
    print("actual_TCP_CmpSpeed0:", robot.robot_state_pkg.actual_TCP_CmpSpeed[0])
    print("actual_TCP_CmpSpeed1:", robot.robot_state_pkg.actual_TCP_CmpSpeed[1])
    print("actual_TCP_Speed0:", robot.robot_state_pkg.actual_TCP_Speed[0])
    print("actual_TCP_Speed1:", robot.robot_state_pkg.actual_TCP_Speed[1])
    print("actual_TCP_Speed2:", robot.robot_state_pkg.actual_TCP_Speed[2])
    print("actual_TCP_Speed3:", robot.robot_state_pkg.actual_TCP_Speed[3])
    print("actual_TCP_Speed4:", robot.robot_state_pkg.actual_TCP_Speed[4])
    print("actual_TCP_Speed5:", robot.robot_state_pkg.actual_TCP_Speed[5])
    print("jt_cur_tor0:", robot.robot_state_pkg.jt_cur_tor[0])
    print("jt_cur_tor1:", robot.robot_state_pkg.jt_cur_tor[1])
    print("jt_cur_tor2:", robot.robot_state_pkg.jt_cur_tor[2])
    print("jt_cur_tor3:", robot.robot_state_pkg.jt_cur_tor[3])
    print("jt_cur_tor4:", robot.robot_state_pkg.jt_cur_tor[4])
    print("jt_cur_tor5:", robot.robot_state_pkg.jt_cur_tor[5])
    print("tool:", robot.robot_state_pkg.tool)
    print("user:", robot.robot_state_pkg.user)
    print("cl_dgt_output_h:", robot.robot_state_pkg.cl_dgt_output_h)
    print("cl_dgt_output_l:", robot.robot_state_pkg.cl_dgt_output_l)
    print("tl_dgt_output_l:", robot.robot_state_pkg.tl_dgt_output_l)
    print("cl_dgt_input_h:", robot.robot_state_pkg.cl_dgt_input_h)
    print("cl_dgt_input_l:", robot.robot_state_pkg.cl_dgt_input_l)
    print("tl_dgt_input_l:", robot.robot_state_pkg.tl_dgt_input_l)
    print("cl_analog_input0:", robot.robot_state_pkg.cl_analog_input[0])
    print("cl_analog_input1:", robot.robot_state_pkg.cl_analog_input[1])
    print("tl_anglog_input:", robot.robot_state_pkg.tl_anglog_input)
    print("ft_sensor_raw_data0:", robot.robot_state_pkg.ft_sensor_raw_data[0])
    print("ft_sensor_raw_data1:", robot.robot_state_pkg.ft_sensor_raw_data[1])
    print("ft_sensor_raw_data2:", robot.robot_state_pkg.ft_sensor_raw_data[2])
    print("ft_sensor_raw_data3:", robot.robot_state_pkg.ft_sensor_raw_data[3])
    print("ft_sensor_raw_data4:", robot.robot_state_pkg.ft_sensor_raw_data[4])
    print("ft_sensor_raw_data5:", robot.robot_state_pkg.ft_sensor_raw_data[5])
    print("ft_sensor_data0:", robot.robot_state_pkg.ft_sensor_data[0])
    print("ft_sensor_data1:", robot.robot_state_pkg.ft_sensor_data[1])
    print("ft_sensor_data2:", robot.robot_state_pkg.ft_sensor_data[2])
    print("ft_sensor_data3:", robot.robot_state_pkg.ft_sensor_data[3])
    print("ft_sensor_data4:", robot.robot_state_pkg.ft_sensor_data[4])
    print("ft_sensor_data5:", robot.robot_state_pkg.ft_sensor_data[5])
    print("ft_sensor_active:", robot.robot_state_pkg.ft_sensor_active)
    print("EmergencyStop:", robot.robot_state_pkg.EmergencyStop)
    print("motion_done:", robot.robot_state_pkg.motion_done)
    print("gripper_motiondone:", robot.robot_state_pkg.gripper_motiondone)
    print("mc_queue_len:", robot.robot_state_pkg.mc_queue_len)
    print("collisionState:", robot.robot_state_pkg.collisionState)
    print("trajectory_pnum:", robot.robot_state_pkg.trajectory_pnum)
    print("safety_stop0_state:", robot.robot_state_pkg.safety_stop0_state)
    print("safety_stop1_state:", robot.robot_state_pkg.safety_stop1_state)
    print("gripper_fault_id:", robot.robot_state_pkg.gripper_fault_id)
    print("gripper_fault:", robot.robot_state_pkg.gripper_fault)
    print("gripper_active:", robot.robot_state_pkg.gripper_active)
    print("gripper_position:", robot.robot_state_pkg.gripper_position)
    print("gripper_speed:", robot.robot_state_pkg.gripper_speed)
    print("gripper_current:", robot.robot_state_pkg.gripper_current)
    print("gripper_tmp:", robot.robot_state_pkg.gripper_tmp)
    print("gripper_voltage:", robot.robot_state_pkg.gripper_voltage)
    print("auxState.servoId:", robot.robot_state_pkg.auxState.servoId)
    print("auxState.servoErrCode:", robot.robot_state_pkg.auxState.servoErrCode)
    print("auxState.servoState:", robot.robot_state_pkg.auxState.servoState)
    print("auxState.servoPos:", robot.robot_state_pkg.auxState.servoPos)
    print("auxState.servoVel:", robot.robot_state_pkg.auxState.servoVel)
    print("auxState.servoTorque:", robot.robot_state_pkg.auxState.servoTorque)
    for i in range(4):
        print("extAxisStatus.pos:", i, robot.robot_state_pkg.extAxisStatus[i].pos)
        print("extAxisStatus.vel:", i, robot.robot_state_pkg.extAxisStatus[i].vel)
        print("extAxisStatus.errorCode:", i, robot.robot_state_pkg.extAxisStatus[i].errorCode)
        print("extAxisStatus.ready:", i, robot.robot_state_pkg.extAxisStatus[i].ready)
        print("extAxisStatus.inPos:", i, robot.robot_state_pkg.extAxisStatus[i].inPos)
        print("extAxisStatus.alarm:", i, robot.robot_state_pkg.extAxisStatus[i].alarm)
        print("extAxisStatus.flerr:", i, robot.robot_state_pkg.extAxisStatus[i].flerr)
        print("extAxisStatus.nlimit:", i, robot.robot_state_pkg.extAxisStatus[i].nlimit)
        print("extAxisStatus.pLimit:", i, robot.robot_state_pkg.extAxisStatus[i].pLimit)
        print("extAxisStatus.mdbsOffLine:", i, robot.robot_state_pkg.extAxisStatus[i].mdbsOffLine)
        print("extAxisStatus.mdbsTimeout:", i, robot.robot_state_pkg.extAxisStatus[i].mdbsTimeout)
        print("extAxisStatus.homingStatus:", i, robot.robot_state_pkg.extAxisStatus[i].homingStatus)
    for i in range(8):
        print("extDIState:", i, robot.robot_state_pkg.extDIState[i])
        print("extDOState:", i, robot.robot_state_pkg.extDOState[i])
    for i in range(4):
        print("extAIState:", i, robot.robot_state_pkg.extAIState[i])
        print("extAOState:", i, robot.robot_state_pkg.extAOState[i])
    print("rbtEnableState:", robot.robot_state_pkg.rbtEnableState)
    print("jointDriverTorque0:", robot.robot_state_pkg.jointDriverTorque[0])
    print("jointDriverTorque1:", robot.robot_state_pkg.jointDriverTorque[1])
    print("jointDriverTorque2:", robot.robot_state_pkg.jointDriverTorque[2])
    print("jointDriverTorque3:", robot.robot_state_pkg.jointDriverTorque[3])
    print("jointDriverTorque4:", robot.robot_state_pkg.jointDriverTorque[4])
    print("jointDriverTorque5:", robot.robot_state_pkg.jointDriverTorque[5])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[0])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[1])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[2])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[3])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[4])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[5])
    print("year:", robot.robot_state_pkg.year)
    print("mouth:", robot.robot_state_pkg.mouth)
    print("day:", robot.robot_state_pkg.day)
    print("hour:", robot.robot_state_pkg.hour)
    print("minute:", robot.robot_state_pkg.minute)
    print("second:", robot.robot_state_pkg.second)
    print("millisecond:", robot.robot_state_pkg.millisecond)
    print("softwareUpgradeState:", robot.robot_state_pkg.softwareUpgradeState)
    print("endLuaErrCode:", robot.robot_state_pkg.endLuaErrCode)
    print("cl_analog_output[0]:", robot.robot_state_pkg.cl_analog_output[0])
    print("cl_analog_output[1]:", robot.robot_state_pkg.cl_analog_output[1])
    print("tl_analog_output:", robot.robot_state_pkg.tl_analog_output)
    print("gripperRotNum:", robot.robot_state_pkg.gripperRotNum)
    print("gripperRotSpeed:", robot.robot_state_pkg.gripperRotSpeed)
    print("gripperRotTorque:", robot.robot_state_pkg.gripperRotTorque)
    print("jt_tgt_tor:", robot.robot_state_pkg.jt_tgt_tor)
    print("smartToolState:", robot.robot_state_pkg.smartToolState)
    print("wideVoltageCtrlBoxTemp:", robot.robot_state_pkg.wideVoltageCtrlBoxTemp)
    print("wideVoltageCtrlBoxFanCurrent:", robot.robot_state_pkg.wideVoltageCtrlBoxFanCurrent)
    print("toolCoord0:", robot.robot_state_pkg.toolCoord[0])
    print("toolCoord1:", robot.robot_state_pkg.toolCoord[1])
    print("toolCoord2:", robot.robot_state_pkg.toolCoord[2])
    print("toolCoord3:", robot.robot_state_pkg.toolCoord[3])
    print("toolCoord4:", robot.robot_state_pkg.toolCoord[4])
    print("toolCoord5:", robot.robot_state_pkg.toolCoord[5])
    print("wobjCoord0:", robot.robot_state_pkg.wobjCoord[0])
    print("wobjCoord1:", robot.robot_state_pkg.wobjCoord[1])
    print("wobjCoord2:", robot.robot_state_pkg.wobjCoord[2])
    print("wobjCoord3:", robot.robot_state_pkg.wobjCoord[3])
    print("wobjCoord4:", robot.robot_state_pkg.wobjCoord[4])
    print("wobjCoord5:", robot.robot_state_pkg.wobjCoord[5])
    print("extoolCoord0:", robot.robot_state_pkg.extoolCoord[0])
    print("extoolCoord1:", robot.robot_state_pkg.extoolCoord[1])
    print("extoolCoord2:", robot.robot_state_pkg.extoolCoord[2])
    print("extoolCoord3:", robot.robot_state_pkg.extoolCoord[3])
    print("extoolCoord4:", robot.robot_state_pkg.extoolCoord[4])
    print("extoolCoord5:", robot.robot_state_pkg.extoolCoord[5])
    print("exAxisCoord0:", robot.robot_state_pkg.exAxisCoord[0])
    print("exAxisCoord1:", robot.robot_state_pkg.exAxisCoord[1])
    print("exAxisCoord2:", robot.robot_state_pkg.exAxisCoord[2])
    print("exAxisCoord3:", robot.robot_state_pkg.exAxisCoord[3])
    print("exAxisCoord4:", robot.robot_state_pkg.exAxisCoord[4])
    print("exAxisCoord5:", robot.robot_state_pkg.exAxisCoord[5])
    print("load:", robot.robot_state_pkg.load)
    print("loadCog0:", robot.robot_state_pkg.loadCog[0])
    print("loadCog1:", robot.robot_state_pkg.loadCog[1])
    print("loadCog2:", robot.robot_state_pkg.loadCog[2])
    print("lastServoTarget0:", robot.robot_state_pkg.lastServoTarget[0])
    print("lastServoTarget1:", robot.robot_state_pkg.lastServoTarget[1])
    print("lastServoTarget2:", robot.robot_state_pkg.lastServoTarget[2])
    print("lastServoTarget3:", robot.robot_state_pkg.lastServoTarget[3])
    print("lastServoTarget4:", robot.robot_state_pkg.lastServoTarget[4])
    print("lastServoTarget5:", robot.robot_state_pkg.lastServoTarget[5])
    print("servoJCmdNum:", robot.robot_state_pkg.servoJCmdNum)

Aufzählungstyp der Roboterstatus-Rückmeldungskonfigurationsliste
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    # ==================== RobotState Konfigurationslisten-Aufzählung ====================
    class RobotState(enum.Enum):
        """CNDE-Statusart-Aufzählung"""
        FrameHead = 0
        FrameCnt = 1
        DataLen = 2
        ProgramState = 3
        RobotState = 4
        MainCode = 5
        SubCode = 6
        RobotMode = 7
        JointCurPos = 8
        ToolCurPos = 9
        FlangeCurPos = 10
        ActualJointVel = 11
        ActualJointAcc = 12
        TargetTCPCmpSpeed = 13
        TargetTCPSpeed = 14
        ActualTCPCmpSpeed = 15
        ActualTCPSpeed = 16
        ActualJointTorque = 17
        Tool = 18
        User = 19
        ClDgtOutputH = 20
        ClDgtOutputL = 21
        TlDgtOutputL = 22
        ClDgtInputH = 23
        ClDgtInputL = 24
        TlDgtInputL = 25
        ClAnalogInput = 26
        TlAnglogInput = 27
        FtSensorRawData = 28
        FtSensorData = 29
        FtSensorActive = 30
        EmergencyStop = 31
        MotionDone = 32
        GripperMotiondone = 33
        McQueueLen = 34
        CollisionState = 35
        TrajectoryPnum = 36
        SafetyStop0State = 37
        SafetyStop1State = 38
        GripperFaultId = 39
        GripperFault = 40
        GripperActive = 41
        GripperPosition = 42
        GripperSpeed = 43
        GripperCurrent = 44
        GripperTemp = 45
        GripperVoltage = 46
        AuxState = 47
        ExtAxisStatus = 48
        ExtDIState = 49
        ExtDOState = 50
        ExtAIState = 51
        ExtAOState = 52
        RbtEnableState = 53
        JointDriverTorque = 54
        JointDriverTemperature = 55
        RobotTime = 56
        SoftwareUpgradeState = 57
        EndLuaErrCode = 58
        ClAnalogOutput = 59
        TlAnalogOutput = 60
        GripperRotNum = 61
        GripperRotSpeed = 62
        GripperRotTorque = 63
        WeldingBreakOffState = 64
        TargetJointTorque = 65
        SmartToolState = 66
        WideVoltageCtrlBoxTemp = 67
        WideVoltageCtrlBoxFanCurrent = 68
        ToolCoord = 69
        WobjCoord = 70
        ExtoolCoord = 71
        ExAxisCoord = 72
        Load = 73
        LoadCog = 74
        LastServoTarget = 75
        ServoJCmdNum = 76
        TargetJointPos = 77
        TargetJointVel = 78
        TargetJointAcc = 79
        TargetJointCurrent = 80
        ActualJointCurrent = 81
        ActualTCPForce = 82
        TargetTCPPos = 83
        CollisionLevel = 84
        SpeedScaleManual = 85
        SpeedScaleAuto = 86
        LuaLineNum = 87
        AbnomalStop = 88
        CurrentLuaFileName = 89
        ProgramTotalLine = 90
        SafetyBoxSingal = 91
        WeldVoltage = 92
        WeldCurrent = 93
        WeldTrackVel = 94
        TpdException = 95
        AlarmRebootRobot = 96
        ModbusMasterConnect = 97
        ModbusSlaveConnect = 98
        BtnBoxStopSignal = 99
        DragAlarm = 100
        SafetyDoorAlarm = 101
        SafetyPlaneAlarm = 102
        MotonAlarm = 103
        InterfaceAlarm = 104
        UdpCmdState = 105
        WeldReadyState = 106
        AlarmCheckEmergStopBtn = 107
        TsTmCmdComError = 108
        TsTmStateComError = 109
        CtrlBoxError = 110
        SafetyDataState = 111
        ForceSensorErrState = 112
        CtrlOpenLuaErrCode = 113
        StrangePosFlag = 114
        Alarm = 115
        DriverAlarm = 116
        AliveSlaveNumError = 117
        SlaveComError = 118
        CmdPointError = 119
        IOError = 120
        GripperError = 121
        FileError = 122
        ParaError = 123
        ExaxisOutLimitError = 124
        DriverComError = 125
        DriverError = 126
        OutSoftLimitError = 127
        AxleGenComData = 128
        SocketConnTimeout = 129
        SocketReadTimeout = 130
        TsWebStateComErr = 131
        exaxisCoordID = 132
        CheckSum = 133