API-Beschreibung
=========================

.. toctree::
   :maxdepth: 6

act Befehle
-------------

Alle folgenden act-Befehle verwenden POST mit der URL /action/act.

Teach-Punkt speichern
+++++++++++++++++++++

Befehlspanne: save_point.

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @param string name Name des aufgezeichneten Teach-Punkts
    * @param string speed Geschwindigkeit
    * @param string elbow_speed Ellenbogengeschwindigkeit
    * @param string acc Beschleunigung
    * @param string elbow_acc Ellenbogenbeschleunigung
    * @param string toolnum Werkzeugnummer
    * @param string workpiecenum Werkstücknummer
    */

Befehlsbeispiel:

.. code-block:: c
    :linenos:

    {
        cmd: "save_point",
        data:{
            name: "point1",
            speed: "100",
            elbow_speed: "100",
            acc: "100",
            elbow_acc: "100",
            toolnum: "1",
            workpiecenum: "1"
        }
    }

Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    /**
    * @return status:200 "success"
    * @return status:404 "fail"
    */

sta Befehle
-------------

Alle folgenden sta-Befehle verwenden POST mit der URL /action/sta.

Roboter-Statusdaten abrufen
++++++++++++++++++++++++++++

Befehlspanne: basic.

Befehlsparameter: Keine.

Befehlsbeispiel:

.. code-block:: c
    :linenos:

    {
        cmd: "basic",
    }

Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    /**
    * @return status:200
    * @param  object joints Gelenkpositionen
    * @param  object tcp Kartesische Pose
    * @param  array exAxisPos Positionen der externen Achsen
    * @return status:404 "fail"
    */
    {
        joints: {
            j1: "90",
            j2: "90",
            j3: "90",
            j4: "90",
            j5: "90",
            j6: "90",
        },
        tcp: {
            x: "100",
            y: "100",
            z: "100",
            rx: "90",
            ry: "90",
            rz: "90",
        },
        exAxisPos: [0,0,0,0]
    }

get Befehle
-------------

Alle folgenden get-Befehle verwenden POST mit der URL /action/get.

Teach-Punkte abrufen
+++++++++++++++++++++

Befehlspanne: get_points().

Befehlsparameter: Keine.

Befehlsbeispiel:

.. code-block:: c
    :linenos:

    {
        cmd: "get_points"
    }

Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    /**
    * @return status:200 "success"
    * @param  ${point_name}: object Informationen zum Teach-Punkt
    * @return status:404 "fail"
    */

Beispiel für Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    {
        "localpoint1": {
            "name":"localpoint1",
            "elbow_speed":"1",
            "elbow_acc":"1",
            "x": "1",
            "y": "1",
            "z": "1",
            "rx": "1",
            "ry": "1",
            "rz": "1",
            "j1": "1",
            "j2": "1",
            "j3": "1",
            "j4": "1",
            "j5": "1",
            "j6": "1",
            "toolnum": "1",
            "workpiecenum": "1",
            "speed": "1",
            "acc": "1",
            "E1": "1",
            "E2": "1",
            "E3": "1",
            "E4": "1"
        }
    }

Systemkonfiguration abrufen
+++++++++++++++++++++++++++++

Befehlspanne: get_syscfg().

Befehlsparameter: Keine.

Befehlsbeispiel:

.. code-block:: c
    :linenos:

    {
        cmd: "get_syscfg"
    }

Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    /**
    * @return status:200 "success"
    * @param  string log_count Maximale Anzahl der Protokolltage
    * @param  string language Aktuell verwendetes Sprachpaket
    * @param  string lifespan Timeout-Zeit
    * @return status:404 "fail"
    */

Beispiel für Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    {
        log_count:"10",
        language:"zh",
        lifespan:"1800"
    }

set Befehle
-------------

Alle folgenden set-Befehle verwenden POST mit der URL /action/set.

Systemvariablenbefehl senden
++++++++++++++++++++++++++++++++++++++

Befehlspanne: 511.

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @param int index Systemvariablenindex: 1-20
    * @param int value Systemvariablenwert
    */

Befehlsbeispiel:

.. code-block:: c
    :linenos:

    {
        cmd: 511,
        data:{
            content:"SetSysVarValue(2,1)"
        }
    }

Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    /**
    * @return status:200 1: Erfolg, 0: Fehler
    * @return status:404 "fail"
    */

Beispiel für Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    1

Systemvariablenwert abrufen
+++++++++++++++++++++++++++++++++++

Befehlspanne: 512.

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @param int index Systemvariablenindex: 1-20
    */

Befehlsbeispiel:

.. code-block:: c
    :linenos:

    {
        cmd: 512,
        data:{
            content:"GetSysVarValue(2)"
        }
    }

Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    /**
    * @return status:200
    * @param int value Systemvariablenwert
    * @return status:404 "fail"
    */

Beispiel für Befehlsrückmeldung:

.. code-block:: c
    :linenos:

    1

