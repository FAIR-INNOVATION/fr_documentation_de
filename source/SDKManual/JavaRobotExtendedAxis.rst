Erweiterungsachsen
========================

.. toctree::
    :maxdepth: 5

Parameter für 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Parameter für eine 485-Erweiterungsachse ein.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [in] param Parameter der 485-Erweiterungsachse.
    * @return Fehlercode.
    */
    int AuxServoSetParam(int servoId, Axis485Param param);

Parameter der 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Konfigurationsparameter einer 485-Erweiterungsachse zurück.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [out] param Parameter der 485-Erweiterungsachse.
    * @return Fehlercode.
    */
    int AuxServoGetParam(int servoId, Axis485Param param);

Aktivierung/Deaktivierung der 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Aktivierung/Deaktivierung der 485-Erweiterungsachse ein.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [in] status Aktivierungsstatus, 0-deaktivieren, 1-aktivieren.
    * @return Fehlercode.
    */
    int AuxServoEnable(int servoId, int status);

Steuerungsmodus der 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt den Steuerungsmodus der 485-Erweiterungsachse ein.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [in] mode Steuerungsmodus, 0-Positionsmodus, 1-Geschwindigkeitsmodus.
    * @return Fehlercode.
    */
    int AuxServoSetControlMode(int servoId, int mode);

Zielposition der 485-Erweiterungsachse einstellen (Positionsmodus)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Zielposition der 485-Erweiterungsachse ein (Positionsmodus).
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [in] pos Zielposition, mm oder °.
    * @param [in] speed Zielgeschwindigkeit, mm/s oder °/s.
    * @param [in] acc Beschleunigungsprozentsatz [0-100].
    * @return Fehlercode.
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed, double acc);

Zieldrehmoment der 485-Erweiterungsachse einstellen (Drehmomentmodus) - noch nicht freigegeben
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt das Zieldrehmoment der 485-Erweiterungsachse ein (Drehmomentmodus) - noch nicht freigegeben.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [in] torque Zieldrehmoment, Nm.
    * @return Fehlercode.
    */
    int AuxServoSetTargetTorque(int servoId, double torque);

Referenzpunktfahrt der 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Referenzpunktfahrt der 485-Erweiterungsachse ein.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [in] mode Referenzpunktfahrt-Modus, 1-aktuelle Position als Nullpunkt; 2-negative Endlage als Nullpunkt; 3-positive Endlage als Nullpunkt.
    * @param [in] searchVel Suchgeschwindigkeit, mm/s oder °/s.
    * @param [in] latchVel Einrastgeschwindigkeit, mm/s oder °/s.
    * @param [in] acc Beschleunigungsprozentsatz [0-100].
    * @return Fehlercode.
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel, double acc);

Fehlerinformationen der 485-Erweiterungsachse löschen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Löscht Fehlerinformationen der 485-Erweiterungsachse.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @return Fehlercode.
    */
    int AuxServoClearError(int servoId);

Servostatus der 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Servostatus der 485-Erweiterungsachse zurück.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [out] servoErrCode Fehlercode des Servoantriebs.
    * @param [out] servoState Status des Servoantriebs. Bit0: 0-nicht aktiviert; 1-aktiviert. Bit1: 0-nicht in Bewegung; 1-in Bewegung. Bit4: 0-Positionierung nicht abgeschlossen; 1-Positionierung abgeschlossen. Bit5: 0-Referenzpunktfahrt nicht abgeschlossen; 1-Referenzpunktfahrt abgeschlossen.
    * @param [out] servoPos Aktuelle Position des Servos mm oder °.
    * @param [out] servoSpeed Aktuelle Geschwindigkeit des Servos mm/s oder °/s.
    * @param [out] servoTorque Aktuelles Drehmoment des Servos Nm.
    * @return Fehlercode.
    */
    int AuxServoGetStatus(int servoId, int[] servoErrCode, int[] servoState, double[] servoPos, double[] servoSpeed, double[] servoTorque);

Zielgeschwindigkeit der 485-Erweiterungsachse einstellen (Geschwindigkeitsmodus)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Zielgeschwindigkeit der 485-Erweiterungsachse ein (Geschwindigkeitsmodus).
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @param [in] speed Zielgeschwindigkeit, mm/s oder °/s.
    * @param [in] acc Beschleunigungsprozentsatz [0-100].
    * @return Fehlercode.
    */
    int AuxServoSetTargetSpeed(int servoId, double speed, double acc);

