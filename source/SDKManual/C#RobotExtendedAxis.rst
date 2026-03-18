Externe Achsen
==============

.. toctree::
    :maxdepth: 5

Parameter für 485-Erweiterungsachsen einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Parameter für 485-Erweiterungsachsen einstellen
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] servoCompany Hersteller des Servoantriebs, 1-Dynatec
    * @param [in] servoModel Modell des Servoantriebs, 1-FD100-750C
    * @param [in] servoSoftVersion Softwareversion des Servoantriebs, 1-V1.0
    * @param [in] servoResolution Auflösung des Encoders
    * @param [in] axisMechTransRatio Mechanisches Übersetzungsverhältnis
    * @return Fehlercode
    */
    int AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);

Konfigurationsparameter für 485-Erweiterungsachsen abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Konfigurationsparameter für 485-Erweiterungsachsen abrufen
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [out] servoCompany Hersteller des Servoantriebs, 1-Dynatec
    * @param [out] servoModel Modell des Servoantriebs, 1-FD100-750C
    * @param [out] servoSoftVersion Softwareversion des Servoantriebs, 1-V1.0
    * @param [out] servoResolution Auflösung des Encoders
    * @param [out] axisMechTransRatio Mechanisches Übersetzungsverhältnis
    * @return Fehlercode
    */
    int AuxServoGetParam(int servoId, ref int servoCompany, ref int servoModel, ref int servoSoftVersion, ref int servoResolution, ref double axisMechTransRatio);

485-Erweiterungsachse aktivieren/deaktivieren
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief 485-Erweiterungsachse aktivieren/deaktivieren
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] status Aktivierungsstatus, 0-deaktivieren, 1-aktivieren
    * @return Fehlercode
    */
    int AuxServoEnable(int servoId, int status);

Steuerungsmodus für 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Steuerungsmodus für 485-Erweiterungsachse einstellen
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] mode Steuerungsmodus, 0-Positionsmodus, 1-Geschwindigkeitsmodus
    * @return Fehlercode
    */
    int AuxServoSetControlMode(int servoId, int mode);

Zielposition für 485-Erweiterungsachse einstellen (Positionsmodus)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Zielposition für 485-Erweiterungsachse einstellen (Positionsmodus)
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] pos Zielposition, mm oder °
    * @param [in] speed Zielgeschwindigkeit, mm/s oder °/s
    * @return Fehlercode
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed);

Zielgeschwindigkeit für 485-Erweiterungsachse einstellen (Geschwindigkeitsmodus)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Zielgeschwindigkeit für 485-Erweiterungsachse einstellen (Geschwindigkeitsmodus)
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] speed Zielgeschwindigkeit, mm/s oder °/s
    * @return Fehlercode
    */
    int AuxServoSetTargetSpeed(int servoId, double speed);

Zieldrehmoment für 485-Erweiterungsachse einstellen (Drehmomentmodus) -- vorübergehend nicht freigegeben
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Zieldrehmoment für 485-Erweiterungsachse einstellen (Drehmomentmodus) -- vorübergehend nicht freigegeben
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] torque Zieldrehmoment, Nm
    * @return Fehlercode
    */
    int AuxServoSetTargetTorque(int servoId, double torque);

485-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief 485-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] mode Referenzfahrmodus, 1- Aktuelle Position als Nullpunkt; 2- Referenzfahrt zum negativen Endschalter; 3- Referenzfahrt zum positiven Endschalter
    * @param [in] searchVel Suchgeschwindigkeit, mm/s oder °/s
    * @param [in] latchVel Einrastgeschwindigkeit, mm/s oder °/s
    * @return Fehlercode
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);

Fehlerinformationen der 485-Erweiterungsachse löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Fehlerinformationen der 485-Erweiterungsachse löschen
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @return Fehlercode
    */
    int AuxServoClearError(int servoId);

Servostatus der 485-Erweiterungsachse abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Servostatus der 485-Erweiterungsachse abrufen
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [out] servoErrCode Fehlercode des Servoantriebs
    * @param [out] servoState Status des Servoantriebs. Bit0: 0-nicht aktiviert; 1-aktiviert; Bit1: 0-nicht in Bewegung; 1-in Bewegung; Bit2: 0-positiver Endschalter nicht ausgelöst; 1-positiver Endschalter ausgelöst; Bit3: 0-negativer Endschalter nicht ausgelöst; 1-negativer Endschalter ausgelöst; Bit4: 0-Positionierung nicht abgeschlossen; 1-Positionierung abgeschlossen; Bit5: 0-Referenzfahrt nicht durchgeführt; 1-Referenzfahrt abgeschlossen
    * @param [out] servoPos Aktuelle Servoposition, mm oder °
    * @param [out] servoSpeed Aktuelle Servogeschwindigkeit, mm/s oder °/s
    * @param [out] servoTorque Aktuelles Servodrehmoment, Nm
    * @return Fehlercode
    */
    int AuxServoGetStatus(int servoId, ref int servoErrCode, ref int servoState, ref double servoPos, ref double servoSpeed, ref double servoTorque);

