Roboterschweißen
================

.. toctree::
    :maxdepth: 5

Parameter für Schweißprozesskurve einstellen
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Parameter für Schweißprozesskurve einstellen
    * @param [in] id Schweißprozessnummer (1-99)
    * @param [in] startCurrent Lichtbogenstartstrom (A)
    * @param [in] startVoltage Lichtbogenstartspannung (V)
    * @param [in] startTime Lichtbogenstartzeit (ms)
    * @param [in] weldCurrent Schweißstrom (A)
    * @param [in] weldVoltage Schweißspannung (V)
    * @param [in] endCurrent Lichtbogenendstrom (A)
    * @param [in] endVoltage Lichtbogenendspannung (V)
    * @param [in] endTime Lichtbogenendzeit (ms)
    * @return Fehlercode
    */
    int WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Parameter für Schweißprozesskurve abrufen
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Parameter für Schweißprozesskurve abrufen
    * @param [in] id Schweißprozessnummer (1-99)
    * @param [out] startCurrent Lichtbogenstartstrom (A)
    * @param [out] startVoltage Lichtbogenstartspannung (V)
    * @param [out] startTime Lichtbogenstartzeit (ms)
    * @param [out] weldCurrent Schweißstrom (A)
    * @param [out] weldVoltage Schweißspannung (V)
    * @param [out] endCurrent Lichtbogenendstrom (A)
    * @param [out] endVoltage Lichtbogenendspannung (V)
    * @param [out] endTime Lichtbogenendzeit (ms)
    * @return Fehlercode
    */
    int WeldingGetProcessParam(int id, ref double startCurrent, ref double startVoltage, ref double startTime, ref double weldCurrent, ref double weldVoltage, ref double endCurrent, ref double endVoltage, ref double endTime);

Beziehung zwischen Schweißstrom und Analogausgang einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Beziehung zwischen Schweißstrom und Analogausgang einstellen
    * @param [in] currentMin Stromwert des linken Punkts der linearen Beziehung (A)
    * @param [in] currentMax Stromwert des rechten Punkts der linearen Beziehung (A)
    * @param [in] outputVoltageMin Analogausgangsspannung des linken Punkts (V)
    * @param [in] outputVoltageMax Analogausgangsspannung des rechten Punkts (V)
    * @return Fehlercode
    */
    int WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Beziehung zwischen Schweißspannung und Analogausgang einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Beziehung zwischen Schweißspannung und Analogausgang einstellen
    * @param [in] weldVoltageMin Spannungswert des linken Punkts der linearen Beziehung (A)
    * @param [in] weldVoltageMax Spannungswert des rechten Punkts der linearen Beziehung (A)
    * @param [in] outputVoltageMin Analogausgangsspannung des linken Punkts (V)
    * @param [in] outputVoltageMax Analogausgangsspannung des rechten Punkts (V)
    * @return Fehlercode
    */
    int WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Beziehung zwischen Schweißstrom und Analogausgang abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Beziehung zwischen Schweißstrom und Analogausgang abrufen
    * @param [out] currentMin Stromwert des linken Punkts der linearen Beziehung (A)
    * @param [out] currentMax Stromwert des rechten Punkts der linearen Beziehung (A)
    * @param [out] outputVoltageMin Analogausgangsspannung des linken Punkts (V)
    * @param [out] outputVoltageMax Analogausgangsspannung des rechten Punkts (V)
    * @return Fehlercode
    */
    int WeldingGetCurrentRelation(ref double currentMin, ref double currentMax, ref double outputVoltageMin, ref double outputVoltageMax);

Beziehung zwischen Schweißspannung und Analogausgang abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Beziehung zwischen Schweißspannung und Analogausgang abrufen
    * @param [out] weldVoltageMin Spannungswert des linken Punkts der linearen Beziehung (A)
    * @param [out] weldVoltageMax Spannungswert des rechten Punkts der linearen Beziehung (A)
    * @param [out] outputVoltageMin Analogausgangsspannung des linken Punkts (V)
    * @param [out] outputVoltageMax Analogausgangsspannung des rechten Punkts (V)
    * @return Fehlercode
    */
    int WeldingGetVoltageRelation(ref double weldVoltageMin, ref double weldVoltageMax, ref double outputVoltageMin, ref double outputVoltageMax);

Schweißstrom einstellen
+++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißstrom einstellen
    * @param [in] ioType Steuerungs-I/O-Typ: 0-Steuerkasten-I/O; 1-Erweiterungs-I/O
    * @param [in] current Schweißstromwert (A)
    * @param [in] AOIndex Analogausgangsport des Steuerkastens für Schweißstrom (0-1)
    * @return Fehlercode
    */
    int WeldingSetCurrent(int ioType, double current, int AOIndex);

Schweißspannung einstellen
++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißspannung einstellen
    * @param [in] ioType Steuerungs-I/O-Typ: 0-Steuerkasten-I/O; 1-Erweiterungs-I/O
    * @param [in] voltage Schweißspannungswert (V)
    * @param [in] AOIndex Analogausgangsport des Steuerkastens für Schweißspannung (0-1)
    * @return Fehlercode
    */
    int WeldingSetVoltage(int ioType, double voltage, int AOIndex);

Pendelparameter einstellen
++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Pendelparameter einstellen
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter
    * @param [in] weaveType Pendeltyp: 0-Ebenen-Dreieck; 1-Vertikal-L-förmiges Dreieck; 2-Kreis im Uhrzeigersinn; 3-Kreis gegen Uhrzeigersinn; 4-Ebenen-Sinus; 5-Vertikal-L-förmiger Sinus; 6-Vertikales Dreieck; 7-Vertikaler Sinus
    * @param [in] weaveFrequency Pendelfrequenz (Hz)
    * @param [in] weaveIncStayTime Wartemodus: 0-Zyklus ohne Wartezeit; 1-Zyklus mit Wartezeit
    * @param [in] weaveRange Pendelamplitude (mm)
    * @param [in] weaveLeftRange Länge der linken Seite beim vertikalen Dreieckspendeln (mm)
    * @param [in] weaveRightRange Länge der rechten Seite beim vertikalen Dreieckspendeln (mm)
    * @param [in] additionalStayTime Verweilzeit am vertikalen Dreieckspunkt (ms)
    * @param [in] weaveLeftStayTime Verweilzeit links (ms)
    * @param [in] weaveRightStayTime Verweilzeit rechts (ms)
    * @param [in] weaveCircleRadio Rücklaufverhältnis für Kreispendeln (0-100%)
    * @param [in] weaveStationary Position während Wartezeit: 0-Position bewegt sich weiter; 1-Position ruht
    * @param [in] weaveYawAngle Azimutwinkel der Pendelrichtung (Rotation um die Pendel-Z-Achse) [°]
    * @return Fehlercode
    */
    int WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle = 0);

Codebeispiel zum Einstellen von Schweißparametern
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button7_Click(object sender, EventArgs e)
    {
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

        robot.WeldingGetProcessParam(1, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 1 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);
        robot.WeldingGetProcessParam(2, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 2 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);

        int rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
        Console.WriteLine("WeldingSetCurrentRelation rtn is: " + rtn);

        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
        Console.WriteLine("WeldingSetVoltageRelation rtn is: " + rtn);

        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        rtn = robot.WeldingGetCurrentRelation(ref current_min, ref current_max, ref output_vmin, ref output_vmax, ref curIndex);
        Console.WriteLine("WeldingGetCurrentRelation rtn is: " + rtn);
        Console.WriteLine("current min " + current_min + " current max " + current_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingGetVoltageRelation(ref vol_min, ref vol_max, ref output_vmin, ref output_vmax, ref volIndex);
        Console.WriteLine("WeldingGetVoltageRelation rtn is: " + rtn);
        Console.WriteLine("vol min " + vol_min + " vol max " + vol_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingSetCurrent(1, 100, 0, 0);
        Console.WriteLine("WeldingSetCurrent rtn is: " + rtn);

        System.Threading.Thread.Sleep(3000);

        rtn = robot.WeldingSetVoltage(1, 10, 0, 0);
        Console.WriteLine("WeldingSetVoltage rtn is: " + rtn);

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
        Console.WriteLine("rtn is: " + rtn);

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        Console.WriteLine("WeldingSetCheckArcInterruptionParam    " + rtn);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        Console.WriteLine("WeldingSetReWeldAfterBreakOffParam    " + rtn);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        rtn = robot.WeldingGetCheckArcInterruptionParam(ref checkEnable, ref arcInterruptTimeLength);
        Console.WriteLine("WeldingGetCheckArcInterruptionParam  checkEnable  " + checkEnable + "   arcInterruptTimeLength  " + arcInterruptTimeLength);
        rtn = robot.WeldingGetReWeldAfterBreakOffParam(ref enable, ref length, ref velocity, ref moveType);
        Console.WriteLine("WeldingGetReWeldAfterBreakOffParam  enable = " + enable + ", length = " + length + ", velocity = " + velocity + ", moveType = " + moveType);

        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            robot.SetWeldMachineCtrlMode(0);
            Thread.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            Thread.Sleep(1000);
        }
    }

Pendelparameter online einstellen
++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Pendelparameter online einstellen (während der Bewegung)
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter
    * @param [in] weaveType Pendeltyp (siehe WeaveSetPara)
    * @param [in] weaveFrequency Pendelfrequenz (Hz)
    * @param [in] weaveIncStayTime Wartemodus (siehe WeaveSetPara)
    * @param [in] weaveRange Pendelamplitude (mm)
    * @param [in] weaveLeftStayTime Verweilzeit links (ms)
    * @param [in] weaveRightStayTime Verweilzeit rechts (ms)
    * @param [in] weaveCircleRadio Rücklaufverhältnis für Kreispendeln (0-100%)
    * @param [in] weaveStationary Position während Wartezeit (siehe WeaveSetPara)
    * @return Fehlercode
    */
    int WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs beim Schweißen einstellen
    * @param [in] checkEnable Erkennung aktivieren? 0-nein; 1-ja
    * @param [in] arcInterruptTimeLength Bestätigungsdauer für Lichtbogenunterbrechung (ms)
    * @return Fehlercode
    */
    int WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs beim Schweißen abrufen
    * @param [out] checkEnable Erkennung aktiviert? 0-nein; 1-ja
    * @param [out] arcInterruptTimeLength Bestätigungsdauer für Lichtbogenunterbrechung (ms)
    * @return Fehlercode
    */
    int WeldingGetCheckArcInterruptionParam(ref int checkEnable, ref int arcInterruptTimeLength);

Parameter für die Wiederaufnahme nach Schweißunterbrechung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Parameter für die Wiederaufnahme nach Schweißunterbrechung einstellen
    * @param[in] enable Wiederaufnahme nach Unterbrechung aktivieren? 0-nein; 1-ja
    * @param[in] length Überlappungslänge der Schweißnaht (mm)
    * @param[in] velocity Geschwindigkeitsprozentsatz für die Rückkehr zum Wiederzündpunkt (0-100)
    * @param[in] moveType Bewegungsart zum Wiederzündpunkt: 0-LIN; 1-PTP
    * @return Fehlercode
    */
    int WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);

Parameter für die Wiederaufnahme nach Schweißunterbrechung abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Parameter für die Wiederaufnahme nach Schweißunterbrechung abrufen
    * @param [out] enable Wiederaufnahme aktiviert? 0-nein; 1-ja
    * @param [out] length Überlappungslänge der Schweißnaht (mm)
    * @param [out] velocity Geschwindigkeitsprozentsatz für die Rückkehr zum Wiederzündpunkt (0-100)
    * @param [out] moveType Bewegungsart zum Wiederzündpunkt: 0-LIN; 1-PTP
    * @return Fehlercode
    */
    int WeldingGetReWeldAfterBreakOffParam(ref int enable, ref double length, ref double velocity, ref int moveType);

Erweiterten DO-Port für Schweißgerät-Steuermodus einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweiterten DO-Port für Schweißgerät-Steuermodus einstellen
    * @param DONum DO-Portnummer für Schweißgerät-Steuermodus (0-127)
    * @return Fehlercode
    */
    int SetWeldMachineCtrlModeExtDoNum(int DONum);

Schweißmaschinen-Steuerungsmodus einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißmaschinen-Steuerungsmodus einstellen
    * @param [in] mode Schweißmaschinen-Steuerungsmodus; 0-Gleichstrom-Einknopf-Modus; 1-Impuls-Einknopf-Modus; 2-JOB-Modus; 3-Nahsteuerungs-Modus; 4-Separat-Modus; 5-CC/CV-Modus; 6-TIG; 7-CMT
    * @param [in] ioType Steuerungstyp; 0-Steuerkasten-IO; 1-Digitales Kommunikationsprotokoll (UDP); 2-Digitales Kommunikationsprotokoll (ModbusTCP)
    * @return Fehlercode
    */
    public int SetWeldMachineCtrlMode(int mode,int ioType = 1)

Schweißstart
++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißstart (Lichtbogen zünden)
    * @param [in] ioType I/O-Typ: 0-Steuerungs-I/O; 1-Erweiterungs-I/O
    * @param [in] arcNum Nummer der Schweißgeräte-Konfigurationsdatei
    * @param [in] timeout Lichtbogenstart-Timeout [ms]
    * @return Fehlercode
    */
    int ARCStart(int ioType, int arcNum, int timeout);

Schweißende
+++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißende (Lichtbogen löschen)
    * @param [in] ioType I/O-Typ: 0-Steuerungs-I/O; 1-Erweiterungs-I/O
    * @param [in] arcNum Nummer der Schweißgeräte-Konfigurationsdatei
    * @param [in] timeout Lichtbogenlösch-Timeout [ms]
    * @return Fehlercode
    */
    int ARCEnd(int ioType, int arcNum, int timeout);

Pendelstart
+++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Pendelstart
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter
    * @return Fehlercode
    */
    int WeaveStart(int weaveNum);

Pendelende
++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Pendelende
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter
    * @return Fehlercode
    */
    int WeaveEnd(int weaveNum);

Vorwärts-Drahtvorschub
++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Vorwärts-Drahtvorschub
    * @param [in] ioType I/O-Typ: 0-Steuerungs-I/O; 1-Erweiterungs-I/O
    * @param [in] wireFeed Drahtvorschubsteuerung: 0-stoppen; 1-vorschub
    * @return Fehlercode
    */
    int SetForwardWireFeed(int ioType, int wireFeed);