Achsnummer der 485-Erweiterungsachse in der Statusrückmeldung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Achsnummer der 485-Erweiterungsachse in der Statusrückmeldung ein.
    * @param [in] servoId Servoantriebs-ID, Bereich [1-16], entspricht der Slave-ID.
    * @return Fehlercode.
    */
    int AuxServosetStatusID(int servoId);

Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse ein.
    * @param [in] acc Bewegungsbeschleunigung der 485-Erweiterungsachse.
    * @param [in] dec Bewegungsverzögerung der 485-Erweiterungsachse.
    * @return Fehlercode.
    */
    int AuxServoSetAcc(double acc, double dec);

Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse ein.
    * @param [in] acc Not-Halt-Beschleunigung der 485-Erweiterungsachse.
    * @param [in] dec Not-Halt-Verzögerung der 485-Erweiterungsachse.
    * @return Fehlercode.
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec);

Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Bewegungsbeschleunigung und -verzögerung der 485-Erweiterungsachse zurück.
    * @return List[0]: Fehlercode; List[1]: Bewegungsbeschleunigung der 485-Erweiterungsachse; List[2]: Bewegungsverzögerung der 485-Erweiterungsachse.
    */
    List<Number> AuxServoGetAcc();

Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Not-Halt-Beschleunigung und -Verzögerung der 485-Erweiterungsachse zurück.
    * @return List[0]: Fehlercode; List[1]: Not-Halt-Beschleunigung der 485-Erweiterungsachse; List[2]: Not-Halt-Verzögerung der 485-Erweiterungsachse.
    */
    List<Number> AuxServoGetEmergencyStopAcc();

Codebeispiel zur Steuerung einer Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int Test485Auxservo(Robot robot)
    {
        Axis485Param ax=new Axis485Param(1, 1, 1, 131072, 15.45);
        int retval = robot.AuxServoSetParam(1, ax);

        Axis485Param ax2=new Axis485Param();
        retval = robot.AuxServoGetParam(1, ax2);

        ax.servoCompany=10;
        ax.servoModel=11;
        ax.servoSoftVersion=12;
        ax.servoResolution=13;
        ax.axisMechTransRatio=14;

        retval = robot.AuxServoSetParam(1, ax);

        retval = robot.AuxServoGetParam(1,ax2);

        ax.servoCompany=1;
        ax.servoModel=1;
        ax.servoSoftVersion=1;
        ax.servoResolution=131072;
        ax.axisMechTransRatio=36;

        retval = robot.AuxServoSetParam(1, ax);
        robot.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        robot.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;

        List<Number> aux=new ArrayList<>();

        aux=robot.AuxServoGetEmergencyStopAcc();
        aux=robot.AuxServoGetAcc();

        robot.AuxServoSetControlMode(1, 0);
        robot.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        robot.Sleep(1000);
        int[] servoerrcode =new int[]{0};
        int[] servoErrCode=new int[]{0};
        int[] servoState=new int[]{0};
        double[] servoPos=new double[]{0};
        double[] servoSpeed=new double[]{0};
        double[] servoTorque=new double[]{0};
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);

        retval = robot.AuxServoEnable(1, 1);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1,100);
        robot.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30,100);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
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
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert die UDP-Kommunikationsparameter für die Erweiterungsachse.
    * @param [in] param Kommunikationsparameter.
    * @return Fehlercode.
    */
    int ExtDevSetUDPComParam(UDPComParam param);

UDP-Kommunikationsparameter für Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Abrufen der UDP-Kommunikationsparameter für Erweiterungsachsen
    * @param [out] ip PLC-IP-Adresse
    * @param [out] port Portnummer
    * @param [out] period Kommunikationszyklus (ms, Standard ist 2, diesen Parameter nicht ändern)
    * @param [out] lossPkgTime Paketverlust-Erkennungszeit (ms)
    * @param [out] lossPkgNum Anzahl der Paketverluste
    * @param [out] disconnectTime Bestätigungsdauer für Kommunikationsunterbrechung
    * @param [out] reconnectEnable Automatische Wiederverbindung bei Kommunikationsunterbrechung aktivieren 0-deaktiviert 1-aktiviert
    * @param [out] reconnectPeriod Wiederverbindungsintervall (ms)
    * @param [out] reconnectNum Anzahl der Wiederverbindungsversuche
    * @param [out] selfConnect Automatische Wiederverbindung nach Neustart des Steuerkastens; 0-keine Wiederverbindung; 1-Wiederverbindung
    * @return Fehlercode
    */
    public int ExtDevGetUDPComParam(ref string ip, ref int port, ref int period, ref int lossPkgTime, ref int lossPkgNum, ref int disconnectTime, ref int reconnectEnable, ref int reconnectPeriod, ref int reconnectNum, ref int selfConnect)

