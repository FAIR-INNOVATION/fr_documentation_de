Erweiterungsachsen
==================

.. toctree::
    :maxdepth: 5

Parameter für 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetParam(servoId, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio)``"
    "Beschreibung", "Parameter für 485-Erweiterungsachse einstellen"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    - ``servoCompany``: Hersteller des Servoantriebs, 1-Dynatec
    - ``servoModel``: Modell des Servoantriebs, 1-FD100-750C
    - ``servoSoftVersion``: Softwareversion des Servoantriebs, 1-V1.0
    - ``servoResolution``: Encoderauflösung
    - ``axisMechTransRatio``: Mechanisches Übersetzungsverhältnis"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Konfigurationsparameter für 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetParam(servoId)``"
    "Beschreibung", "Konfigurationsparameter für 485-Erweiterungsachse abrufen"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``servoCompany``: Hersteller des Servoantriebs, 1-Dynatec
    - ``servoModel``: Modell des Servoantriebs, 1-FD100-750C
    - ``servoSoftVersion``: Softwareversion des Servoantriebs, 1-V1.0
    - ``servoResolution``: Encoderauflösung
    - ``axisMechTransRatio``: Mechanisches Übersetzungsverhältnis"

485-Erweiterungsachse aktivieren/deaktivieren
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoEnable(servoId, status)``"
    "Beschreibung", "485-Erweiterungsachse aktivieren/deaktivieren"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    - ``status``: Aktivierungsstatus, 0 = deaktivieren, 1 = aktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Steuerungsmodus für 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetControlMode(servoId, mode)``"
    "Beschreibung", "Steuerungsmodus für 485-Erweiterungsachse einstellen"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    - ``mode``: Steuerungsmodus, 0 = Positionsmodus, 1 = Geschwindigkeitsmodus"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Zielposition für 485-Erweiterungsachse einstellen (Positionsmodus)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetTargetPos(servoId, pos, speed)``"
    "Beschreibung", "Zielposition für 485-Erweiterungsachse einstellen (Positionsmodus)"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    - ``pos``: Zielposition, mm oder °
    - ``speed``: Zielgeschwindigkeit, mm/s oder °/s"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Zieldrehmoment für 485-Erweiterungsachse einstellen (Drehmomentmodus) - vorübergehend nicht freigegeben
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetTargetTorque(servoId, torque)``"
    "Beschreibung", "Zieldrehmoment für 485-Erweiterungsachse einstellen (Drehmomentmodus)"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    - ``torque``: Zieldrehmoment, Nm"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

485-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoHoming(servoId, mode, searchVel, latchVel)``"
    "Beschreibung", "485-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    - ``mode``: Referenzfahrmodus, 1 = aktuelle Position als Nullpunkt, 2 = Referenzfahrt zum negativen Endschalter, 3 = Referenzfahrt zum positiven Endschalter
    - ``searchVel``: Suchgeschwindigkeit, mm/s oder °/s
    - ``latchVel``: Einrastgeschwindigkeit, mm/s oder °/s"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Fehlerinformationen der 485-Erweiterungsachse löschen
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoClearError(servoId)``"
    "Beschreibung", "Fehlerinformationen der 485-Erweiterungsachse löschen"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Servostatus der 485-Erweiterungsachse abrufen
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetStatus(servoId)``"
    "Beschreibung", "Servostatus der 485-Erweiterungsachse abrufen"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``servoErrCode``: Fehlercode des Servoantriebs
    - ``servoState``: Status des Servoantriebs. Bit0: 0 = nicht aktiviert, 1 = aktiviert; Bit1: 0 = nicht in Bewegung, 1 = in Bewegung; Bit2: 0 = positiver Endschalter nicht ausgelöst, 1 = ausgelöst; Bit3: 0 = negativer Endschalter nicht ausgelöst, 1 = ausgelöst; Bit4: 0 = Positionierung nicht abgeschlossen, 1 = abgeschlossen; Bit5: 0 = Referenzfahrt nicht durchgeführt, 1 = abgeschlossen
    - ``servoPos``: Aktuelle Servoposition, mm oder °
    - ``servoSpeed``: Aktuelle Servogeschwindigkeit, mm/s oder °/s
    - ``servoTorque``: Aktuelles Servodrehmoment, Nm"

Zielgeschwindigkeit für 485-Erweiterungsachse einstellen (Geschwindigkeitsmodus)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetTargetSpeed(servoId, speed)``"
    "Beschreibung", "Zielgeschwindigkeit für 485-Erweiterungsachse einstellen (Geschwindigkeitsmodus)"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID
    - ``speed``: Zielgeschwindigkeit, mm/s oder °/s"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Datenachsnummer für 485-Erweiterungsachse in Statusrückmeldung einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.3

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServosetStatusID(servoId)``"
    "Beschreibung", "Datenachsnummer für 485-Erweiterungsachse in Statusrückmeldung einstellen"
    "Erforderliche Parameter", "- ``servoId``: Servoantriebs-ID, Bereich [1-15], entspricht der Slave-ID"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetAcc(acc, dec)``"
    "Beschreibung", "Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse einstellen"
    "Erforderliche Parameter", "- ``acc``: Bewegungsbeschleunigung der 485-Erweiterungsachse
    - ``dec``: Bewegungsverzögerung der 485-Erweiterungsachse"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetEmergencyStopAcc(acc, dec)``"
    "Beschreibung", "Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse einstellen"
    "Erforderliche Parameter", "- ``acc``: Not-Halt-Beschleunigung der 485-Erweiterungsachse
    - ``dec``: Not-Halt-Verzögerung der 485-Erweiterungsachse"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetAcc()``"
    "Beschreibung", "Bewegungsbeschleunigung und -verzögerung für 485-Erweiterungsachse abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``acc``: Bewegungsbeschleunigung der 485-Erweiterungsachse
    - ``dec``: Bewegungsverzögerung der 485-Erweiterungsachse"

Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetEmergencyStopAcc()``"
    "Beschreibung", "Not-Halt-Beschleunigung und -Verzögerung für 485-Erweiterungsachse abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``acc``: Not-Halt-Beschleunigung der 485-Erweiterungsachse
    - ``dec``: Not-Halt-Verzögerung der 485-Erweiterungsachse"

