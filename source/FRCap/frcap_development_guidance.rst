Entwicklungsleitfaden
=========================

.. toctree::
   :maxdepth: 6

Entwicklungsumgebung und -voraussetzungen
------------------------------------------

Die Entwicklungsumgebung muss mindestens die folgenden Anforderungen erfüllen:

- **CPU**: 1,6 GHz oder schnellerer Prozessor.
- **RAM**: >= 1 GB (2 GB oder mehr empfohlen).
- **ROM**: >= 128 GB.
- **Betriebssystem**: Windows 10 oder höher, macOS 10.15 oder höher, Linux (x64)-System (Ubuntu, Debian usw.).
- **Controller-Version**: Überprüfen Sie diese in der WebApp unter "Systemeinstellungen - Über". Achten Sie bei der Entwicklung auf die Unterscheidung zwischen QX und LA. Vermeiden Sie in der QX-Umgebung moderne JavaScript-Funktionen wie die ES6+-Syntax in Befehlsbeispielen.

Wir haben einige Schnittstellen und Module bereitgestellt. Für ein besseres Entwicklungsergebnis sind jedoch Grundkenntnisse der Webentwicklung empfehlenswert, insbesondere die Vertrautheit mit folgenden Technologien:

- HTML, JavaScript/TypeScript, CSS.
- Vue3.
- Vite.
- Node.js.

Entwicklungswerkzeuge
---------------------

Wir empfehlen die Verwendung der neuesten **Visual Studio Code (VSCode)** Software für die Entwicklung. Besuchen Sie zum Download die offizielle VSCode-Downloadseite und wählen Sie die entsprechende Version für Ihr System aus.

Gleichzeitig muss auf Ihrem lokalen Computer die **Node.js**-Laufzeitumgebung installiert sein. Bei der Installation von Node.js werden auch Tools wie npm mitinstalliert, die die Paketverwaltung erleichtern. Besuchen Sie die offizielle Node.js-Downloadseite und wählen Sie Version 20 für Ihr System aus.

Bei der Entwicklung in VSCode können außerdem die folgenden VSCode-Erweiterungen nützlich sein, die je nach Bedarf installiert und konfiguriert werden können.

- Vue
- ESLint
- npm Intellisense
- Vue Language Features (Volar)
- TypeScript Vue Plugin (Volar) oder Vue.volar
- Tailwind CSS IntelliSense

FRCap-Projektstruktur
---------------------

Die Dateistruktur eines FRCap-Projekts:

.. image:: frcap_pictures/012.png
   :width: 3in
   :align: center

.. centered:: Abbildung 5-1 FRCap-Projektstruktur

- **Public**:

  Öffentlicher Ressourcenordner. Dateien in diesem Ordner werden während des Build-Prozesses nicht verarbeitet, sondern direkt unverändert in das Build-Verzeichnis kopiert.

  Standardmäßig enthält er den Ordner `action` und die Datei `logo.svg`.

  Der Ordner `action` enthält die Logikdateien für die benutzerdefinierten Befehlshintergrundschnittstellen.

  `logo.svg` ist das Plugin-Symbol.

- **Src**:

  Der Ordner `assets` dient hauptsächlich zur Ablage statischer Ressourcen.

  Der Ordner `components` dient hauptsächlich zur Ablage von Komponenten.

  Der Ordner `utils` dient hauptsächlich zur Ablage von Hilfsklassen.

  `App.vue` ist der Code der Startseite.

  `main.js` ist hauptsächlich für den globalen Import von Ressourcen und die Erstellung des Vue-Frameworks zuständig.

  `style.css` ist die grundlegende Stildatei des Projekts.

- **build.bat**: Build-Skript für Windows-Plattformen.
- **index.html**: Hauptgerüst der Seiten-Benutzeroberfläche.
- **package.json**: Paketbeschreibungsdatei und Kompilierungsstrategien usw.
- **vite.config.js**: Vite-Konfigurationsdatei.

Verwendung von Frontend-frcap-ui und frcap-api
-----------------------------------------------

