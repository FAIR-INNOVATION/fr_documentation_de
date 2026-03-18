Erweiterungsachsen
=============================

.. toctree::
    :maxdepth: 5

Parameter für 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Parameter für eine 485-Erweiterungsachse ein
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] servoCompany Hersteller des Servoantriebs, 1-DYNATEC
    * @param [in] servoModel Modell des Servoantriebs, 1-FD100-750C
    * @param [in] servoSoftVersion Softwareversion des Servoantriebs, 1-V1.0
    * @param [in] servoResolution Encoderauflösung
    * @param [in] axisMechTransRatio Mechanisches Übersetzungsverhältnis
    * @return Fehlercode
    */
    errno_t AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);

Konfigurationsparameter der 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Konfigurationsparameter einer 485-Erweiterungsachse zurück
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [out] servoCompany Hersteller des Servoantriebs, 1-DYNATEC
    * @param [out] servoModel Modell des Servoantriebs, 1-FD100-750C
    * @param [out] servoSoftVersion Softwareversion des Servoantriebs, 1-V1.0
    * @param [out] servoResolution Encoderauflösung
    * @param [out] axisMechTransRatio Mechanisches Übersetzungsverhältnis
    * @return Fehlercode
    */
    errno_t AuxServoGetParam(int servoId, int* servoCompany, int* servoModel, int* servoSoftVersion, int* servoResolution, double* axisMechTransRatio);

Aktivierung/Deaktivierung der 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Aktivierung/Deaktivierung der 485-Erweiterungsachse ein
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] status Aktivierungsstatus, 0-deaktivieren, 1-aktivieren
    * @return Fehlercode
    */
    errno_t AuxServoEnable(int servoId, int status);

Steuerungsmodus der 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt den Steuerungsmodus der 485-Erweiterungsachse ein
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] mode Steuerungsmodus, 0-Positionsmodus, 1-Geschwindigkeitsmodus
    * @return Fehlercode
    */
    errno_t AuxServoSetControlMode(int servoId, int mode);

Zielposition der 485-Erweiterungsachse einstellen (Positionsmodus)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Zielposition der 485-Erweiterungsachse ein (Positionsmodus)
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] pos Zielposition, mm oder °
    * @param [in] speed Zielgeschwindigkeit, mm/s oder °/s
    * @return Fehlercode
    */
    errno_t AuxServoSetTargetPos(int servoId, double pos, double speed);

Zieldrehmoment der 485-Erweiterungsachse einstellen (Drehmomentmodus) - noch nicht freigegeben
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt das Zieldrehmoment der 485-Erweiterungsachse ein (Drehmomentmodus)
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] torque Zieldrehmoment, Nm
    * @return Fehlercode
    */
    errno_t AuxServoSetTargetTorque(int servoId, double torque);

Referenzpunktfahrt der 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Referenzpunktfahrt der 485-Erweiterungsachse ein
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] mode Referenzpunktfahrt-Modus, 0-aktuelle Position als Nullpunkt; 1-Endlagenschalter als Nullpunkt
    * @param [in] searchVel Suchgeschwindigkeit, mm/s oder °/s
    * @param [in] latchVel Einrastgeschwindigkeit, mm/s oder °/s
    * @return Fehlercode
    */
    errno_t AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);

Fehlerinformationen der 485-Erweiterungsachse löschen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Löscht Fehlerinformationen der 485-Erweiterungsachse
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @return Fehlercode
    */
    errno_t AuxServoClearError(int servoId);

Servostatus der 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt den Servostatus der 485-Erweiterungsachse zurück
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [out] servoErrCode Fehlercode des Servoantriebs
    * @param [out] servoState Status des Servoantriebs [Dezimalzahl in Binär, bit0-bit5: Servo aktiviert - Servo läuft - positive Endlage ausgelöst - negative Endlage ausgelöst - Positionierung abgeschlossen - Referenzpunktfahrt abgeschlossen]
    * @param [out] servoPos Aktuelle Position des Servos mm oder °
    * @param [out] servoSpeed Aktuelle Geschwindigkeit des Servos mm/s oder °/s
    * @param [out] servoTorque Aktuelles Drehmoment des Servos Nm
    * @return Fehlercode
    */
    errno_t AuxServoGetStatus(int servoId, int* servoErrCode, int* servoState, double* servoPos, double* servoSpeed, double* servoTorque);

Zielgeschwindigkeit der 485-Erweiterungsachse einstellen (Geschwindigkeitsmodus)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Zielgeschwindigkeit der 485-Erweiterungsachse ein (Geschwindigkeitsmodus)
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @param [in] speed Zielgeschwindigkeit, mm/s oder °/s
    * @return Fehlercode
    */
    errno_t AuxServoSetTargetSpeed(int servoId, double speed);

Achsnummer der 485-Erweiterungsachse in der Statusrückmeldung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Achsnummer der 485-Erweiterungsachse in der Statusrückmeldung ein
    * @param [in] servoId Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    * @return Fehlercode
    */
    errno_t AuxServosetStatusID(int servoId);

Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse ein
    * @param [in] acc Bewegungsbeschleunigung der 485-Erweiterungsachse
    * @param [in] dec Bewegungsverzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    errno_t AuxServoSetAcc(double acc, double dec);

Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse ein
    * @param [in] acc Not-Halt-Beschleunigung der 485-Erweiterungsachse
    * @param [in] dec Not-Halt-Verzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    errno_t AuxServoSetEmergencyStopAcc(double acc, double dec);

Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse zurück
    * @param [out] acc Bewegungsbeschleunigung der 485-Erweiterungsachse
    * @param [out] dec Bewegungsverzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    errno_t AuxServoGetAcc(double& acc, double& dec);

Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse zurück
    * @param [out] acc Not-Halt-Beschleunigung der 485-Erweiterungsachse
    * @param [out] dec Not-Halt-Verzögerung der 485-Erweiterungsachse
    * @return Fehlercode
    */
    errno_t AuxServoGetEmergencyStopAcc(double& acc, double& dec);

