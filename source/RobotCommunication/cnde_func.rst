CNDE-Funktionsbedienung
=======================

Eingangskonfiguration und Eingangsdaten
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Der Client sendet über CNDE Datenframes an den Roboter, um die Roboter-DO, -AO-Ausgänge, Eingangsregister usw. zu steuern. Vor dem Senden der Eingangsdaten muss der zu steuernde Funktionsinhalt konfiguriert werden. Tabelle 3-1 zeigt das Format des CNDE-Eingangskonfigurationsinhalts, einschließlich der Rezeptnummer und einer Reihe von Namen für die Eingangskonfigurationsfunktionen (Tabelle 1-2). Die entsprechende Tabelle 3-2 zeigt das Format des Eingangsdateninhalts, einschließlich der Rezeptnummer und der Eingangsdaten-Bytegruppe.

CNDE-Dateneingang unterstützt bis zu 8 Rezepte. Beim Senden von Eingangsdaten gleicht der Roboter die im empfangenen Datenpaket enthaltene Rezeptnummer mit der entsprechenden Rezept-Konfigurations-Funktionsnamengruppe ab, analysiert die Daten, um die Eingangsdatenwerte für jeden Funktionsnamen zu erhalten, und führt dann basierend auf den eingegebenen Daten die Robotersteuerungsoperation durch.

.. centered:: Tabelle 3-1 Format des Eingangskonfigurationsinhalts

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Bezeichnung**
     - **Rezeptnummer**
     - **Funktionsnamens-String**

   * - Länge (Byte)
     - 1
     - --

   * - Inhalt
     - 0 ~ 7
     - Eine Reihe von Namen der Eingangsdatenfunktionen

.. centered:: Tabelle 3-2 Format des Eingangsdateninhalts

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Bezeichnung**
     - **Rezeptnummer**
     - **Daten-Bytegruppe**

   * - Länge (Byte)
     - 1
     - --

   * - Inhalt
     - 0 ~ 7
     - Inhalt der Eingangsdaten

Bei der Eingangskonfiguration überprüft die Robotersteuerung nach Erhalt der Konfigurationsnamensgruppe jeden Namen. Wenn die konfigurierten Funktionsnamen korrekt sind, sendet der Roboter eine Rückmeldung mit den Datentypnamen aller konfigurierten Funktionen, getrennt durch ",". Wenn ein konfigurierter Funktionsname falsch ist, sendet der Roboter eine entsprechende Fehlermeldung zurück. Ein Beispiel für einen Eingangskonfigurations-Datenframe (hexadezimal) ist unten dargestellt:

.. image:: cnde/001.png
   :width: 6in
   :align: center

Die Gesamtlänge der konfigurierten Eingangsfunktionsnamensgruppe beträgt 54 Bytes, plus 1 Byte für die Eingangsrezeptnummer, insgesamt 55 Bytes. In Hexadezimal umgewandelt ergibt dies 0x0037, was im Little-Endian-Format im entsprechenden Eingangsdatenframe als Datenlänge "37 00" erscheint.

Zu diesem Zeitpunkt sendet der Roboter einen Datenframe vom Typ Zeichenketten-Hinweismeldung (Abschnitt 3.3.1 dieses Dokuments, Zeichenketten-Hinweismeldung) zurück:

.. image:: cnde/002.png
   :width: 6in
   :align: center

Der Nachrichtentyp "00" zeigt an, dass dies eine Erfolgsrückmeldung ist. Der Client kann den "Typ der Eingangsdatenkonfiguration" extrahieren und mit Tabelle 1-3 vergleichen, um die Bytelänge der Eingangskonfiguration zu erhalten. In diesem Beispiel beträgt die Gesamtdatenlänge 1*5 + 4*30 + 8*30 = 365 Bytes.

Wenn ein Eingangskonfigurationsname falsch ist:

.. image:: cnde/003.png
   :width: 6in
   :align: center

Die entsprechende Rückmeldung ist:

.. image:: cnde/004.png
   :width: 6in
   :align: center

Eingangsdaten können in einem festen Zyklus wiederholt oder nur bei Bedarf gesendet werden. Bei zyklischer Eingabe beträgt die schnellste vom Roboter verarbeitbare Periode 1 ms. Eine schnellere Eingabeperiode kann jedoch zu einem gewissen Mehraufwand für die Systemressourcen des Roboters führen. Es wird empfohlen, die Dateneingabeperiode basierend auf den tatsächlichen Gegebenheiten angemessen festzulegen.

