Roboter-I/O
============

.. toctree::
    :maxdepth: 5

Digitalausgang des Steuerschranks setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Setzt einen digitalen Ausgang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~15]
    * @param  [in] status 0-aus, 1-ein
    * @param  [in] smooth 0-nicht glätten, 1-glätten
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @return  Fehlercode.
    */
    errno_t SetDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Digitalausgang des Werkzeugs setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Setzt einen digitalen Ausgang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0~1]
    * @param  [in] status 0-aus, 1-ein
    * @param  [in] smooth 0-nicht glätten, 1-glätten
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @return  Fehlercode.
    */
    errno_t SetToolDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Analogausgang des Steuerschranks setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Setzt einen analogen Ausgang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~1]
    * @param  [in] value  Prozentwert des Stroms oder der Spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V]
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @return  Fehlercode.
    */
    errno_t SetAO(int id, float value, uint8_t block);

Analogausgang des Werkzeugs setzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Setzt einen analogen Ausgang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0]
    * @param  [in] value  Prozentwert des Stroms oder der Spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V]
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @return  Fehlercode.
    */
    errno_t SetToolAO(int id, float value, uint8_t block);

Codebeispiel zum Setzen von Digital- und Analogausgängen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAODO(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        uint8_t status = 1;
        uint8_t smooth = 0;
        uint8_t block = 0;
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
            robot.SetAO(0, i * 40.96, block);
            robot.Sleep(30);
        }
        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i * 40.96, block);
            robot.Sleep(30);
        }
        robot.CloseRPC();
        return 0;
    }

Digitaleingang des Steuerschranks abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt den Zustand eines digitalen Eingangs des Steuerschranks zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0~15]
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @param  [out] result  0-niedriger Pegel, 1-hoher Pegel
    * @return  Fehlercode.
    */
    errno_t GetDI(int id, uint8_t block, uint8_t *result);

Digitaleingang des Werkzeugs abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt den Zustand eines digitalen Eingangs des Werkzeugs zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0~1]
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @param  [out] result  0-niedriger Pegel, 1-hoher Pegel
    * @return  Fehlercode.
    */
    errno_t GetToolDI(int id, uint8_t block, uint8_t *result);

Analogeingang des Steuerschranks abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt den Wert eines analogen Eingangs des Steuerschranks zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0~1]
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @param  [out] result  Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V]
    * @return  Fehlercode.
    */
    errno_t GetAI(int id, uint8_t block, float *result);

Analogeingang des Werkzeugs abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt den Wert eines analogen Eingangs des Werkzeugs zurück.
    * @param  [in] id  I/O-Nummer, Bereich [0]
    * @param  [in] block  0-blockierend, 1-nicht blockierend
    * @param  [out] result  Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V]
    * @return  Fehlercode.
    */
    errno_t GetToolAI(int id, uint8_t block, float *result);

Status der Punktaufzeichnungstaste am Roboterende abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt den Status der Punktaufzeichnungstaste am Roboterende zurück.
     * @param [out] state Tastenstatus, 0-gedrückt, 1-losgelassen
     * @return Fehlercode.
     */
    errno_t GetAxlePointRecordBtnState(uint8_t *state);

DO-Ausgangsstatus am Roboterende abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt den DO-Ausgangsstatus am Roboterende zurück.
     * @param [out] do_state DO-Ausgangsstatus, do0~do1 entsprechen bit1~bit2, beginnend bei bit0.
     * @return Fehlercode.
     */
    errno_t GetToolDO(uint8_t *do_state);

DO-Ausgangsstatus des Robotersteuerschranks abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt den DO-Ausgangsstatus des Robotersteuerschranks zurück.
     * @param [out] do_state_h DO-Ausgangsstatus, co0~co7 entsprechen bit0~bit7.
     * @param [out] do_state_l DO-Ausgangsstatus, do0~do7 entsprechen bit0~bit7.
     * @return Fehlercode.
     */
    errno_t GetDO(uint8_t *do_state_h, uint8_t *do_state_l);

