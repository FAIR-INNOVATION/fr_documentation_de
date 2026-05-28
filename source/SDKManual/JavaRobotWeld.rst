Roboterschweißen
========================

.. toctree::
    :maxdepth: 5

Parameter der Schweißprozesskurve einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Parameter der Schweißprozesskurve ein.
    * @param [in] id Schweißprozessnummer (1-99).
    * @param [in] param Parameter der Schweißprozesskurve.
    * @return Fehlercode.
    */
    int WeldingSetProcessParam(int id, WeldingProcessParam param);

Parameter der Schweißprozesskurve abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Parameter der Schweißprozesskurve zurück.
    * @param [in] id Schweißprozessnummer (1-99).
    * @param [out] param Parameter der Schweißprozesskurve.
    * @return Fehlercode.
    */
    int WeldingGetProcessParam(int id, WeldingProcessParam param);

Beziehung zwischen Schweißstrom und Analogausgang festlegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt die Beziehung zwischen Schweißstrom und Analogausgang fest.
    * @param [in] relation Beziehungsobjekt.
    * @return Fehlercode.
    */
    int WeldingSetCurrentRelation(WeldCurrentAORelation relation);

Beziehung zwischen Schweißspannung und Analogausgang festlegen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Legt die Beziehung zwischen Schweißspannung und Analogausgang fest.
    * @param [in] relation Beziehungsobjekt.
    * @return Fehlercode.
    */
    int WeldingSetVoltageRelation(WeldVoltageAORelation relation);

Beziehung zwischen Schweißstrom und Analogausgang abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Beziehung zwischen Schweißstrom und Analogausgang zurück.
    * @param [out] relation Beziehungsobjekt.
    * @return Fehlercode.
    */
    int WeldingGetCurrentRelation(WeldCurrentAORelation relation);

Beziehung zwischen Schweißspannung und Analogausgang abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Beziehung zwischen Schweißspannung und Analogausgang zurück.
    * @param [out] relation Beziehungsobjekt.
    * @return Fehlercode.
    */
    int WeldingGetVoltageRelation(WeldVoltageAORelation relation);

Schweißstrom einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt den Schweißstrom ein.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] current Schweißstromwert (A).
    * @param [in] AOIndex Analogausgangsport des Steuerschranks für den Strom (0-1).
    * @param [in] blend Glättung 0-nicht glätten; 1-glätten.
    * @return Fehlercode.
    */
    int WeldingSetCurrent(int ioType, double current, int AOIndex, int blend);

Schweißspannung einstellen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Schweißspannung ein.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] voltage Schweißspannungswert (V).
    * @param [in] AOIndex Analogausgangsport des Steuerschranks für die Spannung (0-1).
    * @param [in] blend Glättung 0-nicht glätten; 1-glätten.
    * @return Fehlercode.
    */
    int WeldingSetVoltage(int ioType, double voltage, int AOIndex, int blend);

Pendelparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
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
    int WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle);

Codebeispiel zum Einstellen von Schweißparametern
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestSetWeldParam(Robot robot)
    {
        WeldingProcessParam para1 = new WeldingProcessParam(177, 27, 1000, 178, 28, 176, 26, 1000);
        WeldingProcessParam para2 = new WeldingProcessParam(188, 28, 555, 199, 29, 133, 23, 333);

        robot.WeldingSetProcessParam(1, para1);
        robot.WeldingSetProcessParam(2, para2);

        double startCurrent = 0;
        double startVoltage = 0;
        int startTime = 0;
        double weldCurrent = 0;
        double weldVoltage = 0;
        double endCurrent = 0;
        double endVoltage = 0;
        int endTime = 0;

        WeldingProcessParam param=new WeldingProcessParam( startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
        robot.WeldingGetProcessParam(1,param);
        robot.WeldingGetProcessParam(2,param);

        WeldCurrentAORelation rela1 = new WeldCurrentAORelation(0, 400, 0, 10, 0);
        int rtn = robot.WeldingSetCurrentRelation(rela1);

        WeldVoltageAORelation rela2 = new WeldVoltageAORelation(0, 40, 0, 10, 1);
        rtn = robot.WeldingSetVoltageRelation(rela2);

        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        WeldCurrentAORelation rela3=new WeldCurrentAORelation(current_min, current_max, output_vmin, output_vmax, curIndex);
        rtn = robot.WeldingGetCurrentRelation(rela3);

        WeldVoltageAORelation rela4=new WeldVoltageAORelation(0,0,0,0,0);
        rtn = robot.WeldingGetVoltageRelation(rela4);

        rtn = robot.WeldingSetCurrent(0, 100, 0, 0);
        robot.Sleep(3000);
        rtn = robot.WeldingSetVoltage(0, 10, 0, 0);

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000,0);

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        List<Integer> inter=new ArrayList<>();
        List<Number> num=new ArrayList<>();

        inter = robot.WeldingGetCheckArcInterruptionParam();
        num = robot.WeldingGetReWeldAfterBreakOffParam();

        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            robot.SetWeldMachineCtrlMode(0);
            robot.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            robot.Sleep(1000);
        }
        return 0;
    }

Pendelparameter sofort einstellen (Online)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
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
    int WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung ein.
    * @param [in] checkEnable Erkennung aktivieren/deaktivieren; 0-deaktivieren; 1-aktivieren.
    * @param [in] arcInterruptTimeLength Bestätigungsdauer für Lichtbogenunterbrechung (ms).
    * @return Fehlercode.
    */
    int WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Parameter für die Erkennung einer unerwarteten Lichtbogenunterbrechung zurück.
    * @return List[0]: Fehlercode; List[1]: int Erkennung aktiviert? 0-deaktiviert; 1-aktiviert; List[2]: int Bestätigungsdauer (ms).
    */
    List<Integer> WeldingGetCheckArcInterruptionParam();

Parameter für die Wiederaufnahme nach Schweißunterbrechung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Parameter für die Wiederaufnahme nach Schweißunterbrechung ein.
    * @param [in] enable Wiederaufnahme nach Unterbrechung aktivieren.
    * @param [in] length Überlappungslänge der Schweißnaht (mm).
    * @param [in] velocity Geschwindigkeitsprozentsatz für die Rückkehr zum Wiederzündpunkt (0-100).
    * @param [in] moveType Bewegungstyp zum Wiederzündpunkt; 0-LIN; 1-PTP.
    * @return Fehlercode.
    */
    int WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);