Codebeispiel zur Steuerung einer Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int Test485Auxservo(void)
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
      int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      int servoCompany;
      int servoModel;
      int servoSoftVersion;
      int servoResolution;
      double axisMechTransRatio;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      robot.Sleep(3000);
      robot.AuxServoSetAcc(3000, 3000);
      robot.AuxServoSetEmergencyStopAcc(5000, 5000);
      robot.Sleep(1000);
      double emagacc = 0, acc = 0;
      double emagdec = 0, dec = 0;
      robot.AuxServoGetEmergencyStopAcc(emagacc, emagdec);
      printf("emergency acc is %f dec is %f \n", emagacc, emagdec);
      robot.AuxServoGetAcc(acc, dec);
      printf("acc is %f dec is %f \n", acc, dec);
      robot.AuxServoSetControlMode(1, 0);
      robot.Sleep(2000);
      retval = robot.AuxServoEnable(1, 0);
      std::cout << "AuxServoEnable disenable " << retval << std::endl;
      robot.Sleep(1000);
      int servoerrcode = 0;
      int servoErrCode;
      int servoState;
      double servoPos;
      double servoSpeed;
      double servoTorque;
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);;
      retval = robot.AuxServoEnable(1, 1);
      std::cout << "AuxServoEnable enable " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoHoming(1, 1, 5, 1);
      std::cout << "AuxServoHoming " << retval << std::endl;
      robot.Sleep(3000);
      retval = robot.AuxServoSetTargetPos(1, 200, 30);
      std::cout << "AuxServoSetTargetPos " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoSpeed " << servoSpeed << std::endl;
      robot.Sleep(8000);
      robot.AuxServoSetControlMode(1, 1);
      robot.Sleep(2000);
      robot.AuxServoEnable(1, 0);
      robot.Sleep(1000);
      robot.AuxServoEnable(1, 1);
      robot.Sleep(1000);
      robot.AuxServoSetTargetSpeed(1, 100, 80);
      robot.Sleep(5000);
      robot.AuxServoSetTargetSpeed(1, 0, 80);
      robot.CloseRPC();
      return 0;
    }

UDP-Kommunikationsparameter für Erweiterungsachse konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguriert die UDP-Kommunikationsparameter für die Erweiterungsachse
    * @param [in] ip IP-Adresse der SPS
    * @param [in] port  Portnummer
    * @param [in] period    Kommunikationszyklus (ms, Standard 2, diesen Parameter nicht ändern)
    * @param [in] lossPkgTime   Paketverlust-Erkennungszeit (ms)
    * @param [in] lossPkgNum    Anzahl der Paketverluste
    * @param [in] disconnectTime    Bestätigungsdauer für Kommunikationsunterbrechung
    * @param [in] reconnectEnable   Automatische Wiederverbindung bei Kommunikationsunterbrechung aktivieren 0-deaktivieren 1-aktivieren
    * @param [in] reconnectPeriod   Wiederverbindungsintervall (ms)
    * @param [in] reconnectNum  Anzahl der Wiederverbindungsversuche
    * @param [in] selfConnect Automatische Verbindung nach Neustart? 0-keine Verbindung; 1-Verbindung herstellen
    * @return Fehlercode
    */
    errno_t ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect = 1);

UDP-Kommunikationsparameter für Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die UDP-Kommunikationsparameter für die Erweiterungsachse zurück
    * @param [out] ip IP-Adresse der SPS
    * @param [out] port   Portnummer
    * @param [out] period   Kommunikationszyklus (ms)
    * @param [out] lossPkgTime   Paketverlust-Erkennungszeit (ms)
    * @param [out] lossPkgNum   Anzahl der Paketverluste
    * @param [out] disconnectTime   Bestätigungsdauer für Kommunikationsunterbrechung
    * @param [out] reconnectEnable   Automatische Wiederverbindung bei Kommunikationsunterbrechung aktiviert? 0-deaktiviert, 1-aktiviert
    * @param [out] reconnectPeriod   Wiederverbindungsintervall (ms)
    * @param [out] reconnectNum   Anzahl der Wiederverbindungsversuche
    * @return Fehlercode
    */
    errno_t ExtDevGetUDPComParam(std::string& ip, int& port, int& period, int& lossPkgTime, int& lossPkgNum, int& disconnectTime, int& reconnectEnable, int& reconnectPeriod, int& reconnectNum);

UDP-Kommunikation laden
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Lädt die UDP-Kommunikation
    * @return Fehlercode
    */
    errno_t ExtDevLoadUDPDriver();

UDP-Kommunikation entladen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Entlädt die UDP-Kommunikation
    * @return Fehlercode
    */
    errno_t ExtDevUnloadUDPDriver();

Verbindung nach abnormaler UDP-Kommunikationsunterbrechung wiederherstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Verbindung nach einer abnormalen UDP-Kommunikationsunterbrechung wieder her
    * @return Fehlercode
    */
    errno_t ExtDevUDPClientComReset();

