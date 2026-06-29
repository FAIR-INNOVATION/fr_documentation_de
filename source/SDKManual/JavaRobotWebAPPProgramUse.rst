Verwendung von Roboter-WebAPP-Programmen
========================================

.. toctree::
    :maxdepth: 5

Einstellen des standardmäßig beim Start automatisch zu ladenden Arbeitsprogramms
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellen des standardmäßig beim Start automatisch zu ladenden Arbeitsprogramms
    * @param [in] flag 0 - Standardprogramm nicht automatisch beim Start laden, 1 - Standardprogramm automatisch beim Start laden
    * @param [in] program_name Name und Pfad des Arbeitsprogramms, z.B. "movej.lua"
    * @return Fehlercode
    */
    int LoadDefaultProgConfig(int flag, String program_name);

Angegebenes Arbeitsprogramm laden
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Angegebenes Arbeitsprogramm laden
    * @param [in] program_name Name und Pfad des Arbeitsprogramms, z.B. "movej.lua"
    * @return Fehlercode
    */
    int ProgramLoad(String program_name);

Name des geladenen Arbeitsprogramms abrufen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Name des geladenen Arbeitsprogramms abrufen
    * @param [out] program_name Array (Länge 1) zum Befüllen mit dem Namen und Pfad des Arbeitsprogramms, z.B. "movej.lua"
    * @return Fehlercode
    */
    int GetLoadedProgram(String[] program_name);

Aktuelle Zeilennummer der Roboter-Arbeitsprogrammausführung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuelle Zeilennummer der Roboter-Arbeitsprogrammausführung abrufen
    * @return List<Integer> List[0]: Fehlercode; List[1]: int line Zeilennummer
    */
    List<Integer> GetCurrentLine();

Aktuell geladenes Arbeitsprogramm ausführen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuell geladenes Arbeitsprogramm ausführen
    * @return Fehlercode
    */
    int ProgramRun();

Aktuell laufendes Arbeitsprogramm pausieren
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuell laufendes Arbeitsprogramm pausieren
    * @return Fehlercode
    */
    int PauseMotion();

Aktuell pausiertes Arbeitsprogramm fortsetzen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuell pausiertes Arbeitsprogramm fortsetzen
    * @return Fehlercode
    */
    int ResumeMotion();

Aktuell laufendes Arbeitsprogramm beenden
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktuell laufendes Arbeitsprogramm beenden
    * @return Fehlercode
    */
    int StopMotion();

Ausführungsstatus des Roboter-Arbeitsprogramms abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ausführungsstatus des Roboter-Arbeitsprogramms abrufen
    * @param [out] state Array (Länge 1) für den Status: 1 - Programm gestoppt oder kein Programm läuft, 2 - Programm läuft, 3 - Programm pausiert
    * @return Fehlercode
    */
    public int GetProgramState(int[] state)

Codebeispiel für Roboter-LUA-Programmoperationen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLuaOp(Robot robot)
    {
        String program_name = "Text1.lua";
        String[] loaded_name = new String[]{""};
        int[] state = new int[]{0};
        List<Integer> line = new ArrayList<>();

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        robot.Sleep(1000);
        robot.PauseMotion(); // Hinweis: Im Original wurde ProgramPause() verwendet, aber Methode heißt PauseMotion()
        robot.GetProgramState(state);
        System.out.println("program state: " + state[0]);
        line = robot.GetCurrentLine();
        System.out.println("current line: " + line.get(1));
        robot.GetLoadedProgram(loaded_name);
        System.out.println("program name: " + loaded_name[0]);
        robot.Sleep(1000);
        robot.ResumeMotion();
        robot.Sleep(1000);
        robot.StopMotion();
        robot.Sleep(1000);

        robot.CloseRPC();
        return 0;
    }

Lua-Programm herunterladen
+++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Arbeitsprogramm (Lua) herunterladen
    * @param [in] fileName Name der herunterzuladenden Lua-Datei, z.B. "test.lua" oder "test.tar.gz"
    * @param [in] savePath Lokaler Pfad zum Speichern der Datei, z.B. "D://Down/"
    * @return Fehlercode
    */
    int LuaDownLoad(String fileName, String savePath);

Lua-Programm löschen
++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Arbeitsprogramm (Lua) löschen
    * @param [in] fileName Name der zu löschenden Lua-Datei, z.B. "test.lua"
    * @return Fehlercode
    */
    int LuaDelete(String fileName);

Namen aller aktuellen Lua-Dateien abrufen
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Namen aller aktuellen Lua-Dateien abrufen
    * @param [out] luaNames Liste (List<String>) zum Befüllen mit den Namen der Arbeitsprogrammdateien
    * @return Fehlercode
    */
    int GetLuaList(List<String> luaNames);

Lua-Programm hochladen
++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Arbeitsprogramm (Lua) hochladen
    * @param [in] filePath Lokaler Pfad zur Lua-Datei, z.B. ".../test.lua" oder ".../test.tar.gz"
    * @param [out] errStr Fehlermeldung (als String, wird bei Fehler befüllt)
    * @return Fehlercode
    */
    int LuaUpload(String filePath, String[] errStr); // Hinweis: errStr sollte als String[] übergeben werden, um Wert zurückzugeben.

Codebeispiel für Roboter-LUA-Datei-Upload/Download
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLUAUpDownLoad(Robot robot)
    {
        List<String> luaNames=new ArrayList<>();
        int rtn = robot.GetLuaList(luaNames);
        System.out.println("res is: "+rtn);
        System.out.println("size is: "+luaNames.size());
        for (int it =1; it < luaNames.size(); it++)
        {
            System.out.println(luaNames.get(it));
        }

        rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
        System.out.println("LuaDownLoad rtn is:"+rtn);

        rtn = robot.LuaUpload("D://zUP/XG.lua","");
        System.out.println("LuaUpload rtn is:"+ rtn);

        rtn = robot.LuaDelete("XG.lua");
        System.out.println("LuaDelete rtn is:"+ rtn);

        return 0;
    }