Parameter für die Wiederaufnahme nach Schweißunterbrechung abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Gibt die Parameter für die Wiederaufnahme nach Schweißunterbrechung zurück.
    * @return List[0]: Fehlercode; List[1]: int Wiederaufnahme aktiviert?; List[2]: double Überlappungslänge (mm); List[3]: double Geschwindigkeit (%); List[4]: int Bewegungstyp (0-LIN, 1-PTP).
    */
    List<Number> WeldingGetReWeldAfterBreakOffParam();

Erweiterten DO-Port für Schweißgeräte-Steuermodus einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt den erweiterten DO-Port für den Schweißgeräte-Steuermodus ein.
    * @param [in] DONum DO-Portnummer (0-127).
    * @return Fehlercode.
    */
    int SetWeldMachineCtrlModeExtDoNum(int DONum);

Schweißgeräte-Steuermodus einstellen
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schweißmaschinen-Steuerungsmodus einstellen
    * @param mode Schweißmaschinen-Steuerungsmodus; 0-Gleichstrom-Einknopf-Modus; 1-Impuls-Einknopf-Modus; 2-JOB-Modus; 3-Nahsteuerungs-Modus; 4-Separat-Modus; 5-CC/CV-Modus; 6-TIG; 7-CMT
    * @param ioType Steuerungstyp; 0-Steuerkasten-IO; 1-Digitales Kommunikationsprotokoll (UDP); 2-Digitales Kommunikationsprotokoll (ModbusTCP)
    * @return Fehlercode
    */
    public int SetWeldMachineCtrlMode(int mode, int ioType)

Schweißen starten (Lichtbogen zünden)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet das Schweißen (zündet den Lichtbogen).
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] arcNum Nummer der Schweißgerätekonfigurationsdatei.
    * @param [in] timeout Zeitüberschreitung für die Lichtbogenzündung (ms).
    * @return Fehlercode.
    */
    int ARCStart(int ioType, int arcNum, int timeout);

Schweißen beenden (Lichtbogen löschen)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Beendet das Schweißen (löscht den Lichtbogen).
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] arcNum Nummer der Schweißgerätekonfigurationsdatei.
    * @param [in] timeout Zeitüberschreitung für das Lichtbogenlöschen (ms).
    * @return Fehlercode.
    */
    int ARCEnd(int ioType, int arcNum, int timeout);

Pendeln starten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet das Pendeln.
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter.
    * @return Fehlercode.
    */
    int WeaveStart(int weaveNum);

Pendeln beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Beendet das Pendeln.
    * @param [in] weaveNum Konfigurationsnummer der Pendelparameter.
    * @return Fehlercode.
    */
    int WeaveEnd(int weaveNum);

Vorwärts-Drahtvorschub
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Steuert den Vorwärts-Drahtvorschub.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] wireFeed Drahtvorschubsteuerung 0-stoppen; 1-starten.
    * @return Fehlercode.
    */
    int SetForwardWireFeed(int ioType, int wireFeed);

Rückwärts-Drahtvorschub
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Steuert den Rückwärts-Drahtvorschub.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] wireFeed Drahtvorschubsteuerung 0-stoppen; 1-starten.
    * @return Fehlercode.
    */
    int SetReverseWireFeed(int ioType, int wireFeed);

Schutzgas steuern
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Steuert das Schutzgas.
    * @param [in] ioType I/O-Typ 0-Steuerschrank I/O; 1-Erweiterungs-I/O.
    * @param [in] airControl Gassteuerung 0-stoppen; 1-starten.
    * @return Fehlercode.
    */
    int SetAspirated(int ioType, int airControl);

Schweißen nach Unterbrechung wiederaufnehmen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Nimmt das Schweißen nach einer Unterbrechung wieder auf.
    * @return Fehlercode.
    */
    int WeldingStartReWeldAfterBreakOff();

Schweißen nach Unterbrechung abbrechen
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Bricht das Schweißen nach einer Unterbrechung ab.
    * @return Fehlercode.
    */
    int WeldingAbortWeldAfterBreakOff();