Beim Senden von Datenframes an den Roboter gibt es keine Rückmeldung, es sei denn, die Länge des gesendeten Datenframes oder die Daten selbst sind anomal. Ein Beispiel für einen Eingangsdatenframe ist unten dargestellt, wobei die Nummer des Eingangsdatenrezepts und die Länge der Eingangsdaten-Bytegruppe mit der Eingangskonfiguration übereinstimmen sollten:

.. image:: cnde/005.png
   :width: 6in
   :align: center

Ausgangskonfiguration und Ausgangsdaten
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Der Client kann den Inhalt der Statusrückmeldung und den Rückmeldezyklus nach Bedarf anpassen, indem er den Roboterstatus über CNDE abruft. Die Verwendung der CNDE-Statusrückmeldung des Roboters erfordert die folgenden drei Schritte: ① Ausgangskonfiguration; ② Ausgang starten; ③ Ausgangsdaten empfangen.

Ausgangskonfiguration
+++++++++++++++++++++++

Der Ausgangskonfigurationsframe enthält den Ausgabezyklus und eine Gruppe von Ausgangsfunktionsnamen (alle konfigurierbaren Namen siehe Tabelle 1-1). Der Ausgabezyklus kann im Bereich von 1 ~ 200 ms konfiguriert werden. Die maximale Größe der Ausgangsdatenbytes beträgt 4096 Byte. Die Gruppe der Ausgangsfunktionsnamen ist eine Reihe von Ausgangsfunktionsnamen-Strings, die durch "," getrennt sind. Nachdem der Client den Ausgangskonfigurationsframe gesendet hat, überprüft der Roboter die konfigurierten Funktionsnamen. Wenn alle konfigurierten Funktionsnamen von der aktuellen CNDE des Roboters unterstützt werden, sendet der Roboter eine Reihe von durch "," getrennten Datentypkombinationen zurück; andernfalls, wenn die Überprüfung der Ausgangskonfigurationsnamen fehlschlägt, wird eine entsprechende Fehlermeldung zurückgesendet.

.. centered:: Tabelle 3-3 Inhalt der Ausgangskonfiguration

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Bezeichnung**
     - **Ausgabezyklus (ms)**
     - **Funktionsnamens-String**

   * - Länge (Byte)
     - 2
     - --

   * - Inhalt
     - 1-200
     - Gruppe der Ausgangsfunktionsnamen

Ein Beispiel für einen Ausgangskonfigurationsframe ist unten dargestellt:

.. image:: cnde/006.png
   :width: 6in
   :align: center

Die Gesamtlänge der konfigurierten Ausgangsfunktionsnamensgruppe beträgt 48 Bytes, plus 2 Bytes für den Ausgabezyklus, insgesamt 50 Bytes. In Hexadezimal umgewandelt ergibt dies 0x0032, was im Little-Endian-Format im entsprechenden Eingangsdatenframe als Datenlänge "32 00" erscheint.

Zu diesem Zeitpunkt sendet der Roboter einen Datenframe vom Typ Zeichenketten-Hinweismeldung (Abschnitt 3.3.1 dieses Dokuments, Zeichenketten-Hinweismeldung) zurück:

.. image:: cnde/007.png
   :width: 6in
   :align: center

Der Nachrichtentyp "00" zeigt an, dass dies eine Erfolgsrückmeldung ist. Der Client kann den "Typ der Ausgangsdatenkonfiguration" extrahieren und mit Tabelle 1-3 vergleichen, um die Bytelänge der Ausgangskonfiguration zu erhalten. In diesem Beispiel beträgt die Gesamtdatenlänge 1 + 8*10 + 4 = 85 Bytes.

Wenn ein Eingangskonfigurationsname falsch ist, z.B. "queue" fälschlicherweise als "quene" geschrieben:

.. image:: cnde/008.png
   :width: 6in
   :align: center

Die entsprechende Rückmeldung ist:

.. image:: cnde/009.png
   :width: 6in
   :align: center

Ausgang starten und stoppen
++++++++++++++++++++++++++++

Nach Abschluss der CNDE-Ausgangskonfiguration des Roboters sendet der Client den Befehl zum Starten der CNDE-Ausgabe. Der Roboter beginnt dann mit der Statusrückmeldungsausgabe gemäß dem konfigurierten Ausgabezyklus und -inhalt. Ebenso stoppt der Roboter die Statusrückmeldungsausgabe, wenn der CNDE-Stopp-Ausgabebefehl gesendet wird. Die CNDE-Start- und Stoppbefehle haben keinen Befehlsinhalt; die entsprechende Datenlänge beträgt 0.

