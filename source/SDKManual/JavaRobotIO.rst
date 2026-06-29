Roboter-I/O
============

.. toctree::
    :maxdepth: 5

Digitalausgang des Steuerschranks setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Setzt einen digitalen Ausgang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~15].
    * @param  [in] status 0-aus, 1-ein.
    * @param  [in] smooth 0-nicht glätten, 1-glätten.
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @return  Fehlercode.
    */
    int SetDO(int id, int status, int smooth, int block);

Digitalausgang des Werkzeugs setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Setzt einen digitalen Ausgang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0~1].
    * @param  [in] status 0-aus, 1-ein.
    * @param  [in] smooth 0-nicht glätten, 1-glätten.
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @return  Fehlercode.
    */
    int SetToolDO(int id, int status, int smooth, int block);

Analogausgang des Steuerschranks setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Setzt einen analogen Ausgang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~1].
    * @param  [in] value  Prozentwert des Stroms oder der Spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V].
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @return  Fehlercode.
    */
    int SetAO(int id, double value, int block);

Analogausgang des Werkzeugs setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Setzt einen analogen Ausgang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0].
    * @param  [in] value  Prozentwert des Stroms oder der Spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V].
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @return  Fehlercode.
    */
    int SetToolAO(int id, double value, int block);

Codebeispiel zum Setzen von Digital- und Analogausgängen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestAODO(Robot robot)
    {

        int status = 1;
        int smooth = 0;
        int block = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            robot.Sleep(300);
        }

        status = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            robot.Sleep(300);
        }

        status = 1;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            robot.Sleep(1000);
        }

        status = 0;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            robot.Sleep(1000);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetAO(0, i, block);
            robot.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            robot.Sleep(30);
        }

        robot.CloseRPC();
        return 0;
    }

Digitaleingang des Steuerschranks abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Gibt den Zustand eines digitalen Eingangs des Steuerschranks zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0~15].
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @param  [out] level  Array der Länge 1, 0-niedriger Pegel, 1-hoher Pegel.
    * @return  Fehlercode.
    */
    int GetDI(int id, int block, int[] level);

Digitaleingang des Werkzeugs abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Gibt den Zustand eines digitalen Eingangs des Werkzeugs zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0~1].
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @param  [out] level  Array der Länge 1, 0-niedriger Pegel, 1-hoher Pegel.
    * @return  Fehlercode.
    */
    int GetToolDI(int id, int block, int[] level);

Analogeingang des Steuerschranks abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Gibt den Wert eines analogen Eingangs des Steuerschranks zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0~1].
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @param  [out] persent  Array der Länge 1, Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V].
    * @return  Fehlercode.
    */
    int GetAI(int id, int block, double[] persent);

Analogeingang des Werkzeugs abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Gibt den Wert eines analogen Eingangs des Werkzeugs zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0].
    * @param  [in] block  0-blockierend, 1-nicht blockierend.
    * @param  [out] persent  Array der Länge 1, Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V].
    * @return  Fehlercode.
    */
    int GetToolAI(int id, int block, double[] persent);

Status der Punktaufzeichnungstaste am Roboterende abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Gibt den Status der Punktaufzeichnungstaste am Roboterende zurück.
    * @param  [out] state  Array der Länge 1, Tastenstatus, 0-gedrückt, 1-losgelassen.
    * @return  Fehlercode.
    */
    int GetAxlePointRecordBtnState(int[] state);

DO-Ausgangsstatus am Roboterende abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Gibt den DO-Ausgangsstatus am Roboterende zurück.
    * @param  [out] do_state  Array der Länge 1, DO-Ausgangsstatus, do0~do1 entsprechen bit1~bit2, beginnend bei bit0.
    * @return  Fehlercode.
    */
    int GetToolDO(int[] do_state);

DO-Ausgangsstatus des Robotersteuerschranks abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Gibt den DO-Ausgangsstatus des Robotersteuerschranks zurück.
    * @param  [out] do_state_h  Array der Länge 1, DO-Ausgangsstatus, co0~co7 entsprechen bit0~bit7.
    * @param  [out] do_state_l  Array der Länge 1, DO-Ausgangsstatus, do0~do7 entsprechen bit0~bit7.
    * @return  Fehlercode.
    */
    int GetDO(int[] do_state_h, int[] do_state_l);