Kommunikation nach abnormaler UDP-Kommunikationsunterbrechung schließen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Schließt die Kommunikation nach einer abnormalen UDP-Kommunikationsunterbrechung
    * @return Fehlercode
    */
    errno_t ExtDevUDPClientComClose();

Parameter für UDP-Erweiterungsachse konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguriert die Parameter einer UDP-Erweiterungsachse
    * @param [in] axisID Achsnummer
    * @param [in] axisType Erweiterungsachsentyp 0-Translation; 1-Rotation
    * @param [in] axisDirection Richtung der Erweiterungsachse 0-positive Richtung; 1-negative Richtung (Achtung: 0-positiv, 1-negativ? Laut Beispiel 1)
    * @param [in] axisMax Maximale Position der Achse mm
    * @param [in] axisMin Minimale Position der Achse mm
    * @param [in] axisVel Geschwindigkeit mm/s
    * @param [in] axisAcc Beschleunigung mm/s²
    * @param [in] axisLead Spindelsteigung mm
    * @param [in] encResolution Encoderauflösung
    * @param [in] axisOffect Versatz des Schweißnahtstartpunkts zur Erweiterungsachse
    * @param [in] axisCompany Antriebshersteller 1-Hechuan; 2-Inovance; 3-Panasonic
    * @param [in] axisModel Antriebsmodell 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Encodertyp 0-inkremental; 1-absolut
    * @return Fehlercode
    */
    errno_t ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Einbauposition der Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Einbauposition der Erweiterungsachse ein
    * @param [in] installType 0-Roboter auf der externen Achse montiert, 1-Roboter außerhalb der externen Achse montiert
    * @return Fehlercode
    */
    errno_t SetRobotPosToAxis(int installType);

DH-Parameter des Erweiterungsachsensystems einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die DH-Parameter des Erweiterungsachsensystems ein
    * @param [in] axisConfig Konfiguration der externen Achse, 0-Linearführung mit einem Freiheitsgrad, 1-L-förmiger Positionierer mit zwei Freiheitsgraden, 2-drei Freiheitsgrade, 3-vier Freiheitsgrade, 4-Positionierer mit einem Freiheitsgrad
    * @param [in] axisDHd1 DH-Parameter d1 der externen Achse mm
    * @param [in] axisDHd2 DH-Parameter d2 der externen Achse mm
    * @param [in] axisDHd3 DH-Parameter d3 der externen Achse mm
    * @param [in] axisDHd4 DH-Parameter d4 der externen Achse mm
    * @param [in] axisDHa1 DH-Parameter a1 der externen Achse mm
    * @param [in] axisDHa2 DH-Parameter a2 der externen Achse mm
    * @param [in] axisDHa3 DH-Parameter a3 der externen Achse mm
    * @param [in] axisDHa4 DH-Parameter a4 der externen Achse mm
    * @return Fehlercode
    */
    errno_t SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

UDP-Erweiterungsachse aktivieren
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktiviert/Deaktiviert die UDP-Erweiterungsachse
    * @param [in] axisID Achsnummer [1-4]
    * @param [in] status 0-deaktivieren; 1-aktivieren
    * @return Fehlercode
    */
    errno_t ExtAxisServoOn(int axisID, int status);

Referenzpunktfahrt der UDP-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Referenzpunktfahrt der UDP-Erweiterungsachse ein
    * @param [in] axisID Achsnummer [1-4]
    * @param [in] mode Referenzpunktfahrt-Modus 0-aktuelle Position als Nullpunkt, 1-negative Endlage als Nullpunkt, 2-positive Endlage als Nullpunkt
    * @param [in] searchVel Suchgeschwindigkeit (mm/s)
    * @param [in] latchVel Einrastgeschwindigkeit (mm/s)
    * @return Fehlercode
    */
    errno_t ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Tippbetrieb (Jog) der UDP-Erweiterungsachse starten
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Startet den Tippbetrieb (Jog) der UDP-Erweiterungsachse
    * @param [in] axisID Achsnummer [1-4]
    * @param [in] direction Drehrichtung 0-negativ; 1-positiv
    * @param [in] vel Geschwindigkeit (mm/s)
    * @param [in] acc Beschleunigung (mm/s²)
    * @param [in] maxDistance Maximale Tippdistanz
    * @return Fehlercode
    */
    errno_t ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);

Tippbetrieb (Jog) der UDP-Erweiterungsachse stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stoppt den Tippbetrieb (Jog) der UDP-Erweiterungsachse
    * @param [in] axisID Achsnummer [1-4]
    * @return Fehlercode
    */
    errno_t ExtAxisStopJog(int axisID);

Codebeispiel für Konfiguration und Tippbetrieb einer UDP-Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxis(void)
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
      rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
      cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
      string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
      rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum);
      string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum " + to_string(lossPkgNum) + "\ndisConntime " + to_string(disconnectTime) + "\nreconnecable " + to_string(reconnectEnable) + "\nreconnperiod " + to_string(reconnectPeriod) + "\nreconnnun " + to_string(reconnectNum);
      cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
      robot.ExtDevLoadUDPDriver();
      rtn = robot.ExtAxisServoOn(1, 1);
      cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
      rtn = robot.ExtAxisServoOn(2, 1);
      cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
      robot.Sleep(2000);
      robot.ExtAxisSetHoming(1, 0, 10, 2);
      robot.Sleep(2000);
      rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
      cout << "ExtAxisSetHoming rtnn is " << rtn << endl;
      robot.Sleep(4000);
      rtn = robot.SetRobotPosToAxis(1);
      cout << "SetRobotPosToAxis rtn is " << rtn << endl;
      rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
      cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
      rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
      cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
      rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
      cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
      robot.Sleep(1000 * 3);
      robot.ExtAxisStartJog(1, 0, 10, 10, 30);
      robot.Sleep(1000 * 1);
      robot.ExtAxisStopJog(1);
      robot.Sleep(1000 * 3);
      robot.ExtAxisServoOn(1, 0);
      robot.Sleep(1000 * 3);
      robot.ExtAxisStartJog(2, 0, 10, 10, 30);
      robot.Sleep(1000 * 1);
      robot.ExtAxisStopJog(2);
      robot.Sleep(1000 * 3);
      robot.ExtAxisServoOn(2, 0);
      robot.ExtDevUnloadUDPDriver();
      robot.CloseRPC();
      return 0;
    }