Codebeispiel zum Abrufen von Roboter-DI/DO-Status
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetDIAI(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        uint8_t status = 1;
        uint8_t smooth = 0;
        uint8_t block = 0;
        uint8_t di = 0, tool_di = 0;
        float ai = 0.0, tool_ai = 0.0;
        robot.GetDI(0, block, &di);
        printf("di0:%u\n", di);
        robot.GetToolDI(1, block, &tool_di);
        printf("tool_di1:%u\n", tool_di);
        robot.GetAI(0, block, &ai);
        printf("ai0:%f\n", ai);
        robot.GetToolAI(0, block, &tool_ai);
        printf("tool_ai0:%f\n", tool_ai);
        uint8_t _button_state = 0;
        robot.GetAxlePointRecordBtnState(&_button_state);
        printf("_button_state is: %u\n", _button_state);
        uint8_t tool_do_state = 0;
        robot.GetToolDO(&tool_do_state);
        printf("tool DO state is: %u\n", tool_do_state);
        uint8_t do_state_h = 0;
        uint8_t do_state_l = 0;
        robot.GetDO(&do_state_h, &do_state_l);
        printf("DO state high is: %u \n DO state low is: %u\n", do_state_h, do_state_l);
        robot.CloseRPC();
        return 0;
    }

Auf digitalen Eingang des Steuerschranks warten
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wartet auf einen digitalen Eingang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~15]
    * @param  [in] status 0-aus, 1-ein
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return  Fehlercode.
    */
    errno_t WaitDI(int id, uint8_t status, int max_time, int opt);

Auf mehrere digitale Eingänge des Steuerschranks warten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wartet auf mehrere digitale Eingänge des Steuerschranks.
    * @param  [in] mode 0-UND-Verknüpfung aller Kanäle, 1-ODER-Verknüpfung aller Kanäle
    * @param  [in] id  I/O-Nummern als Bitmaske, Bits 0-7 für DI0-DI7, Bits 8-15 für CI0-CI7
    * @param  [in] status 0-aus, 1-ein
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return  Fehlercode.
    */
    errno_t WaitMultiDI(int mode, int id, uint8_t status, int max_time, int opt);

Auf digitalen Eingang des Werkzeugs warten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wartet auf einen digitalen Eingang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0~1]
    * @param  [in] status 0-aus, 1-ein
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return  Fehlercode.
    */
    errno_t WaitToolDI(int id, uint8_t status, int max_time, int opt);

Auf analogen Eingang des Steuerschranks warten
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wartet auf einen analogen Eingang des Steuerschranks.
    * @param  [in] id  I/O-Nummer, Bereich [0~1]
    * @param  [in] sign 0-größer als, 1-kleiner als
    * @param  [in] value  Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V]
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return  Fehlercode.
    */
    errno_t WaitAI(int id, int sign, float value, int max_time, int opt);

Auf analogen Eingang des Werkzeugs warten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wartet auf einen analogen Eingang des Werkzeugs.
    * @param  [in] id  I/O-Nummer, Bereich [0]
    * @param  [in] sign 0-größer als, 1-kleiner als
    * @param  [in] value  Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht Strom [0~20 mA] oder Spannung [0~10 V]
    * @param  [in] max_time  Maximale Wartezeit, Einheit ms
    * @param  [in] opt  Strategie bei Zeitüberschreitung: 0-Programm stoppen und Timeout melden, 1-Timeout ignorieren und Programm fortsetzen, 2-unbegrenzt warten
    * @return  Fehlercode.
    */
    errno_t WaitToolAI(int id, int sign, float value, int max_time, int opt);