Datenachsnummer für 485-Erweiterungsachse in Statusrückmeldung einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Datenachsnummer für 485-Erweiterungsachse in Statusrückmeldung einstellen
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @return Fehlercode
    */
    int AuxServosetStatusID(int servoId);

Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse einstellen
    * @param [in] acc Bewegungsbeschleunigung der 485-Erweiterungsachse
    * @param [in] dec Bewegungsverzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    int AuxServoSetAcc(double acc, double dec);

Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse einstellen
    * @param [in] acc Not-Halt-Beschleunigung der 485-Erweiterungsachse
    * @param [in] dec Not-Halt-Verzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec);

Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse abrufen
    * @param [out] acc Bewegungsbeschleunigung der 485-Erweiterungsachse
    * @param [out] dec Bewegungsverzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    int AuxServoGetAcc(ref double acc, ref double dec);

Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse abrufen
    * @param [out] acc Not-Halt-Beschleunigung der 485-Erweiterungsachse
    * @param [out] dec Not-Halt-Verzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    int AuxServoGetEmergencyStopAcc(ref double acc, ref double dec);

Codebeispiel für die Steuerung von Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button64_Click(object sender, EventArgs e)
    {
        int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        int servoCompany = 0;
        int servoModel = 0;
        int servoSoftVersion = 0;
        int servoResolution = 0;
        double axisMechTransRatio = 0;
        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
        Console.WriteLine($"AuxServoSetParam is: {retval}");
        Thread.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        Thread.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;
        robot.AuxServoGetEmergencyStopAcc(ref emagacc, ref emagdec);
        Console.WriteLine($"emergency acc is {emagacc}  dec is {emagdec}");
        robot.AuxServoGetAcc(ref acc, ref dec);
        Console.WriteLine($"acc is {acc}  dec is {dec}");

        robot.AuxServoSetControlMode(1, 0);
        Thread.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        Console.WriteLine($"AuxServoEnable disenable {retval}");
        Thread.Sleep(1000);
        int servoerrcode = 0;
        int servoErrCode = 0;
        int servoState = 0;
        double servoPos = 0;
        double servoSpeed = 0;
        double servoTorque = 0;
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoEnable(1, 1);
        Console.WriteLine($"AuxServoEnable enable {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1);
        Console.WriteLine($"AuxServoHoming {retval}");
        Thread.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30);
        Console.WriteLine($"AuxServoSetTargetPos {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoSpeed {servoSpeed}");
        Thread.Sleep(8000);

        robot.AuxServoSetControlMode(1, 1);
        Thread.Sleep(2000);

        robot.AuxServoEnable(1, 0);
        Thread.Sleep(1000);
        robot.AuxServoEnable(1, 1);
        Thread.Sleep(1000);
        robot.AuxServoSetTargetSpeed(1, 100, 80);

        Thread.Sleep(5000);
        robot.AuxServoSetTargetSpeed(1, 0, 80);
    }

Konfiguration der UDP-Kommunikationsparameter für Erweiterungsachsen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Konfiguration der UDP-Kommunikationsparameter für Erweiterungsachsen
    * @param [in] ip IP-Adresse der SPS
    * @param [in] port Portnummer
    * @param [in] period Kommunikationszyklus (ms, Standard ist 2, diesen Parameter nicht ändern)
    * @param [in] lossPkgTime Paketverlust-Erkennungszeit (ms)
    * @param [in] lossPkgNum Anzahl der Paketverluste
    * @param [in] disconnectTime Zeitdauer zur Bestätigung einer Kommunikationsunterbrechung
    * @param [in] reconnectEnable Automatische Wiederverbindung bei Kommunikationsunterbrechung aktivieren (0-deaktivieren, 1-aktivieren)
    * @param [in] reconnectPeriod Intervall für Wiederverbindungsversuche (ms)
    * @param [in] reconnectNum Anzahl der Wiederverbindungsversuche
    * @param [in] selfConnect Automatische Verbindungsherstellung nach Stromausfall/Neustart (0-keine Verbindung herstellen, 1-Verbindung herstellen)
    * @return Fehlercode
    */
    int ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect);

Konfiguration der UDP-Kommunikationsparameter für Erweiterungsachsen abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Konfiguration der UDP-Kommunikationsparameter für Erweiterungsachsen abrufen
    * @param [out] ip IP-Adresse der SPS
    * @param [out] port Portnummer
    * @param [out] period Kommunikationszyklus (ms, Standard ist 2, diesen Parameter nicht ändern)
    * @param [out] lossPkgTime Paketverlust-Erkennungszeit (ms)
    * @param [out] lossPkgNum Anzahl der Paketverluste
    * @param [out] disconnectTime Zeitdauer zur Bestätigung einer Kommunikationsunterbrechung
    * @param [out] reconnectEnable Automatische Wiederverbindung bei Kommunikationsunterbrechung aktivieren (0-deaktivieren, 1-aktivieren)
    * @param [out] reconnectPeriod Intervall für Wiederverbindungsversuche (ms)
    * @param [out] reconnectNum Anzahl der Wiederverbindungsversuche
    * @return Fehlercode
    */
    int ExtDevGetUDPComParam(std::string& ip, int& port, int& period, int& lossPkgTime, int& lossPkgNum, int& disconnectTime, int& reconnectEnable, int& reconnectPeriod, int& reconnectNum);

