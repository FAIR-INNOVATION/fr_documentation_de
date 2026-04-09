Roboter-I/O
===========

.. toctree::
    :maxdepth: 5

Digitalausgang des Steuerkastens setzen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Digitalausgang des Steuerkastens setzen
    * @param [in] id IO-Nummer, Bereich [0~15]
    * @param [in] status 0-aus, 1-ein
    * @param [in] smooth 0-nicht glätten, 1-glätten
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @return Fehlercode
    */
    int SetDO(int id, byte status, byte smooth, byte block);

Digitalausgang des Werkzeugs setzen
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Digitalausgang des Werkzeugs setzen
    * @param [in] id IO-Nummer, Bereich [0~1]
    * @param [in] status 0-aus, 1-ein
    * @param [in] smooth 0-nicht glätten, 1-glätten
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @return Fehlercode
    */
    int SetToolDO(int id, byte status, byte smooth, byte block);

Analogausgang des Steuerkastens setzen
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Analogausgang des Steuerkastens setzen
    * @param [in] id IO-Nummer, Bereich [0~1]
    * @param [in] value Prozentwert des Stroms oder der Spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @return Fehlercode
    */
    int SetAO(int id, float value, byte block);

Analogausgang des Werkzeugs setzen
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Analogausgang des Werkzeugs setzen
    * @param [in] id IO-Nummer, Bereich [0]
    * @param [in] value Prozentwert des Stroms oder der Spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @return Fehlercode
    */
    int SetToolAO(int id, float value, byte block);

Codebeispiel zum Setzen von Digital- und Analogausgängen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button14_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 1;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        status = 0;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetAO(0, i, block);
            Thread.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            Thread.Sleep(30);
        }
    }

Digitaleingang des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Digitaleingang des Steuerkastens abrufen
    * @param [in] id IO-Nummer, Bereich [0~15]
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @param [out] level 0-niedriger Pegel, 1-hoher Pegel
    * @return Fehlercode
    */
    int GetDI(int id, byte block, ref byte level);

Digitaleingang des Werkzeugs abrufen
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Digitaleingang des Werkzeugs abrufen
    * @param [in] id IO-Nummer, Bereich [0~1]
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @param [out] level 0-niedriger Pegel, 1-hoher Pegel
    * @return Fehlercode
    */
    int GetToolDI(int id, byte block, ref byte level);

Analogeingang des Steuerkastens abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Analogeingang des Steuerkastens abrufen
    * @param [in] id IO-Nummer, Bereich [0~1]
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @param [out] percent Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    * @return Fehlercode
    */
    int GetAI(int id, byte block, ref float percent);

Analogeingang des Werkzeugs abrufen
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Analogeingang des Werkzeugs abrufen
    * @param [in] id IO-Nummer, Bereich [0]
    * @param [in] block 0-blockierend, 1-nicht blockierend
    * @param [out] percent Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    * @return Fehlercode
    */
    int GetToolAI(int id, byte block, ref float percent);

Status der Aufnahmetaste am Roboterende abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Status der Aufnahmetaste am Roboterende abrufen
    * @param [out] state Tastenstatus, 0-gedrückt, 1-losgelassen
    * @return Fehlercode
    */
    int GetAxlePointRecordBtnState(ref byte state);

Ausgangszustand des Werkzeug-DO abrufen
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ausgangszustand des Werkzeug-DO abrufen
    * @param [out] do_state DO-Ausgangszustand, do0~do1 entsprechen Bit1~Bit2, beginnend bei Bit0
    * @return Fehlercode
    */
    int GetToolDO(ref byte do_state);

Ausgangszustand des Robotercontroller-DO abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ausgangszustand des Robotercontroller-DO abrufen
    * @param [out] do_state_h DO-Ausgangszustand, co0~co7 entsprechen Bit0~Bit7
    * @param [out] do_state_l DO-Ausgangszustand, do0~do7 entsprechen Bit0~Bit7
    * @return Fehlercode
    */
    int GetDO(ref int do_state_h, ref int do_state_l);

