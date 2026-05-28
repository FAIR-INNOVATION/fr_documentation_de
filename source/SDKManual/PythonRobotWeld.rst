Schweißen
=========

.. toctree::
    :maxdepth: 5

Parameter für Schweißprozesskurve einstellen
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetProcessParam(id, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime)``"
    "Beschreibung", "Parameter für Schweißprozesskurve einstellen"
    "Erforderliche Parameter", "- ``id``: Schweißprozessnummer (1-99)
    - ``startCurrent``: Lichtbogenstartstrom (A)
    - ``startVoltage``: Lichtbogenstartspannung (V)
    - ``startTime``: Lichtbogenstartzeit (ms)
    - ``weldCurrent``: Schweißstrom (A)
    - ``weldVoltage``: Schweißspannung (V)
    - ``endCurrent``: Lichtbogenendstrom (A)
    - ``endVoltage``: Lichtbogenendspannung (V)
    - ``endTime``: Lichtbogenendzeit (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Parameter für Schweißprozesskurve abrufen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetProcessParam(id)``"
    "Beschreibung", "Parameter für Schweißprozesskurve abrufen"
    "Erforderliche Parameter", "- ``id``: Schweißprozessnummer (1-99)"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``startCurrent``: Lichtbogenstartstrom (A)
    - ``startVoltage``: Lichtbogenstartspannung (V)
    - ``startTime``: Lichtbogenstartzeit (ms)
    - ``weldCurrent``: Schweißstrom (A)
    - ``weldVoltage``: Schweißspannung (V)
    - ``endCurrent``: Lichtbogenendstrom (A)
    - ``endVoltage``: Lichtbogenendspannung (V)
    - ``endTime``: Lichtbogenendzeit (ms)"

Beziehung zwischen Schweißstrom und Analogausgang einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrentRelation(currentMin, currentMax, outputVoltageMin, outputVoltageMax)``"
    "Beschreibung", "Beziehung zwischen Schweißstrom und Analogausgang einstellen"
    "Erforderliche Parameter", "- ``currentMin``: Stromwert des linken Punkts der linearen Beziehung (A)
    - ``currentMax``: Stromwert des rechten Punkts der linearen Beziehung (A)
    - ``outputVoltageMin``: Analogausgangsspannung des linken Punkts (V)
    - ``outputVoltageMax``: Analogausgangsspannung des rechten Punkts (V)
    - ``AOIndex``: Analogausgangsport für Schweißstrom"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Beziehung zwischen Schweißspannung und Analogausgang einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltageRelation(weldVoltageMin, weldVoltageMax, outputVoltageMin, outputVoltageMax)``"
    "Beschreibung", "Beziehung zwischen Schweißspannung und Analogausgang einstellen"
    "Erforderliche Parameter", "- ``weldVoltageMin``: Spannungswert des linken Punkts der linearen Beziehung (V)
    - ``weldVoltageMax``: Spannungswert des rechten Punkts der linearen Beziehung (V)
    - ``outputVoltageMin``: Analogausgangsspannung des linken Punkts (V)
    - ``outputVoltageMax``: Analogausgangsspannung des rechten Punkts (V)
    - ``AOIndex``: Analogausgangsport für Schweißspannung"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Beziehung zwischen Schweißstrom und Analogausgang abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetCurrentRelation()``"
    "Beschreibung", "Beziehung zwischen Schweißstrom und Analogausgang abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``currentMin``: Stromwert des linken Punkts (A)
    - ``currentMax``: Stromwert des rechten Punkts (A)
    - ``outputVoltageMin``: Analogausgangsspannung des linken Punkts (V)
    - ``outputVoltageMax``: Analogausgangsspannung des rechten Punkts (V)
    - ``AOIndex``: Analogausgangsport"

Beziehung zwischen Schweißspannung und Analogausgang abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetVoltageRelation()``"
    "Beschreibung", "Beziehung zwischen Schweißspannung und Analogausgang abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``weldVoltageMin``: Spannungswert des linken Punkts (V)
    - ``weldVoltageMax``: Spannungswert des rechten Punkts (V)
    - ``outputVoltageMin``: Analogausgangsspannung des linken Punkts (V)
    - ``outputVoltageMax``: Analogausgangsspannung des rechten Punkts (V)
    - ``AOIndex``: Analogausgangsport"

Schweißstrom einstellen
+++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrent(ioType, current, AOIndex, blend)``"
    "Beschreibung", "Schweißstrom einstellen"
    "Erforderliche Parameter", "- ``ioType``: Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``current``: Schweißstromwert (A)
    - ``AOIndex``: Analogausgangsport für Schweißstrom (0-1)
    - ``blend``: Glättung, 0 = nein, 1 = ja"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißspannung einstellen
++++++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltage(ioType, voltage, AOIndex, blend)``"
    "Beschreibung", "Schweißspannung einstellen"
    "Erforderliche Parameter", "- ``ioType``: Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``voltage``: Schweißspannungswert (V)
    - ``AOIndex``: Analogausgangsport für Schweißspannung (0-1)
    - ``blend``: Glättung, 0 = nein, 1 = ja"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Pendelparameter einstellen
++++++++++++++++++++++++++
.. versionchanged:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveSetPara(weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftRange, weaveRightRange, additionalStayTime, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary, weaveYawAngle, weaveRotAngle)``"
    "Beschreibung", "Pendelparameter einstellen"
    "Erforderliche Parameter", "- ``weaveNum``: Konfigurationsnummer der Pendelparameter
    - ``weaveType``: Pendeltyp: 0 = Ebenen-Dreieck, 1 = Vertikal-L-förmiges Dreieck, 2 = Kreis im Uhrzeigersinn, 3 = Kreis gegen Uhrzeigersinn, 4 = Ebenen-Sinus, 5 = Vertikal-L-förmiger Sinus, 6 = Vertikales Dreieck, 7 = Vertikaler Sinus
    - ``weaveFrequency``: Pendelfrequenz (Hz)
    - ``weaveIncStayTime``: Wartemodus, 0 = Zyklus ohne Wartezeit, 1 = Zyklus mit Wartezeit
    - ``weaveRange``: Pendelamplitude (mm)
    - ``weaveLeftRange``: Länge der linken Seite beim vertikalen Dreieckspendeln (mm)
    - ``weaveRightRange``: Länge der rechten Seite beim vertikalen Dreieckspendeln (mm)
    - ``additionalStayTime``: Verweilzeit am vertikalen Dreieckspunkt (ms)
    - ``weaveLeftStayTime``: Verweilzeit links (ms)
    - ``weaveRightStayTime``: Verweilzeit rechts (ms)
    - ``weaveCircleRadio``: Rücklaufverhältnis für Kreispendeln (0-100%)
    - ``weaveStationary``: Position während Wartezeit, 0 = Position bewegt sich weiter, 1 = Position ruht"
    "Standardparameter", "- ``weaveYawAngle``: Azimutwinkel der Pendelrichtung (Rotation um die Pendel-Z-Achse) [°], Standard = 0
    - ``weaveRotAngle``: Rotationswinkel (Rotation um die Pendel-X-Achse) [°], Standard = 0"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Einstellen von Schweißparametern
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000)
    robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333)
    start_current = 0
    start_voltage = 0
    start_time = 0
    weld_current = 0
    weld_voltage = 0
    end_current = 0
    end_voltage = 0
    end_time = 0
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(1)
    print(f"the Num 1 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(2)
    print(f"the Num 2 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0)
    print(f"WeldingSetCurrentRelation rtn is: {rtn}")
    rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1)
    print(f"WeldingSetVoltageRelation rtn is: {rtn}")
    current_min = 0
    current_max = 0
    vol_min = 0
    vol_max = 0
    output_vmin = 0
    output_vmax = 0
    cur_index = 0
    vol_index = 0
    rtn,current_min, current_max, output_vmin, output_vmax, cur_index = robot.WeldingGetCurrentRelation()
    print(f"WeldingGetCurrentRelation rtn is: {rtn}")
    print(f"current min {current_min} current max {current_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn,vol_min, vol_max, output_vmin, output_vmax, vol_index = robot.WeldingGetVoltageRelation()
    print(f"WeldingGetVoltageRelation rtn is: {rtn}")
    print(f"vol min {vol_min} vol max {vol_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn = robot.WeldingSetCurrent(1, 100, 0, 0)
    print(f"WeldingSetCurrent rtn is: {rtn}")
    time.sleep(3)
    rtn = robot.WeldingSetVoltage(1, 10, 0, 0)
    print(f"WeldingSetVoltage rtn is: {rtn}")
    rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0,0.0, 60.000000)
    print(f"rtn is: {rtn}")
    robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0)
    rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200)
    print(f"WeldingSetCheckArcInterruptionParam {rtn}")
    rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0)
    print(f"WeldingSetReWeldAfterBreakOffParam {rtn}")
    enable = 0
    length = 0
    velocity = 0
    move_type = 0
    check_enable = 0
    arc_interrupt_time_length = 0
    rtn,check_enable, arc_interrupt_time_length = robot.WeldingGetCheckArcInterruptionParam()
    print(f"WeldingGetCheckArcInterruptionParam checkEnable {check_enable} arcInterruptTimeLength {arc_interrupt_time_length}")
    rtn,enable, length, velocity, move_type = robot.WeldingGetReWeldAfterBreakOffParam()
    print(f"WeldingGetReWeldAfterBreakOffParam enable = {enable}, length = {length}, velocity = {velocity}, moveType = {move_type}")
    robot.SetWeldMachineCtrlModeExtDoNum(17)
    for i in range(5):
        robot.SetWeldMachineCtrlMode(0)
        time.sleep(1)
        robot.SetWeldMachineCtrlMode(1)
        time.sleep(1)
    robot.CloseRPC()