Codebeispiel für Roboter-Schweißsteuerung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestWelding(Robot robot)
    {
        robot.WeldingSetCurrent(0, 230, 0, 0);
        robot.WeldingSetVoltage(0, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ARCStart(1, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCEnd(1, 0, 10000);
        robot.WeaveEnd(0);
        return 0;
    }

Segmentweises Schweißen starten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
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
    * @param [in] tool Werkzeugnummer.
    * @param [in] user Werkstücknummer.
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
    int SegmentWeldStart(DescPose startDesePos, DescPose endDesePos, JointPos startJPos, JointPos endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout, boolean isWeave, int weaveNum, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos);

Codebeispiel für robotergestütztes segmentweises Schweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestSegWeld(Robot robot)
    {
        robot.WeldingSetCurrent(0, 230, 0, 0);
        robot.WeldingSetVoltage(0, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint, p2Desc);

        int rtn = robot.SegmentWeldStart(p1Desc, p2Desc, p1Joint, p2Joint, 20, 20, 0, 0, 5000, true, 0, 1, 0, 30, 100, 100, -1, exaxisPos, 0, 0, offdese);
        return 0;
    }

Simulationspendeln starten
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet das Simulationspendeln (nur Visualisierung, ohne Bewegung?).
    * @param [in] weaveNum Pendelparameternummer.
    * @return Fehlercode.
    */
    int WeaveStartSim(int weaveNum);

Simulationspendeln beenden
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Beendet das Simulationspendeln.
    * @param [in] weaveNum Pendelparameternummer.
    * @return Fehlercode.
    */
    int WeaveEndSim(int weaveNum);

Bahnprüfung/-warnung starten (ohne Bewegung)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet die Bahnprüfung/-warnung (ohne Bewegung).
    * @param [in] weaveNum Pendelparameternummer.
    * @return Fehlercode.
    */
    int WeaveInspectStart(int weaveNum);

Bahnprüfung/-warnung beenden (ohne Bewegung)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Beendet die Bahnprüfung/-warnung (ohne Bewegung).
    * @param [in] weaveNum Pendelparameternummer.
    * @return Fehlercode.
    */
    int WeaveInspectEnd(int weaveNum);

Pendel-Gradientenstart (WeaveChangeStart)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Startet den Pendel-Gradienten (Änderung von Parametern während der Bewegung).
    * @param [in] weaveChangeFlag 1-Pendelparameter ändern; 2-Pendelparameter + Schweißgeschwindigkeit ändern.
    * @param [in] weaveNum Pendelnummer.
    * @param [in] velStart Schweißgeschwindigkeit am Start (cm/min).
    * @param [in] velEnd Schweißgeschwindigkeit am Ende (cm/min).
    * @return Fehlercode.
    */
    int WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Codebeispiel für robotergestütztes Pendel-Gradientenschweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestWeave(Robot robot)
    {
        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveStartSim(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.WeaveEndSim(0);
        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveInspectStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.WeaveInspectEnd(0);

        robot.WeldingSetVoltage(1, 19, 0, 0);
        robot.WeldingSetCurrent(1, 190, 0, 0);
        robot.MoveL(p1Joint, p1Desc, 1, 1, 100, 100, 50, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCStart(1, 0, 10000);
        robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(1, 0, 50, 30);
        robot.MoveL(p2Joint, p2Desc, 1, 1, 100, 100, 1, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.ARCEnd(1, 0, 10000);
        return 0;
    }

Pendel-Gradienten beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.2-3.7.9

.. code-block:: java
    :linenos:

    /**
    * @brief Beendet den Pendel-Gradienten.
    * @return Fehlercode.
    */
    int WeaveChangeEnd();

Erweiterter I/O - Gasprüfsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den erweiterten DO-Port für das Gasprüfsignal des Schweißgeräts.
    * @param [in] DONum Erweiterte DO-Nummer für das Gasprüfsignal.
    * @return Fehlercode.
    */
    int SetAirControlExtDoNum(int DONum);

Erweiterter I/O - Lichtbogenzünde-Signal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den erweiterten DO-Port für das Lichtbogenzünde-Signal des Schweißgeräts.
    * @param [in] DONum Erweiterte DO-Nummer für das Lichtbogenzünde-Signal.
    * @return Fehlercode.
    */
    int SetArcStartExtDoNum(int DONum);

Erweiterter I/O - Rückwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den erweiterten DO-Port für das Rückwärts-Drahtvorschubsignal des Schweißgeräts.
    * @param [in] DONum Erweiterte DO-Nummer für das Rückwärts-Drahtvorschubsignal.
    * @return Fehlercode.
    */
    int SetWireReverseFeedExtDoNum(int DONum);

Erweiterter I/O - Vorwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den erweiterten DO-Port für das Vorwärts-Drahtvorschubsignal des Schweißgeräts.
    * @param [in] DONum Erweiterte DO-Nummer für das Vorwärts-Drahtvorschubsignal.
    * @return Fehlercode.
    */
    int SetWireForwardFeedExtDoNum(int DONum);

Erweiterter I/O - Erfolgreiche Lichtbogenzündung-Signal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den erweiterten DI-Port für das Signal "Lichtbogenzündung erfolgreich" des Schweißgeräts.
    * @param [in] DINum Erweiterte DI-Nummer für das Signal "Lichtbogenzündung erfolgreich".
    * @return Fehlercode.
    */
    int SetArcDoneExtDiNum(int DINum);

Erweiterter I/O - Bereitschaftssignal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert den erweiterten DI-Port für das Bereitschaftssignal des Schweißgeräts.
    * @param [in] DINum Erweiterte DI-Nummer für das Bereitschaftssignal.
    * @return Fehlercode.
    */
    int SetWeldReadyExtDiNum(int DINum);

Erweiterte I/O - Signale für Wiederaufnahme/Abruch nach Schweißunterbrechung konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Konfiguriert die erweiterten DI-Ports für die Signale "Wiederaufnahme nach Unterbrechung" und "Abbruch nach Unterbrechung".
    * @param [in] reWeldDINum Erweiterte DI-Nummer für das Signal "Wiederaufnahme nach Unterbrechung".
    * @param [in] abortWeldDINum Erweiterte DI-Nummer für das Signal "Abbruch nach Unterbrechung".
    * @return Fehlercode.
    */
    int SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Codebeispiel zum Konfigurieren erweiterter I/O-Schweißsignale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestExtDIConfig(Robot robot)
    {
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);

        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);

        return 0;
    }

Lichtbogen-Tracking-Steuerung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.2-3.7.9

.. code-block:: java
    :linenos:

    /**
    * @brief Steuert das Lichtbogen-Tracking.
    * @param [in] flag Schalter, 0-aus; 1-ein.
    * @param [in] delaytime Verzögerungszeit, Einheit ms.
    * @param [in] isLeftRight Links/Rechts-Abweichungskompensation aktivieren.
    * @param [in] klr Links/Rechts-Einstellkoeffizient (Empfindlichkeit).
    * @param [in] tStartLr Startzeit für Links/Rechts-Kompensation (cyc).
    * @param [in] stepMaxLr Maximale Kompensation pro Schritt links/rechts (mm).
    * @param [in] sumMaxLr Maximale Gesamtkompensation links/rechts (mm).
    * @param [in] isUpLow Oben/Unten-Abweichungskompensation aktivieren.
    * @param [in] kud Oben/Unten-Einstellkoeffizient (Empfindlichkeit).
    * @param [in] tStartUd Startzeit für Oben/Unten-Kompensation (cyc).
    * @param [in] stepMaxUd Maximale Kompensation pro Schritt oben/unten (mm).
    * @param [in] sumMaxUd Maximale Gesamtkompensation oben/unten (mm).
    * @param [in] axisSelect Koordinatensystem für oben/unten, 0-Pendel; 1-Werkzeug; 2-Basis.
    * @param [in] referenceType Einstellungsart für oben/unten-Referenzstrom, 0-Rückmeldung; 1-Konstante.
    * @param [in] referSampleStartUd Startzähler für Abtastung des oben/unten-Referenzstroms (bei Rückmeldung) (cyc).
    * @param [in] referSampleCountUd Zyklenzahl für Abtastung des oben/unten-Referenzstroms (bei Rückmeldung) (cyc).
    * @param [in] referenceCurrent Oben/unten-Referenzstrom (mA).
    * @param [in] offsetType Versatz-Tracking-Typ, 0-kein Versatz; 1-Abtastung; 2-Prozentsatz.
    * @param [in] offsetParameter Versatzparameter; Abtastung (Startzeit der Versatzabtastung, Standard eine Abtastperiode); Prozentsatz (Versatzprozentsatz (-100 ~ 100)).
    * @return Fehlercode.
    */
    int ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType, int offsetParameter);

AI-Kanal für Lichtbogen-Tracking auswählen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wählt den AI-Kanal für das Lichtbogen-Tracking aus.
    * @param channel Kanal; 0-Erweiterungs-AI0; 1-Erweiterungs-AI1; 2-Erweiterungs-AI2; 3-Erweiterungs-AI3; 4-Steuerschrank-AI0; 5-Steuerschrank-AI1.
    * @return Fehlercode.
    */
    public int ArcWeldTraceExtAIChannelConfig(int channel);

Lichtbogen-Tracking + Mehrlagenschweiß-Kompensation starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet Lichtbogen-Tracking mit Kompensation für Mehrlagenschweißen.
    * @return Fehlercode.
    */
    public int ArcWeldTraceReplayStart();

Lichtbogen-Tracking + Mehrlagenschweiß-Kompensation beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Beendet Lichtbogen-Tracking mit Kompensation für Mehrlagenschweißen.
    * @return Fehlercode.
    */
    public int ArcWeldTraceReplayEnd();

Koordinatentransformation für Mehrlagenschweiß-Versatz
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Führt eine Koordinatentransformation für den Versatz beim Mehrlagenschweißen durch.
    * @param pointO Ursprungspunkt O.
    * @param pointX Punkt auf der X-Achse.
    * @param pointZ Punkt auf der Z-Achse.
    * @param dx Versatz in x-Richtung (mm).
    * @param dz Versatz in z-Richtung (mm).
    * @param dry Versatz um die y-Achse (°).
    * @param offset [out] Resultierender Posenversatz.
    * @return Fehlercode.
    */
    public int MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dz, double dry, DescPose offset);

Codebeispiel für Lichtbogen-Tracking mit Mehrlagenschweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestArcWeldTrace(Robot robot)
    {
        JointPos mulitilineorigin1_joint = new JointPos(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
        DescPose mulitilineorigin1_desc = new DescPose(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);

        DescTran mulitilineX1_desc=new DescTran(0,0,0);
        mulitilineX1_desc.x = -677.556;
        mulitilineX1_desc.y = 211.949;
        mulitilineX1_desc.z = -1.206;

        DescTran mulitilineZ1_desc=new DescTran(0,0,0);
        mulitilineZ1_desc.x = -677.564;
        mulitilineZ1_desc.y = 190.956;
        mulitilineZ1_desc.z = 19.817;

        JointPos mulitilinesafe_joint=new JointPos(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
        DescPose mulitilinesafe_desc=new DescPose(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
        JointPos mulitilineorigin2_joint=new JointPos(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
        DescPose mulitilineorigin2_desc=new DescPose(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);

        DescTran mulitilineX2_desc=new DescTran(0,0,0);
        mulitilineX2_desc.x = -563.965;
        mulitilineX2_desc.y = 220.355;
        mulitilineX2_desc.z = -0.680;

        DescTran mulitilineZ2_desc=new DescTran(0,0,0);
        mulitilineZ2_desc.x = -563.968;
        mulitilineZ2_desc.y = 215.362;
        mulitilineZ2_desc.z = 4.331;

        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        DescPose offset=new DescPose(0, 0, 0, 0, 0, 0);

        robot.Sleep(10);
        int error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 0, offset, 0, 100);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 0, offset, 0, 100);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,0, epos, 0, 0, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);
        error = robot.WeaveStart(0);

        error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1, 0,epos, 0, 0,offset, 0, 100);

        error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0);

        error = robot.WeaveEnd(0);

        error = robot.ARCEnd(1, 0, 10000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 1, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, offset);

        error = robot.ArcWeldTraceReplayStart();
        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, 0, epos, 0, 1, offset, 0, 100);
        error = robot.ArcWeldTraceReplayEnd();

        error = robot.ARCEnd(1, 0, 10000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,0, epos, 0, 1, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);
        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, offset);

        error = robot.ArcWeldTraceReplayStart();

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1,0, epos, 0, 1, offset, 0, 100);

        error = robot.ArcWeldTraceReplayEnd();

        error = robot.ARCEnd(1, 0, 3000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        robot.CloseRPC();
        return 0;
    }

