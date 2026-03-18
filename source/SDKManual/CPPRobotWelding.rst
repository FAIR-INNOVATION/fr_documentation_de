Robotersystem - Schweißen
======================================

.. toctree::
    :maxdepth: 5

Parameter der Schweißprozesskurve einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Stellt die Parameter der Schweißprozesskurve ein.
     * @param [in] id Schweißprozessnummer (1-99).
     * @param [in] startCurrent Lichtbogenzündstrom (A).
     * @param [in] startVoltage Lichtbogenzündspannung (V).
     * @param [in] startTime Lichtbogenzündzeit (ms).
     * @param [in] weldCurrent Schweißstrom (A).
     * @param [in] weldVoltage Schweißspannung (V).
     * @param [in] endCurrent Lichtbogenendstrom (A).
     * @param [in] endVoltage Lichtbogenendspannung (V).
     * @param [in] endTime Lichtbogenendzeit (ms).
     * @return Fehlercode.
     */
    errno_t WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Parameter der Schweißprozesskurve abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die Parameter der Schweißprozesskurve zurück.
     * @param [in] id Schweißprozessnummer (1-99).
     * @param [out] startCurrent Lichtbogenzündstrom (A).
     * @param [out] startVoltage Lichtbogenzündspannung (V).
     * @param [out] startTime Lichtbogenzündzeit (ms).
     * @param [out] weldCurrent Schweißstrom (A).
     * @param [out] weldVoltage Schweißspannung (V).
     * @param [out] endCurrent Lichtbogenendstrom (A).
     * @param [out] endVoltage Lichtbogenendspannung (V).
     * @param [out] endTime Lichtbogenendzeit (ms).
     * @return Fehlercode.
     */
    errno_t WeldingGetProcessParam(int id, double& startCurrent, double& startVoltage, double& startTime, double& weldCurrent, double& weldVoltage, double& endCurrent, double& endVoltage, double& endTime);

Beziehung zwischen Schweißstrom und Analogausgang festlegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt die Beziehung zwischen Schweißstrom und Analogausgang fest.
    * @param [in] currentMin Stromwert des linken Punkts der linearen Beziehung (A).
    * @param [in] currentMax Stromwert des rechten Punkts der linearen Beziehung (A).
    * @param [in] outputVoltageMin Analogausgangsspannung des linken Punkts (V).
    * @param [in] outputVoltageMax Analogausgangsspannung des rechten Punkts (V).
    * @return Fehlercode.
    */
    errno_t WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Beziehung zwischen Schweißspannung und Analogausgang festlegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Legt die Beziehung zwischen Schweißspannung und Analogausgang fest.
    * @param [in] weldVoltageMin Spannungswert des linken Punkts der linearen Beziehung (V).
    * @param [in] weldVoltageMax Spannungswert des rechten Punkts der linearen Beziehung (V).
    * @param [in] outputVoltageMin Analogausgangsspannung des linken Punkts (V).
    * @param [in] outputVoltageMax Analogausgangsspannung des rechten Punkts (V).
    * @return Fehlercode.
    */
    errno_t WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Beziehung zwischen Schweißstrom und Analogausgang abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Beziehung zwischen Schweißstrom und Analogausgang zurück.
    * @param [out] currentMin Stromwert des linken Punkts (A).
    * @param [out] currentMax Stromwert des rechten Punkts (A).
    * @param [out] outputVoltageMin Analogausgangsspannung des linken Punkts (V).
    * @param [out] outputVoltageMax Analogausgangsspannung des rechten Punkts (V).
    * @return Fehlercode.
    */
    errno_t WeldingGetCurrentRelation(double *currentMin, double *currentMax, double *outputVoltageMin, double *outputVoltageMax);

Beziehung zwischen Schweißspannung und Analogausgang abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt die Beziehung zwischen Schweißspannung und Analogausgang zurück.
    * @param [out] weldVoltageMin Spannungswert des linken Punkts (V).
    * @param [out] weldVoltageMax Spannungswert des rechten Punkts (V).
    * @param [out] outputVoltageMin Analogausgangsspannung des linken Punkts (V).
    * @param [out] outputVoltageMax Analogausgangsspannung des rechten Punkts (V).
    * @return Fehlercode.
    */
    errno_t WeldingGetVoltageRelation(double *weldVoltageMin, double *weldVoltageMax, double *outputVoltageMin, double *outputVoltageMax);

Schweißstrom einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt den Schweißstrom ein.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] current Schweißstromwert (A).
    * @param [in] AOIndex Analogausgangsport des Steuerschranks für den Strom (0-1).
    * @param [in] blend Glättung 0-nicht glätten; 1-glätten.
    * @return Fehlercode.
    */
    errno_t WeldingSetCurrent(int ioType, double current, int AOIndex, int blend);

Schweißspannung einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Schweißspannung ein.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] voltage Schweißspannungswert (V).
    * @param [in] AOIndex Analogausgangsport des Steuerschranks für die Spannung (0-1).
    * @param [in] blend Glättung 0-nicht glätten; 1-glätten.
    * @return Fehlercode.
    */
    errno_t WeldingSetVoltage(int ioType, double voltage, int AOIndex, int blend);

Pendelparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Stellt die Pendelparameter ein.
     * @param [in] weaveNum Konfigurationsnummer der Pendelparameter.
     * @param [in] weaveType Pendeltyp 0-Ebenes Dreieck; 1-Vertikales L-Dreieck; 2-Kreis im Uhrzeigersinn; 3-Kreis gegen Uhrzeigersinn; 4-Ebene Sinus; 5-Vertikales L-Sinus; 6-Vertikales Dreieck; 7-Vertikales Sinus.
     * @param [in] weaveFrequency Pendelfrequenz (Hz).
     * @param [in] weaveIncStayTime Wartezeitmodus 0-Zyklus ohne Wartezeit; 1-Zyklus mit Wartezeit.
     * @param [in] weaveRange Pendelamplitude (mm).
     * @param [in] weaveLeftRange Länge der linken Sehne bei vertikalem Dreieck (mm).
     * @param [in] weaveRightRange Länge der rechten Sehne bei vertikalem Dreieck (mm).
     * @param [in] additionalStayTime Verweilzeit am vertikalen Dreieckspunkt (ms).
     * @param [in] weaveLeftStayTime Linke Pendelverweilzeit (ms).
     * @param [in] weaveRightStayTime Rechte Pendelverweilzeit (ms).
     * @param [in] weaveCircleRadio Rückrufverhältnis für Kreispendeln (0-100%).
     * @param [in] weaveStationary Position während Wartezeit 0-weiterbewegen; 1-stillstehen.
     * @param [in] weaveYawAngle Azimutwinkel der Pendelrichtung (Rotation um Pendel-Z-Achse), Einheit °.
     * @param [in] weaveRotAngle Rollwinkel der Pendelrichtung (Neigung um Pendel-X-Achse), Einheit °.
     * @return Fehlercode.
     */
     errno_t WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle = 0);

