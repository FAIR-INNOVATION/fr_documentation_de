CNDE-Einführung
===============

Das konfigurierbare Netzwerkdatenaustauschprotokoll für kollaborative Roboter (im Folgenden als CNDE bezeichnet) ist eine Methode, mit der ein Client über UDP-Kommunikation den Roboter steuern und seinen Rückmeldestatus abrufen kann.

Tabelle 1-1 zeigt die vollständige Sammlung aller Roboterzustände, die über CNDE abgerufen werden können. Der Client kann eine beliebige Anzahl benötigter Zustände aus der Tabelle auswählen und den Roboter veranlassen, diese Zustände gemäß dem eingestellten Rückmeldezyklus zurückzumelden.

Ebenso kann der Client die benötigten Robotersteuerungsfunktionskombinationen aus Tabelle 1-2 auswählen, um Robotersteuerungsvorgänge durchzuführen. Die Kommunikationsdaten zwischen Client und Roboter-CNDE müssen dem angegebenen Frame-Format entsprechen. Die CNDE-Kommunikationsports des Roboters sind 20005 und 20006. Port 20005 wird für die TCP-Kommunikation verwendet, Port 20006 für die UDP-Kommunikation.

Die Verwendung der CNDE-Funktion des Roboters umfasst hauptsächlich die folgenden vier Schritte:

① **Konfiguration des Eingangs-/Ausgangsdateninhalts**: Der Client sendet einen Befehl zur Eingangs-/Ausgangskonfiguration an den Roboter. Der Befehlsinhalt hat die Form einer Reihe von Steuerungs- oder Statusfunktionsnamen wie "std_DI_box,cfg_DI_box,motion_queue_len". Die Roboterseite zeichnet diese Namen auf, identifiziert sie und sendet dann die entsprechenden Funktionsdatentypen wie "UINT8, UINT8, INT32" an den Client zurück, was eine erfolgreiche Konfiguration anzeigt.

② **Starten der CNDE-Datenausgabe des Roboters**: Der Client sendet einen Befehl zum Starten der CNDE-Datenausgabe an den Roboter. Daraufhin beginnt der Roboter, die Roboterzustandsdaten gemäß dem konfigurierten Zyklus in Form eines Byte-Arrays (Little-Endian-Format) über UDP an den Client zu senden.

③ **Parsen der Roboterzustandsdaten**: Der Client empfängt die vom Roboter zurückgemeldeten Zustandsdaten in einer Schleife und parst die Daten basierend auf den vom Roboter während der Ausgangskonfiguration zurückgemeldeten Datentypen und der jedem Datentyp entsprechenden Bytelänge aus Tabelle 1-3, um die tatsächlichen Werte jedes Zustands zu erhalten. Die CNDE-Ausgabedaten des Roboters unterstützen maximal 4096 Bytes. Der konfigurierbare CNDE-Ausgabezyklus beträgt 1 ~ 200 ms.

④ **Senden von Roboter-Steuerdaten**: Der Client paketiert die Steuerdaten basierend auf den vom Roboter während der Eingangskonfiguration zurückgemeldeten Datentypen und der jedem Datentyp entsprechenden Bytelänge aus Tabelle 1-3 und sendet sie über UDP-Kommunikation an den Roboter. Die Roboterseite empfängt die Steuerdaten, parst sie und führt die Robotersteuerungsoperationen durch. Die CNDE-Eingabe des Roboters unterstützt 256 Rezepte. Der Client kann je nach Bedarf zunächst mehrere Eingangsrezepte konfigurieren und beim Senden von Eingangsdaten an den Roboter die dem aktuellen Daten entsprechende Rezeptnummer angeben.