Codebeispiel zum Abrufen von DI- und DO-Status
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button15_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        robot.GetDI(0, block, ref di);
        Console.WriteLine($"di0: {di}");

        tool_di = (byte)robot.GetToolDI(1, block, ref tool_di);
        Console.WriteLine($"tool_di1: {tool_di}");

        robot.GetAI(0, block, ref ai);
        Console.WriteLine($"ai0: {ai}");

        tool_ai = robot.GetToolAI(0, block, ref tool_ai);
        Console.WriteLine($"tool_ai0: {tool_ai}");

        byte _button_state = 0;
        robot.GetAxlePointRecordBtnState(ref _button_state);
        Console.WriteLine($"_button_state is: {_button_state}");

        byte tool_do_state = 0;
        robot.GetToolDO(ref tool_do_state);
        Console.WriteLine($"tool DO state is: {tool_do_state}");

        int do_state_h = 0;
        int do_state_l = 0;
        robot.GetDO(ref do_state_h, ref do_state_l);
        Console.WriteLine($"DO state high is: {do_state_h}\n DO state low is: {do_state_l}");
    }

Auf Digitaleingang des Steuerkastens warten
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Auf Digitaleingang des Steuerkastens warten
    * @param [in] id IO-Nummer, Bereich [0~15]
    * @param [in] status 0-aus, 1-ein
    * @param [in] max_time Maximale Wartezeit [ms]
    * @param [in] opt Strategie bei Timeout: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return Fehlercode
    */
    int WaitDI(int id, byte status, int max_time, int opt);

Auf mehrere Digitaleingänge des Steuerkastens warten
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Auf mehrere Digitaleingänge des Steuerkastens warten
    * @param [in] mode 0-UND-Verknüpfung, 1-ODER-Verknüpfung
    * @param [in] id IO-Nummern als Bitmaske: Bit0~Bit7 für DI0~DI7, Bit8~Bit15 für CI0~CI7
    * @param [in] status 0-aus, 1-ein
    * @param [in] max_time Maximale Wartezeit [ms]
    * @param [in] opt Strategie bei Timeout: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return Fehlercode
    */
    int WaitMultiDI(int mode, int id, byte status, int max_time, int opt);

Auf Digitaleingang des Werkzeugs warten
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Auf Digitaleingang des Werkzeugs warten
    * @param [in] id IO-Nummer, Bereich [0~1]
    * @param [in] status 0-aus, 1-ein
    * @param [in] max_time Maximale Wartezeit [ms]
    * @param [in] opt Strategie bei Timeout: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return Fehlercode
    */
    int WaitToolDI(int id, byte status, int max_time, int opt);

Auf Analogeingang des Steuerkastens warten
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Auf Analogeingang des Steuerkastens warten
    * @param [in] id IO-Nummer, Bereich [0~1]
    * @param [in] sign 0-größer als, 1-kleiner als
    * @param [in] value Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    * @param [in] max_time Maximale Wartezeit [ms]
    * @param [in] opt Strategie bei Timeout: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return Fehlercode
    */
    int WaitAI(int id, int sign, float value, int max_time, int opt);

Auf Analogeingang des Werkzeugs warten
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Auf Analogeingang des Werkzeugs warten
    * @param [in] id IO-Nummer, Bereich [0]
    * @param [in] sign 0-größer als, 1-kleiner als
    * @param [in] value Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    * @param [in] max_time Maximale Wartezeit [ms]
    * @param [in] opt Strategie bei Timeout: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return Fehlercode
    */
    int WaitToolAI(int id, int sign, float value, int max_time, int opt);

Codebeispiel zum Warten auf digitale und analoge Eingangssignale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnIOTest_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        int rtn = robot.WaitDI(0, 1, 1000, 1);
        Console.WriteLine("WaitDI beendet; rtn is: " + rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        Console.WriteLine("WaitMultiDI beendet; rtn is: " + rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        Console.WriteLine("WaitToolDI beendet; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitAI beendet; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitToolAI beendet; rtn is: " + rtn);
    }

Festlegen, ob der Steuerkasten-DO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Festlegen, ob der Steuerkasten-DO nach Stopp/Pause zurückgesetzt wird
    * @param [in] resetFlag 0-nicht zurücksetzen, 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Pausenfortsetzung neu geladen wird: 0-nicht laden, 1-laden
    * @return Fehlercode
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag);