Codebeispiel zum Einstellen von Schweißparametern
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSetWeldParam(void)
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
      robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000);
      robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333);
      double startCurrent = 0;
      double startVoltage = 0;
      double startTime = 0;
      double weldCurrent = 0;
      double weldVoltage = 0;
      double endCurrent = 0;
      double endVoltage = 0;
      double endTime = 0;
      robot.WeldingGetProcessParam(1, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
      cout << "the Num 1 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
      robot.WeldingGetProcessParam(2, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
      cout << "the Num 2 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
      rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
      cout << "WeldingSetCurrentRelation rtn is: " << rtn << endl;
      rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
      cout << "WeldingSetVoltageRelation rtn is: " << rtn << endl;
      double current_min = 0;
      double current_max = 0;
      double vol_min = 0;
      double vol_max = 0;
      double output_vmin = 0;
      double output_vmax = 0;
      int curIndex = 0;
      int volIndex = 0;
      rtn = robot.WeldingGetCurrentRelation(&current_min, &current_max, &output_vmin, &output_vmax, &curIndex);
      cout << "WeldingGetCurrentRelation rtn is: " << rtn << endl;
      cout << "current min " << current_min << " current max " << current_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
      rtn = robot.WeldingGetVoltageRelation(&vol_min, &vol_max, &output_vmin, &output_vmax, &volIndex);
      cout << "WeldingGetVoltageRelation rtn is: " << rtn << endl;
      cout << "vol min " << vol_min << " vol max " << vol_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
      rtn = robot.WeldingSetCurrent(1, 100, 0, 0);
      cout << "WeldingSetCurrent rtn is: " << rtn << endl;
      this_thread::sleep_for(chrono::seconds(3));
      rtn = robot.WeldingSetVoltage(1, 10, 0, 0);
      cout << "WeldingSetVoltage rtn is: " << rtn << endl;
      rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
      cout << "rtn is: " << rtn << endl;
      robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);
      rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
      printf("WeldingSetCheckArcInterruptionParam  %d\n", rtn);
      rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
      printf("WeldingSetReWeldAfterBreakOffParam  %d\n", rtn);
      int enable = 0;
      double length = 0;
      double velocity = 0;
      int moveType = 0;
      int checkEnable = 0;
      int arcInterruptTimeLength = 0;
      rtn = robot.WeldingGetCheckArcInterruptionParam(&checkEnable, &arcInterruptTimeLength);
      printf("WeldingGetCheckArcInterruptionParam checkEnable %d  arcInterruptTimeLength %d\n", checkEnable, arcInterruptTimeLength);
      rtn = robot.WeldingGetReWeldAfterBreakOffParam(&enable, &length, &velocity, &moveType);
      printf("WeldingGetReWeldAfterBreakOffParam enable = %d, length = %lf, velocity = %lf, moveType = %d\n", enable, length, velocity, moveType);
      robot.SetWeldMachineCtrlModeExtDoNum(17);
      for (int i = 0; i < 5; i++)
      {
        robot.SetWeldMachineCtrlMode(0);
        robot.Sleep(1000);
        robot.SetWeldMachineCtrlMode(1);
        robot.Sleep(1000);
      }
      robot.CloseRPC();
      return 0;
    }

Pendelparameter sofort einstellen (Online)
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die Pendelparameter sofort ein (Online).
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter.
    * @param [in] weaveType Pendeltyp (siehe WeaveSetPara).
    * @param [in] weaveFrequency Pendelfrequenz (Hz).
    * @param [in] weaveIncStayTime Wartezeitmodus 0-Zyklus ohne Wartezeit; 1-Zyklus mit Wartezeit.
    * @param [in] weaveRange Pendelamplitude (mm).
    * @param [in] weaveLeftStayTime Linke Pendelverweilzeit (ms).
    * @param [in] weaveRightStayTime Rechte Pendelverweilzeit (ms).
    * @param [in] weaveCircleRadio Rückrufverhältnis für Kreispendeln (0-100%).
    * @param [in] weaveStationary Position während Wartezeit 0-weiterbewegen; 1-stillstehen.
    * @return Fehlercode.
    */
    errno_t WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Stellt die Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung ein.
     * @param [in] checkEnable Erkennung aktivieren/deaktivieren; 0-deaktivieren; 1-aktivieren.
     * @param [in] arcInterruptTimeLength Bestätigungsdauer für Lichtbogenunterbrechung (ms).
     * @return Fehlercode.
    */
    errno_t WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung zurück.
     * @param [out] checkEnable Erkennung aktiviert? 0-deaktiviert; 1-aktiviert.
     * @param [out] arcInterruptTimeLength Bestätigungsdauer für Lichtbogenunterbrechung (ms).
     * @return Fehlercode.
    */
    errno_t WeldingGetCheckArcInterruptionParam(int* checkEnable, int* arcInterruptTimeLength);

Parameter für die Wiederaufnahme nach Schweißunterbrechung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Stellt die Parameter für die Wiederaufnahme nach Schweißunterbrechung ein.
     * @param [in] enable Wiederaufnahme nach Unterbrechung aktivieren.
     * @param [in] length Überlappungslänge der Schweißnaht (mm).
     * @param [in] velocity Geschwindigkeitsprozentsatz für die Rückkehr zum Wiederzündpunkt (0-100).
     * @param [in] moveType Bewegungstyp zum Wiederzündpunkt; 0-LIN; 1-PTP.
     * @return Fehlercode.
    */
    errno_t WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);