UDP-Kommunikation laden
+++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief UDP-Kommunikation laden
    * @return Fehlercode
    */
    int ExtDevLoadUDPDriver();

UDP-Kommunikation entladen
+++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief UDP-Kommunikation entladen
    * @return Fehlercode
    */
    int ExtDevUnloadUDPDriver();

Verbindung nach UDP-Kommunikationsabbruch für Erweiterungsachsen wiederherstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Verbindung nach UDP-Kommunikationsabbruch für Erweiterungsachsen wiederherstellen
    * @return Fehlercode
    */
    int ExtDevUDPClientComReset();

Kommunikation nach UDP-Kommunikationsabbruch für Erweiterungsachsen schließen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Kommunikation nach UDP-Kommunikationsabbruch für Erweiterungsachsen schließen
    * @return Fehlercode
    */
    int ExtDevUDPClientComClose();

Parameterkonfiguration für UDP-Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Parameterkonfiguration für UDP-Erweiterungsachsen
    * @param [in] axisID Achsnummer
    * @param [in] axisType Erweiterungsachstyp 0-Translatorisch; 1-Rotatorisch
    * @param [in] axisDirection Richtung der Erweiterungsachse 0-positive Richtung; 1-negative Richtung
    * @param [in] axisMax Maximale Position der Achse (mm)
    * @param [in] axisMin Minimale Position der Achse (mm)
    * @param [in] axisVel Geschwindigkeit (mm/s)
    * @param [in] axisAcc Beschleunigung (mm/s²)
    * @param [in] axisLead Spindelsteigung (mm)
    * @param [in] encResolution Encoderauflösung
    * @param [in] axisOffect Versatz der Erweiterungsachse am Schweißstartpunkt
    * @param [in] axisCompany Hersteller des Antriebs 1-Hechuan; 2-Huichuan; 3-Panasonic
    * @param [in] axisModel Modell des Antriebs 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Huichuan-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Encodertyp 0-inkrementell; 1-absolut
    * @return Fehlercode
    */
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Einbauposition der Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Einbauposition der Erweiterungsachse einstellen
    * @param [in] installType 0-Roboter ist auf der externen Achse montiert, 1-Roboter ist außerhalb der externen Achse montiert
    * @return Fehlercode
    */
    int SetRobotPosToAxis(int installType);

DH-Parameterkonfiguration für Erweiterungsachssystem einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief DH-Parameterkonfiguration für Erweiterungsachssystem einstellen
    * @param [in] axisConfig Konfiguration der externen Achse, 0-Ein-Freiheitsgrad-Linearschiene, 1-Zwei-Freiheitsgrad-L-Positionierer, 2-Drei-Freiheitsgrade, 3-Vier-Freiheitsgrade, 4-Ein-Freiheitsgrad-Positionierer
    * @param [in] axisDHd1 DH-Parameter d1 (mm)
    * @param [in] axisDHd2 DH-Parameter d2 (mm)
    * @param [in] axisDHd3 DH-Parameter d3 (mm)
    * @param [in] axisDHd4 DH-Parameter d4 (mm)
    * @param [in] axisDHa1 DH-Parameter a1 (mm)
    * @param [in] axisDHa2 DH-Parameter a2 (mm)
    * @param [in] axisDHa3 DH-Parameter a3 (mm)
    * @param [in] axisDHa4 DH-Parameter a4 (mm)
    * @return Fehlercode
    */
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

UDP-Erweiterungsachse aktivieren
++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief UDP-Erweiterungsachse aktivieren
    * @param [in] axisID Achsnummer [1-4]
    * @param [in] status 0-deaktivieren; 1-aktivieren
    * @return Fehlercode
    */
    int ExtAxisServoOn(int axisID, int status);

UDP-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief UDP-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)
    * @param [in] axisID Achsnummer [1-4]
    * @param [in] mode Referenzfahrmodus 0-aktuelle Position als Nullpunkt, 1-Referenzfahrt zum negativen Endschalter, 2-Referenzfahrt zum positiven Endschalter
    * @param [in] searchVel Suchgeschwindigkeit (mm/s)
    * @param [in] latchVel Einrastgeschwindigkeit (mm/s)
    * @return Fehlercode
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

UDP-Erweiterungsachse Tippbetrieb starten
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief UDP-Erweiterungsachse Tippbetrieb starten
    * @param [in] axisID Achsnummer [1-4]
    * @param [in] direction Drehrichtung 0-negativ; 1-positiv
    * @param [in] vel Geschwindigkeit (mm/s)
    * @param [in] acc Beschleunigung (mm/s²)
    * @param [in] maxDistance Maximale Tippdistanz
    * @return Fehlercode
    */
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);