AI-Kanal für Schweißstromrückmeldung beim Lichtbogen-Tracking auswählen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Wählt den AI-Kanal für die Schweißstromrückmeldung beim Lichtbogen-Tracking aus.
    * @param channel Kanal; 0-Erweiterungs-AI0; 1-Erweiterungs-AI1; 2-Erweiterungs-AI2; 3-Erweiterungs-AI3; 4-Steuerschrank-AI0; 5-Steuerschrank-AI1.
    * @return Fehlercode.
    */
    int ArcWeldTraceAIChannelCurrent(int channel);

AI-Kanal für Schweißspannungsrückmeldung beim Lichtbogen-Tracking auswählen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Wählt den AI-Kanal für die Schweißspannungsrückmeldung beim Lichtbogen-Tracking aus.
    * @param channel Kanal; 0-Erweiterungs-AI0; 1-Erweiterungs-AI1; 2-Erweiterungs-AI2; 3-Erweiterungs-AI3; 4-Steuerschrank-AI0; 5-Steuerschrank-AI1.
    * @return Fehlercode.
    */
    int ArcWeldTraceAIChannelVoltage(int channel);

Umrechnungsparameter für die Schweißstromrückmeldung beim Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Umrechnungsparameter für die Schweißstromrückmeldung beim Lichtbogen-Tracking ein.
    * @param [in] AILow Untere Grenze des AI-Kanals, Standard 0 V, Bereich [0-10 V].
    * @param [in] AIHigh Obere Grenze des AI-Kanals, Standard 10 V, Bereich [0-10 V].
    * @param [in] currentLow Schweißstromwert entsprechend der unteren AI-Grenze, Standard 0 A, Bereich [0-200 A].
    * @param [in] currentHigh Schweißstromwert entsprechend der oberen AI-Grenze, Standard 100 A, Bereich [0-200 A].
    * @return Fehlercode.
    */
    int ArcWeldTraceCurrentPara(double AILow, double AIHigh, double currentLow, double currentHigh);

Umrechnungsparameter für die Schweißspannungsrückmeldung beim Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die Umrechnungsparameter für die Schweißspannungsrückmeldung beim Lichtbogen-Tracking ein.
    * @param [in] AILow Untere Grenze des AI-Kanals, Standard 0 V, Bereich [0-10 V].
    * @param [in] AIHigh Obere Grenze des AI-Kanals, Standard 10 V, Bereich [0-10 V].
    * @param [in] voltageLow Schweißspannungswert entsprechend der unteren AI-Grenze, Standard 0 V, Bereich [0-200 V].
    * @param [in] voltageHigh Schweißspannungswert entsprechend der oberen AI-Grenze, Standard 100 V, Bereich [0-200 V].
    * @return Fehlercode.
    */
    int ArcWeldTraceVoltagePara(double AILow, double AIHigh, double voltageLow, double voltageHigh);

Codebeispiel für Lichtbogen-Tracking
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void WeldTraceControlWithCtrlBoxAI(Robot robot)
    {
        DescPose startdescPose = new DescPose(-473.86, 257.879, -20.849, -37.317, -42.021, 2.543);
        JointPos startjointPos = new JointPos(-43.487, -76.526, 95.568, -104.445, -89.356, 3.72);

        DescPose safedescPose = new DescPose(-504.043, 275.181, 40.908, -28.002, -42.025, -14.044);
        JointPos safejointPos = new JointPos(-39.078, -76.732, 87.227, -99.47, -94.301, 18.714);

        DescPose enddescPose = new DescPose(-499.844, 141.225, 7.72, -34.856, -40.17, 13.13);
        JointPos endjointPos = new JointPos(-31.305, -82.998, 99.401, -104.426, -89.35, 3.696);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 20, 100, exaxisPos, -1, 0, offdese);

        WeldCurrentAORelation current = new WeldCurrentAORelation(0, 495, 1, 10, 0);
        WeldVoltageAORelation voltage = new WeldVoltageAORelation(10, 45, 1, 10, 1);
        robot.WeldingSetCurrentRelation(current);
        robot.WeldingSetVoltageRelation(voltage);
        robot.WeldingSetVoltage(0, 25, 1, 0);
        robot.WeldingSetCurrent(0, 260, 0, 0);

        int rtn = robot.ArcWeldTraceAIChannelCurrent(4);
        System.out.println("ArcWeldTraceAIChannelCurrent rtn is " + rtn);

        rtn = robot.ArcWeldTraceAIChannelVoltage(5);
        System.out.println("ArcWeldTraceAIChannelVoltage rtn is " + rtn);

        rtn = robot.ArcWeldTraceCurrentPara(0.0, 5, 0, 500);
        System.out.println("ArcWeldTraceCurrentPara rtn is " + rtn);

        rtn = robot.ArcWeldTraceVoltagePara(1.018, 10, 0, 50);
        System.out.println("ArcWeldTraceVoltagePara rtn is " + rtn);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 20, 20, 100, exaxisPos, -1, 0, offdese);
        robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 20, 20, 100, exaxisPos, -1, 0, offdese);
    }

Erweiterte I/O-Ports für die Schweißdraht-Positionssuche einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Stellt die erweiterten I/O-Ports für die Schweißdraht-Positionssuche ein.
    * @param [in] searchDoneDINum Erweiterter DI-Port für "Positionssuche erfolgreich" (0-127).
    * @param [in] searchStartDONum Erweiterter DO-Port für Start/Stopp der Positionssuche (0-127).
    * @return Fehlercode.
    */
    int SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Beispielprogramm für Schweißdraht-Positionssuche (UDP)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    private static void TestUDPWireSearch(Robot robot)
    {
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10, 0);
        robot.ExtDevSetUDPComParam(param);

        robot.SetWireSearchExtDIONum(0, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offdese = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        DescPose descStart = new DescPose(-158.767, -510.596, 271.709, -179.427, -0.745, -137.349);
        JointPos jointStart = new JointPos(61.667, -79.848, 108.639, -119.682, -89.700, -70.985);

        DescPose descEnd = new DescPose(0.332, -516.427, 270.688, 178.165, 0.017, -119.989);
        JointPos jointEnd = new JointPos(79.021, -81.839, 110.752, -118.298, -91.729, -70.981);

        robot.MoveL(jointStart, descStart, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);
        robot.MoveL(jointEnd, descEnd, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);

        DescPose descREF0A = new DescPose(-66.106, -560.746, 270.381, 176.479, -0.126, -126.745);
        JointPos jointREF0A = new JointPos(73.531, -75.588, 102.941, -116.250, -93.347, -69.689);
        DescPose descREF0B = new DescPose(-66.109, -528.440, 270.407, 176.479, -0.129, -126.744);
        JointPos jointREF0B = new JointPos(72.534, -79.625, 108.046, -117.379, -93.366, -70.687);
        DescPose descREF1A = new DescPose(72.975, -473.242, 270.399, 176.479, -0.129, -126.744);
        JointPos jointREF1A = new JointPos(87.169, -86.509, 115.710, -117.341, -92.993, -56.034);
        DescPose descREF1B = new DescPose(31.355, -473.238, 270.405, 176.480, -0.130, -126.745);
        JointPos jointREF1B = new JointPos(82.117, -87.146, 116.470, -117.737, -93.145, -61.090);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        String[] varNameRef = {"REF0", "REF1", "#", "#", "#", "#"};
        String[] varNameRes = {"RES0", "RES1", "#", "#", "#", "#"};
        int offectFlag = 0;
        //DescPose offectPos = new DescPose(0, 0, 0, 0, 0, 0);
        DescOffset offset = new DescOffset();
        robot.MoveL(jointStart, descStart, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);
        robot.PointsOffsetEnable(0, offset.offset);
        robot.MoveL(jointStart, descStart, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);
        robot.MoveL(jointEnd, descEnd, 1, 0, 100, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);
        robot.PointsOffsetDisable();
    }

Schweißdraht-Positionssuche starten
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Startet die Schweißdraht-Positionssuche.
    * @param [in] refPos 1-Referenzpunkt; 0-Kontaktpunkt.
    * @param [in] searchVel Suchgeschwindigkeit (%).
    * @param [in] searchDis Suchstrecke (mm).
    * @param [in] autoBackFlag Automatische Rückkehr-Flag, 0-nicht automatisch; 1-automatisch.
    * @param [in] autoBackVel Automatische Rückkehrgeschwindigkeit (%).
    * @param [in] autoBackDis Automatische Rückkehrstrecke (mm).
    * @param [in] offectFlag 1-Positionssuche mit Versatz; 0-Positionssuche mit Teachpunkten.
    * @return Fehlercode.
    */
    int WireSearchStart(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Schweißdraht-Positionssuche beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Beendet die Schweißdraht-Positionssuche.
    * @param [in] refPos 1-Referenzpunkt; 2-Kontaktpunkt.
    * @param [in] searchVel Suchgeschwindigkeit (%).
    * @param [in] searchDis Suchstrecke (mm).
    * @param [in] autoBackFlag Automatische Rückkehr-Flag, 0-nicht automatisch; 1-automatisch.
    * @param [in] autoBackVel Automatische Rückkehrgeschwindigkeit (%).
    * @param [in] autoBackDis Automatische Rückkehrstrecke (mm).
    * @param [in] offectFlag 1-Positionssuche mit Versatz; 2-Positionssuche mit Teachpunkten.
    * @return Fehlercode.
    */
    int WireSearchEnd(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Versatz aus Schweißdraht-Positionssuche berechnen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Berechnet den Versatz aus der Schweißdraht-Positionssuche.
    * @param [in] seamType Nahttyp.
    * @param [in] method Berechnungsmethode.
    * @param [in] varNameRef Array der Referenzpunktnamen 1-6, "#" für nicht verwendete Punkte.
    * @param [in] varNameRes Array der Kontaktpunktnamen 1-6, "#" für nicht verwendete Punkte.
    * @param [out] offset Versatzpose und -art.
    * @return Fehlercode.
    */
    int GetWireSearchOffset(int seamType, int method, String[] varNameRef, String[] varNameRes, DescOffset offset);

Auf Abschluss der Schweißdraht-Positionssuche warten
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Wartet auf den Abschluss der Schweißdraht-Positionssuche.
    * @param name Name der Variable, die das Ergebnis speichern soll (z.B. "REF0").
    * @return Fehlercode.
    */
    int WireSearchWait(String name);

Kontaktpunkt der Schweißdraht-Positionssuche in Datenbank schreiben
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief Schreibt einen Kontaktpunkt der Schweißdraht-Positionssuche in die Datenbank.
    * @param [in] varName Kontaktpunktname "RES0" ~ "RES99".
    * @param [in] pos Kontaktpunktdaten [x, y, z, rx, ry, rz].
    * @return Fehlercode.
    */
    int SetPointToDatabase(String varName, DescPose pos);

Codebeispiel für robotergestützte Schweißdraht-Positionssuche
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static int TestWireSearch(Robot robot)
    {
        DescPose toolCoord=new DescPose(0, 0, 200, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);
        DescPose wobjCoord = new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetWObjCoord(1, wobjCoord, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos( 0, 0, 0, 0 );
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);


        DescPose descStart = new DescPose(216.543, 445.175, 93.465, 179.683, 1.757, -112.641);
        JointPos jointStart = new JointPos(-128.345, -86.660, 114.679, -119.625, -89.219, 74.303);

        DescPose descEnd =new DescPose(111.143, 523.384, 87.659, 179.703, 1.835, -97.750);
        JointPos jointEnd =new JointPos(-113.454, -81.060, 109.328, -119.954, -89.218, 74.302 );

        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, 0, exaxisPos, 0, 0, offdese, 0, 100);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, 0, exaxisPos, 0, 0, offdese, 0, 100);

        DescPose descREF0A = new DescPose(142.135, 367.604, 86.523, 179.728, 1.922, -111.089);
        JointPos jointREF0A =new JointPos(-126.794, -100.834, 128.922, -119.864, -89.218, 74.302);

        DescPose descREF0B = new DescPose(254.633, 463.125, 72.604, 179.845, 2.341, -114.704);
        JointPos jointREF0B = new JointPos(-130.413, -81.093, 112.044, -123.163, -89.217, 74.303);

        DescPose descREF1A =new DescPose(92.556, 485.259, 47.476, -179.932, 3.130, -97.512);
        JointPos jointREF1A =new JointPos(-113.231, -83.815, 119.877, -129.092, -89.217, 74.303);

        DescPose descREF1B =new DescPose(203.103, 583.836, 63.909, 179.991, 2.854, -103.372);
        JointPos jointREF1B = new JointPos(-119.088, -69.676, 98.692, -121.761, -89.219, 74.303);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        String[] varNameRef =new String[]{"REF0", "REF1", "#", "#", "#", "#"};
        String[] varNameRes = new String[]{ "RES0", "RES1", "#", "#", "#", "#" };
        int offectFlag = 0;

        DescPose pos = new DescPose(0,0,0,0,0,0);
        DescOffset offectPos=new DescOffset();
        offectPos.offset=pos;
        offectPos.offsetFlag=0;

        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectPos);
        robot.PointsOffsetEnable(0, pos);
        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 1, 0, offdese,0,10);
        robot.PointsOffsetDisable();

        robot.CloseRPC();
        return 0;
    }

Schweißspannungs-Gradienten starten
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
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
    int WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Schweißspannungs-Gradienten beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Beendet den Schweißspannungs-Gradienten.
    * @return Fehlercode.
    */
    int WeldingSetVoltageGradualChangeEnd();

Schweißstrom-Gradienten starten
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
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
    int WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Schweißstrom-Gradienten beenden
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: java
    :linenos:

    /**
    * @brief Beendet den Schweißstrom-Gradienten.
    * @return Fehlercode.
    */
    int WeldingSetCurrentGradualChangeEnd();

