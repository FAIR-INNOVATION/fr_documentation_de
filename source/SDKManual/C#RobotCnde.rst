CNDE
=================

.. toctree:: 
    :maxdepth: 5

Konfigurieren der CNDE-Datenliste und des Aktualisierungszeitraums des Roboters
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Konfiguriert die Datenliste und den Aktualisierungszeitraum für die Echtzeitstatusrückmeldung des Roboters (überschreibt vorherige Konfiguration)
    * @param [in] states Liste der zu abonnierenden Status-Enums, die Reihenfolge bestimmt die Anordnung im Datenpaket
    * @param [in] period Datenaktualisierungszeitraum, Einheit Millisekunden, Wertebereich [8, 1000]
    * @return Gibt bei Erfolg 0 zurück; bei Fehler einen negativen Fehlercode (z. B. ERR_STATE_INVALID, ERR_PARAM_VALUE usw.)
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> states, int period)

Hinzufügen eines Statuselements zur bestehenden Statusrückmeldeliste
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fügt ein Statuselement zur bestehenden Statusrückmeldeliste hinzu
    * @param [in] state Hinzuzufügender Status-Enum-Wert
    * @return Gibt bei Erfolg 0 zurück; bei Fehler einen negativen Fehlercode (z. B. ERR_STATE_ALREADY_EXISTS, ERR_STATE_INVALID usw.)
    */
    public int AddRobotRealtimeState(RobotState state)
    
Löschen eines Statuselements aus der bestehenden Statusrückmeldeliste
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Löscht ein Statuselement aus der bestehenden Statusrückmeldeliste (mindestens ein Status muss verbleiben)
    * @param [in] state Zu löschender Status-Enum-Wert
    * @return Gibt bei Erfolg 0 zurück; bei Fehler einen negativen Fehlercode (z. B. ERR_STATE_INVALID, ERR_NEED_AT_LEAST_ONE_STATE)
    */
    public int DeleteRobotRealtimeState(RobotState state)
        
Nur den Aktualisierungszeitraum der Statusrückmeldung ändern
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

     /**
    * @brief Ändert nur den Aktualisierungszeitraum der Statusrückmeldung, ohne die Statusliste zu ändern
    * @param [in] period Neuer Aktualisierungszeitraum, Einheit Millisekunden, Wertebereich [8, 1000]
    * @return Gibt bei Erfolg 0 zurück; bei Fehler einen negativen Fehlercode (z. B. ERR_PARAM_VALUE)
    */
    public int SetRobotRealtimeStatePeriod(int period)
        
Abrufen der aktuell konfigurierten Statusrückmeldeliste und des Aktualisierungszeitraums
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ruft die aktuell konfigurierte Statusrückmeldeliste und den Aktualisierungszeitraum ab
    * @param [out] states Gibt die aktuell abonnierte Status-Enum-Liste aus
    * @param [out] period Gibt den aktuellen Datenaktualisierungszeitraum in Millisekunden aus
    * @return Gibt bei Erfolg 0 zurück; bei Fehler einen negativen Fehlercode
    */
    public int GetRobotRealtimeStateConfig(out List<RobotState> states, out int period)

CNDE-Konfigurationsbezogenes SDK-Codebeispiel
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestRobotRealtimeStates()
    {
        // 1. Definieren der zu abonnierenden Statusfelder
        List<RobotState> requiredStates = new List<RobotState>
        {
            RobotState.JointCurPos,
            RobotState.ToolCurPos, 
            RobotState.JointDriverTemperature,
            RobotState.RobotTime,
        };

        // 2. Konfigurieren der Statusrückmeldung (Zeitraum 8ms)
        int periodMs = 8;
        int ret = robot.SetRobotRealtimeStateConfig(requiredStates, periodMs);
        if (ret != 0)
        {
            Console.WriteLine($"Statuskonfiguration fehlgeschlagen, Fehlercode: {ret}");
            return;
        }
        Console.WriteLine($"Statuskonfiguration erfolgreich, {requiredStates.Count} Felder, Zeitraum {periodMs} ms");

        // Überprüfen, ob die Konfiguration wirksam ist
        List<RobotState> actualStates;
        int actualPeriod;
        robot.GetRobotRealtimeStateConfig(out actualStates, out actualPeriod);
        Console.WriteLine($"Tatsächlich aktive Statusanzahl: {actualStates.Count}, Zeitraum: {actualPeriod} ms");
        Thread.Sleep(3000);
        // 3. RPC-Verbindung herstellen (intern automatischer CNDE-Handshake)
        robot.SetReconnectParam(true, 10, 1000);
        ret = robot.RPC("192.168.58.2");  // Entsprechend der tatsächlichen Roboter-IP ändern
        if (ret != 0)
        {
            Console.WriteLine($"RPC-Verbindung fehlgeschlagen, Fehlercode: {ret}");
            return;
        }
        // 4. Schleife zum Lesen und Drucken der Statusdaten
        DateTime startTime = DateTime.Now;
        const int durationSeconds = 500;

        while ((DateTime.Now - startTime).TotalSeconds < durationSeconds)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            ret = robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"GetRobotRealTimeState: {ret}");

            //Gelenkpositionen (Grad)
            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
                Console.WriteLine($"Gelenkpositionen(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");

            //TCP-Pose (mm /°)
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
                Console.WriteLine($"TCP-Pose(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
    
            // Gelenktemperaturen
            if (pkg.jointDriverTemperature != null && pkg.jointDriverTemperature.Length >= 6)
                Console.WriteLine($"Gelenktemperaturen(°C): J1={pkg.jointDriverTemperature[0]:F2}, J2={pkg.jointDriverTemperature[1]:F2}, J3={pkg.jointDriverTemperature[2]:F2}, J4={pkg.jointDriverTemperature[3]:F2}, J5={pkg.jointDriverTemperature[4]:F2}, J6={pkg.jointDriverTemperature[5]:F2}");

            // Roboterzeit
            Console.WriteLine($"Roboterzeit: {pkg.robotTime.year}-{pkg.robotTime.mouth:D2}-{pkg.robotTime.day:D2} {pkg.robotTime.hour:D2}:{pkg.robotTime.minute:D2}:{pkg.robotTime.second:D2}.{pkg.robotTime.millisecond:D3}");

            await Task.Delay(100);
        }

        // 5. Verbindung trennen
        robot.CloseRPC();
    }