Referenzpunkte für das Erweiterungsachsen-Koordinatensystem einstellen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt Referenzpunkte für das Erweiterungsachsen-Koordinatensystem ein - Vier-Punkt-Methode
    * @param [in] pointNum Punktnummer [1-4]
    * @return Fehlercode
    */
    errno_t ExtAxisSetRefPoint(int pointNum);

Erweiterungsachsen-Koordinatensystem berechnen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Berechnet das Erweiterungsachsen-Koordinatensystem - Vier-Punkt-Methode
    * @param [out] coord Koordinatenwerte
    * @return Fehlercode
    */
    errno_t ExtAxisComputeECoordSys(DescPose& coord);

Referenzpunkte für das Positionierer-Koordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt Referenzpunkte für das Positionierer-Koordinatensystem ein
    * @param [in] pointNum Punktnummer [1-4]
    * @return Fehlercode
    */
    errno_t PositionorSetRefPoint(int pointNum);

Positionierer-Koordinatensystem berechnen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Berechnet das Positionierer-Koordinatensystem - Vier-Punkt-Methode
    * @param [out] coord Koordinatenwerte
    * @return Fehlercode
    */
    errno_t PositionorComputeECoordSys(DescPose& coord);

Pose des Kalibrierreferenzpunkts im Positionierer-Endkoordinatensystem einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Pose des Kalibrierreferenzpunkts im Positionierer-Endkoordinatensystem ein
    * @param [in] pos Posenwert
    * @return Fehlercode
    */
    errno_t SetRefPointInExAxisEnd(DescPose pos);

Erweiterungsachsen-Koordinatensystem anwenden
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Wendet das Erweiterungsachsen-Koordinatensystem an
    * @param [in] applyAxisId Erweiterungsachsennummern als Bitmaske, Bit0-Bit3 entsprechen den Achsnummern 1-4. z.B. Achsen 1 und 3 anwenden: 0b 0000 0101 = 5
    * @param [in] axisCoordNum Nummer des Erweiterungsachsen-Koordinatensystems
    * @param [in] coord Koordinatenwerte
    * @param [in] calibFlag Kalibrierungsflag 0-nein, 1-ja
    * @return Fehlercode
    */
    errno_t ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Erweiterungsachsen-Koordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt das Erweiterungsachsen-Koordinatensystem zurück
    * @param [out] coord Erweiterungsachsen-Koordinatensystem
    * @return Fehlercode
    */
    errno_t ExtAxisGetCoord(DescPose& coord);