UDP-Kommunikation laden
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Lädt die UDP-Kommunikation.
    * @return Fehlercode.
    */
    int ExtDevLoadUDPDriver();

UDP-Kommunikation entladen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Entlädt die UDP-Kommunikation.
    * @return Fehlercode.
    */
    int ExtDevUnloadUDPDriver();

Verbindung nach abnormaler UDP-Kommunikationsunterbrechung wiederherstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Verbindung nach einer abnormalen UDP-Kommunikationsunterbrechung wieder her.
    * @return Fehlercode.
    */
    int ExtDevUDPClientComReset();

Kommunikation nach abnormaler UDP-Kommunikationsunterbrechung schließen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schließt die Kommunikation nach einer abnormalen UDP-Kommunikationsunterbrechung.
    * @return Fehlercode.
    */
    int ExtDevUDPClientComClose();

Parameter für UDP-Erweiterungsachse konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert die Parameter einer UDP-Erweiterungsachse.
    * @param [in] axisID Achsnummer.
    * @param [in] axisType Erweiterungsachsentyp 0-Translation; 1-Rotation.
    * @param [in] axisDirection Richtung der Erweiterungsachse 0-positive Richtung; 1-negative Richtung.
    * @param [in] axisMax Maximale Position der Achse mm.
    * @param [in] axisMin Minimale Position der Achse mm.
    * @param [in] axisVel Geschwindigkeit mm/s.
    * @param [in] axisAcc Beschleunigung mm/s².
    * @param [in] axisLead Spindelsteigung mm.
    * @param [in] encResolution Encoderauflösung.
    * @param [in] axisOffect Versatz des Schweißnahtstartpunkts zur Erweiterungsachse.
    * @param [in] axisCompany Antriebshersteller 1-Hechuan; 2-Inovance; 3-Panasonic.
    * @param [in] axisModel Antriebsmodell 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG.
    * @param [in] axisEncType Encodertyp 0-inkremental; 1-absolut.
    * @return Fehlercode.
    */
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, int encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Einbauposition der Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Einbauposition der Erweiterungsachse ein.
    * @param [in] installType 0-Roboter auf der externen Achse montiert, 1-Roboter außerhalb der externen Achse montiert.
    * @return Fehlercode.
    */
    int SetRobotPosToAxis(int installType);

DH-Parameter des Erweiterungsachsensystems einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die DH-Parameter des Erweiterungsachsensystems ein.
    * @param [in] axisConfig Konfiguration der externen Achse, 0-Linearführung mit einem Freiheitsgrad, 1-L-förmiger Positionierer mit zwei Freiheitsgraden, 2-drei Freiheitsgrade, 3-vier Freiheitsgrade, 4-Positionierer mit einem Freiheitsgrad.
    * @param [in] axisDHd1 DH-Parameter d1 der externen Achse mm.
    * @param [in] axisDHd2 DH-Parameter d2 der externen Achse mm.
    * @param [in] axisDHd3 DH-Parameter d3 der externen Achse mm.
    * @param [in] axisDHd4 DH-Parameter d4 der externen Achse mm.
    * @param [in] axisDHa1 DH-Parameter a1 der externen Achse mm.
    * @param [in] axisDHa2 DH-Parameter a2 der externen Achse mm.
    * @param [in] axisDHa3 DH-Parameter a3 der externen Achse mm.
    * @param [in] axisDHa4 DH-Parameter a4 der externen Achse mm.
    * @return Fehlercode.
    */
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

UDP-Erweiterungsachse aktivieren
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Aktiviert/Deaktiviert die UDP-Erweiterungsachse.
    * @param [in] axisID Achsnummer [1-4].
    * @param [in] status 0-deaktivieren; 1-aktivieren.
    * @return Fehlercode.
    */
    int ExtAxisServoOn(int axisID, int status);

Referenzpunktfahrt der UDP-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Referenzpunktfahrt der UDP-Erweiterungsachse ein.
    * @param [in] axisID Achsnummer [1-4].
    * @param [in] mode Referenzpunktfahrt-Modus 0-aktuelle Position als Nullpunkt, 1-negative Endlage als Nullpunkt, 2-positive Endlage als Nullpunkt.
    * @param [in] searchVel Suchgeschwindigkeit (mm/s).
    * @param [in] latchVel Einrastgeschwindigkeit (mm/s).
    * @return Fehlercode.
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Tippbetrieb (Jog) der UDP-Erweiterungsachse starten
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet den Tippbetrieb (Jog) der UDP-Erweiterungsachse.
    * @param [in] axisID Achsnummer [1-4].
    * @param [in] direction Drehrichtung 0-negativ; 1-positiv.
    * @param [in] vel Geschwindigkeit (mm/s).
    * @param [in] acc Beschleunigung (mm/s²).
    * @param [in] maxDistance Maximale Tippdistanz.
    * @return Fehlercode.
    */
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);

