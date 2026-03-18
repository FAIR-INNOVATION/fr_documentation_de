Roboter-I/O
===========

.. toctree::
    :maxdepth: 5

Digitalausgang des Steuerkastens setzen
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDO(id, status, smooth=0, block=0)``"
    "Beschreibung", "Digitalausgang des Steuerkastens setzen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~15]
    - ``status``: 0 = aus, 1 = ein"
    "Standardparameter", "- ``smooth``: 0 = nicht glätten, 1 = glätten, Standard = 0
    - ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Digitalausgang des Werkzeugs setzen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolDO(id, status, smooth=0, block=0)``"
    "Beschreibung", "Digitalausgang des Werkzeugs setzen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~1]
    - ``status``: 0 = aus, 1 = ein"
    "Standardparameter", "- ``smooth``: 0 = nicht glätten, 1 = glätten, Standard = 0
    - ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Analogausgang des Steuerkastens setzen
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAO(id, value, block=0)``"
    "Beschreibung", "Analogausgang des Steuerkastens setzen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~1]
    - ``value``: Prozentwert des Stroms oder der Spannung, Bereich [0~100%] entspricht [0~20mA] oder [0~10V]"
    "Standardparameter", "- ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Analogausgang des Werkzeugs setzen
+++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolAO(id, value, block=0)``"
    "Beschreibung", "Analogausgang des Werkzeugs setzen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0]
    - ``value``: Prozentwert des Stroms oder der Spannung, Bereich [0~100%] entspricht [0~20mA] oder [0~10V]"
    "Standardparameter", "- ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Setzen von Digital- und Analogausgängen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0  
    block = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3) 
    status = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1) 
    status = 0 
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    robot.CloseRPC()

Digitaleingang des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDI(id, block=0)``"
    "Beschreibung", "Digitaleingang des Steuerkastens abrufen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~15]"
    "Standardparameter", "- ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``di``: 0 = niedriger Pegel, 1 = hoher Pegel"

Digitaleingang des Werkzeugs abrufen
+++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDI(id, block=0)``"
    "Beschreibung", "Digitaleingang des Werkzeugs abrufen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~1]"
    "Standardparameter", "- ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``di``: 0 = niedriger Pegel, 1 = hoher Pegel"

Analogeingang des Steuerkastens abrufen
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAI(id, block=0)``"
    "Beschreibung", "Analogeingang des Steuerkastens abrufen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~1]"
    "Standardparameter", "- ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``value``: Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]"

Analogeingang des Werkzeugs abrufen
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolAI(id, block=0)``"
    "Beschreibung", "Analogeingang des Endeffektors abrufen"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0]"
    "Standardparameter", "- ``block``: 0 = blockierend, 1 = nicht blockierend, Standard = 0"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``value``: Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]"

Status der Aufnahmetaste am Roboterende abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxlePointRecordBtnState()``"
    "Beschreibung", "Status der Aufnahmetaste am Roboterende abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``buttonstatus``: Tastenstatus, 0 = gedrückt, 1 = losgelassen"

Ausgangszustand des Werkzeug-DO abrufen
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDO()``"
    "Beschreibung", "Ausgangszustand des Werkzeug-DO abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``do_state``: DO-Ausgangszustand, do0~do1 entsprechen Bit1~Bit2, beginnend bei Bit0"

Ausgangszustand des Robotercontroller-DO abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDO()``"
    "Beschreibung", "Ausgangszustand des Robotercontroller-DO abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``do_state_h``: DO-Ausgangszustand, co0~co7 entsprechen Bit0~Bit7"

Codebeispiel zum Abrufen von DI- und DO-Status
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    block = 0 
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}") 
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error,[do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state hight  : {do_state_h}")
    print(f"DO state low : {do_state_l}")
    robot.CloseRPC()

Auf Digitaleingang des Steuerkastens warten
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitDI(id, status, maxtime, opt)``"
    "Beschreibung", "Auf Digitaleingang des Steuerkastens warten"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~15]
    - ``status``: 0 = aus, 1 = ein
    - ``maxtime``: Maximale Wartezeit [ms]
    - ``opt``: Strategie bei Timeout: 0 = Programm stoppen und Timeout melden, 1 = Timeout ignorieren und Programm fortsetzen, 2 = unbegrenzt warten"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Auf mehrere Digitaleingänge des Steuerkastens warten
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitMultiDI(mode, id, status, maxtime, opt)``"
    "Beschreibung", "Auf mehrere Digitaleingänge des Steuerkastens warten"
    "Erforderliche Parameter", "- ``mode``: 0 = UND-Verknüpfung, 1 = ODER-Verknüpfung
    - ``id``: IO-Nummern als Bitmaske: Bit0~Bit7 für DI0~DI7, Bit8~Bit15 für CI0~CI7
    - ``status``: Erwarteter Zustand als Bitmaske: Bit0~Bit7 für DI0~DI7, Bit8~Bit15 für CI0~CI7, Bit = 0 = aus, Bit = 1 = ein
    - ``maxtime``: Maximale Wartezeit [ms]
    - ``opt``: Strategie bei Timeout: 0 = Programm stoppen und Timeout melden, 1 = Timeout ignorieren und Programm fortsetzen, 2 = unbegrenzt warten"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Auf Digitaleingang des Werkzeugs warten
++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitToolDI(id, status, maxtime, opt)``"
    "Beschreibung", "Auf Digitaleingang des Endeffektors warten"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~1]
    - ``status``: 0 = aus, 1 = ein
    - ``maxtime``: Maximale Wartezeit [ms]
    - ``opt``: Strategie bei Timeout: 0 = Programm stoppen und Timeout melden, 1 = Timeout ignorieren und Programm fortsetzen, 2 = unbegrenzt warten"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Auf Analogeingang des Steuerkastens warten
