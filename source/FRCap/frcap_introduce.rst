Einführung
==========

FRCap ist ein webbasiertes Plugin, das in die WebApp von kollaborativen Robotern integriert werden kann. FRCap nutzt Module wie Element Plus (basierend auf Node.js und Vue3), frcap-ui und frcap-api, um eine Konfigurationsseite oder Anwendung für die WebApp des kollaborativen Roboters zu erstellen und so die Roboterfunktionen und Anwendungsszenarien zu erweitern.

Im Kern ist ein FRCap eine Webanwendung, die in einer Node.js-Umgebung läuft und von der WebApp unabhängig ist. Die WebApp stellt Verwaltungs- und Zugriffsdienste bereit. Ein FRCap kann über die bereitgestellten offiziellen Schnittstellen mit der Robotersteuerung interagieren, oder Kunden können basierend auf den tatsächlichen Anforderungen benutzerdefinierte Schnittstellenbefehle und Verarbeitungslogiken für individuelle Entwicklungen schreiben.

.. image:: frcap_pictures/001.png
   :width: 6in
   :align: center

.. centered:: Abbildung 1.1 WebApp + FRCap-Darstellung