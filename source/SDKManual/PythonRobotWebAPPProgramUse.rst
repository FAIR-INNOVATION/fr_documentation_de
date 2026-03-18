Verwendung von Roboter-WebAPP-Programmen
========================================

.. toctree::
    :maxdepth: 5

Einstellen des standardmäßig beim Start automatisch zu ladenden Arbeitsprogramms
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadDefaultProgConfig(flag, program_name)``"
    "Beschreibung", "Einstellen des standardmäßig beim Start automatisch zu ladenden Arbeitsprogramms"
    "Erforderliche Parameter", "- ``flag``: 1 = Standardprogramm automatisch beim Start laden, 0 = nicht automatisch laden
    - ``program_name``: Name und Pfad des Arbeitsprogramms, z.B. /fruser/movej.lua, wobei /fruser/ der feste Pfad für QX und /usr/local/etc/controller/lua/ der feste Pfad für LA ist"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Angegebenes Arbeitsprogramm laden
++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramLoad(program_name)``"
    "Beschreibung", "Angegebenes Arbeitsprogramm laden"
    "Erforderliche Parameter", "- ``program_name``: Name und Pfad des Arbeitsprogramms, z.B. /fruser/movej.lua, wobei /fruser/ der feste Pfad für QX und /usr/local/etc/controller/lua/ der feste Pfad für LA ist"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Name des geladenen Arbeitsprogramms abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLoadedProgram()``"
    "Beschreibung", "Name des geladenen Arbeitsprogramms abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``program_name``: Name des geladenen Arbeitsprogramms"

Aktuelle Zeilennummer der Roboter-Arbeitsprogrammausführung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurrentLine()``"
    "Beschreibung", "Aktuelle Zeilennummer der Roboter-Arbeitsprogrammausführung abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``line_num``: Aktuelle Zeilennummer der Ausführung"

Aktuell geladenes Arbeitsprogramm ausführen
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramRun()``"
    "Beschreibung", "Aktuell geladenes Arbeitsprogramm ausführen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Aktuell laufendes Arbeitsprogramm pausieren
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramPause()``"
    "Beschreibung", "Aktuell laufendes Arbeitsprogramm pausieren"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Aktuell pausiertes Arbeitsprogramm fortsetzen
++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramResume()``"
    "Beschreibung", "Aktuell pausiertes Arbeitsprogramm fortsetzen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Aktuell laufendes Arbeitsprogramm beenden
++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramStop()``"
    "Beschreibung", "Aktuell laufendes Arbeitsprogramm beenden"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Ausführungsstatus des Roboter-Arbeitsprogramms abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetProgramState()``"
    "Beschreibung", "Ausführungsstatus des Roboter-Arbeitsprogramms abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``state``: Ausführungsstatus: 1 = Programm gestoppt oder kein Programm läuft, 2 = Programm läuft, 3 = Programm pausiert"

Codebeispiel für Roboter-LUA-Programmoperationen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    program_name = "/fruser/test0610.lua"
    loaded_name = ""
    state = 0
    line = 0
    robot.Mode(0)
    robot.LoadDefaultProgConfig(0, program_name)
    robot.ProgramLoad(program_name)
    robot.ProgramRun()
    time.sleep(1)
    robot.ProgramPause()
    error,state = robot.GetProgramState()
    print(f"program state:{state}")
    error,line = robot.GetCurrentLine()
    print(f"current line:{line}")
    error,loaded_name = robot.GetLoadedProgram()
    print(f"program name:{loaded_name}")
    time.sleep(1)
    robot.ProgramResume()
    time.sleep(1)
    robot.ProgramStop()
    time.sleep(1)
    robot.CloseRPC()

Lua-Datei herunterladen
++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LuaDownLoad(fileName, savePath)``"
    "Beschreibung", "Lua-Datei herunterladen"
    "Erforderliche Parameter", "- ``fileName``: Name der herunterzuladenden Lua-Datei, z.B. test.lua
    - ``savePath``: Lokaler Pfad zum Speichern der Datei, z.B. D://Down/"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Lua-Datei löschen
+++++++++++++++++
.. versionadded:: Python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LuaDelete(fileName)``"
    "Beschreibung", "Lua-Datei löschen"
    "Erforderliche Parameter", "- ``fileName``: Name der zu löschenden Lua-Datei, z.B. test.lua"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Namen aller aktuellen Lua-Dateien abrufen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLuaList()``"
    "Beschreibung", "Namen aller aktuellen Lua-Dateien abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``lua_num``: Anzahl der Lua-Dateien
    - ``luaNames``: Liste der Lua-Dateinamen"

Lua-Datei hochladen
+++++++++++++++++++
.. versionadded:: Python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LuaUpload(filePath)``"
    "Beschreibung", "Lua-Datei hochladen"
    "Erforderliche Parameter", "- ``filePath``: Vollständiger Pfad zur hochzuladenden Datei, z.B. D://test/test.lua"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - errorStr (Fehlermeldung, falls die Lua-Datei fehlerhaft ist)"

Codebeispiel für Roboter-LUA-Datei-Upload/Download
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn,lua_num,luaNames = robot.GetLuaList()
    print(f"res is:{rtn}")
    print(f"size is:{lua_num}")
    for name in luaNames:
        print(name)
    rtn = robot.LuaDownLoad("test0610.lua", "D://zDOWN/")
    print(f"LuaDownLoad rtn is:{rtn}")
    rtn = robot.LuaUpload("D://zDOWN/test0610.lua")
    print(f"LuaUpload rtn is:{rtn}")
    rtn = robot.LuaDelete("test0610.lua")
    print(f"LuaDelete rtn is:{rtn}")
    robot.CloseRPC()
    