Festlegen, ob der Steuerkasten-AO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Festlegen, ob der Steuerkasten-AO nach Stopp/Pause zurückgesetzt wird
    * @param [in] resetFlag 0-nicht zurücksetzen, 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Pausenfortsetzung neu geladen wird: 0-nicht laden, 1-laden
    * @return Fehlercode
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag);

Festlegen, ob der Werkzeug-DO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Festlegen, ob der Werkzeug-DO nach Stopp/Pause zurückgesetzt wird
    * @param [in] resetFlag 0-nicht zurücksetzen, 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Pausenfortsetzung neu geladen wird: 0-nicht laden, 1-laden
    * @return Fehlercode
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag);

Festlegen, ob der Werkzeug-AO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Festlegen, ob der Werkzeug-AO nach Stopp/Pause zurückgesetzt wird
    * @param [in] resetFlag 0-nicht zurücksetzen, 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Pausenfortsetzung neu geladen wird: 0-nicht laden, 1-laden
    * @return Fehlercode
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag);

Festlegen, ob der erweiterte DO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Festlegen, ob der erweiterte DO nach Stopp/Pause zurückgesetzt wird
    * @param [in] resetFlag 0-nicht zurücksetzen, 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Pausenfortsetzung neu geladen wird: 0-nicht laden, 1-laden
    * @return Fehlercode
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag);

Festlegen, ob der erweiterte AO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Festlegen, ob der erweiterte AO nach Stopp/Pause zurückgesetzt wird
    * @param [in] resetFlag 0-nicht zurücksetzen, 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Pausenfortsetzung neu geladen wird: 0-nicht laden, 1-laden
    * @return Fehlercode
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag);

Festlegen, ob der SmartTool-DO nach Stopp/Pause zurückgesetzt wird
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Festlegen, ob der SmartTool-DO nach Stopp/Pause zurückgesetzt wird
    * @param [in] resetFlag 0-nicht zurücksetzen, 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Pausenfortsetzung neu geladen wird: 0-nicht laden, 1-laden
    * @return Fehlercode
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag);

Codebeispiel zum Festlegen des Ausgangs-Rücksetzverhaltens nach Stopp/Pause für LUA-Programme
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestDOReset()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            Thread.Sleep(200);
        }

        int resetFlag = 1;
        int resumeReloadFlag = 1;
        int rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag);

        robot.ProgramLoad("/fruser/test.lua");
        robot.ProgramRun();

        Thread.Sleep(2000);
        robot.PauseMotion();
        Thread.Sleep(2000);
        robot.ResumeMotion();
        Thread.Sleep(2000);
    }

Konfigurierbare CI-Portfunktionen des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen der konfigurierbaren CI-Portfunktionen des Steuerkastens
    * @param [in] config CI0-CI7 Funktionscodes;
    * 0-Keine;1-Lichtbogenstart erfolgreich;2-Schweißgerät bereit;3-Förderbanderkennung;4-Pause;5-Fortsetzen;6-Start;7-Stopp;
    8-Pause/Fortsetzen;9-Start/Stopp;10-Fußtaster-Ziehen;11-Zur Arbeitsposition bewegen;12-Manuell/Auto umschalten;
    13-Drahtpositionssuche erfolgreich;14-Bewegungsunterbrechung;15-Hauptprogramm starten;16-Rückspulen starten;17-Startbestätigung;
    18-Photoelektrisches Erkennungssignal X;19-Photoelektrisches Erkennungssignal Y;20-Externer Not-Halt-Eingangssignal 1;21-Externer Not-Halt-Eingangssignal 2;
    22-Stufe 1 Reduzierungsmodus;23-Stufe 2 Reduzierungsmodus;24-Stufe 3 Reduzierungsmodus (Stopp);25-Schweißen fortsetzen;26-Schweißen beenden;
    27-Hilfszug aktivieren;28-Hilfszug deaktivieren;29-Hilfszug aktivieren/deaktivieren;30-Alle Fehler löschen;
    31-Manuell/Auto umschalten (High/Low-Pegel);32-Aktivieren;33-Deaktivieren;34-Aktivieren/Deaktivieren (steigende/fallende Flanke);35-Fixpunkt-Tracking starten/beenden
    * @return Fehlercode
    */
    public int SetDIConfig(int[] config)