Codebeispiel für die Steuerung von Erweiterungsachsen
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45)
    print(f"AuxServoSetParam is: {retval}")
    servoCompany = 0
    servoModel = 0
    servoSoftVersion = 0
    servoResolution = 0
    axisMechTransRatio = 0.0
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14)
    print(f"AuxServoSetParam is: {retval}")
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36)
    print(f"AuxServoSetParam is: {retval}")
    time.sleep(3)
    robot.AuxServoSetAcc(3000, 3000)
    robot.AuxServoSetEmergencyStopAcc(5000, 5000)
    time.sleep(1)
    emagacc = 0.0
    emagdec = 0.0
    acc = 0.0
    dec = 0.0
    error,emagacc, emagdec = robot.AuxServoGetEmergencyStopAcc()
    print(f"emergency acc is {emagacc}  dec is {emagdec}")
    error,acc, dec = robot.AuxServoGetAcc()
    print(f"acc is {acc}  dec is {dec}")
    robot.AuxServoSetControlMode(1, 0)
    time.sleep(2)
    retval = robot.AuxServoEnable(1, 0)
    print(f"AuxServoEnable disenable {retval}")
    time.sleep(1)
    servoErrCode = 0
    servoState = 0
    servoPos = 0.0
    servoSpeed = 0.0
    servoTorque = 0.0
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoEnable(1, 1)
    print(f"AuxServoEnable enable {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoHoming(1, 1, 5, 1,100)
    print(f"AuxServoHoming {retval}")
    time.sleep(3)
    retval = robot.AuxServoSetTargetPos(1, 200, 30,100)
    print(f"AuxServoSetTargetPos {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoSpeed {servoSpeed}")
    time.sleep(8)
    robot.AuxServoSetControlMode(1, 1)
    time.sleep(2)
    robot.AuxServoEnable(1, 0)
    time.sleep(1)
    robot.AuxServoEnable(1, 1)
    time.sleep(1)
    robot.AuxServoSetTargetSpeed(1, 100, 80)
    time.sleep(5)
    robot.AuxServoSetTargetSpeed(1, 0, 80)
    robot.CloseRPC()

Konfiguration der UDP-Kommunikationsparameter für Erweiterungsachsen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevSetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum, selfConnect)``"
    "Beschreibung", "Konfiguration der UDP-Kommunikationsparameter für Erweiterungsachsen"
    "Erforderliche Parameter", "
    - ``ip``: IP-Adresse der SPS
    - ``port``: Portnummer
    - ``period``: Kommunikationszyklus (ms, vorübergehend nicht freigegeben)
    - ``lossPkgTime``: Paketverlust-Erkennungszeit (ms)
    - ``lossPkgNum``: Anzahl der Paketverluste
    - ``disconnectTime``: Zeitdauer zur Bestätigung einer Kommunikationsunterbrechung
    - ``reconnectEnable``: Automatische Wiederverbindung bei Kommunikationsunterbrechung aktivieren: 0 = deaktivieren, 1 = aktivieren
    - ``reconnectPeriod``: Intervall für Wiederverbindungsversuche (ms)
    - ``reconnectNum``: Anzahl der Wiederverbindungsversuche
    - ``selfConnect``: Automatische Verbindungsherstellung nach Stromausfall/Neustart: 0 = keine Verbindung herstellen, 1 = Verbindung herstellen"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

UDP-Kommunikationsparameter für Erweiterungsachsen abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevGetUDPComParam()``"
    "Beschreibung", "UDP-Kommunikationsparameter für Erweiterungsachsen abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "
    - Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``ip``: IP-Adresse der SPS
    - ``port``: Portnummer
    - ``period``: Kommunikationszyklus (ms)
    - ``lossPkgTime``: Paketverlust-Erkennungszeit (ms)
    - ``lossPkgNum``: Anzahl der Paketverluste
    - ``disconnectTime``: Zeitdauer zur Bestätigung einer Kommunikationsunterbrechung
    - ``reconnectEnable``: Automatische Wiederverbindung aktiviert; 0 = nein, 1 = ja
    - ``reconnectPeriod``: Intervall für Wiederverbindungsversuche (ms)
    - ``reconnectNum``: Anzahl der Wiederverbindungsversuche
    - ``selfConnect``: Automatische Wiederverbindung nach Neustart des Steuerkastens; 0-keine Wiederverbindung; 1-Wiederverbindung
    "

UDP-Kommunikation laden
+++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevLoadUDPDriver()``"
    "Beschreibung", "UDP-Kommunikation laden"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