.. centered:: Tabelle 3-4 Inhalt für CNDE-Ausgangsstart und -stopp

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Bezeichnung**
     - **Daten-Bytegruppe**

   * - Länge (Byte)
     - 0

   * - Inhalt
     - Kein Inhalt

Ein Beispiel für einen Datenframe zum Starten der CNDE-Ausgabe des Roboters ist unten dargestellt:

.. image:: cnde/010.png
   :width: 3in
   :align: center

Client empfängt Ausgangsdaten
+++++++++++++++++++++++++++++++

Nachdem die CNDE-Datenausgabe des Roboters gestartet wurde, benötigt der Client eine Schleife, um die vom Roboter zurückgemeldeten Dateninformationen zu empfangen. Die Empfangsfrequenz der Client-Schleife sollte höher sein als die konfigurierte Ausgangsdatenfrequenz, da sonst Datenverluste auftreten können. Der Inhalt der Roboter-Ausgangsdaten ist in Tabelle 3-5 dargestellt. Die Länge der Roboter-Ausgangsdaten-Bytegruppe ist die Summe der Bytelängen aller Funktionsdaten der Ausgangskonfiguration. Das Byte-Array ist eine 1-Byte-ausgerichtete Kombination aller Statusdaten in der Reihenfolge der konfigurierten Funktionen.

.. centered:: Tabelle 3-5 Inhalt der CNDE-Ausgangsdaten

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Bezeichnung**
     - **Daten-Bytegruppe**

   * - Länge (Byte)
     - --

   * - Inhalt
     - Ausgangsdaten-Bytegruppe

Ein Beispiel für einen Roboter-Ausgangsdatenframe ist unten dargestellt:

.. image:: cnde/011.png
   :width: 4in
   :align: center

CNDE-Hilfsfunktionen
~~~~~~~~~~~~~~~~~~~~~

Zeichenketten-Hinweismeldungen
+++++++++++++++++++++++++++++++

Client und Roboter können sich gegenseitig Zeichenketten-Hinweismeldungen über CNDE senden. Der Nachrichteninhalt umfasst den Nachrichtentyp und den Nachrichten-String (Tabelle 3-6), wobei die Definition der Nachrichtentypen in Tabelle 3-7 aufgeführt ist. Wenn der CNDE-Client Befehle wie Eingangskonfiguration, Ausgangskonfiguration, Ausgangsstart, Ausgangsstopp usw. an den Roboter sendet, antwortet der Roboter jeweils mit einer Zeichenketten-Hinweismeldung.

Wenn der oben genannte Befehl erfolgreich ausgeführt wird, sendet der Roboter eine Rückmeldung mit dem Nachrichtentyp "Erfolg", dem entsprechenden numerischen Code 0x00. Umgekehrt, wenn die Ausführung des oben genannten Befehls fehlschlägt, sendet der Roboter eine Rückmeldung mit dem Nachrichtentyp "Fehler", dem entsprechenden numerischen Code 0x03. Der Client kann anhand des zurückgemeldeten Nachrichtentyps das Ausführungsergebnis des Befehls beurteilen. Wenn der Nachrichtentyp "Fehler" ist, kann die Fehlermeldung extrahiert werden, um die Fehlerursache zu analysieren.

.. centered:: Tabelle 3-6 Inhalt der Zeichenketten-Hinweismeldung

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Bezeichnung**
     - **Nachrichtentyp**
     - **Nachrichten-String**

   * - Länge (Byte)
     - 1
     - --

   * - Inhalt
     - 0 ~ 4
     - Nachrichten-String

.. centered:: Tabelle 3-7 Roboter-CNDE-Zeichenketten-Hinweismeldungstypen

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Typ**
     - **Wert**

   * - Erfolg
     - 0x00

   * - Information
     - 0x01

   * - Warnung
     - 0x02

   * - Fehler
     - 0x03

   * - Störung
     - 0x04

Umschalten der CNDE-Protokollversionsnummer des Roboters
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Derzeit gibt es nur eine Version des Roboter-CNDE, die Versionsnummer lautet "FR-CNDE-V0001". Daher ist diese Funktion eine reservierte Funktion und wurde vorübergehend nicht freigegeben.

Abrufen von Informationen zur Software- und Firmwareversion des Roboters
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Der Client sendet über CNDE einen Befehl zum Abrufen von Software- und Firmwareversionsinformationen an den Roboter. Der Befehlsinhalt ist leer. Nach Erhalt der Anfrage sendet der Roboter eine Zeichenketten-Hinweismeldung zurück. Der Nachrichteninhalt enthält relevante Informationen wie Robotermodell, Roboter-Softwareversion, Roboter-Firmwareversion, Roboter-Hardwareversion usw.