Konfigurierbare CI-Portfunktionen des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen der konfigurierbaren CI-Portfunktionen des Steuerkastens
    * @param [in] config CI0-CI7 Funktionscodes;
    * 0-Keine;1-Lichtbogenstart erfolgreich;2-Schweißgerät bereit;3-Förderbanderkennung;4-Pause;5-Fortsetzen;6-Start;7-Stopp;
    8-Pause/Fortsetzen;9-Start/Stopp;10-Fußtaster-Ziehen;11-Zur Arbeitsposition bewegen;12-Manuell/Auto umschalten;
    13-Drahtpositionssuche erfolgreich;14-Bewegungsunterbrechung;15-Hauptprogramm starten;16-Rückspulen starten;17-Startbestätigung;
    18-Photoelektrisches Erkennungssignal X;19-Photoelektrisches Erkennungssignal Y;20-Externer Not-Halt-Eingangssignal 1;21-Externer Not-Halt-Eingangssignal 2;
    22-Stufe 1 Reduzierungsmodus;23-Stufe 2 Reduzierungsmodus;24-Stufe 3 Reduzierungsmodus (Stopp);25-Schweißen fortsetzen;26-Schweißen beenden;
    27-Hilfszug aktivieren;28-Hilfszug deaktivieren;29-Hilfszug aktivieren/deaktivieren;30-Alle Fehler löschen;
    31-Manuell/Auto umschalten (High/Low-Pegel);32-Aktivieren;33-Deaktivieren;34-Aktivieren/Deaktivieren (steigende/fallende Flanke);35-Fixpunkt-Tracking starten/beenden
    * @return Fehlercode
    */
    public int GetDIConfig(out int[] config)

Konfigurierbare CO-Portfunktionen des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen der konfigurierbaren CO-Portfunktionen des Steuerkastens
    * @param [out] config CO0-CO7 Funktionscodes;
    * 0-Keine;1-Roboterfehler;2-Roboter in Bewegung;3-Spritzen start/stopp;4-Spritzpistolenreinigung;5-Gaszufuhrsignal;6-Lichtbogenstartsignal;7-Tippen Drahtvorschub;
    8-Rückwärts Drahtvorschub;9-JOB-Eingang 1;10-JOB-Eingang 2;11-JOB-Eingang 3;12-Förderband start/stopp Steuerung;13-Roboter pausiert;14-Arbeitsposition erreicht;
    15-Interferenzbereich erreicht;16-Drahtpositionssuche start/stopp Steuerung;17-Roboterstart abgeschlossen;18-Programm start/stopp;19-Auto/Manuell-Modus;20-Not-Halt-Ausgangssignal 1-Sicherheit;
    21-Not-Halt-Ausgangssignal 2-Sicherheit;22-Lua-Skriptprogramm läuft/gestoppt;23-Sicherheitsstatusausgang-Sicherheit;24-Schutzstopp-Statusausgang-Sicherheit;
    25-Roboter in Bewegung-Sicherheit;26-Roboter im Reduzierungsmodus-Sicherheit;27-Roboter nicht im Reduzierungsmodus-Sicherheit;28-Roboter nicht gestoppt;29-Roboterfehler-Befehlspunktfehler;
    30-Roboterfehler-Antriebsfehler;31-Roboterfehler-Weichgrenze überschritten;32-Roboterfehler-Kollisionsfehler;33-Roboterfehler-Fehler bei Anzahl aktiver Slaves;
    34-Roboterfehler-Slave-Fehler;35-Roboterfehler-IO-Fehler;36-Roboterfehler-Greiferfehler;37-Roboterfehler-Dateifehler;38-Roboterfehler-Singuläre Pose;
    39-Roboterfehler-Antriebskommunikationsfehler;40-Roboterfehler-Parameterfehler;41-Roboterfehler-Externe Achse Weichgrenze überschritten;42-Roboterwarnung-Warnung;
    43-Roboterwarnung-Sicherheitstürwarnung;44-Roboterwarnung-Bewegungswarnung;45-Roboterwarnung-Interferenzbereichswarnung;46-Roboterwarnung-Sicherheitswandwarnung;
    47-Aktivierungsstatus;48-Automatisches Anheben bei Unterbrechung;49-Würfel 1 Interferenzwarnung;50-Würfel 2 Interferenzwarnung;51-Würfel 3 Interferenzwarnung;52-Würfel 4 Interferenzwarnung;
    * @return Fehlercode
    */
    public int SetDOConfig(int[] config)