UDP-Kommunikation entladen
++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevUnloadUDPDriver()``"
    "Beschreibung", "UDP-Kommunikation entladen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Verbindung nach UDP-Kommunikationsabbruch für Erweiterungsachsen wiederherstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevUDPClientComReset()``"
    "Beschreibung", "Verbindung nach UDP-Kommunikationsabbruch für Erweiterungsachsen wiederherstellen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kommunikation nach UDP-Kommunikationsabbruch für Erweiterungsachsen schließen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevUDPClientComClose()``"
    "Beschreibung", "Kommunikation nach UDP-Kommunikationsabbruch für Erweiterungsachsen schließen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Parameterkonfiguration für UDP-Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisParamConfig(axisId, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType)``"
    "Beschreibung", "Parameterkonfiguration für UDP-Erweiterungsachsen"
    "Erforderliche Parameter", "
    - ``axisId``: Achsnummer [1-4]
    - ``axisType``: Erweiterungsachstyp: 0 = translatorisch, 1 = rotatorisch
    - ``axisDirection``: Richtung der Erweiterungsachse: 0 = positive Richtung, 1 = negative Richtung
    - ``axisMax``: Maximale Position der Achse (mm)
    - ``axisMin``: Minimale Position der Achse (mm)
    - ``axisVel``: Geschwindigkeit (mm/s)
    - ``axisAcc``: Beschleunigung (mm/s²)
    - ``axisLead``: Spindelsteigung (mm)
    - ``encResolution``: Encoderauflösung
    - ``axisOffect``: Versatz der Erweiterungsachse am Schweißstartpunkt
    - ``axisCompany``: Hersteller des Antriebs: 1 = Hechuan, 2 = Huichuan, 3 = Panasonic
    - ``axisModel``: Modell des Antriebs: 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Huichuan-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    - ``axisEncType``: Encodertyp: 0 = inkrementell, 1 = absolut"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Position des Roboters relativ zur Erweiterungsachse einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotPosToAxis(installType)``"
    "Beschreibung", "Position des Roboters relativ zur Erweiterungsachse einstellen"
    "Erforderliche Parameter", "- ``installType``: 0 = Roboter ist auf der externen Achse montiert, 1 = Roboter ist außerhalb der externen Achse montiert"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

DH-Parameterkonfiguration für Erweiterungsachssystem einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxisDHParaConfig(axisConfig, axisDHd1, axisDHd2, axisDHd3, axisDHd4, axisDHa1, axisDHa2, axisDHa3, axisDHa4)``"
    "Beschreibung", "DH-Parameterkonfiguration für Erweiterungsachssystem einstellen"
    "Erforderliche Parameter", "- ``axisConfig``: Konfiguration der externen Achse: 0 = Ein-Freiheitsgrad-Linearschiene, 1 = Zwei-Freiheitsgrad-L-Positionierer, 2 = Drei-Freiheitsgrade, 3 = Vier-Freiheitsgrade, 4 = Ein-Freiheitsgrad-Positionierer
    - ``axisDHd1``: DH-Parameter d1 (mm)
    - ``axisDHd2``: DH-Parameter d2 (mm)
    - ``axisDHd3``: DH-Parameter d3 (mm)
    - ``axisDHd4``: DH-Parameter d4 (mm)
    - ``axisDHa1``: DH-Parameter a1 (mm)
    - ``axisDHa2``: DH-Parameter a2 (mm)
    - ``axisDHa3``: DH-Parameter a3 (mm)
    - ``axisDHa4``: DH-Parameter a4 (mm)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

UDP-Erweiterungsachse aktivieren
++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisServoOn(axisID, status)``"
    "Beschreibung", "UDP-Erweiterungsachse aktivieren"
    "Erforderliche Parameter", "- ``axisID``: Achsnummer [1-4]
    - ``status``: 0 = deaktivieren, 1 = aktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

UDP-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSetHoming(axisID, mode, searchVel, latchVel)``"
    "Beschreibung", "UDP-Erweiterungsachse auf Nullpunkt fahren (Referenzfahrt)"
    "Erforderliche Parameter", "
    - ``axisID``: Achsnummer [1-4]
    - ``mode``: Referenzfahrmodus: 0 = aktuelle Position als Nullpunkt, 1 = Referenzfahrt zum negativen Endschalter, 2 = Referenzfahrt zum positiven Endschalter
    - ``searchVel``: Suchgeschwindigkeit (mm/s)
    - ``latchVel``: Einrastgeschwindigkeit (mm/s)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

UDP-Erweiterungsachse Tippbetrieb starten
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisStartJog(axisID, direction, vel, acc, maxDistance)``"
    "Beschreibung", "UDP-Erweiterungsachse Tippbetrieb starten"
    "Erforderliche Parameter", "
    - ``axisID``: Achsnummer [1-4]
    - ``direction``: Drehrichtung: 0 = negativ, 1 = positiv
    - ``vel``: Geschwindigkeit (mm/s)
    - ``acc``: Beschleunigung (mm/s²)
    - ``maxDistance``: Maximale Tippdistanz"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

UDP-Erweiterungsachse Tippbetrieb stoppen
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisStopJog(axisID)``"
    "Beschreibung", "UDP-Erweiterungsachse Tippbetrieb stoppen"
    "Erforderliche Parameter", "- ``axisID``: Achsnummer [1-4]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für Konfiguration und Tippbetrieb von UDP-Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
    print(f"ExtDevSetUDPComParam rtn is {rtn}")
    ip = ""
    port = 0
    period = 0
    lossPkgTime = 0
    lossPkgNum = 0
    disconnectTime = 0
    reconnectEnable = 0
    reconnectPeriod = 0
    reconnectNum = 0
    rtn,[ip, port, period, lossPkgTime, lossPkgNum,disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum] = robot.ExtDevGetUDPComParam()
    param_str = (f"\nip {ip}\nport {port}\nperiod {period}\nlossPkgTime {lossPkgTime}"
                 f"\nlossPkgNum {lossPkgNum}\ndisConntime {disconnectTime}"
                 f"\nreconnecable {reconnectEnable}\nreconnperiod {reconnectPeriod}"
                 f"\nreconnnun {reconnectNum}")
    print(f"ExtDevGetUDPComParam rtn ist {rtn}{param_str}")
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
    rtn = robot.ExtAxisServoOn(2, 1)
    print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    print(f"ExtAxisSetHoming rtn is {rtn}")
    time.sleep(4)
    rtn = robot.SetRobotPosToAxis(1)
    print(f"SetRobotPosToAxis rtn is {rtn}")
    rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0)
    print(f"SetAxisDHParaConfig rtn ist {rtn}")
    rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig Achse 1 rtn ist {rtn}")
    rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")
    time.sleep(3)
    robot.ExtAxisStartJog(1, 0, 10, 10, 30)
    time.sleep(1)
    robot.ExtAxisStopJog(1)
    time.sleep(3)
    robot.ExtAxisServoOn(1, 0)
    time.sleep(3)
    robot.ExtAxisStartJog(2, 0, 10, 10, 30)
    time.sleep(1)
    robot.ExtAxisStopJog(2)
    time.sleep(3)
    robot.ExtAxisServoOn(2, 0)
    robot.ExtDevUnloadUDPDriver()
    robot.CloseRPC()