Codebeispiel zum Warten auf digitale/analoge Eingangssignale des Steuerschranks
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

     int TestWaitDIAI(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         uint8_t di = 0, tool_di = 0;
         float ai = 0.0, tool_ai = 0.0;
         float value = 0.0;
         rtn = robot.WaitDI(0, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitMultiDI(1, 3, 3, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolDI(1, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Einstellung, ob DO-Ausgänge des Steuerschranks nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt fest, ob die DO-Ausgänge des Steuerschranks nach einem Stopp/Pause zurückgesetzt werden.
    * @param [in] resetFlag 0-nicht zurücksetzen; 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden
    * @return Fehlercode.
    */
    errno_t SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag = 0);

Einstellung, ob AO-Ausgänge des Steuerschranks nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt fest, ob die AO-Ausgänge des Steuerschranks nach einem Stopp/Pause zurückgesetzt werden.
    * @param [in] resetFlag  0-nicht zurücksetzen; 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden
    * @return Fehlercode.
    */
    errno_t SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag = 0);

Einstellung, ob DO-Ausgänge des Endeffektorwerkzeugs nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt fest, ob die DO-Ausgänge des Endeffektorwerkzeugs nach einem Stopp/Pause zurückgesetzt werden.
    * @param [in] resetFlag  0-nicht zurücksetzen; 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden
    * @return Fehlercode.
    */
    errno_t SetOutputResetAxleDO(int resetFlag, int reloadFlag = 0);

Einstellung, ob AO-Ausgänge des Endeffektorwerkzeugs nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt fest, ob die AO-Ausgänge des Endeffektorwerkzeugs nach einem Stopp/Pause zurückgesetzt werden.
    * @param [in] resetFlag  0-nicht zurücksetzen; 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden
    * @return  Fehlercode.
    */
    errno_t SetOutputResetAxleAO(int resetFlag, int reloadFlag = 0);

Einstellung, ob erweiterte DO-Ausgänge nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt fest, ob die erweiterten DO-Ausgänge nach einem Stopp/Pause zurückgesetzt werden.
    * @param [in] resetFlag  0-nicht zurücksetzen; 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden
    * @return  Fehlercode.
    */
    errno_t SetOutputResetExtDO(int resetFlag, int reloadFlag = 0);

Einstellung, ob erweiterte AO-Ausgänge nach Stopp/Pause zurückgesetzt werden
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt fest, ob die erweiterten AO-Ausgänge nach einem Stopp/Pause zurückgesetzt werden.
    * @param [in] resetFlag  0-nicht zurücksetzen; 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden
    * @return  Fehlercode.
    */
    errno_t SetOutputResetExtAO(int resetFlag, int reloadFlag = 0);

Einstellung, ob SmartTool-DO-Ausgänge nach Stopp/Pause zurückgesetzt werden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt fest, ob die SmartTool-DO-Ausgänge nach einem Stopp/Pause zurückgesetzt werden.
    * @param [in] resetFlag  0-nicht zurücksetzen; 1-zurücksetzen
    * @param [in] reloadFlag Ob nach Wiederaufnahme der Pause neu geladen werden soll, 0-nicht laden; 1-laden
    * @return  Fehlercode.
    */
    errno_t SetOutputResetSmartToolDO(int resetFlag, int reloadFlag = 0);

Codebeispiel zum Zurücksetzen der Ausgänge nach LUA-Programmstopp/-pause
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestDOReset(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(3);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            robot.Sleep(200);
        }
        int resetFlag = 0;
        int resumeReloadFlag = 0;
        rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag);
        robot.ProgramLoad("/fruser/test.lua");
        robot.ProgramRun();
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);
        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.CloseRPC();
        return 0;
    }

Konfigurierbare CI-Portfunktionen des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetDIConfig(int config[8]);

Konfigurierbare CI-Portfunktionen des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t GetDIConfig(int config[8]);

Konfigurierbare CO-Portfunktionen des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetDOConfig(int config[8]);

Konfigurierbare CO-Portfunktionen des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t GetDOConfig(int config[8]);

Konfigurierbare End-CI-Portfunktionen des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetToolDIConfig(int config[2]);

Konfigurierbare End-CI-Portfunktionen des Endeffektors abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t GetToolDIConfig(int config[2]);
    
Konfigurierbaren CI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CI-Aktivzustands des Steuerkastens
    * @param [in] config CI0-CI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t SetDIConfigLevel(int config[8]);
        
Konfigurierbaren CI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CI-Aktivzustands des Steuerkastens
    * @param [out] config CI0-CI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t GetDIConfigLevel(int config[8]);
        
Konfigurierbaren CO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CO-Aktivzustands des Steuerkastens
    * @param [in] config CO0-CO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t SetDOConfigLevel(int config[8]);