Rückwärts-Drahtvorschub
+++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Rückwärts-Drahtvorschub
    * @param [in] ioType I/O-Typ: 0-Steuerungs-I/O; 1-Erweiterungs-I/O
    * @param [in] wireFeed Drahtvorschubsteuerung: 0-stoppen; 1-vorschub
    * @return Fehlercode
    */
    int SetReverseWireFeed(int ioType, int wireFeed);

Gaszufuhr
+++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Gaszufuhr
    * @param [in] ioType I/O-Typ: 0-Steuerungs-I/O; 1-Erweiterungs-I/O
    * @param [in] airControl Gassteuerung: 0-stoppen; 1-zufuhr
    * @return Fehlercode
    */
    int SetAspirated(int ioType, int airControl);

Wiederaufnahme des Schweißens nach Unterbrechung starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Wiederaufnahme des Schweißens nach Unterbrechung starten
    * @return Fehlercode
    */
    int WeldingStartReWeldAfterBreakOff();

Schweißen nach Unterbrechung abbrechen
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißen nach Unterbrechung abbrechen (nicht wiederaufnehmen)
    * @return Fehlercode
    */
    int WeldingAbortWeldAfterBreakOff();

Codebeispiel (Schweißablauf)
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button7_Click(object sender, EventArgs e)
    {
        robot.WeldingSetCurrent(1, 230, 0, 0);
        robot.WeldingSetVoltage(1, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ARCStart(1, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL (p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.ARCEnd(1, 0, 10000);
        robot.WeaveEnd(0);
    }

Segment-Schweißen starten
+++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Segment-Schweißen starten (Heftschweißen / Intervallschweißen)
    * @param [in] startDesePos Kartesische Position des Startpunkts
    * @param [in] endDesePos Kartesische Pose des Endpunkts
    * @param [in] startJPos Gelenkpose des Startpunkts
    * @param [in] endJPos Gelenkpose des Endpunkts
    * @param [in] weldLength Länge des Schweißsegments (mm)
    * @param [in] noWeldLength Länge des Nicht-Schweißsegments (mm)
    * @param [in] weldIOType Schweiß-I/O-Typ (0-Steuerkasten-I/O; 1-Erweiterungs-I/O)
    * @param [in] arcNum Nummer der Schweißgeräte-Konfigurationsdatei
    * @param [in] weldTimeout Lichtbogenstart/-lösch-Timeout [ms]
    * @param [in] isWeave Pendeln verwenden? true/false
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter
    * @param [in] tool Werkzeugnummer
    * @param [in] user Werkstücknummer
    * @param [in] vel Geschwindigkeitsprozentsatz [0~100]
    * @param [in] acc Beschleunigungsprozentsatz [0~100] (vorübergehend nicht freigegeben)
    * @param [in] ovl Geschwindigkeitsskalierungsfaktor [0~100]
    * @param [in] blendR [-1.0]-Bewegung abschließen (blockierend), [0~1000.0]-Glättungsradius (nicht blockierend) [mm]
    * @param [in] epos Position der Erweiterungsachse [mm]
    * @param [in] search 0-keine Schweißdrahtsuche, 1-Schweißdrahtsuche
    * @param [in] offset_flag 0-kein Versatz, 1-Versatz im Basis-/Werkstückkoordinatensystem, 2-Versatz im Werkzeugkoordinatensystem
    * @param [in] offset_pos Posenversatz
    * @return Fehlercode
    */
    int SegmentWeldStart(DescPose startDesePos, DescPose endDesePos, JointPos startJPos, JointPos endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout, bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, byte search, byte offset_flag, DescPose offset_pos);

Codebeispiel für Robotersegment-Schweißen
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    private void btnWeldStart_Click(object sender, EventArgs e)
    {
        robot.WeldingSetCurrent(1, 230, 0, 0);
        robot.WeldingSetVoltage(1, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        int rtn = robot.SegmentWeldStart( p1Desc,  p2Desc,  p1Joint,  p2Joint, 20, 20, 0, 0, 5000, false, 0, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        Console.WriteLine("SegmentWeldStart rtn is {0}", rtn);
    }

Simulations-Pendelstart
+++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Simulations-Pendelstart (nur Visualisierung, keine I/O)
    * @param [in] weaveNum Pendelparameternummer
    * @return Fehlercode
    */
    int WeaveStartSim(int weaveNum);

Simulations-Pendelende
++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Simulations-Pendelende
    * @param [in] weaveNum Pendelparameternummer
    * @return Fehlercode
    */
    int WeaveEndSim(int weaveNum);

Trajektorienprüfungs-Warnung starten (ohne Bewegung)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Trajektorienprüfungs-Warnung starten (ohne Bewegung)
    * @param [in] weaveNum Pendelparameternummer
    * @return Fehlercode
    */
    int WeaveInspectStart(int weaveNum);

Trajektorienprüfungs-Warnung beenden
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Trajektorienprüfungs-Warnung beenden
    * @param [in] weaveNum Pendelparameternummer
    * @return Fehlercode
    */
    int WeaveInspectEnd(int weaveNum);

Pendel-Gradientenstart (allmähliche Änderung)
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Pendel-Gradientenstart (allmähliche Änderung der Parameter)
    * @param [in] weaveChangeFlag 1-nur Pendelparameter ändern; 2-Pendelparameter + Schweißgeschwindigkeit ändern
    * @param [in] weaveNum Pendelnummer
    * @param [in] velStart Start-Schweißgeschwindigkeit (cm/min)
    * @param [in] velEnd End-Schweißgeschwindigkeit (cm/min)
    * @return Fehlercode
    */
    int WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Pendel-Gradientenende
+++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Pendel-Gradientenende
    * @return Fehlercode
    */
    int WeaveChangeEnd();

Codebeispiel für robotergestütztes Gradienten-Pendelschweißen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    private void btnweld_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveStartSim(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.WeaveEndSim(0);
        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveInspectStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.WeaveInspectEnd(0);

        robot.WeldingSetVoltage(1, 19, 0, 0);
        robot.WeldingSetCurrent(1, 190, 0, 0);
        robot.MoveL( p1Joint,  p1Desc, 1, 1, 100, 100, 50, -1,  exaxisPos, 0, 0,  offdese);
        robot.ARCStart(1, 0, 10000);
        robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(1, 0, 50, 30);
        robot.MoveL( p2Joint,  p2Desc, 1, 1, 100, 100, 1, -1,  exaxisPos, 0, 0,  offdese);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.ARCEnd(1, 0, 10000);
    }

Erweitertes I/O - Gasprüfsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweitertes I/O - Gasprüfsignal für Schweißgerät konfigurieren
    * @param [in] DONum Erweiterte DO-Nummer für Gasprüfsignal
    * @return Fehlercode
    */
    int SetAirControlExtDoNum(int DONum);

Erweitertes I/O - Lichtbogenstartsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweitertes I/O - Lichtbogenstartsignal für Schweißgerät konfigurieren
    * @param [in] DONum Erweiterte DO-Nummer für Lichtbogenstartsignal
    * @return Fehlercode
    */
    int SetArcStartExtDoNum(int DONum);

Erweitertes I/O - Rückwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweitertes I/O - Rückwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
    * @param [in] DONum Erweiterte DO-Nummer für Rückwärts-Drahtvorschubsignal
    * @return Fehlercode
    */
    int SetWireReverseFeedExtDoNum(int DONum);

Erweitertes I/O - Vorwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweitertes I/O - Vorwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
    * @param [in] DONum Erweiterte DO-Nummer für Vorwärts-Drahtvorschubsignal
    * @return Fehlercode
    */
    int SetWireForwardFeedExtDoNum(int DONum);

Erweitertes I/O - Lichtbogen-Erfolgssignal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweitertes I/O - Lichtbogen-Erfolgssignal für Schweißgerät konfigurieren
    * @param [in] DINum Erweiterte DI-Nummer für Lichtbogen-Erfolgssignal
    * @return Fehlercode
    */
    int SetArcDoneExtDiNum(int DINum);

Erweitertes I/O - Bereitschaftssignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweitertes I/O - Bereitschaftssignal für Schweißgerät konfigurieren
    * @param [in] DINum Erweiterte DI-Nummer für Bereitschaftssignal
    * @return Fehlercode
    */
    int SetWeldReadyExtDiNum(int DINum);

Erweitertes I/O - Signale für Wiederaufnahme nach Schweißunterbrechung konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweitertes I/O - Signale für Wiederaufnahme nach Schweißunterbrechung konfigurieren
    * @param [in] reWeldDINum Erweiterte DI-Nummer für "Wiederaufnahme starten"
    * @param [in] abortWeldDINum Erweiterte DI-Nummer für "Wiederaufnahme abbrechen"
    * @return Fehlercode
    */
    int SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Codebeispiel zum Einstellen erweiterter I/O-Schweißsignale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button51_Click(object sender, EventArgs e)
    {
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);

        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);
    }

Lichtbogenverfolgungssteuerung (Arc Tracking)
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Lichtbogenverfolgungssteuerung (Arc Tracking)
    * @param [in] flag Schalter: 0-aus; 1-an
    * @param [in] delayTime Verzögerungszeit [ms]
    * @param [in] isLeftRight Links-Rechts-Abweichungskompensation aktivieren? 0/1
    * @param [in] klr Links-Rechts-Regelkoeffizient (Empfindlichkeit)
    * @param [in] tStartLr Startzeit für Links-Rechts-Kompensation [Zyklen]
    * @param [in] stepMaxLr Maximale Schrittweite Links-Rechts [mm]
    * @param [in] sumMaxLr Maximale Gesamtkompensation Links-Rechts [mm]
    * @param [in] isUpLow Oben-Unten-Abweichungskompensation aktivieren? 0/1
    * @param [in] kud Oben-Unten-Regelkoeffizient (Empfindlichkeit)
    * @param [in] tStartUd Startzeit für Oben-Unten-Kompensation [Zyklen]
    * @param [in] stepMaxUd Maximale Schrittweite Oben-Unten [mm]
    * @param [in] sumMaxUd Maximale Gesamtkompensation Oben-Unten [mm]
    * @param [in] axisSelect Koordinatensystem für Oben-Unten: 0-Pendel; 1-Werkzeug; 2-Basis
    * @param [in] referenceType Einstellungsart des Referenzstroms (Oben-Unten): 0-Rückmeldung; 1-Konstante
    * @param [in] referSampleStartUd Startzähler für Abtastung des Referenzstroms (nur bei Rückmeldung) [Zyklen]
    * @param [in] referSampleCountUd Anzahl der Abtastzyklen für Referenzstrom (nur bei Rückmeldung) [Zyklen]
    * @param [in] referenceCurrent Konstanter Referenzstrom (nur bei referenceType=1) [mA]
    * @param [in] offsetType Versatz-Tracking-Typ: 0-kein Versatz; 1-Abtastung; 2-Prozentsatz (ab Version 3.7.9)
    * @param [in] offsetParameter Versatzparameter: bei Abtastung (Startzeit der Versatzabtastung, standardmäßig ein Zyklus); bei Prozentsatz (Versatzprozentsatz (-100 ~ 100)) (ab Version 3.7.9)
    * @return Fehlercode
    */
    int ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType, int offsetParameter);

AI-Kanalwahl für Lichtbogenverfolgung
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief AI-Kanalwahl für Lichtbogenverfolgung (Strom-/Spannungsrückmeldung)
    * @param [in] channel AI-Kanal [0-3] (wahrscheinlich erweiterte AI)
    * @return Fehlercode
    */
    int ArcWeldTraceExtAIChannelConfig(int channel);

Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung starten
    * @return Fehlercode
    */
    int ArcWeldTraceReplayStart();

Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung beenden
    * @return Fehlercode
    */
    int ArcWeldTraceReplayEnd();

Koordinatentransformation für Versatz (Mehrlagenschweißen)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
     * @brief Koordinatentransformation für Versatz (Mehrlagenschweißen)
     * @param [in] pointO Kartesische Pose des Basispunkts
     * @param [in] pointX Kartesische Pose eines Punkts in X-Richtung (zur Definition der X-Achse)
     * @param [in] pointZ Kartesische Pose eines Punkts in Z-Richtung (zur Definition der Z-Achse)
     * @param [in] dx Versatz in X-Richtung (mm)
     * @param [in] dy Versatz in Y-Richtung (mm)
     * @param [in] db Rotation um Y-Achse (°)
     * @param [out] offset Berechneter Versatz (Pose)
     * @return Fehlercode
     */
    int MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, ref DescPose offset);

Codebeispiel für Lichtbogenverfolgung mit Mehrlagenschweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    private void button52_Click(object sender, EventArgs e)
    {
        JointPos mulitilineorigin1_joint = new JointPos(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
        DescPose mulitilineorigin1_desc = new DescPose(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);

        DescTran mulitilineX1_desc = new DescTran();
        mulitilineX1_desc.x = -677.556;
        mulitilineX1_desc.y = 211.949;
        mulitilineX1_desc.z = -1.206;

        DescTran mulitilineZ1_desc = new DescTran();
        mulitilineZ1_desc.x = -677.564;
        mulitilineZ1_desc.y = 190.956;
        mulitilineZ1_desc.z = 19.817;

        JointPos mulitilinesafe_joint = new JointPos(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
        DescPose mulitilinesafe_desc = new DescPose(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
        JointPos mulitilineorigin2_joint = new JointPos(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
        DescPose mulitilineorigin2_desc = new DescPose(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);

        DescTran mulitilineX2_desc = new DescTran();
        mulitilineX2_desc.x = -563.965;
        mulitilineX2_desc.y = 220.355;
        mulitilineX2_desc.z = -0.680;

        DescTran mulitilineZ2_desc = new DescTran();
        mulitilineZ2_desc.x = -563.968;
        mulitilineZ2_desc.y = 215.362;
        mulitilineZ2_desc.z = 4.331;

        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset = new DescPose(0, 0, 0, 0, 0, 0);

        Thread.Sleep(10);
        int error = robot.MoveJ( mulitilinesafe_joint,  mulitilinesafe_desc, 13, 0, 10, 100, 100,  epos, -1, 0,  offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.WeaveStart(0);
        Console.WriteLine("WeaveStart return: {0}", error);

        error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
        Console.WriteLine("ArcWeldTraceControl return: {0}", error);

        error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
        Console.WriteLine("ArcWeldTraceControl return: {0}", error);

        error = robot.WeaveEnd(0);
        Console.WriteLine("WeaveEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 10000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.ArcWeldTraceReplayStart();
        Console.WriteLine("ArcWeldTraceReplayStart return: {0}", error);

        error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceReplayEnd();
        Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 10000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.ArcWeldTraceReplayStart();
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 1, 2, 100, 100, -1, epos, 1, 1, offset, 1, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceReplayEnd();
        Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 3000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);
    }

AI-Kanalwahl für Lichtbogenverfolgung (Strom)
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief AI-Kanalwahl für Lichtbogenverfolgung (Stromrückmeldung)
    * @param [in] channel Kanal: 0-Erw. AI0; 1-Erw. AI1; 2-Erw. AI2; 3-Erw. AI3; 4-Steuerkasten AI0; 5-Steuerkasten AI1
    * @return Fehlercode
    */
    int ArcWeldTraceAIChannelCurrent(int channel);

AI-Kanalwahl für Lichtbogenverfolgung (Spannung)
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief AI-Kanalwahl für Lichtbogenverfolgung (Spannungsrückmeldung)
    * @param [in] channel Kanal: 0-Erw. AI0; 1-Erw. AI1; 2-Erw. AI2; 3-Erw. AI3; 4-Steuerkasten AI0; 5-Steuerkasten AI1
    * @return Fehlercode
    */
    int ArcWeldTraceAIChannelVoltage(int channel);

Umrechnungsparameter für Stromrückmeldung (Lichtbogenverfolgung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Umrechnungsparameter für Stromrückmeldung (Lichtbogenverfolgung)
    * @param [in] AILow Untere Grenze des AI-Kanals (Spannung), Standard 0V, Bereich [0-10V]
    * @param [in] AIHigh Obere Grenze des AI-Kanals (Spannung), Standard 10V, Bereich [0-10V]
    * @param [in] currentLow Schweißstromwert für untere AIGrenze, Standard 0A, Bereich [0-200A]? (Dokument sagt 0-200V, wahrscheinlich A)
    * @param [in] currentHigh Schweißstromwert für obere AIGrenze, Standard 100A, Bereich [0-200A]?
    * @return Fehlercode
    */
    public int ArcWeldTraceCurrentPara(double AILow, double AIHigh, double currentLow, double currentHigh)

Umrechnungsparameter für Spannungsrückmeldung (Lichtbogenverfolgung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Umrechnungsparameter für Spannungsrückmeldung (Lichtbogenverfolgung)
    * @param [in] AILow Untere Grenze des AI-Kanals (Spannung), Standard 0V, Bereich [0-10V]
    * @param [in] AIHigh Obere Grenze des AI-Kanals (Spannung), Standard 10V, Bereich [0-10V]
    * @param [in] voltageLow Schweißspannungswert für untere AIGrenze, Standard 0V, Bereich [0-200V]
    * @param [in] voltageHigh Schweißspannungswert für obere AIGrenze, Standard 100V, Bereich [0-200V]
    * @return Fehlercode
    */
    public int ArcWeldTraceVoltagePara(double AILow, double AIHigh, double voltageLow, double voltageHigh)

Codebeispiel für Lichtbogenverfolgung
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button8_Click(object sender, EventArgs e)
    {
        DescPose startdescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
        JointPos startjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

        DescPose enddescPose = new DescPose(441.901, 615.317, -51.979, -179.234, 0.718, -115.305);
        JointPos endjointPos = new JointPos(-133.22, -44.193, 74.934, -121.661, -90.509, 72.087);

        DescPose safetydescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
        JointPos safetyjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

        robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
        robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);
        robot.WeldingSetVoltage(0, 25, 1, 0); 
        robot.WeldingSetCurrent(0, 260, 0, 0); 

        int rtn = robot.ArcWeldTraceAIChannelCurrent(4);
        Console.WriteLine("ArcWeldTraceAIChannelCurrent rtn is " + rtn);
        rtn = robot.ArcWeldTraceAIChannelVoltage(5);
        Console.WriteLine("ArcWeldTraceAIChannelVoltage rtn is " + rtn);
        rtn = robot.ArcWeldTraceCurrentPara((double)0, (double)5, (double)0, (double)500);
        Console.WriteLine("ArcWeldTraceCurrentPara rtn is " + rtn);
        rtn = robot.ArcWeldTraceVoltagePara((double)1.018, (double)10, (double)0, (double)50);
        Console.WriteLine("ArcWeldTraceVoltagePara rtn is " + rtn);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0,exaxisPos, 0, 0, offdese);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

    }

Erweiterte I/O-Ports für Schweißdrahtsuche einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Erweiterte I/O-Ports für Schweißdrahtsuche einstellen
    * @param searchDoneDINum Erweiterte DI-Nummer für "Drahtsuche erfolgreich" (Eingang)
    * @param searchStartDONum Erweiterte DO-Nummer für "Drahtsuche Start/Stopp" (Ausgang)
    * @return Fehlercode
    */
    int SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Schweißdrahtsuche starten
+++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißdrahtsuche starten
    * @param [in] refPos 1-Referenzpunkt; 0-Kontaktpunkt (vermutlich)
    * @param [in] searchVel Suchgeschwindigkeit [%]
    * @param [in] searchDis Suchdistanz [mm]
    * @param [in] autoBackFlag Automatische Rückkehr-Flag: 0-nicht automatisch; 1-automatisch
    * @param [in] autoBackVel Geschwindigkeit der automatischen Rückkehr [%]
    * @param [in] autoBackDis Distanz der automatischen Rückkehr [mm]
    * @param [in] offectFlag 1-Suche mit Versatz; 0-Suche an Teachpunkt
    * @return Fehlercode
    */
    int WireSearchStart(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Schweißdrahtsuche beenden
+++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißdrahtsuche beenden
    * @param [in] refPos 1-Referenzpunkt; 2-Kontaktpunkt (vermutlich)
    * @param [in] searchVel Suchgeschwindigkeit [%]
    * @param [in] searchDis Suchdistanz [mm]
    * @param [in] autoBackFlag Automatische Rückkehr-Flag: 0-nicht automatisch; 1-automatisch
    * @param [in] autoBackVel Geschwindigkeit der automatischen Rückkehr [%]
    * @param [in] autoBackDis Distanz der automatischen Rückkehr [mm]
    * @param [in] offectFlag 1-Suche mit Versatz; 2-Suche an Teachpunkt (vermutlich)
    * @return Fehlercode
    */
    int WireSearchEnd(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Schweißdrahtsuch-Versatz berechnen
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißdrahtsuch-Versatz berechnen
    * @param [in] seamType Schweißnahttyp
    * @param [in] method Berechnungsmethode
    * @param [in] varNameRef Array mit Namen der Referenzpunkte (1-6), "#" für keinen Punkt
    * @param [in] varNameRes Array mit Namen der Kontaktpunkte (1-6), "#" für keinen Punkt
    * @param [out] offsetFlag 0-Versatz direkt zum Befehlspunkt addieren; 1-Versatz erfordert Koordinatentransformation des Befehlspunkts
    * @param [out] offset Berechneter Versatz [x, y, z, a, b, c]
    * @return Fehlercode
    */
    int GetWireSearchOffset(int seamType, int method, string[] varNameRef, string[] varNameRes, ref int offsetFlag, ref DescPose offset);

Auf Abschluss der Schweißdrahtsuche warten
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Auf Abschluss der Schweißdrahtsuche warten
    * @param [in] name Name der Suche/Variable (vermutlich)
    * @return Fehlercode
    */
    int WireSearchWait(string name);

Schweißdrahtsuch-Kontaktpunkt in Datenbank schreiben
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißdrahtsuch-Kontaktpunkt in Datenbank schreiben
    * @param [in] varName Name des Kontaktpunkts (z.B. "RES0" bis "RES99")
    * @param [in] pos Kontaktpunktdaten [x, y, z, a, b, c]
    * @return Fehlercode
    */
    int SetPointToDatabase(string varName, DescPose pos);

Codebeispiel für robotergestützte Schweißdrahtsuche
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button53_Click(object sender, EventArgs e)
    {
        DescPose toolCoord = new DescPose(0, 0, 200, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);
        DescPose wobjCoord = new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetWObjCoord(1, wobjCoord, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose descStart = new DescPose(216.543, 445.175, 93.465, 179.683, 1.757, -112.641);
        JointPos jointStart = new JointPos(-128.345, -86.660, 114.679, -119.625, -89.219, 74.303);

        DescPose descEnd = new DescPose(111.143, 523.384, 87.659, 179.703, 1.835, -97.750);
        JointPos jointEnd = new JointPos(-113.454, -81.060, 109.328, -119.954, -89.218, 74.302);

        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);

        DescPose descREF0A = new DescPose(142.135, 367.604, 86.523, 179.728, 1.922, -111.089);
        JointPos jointREF0A = new JointPos(-126.794, -100.834, 128.922, -119.864, -89.218, 74.302);

        DescPose descREF0B = new DescPose(254.633, 463.125, 72.604, 179.845, 2.341, -114.704);
        JointPos jointREF0B = new JointPos(-130.413, -81.093, 112.044, -123.163, -89.217, 74.303);

        DescPose descREF1A = new DescPose(92.556, 485.259, 47.476, -179.932, 3.130, -97.512);
        JointPos jointREF1A = new JointPos(-113.231, -83.815, 119.877, -129.092, -89.217, 74.303);

        DescPose descREF1B = new DescPose(203.103, 583.836, 63.909, 179.991, 2.854, -103.372);
        JointPos jointREF1B = new JointPos(-119.088, -69.676, 98.692, -121.761, -89.219, 74.303);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  // Startpunkt
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  // Richtungspunkt
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  // Startpunkt
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  // Richtungspunkt
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  // Startpunkt
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  // Richtungspunkt
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  // Startpunkt
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  // Richtungspunkt
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        string[] varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
        string[] varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
        int offectFlag = 0;
        DescPose offectPos = new DescPose(0, 0, 0, 0, 0, 0);
        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, ref offectFlag, ref offectPos);
        robot.PointsOffsetEnable(0, offectPos);
        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);
        robot.PointsOffsetDisable();
    }

Schweißspannungsgradienten starten
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißspannungsgradienten starten (allmähliche Änderung)
    * @param [in] IOType Steuerungstyp: 0-Steuerkasten-I/O; 1-Digitalkommunikation (UDP); 2-Digitalkommunikation (ModbusTCP)
    * @param [in] voltageStart Start-Schweißspannung (V)
    * @param [in] voltageEnd End-Schweißspannung (V)
    * @param [in] AOIndex AO-Portnummer des Steuerkastens (0-1)
    * @param [in] blend Glättung? 0-nein; 1-ja
    * @return Fehlercode
    */
    int WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Schweißspannungsgradienten beenden
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißspannungsgradienten beenden
    * @return Fehlercode
    */
    int WeldingSetVoltageGradualChangeEnd();

Schweißstromgradienten starten
+++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißstromgradienten starten (allmähliche Änderung)
    * @param [in] IOType Steuerungstyp: 0-Steuerkasten-I/O; 1-Digitalkommunikation (UDP); 2-Digitalkommunikation (ModbusTCP)
    * @param [in] currentStart Start-Schweißstrom (A)
    * @param [in] currentEnd End-Schweißstrom (A)
    * @param [in] AOIndex AO-Portnummer des Steuerkastens (0-1)
    * @param [in] blend Glättung? 0-nein; 1-ja
    * @return Fehlercode
    */
    int WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Schweißstromgradienten beenden
+++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    /**
    * @brief Schweißstromgradienten beenden
    * @return Fehlercode
    */
    int WeldingSetCurrentGradualChangeEnd();

Codebeispiel für Schweißstrom- und Spannungsgradienten
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3 Web-3.8.2

.. code-block:: c#
    :linenos:

    private void btnweld_Click(object sender, EventArgs e)
    {
        DescPose startdescPose = new DescPose(-319.303, -240.689, 116.379, -175.879, -0.337, 148.239);
        JointPos startjointPos = new JointPos(20.474, -103.554, 126.774, -116.682, -87.746, -37.709);

        DescPose enddescPose = new DescPose(-454.166, -327.159, 62.217, 177.199, -2.276, 154.955);
        JointPos endjointPos = new JointPos(27.176, -74.423, 104.557, -119.315, -93.514, -37.698);

        DescPose safedescPose = new DescPose(-375.533, -543.319, 19.798, 177.486, -2.489, 175.825);
        JointPos safejointPos = new JointPos(48.074, -59.714, 89.955, -119.777, -93.508, -37.683);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
        robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);

        robot.WeldingSetVoltage(0, 25, 1, 0);//
        robot.WeldingSetCurrent(0, 260, 0, 0);// 

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        int rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
        Console.WriteLine($"WeldingSetCurrentGradualChangeStart rtn is {rtn}");
        rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
        Console.WriteLine($"WeldingSetVoltageGradualChangeStart rtn is {rtn}");

        rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        Console.WriteLine($"ArcWeldTraceControl rtn is {rtn}");

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        rtn = robot.WeaveChangeStart(2, 1, 24, 36);
        Console.WriteLine($"WeaveChangeStart rtn is {rtn}");
        //robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, exaxisPos, 0, 0, offdese);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.WeldingSetCurrentGradualChangeEnd();
        robot.WeldingSetVoltageGradualChangeEnd();
    }

Benutzerdefinierte Pendelparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Benutzerdefinierte Pendelparameter einstellen
     * @param [in] id Benutzerdefinierte Pendelnummer: 0-2
     * @param [in] pointNum Anzahl der Pendelpunkte 0-10
     * @param [in] points Array der Bewegungspunkte (x, y, z) relativ zum Pfad
     * @param [in] stayTimes Array der Verweilzeiten an den Punkten [ms]
     * @param [in] frequency Pendelfrequenz [Hz]
     * @param [in] incStayType Wartemodus: 0-Zyklus ohne Wartezeit; 1-Zyklus mit Wartezeit
     * @param [in] stationary Position während Wartezeit: 0-Bewegung wird fortgesetzt; 1-Position ruht
     * @return Fehlercode
     */
    int CustomWeaveSetPara(int id, int pointNum, DescTran[] points, double[] stayTimes, double frequency, int incStayType, int stationary);

Benutzerdefinierte Pendelparameter abrufen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Benutzerdefinierte Pendelparameter abrufen
     * @param [in] id Benutzerdefinierte Pendelnummer: 0-2
     * @param [out] pointNum Anzahl der Pendelpunkte
     * @param [out] points Array der Bewegungspunkte
     * @param [out] stayTimes Array der Verweilzeiten
     * @param [out] frequency Pendelfrequenz [Hz]
     * @param [out] incStayType Wartemodus
     * @param [out] stationary Position während Wartezeit
     * @return Fehlercode
     */
    int CustomWeaveGetPara(int id, ref int pointNum, ref DescTran[] points, ref double[] stayTimes, ref double frequency, ref int incStayType, ref int stationary);

Codebeispiel für benutzerdefinierte Pendelparameter
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8 Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestCoordMain5()
    {
        DescTran[] points = new DescTran[10];
        for (int i = 0; i < 10; i++)
        {
            points[i] = new DescTran();
        }
        points[0].x = -3;
        points[0].y = -3;
        points[0].z = 0;
        points[1].x = -6;
        points[1].y = 0;
        points[1].z = 0;
        points[2].x = -3;
        points[2].y = 3;
        points[2].z = 0;
        points[3].x = 0;
        points[3].y = 0;
        points[3].z = 0;
        double[] stayTimes = new double[10] { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
        int rtn = robot.CustomWeaveSetPara(2, 4, points, stayTimes, 1.000, 0, 0);
        Console.WriteLine($"CustomWeaveSetPara rtn is {rtn}");
        System.Threading.Thread.Sleep(1000);
        int pointNum = 0;
        double frequency = 0;
        int incStayType = 0;
        int stationary = 0;
        rtn = robot.CustomWeaveGetPara(2, ref pointNum, ref points, ref stayTimes, ref frequency, ref incStayType, ref stationary);
        Console.WriteLine($"pointNum is {pointNum}");
        for (int i = 0; i < pointNum; i++)
        {
            Console.WriteLine($"point {i}, point x y z {points[i].x:F6} {points[i].y:F6} {points[i].z:F6}");
        }
        Console.WriteLine($"fre is {frequency:F6}, stay is {incStayType} {stationary}");
        robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
        DescPose desc_p1 = new DescPose(-288.650, 367.807, 288.404, 0.000, -0.001, 0.001);
        DescPose desc_p2 = new DescPose(-431.714, 367.815, 288.415, 0.001, 0.001, 0.000);    
        DescPose desc_p3 = new DescPose(-348.666, 427.798, 288.404, -0.000, -0.000, 0.001);
        JointPos j1 = new JointPos(140.656,  -84.560,  -91.707, -93.734,  90.000,50.655 );
        JointPos j2 = new JointPos ( 149.873, -98.298, -77.599,  -94.103,  90.000,  59.873 );
        JointPos j3 = new JointPos (139.773,  -96.173, -80.014,  -93.814,  90.000,  49.772 );
        ExaxisPos epos = new ExaxisPos(0,0,0,0);
        DescPose offset_pos = new DescPose(0,0,0,0,0,0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.Circle(j3, desc_p3, 3, 0, 100, 100, epos, j2, desc_p2, 3, 0, 100, 100, epos, 10, -1, offset_pos, 100, -1, 0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveC(j3, desc_p3, 3, 0, 100, 100, epos, 0, offset_pos, j2, desc_p2, 3, 0, 100, 100, epos, 0, offset_pos, 10, -1, 0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveL(j2, desc_p2, 3, 0, 100, 100, 10, -1, epos, 0, 0, offset_pos, 0, 0, 10);
        robot.WeaveEnd(0);
    }

Konfiguration der Laserschweißgerät-Parameter
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Schreibt die Konfigurationsparameter für eine der 10 Prozessgruppen des Laserschweißgeräts und konfiguriert das Schweißgerät
    * @param[in] io_type Kommunikationstyp 0-IO 1-UDP
    * @param[in] num Gruppennummer, die eingestellt werden soll (1~10)
    * @param[in] scanSpeed Scangeschwindigkeit
    * @param[in] scanWidth Scanbreite
    * @param[in] peakPower Spitzenleistung
    * @param[in] dutyCycle Tastverhältnis
    * @param[in] freq Frequenz
    * @return Fehlercode
    */
    public int SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq)

Laserschweißen Start/Stopp einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Laserschweißgerät ein-/ausschalten
    * @param[in] io_type Kommunikationstyp 0-IO 1-UDP
    * @param[in] status Steuerwort 0-Laser aus 1-Laser an
    * @param[in] max_waittime Maximale Wartezeit
    * @return Fehlercode
    */
    public int SetLaserWeldingStartEnd(int io_type, int status, int max_waittime)

Laserschweißgerät aktivieren/deaktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Laserschweißgerät aktivieren/deaktivieren
    * @param[in] io_type Kommunikationstyp 0-IO 1-UDP
    * @param[in] status 0-deaktivieren 1-aktivieren
    * @return Fehlercode
    */
    public int SetLaserWeldingEnable(int io_type, int status)

Laserschweißgerät-Fehler zurücksetzen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Fehler des Laserschweißgeräts zurücksetzen
    * @param[in] io_type Kommunikationstyp 0-IO 1-UDP
    * @param[in] status Steuerwort 0-ungültig 1-Fehler zurücksetzen
    * @return Fehlercode
    */
    public int ResetLaserWeldingErr(int io_type, int status)

Laserschweißgerät-Betriebsstatus abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Betriebsstatus des Laserschweißgeräts abrufen
    * @param[in] io_type Kommunikationstyp 0-IO 1-UDP
    * @param[out] status Steuerwort 0-gestoppt 1-läuft
    * @return Fehlercode
    */
    public int GetLaserWeldingRunningState(int io_type, ref int status)

Laserschweißgerät-Fehlerstatus abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Fehlerstatus des Laserschweißgeräts abrufen
    * @param[in] io_type Kommunikationstyp 0-IO 1-UDP
    * @param[out] status 0-kein Fehler 1-Fehler vorhanden
    * @return Fehlercode
    */
    public int GetLaserWeldingErrState(int io_type, ref int status)

Konfigurierte Parameter des Laserschweißgeräts abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Konfigurationsparameter für eine der 10 Prozessgruppen des Laserschweißgeräts abrufen
    * @param[in] num Gruppennummer, die eingestellt werden soll (1~10)
    * @param[out] scanSpeed Scangeschwindigkeit
    * @param[out] scanWidth Scanbreite
    * @param[out] peakPower Spitzenleistung
    * @param[out] dutyCycle Tastverhältnis
    * @param[out] freq Frequenz
    * @return Fehlercode
    */
    public int GetLaserWeldingParamTarget(int num, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)

Aktuell aktive Konfigurationsparameter des Laserschweißgeräts abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Die aktuell aktiven Konfigurationsparameter des Laserschweißgeräts abrufen
    * @param[in] io_type Kommunikationstyp 0-IO 1-UDP
    * @param[out] scanSpeed Scangeschwindigkeit
    * @param[out] scanWidth Scanbreite
    * @param[out] peakPower Spitzenleistung
    * @param[out] dutyCycle Tastverhältnis
    * @param[out] freq Frequenz
    * @return Fehlercode
    */
    public int GetLaserWeldingParamActual(int io_type, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)
    
Erweiterte IO-Aktivierungs-DO-Port des Laserschweißgeräts konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Erweiterte IO der Laserschweißgeräts einstellen, Aktivierungs-DO-Port
    * @param[in] ctrlModeDONum Erweiterte DO-Portnummer für die Aktivierung des Laserschweißgeräts
    * @return Fehlercode
    */
    public int SetLaserWeldingEnableExtDoNum(int ctrlModeDONum)

Erweiterte IO-Start-DO-Port des Laserschweißgeräts konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Erweiterte IO der Laserschweißgeräts einstellen, Start-DO-Port
    * @param[in] ctrlModeDONum Erweiterte DO-Portnummer für den Start (Laser an/aus) des Laserschweißgeräts
    * @return Fehlercode
    */
    public int SetLaserWeldingStartExtDoNum(int ctrlModeDONum)

Erweiterte IO-Fehlerrücksetzungs-DO-Port des Laserschweißgeräts konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Erweiterte IO der Laserschweißgeräts einstellen, Fehlerrücksetzungs-DO-Port
    * @param[in] ctrlModeDONum Erweiterte DO-Portnummer für die Fehlerrücksetzung des Laserschweißgeräts
    * @return Fehlercode
    */
    public int SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum)

Erweiterte DI für Betriebsstatus (Laser an-Status) des Laserschweißgeräts konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Erweiterte DI für den Betriebsstatus (Laser an-Status) des Laserschweißgeräts konfigurieren
    * @param[in] diNum Erweiterte DI-Portnummer für den Betriebsstatus (Laser an-Status) des Laserschweißgeräts
    * @return Fehlercode
    */
    public int SetLaserWeldingRunningStateExtDiNum(int diNum)
    
Erweiterte IO-Fehlerstatus-DI-Port des Laserschweißgeräts konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Erweiterte DI für den Fehlerstatus des Laserschweißgeräts konfigurieren
    * @param[in] diNum Erweiterte DI-Portnummer für den Fehlerstatus des Laserschweißgeräts
    * @return Fehlercode
    */
    public int SetLaserWeldingErrStateExtDiNum(int diNum)
        
Laserschweiß-Codebeispiel
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    private void btnLaserWeld_Click(object sender, EventArgs e)
    {

        int rtn = -1;
        // UDP-Treiber laden
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0)
        {
            Console.WriteLine("Failed to load UDP driver, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Laserschweißparameter einstellen: io_type=1, num=3, scanSpeed=2000, scanWidth=3, peakPower=1500, dutyCycle=100, freq=1000
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingParam failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("SetLaserWeldingParam success");
        }

        // Start-DO-Portnummer einstellen
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartExtDoNum failed, error code: " + rtn);
        }

        // Auf Modus 0 (Teach-Modus) einstellen
        rtn = robot.Mode(0);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 0 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);


        DescPose desc_pos1 = new DescPose(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2 = new DescPose(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe = new DescPose(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);


        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offset = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        // Zum ersten Schweißpunkt bewegen
        int error = robot.MoveL(desc_pos1, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos1 return: " + error);

        // Laser starten (Laser an)
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (start) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser started");
        }

        // Zum zweiten Schweißpunkt bewegen (während des Schweißens)
        rtn = robot.MoveL(desc_pos2, 0, 0, 30, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos2 return: " + rtn);

        Thread.Sleep(500);
        // Laser stoppen (Laser aus)
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (stop) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser stopped");
        }

        // Zum Sicherheitspunkt bewegen
        rtn = robot.MoveL(desc_safe, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to safe_pos return: " + rtn);

        // Auf Modus 1 (Fernmodus) einstellen
        rtn = robot.Mode(1);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 1 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Verbindung schließen
        robot.CloseRPC();
        Thread.Sleep(1000);

        Console.WriteLine("Test completed");

        return ;
    }

Einstellen der Rückkehr zum Zyklus-Nullpunkt nach Pendelende
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Legt fest, ob nach Pendelende zum Zyklus-Nullpunkt zurückgekehrt wird
    * @param [in] flag Ob nach Pendelende zum Zyklus-Nullpunkt zurückgekehrt wird; 0-nicht zurückkehren; 1-zum Zyklus-Nullpunkt zurückkehren
    * @return  Fehlercode
    */
    public int SetWeavebackCenterConfig(int flag) 
           
Abrufen der Parameter für die Rückkehr zum Zyklus-Nullpunkt nach Pendelende
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruft die Parameter für die Rückkehr zum Zyklus-Nullpunkt nach Pendelende ab
    * @param [out] flag Ob nach Pendelende zum Zyklus-Nullpunkt zurückgekehrt wird; 0-nicht zurückkehren; 1-zum Zyklus-Nullpunkt zurückkehren
    * @return  Fehlercode
    */
    public int GetWeavebackCenterConfig(ref int flag)
           
Codebeispiel für die Rückkehr zum Zyklus-Nullpunkt nach Pendelende
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void TestSplineWeave()
    {
        int rtn;

        // Pendel-Rückkehr-zur-Mitte-Konfiguration
        robot.SetWeavebackCenterConfig(1);
        int weaveBackConfig = 0;
        robot.GetWeavebackCenterConfig(ref weaveBackConfig);
        Console.WriteLine("GetWeavebackCenterConfig: {0}", weaveBackConfig);

        JointPos j1 = new JointPos(9.000, -66.067, 67.706, -103.217, -90.151, 100.669);
        JointPos j2 = new JointPos(-4.660, -107.973, 103.734, -76.214, -89.999, 90.886);
        JointPos j3 = new JointPos(-36.762, -77.380, 91.364, -127.159, -90.024, 54.833);
        JointPos j4 = new JointPos(-62.875, -89.460, 86.437, -77.030, -90.012, 31.539);
        DescPose desc_pos1 = new DescPose(-654.129, -235.344, 246.543, 6.010, -11.535, -176.787);
        DescPose desc_pos2 = new DescPose(-273.710, -100.871, 280.935, 5.692, 9.522, 179.512);
        DescPose desc_pos3 = new DescPose(-566.093, 311.278, 215.008, -10.453, -17.486, -174.209);
        DescPose desc_pos4 = new DescPose(-246.558, 328.240, 292.173, 13.912, 4.437, -179.067);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 2;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 20.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;

        robot.SetSpeed(1);

        // Bewegung zum Startpunkt j1
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, 100.0f, epos, blendT, flag, offset_pos);
        Console.WriteLine("MoveJ to j1 rtn: {0}", rtn);

        // Pendel + Spline-Kurvenbewegung
        robot.WeaveStart(0);
        robot.NewSplineStart(0, 6000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1.0f, 1);
        robot.NewSplineEnd();

        Console.WriteLine("TestSplineWeave completed");
    }    