Codebeispiel für die Kalibrierung des Erweiterungsachsen-Koordinatensystems
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
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
       rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
       cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
       string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
       rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum);
       string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum " + to_string(lossPkgNum) + "\ndisConntime " + to_string(disconnectTime) + "\nreconnecable " + to_string(reconnectEnable) + "\nreconnperiod " + to_string(reconnectPeriod) + "\nreconnnun " + to_string(reconnectNum);
       cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
       robot.ExtDevLoadUDPDriver();
       rtn = robot.ExtAxisServoOn(1, 1);
       cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisServoOn(2, 1);
       cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.ExtAxisSetHoming(1, 0, 10, 2);
       robot.Sleep(2000);
       rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
       cout << "ExtAxisSetHoming rtnn is " << rtn << endl;
       robot.Sleep(4000);
       rtn = robot.SetRobotPosToAxis(1);
       cout << "SetRobotPosToAxis rtn is " << rtn << endl;
       rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0);
       cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       DescPose toolCoord(0, 0, 210, 0, 0, 0);
       robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
       JointPos jSafe(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
       JointPos j1(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
       JointPos j2(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
       JointPos j3(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
       JointPos j4(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);
       DescPose descSafe = {};
       DescPose desc1 = {};
       DescPose desc2 = {};
       DescPose desc3 = {};
       DescPose desc4 = {};
       ExaxisPos exaxisPos = { 0, 0, 0, 0 };
       DescPose offdese = { 0, 0, 0, 0, 0, 0 };
       robot.GetForwardKin(&jSafe, &descSafe);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       robot.GetForwardKin(&j1, &desc1);
       robot.MoveJ(&j1, &desc1, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       DescPose actualTCPPos = {};
       robot.GetActualTCPPose(0, &actualTCPPos);
       robot.SetRefPointInExAxisEnd(actualTCPPos);
       rtn = robot.PositionorSetRefPoint(1);
       cout << "PositionorSetRefPoint 1 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j2, &desc2);
       rtn = robot.MoveJ(&j2, &desc2, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(2);
       cout << "PositionorSetRefPoint 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j3, &desc3);
       robot.MoveJ(&j3, &desc3, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(3);
       cout << "PositionorSetRefPoint 3 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j4, &desc4);
       robot.MoveJ(&j4, &desc4, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(4);
       cout << "PositionorSetRefPoint 4 rtn is " << rtn << endl;
       robot.Sleep(2000);
       DescPose axisCoord = {};
       robot.PositionorComputeECoordSys(axisCoord);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       printf("PositionorComputeECoordSys rtn is %f %f %f %f %f %f\n", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
       rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
       cout << "ExtAxisActiveECoordSys rtn is " << rtn << endl;
       DescPose getCoord(0, 0, 0, 0, 0, 0);
       rtn = robot.ExtAxisGetCoord(getCoord);
       printf("ExtAxisGetCoord rtn is %f %f %f %f %f %f\n", getCoord.tran.x, getCoord.tran.y, getCoord.tran.z, getCoord.rpy.rx, getCoord.rpy.ry, getCoord.rpy.rz);
       robot.CloseRPC();
       return 0;
    }

UDP-Erweiterungsachsen-Bewegung
++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Bewegung der UDP-Erweiterungsachse
    * @param [in] pos Zielposition
    * @param [in] ovl Geschwindigkeitsprozentsatz
    * @param [in] blend Glättungsparameter (mm oder ms); -1: auf Bewegungsabschluss warten (blockierend)
    * @return Fehlercode
    */
    errno_t ExtAxisMove(ExaxisPos pos, double ovl, double blend = -1);

Codebeispiel für UDP-Erweiterungsachsen-Bewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
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
      ExaxisPos axisPos;
      axisPos.ePos[0] = 20;
      axisPos.ePos[1] = 0;
      axisPos.ePos[2] = 0;
      axisPos.ePos[3] = 0;
      robot.ExtAxisMove(axisPos, 50);
      robot.CloseRPC();
      return 0;
    }

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg
    * @param [in] desc_pos Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] epos Erweiterachsenposition, Einheit mm
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit ms
    * @param [in] offset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos  Posenversatz
    * @return  Fehlercode
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung (automatische Vorwärtskinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung (automatische Vorwärtskinematik)
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] epos Erweiterachsenposition, Einheit mm
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit ms
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, uint8_t offset_flag, DescPose offset_pos);

Codebeispiel für synchronisierte Gelenkbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveJ()
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

        //1. Kalibrieren und Anwenden des Roboter-Werkzeugkoordinatensystems. Sie können die Vier-Punkt- oder Sechs-Punkt-Methode verwenden. Die relevanten Schnittstellen sind:
        //  int SetToolPoint(int point_num); // Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
        //  int ComputeTool(ref DescPose tcp_pose); // Werkzeugkoordinatensystem berechnen
        //  int SetTcp4RefPoint(int point_num);  // Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
        //  int ComputeTcp4(ref DescPose tcp_pose);  // Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
        //  int SetToolCoord(int id, DescPose coord, int type, int install); // Werkzeugkoordinatensystem einstellen und anwenden
        //  int SetToolList(int id, DescPose coord, int type, int install);  // Werkzeugkoordinatensystem in Liste einstellen und anwenden

        //2. UDP-Kommunikationsparameter einstellen und UDP-Kommunikation laden
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Parameter für Erweiterungsachsen einstellen, einschließlich Typ, Antriebsparameter, DH-Parameter
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Einachs-Positionierer und DH-Parameter
        robot.SetRobotPosToAxis(1); // Einbauposition der Erweiterungsachse
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Servoantriebsparameter, hier für Einachs-Positionierer. Bei mehreren Achsen müssen für jede Achse Parameter gesetzt werden.

        //4. Ausgewählte Achse aktivieren und Referenzfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibrierung und Anwendung des Erweiterungsachsen-Koordinatensystems
        DescPose pos = {/* Geben Sie hier Ihre Kalibrierungspunktkoordinaten ein */ };
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sie müssen diese Schnittstelle 4 Mal mit verschiedenen Punkten aufrufen, um die Achse zu kalibrieren */
        DescPose coord = {};
        robot.PositionorComputeECoordSys(coord); // Kalibrierungsergebnis berechnen
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); // Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden

        //6. Werkstückkoordinatensystem auf der Erweiterungsachse kalibrieren. Sie benötigen folgende Schnittstellen:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Startpunkt der synchronen Gelenkbewegung erfassen
        DescPose startdescPose = {/* Geben Sie hier Ihre Koordinaten ein */ };
        JointPos startjointPos = {/* Geben Sie hier Ihre Koordinaten ein */ };
        ExaxisPos startexaxisPos = {/* Geben Sie hier Ihre Startkoordinaten für die Erweiterungsachse ein */ };

        //8. Endpunkt der synchronen Gelenkbewegung erfassen
        DescPose enddescPose = {/* Geben Sie hier Ihre Koordinaten ein */ };
        JointPos endjointPos = {/* Geben Sie hier Ihre Koordinaten ein */ };
        ExaxisPos endexaxisPos = {/* Geben Sie hier Ihre Endkoordinaten für die Erweiterungsachse ein */ };

        //9. Synchronbewegungsprogramm erstellen
        // Zum Startpunkt bewegen, angenommen Werkzeug- und Werkstückkoordinatensystem sind beide 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = { 0, 0, 0, 0, 0, 0 };
        robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);

        // Synchronbewegung starten
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);

        // Zum Startpunkt bewegen (Überladung ohne Zielpose)
        robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);

        // Synchronbewegung starten (Überladung ohne Zielpose)
        robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);

        robot.CloseRPC();
    }

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung
    * @param [in] joint_pos  Ziel-Gelenkposition, Einheit deg
    * @param [in] desc_pos   Ziel-Kartesische Pose
    * @param [in] tool  Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user  Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel  Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc  Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl  Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param [in] epos  Erweiterachsenposition, Einheit mm
    * @param [in] offset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos  Posenversatz
    * @return Fehlercode
    */
    errno_t ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung (automatische inverse Kinematik)
    * @param [in] desc_pos  Ziel-Kartesische Pose
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14]
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14]
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100]
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param [in] epos Erweiterachsenposition, Einheit mm
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen
    * @return Fehlercode
    */
    errno_t ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, uint8_t offset_flag, DescPose offset_pos, int config = -1);