`frcap-ui` bietet einige über Vue-Komponenten gekapselte HTML-Steuerelemente, die in das Projekt importiert werden können. Dies reduziert den Aufwand für die Entwicklung der Seiten-Benutzeroberfläche, verringert die Code-Menge und verbessert die Lesbarkeit des Codes. Natürlich können Sie auch andere gute Open-Source-UI-Komponentenbibliotheken wie Element Plus verwenden.

Öffnen Sie zunächst ein Terminal im Pfad Ihres Projekts und installieren Sie `frcap-ui`.

.. code-block:: bash
   :linenos:

   npm install frcap-ui --save

Nach erfolgreicher Installation importieren Sie es in der Komponente, die `frcap-ui` verwenden soll, am Beispiel des Button-Steuerelements.

.. code-block:: javascript
   :linenos:

   import { AppButton } from 'frcap-ui'

Verwenden Sie es dann im `<template>`-Element der Komponente.

.. code-block:: html
   :linenos:

   <AppButton button-text="Start" button-type="primary"></AppButton>

Vorschau des Entwicklungsergebnisses im Browser.

.. image:: frcap_pictures/009.png
   :width: 6in
   :align: center

.. centered:: Abbildung 5-2 AppButton-Effekt

Derzeit bieten wir vier gängige Steuerelement-Komponenten an.

- **AppButton**: Schaltflächenkomponente.

  - `buttonType`: Schaltflächentyp, String, bestimmt das entsprechende Schaltflächendesign. Standard ist `primary`.
    - `primary`: Blau.
    - `secondary`: Grau.
    - `safety`: Grün.
    - `warning`: Gelb.
    - `serious`: Rot.

  - `buttonText`: Schaltflächentext, String. Standardwert ist "primary".

- **AppInput**: Eingabekomponente.

  - `type`: Erforderlich, String. Standardwert ist `text`. Gibt den Typ des Eingabefelds an.
    - `number`: Zahlen-Eingabefeld.
    - `text`: Text-Eingabefeld.
  - `inputLabel`: Erforderlich, String. Beschriftungstext des Eingabefelds.
  - `inputUnit`: String. Einheitentext des Eingabefelds.
  - `hasUnit`: Boolean, Standard `false`. Gibt an, ob ein Einheitentext benötigt wird.
  - `isEmptyErr`: Boolean. Gibt an, ob das Eingabefeld leer ist (für Fehlerbehandlung).
  - `isReadonly`: Boolean. Gibt an, ob das Eingabefeld schreibgeschützt ist.

- **AppSelect**: Auswahlfeld-Komponente.

  - `selectionLabel`: Erforderlich, String. Beschriftungstext des Auswahlfelds.
  - `optionsData`: Erforderlich, Array. Daten für die Optionen.

- **Modal**: Modalfenster-Komponente.

  - `show`: Boolean. Gibt an, ob das Modalfenster angezeigt wird.
  - `title`: String. Titel des Modalfensters.

Um die Entwicklung benutzerdefinierter Befehle in FRCap zu erleichtern, haben wir die HTTP-Anfragen und APIs bereits in das über den "Erstellungsassistenten" heruntergeladene initiale FRCap-Projekt integriert. Dadurch können sowohl benutzerdefinierte als auch die standardmäßig bereitgestellten Befehle in der Datei `api.js` unter `./src/api/api.js` abgelegt werden.

Die Verwendung von `frcap-api` ähnelt der von `frcap-ui`:

1.  Importieren Sie die API in der Datei (z.B. einer Komponente), die sie benötigt.

.. code-block:: javascript
   :linenos:

   import api from '@/api/api';

2.  Rufen Sie die standardmäßig bereitgestellten Befehle in Ihrer Schnittstelle auf.

.. code-block:: javascript
   :linenos:

   api.getRobotStatus();

3.  Verarbeiten Sie die Logik im zurückgegebenen Promise.

