WebApp Zugriff und Anmeldung
============================

.. toctree::
   :maxdepth: 6

Aufrufen der WebApp-Anmeldeschnittstelle
----------------------------------------

1. Schalten Sie das Steuerpult ein und verbinden Sie es per Netzwerkkabel mit einem PC.
2. Öffnen Sie auf dem PC den Chrome-Browser und rufen Sie die Ziel-IP-Adresse 192.168.58.2 auf.
3. Geben Sie Benutzernamen und Passwort ein und klicken Sie auf "Anmelden", um sich in der WebApp anzumelden.

Der initiale Benutzername ist "admin", das Passwort "123".

.. figure:: teaching_pendant_software/001.png
   :width: 6in
   :align: center

.. centered:: Abbildung 2.1‑1 Anmeldeoberfläche

Einführung in die WebApp-Oberfläche
------------------------------------

Nach erfolgreicher Anmeldung gelangt das System in die "Startoberfläche". Diese enthält hauptsächlich:

1. FAIRINO Logo;
2. Schaltfläche zum Ein-/Ausblenden der Menüleiste;
3. Menüleiste;
4. Roboter-Steuerungsbereich;
5. Roboter-Statusbereich;
6. 3D-Roboter-Simulation – 3D-Szenenbedienung;
7. 3D-Roboter-Simulation – Bedienung des Roboterarms;
8. Zusatzfunktionen des Roboters;
9. Status des Roboters und der Zusatzfunktionen.

Die folgende Abbildung zeigt die schematische Darstellung der System-Startoberfläche:

.. image:: teaching_pendant_software/002.png
   :align: center
   :width: 6in

.. centered:: Abbildung 2.2‑1 Schematische Darstellung der System-Startoberfläche

Steuerungsbereich
~~~~~~~~~~~~~~~~~~

.. note::
   .. image:: teaching_pendant_software/064.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Teach-Programm öffnen"**

   Funktion: Öffnet ein Teach-Programm für die Programmierung, grafische Programmierung oder Knotenpunkt-Programmierung.

.. note::
   .. image:: teaching_pendant_software/003.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Enable" (Freigabe)**

   Funktion: Aktiviert den Roboter (Einschalten der Motoren).

.. note::
   .. image:: teaching_pendant_software/004.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Start"**

   Funktion: Lädt das Teach-Programm hoch und startet dessen Ausführung.

.. note::
   .. image:: teaching_pendant_software/005.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Stopp"**

   Funktion: Stoppt die Ausführung des aktuellen Teach-Programms.

.. note::
   .. image:: teaching_pendant_software/006.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Pause/Fortsetzen"**

   Funktion: Pausiert und setzt das aktuelle Teach-Programm fort.

.. important::
   Ein Pause-Befehl am Ende des Programms kann nicht verarbeitet werden.

Statusleiste
~~~~~~~~~~~~

.. note::
   .. image:: teaching_pendant_software/011.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Roboter-Fehlerstatus**

   Funktion: Zeigt an, dass aktuell ein Fehler im Roboterbetrieb vorliegt. Bei keinem Fehler ausgeblendet.

.. note::
   .. image:: teaching_pendant_software/007.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Roboterstatus**

   Funktion: Stopped – Gestoppt, Running – Läuft, Pause – Pausiert, Drag – Manuelles Führen (Drag & Teach).

.. note::
   .. image:: teaching_pendant_software/010.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Roboter-Werkzeugkoordinatensystem, Werkstückkoordinatensystem, erweitertes Achskoordinatensystem und Lastkennung**

   Funktion: Oben links – Aktuelle Werkzeugkoordinatensystem-Nummer, oben rechts – Aktuelle Werkstückkoordinatensystem-Nummer, unten links – Aktuelle Nummer des erweiterten Achskoordinatensystems, unten rechts – Aktuelle Lastkennung.

.. note::
   .. image:: teaching_pendant_software/009.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Geschwindigkeitsprozentsatz**

   Funktion: Aktuelle Betriebsgeschwindigkeit des Roboters im jeweiligen Modus (in Prozent).

.. note::
   .. image:: teaching_pendant_software/012.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Automatikmodus**

   Funktion: Automatischer Betriebsmodus des Roboters. Wenn beim Wechsel von Hand- zu Automatikmodus die Globale Geschwindigkeit angepasst werden soll, wird die globale Geschwindigkeit automatisch auf den angegebenen Wert gesetzt.

.. note::
   .. image:: teaching_pendant_software/013.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Handmodus**

   Funktion: Manueller Modus des Roboters zum Teach-In (Programmieren durch Vorführen).

.. note::
   .. image:: teaching_pendant_software/065.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche zum Ein-/Ausklappen des Roboterstatus**

   Funktion: Klappt die Anzeige für Werkzeugkoordinatensystem, Werkstückkoordinatensystem, erweitertes Achskoordinatensystem, Last, Roboterschleppmodus, Lokal/Fern-Modus, Roboter-Verbindungsstatus, BOOT-Modus und Kontoinformationen ein oder aus.

Durch Klicken auf die Ausklapp-Schaltfläche werden die folgenden zusätzlichen Statusinformationen angezeigt.

.. note::
   .. image:: teaching_pendant_software/008.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Werkzeugkoordinatensystem-Nummer**

   Funktion: Zeigt die Nummer des aktuell verwendeten Werkzeugkoordinatensystems an.

.. note::
   .. image:: teaching_pendant_software/027.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Werkstückkoordinatensystem-Nummer**

   Funktion: Zeigt die Nummer des aktuell verwendeten Werkstückkoordinatensystems an.

.. note::
   .. image:: teaching_pendant_software/028.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Erweitertes Achskoordinatensystem - Nummer**

   Funktion: Zeigt die Nummer des aktuell verwendeten erweiterten Achskoordinatensystems an.

.. note::
   .. image:: teaching_pendant_software/066.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Last**

   Funktion: Zeigt das aktuell verwendete Lastgewicht und den Schwerpunkt (Koordinaten X, Y, Z) an.

.. note::
   .. image:: teaching_pendant_software/014.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Roboter-Schleppmodus-Status**

   Funktion: Der Roboter kann manuell geführt werden (Drag & Teach).

.. note::
   .. image:: teaching_pendant_software/015.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Roboter-Schleppmodus-Status**

   Funktion: Der Roboter kann nicht manuell geführt werden.

.. note::
   .. image:: teaching_pendant_software/068.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Roboter Lokal-Modus**

   Funktion: Der Roboter wird über das Steuerpult gesteuert.

.. note::
   .. image:: teaching_pendant_software/067.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Roboter Fern-Modus**

   Funktion: Der Roboter kann nur über eine SPS gesteuert werden.

.. note::
   .. image:: teaching_pendant_software/017.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Verbindungsstatus**

   Funktion: Roboter ist verbunden.

.. note::
   .. image:: teaching_pendant_software/016.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Verbindungsstatus**

   Funktion: Roboter ist nicht verbunden.

.. note::
   .. image:: teaching_pendant_software/018.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Kontoinformationen**

   Funktion: Zeigt Benutzername, Berechtigungen und bietet die Möglichkeit zum Abmelden.