Codebeispiel für synchronisierte Linearbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveL()
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

        //1. Kalibrieren und Anwenden des Roboter-Werkzeugkoordinatensystems. Sie können die Vier-Punkt- oder Sechs-Punkt-Methode verwenden. Die relevanten Schnittstellen sind:
        //  int SetToolPoint(int point_num); // Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
        //  int ComputeTool(ref DescPose tcp_pose); // Werkzeugkoordinatensystem berechnen
        //  int SetTcp4RefPoint(int point_num);  // Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
        //  int ComputeTcp4(ref DescPose tcp_pose);  // Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
        //  int SetToolCoord(int id, DescPose coord, int type, int install); // Werkzeugkoordinatensystem einstellen und anwenden
        //  int SetToolList(int id, DescPose coord, int type, int install);  // Werkzeugkoordinatensystem in Liste einstellen und anwenden

        //2. UDP-Kommunikationsparameter einstellen und UDP-Kommunikation laden
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Parameter für Erweiterungsachsen einstellen, einschließlich Typ, Antriebsparameter, DH-Parameter
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Einachs-Positionierer und DH-Parameter
        robot.SetRobotPosToAxis(1); // Einbauposition der Erweiterungsachse
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Servoantriebsparameter, hier für Einachs-Positionierer. Bei mehreren Achsen müssen für jede Achse Parameter gesetzt werden.

        //4. Ausgewählte Achse aktivieren und Referenzfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibrierung und Anwendung des Erweiterungsachsen-Koordinatensystems
        DescPose pos = {/* Geben Sie hier Ihre Kalibrierungspunktkoordinaten ein */ };
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sie müssen diese Schnittstelle 4 Mal mit verschiedenen Punkten aufrufen, um die Achse zu kalibrieren */
        DescPose coord = {};
        robot.PositionorComputeECoordSys(coord); // Kalibrierungsergebnis berechnen
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); // Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden

        //6. Werkstückkoordinatensystem auf der Erweiterungsachse kalibrieren. Sie benötigen folgende Schnittstellen:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Startpunkt der synchronen Linearbewegung erfassen
        DescPose startdescPose = {/* Geben Sie hier Ihre Koordinaten ein */ };
        JointPos startjointPos = {/* Geben Sie hier Ihre Koordinaten ein */ };
        ExaxisPos startexaxisPos = {/* Geben Sie hier Ihre Startkoordinaten für die Erweiterungsachse ein */ };

        //8. Endpunkt der synchronen Linearbewegung erfassen
        DescPose enddescPose = {/* Geben Sie hier Ihre Koordinaten ein */ };
        JointPos endjointPos = {/* Geben Sie hier Ihre Koordinaten ein */ };
        ExaxisPos endexaxisPos = {/* Geben Sie hier Ihre Endkoordinaten für die Erweiterungsachse ein */ };

        //9. Synchronbewegungsprogramm erstellen
        // Zum Startpunkt bewegen, angenommen Werkzeug- und Werkstückkoordinatensystem sind beide 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = { 0, 0, 0, 0, 0, 0 };
        robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);

        // Synchronbewegung starten (mit Gelenkposition)
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);

        // Zum Startpunkt bewegen (Überladung ohne Zielpose)
        robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);

        // Synchronbewegung starten (Überladung ohne Gelenkposition)
        robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);

        robot.CloseRPC();
    }

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung
    * @param [in] joint_pos_p Gelenkposition des Zwischenpunkts, Einheit deg
    * @param [in] desc_pos_p  Kartesische Pose des Zwischenpunkts
    * @param [in] ptool  Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] puser  Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] pvel  Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100]
    * @param [in] pacc  Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_p  Erweiterachsenposition am Zwischenpunkt, Einheit mm
    * @param [in] poffset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zwischenpunkt
    * @param [in] offset_pos_p  Posenversatz für Zwischenpunkt
    * @param [in] joint_pos_t  Gelenkposition des Zielpunkts, Einheit deg
    * @param [in] desc_pos_t   Kartesische Pose des Zielpunkts
    * @param [in] ttool  Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tuser  Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tvel  Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100]
    * @param [in] tacc  Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_t  Erweiterachsenposition am Zielpunkt, Einheit mm
    * @param [in] toffset_flag  0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zielpunkt
    * @param [in] offset_pos_t  Posenversatz für Zielpunkt
    * @param [in] ovl  Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @return Fehlercode
    */
    errno_t ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung (automatische inverse Kinematik)
    * @param [in] desc_pos_p  Kartesische Pose des Zwischenpunkts
    * @param [in] ptool Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] puser Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14]
    * @param [in] pvel Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100]
    * @param [in] pacc Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_p Erweiterachsenposition am Zwischenpunkt, Einheit mm
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zwischenpunkt
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt
    * @param [in] desc_pos_t  Kartesische Pose des Zielpunkts
    * @param [in] ttool Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tuser Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14]
    * @param [in] tvel Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100]
    * @param [in] tacc Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100], vorerst nicht verfügbar
    * @param [in] epos_t Erweiterachsenposition am Zielpunkt, Einheit mm
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zielpunkt
    * @param [in] offset_pos_t Posenversatz für Zielpunkt
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen
    * @return Fehlercode
    */
    errno_t ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, uint8_t poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, uint8_t toffset_flag, DescPose offset_pos_t, float ovl, float blendR, int config = -1);

