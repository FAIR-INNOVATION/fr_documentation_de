Verwendung von Roboter-WebAPP-Programmen
========================================

.. toctree::
    :maxdepth: 5

Einstellen des standardmäßig beim Start automatisch zu ladenden Arbeitsprogramms
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Einstellen des standardmäßig beim Start automatisch zu ladenden Arbeitsprogramms
    * @param [in] flag 0 - Standardprogramm nicht automatisch beim Start laden, 1 - Standardprogramm automatisch beim Start laden
    * @param [in] program_name Name und Pfad des Arbeitsprogramms, z.B. "movej.lua"
    * @return Fehlercode
    */
    int LoadDefaultProgConfig(byte flag, string program_name);

Angegebenes Arbeitsprogramm laden
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Angegebenes Arbeitsprogramm laden
    * @param [in] program_name Name und Pfad des Arbeitsprogramms, z.B. "movej.lua"
    * @return Fehlercode
    */
    int ProgramLoad(string program_name);

Name des geladenen Arbeitsprogramms abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Name des geladenen Arbeitsprogramms abrufen
    * @param [out] program_name Name und Pfad des Arbeitsprogramms, z.B. "movej.lua"
    * @return Fehlercode
    */
    int GetLoadedProgram(ref string program_name);

Aktuelle Zeilennummer der Roboter-Arbeitsprogrammausführung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktuelle Zeilennummer der Roboter-Arbeitsprogrammausführung abrufen
    * @param [out] line Zeilennummer
    * @return Fehlercode
    */
    int GetCurrentLine(ref int line);

Aktuell geladenes Arbeitsprogramm ausführen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktuell geladenes Arbeitsprogramm ausführen
    * @return Fehlercode
    */
    int ProgramRun();

Aktuell laufendes Arbeitsprogramm pausieren
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktuell laufendes Arbeitsprogramm pausieren
    * @return Fehlercode
    */
    int ProgramPause();

Aktuell pausiertes Arbeitsprogramm fortsetzen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktuell pausiertes Arbeitsprogramm fortsetzen
    * @return Fehlercode
    */
    int ProgramResume();

Aktuell laufendes Arbeitsprogramm beenden
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktuell laufendes Arbeitsprogramm beenden
    * @return Fehlercode
    */
    int ProgramStop();

Ausführungsstatus des Roboter-Arbeitsprogramms abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ausführungsstatus des Roboter-Arbeitsprogramms abrufen
    * @param [out] state 1 - Programm gestoppt oder kein Programm läuft, 2 - Programm läuft, 3 - Programm pausiert
    * @return Fehlercode
    */
    int GetProgramState(ref byte state);

Codebeispiel für Roboter-LUA-Programmoperationen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnWebApp_Click(object sender, EventArgs e)
    {
        string program_name = "Text1.lua";
        string loaded_name = "";
        byte state=0;
        int line=0;

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        Thread.Sleep(1000);
        robot.ProgramPause();
        robot.GetProgramState(ref state);
        Console.WriteLine("program state:{0}\n", state);
        robot.GetCurrentLine(ref line);
        Console.WriteLine("current line:{0}\n", line);
        robot.GetLoadedProgram(ref loaded_name);
        Console.WriteLine("program name:{0}\n", loaded_name);
        Thread.Sleep(1000);
        robot.ProgramResume();
        Thread.Sleep(1000);
        robot.ProgramStop();
        Thread.Sleep(1000);
    }

Lua-Datei herunterladen
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Lua-Datei herunterladen
    * @param [in] fileName Name der herunterzuladenden Arbeitsprogrammdatei, z.B. "test.lua" oder "test.tar.gz"
    * @param [in] savePath Lokaler Pfad zum Speichern der Arbeitsprogrammdatei, z.B. "D://Down/"
    * @return Fehlercode
    */
    public int LuaDownLoad(string fileName, string savePath);

Lua-Datei hochladen
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Lua-Datei hochladen
    * @param [in] filePath Lokaler Pfad zur Arbeitsprogrammdatei, z.B. ".../test.lua" oder ".../test.tar.gz"
    * @param [out] errStr Fehlermeldung (falls vorhanden)
    * @return Fehlercode
    */
    public int LuaUpload(string filePath, ref string errStr);

Lua-Datei löschen
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Lua-Datei löschen
    * @param [in] fileName Name der zu löschenden Arbeitsprogrammdatei, z.B. "test.lua"
    * @return Fehlercode
    */
    public int LuaDelete(string fileName);

Namen aller aktuellen Lua-Dateien abrufen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Namen aller aktuellen Lua-Dateien abrufen
    * @param [out] luaNames Liste der Namen der Arbeitsprogrammdateien
    * @return Fehlercode
    */
    public int GetLuaList(ref List<string> luaNames);

Codebeispiel für Roboter-LUA-Datei-Upload/Download
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    private void btnUploadLua_Click(object sender, EventArgs e)
    {
        int rtn;
        List<string> luaNames = new List<string>();
        rtn = robot.GetLuaList(ref luaNames);
        Console.WriteLine("res is: {0}", rtn);
        Console.WriteLine("size is: {0}", luaNames.Count);
        foreach (var name in luaNames)
        {
        Console.WriteLine(name);
        }
        rtn = robot.LuaDownLoad("TT.lua", "D://zDOWN/");
        Console.WriteLine("LuaDownLoad rtn is {0}", rtn);
        string errStr = "";
        Thread.Sleep(2000);

        rtn = robot.LuaUpload("D://zUP/airlab.lua", ref errStr);
        Console.WriteLine("LuaUpload rtn is {0}", errStr);
        Thread.Sleep(2000);
        rtn = robot.LuaDelete("TT.lua");
        Console.WriteLine("LuaDelete rtn is {0}", rtn);
    }