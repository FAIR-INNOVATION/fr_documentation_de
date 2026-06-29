Verwendung von Roboter-WebAPP-Programmen
==============================================

.. toctree:: 
    :maxdepth: 5

Automatisches Laden des Standard-Jobprogramms beim Start einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Legt fest, ob das Standard-Jobprogramm beim Start automatisch geladen wird.
    * @param  [in] flag  0-nicht automatisch laden, 1-automatisch laden.
    * @param  [in] program_name Name und Pfad des Jobprogramms, z.B. "movej.lua"
    * @return  Fehlercode.
    */
    errno_t LoadDefaultProgConfig(uint8_t flag, char program_name[64]);

Bestimmtes Jobprogramm laden
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Lädt ein bestimmtes Jobprogramm.
    * @param  [in] program_name Name und Pfad des Jobprogramms, z.B. "movej.lua". 
    * @return  Fehlercode.
    */
    errno_t ProgramLoad(char program_name[64]);

Name des geladenen Jobprogramms abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt den Namen des geladenen Jobprogramms zurück.
    * @param  [out] program_name Name und Pfad des Jobprogramms, z.B. "movej.lua". 
    * @return  Fehlercode.
    */
    errno_t GetLoadedProgram(char program_name[64]);

Aktuelle Zeilennummer des ausgeführten Roboter-Jobprogramms abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt die aktuelle Zeilennummer des ausgeführten Roboter-Jobprogramms zurück.
    * @param  [out] line  Zeilennummer.
    * @return  Fehlercode.
    */
    errno_t GetCurrentLine(int *line);

Aktuell geladenes Jobprogramm starten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Startet das aktuell geladene Jobprogramm.
    * @return  Fehlercode.
    */
    errno_t ProgramRun();

Laufendes Jobprogramm pausieren
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pausiert das aktuell laufende Jobprogramm.
    * @return  Fehlercode.
    */
    errno_t ProgramPause();

Pausiertes Jobprogramm fortsetzen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Setzt das aktuell pausierte Jobprogramm fort.
    * @return  Fehlercode.
    */
    errno_t ProgramResume();

Laufendes Jobprogramm beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Beendet das aktuell laufende Jobprogramm.
    * @return  Fehlercode.
    */
    errno_t ProgramStop();

Ausführungsstatus des Roboter-Jobprogramms abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Gibt den Ausführungsstatus des Roboter-Jobprogramms zurück.
    * @param  [out] state 1-Programm gestoppt oder kein Programm läuft, 2-Programm läuft, 3-Programm pausiert.
    * @return  Fehlercode.
    */
    errno_t GetProgramState(uint8_t *state);

Codebeispiel für Roboter-LUA-Programmoperationen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLuaOp(void)
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
      char program_name[64] = "test.lua";
      char loaded_name[64] = "";
      uint8_t state;
      int line;
      robot.Mode(0);
      robot.LoadDefaultProgConfig(0, program_name);
      robot.ProgramLoad(program_name);
      robot.ProgramRun();
      robot.Sleep(1000);
      robot.ProgramPause();
      robot.GetProgramState(&state);
      printf("program state:%u\n", state);
      robot.GetCurrentLine(&line);
      printf("current line:%d\n", line);
      robot.GetLoadedProgram(loaded_name);
      printf("program name:%s\n", loaded_name);
      robot.Sleep(1000);
      robot.ProgramResume();
      robot.Sleep(1000);
      robot.ProgramStop();
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }

Lua-Datei herunterladen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Lädt eine Lua-Datei herunter.
    * @param [in] fileName Name der herunterzuladenden Lua-Datei, z.B. "test.lua".
    * @param [in] savePath Lokaler Pfad zum Speichern der Datei, z.B. "D://Down/".
    * @return Fehlercode.
    */
    errno_t LuaDownLoad(std::string fileName, std::string savePath);

Lua-Datei löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Löscht eine Lua-Datei.
    * @param [in] fileName Name der zu löschenden Lua-Datei, z.B. "test.lua".
    * @return Fehlercode.
    */
    errno_t LuaDelete(std::string fileName);

Namen aller aktuellen Lua-Dateien abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Namen aller aktuellen Lua-Dateien zurück.
    * @param [out] luaNames Liste der Lua-Dateinamen.
    * @return Fehlercode.
    */
    errno_t GetLuaList(std::list<std::string>* luaNames);

Lua-Datei hochladen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Lädt eine Lua-Datei hoch.
    * @param [in] filePath Lokaler Pfad der Lua-Datei.
    * @return Fehlercode.
    */
    errno_t LuaUpload(std::string filePath);

Codebeispiel für Roboter-LUA-Datei-Upload/-Download
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLUAUpDownLoad(void)
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
      list<std::string> luaNames;
      rtn = robot.GetLuaList(&luaNames);
      std::cout << "res is: " << rtn << std::endl;
      std::cout << "size is: " << luaNames.size() << std::endl;
      for (auto it = luaNames.begin(); it != luaNames.end(); it++)
      {
        std::cout << it->c_str() << std::endl;
      }
      rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
      printf("LuaDownLoad rtn is %d\n", rtn);
      rtn = robot.LuaUpload("D://zUP/airlab.lua");
      printf("LuaUpload rtn is %d\n", rtn);
      rtn = robot.LuaDelete("test.lua");
      printf("LuaDelete rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }