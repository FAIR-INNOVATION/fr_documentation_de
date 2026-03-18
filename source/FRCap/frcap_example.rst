FRCap-Beispiele
===============

.. toctree::
   :maxdepth: 6

FAIRINO Palettierer
-------------------

Nachdem Sie die Datei "Palettierer.plugin" aus dem Build-Ordner des Projekts in der WebApp hochgeladen, registriert und aktiviert haben, kann sie verwendet werden.

.. image:: frcap_pictures/011.png
   :width: 6in
   :align: center

.. centered:: Abbildung 7.1 Verwendung des Palettier-FRCap

Palettier-Werkstückkonfiguration
++++++++++++++++++++++++++++++++

Befehlsname: `palletizing_config_box`.

Befehlsparameter:

.. code-block:: c++
   :linenos:

   /**
   * @param int length   Werkstücklänge
   * @param int width    Werkstückbreite
   * @param int height   Werkstückhöhe
   * @param int payload  Werkstücklast
   * @param string grip_point Werkstückgreifpunkt
   * /

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_box",
      data: {
         length: 800,
         width: 615,
         height: 312,
         payload: 2.34,
         grip_point: "grippoint"
      }
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Palettier-Palettenkonfiguration
++++++++++++++++++++++++++++++++

Befehlsname: `palletizing_config_pallet`.

Befehlsparameter:

.. code-block:: c++
   :linenos:

   /**
   * @param int front   Palettenvorderseite (Länge)
   * @param int side    Palettenseite (Breite)
   * @param int height  Palettenhöhe
   * @param int left_pallet  Linke Palette aktivieren (1) / deaktivieren (0)
   * @param int right_pallet Rechte Palette aktivieren (1) / deaktivieren (0)
   */

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_pallet",
      data: {
            front: 1200,
            side: 1000,
            height: 110,
            left_pallet: 0,
            right_pallet: 1
         }
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Palettier-Erweiterte Konfiguration
+++++++++++++++++++++++++++++++++++

Befehlsname: `palletizing_advanced_cfg`.

Befehlsparameter:

.. code-block:: c++
   :linenos:

   /**
   * @param string height Anhebehöhe am Greifpunkt
   * @param string x1     Annäherungspunkt 1: x-Offset (mm)
   * @param string y1     Annäherungspunkt 1: y-Offset (mm)
   * @param string z1     Annäherungspunkt 1: z-Offset (mm)
   * @param string x2     Annäherungspunkt 2: x-Offset (mm)
   * @param string y2     Annäherungspunkt 2: y-Offset (mm)
   * @param string z2     Annäherungspunkt 2: z-Offset (mm)
   * @param string time   Wartezeit für Materialaufnahme (ms)
   */

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_advanced_cfg",
      data: {
      height: "1000",
            x1: "100",
            y1: "100",
            z1: "100",
            x2: "10",
            y2: "10",
            z2: "10",
            time: "1"
         }
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Palettier-Geräteabmessungskonfiguration
++++++++++++++++++++++++++++++++++++++++

Befehlsname: `palletizing_config_device`.

Befehlsparameter:

.. code-block:: c++
   :linenos:

   /**
   * @param int x     Absolutwert der x-Koordinate des oberen rechten Eckpunkts der linken Palette relativ zum Roboter-Basiskoordinatensystem
   * @param int y     Absolutwert der y-Koordinate des oberen rechten Eckpunkts der linken Palette relativ zum Roboter-Basiskoordinatensystem
   * @param int z     Absolutwert der z-Koordinate des oberen rechten Eckpunkts der linken Palette relativ zum Roboter-Basiskoordinatensystem
   * @param int angle Rotationswinkel bei der Roboterinstallation
   */

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_device",
      data: {
         x: 2400,
         y: 1800,
         z: 120,
         angle: 0
      }
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Palettier-Musterkonfiguration
++++++++++++++++++++++++++++++

Befehlsname: `palletizing_config_pattern`.

Befehlsparameter:

.. code-block:: c++
   :linenos:

   /**
   * @param int layers        Anzahl der Palettierlagen
   * @param int box_gap       Abstand zwischen Werkstück-Pixeln (mm)
   * @param string sequence   Palettier-Arbeitsmuster-Sequenz (z.B. "a,b,a,b")
   * @param int pattern_b_enable Muster b aktivieren (1) / deaktivieren (0)
   * @param string left_pattern_a   Kartesische Koordinaten für Muster a am linken Arbeitsplatz
   * @param string left_pattern_b   Kartesische Koordinaten für Muster b am linken Arbeitsplatz
   * @param string right_pattern_a  Kartesische Koordinaten für Muster a am rechten Arbeitsplatz
   * @param string right_pattern_b  Kartesische Koordinaten für Muster b am rechten Arbeitsplatz
   * @param string origin_pattern_a Kartesische Koordinaten für Startmuster a
   * @param string origin_pattern_b Kartesische Koordinaten für Startmuster b
   */

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_pattern",
      data: {
         layers: 8,
         box_gap: 0,
         sequence: "a,b,a,b,a,b,a,b",
         pattern_b_enable: 1,
         left_pattern_a: "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "left_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "right_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "right_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "origin_pattern_a": "[]",
         "origin_pattern_b": "[]"
      }
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Palettier-Programmgenerierung
++++++++++++++++++++++++++++++

Befehlsname: `generate_palletizing_program`.

Befehlsparameter:

.. code-block:: c++
   :linenos:

   /**
   * @param string palletizing_name   Name des Palettier-Programms
   * @param string depalletizing_name Name des Entpalettier-Programms
   * @param string flag               Bestimmt, ob Palettier- (Index 0) und/oder Entpalettier-Programm (Index 1) generiert werden sollen. 0 = nicht generieren, 1 = generieren. Format: z.B. "[0,1]"
   */

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "generate_palletizing_program",
      data: {
         palletizing_name: "palletizing_1",
         depalletizing_name:"depalletizing_1",
         flag:"[0,1]"
      }
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Palettierrezept abrufen
+++++++++++++++++++++++

Befehlsname: `get_palletizing_formula`.

Befehlsparameter:

.. code-block:: c++
   :linenos:

   /**
   * @param string name Name des Palettierrezepts
   */

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "get_palletizing_formula",
      data: {
         name: "palletizing_1"
      }
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200
   * @param object box_config         Werkstückkonfiguration
   * @param object pallet_config      Palettenkonfiguration
   * @param object device_config      Installationsgeräteposition
   * @param object pattern_config     Musterkonfiguration
   * @param object program_config     Programmgenerierungskonfiguration
   * @param object lefttransitionpoint  Kartesische Koordinaten des linken Übergangspunkts
   * @param object righttransitionpoint Kartesische Koordinaten des rechten Übergangspunkts
   * @param object advanced_config    Erweiterte Konfiguration
   * @return status:404 "fail"
   */

Beispiel für Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   {
      "box_config": {
        "flag": 1,
        "length": 200,
        "width": 400,
        "height": 300,
        "payload": 2.34,
        "grip_point": "grippoint"
      },
      "pallet_config": {
        "flag": 1,
        "front": 1000,
        "side": 1200,
        "height": 110,
         "left_pallet": 0,
         "right_pallet": 1
      },
      "device_config": {
      "flag": 1,
      "x": 2400,
      "y": 1800,
      "z": 120,
      "angle": 0
      },
      "pattern_config": {
      "flag": 1,
      "layers": 8,
      "box_gap": 0,
      "sequence": "a,b,a,b,a,b,a,b",
      "pattern_b_enable": 1,
      "left_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "left_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "right_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "right_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "origin_pattern_a": "[]",
      "origin_pattern_b": "[]"
      },
      "program_config": {
      "palletizing_name": "palletizing_1",
      "depalletizing_name":"depalletizing_1",
      "flag":"[0,1]"
      },
      "lefttransitionpoint":{
      "j1":"120",
      "j2":"120",
      "j3":"120",
      "j4":"120",
      "j5":"120",
      "j6":"120"
      },
      "righttransitionpoint":{
      "j1":"120",
      "j2":"120",
      "j3":"120",
      "j4":"120",
      "j5":"120",
      "j6":"120"
      },
      "advanced_config":{
      "height": "1000",
      "x1": "100",
      "y1": "100",
      "z1": "100",
      "x2": "10",
      "y2": "10",
      "z2": "10",
      "time": "1"
      }
   }

Liste der vorhandenen Palettierrezeptnamen abrufen
+++++++++++++++++++++++++++++++++++++++++++++++++++

Befehlsname: `get_palletizing_formula_list`.

Befehlsparameter: Keine.

Befehlsbeispiel:

.. code-block:: c++
   :linenos:

   {
      cmd: "get_palletizing_formula_list"
   }

Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   /**
   * @return status:200
   * @param Array ${name} Liste der Palettiernamen
   * @return status:404 "fail"
   */

Beispiel für Befehlsrückmeldung:

.. code-block:: c++
   :linenos:

   ["palletizing1"]