Referenzpunkt für Koordinatensystem der Erweiterungsachse einstellen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSetRefPoint(pointNum)``"
    "Beschreibung", "Referenzpunkt für Koordinatensystem der Erweiterungsachse einstellen - Vier-Punkt-Methode"
    "Erforderliche Parameter", "- ``pointNum``: Punktnummer [1-4]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Koordinatensystem der Erweiterungsachse berechnen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisComputeECoordSys()``"
    "Beschreibung", "Koordinatensystem der Erweiterungsachse berechnen - Vier-Punkt-Methode"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Werte des Erweiterungsachsen-Koordinatensystems [x, y, z, rx, ry, rz]"

Referenzpunkt für Positionierer-Koordinatensystem einstellen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PositionorSetRefPoint(pointNum)``"
    "Beschreibung", "Referenzpunkt für Positionierer-Koordinatensystem einstellen - Vier-Punkt-Methode"
    "Erforderliche Parameter", "- ``pointNum``: Punktnummer [1-4]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Koordinatensystem des Positionierers berechnen - Vier-Punkt-Methode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PositionorComputeECoordSys()``"
    "Beschreibung", "Koordinatensystem des Positionierers berechnen - Vier-Punkt-Methode"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Werte des Positionierer-Koordinatensystems [x, y, z, rx, ry, rz]"

Pose des Kalibrierungsreferenzpunkts im Endeffektor-Koordinatensystem des Positionierers einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRefPointInExAxisEnd(pos)``"
    "Beschreibung", "Pose des Kalibrierungsreferenzpunkts im Endeffektor-Koordinatensystem des Positionierers einstellen"
    "Erforderliche Parameter", "- ``pos``: Posenwerte [x, y, z, rx, ry, rz]"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Koordinatensystem der Erweiterungsachse anwenden
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisActiveECoordSys(applyAxisId, axisCoordNum, coord, calibFlag)``"
    "Beschreibung", "Koordinatensystem der Erweiterungsachse anwenden"
    "Erforderliche Parameter", "
    - ``applyAxisId``: Erweiterungsachsennummer. Bit0-Bit3 entsprechen den Achsnummern 1-4, z.B. für Achse 1 und 3: 0b00000101 = 5
    - ``axisCoordNum``: Nummer des Erweiterungsachsen-Koordinatensystems
    - ``coord``: Werte des Koordinatensystems [x, y, z, rx, ry, rz]
    - ``calibFlag``: Kalibrierungsflag: 0 = nein, 1 = ja"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Koordinatensystem der Erweiterungsachse abrufen
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisGetCoord()``"
    "Beschreibung", "Koordinatensystem der Erweiterungsachse abrufen"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``coord``: Werte des Erweiterungsachsen-Koordinatensystems [x, y, z, rx, ry, rz]"