better-sqlite3 Befehle
-----------------------

Ersten Datensatz in der Datenbank abfragen
++++++++++++++++++++++++++++++++++++++++++++++++++++++

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @param string db_name Datenbankname (mit absolutem Pfad)
    * @param string sql SQL-Anweisung
    * @return string result Abgefragter erster Datensatz
    */

Befehlsinhalt:

.. code-block:: c
    :linenos:

    queryget(string db_name, string sql);

Alle Datensätze in der Datenbank abfragen
+++++++++++++++++++++++++++++++++++++++++++++++++++

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @param string db_name Datenbankname (mit absolutem Pfad)
    * @param string sql SQL-Anweisung
    * @return string result Abgefragte alle Datensätze
    */

Befehlsinhalt:

.. code-block:: c
    :linenos:

    queryall(string db_name, string sql);

Datenbankanweisung ausführen
+++++++++++++++++++++++++++++++++++++

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @param string db_name Datenbankname (mit absolutem Pfad)
    * @param string sql SQL-Anweisung
    * @param object obj Parameter, die für die Ausführung der SQL-Anweisung erforderlich sind
    * @return \
    */

Befehlsinhalt:

.. code-block:: c
    :linenos:

    exec(string db_name, string sql, object obj);

socket Befehle
-----------------------

socket senden
++++++++++++++++++++++++++++++

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @param string send_content Zu sendender Inhalt des Socket-Kommunikationsbefehls
    * @return \
    */

Befehlsinhalt:

.. code-block:: c
    :linenos:

    socket_cmd.send(string send_content); //8065
    socket_file.send(string send_content); //8067

socket empfangen
+++++++++++++++++++++++++++++

Befehlsparameter:

.. code-block:: c
    :linenos:

    /**
    * @return string recv_content Antwortinhalt des Socket-Kommunikationsbefehls
    */

Befehlsinhalt:

.. code-block:: c
    :linenos:

    socket_cmd.recv(); //8065
    socket_file.recv(); //8067

Dateioperationsbefehle
---------------------------

Dateiinhalt schreiben
++++++++++++++++++++++++++++++++

.. code-block:: c
    :linenos:

    /**
    * @param String filename Dateipfad
    * @param string content Zu schreibender Inhalt
    * @return true/false
    */

    write(filename, content);

Dateiinhalt lesen
++++++++++++++++++++++++++++++++

.. code-block:: c
    :linenos:

    /**
    * @param String filename Dateipfad
    * @return String Dateiinhalt
    */

    read(filename);

Dateiberechtigungen ändern
++++++++++++++++++++++++++++++++

.. code-block:: c
    :linenos:

    /**
    * @param String filename Dateipfad
    * @param Number mode Berechtigungsmodus (z.B. 0644)
    * @return true/false
    */

    chmod(filename, mode);

Verzeichnisinhalt lesen, einschließlich Unterverzeichnisse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c
    :linenos:

    /**
    * @param String path Verzeichnispfad
    * @return Array Array mit Dateinamen
    */

    readdir(path);

Komprimierungs- und Dekomprimierungsbefehle
---------------------------------------------------------------

.. note::
    Unterscheidung zwischen LA- und QX-Version:

    LA-Modulimport: `var execSync = require('child_process').execSync;`

    QX-Modulimport: `var tar_utils = require('/usr/local/etc/node/sys/tools/tar_utils');`

tar.gz-Archiv erstellen
+++++++++++++++++++++++++++++++++++++++++

Beispiel zum Erstellen eines tar.gz-Archivs (LA):

.. code-block:: javascript
    :linenos:

    var cmd = 'cd / && tar -zcvf ' + FILENAME + ' -C ' + DIR;
    execSync(cmd);

Befehlsbeschreibung zum Erstellen eines tar.gz-Archivs (QX):

.. code-block:: c
    :linenos:

    /**
    * @param {Array|String} sourcePaths Pfade der Quelldateien/-verzeichnisse (Array oder einzelner Pfad)
    * @param String targetFile Zielpfad der Archivdatei
    * @param Function callback Callback-Funktion, Parameter ist (error)
    * @param String basePath Basispfad, Standard ist '/'
    * @return \
    */

    createTarGz(sourcePaths, targetFile, callback, basePath);

tar.gz-Datei entpacken
+++++++++++++++++++++++++++++++++++++++++

Beispiel zum Entpacken einer tar.gz-Datei (LA):

.. code-block:: javascript
    :linenos:

    var cmd = 'cd / && tar -zxvf ' + FILENAME;
    execSync(cmd);

Befehlsbeschreibung zum Entpacken einer tar.gz-Datei (QX):

.. code-block:: c
    :linenos:

    /**
    * @param String sourceFile Pfad der Quellarchivdatei
    * @param String targetDir Zielverzeichnis zum Entpacken
    * @param Function callback Callback-Funktion, Parameter ist (error)
    * @return \
    */
    extractTarGz(sourceFile, targetDir, callback);