Konfigurierbare CO-Portfunktionen des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen der konfigurierbaren CO-Portfunktionen des Steuerkastens
    * @param [out] config CO0-CO7 Funktionscodes;
    * 0-Keine;1-Roboterfehler;2-Roboter in Bewegung;3-Spritzen start/stopp;4-Spritzpistolenreinigung;5-Gaszufuhrsignal;6-Lichtbogenstartsignal;7-Tippen Drahtvorschub;
    8-Rückwärts Drahtvorschub;9-JOB-Eingang 1;10-JOB-Eingang 2;11-JOB-Eingang 3;12-Förderband start/stopp Steuerung;13-Roboter pausiert;14-Arbeitsposition erreicht;
    15-Interferenzbereich erreicht;16-Drahtpositionssuche start/stopp Steuerung;17-Roboterstart abgeschlossen;18-Programm start/stopp;19-Auto/Manuell-Modus;20-Not-Halt-Ausgangssignal 1-Sicherheit;
    21-Not-Halt-Ausgangssignal 2-Sicherheit;22-Lua-Skriptprogramm läuft/gestoppt;23-Sicherheitsstatusausgang-Sicherheit;24-Schutzstopp-Statusausgang-Sicherheit;
    25-Roboter in Bewegung-Sicherheit;26-Roboter im Reduzierungsmodus-Sicherheit;27-Roboter nicht im Reduzierungsmodus-Sicherheit;28-Roboter nicht gestoppt;29-Roboterfehler-Befehlspunktfehler;
    30-Roboterfehler-Antriebsfehler;31-Roboterfehler-Weichgrenze überschritten;32-Roboterfehler-Kollisionsfehler;33-Roboterfehler-Fehler bei Anzahl aktiver Slaves;
    34-Roboterfehler-Slave-Fehler;35-Roboterfehler-IO-Fehler;36-Roboterfehler-Greiferfehler;37-Roboterfehler-Dateifehler;38-Roboterfehler-Singuläre Pose;
    39-Roboterfehler-Antriebskommunikationsfehler;40-Roboterfehler-Parameterfehler;41-Roboterfehler-Externe Achse Weichgrenze überschritten;42-Roboterwarnung-Warnung;
    43-Roboterwarnung-Sicherheitstürwarnung;44-Roboterwarnung-Bewegungswarnung;45-Roboterwarnung-Interferenzbereichswarnung;46-Roboterwarnung-Sicherheitswandwarnung;
    47-Aktivierungsstatus;48-Automatisches Anheben bei Unterbrechung;49-Würfel 1 Interferenzwarnung;50-Würfel 2 Interferenzwarnung;51-Würfel 3 Interferenzwarnung;52-Würfel 4 Interferenzwarnung;
    * @return Fehlercode
    */
    public int GetDOConfig(out int[] config)