.. code-block:: javascript
   :linenos:

   api.getRobotStatus()
   .then((res) => {
       console.log(res.data);
   })
   .catch((err) => {
       console.error(err);
   });

Entwicklung benutzerdefinierter Backend-Befehle
------------------------------------------------

Beispiel für Datenbankoperationen (LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++

1.  Datenbankmodul importieren

.. code-block:: javascript
   :linenos:

   var node = "/usr/local/etc/node/sys";
   var Sqlite3_Action = require(node + '/better-sqlite3/better-sqlite3.js');
   var sqlite = new Sqlite3_Action();

2.  Inhalt der Punktedatenbank abrufen

.. code-block:: javascript
   :linenos:

   // cmd abgleichen
   case 'get_points':
       // SQL-Anweisung schreiben: aufsteigend nach Name sortieren, zuerst Zahlen, dann Buchstaben, dann Chinesisch
       var sql = "select * from points order by name ASC";
       var sql_data = sqlite.queryall(DB_POINTS, sql);
       // JSON-Daten formatieren
       for (var i = 0; i < sql_data.length; i++) {
           response_data[sql_data[i].name] = sql_data[i];
       }
       // JSON-Daten an das Frontend zurücksenden
       event_socket.emit('response', res, response_status, response_data);
       break;

Beispiel für Datenbankoperationen (QX)
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. note:: Die QX-Version speichert Daten im JSON-Format.

1.  Datenbankmodul importieren

.. code-block:: javascript
   :linenos:

   var node = "/usr/local/etc/node/sys";
   var sqlite_adapter = require(node + '/jsdb/sqlite_adapter');
   var db = new sqlite_adapter.Database(palletizing_db);

2.  Beispiel für die Datenbankverwendung

.. code-block:: javascript
   :linenos:

   // SELECT-Abfrage ausführen und alle Zeilen abrufen
   var rows = db.queryall('SELECT * FROM box_cfg');
   console.log('result:', rows);

   // SELECT-Abfrage ausführen und eine einzelne Zeile abrufen
   var row = db.queryget('SELECT * FROM box_cfg WHERE flag=1');
   console.log('result:', row);

   // UPDATE-Anweisung ausführen
   db.run('UPDATE box_cfg SET height=100 WHERE flag=1', function(err) {
       if (err) {
           console.error('Update failed:', err);
       } else {
           console.log('Update success');
       }
   });

   // Parametrisierte Abfrage ausführen
   var params = [100, 200, 300, 1];
   db.run('UPDATE box_cfg SET height=?, width=?, length=? WHERE flag=?', params, function(err) {
       if (err) {
           console.error('update failed:', err);
       } else {
           console.log('update success');
       }
   });

   // Datenbankverbindung schließen
   db.close();

Beispiel für Socket-Kommunikationsoperationen
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

- Socket-Kommunikationsmodul importieren

.. code-block:: javascript
   :linenos:

   var node = "/usr/local/etc/node/sys";
   var Socket_Cmd = require(node + '/socket/socket_cmd');
   var socket_cmd = new Socket_Cmd();

- Befehl zum Setzen einer Systemvariablen senden

.. code-block:: javascript
   :linenos:

   // cmd abgleichen
   case 511:
       // Gesendete Daten abrufen
       content = data_json.content;
       // Länge der gesendeten Daten abrufen
       len = data_json.content.length;
       // Datenpaket zusammensetzen
       send_content = '/f/bIII1III511III' + len + 'III' + content + 'III/b/f';
       // Socket senden
       socket_cmd.send(send_content);
       // Socket empfangen (Unterschied LA/QX beachten)
       // LA Version:
       socket_cmd.recv().then((recv_data) => {
           response_data = recv_data;
           event_socket.emit('response', res, response_status, response_data);
       }).catch((err) => {
           console.log(err);
       });
       // QX Version
       // socket_cmd.recv().then(function(recv_data) {
       //     response_data = recv_data;
       //     event_socket.emit('response', res, response_status, response_data);
       // }).catch(function(err) {
       //     console.log(err);
       // });
       break;