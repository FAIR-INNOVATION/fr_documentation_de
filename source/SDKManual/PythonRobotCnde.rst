CNDE
=============

.. toctree:: 
    :maxdepth: 5

CNDE-Statusrückmeldung des Roboters konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotRealtimeStateConfig(states: List[RobotState], period: int = 500) -> int:``"
    "Beschreibung", "CNDE-Standardkonfiguration setzen (vor der RPC-Verbindung aufrufen)"
    "Erforderliche Parameter", "
    - ``states``: Liste von RobotState-Enums
    - ``period``: Datenperiode (ms), Bereich 8-1000, Standard 8ms
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode"

Roboterstatus zur CNDE-Statuskonfiguration hinzufügen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AddRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Beschreibung", "CNDE-Statusliste basierend auf bestehender Konfiguration hinzufügen (unterstützt dynamische Wartung und IP-Isolierung)"
    "Erforderliche Parameter", "
    - ``states``: Liste von RobotState-Enums, hinzuzufügende Zustände
    - ``ip``: Optional, Roboter-IP angeben (für isolierte Konfiguration bei mehreren Robotern; wenn nicht angegeben, wird globale Konfiguration geändert)
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode"

Roboterstatus aus CNDE-Statuskonfiguration löschen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``DeleteRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Beschreibung", "CNDE-Statusliste basierend auf bestehender Konfiguration löschen (unterstützt dynamische Wartung und IP-Isolierung)"
    "Erforderliche Parameter", "
    - ``states``: Liste von RobotState-Enums, zu löschende Zustände
    - ``ip``: Optional, Roboter-IP angeben (für isolierte Konfiguration bei mehreren Robotern; wenn nicht angegeben, wird globale Konfiguration geändert)
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode"

CNDE-Statusrückmeldeperiode festlegen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotRealtimeStatePeriod(period: int, ip: str = None) -> int:``"
    "Beschreibung", "CNDE-Statusrückmeldeperiode festlegen (unterstützt globale oder IP-isolierte Konfiguration)"
    "Erforderliche Parameter", "
    - ``period``: Datenperiode (ms), Bereich 8-1000
    - ``ip``: Optional, Roboter-IP angeben (wenn nicht angegeben, wird globale Konfiguration geändert)
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode"

Aktuelle CNDE-Statusrückmeldung alle Zustandssätze abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CNDEGetConfig(self) -> tuple:``"
    "Beschreibung", "Alle aktuellen Zustandssätze abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode Erfolg-0 Fehler-errcode Konfigurationsergebnisstruktur mit Zustandsliste"