Tippbetrieb (Jog) der UDP-Erweiterungsachse stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stoppt den Tippbetrieb (Jog) der UDP-Erweiterungsachse.
    * @param [in] axisID Achsnummer [1-4].
    * @return Fehlercode.
    */
    int ExtAxisStopJog(int axisID);

Codebeispiel für Konfiguration und Tippbetrieb einer UDP-Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public static int TestUDPAxis(Robot robot)//UDP
    {
        UDPComParam para1=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        int rtn = robot.ExtDevSetUDPComParam(para1);
        String ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        UDPComParam para2=new UDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum,0);
        rtn = robot.ExtDevGetUDPComParam(para2);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);
        robot.Sleep(3000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.Sleep(3000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);

        robot.Sleep(4000);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        robot.Sleep(4000);
        robot.ExtAxisStopJog(1);
        robot.Sleep(4000);
        robot.ExtAxisServoOn(1, 0);

        robot.Sleep(4000);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        robot.Sleep(4000);
        robot.ExtAxisStopJog(2);
        robot.Sleep(4000);
        robot.ExtAxisServoOn(2, 0);
        robot.Sleep(4000);
        robot.ExtDevUnloadUDPDriver();

        return 0;
    }

Referenzpunkte für das Erweiterungsachsen-Koordinatensystem einstellen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt Referenzpunkte für das Erweiterungsachsen-Koordinatensystem ein - Vier-Punkt-Methode.
    * @param [in] pointNum Punktnummer [1-4].
    * @return Fehlercode.
    */
    int ExtAxisSetRefPoint(int pointNum);

Erweiterungsachsen-Koordinatensystem berechnen - Vier-Punkt-Methode
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Berechnet das Erweiterungsachsen-Koordinatensystem - Vier-Punkt-Methode.
    * @param [out] coord Koordinatenwerte.
    * @return Fehlercode.
    */
    int ExtAxisComputeECoordSys(DescPose coord);

Referenzpunkte für das Positionierer-Koordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt Referenzpunkte für das Positionierer-Koordinatensystem ein.
    * @param [in] pointNum Punktnummer [1-4].
    * @return Fehlercode.
    */
    int PositionorSetRefPoint(int pointNum);

Positionierer-Koordinatensystem berechnen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Berechnet das Positionierer-Koordinatensystem - Vier-Punkt-Methode.
    * @param [out] coord Koordinatenwerte.
    * @return Fehlercode.
    */
    int PositionorComputeECoordSys(DescPose coord);

Pose des Kalibrierreferenzpunkts im Positionierer-Endkoordinatensystem einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Pose des Kalibrierreferenzpunkts im Positionierer-Endkoordinatensystem ein.
    * @param [in] pos Posenwert.
    * @return Fehlercode.
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Erweiterungsachsen-Koordinatensystem anwenden
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wendet das Erweiterungsachsen-Koordinatensystem an.
    * @param [in] applyAxisId Erweiterungsachsennummern als Bitmaske, Bit0-Bit3 entsprechen den Achsnummern 1-4. z.B. Achsen 1 und 3 anwenden: 0b 0000 0101 = 5.
    * @param [in] axisCoordNum Nummer des Erweiterungsachsen-Koordinatensystems.
    * @param [in] coord Koordinatenwerte.
    * @param [in] calibFlag Kalibrierungsflag 0-nein, 1-ja.
    * @return Fehlercode.
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Erweiterungsachsen-Koordinatensystem abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Gibt das Erweiterungsachsen-Koordinatensystem zurück.
    * @param [out] coord Erweiterungsachsen-Koordinatensystem.
    * @return Fehlercode.
    */
    int ExtAxisGetCoord(DescPose coord);

Codebeispiel für die Kalibrierung des Erweiterungsachsen-Koordinatensystems
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public static int TestUDPAxisCalib(Robot robot)
    {
        UDPComParam para1=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);

        int rtn = robot.ExtDevSetUDPComParam(para1);
        String ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        UDPComParam para2=new UDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum,0);

        rtn = robot.ExtDevGetUDPComParam(para2);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);
        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4,  0, 0, 0, 0, 0, 0);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);

        DescPose toolCoord=new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe=new JointPos(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
        JointPos j1=new JointPos(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
        JointPos j2=new JointPos(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
        JointPos j3=new JointPos(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
        JointPos j4=new JointPos(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);

        DescPose descSafe =new DescPose(0,0,0,0,0,0);
        DescPose desc1 = new DescPose(0,0,0,0,0,0);
        DescPose desc2 = new DescPose(0,0,0,0,0,0);
        DescPose desc3 = new DescPose(0,0,0,0,0,0);
        DescPose desc4 = new DescPose(0,0,0,0,0,0);
        ExaxisPos exaxisPos =new ExaxisPos(0,0,0,0);
        DescPose offdese =new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin(jSafe, descSafe);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        robot.GetForwardKin(j1, desc1);
        robot.MoveJ(j1, desc1, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        DescPose actualTCPPos =new DescPose(0,0,0,0,0,0);

        robot.GetActualTCPPose(actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j2, desc2);
        rtn = robot.MoveJ(j2, desc2, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(2);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j3, desc3);
        robot.MoveJ(j3, desc3, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(3);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j4, desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        robot.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);

        robot.CloseRPC();
        return 0;
    }

UDP-Erweiterungsachsen-Bewegung
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.7-3.8.4

.. code-block:: java
    :linenos:

    /**
    * @brief Bewegung der UDP-Erweiterungsachse.
    * @param [in] pos Zielposition.
    * @param [in] ovl Geschwindigkeitsprozentsatz.
    * @param [in] blend Glättungsparameter (mm oder ms).
    * @return Fehlercode.
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend);

UDP-Erweiterungsachsen-Bewegung - Codebeispiel
++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public static int TestUDPAxisCalib(Robot robot)
    {
        ExaxisPos exaxisPos = new ExaxisPos( 20, 0, 0, 0 );
        robot.ExtAxisMove(exaxisPos,40);
        robot.CloseRPC();
        return 0;
    }

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung.
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg.
    * @param [in] desc_pos Ziel-Kartesische Pose.
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14].
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14].
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100].
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] epos Position der Erweiterungsachse, Einheit mm.
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit ms.
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem.
    * @param [in] offset_pos Posenversatz.
    * @return Fehlercode.
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung (automatische Vorwärtskinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Gelenkbewegung (automatische Vorwärtskinematik).
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg.
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14].
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14].
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100].
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] epos Position der Erweiterungsachse, Einheit mm.
    * @param [in] blendT [-1.0]-Bewegung abschließen (blockierend), [0~500.0]-Glättungszeit (nicht blockierend), Einheit ms.
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem.
    * @param [in] offset_pos Posenversatz.
    * @return Fehlercode.
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Codebeispiel für synchronisierte Gelenkbewegung
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public int testSyncMoveJ(Robot robot)
    {
        //1. Kalibrieren und Anwenden des Roboter-Werkzeugkoordinatensystems. Sie können die Vier-Punkt- oder Sechs-Punkt-Methode verwenden. Die relevanten Schnittstellen sind:
        //  int SetToolPoint(int point_num); // Werkzeug-Referenzpunkt einstellen - Sechs-Punkt-Methode
        //  int ComputeTool(ref DescPose tcp_pose); // Werkzeugkoordinatensystem berechnen
        //  int SetTcp4RefPoint(int point_num);  // Werkzeug-Referenzpunkt einstellen - Vier-Punkt-Methode
        //  int ComputeTcp4(ref DescPose tcp_pose);  // Werkzeugkoordinatensystem berechnen - Vier-Punkt-Methode
        //  int SetToolCoord(int id, DescPose coord, int type, int install); // Werkzeugkoordinatensystem einstellen und anwenden
        //  int SetToolList(int id, DescPose coord, int type, int install);  // Werkzeugkoordinatensystem in Liste einstellen und anwenden
        //2. UDP-Kommunikationsparameter einstellen und UDP-Kommunikation laden
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10, 0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3. Parameter für Erweiterungsachsen einstellen, einschließlich Typ, Antriebsparameter, DH-Parameter
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Einachs-Positionierer und DH-Parameter
        robot.SetRobotPosToAxis(1); // Einbauposition der Erweiterungsachse
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Servoantriebsparameter, hier für Einachs-Positionierer. Bei mehreren Achsen müssen für jede Achse Parameter gesetzt werden.
        //4. Ausgewählte Achse aktivieren und Referenzfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5. Kalibrierung und Anwendung des Erweiterungsachsen-Koordinatensystems
        DescPose pos = new DescPose(/* Geben Sie hier Ihre Kalibrierungspunktkoordinaten ein */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sie müssen diese Schnittstelle 4 Mal mit verschiedenen Punkten aufrufen, um die Achse zu kalibrieren */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); // Kalibrierungsergebnis berechnen
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); // Kalibrierungsergebnis auf das Erweiterungsachsen-Koordinatensystem anwenden
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
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        // Synchronbewegung starten
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        // Zum Startpunkt bewegen (Überladung ohne Zielpose)
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        // Synchronbewegung starten (Überladung ohne Zielpose)
        robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        robot.CloseRPC();
        return 0;
    }

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung.
    * @param [in] joint_pos Ziel-Gelenkposition, Einheit deg.
    * @param [in] desc_pos Ziel-Kartesische Pose.
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14].
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14].
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100].
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm.
    * @param [in] epos Position der Erweiterungsachse, Einheit mm.
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem.
    * @param [in] offset_pos Posenversatz.
    * @return Fehlercode.
    */
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Linearbewegung (automatische inverse Kinematik).
    * @param [in] desc_pos Ziel-Kartesische Pose.
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14].
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14].
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100].
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm.
    * @param [in] epos Position der Erweiterungsachse, Einheit mm.
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem.
    * @param [in] offset_pos Posenversatz.
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen.
    * @return Fehlercode.
    */
    int ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos, int config);

Codebeispiel für synchronisierte Linearbewegung
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public int testSyncMoveL(Robot robot)
    {
        // 1. Werkzeugkoordinatensystem kalibrieren und anwenden...
        // 2. UDP-Kommunikationsparameter setzen und laden
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10, 0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        // 3. Erweiterachsenparameter setzen
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0);
        robot.SetRobotPosToAxis(1);
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0);
        // 4. Achse aktivieren und Referenzpunktfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        // 5. Erweiterachsen-Koordinatensystem kalibrieren und anwenden
        DescPose pos = new DescPose(/* Ihre Koordinaten */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1);
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord);
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);
        // 6. Werkstückkoordinatensystem auf der Erweiterachse kalibrieren
        // ...
        // 7. Startpunkt der synchronen Linearbewegung aufzeichnen
        DescPose startdescPose = new DescPose(/* Ihre Koordinaten */);
        JointPos startjointPos = new JointPos(/* Ihre Koordinaten */);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Ihre Koordinaten */);
        // 8. Endpunkt der synchronen Linearbewegung aufzeichnen
        DescPose enddescPose = new DescPose(/* Ihre Koordinaten */);
        JointPos endjointPos = new JointPos(/* Ihre Koordinaten */);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Ihre Koordinaten */);
        // 9. Synchrones Bewegungsprogramm schreiben
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese, -1);
        robot.CloseRPC();
        return 0;
    }

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung.
    * @param [in] joint_pos_p Gelenkposition des Zwischenpunkts, Einheit deg.
    * @param [in] desc_pos_p Kartesische Pose des Zwischenpunkts.
    * @param [in] ptool Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14].
    * @param [in] puser Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14].
    * @param [in] pvel Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100].
    * @param [in] pacc Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt, Einheit mm.
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zwischenpunkt.
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt.
    * @param [in] joint_pos_t Gelenkposition des Zielpunkts, Einheit deg.
    * @param [in] desc_pos_t Kartesische Pose des Zielpunkts.
    * @param [in] ttool Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14].
    * @param [in] tuser Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14].
    * @param [in] tvel Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100].
    * @param [in] tacc Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt, Einheit mm.
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zielpunkt.
    * @param [in] offset_pos_t Posenversatz für Zielpunkt.
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm.
    * @return Fehlercode.
    */
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR);

Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung (automatische inverse Kinematik)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: java
    :linenos:

    /**
    * @brief Synchronisierte Bewegung: UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung (automatische inverse Kinematik).
    * @param [in] desc_pos_p Kartesische Pose des Zwischenpunkts.
    * @param [in] ptool Werkzeugkoordinatennummer für Zwischenpunkt, Bereich [0~14].
    * @param [in] puser Werkstückkoordinatennummer für Zwischenpunkt, Bereich [0~14].
    * @param [in] pvel Geschwindigkeitsprozentsatz für Zwischenpunkt, Bereich [0~100].
    * @param [in] pacc Beschleunigungsprozentsatz für Zwischenpunkt, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] epos_p Position der Erweiterungsachse am Zwischenpunkt, Einheit mm.
    * @param [in] poffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zwischenpunkt.
    * @param [in] offset_pos_p Posenversatz für Zwischenpunkt.
    * @param [in] desc_pos_t Kartesische Pose des Zielpunkts.
    * @param [in] ttool Werkzeugkoordinatennummer für Zielpunkt, Bereich [0~14].
    * @param [in] tuser Werkstückkoordinatennummer für Zielpunkt, Bereich [0~14].
    * @param [in] tvel Geschwindigkeitsprozentsatz für Zielpunkt, Bereich [0~100].
    * @param [in] tacc Beschleunigungsprozentsatz für Zielpunkt, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] epos_t Position der Erweiterungsachse am Zielpunkt, Einheit mm.
    * @param [in] toffset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem für Zielpunkt.
    * @param [in] offset_pos_t Posenversatz für Zielpunkt.
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm.
    * @param [in] config Konfiguration des inversen Gelenkraums, [-1]-basierend auf aktueller Gelenkposition berechnen, [0~7]-basierend auf spezifischer Konfiguration lösen.
    * @return Fehlercode.
    */
    int ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config);