CNDE-Hinzufügen/Löschen von Konfigurationsstatus und Einstellen des Kommunikationszeitraums SDK-Codebeispiel
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestAddDeleteCNDE()
    {
        List<RobotState> finalStates;
        int finalPeriod;
        // Anfangskonfiguration: Keinen Status anfordern (Standardkonfiguration)
        List<RobotState> emptyStates = new List<RobotState>();
        int ret = robot.SetRobotRealtimeStateConfig(emptyStates, 20);

        robot.SetRobotRealtimeStatePeriod(10);
        // Zwei Status löschen
        ret = robot.DeleteRobotRealtimeState(RobotState.JointCurPos);
        Console.WriteLine($"Löschen von JointCurPos Ergebnis: {ret}");
        ret = robot.DeleteRobotRealtimeState(RobotState.ToolCurPos);
        Console.WriteLine($"Löschen von ToolCurPos Ergebnis: {ret}");
        // Einen Status hinzufügen
        ret = robot.AddRobotRealtimeState(RobotState.CollisionLevel);
        Console.WriteLine($"Hinzufügen von CollisionLevel Ergebnis: {ret}");

        // Aktuelle Konfigurationsliste abrufen und erneut senden
        List<RobotState> currentStates;
        int currentPeriod;
        robot.GetRobotRealtimeStateConfig(out currentStates, out currentPeriod);
        Console.WriteLine($"Aktuelle Konfigurationsstatusanzahl: {currentStates.Count}");
        ret = robot.SetRobotRealtimeStateConfig(currentStates, currentPeriod);
        Console.WriteLine($"Anwenden der neuen Konfiguration Ergebnis: {ret}"); Console.WriteLine($"Anfangskonfiguration Ergebnis: {ret}");
        robot.GetRobotRealtimeStateConfig(out finalStates, out finalPeriod);
        Console.WriteLine($"Konfigurationsstatusanzahl: {finalStates.Count}");
        foreach (var s in finalStates) Console.WriteLine($"  {s}");
        Console.WriteLine($"Zeitraum: {finalPeriod} ms");

        Thread.Sleep(1000);
        // RPC-Verbindung herstellen (intern automatische CNDE-Verbindung)
        robot.SetReconnectParam(true, 100, 1000);
        ret = robot.RPC("192.168.58.2");
        if (ret != 0)
        {
            Console.WriteLine($"RPC-Verbindung fehlgeschlagen: {ret}");
            return;
        }

        // Schleife zum Drucken der gelöschten und hinzugefügten Status, gelöschte Status werden als 0 gedruckt, hinzugefügte Status können normale Echtzeitwerte abrufen
        DateTime lastTime = DateTime.Now;
        int frameCount = 0;
        DateTime startTime = DateTime.Now;
        while ((DateTime.Now - startTime).TotalSeconds < 10)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.GetRobotRealTimeState(ref pkg);
            DateTime now = DateTime.Now;
            double interval = (now - lastTime).TotalMilliseconds;
            lastTime = now;
            frameCount++;

            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  Gelenkpositionen(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");
            }
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  TCP-Pose(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
            }
            // Kollisionsstufe
            if (pkg.collisionLevel != null && pkg.collisionLevel.Length >= 6)
                Console.WriteLine($"Kollisionsstufe: J1={pkg.collisionLevel[0]}, J2={pkg.collisionLevel[1]}, J3={pkg.collisionLevel[2]}, J4={pkg.collisionLevel[3]}, J5={pkg.collisionLevel[4]}, J6={pkg.collisionLevel[5]}");

            await Task.Delay(50);
        }
        //Verbindung trennen
        robot.CloseRPC();
        Console.WriteLine("Test abgeschlossen.");
    }