Codebeispiel zum Abrufen von Roboter-DI/DO-Status
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestGetDIAI(Robot robot)
    {
        int status = 1;
        int smooth = 0;
        int block = 0;
        int[] di =new int[]{0}, tool_di =new int[] {0};
        double[] ai =new double[] {0}, tool_ai = new double[]{0};
        double value = 0.0;


        robot.GetDI(0, block, di);
        System.out.println("di0:"+di[0]);

        robot.GetToolDI(1, block, tool_di);
        System.out.println("tool_di1:"+ tool_di[0]);

        robot.GetAI(0, block, ai);
        System.out.println("ai0:"+ ai[0]);

        robot.GetToolAI(0, block, tool_ai);
        System.out.println("tool_ai0:"+ tool_ai[0]);

        int[] _button_state=new int[]{0};
        robot.GetAxlePointRecordBtnState(_button_state);
        System.out.println("_button_state is: "+ _button_state[0]);

        int[] tool_do_state=new int[]{0};
        robot.GetToolDO(tool_do_state);
        System.out.println("tool DO state is: "+ tool_do_state[0]);

        int[] do_state_h=new int[]{0};
        int[] do_state_l=new int[]{0};
        robot.GetDO(do_state_h, do_state_l);
        System.out.println("DO state high is: "+do_state_h[0]+", DO state low is: "+ do_state_l[0]);

        return 0;
    }

Auf digitalen Eingang des Steuerschranks warten
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen digitalen Eingang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~15].
    * @param  [in] status 0-aus, 1-ein.
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms.
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten.
    * @return  Fehlercode.
    */
    int WaitDI(int id, int status, int max_time, int opt);

Auf mehrere digitale Eingänge des Steuerschranks warten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf mehrere digitale Eingänge des Steuerschranks.
    * @param  [in] mode 0-UND-Verknüpfung aller Kanäle, 1-ODER-Verknüpfung aller Kanäle.
    * @param  [in] id  I/O-Nummern als Bitmaske, Bits 0-7 für DI0-DI7, Bits 8-15 für CI0-CI7.
    * @param  [in] status 0-aus, 1-ein.
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms.
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten.
    * @return  Fehlercode.
    */
    int WaitMultiDI(int mode, int id, int status, int max_time, int opt);

Auf digitalen Eingang des Werkzeugs warten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen digitalen Eingang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0~1].
    * @param  [in] status 0-aus, 1-ein.
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms.
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten.
    * @return  Fehlercode.
    */
    int WaitToolDI(int id, int status, int max_time, int opt);

Auf analogen Eingang des Steuerschranks warten
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen analogen Eingang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~1].
    * @param  [in] sign 0-größer als, 1-kleiner als.
    * @param  [in] value  Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V].
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms.
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten.
    * @return  Fehlercode.
    */
    int WaitAI(int id, int sign, double value, int max_time, int opt);

Auf analogen Eingang des Werkzeugs warten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen analogen Eingang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0].
    * @param  [in] sign 0-größer als, 1-kleiner als.
    * @param  [in] value  Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V].
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms.
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten.
    * @return  Fehlercode.
    */
    int WaitToolAI(int id, int sign, double value, int max_time, int opt);

Codebeispiel zum Warten auf digitale/analoge Eingangssignale des Steuerschranks
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestWaitDIAI(Robot robot)
    {
        int rtn=-1;

        int status = 1;
        int smooth = 0;
        int block = 0;
        int di = 0, tool_di = 0;
        double ai = 0.0, tool_ai = 0.0;
        double value = 0.0;

        rtn = robot.WaitDI(0, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: "+ rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        System.out.println("WaitDI over; rtn is: "+ rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);
        return 0;
    }

Einstellung, ob DO-Ausgänge des Steuerschranks nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt fest, ob die DO-Ausgänge des Steuerschranks nach einem Stopp/Pause zurückgesetzt werden.
    * @param resetFlag  0-nicht zurücksetzen; 1-zurücksetzen.
    * @param reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden.
    * @return Fehlercode.
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag);

