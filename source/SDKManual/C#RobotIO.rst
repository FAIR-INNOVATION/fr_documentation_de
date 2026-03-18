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