Codebeispiel für Schweißstrom-/spannungs-Gradienten
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void WeldparamChange(Robot robot) 
    {
        DescPose startdescPose = new DescPose(-484.707, 276.996, -14.013, -37.657, -40.508, -1.548);
        JointPos startjointPos = new JointPos(-45.421, -75.673, 93.627, -104.302, -87.938, 6.005);
        DescPose enddescPose = new DescPose(-508.767, 137.109, -13.966, -37.639, -40.508, -1.559);
        JointPos endjointPos = new JointPos(-32.768, -80.947, 100.254, -106.201, -87.201, 18.648);
        DescPose safedescPose = new DescPose(-484.709, 294.436, 13.621, -37.660, -40.508, -1.545);
        JointPos safejointPos = new JointPos(-46.604, -75.410, 89.109, -100.003, -88.012, 4.823);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        WeldCurrentAORelation cur = new WeldCurrentAORelation(0, 495, 1, 10, 0);
        WeldVoltageAORelation vol = new WeldVoltageAORelation(10, 45, 1, 10, 1);
        robot.WeldingSetCurrentRelation(cur);
        robot.WeldingSetVoltageRelation(vol);

        robot.WeldingSetVoltage(0, 25, 1, 0);
        robot.WeldingSetCurrent(0, 260, 0, 0);

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
        robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
        int rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);
        System.out.println("ArcWeldTraceControl rtn is " + rtn);

        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(2, 1, 24, 36);
        robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.WeldingSetCurrentGradualChangeEnd();
        robot.WeldingSetVoltageGradualChangeEnd();
    }

Benutzerdefinierte Pendelparameter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
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
    public int CustomWeaveSetPara(int id, int pointNum, DescTran[] point, double[] stayTime, double frequency, int incStayType, int stationary);

Benutzerdefinierte Pendelparameter abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: java
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
    public int CustomWeaveGetPara(int id, int[] pointNum, DescTran[] point, double[] stayTime, double[] frequency, int[] incStayType, int[] stationary);

Codebeispiel für benutzerdefinierte Pendelparameter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    public static void TestCustomWeaveSetPara(Robot robot)
    {
        DescTran[] point = new DescTran[10];
        point[0]=new DescTran();
        point[0].x = -3;
        point[0].y = -3;
        point[0].z = 0;

        point[1]=new DescTran();
        point[1].x = -6;
        point[1].y = 0;
        point[1].z = 0;

        point[2]=new DescTran();
        point[2].x = -3;
        point[2].y = 3;
        point[2].z = 0;

        point[3]=new DescTran();
        point[3].x = 0;
        point[3].y = 0;
        point[3].z = 0;
        point[4]=new DescTran(0,0,0);
        point[5]=new DescTran(0,0,0);
        point[6]=new DescTran(0,0,0);
        point[7]=new DescTran(0,0,0);
        point[8]=new DescTran(0,0,0);
        point[9]=new DescTran(0,0,0);

        double[] stayTime =new double[] { 0,0,0,0,0,0,0,0,0,0 };
        int rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0);
        System.out.println("CustomWeaveSetPara rtn is :"+ rtn);
        robot.Sleep(1000);

        int[] pointNum = new int[1];
        double[] frequency=new double[1];
        int[] incStayType=new int[1];
        int[] stationary=new int[1];
        robot.CustomWeaveGetPara(2, pointNum, point, stayTime, frequency, incStayType, stationary);
        System.out.println("pointNum is :"+ pointNum[0]);
        for (int i = 0; i < pointNum[0]; i++)
        {
            System.out.println("point:"+i+", "+ point[i].x+", "+ point[i].y+", "+ point[i].z);
        }
        System.out.println("fre is :"+ frequency[0]+", stay is:"+ incStayType[0]+", "+ stationary[0]);

        robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000,
                6.000000, 5.000000, 50, 100, 100,
                0, 1, 0.000000, 0.000000);

        DescPose desc_p1 =new DescPose(-288.650, 367.807, 288.404, 0.000, -0.001, 0.001 );
        DescPose desc_p2 = new DescPose( -431.714, 367.815, 288.415, 0.001, 0.001, 0.000 );
        DescPose desc_p3 = new DescPose( -348.666, 427.798, 288.404, -0.000, -0.000, 0.001 );
        JointPos j1 = new JointPos( 140.656, -84.560, -91.707, -93.734, 90.000, 50.655 );
        JointPos j2 = new JointPos( 149.873, -98.298, -77.599, -94.103, 90.000, 59.873 );
        JointPos j3 = new JointPos( 139.773, -96.173, -80.014, -93.814, 90.000, 49.772 );

        ExaxisPos epos = new ExaxisPos();
        DescPose offset_pos = new DescPose();

        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100,100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.Circle(j3, desc_p3, 3, 0, 100, 100, epos, j2, desc_p2, 3, 0, 100, 100, epos, 10, -1, offset_pos,0,-1,0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveC(j3, desc_p3, 3, 0, 100, 100, epos, 0, offset_pos, j2, desc_p2, 3, 0, 100, 100, epos, 0, offset_pos, 10, -1,0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveL(j2, desc_p2, 3, 0, 100, 100, 10, -1,epos, 0, 0, offset_pos, 0,0, 100);
        robot.WeaveEnd(0);

        robot.CloseRPC();
    }

Laserschweißgerät-Parameterkonfiguration
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Laserschweißgerät-Parameterkonfiguration
    * @param  io_type Kommunikationstyp 0-IO 1-UDP
    * @param  num Zu setzende Gruppennummer (1~10)
    * @param  scanSpeed Scangeschwindigkeit
    * @param  scanWidth Scanbreite
    * @param  peakPower Spitzenleistung
    * @param  dutyCycle Tastverhältnis
    * @param  freq Frequenz
    * @return Fehlercode
    */
    public int SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq);

Laserschweißen Starten/Stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Laserschweißen starten/stoppen
    * @param io_type Kommunikationstyp 0-IO 1-UDP
    * @param status Steuerwort 0-Laser aus 1-Laser ein
    * @param max_waittime Maximale Wartezeit in Millisekunden, Standard 10000
    * @return Fehlercode
    */
    public int SetLaserWeldingStartEnd(int io_type, int status, int max_waittime)

Laserschweißgerät Aktivieren/Deaktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Laserschweißgerät aktivieren/deaktivieren
    * @param io_type Kommunikationstyp 0-IO 1-UDP
    * @param status 0-deaktivieren 1-aktivieren
    * @return Fehlercode
    */
    public int SetLaserWeldingEnable(int io_type, int status)