Codebeispiel für die Kalibrierung des Erweiterungsachsen-Koordinatensystems
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
    print(f"ExtDevSetUDPComParam rtn is {rtn}")
    rtn,udp_params = robot.ExtDevGetUDPComParam()
    ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum = udp_params
    patam = (
        f"\nip {ip}\nport {port}\nperiod {period}\nlossPkgTime {lossPkgTime}\n"
        f"lossPkgNum {lossPkgNum}\ndisConntime {disconnectTime}\nreconnecable {reconnectEnable}\n"
        f"reconnperiod {reconnectPeriod}\nreconnnun {reconnectNum}"
    )
    print(f"ExtDevGetUDPComParam rtn is {rtn}{patam}")
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    print(f"ExtAxisServoOn Achse 1 rtn ist {rtn}")
    rtn = robot.ExtAxisServoOn(2, 1)
    print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    print(f"ExtAxisSetHoming rtn is {rtn}")
    time.sleep(4)
    rtn = robot.SetRobotPosToAxis(1)
    print(f"SetRobotPosToAxis rtn is {rtn}")
    rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0)
    print(f"SetAxisDHParaConfig rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 1 rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")
    toolCoord = [0, 0, 210, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    jSafe = [115.193, -96.149, 92.489, -87.068, -89.15, -83.488]
    j1 = [117.559, -92.624, 100.329, -96.909, -94.057, -83.488]
    j2 = [112.239, -90.096, 99.282, -95.909, -89.824, -83.488]
    j3 = [110.839, -83.473, 93.166, -89.22, -90.499, -83.487]
    j4 = [107.935, -83.572, 95.424, -92.873, -87.933, -83.488]
    descSafe = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc1 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc2 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc3 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc4 = [0.0,0.0,0.0,0.0,0.0,0.0]
    exaxisPos = [0.0,0.0,0.0,0.0]
    offdese = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, descSafe = robot.GetForwardKin(jSafe)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    error, desc1 = robot.GetForwardKin(j1)
    robot.MoveJ(joint_pos=j1,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    actualTCPPos = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, actualTCPPos = robot.GetActualTCPPose(0)
    robot.SetRefPointInExAxisEnd(actualTCPPos)
    rtn = robot.PositionorSetRefPoint(1)
    print(f"PositionorSetRefPoint 1 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc2 = robot.GetForwardKin(j2)
    rtn = robot.MoveJ(joint_pos=j2,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(2)
    print(f"PositionorSetRefPoint 2 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc3 = robot.GetForwardKin(j3)
    robot.MoveJ(joint_pos=j3,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(3)
    print(f"PositionorSetRefPoint 3 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc4 = robot.GetForwardKin(j4)
    robot.MoveJ(joint_pos=j4,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(4)
    print(f"PositionorSetRefPoint 4 rtn is {rtn}")
    time.sleep(2)
    axisCoord = [0.0,0.0,0.0,0.0,0.0,0.0]
    error,axisCoord = robot.PositionorComputeECoordSys()
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    print(f"PositionorComputeECoordSys rtn is {axisCoord[0]} {axisCoord[1]} {axisCoord[2]} {axisCoord[3]} {axisCoord[4]} {axisCoord[5]}")
    rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1)
    print(f"ExtAxisActiveECoordSys rtn is {rtn}")
    robot.CloseRPC()

UDP-Erweiterungsachse bewegen
+++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisMove(pos, ovl, blend=-1)``"
    "Beschreibung", "UDP-Erweiterungsachse bewegen"
    "Erforderliche Parameter", "- ``pos = [exaxis[0], exaxis[1], exaxis[2], exaxis[3]]``: Zielpositionen der Achsen 1 bis 4
    - ``ovl``: Geschwindigkeitsprozentsatz"
    "Standardparameter", "- ``blend``: Glättungsparameter (mm oder ms), -1 = auf Bewegungsende warten (blockierend), Standard = -1"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für die Bewegung von UDP-Erweiterungsachsen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Verbindung zur Robotersteuerung herstellen, bei Erfolg wird ein Roboterobjekt zurückgegeben
    robot = Robot.RPC('192.168.58.2')
    axisPos = [20,0,0,0]
    robot.ExtAxisMove(axisPos, 50, -1)
    robot.CloseRPC()

Synchronbewegung von UDP-Erweiterungsachse und Roboter-Gelenkbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSyncMoveJ(joint_pos, tool, user, exaxis_pos, desc_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0, blendT=-1.0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Beschreibung", "Synchronbewegung von UDP-Erweiterungsachse und Roboter-Gelenkbewegung"
    "Erforderliche Parameter", "
    - ``joint_pos``: Ziel-Gelenkposition [°]
    - ``desc_pos``: Ziel-Kartesische Pose [mm, °]
    - ``tool``: Werkzeugnummer [0~14]
    - ``user``: Werkstücknummer [0~14]
    - ``exaxis_pos``: Position der externen Achsen 1 bis 4"
    "Standardparameter", "
    - ``desc_pos``: Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0] (bei Standardwert wird die Vorwärtskinematik verwendet)
    - ``vel``: Geschwindigkeitsprozentsatz [0~100], Standard = 20.0
    - ``acc``: Beschleunigungsprozentsatz [0~100] (vorübergehend nicht freigegeben), Standard = 0.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor [0~100], Standard = 100.0
    - ``blendT``: [-1.0] = Bewegung abschließen (blockierend), [0~500.0] = Glättungszeit (nicht blockierend) [ms], Standard = -1.0
    - ``offset_flag``: [0] = kein Versatz, [1] = Versatz im Basis-/Werkstückkoordinatensystem, [2] = Versatz im Werkzeugkoordinatensystem, Standard = 0
    - ``offset_pos``: Posenversatz [mm, °], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für synchronen Gelenkbewegung mit Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    # UDP-Kommunikationsparameter einstellen und laden
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Parameter für Erweiterungsachsen einstellen
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Erweiterungsachse aktivieren und Referenzfahrt durchführen
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Koordinatensystem der Erweiterungsachse kalibrieren
    pos = []  # Bitte hier die Kalibrierungspunktkoordinaten eintragen
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Dieser Vorgang muss 4 Mal (mit 4 Punkten) wiederholt werden
    error, coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Start- und Endpunkt der Synchronbewegung
    startdescPose = []  # Bitte hier die Koordinaten eintragen
    startjointPos = []  # Bitte hier die Koordinaten eintragen
    startexaxisPos = []  # Bitte hier die Koordinaten eintragen
    enddescPose = []  # Bitte hier die Koordinaten eintragen
    endjointPos = []  # Bitte hier die Koordinaten eintragen
    endexaxisPos = []  # Bitte hier die Koordinaten eintragen
    # Zum Startpunkt bewegen
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos,tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0,offset_flag= 0,offset_pos= offdese)
    robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, endexaxisPos, 100, 100, 100, -1, 0, offdese)
    robot.CloseRPC()

Synchronbewegung von UDP-Erweiterungsachse und Roboter-Linearbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSyncMoveL(desc_pos, tool, user, exaxis_pos, joint_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0, search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], config=-1)``"
    "Beschreibung", "Synchronbewegung von UDP-Erweiterungsachse und Roboter-Linearbewegung"
    "Erforderliche Parameter", "
    - ``desc_pos``: Ziel-Kartesische Pose [mm, °]
    - ``tool``: Werkzeugnummer [0~14]
    - ``user``: Werkstücknummer [0~14]
    - ``exaxis_pos``: Position der externen Achsen 1 bis 4"
    "Standardparameter", "
    - ``joint_pos``: Ziel-Gelenkposition [°], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0] (bei Standardwert wird die inverse Kinematik verwendet)
    - ``vel``: Geschwindigkeitsprozentsatz [0~100], Standard = 20.0
    - ``acc``: Beschleunigungsprozentsatz [0~100] (vorübergehend nicht freigegeben), Standard = 0.0
    - ``ovl``: Geschwindigkeitsskalierungsfaktor [0~100], Standard = 100.0
    - ``blendR``: [-1.0] = Bewegung abschließen (blockierend), [0~500.0] = Glättungszeit (nicht blockierend) [ms], Standard = -1.0
    - ``search``: [0] = keine Schweißdrahtsuche, [1] = Schweißdrahtsuche
    - ``offset_flag``: [0] = kein Versatz, [1] = Versatz im Basis-/Werkstückkoordinatensystem, [2] = Versatz im Werkzeugkoordinatensystem, Standard = 0
    - ``offset_pos``: Posenversatz [mm, °], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    - ``config``: Konfiguration des Gelenkraums für inverse Kinematik, [-1] = Berechnung basierend auf aktueller Gelenkposition, [0~7] = Berechnung basierend auf spezifischer Gelenkraumkonfiguration, Standard = -1"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für synchronen Linearbewegung mit Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    # UDP-Kommunikationsparameter einstellen und laden
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Parameter für Erweiterungsachsen einstellen
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Erweiterungsachse aktivieren und Referenzfahrt durchführen
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Koordinatensystem der Erweiterungsachse kalibrieren
    pos = []  # Bitte hier die Kalibrierungspunktkoordinaten eintragen
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Muss 4 Mal aufgerufen werden
    error, coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Start- und Endpunkt der Synchronbewegung
    startdescPose = []  # Bitte Koordinaten eintragen
    startjointPos = []  # Bitte Koordinaten eintragen
    startexaxisPos = []  # Bitte Koordinaten eintragen
    enddescPose = []  # Bitte Koordinaten eintragen
    endjointPos = []  # Bitte Koordinaten eintragen
    endexaxisPos = []  # Bitte Koordinaten eintragen
    # Zum Startpunkt bewegen
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=1, vel=100, acc=100, ovl=100, exaxis_pos=startexaxisPos, blendT=0)
    # Synchron-Linearbewegung ausführen
    robot.ExtAxisSyncMoveL(desc_pos=enddescPose, tool=1, user=1, exaxis_pos=endexaxisPos, vel=100, acc=100, ovl=100, blendR=0, offset_flag=0, offset_pos=offdese)
    robot.CloseRPC()

Synchronbewegung von UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSyncMoveC(desc_pos_p, tool_p, user_p, exaxis_pos_p, desc_pos_t, tool_t, user_t, exaxis_pos_t, joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_p=20.0, acc_p=100.0, offset_flag_p=0, offset_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=100.0, offset_flag_t=0, offset_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], ovl=100.0, blendR=-1.0, config=-1)``"
    "Beschreibung", "Synchronbewegung von UDP-Erweiterungsachse und Roboter-Kreisbogenbewegung"
    "Erforderliche Parameter", "
    - ``desc_pos_p``: Kartesische Pose des Zwischenpunkts [mm, °]
    - ``tool_p``: Werkzeugnummer für Zwischenpunkt [0~14]
    - ``user_p``: Werkstücknummer für Zwischenpunkt [0~14]
    - ``exaxis_pos_p``: Position der externen Achsen am Zwischenpunkt
    - ``desc_pos_t``: Kartesische Pose des Zielpunkts [mm, °]
    - ``tool_t``: Werkzeugnummer für Zielpunkt [0~14]
    - ``user_t``: Werkstücknummer für Zielpunkt [0~14]
    - ``exaxis_pos_t``: Position der externen Achsen am Zielpunkt"
    "Standardparameter", "
    - ``joint_pos_p``: Gelenkposition des Zwischenpunkts [°], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0] (inverse Kinematik wird verwendet)
    - ``joint_pos_t``: Gelenkposition des Zielpunkts [°], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0] (inverse Kinematik wird verwendet)
    - ``vel_p``: Geschwindigkeitsprozentsatz für Zwischenpunkt [0~100], Standard = 20.0
    - ``acc_p``: Beschleunigungsprozentsatz für Zwischenpunkt [0~100] (vorübergehend nicht freigegeben), Standard = 100.0
    - ``offset_flag_p``: Versatz für Zwischenpunkt: [0] = kein Versatz, [1] = Versatz im Basis-/Werkstückkoordinatensystem, [2] = Versatz im Werkzeugkoordinatensystem, Standard = 0
    - ``offset_pos_p``: Posenversatz für Zwischenpunkt [mm, °], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    - ``vel_t``: Geschwindigkeitsprozentsatz für Zielpunkt [0~100], Standard = 20.0
    - ``acc_t``: Beschleunigungsprozentsatz für Zielpunkt [0~100] (vorübergehend nicht freigegeben), Standard = 100.0
    - ``offset_flag_t``: Versatz für Zielpunkt: [0] = kein Versatz, [1] = Versatz im Basis-/Werkstückkoordinatensystem, [2] = Versatz im Werkzeugkoordinatensystem, Standard = 0
    - ``offset_pos_t``: Posenversatz für Zielpunkt [mm, °], Standard = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    - ``ovl``: Geschwindigkeitsskalierungsfaktor [0~100], Standard = 100.0
    - ``blendR``: [-1.0] = Bewegung abschließen (blockierend), [0~1000] = Glättungsradius (nicht blockierend) [mm], Standard = -1.0
    - ``config``: Konfiguration des Gelenkraums für inverse Kinematik, [-1] = Berechnung basierend auf aktueller Gelenkposition, [0~7] = Berechnung basierend auf spezifischer Gelenkraumkonfiguration, Standard = -1"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für synchronen Kreisbogenbewegung mit Erweiterungsachse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    # UDP-Kommunikationsparameter einstellen und laden
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Parameter für Erweiterungsachsen einstellen
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Erweiterungsachse aktivieren und Referenzfahrt durchführen
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Koordinatensystem der Erweiterungsachse kalibrieren
    pos = []  # Bitte hier die Kalibrierungspunktkoordinaten eintragen
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Muss 4 Mal aufgerufen werden
    error, coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Start-, Zwischen- und Endpunkt der Synchronbewegung
    startdescPose = []  # Bitte Koordinaten eintragen
    startjointPos = []  # Bitte Koordinaten eintragen
    startexaxisPos = []  
    middescPose = []  
    midjointPos = []  
    midexaxisPos = []  
    enddescPose = []  
    endjointPos = []  
    endexaxisPos = []  
    # Zum Startpunkt bewegen
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=1, vel=100, acc=100, ovl=100, exaxis_pos=startexaxisPos, blendT=0, offset_flag=0, offset_pos=offdese)
    # Synchron-Kreisbogenbewegung starten
    robot.ExtAxisSyncMoveC(desc_pos_p=middescPose, tool_p=1, user_p=1, exaxis_pos_p=midexaxisPos,
                           desc_pos_t=enddescPose, tool_t=1, user_t=1, exaxis_pos_t=endexaxisPos,
                           vel_p=100, acc_p=100, offset_flag_p=0, offset_pos_p=offdese,
                           vel_t=100, acc_t=100, offset_flag_t=0, offset_pos_t=offdese,
                           ovl=100, blendR=0)
    robot.CloseRPC()