Codebeispiel für synchronisierte Kreisbogenbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveC()
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

        //1. Kalibrieren und Anwenden des Roboter-Werkzeugkoordinatensystems. Sie können die Vier-Punkt- oder Sechs-Punkt-Methode verwenden. Die relevanten Schnittstellen sind:
        //  int SetToolPoint(int point_num); // Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
        //  int ComputeTool(ref DescPose tcp_pose); // Werkzeugkoordinatensystem berechnen
        //  int SetTcp4RefPoint(int point_num);  // Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
        //  int ComputeTcp4(ref DescPose tcp_pose);  // Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
        //  int SetToolCoord(int id, DescPose coord, int type, int install); // Werkzeugkoordinatensystem einstellen und anwenden
        //  int SetToolList(int id, DescPose coord, int type, int install);  // Werkzeugkoordinatensystem in Liste einstellen und anwenden

        //2. UDP-Kommunikationsparameter einstellen und UDP-Kommunikation laden
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Parameter für Erweiterungsachsen einstellen, einschließlich Typ, Antriebsparameter, DH-Parameter
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Einachs-Positionierer und DH-Parameter
        robot.SetRobotPosToAxis(1); // Einbauposition der Erweiterungsachse
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Servoantriebsparameter, hier für Einachs-Positionierer. Bei mehreren Achsen müssen für jede Achse Parameter gesetzt werden.

        //4. Ausgewählte Achse aktivieren und Referenzfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibrierung und Anwendung des Erweiterungsachsen-Koordinatensystems
        DescPose pos = {/* Geben Sie hier Ihre Kalibrierungspunktkoordinaten ein */ };
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sie müssen diese Schnittstelle 4 Mal mit verschiedenen Punkten aufrufen, um die Achse zu kalibrieren */
        DescPose coord = {};
        robot.PositionorComputeECoordSys(coord); // Kalibrierungsergebnis berechnen
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); // Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden

        //6. Werkstückkoordinatensystem auf der Erweiterungsachse kalibrieren. Sie benötigen folgende Schnittstellen:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Startpunkt der synchronen Kreisbogenbewegung erfassen
        DescPose startdescPose = {/* Geben Sie hier Ihre Koordinaten ein */ };
        JointPos startjointPos = {/* Geben Sie hier Ihre Koordinaten ein */ };
        ExaxisPos startexaxisPos = {/* Geben Sie hier Ihre Startkoordinaten für die Erweiterungsachse ein */ };

        //8. Endpunkt der synchronen Kreisbogenbewegung erfassen
        DescPose enddescPose = {/* Geben Sie hier Ihre Koordinaten ein */ };
        JointPos endjointPos = {/* Geben Sie hier Ihre Koordinaten ein */ };
        ExaxisPos endexaxisPos = {/* Geben Sie hier Ihre Endkoordinaten für die Erweiterungsachse ein */ };

        //9. Zwischenpunkt der synchronen Kreisbogenbewegung erfassen
        DescPose middescPose = {/* Geben Sie hier Ihre Koordinaten ein */ };
        JointPos midjointPos = {/* Geben Sie hier Ihre Koordinaten ein */ };
        ExaxisPos midexaxisPos = {/* Geben Sie hier die Koordinaten der Erweiterungsachse am Kreisbogen-Zwischenpunkt ein */ };

        //10. Synchronbewegungsprogramm erstellen
        // Zum Startpunkt bewegen, angenommen Werkzeug- und Werkstückkoordinatensystem sind beide 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = { 0, 0, 0, 0, 0, 0 };
        robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);

        // Synchronbewegung starten (mit Gelenkpositionen für Zwischen- und Endpunkt)
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese,
                            endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);

        // Zum Startpunkt bewegen (Überladung ohne Zielpose)
        robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);

        // Synchronbewegung starten (Überladung ohne Gelenkpositionen)
        robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese,
                            enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);

        robot.CloseRPC();
    }

Erweiterungs-DO setzen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Setzt einen erweiterten digitalen Ausgang (AuxDO)
    * @param [in] DONum DO-Nummer
    * @param [in] bOpen Schalter true-ein; false-aus
    * @param [in] smooth Glättung (ob Befehl geglättet wird)
    * @param [in] block Blockierung (ob auf Abschluss gewartet wird)
    * @return Fehlercode
    */
    errno_t SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);

Erweiterungs-AO setzen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Setzt einen erweiterten analogen Ausgang (AuxAO)
    * @param [in] AONum AO-Nummer
    * @param [in] value Analogwert [0-4095]
    * @param [in] block Blockierung (ob auf Abschluss gewartet wird)
    * @return Fehlercode
    */
    errno_t SetAuxAO(int AONum, double value, bool block);

Filterzeit für erweiterten digitalen Eingang (AuxDI) einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Filterzeit für einen erweiterten digitalen Eingang (AuxDI) ein
    * @param [in] filterTime Filterzeit (ms)
    * @return Fehlercode
    */
    errno_t SetAuxDIFilterTime(int filterTime);

Filterzeit für erweiterten analogen Eingang (AuxAI) einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Filterzeit für einen erweiterten analogen Eingang (AuxAI) ein
    * @param [in] filterTime Filterzeit (ms)
    * @return Fehlercode
    */
    errno_t SetAuxAIFilterTime(int filterTime);

