Glossar
=======

.. toctree::
	:maxdepth: 5


**Stopp-Kategorien**:

- **Stopp der Kategorie 0**: Der Roboter stoppt sofort, wenn seine Stromversorgung unterbrochen wird. Dies ist ein unkontrollierter Stopp, bei dem der Roboter aufgrund der maximalen Verzögerung jedes Gelenks vom programmierten Pfad abweichen kann. Diese Art von Schutzhalt darf nur verwendet werden, wenn die Sicherheitsbewertungsgrenzen überschritten werden oder ein Fehler im sicherheitsgerichteten Teil der Steuerung vorliegt. Weitere Informationen finden Sie in EN ISO 13850:2008 oder IEC 60204-1:2006.
- **Stopp der Kategorie 1**: Der Roboter stoppt, solange er mit Strom versorgt wird, um den Stopp durchzuführen. Die Stromversorgung wird erst nach dem Stillstand des Roboters unterbrochen. Dies ist ein kontrollierter Stopp, bei dem der Roboter dem programmierten Pfad folgt. Die Stromversorgung wird nach einer Sekunde oder sobald der Roboter zum Stillstand gekommen ist, unterbrochen. Weitere Informationen finden Sie in EN ISO 13850:2008 oder IEC 60204-1:2006.
- **Stopp der Kategorie 2**: Ein kontrollierter Stopp, bei dem der Roboter unter Spannung bleibt. Der Roboter stoppt alle Bewegungen innerhalb einer Sekunde. Die Steuerung des sicherheitsgerichteten Steuerungssystems kann den Roboter in der Stopposition halten. Weitere Informationen finden Sie in IEC 60204-1:2006.

**Diagnosedeckungsgrad (DC)**: Ein Maß für die Wirksamkeit der Diagnose, die zur Erreichung der bewerteten Leistungsstufe implementiert wurde. Weitere Informationen finden Sie in EN ISO 13849-1:2008.

**Integrator**: Ein Integrator ist die Organisation, die die endgültige Installation des Roboters plant. Der Integrator ist für die abschließende Risikobeurteilung verantwortlich und muss sicherstellen, dass die endgültige Installation den lokalen Gesetzen und Vorschriften entspricht.

**Mittlere Zeit bis zum gefahrbringenden Ausfall (MTTFd)**: Die mittlere Zeit bis zum gefahrbringenden Ausfall ist ein Wert, der berechnet und ermittelt wird, um die bewertete Leistungsstufe zu erreichen. Weitere Informationen finden Sie in EN ISO 13849-1:2008.

**Risikobeurteilung**: Die Risikobeurteilung ist der gesamte Prozess der Identifizierung aller Risiken und deren Reduzierung auf ein angemessenes Maß. Die Risikobeurteilung sollte dokumentiert werden. Weitere Informationen finden Sie in ISO 12100.

**Leistungsstufe (PL)**: Die Leistungsstufe ist eine diskrete Stufe, die die Fähigkeit sicherheitsbezogener Teile von Steuerungen beschreibt, eine Sicherheitsfunktion unter vorhersehbaren Bedingungen auszuführen. PLd ist die zweithöchste Vertrauenswürdigkeitsklassifizierung und bedeutet, dass die Sicherheitsfunktion als ziemlich zuverlässig angesehen wird. Weitere Informationen finden Sie in EN ISO 13849-1:2008.

**Verbindungsflansch**: Die Struktur zum Anschluss externer Werkzeuge, allgemein als Flansch bezeichnet.

**Roboterende**: Der Mittelpunkt der letzten Achse des Roboters oder des Verbindungsflansches.