Codebeispiel für synchronisierte Kreisbogenbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public int testSyncMoveC(Robot robot)
    {
        // 1. Werkzeugkoordinatensystem kalibrieren und anwenden...
        // 2. UDP-Kommunikationsparameter setzen und laden
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10, 0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        // 3. Erweiterachsenparameter setzen
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0);
        robot.SetRobotPosToAxis(1);
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0);
        // 4. Achse aktivieren und Referenzpunktfahrt durchführen
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        // 5. Erweiterachsen-Koordinatensystem kalibrieren und anwenden
        DescPose pos = new DescPose(/* Ihre Koordinaten */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1);
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord);
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);
        // 6. Werkstückkoordinatensystem auf der Erweiterachse kalibrieren
        // ...
        // 7. Startpunkt der synchronen Kreisbogenbewegung aufzeichnen
        DescPose startdescPose = new DescPose(/* Ihre Koordinaten */);
        JointPos startjointPos = new JointPos(/* Ihre Koordinaten */);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Ihre Koordinaten */);
        // 8. Endpunkt der synchronen Kreisbogenbewegung aufzeichnen
        DescPose enddescPose = new DescPose(/* Ihre Koordinaten */);
        JointPos endjointPos = new JointPos(/* Ihre Koordinaten */);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Ihre Koordinaten */);
        // 9. Zwischenpunkt der synchronen Kreisbogenbewegung aufzeichnen
        DescPose middescPose = new DescPose(/* Ihre Koordinaten */);
        JointPos midjointPos = new JointPos(/* Ihre Koordinaten */);
        ExaxisPos midexaxisPos = new ExaxisPos(/* Ihre Koordinaten */);
        // 10. Synchrones Bewegungsprogramm schreiben
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0, -1);
        robot.CloseRPC();
        return 0;
    }

Erweiterungs-DO setzen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Setzt einen erweiterten digitalen Ausgang (AuxDO).
    * @param [in] DONum DO-Nummer.
    * @param [in] bOpen Schalter true-ein; false-aus.
    * @param [in] smooth Glättung (ob Befehl geglättet wird).
    * @param [in] block Blockierung (ob auf Abschluss gewartet wird).
    * @return Fehlercode.
    */
    int SetAuxDO(int DONum, boolean bOpen, boolean smooth, boolean block);

Erweiterungs-AO setzen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Setzt einen erweiterten analogen Ausgang (AuxAO).
    * @param [in] AONum AO-Nummer.
    * @param [in] value Analogwert [0-4095].
    * @param [in] block Blockierung (ob auf Abschluss gewartet wird).
    * @return Fehlercode.
    */
    int SetAuxAO(int AONum, double value, boolean block);

Filterzeit für erweiterten digitalen Eingang (AuxDI) einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Filterzeit für einen erweiterten digitalen Eingang (AuxDI) ein.
    * @param [in] filterTime Filterzeit (ms).
    * @return Fehlercode.
    */
    int SetAuxDIFilterTime(int filterTime);

Filterzeit für erweiterten analogen Eingang (AuxAI) einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Filterzeit für einen erweiterten analogen Eingang (AuxAI) ein.
    * @param [in] AONum AO-Nummer.
    * @param [in] filterTime Filterzeit (ms).
    * @return Fehlercode.
    */
    int SetAuxAIFilterTime(int AONum, int filterTime);

Auf erweiterten digitalen Eingang (AuxDI) warten
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen erweiterten digitalen Eingang (AuxDI).
    * @param [in] DINum DI-Nummer.
    * @param [in] bOpen Schalter 0-aus; 1-ein.
    * @param [in] time Maximale Wartezeit (ms).
    * @param [in] errorAlarm Verhalten bei Zeitüberschreitung (false: Fehler, Bewegung stoppen; true: Warnung, Bewegung fortsetzen).
    * @return Fehlercode.
    */
    int WaitAuxDI(int DINum, boolean bOpen, int time, boolean errorAlarm);