Pendelparameter online einstellen
++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveOnlineSetPara(weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary)``"
    "Beschreibung", "Pendelparameter online einstellen (während der Bewegung)"
    "Erforderliche Parameter", "- ``weaveNum``: Konfigurationsnummer der Pendelparameter
    - ``weaveType``: Pendeltyp (siehe WeaveSetPara)
    - ``weaveFrequency``: Pendelfrequenz (Hz)
    - ``weaveIncStayTime``: Wartemodus (siehe WeaveSetPara)
    - ``weaveRange``: Pendelamplitude (mm)
    - ``weaveLeftStayTime``: Verweilzeit links (ms)
    - ``weaveRightStayTime``: Verweilzeit rechts (ms)
    - ``weaveCircleRadio``: Rücklaufverhältnis für Kreispendeln (0-100%)
    - ``weaveStationary``: Position während Wartezeit (siehe WeaveSetPara)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetCheckArcInterruptionParam()``"
    "Beschreibung", "Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``checkEnable``: Erkennung aktiviert? 0 = nein, 1 = ja
    - ``arcInterruptTimeLength``: Bestätigungsdauer für Lichtbogenunterbrechung (ms)"

Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCheckArcInterruptionParam(checkEnable, arcInterruptTimeLength)``"
    "Beschreibung", "Parameter zur Erkennung eines unerwarteten Lichtbogenabbruchs einstellen"
    "Erforderliche Parameter", "- ``checkEnable``: Erkennung aktivieren? 0 = nein, 1 = ja
    - ``arcInterruptTimeLength``: Bestätigungsdauer für Lichtbogenunterbrechung (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Parameter für die Wiederaufnahme nach Schweißunterbrechung abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetReWeldAfterBreakOffParam()``"
    "Beschreibung", "Parameter für die Wiederaufnahme nach Schweißunterbrechung abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``enable``: Wiederaufnahme aktiviert? 0 = nein, 1 = ja
    - ``length``: Überlappungslänge der Schweißnaht (mm)
    - ``velocity``: Geschwindigkeitsprozentsatz für die Rückkehr zum Wiederzündpunkt (0-100)
    - ``moveType``: Bewegungsart zum Wiederzündpunkt: 0 = LIN, 1 = PTP"

Parameter für die Wiederaufnahme nach Schweißunterbrechung einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetReWeldAfterBreakOffParam(enable, length, velocity, moveType)``"
    "Beschreibung", "Parameter für die Wiederaufnahme nach Schweißunterbrechung einstellen"
    "Erforderliche Parameter", "- ``enable``: Wiederaufnahme aktivieren? 0 = nein, 1 = ja
    - ``length``: Überlappungslänge der Schweißnaht (mm)
    - ``velocity``: Geschwindigkeitsprozentsatz für die Rückkehr zum Wiederzündpunkt (0-100)
    - ``moveType``: Bewegungsart zum Wiederzündpunkt: 0 = LIN, 1 = PTP"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweiterten DO-Port für Schweißgerät-Steuermodus einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeldMachineCtrlModeExtDoNum(DONum)``"
    "Beschreibung", "Erweiterten DO-Port für Schweißgerät-Steuermodus einstellen"
    "Erforderliche Parameter", "- ``DONum``: DO-Portnummer für Schweißgerät-Steuermodus (0-127)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißgerät-Steuermodus einstellen
++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeldMachineCtrlMode(mode, ioType)``"
    "Beschreibung", "Schweißmaschinen-Steuerungsmodus einstellen"
    "Erforderliche Parameter", "
    - ``ioType``: Steuerungstyp; 0-Steuerkasten-IO; 1-Digitales Kommunikationsprotokoll (UDP); 2-Digitales Kommunikationsprotokoll (ModbusTCP)
    - ``mode``: Schweißmaschinen-Steuerungsmodus; 0-Einknopf-Modus"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler-errcode"

Schweißstart
++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ARCStart(ioType, arcNum, timeout)``"
    "Beschreibung", "Schweißstart (Lichtbogen zünden)"
    "Erforderliche Parameter", "- ``ioType``: I/O-Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``arcNum``: Nummer der Schweißgeräte-Konfigurationsdatei
    - ``timeout``: Lichtbogenstart-Timeout (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißende
+++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ARCEnd(ioType, arcNum, timeout)``"
    "Beschreibung", "Schweißende (Lichtbogen löschen)"
    "Erforderliche Parameter", "- ``ioType``: I/O-Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``arcNum``: Nummer der Schweißgeräte-Konfigurationsdatei
    - ``timeout``: Lichtbogenlösch-Timeout (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Pendelstart
+++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveStart(weaveNum)``"
    "Beschreibung", "Pendelstart"
    "Erforderliche Parameter", "- ``weaveNum``: Konfigurationsnummer der Pendelparameter"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Pendelende
++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveEnd(weaveNum)``"
    "Beschreibung", "Pendelende"
    "Erforderliche Parameter", "- ``weaveNum``: Konfigurationsnummer der Pendelparameter"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Vorwärts-Drahtvorschub
++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetForwardWireFeed(ioType, wireFeed)``"
    "Beschreibung", "Vorwärts-Drahtvorschub"
    "Erforderliche Parameter", "- ``ioType``: I/O-Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``wireFeed``: Drahtvorschubsteuerung, 0 = stopp, 1 = vorschub"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Rückwärts-Drahtvorschub
+++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetReverseWireFeed(ioType, wireFeed)``"
    "Beschreibung", "Rückwärts-Drahtvorschub"
    "Erforderliche Parameter", "- ``ioType``: I/O-Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``wireFeed``: Drahtvorschubsteuerung, 0 = stopp, 1 = vorschub"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Gaszufuhr
+++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAspirated(ioType, airControl)``"
    "Beschreibung", "Gaszufuhr"
    "Erforderliche Parameter", "- ``ioType``: I/O-Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``airControl``: Gassteuerung, 0 = stopp, 1 = zu"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Wiederaufnahme des Schweißens nach Unterbrechung starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingStartReWeldAfterBreakOff()``"
    "Beschreibung", "Wiederaufnahme des Schweißens nach Unterbrechung starten"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißen nach Unterbrechung abbrechen
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.8

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingAbortWeldAfterBreakOff()``"
    "Beschreibung", "Schweißen nach Unterbrechung abbrechen (nicht wiederaufnehmen)"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Roboter-Schweißsteuerung
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.SetForwardWireFeed(0, 1)
    time.sleep(1)
    robot.SetForwardWireFeed(0, 0)
    robot.SetReverseWireFeed(0, 1)
    time.sleep(1)
    robot.SetReverseWireFeed(0, 0)
    robot.SetAspirated(0, 1)
    time.sleep(1)
    robot.SetAspirated(0, 0)
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint, tool=13, user=0)
    robot.ARCStart(1, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=p2Desc, tool=13, user=0)
    robot.ARCEnd(1, 0, 10000)
    robot.WeaveEnd(0)
    robot.WeldingStartReWeldAfterBreakOff()
    robot.WeldingAbortWeldAfterBreakOff()
    robot.CloseRPC()

Segment-Schweißen starten
+++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SegmentWeldStart(startDesePos, endDesePos, startJPos, endJPos, weldLength, noWeldLength, weldIOType, arcNum, weldTimeout, isWeave, weaveNum, tool, user, vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0, exaxis_pos=[0.0, 0.0, 0.0, 0.0], search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Beschreibung", "Segment-Schweißen starten (Heftschweißen / Intervallschweißen)"
    "Erforderliche Parameter", "- ``startDesePos``: Kartesische Pose des Startpunkts [mm, °]
    - ``endDesePos``: Kartesische Pose des Endpunkts [mm, °]
    - ``startJPos``: Gelenkposition des Startpunkts [°]
    - ``endJPos``: Gelenkposition des Endpunkts [°]
    - ``weldLength``: Länge des Schweißsegments (mm)
    - ``noWeldLength``: Länge des Nicht-Schweißsegments (mm)
    - ``weldIOType``: Schweiß-I/O-Typ, 0 = Steuerungs-I/O, 1 = Erweiterungs-I/O
    - ``arcNum``: Nummer der Schweißgeräte-Konfigurationsdatei
    - ``weldTimeout``: Lichtbogenstart/-lösch-Timeout (ms)
    - ``isWeave``: Pendeln verwenden? (True/False)
    - ``weaveNum``: Konfigurationsnummer der Pendelparameter
    - ``tool``: Werkzeugnummer [0~14]
    - ``user``: Werkstücknummer [0~14]"
    "Standardparameter", "- ``vel``: Geschwindigkeitsprozentsatz [0~100], Standard = 20.0
    - ``acc``: Beschleunigungsprozentsatz [0~100] (vorübergehend nicht freigegeben), Standard = 0.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor [0~100], Standard = 100.0
    - ``blendR``: [-1.0] = Bewegung abschließen (blockierend), [0~1000] = Glättungsradius (nicht blockierend) [mm], Standard = -1.0
    - ``exaxis_pos``: Position der externen Achsen 1 bis 4, Standard = [0.0, 0.0, 0.0, 0.0]
    - ``search``: [0] = keine Schweißdrahtsuche, [1] = Schweißdrahtsuche
    - ``offset_flag``: [0] = kein Versatz, [1] = Versatz im Basis-/Werkstückkoordinatensystem, [2] = Versatz im Werkzeugkoordinatensystem, Standard = 0
    - ``offset_pos``: Posenversatz [mm, °], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Robotersegment-Schweißen
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    rtn = robot.SegmentWeldStart(p1Desc, p2Desc, p1Joint, p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0)
    print(f"SegmentWeldStart rtn is {rtn}")
    robot.CloseRPC()

Simulations-Pendelstart
+++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveStartSim(weaveNum)``"
    "Beschreibung", "Simulations-Pendelstart"
    "Erforderliche Parameter", "- ``weaveNum``: Pendelparameternummer"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Simulations-Pendelende
++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveEndSim(weaveNum)``"
    "Beschreibung", "Simulations-Pendelende"
    "Erforderliche Parameter", "- ``weaveNum``: Pendelparameternummer"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Trajektorienprüfungs-Warnung starten (ohne Bewegung)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveInspectStart(weaveNum)``"
    "Beschreibung", "Trajektorienprüfungs-Warnung starten (ohne Bewegung)"
    "Erforderliche Parameter", "- ``weaveNum``: Pendelparameternummer"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Trajektorienprüfungs-Warnung beenden
+++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveInspectEnd(weaveNum)``"
    "Beschreibung", "Trajektorienprüfungs-Warnung beenden"
    "Erforderliche Parameter", "- ``weaveNum``: Pendelparameternummer"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Pendel-Gradientenstart
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveChangeStart(weaveChangeFlag, weaveNum, velStart, velEnd)``"
    "Beschreibung", "Pendel-Gradientenstart (allmähliche Änderung der Parameter)"
    "Erforderliche Parameter", "- ``weaveChangeFlag``: 1 = nur Pendelparameter ändern, 2 = Pendelparameter + Schweißgeschwindigkeit ändern
    - ``weaveNum``: Pendelnummer
    - ``velStart``: Start-Schweißgeschwindigkeit (cm/min)
    - ``velEnd``: End-Schweißgeschwindigkeit (cm/min)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für robotergestütztes Gradienten-Pendelschweißen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint, tool=13, user=0, vel=100)
    robot.WeaveStartSim(0)
    robot.MoveL(desc_pos=p2Desc, tool=13, user=0, vel=100)
    robot.WeaveEndSim(0)
    robot.MoveJ(joint_pos=p1Joint, tool=13, user=0, vel=100)
    robot.WeaveInspectStart(0)
    robot.MoveL(desc_pos=p2Desc, tool=13, user=0, vel=100)
    robot.WeaveInspectEnd(0)
    robot.WeldingSetVoltage(1, 19, 0, 0)
    robot.WeldingSetCurrent(1, 190, 0, 0)
    robot.MoveL(desc_pos=p1Desc, tool=1, user=1, vel=100, acc=100, ovl=50)
    robot.ARCStart(1, 0, 10000)
    robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(1, 0, 50, 30)
    robot.MoveL(desc_pos=p2Desc, tool=1, user=1, vel=100, acc=100, ovl=100)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.ARCEnd(1, 0, 10000)
    robot.CloseRPC()

Pendel-Gradientenende
+++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.9-3.7.9

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveChangeEnd()``"
    "Beschreibung", "Pendel-Gradientenende"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweitertes I/O - Gasprüfsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAirControlExtDoNum(DONum)``"
    "Beschreibung", "Erweitertes I/O - Gasprüfsignal für Schweißgerät konfigurieren"
    "Erforderliche Parameter", "- ``DONum``: Erweiterte DO-Nummer für Gasprüfsignal"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweitertes I/O - Lichtbogenstartsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetArcStartExtDoNum(DONum)``"
    "Beschreibung", "Erweitertes I/O - Lichtbogenstartsignal für Schweißgerät konfigurieren"
    "Erforderliche Parameter", "- ``DONum``: Erweiterte DO-Nummer für Lichtbogenstartsignal"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweitertes I/O - Rückwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWireReverseFeedExtDoNum(DONum)``"
    "Beschreibung", "Erweitertes I/O - Rückwärts-Drahtvorschubsignal für Schweißgerät konfigurieren"
    "Erforderliche Parameter", "- ``DONum``: Erweiterte DO-Nummer für Rückwärts-Drahtvorschubsignal"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweitertes I/O - Vorwärts-Drahtvorschubsignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWireForwardFeedExtDoNum(DONum)``"
    "Beschreibung", "Erweitertes I/O - Vorwärts-Drahtvorschubsignal für Schweißgerät konfigurieren"
    "Erforderliche Parameter", "- ``DONum``: Erweiterte DO-Nummer für Vorwärts-Drahtvorschubsignal"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweitertes I/O - Lichtbogen-Erfolgssignal für Schweißgerät konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetArcDoneExtDiNum(DINum)``"
    "Beschreibung", "Erweitertes I/O - Lichtbogen-Erfolgssignal für Schweißgerät konfigurieren"
    "Erforderliche Parameter", "- ``DINum``: Erweiterte DI-Nummer für Lichtbogen-Erfolgssignal"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweitertes I/O - Bereitschaftssignal für Schweißgerät konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeldReadyExtDiNum(DINum)``"
    "Beschreibung", "Erweitertes I/O - Bereitschaftssignal für Schweißgerät konfigurieren"
    "Erforderliche Parameter", "- ``DINum``: Erweiterte DI-Nummer für Bereitschaftssignal"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweitertes I/O - Signale für Wiederaufnahme nach Schweißunterbrechung konfigurieren
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExtDIWeldBreakOffRecover(reWeldDINum, abortWeldDINum)``"
    "Beschreibung", "Erweitertes I/O - Signale für Wiederaufnahme nach Schweißunterbrechung konfigurieren"
    "Erforderliche Parameter", "- ``reWeldDINum``: Erweiterte DI-Nummer für 'Wiederaufnahme starten'
    - ``abortWeldDINum``: Erweiterte DI-Nummer für 'Wiederaufnahme abbrechen'"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel zum Einstellen erweiterter I/O-Schweißsignale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetArcStartExtDoNum(10)
    print(f"SetArcStartExtDoNum rtn is {rtn}")
    rtn = robot.SetAirControlExtDoNum(20)
    print(f"SetAirControlExtDoNum rtn is {rtn}")
    rtn = robot.SetWireForwardFeedExtDoNum(30)
    print(f"SetWireForwardFeedExtDoNum rtn is {rtn}")
    rtn = robot.SetWireReverseFeedExtDoNum(40)
    rtn = robot.SetWeldReadyExtDiNum(50)
    print(f"SetWeldReadyExtDiNum rtn is {rtn}")
    rtn = robot.SetArcDoneExtDiNum(60)
    print(f"SetArcDoneExtDiNum rtn is {rtn}")
    rtn = robot.SetExtDIWeldBreakOffRecover(70, 80)
    print(f"SetExtDIWeldBreakOffRecover rtn is {rtn}")
    rtn = robot.SetWireSearchExtDIONum(0, 1)
    print(f"SetWireSearchExtDIONum rtn is {rtn}")
    robot.CloseRPC()

Lichtbogenverfolgungssteuerung (Arc Tracking)
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.9-3.7.9

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceControl(flag, delaytime, isLeftRight, klr, tStartLr, stepMaxLr, sumMaxLr, isUpLow, kud, tStartUd, stepMaxUd, sumMaxUd, axisSelect, referenceType, referSampleStartUd, referSampleCountUd, referenceCurrent, offsetType, offsetParameter)``"
    "Beschreibung", "Lichtbogenverfolgungssteuerung (Arc Tracking)"
    "Erforderliche Parameter", "- ``flag``: Schalter, 0 = aus, 1 = an
    - ``delaytime``: Verzögerungszeit (ms)
    - ``isLeftRight``: Links-Rechts-Abweichungskompensation aktivieren? 0 = nein, 1 = ja
    - ``klr``: Links-Rechts-Regelkoeffizient (Empfindlichkeit)
    - ``tStartLr``: Startzeit für Links-Rechts-Kompensation (Zyklen)
    - ``stepMaxLr``: Maximale Schrittweite Links-Rechts (mm)
    - ``sumMaxLr``: Maximale Gesamtkompensation Links-Rechts (mm)
    - ``isUpLow``: Oben-Unten-Abweichungskompensation aktivieren? 0 = nein, 1 = ja
    - ``kud``: Oben-Unten-Regelkoeffizient (Empfindlichkeit)
    - ``tStartUd``: Startzeit für Oben-Unten-Kompensation (Zyklen)
    - ``stepMaxUd``: Maximale Schrittweite Oben-Unten (mm)
    - ``sumMaxUd``: Maximale Gesamtkompensation Oben-Unten (mm)
    - ``axisSelect``: Koordinatensystem für Oben-Unten: 0 = Pendel, 1 = Werkzeug, 2 = Basis
    - ``referenceType``: Einstellungsart des Referenzstroms (Oben-Unten): 0 = Rückmeldung, 1 = Konstante
    - ``referSampleStartUd``: Startzähler für Abtastung des Referenzstroms (nur bei Rückmeldung) (Zyklen)
    - ``referSampleCountUd``: Anzahl der Abtastzyklen für Referenzstrom (nur bei Rückmeldung) (Zyklen)
    - ``referenceCurrent``: Konstanter Referenzstrom (nur bei referenceType=1) (mA)
    - ``offsetType``: Versatz-Tracking-Typ: 0 = kein Versatz, 1 = Abtastung, 2 = Prozentsatz
    - ``offsetParameter``: Versatzparameter: bei Abtastung (Startzeit der Versatzabtastung, standardmäßig ein Zyklus); bei Prozentsatz (Versatzprozentsatz -100 ~ 100)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

AI-Kanalwahl für Lichtbogenverfolgung
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceExtAIChannelConfig(channel)``"
    "Beschreibung", "AI-Kanalwahl für Lichtbogenverfolgung (Strom-/Spannungsrückmeldung?)"
    "Erforderliche Parameter", "- ``channel``: AI-Kanal [0-3]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung starten
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceReplayStart()``"
    "Beschreibung", "Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung starten"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung beenden
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceReplayEnd()``"
    "Beschreibung", "Kompensation für Mehrlagenschweißen mit Lichtbogenverfolgung beenden"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Koordinatentransformation für Versatz (Mehrlagenschweißen)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MultilayerOffsetTrsfToBase(pointO, pointX, pointZ, dx, dy, db)``"
    "Beschreibung", "Koordinatentransformation für Versatz (Mehrlagenschweißen)"
    "Erforderliche Parameter", "- ``pointO``: Kartesische Pose des Basispunkts (nur [x,y,z] werden verwendet)
    - ``pointX``: Kartesische Position eines Punkts in X-Richtung (nur [x,y,z])
    - ``pointZ``: Kartesische Position eines Punkts in Z-Richtung (nur [x,y,z])
    - ``dx``: Versatz in X-Richtung (mm)
    - ``dy``: Versatz in Y-Richtung (mm) # Hinweis: Im Original steht 'dz' für Z-Versatz, aber Parameter heißt 'dy'? Konsistenz prüfen.
    - ``db``: Rotation um Y-Achse (°)"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``offset``: Berechneter Versatz [x, y, z, rx, ry, rz]"

Codebeispiel für Lichtbogenverfolgung mit Mehrlagenschweißen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    mulitilineorigin1_joint = [-24.090, -63.501, 84.288, -111.940, -93.426, 57.669]
    mulitilineorigin1_desc = [-677.559, 190.951, -1.205, 1.144, -41.482, -82.577]
    mulitilineX1_desc = [-677.556, 211.949, -1.206]
    mulitilineZ1_desc = [-677.564, 190.956, 19.817]
    mulitilinesafe_joint = [-25.734, -63.778, 81.502, -108.975, -93.392, 56.021]
    mulitilinesafe_desc = [-677.561, 211.950, 19.812, 1.144, -41.482, -82.577]
    mulitilineorigin2_joint = [-29.743, -75.623, 101.241, -116.354, -94.928, 55.735]
    mulitilineorigin2_desc = [-563.961, 215.359, -0.681, 2.845, -40.476, -87.443]
    mulitilineX2_desc = [-563.965, 220.355, -0.680]
    mulitilineZ2_desc = [-563.968, 215.362, 4.331]
    epos = [0, 0, 0, 0]
    offset = [0, 0, 0, 0, 0, 0]
    time.sleep(0.01)
    error = robot.MoveJ(joint_pos=mulitilinesafe_joint, tool=13, user=0, vel=10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin1_desc, tool=13, user=0, vel=10, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos=mulitilinesafe_joint, tool=13, user=0, vel=10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin2_desc, tool=13, user=0, vel=10, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos=mulitilinesafe_joint, tool=13, user=0, vel=10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin1_desc, tool=13, user=0, vel=10, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error = robot.WeaveStart(0)
    print(f"WeaveStart return: {error}")
    error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10, 0, 0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin2_desc, tool=13, user=0, vel=1, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10, 0, 0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.WeaveEnd(0)
    print(f"WeaveEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos=mulitilinesafe_joint, tool=13, user=0, vel=10)
    print(f"MoveJ return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin1_desc, tool=13, user=0, vel=10, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin2_desc, tool=13, user=0, vel=2, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos=mulitilinesafe_joint, tool=13, user=0, vel=10)
    print(f"MoveJ return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin1_desc, tool=13, user=0, vel=10, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0)
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos=mulitilineorigin2_desc, tool=13, user=0, vel=2, speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 3000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos=mulitilinesafe_joint, tool=13, user=0, vel=10)
    print(f"MoveJ return: {error}")
    robot.CloseRPC()

AI-Kanalwahl für Lichtbogenverfolgung (Strom)
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceAIChannelCurrent(channel)``"
    "Beschreibung", "AI-Kanalwahl für Lichtbogenverfolgung (Stromrückmeldung)"
    "Erforderliche Parameter", "- ``channel``: Kanal: 0 = Erw. AI0, 1 = Erw. AI1, 2 = Erw. AI2, 3 = Erw. AI3, 4 = Steuerkasten AI0, 5 = Steuerkasten AI1"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

AI-Kanalwahl für Lichtbogenverfolgung (Spannung)
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceAIChannelVoltage(channel)``"
    "Beschreibung", "AI-Kanalwahl für Lichtbogenverfolgung (Spannungsrückmeldung)"
    "Erforderliche Parameter", "- ``channel``: Kanal: 0 = Erw. AI0, 1 = Erw. AI1, 2 = Erw. AI2, 3 = Erw. AI3, 4 = Steuerkasten AI0, 5 = Steuerkasten AI1"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Umrechnungsparameter für Stromrückmeldung (Lichtbogenverfolgung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceCurrentPara(AILow, AIHigh, currentLow, currentHigh)``"
    "Beschreibung", "Umrechnungsparameter für Stromrückmeldung (Lichtbogenverfolgung)"
    "Standardparameter", "- ``AILow``: Untere Grenze des AI-Kanals (Spannung) [V], Standard = 0, Bereich [0-10]
    - ``AIHigh``: Obere Grenze des AI-Kanals (Spannung) [V], Standard = 10, Bereich [0-10]
    - ``currentLow``: Schweißstromwert für untere AI-Grenze [A], Standard = 0, Bereich [0-200] (Einheit im Original 'V'? Vermutlich A)
    - ``currentHigh``: Schweißstromwert für obere AI-Grenze [A], Standard = 100, Bereich [0-200]"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Umrechnungsparameter für Spannungsrückmeldung (Lichtbogenverfolgung)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceVoltagePara(AILow, AIHigh, voltageLow, voltageHigh)``"
    "Beschreibung", "Umrechnungsparameter für Spannungsrückmeldung (Lichtbogenverfolgung)"
    "Standardparameter", "- ``AILow``: Untere Grenze des AI-Kanals (Spannung) [V], Standard = 0, Bereich [0-10]
    - ``AIHigh``: Obere Grenze des AI-Kanals (Spannung) [V], Standard = 10, Bereich [0-10]
    - ``voltageLow``: Schweißspannungswert für untere AI-Grenze [V], Standard = 0, Bereich [0-200]
    - ``voltageHigh``: Schweißspannungswert für obere AI-Grenze [V], Standard = 100, Bereich [0-200]"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Lichtbogenverfolgung
+++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')

    safetydescPose = [-504.043, 275.181, 40.908, -28.002, -42.025, -14.044]
    safetyjointPos = [-39.078, -76.732, 87.227, -99.47, -94.301, 18.714]
    startdescPose = [-473.86, 257.879, -20.849, -37.317, -42.021, 2.543]
    startjointPos = [-43.487, -76.526, 95.568, -104.445, -89.356, 3.72]
    enddescPose = [-499.844, 141.225, 7.72, -34.856, -40.17, 13.13]
    endjointPos = [-31.305, -82.998, 99.401, -104.426, -89.35, 3.696]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ---- Spannung einstellen
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ---- Strom einstellen
    rtn = robot.ArcWeldTraceAIChannelCurrent(4)
    print("ArcWeldTraceAIChannelCurrent rtn is", rtn)
    rtn = robot.ArcWeldTraceAIChannelVoltage(5)
    print("ArcWeldTraceAIChannelVoltage rtn is", rtn)
    rtn = robot.ArcWeldTraceCurrentPara(0, 5, 0, 500)
    print("ArcWeldTraceCurrentPara rtn is", rtn)
    rtn = robot.ArcWeldTraceVoltagePara(1.018, 10, 0, 50)
    print("ArcWeldTraceVoltagePara rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=20, acc=100)
    robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl=2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)
    robot.CloseRPC()

Erweiterte I/O-Ports für Schweißdrahtsuche einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWireSearchExtDIONum(searchDoneDINum, searchStartDONum)``"
    "Beschreibung", "Erweiterte I/O-Ports für Schweißdrahtsuche einstellen"
    "Erforderliche Parameter", "- ``searchDoneDINum``: Erweiterte DI-Nummer für 'Drahtsuche erfolgreich' (Eingang)
    - ``searchStartDONum``: Erweiterte DO-Nummer für 'Drahtsuche Start/Stopp' (Ausgang)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißdrahtsuche starten
+++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WireSearchStart(refPos, searchVel, searchDis, autoBackFlag, autoBackVel, autoBackDis, offectFlag)``"
    "Beschreibung", "Schweißdrahtsuche starten"
    "Erforderliche Parameter", "- ``refPos``: 1 = Referenzpunkt, 0 = Kontaktpunkt
    - ``searchVel``: Suchgeschwindigkeit (%)
    - ``searchDis``: Suchdistanz (mm)
    - ``autoBackFlag``: Automatische Rückkehr-Flag, 0 = nicht automatisch, 1 = automatisch
    - ``autoBackVel``: Geschwindigkeit der automatischen Rückkehr (%)
    - ``autoBackDis``: Distanz der automatischen Rückkehr (mm)
    - ``offectFlag``: 1 = Suche mit Versatz, 0 = Suche an Teachpunkt"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißdrahtsuche beenden
+++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WireSearchEnd(refPos, searchVel, searchDis, autoBackFlag, autoBackVel, autoBackDis, offectFlag)``"
    "Beschreibung", "Schweißdrahtsuche beenden"
    "Erforderliche Parameter", "- ``refPos``: 1 = Referenzpunkt, 2 = Kontaktpunkt
    - ``searchVel``: Suchgeschwindigkeit (%)
    - ``searchDis``: Suchdistanz (mm)
    - ``autoBackFlag``: Automatische Rückkehr-Flag, 0 = nicht automatisch, 1 = automatisch
    - ``autoBackVel``: Geschwindigkeit der automatischen Rückkehr (%)
    - ``autoBackDis``: Distanz der automatischen Rückkehr (mm)
    - ``offectFlag``: 1 = Suche mit Versatz, 2 = Suche an Teachpunkt"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißdrahtsuch-Versatz berechnen
+++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWireSearchOffset(seamType, method, varNameRef, varNameRes)``"
    "Beschreibung", "Schweißdrahtsuch-Versatz berechnen"
    "Erforderliche Parameter", "
    - ``seamType``: Schweißnahttyp
    - ``method``: Berechnungsmethode
    - ``varNameRef``: Liste der Referenzpunktnamen (1-6 Elemente), # für keinen Punkt
    - ``varNameRes``: Liste der Kontaktpunktnamen (1-6 Elemente), # für keinen Punkt"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``offsetFlag``: 0 = Versatz direkt zum Befehlspunkt addieren, 1 = Versatz erfordert Koordinatentransformation des Befehlspunkts
    - ``offset``: Berechneter Versatz [x, y, z, rx, ry, rz]"

Auf Abschluss der Schweißdrahtsuche warten
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WireSearchWait(varname)``"
    "Beschreibung", "Auf Abschluss der Schweißdrahtsuche warten"
    "Erforderliche Parameter", "- ``varName``: Name der Suche/Variable (z.B. 'RES0')"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißdrahtsuch-Kontaktpunkt in Datenbank schreiben
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetPointToDatabase(varName, pos)``"
    "Beschreibung", "Schweißdrahtsuch-Kontaktpunkt in Datenbank schreiben"
    "Erforderliche Parameter", "- ``varName``: Name des Kontaktpunkts (z.B. 'RES0' bis 'RES99')
    - ``pos``: Kontaktpunktdaten [x, y, z, rx, ry, rz]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für robotergestützte Schweißdrahtsuche
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    toolCoord = [0, 0, 200, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    wobjCoord = [0, 0, 0, 0, 0, 0]
    robot.SetWObjCoord(1, wobjCoord, 0)
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    descStart = [216.543, 445.175, 93.465, 179.683, 1.757, -112.641]
    jointStart = [-128.345, -86.660, 114.679, -119.625, -89.219, 74.303]
    descEnd = [111.143, 523.384, 87.659, 179.703, 1.835, -97.750]
    jointEnd = [-113.454, -81.060, 109.328, -119.954, -89.218, 74.302]
    error = robot.MoveL(desc_pos=descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    descREF0A = [142.135, 367.604, 86.523, 179.728, 1.922, -111.089]
    jointREF0A = [-126.794, -100.834, 128.922, -119.864, -89.218, 74.302]
    descREF0B = [254.633, 463.125, 72.604, 179.845, 2.341, -114.704]
    jointREF0B = [-130.413, -81.093, 112.044, -123.163, -89.217, 74.303]
    descREF1A = [92.556, 485.259, 47.476, -179.932, 3.130, -97.512]
    jointREF1A = [-113.231, -83.815, 119.877, -129.092, -89.217, 74.303]
    descREF1B = [203.103, 583.836, 63.909, 179.991, 2.854, -103.372]
    jointREF1B = [-119.088, -69.676, 98.692, -121.761, -89.219, 74.303]
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos=descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B, tool=1, user=1, vel=100, search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B, tool=1, user=1, vel=100, search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    varNameRef = ["REF0", "REF1", "#", "#", "#", "#"]
    varNameRes = ["RES0", "RES1", "#", "#", "#", "#"]
    offectFlag = 0
    offectPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error, offectFlag, offectPos = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes)
    print(f"GetWireSearchOffset return: {error}")
    error = robot.PointsOffsetEnable(0, offectPos)
    print(f"PointsOffsetEnable return: {error}")
    error = robot.MoveL(desc_pos= descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd, tool=1, user=1, vel=100, search=1)
    print(f"MoveL return: {error}")
    error = robot.PointsOffsetDisable()
    robot.CloseRPC()

Schweißspannungsgradienten starten
+++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltageGradualChangeStart(IOType, voltageStart, voltageEnd, AOIndex, blend)``"
    "Beschreibung", "Schweißspannungsgradienten starten"
    "Erforderliche Parameter", "- ``IOType``: Steuerungstyp: 0 = Steuerkasten-I/O, 1 = Digitalkommunikation (UDP), 2 = Digitalkommunikation (ModbusTCP)
    - ``voltageStart``: Start-Schweißspannung (V)
    - ``voltageEnd``: End-Schweißspannung (V)
    - ``AOIndex``: AO-Portnummer des Steuerkastens (0-1)
    - ``blend``: Glättung? 0 = nein, 1 = ja"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißspannungsgradienten beenden
+++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltageGradualChangeEnd()``"
    "Beschreibung", "Schweißspannungsgradienten beenden"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißstromgradienten starten
+++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrentGradualChangeStart(IOType, currentStart, currentEnd, AOIndex, blend)``"
    "Beschreibung", "Schweißstromgradienten starten (allmähliche Änderung)"
    "Erforderliche Parameter", "- ``IOType``: Steuerungstyp: 0 = Steuerkasten-I/O, 1 = Digitalkommunikation (UDP), 2 = Digitalkommunikation (ModbusTCP)
    - ``currentStart``: Start-Schweißstrom (A)
    - ``currentEnd``: End-Schweißstrom (A)
    - ``AOIndex``: AO-Portnummer des Steuerkastens (0-1)
    - ``blend``: Glättung? 0 = nein, 1 = ja"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Schweißstromgradienten beenden
+++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrentGradualChangeEnd()``"
    "Beschreibung", "Schweißstromgradienten beenden"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Schweißstrom- und Spannungsgradienten
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    startdescPose = [-484.707, 276.996, -14.013, -37.657, -40.508, -1.548]
    startjointPos = [-45.421, -75.673, 93.627, -104.302, -87.938, 6.005]
    enddescPose = [-508.767, 137.109, -13.966, -37.639, -40.508, -1.559]
    endjointPos = [-32.768, -80.947, 100.254, -106.201, -87.201, 18.648]
    safedescPose = [-484.709, 294.436, 13.621, -37.660, -40.508, -1.545]
    safejointPos = [-46.604, -75.410, 89.109, -100.003, -88.012, 4.823]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ---- Spannung einstellen
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ---- Strom einstellen
    robot.MoveJ(joint_pos=safejointPos, tool=1, user=0, vel=5, acc=100)
    rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0)
    print("WeldingSetCurrentGradualChangeStart rtn is", rtn)
    rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0)
    print("WeldingSetVoltageGradualChangeStart rtn is", rtn)
    rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    print("ArcWeldTraceControl rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=5, acc=100)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(2, 1, 24, 36)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl=2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.WeldingSetCurrentGradualChangeEnd()
    robot.WeldingSetVoltageGradualChangeEnd()

Benutzerdefinierte Pendelparameter einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomWeaveSetPara(id, pointNum, point, stayTime, frequency, incStayType, stationary)``"
    "Beschreibung", "Benutzerdefinierte Pendelparameter einstellen"
    "Erforderliche Parameter", "- ``id``: Benutzerdefinierte Pendelnummer: 0-2
    - ``pointNum``: Anzahl der Pendelpunkte (0-10)
    - ``point``: Liste der Bewegungspunkte (x, y, z) relativ zum Pfad, als flache Liste [x1,y1,z1, x2,y2,z2, ...]
    - ``stayTime``: Liste der Verweilzeiten an den Punkten [ms] (Länge pointNum)
    - ``frequency``: Pendelfrequenz [Hz]
    - ``incStayType``: Wartemodus: 0 = Zyklus ohne Wartezeit, 1 = Zyklus mit Wartezeit
    - ``stationary``: Position während Wartezeit: 0 = Bewegung wird fortgesetzt, 1 = Position ruht"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Benutzerdefinierte Pendelparameter abrufen
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomWeaveGetPara(id)``"
    "Beschreibung", "Benutzerdefinierte Pendelparameter abrufen"
    "Erforderliche Parameter", "- ``id``: Benutzerdefinierte Pendelnummer: 0-2"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``pointNum``: Anzahl der Pendelpunkte
    - ``point``: Liste der Bewegungspunkte (flache Liste)
    - ``stayTime``: Liste der Verweilzeiten
    - ``frequency``: Pendelfrequenz [Hz]
    - ``incStayType``: Wartemodus
    - ``stationary``: Position während Wartezeit"

Codebeispiel für benutzerdefinierte Pendelparameter
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    point = [0.0] * 30
    point[0] = -3.0
    point[1] = -3.0
    point[2] = 0.0
    point[3] = -6.0
    point[4] = 0.0
    point[5] = 0.0
    point[6] = -3.0
    point[7] = 3.0
    point[8] = 0.0
    point[9] = 0.0
    point[10] = 0.0
    point[11] = 0.0
    stayTime = [0.0] * 10
    rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0)
    print(f"CustomWeaveSetPara rtn is {rtn}")
    time.sleep(1)
    rtn, pointNum, point_out, stayTime_out, frequency, incStayType, stationary = robot.CustomWeaveGetPara(2)
    print(f"pointNum is {pointNum}")
    for i in range(pointNum):
        print(f"point {i}, point x y z {point[i * 3 + 0]},{point[i * 3 + 1]},{point[i * 3 + 2]}")
    print(f"fre is {frequency}, stay is {incStayType},{stationary}")
    robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000)
    desc_p1 = [-288.650, 367.807, 288.404, 0.000, -0.001, 0.001]
    desc_p2 = [-431.714, 367.815, 288.415, 0.001, 0.001, 0.000]
    desc_p3 = [-348.666, 427.798, 288.404, -0.000, -0.000, 0.001]
    j1 = [140.656, -84.560, -91.707, -93.734, 90.000, 50.655]
    j2 = [149.873, -98.298, -77.599, -94.103, 90.000, 59.873]
    j3 = [139.773, -96.173, -80.014, -93.814, 90.000, 49.772]
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.Circle(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50, oacc=10)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveC(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=desc_p2, tool=3, user=0, vel=100, ovl=10, speedPercent=100)
    robot.WeaveEnd(0)
    robot.CloseRPC()

Laserschweißgerät-Parameterkonfiguration
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingParam(self, num, scanSpeed, scanWidth, peakPower, dutyCycle, Freq, io_type=1)``"
    "Beschreibung", "Schreibt die Konfigurationsparameter einer der 10 Prozessgruppen des Laserschweißgeräts und konfiguriert sie dem Schweißgerät"
    "Erforderliche Parameter", "
    - ``io_type``: Kommunikationstyp 0-IO 1-UDP
    - ``Num``: Zu setzende Gruppennummer (1~10)
    - ``scanSpeed``: Scangeschwindigkeit
    - ``scanWidth``: Scanbreite
    - ``peakPower``: Spitzenleistung
    - ``dutyCycle``: Tastverhältnis
    - ``Freq``: Frequenz
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Laserschweißen Starten/Stoppen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingStartEnd(self, status, io_type=1, max_waittime=10000)``"
    "Beschreibung", "Startet/stoppt das Laserschweißgerät"
    "Erforderliche Parameter", "
    - ``io_type``: Kommunikationstyp 0-IO 1-UDP
    - ``status``: Steuerwort 0-Laser aus 1-Laser ein
    - ``max_waittime``: Maximale Wartezeit
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Laserschweißgerät Aktivieren/Deaktivieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingEnable(self, status, io_type=1)``"
    "Beschreibung", "Aktiviert/deaktiviert das Laserschweißgerät"
    "Erforderliche Parameter", "
    - ``io_type``: Kommunikationstyp 0-IO 1-UDP
    - ``status``: 0-deaktivieren 1-aktivieren
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Laserschweißgerät-Fehlerrücksetzung
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ResetLaserWeldingErr(self,status, io_type=1)``"
    "Beschreibung", "Laserschweißgerät-Fehlerrücksetzung"
    "Erforderliche Parameter", "
    - ``io_type``: Kommunikationstyp 0-IO 1-UDP
    - ``status``: Steuerwort 0-ungültig 1-Fehlerrücksetzung
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Betriebszustand des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingRunningState(self, io_type=1)``"
    "Beschreibung", "Ruft den Betriebszustand des Laserschweißgeräts ab"
    "Erforderliche Parameter", "
    - ``io_type``: Kommunikationstyp 0-IO 1-UDP
    - ``status``: Steuerwort 0-gestoppt 1-in Betrieb
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Fehlerzustand des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingErrState(self, io_type=1)``"
    "Beschreibung", "Ruft den Fehlerzustand des Laserschweißgeräts ab"
    "Erforderliche Parameter", "
    - ``io_type``: Kommunikationstyp 0-IO 1-UDP
    - ``status``: 0-kein Fehler 1-Fehler vorhanden
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Konfigurationsparameter des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingParamTarget(self, num)``"
    "Beschreibung", "Ruft die Konfigurationsparameter einer der 10 Prozessgruppen des Laserschweißgeräts ab"
    "Erforderliche Parameter", "
    - ``Num``: Zu setzende Gruppennummer (1~10)
    - ``scanSpeed``: Scangeschwindigkeit
    - ``scanWidth``: Scanbreite
    - ``peakPower``: Spitzenleistung
    - ``dutyCycle``: Tastverhältnis
    - ``Freq``: Frequenz
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Aktive Konfigurationsparameter des Laserschweißgeräts Abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingParamActual(self, io_type=1)``"
    "Beschreibung", "Ruft die aktuell aktiven Konfigurationsparameter des Laserschweißgeräts ab"
    "Erforderliche Parameter", "
    - ``io_type``: Kommunikationstyp 0-IO 1-UDP
    - ``scanSpeed``: Scangeschwindigkeit
    - ``scanWidth``: Scanbreite
    - ``peakPower``: Spitzenleistung
    - ``dutyCycle``: Tastverhältnis
    - ``Freq``: Frequenz
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Erweiterte IO-Aktivierungs-DO-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingEnableExtDoNum(self, ctrlModeDONum)``"
    "Beschreibung", "Konfiguriert den erweiterten IO-Aktivierungs-DO-Port für Laserschweißgerät"
    "Erforderliche Parameter", "
    - ``ctrlModeDONum``: Erweiterte DO-Portnummer für Laserschweißgerät-Aktivierung
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Erweiterte IO-Start-DO-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingStartExtDoNum(self, ctrlModeDONum)``"
    "Beschreibung", "Konfiguriert den erweiterten IO-Start-DO-Port für Laserschweißgerät"
    "Erforderliche Parameter", "
    - ``ctrlModeDONum``: Erweiterte DO-Portnummer für Laserschweißgerät-Start/Stopp
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Erweiterte IO-Fehlerrücksetzungs-DO-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingErrResetExtDoNum(self, ctrlModeDONum)``"
    "Beschreibung", "Konfiguriert den erweiterten IO-Fehlerrücksetzungs-DO-Port für Laserschweißgerät"
    "Erforderliche Parameter", "
    - ``ctrlModeDONum``: Erweiterte DO-Portnummer für Laserschweißgerät-Fehlerrücksetzung
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Erweiterte IO-Betriebszustands-(Laser-Ein-Zustands)-DI-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingRunningStateExtDiNum(self, diNum)``"
    "Beschreibung", "Konfiguriert den erweiterten IO-Betriebszustands-(Laser-Ein-Zustands)-DI-Port für Laserschweißgerät"
    "Erforderliche Parameter", "
    - ``diNum``: Erweiterte DI-Portnummer für Laserschweißgerät-Betriebszustand (Laser-Ein-Zustand)
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Erweiterte IO-Fehlerzustands-DI-Port für Laserschweißgerät Konfigurieren
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingErrStateExtDiNum(self, diNum)``"
    "Beschreibung", "Konfiguriert den erweiterten IO-Fehlerzustands-DI-Port für Laserschweißgerät"
    "Erforderliche Parameter", "
    - ``diNum``: Erweiterte DI-Portnummer für Laserschweißgerät-Fehlerzustand
    "
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode Erfolg-0 Fehler- errcode"

Beispielcode für Laserschweißen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    import time

    # Verbindung mit der Robotersteuerung herstellen, bei erfolgreicher Verbindung wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')

    def testLsaerWeld():
        robot.ExtDevLoadUDPDriver()
        time.sleep(1)

        robot.SetLaserWeldingParam(num = 3, scanSpeed = 2000, scanWidth = 3, peakPower = 1500, dutyCycle = 100, Freq = 1000, io_type=1)
        robot.SetLaserWeldingStartExtDoNum(ctrlModeDONum=1)

        robot.Mode(0)
        time.sleep(1)

        desc_pos1 = [-303.721, -206.960, 297.105, 152.209, 19.857, 109.166]
        desc_pos2 = [-301.575, -254.888, 284.786, 155.919, 26.946, 111.629]
        desc_safe = [-344.386, -280.830, 435.073, 173.835, 15.333, 124.931]
        jointPos1 = [9.827, -99.740, 120.088, -78.900, -77.241, -17.904]
        jointPos2 = [15.251, -96.456, 120.138, -84.664, -68.542, -17.843]
        jointSafe = [19.142, -98.078, 101.493, -83.078, -77.070, -17.794]

        error = robot.MoveL(desc_pos=desc_pos1,joint_pos=jointPos1, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(1, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_pos2, joint_pos=jointPos2, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(0, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_safe, joint_pos=jointSafe, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)

        robot.Mode(1)
        time.sleep(1)

        # Verbindung schließen
        robot.CloseRPC()
        time.sleep(1)

    # Testfunktion aufrufen
    testLsaerWeld()