Laserschweißgerät-Fehlerrücksetzung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Laserschweißgerät-Fehlerrücksetzung
    * @param io_type Kommunikationstyp 0-IO 1-UDP
    * @param status Steuerwort 0-ungültig 1-Fehlerrücksetzung
    * @return Fehlercode
    */
    public int ResetLaserWeldingErr(int io_type, int status)

Betriebszustand des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Betriebszustand des Laserschweißgeräts abrufen
    * @param io_type Kommunikationstyp 0-IO 1-UDP
    * @param  status Steuerwort 0-gestoppt 1-in Betrieb
    * @return Fehlercode
    */
    public int GetLaserWeldingRunningState(int io_type, int[] status)

Fehlerzustand des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fehlerzustand des Laserschweißgeräts abrufen
    * @param io_type Kommunikationstyp 0-IO 1-UDP
    * @param  status 0-kein Fehler 1-Fehler vorhanden
    * @return Fehlercode
    */
    public int GetLaserWeldingErrState(int io_type, int[] status)

Konfigurationsparameter des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Konfigurationsparameter einer der 10 Prozessgruppen des Laserschweißgeräts abrufen
    * @param num Zu setzende Gruppennummer (1~10)
    * @param params Ausgabeparameter-Array: [scanSpeed, scanWidth, peakPower, dutyCycle, freq]
    * @return Fehlercode
    */
    public int GetLaserWeldingParamTarget(int num, int[] params)

Aktive Konfigurationsparameter des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aktive Konfigurationsparameter des Laserschweißgeräts abrufen
    * @param io_type Kommunikationstyp 0-IO 1-UDP
    * @param params Ausgabeparameter-Array: [scanSpeed, scanWidth, peakPower, dutyCycle, freq]
    * @return Fehlercode
    */
    public int GetLaserWeldingParamActual(int io_type, int[] params)

Erweiterte IO-Aktivierungs-DO-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Erweiterte IO-Aktivierungs-DO-Port für Laserschweißgerät konfigurieren
    * @param ctrlModeDONum Erweiterte DO-Portnummer für Laserschweißgerät-Aktivierung
    * @return Fehlercode
    */
    public int SetLaserWeldingEnableExtDoNum(int ctrlModeDONum)

Erweiterte IO-Start-DO-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Erweiterte IO-Start-DO-Port für Laserschweißgerät konfigurieren
    * @param ctrlModeDONum Erweiterte DO-Portnummer für Laserschweißgerät-Start/Stopp
    * @return Fehlercode
    */
    public int SetLaserWeldingStartExtDoNum(int ctrlModeDONum)

Erweiterte IO-Fehlerrücksetzungs-DO-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Erweiterte IO-Fehlerrücksetzungs-DO-Port für Laserschweißgerät konfigurieren
    * @param ctrlModeDONum Erweiterte DO-Portnummer für Laserschweißgerät-Fehlerrücksetzung
    * @return Fehlercode
    */
    public int SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum)

Erweiterte IO-Betriebszustands-(Laser-Ein-Zustands)-DI-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Erweiterte IO-Betriebszustands-(Laser-Ein-Zustands)-DI-Port für Laserschweißgerät konfigurieren
    * @param diNum Erweiterte DI-Portnummer für Laserschweißgerät-Betriebszustand (Laser-Ein-Zustand)
    * @return Fehlercode, 0 zeigt Erfolg an, Nicht-Null zeigt Fehler an
    */
    public int SetLaserWeldingRunningStateExtDiNum(int diNum);

Erweiterte IO-Fehlerzustands-DI-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Erweiterte IO-Fehlerzustands-DI-Port für Laserschweißgerät konfigurieren
    * @param diNum Erweiterte DI-Portnummer für Laserschweißgerät-Fehlerzustand
    * @return Fehlercode, 0 zeigt Erfolg an, Nicht-Null zeigt Fehler an
    */
    public int SetLaserWeldingErrStateExtDiNum(int diNum);

Beispielcode für Laserschweißen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int testLsaerWeld(Robot robot) {
        int rtn = -1;
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0) {
            System.out.println("Fehler beim Laden des UDP-Treibers, Fehlercode: " + rtn);
        }
        robot.Sleep(1000);
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingParam fehlgeschlagen, Fehlercode: " + rtn);
        } else {
            System.out.println("SetLaserWeldingParam erfolgreich");
        }
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingStartExtDoNum fehlgeschlagen, Fehlercode: " + rtn);
        }
        rtn = robot.Mode(0);
        if (rtn != 0) {
            System.out.println("Setzen des Modus 0 fehlgeschlagen, Fehlercode: " + rtn);
        }
        robot.Sleep(1000);
        DescPose desc_pos1 = new DescPose(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2 = new DescPose(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe = new DescPose(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);

        JointPos jointPos1 = new JointPos(9.827, -99.740, 120.088, -78.900, -77.241, -17.904);
        JointPos jointPos2 = new JointPos(15.251, -96.456, 120.138, -84.664, -68.542, -17.843);
        JointPos jointSafe = new JointPos(19.142, -98.078, 101.493, -83.078, -77.070, -17.794);

        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offset = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int error = robot.MoveL(desc_pos1, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0,0,0);
        System.out.println("MoveL zu pos1 Rückgabe: " + error);
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingStartEnd (Start) fehlgeschlagen, Fehlercode: " + rtn);
        } else {
            System.out.println("Laser gestartet");
        }
        rtn = robot.MoveL(desc_pos2, 0, 0, 30, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0,0, 0);
        System.out.println("MoveL zu pos2 Rückgabe: " + rtn);
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingStartEnd (Stopp) fehlgeschlagen, Fehlercode: " + rtn);
        } else {
            System.out.println("Laser gestoppt");
        }
        robot.Sleep(500);
        rtn = robot.MoveL(desc_safe, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0,0,0);
        System.out.println("MoveL zu safe_pos Rückgabe: " + rtn);
        rtn = robot.Mode(1);
        if (rtn != 0) {
            System.out.println("Setzen des Modus 1 fehlgeschlagen, Fehlercode: " + rtn);
        }
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);

        System.out.println("Test abgeschlossen");

        return 0;
    }