Auf erweiterten analogen Eingang (AuxAI) warten
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf einen erweiterten analogen Eingang (AuxAI).
    * @param [in] AINum AI-Nummer.
    * @param [in] sign 0-größer als; 1-kleiner als.
    * @param [in] value AI-Wert.
    * @param [in] time Maximale Wartezeit (ms).
    * @param [in] errorAlarm Verhalten bei Zeitüberschreitung (false: Fehler, Bewegung stoppen; true: Warnung, Bewegung fortsetzen).
    * @return Fehlercode.
    */
    int WaitAuxAI(int AINum, int sign, int value, int time, boolean errorAlarm);

Wert eines erweiterten digitalen Eingangs (AuxDI) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Wert eines erweiterten digitalen Eingangs (AuxDI) zurück.
    * @param [in] DINum DI-Nummer.
    * @param [in] isNoBlock Blockierung (false: blockierend; true: nicht blockierend).
    * @return List[0]: Fehlercode; List[1]: isOpen 0-aus; 1-ein.
    */
    List<Integer> GetAuxDI(int DINum, boolean isNoBlock);

Wert eines erweiterten analogen Eingangs (AuxAI) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt den Wert eines erweiterten analogen Eingangs (AuxAI) zurück.
    * @param [in] AINum AI-Nummer.
    * @param [in] isNoBlock Blockierung (false: blockierend; true: nicht blockierend).
    * @return List[0]: Fehlercode; List[1]: value Eingangswert.
    */
    List<Integer> GetAuxAI(int AINum, boolean isNoBlock);

Codebeispiel für erweiterte I/Os (AuxIO)
+++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public static int TestAuxDOAO(Robot robot)
    {
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            robot.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            robot.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            robot.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);

        List<Integer> liter = new ArrayList<>();
        for (int i = 0; i < 4; i++)
        {
            liter = robot.GetAuxAI(i, true);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);

        robot.CloseRPC();
        return 0;
    }

Fahrbare Einheit aktivieren
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Aktiviert/Deaktiviert die fahrbare Einheit.
    * @param [in] enable false-deaktivieren; true-aktivieren.
    * @return Fehlercode.
    */
    int TractorEnable(Boolean enable);

Referenzpunktfahrt der fahrbaren Einheit
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Führt die Referenzpunktfahrt der fahrbaren Einheit durch.
    * @return Fehlercode.
    */
    int TractorHoming();

Linearbewegung der fahrbaren Einheit
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Linearbewegung der fahrbaren Einheit.
    * @param [in] distance Bewegungsstrecke (mm).
    * @param [in] vel Geschwindigkeitsprozentsatz (0-100).
    * @return Fehlercode.
    */
    int TractorMoveL(double distance, double vel);

Kreisbogenbewegung der fahrbaren Einheit
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Kreisbogenbewegung der fahrbaren Einheit.
    * @param [in] radius Radius der Kreisbogenbewegung (mm).
    * @param [in] angle Winkel der Kreisbogenbewegung (°).
    * @param [in] vel Geschwindigkeitsprozentsatz (0-100).
    * @return Fehlercode.
    */
    int TractorMoveC(double radius, double angle, double vel);

Bewegung der fahrbaren Einheit stoppen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stoppt die Bewegung der fahrbaren Einheit.
    * @return Fehlercode.
    */
    int TractorStop();

Codebeispiel für fahrbare Einheit
+++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("RPC-Verbindung erfolgreich");
        }
        else
        {
            System.out.println("RPC-Verbindung fehlgeschlagen");
            return ;
        }
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);

        robot.TractorEnable(false);
        robot.Sleep(2000);
        robot.TractorEnable(true);
        robot.Sleep(2000);
        robot.TractorHoming();

        robot.Sleep(2000);
        robot.TractorMoveL(100, 20);
        robot.Sleep(5000);
        robot.TractorMoveL(-100, 20);
        robot.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        robot.Sleep(2000);
        robot.TractorStop(); // Fahrbare Einheit stoppen
        robot.TractorMoveC(300, -90, 20);
    }

Einstellung der Positionierungsabschlusszeit für UDP-Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Einstellung der Positionierungsabschlusszeit für UDP-Erweiterungsachsen
    * @param time Positionierungsabschlusszeit [ms]
    * @return Fehlercode
    */
    public int SetExAxisCmdDoneTime(double time)