CNDE-Statusrückmeldung Anwendungscodebeispiel
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    from fairino.Robot import RobotState, SetRobotRealtimeStateConfig, DEFAULT_CNDE_STATES, AddRobotRealtimeState, DeleteRobotRealtimeState, SetRobotRealtimeStatePeriod
    import time

    # ==================== Globale Konfigurationsparameter ====================
    ROBOT_IP = '192.168.58.2'       # Roboter-IP-Adresse
    # ========== Test1: CNDE-Konfigurations- und Datenabruftest =============
    # Tests
    # 1. CNDE-Konfiguration setzen (JointCurPos, ToolCurPos, 20ms Periode)
    # 2. RPC-Verbindung herstellen
    # 3. Roboter-Gelenk- und TCP-Posendaten ausgeben
    # 4. Zeitstempel abrufen und Periode validieren
    # 5. Konfiguration ändern (RobotMode, RbtEnableState, 10ms Periode)
    # 6. Überprüfen, ob neue Konfiguration wirksam ist

    def test1_cnde_config_and_data():
        """Test1: CNDE-Konfigurations- und Datenabruftest - Konfigurationseinstellungen und Echtzeitdaten validieren"""
        print_separator("Test1: CNDE-Konfigurations- und Datenabruftest")

        # ===== Schritt 1: CNDE-Konfiguration setzen (JointCurPos, ToolCurPos, 20ms) =====
        print("\n[Schritt 1] CNDE-Konfiguration wird gesetzt...")
        print("  Konfigurationsfelder: JointCurPos, ToolCurPos")
        print("  Rückmeldeperiode: 20ms")

        custom_states = [
            RobotState.JointCurPos,   # Aktuelle Gelenkposition
            RobotState.ToolCurPos,    # Aktuelle Werkzeugposition (TCP)
        ]

        rtn = SetRobotRealtimeStateConfig(custom_states, 20)
        if rtn != 0:
            print(f"✗ Konfigurationseinstellung fehlgeschlagen, Fehlercode: {rtn}")
            return None
        print("✓ CNDE-Konfiguration erfolgreich gesetzt")

        # ===== Schritt 2: RPC-Verbindung herstellen =====
        print(f"\n[Schritt 2] RPC-Verbindung wird hergestellt ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Auf Verbindung und Datenempfang warten

        # Konfiguration validieren
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Verbindung erfolgreich, aktuelle Konfiguration: {len(states)} Felder, Periode {period}ms")
        else:
            print("✗ CNDE-Konfiguration kann nicht abgerufen werden")
            return robot

        # ===== Schritt 3: Roboter-Gelenk- und TCP-Posen ausgeben =====
        print("\n[Schritt 3] Roboter-Gelenk- und TCP-Posen werden ausgegeben...")
        print("  (Hinweis: Roboter ziehen, um Datenänderungen zu beobachten)")
        print("  Drücken Sie Ctrl+C, um die Datenausgabe zu stoppen")
        print("  (Verwenden Sie Wireshark zur Paketerfassung, um die tatsächliche Datenperiode zu validieren)\n")

        sample_count = 0
        try:
            while sample_count < 100:  # 100 Proben sammeln
                pkg = robot.robot_state_pkg

                # Alle 10 Frames ausgeben
                if sample_count % 10 == 0:
                    print(f"--- Probe #{sample_count} ---")
                    print(f"  Gelenkpositionen (deg): [{', '.join([f'{x:.3f}' for x in pkg.jt_cur_pos])}]")
                    print(f"  TCP-Pose (mm/deg): [{', '.join([f'{x:.3f}' for x in pkg.tl_cur_pos])}]")
                    print(f"  Aktuelle Frame-Zählung: {pkg.frame_cnt}")
                    print()

                sample_count += 1
                time.sleep(0.02)  # 20ms

        except KeyboardInterrupt:
            print("\n  Datenausgabe durch Benutzer unterbrochen")

        # Verbindung schließen
        robot.CloseRPC()
        time.sleep(1)

        # ===== Schritt 4: Konfiguration ändern und validieren =====
        print("\n[Schritt 4] CNDE-Konfiguration wird geändert...")
        print("  Neue Konfigurationsfelder: RobotMode, RbtEnableState")
        print("  Neue Rückmeldeperiode: 10ms")

        new_states = [
            RobotState.RobotMode,
            RobotState.RbtEnableState,
        ]

        # Neue Konfiguration setzen
        rtn = SetRobotRealtimeStateConfig(new_states, 10)
        if rtn != 0:
            print(f"✗ Neue Konfigurationseinstellung fehlgeschlagen, Fehlercode: {rtn}")
            return robot
        print("✓ Neue Konfiguration erfolgreich gesetzt")

        # Erneut verbinden
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Neue Konfiguration validieren
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Aktuelle Konfiguration: {[s.name for s in states]}")
            print(f"✓ Aktuelle Periode: {period}ms")

            if period == 10:
                print("✓ Konfigurationsänderungsvalidierung bestanden (Periode auf 10ms geändert)")
            else:
                print(f"⚠ Periode nicht wirksam (erwartet 10ms, tatsächlich {period}ms)")

            # Neue Daten ausgeben
            pkg = robot.robot_state_pkg
            print(f"\n[Neue Konfigurationsdaten]")
            print(f"  robot_mode: {pkg.robot_mode}")
            print(f"  rbtEnableState: {pkg.rbtEnableState}")
        else:
            print("✗ Neue Konfiguration kann nicht abgerufen werden")

        print("\n✓ Test1 abgeschlossen")
        return robot


    if __name__ == "__main__":
        test1_cnde_config_and_data()


    # ======== Test2: Add/Delete Zustandsfeld-Test ====================
    # Funktion: Testet AddRobotRealtimeState() und DeleteRobotRealtimeState()
    # Tests:
    #   1. Verwenden Sie AddRobotRealtimeState(), um SpeedScaleManual und SpeedScaleAuto hinzuzufügen
    #   2. Verbinden Sie sich mit dem Roboter, geben Sie die globale Geschwindigkeit im Hand-/Automatikmodus aus
    #   3. Ändern Sie die globale Geschwindigkeit in der WebApp und beobachten Sie die SDK-Datenänderungen
    #   4. Verwenden Sie DeleteRobotRealtimeState(), um die hinzugefügten Felder zu löschen
    #   5. Verbinden Sie sich erneut und validieren Sie, ob die Geschwindigkeitswerte 0 sind (Felder werden nicht mehr aktualisiert)


    def test2_add_delete_state():
        """Test2: Add/Delete Zustandsfeld-Test - Dynamisches Hinzufügen und Löschen von CNDE-Zuständen validieren"""
        print_separator("Test2: Add/Delete Zustandsfeld-Test")

        # ===== Schritt 1: SpeedScaleManual- und SpeedScaleAuto-Felder hinzufügen =====
        print("\n[Schritt 1] Verwenden von AddRobotRealtimeState() zum Hinzufügen von Geschwindigkeitsskalenfeldern...")
        print("  Hinzugefügte Felder: SpeedScaleManual, SpeedScaleAuto")

        rtn = AddRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Feld hinzufügen fehlgeschlagen, Fehlercode: {rtn}")
            return None
        print("✓ Felder erfolgreich hinzugefügt")

        # ===== Schritt 2: RPC-Verbindung herstellen und Geschwindigkeit ausgeben =====
        print(f"\n[Schritt 2] RPC-Verbindung wird hergestellt ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Auf Verbindung und Datenempfang warten

        # Konfiguration validieren
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Verbindung erfolgreich, aktuelle Konfiguration: {len(states)} Felder")
            # Prüfen, ob die hinzugefügten Felder enthalten sind
            has_manual = RobotState.SpeedScaleManual in states
            has_auto = RobotState.SpeedScaleAuto in states
            if has_manual and has_auto:
                print("✓ Konfigurationsvalidierung bestanden: SpeedScaleManual und SpeedScaleAuto wurden hinzugefügt")
            else:
                print(f"⚠ Konfigurationsvalidierungswarnung: Manual={has_manual}, Auto={has_auto}")
        else:
            print("✗ CNDE-Konfiguration kann nicht abgerufen werden")

        # Geschwindigkeitsdaten ausgeben
        print("\n[Aktuelle Geschwindigkeitsdaten] (Ändern Sie die globale Geschwindigkeit in der WebApp, um Änderungen zu beobachten)")
        print("  Hinweis: Roboter durch Ziehen aktivieren und zwischen Hand-/Automatikmodus wechseln, um Geschwindigkeitswerte zu beobachten")
        print("  Drücken Sie Ctrl+C, um die Datenausgabe zu stoppen\n")

        sample_count = 0
        try:
            while sample_count < 100:  # 100 Proben sammeln (ca. 10 Sekunden bei 100ms Intervall)
                pkg = robot.robot_state_pkg
                print(f"  [{sample_count:3d}] SpeedScaleManual: {pkg.speedScaleManual:.2f}, "
                    f"SpeedScaleAuto: {pkg.speedScaleAuto:.2f}, "
                    f"Mode: {pkg.robot_mode}")
                sample_count += 1
                time.sleep(0.1)  # 100ms Intervall
        except KeyboardInterrupt:
            print("\n  Datenausgabe durch Benutzer unterbrochen")

        print(f"\n✓ Datenerfassung abgeschlossen, insgesamt {sample_count} Proben")

        # ===== Schritt 3: Verbindung trennen =====
        print("\n[Schritt 3] Aktuelle Verbindung wird getrennt...")
        robot.CloseRPC()
        time.sleep(1.0)  # Auf vollständiges Schließen von CNDE warten

        # ===== Schritt 4: Hinzugefügte Felder löschen =====
        print("\n[Schritt 4] Verwenden von DeleteRobotRealtimeState() zum Löschen der Geschwindigkeitsskalenfelder...")
        rtn = DeleteRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Feld löschen fehlgeschlagen, Fehlercode: {rtn}")
            return robot
        print("✓ Felder erfolgreich gelöscht")

        # ===== Schritt 5: Erneut verbinden und validieren, dass die Feldwerte 0 sind =====
        print(f"\n[Schritt 5] Erneutes Verbinden und Validieren der gelöschten Feldwerte...")

        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Geschwindigkeitswerte lesen
        pkg = robot.robot_state_pkg
        manual_speed = pkg.speedScaleManual
        auto_speed = pkg.speedScaleAuto

        print(f"\n  SpeedScaleManual nach Löschung: {manual_speed:.2f}")
        print(f"  SpeedScaleAuto nach Löschung: {auto_speed:.2f}")

        # Prüfen, ob sie 0 sind
        if manual_speed == 0 and auto_speed == 0:
            print("\n✓ Test2-Validierung bestanden: Geschwindigkeitswerte sind 0 nach Feldlöschung")
        else:
            print(f"\n⚠ Test2-Warnung: Geschwindigkeitswerte sind nicht Null nach Feldlöschung")

        print("\n✓ Test2 abgeschlossen")
        return robot

    if __name__ == "__main__":
        test2_add_delete_state()