+++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitAI(id, sign, value, maxtime, opt)``"
    "Beschreibung", "Auf Analogeingang des Steuerkastens warten"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0~1]
    - ``sign``: 0 = größer als, 1 = kleiner als
    - ``value``: Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    - ``maxtime``: Maximale Wartezeit [ms]
    - ``opt``: Strategie bei Timeout: 0 = Programm stoppen und Timeout melden, 1 = Timeout ignorieren und Programm fortsetzen, 2 = unbegrenzt warten"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Auf Analogeingang des Werkzeugs warten
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitToolAI(id, sign, value, maxtime, opt)``"
    "Beschreibung", "Auf Analogeingang des Endeffektors warten"
    "Erforderliche Parameter", "- ``id``: IO-Nummer, Bereich [0]
    - ``sign``: 0 = größer als, 1 = kleiner als
    - ``value``: Prozentwert des Eingangsstroms oder der -spannung, Bereich [0~100] entspricht [0~20mA] oder [0~10V]
    - ``maxtime``: Maximale Wartezeit [ms]
    - ``opt``: Strategie bei Timeout: 0 = Programm stoppen und Timeout melden, 1 = Timeout ignorieren und Programm fortsetzen, 2 = unbegrenzt warten"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Warten auf digitale und analoge Eingangssignale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0
    block = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    status = 0
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    block = 0
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}")
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error, [do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state high: {do_state_h}")
    print(f"DO state low: {do_state_l}")
    rtn = robot.WaitDI(0, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitMultiDI(1, 3, 3, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolDI(1, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    robot.CloseRPC()

Festlegen, ob der Steuerkasten-DO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetCtlBoxDO(resetFlag, reloadFlag)``"
    "Beschreibung", "Festlegen, ob der Steuerkasten-DO nach Stopp/Pause zurückgesetzt wird"
    "Erforderliche Parameter", "- ``resetFlag``: 0 = nicht zurücksetzen, 1 = zurücksetzen
    - ``reloadFlag``: Ob nach Pausenfortsetzung neu geladen wird: 0 = nicht laden, 1 = laden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Festlegen, ob der Steuerkasten-AO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetCtlBoxAO(resetFlag, reloadFlag)``"
    "Beschreibung", "Festlegen, ob der Steuerkasten-AO nach Stopp/Pause zurückgesetzt wird"
    "Erforderliche Parameter", "
    - ``resetFlag``: 0 = nicht zurücksetzen, 1 = zurücksetzen
    - ``reloadFlag``: Ob nach Pausenfortsetzung neu geladen wird: 0 = nicht laden, 1 = laden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Festlegen, ob der Werkzeug-DO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetAxleDO(resetFlag, reloadFlag)``"
    "Beschreibung", "Festlegen, ob der Werkzeug-DO nach Stopp/Pause zurückgesetzt wird"
    "Erforderliche Parameter", "
    - ``resetFlag``: 0 = nicht zurücksetzen, 1 = zurücksetzen
    - ``reloadFlag``: Ob nach Pausenfortsetzung neu geladen wird: 0 = nicht laden, 1 = laden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Festlegen, ob der Werkzeug-AO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetAxleAO(resetFlag, reloadFlag)``"
    "Beschreibung", "Festlegen, ob der Werkzeug-AO nach Stopp/Pause zurückgesetzt wird"
    "Erforderliche Parameter", "
    - ``resetFlag``: 0 = nicht zurücksetzen, 1 = zurücksetzen
    - ``reloadFlag``: Ob nach Pausenfortsetzung neu geladen wird: 0 = nicht laden, 1 = laden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Festlegen, ob der erweiterte DO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetExtDO(resetFlag, reloadFlag)``"
    "Beschreibung", "Festlegen, ob der erweiterte DO nach Stopp/Pause zurückgesetzt wird"
    "Erforderliche Parameter", "
    - ``resetFlag``: 0 = nicht zurücksetzen, 1 = zurücksetzen
    - ``reloadFlag``: Ob nach Pausenfortsetzung neu geladen wird: 0 = nicht laden, 1 = laden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Festlegen, ob der erweiterte AO nach Stopp/Pause zurückgesetzt wird
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetExtAO(resetFlag, reloadFlag)``"
    "Beschreibung", "Festlegen, ob der erweiterte AO nach Stopp/Pause zurückgesetzt wird"
    "Erforderliche Parameter", "
    - ``resetFlag``: 0 = nicht zurücksetzen, 1 = zurücksetzen
    - ``reloadFlag``: Ob nach Pausenfortsetzung neu geladen wird: 0 = nicht laden, 1 = laden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Festlegen, ob der SmartTool-DO nach Stopp/Pause zurückgesetzt wird
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetSmartToolDO(resetFlag, reloadFlag)``"
    "Beschreibung", "Festlegen, ob der SmartTool-DO nach Stopp/Pause zurückgesetzt wird"
    "Erforderliche Parameter", "
    - ``resetFlag``: 0 = nicht zurücksetzen, 1 = zurücksetzen
    - ``reloadFlag``: Ob nach Pausenfortsetzung neu geladen wird: 0 = nicht laden, 1 = laden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Festlegen des Ausgangs-Rücksetzverhaltens nach Stopp/Pause für LUA-Programme
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    for i in range(16):
        robot.SetDO(i, 1, 0, 0)
        time.sleep(0.2)
    resetFlag = 0
    resumeReloadFlag = 0
    rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag)
    robot.ProgramLoad("/fruser/test.lua")
    robot.ProgramRun()
    time.sleep(2)
    robot.PauseMotion()
    time.sleep(2)
    robot.ResumeMotion()
    time.sleep(2)
    robot.CloseRPC()
    return 0