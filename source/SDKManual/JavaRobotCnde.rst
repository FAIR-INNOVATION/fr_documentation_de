CNDE
=============

.. toctree:: 
    :maxdepth: 5

Roboterstatus-Feedback konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Roboterstatus-Feedback konfigurieren
    * @param state Liste der Roboterstatus-Enums
    * @param period Status-Feedback-Periode, Bereich 8-1000
    * @return Fehlercode, 0-normal, 4-Parameterfehler, 18-Statusfeld existiert nicht, 20-Gesamtbytes überschreiten 4K
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> state, int period)
    
Einen Roboterstatus zur CNDE-Statuskonfiguration hinzufügen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Einen Roboterstatus zur Konfigurationsliste hinzufügen
    * @param state Roboterstatus-Enum
    * @return Fehlercode, 0-normal, 17-Status existiert bereits, 18-Statusfeld existiert nicht, 20-überschreitet 4K
    */
    public int AddRobotRealtimeState(RobotState state)
    
Einen Roboterstatus aus der CNDE-Statuskonfiguration löschen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Einen Roboterstatus aus der Konfigurationsliste löschen
    * @param state Roboterstatus-Enum
    * @return Fehlercode, 0-normal, 18-Status existiert nicht, 19-wenigstens ein Status muss verbleiben
    */
    public int DeleteRobotRealtimeState(RobotState state)
        
CNDE-Status-Feedback-Periode festlegen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief CNDE-Status-Feedback-Periode festlegen
    * @param period Status-Feedback-Periode, Bereich 8-1000
    * @return Fehlercode, 0-normal, 4-Parameterfehler
    */
    public int SetRobotRealtimeStatePeriod(int period)
            
Aktuelle CNDE-Status-Feedback-Statusmenge und -Periode abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Alle aktuellen Statusmengen und die Periode abrufen
     * @return Konfigurationsergebnisstruktur mit Statusliste und Periode
    */
    public StateConfigResult GetRobotRealtimeStateConfig()
                