UDP-Erweiterungsachse Tippbetrieb stoppen
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief UDP-Erweiterungsachse Tippbetrieb stoppen
    * @param [in] axisID Achsnummer [1-4]
    * @return Fehlercode
    */
    int ExtAxisStopJog(int axisID);

Codebeispiel für Konfiguration und Tippbetrieb von UDP-Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnJog_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5,1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        rtn = robot.ExtAxisSetHoming(1, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 1 rtnn is  " + rtn);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 2 rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 2 rtn is " + rtn);

        Thread.Sleep(3000);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(1);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(1, 0);

        Thread.Sleep(3000);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(2);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(2, 0);
        Thread.Sleep(3000);
        robot.ExtDevUnloadUDPDriver();
    }

Referenzpunkt für Koordinatensystem der Erweiterungsachse einstellen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Referenzpunkt für Koordinatensystem der Erweiterungsachse einstellen - Vier-Punkt-Methode
    * @param [in] pointNum Punktnummer [1-4]
    * @return Fehlercode
    */
    int ExtAxisSetRefPoint(int pointNum);

Koordinatensystem der Erweiterungsachse berechnen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Koordinatensystem der Erweiterungsachse berechnen - Vier-Punkt-Methode
    * @param [out] coord Koordinatenwerte des Systems
    * @return Fehlercode
    */
    int ExtAxisComputeECoordSys(DescPose& coord);

Koordinatensystem der Erweiterungsachse anwenden
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Koordinatensystem der Erweiterungsachse anwenden
    * @param [in] applyAxisId Erweiterungsachsennummer Bit0-Bit3 entsprechen den Achsnummern 1-4, z.B. für Achse 1 und 3: 0b00000101 = 5
    * @param [in] axisCoordNum Nummer des Erweiterungsachsen-Koordinatensystems
    * @param [in] coord Koordinatenwerte des Systems
    * @param [in] calibFlag Kalibrierungsflag 0-nein, 1-ja
    * @return Fehlercode
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Pose des Kalibrierungsreferenzpunkts im Endeffektor-Koordinatensystem des Positionierers einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Pose des Kalibrierungsreferenzpunkts im Endeffektor-Koordinatensystem des Positionierers einstellen
    * @param [in] pos Posenwerte
    * @return Fehlercode
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Referenzpunkt für Positionierer-Koordinatensystem einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Referenzpunkt für Positionierer-Koordinatensystem einstellen
    * @param [in] pointNum Punktnummer [1-4]
    * @return Fehlercode
    */
    int PositionorSetRefPoint(int pointNum);

Koordinatensystem des Positionierers berechnen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Koordinatensystem des Positionierers berechnen - Vier-Punkt-Methode
    * @param [out] coord Koordinatenwerte des Systems
    * @return Fehlercode
    */
    int PositionorComputeECoordSys(DescPose& coord);

Koordinatensystem der Erweiterungsachse abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Koordinatensystem der Erweiterungsachse abrufen
    * @param [out] coord Koordinatensystem der Erweiterungsachse
    * @return Fehlercode
    */
    int ExtAxisGetCoord(ref DescPose coord);