**Werkzeugmittelpunkt (TCP)**: Der Werkzeugmittelpunkt ist der charakteristische Punkt des Roboterwerkzeugs und der Steuerungspunkt des Robotersystems. Ab Werk ist er standardmäßig auf den Mittelpunkt der letzten Bewegungsachse oder des Verbindungsflansches eingestellt. Der TCP jedes Werkzeugs umfasst eine Translation und Rotation, die relativ zum Mittelpunkt des Werkzeugausgangsflansches eingestellt sind. Die Positionskoordinaten X, Y, Z bestimmen die Position des TCP, während RX, RY, RZ die Ausrichtung des Werkzeugs bestimmen. Wenn alle diese Werte Null sind, fällt der Werkzeugmittelpunkt mit dem Mittelpunkt des Verbindungsflansches zusammen.

**Werkzeugposenpunkt (TCF)**: Bildet auf Basis des TCP die Ausrichtung des Werkzeugkoordinatensystems relativ zum Koordinatensystem des Endglieds ab.

**Basiskoordinatensystem**: Der Ursprung des Basiskoordinatensystems ist im Allgemeinen im Mittelpunkt zwischen der ersten Achse des Roboters und der Montagefläche definiert. Die x-Achse zeigt nach vorne. Die y-Achse wird gemäß der rechten-Hand-Regel bestimmt.

**Weltkoordinatensystem**: Ein festes Koordinatensystem, das in einer Arbeitszelle oder einem Arbeitsplatz eingerichtet ist. Bei nur einem Roboter kann dieses Koordinatensystem als deckungsgleich mit dem Basiskoordinatensystem betrachtet werden. Bei mehreren Robotern oder externen Geräten bietet das Weltkoordinatensystem eine einheitliche Referenz für diese Geräte. Seine genaue Position kann beliebig festgelegt werden, solange es die einfache Kalibrierung der Koordinatensysteme anderer Geräte ermöglicht.

**Gelenkkoordinatensystem**: Das Gelenkkoordinatensystem ist das Koordinatensystem in den Robotergelenken. Im Gelenkkoordinatensystem kann jede Achse des Roboters einzeln innerhalb ihrer Grenzen vorwärts oder rückwärts bewegt werden. Es eignet sich für großräumige Roboterbewegungen, bei denen die TCP-Ausrichtung nicht entscheidend ist. Die Einzelachsen-Jog-Bewegung im Handmodus des Roboters erfolgt in diesem Koordinatensystem.

**Werkzeugkoordinatensystem**: Das Koordinatensystem, das verwendet wird, um die Position des Werkzeugmittelpunkts und die Ausrichtung des Werkzeugs zu definieren. Wenn es nicht definiert ist, befindet sich das Werkzeugkoordinatensystem standardmäßig im Mittelpunkt des Verbindungsflansches. Nach der Montage eines Werkzeugs ändert sich der TCP und wird zum Mittelpunkt der Werkzeugspitze.

**Externes Werkzeugkoordinatensystem**: Das Koordinatensystem zur Definition der Position und Ausrichtung eines außerhalb des Roboters fixierten Werkzeugs.

**Externe Achsen**: Zusätzliche Achsen, die über die Achsen des Roboterkörpers hinaus für die Arbeit benötigt werden. Externe Achsen umfassen hauptsächlich Typen wie Linearschienen, Positionierer und externe Servogeräte.

**Handmodus**: In diesem Modus werden alle Bewegungen des Roboters manuell vom Benutzer gesteuert. Externe Sicherheitseinrichtungen wie Lichtschranken und Sicherheitstüren sind inaktiv, um Nahfeld-Programmierungen zu ermöglichen.

**Automatikmodus**: Dieser Modus wird im Allgemeinen zum Ausführen von Teachprogrammen verwendet. Externe Sicherheitseinrichtungen sind aktiviert.

**Wiederholgenauigkeit**: Das Maß der Übereinstimmung der Positionen und Ausrichtungen, die erreicht werden, wenn derselbe Vorgang unter denselben Bedingungen mehrfach (n-mal) wiederholt wird.

**Teachpendant**: Eine handgehaltene Einheit, die mit der Steuerung verbunden ist und zum Programmieren oder Bewegen des Roboters verwendet wird.