Erweiterten Digitalausgang (DO) setzen
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxDO(DONum, bOpen, smooth, block)``"
    "Beschreibung", "Erweiterten Digitalausgang (DO) setzen"
    "Erforderliche Parameter", "
    - ``DONum``: DO-Nummer
    - ``bOpen``: Schaltzustand: True = ein, False = aus
    - ``smooth``: Glättung aktivieren: True = ja, False = nein
    - ``block``: Blockierend ausführen: True = ja, False = nein"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Erweiterten Analogausgang (AO) setzen
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxAO(AONum, value, block)``"
    "Beschreibung", "Erweiterten Analogausgang (AO) setzen"
    "Erforderliche Parameter", "
    - ``AONum``: AO-Nummer
    - ``value``: Analogwert [0-4095]
    - ``block``: Blockierend ausführen: True = ja, False = nein"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Eingangsfilterzeit für erweiterten Digitaleingang (DI) einstellen
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxDIFilterTime(filterTime)``"
    "Beschreibung", "Eingangsfilterzeit für erweiterten Digitaleingang (DI) einstellen"
    "Erforderliche Parameter", "- ``filterTime``: Filterzeit (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Eingangsfilterzeit für erweiterten Analogeingang (AI) einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxAIFilterTime(AINum, filterTime)``"
    "Beschreibung", "Eingangsfilterzeit für erweiterten Analogeingang (AI) einstellen"
    "Erforderliche Parameter", "
    - ``AINum``: AI-Nummer
    - ``filterTime``: Filterzeit (ms)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Auf erweiterten Digitaleingang (DI) warten
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitAuxDI(DINum, bOpen, time, errorAlarm)``"
    "Beschreibung", "Auf erweiterten Digitaleingang (DI) warten"
    "Erforderliche Parameter", "
    - ``DINum``: DI-Nummer
    - ``bOpen``: Erwarteter Zustand: True = ein, False = aus
    - ``time``: Maximale Wartezeit (ms)
    - ``errorAlarm``: Bewegung bei Timeout fortsetzen: True = ja, False = nein (Fehler auslösen)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Auf erweiterten Analogeingang (AI) warten
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitAuxAI(AINum, sign, value, time, errorAlarm)``"
    "Beschreibung", "Auf erweiterten Analogeingang (AI) warten"
    "Erforderliche Parameter", "
    - ``AINum``: AI-Nummer
    - ``sign``: Bedingung: 0 = größer als, 1 = kleiner als
    - ``value``: Vergleichswert
    - ``time``: Maximale Wartezeit (ms)
    - ``errorAlarm``: Bewegung bei Timeout fortsetzen: True = ja, False = nein (Fehler auslösen)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Wert des erweiterten Digitaleingangs (DI) abrufen
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAuxDI(DINum, isNoBlock)``"
    "Beschreibung", "Wert des erweiterten Digitaleingangs (DI) abrufen"
    "Erforderliche Parameter", "
    - ``DINum``: DI-Nummer
    - ``isNoBlock``: Nicht-blockierend: True = ja, False = blockierend"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``isOpen``: 0 = aus, 1 = ein"