Codebeispiel für die Kalibrierung des Erweiterungsachsen-Koordinatensystems
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5,1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(1, 128.5f, 206.4f, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);

        DescPose toolCoord = new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe = new JointPos(115.193f, -96.149f, 92.489f, -87.068f, -89.15f, -83.488f);
        JointPos j1 = new JointPos(117.559f, -92.624f, 100.329f, -96.909f, -94.057f, -83.488f);
        JointPos j2 = new JointPos(112.239f, -90.096f, 99.282f, -95.909f, -89.824f, -83.488f);
        JointPos j3 = new JointPos(110.839f, -83.473f, 93.166f, -89.22f, -90.499f, -83.487f);
        JointPos j4 = new JointPos(107.935f, -83.572f, 95.424f, -92.873f, -87.933f, -83.488f);

        DescPose descSafe = new DescPose();
        DescPose desc1 = new DescPose();
        DescPose desc2 = new DescPose();
        DescPose desc3 = new DescPose();
        DescPose desc4 = new DescPose();
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin( jSafe,  ref descSafe);
        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        robot.GetForwardKin( j1, ref desc1);
        robot.MoveJ( j1,  desc1, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        DescPose actualTCPPos = new DescPose();
        robot.GetActualTCPPose(0, ref actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        Console.WriteLine("PositionorSetRefPoint 1 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j2, ref desc2);
        rtn = robot.MoveJ( j2,  desc2, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(2);
        Console.WriteLine("PositionorSetRefPoint 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j3, ref desc3);
        robot.MoveJ( j3,  desc3, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(3);
        Console.WriteLine("PositionorSetRefPoint 3 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin(j4, ref desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        Console.WriteLine("PositionorSetRefPoint 4 rtn is " + rtn);
        Thread.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(ref axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        Console.WriteLine("PositionorComputeECoordSys rtn is {0} {1} {2} {3} {4} {5}", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
        Console.WriteLine("ExtAxisActiveECoordSys rtn is " + rtn);
    }

UDP-Erweiterungsachse bewegen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: C#
    :linenos:

    /**
    * @brief UDP-Erweiterungsachse bewegen
    * @param [in] pos Zielposition
    * @param [in] ovl Geschwindigkeitsprozentsatz
    * @param [in] blend Glättungsparameter (mm oder ms)
    * @return Fehlercode
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend=-1);

Codebeispiel für die Bewegung von UDP-Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        ExaxisPos axisPos;
        axisPos.ePos[0] = 20;
        axisPos.ePos[1] = 0;
        axisPos.ePos[2] = 0;
        axisPos.ePos[3] = 0;
        robot.ExtAxisMove(axisPos, 50);
    }

Synchronbewegung von UDP-Erweiterungsachse und Roboter-Gelenkbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Synchronbewegung von UDP-Erweiterungsachse und Roboter-Gelenkbewegung
    * @param [in] joint_pos Ziel-Gelenkposition (Grad)
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] epos Position der Erweiterungsachse (mm)
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend) (ms)
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Codebeispiel
++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveJ_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

        //1. Kalibrieren und Anwenden des Roboter-Werkzeugkoordinatensystems. Sie können die Vier-Punkt- oder Sechs-Punkt-Methode verwenden. Die relevanten Schnittstellen sind:
        //    int SetToolPoint(int point_num);  // Werkzeugreferenzpunkt einstellen - Sechs-Punkt-Methode
        //    int ComputeTool(ref DescPose tcp_pose);  // Werkzeugkoordinatensystem berechnen
        //    int SetTcp4RefPoint(int point_num);    // Werkzeugreferenzpunkt einstellen - Vier-Punkt-Methode
        //    int ComputeTcp4(ref DescPose tcp_pose);   // Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  // Werkzeugkoordinatensystem einstellen und anwenden
        //    int SetToolList(int id, DescPose coord, int type, int install);   // Werkzeugkoordinatensystem in Liste einstellen und anwenden

        //2. UDP-Kommunikationsparameter einstellen und UDP-Kommunikation laden
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Parameter für Erweiterungsachsen einstellen, einschließlich Typ, Antriebsparameter, DH-Parameter
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Einachs-Positionierer und DH-Parameter
        robot.SetRobotPosToAxis(1);  // Einbauposition der Erweiterungsachse
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Servoantriebsparameter, hier für Einachs-Positionierer. Bei mehreren Achsen müssen für jede Achse Parameter gesetzt werden.

        //4. Ausgewählte Achse aktivieren und Referenzfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibrierung und Anwendung des Erweiterungsachsen-Koordinatensystems (Hinweis: Positionierer und Linearschiene haben unterschiedliche Schnittstellen. Hier folgen die des Positionierers)
        DescPose pos = new DescPose(/* Geben Sie hier Ihre Kalibrierungspunktkoordinaten ein */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sie müssen diese Schnittstelle 4 Mal mit verschiedenen Punkten aufrufen, um die Achse zu kalibrieren */
        DescPose coord = new DescPose( );
        robot.PositionorComputeECoordSys(ref coord); // Kalibrierungsergebnis berechnen
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  // Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden

        //6. Werkstückkoordinatensystem auf der Erweiterungsachse kalibrieren. Sie benötigen folgende Schnittstellen:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Startpunkt der synchronen Gelenkbewegung erfassen
        DescPose startdescPose = new DescPose(/* Geben Sie hier Ihre Koordinaten ein */);
        JointPos startjointPos = new JointPos(/* Geben Sie hier Ihre Koordinaten ein */);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Geben Sie hier Ihre Startkoordinaten für die Erweiterungsachse ein */);

        //8. Endpunkt der synchronen Gelenkbewegung erfassen
        DescPose enddescPose = new DescPose(/* Geben Sie hier Ihre Koordinaten ein */);
        JointPos endjointPos = new JointPos(/* Geben Sie hier Ihre Koordinaten ein */);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Geben Sie hier Ihre Endkoordinaten für die Erweiterungsachse ein */);

        //9. Synchronbewegungsprogramm erstellen
        // Zum Startpunkt bewegen, angenommen Werkzeug- und Werkstückkoordinatensystem sind beide 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        // Synchronbewegung starten
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
    }

Synchronbewegung von UDP-Erweiterungsachse und Roboter-Linearbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Synchronbewegung von UDP-Erweiterungsachse und Roboter-Linearbewegung
    * @param [in] joint_pos Ziel-Gelenkposition (Grad)
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) (mm)
    * @param [in] epos Position der Erweiterungsachse (mm)
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Codebeispiel
++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveL_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1. Kalibrieren und Anwenden des Roboter-Werkzeugkoordinatensystems. Sie können die Vier-Punkt- oder Sechs-Punkt-Methode verwenden. Die relevanten Schnittstellen sind:
        //    int SetToolPoint(int point_num);  // Werkzeugreferenzpunkt einstellen - Sechs-Punkt-Methode
        //    int ComputeTool(ref DescPose tcp_pose);  // Werkzeugkoordinatensystem berechnen
        //    int SetTcp4RefPoint(int point_num);    // Werkzeugreferenzpunkt einstellen - Vier-Punkt-Methode
        //    int ComputeTcp4(ref DescPose tcp_pose);   // Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  // Werkzeugkoordinatensystem einstellen und anwenden
        //    int SetToolList(int id, DescPose coord, int type, int install);   // Werkzeugkoordinatensystem in Liste einstellen und anwenden

        //2. UDP-Kommunikationsparameter einstellen und UDP-Kommunikation laden
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Parameter für Erweiterungsachsen einstellen, einschließlich Typ, Antriebsparameter, DH-Parameter
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Einachs-Positionierer und DH-Parameter
        robot.SetRobotPosToAxis(1);  // Einbauposition der Erweiterungsachse
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Servoantriebsparameter, hier für Einachs-Positionierer. Bei mehreren Achsen müssen für jede Achse Parameter gesetzt werden.

        //4. Ausgewählte Achse aktivieren und Referenzfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibrierung und Anwendung des Erweiterungsachsen-Koordinatensystems (Hinweis: Positionierer und Linearschiene haben unterschiedliche Schnittstellen. Hier folgen die des Positionierers)
        DescPose pos = new DescPose(/* Geben Sie hier Ihre Kalibrierungspunktkoordinaten ein */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sie müssen diese Schnittstelle 4 Mal mit verschiedenen Punkten aufrufen, um die Achse zu kalibrieren */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); // Kalibrierungsergebnis berechnen
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  // Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden

        //6. Werkstückkoordinatensystem auf der Erweiterungsachse kalibrieren. Sie benötigen folgende Schnittstellen:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Startpunkt der synchronen Linearbewegung erfassen
        DescPose startdescPose = new DescPose(/* Geben Sie hier Ihre Koordinaten ein */);
        JointPos startjointPos = new JointPos(/* Geben Sie hier Ihre Koordinaten ein */);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Geben Sie hier Ihre Startkoordinaten für die Erweiterungsachse ein */);

        //8. Endpunkt der synchronen Linearbewegung erfassen
        DescPose enddescPose = new DescPose(/* Geben Sie hier Ihre Koordinaten ein */);
        JointPos endjointPos = new JointPos(/* Geben Sie hier Ihre Koordinaten ein */);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Geben Sie hier Ihre Endkoordinaten für die Erweiterungsachse ein */);

        //9. Synchronbewegungsprogramm erstellen
        // Zum Startpunkt bewegen, angenommen Werkzeug- und Werkstückkoordinatensystem sind beide 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        // Synchronbewegung starten
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
    }

Synchronbewegung von UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Synchronbewegung von UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung
    * @param [in] joint_pos_p Gelenkposition des Zwischenpunkts (Grad)
    * @param [in] desc_pos_p Kartesische Pose des Zwischenpunkts
    * @param [in] ptool Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] puser Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] pvel Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt (mm)
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zwischenpunkt)
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt
    * @param [in] joint_pos_t Gelenkposition des Zielpunkts (Grad)
    * @param [in] desc_pos_t Kartesische Pose des Zielpunkts
    * @param [in] ttool Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tuser Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tvel Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100], vorübergehend nicht freigegeben
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt (mm)
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem (für Zielpunkt)
    * @param [in] offset_pos_t Posenversatz für Zielpunkt
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) (mm)
    * @return Fehlercode
    */
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);