Konfigurierbare End-CI-Portfunktionen des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen der konfigurierbaren End-CI-Portfunktionen des Endeffektors
    * @param [in] config End CI0-CI1 Funktionscodes;
    * 0-Keine;1-Zieh-Teaching-Werkzeugschalter;2-Punktaufzeichnungssignal;3-Manuell/Auto umschalten (Impulssignal);4-TPD-Aufzeichnung start/stopp;5-Bewegung pausieren;
    6-Bewegung fortsetzen;7-Start;8-Stopp;9-Pause/Fortsetzen;10-Start/Stopp;11-Kraftsensor-Hilfszug aktivieren;12-Kraftsensor-Hilfszug deaktivieren;
    13-Kraftsensor-Hilfszug aktivieren/deaktivieren;14-Lasererkennungssignal X;15-Lasererkennungssignal Y;16-PTP-Bewegung zur Arbeitsposition;17-Bewegungsunterbrechung, aktuelle Bewegung je nach Signal stoppen;
    18-Hauptprogramm starten;19-Rückspulen starten;20-Startbestätigung;21-Schweißen fortsetzen;22-Schweißen beenden;23-Fehler löschen;24-Manuell/Auto umschalten (High/Low-Pegel);
    25-Aktivieren;26-Deaktivieren;27-Aktivieren/Deaktivieren;28-Laser-Servo-Tracking start/stopp Signal;
    * @return Fehlercode
    */
    public int SetToolDIConfig(int[] config)

Konfigurierbare End-CI-Portfunktionen des Endeffektors abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen der konfigurierbaren End-CI-Portfunktionen des Endeffektors
    * @param [out] config End CI0-CI1 Funktionscodes;
    * 0-Keine;1-Zieh-Teaching-Werkzeugschalter;2-Punktaufzeichnungssignal;3-Manuell/Auto umschalten (Impulssignal);4-TPD-Aufzeichnung start/stopp;5-Bewegung pausieren;
    6-Bewegung fortsetzen;7-Start;8-Stopp;9-Pause/Fortsetzen;10-Start/Stopp;11-Kraftsensor-Hilfszug aktivieren;12-Kraftsensor-Hilfszug deaktivieren;
    13-Kraftsensor-Hilfszug aktivieren/deaktivieren;14-Lasererkennungssignal X;15-Lasererkennungssignal Y;16-PTP-Bewegung zur Arbeitsposition;17-Bewegungsunterbrechung, aktuelle Bewegung je nach Signal stoppen;
    18-Hauptprogramm starten;19-Rückspulen starten;20-Startbestätigung;21-Schweißen fortsetzen;22-Schweißen beenden;23-Fehler löschen;24-Manuell/Auto umschalten (High/Low-Pegel);
    25-Aktivieren;26-Deaktivieren;27-Aktivieren/Deaktivieren;28-Laser-Servo-Tracking start/stopp Signal;
    * @return Fehlercode
    */
    public int GetToolDIConfig(out int[] config)
    
Konfigurierbaren CI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CI-Aktivzustands des Steuerkastens
    * @param [in] config CI0-CI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetDIConfigLevel(int[] config)
        
Konfigurierbaren CI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CI-Aktivzustands des Steuerkastens
    * @param [out] config CI0-CI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetDIConfigLevel(out int[] config)
        
Konfigurierbaren CO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CO-Aktivzustands des Steuerkastens
    * @param [in] config CO0-CO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetDOConfigLevel(int[] config)

Konfigurierbaren CO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CO-Aktivzustands des Steuerkastens
    * @param [out] config CO0-CO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetDOConfigLevel(out int[] config)
    
Konfigurierbaren CI-Aktivzustand des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CI-Aktivzustands des Endeffektors
    * @param [in] config CI0-CI1 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetToolDIConfigLevel(int[] config)
    
Konfigurierbaren CI-Aktivzustand des Endeffektors abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CI-Aktivzustands des Endeffektors
    * @param [out] config CI0-CI1 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetToolDIConfigLevel(out int[] config)
    
Standard-DI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen des Standard-DI-Aktivzustands des Steuerkastens
    * @param [in] config DI0-DI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetStandardDILevel(int[] config)
    
Standard-DI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen des Standard-DI-Aktivzustands des Steuerkastens
    * @param [out] config DI0-DI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetStandardDILevel(out int[] config)

Standard-DO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen des Standard-DO-Aktivzustands des Steuerkastens
    * @param [in] config DO0-DO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetStandardDOLevel(int[] config)
    