CNDE-Status-Feedback-Anwendungscodebeispiel
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Beispiel für die Verwendung der CNDE-Echtzeitstatus-Konfigurationsschnittstelle
    */
    public static void TestRealtimeStateConfig(Robot robot)
    {
        
        // 1. Erste Statusliste erstellen
        List<RobotState> stateList1 = new ArrayList<>();
        stateList1.add(RobotState.ProgramState);
        stateList1.add(RobotState.RobotState);
        stateList1.add(RobotState.JointCurPos);
        stateList1.add(RobotState.ToolCurPos);
        
        // 2. Erster Aufruf von SetRobotRealtimeStateConfig zur Konfiguration von Status und Periode
        int period1 = 100;  // 100ms Periode
        int rtn = robot.SetRobotRealtimeStateConfig(stateList1, period1);
        System.out.printf("1. SetRobotRealtimeStateConfig (erste Liste, Periode=%d) rtn: %d%n", period1, rtn);
        
        if (rtn == 0) {
            // 3. Zusätzlichen Status hinzufügen
            rtn = robot.AddRobotRealtimeState(RobotState.RobotTime);
            System.out.printf("2. AddRobotRealtimeState (RobotTime) rtn: %d%n", rtn);
            
            // 4. SetRobotRealtimeStateConfig erneut aufrufen zur Neukonfiguration (andere Statusliste)
            List<RobotState> stateList2 = new ArrayList<>();
            stateList2.add(RobotState.ProgramState);
            stateList2.add(RobotState.RobotState);
            stateList2.add(RobotState.MainCode);
            stateList2.add(RobotState.SubCode);
            stateList2.add(RobotState.JointCurPos);
            stateList2.add(RobotState.ToolCurPos);
            stateList2.add(RobotState.ActualJointTorque);
            
            int period2 = 50;  // 50ms Periode
            rtn = robot.SetRobotRealtimeStateConfig(stateList2, period2);
            System.out.printf("3. SetRobotRealtimeStateConfig (aktualisierte Liste, Periode=%d) rtn: %d%n", period2, rtn);
            
            // 5. Periode ändern
            int newPeriod = 80;  // 80ms Periode
            rtn = robot.SetRobotRealtimeStatePeriod(newPeriod);
            System.out.printf("4. SetRobotRealtimeStatePeriod (Periode=%d) rtn: %d%n", newPeriod, rtn);
            
            // 6. Aktuelle Konfiguration abrufen und ausgeben
            Robot.StateConfigResult configResult = robot.GetRobotRealtimeStateConfig();
            System.out.println("5. GetRobotRealtimeStateConfig Ergebnis:");
            System.out.printf("   - Periode: %d ms%n", configResult.period);
            System.out.println("   - Konfigurierte Status:");
            for (int i = 0; i < configResult.stateList.size(); i++) {
                System.out.printf("     [%d] %s%n", i, configResult.stateList.get(i));
            }
            
            rtn = robot.RPC("192.168.58.2");
            if (rtn == 0) {
                System.out.println("RPC-Verbindung erfolgreich");
            } else {
                System.out.println("RPC-Verbindung fehlgeschlagen");
                return;
            }
            // Auf CNDE-Verbindungsaufbau warten
            System.out.println("Warte auf CNDE-Verbindungsaufbau...");
            while (robot.CNDEGetStateData() == null) {
                robot.Sleep(100);
            }
            System.out.println("CNDE-Verbindung hergestellt, Datenempfang beginnt...");

            // 7. Schleife zum Lesen des Echtzeitstatus zur Überprüfung der Konfiguration
            System.out.println("6. Lese Echtzeitstatus...");
            while(true) {
                robot.Sleep(1000);
                // Statusdaten über CNDE abrufen
                ROBOT_STATE_PKG pkg = robot.CNDEGetStateData();
                if (pkg == null) {
                    System.out.println("Statusdaten sind null, CNDE-Verbindung getrennt, warte auf Wiederverbindung");
                    continue;  // Schleife bei getrennter Verbindung fortsetzen, auf Wiederverbindung warten
                }
                System.out.println("\n--- Roboterzeit ---");
                if (pkg.robotTime != null) {
                    System.out.println("robotTime: " + pkg.robotTime.year + "-" + pkg.robotTime.month + "-" + pkg.robotTime.day +
                            " " + pkg.robotTime.hour + ":" + pkg.robotTime.minute + ":" + pkg.robotTime.second +
                            "." + pkg.robotTime.millisecond);
                }

                System.out.println("   --- Statusinformationen ---");
                System.out.printf("   program_state: %d%n", pkg.program_state);
                System.out.printf("   robot_state: %d%n", pkg.robot_state);
                System.out.printf("   main_code: %d%n", pkg.main_code);
                System.out.printf("   sub_code: %d%n", pkg.sub_code);
                System.out.println("   --- Gelenkpositionen (actual_joint_pos) ---");
                System.out.printf("   jt_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[0], pkg.jt_cur_pos[1], pkg.jt_cur_pos[2]);
                System.out.printf("   jt_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[3], pkg.jt_cur_pos[4], pkg.jt_cur_pos[5]);
                System.out.println("   --- TCP-Positionen (actual_TCP_pos) ---");
                System.out.printf("   tl_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2]);
                System.out.printf("   tl_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[3], pkg.tl_cur_pos[4], pkg.tl_cur_pos[5]);
                System.out.println("   --- Gelenkmomente (actual_joint_torque) ---");
                System.out.printf("   jt_cur_tor[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[0], pkg.jt_cur_tor[1], pkg.jt_cur_tor[2]);
                System.out.printf("   jt_cur_tor[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[3], pkg.jt_cur_tor[4], pkg.jt_cur_tor[5]);
                robot.Sleep(500);
            }
        } else {
            System.out.printf("SetRobotRealtimeStateConfig fehlgeschlagen mit Fehler: %d%n", rtn);
        }
    }