Codebeispiel
++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveC_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1. Kalibrieren und Anwenden des Roboter-Werkzeugkoordinatensystems. Sie können die Vier-Punkt- oder Sechs-Punkt-Methode verwenden. Die relevanten Schnittstellen sind:
        //    int SetToolPoint(int point_num);  // Werkzeugreferenzpunkt einstellen - Sechs-Punkt-Methode
        //    int ComputeTool(ref DescPose tcp_pose);  // Werkzeugkoordinatensystem berechnen
        //    int SetTcp4RefPoint(int point_num);    // Werkzeugreferenzpunkt einstellen - Vier-Punkt-Methode
        //    int ComputeTcp4(ref DescPose tcp_pose);   // Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  // Werkzeugkoordinatensystem einstellen und anwenden
        //    int SetToolList(int id, DescPose coord, int type, int install);   // Werkzeugkoordinatensystem in Liste einstellen und anwenden

        //2. UDP-Kommunikationsparameter einstellen und UDP-Kommunikation laden
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Parameter für Erweiterungsachsen einstellen, einschließlich Typ, Antriebsparameter, DH-Parameter
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Einachs-Positionierer und DH-Parameter
        robot.SetRobotPosToAxis(1);  // Einbauposition der Erweiterungsachse
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Servoantriebsparameter, hier für Einachs-Positionierer. Bei mehreren Achsen müssen für jede Achse Parameter gesetzt werden.

        //4. Ausgewählte Achse aktivieren und Referenzfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibrierung und Anwendung des Erweiterungsachsen-Koordinatensystems (Hinweis: Positionierer und Linearschiene haben unterschiedliche Schnittstellen. Hier folgen die des Positionierers)
        DescPose pos = new DescPose(/* Geben Sie hier Ihre Kalibrierungspunktkoordinaten ein */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sie müssen diese Schnittstelle 4 Mal mit verschiedenen Punkten aufrufen, um die Achse zu kalibrieren */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); // Kalibrierungsergebnis berechnen
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  // Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden

        //6. Werkstückkoordinatensystem auf der Erweiterungsachse kalibrieren. Sie benötigen folgende Schnittstellen:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Startpunkt der synchronen Kreisbogenbewegung erfassen
        DescPose startdescPose = new DescPose(/* Geben Sie hier Ihre Koordinaten ein */);
        JointPos startjointPos = new JointPos(/* Geben Sie hier Ihre Koordinaten ein */);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Geben Sie hier Ihre Startkoordinaten für die Erweiterungsachse ein */);

        //8. Endpunkt der synchronen Kreisbogenbewegung erfassen
        DescPose enddescPose = new DescPose(/* Geben Sie hier Ihre Koordinaten ein */);
        JointPos endjointPos = new JointPos(/* Geben Sie hier Ihre Koordinaten ein */);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Geben Sie hier Ihre Endkoordinaten für die Erweiterungsachse ein */);

        //9. Zwischenpunkt der synchronen Kreisbogenbewegung erfassen
        DescPose middescPose = new DescPose(/* Geben Sie hier Ihre Koordinaten ein */);
        JointPos midjointPos = new JointPos(/* Geben Sie hier Ihre Koordinaten ein */);
        ExaxisPos midexaxisPos = new ExaxisPos(/* Geben Sie hier die Koordinaten der Erweiterungsachse am Kreisbogen-Zwischenpunkt ein */);

        //10. Synchronbewegungsprogramm erstellen
        // Zum Startpunkt bewegen, angenommen Werkzeug- und Werkstückkoordinatensystem sind beide 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        // Synchronbewegung starten
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
    }

