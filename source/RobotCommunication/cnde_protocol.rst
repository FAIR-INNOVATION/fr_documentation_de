CNDE-Datenrahmen-Protokollformat
=================================

Das Kommunikationsprotokoll des kollaborativen Roboters CNDE ist wie folgt. Sowohl das Senden von Daten vom Client an den Roboter als auch die Rückmeldung von Daten vom Roboter an den Client müssen diesem Protokoll folgen. Das Protokoll unterscheidet Datenrahmen verschiedener Funktionen über den Rahmentyp. Die Definition der Rahmentypen ist in Tabelle 2-2 aufgeführt. Verschiedene Rahmentypen entsprechen unterschiedlichen Dateninhalten. Die spezifische Definition der Dateninhalte ist in den Tabellen 3-1 bis 3-7 dargestellt.

.. centered:: Tabelle 2-1 Format des Roboter-CNDE-Datenrahmens

.. list-table::
   :widths: 15 10 10 10 10 25 10
   :header-rows: 0
   :align: center
   :class: sheet-center-auto

   * - **Bezeichnung**
     - **Rahmenkopf**
     - **Rahmenzähler**
     - **Rahmentyp**
     - **Datenlänge**
     - **Inhalt**
     - **Rahmenende**
   
   * - **Länge (Byte)**
     - 2
     - 1
     - 1
     - 2
     - --
     - 2
   
   * - **Inhalt**
     - 0x5A5A
     - 0 ~ 255
     - 0 ~ 8
     - Anzahl der Bytes des "Dateninhalts"
     - Inhalt des Datenrahmens
     - 0xA5A5

.. centered:: Tabelle 2-2 Typen der Roboter-CNDE-Datenrahmen

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Typ**
     - **Wert**
     - **Richtung des Datenrahmens**

   * - Eingangskonfigurationsrahmen (Steuerungskonfiguration)
     - 0x00
     - Client -> Roboter

   * - Ausgangskonfigurationsrahmen (Statuskonfiguration)
     - 0x01
     - Client -> Roboter

   * - CNDE-Ausgangsstart
     - 0x02
     - Client -> Roboter

   * - CNDE-Ausgangsstopp
     - 0x03
     - Client -> Roboter

   * - Ausgangsdatenrahmen (Statusdaten)
     - 0x04
     - Roboter -> Client

   * - Eingangsdatenrahmen (Steuerdaten)
     - 0x05
     - Client -> Roboter

   * - Zeichenketten-Hinweismeldung
     - 0x06
     - Client -> Roboter, Roboter -> Client

   * - Einstellen der CNDE-Protokollversionsnummer des Roboters
     - 0x07
     - Client -> Roboter

   * - Abrufen der Software-/Firmware-Version des Roboters
     - 0x08
     - Client -> Roboter, Roboter -> Client