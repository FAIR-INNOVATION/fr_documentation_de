Erstellungsassistent
====================

.. toctree::
   :maxdepth: 6

Der "Erstellungsassistent" ist ein Werkzeug in den FRCap-Tools. Mit diesem Tool können Sie durch die Eingabe weniger Parameter schnell und bequem ein FRCap-Projekt initialisieren.

Parameterkonfiguration
----------------------

Für die Erstellung eines FRCap werden hauptsächlich zwei Arten von Parametern benötigt: die Basisinformationen des FRCap und die Konfigurationen auf verschiedenen Ebenen. Diese werden im Folgenden jeweils erläutert.

Basisinformationen
++++++++++++++++++

Die Basisinformationen enthalten den "Plug-in-Namen", den "Plug-in-Autor" und die "Plug-in-Beschreibung".

Plug-in-Name:

- Pflichtfeld.
- Es gibt keine Einschränkung hinsichtlich der Eingabezeichen oder der Zeichenlänge. Leerzeichen sind nicht erlaubt.
- Es wird empfohlen, dass der Name 7 CJK-Zeichen (Chinesisch, Japanisch, Koreanisch usw.), 10 lateinische Großbuchstaben oder 14 lateinische Kleinbuchstaben (Englisch, Französisch usw.) nicht überschreitet.
- Empfohlene Beispiele:

  - Palettierer
  - Schleifprozesssoftware
  - Gerätekonfiguration
  - HALLO FRCAP

Plug-in-Autor:

- Pflichtfeld.
- Es gibt keine Einschränkung hinsichtlich der Eingabezeichen oder der Zeichenlänge. Sie können z. B. Ihren persönlichen Namen, Firmennamen usw. eingeben.
- Empfohlene Beispiele:

  - Zhang San
  - Franklin Peter
  - FAIR Innovation (Suzhou) Robot Systems Co., Ltd.

Plug-in-Beschreibung:

- Kein Pflichtfeld.
- Es gibt keine Einschränkung hinsichtlich der Eingabezeichen oder der Zeichenlänge. Beschreiben Sie Ihr Plug-in kurz.

Erweiterte Einstellungen
------------------------

Plug-in-Typ:

- Pflichtfeld.
- Die Typoptionen sind "Konfiguration" und "Anwendung".
- "Konfiguration" wird für FRCaps empfohlen, die relativ einfache Konfigurations- und Steuerungsoperationen wie das Einstellen von Parametern oder Schaltflächenaktionen implementieren. Nach dem Import werden sie in der WebApp unter "Zusatzanwendungen" -> "FRCap" verwendet.
- "Anwendung" wird für FRCaps empfohlen, die komplexe Prozessszenarien implementieren, wie z. B. Branchenanwendungen für Palettierszenarien, Schweißprozesse usw. Nach dem Import werden sie direkt unter "Zusatzanwendungen" in der WebApp verwendet.

Plug-in-Symbol:

- Kein Pflichtfeld.
- Als Symbol können Sie Ihr Firmenlogo oder ein beliebiges anderes Symbol hochladen, das Sie verwenden möchten. Achten Sie auf das Urheberrecht. Unser Unternehmen übernimmt keine Haftung für urheberrechtliche Probleme, die aus irgendeinem Grund entstehen.
- Wenn Sie kein Symbol hochladen, verwendet das exportierte FRCap-Projekt standardmäßig das "FAIRINO"-Logo unseres Unternehmens. Sie können es im Projektordner unter "public" ersetzen oder ändern. Dieses Symbol dient nur zur Veranschaulichung der Initialisierung. Bitte verwenden Sie das "FAIRINO"-Logo nicht direkt in kommerziellen Szenarien.

Herunterladen
-------------

Nachdem alle oben genannten Parameter konfiguriert wurden und die FRCap-Erstellung erfolgreich war, gelangen Sie zur Download-Seite. Sie müssen nur bestätigen, dass der Name korrekt ist, und können dann das erstellte FRCap-Projekt auf Ihren lokalen Computer herunterladen, um es weiterzuentwickeln und zu verwenden.

Das heruntergeladene Plug-in liegt im ".tar.gz"-Komprimierungsformat vor.

Unter Windows empfehlen wir die Verwendung der 7-Zip-Software zum Entpacken.

Unter Linux können Sie den folgenden Befehl im Terminal zum Entpacken verwenden.

.. code-block:: c++
   :linenos:

    tar -zxvf frcap_{FRCapName}.tar.gz