Erweiterten Digitalausgang (DO) setzen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Erweiterten Digitalausgang (DO) setzen
    * @param [in] DONum DO-Nummer
    * @param [in] bOpen Schaltzustand true-ein; false-aus
    * @param [in] smooth Glättung aktivieren
    * @param [in] block Blockierend ausführen
    * @return Fehlercode
    */
    int SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);

Erweiterten Analogausgang (AO) setzen
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Erweiterten Analogausgang (AO) setzen
    * @param [in] AONum AO-Nummer
    * @param [in] value Analogwert [0-4095]
    * @param [in] block Blockierend ausführen
    * @return Fehlercode
    */
    int SetAuxAO(int AONum, double value, bool block);

Eingangsfilterzeit für erweiterten Digitaleingang (DI) einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Eingangsfilterzeit für erweiterten Digitaleingang (DI) einstellen
    * @param [in] filterTime Filterzeit (ms)
    * @return Fehlercode
    */
    int SetAuxDIFilterTime(int filterTime);

Eingangsfilterzeit für erweiterten Analogeingang (AI) einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Eingangsfilterzeit für erweiterten Analogeingang (AI) einstellen
    * @param [in] filterTime Filterzeit (ms)
    * @return Fehlercode
    */
    int SetAuxAIFilterTime(int filterTime);

Auf erweiterten Digitaleingang (DI) warten
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Auf erweiterten Digitaleingang (DI) warten
    * @param [in] DINum DI-Nummer
    * @param [in] bOpen Erwarteter Zustand 0-aus; 1-ein
    * @param [in] time Maximale Wartezeit (ms)
    * @param [in] errorAlarm Bewegung bei Timeout fortsetzen (false) oder anhalten (true)
    * @return Fehlercode
    */
    int WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);

Auf erweiterten Analogeingang (AI) warten
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Auf erweiterten Analogeingang (AI) warten
    * @param [in] AINum AI-Nummer
    * @param [in] sign Bedingung 0-größer als; 1-kleiner als
    * @param [in] value Vergleichswert
    * @param [in] time Maximale Wartezeit (ms)
    * @param [in] errorAlarm Bewegung bei Timeout fortsetzen (false) oder anhalten (true)
    * @return Fehlercode
    */
    int WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);

Wert des erweiterten Digitaleingangs (DI) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Wert des erweiterten Digitaleingangs (DI) abrufen
    * @param [in] DINum DI-Nummer
    * @param [in] isNoBlock Nicht-blockierend (true) / blockierend (false)
    * @param [out] isOpen 0-aus; 1-ein
    * @return Fehlercode
    */
    int GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);

Wert des erweiterten Analogeingangs (AI) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Wert des erweiterten Analogeingangs (AI) abrufen
    * @param [in] AINum AI-Nummer
    * @param [in] isNoBlock Nicht-blockierend (true) / blockierend (false)
    * @param [out] value Eingangswert
    * @return Fehlercode
    */
    int GetAuxAI(int AINum, bool isNoBlock, int& value);