Wert des erweiterten Analogeingangs (AI) abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAuxAI(AINum, isNoBlock)``"
    "Beschreibung", "Wert des erweiterten Analogeingangs (AI) abrufen"
    "Erforderliche Parameter", "
    - ``AINum``: AI-Nummer
    - ``isNoBlock``: Nicht-blockierend: True = ja, False = blockierend"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``value``: Eingangswert"

Codebeispiel für erweiterten I/O
++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    for i in range(128):
        robot.SetAuxDO(i, True, False, True)
        time.sleep(0.1)
    for i in range(128):
        robot.SetAuxDO(i, False, False, True)
        time.sleep(0.1)
    for i in range(409):
        value1 = i * 10
        value2 = 4095 - i * 10
        robot.SetAuxAO(0, value1, True)
        robot.SetAuxAO(1, value2, True)
        robot.SetAuxAO(2, value1, True)
        robot.SetAuxAO(3, value2, True)
        time.sleep(0.01)
    robot.SetAuxDIFilterTime(10)
    robot.SetAuxAIFilterTime(0, 10)
    for i in range(20):
        curValue = False
        error, curValue = robot.GetAuxDI(i, False)  # Hinweis: Referenzübergabe je nach Bibliotheksimplementierung anpassen
        print(f"DI{i}   {curValue}")
    curValue = -1
    for i in range(4):
        error, curValue = robot.GetAuxAI(i, True)  # Hinweis: Referenzübergabe je nach Bibliotheksimplementierung anpassen
        print(f"AI{i}   {curValue}")
    robot.WaitAuxDI(1, False, 1000, False)
    robot.WaitAuxAI(1, 1, 132, 1000, False)
    robot.CloseRPC()