Konfigurierbaren CO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CO-Aktivzustands des Steuerkastens
    * @param [out] config CO0-CO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t GetDOConfigLevel(int config[8]);
    
Konfigurierbaren CI-Aktivzustand des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Einstellen des konfigurierbaren CI-Aktivzustands des Endeffektors
    * @param [in] config CI0-CI1 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t SetToolDIConfigLevel(int config[2]);
    
Konfigurierbaren CI-Aktivzustand des Endeffektors abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Abrufen des konfigurierbaren CI-Aktivzustands des Endeffektors
    * @param [out] config CI0-CI1 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t GetToolDIConfigLevel(int config[2]);
    
Standard-DI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Einstellen des Standard-DI-Aktivzustands des Steuerkastens
    * @param [in] config DI0-DI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t SetStandardDILevel(int config[8]);
    
Standard-DI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Abrufen des Standard-DI-Aktivzustands des Steuerkastens
    * @param [out] config DI0-DI7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t GetStandardDILevel(int config[8]);

Standard-DO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Einstellen des Standard-DO-Aktivzustands des Steuerkastens
    * @param [in] config DO0-DO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t SetStandardDOLevel(int config[8]);
    
Standard-DO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Abrufen des Standard-DO-Aktivzustands des Steuerkastens
    * @param [out] config DO0-DO7 Port-Aktivzustand; 0-aktiv high; 1-aktiv low
    * @return Fehlercode
    */
    errno_t GetStandardDOLevel(int config[8]);
        
Robot IO Konfigurationscodebeispiel
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestIOConfig()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        int setDIConfig[8] = { 1, 2, 3, 4, 5, 6, 7, 8 };
        int getDIConfig[8] = { 0 };
        rtn = robot.SetDIConfig(setDIConfig);
        printf("SetDIConfig rtn is %d\n", rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn, 
            getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);
        int setDOConfig[8] = { 9, 10, 11, 12, 13, 14, 15, 16 };
        int getDOConfig[8] = { 0 };
        rtn = robot.SetDOConfig(setDOConfig);
        printf("SetDOConfig rtn is %d\n", rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);
        int setToolDIConfig[2] = { 17, 18 };
        int getToolDIConfig[2] = { 0 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        printf("SetToolDIConfig rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        printf("GetToolDIConfig rtn is %d, value is %d %d \n", rtn, getToolDIConfig[0], getToolDIConfig[1]);
        int setDIConfigLevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getDIConfigLevel[8] = { 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        printf("SetDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        printf("GetDIConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDIConfigLevel[0], getDIConfigLevel[1], getDIConfigLevel[2], getDIConfigLevel[3], getDIConfigLevel[4], getDIConfigLevel[5], getDIConfigLevel[6], getDIConfigLevel[7]);
        int setDOConfigLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getDOConfigLevel[8] = { 0 };
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        printf("SetDOConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        printf("GetDOConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfigLevel[0], getDOConfigLevel[1], getDOConfigLevel[2], getDOConfigLevel[3], getDOConfigLevel[4], getDOConfigLevel[5], getDOConfigLevel[6], getDOConfigLevel[7]);
        int setToolDIConfigLevel[2] = { 1, 0 };
        int getToolDIConfigLevel[2] = { 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        printf("SetToolDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        printf("GetToolDIConfigLevel rtn is %d, value is %d %d \n", rtn, getToolDIConfigLevel[0], getToolDIConfigLevel[1]);
        int setStandardDILevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getStandardDILevel[8] = { 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        printf("SetStandardDILevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        printf("GetStandardDILevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDILevel[0], getStandardDILevel[1], getStandardDILevel[2], getStandardDILevel[3], getStandardDILevel[4], getStandardDILevel[5], getStandardDILevel[6], getStandardDILevel[7]);
        int setStandardDOLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getStandardDOLevel[8] = { 0 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        printf("SetStandardDOLevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        printf("GetStandsrdDOLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDOLevel[0], getStandardDOLevel[1], getStandardDOLevel[2], getStandardDOLevel[3], getStandardDOLevel[4], getStandardDOLevel[5], getStandardDOLevel[6], getStandardDOLevel[7]);
        robot.Sleep(2000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }