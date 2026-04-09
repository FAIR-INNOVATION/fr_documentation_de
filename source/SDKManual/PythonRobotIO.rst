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

Konfigurierbare CI-Portfunktionen einstellen
+++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDIConfig(config)``"
    "Beschreibung", "Konfigurierbare CI-Portfunktionen einstellen"
    "Erforderliche Parameter", "
    - ``config``: CI0-CI7 Funktionscode-Array, 0-Keine;1-Lichtbogenstart erfolgreich;2-Schweißgerät bereit;3-Förderbanderkennung;4-Pause;5-Fortsetzen;6-Start;7-Stopp;
      8-Pause/Fortsetzen;9-Start/Stopp;10-Fußtaster-Ziehen;11-Zur Arbeitsposition bewegen;12-Manuell/Auto umschalten;
      13-Drahtpositionssuche erfolgreich;14-Bewegungsunterbrechung;15-Hauptprogramm starten;16-Rückspulen starten;17-Startbestätigung;
      18-Photoelektrisches Erkennungssignal X;19-Photoelektrisches Erkennungssignal Y;20-Externer Not-Halt-Eingangssignal 1;21-Externer Not-Halt-Eingangssignal 2;
      22-Stufe 1 Reduzierungsmodus;23-Stufe 2 Reduzierungsmodus;24-Stufe 3 Reduzierungsmodus (Stopp);25-Schweißen fortsetzen;26-Schweißen beenden;
      27-Hilfszug aktivieren;28-Hilfszug deaktivieren;29-Hilfszug aktivieren/deaktivieren;30-Alle Fehler löschen;
      31-Manuell/Auto umschalten (High/Low-Pegel);32-Aktivieren;33-Deaktivieren;34-Aktivieren/Deaktivieren (steigende/fallende Flanke);35-Fixpunkt-Tracking starten/beenden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbare CI-Portfunktionen des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDIConfig()``"
    "Beschreibung", "Konfigurierbare CI-Portfunktionen des Steuerkastens abrufen"
    "Erforderliche Parameter", "
    - ``config``: CI0-CI7 Funktionscode-Array, 0-Keine;1-Lichtbogenstart erfolgreich;2-Schweißgerät bereit;3-Förderbanderkennung;4-Pause;5-Fortsetzen;6-Start;7-Stopp;
      8-Pause/Fortsetzen;9-Start/Stopp;10-Fußtaster-Ziehen;11-Zur Arbeitsposition bewegen;12-Manuell/Auto umschalten;
      13-Drahtpositionssuche erfolgreich;14-Bewegungsunterbrechung;15-Hauptprogramm starten;16-Rückspulen starten;17-Startbestätigung;
      18-Photoelektrisches Erkennungssignal X;19-Photoelektrisches Erkennungssignal Y;20-Externer Not-Halt-Eingangssignal 1;21-Externer Not-Halt-Eingangssignal 2;
      22-Stufe 1 Reduzierungsmodus;23-Stufe 2 Reduzierungsmodus;24-Stufe 3 Reduzierungsmodus (Stopp);25-Schweißen fortsetzen;26-Schweißen beenden;
      27-Hilfszug aktivieren;28-Hilfszug deaktivieren;29-Hilfszug aktivieren/deaktivieren;30-Alle Fehler löschen;
      31-Manuell/Auto umschalten (High/Low-Pegel);32-Aktivieren;33-Deaktivieren;34-Aktivieren/Deaktivieren (steigende/fallende Flanke);35-Fixpunkt-Tracking starten/beenden"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbare CO-Portfunktionen einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDOConfig(config)``"
    "Beschreibung", "Konfigurierbare CO-Portfunktionen einstellen"
    "Erforderliche Parameter", "
    - ``config``: CO0-CO7 Funktionscode-Array, 0-Keine;1-Roboterfehler;2-Roboter in Bewegung;3-Spritzen start/stopp;4-Spritzpistolenreinigung;5-Gaszufuhrsignal;6-Lichtbogenstartsignal;7-Tippen Drahtvorschub;
      8-Rückwärts Drahtvorschub;9-JOB-Eingang 1;10-JOB-Eingang 2;11-JOB-Eingang 3;12-Förderband start/stopp Steuerung;13-Roboter pausiert;14-Arbeitsposition erreicht;
      15-Interferenzbereich erreicht;16-Drahtpositionssuche start/stopp Steuerung;17-Roboterstart abgeschlossen;18-Programm start/stopp;19-Auto/Manuell-Modus;20-Not-Halt-Ausgangssignal 1-Sicherheit;
      21-Not-Halt-Ausgangssignal 2-Sicherheit;22-Lua-Skriptprogramm läuft/gestoppt;23-Sicherheitsstatusausgang-Sicherheit;24-Schutzstopp-Statusausgang-Sicherheit;
      25-Roboter in Bewegung-Sicherheit;26-Roboter im Reduzierungsmodus-Sicherheit;27-Roboter nicht im Reduzierungsmodus-Sicherheit;28-Roboter nicht gestoppt;29-Roboterfehler-Befehlspunktfehler;
      30-Roboterfehler-Antriebsfehler;31-Roboterfehler-Weichgrenze überschritten;32-Roboterfehler-Kollisionsfehler;33-Roboterfehler-Fehler bei Anzahl aktiver Slaves;
      34-Roboterfehler-Slave-Fehler;35-Roboterfehler-IO-Fehler;36-Roboterfehler-Greiferfehler;37-Roboterfehler-Dateifehler;38-Roboterfehler-Singuläre Pose;
      39-Roboterfehler-Antriebskommunikationsfehler;40-Roboterfehler-Parameterfehler;41-Roboterfehler-Externe Achse Weichgrenze überschritten;42-Roboterwarnung-Warnung;
      43-Roboterwarnung-Sicherheitstürwarnung;44-Roboterwarnung-Bewegungswarnung;45-Roboterwarnung-Interferenzbereichswarnung;46-Roboterwarnung-Sicherheitswandwarnung;
      47-Aktivierungsstatus;48-Automatisches Anheben bei Unterbrechung;49-Würfel 1 Interferenzwarnung;50-Würfel 2 Interferenzwarnung;51-Würfel 3 Interferenzwarnung;52-Würfel 4 Interferenzwarnung;"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbare CO-Portfunktionen abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDOConfig()``"
    "Beschreibung", "Konfigurierbare CO-Portfunktionen abrufen"
    "Erforderliche Parameter", "
    - ``config``: CO0-CO7 Funktionscode-Array, 0-Keine;1-Roboterfehler;2-Roboter in Bewegung;3-Spritzen start/stopp;4-Spritzpistolenreinigung;5-Gaszufuhrsignal;6-Lichtbogenstartsignal;7-Tippen Drahtvorschub;
      8-Rückwärts Drahtvorschub;9-JOB-Eingang 1;10-JOB-Eingang 2;11-JOB-Eingang 3;12-Förderband start/stopp Steuerung;13-Roboter pausiert;14-Arbeitsposition erreicht;
      15-Interferenzbereich erreicht;16-Drahtpositionssuche start/stopp Steuerung;17-Roboterstart abgeschlossen;18-Programm start/stopp;19-Auto/Manuell-Modus;20-Not-Halt-Ausgangssignal 1-Sicherheit;
      21-Not-Halt-Ausgangssignal 2-Sicherheit;22-Lua-Skriptprogramm läuft/gestoppt;23-Sicherheitsstatusausgang-Sicherheit;24-Schutzstopp-Statusausgang-Sicherheit;
      25-Roboter in Bewegung-Sicherheit;26-Roboter im Reduzierungsmodus-Sicherheit;27-Roboter nicht im Reduzierungsmodus-Sicherheit;28-Roboter nicht gestoppt;29-Roboterfehler-Befehlspunktfehler;
      30-Roboterfehler-Antriebsfehler;31-Roboterfehler-Weichgrenze überschritten;32-Roboterfehler-Kollisionsfehler;33-Roboterfehler-Fehler bei Anzahl aktiver Slaves;
      34-Roboterfehler-Slave-Fehler;35-Roboterfehler-IO-Fehler;36-Roboterfehler-Greiferfehler;37-Roboterfehler-Dateifehler;38-Roboterfehler-Singuläre Pose;
      39-Roboterfehler-Antriebskommunikationsfehler;40-Roboterfehler-Parameterfehler;41-Roboterfehler-Externe Achse Weichgrenze überschritten;42-Roboterwarnung-Warnung;
      43-Roboterwarnung-Sicherheitstürwarnung;44-Roboterwarnung-Bewegungswarnung;45-Roboterwarnung-Interferenzbereichswarnung;46-Roboterwarnung-Sicherheitswandwarnung;
      47-Aktivierungsstatus;48-Automatisches Anheben bei Unterbrechung;49-Würfel 1 Interferenzwarnung;50-Würfel 2 Interferenzwarnung;51-Würfel 3 Interferenzwarnung;52-Würfel 4 Interferenzwarnung;"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbare End-CI-Portfunktionen des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolDIConfig(config)``"
    "Beschreibung", "Konfigurierbare End-CI-Portfunktionen des Endeffektors einstellen"
    "Erforderliche Parameter", "
    - ``config``: End CI0-CI1 Funktionscode-Array, 0-Keine;1-Zieh-Teaching-Werkzeugschalter;2-Punktaufzeichnungssignal;3-Manuell/Auto umschalten (Impulssignal);4-TPD-Aufzeichnung start/stopp;5-Bewegung pausieren;
      6-Bewegung fortsetzen;7-Start;8-Stopp;9-Pause/Fortsetzen;10-Start/Stopp;11-Kraftsensor-Hilfszug aktivieren;12-Kraftsensor-Hilfszug deaktivieren;
      13-Kraftsensor-Hilfszug aktivieren/deaktivieren;14-Lasererkennungssignal X;15-Lasererkennungssignal Y;16-PTP-Bewegung zur Arbeitsposition;17-Bewegungsunterbrechung, aktuelle Bewegung je nach Signal stoppen;
      18-Hauptprogramm starten;19-Rückspulen starten;20-Startbestätigung;21-Schweißen fortsetzen;22-Schweißen beenden;23-Fehler löschen;24-Manuell/Auto umschalten (High/Low-Pegel);
      25-Aktivieren;26-Deaktivieren;27-Aktivieren/Deaktivieren;28-Laser-Servo-Tracking start/stopp Signal;"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbare End-CI-Portfunktionen des Endeffektors abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDIConfig()``"
    "Beschreibung", "Konfigurierbare End-CI-Portfunktionen des Endeffektors abrufen"
    "Erforderliche Parameter", "
    - ``config``: End CI0-CI1 Funktionscode-Array, 0-Keine;1-Zieh-Teaching-Werkzeugschalter;2-Punktaufzeichnungssignal;3-Manuell/Auto umschalten (Impulssignal);4-TPD-Aufzeichnung start/stopp;5-Bewegung pausieren;
      6-Bewegung fortsetzen;7-Start;8-Stopp;9-Pause/Fortsetzen;10-Start/Stopp;11-Kraftsensor-Hilfszug aktivieren;12-Kraftsensor-Hilfszug deaktivieren;
      13-Kraftsensor-Hilfszug aktivieren/deaktivieren;14-Lasererkennungssignal X;15-Lasererkennungssignal Y;16-PTP-Bewegung zur Arbeitsposition;17-Bewegungsunterbrechung, aktuelle Bewegung je nach Signal stoppen;
      18-Hauptprogramm starten;19-Rückspulen starten;20-Startbestätigung;21-Schweißen fortsetzen;22-Schweißen beenden;23-Fehler löschen;24-Manuell/Auto umschalten (High/Low-Pegel);
      25-Aktivieren;26-Deaktivieren;27-Aktivieren/Deaktivieren;28-Laser-Servo-Tracking start/stopp Signal;"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbaren CI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDIConfigLevel(config)``"
    "Beschreibung", "Konfigurierbaren CI-Aktivzustand des Steuerkastens einstellen"
    "Erforderliche Parameter", "
    - ``config``: CI0-CI7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbaren CI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDIConfigLevel()``"
    "Beschreibung", "Konfigurierbaren CI-Aktivzustand des Steuerkastens abrufen"
    "Erforderliche Parameter", "
    - ``config``: CI0-CI7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbaren CO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDOConfigLevel(config)``"
    "Beschreibung", "Konfigurierbaren CO-Aktivzustand des Steuerkastens einstellen"
    "Erforderliche Parameter", "
    - ``config``: CO0-CO7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbaren CO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDOConfigLevel()``"
    "Beschreibung", "Konfigurierbaren CO-Aktivzustand des Steuerkastens abrufen"
    "Erforderliche Parameter", "
    - ``config``: CO0-CO7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbaren CI-Aktivzustand des Endeffektors einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolDIConfigLevel(config)``"
    "Beschreibung", "Konfigurierbaren CI-Aktivzustand des Endeffektors einstellen"
    "Erforderliche Parameter", "
    - ``config``: CI0-CI7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Konfigurierbaren CI-Aktivzustand des Endeffektors abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDIConfigLevel()``"
    "Beschreibung", "Konfigurierbaren CI-Aktivzustand des Endeffektors abrufen"
    "Erforderliche Parameter", "
    - ``config``: CI0-CI7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Standard-DI-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetStandardDILevel(config)``"
    "Beschreibung", "Standard-DI-Aktivzustand des Steuerkastens einstellen"
    "Erforderliche Parameter", "
    - ``config``: DI0-DI7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Standard-DI-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetStandardDILevel()``"
    "Beschreibung", "Standard-DI-Aktivzustand des Steuerkastens abrufen"
    "Erforderliche Parameter", "
    - ``config``: DI0-DI7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Standard-DO-Aktivzustand des Steuerkastens einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetStandardDOLevel(config)``"
    "Beschreibung", "Standard-DO-Aktivzustand des Steuerkastens einstellen"
    "Erforderliche Parameter", "
    - ``config``: DO0-DO7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
