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