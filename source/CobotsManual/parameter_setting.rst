Parametereinstellungen des Roboters
=========================================

Installationsart einstellen
-----------------------------------------

Die Standardinstallationsart des Roboters ist die horizontale Montage. Wenn sich die Installationsart des Roboters ändert, muss die tatsächliche Installationsart des Roboters rechtzeitig im Menü "Initiale Einstellungen" -> "Basis" -> "Installation" eingestellt werden, um den ordnungsgemäßen Betrieb des Roboters zu gewährleisten.

Im Hinblick auf flexiblere und vielfältigere Einsatzszenarien des Roboters bieten wir eine Funktion zur freien Installation an. Der Benutzer klickt auf "Initiale Einstellungen" -> "Basis" -> "Installation", um zur Seite für die Einstellung der Roboter-Installationsart zu gelangen. Passen Sie die Winkel für "Basisneigung" und "Basisrotation" manuell an. Das 3D-Modell zeigt den entsprechenden Installationseffekt an. Nach der Änderung klicken Sie auf die Schaltfläche "Anwenden", um die Einstellung der Roboter-Installationsart abzuschließen.

.. image:: teaching_pendant_software/026.png
   :width: 6in
   :align: center

.. centered:: Abbildung 3.1-1 Roboterinstallation

.. important::
    Nach Abschluss der Roboterinstallation muss die Installationsart korrekt eingestellt werden, da sonst die Ziehemodus-Funktion (Drag & Drop) und die Kollisionserkennung des Roboters beeinträchtigt werden.

Endnutzlast einstellen
--------------------------------

Wählen Sie unter "Initiale Einstellungen" -> "Basis" -> "Nutzlast" den Identifikationstyp für die "Bahnidentifikation" aus, um zur Oberfläche für die Einstellung der Endnutzlast zu gelangen.

.. note::
   .. image:: base/071.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Anwenden"**

   Funktion: Durch Anklicken werden das Gewicht und die Schwerpunktkoordinaten angewendet, die der Nutzlastnummer entsprechen.

.. note::
   .. image:: base/072.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Ändern"**

   Funktion: Durch Anklicken wird die Oberfläche für die Identifikationsbewegung geöffnet/geschlossen.

.. note::
   .. image:: base/073.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Umbenennen"**

   Funktion: Benennt die Nutzlast um.

.. note::
   .. image:: base/074.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Leeren"**

   Funktion: Löscht die aktuellen Nutzlastinformationen (Nutzlastgewicht und Schwerpunktkoordinaten werden auf 0 gesetzt).

Bei der Konfiguration der Endnutzlast können Sie direkt die Masse des Endeffektors sowie die entsprechenden Schwerpunktkoordinaten X, Y und Z eingeben und anschließend auf die Schaltfläche "Anwenden" klicken, um die Einstellung vorzunehmen.

Gleichzeitig können Sie auf die Schaltfläche "Bearbeiten" klicken, um die Oberfläche "Identifikationsbewegung" zu öffnen und eine automatische Nutzlastidentifikation durchzuführen. Nach Abschluss des Identifikationslaufs kann die Nutzlast angewendet werden.

.. important::
    Das Nutzlastgewicht darf den maximalen Nutzlastbereich des Roboters nicht überschreiten. Die entsprechenden Nutzlasten für die Modelle sind:

    - FR3: 3 kg
    - FR5: 5 kg
    - FR10: 10 kg
    - FR16: 16 kg
    - FR20: 20 kg
    - FR30: 30 kg

    Der Einstellbereich für die Schwerpunktkoordinaten beträgt 0-1000, Einheit mm.

.. image:: base/016.png
   :width: 4in
   :align: center

.. centered:: Abbildung 3.2-1 Schema der Nutzlasteinstellung

.. important::
    Nach der Montage einer Nutzlast am Roboterflansch müssen das Gewicht und die Schwerpunktkoordinaten der Endnutzlast korrekt eingestellt werden, da sonst die Ziehemodus-Funktion (Drag & Drop) und die Kollisionserkennung des Roboters beeinträchtigt werden.

Werkzeugkoordinate einstellen
---------------------------------------------

Navigieren Sie zu "Initiale Einstellungen" -> "Basis" -> "Werkzeugkoordinaten", um zur Seite für Werkzeugkoordinaten zu gelangen.

.. note::
   .. image:: base/071.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Anwenden"**

   Funktion: Durch Anklicken wird das Werkzeugkoordinatensystem angewendet.

.. note::
   .. image:: base/072.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Ändern"**

   Funktion: Durch Anklicken wird die Oberfläche zur Kalibrierung des Koordinatensystems geöffnet/geschlossen.

.. note::
   .. image:: base/073.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Umbenennen"**

   Funktion: Benennt das Werkzeugkoordinatensystem um.

.. note::
   .. image:: base/074.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Bezeichnung: **Schaltfläche "Leeren"**

   Funktion: Löscht die aktuellen Informationen des Werkzeugkoordinatensystems.

Die Werkzeugkoordinate ermöglicht das Ändern, Löschen und Anwenden von Werkzeugkoordinaten. Wählen Sie in der Dropdown-Liste der Werkzeugkoordinatensysteme das entsprechende System aus. Darunter werden die entsprechenden Koordinatenwerte (der Name des Koordinatensystems kann benutzerdefiniert angepasst werden), der Werkzeugtyp und die Einbauposition (nur bei Sensortyp-Werkzeugen angezeigt) eingeblendet. Nach Auswahl eines Koordinatensystems klicken Sie auf die Schaltfläche "Anwenden". Das aktuell verwendete Werkzeugkoordinatensystem wechselt zu dem ausgewählten Koordinatensystem, wie unten gezeigt.

.. image:: base/001.png
   :width: 4in
   :align: center

.. centered:: Abbildung 3.3-1 Werkzeugkoordinate einstellen

Durch Klicken auf "Ändern" kann das Werkzeugkoordinatensystem für diese Nummer gemäß den Anweisungen neu eingestellt werden. Die Werkzeugkalibrierungsmethode ist in die Vier-Punkt-Methode und die Sechs-Punkt-Methode unterteilt. Die Vier-Punkt-Methode kalibriert nur das Werkzeug-TCP (Tool Center Point), d.h. die Position des Werkzeugmittelpunkts. Seine Ausrichtung ist standardmäßig identisch mit der Ausrichtung des Flansches. Die Sechs-Punkt-Methode fügt der Vier-Punkt-Methode zwei weitere Punkte hinzu, um die Ausrichtung des Werkzeugs zu kalibrieren.

.. image:: base/002.png
   :width: 4in
   :align: center

.. centered:: Abbildung 3.3-2 Kalibrierung des Werkzeugkoordinatensystems

.. important::
    1. Nach der Montage eines Werkzeugs am Flansch muss das Werkzeugkoordinatensystem zwingend kalibriert und angewendet werden. Andernfalls könnte die Position und Ausrichtung des Werkzeugmittelpunkts (TCP) bei der Ausführung von Bewegungsbefehlen nicht den Erwartungen entsprechen.

    2. Für Werkzeugkoordinatensysteme werden in der Regel toolcoord1 bis toolcoord19 verwendet. Die Anwendung von toolcoord0 bedeutet, dass sich die TCP-Position des Werkzeugs im Zentrum des Flansches befindet. Bei der Kalibrierung eines Werkzeugkoordinatensystems muss zunächst das Werkzeugkoordinatensystem auf toolcoord0 angewendet werden. Anschließend können andere Werkzeugkoordinatensysteme ausgewählt, kalibriert und angewendet werden.