Einstellung, ob AO-Ausgänge des Steuerschranks nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt fest, ob die AO-Ausgänge des Steuerschranks nach einem Stopp/Pause zurückgesetzt werden.
    * @param resetFlag  0-nicht zurücksetzen; 1-zurücksetzen.
    * @param reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden.
    * @return Fehlercode.
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag);

Einstellung, ob DO-Ausgänge des Endeffektorwerkzeugs nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt fest, ob die DO-Ausgänge des Endeffektorwerkzeugs nach einem Stopp/Pause zurückgesetzt werden.
    * @param resetFlag  0-nicht zurücksetzen; 1-zurücksetzen.
    * @param reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden.
    * @return Fehlercode.
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag);

Einstellung, ob AO-Ausgänge des Endeffektorwerkzeugs nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt fest, ob die AO-Ausgänge des Endeffektorwerkzeugs nach einem Stopp/Pause zurückgesetzt werden.
    * @param resetFlag  0-nicht zurücksetzen; 1-zurücksetzen.
    * @param reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden.
    * @return Fehlercode.
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag);

Einstellung, ob erweiterte DO-Ausgänge nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt fest, ob die erweiterten DO-Ausgänge nach einem Stopp/Pause zurückgesetzt werden.
    * @param resetFlag  0-nicht zurücksetzen; 1-zurücksetzen.
    * @param reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden.
    * @return Fehlercode.
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag);

Einstellung, ob erweiterte AO-Ausgänge nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt fest, ob die erweiterten AO-Ausgänge nach einem Stopp/Pause zurückgesetzt werden.
    * @param resetFlag  0-nicht zurücksetzen; 1-zurücksetzen.
    * @param reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden.
    * @return Fehlercode.
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag);

Einstellung, ob SmartTool-DO-Ausgänge nach Stopp/Pause zurückgesetzt werden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt fest, ob die SmartTool-DO-Ausgänge nach einem Stopp/Pause zurückgesetzt werden.
    * @param resetFlag  0-nicht zurücksetzen; 1-zurücksetzen.
    * @param reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden.
    * @return Fehlercode.
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag);

Codebeispiel zum Zurücksetzen der Ausgänge nach LUA-Programmstopp/-pause
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void TestDOReset(Robot robot)
    {
        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            robot.Sleep(200);
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
        robot.ProgramLoad("test.lua");
        robot.ProgramRun();
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);
        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.CloseRPC();
    }

Konfigurierbare CI-Portfunktionen des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen der konfigurierbaren CI-Portfunktionen des Steuerkastens
    * @param config CI0-CI7 Funktionscodes;
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
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen der konfigurierbaren CI-Portfunktionen des Steuerkastens
    * @param config CI0-CI7 Funktionscodes;
    * 0-Keine;1-Lichtbogenstart erfolgreich;2-Schweißgerät bereit;3-Förderbanderkennung;4-Pause;5-Fortsetzen;6-Start;7-Stopp;
    8-Pause/Fortsetzen;9-Start/Stopp;10-Fußtaster-Ziehen;11-Zur Arbeitsposition bewegen;12-Manuell/Auto umschalten;
    13-Drahtpositionssuche erfolgreich;14-Bewegungsunterbrechung;15-Hauptprogramm starten;16-Rückspulen starten;17-Startbestätigung;
    18-Photoelektrisches Erkennungssignal X;19-Photoelektrisches Erkennungssignal Y;20-Externer Not-Halt-Eingangssignal 1;21-Externer Not-Halt-Eingangssignal 2;
    22-Stufe 1 Reduzierungsmodus;23-Stufe 2 Reduzierungsmodus;24-Stufe 3 Reduzierungsmodus (Stopp);25-Schweißen fortsetzen;26-Schweißen beenden;
    27-Hilfszug aktivieren;28-Hilfszug deaktivieren;29-Hilfszug aktivieren/deaktivieren;30-Alle Fehler löschen;
    31-Manuell/Auto umschalten (High/Low-Pegel);32-Aktivieren;33-Deaktivieren;34-Aktivieren/Deaktivieren (steigende/fallende Flanke);35-Fixpunkt-Tracking starten/beenden
    * @return Fehlercode
    */
    public int GetDIConfig(int[] config)

