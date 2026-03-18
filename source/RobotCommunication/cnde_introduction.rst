CNDE-Einführung
===============

Das konfigurierbare Netzwerkdatenaustauschprotokoll für kollaborative Roboter (im Folgenden als CNDE bezeichnet) ist eine Methode, mit der ein Client über UDP-Kommunikation den Roboter steuern und seinen Rückmeldestatus abrufen kann.

Tabelle 1-1 zeigt die vollständige Sammlung aller Roboterzustände, die über CNDE abgerufen werden können. Der Client kann eine beliebige Anzahl benötigter Zustände aus der Tabelle auswählen und den Roboter veranlassen, diese Zustände gemäß dem eingestellten Rückmeldezyklus zurückzumelden.

Ebenso kann der Client aus Tabelle 1-2 die benötigten Kombinationen von Robotersteuerungsfunktionen auswählen, um Steuerungsoperationen durchzuführen. Die Kommunikationsdaten zwischen Client und Roboter-CNDE müssen dem angegebenen Frame-Format entsprechen. Der Kommunikationsport des Roboter-CNDE ist 20006.

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

   * - ft_sensor_data
     - DOUBLE_6
     - Kraftsensordaten

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