Parameter für die Wiederaufnahme nach Schweißunterbrechung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Gibt die Parameter für die Wiederaufnahme nach Schweißunterbrechung zurück.
     * @param [out] enable Wiederaufnahme nach Unterbrechung aktiviert?.
     * @param [out] length Überlappungslänge der Schweißnaht (mm).
     * @param [out] velocity Geschwindigkeitsprozentsatz für die Rückkehr zum Wiederzündpunkt.
     * @param [out] moveType Bewegungstyp zum Wiederzündpunkt; 0-LIN; 1-PTP.
     * @return Fehlercode.
    */
    errno_t WeldingGetReWeldAfterBreakOffParam(int* enable, double* length, double* velocity, int* moveType);

Erweiterten DO-Port für Schweißgeräte-Steuermodus einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt den erweiterten DO-Port für den Schweißgeräte-Steuermodus ein.
    * @param DONum DO-Portnummer (0-127).
    * @return Fehlercode.
    */
    errno_t SetWeldMachineCtrlModeExtDoNum(int DONum);

Schweißgeräte-Steuermodus einstellen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt den Schweißgeräte-Steuermodus ein.
    * @param mode Schweißgeräte-Steuermodus; 0-Einheitlich.
    * @return Fehlercode.
    */
    errno_t SetWeldMachineCtrlMode(int mode);

Schweißen starten (Lichtbogen zünden)
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Startet das Schweißen (zündet den Lichtbogen).
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] arcNum Nummer der Schweißgerätekonfigurationsdatei.
    * @param [in] timeout Zeitüberschreitung für die Lichtbogenzündung (ms).
    * @return Fehlercode.
    */
    errno_t ARCStart(int ioType, int arcNum, int timeout);

Schweißen beenden (Lichtbogen löschen)
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Beendet das Schweißen (löscht den Lichtbogen).
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] arcNum Nummer der Schweißgerätekonfigurationsdatei.
    * @param [in] timeout Zeitüberschreitung für das Lichtbogenlöschen (ms).
    * @return Fehlercode.
    */
    errno_t ARCEnd(int ioType, int arcNum, int timeout);

Pendeln starten
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Startet das Pendeln.
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter.
    * @return Fehlercode.
    */
    errno_t WeaveStart(int weaveNum);

Pendeln beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Beendet das Pendeln.
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter.
    * @return Fehlercode.
    */
    errno_t WeaveEnd(int weaveNum);

Vorwärts-Drahtvorschub
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Steuert den Vorwärts-Drahtvorschub.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] wireFeed Drahtvorschubsteuerung 0-stoppen; 1-starten.
    * @return Fehlercode.
    */
    errno_t SetForwardWireFeed(int ioType, int wireFeed);

Rückwärts-Drahtvorschub
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Steuert den Rückwärts-Drahtvorschub.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] wireFeed Drahtvorschubsteuerung 0-stoppen; 1-starten.
    * @return Fehlercode.
    */
    errno_t SetReverseWireFeed(int ioType, int wireFeed);

Schutzgas steuern
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Steuert das Schutzgas.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] airControl Gassteuerung 0-stoppen; 1-starten.
    * @return Fehlercode.
    */
    errno_t SetAspirated(int ioType, int airControl);

Schweißen nach Unterbrechung wiederaufnehmen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Nimmt das Schweißen nach einer Unterbrechung wieder auf.
     * @return Fehlercode.
    */
    errno_t WeldingStartReWeldAfterBreakOff();

Schweißen nach Unterbrechung abbrechen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Bricht das Schweißen nach einer Unterbrechung ab.
     * @return Fehlercode.
     */
    errno_t WeldingAbortWeldAfterBreakOff();

Codebeispiel für Roboter-Schweißsteuerung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestWelding(void)
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
      robot.SetForwardWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetForwardWireFeed(0, 0);
      robot.SetReverseWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetReverseWireFeed(0, 0);
      robot.SetAspirated(0, 1);
      robot.Sleep(1000);
      robot.SetAspirated(0, 0);
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.WeaveStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.ARCEnd(1, 0, 10000);
      robot.WeaveEnd(0);
      robot.WeldingStartReWeldAfterBreakOff();
      robot.WeldingAbortWeldAfterBreakOff();
      robot.CloseRPC();
      return 0;
    }

Segmentweises Schweißen starten
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Startet das segmentweise Schweißen.
    * @param [in] startDesePos Kartesische Position des Startpunkts.
    * @param [in] endDesePos Kartesische Pose des Endpunkts.
    * @param [in] startJPos Gelenkposition des Startpunkts.
    * @param [in] endJPos Gelenkposition des Endpunkts.
    * @param [in] weldLength Länge des Schweißsegments (mm).
    * @param [in] noWeldLength Länge des Nicht-Schweißsegments (mm).
    * @param [in] weldIOType Schweiß-I/O-Typ (0-Steuerschrank I/O; 1-Erweiterungs-I/O).
    * @param [in] arcNum Nummer der Schweißgerätekonfigurationsdatei.
    * @param [in] weldTimeout Zeitüberschreitung für Lichtbogenzündung/-löschung (ms).
    * @param [in] isWeave Soll gependelt werden?.
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter.
    * @param [in] tool Werkzeugkoordinatennummer, Bereich [0~14].
    * @param [in] user Werkstückkoordinatennummer, Bereich [0~14].
    * @param [in] vel Geschwindigkeitsprozentsatz, Bereich [0~100].
    * @param [in] acc Beschleunigungsprozentsatz, Bereich [0~100] (vorerst nicht verfügbar).
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor, Bereich [0~100].
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend), Einheit mm.
    * @param [in] epos Position der Erweiterungsachse, Einheit mm.
    * @param [in] search 0-keine Schweißdraht-Positionssuche, 1-Schweißdraht-Positionssuche.
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem.
    * @param [in] offset_pos Posenversatz.
    * @return Fehlercode.
    */
    errno_t SegmentWeldStart(DescPose *startDesePos, DescPose *endDesePos, JointPos *startJPos, JointPos *endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout, bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos);