Konfigurierbare CO-Portfunktionen des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen der konfigurierbaren CO-Portfunktionen des Steuerkastens
    * @param config CO0-CO7 Funktionscodes;
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
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen der konfigurierbaren CO-Portfunktionen des Steuerkastens
    * @param config CO0-CO7 Funktionscodes;
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
    public int GetDOConfig(int[] config)

Konfigurierbare End-CI-Portfunktionen des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen der konfigurierbaren End-CI-Portfunktionen des Endeffektors
    * @param config End CI0-CI1 Funktionscodes;
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
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen der konfigurierbaren End-CI-Portfunktionen des Endeffektors
    * @param config End CI0-CI1 Funktionscodes;
    * 0-Keine;1-Zieh-Teaching-Werkzeugschalter;2-Punktaufzeichnungssignal;3-Manuell/Auto umschalten (Impulssignal);4-TPD-Aufzeichnung start/stopp;5-Bewegung pausieren;
    6-Bewegung fortsetzen;7-Start;8-Stopp;9-Pause/Fortsetzen;10-Start/Stopp;11-Kraftsensor-Hilfszug aktivieren;12-Kraftsensor-Hilfszug deaktivieren;
    13-Kraftsensor-Hilfszug aktivieren/deaktivieren;14-Lasererkennungssignal X;15-Lasererkennungssignal Y;16-PTP-Bewegung zur Arbeitsposition;17-Bewegungsunterbrechung, aktuelle Bewegung je nach Signal stoppen;
    18-Hauptprogramm starten;19-Rückspulen starten;20-Startbestätigung;21-Schweißen fortsetzen;22-Schweißen beenden;23-Fehler löschen;24-Manuell/Auto umschalten (High/Low-Pegel);
    25-Aktivieren;26-Deaktivieren;27-Aktivieren/Deaktivieren;28-Laser-Servo-Tracking start/stopp Signal;
    * @return Fehlercode
    */
    public int GetToolDIConfig(int[] config)
    
Konfigurierbaren CI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CI-Aktivzustands des Steuerkastens
    * @param config CI0-CI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetDIConfigLevel(int[] config)
        
Konfigurierbaren CI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CI-Aktivzustands des Steuerkastens
    * @param config CI0-CI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetDIConfigLevel(int[] config)
        
Konfigurierbaren CO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CO-Aktivzustands des Steuerkastens
    * @param config CO0-CO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetDOConfigLevel(int[] config)

Konfigurierbaren CO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CO-Aktivzustands des Steuerkastens
    * @param config CO0-CO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetDOConfigLevel(int[] config)
    
Konfigurierbaren CI-Aktivzustand des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CI-Aktivzustands des Endeffektors
    * @param config CI0-CI1 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetToolDIConfigLevel(int[] config)
    
Konfigurierbaren CI-Aktivzustand des Endeffektors abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CI-Aktivzustands des Endeffektors
    * @param config CI0-CI1 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetToolDIConfigLevel(int[] config)
    
Standard-DI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen des Standard-DI-Aktivzustands des Steuerkastens
    * @param config DI0-DI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetStandardDILevel(int[] config)
    
Standard-DI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen des Standard-DI-Aktivzustands des Steuerkastens
    * @param config DI0-DI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetStandardDILevel(int[] config)

Standard-DO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen des Standard-DO-Aktivzustands des Steuerkastens
    * @param config DO0-DO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int SetStandardDOLevel(int[] config)
    
Standard-DO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Abrufen des Standard-DO-Aktivzustands des Steuerkastens
    * @param config DO0-DO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    public int GetStandardDOLevel(int[] config)
        