Mobile Basis aktivieren (z.B. fahrerloses Transportfahrzeug)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorEnable(enable)``"
    "Beschreibung", "Mobile Basis aktivieren"
    "Erforderliche Parameter", "- ``enable``: Aktivierungsstatus: 0 = deaktivieren, 1 = aktivieren"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Mobile Basis auf Nullpunkt fahren (Referenzfahrt)
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorHoming()``"
    "Beschreibung", "Mobile Basis auf Nullpunkt fahren (Referenzfahrt)"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Linearbewegung der mobilen Basis
++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorMoveL(distance, vel)``"
    "Beschreibung", "Linearbewegung der mobilen Basis"
    "Erforderliche Parameter", "- ``distance``: Lineare Bewegungsdistanz (mm)
    - ``vel``: Geschwindigkeitsprozentsatz für Linearbewegung (0-100)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Kreisbogenbewegung der mobilen Basis
++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorMoveC(radius, angle, vel)``"
    "Beschreibung", "Kreisbogenbewegung der mobilen Basis"
    "Erforderliche Parameter", "- ``radius``: Radius der Kreisbogenbewegung (mm)
    - ``angle``: Winkel der Kreisbogenbewegung (°)
    - ``vel``: Geschwindigkeitsprozentsatz für Kreisbogenbewegung (0-100)"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Mobile Basis anhalten
+++++++++++++++++++++
.. versionadded:: Python SDK-v2.0.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramStop()``"
    "Beschreibung", "Mobile Basis anhalten"
    "Erforderliche Parameter", "Keine"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für mobile Basis
+++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1)
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    rtn = robot.ExtAxisServoOn(2, 1)
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    time.sleep(4)
    robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0)
    robot.TractorEnable(False)
    time.sleep(2)
    robot.TractorEnable(True)
    time.sleep(2)
    robot.TractorHoming()
    time.sleep(2)
    robot.TractorMoveL(100, 2)
    time.sleep(5)
    robot.TractorStop()
    robot.TractorMoveL(-100, 20)
    time.sleep(5)
    robot.TractorMoveC(300, 90, 20)
    time.sleep(10)
    robot.TractorMoveC(300, -90, 20)
    time.sleep(1)
    robot.CloseRPC()

Punkt des Lasersensors aufzeichnen
++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserRecordPoint(coordID)``"
    "Beschreibung", "Punkt des Lasersensors aufzeichnen (nach erfolgreicher Suche)"
    "Erforderliche Parameter", "- ``coordID``: Koordinatensystem des Lasersensors"
    "Standardparameter", "Keine"
    "Rückgabewert", "- Fehlercode: 0 = Erfolg, sonst Fehlercode
    - ``joint``: Gelenkposition des erkannten Punktes [°]
    - ``desc``: Kartesische Position des erkannten Punktes [mm, °]
    - ``exaxis``: Position der Erweiterungsachse am erkannten Punkt [mm]"

Codebeispiel zum Aufzeichnen eines Laserpunkts
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.4

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    direction_point = [0, 0, 0]
    rtn = robot.LaserTrackingSearchStart(2, direction_point, 10, 100, 10000, 2)
    print(f"LaserTrackingSearchStart rtn ist {rtn}")
    robot.LaserTrackingSearchStop()
    coord_id = 2
    rtn, joint, desc, exaxis = robot.LaserRecordPoint(coord_id)
    print(f"rtn is {rtn}")
    print(f"desc_pos:{desc[0]},{desc[1]},{desc[2]},"
          f"{desc[3]},{desc[4]},{desc[5]}")
    print(f"joint_pos:{joint[0]},{joint[1]},{joint[2]},{joint[3]},{joint[4]},{joint[5]}")
    print(f"exaxis pos is {exaxis[0]} {exaxis[1]} {exaxis[2]} {exaxis[3]}")
    off = [0] * 6
    robot.MoveJ(joint,tool=1,user=0,vel=100,acc=100,ovl=50,exaxis_pos=exaxis,blendT=-1,offset_flag=0,offset_pos=off)
    robot.CloseRPC()

Strategie für die Synchronbewegung von Erweiterungsachse und Roboter einstellen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.5

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExAxisRobotPlan(strategy)``"
    "Beschreibung", "Strategie für die Synchronbewegung von Erweiterungsachse und Roboter einstellen"
    "Erforderliche Parameter", "- ``strategy``: Strategie: 0 = Roboter ist führend, 1 = Erweiterungsachse und Roboter synchron"
    "Standardparameter", "Keine"
    "Rückgabewert", "Fehlercode: 0 = Erfolg, sonst Fehlercode"

Codebeispiel für die Synchronbewegungsstrategie
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Verbindung zur Robotersteuerung herstellen
    robot = Robot.RPC('192.168.58.2')
    joint_pos1 = [-22.016, -49.217, 124.714, -161.100, -85.108, -0.333]
    joint_pos2 = [-21.083, -46.613, 110.079, -147.796, -80.757, -0.330]
    joint_pos3 = [-25.572, -60.090, 135.397, -163.889, -82.489, -0.345]
    desc_pos1 = [2.637, -0.001, 30.673, 178.786, -4.134, 68.326]
    desc_pos2 = [213.812, -1.440, 47.311, 177.410, 0.166, 68.946]
    desc_pos3 = [444.342, -12.723, 82.470, -177.701, -1.325, 65.151]
    epos1 = [0.001, 0.000, 0.000, 0.000]
    epos2 = [299.977, 0.000, 0.000, 0.000]
    epos3 = [399.969, 0.000, 0.000, 0.000]
    offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.SetExAxisRobotPlan(0)
    print(f"SetExAxisRobotPlan rtn is {rtn}")
    time.sleep(1)
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos1,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos1,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 1 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos2,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos2,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 2 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos3,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos3,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 3 rtn is {rtn}")
    time.sleep(8)
    robot.CloseRPC()