Auf erweiterten digitalen Eingang (AuxDI) warten
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Wartet auf einen erweiterten digitalen Eingang (AuxDI)
    * @param [in] DINum DI-Nummer
    * @param [in] bOpen Schalter 0-aus; 1-ein
    * @param [in] time Maximale Wartezeit (ms)
    * @param [in] errorAlarm Verhalten bei Zeitüberschreitung (false: Fehler, Bewegung stoppen; true: Warnung, Bewegung fortsetzen)
    * @return Fehlercode
    */
    errno_t WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);

Auf erweiterten analogen Eingang (AuxAI) warten
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Wartet auf einen erweiterten analogen Eingang (AuxAI)
    * @param [in] AINum AI-Nummer
    * @param [in] sign 0-größer als; 1-kleiner als
    * @param [in] value AI-Wert
    * @param [in] time Maximale Wartezeit (ms)
    * @param [in] errorAlarm Verhalten bei Zeitüberschreitung (false: Fehler, Bewegung stoppen; true: Warnung, Bewegung fortsetzen)
    * @return Fehlercode
    */
    errno_t WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);

Wert eines erweiterten digitalen Eingangs (AuxDI) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt den Wert eines erweiterten digitalen Eingangs (AuxDI) zurück
    * @param [in] DINum DI-Nummer
    * @param [in] isNoBlock Blockierung (false: blockierend; true: nicht blockierend)
    * @param [out] isOpen 0-aus; 1-ein
    * @return Fehlercode
    */
    errno_t GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);

Wert eines erweiterten analogen Eingangs (AuxAI) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt den Wert eines erweiterten analogen Eingangs (AuxAI) zurück
    * @param [in] AINum AI-Nummer
    * @param [in] isNoBlock Blockierung (false: blockierend; true: nicht blockierend)
    * @param [out] value Eingangswert
    * @return Fehlercode
    */
    errno_t GetAuxAI(int AINum, bool isNoBlock, int& value);

Codebeispiel für erweiterte I/Os (AuxIO)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAuxDOAO(void)
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
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, true, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, false, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 409; i++)
      {
        robot.SetAuxAO(0, i * 10, true);
        robot.SetAuxAO(1, 4095 - i * 10, true);
        robot.SetAuxAO(2, i * 10, true);
        robot.SetAuxAO(3, 4095 - i * 10, true);
        Sleep(10);
      }
      robot.SetAuxDIFilterTime(10);
      robot.SetAuxAIFilterTime(0, 10);
      for (int i = 0; i < 20; i++)
      {
        bool curValue = false;
        int rtn = robot.GetAuxDI(i, false, curValue);
        cout << "DI" << i << "  " << curValue << endl;
      }
      int curValue = -1;
      for (int i = 0; i < 4; i++)
      {
        rtn = robot.GetAuxAI(i, true, curValue);
      }
      robot.WaitAuxDI(1, false, 1000, false);
      robot.WaitAuxAI(1, 1, 132, 1000, false);
      robot.CloseRPC();
      return 0;
    }

Fahrbare Einheit aktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktiviert/Deaktiviert die fahrbare Einheit
    * @param enable false-deaktivieren; true-aktivieren
    * @return Fehlercode
    */
    errno_t TractorEnable(bool enable);

Referenzpunktfahrt der fahrbaren Einheit
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Führt die Referenzpunktfahrt der fahrbaren Einheit durch
    * @return Fehlercode
    */
    errno_t TractorHoming();

Linearbewegung der fahrbaren Einheit
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Linearbewegung der fahrbaren Einheit
    * @param distance Bewegungsstrecke (mm)
    * @param vel Geschwindigkeitsprozentsatz (0-100)
    * @return Fehlercode
    */
    errno_t TractorMoveL(double distance, double vel);

Kreisbogenbewegung der fahrbaren Einheit
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Kreisbogenbewegung der fahrbaren Einheit
    * @param radio Radius der Kreisbogenbewegung (mm)
    * @param angle Winkel der Kreisbogenbewegung (°)
    * @param vel Geschwindigkeitsprozentsatz (0-100)
    * @return Fehlercode
    */
    errno_t TractorMoveC(double radio, double angle, double vel);

Bewegung der fahrbaren Einheit stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stoppt die Bewegung der fahrbaren Einheit
    * @return Fehlercode
    */
    errno_t TractorStop();

Codebeispiel für fahrbare Einheit
+++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTractor(void)
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
      robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1);
      robot.ExtDevLoadUDPDriver();
      rtn = robot.ExtAxisServoOn(1, 1);
      rtn = robot.ExtAxisServoOn(2, 1);
      robot.Sleep(2000);
      robot.ExtAxisSetHoming(1, 0, 10, 2);
      robot.Sleep(2000);
      rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
      robot.Sleep(4000);
      robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
      robot.TractorEnable(false);
      robot.Sleep(2000);
      robot.TractorEnable(true);
      robot.Sleep(2000);
      robot.TractorHoming();
      robot.Sleep(2000);
      robot.TractorMoveL(100, 2);
      robot.Sleep(5000);
      robot.TractorStop();
      robot.TractorMoveL(-100, 20);
      robot.Sleep(5000);
      robot.TractorMoveC(300, 90, 20);
      robot.Sleep(10000);
      robot.TractorMoveC(300, -90, 20);
      robot.Sleep(1);
      robot.CloseRPC();
      return 0;
    }