Standard-DO-Aktivzustand des Steuerkastens abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetStandardDOLevel()``"
    "Beschreibung", "Standard-DO-Aktivzustand des Steuerkastens abrufen"
    "Erforderliche Parameter", "
    - ``config``: DO0-DO7 Port-Aktivzustand-Array; 0-aktiv high; 1-aktiv low"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"
    
IO-Konfigurationsbezogenes SDK-Codebeispiel
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Verbindung mit der Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')


    def TestIOConfig(self):
        # DI-Konfiguration einstellen und abrufen
        setDIConfig = [1, 2, 3, 4, 5, 6, 7, 8]
        getDIConfig = [0] * 8
        rtn = robot.SetDIConfig(setDIConfig)
        print(f"SetDIConfig rtn is {rtn}")
        rtn, getDIConfig = robot.GetDIConfig()
        print(f"GetDIConfig rtn is {rtn}, value is {getDIConfig[0]} {getDIConfig[1]} {getDIConfig[2]} {getDIConfig[3]} {getDIConfig[4]} {getDIConfig[5]} {getDIConfig[6]} {getDIConfig[7]}")

        # DO-Konfiguration einstellen und abrufen
        setDOConfig = [9, 10, 11, 12, 13, 14, 15, 16]
        getDOConfig = [0] * 8
        rtn = robot.SetDOConfig(setDOConfig)
        print(f"SetDOConfig rtn is {rtn}")
        rtn, getDOConfig = robot.GetDOConfig()
        print(f"GetDOConfig rtn is {rtn}, value is {getDOConfig[0]} {getDOConfig[1]} {getDOConfig[2]} {getDOConfig[3]} {getDOConfig[4]} {getDOConfig[5]} {getDOConfig[6]} {getDOConfig[7]}")

        # Tool-DI-Konfiguration einstellen und abrufen
        setToolDIConfig = [17, 18]
        getToolDIConfig = [0] * 2
        rtn = robot.SetToolDIConfig(setToolDIConfig)
        print(f"SetToolDIConfig rtn is {rtn}")
        rtn, getToolDIConfig = robot.GetToolDIConfig()
        print(f"GetToolDIConfig rtn is {rtn}, value is {getToolDIConfig[0]} {getToolDIConfig[1]}")

        # DI-Pegelkonfiguration einstellen und abrufen (0: aktiv low, 1: aktiv high)
        setDIConfigLevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getDIConfigLevel = [0] * 8
        rtn = robot.SetDIConfigLevel(setDIConfigLevel)
        print(f"SetDIConfigLevel rtn is {rtn}")
        rtn, getDIConfigLevel = robot.GetDIConfigLevel()
        print(f"GetDIConfigLevel rtn is {rtn}, value is {getDIConfigLevel[0]} {getDIConfigLevel[1]} {getDIConfigLevel[2]} {getDIConfigLevel[3]} {getDIConfigLevel[4]} {getDIConfigLevel[5]} {getDIConfigLevel[6]} {getDIConfigLevel[7]}")

        # DO-Pegelkonfiguration einstellen und abrufen (0: aktiv low, 1: aktiv high)
        setDOConfigLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getDOConfigLevel = [0] * 8
        rtn = robot.SetDOConfigLevel(setDOConfigLevel)
        print(f"SetDOConfigLevel rtn is {rtn}")
        rtn, getDOConfigLevel = robot.GetDOConfigLevel()
        print(f"GetDOConfigLevel rtn is {rtn}, value is {getDOConfigLevel[0]} {getDOConfigLevel[1]} {getDOConfigLevel[2]} {getDOConfigLevel[3]} {getDOConfigLevel[4]} {getDOConfigLevel[5]} {getDOConfigLevel[6]} {getDOConfigLevel[7]}")

        # Tool-DI-Pegelkonfiguration einstellen und abrufen
        setToolDIConfigLevel = [1, 0]
        getToolDIConfigLevel = [0] * 2
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel)
        print(f"SetToolDIConfigLevel rtn is {rtn}")
        rtn, getToolDIConfigLevel = robot.GetToolDIConfigLevel()
        print(f"GetToolDIConfigLevel rtn is {rtn}, value is {getToolDIConfigLevel[0]} {getToolDIConfigLevel[1]}")

        # Standard-DI-Pegelkonfiguration einstellen und abrufen
        setStandardDILevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getStandardDILevel = [0] * 8
        rtn = robot.SetStandardDILevel(setStandardDILevel)
        print(f"SetStandardDILevel rtn is {rtn}")
        rtn, getStandardDILevel = robot.GetStandardDILevel()
        print(f"GetStandardDILevel rtn is {rtn}, value is {getStandardDILevel[0]} {getStandardDILevel[1]} {getStandardDILevel[2]} {getStandardDILevel[3]} {getStandardDILevel[4]} {getStandardDILevel[5]} {getStandardDILevel[6]} {getStandardDILevel[7]}")

        # Standard-DO-Pegelkonfiguration einstellen und abrufen
        setStandardDOLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getStandardDOLevel = [0] * 8
        rtn = robot.SetStandardDOLevel(setStandardDOLevel)
        print(f"SetStandardDOLevel rtn is {rtn}")
        rtn, getStandardDOLevel = robot.GetStandardDOLevel()
        print(f"GetStandsrdDOLevel rtn is {rtn}, value is {getStandardDOLevel[0]} {getStandardDOLevel[1]} {getStandardDOLevel[2]} {getStandardDOLevel[3]} {getStandardDOLevel[4]} {getStandardDOLevel[5]} {getStandardDOLevel[6]} {getStandardDOLevel[7]}")

        # 2 Sekunden warten
        time.sleep(2)

        # Verbindung schließen
        robot.CloseRPC()
        time.sleep(1)

    # Testfunktion aufrufen
    TestIOConfig(robot)