.. centered:: Tabelle 1-1 Funktionen der Roboter-Ausgangskonfiguration

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Name**
     - **Datentyp**
     - **Beschreibung**

   * - std_DI_box
     - UINT8
     - Standard-DI-Eingang des Steuerkastens (Bit0 ~ Bit7 entsprechen DI0 ~ DI7)

   * - cfg_DI_box
     - UINT8
     - Konfigurierbarer CI-Eingang des Steuerkastens (Bit0 ~ Bit7 entsprechen CI0 ~ CI7)

   * - cfg_DI_tool
     - UINT8
     - Konfigurierbarer Werkzeug-DI-Eingang des Steuerkastens (Bit0 ~ Bit2 entsprechen toolDI0 ~ toolDI1)

   * - std_AI0_box
     - DOUBLE
     - Analogeingang AI0 des Steuerkastens (0 ~ 4095)

   * - std_AI1_box
     - DOUBLE
     - Analogeingang AI1 des Steuerkastens (0 ~ 4095)

   * - std_AI_tool
     - DOUBLE
     - Analogeingang tool_AI0 des Endeffektors (0 ~ 4095)

   * - run_up_time
     - DOUBLE
     - Betriebszeit des Roboters seit Einschalten (s)

   * - target_joint_pos
     - DOUBLE_6
     - Zielposition der Gelenke 1-6 (°)

   * - target_joint_vel
     - DOUBLE_6
     - Zielgeschwindigkeit der Gelenke 1-6 (°/s)

   * - target_joint_acc
     - DOUBLE_6
     - Zielbeschleunigung der Gelenke 1-6 (°/s²)

   * - target_joint_current
     - DOUBLE_6
     - Zielstrom der Gelenke 1-6 (A)

   * - target_joint_torque
     - DOUBLE_6
     - Zieldrehmoment der Gelenke 1-6 (Nm)

   * - actual_joint_pos
     - DOUBLE_6
     - Aktuelle Position der Gelenke 1-6 (°)

   * - actual_joint_vel
     - DOUBLE_6
     - Aktuelle Geschwindigkeit der Gelenke 1-6 (°/s)

   * - actual_joint_current
     - DOUBLE_6
     - Aktueller Strom der Gelenke 1-6 (A)

   * - actual_joint_torque
     - DOUBLE_6
     - Aktuelles Drehmoment der Gelenke 1-6 (Nm)

   * - actual_TCP_pos
     - DOUBLE_6
     - Aktuelle Werkzeugposition (TCP) im kartesischen Raum (mm)

   * - actual_TCP_vel
     - DOUBLE_6
     - Aktuelle Werkzeuggeschwindigkeit (TCP) im kartesischen Raum (mm/s)

   * - actual_TCP_force
     - DOUBLE_6
     - Resultierende Kraft am Werkzeug (TCP) im kartesischen Raum (N)

   * - target_TCP_pos
     - DOUBLE_6
     - Zielposition des Werkzeugs (TCP) im kartesischen Raum (mm)

   * - target_TCP_vel
     - DOUBLE_6
     - Zielgeschwindigkeit des Werkzeugs (TCP) im kartesischen Raum (mm/s)

   * - std_DO_box
     - UINT8
     - Standard-DO-Ausgang des Steuerkastens (Bit0 ~ Bit7 entsprechen DO0 ~ DO7)

   * - cfg_DO_box
     - UINT8
     - Konfigurierbarer CO-Ausgang des Steuerkastens (Bit0 ~ Bit7 entsprechen CO0 ~ CO7)

   * - cfg_DO_tool
     - UINT8
     - Standard-Werkzeug-DO-Ausgang des Steuerkastens (Bit0 ~ Bit1 entsprechen toolDO0 ~ toolDO1)

   * - std_AO0_box
     - DOUBLE
     - Analogausgang AO0 des Steuerkastens (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Analogausgang AO1 des Steuerkastens (0.0 ~ 4095.0)

   * - std_AO_tool
     - DOUBLE
     - Werkzeug-Analogausgang AO1 (0.0 ~ 4095.0)

   * - robot_mode
     - UINT8
     - Robotermodus (0 = Automatik; 1 = Hand)

   * - collision_level
     - UINT8_6
     - Kollisionsstufe der Gelenke 1-6 (1 ~ 10)

   * - speed_scaling_man
     - DOUBLE
     - Geschwindigkeitsprozentsatz im Handmodus (0 ~ 100)

   * - speed_scaling_auto
     - DOUBLE
     - Geschwindigkeitsprozentsatz im Automatikmodus (0 ~ 100)

   * - program_state
     - UINT8
     - Roboterprogramm-Ausführungsstatus (1 = gestoppt; 2 = in Bewegung; 3 = pausiert; 4 = Führung)

   * - line_number
     - INT32
     - Aktuelle Zeilennummer der Programmausführung

   * - payload
     - DOUBLE
     - Lastmasse (kg)

   * - pay_cog
     - DOUBLE_3
     - Lastschwerpunkt (x, y, z) (mm)

   * - motion_queue_len
     - INT32
     - Aktuelle Länge der Bewegungswarteschlange
   
   * - ft_sensor_data
     - DOUBLE_6
     - Rohdaten des Kraftsensors

   * - main_code
     - INT32
     - Hauptfehlercode

   * - sub_code
     - INT32
     - Unterfehlercode

   * - emergency_stop
     - UINT8
     - Not-Halt-Status

   * - motion_done
     - INT32
     - Bewegungsabschlussstatus

   * - timestamp_us
     - UINT64
     - Robotersystemzeit (µs)

   * - output_BIT_reg_8xX
     - UINT8_X
     - BIT-Typ Roboter-Ausgangsregister (8xX gibt die Anzahl der Register an. Wenn Sie 16 BIT-Ausgangsregister benötigen, lautet der tatsächliche Name: "output_BIT_reg_8x2". Der Roboter unterstützt maximal 128 BIT-Ausgangsregister.)

   * - output_INT_reg_X
     - INT32_X
     - INT-Typ Roboter-Ausgangsregister (X gibt die Anzahl der Register an. Wenn Sie 16 INT-Ausgangsregister benötigen, lautet der tatsächliche Name: "output_INT_reg_16". Der Roboter unterstützt maximal 64 INT-Ausgangsregister.)

   * - output_DOUBLE_reg_X
     - DOUBLE_X
     - DOUBLE-Typ Roboter-Ausgangsregister (X gibt die Anzahl der Register an. Wenn Sie 16 DOUBLE-Ausgangsregister benötigen, lautet der tatsächliche Name: "output_DOUBLE_reg_16". Der Roboter unterstützt maximal 64 DOUBLE-Ausgangsregister.)

   * - servoj_time
     - UINT64_5
     - servoj Zeitstempeldaten, Einheit ns

   * - actual_joint_temp
     - DOUBLE_6
     - Gelenk j1-j6 Treibertemperatur, Einheit °

   * - axle_gen_com_data
     - UINT8_130
     - Allgemeine periodische Daten des Endeffektors

   * - abnormal_stop
     - UINT8
     - Abnormaler Status, 0: keine Abnormalität, 1: Abnormalität vorhanden

   * - cur_lua_file_name
     - UINT8_256
     - Name der aktuell ausgeführten Lua-Datei

   * - prog_total_line
     - UINT8
     - Gesamtzahl der Zeilen in der aktuellen Datei

   * - safety_box_signal
     - UINT8_6
     - Tastenfeldsignal 0: gedrückt 1: losgelassen

   * - welding_voltage
     - DOUBLE
     - Tatsächliche Schweißspannung, Einheit V

   * - welding_current
     - DOUBLE
     - Tatsächlicher Schweißstrom, Einheit A

   * - welding_track_speed
     - DOUBLE
     - Schweißnahtverfolgungsgeschwindigkeit mm/s

   * - tpd_exception
     - UINT8
     - TPD-Ausnahme

   * - alarm_reboot_robot
     - UINT8
     - Roboter-Neustartwarnung

   * - modbus_master_connect
     - UINT8
     - | Verbindungsstatus von 8 Modbus-Mastern  
       | bit0-bit7 repräsentieren Master 0-7, 0-nicht verbunden, 1-verbunden

   * - modbus_slave_connect
     - UINT8
     - Modbus-Slave-Verbindungsstatus, 0-nicht verbunden, 1-verbunden

   * - btn_box_stop_signal
     - UINT8
     - Not-Halt-Tastensignal

   * - drag_alarm
     - UINT8
     - Ziehwarnung

   * - safety_door_alarm
     - UINT8
     - Sicherheitstürwarnung, 0 keine Warnung, 1 Sicherheitstür ausgelöst

   * - safety_plane_alarm
     - UINT8
     - Sicherheitswandwarnung, 0 keine Warnung, 1 Eintritt in Sicherheitswand

   * - motion_alarm
     - UINT8
     - | Bewegungswarnung, 0-keine Warnung,
       | 1-LIN-Befehl Haltungsänderung zu groß,
       | 2-TCP-Übergeschwindigkeit,
       | 3-Kollision aufgetreten,
       | 4-Achse 1 überschritt maximale Geschwindigkeit,
       | 5-Achse 2 überschritt maximale Geschwindigkeit,
       | 6-Achse 3 überschritt maximale Geschwindigkeit,
       | 7-Achse 4 überschritt maximale Geschwindigkeit,
       | 8-Achse 5 überschritt maximale Geschwindigkeit,
       | 9-Achse 6 überschritt maximale Geschwindigkeit,
       | 10-Achse 1 Gelenkbefehl und Rückmeldungsabweichung zu groß,
       | 11-Achse 2 Gelenkbefehl und Rückmeldungsabweichung zu groß,
       | 12-Achse 3 Gelenkbefehl und Rückmeldungsabweichung zu groß,
       | 13-Achse 4 Gelenkbefehl und Rückmeldungsabweichung zu groß,
       | 14-Achse 5 Gelenkbefehl und Rückmeldungsabweichung zu groß,
       | 15-Achse 6 Gelenkbefehl und Rückmeldungsabweichung zu groß,
       | 16-Singuläre Pose,
       | 17-LIN-Befehl Bewegungsgeschwindigkeit adaptiv,
       | 18-Zielgeschwindigkeitsanpassung Zeitüberschreitung oder nicht abgeschlossen,
       | 19-Dreheinfügebewegung fehlgeschlagen,
       | 20-Schraubenförmige Einführbewegung fehlgeschlagen,
       | 21-Lineare Einführbewegung fehlgeschlagen,
       | 22-Oberflächenpositionierungsbewegung fehlgeschlagen

   * - interfere_alarm
     - UINT8
     - Interferenzbereichswarnung, 0 keine Warnung, 1 Eintritt in Interferenzbereich

   * - udp_cmd_state
     - INT32
     - UDP-Verbindungsstatus

   * - weld_ready_state
     - UINT8
     - Schweißgerät-Bereitschaftsstatus, 1: bereit, 0: Schweißgerätefehler

   * - alarm_check_emerg_stop_btn
     - UINT8
     - Gelenkkommunikations-Anomaliewarnung

   * - ts_tm_cmd_com_error
     - UINT8
     - Drehmomentsystem-Befehlsfehler

   * - ts_tm_state_com_error
     - UINT8
     - Drehmomentsystem-Statusfehler

   * - ctrl_box_error
     - INT32
     - Steuerkastenfehler

   * - safety_data_state
     - UINT8
     - Sicherheitsdaten-Statusflag, 0 keine Abnormalität, 1-Abnormalität

   * - force_sensor_err_state
     - UINT8
     - Kraftsensor-Verbindungszeitüberschreitungsfehler; bit0-bit1 entsprechen Kraftsensor ID1-ID2

   * - ctrl_open_lua_errcode
     - UINT8_4
     - Controller-Open-Protocol-Fehlercode

   * - servo_id
     - UINT8
     - Servotreiber-ID-Nummer

   * - servo_errcode
     - INT32
     - Servotreiber-Fehlercode

   * - servo_state
     - INT32
     - Servotreiber-Status

   * - servo_actual_pos
     - DOUBLE
     - Servo aktuelle Position

   * - servo_actual_speed
     - DOUBLE
     - Servo aktuelle Geschwindigkeit
   
   * - servo_actual_torque
     - DOUBLE
     - Servo aktuelles Drehmoment
   
   * - gripper_active
     - INT32
     - Greifer-Aktivierungsstatus
   
   * - gripper_position
     - UINT8
     - Greifer-Positionsrückmeldung (Prozentsatz)
   
   * - gripper_speed
     - INT32
     - Greifer-Geschwindigkeitsrückmeldung (Prozentsatz)
   
   * - gripper_current
     - INT32
     - Greifer-Stromrückmeldung (Prozentsatz)
   
   * - gripper_temp
     - INT32
     - Greifer aktuelle Temperatur, Einheit °
   
   * - gripper_voltage
     - INT32
     - Greifer aktuelle Spannung, Einheit V
   
   * - rotating_gripper_num
     - DOUBLE
     - Rotationsgreifer-Drehzahlrückmeldung
   
   * - rotating_gripper_speed
     - UINT8
     - Rotationsgreifer-Drehgeschwindigkeitsrückmeldung (Prozentsatz)
   
   * - rotating_gripper_tor
     - UINT8
     - Rotationsgreifer-Drehmomentrückmeldung (Prozentsatz)
   
   * - weld_break_off_state
     - UINT8
     - Schweißunterbrechungsstatus: 0-Schweißen nicht unterbrochen, 1-Schweißen unterbrochen
   
   * - weld_arc_state
     - UINT8
     - Schweißlichtbogenstatus, 0-Lichtbogen nicht unterbrochen, 1-Lichtbogen unterbrochen
   
   * - smarttool_state
     - UINT32
     - Endeffektor-erweiterte IO-Daten (Smart-Tool)
   
   * - tool_coord
     - DOUBLE_6
     - Aktuelle Werkzeugpose relativ zum Endeffektor
   
   * - wobj_coord
     - DOUBLE_6
     - Aktuelle Werkstückpose relativ zur Basis
   
   * - exTool_coord
     - DOUBLE_6
     - Aktuelle externe Werkzeugpose relativ zum Werkzeug
   
   * - exAxis_coord
     - DOUBLE_6
     - Aktuelle externe Achspose relativ zum Basiskoordinatensystem
   
   * - robot_state
     - UINT8
     - | Roboter-Betriebsstatus,
       | 1. Gestoppt; 2. In Bewegung; 3. Pausiert; 4. Ziehen
   
   * - actual_flange_pos
     - DOUBLE_6
     - Tatsächliche Endeffektor-Pose
   
   * - target_TCP_cmpvel
     - DOUBLE_2
     - TCP-Befehlslineare und -winkelgeschwindigkeit, Einheit mm/s, °/s
   
   * - actual_TCP_cmpvel
     - DOUBLE_2
     - TCP tatsächliche lineare und winkelgeschwindigkeit, Einheit mm/s, °/s
   
   * - tool_id
     - INT32
     - Werkzeugnummer
   
   * - wobj_id
     - INT32
     - Werkstücknummer
   
   * - ft_sensor_raw_data
     - DOUBLE_6
     - Endeffektor-Kraft/Drehmoment - Rohdaten im Sensorkoordinatensystem
   
   * - ft_sensor_active
     - UINT8
     - Kraft/Drehmoment-Sensor-Aktivierungsstatus
   
   * - gripper_motion_done
     - UINT8
     - Greiferbewegung abgeschlossen
   
   * - collision_state
     - UINT8
     - Kollisionserkennungsstatus
   
   * - trajectory_pnum
     - INT32
     - Aktuelle Sequenznummer der diskreten Punktbewegung
   
   * - safety_stop0_state
     - UINT8
     - Sicherheitsstopp SI0-Signalstatus
   
   * - safety_stop1_state
     - UINT8
     - Sicherheitsstopp SI1-Signalstatus
   
   * - gripper_fault_id
     - UINT8
     - Fehlerhafte Greifernummer
   
   * - gripper_fault
     - INT32
     - Greifer-Fehlernummer
   
   * - ext_DI_state
     - UINT8_16
     - Erweiterte DI
   
   * - ext_DO_state
     - UINT8_16
     - Erweiterte DO
   
   * - ext_AI_state
     - INT32_4
     - Erweiterte AI
   
   * - ext_AO_state
     - INT32_4
     - Erweiterte AO
   
   * - rbt_enable_state
     - INT32
     - Treiber-Aktivierungsabschlussstatus
   
   * - joint_driver_torque
     - DOUBLE_6
     - Tatsächliche Drehmomentwerte der Gelenke j1-j6, Einheit Nm
   
   * - robot_time
     - INT32_7
     - Robotersystemzeit, Jahr, Monat, Tag, Stunde, Minute, Sekunde, Millisekunde
   
   * - software_upgrade_state
     - INT32
     - Roboter-Software-Upgrade-Status
   
   * - end_lua_err_code
     - INT32
     - Endtasten-Signalstatus
   
   * - wide_voltage_ctrl_box_temp
     - DOUBLE
     - Weitspannungs-Steuerkastentemperatur, Einheit °
   
   * - wide_voltage_ctrl_box_fan_current
     - INT32
     - Weitspannungs-Steuerkasten-Lüfterstrom
   
   * - last_servoJ_target
     - DOUBLE_6
     - Letzter servoJ-Zielbefehlspose
   
   * - servoJ_cmd_num
     - INT32
     - servoJ-Befehlszähler
   
   * - strange_pos_flag
     - UINT8
     - Singuläre Posenkennzeichnung
   
   * - alarm
     - UINT8
     - | Warnung, 0-keine Warnung,
       | 1-Schultergelenkkonfigurationsänderung,
       | 2-Ellbogengelenkkonfigurationsänderung,
       | 3-Handgelenkkonfigurationsänderung,
       | 4-RPY-Initialisierung fehlgeschlagen,
       | 5-WaitDI-Wartezeitüberschreitung,
       | 6-WaitAI-Wartezeitüberschreitung,
       | 7-WaitToolDI-Wartezeitüberschreitung,
       | 8-WaitToolAI-Wartezeitüberschreitung,
       | 9-Lichtbogenstart-Erfolg DI nicht konfiguriert,
       | 10-WaitAuxDI-Wartezeitüberschreitung,
       | 11-WaitAuxAI-Wartezeitüberschreitung,
       | 12-Unerreichbarer Punkt in der Pendelbahn,
       | 13-Förderbandverfolgung Greifpunktberechnung fehlgeschlagen,
       | 14-Gelenkdrehmomentsensor-Datenanomalie
   
   * - dr_alarm
     - UINT8
     - | Treiberwarnung, 0-keine Warnung,
       | 1-Achse 1 Treiberwarnung, zurücksetzbar,
       | 2-Achse 2 Treiberwarnung, zurücksetzbar,
       | 3-Achse 3 Treiberwarnung, zurücksetzbar,
       | 4-Achse 4 Treiberwarnung, zurücksetzbar,
       | 5-Achse 5 Treiberwarnung, zurücksetzbar,
       | 6-Achse 6 Treiberwarnung, zurücksetzbar
   
   * - alive_slave_num_error
     - UINT8
     - Aktiver Slave-Anzahlfehler, 0-kein Fehler, 1-Fehler, nicht zurücksetzbar
   
   * - slave_com_error
     - UINT8_8
     - | Slave-Kommunikationsfehler, 0-kein Fehler,
       | 1-Slave offline,
       | 2-Slave-Status stimmt nicht mit eingestelltem Wert überein,
       | 3-Slave nicht konfiguriert,
       | 4-Slave-Konfigurationsfehler,
       | 5-Slave-Initialisierungsfehler,
       | 6-Slave-Mailbox-Kommunikationsinitialisierungsfehler
   
   * - cmd_point_error
     - UINT8
     - | Befehlspunktfehler, 0-kein Fehler,
       | 1-Gelenkbefehlspunktfehler,
       | 2-Linearer Zielpunktfehler,
       | 3-Bogen-Zwischenpunktfehler,
       | 4-Bogen-Zielpunktfehler,
       | 5-Bogen-Befehlspunktabstand zu klein,
       | 6-Vollkreis/Helix Zwischenpunkt 1 Fehler,
       | 7-Vollkreis/Helix Zwischenpunkt 2 Fehler,
       | 8-Vollkreis/Helix Zwischenpunkt 3 Fehler,
       | 9-Vollkreis/Helix Befehlspunktabstand zu klein,
       | 10-TPD-Befehlspunktfehler,
       | 11-TPD-Befehlswerkzeug stimmt nicht mit aktuellem Werkzeug überein,
       | 12-TPD aktueller Befehl und nächster Befehl Startpunktabweichung zu groß,
       | 13-Interner/externer Werkzeugwechsel Fehler,
       | 14-Neuer Helix-Startpunktfehler,
       | 15-Neuer Spline-Kurven-Befehlspunktfehler,
       | 17-PTP-Gelenkbefehl außerhalb des Grenzwerts,
       | 18-TPD-Gelenkbefehl außerhalb des Grenzwerts,
       | 19-LIN\ARC gesendeter Gelenkbefehl außerhalb des Grenzwerts,
       | 20-Befehlsübergeschwindigkeit im kartesischen Raum,
       | 21-Drehmomentbefehl im Gelenkraum außerhalb des Grenzwerts,
       | 22-JOG-Gelenkbefehl außerhalb des Grenzwerts,
       | 23-Achse 1 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 24-Achse 2 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 25-Achse 3 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 26-Achse 4 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 27-Achse 5 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 28-Achse 6 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 29-Gelenkrückmeldegeschwindigkeit außerhalb des Grenzwerts,
       | 30-Gelenkbefehl und Rückmeldungsabweichung zu groß,
       | 31-DMP-Zielpunktfehler (einschließlich Werkzeugkonflikt),
       | 32-TCP-Geschwindigkeit außerhalb des Grenzwerts,
       | 33-Nächster Befehl Gelenkkonfigurationsänderung,
       | 34-Aktueller Befehl Gelenkkonfigurationsänderung,
       | 35-Gelenkgeschwindigkeit in LIN-Befehl außerhalb des Grenzwerts,
       | 36-LIN-Befehl adaptive Geschwindigkeit überschreitet Schwellwert,
       | 37-Unerreichbarer Punkt in der Bahn,
       | 38-Unerreichbarer Punkt in der Bahn - singuläre Pose,
       | 49-PTP- und SPTP-Befehle zwischen ARCSTART und ARCEND nicht erlaubt,
       | 50-PTP- und SPTP-Befehle zwischen WEAVESTART und WEAVEEND nicht erlaubt,
       | 51-Pendelschweißparameter Fehler,
       | 52-Pendelschweiß-Befehlspunktabstand zu klein,
       | 53-Unerreichbarer Punkt in der Pendelbahn - singuläre Pose,
       | 54-Unerreichbarer Punkt in der Pendelbahn - Gelenkbefehl außerhalb des Grenzwerts,
       | 55-Unerreichbarer Punkt in der Pendelbahn - Planungsausnahme (Werkzeug Z stimmt mit Vorwärtsrichtung X Winkel überein),
       | 56-Unerreichbarer Punkt in der Pendelbahn - Planungsausnahme (Bogenbahnpunkt Fehler),
       | 65-Lasersensorbefehl Abweichung zu groß,
       | 66-Lasersensorbefehl unterbrochen, Schweißnahtverfolgung vorzeitig beendet,
       | 81-Externe Achse Befehlgeschwindigkeit außerhalb des Grenzwerts,
       | 82-Externe Achse Befehl und Rückmeldungsabweichung zu groß,
       | 83-Erweitertes Peripheriegerät (externe Achse/IO) Kommunikation unterbrochen,
       | 84-Erweitertes Peripheriegerät (externe Achse/IO) Kommunikationspaketverlust-Ausnahme,
       | 85-Externe Achse 1 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 86-Externe Achse 2 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 87-Externe Achse 3 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 88-Externe Achse 4 Befehlgeschwindigkeit im Gelenkraum außerhalb des Grenzwerts,
       | 89-Erweitertes Peripheriegerät (externe Achse/IO) Ethercat-Kommunikationsfehler,
       | 90-Erweitertes Peripheriegerät (externe Achse/IO) Canopen-Kommunikationsfehler,
       | 97-Förderbandverfolgung - Startpunkt und Referenzpunkt Haltungsänderung zu groß,
       | 113-Konstantkraftregelung - X-Richtung überschreitet maximalen Verstellweg,
       | 114-Konstantkraftregelung - Y-Richtung überschreitet maximalen Verstellweg,
       | 115-Konstantkraftregelung - Z-Richtung überschreitet maximalen Verstellweg,
       | 116-Konstantkraftregelung - RX-Richtung überschreitet maximalen Verstellwinkel,
       | 117-Konstantkraftregelung - RY-Richtung überschreitet maximalen Verstellwinkel,
       | 118-Konstantkraftregelung - RZ-Richtung überschreitet maximalen Verstellwinkel,
       | 119-Externer Sensordatenfehler,
       | 120-Schraubenförmige Suchbewegung fehlgeschlagen,
       | 121-Dreheinfügebewegung fehlgeschlagen,
       | 122-Lineare Einführbewegung fehlgeschlagen,
       | 123-Oberflächenpositionierungsbewegung fehlgeschlagen,
       | 124-Ziehkraft abnormal, Ziehen fehlgeschlagen,
       | 129-Maximale Drehmomentaufzeichnungspunkte überschritten,
       | 130-Geschwindigkeitswechsel Fehler,
       | 131-Werkzeugrichtung außerhalb des Grenzwerts,
       | 132-Impuls außerhalb des Grenzwerts,
       | 133-Leistung außerhalb des Grenzwerts,
       | 134-STL-Flash-Diagnoseanomalie,
       | 135-STL-RAM-Diagnoseanomalie,
       | 136-STL-CPU-Diagnoseanomalie,
       | 137-Sicherheitsplatine II-ECAT Sicherheitsdatenanomalie,
       | 138-Achse 1 ECAT Sicherheitsdatenanomalie,
       | 139-Achse 2 ECAT Sicherheitsdatenanomalie,
       | 140-Achse 3 ECAT Sicherheitsdatenanomalie,
       | 141-Achse 4 ECAT Sicherheitsdatenanomalie,
       | 142-Achse 5 ECAT Sicherheitsdatenanomalie,
       | 143-Achse 6 ECAT Sicherheitsdatenanomalie,
       | 145-Kommunikationsanomalie zwischen Sicherheitsplatine und Controller,
       | 147-Fokusverfolgungsfehler,
       | 148-Winkelgeschwindigkeit außerhalb des Grenzwerts,
       | 149-Gelenkstatuswort-Rückmeldeanomalie
   
   * - IO_error
     - UINT8
     - | IO-Fehler, 0-kein Fehler,
       | 1-Kanal Fehler, zurücksetzbar,
       | 2-Wert Fehler, zurücksetzbar,
       | 3-WaitDI Wartezeitüberschreitung, zurücksetzbar,
       | 4-WaitAI Wartezeitüberschreitung, zurücksetzbar,
       | 5-WaitAxleDI Wartezeitüberschreitung, zurücksetzbar,
       | 6-WaitAxleAI Wartezeitüberschreitung, zurücksetzbar,
       | 7-Kanal konfigurierte Funktionsfehler, zurücksetzbar,
       | 8-Lichtbogenstart Zeitüberschreitung, zurücksetzbar,
       | 9-Lichtbogenende Zeitüberschreitung, zurücksetzbar,
       | 10-Suchzeitüberschreitung, zurücksetzbar,
       | 11-Förderband IO-Erkennungszeitüberschreitung, zurücksetzbar,
       | 12-WaitAuxDI Wartezeitüberschreitung, zurücksetzbar,
       | 13-WaitAuxAI Wartezeitüberschreitung, zurücksetzbar,
       | 14-Drahtsuchzeitüberschreitung, zurücksetzbar
   
   * - gripper_error
     - UINT8
     - Greiferfehler, 0-kein Fehler, 1-Greiferbewegungszeitüberschreitungsfehler, zurücksetzbar
   
   * - file_error
     - UINT8
     - | Konfigurationsdateifehler, 0-kein Fehler,
       | 1-zbt Konfigurationsdatei Versionsfehler, Initialisierungsfehler - nicht zurücksetzbar,
       | 2-zbt Konfigurationsdatei Laden fehlgeschlagen, Initialisierungsfehler - nicht zurücksetzbar,
       | 3-user Konfigurationsdatei Versionsfehler, Initialisierungsfehler - nicht zurücksetzbar,
       | 4-user Konfigurationsdatei Laden fehlgeschlagen, Initialisierungsfehler - nicht zurücksetzbar,
       | 5-exaxis Konfigurationsdatei Versionsfehler, Initialisierungsfehler - nicht zurücksetzbar,
       | 6-exaxis Konfigurationsdatei Laden fehlgeschlagen, Initialisierungsfehler - nicht zurücksetzbar,
       | 7-Robotermodell stimmt nicht überein, Neukonfiguration erforderlich - nicht zurücksetzbar,
       | 8-dhpara Konfigurationsdatei Versionsfehler, Initialisierungsfehler - nicht zurücksetzbar,
       | 9-dhpara Konfigurationsdatei Laden fehlgeschlagen, Initialisierungsfehler - nicht zurücksetzbar,
       | 10-Robotermodell nicht festgelegt - nicht zurücksetzbar,
       | 11-load Konfigurationsdatei Versionsfehler, Initialisierungsfehler - nicht zurücksetzbar,
       | 12-load Konfigurationsdatei Laden fehlgeschlagen, Initialisierungsfehler - nicht zurücksetzbar,
       | 13-speed Konfigurationsdatei Versionsfehler, Initialisierungsfehler - nicht zurücksetzbar,
       | 14-speed Konfigurationsdatei Laden fehlgeschlagen, Initialisierungsfehler - nicht zurücksetzbar,
       | 15-weavepara Konfigurationsdatei Versionsfehler, Initialisierungsfehler - nicht zurücksetzbar,
       | 16-weavepara Konfigurationsdatei Laden fehlgeschlagen, Initialisierungsfehler - nicht zurücksetzbar
   
   * - para_error
     - UINT8
     - | Konfigurationsparameterfehler, 0-kein Fehler,
       | 1-Werkzeugnummer außerhalb des Grenzwerts - zurücksetzbar,
       | 2-Positionierungsabschlussschwellenwert Fehler - zurücksetzbar,
       | 3-Kollisionsstufenfehler - zurücksetzbar,
       | 4-Lastgewichtsfehler - zurücksetzbar,
       | 5-Lastschwerpunkt X Fehler - zurücksetzbar,
       | 6-Lastschwerpunkt Y Fehler - zurücksetzbar,
       | 7-Lastschwerpunkt Z Fehler - zurücksetzbar,
       | 8-DI-Filterzeitfehler - zurücksetzbar,
       | 9-AxleDI-Filterzeitfehler - zurücksetzbar,
       | 10-AI-Filterzeitfehler - zurücksetzbar,
       | 11-AxleAI-Filterzeitfehler - zurücksetzbar,
       | 12-DI High/Low-Pegelbereichsfehler - zurücksetzbar,
       | 13-DO High/Low-Pegelbereichsfehler - zurücksetzbar,
       | 14-Werkstücknummer außerhalb des Grenzwerts - zurücksetzbar,
       | 15-Externe Achsennummer außerhalb des Grenzwerts - zurücksetzbar,
       | 16-Förderbandverfolgung - Encoderkanalfehler - zurücksetzbar,
       | 17-Förderbandverfolgung - Werkstückachsennummer Fehler - zurücksetzbar,
       | 18-FR30L Montageart - Nicht-Standardmontage Fehler - zurücksetzbar
   
   * - exaxis_out_slimit_error
     - UINT8
     - | Externe Achse Weichgrenzfehler, 0-kein Fehler,
       | 1-Externe Achse 1 außerhalb der Weichgrenze, zurücksetzbar,
       | 2-Externe Achse 2 außerhalb der Weichgrenze, zurücksetzbar,
       | 3-Externe Achse 3 außerhalb der Weichgrenze, zurücksetzbar,
       | 4-Externe Achse 4 außerhalb der Weichgrenze, zurücksetzbar,
       | 5-Externe Achse 5 außerhalb der Weichgrenze, zurücksetzbar,
       | 6-Externe Achse 6 außerhalb der Weichgrenze, zurücksetzbar
   
   * - dr_com_err
     - UINT8_6
     - Treiberkommunikationsfehler, 0-kein Fehler, 1-Fehler
   
   * - dr_err
     - UINT8
     - | Treiberfehler, 0-kein Fehler,
       | 1-Achse 1 Treiberfehler, nicht zurücksetzbar,
       | 2-Achse 2 Treiberfehler, nicht zurücksetzbar,
       | 3-Achse 3 Treiberfehler, nicht zurücksetzbar,
       | 4-Achse 4 Treiberfehler, nicht zurücksetzbar,
       | 5-Achse 5 Treiberfehler, nicht zurücksetzbar,
       | 6-Achse 6 Treiberfehler, nicht zurücksetzbar
   
   * - out_sflimit_err
     - UINT8
     - | Weichgrenzfehler, 0-kein Fehler,
       | 1-Achse 1 außerhalb der Weichgrenze, zurücksetzbar,
       | 2-Achse 2 außerhalb der Weichgrenze, zurücksetzbar,
       | 3-Achse 3 außerhalb der Weichgrenze, zurücksetzbar,
       | 4-Achse 4 außerhalb der Weichgrenze, zurücksetzbar,
       | 5-Achse 5 außerhalb der Weichgrenze, zurücksetzbar,
       | 6-Achse 6 außerhalb der Weichgrenze, zurücksetzbar

.. centered:: Tabelle 1-2 Funktionen der Roboter-Eingangssteuerungskonfiguration

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Name**
     - **Datentyp**
     - **Beschreibung**

   * - speed_mask
     - UINT8
     - Maske für globale Geschwindigkeitseinstellung: 0 = unwirksam; 1 = wirksam

   * - speed
     - UINT8
     - Globale Geschwindigkeit einstellen (0-100)

   * - std_DO_mask
     - UINT8
     - Steuermaske für Standard-DO-Ausgang des Steuerkastens (Bit0 ~ Bit7 entsprechen DO0 ~ DO7)

   * - std_DO_box
     - UINT8
     - Standard-DO-Ausgang des Steuerkastens (Bit0 ~ Bit7 entsprechen DO0 ~ DO7)

   * - cfg_DO_mask
     - UINT8
     - Steuermaske für konfigurierbaren CO-Ausgang des Steuerkastens (Bit0 ~ Bit7 entsprechen CO0 ~ CO7)

   * - cfg_DO_box
     - UINT8
     - Konfigurierbarer CO-Ausgang des Steuerkastens (Bit0 ~ Bit7 entsprechen CO0 ~ CO7)

   * - cfg_DO_tool_mask
     - UINT8
     - Steuermaske für Standard-Werkzeug-DO-Ausgang des Steuerkastens (Bit0 ~ Bit1 entsprechen toolDO0 ~ toolDO1)

   * - cfg_DO_tool
     - UINT8
     - Standard-Werkzeug-DO-Ausgang des Steuerkastens (Bit0 ~ Bit1 entsprechen toolDO0 ~ toolDO1)

   * - std_AO_mask
     - UINT8
     - Steuermaske für Analogausgänge des Roboters (Bit0 ~ Bit1 entsprechen Steuerkasten AO0 ~ AO1; Bit2 entspricht Werkzeug AO0)

   * - std_AO0_box
     - DOUBLE
     - Analogausgang AO0 des Steuerkastens (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Analogausgang AO1 des Steuerkastens (0.0 ~ 4095.0)

   * - std_AO0_tool
     - DOUBLE
     - Werkzeug-Analogausgang AO1 (0.0 ~ 4095.0)

   * - input_BIT_reg_8xX
     - UINT8_X
     - BIT-Typ Roboter-Eingangsregister (8xX gibt die Anzahl der Register an. Wenn Sie 16 BIT-Eingangsregister benötigen, lautet der tatsächliche Name: "input_BIT_reg_8x2". Der Roboter unterstützt maximal 128 BIT-Register.)

   * - input_INT_reg_X
     - INT32_X
     - INT-Typ Roboter-Eingangsregister (X gibt die Anzahl der Register an. Wenn Sie 16 INT-Eingangsregister benötigen, lautet der tatsächliche Name: "input_INT_reg_16". Der Roboter unterstützt maximal 64 INT-Register.)
  
   * - input_DOUBLE_reg_X
     - DOUBLE_X
     - DOUBLE-Typ Roboter-Eingangsregister (X gibt die Anzahl der Register an. Wenn Sie 16 DOUBLE-Eingangsregister benötigen, lautet der tatsächliche Name: "input_DOUBLE_reg_16". Der Roboter unterstützt maximal 64 DOUBLE-Register.)

.. centered:: Tabelle 1-3 Entsprechung von Datentypen und Bytelängen

.. list-table::
   :widths: 60 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Datentyp**
     - **Bytelänge**

   * - UINT8
     - 1

   * - INT32
     - 4

   * - DOUBLE
     - 8

   * - UINT8_X
     - 1*X

   * - INT32_X
     - 4*X

   * - DOUBLE_X
     - 8*X