Robot IO Konfigurationscodebeispiel
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestIOConfig(Robot robot) {
        int[] setDIConfig = new int[]{1, 2, 3, 4, 5, 6, 7, 8};
        int[] getDIConfig = new int[8];
        int rtn = robot.SetDIConfig(setDIConfig);
        System.out.println("SetDIConfig rtn is " + rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        System.out.println("GetDIConfig rtn is " + rtn + ", value is " + 
            getDIConfig[0] + " " + getDIConfig[1] + " " + getDIConfig[2] + " " + getDIConfig[3] + " " + 
            getDIConfig[4] + " " + getDIConfig[5] + " " + getDIConfig[6] + " " + getDIConfig[7]);

        int[] setDOConfig = new int[]{9, 10, 11, 12, 13, 14, 15, 16};
        int[] getDOConfig = new int[8];
        rtn = robot.SetDOConfig(setDOConfig);
        System.out.println("SetDOConfig rtn is " + rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        System.out.println("GetDOConfig rtn is " + rtn + ", value is " + 
            getDOConfig[0] + " " + getDOConfig[1] + " " + getDOConfig[2] + " " + getDOConfig[3] + " " + 
            getDOConfig[4] + " " + getDOConfig[5] + " " + getDOConfig[6] + " " + getDOConfig[7]);

        int[] setToolDIConfig = new int[]{17, 18};
        int[] getToolDIConfig = new int[2];
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        System.out.println("SetToolDIConfig rtn is " + rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        System.out.println("GetToolDIConfig rtn is " + rtn + ", value is " + getToolDIConfig[0] + " " + getToolDIConfig[1]);

        int[] setDIConfigLevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getDIConfigLevel = new int[8];
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        System.out.println("SetDIConfigLevel rtn is " + rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        System.out.println("GetDIConfigLevel rtn is " + rtn + ", value is " + 
            getDIConfigLevel[0] + " " + getDIConfigLevel[1] + " " + getDIConfigLevel[2] + " " + getDIConfigLevel[3] + " " + 
            getDIConfigLevel[4] + " " + getDIConfigLevel[5] + " " + getDIConfigLevel[6] + " " + getDIConfigLevel[7]);

        int[] setDOConfigLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getDOConfigLevel = new int[8];
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        System.out.println("SetDOConfigLevel rtn is " + rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        System.out.println("GetDOConfigLevel rtn is " + rtn + ", value is " + 
            getDOConfigLevel[0] + " " + getDOConfigLevel[1] + " " + getDOConfigLevel[2] + " " + getDOConfigLevel[3] + " " + 
            getDOConfigLevel[4] + " " + getDOConfigLevel[5] + " " + getDOConfigLevel[6] + " " + getDOConfigLevel[7]);

        int[] setToolDIConfigLevel = new int[]{1, 0};
        int[] getToolDIConfigLevel = new int[2];
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        System.out.println("SetToolDIConfigLevel rtn is " + rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        System.out.println("GetToolDIConfigLevel rtn is " + rtn + ", value is " + getToolDIConfigLevel[0] + " " + getToolDIConfigLevel[1]);

        int[] setStandardDILevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getStandardDILevel = new int[8];
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        System.out.println("SetStandardDILevel rtn is " + rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        System.out.println("GetStandardDILevel rtn is " + rtn + ", value is " + 
            getStandardDILevel[0] + " " + getStandardDILevel[1] + " " + getStandardDILevel[2] + " " + getStandardDILevel[3] + " " + 
            getStandardDILevel[4] + " " + getStandardDILevel[5] + " " + getStandardDILevel[6] + " " + getStandardDILevel[7]);

        int[] setStandardDOLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getStandardDOLevel = new int[8];
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        System.out.println("SetStandardDOLevel rtn is " + rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        System.out.println("GetStandardDOLevel rtn is " + rtn + ", value is " + 
            getStandardDOLevel[0] + " " + getStandardDOLevel[1] + " " + getStandardDOLevel[2] + " " + getStandardDOLevel[3] + " " + 
            getStandardDOLevel[4] + " " + getStandardDOLevel[5] + " " + getStandardDOLevel[6] + " " + getStandardDOLevel[7]);

        robot.Sleep(2000);
        return 0;
    }