Standard-DO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abrufen des Standard-DO-Aktivzustands des Steuerkastens
    * @param [out] config DO0-DO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetStandardDOLevel(out int[] config)
        
Robot IO Konfigurationscodebeispiel
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestIOConfig()
    {
        int rtn = 0;

        // ---------- Test konfigurierbare CI-Portfunktionen ----------
        int[] setDIConfig = new int[] { 3, 9, 1, 4, 5, 6, 7, 8 };
        rtn = robot.SetDIConfig(setDIConfig);
        Console.WriteLine($"SetDIConfig rtn is {rtn}");

        // Verwenden Sie den out-Parameter, um das abgerufene Konfigurationsarray zu empfangen
        int[] getDIConfig;
        rtn = robot.GetDIConfig(out getDIConfig);  
        Console.WriteLine($"GetDIConfig rtn is {rtn}, value is {string.Join(" ", getDIConfig)}");

        // ---------- Test konfigurierbare CO-Portfunktionen ----------
        int[] setDOConfig = new int[] { 9, 10, 11, 12, 13, 14, 15, 16 };
        rtn = robot.SetDOConfig(setDOConfig);
        Console.WriteLine($"SetDOConfig rtn is {rtn}");

        int[] getDOConfig;
        rtn = robot.GetDOConfig(out getDOConfig);
        Console.WriteLine($"GetDOConfig rtn is {rtn}, value is {string.Join(" ", getDOConfig)}");

        // ---------- Test konfigurierbare End-CI-Portfunktionen des Endeffektors ----------
        int[] setToolDIConfig = new int[] { 17, 18 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        Console.WriteLine($"SetToolDIConfig rtn is {rtn}");

        int[] getToolDIConfig;
        rtn = robot.GetToolDIConfig(out getToolDIConfig);
        Console.WriteLine($"GetToolDIConfig rtn is {rtn}, value is {string.Join(" ", getToolDIConfig)}");

        // ---------- Test konfigurierbaren CI-Aktivzustand des Steuerkastens ----------
        int[] setDIConfigLevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        Console.WriteLine($"SetDIConfigLevel rtn is {rtn}");

        int[] getDIConfigLevel;
        rtn = robot.GetDIConfigLevel(out getDIConfigLevel);
        Console.WriteLine($"GetDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getDIConfigLevel)}");

        // ---------- Test konfigurierbaren CO-Aktivzustand des Steuerkastens ----------
        int[] setDOConfigLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetDIConfigLevel(setDOConfigLevel);
        Console.WriteLine($"SetDOConfigLevel rtn is {rtn}");

        int[] getDOConfigLevel;
        rtn = robot.GetDOConfigLevel(out getDOConfigLevel);
        Console.WriteLine($"GetDOConfigLevel rtn is {rtn}, value is {string.Join(" ", getDOConfigLevel)}");

        // ---------- Test konfigurierbaren CI-Aktivzustand des Endeffektors ----------
        int[] setToolDIConfigLevel = new int[] { 1, 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        Console.WriteLine($"SetToolDIConfigLevel rtn is {rtn}");

        int[] getToolDIConfigLevel;
        rtn = robot.GetToolDIConfigLevel(out getToolDIConfigLevel);
        Console.WriteLine($"GetToolDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getToolDIConfigLevel)}");

        // ---------- Test Standard-DI-Aktivzustand des Steuerkastens ----------
        int[] setStandardDILevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        Console.WriteLine($"SetStandardDILevel rtn is {rtn}");

        int[] getStandardDILevel;
        rtn = robot.GetStandardDILevel(out getStandardDILevel);
        Console.WriteLine($"GetStandardDILevel rtn is {rtn}, value is {string.Join(" ", getStandardDILevel)}");

        // ---------- Test Standard-DO-Aktivzustand des Steuerkastens ----------
        int[] setStandardDOLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        Console.WriteLine($"SetStandardDOLevel rtn is {rtn}");

        int[] getStandardDOLevel;
        rtn = robot.GetStandardDOLevel(out getStandardDOLevel);
        Console.WriteLine($"GetStandardDOLevel rtn is {rtn}, value is {string.Join(" ", getStandardDOLevel)}");
    }