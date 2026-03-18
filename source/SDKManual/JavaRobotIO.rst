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
        robot.ProgramLoad("/fruser/test.lua");
        robot.ProgramRun();
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);
        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.CloseRPC();
    }