Codebeispiel für robotergestütztes segmentweises Schweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    int TestSegWeld(void)
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
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      rtn = robot.SegmentWeldStart(&p1Desc, &p2Desc, &p1Joint, &p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      printf("SegmentWeldStart rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Simulationspendeln starten
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Startet das Simulationspendeln (nur Visualisierung, ohne Bewegung?).
     * @param [in] weaveNum Pendelparameternummer.
     * @return Fehlercode.
     */
    errno_t WeaveStartSim(int weaveNum);

Simulationspendeln beenden
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Beendet das Simulationspendeln.
     * @param [in] weaveNum Pendelparameternummer.
     * @return Fehlercode.
     */
    errno_t WeaveEndSim(int weaveNum);

Bahnprüfung/-warnung starten (ohne Bewegung)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Startet die Bahnprüfung/-warnung (ohne Bewegung).
     * @param [in] weaveNum Pendelparameternummer.
     * @return Fehlercode.
     */
    errno_t WeaveInspectStart(int weaveNum);

Bahnprüfung/-warnung beenden (ohne Bewegung)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Beendet die Bahnprüfung/-warnung (ohne Bewegung).
     * @param [in] weaveNum Pendelparameternummer.
     * @return Fehlercode.
     */
    errno_t WeaveInspectEnd(int weaveNum);

Pendel-Gradientenstart (WeaveChangeStart)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Startet den Pendel-Gradienten (Änderung von Parametern während der Bewegung).
     * @param [in] weaveChangeFlag 1-Pendelparameter ändern; 2-Pendelparameter + Schweißgeschwindigkeit ändern.
     * @param [in] weaveNum Pendelnummer.
     * @param [in] velStart Schweißgeschwindigkeit am Start (cm/min).
     * @param [in] velEnd Schweißgeschwindigkeit am Ende (cm/min).
     * @return Fehlercode.
     */
     errno_t WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Codebeispiel für robotergestütztes Pendel-Gradientenschweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestWeave(void)
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
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveStartSim(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveEndSim(0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveInspectStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveInspectEnd(0);
      robot.WeldingSetVoltage(1, 19, 0, 0);
      robot.WeldingSetCurrent(1, 190, 0, 0);
      robot.MoveL(&p1Joint, &p1Desc, 1, 1, 100, 100, 50, -1, &exaxisPos, 0, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.WeaveStart(0);
      robot.WeaveChangeStart(1, 0, 50, 30);
      robot.MoveL(&p2Joint, &p2Desc, 1, 1, 100, 100, 1, -1, &exaxisPos, 0, 0, &offdese);
      robot.WeaveChangeEnd();
      robot.WeaveEnd(0);
      robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.ARCEnd(1, 0, 10000);
      robot.CloseRPC();
      return 0;
    }

Pendel-Gradienten beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Beendet den Pendel-Gradienten.
     * @return Fehlercode.
     */
    errno_t WeaveChangeEnd();

Erweiterter I/O - Gasprüfsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguriert den erweiterten DO-Port für das Gasprüfsignal des Schweißgeräts.
     * @param [in] DONum Erweiterte DO-Nummer für das Gasprüfsignal.
     * @return Fehlercode.
     */
    errno_t SetAirControlExtDoNum(int DONum);

Erweiterter I/O - Lichtbogenzünde-Signal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguriert den erweiterten DO-Port für das Lichtbogenzünde-Signal des Schweißgeräts.
     * @param [in] DONum Erweiterte DO-Nummer für das Lichtbogenzünde-Signal.
     * @return Fehlercode.
     */
    errno_t SetArcStartExtDoNum(int DONum);

Erweiterter I/O - Rückwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguriert den erweiterten DO-Port für das Rückwärts-Drahtvorschubsignal des Schweißgeräts.
     * @param [in] DONum Erweiterte DO-Nummer für das Rückwärts-Drahtvorschubsignal.
     * @return Fehlercode.
     */
    errno_t SetWireReverseFeedExtDoNum(int DONum);

Erweiterter I/O - Vorwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguriert den erweiterten DO-Port für das Vorwärts-Drahtvorschubsignal des Schweißgeräts.
     * @param [in] DONum Erweiterte DO-Nummer für das Vorwärts-Drahtvorschubsignal.
     * @return Fehlercode.
     */
    errno_t SetWireForwardFeedExtDoNum(int DONum);

Erweiterter I/O - Erfolgreiche Lichtbogenzündung-Signal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguriert den erweiterten DI-Port für das Signal "Lichtbogenzündung erfolgreich" des Schweißgeräts.
     * @param [in] DINum Erweiterte DI-Nummer für das Signal "Lichtbogenzündung erfolgreich".
     * @return Fehlercode.
     */
    errno_t SetArcDoneExtDiNum(int DINum);

Erweiterter I/O - Bereitschaftssignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguriert den erweiterten DI-Port für das Bereitschaftssignal des Schweißgeräts.
     * @param [in] DINum Erweiterte DI-Nummer für das Bereitschaftssignal.
     * @return Fehlercode.
     */
    errno_t SetWeldReadyExtDiNum(int DINum);

Erweiterte I/O - Signale für Wiederaufnahme/Abruch nach Schweißunterbrechung konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguriert die erweiterten DI-Ports für die Signale "Wiederaufnahme nach Unterbrechung" und "Abbruch nach Unterbrechung".
     * @param [in] reWeldDINum Erweiterte DI-Nummer für das Signal "Wiederaufnahme nach Unterbrechung".
     * @param [in] abortWeldDINum Erweiterte DI-Nummer für das Signal "Abbruch nach Unterbrechung".
     * @return Fehlercode.
     */
    errno_t SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Codebeispiel zum Konfigurieren erweiterter I/O-Schweißsignale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestExtDIConfig(void)
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
      robot.SetArcStartExtDoNum(10);
      robot.SetAirControlExtDoNum(20);
      robot.SetWireForwardFeedExtDoNum(30);
      robot.SetWireReverseFeedExtDoNum(40);
      robot.SetWeldReadyExtDiNum(50);
      robot.SetArcDoneExtDiNum(60);
      robot.SetExtDIWeldBreakOffRecover(70, 80);
      robot.SetWireSearchExtDIONum(0, 1);
      robot.CloseRPC();
      return 0;
    }

Lichtbogen-Tracking-Steuerung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

      /**
      * @brief Steuert das Lichtbogen-Tracking.
      * @param  [in] flag Schalter, 0-aus; 1-ein.
      * @param  [in] delaytime Verzögerungszeit, Einheit ms.
      * @param  [in] isLeftRight Links/Rechts-Abweichungskompensation aktivieren.
      * @param  [in] klr Links/Rechts-Einstellkoeffizient (Empfindlichkeit).
      * @param  [in] tStartLr Startzeit für Links/Rechts-Kompensation (cyc).
      * @param  [in] stepMaxLr Maximale Kompensation pro Schritt links/rechts (mm).
      * @param  [in] sumMaxLr Maximale Gesamtkompensation links/rechts (mm).
      * @param  [in] isUpLow Oben/Unten-Abweichungskompensation aktivieren.
      * @param  [in] kud Oben/Unten-Einstellkoeffizient (Empfindlichkeit).
      * @param  [in] tStartUd Startzeit für Oben/Unten-Kompensation (cyc).
      * @param  [in] stepMaxUd Maximale Kompensation pro Schritt oben/unten (mm).
      * @param  [in] sumMaxUd Maximale Gesamtkompensation oben/unten (mm).
      * @param  [in] axisSelect Koordinatensystem für oben/unten, 0-Pendel; 1-Werkzeug; 2-Basis.
      * @param  [in] referenceType Einstellungsart für oben/unten-Referenzstrom, 0-Rückmeldung; 1-Konstante.
      * @param  [in] referSampleStartUd Startzähler für Abtastung des oben/unten-Referenzstroms (bei Rückmeldung) (cyc).
      * @param  [in] referSampleCountUd Zyklenzahl für Abtastung des oben/unten-Referenzstroms (bei Rückmeldung) (cyc).
      * @param  [in] referenceCurrent Oben/unten-Referenzstrom (mA).
      * @param  [in] offsetType Versatz-Tracking-Typ, 0-kein Versatz; 1-Abtastung; 2-Prozentsatz.
      * @param  [in] offsetParameter Versatzparameter; Abtastung (Startzeit der Versatzabtastung, Standard eine Abtastperiode); Prozentsatz (Versatzprozentsatz (-100 ~ 100)).
      * @return  Fehlercode.
      */
     errno_t ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType = 0, int offsetParameter = 0);

Eingangssignalport für Lichtbogen-Tracking einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief Stellt den erweiterten AI-Kanal für das Lichtbogen-Tracking-Eingangssignal ein.
      * @param  [in] channel Auswahl des AI-Kanals für das Lichtbogen-Tracking, [0-3].
      * @return Fehlercode.
      */
     errno_t ArcWeldTraceExtAIChannelConfig(int channel);

Lichtbogen-Tracking + Mehrlagenschweiß-Kompensation starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Startet Lichtbogen-Tracking mit Kompensation für Mehrlagenschweißen.
    * @return Fehlercode.
    */
    errno_t ArcWeldTraceReplayStart();

Lichtbogen-Tracking + Mehrlagenschweiß-Kompensation beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Beendet Lichtbogen-Tracking mit Kompensation für Mehrlagenschweißen.
    * @return Fehlercode.
    */
    errno_t ArcWeldTraceReplayEnd();

Koordinatentransformation für Mehrlagenschweiß-Versatz
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Führt eine Koordinatentransformation für den Versatz beim Mehrlagenschweißen durch.
    * @param [in] pointO Ursprungspunkt O.
    * @param [in] pointX Punkt auf der X-Achse.
    * @param [in] pointZ Punkt auf der Z-Achse.
    * @param [in] dx Versatz in x-Richtung.
    * @param [in] dy Versatz in y-Richtung.
    * @param [in] db Versatz in ?-Richtung (wahrscheinlich z).
    * @param [out] offset Resultierender Posenversatz.
    * @return Fehlercode.
    */
    errno_t MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, DescPose& offset);

Codebeispiel für Lichtbogen-Tracking mit Mehrlagenschweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestArcWeldTrace(void)
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
      JointPos mulitilineorigin1_joint(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
      DescPose mulitilineorigin1_desc(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);
      DescTran mulitilineX1_desc;
      mulitilineX1_desc.x = -677.556;
      mulitilineX1_desc.y = 211.949;
      mulitilineX1_desc.z = -1.206;
      DescTran mulitilineZ1_desc;
      mulitilineZ1_desc.x = -677.564;
      mulitilineZ1_desc.y = 190.956;
      mulitilineZ1_desc.z = 19.817;
      JointPos mulitilinesafe_joint(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
      DescPose mulitilinesafe_desc(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
      JointPos mulitilineorigin2_joint(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
      DescPose mulitilineorigin2_desc(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);
      DescTran mulitilineX2_desc;
      mulitilineX2_desc.x = -563.965;
      mulitilineX2_desc.y = 220.355;
      mulitilineX2_desc.z = -0.680;
      DescTran mulitilineZ2_desc;
      mulitilineZ2_desc.x = -563.968;
      mulitilineZ2_desc.y = 215.362;
      mulitilineZ2_desc.z = 4.331;
      ExaxisPos epos(0, 0, 0, 0);
      DescPose offset(0, 0, 0, 0, 0, 0);
      robot.Sleep(10);
      int error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.WeaveStart(0);
      printf("WeaveStart return: %d\n", error);
      error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.WeaveEnd(0);
      printf("WeaveEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("ArcWeldTraceReplayStart return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 3000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      robot.CloseRPC();
      return 0;
    }

Auswahl des AI-Kanals für die Schweißstromrückmeldung beim Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Wählt den AI-Kanal für die Schweißstromrückmeldung beim Lichtbogen-Tracking aus.
     * @param [in] channel Kanal; 0-Erweiterungs-AI0; 1-Erweiterungs-AI1; 2-Erweiterungs-AI2; 3-Erweiterungs-AI3; 4-Steuerschrank-AI0; 5-Steuerschrank-AI1.
     * @return Fehlercode.
     */
     errno_t ArcWeldTraceAIChannelCurrent(int channel);

Auswahl des AI-Kanals für die Schweißspannungsrückmeldung beim Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Wählt den AI-Kanal für die Schweißspannungsrückmeldung beim Lichtbogen-Tracking aus.
     * @param [in] channel Kanal; 0-Erweiterungs-AI0; 1-Erweiterungs-AI1; 2-Erweiterungs-AI2; 3-Erweiterungs-AI3; 4-Steuerschrank-AI0; 5-Steuerschrank-AI1.
     * @return Fehlercode.
     */
     errno_t ArcWeldTraceAIChannelVoltage(int channel);

Umrechnungsparameter für die Schweißstromrückmeldung beim Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
      * @brief Stellt die Umrechnungsparameter für die Schweißstromrückmeldung beim Lichtbogen-Tracking ein.
      * @param [in] AILow Untere Grenze des AI-Kanals, Standard 0 V, Bereich [0-10 V].
      * @param [in] AIHigh Obere Grenze des AI-Kanals, Standard 10 V, Bereich [0-10 V].
      * @param [in] currentLow Schweißstromwert entsprechend der unteren AI-Grenze, Standard 0 A, Bereich [0-200 A].
      * @param [in] currentHigh Schweißstromwert entsprechend der oberen AI-Grenze, Standard 100 A, Bereich [0-200 A].
      * @return Fehlercode.
      */
     errno_t ArcWeldTraceCurrentPara(float AILow, float AIHigh, float currentLow, float currentHigh);

Umrechnungsparameter für die Schweißspannungsrückmeldung beim Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
      * @brief Stellt die Umrechnungsparameter für die Schweißspannungsrückmeldung beim Lichtbogen-Tracking ein.
      * @param [in] AILow Untere Grenze des AI-Kanals, Standard 0 V, Bereich [0-10 V].
      * @param [in] AIHigh Obere Grenze des AI-Kanals, Standard 10 V, Bereich [0-10 V].
      * @param [in] voltageLow Schweißspannungswert entsprechend der unteren AI-Grenze, Standard 0 V, Bereich [0-200 V].
      * @param [in] voltageHigh Schweißspannungswert entsprechend der oberen AI-Grenze, Standard 100 V, Bereich [0-200 V].
      * @return Fehlercode.
      */
      errno_t ArcWeldTraceVoltagePara(float AILow, float AIHigh, float voltageLow, float voltageHigh);

Codebeispiel für Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int WeldTraceControlWithCtrlBoxAI(FRRobot* robot)
    {
      DescPose startdescPose = { -473.86, 257.879, -20.849, -37.317, -42.021, 2.543 };
      JointPos startjointPos = { -43.487, -76.526, 95.568, -104.445, -89.356, 3.72 };

      DescPose enddescPose = { -499.844, 141.225, 7.72, -34.856, -40.17, 13.13 };
      JointPos endjointPos = { -31.305, -82.998, 99.401, -104.426, -89.35, 3.696 };

      DescPose safedescPose = { -504.043, 275.181, 40.908, -28.002, -42.025, -14.044 };
      JointPos safejointPos = { -39.078, -76.732, 87.227, -99.47, -94.301, 18.714 };

      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10);

      robot->WeldingSetVoltage(0, 25, 1, 0);// ----Spannung einstellen
      robot->WeldingSetCurrent(0, 260, 0, 0);// ----Strom einstellen

      int rtn = robot->ArcWeldTraceAIChannelCurrent(4);
      cout << "ArcWeldTraceAIChannelCurrent rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceAIChannelVoltage(5);
      cout << "ArcWeldTraceAIChannelVoltage rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceCurrentPara(0, 5, 0, 500);
      cout << "ArcWeldTraceCurrentPara rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceVoltagePara(1.018, 10, 0, 50);
      cout << "ArcWeldTraceVoltagePara rtn is " << rtn << endl;
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      return 0;
    }

Erweiterte I/O-Ports für die Schweißdraht-Positionssuche einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt die erweiterten I/O-Ports für die Schweißdraht-Positionssuche ein.
    * @param searchDoneDINum Erweiterter DI-Port für "Positionssuche erfolgreich" (0-127).
    * @param searchStartDONum Erweiterter DO-Port für Start/Stopp der Positionssuche (0-127).
    * @return Fehlercode.
    */
    errno_t SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Beispielprogramm für Schweißdraht-Positionssuche (UDP)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    void TestUDPWireSearch(FRRobot* robot)
    {
    robot->ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 50, 5, 50, 1, 50, 10);
    robot->ExtDevLoadUDPDriver();

    robot->SetWireSearchExtDIONum(0, 0);

    int rtn0, rtn1, rtn2 = 0;
    ExaxisPos exaxisPos = { 0.0, 0.0, 0.0, 0.0 };
    DescPose offdese = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
    
    DescPose descStart = { -158.767, -510.596, 271.709, -179.427, -0.745, -137.349 };
    JointPos jointStart = { 61.667, -79.848, 108.639, -119.682, -89.700, -70.985 };
    
    DescPose descEnd = { 0.332, -516.427, 270.688, 178.165, 0.017, -119.989 };
    JointPos jointEnd = { 79.021, -81.839, 110.752, -118.298, -91.729, -70.981 };

    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    
    DescPose descREF0A = { -66.106, -560.746, 270.381, 176.479, -0.126, -126.745 };
    JointPos jointREF0A = { 73.531, -75.588, 102.941, -116.250, -93.347, -69.689 };
    
    DescPose descREF0B = { -66.109, -528.440, 270.407, 176.479, -0.129, -126.744 };
    JointPos jointREF0B = { 72.534, -79.625, 108.046, -117.379, -93.366, -70.687 };
    
    DescPose descREF1A = { 72.975, -473.242, 270.399, 176.479, -0.129, -126.744 };
    JointPos jointREF1A = { 87.169, -86.509, 115.710, -117.341, -92.993, -56.034 };
    
    DescPose descREF1B = { 31.355, -473.238, 270.405, 176.480, -0.130, -126.745 };
    JointPos jointREF1B = { 82.117, -87.146, 116.470, -117.737, -93.145, -61.090 };

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
    rtn1 = robot->WireSearchWait("REF0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
    rtn1 = robot->WireSearchWait("REF1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
    rtn1 = robot->WireSearchWait("RES0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
    rtn1 = robot->WireSearchWait("RES1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
    vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
    int offectFlag = 0;
    DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
    rtn0 = robot->GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
    robot->PointsOffsetEnable(0, &offectPos);
    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->PointsOffsetDisable();
    }

Schweißdraht-Positionssuche starten
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Startet die Schweißdraht-Positionssuche.
    * @param  [in] refPos  1-Referenzpunkt; 0-Kontaktpunkt.
    * @param  [in] searchVel   Suchgeschwindigkeit (%).
    * @param  [in] searchDis  Suchstrecke (mm).
    * @param  [in] autoBackFlag Automatische Rückkehr-Flag, 0-nicht automatisch; 1-automatisch.
    * @param  [in] autoBackVel  Automatische Rückkehrgeschwindigkeit (%).
    * @param  [in] autoBackDis  Automatische Rückkehrstrecke (mm).
    * @param  [in] offectFlag  1-Positionssuche mit Versatz; 0-Positionssuche mit Teachpunkten.
    * @return Fehlercode.
    */
     errno_t WireSearchStart(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Schweißdraht-Positionssuche beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief Beendet die Schweißdraht-Positionssuche.
      * @param  [in] refPos  1-Referenzpunkt; 2-Kontaktpunkt.
      * @param  [in] searchVel   Suchgeschwindigkeit (%).
      * @param  [in] searchDis  Suchstrecke (mm).
      * @param  [in] autoBackFlag Automatische Rückkehr-Flag, 0-nicht automatisch; 1-automatisch.
      * @param  [in] autoBackVel  Automatische Rückkehrgeschwindigkeit (%).
      * @param  [in] autoBackDis  Automatische Rückkehrstrecke (mm).
      * @param  [in] offectFlag  1-Positionssuche mit Versatz; 2-Positionssuche mit Teachpunkten.
      * @return Fehlercode.
      */
     errno_t WireSearchEnd(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Versatz aus Schweißdraht-Positionssuche berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief Berechnet den Versatz aus der Schweißdraht-Positionssuche.
      * @param  [in] seamType  Nahttyp.
      * @param  [in] method   Berechnungsmethode.
      * @param  [in] varNameRef Array der Referenzpunktnamen 1-6, "#" für nicht verwendete Punkte.
      * @param  [in] varNameRes Array der Kontaktpunktnamen 1-6, "#" für nicht verwendete Punkte.
      * @param  [out] offectFlag 0-Versatz direkt zum Befehlspunkt addieren; 1-Versatz erfordert Koordinatentransformation des Befehlspunkts.
      * @param  [out] offect Versatzpose [x, y, z, a, b, c].
      * @return Fehlercode.
      */
     errno_t GetWireSearchOffset(int seamType, int method, std::vector<std::string> varNameRef, std::vector<std::string> varNameRes, int& offectFlag, DescPose& offect);

Auf Abschluss der Schweißdraht-Positionssuche warten
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief Wartet auf den Abschluss der Schweißdraht-Positionssuche.
      * @param [in] varName Name der Variable, die das Ergebnis speichern soll? (z.B. "REF0")
      * @return Fehlercode.
      */
     errno_t WireSearchWait(std::string varName);

Kontaktpunkt der Schweißdraht-Positionssuche in Datenbank schreiben
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief Schreibt einen Kontaktpunkt der Schweißdraht-Positionssuche in die Datenbank.
      * @param  [in] varName  Kontaktpunktname "RES0" ~ "RES99".
      * @param  [in] pos  Kontaktpunktdaten [x, y, z, a, b, c].
      * @return Fehlercode.
      */
     errno_t SetPointToDatabase(std::string varName, DescPose pos);

Codebeispiel für robotergestützte Schweißdraht-Positionssuche
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestWireSearch(void)
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
      DescPose toolCoord(0, 0, 200, 0, 0, 0);
      robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
      DescPose wobjCoord(0, 0, 0, 0, 0, 0);
      robot.SetWObjCoord(1, &wobjCoord, 0);
      int rtn0, rtn1, rtn2 = 0;
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      DescPose descStart = { 216.543, 445.175, 93.465, 179.683, 1.757, -112.641 };
      JointPos jointStart = { -128.345, -86.660, 114.679, -119.625, -89.219, 74.303 };
      DescPose descEnd = { 111.143, 523.384, 87.659, 179.703, 1.835, -97.750 };
      JointPos jointEnd = { -113.454, -81.060, 109.328, -119.954, -89.218, 74.302 };
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      DescPose descREF0A = { 142.135, 367.604, 86.523, 179.728, 1.922, -111.089 };
      JointPos jointREF0A = { -126.794, -100.834, 128.922, -119.864, -89.218, 74.302 };
      DescPose descREF0B = { 254.633, 463.125, 72.604, 179.845, 2.341, -114.704 };
      JointPos jointREF0B = { -130.413, -81.093, 112.044, -123.163, -89.217, 74.303 };
      DescPose descREF1A = { 92.556, 485.259, 47.476, -179.932, 3.130, -97.512 };
      JointPos jointREF1A = { -113.231, -83.815, 119.877, -129.092, -89.217, 74.303 };
      DescPose descREF1B = { 203.103, 583.836, 63.909, 179.991, 2.854, -103.372 };
      JointPos jointREF1B = { -119.088, -69.676, 98.692, -121.761, -89.219, 74.303 };
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
      rtn1 = robot.WireSearchWait("REF0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
      rtn1 = robot.WireSearchWait("REF1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
      rtn1 = robot.WireSearchWait("RES0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //起点
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //方向点
      rtn1 = robot.WireSearchWait("RES1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
      vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
      int offectFlag = 0;
      DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
      rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
      robot.PointsOffsetEnable(0, &offectPos);
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese);
      robot.PointsOffsetDisable();
      robot.CloseRPC();
      return 0;
    }

Schweißspannungs-Gradienten starten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
      * @brief Startet den Schweißspannungs-Gradienten.
      * @param [in] IOType Steuerungstyp; 0-Steuerschrank I/O; 1-UDP; 2-ModbusTCP.
      * @param [in] voltageStart Start-Schweißspannung (V).
      * @param [in] voltageEnd End-Schweißspannung (V).
      * @param [in] AOIndex AO-Port des Steuerschranks (0-1).
      * @param [in] blend Glättung 0-nicht glätten; 1-glätten.
      * @return Fehlercode.
      */
      errno_t WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Schweißspannungs-Gradienten beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
      * @brief Beendet den Schweißspannungs-Gradienten.
      * @return Fehlercode.
      */
     errno_t WeldingSetVoltageGradualChangeEnd();

Schweißstrom-Gradienten starten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
      * @brief Startet den Schweißstrom-Gradienten.
      * @param [in] IOType Steuerungstyp; 0-Steuerschrank I/O; 1-UDP; 2-ModbusTCP.
      * @param [in] currentStart Start-Schweißstrom (A).
      * @param [in] currentEnd End-Schweißstrom (A).
      * @param [in] AOIndex AO-Port des Steuerschranks (0-1).
      * @param [in] blend Glättung 0-nicht glätten; 1-glätten.
      * @return Fehlercode.
      */
     errno_t WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Schweißstrom-Gradienten beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Beendet den Schweißstrom-Gradienten.
     * @return Fehlercode.
     */
    errno_t WeldingSetCurrentGradualChangeEnd();

Codebeispiel für Schweißstrom-/spannungs-Gradienten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int WeldparamChange(FRRobot* robot)
    {
      DescPose startdescPose = { -484.707, 276.996, -14.013, -37.657, -40.508, -1.548 };
      JointPos startjointPos = { -45.421, -75.673, 93.627, -104.302, -87.938, 6.005 };

      DescPose enddescPose = { -508.767, 137.109, -13.966, -37.639, -40.508, -1.559 };
      JointPos endjointPos = { -32.768, -80.947, 100.254, -106.201, -87.201, 18.648 };

      DescPose safedescPose = { -484.709, 294.436, 13.621, -37.660, -40.508, -1.545 };
      JointPos safejointPos = { -46.604, -75.410, 89.109, -100.003, -88.012, 4.823 };
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10, 1);
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      int rtn = robot->WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
      cout << "WeldingSetCurrentGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
      cout << "WeldingSetVoltageGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      
      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->WeaveChangeStart(2, 1, 24, 36);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveChangeEnd();
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      robot->WeldingSetCurrentGradualChangeEnd();
      robot->WeldingSetVoltageGradualChangeEnd();
      return 0;
    }

Benutzerdefinierte Pendelparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Stellt benutzerdefinierte Pendelparameter ein.
    * @param [in] id Benutzerdefinierte Pendelnummer: 0-2.
    * @param [in] pointNum Anzahl der Pendelpunkte (0-10).
    * @param [in] point Array der Bewegungspunkte (x, y, z).
    * @param [in] stayTime Array der Verweilzeiten an den Punkten (ms).
    * @param [in] frequency Pendelfrequenz (Hz).
    * @param [in] incStayType Wartezeitmodus: 0-Zyklus ohne Wartezeit; 1-Zyklus mit Wartezeit.
    * @param [in] stationary Position während Wartezeit: 0-weiterbewegen; 1-stillstehen.
    * @return Fehlercode.
    */
    errno_t CustomWeaveSetPara(int id, int pointNum, DescTran point[10], double stayTime[10], double frequency, int incStayType, int stationary);

Benutzerdefinierte Pendelparameter abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Gibt benutzerdefinierte Pendelparameter zurück.
    * @param [in] id Benutzerdefinierte Pendelnummer: 0-2.
    * @param [out] pointNum Anzahl der Pendelpunkte (0-10).
    * @param [out] point Array der Bewegungspunkte (x, y, z).
    * @param [out] stayTime Array der Verweilzeiten an den Punkten (ms).
    * @param [out] frequency Pendelfrequenz (Hz).
    * @param [out] incStayType Wartezeitmodus: 0-Zyklus ohne Wartezeit; 1-Zyklus mit Wartezeit.
    * @param [out] stationary Position während Wartezeit: 0-weiterbewegen; 1-stillstehen.
    * @return Fehlercode.
    */
    errno_t CustomWeaveGetPara(int id, int& pointNum, DescTran point[10], double stayTime[10], double& frequency, int& incStayType, int& stationary);

Codebeispiel für benutzerdefinierte Pendelparameter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    int TestCustomWeaveSetPara()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return 0;
      }
      robot.SetReConnectParam(true, 30000, 500);
      DescTran point[10] = {}; 
      point[0].x = -3;
      point[0].y = -3;
      point[0].z = 0;
      point[1].x = -6;
      point[1].y = 0;
      point[1].z = 0;
      point[2].x = -3;
      point[2].y = 3;
      point[2].z = 0;
      point[3].x = 0;
      point[3].y = 0;
      point[3].z = 0;
      double stayTime[10] = { 0,0,0,0,0,0,0,0,0,0 };
      rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0);
      printf("CustomWeaveSetPara rtn is %d\n", rtn);
      robot.Sleep(1000);
      int pointNum = 0;
      double frequency;
      int incStayType;
      int stationary;
      robot.CustomWeaveGetPara(2, pointNum, point, stayTime, frequency, incStayType, stationary);
      printf("pointNum is %d\n", pointNum);
      for (int i = 0; i < pointNum; i++)
      {
        printf("point %d, point x y z %f %f %f\n", i, point[i].x, point[i].y, point[i].z);
      }
      printf("fre is %f, stay is %d %d \n", frequency, incStayType, stationary);
      robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
      DescPose desc_p1 = { -288.650, 367.807, 288.404, 0.000, -0.001, 0.001 };
      DescPose desc_p2 = { -431.714, 367.815, 288.415, 0.001, 0.001, 0.000 };
      DescPose desc_p3 = { -348.666, 427.798, 288.404, -0.000, -0.000, 0.001 };
      JointPos j1 = { 140.656, -84.560, -91.707, -93.734, 90.000, 50.655 };
      JointPos j2 = { 149.873, -98.298, -77.599, -94.103, 90.000, 59.873 };
      JointPos j3 = { 139.773, -96.173, -80.014, -93.814, 90.000, 49.772 };
      ExaxisPos epos = {};
      DescPose offset_pos = {};
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.Circle(&j3, &desc_p3, 3, 0, 100, 100, &epos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 10, -1, &offset_pos);
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveC(&j3, &desc_p3, 3, 0, 100, 100, &epos, 0, &offset_pos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 0, &offset_pos, 10, -1); 
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveL(&j2, &desc_p2, 3, 0, 100, 100, 10, -1, &epos, 0, 0, &offset_pos, 0, 100);
      robot.WeaveEnd(0);
      robot.CloseRPC();
    }