Codebeispiel für erweiterten I/O
++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnAODO_Click(object sender, EventArgs e)
    {
        int rtn;
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            Thread.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            Thread.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            Thread.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);

        for (int i = 0; i < 20; i++)
        {
            bool curValue = false;
            rtn = robot.GetAuxDI(i, false, ref curValue);
            Console.WriteLine("DI" + i + "   " + curValue);
        }
        int curValueAI = -1;
        for (int i = 0; i < 4; i++)
        {
            rtn = robot.GetAuxAI(i, true, ref curValueAI);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);
    }

Mobile Basis aktivieren (z.B. fahrerlose Transportfahrzeug)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Mobile Basis aktivieren
    * @param enable false-deaktivieren; true-aktivieren
    * @return Fehlercode
    */
    int TractorEnable(bool enable);

Mobile Basis anhalten
+++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Mobile Basis anhalten
    * @return Fehlercode
    */
    int TractorStop();

Mobile Basis auf Nullpunkt fahren (Referenzfahrt)
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Mobile Basis auf Nullpunkt fahren (Referenzfahrt)
    * @return Fehlercode
    */
    int TractorHoming();

Linearbewegung der mobilen Basis
++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Linearbewegung der mobilen Basis
    * @param distance Lineare Bewegungsdistanz (mm)
    * @param vel Geschwindigkeitsprozentsatz für Linearbewegung (0-100)
    * @return Fehlercode
    */
    int TractorMoveL(double distance, double vel);

Kreisbogenbewegung der mobilen Basis
++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Kreisbogenbewegung der mobilen Basis
    * @param radius Radius der Kreisbogenbewegung (mm)
    * @param angle Winkel der Kreisbogenbewegung (°)
    * @param vel Geschwindigkeitsprozentsatz für Linearbewegung (0-100)
    * @return Fehlercode
    */
    int TractorMoveC(double radius, double angle, double vel);

Codebeispiel
++++++++++++

.. code-block:: c#
    :linenos:

    private void button6_Click(object sender, EventArgs e)
    {
        int rtn;
        robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10,1);
        robot.ExtDevLoadUDPDriver();
        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);
        Thread.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Thread.Sleep(4000);
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
        robot.TractorEnable(false);
        Thread.Sleep(2000);
        robot.TractorEnable(true);
        Thread.Sleep(2000);
        robot.TractorHoming();
        Thread.Sleep(2000);
        robot.TractorMoveL(100, 2);
        Thread.Sleep(5000);
        robot.TractorStop();
        robot.TractorMoveL(-100, 20);
        Thread.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        Thread.Sleep(10000);
        robot.TractorMoveC(300, -90, 20);
        Thread.Sleep(1000);
        robot.TractorStop();
    }

Strategie für die Synchronbewegung von Erweiterungsachse und Roboter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    /**
    * @brief Strategie für die Synchronbewegung von Erweiterungsachse und Roboter einstellen
    * @param strategy Strategie; 0-Roboter ist führend; 1-Erweiterungsachse und Roboter synchron
    * @return Fehlercode
    */
    int SetExAxisRobotPlan(int strategy)

Codebeispiel für das Einstellen der Synchronbewegungsstrategie von Erweiterungsachse und Roboter
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    private void button94_Click(object sender, EventArgs e)
    {
        JointPos joint_pos1 = new JointPos(-22.016, -49.217, 124.714, -161.100, -85.108, -0.333);
        JointPos joint_pos2 = new JointPos(-21.083, -46.613, 110.079, -147.796, -80.757, -0.330);
        JointPos joint_pos3 = new JointPos(-25.572, -60.090, 135.397, -163.889, -82.489, -0.345);
        DescPose desc_pos1 = new DescPose(2.637, -0.001, 30.673, 178.786, -4.134, 68.326);
        DescPose desc_pos2 = new DescPose(213.812, -1.440, 47.311, 177.410, 0.166, 68.946);
        DescPose desc_pos3 = new DescPose(444.342, -12.723, 82.470, -177.701, -1.325, 65.151);
        ExaxisPos epos1 = new ExaxisPos(0.001, 0.000, 0.000, 0.000);
        ExaxisPos epos2 = new ExaxisPos(299.977, 0.000, 0.000, 0.000);
        ExaxisPos epos3 = new ExaxisPos(399.969, 0.000, 0.000, 0.000);
        DescPose offset_pos = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.SetExAxisRobotPlan(0);
        Console.WriteLine($"SetExAxisRobotPlan rtn is {rtn}");
        Thread.Sleep(1000);
        rtn = robot.ExtAxisSyncMoveL(joint_pos1, desc_pos1, 1, 0, 100, 100, 100, -1, epos1, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 1 rtn is {rtn}");

        rtn = robot.ExtAxisSyncMoveL(joint_pos2, desc_pos2, 1, 0, 100, 100, 100, -1, epos2, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 2 rtn is {rtn}");
        rtn = robot.ExtAxisSyncMoveL(joint_pos3, desc_pos3, 1, 0, 100, 100, 100, -1, epos3, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 3 rtn is {rtn}");
        Thread.Sleep(8000);
    }