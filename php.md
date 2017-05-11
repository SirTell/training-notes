# PHP Notizen

Ein paar Notizen vorbereitet beim Schreiben von Schulungen ...


## Übersicht

### Server-seitige Verarbeitung

Wenn Sie eine URL in Ihrem Browser besuchen (oder anfordern), passiert viel hinter den Kulissen, damit Sie die Seite sehen

Es gibt mehrere Schritte zum Rendering-Prozess, bevor die Seite, die Sie sehen, generiert wird

Verschiedene Technologien und Sprachen erfüllen dabei spezifische Rollen

Der Rendering-Prozess kann in zwei verschiedene Kategorien aufgeteilt werden, die auf der Client-Seite und die auf der Server-Seite

  - *Server* sind Computer, die zum Speichern von Daten und zum Hosten / Erstellen von Webseiten verwendet werden
  - *Clients* sind Computer, die um das Netzwerk verteilt sind und die Dienste nutzen, die von Servern bereitgestellt werden - in der Regel eine Maschine des Benutzers

Beispielsweise ist ein Webbrowser ein Programm auf dem Computer eines Benutzers, der Daten von einem Webserver anfordert.

  - *Server-seitige Verarbeitung* - findet auf dem Server statt
  - *Client-seitige Verarbeitung* - erfolgt auf eigene Maschine


### Programmierung & Markup

Eine Markup-Sprache (z. B. HTML) ist statisch - sie wird verwendet, um das Aussehen und das Format der angezeigten Informationen zu diktieren

Eine Programmiersprache (z. B. PHP, JavaScript) ist dynamisch - sie wird verwendet, um bestimmte Aufgaben / Aktionen wie das Filtern oder Manipulieren von Daten auszuführen


### PHP

PHP ist nur eine von vielen Sprachen, die Sie für die serverseitige Programmierung verwendet werden können

Es ist weit verbreitet auf Webservern

Es gibt viele Bücher und Online-Dokumentation, um Ihr Lernen zu unterstützen

Viele Drittanbieter-Ressourcen - PHP-Skripte von anderen frei online verfügbar geschrieben

Im Einsatz auf zahlreichen grossen Webseiten


### Anfangen

PHP muss von einem Webserver ausgeführt (geparst) werden

Wenn Sie eine PHP-Datei in einem Webbrowser direkt öffnen, sehen Sie den unverarbeiteten Code

Sie müssen PHP-Skripte über einen Webserver (typischerweise Apache) ausführen, der Server verarbeitet den Code und gibt die Ergebnisse aus

Zum Glück ist die Installation einfach. Diese kann separat installiert werden, oder zusammen mit so etwas wie WAMP, MAMP etc.

Apache ist ein kontinuierlich laufender Prozess auf dem Server - denken Sie an ein Computerprogramm, das Sie niemals beenden

Die meisten Web-Server benutzen eine Version von Linux. Es gibt eine Reihe von Vorteilen für Linux-Server (gegenüber z.B. Windows-basierten Servern). Das wichtigste ist, dass es kostenlos ist!


### Vorteile der serverseitigen Verarbeitung

Stellen Sie sich vor, eine Website zu haben, die sich aus statischen HTML-Seiten zusammensetzt

  - Um alle Informationen zu bearbeiten, benötigen Sie HTML-Kenntnisse
  - Um die Seitenstruktur zu aktualisieren, muss man jede Datei anpassen
  - Sie können die Daten nicht anderswo wiederverwenden
  - Man kann die Daten nicht manipulieren, z.B. um nur die Seitentitel als Links zu extrahieren

Es ist sinnvoll, Daten und Logik aus der Präsentation zu trennen

  - Dadurch ist es einfacher einen einzelnen Aspekt zu verändern, ohne die anderen zu berühren
  - Trennung von Angelegenheiten
  - Daten können an anderer Stelle wiederverwendet werden
  - Nur eine 'Vorlage' Datei haben, die enthält, wie der Inhalt gerendert wird
  - Daten können mit einem einfachen Formular editiert werden - kein HTML-Kenntnisse erforderlich

Noch ein paar Gründe, warum die serverseitige Verarbeitung sinnvoll ist:

  - Automatisieren von monotonen Aufgaben: z.B. Hinzufügen eines Datumseintrags von 1900 bis 201x:

```
<option>1900<option>
<option>1901<option>
<option>1902<option>
```

  - Möglichkeit, das heutige Datum automatisch auf eine Webseite zu setzen
  - Möglichkeit, Aufgaben zu automatisieren oder Inhalte zu erzeugen
  - Datei Includes - die früheste Form des serverseitigen Skripts (z.B. das Speichern von sich wiederholenden Inhalten in einer separaten Datei, so dass Sie nur einmal schreiben müssen)
  - Anzeige spezifischer Inhalte nur, wenn bestimmte Bedingungen erfüllt sind
  - Verarbeiten Sie die in einem HTML-Formular eingegebenen Informationen
  - Man kann E-Mails senden
  - Man kann Dateien auf dem Webserver lesen und schreiben
  - Man kann Webseiten lesen (manchmal auch als Screen- oder Data-Scraping bekannt)
  - Man kann mit anderen Webdiensten über APIs interagieren

Etc ... hoffentlich sind Sie jetzt von den Vorteilen der Verwendung einer serverseitigen Sprache überzeugt


## Grundlagen

### Anfangen

PHP-Code wird identifiziert, indem er in bestimmte Skript-Tags gesetzt wird:

```
<?php

  // PHP hier zwischen

?>
```

So starten Sie PHP:

  - Erstellen Sie eine neue Datei
  - Geben Sie ihm eine Dateierweiterung von .php (z. B. index.php)
  - (Oder ändern eine vorhandene Datei von .html zu .php)
  - Schreiben Sie einen PHP-Code innerhalb der Tags <?php und ?>
  - Öffentliche URL in einem Browser anzeigen

PHP-Code kann frei mit normalem HTML durchsetzt werden.

Der PHP-Interpreter auf dem Server liest die Anweisungen und erzeugt HTML, das an den Browser gesendet wird

Eine statische HTML-Datei könnte wie folgt aussehen:

```
<!DOCTYPE html>
<html>
  <head>
    <title>Der heutige Tag</title>
  </head>
  <body>
    <h1>Welcher Tag ist heute?</h1>
  </body>
</html>
```

Fügen Sie PHP hinzu:

```
<!DOCTYPE html>
<html>
  <head>
    <title>Der heutige Tag</title>
  </head>
  <body>
    <h1>Welcher Tag ist heute?</h1>
    <p>
    <?php
      echo date("l");
    ?>
    </p>
  </body>
</html>
```

Der Server interpretiert das PHP und generiert:

```
<!DOCTYPE html>
<html>
  <head>
    <title>Der heutige Tag</title>
  </head>
  <body>
    <h1>Welcher Tag ist heute?</h1>
    <p>
      Freitag
    </p>
  </body>
</html>
```

Einige Regeln, um sofort zu beachten:

  - Wenn Sie einen PHP-Befehl beenden, stellen Sie sicher, dass Sie ein Semikolon verwenden, um einen Fehler zu vermeiden (mehr dazu später)
  - Der Befehl `echo` wird verwendet, um Inhalte in die HTML-Seite einzufügen.
  - PHP unterscheidet bei Variablen- und Konstantennamen zwischen Gross-/Kleinschreibung


### Variablen

```
$x = 4;
$y = 10;
$z = $x + $y;
echo $z;
// $z === 14
```

Benutzen Sie `=` um einer Variablen einen Wert zuzuweisen

Benutzen Sie `+` um zwei Zahlenwerte zu addieren

Benutzen Sie `==` um zwei Werte von Variablen miteinander zu vergleichen (`0` ist in diesem Fall identisch mit `false`)

Benutzen Sie `===` um zwei Werte von Variablen miteinander zu vergleichen und den Wert `0` dabei nicht als `false` interpretieren zu lassen

```
$word1 = "hello";
$word2 = "world";
$sentence = $word1 . $word2;
echo $sentence;

// $sentence === "helloworld"
```

```
$sentence2 = $word1 . " " . $word2;
// $sentence2 === "hello world"
```
Benutzen Sie `.` um Strings und Variablen aneinander zu hängen

```
$x = 3;
$y = 5;

$z = $x + $y;
echo $z;
// $z === 8

$z = $x . $y;
echo $z;
// $z === "35"
```
Beachten Sie die Unterschieden zwischen `.` und `+`


#### Was ist eine Variable?

Eine Variable ist ein Container oder ein Verweis auf etwas, das wir speichern wollen

In den Fällen, die wir gerade gesehen haben, ist es eine Zahl oder eine Zeichenfolge (String)

Wir können einer Variablen einen Wert zuordnen und können jederzeit ihren Wert ändern oder ablesen

In PHP beginnen alle Variablennamen mit dem Symbol $.

Wie man die Variable benennt, ist nicht wichtig!

Bei Variablennamen wird zwischen Gross-/Kleinschreibung unterschieden. Zudem dürfen Sie keine Leerzeichen oder Bindestriche enthalten.

Um mehrere Wörter in einem Variablennamen zu verwenden, ist die Konvention entweder zu `$use_underscores_to_seperate` oder` $camelCaseVariableNames`
(Versuchen Sie, bei einer Konvention zu bleiben)

Seien Sie vorsichtig bei der Wiederverwendung von Variablennamen, der in der Variablen gespeicherte alte Wert wird dann überschrieben

PHP wird eine neue Variable (Platz in seinem Speicher) für jeden Namen erstellen, den es nicht als vorher verwendete Variable erkennt

Variablen können verwendet werden, um verschiedene Arten von Daten zu speichern:

 - Integer: `$num = 4;`
 - Float: `$number = 3.14;`
 - String: `$str = "this is some text!";`
 - Boolean: `$something = true;` // or `false`


### Anführungszeichen

Verwenden Sie Anführungszeichen (einzeln oder doppelt), um Standardtext zu umgeben

Anführungszeichen um Strings von Text unterscheidet diese Strings aus Programmbefehlen wie Funktionen - mehr dazu später

Es gibt einen Unterschied zwischen der Verwendung von Single-Quotes und Double-Quotes: Wenn ein Variablenname in Text erscheint, der von doppelten Anführungszeichen umgeben ist, wird sein aktueller Wert automatisch in den String gesetzt

```
$name = "Pete";
echo "Hello $name";
// "Hello Pete";
```


### Kommentare

Einzeilenkommentare fangen mit `//` oder `#` an.

```
// Einzeilenkommentar
# Ein weiterer Kommentar
```

Text rechts davon wird vom Interpreter ignoriert, bis wir eine neue Zeile starten.

Mehrzeilenkommentare benutzen `/*` und `*/` (genau wie bei JavaScript und CSS)

```
/*
  Mehrzeilen-
  kommentar
*/
```


### Operatoren

Diese werden in PHP verwendet, um Variablen zu überprüfen oder zuzuordnen

Wir haben schon ein paar Beispiele gesehen, der Rest wird nützlich sein, wenn wir weiter lernen

 - `=` einen Wert einer Variable zuweisen
 - `.` zwei Werte miteinander verbinden
 - `+` zwei Werte miteinander addieren


#### Vergleichs-Operatoren

 - `==` prüfen, ob etwas identisch zu etwas anderem ist (nicht Typen-sicher)
 - `!=` prüfen, ob etwas nicht identisch zu etwas anderem ist (nicht Typen-sicher)
 - `===` prüfen, ob etwas identisch zu etwas anderem ist (Typen-sicher)
 - `!==` prüfen, ob etwas nicht identisch zu etwas anderem ist (Typen-sicher)

(Wir neigen dazu, drei === häufiger als zwei zu verwenden, da es auch den "Typ" der Variablen prüft und daher genauer ist)

 - `>` prüfen, ob etwas grösser ist
 - `<` prüfen, ob etwas kleiner ist
 - `>=` prüfen, ob etwas grösser oder gleich ist
 - `<=` prüfen, ob etwas kleiner oder gleich ist


#### Mathematische Operatoren

 - `+` addieren
 - `-` subtrahieren
 - `*` multiplizieren
 - `/` dividieren

Die in der Mathematik gültige Punkt-vor-Strich-Regel kennt PHP nicht und wird daher nicht berücksichtigt.
Verwenden Sie stattdessen Klammern, um die Reihenfolge zu steuern, wie eine Gleichung berechnet wird:

```
$total = (($x * $y) + $z) / 3.14
```


### Arrays

Wir verwenden Arrays, wenn wir eine Sammlung von verwandten Datenbits speichern möchten

```
$planet = "Merucury";
$anotherPlanet = "Venus";
$planet3 = "Earth";
...
$planetEight = "Neptune";
```

Dies ist "verwandte" Informationen, also sollten wir sie zusammen speichern

```
$planets = array(
  "Mercury",
  "Venus",
  "Earth",
  "Mars",
  "Jupiter",
  "Saturn",
  "Uranus",
  "Neptune"
);
```

Wir können auf ein Item innerhalb eines Arrays zugreifen, indem wir auf seinen 'Index' referenzieren

```
echo $planets[2]; // === "Earth"
```

Jedes Item innerhalb eines Arrays verhält sich wie eine Variable

Auf einzelne Array-Elemente wird zugegriffen, indem man den Array-Variablennamen mit einem Index versieht, der in eckigen Klammern `$stuff[2]` eingeschlossen ist

Beachten Sie, dass Indizes bei 0 und nicht bei 1 beginnen!

Die Funktion `count()` gibt die Gesamtzahl der Elemente im Array zurück:

```
echo count($planets); // === 8
```


#### Assoziative Arrays

Dies sind Arrays mit nicht-numerischen Indizes

```
$earth = array(
  "radius" => 6371,
  "distanceFromSun" => 149600000
);
```

Dies bedeutet, dass wir auf ein Item im Array über seinen Namen und nicht auf einen numerischen Index verweisen können

```
echo $earth["radius"]; // === 6371
```

Assoziative Arrays werden oft verwendet, wenn wir komplexere Datensammlungen speichern möchten

Der Wert links vom Operator `=>` ist der Index, der Wert rechts ist der Wert des Elements


#### Warum verwenden wir Arrays

Arrays sind eine praktische Möglichkeit, Informationen zu speichern und zu nutzen

Wenn wir auf Daten von eingereichten Formularen zugreifen, verwenden wir oft Arrays

Wenn wir auf Daten aus Datenbanken zugreifen, verwenden wir oft Arrays


### Datei Includes

Es kann sinnvoll sein, verschiedene Teile einer Website in eine Anzahl von enthaltenen Dateien aufzuteilen

Zum Beispiel, auf einer typischen Website werden Kopf- und Fusszeile über alle Seiten konsistent sein

Nachdem diese in einer einzigen importierbaren Datei gespeichert wurden, müssen sie nur an einem Ort aktualisiert werden, um die gesamte Website zu aktualisieren

Eine statische HTML-Datei könnte wie folgt aussehen:

```
<!DOCTYPE html>
<html>
  <head>
    <title>Lorem ipsum</title>
  </head>
  <body>
    <!-- this is where page content goes -->
  </body>
</html>
```

Unsere header.php Include Datei könnte so aussehen:

```
<!DOCTYPE html>
<html>
  <head>
    <title>Lorem ipsum</title>
  </head>
  <body>
```

Unsere footer.php Include Datei könnte so aussehen:

```
  </body>
</html>
```

Das vereinfacht alle Seiten unserer Website:

```
<?php include_once "header.php"; ?>

<h1>Page content...</h1>

<?php include_once "footer.php"; ?>
```

Um Dateien zu importieren, benutzen Sie eine der folgenden PHP Funktionen:

 - `include`
 - `include_once`
 - `require`
 - `require_once`

`include_once` und `require_once` werden benutzt, um spezifische Funktinalität zu importieren, die man nur einmal auf der Seite benötigt. Beispielsweise die Details zur Datenbankverbindung

`include` und `require` können mehrfach in einer einzelnen Seite verwendet werden und sind daher praktisch, wenn es darum geht wiederholte Funktionalität zu importieren (z.B. eine 'Zurück-zum-Anfang' Link)

Wenn Sie versuchen, eine Datei mit `include` oder` include_once` zu importieren, und die Datei existiert nicht, gibt der Server eine Warnung aus und fährt fort.

Beim Versuch, eine Datei mit `require` oder` require_once` zu importieren, wenn die Datei nicht existiert, gibt der Server einen Fehler aus und stoppt.

(Sie werden lernen, eine der vier Optionen zu verwenden, je nach den Anforderungen des Include)


### Logikstrukturen

PHP kann nur dann verwendet werden, wenn bestimmte Bedingungen erfüllt sind

Die Haupttypen der bedingten Logikstrukturen sind:

  - if/else
  - for
  - foreach

(Nochmal, diese sind in den meisten Programmiersprachen üblich, nicht nur in PHP)


#### if/else

Verwenden Sie eine andere Logik, je nachdem, ob eine Anweisung wahr oder falsch ist

```
$today = date("l");

if ($today === "Friday") {
  echo "Hooray, it's Friday!";
} else {
  echo "Is it Friday yet?";
}
```

Um mehr als eine Bedingung zu verwenden, benutzen Sie:

 - `||` (oder)
 - `&&` (und)

Wir können mehrere if/else statments mit "else if" verbinden

```
$today = date("l");
$hour = date("G");

if ($today === "Friday" && $hour >= 17) {
  echo "Beer o'clock!";
} else if ($today === "Saturday" || $today === "Sunday" || $hour < 9 || $hour >= 17) {
  echo "Time to relax";
} else {
  echo "Get back to work!";
}
```


#### for Schleifen

Erlauben uns eine Logik zu wiederholen, bis eine Bedingung erfüllt ist:

```
for ($counter = 1900; $counter <= date("Y"); $counter++) {
  echo "<option>" . $counter . "</option>";
}
```

Das Ergebnis:

```
<option>1900<option>
<option>1901</option>
...
<option>201x</option>
```


#### foreach Schleifen

Werden benutzt, um durch Arrays zu laufen

```
$planets = array("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune");
foreach ($planets as $key => $planet) {
  echo "<p> Planet " . $key . " = " . $planet . "</p>";
}
```

Das Ergebnis:

```
<p>Planet 0 = Mercury</p>
<p>Planet 1 = Venus</p>
...
<p>Planet 7 = Neptune</p>
```

Beginnt mit dem zu durchlaufenden Array, gefolgt vom Schlüsselwort `as`, gefolgt von zwei Variablen: die erste bezieht sich auf den Index jeden Elements, die zweie auf den entsprechenden Wert.

(Wenn nur eine Variable nach dem `as` steht, bezieht es sich immer auf den Wert.)

In unserem Beispiel läuft die `foreach` Anweisung durch das Array `$planets` und schreibt pro Lauf ein Element in die Variable `$planet`


### Formulare

Hier ist ein einfaches HTML Formular:

```
<form action="" method="post">
  <fieldset>
    <legend>What is your name?</legend>
    <label for="name">Your name</label>
    <input id="name" name="name" type="text" />
    <input type="submit" value="Submit" />
  </fieldset>
</form>
```

Es gibt zwei wichtige Attribute in einem Formular: `action` und `method`:


#### Action

Das Action-Attribut in einem HTML-Formularelement bezieht sich auf die URL, an die das Formular bei der Übermittlung seine Daten senden soll.

Das Action-Attribut kann leer gelassen werden. In diesem Fall sendet das Formular Daten an die aktuelle URL.

Alternativ können Formulardaten bei der Übermittlung des Formulars an ein anderes Skript / URL gesendet werden.


#### Method

Das Method-Attribut kann eine dieser beiden Optionen haben, GET und POST

Bei der Verwendung eines Formulars zu GET- oder POST-Werten verwandelt PHP automatisch die Formulardaten in Variablen und setzt sie auf den Wert, der vom Benutzer eingegeben wurde.

Je nachdem, ob die Formularaktion auf GET oder POST gesetzt ist, stehen die Werte zur Verfügung als `$_GET['field-name']` oder `$_POST['field-name']`

Ob Sie GET oder POST verwenden, hängt davon ab, was für die aktuelle Situation besser geeignet ist.

Um PHP-seitig sowhl GET, als auch POST abzufangen ohne doppelt Code schreiben zu müssen, können Sie `$_REQUEST['field-name']` verwenden.


#### GET (hängt die Werte an die URL)

PROs:

 - nützlich zum URL hacken (die Werte in der URL sind als Namen und Werte mit ?, & und = von einander getrennt)
 - nützlich um direkt Links als Lesezeichen zu speichern

CONs:

 - Unsicher und sollte nicht für sensible Daten (bspw. Passwörter) verwendet werden
 - Kann nur eine begrenzte Menge an Daten enhalten
 - Kann nur einfache Formulardaten enthalten

#### POST (hängt keine Werte an die URL)

PROs:

 - Kann Dateien verarbeiten
 - Kann mehr Daten als GET verarbeiten
 - Der gepostete Inhalt ist vor dem Benutzer unsichtbar und somit für die Verarbeitung von Passwörtern brauchbar

CONs:

 - Kann nicht direkt als Lesezeichen gespeichert werden
 - Kann nicht über die URL verändert werden

Wenn das Formular abgeschickt wurde, können wir auf die über PHP eingegebenen Werte zugreifen


### Fehler

Anders als bei HTML, wenn der Server auf einen PHP-Fehler trifft, wird er wahrscheinlich stoppen, was dazu führt, dass keine Seite generiert wird

Die Fehlermeldungen sollten hilfreich sein, um zu zeigen, auf welcher Zeile der Fehler aufgetreten ist, und hoffentlich eine Nachricht, die anzeigt, was schief gelaufen ist. Diese Nachrichten sind oft kryptisch!

Fehler mit PHP sind weit häufiger als bei HTML / CSS:

  - Syntaxfehler
  - Fehlende Semikolons am Ende einer Zeile
  - Nicht genug (oder zu viele) Zitate, Klammern, geschweifte Klammern oder andere Interpunktion


## Arrays

### Mit Arrays arbeiten

Mit einfachen Variablen wie Strings und Zahlen, können wir mit `echo` ihren Wert an jedem Punkt ausgeben:

```
$planets = 5;
$planets = $planets + 3;
echo $planets; // 8
```

```
$sentence = "There are " . $planets . " planets";
echo $sentence;
// "There are 8 planets"
```

Wenn Sie das mit einem Array versuchen, bekommen Sie ... `Array`

```
$planets = array("Mercury", "Venus", "Earth", "Mars", "Jupiter");
echo $planets; // Array
```

Benutzen Sie stattdessen `foreach`:

```
$planets = array("Mercury", "Venus", "Earth", "Mars", "Jupiter");
foreach ($planets as $planet) {
  echo "<p>" . $planet . "</p>";
}
```

Das Ergbnis sieht dann so aus:

```
<p>Mercury</p>
<p>Venus</p>
...
```

Das ist gut, wenn man die Struktur des Arrays kennt, aber das ist nicht immer der Fall

Wenn Sie eine Reihe von Daten haben, die Sie nicht kennen, bietet PHP eine einfache Möglichkeit, die Inhalte zu sehen

Um die Inhalte eines Arrays zu betrachten, können Sie die Funktion `print_r ()` verwenden

```
$planets = array("Mercury", "Venus", "Earth", "Mars", "Jupiter");
print_r($planets);
Array ( [0] => "Mercury" [1] => "Venus" [2] => "Earth" [3] => "Mars" [4] => "Jupiter" )
```

Das funktioniert zwar, ist aber schwer zu lesen

Wenn Sie `print_r()` benutzen, ist es ratsam, es mit HTTML `<pre>` Tags einzufassen:

```
$planets = array("Mercury", "Venus", "Earth", "Mars", "Jupiter");
echo "<pre>";
print_r($planets);
echo "</pre>";
```

Das Ergbnis sieht so aus:

```
Array (
  [0] => Mercury
  [1] => Venus
  [2] => Earth
  [3] => Mars
  [4] => Jupiter
)
```

`print_r()` funktioniert auch mit assoziativen Arrays:

```
$earth = array(
  "radius" => 6371,
  "distanceFromSun" => 149600000
);

echo "<pre>";
print_r($earth);
echo "</pre>";
```

Das Ergbnis lautet:

```
Array (
  [radius] => 6371
  [distanceFromSun] => 149600000
)
```

`print_r ()` ist nicht für ein Endprodukt nützlich - Sie möchten keine Informationen auf diese Weise anzeigen

Aber während der Entwicklung ist es eine praktische Möglichkeit, den aktuellen Wert eines Arrays zu überprüfen


### Warum Arrays sind nützlich

Arrays sind eine nützliche Möglichkeit, Informationen zu verwenden / zu manipulieren / zu filtern

Später werden wir diese Arrays nicht manuell erstellen

Stattdessen werden wir Daten aus externen Quellen abrufen - z.B. Aus einer Datenbank

Wir werden nicht wissen, was der Inhalt des Arrays ist, aber eine Vorstellung von seiner Struktur haben

Wenn wir diese Daten erhalten, müssen wir sie in ein Format setzen, das wir mit PHP manipulieren können

Wir werden lernen, wie man Informationen aus einer Datenbank extrahiert und sie zu einem Array macht

Wenn Sie lernen, wie Sie Arrays verwenden, dann wissen Sie, wie Sie Daten aus verschiedenen Quellen, wie z.B. eine Datenbank oder einen API-Anruf von einer anderen Website, verwenden


### Multi-dimensionale Arrays

Arrays können eine Mischung aus verschiedenen Arten von Inhalten enthalten:

```
$things = array(1, 5, "hello", 3.14);
foreach ($things as $thing) {
  echo "<p>". $thing . " = " . gettype($thing) . "</p>";
}

1 = integer
5 = integer
hello = string
3.14 = double
```

Mit unseren Planetenbeispielen von vorhin, stellen wir uns vor, dass wir Informationen über jeden Planeten als Array speichern möchten

```
$mercury => array(
  "size" => 0.3,
  "distance" => 0.3
);
```

```
$venus => array(
  "size" => 0.9,
  "distance" => 0.6
);
```

Das vorherige Beispiel erlaubt uns, Informationen über jeden Planeten zu speichern

Aber es gibt keinen einfachen Weg, um alle Planeten zusammenzufassen

Der Grund für die Verwendung von Arrays besteht darin, Inhalte zusammenzufassen

Wir wollen jede dieser Planetenarrays in ein einziges Array setzen

Wir können stattdessen diese in einem einzigen Array enthalten, das andere Arrays enthält:

```
$planets = array(
  "mercury" => array(
    "size" => 0.3,
    "distance" => 0.3
  ),
  "venus" => array(
    "size" => 0.9,
    "distance" => 0.6
  ),
  "earth" => array(
    "size" => 1,
    "distance" => 1
  )
);
```

Arrays, die andere Arrays enthalten, heissen *multi-dimensionale Arrays*

Wir können auf die Werte aus den Arrays auf die gleiche Weise wie zuvor zugreifen:

```
foreach ($planets as $planetName => $planetData) {
  echo "<p>" . $planetName . " size = " . $planetData["size"] . "</p>";
}
```

Das Ergebnis lautet:

```
<p>mercury size = 0.3</p>
<p>venus size = 0.9</p>
<p>earth size = 1</p>
```

Die Fähigkeit, mehrdimensionale Arrays zu erstellen, ist nützlich, da es uns erlaubt, eine komplexere Informationsstruktur zu verwenden

In den meisten real-world Beispiele werden die Daten, die Sie verwenden werden, komplexer als eine einfache Reihe von Informationen

Während wir das ausarbeiten, erlaubt uns die `print_r()` Funktion, die wir vorhin gesehen haben, eine Vorschau aller Werte im Array


#### Verschachtelte foreach Schleifen

Eine Möglichkeit, auf alle Informationen innerhalb eines mehrdimensionalen Arrays zuzugreifen, besteht darin, eine "foreach"-Schleife innerhalb einer anderen "foreach"-Schleife zu verwenden

```
foreach ($planets as $planetName => $planetData) {
  echo "<h2>" . $planetName . "</h2>";

  foreach($planetData as $attribute => $value) {
    echo "<p><strong>" . $attribute . "</strong>: <em>" . $value . "</em></p>";
  }
}
```

Wir können die Informationen auf unterschiedliche Weise manipulieren, verschiedene Teile in verschiedenen Situationen verwenden

Zum Beispiel können wir nicht alle detaillierten Informationen für jedes Element in einer langen Seite anzeigen

Wir können einfach nur jedes Element zusammenfassen, dann, wenn man es auswählt, zeigen Sie die detaillierten Informationen nur für diesen Artikel an

Lassen Sie uns gerade den Namen jedes Planeten ausgeben:

```
foreach($planets as $planetName => $planetData) {
  echo '<li><a href="?planet=' . $planetName . '">' . $planetName . '</a></li>';
}
```

Dadurch werden folgende Links generiert:

```
<li><a href="?planet=mercury">mercury</a></li>
<li><a href="?planet=venus">venus</a></li>
<li><a href="?planet=earth">earth</a></li>
```

Als nächstes lernen wir, wie man diese Links benutzt, um planetenspezifische Daten anzuzeigen


### Superglobale Variables

Superglobale Variablen sind spezielle Variablen, die automatisch von PHP erstellt werden.

Es handelt sich um assoziative Arrays, die Werte enthalten, die von der Benutzereingabe oder dem Server erfasst wurden

Sie heissen superglobal, weil sie in jedem variablen Bereich zugänglich sind (mehr dazu später)

Die wichtigsten superglobalen Arrays:

 - `$_SERVER`
 - `$_GET`
 - `$_POST`
 - `$_COOKIE`
 - `$_SESSION`

Wir haben bereits zwei Beispiele für `$_GET` und `$_POST` gesehen. Diese Arrays werden automatisch befüllt, wenn ein Formular abgeschickt wird

Das 'name' Attribut eines jeden Formularelements wird in diesen Arrays benutzt

z.B. wenn Sie folgendes Formularelement haben:

```
<input type="text" name="firstname" id="firstname" />
```

Wenn Sie das Formular abschicken, ist entweder `$_GET['firstname']` oder `$_POST['firstname']` verfügbar

Die `$_POST` superglobale Variable wird in der Regel über ein Formular befüllt.

`$_GET` Parameter können das zwar auch über Formulare, aber das ist nicht der einzige Weg

Wir können das auch über Links erreichen

Um eine Variable über eine URL zu befüllen, fügen Sie den Parameter einfach ans Ende der URL

Am Ende der standard URL fügen Sie ein `?`, gefolgt von der Variable und deren Wert, jeweils getrennt mit einem `=`

```
<a href="index.php?index=value">
<a href="index.php?name=pete">
```

Um mehrere Variablen einer URL hinzuzufügen, trennen Sie sie mit `&`

Denken Sie daran, das `&` in ihrem HTML als `&amp;` zu notieren, sonst schlägt die Validierung fehl.

```
<a href="file.php?key=value&amp;lorem=ipsum&amp;foo=bar">
<a href="file.php?name=pete&amp;colour=orange">
```

Dies ist ein nützlicher Weg, um einfache Variablen zwischen verschiedenen Seiten zu übergeben

Zurück zu unseren Planeten Beispiel, so weit haben wir eine Liste von Links, eine für jeden Planetennamen

Diese Links geben den ausgewählten Planetnamen an die URL an

Wenn ein Planetenlink geklickt wurde, hat `$_GET['Planet']` einen Wert

Wir können dies verwenden, kombiniert mit einer einfachen if / else-Anweisung, um festzustellen, ob die Übersichtsliste oder Detailansicht angezeigt werden soll


```
<?php
  // planets array, details displayed above...
  $planets = array(...);

  // has a planet been selected?
  if (!empty($_GET['planet'])) {
    // save the variable (quicker to not reference the GET array each time!)
    $planet = $_GET['planet'];
?>
  <p>You have selected planet <strong><?php echo $planet; ?></strong>. Here are its details:</p>
  <ul>
<?php
    // loop through each of the planet's attributes
    foreach ($planets[$planet] as $key => $value) {
      echo '<li><strong>'.$key.'</strong>: <em>'.$value.'</em></li>';
    }
?>
  </ul>
<?php
  } else {
?>
    <p>Select a planet to see its details...</p>
    <ul>
<?php
    foreach($planets as $planetName => $planetData) {
      echo '<li><a href="?planet='.$planetName.'">'.$planetName.'</a></li>';
    }
?>
    </ul>
<?php
  }
?>
```


### $_SERVER

Hier finden Sie nützliche Informationen zum Server

Beispielsweise können Sie die URL der aktuellen Seite, die aktuell verwendete Datei oder den Browser des Benutzers erkennen

Sie können `print_r ()` verwenden, um alle möglichen Werte des `$_SERVER` Arrays zu sehen


## State, Sessions und Cookies

Ein wichtiger Punkt zu beachten: Variablen werden nicht automatisch gespeichert oder gespeichert, wenn Sie zwischen den Seiten wechseln

Das `$_POST`-Array wird nur auf einer Seite gefüllt, nachdem ein Formular übergeben wurde

Das `$_GET`-Array wird nur dann gefüllt, wenn auf der vorherigen Seite ein Formular übergeben wurde oder wenn Parameter an die URL angehängt werden

Um Variablen zwischen Seitenaktualisierungen zu speichern, müssen wir eine alternative Technik verwenden

HTTP ist ein "stateless Protokoll"

Dies bedeutet, dass jede Serveranforderung unabhängig ist - jedes Mal, wenn Sie eine Seite anfordern, vergisst der Server diese am Schluss

PHP pflegt keine Verbindung zwischen Client und Server, es gibt keine Möglichkeit, eine Sequenz von Anfragen zu identifizieren, die von demselben Benutzer kommen

Um in einer Website angemeldet zu bleiben, benötigen Sie einen Weg, um über mehrere Anfragen Credentials zu ermitteln

Es ist möglich, Informationen zu übermitteln, indem ein Wert an die URL angehängt wird

Es kann auch als versteckte Felder in einer Form hinzugefügt werden

In beiden Fällen ist die Information jedoch am Client-Ende potenziell sichtbar, entweder in der Adressleiste des Browsers oder im Quellcode der konstruierten Seite

Eine bessere Technik ist nötig!


### Cookies

Cookies sind kleine Daten, die zwischen Browser und Server als Teil des http-Nachrichten-Headers statt im Dokumentenkörper übergeben werden

Sie werden als Datei auf dem Client-Rechner gespeichert

Sie können für eine einzelne Browser-Sitzung gespeichert werden (bis Sie den Browser schliessen) oder für einen bestimmten Zeitraum

Sie können gelesen und geschrieben werden von PHP und JavaScript

Wenn irgendwelche Cookies für die jeweilige Website vorhanden sind, stehen sie in der `$_COOKIE` superglobalen Variable zur Verfügung

(Javascript kann auf dieselben Cookies zugreifen, indem auf das `document.cookie`-Objekt verwiesen wird)

Cookies werden in PHP mit der eingebauten Funktion `setcookie()` erstellt

Wenn wir zum Beispiel während einer einzigen Browser-Sitzung einen mitgelieferten Benutzernamen abgeben wollten, würden wir folgende Befehle verwenden:

```
$username = $_GET['username'];
setcookie('username', $username);
```

Dies wäre dann als `$_COOKIE ['username']` zugänglich, egal wie oft ein Benutzer die Seite aktualisiert hat, bis der Browser geschlossen wurde.

Es ist möglich, einen Cookie länger als eine Browser-Session zu machen - Sie können Ihr eigenes Verfallsdatum festlegen:

```
// store the cookie for 30 days from today
setcookie('username', $username, time() + 60*60*24*30)
```

```
// store the cookie until the eighteenth of July, 2026
setcookie('username', $username, mktime(0,0,0,7,18,2026));
```

Der dritte Parameter für die `setcookie()` Funktion nimmt einen numerischen Wert ein, der der Zeit entspricht, die das Cookie ablaufen soll

Um ein Cookie zu entfernen, setzen Sie einfach seinen Datumswert auf ein Datum in der Vergangenheit

```
setcookie('username', NULL, -1);
```

Befehle zum Einstellen oder Ändern von Cookie-Werten beinhalten das Schreiben eines Dokumentenkopfes, so dass sie vor dem Ausgeben eines anderen Dokumentinhalts auftreten müssen

PHP-Code, um Cookies einzustellen, kann nicht mit normalem HTML durchsetzt werden, es muss am Anfang einer Seite sein, bevor irgendein HTML ausgegeben wird

(Sogar ein einziges Zeichen am Anfang einer PHP-Datei vor dem `<?php`-Tag reicht aus, um einen Fehler zu erzeugen.)

PROs

 - Cookies machen es einfacher, sich an Daten zu erinnern, ohne es immer wieder hin und her zu senden

CONs

 - Browser können eingestellt werden, um Cookies zu verweigern, ihre Lebensdauer zu begrenzen oder ihre Ankunft zu warnen
 - Benutzer können Cookies ansehen, bearbeiten und löschen

Sie können Cookies verwenden, aber nicht auf sie verlassen...


### Sessions

Sessions sind eine Alternative zu Cookies

PHP ermöglicht es Ihnen, den Beginn einer eindeutig identifizierten Sitzung zu definieren und mit ihr eine beliebige Anzahl von Variablen zu verknüpfen, die für jedes Skript, das während dieser Sitzung ausgeführt wird, zugänglich sind.

Eine Sitzung wird durch Aufruf der PHP-Funktion `session_start()` initialisiert

Dies muss platziert werden, bevor ein HTML ausgegeben wurde

Setzen Sie dies am Anfang einer PHP-Datei:

```
<?php

  session_start();

  // ... the rest of the code starts here
?>
```

Sobald eine Sitzung gestartet wurde, können wir mit dem superglobalen `$_SESSION` Array auf Variablen verweisen

Session-Variablen können jederzeit dem assoziativen Array `$_SESSION` zugeordnet oder abgerufen werden

```
// start the session - must always happen at the top of the page
session_start();

// (assuming form has been posted, set session variable)
$_SESSION['username'] = $_POST['username'];

// this is now accessible anywhere we have a session
echo $_SESSION['username'];
```

Sobald Sie eine Session-Variable gesetzt haben, bleibt sie bestehen, bis Sie sie entfernen oder die Browser-Sitzung beenden

Um eine Sitzungsvariable zu entfernen, verwenden Sie `unset()`

```
unset($_SESSION['username']);
```

Benutzen Sie Sessions anstatt Cookies:

 - Session-Werte werden in temporären Dateien am Server-Ende und nicht im Client gespeichert
 - Deshalb sind Sessions weit sicherer und zuverlässiger als Cookies


## PHP und MySQL

***(Es könnte hilfreich sein, die Datenbank Notizen zu lesen, bevor Sie fortfahren)***


### Mit PHP zu einer MySQL Datenbank verbinden

Um eine Verbindung zu einer MySQL-Datenbank mit PHP herzustellen, verwenden wir eine _Klasse_ namens `mysqli`

Folgende Zeile PHP-Codes macht genau das:

```
$db = new mysqli("host", "username", "password", "database");
```

Wir können ein einfaches PHP-Skript erstellen, um zu testen, ob wir eine korrekte Verbindung zur Datenbank herstellen können:

```
// connect
$db = new mysqli("server","u","p","db");

// check if there was an error
if ($db->connect_error) {
  echo "Connect failed: " . $db->connect_error;
  exit();
} else {
  // no error!
  echo "Database connected!";
}
```

Erläuterung des Datenbankverbindungscodes:

  - Wir speichern die Datenbankverbindung in einer Variablen namens `$db` (Wir werden diese Variable später nochmals verwenden, wenn wir die Datenbank abfragen)
  - Wir testen, ob es einen Fehler gibt (z.B. wegen falscher Anmeldeinformationen), indem man schaut, ob `$db->connect_error` einen Wert hat
  - Wenn es einen Fehler gibt, dann zeigen wir ihn
  - Ansonsten war die Datenbankverbindung erfolgreich!

Beachten Sie, dass von nun an in diesen Beispielen davon ausgegangen wird, dass die Datenbankverbindung aktiv ist

Es ist oft eine gute Idee, die Verbindungsdetails in einer separaten Datei zu halten

Diese Datei kann zu Beginn jeder Seite mit `require_once` importiert werden

Dieser Ansatz bedeutet, dass Sie nur den Inhalt für diese an einem Ort aktualisieren müssen

(Eine gute Praxis, um zu starten!)


### SQL Abfragen mit PHP ausführen

Sobald wir eine Verbindung zur Datenbank aufgebaut haben, können wir sie mit SQL abfragen

Ein grundlegendes SQL-Beispiel ist, alles aus der Antworttabelle auszuwählen:

```
SELECT * FROM `answers`
```

Dies sollte den folgenden Inhalt zurückgeben:


| id | question_id | user_id | answer    | tweet_id    | date_added          |
|----|-------------|---------|-----------|-------------|---------------------|
| 1  | 1           | 1       | Edam      | 23741876128 | 2013-03-19 18:34:23 |
| 2  | 2           | 1       | Charles   | 23741456214 | 2013-03-21 18:35:51 |
| 3  | 1           | 2       | Melted    | 23723849723 | 2013-03-22 09:02:12 |


Wenn wir es in PHP bekommen, werden diese Daten als assoziatives Array dargestellt, wie wir es früher gesehen haben

Um dies mit PHP auszuführen, fügen wir zuerst unsere SQL-Abfrage einer Variablen hinzu:

```
$query = "SELECT * FROM `answers`";
```

Dann führen wir die Abfrage aus ...

```
$result = $db->query($query);
```

... und holen das Ergebnis

```
$row = $result->fetch_assoc();
```

Dies wird uns die relevanten Daten in einem assoziativen Array zurückgeben, das in der Variablen `$row` gespeichert ist


Hier ein Beispiel

```
// include connection settings
require_once "../includes/connect.php";

// get a list of all answers in the database
$query = "SELECT * FROM `answers`";

// perform the query
$result = $db->query($query);

// loop through the results as an associative array
while ($row = $result->fetch_assoc()) {
  echo "<pre>";
  print_r($row);
  echo "</pre>";
}
```


### while() Schleifen

Wir wollen jede Zeile in der Tabelle in ein einfaches PHP assoziatives Array umwandeln

Wir werden mit jedem Ergebnis einzeln umgehen, indem wir sie eines nach dem anderen durchschleifen

Wir werden eine `while()` Schleife verwenden, die in vielerlei Hinsicht den `foreach()` Schleifen ähnelt, die wir bisher gesehen haben

Die while-Schleife setzt die Variable `$row` auf ein Array, das die Werte der aktuellen Zeile in der Tabelle enthält

Die `$row`-Array-Schlüssel sind die Tabellenspaltennamen

Wenn das erste Mal die while-Schleife ausgeführt wird, sind die folgenden Werte vorhanden

```
echo $row['id'];            // 1
echo $row['answer'];        // 'Edam'
echo $row['date_added'];    // '2013-03-19 18:34:23'
```

Wenn das Skript das Ende der while-Schleife erreicht - das schliessende `}` - geht es zurück zum Anfang der while-Schleife, aber dieses Mal wird der Wert von `$row` auf die nächste Zeile in der Tabelle gesetzt

Dies wird fortgesetzt, bis es jede Zeile durchlaufen hat, die von der SQL-Abfrage zurückgegeben wurde


### Mehrere SQL Abfragen

Es ist einfach, die SQL-Abfrage zu ändern, um die Daten zu aktualisieren, die wir erhalten werden

Im nächsten Beispiel habe ich gerade die Abfrage von der `answers`- auf die `questions`-Tabelle geändert, um unterschiedliche Ergebnisse zu erhalten

```
$question_query = "SELECT * FROM `questions`";
```


### SQL Fehler

Es ist eine gute Idee, eine if / else bedingte Anweisung um die Abfrage zu wickeln

Dies wird dazu beitragen, Fehler mit der SQL-Abfrage zu identifizieren

```
// get a list of all content from an unknown table
$query = "SELECT * FROM `lorem_ipsum`";

// perform the query
if ($result = $db->query($query)) {

  // ... display results as before

// if there was an error with your query
// this will display it
} else {
  echo "SQL Error: " . $db->error;
}
```


### CRUD

Wir haben jetzt funktionierende SELECT SQL-Abfragen mit PHP

Wir kommen später wieder darauf zurück

Lassen Sie uns die anderen CRUD-Befehle anschauen

 - Create = `INSERT`
 - Request = `SELECT`
 - Update = `UPDATE`
 - Delete = `DELETE`

Wir können auch PHP-Skripte schreiben, um Daten mit SQL zu erstellen, zu aktualisieren und zu löschen

Diese Beispiele verwenden einen Wert namens `affected_rows`, um zu testen, wie viele Zeilen (falls vorhanden) in der Datenbank geändert wurden

Um zu überprüfen, ob sie die Daten geändert haben, könnten wir zurückgehen und uns eines der `SELECT` Beispiele wieder anschauen


#### INSERT

Dieser SQL-Befehl fügt einen neuen Eintrag zur Tabelle `questions` hinzu:

```
INSERT INTO
  `questions` (`id`, `question`, `date_added`)
VALUES
  (3, 'Favourite Fish', 2013-03-25 18:34:13);
```

Dies kann durch ein PHP-Skript in ähnlicher Weise wie die SELECT-Befehle ausgeführt werden, die wir früher gesehen haben

```
// add new question
$query = "INSERT INTO `questions` (`id`, `question`, `date_added`) VALUES (3, 'Favourite Fish', 2013-03-25 18:34:13);";

// perform the query
$result = $db->query($query);
if ($result) {

  // output a count of how many rows were changed
  echo "SQL successful, affected rows: " . $db->affected_rows;

// there was an SQL error
} else {
    echo "SQL Error: " . $db->error;
}
```


#### UPDATE

Dieser SQL-Befehl aktualisiert das Fragefeld des Eintrags, den wir gerade der Tabelle `questions` hinzugefügt haben:

```
UPDATE `questions` SET `question` = 'Favourite Fruit' WHERE `id` = 3;
```

Dies kann durch ein PHP-Skript auf die gleiche Weise wie der INSERT-Befehl ausgeführt werden

```
// update question
$query = "UPDATE `questions` SET `question` = 'Favourite Fruit' WHERE `id` = 3";

// perform the query
$result = $db->query($query);
if ($result) {
	// output a count of how many rows were changed
	echo "SQL successful, affected rows: " . $db->affected_rows;
} else {
	// there was an SQL error
	echo "SQL Error: " . $db->error;
}
```


#### DELETE

Dieser SQL-Befehl löscht die Frage, die wir gerade der Tabelle `questions` hinzugefügt haben:

```
DELETE FROM `questions` WHERE `id` = 3;
```

Dies kann durch ein PHP-Skript auf die gleiche Weise wie die INSERT- und UPDATE-Befehle ausgeführt werden

```
// delete question
$query = "DELETE FROM `questions` WHERE `id` = 3;";

// perform the query
$result = $db->query($query);
if ($result) {

  // output a count of how many rows were changed
  echo "SQL successful, affected rows: " . $db->affected_rows;

// there was an SQL error
} else {
    echo "SQL Error: " . $db->error;
}
```


### Ergebnisse anzeigen

An diesem Punkt haben wir grundlegende SELECT SQL Abfragen, die mit PHP arbeiten

Jetzt verwenden wir `print_r()` um zu testen, dass wir Daten in einer Variablen haben, ähnlich wie die Beispiele, die wir früher gesehen haben

Dies ist während der Entwicklung in Ordnung, aber Sie wollen nicht auf diese Weise Daten auf einer produktiven Website anzeigen

Wir müssen lernen, wie man das SQL-Abfrage-Ergebnis-Array, das wir erhalten, nehmen und es richtig mit HTML anzeigen

Mit einer while-Schleife können Sie jede Zeile einzeln aufrufen:

```
// query the database
$query = "SELECT `id`, `answer`, `date_added` FROM `answers`";

// fetch all results
$result = $db->query($query);

// loop through each result one at a time
while ($row = $result->fetch_assoc()) {
  // do something with $row
}
```

Die while-Schleife setzt die Variable `$row` auf ein Array, das die Werte der aktuellen Zeile in der Tabelle enthält

Die `$row`-Array-Schlüssel sind die Tabellenspaltennamen

Wenn das erste Mal die while-Schleife ausgeführt wird, sind die folgenden Werte vorhanden

```
echo $row['id'];            // 1
echo $row['answer'];        // 'Edam'
echo $row['date_added'];    // '2013-03-19 18:34:23'
```

Um diese dem HTML hinzuzufügen:

```
// query the database
$query = "SELECT `id`, `answer`, `date_added` FROM `answers`";

// fetch all results
$result = $db->query($query);

// loop through each result one at a time
while ($row = $result->fetch_assoc()) {
    echo '
      <p>
        Answer ' . $row['id'] . ' = ' . $row['answer'] . ' (added on ' . $row['date_added'] . ')
      </p>
    ';
}
```

### Ergebnisse zählen

Sie werden nur Ergebnisse anzeigen wollen, wenn es welche gibt

Um dies zu tun, können Sie `num_rows` verwenden, um die Anzahl der zurückgegebenen Zeilen zu zählen


```
$result = $db->query($query);

// check we have a result
if ($result->num_rows > 0) {
  // do something
  echo "There were " . $result->num_rows . " results";

// if there are no results
} else {
  // do something else
  echo "Sorry, there were no results";
}
```


### Anpassen von Abfragen basierend auf Benutzereingaben

Bis zu diesem Punkt haben wir feste SQL-Abfragen gesehen

Wir können PHP verwenden, um unsere SQL-Abfragen dynamisch anzupassen, indem wir Variablen verwenden, anstatt harte Codierungswerte

Zum Beispiel könnten wir ein HTML-Formular verwenden, um einem Benutzer zu erlauben, einen Wert einzugeben, der dann in unserer Datenbank gesucht wird

```
$query = "SELECT * FROM `answers` WHERE `answer` LIKE '%" . $_GET['suggestion'] . "%''";
```
(Randnotiz: dieses Beispiel erlaubt SQL Injection!)


#### Dynamische CRUD Abfragen

Wir haben früher einige grundlegende Beispiele für andere CRUD-Befehle gesehen, die für INSERT, UPDATE und DELETE Daten aus der Datenbank verwendet wurden

Wir können diese mit HTML-Formularen kombinieren, um diese dynamischer zu machen

```
<form method="post" action="">
  <fieldset>
    <legend>Add question</legend>
    <label for="question">Question</label>
    <input id="question" name="question" type="text" value="" />
    <input type="submit" value="Submit" />
  </fieldset>
</form>
```

Dieses Formular kann verwendet werden, um neue Fragen hinzuzufügen:

```
// check if form has been posted
if (!empty($_POST) && !empty($_POST['question'])) {

// create insert SQL query
$query = "INSERT INTO `questions` (`question`, `date_added`) VALUES ('".$_POST['question']."', NOW())";

$result = $db->query($query);
```

Es gibt ein Problem mit diesem Einfügungsformular - es prüft nicht auf vorhandene Daten vor dem Hinzufügen einer neuen Zeile zur Datenbank

Vor dem Hinzufügen einer neuen Frage sollte zunächst geprüft werden, ob der Fragecode bereits vorhanden ist

(Dieselbe Technik kann praktisch sein, wenn man darüber nachdenkt, Benutzer zu Ihrer Website hinzuzufügen - Sie sollten nicht zwei Benutzer mit demselben Benutzernamen haben)

```
// only add to the database if the form has been submitted
if (!empty($_POST) && !empty($_POST['question'])) {

  // save a reference to the question
  $question = $_POST['question'];

  // check whether question exists already
  $query = "SELECT COUNT(*) AS `count` FROM `questions` WHERE `question` = '".$question."'";
  $result = $db->query($query);
  $data = $result->fetch_assoc();

  // if question exists already, don't add a new one
  if ($data['count'] > 0) {
    echo "<p>This question exists already, please add a different one</p>";
  // no question, so add it
  } else {
    // insert SQL query
    $query = "INSERT INTO `questions` (`question`, `date_added`) VALUES ('".$question."', NOW())";
    // perform the query
    $result = $db->query($query);
    // check the query was successful
    if ($result) {
      // output a count of how many rows were changed
      echo "<p>SQL successful, affected rows: " . $db->affected_rows . "</p>";
    } else {
      // there was an SQL error
      echo "SQL Error: " . $db->error;
    }
  }
}
```


#### Updaten und löschen

Beim Aktualisieren oder Löschen von Daten ist es oft sinnvoll, dies zu einem zweistufigen Prozess zu machen

Erstens sollte der Benutzer in der Lage sein, das zu aktualisierende oder zu löschende Element auszuwählen

Sobald ein Artikel für die Aktualisierung ausgewählt wurde, füllen wir die Werte eines Formulars vor, um es einfacher zu aktualisieren

Sobald ein Artikel zum Löschen ausgewählt wurde, bieten wir dem Benutzer eine endgültige Chance, sich zu entscheiden. (Denken Sie daran, es gibt keine Rückgängig-Funktion!)


## Verschiedene Tipps

Viele dieser Themen sind unabhängig voneinander, manche können relevanter oder interessanter sein als andere ...


### Seitenarchitektur

Bei der Erstellung einer Website ist es wichtig, über die Website-Struktur (oder Architektur) zu entscheiden,

  - Welche Abschnitte (oder Seiten) wird die Website haben?
  - Gibt es Unterabschnitte?
  - Kann jeder Benutzer auf jeden Teil der Website zugreifen, oder müssen Sie angemeldet sein, um auf bestimmte Aspekte zuzugreifen?


Eine Beispielseitenliste:

  - Startseite
  - Artikeldetailsseite
  - Benutzeranmeldeseite
  - Benutzerregistrierungsseite
  - Hinzufügen einer Artikelseite
  - (etc)

Sobald Sie sich für die Website-Architektur entschieden haben, können Sie die Dateistruktur in einer logischen Weise zusammenfügen

Sie können eine PHP-Datei für jede Seite in der Website erstellen

Sie könnten diese alle im selben Ordner haben und sie anders benennen:

 - index.php
 - details.php
 - login.php
 - register.php
 - add.php

Oder Sie könnten sie alle index.php nennen und in verschiedene Verzeichnisse legen:

 - /index.php
 - /details/index.php
 - /login/index.php
 - /register/index.php
 - /add/index.php

Der Vorteil des zweiten Ansatzes ist, dass Sie nicht auf den Dateinamen verweisen müssen, was Ihre URLs sauberer macht

 - http://url.com/details.php
 - http://url.com/register.php

vs.

 - http://url.com/details/
 - http://url.com/register/

(subjektive Meinung!)

Erwägen Sie das Erstellen eines Include- (oder Assets-) Verzeichnisses für alle Dateien, die nicht direkt in einem Browser angezeigt werden

Beispiele für Dateien, die in dieses Verzeichnis gehen könnten, sind:

 - eine CSS-Datei
 - ein Ordner, der Bilder enthält
 - eine JavaScript-Datei (oder einen Ordner mit JavaScript-Dateien)
 - PHP Include-Dateien
   - Datenbankverbindung
   - header und footer

Betrachten Sie die Trennung von Funktionalität in Dateien:

 - Achten Sie darauf die gleiche Funktionalität nicht in mehrere Dateien hinzuzufügen
 - Jedes Mal, wenn Sie Code wiederholen, gibt es eine effizientere Möglichkeit, es zu tun

Erwägen Sie, diesen Code in eine separate Datei zu setzen und ihn jedes Mal einzubinden, wenn Sie ihn brauchen (wie wir es mit der Datenbank-Verbindung gemacht haben, Header, Footer)

 - Sie können Ihre Session-Handling-Logik in eine Datei auslagern, die Sie am Anfang jeder Seite laden
 - Sie können Ihre Datenbankanrufe in eine separate Datei stellen
 - Darüber hinaus können Sie Funktionen verwenden, und darauf zu verweisen, wann immer sie benötigt werden (wir werden die Funktionen ein wenig später betrachten)


### Header Include Daten und Seitentitel

Wir haben Beispiele von Header und Footer Include-Dateien gesehen:

```
<?php require_once "header.php"; ?>

  <!-- page content goes here -->

<?php require_once "footer.php"; ?>
```

Im vorherigen Beispiel wurde für jede Seite der gleiche Titel verwendet

Um einen anderen Seitentitel für jede Seite festzulegen, können Sie eine Variable über dem Header einstellen:

```
<?php
  $title = "Details page";
  require_once "header.php";
?>
```

Die `$title` Variable ist dann verfügbar und kann mit echo in der header.php Datei ausgegeben werden, so dass man auf jeder Seite einen anderen Seitentitel hat


### Funktionen

Funktionen sind eine Möglichkeit, eine Reihe von Befehlen zusammenzufassen, damit wir sie wieder verwenden können, wann immer wir müssen

Funktionen sind nützlich, weil man sie einmal schreiben kann, dann benutzt man sie wo immer und wann immer man es benötigt

Es gibt zwei Arten von Funktion:

  - Die, die in der Sprache bereits eingebaut sind
  - Funktionen, die wir selbst schreiben - oder alternativ `Drittanbieter`-Funktionen, die jemand anderes geschrieben hat, die wir einschliessen und verwenden können


#### Native Funktionen

Es gibt viele eingebaute Funktionen in PHP, die uns erlauben, leicht eine bestimmte Aufgabe durchzuführen. Beispielsweise:

  - `date()` - Holen Sie sich das aktuelle Datum / Uhrzeit
  - `mail()` - Senden Sie eine E-Mail
  - `scandir()` - Auflisten aller Dateien und Ordner in einem bestimmten Verzeichnis auf dem Webserver

Es gibt eine umfassende Liste bei [php.net] (http://php.net) - Das Suchfeld dort ist ein guter Ort zu starten


#### Drittanbieterfunktionen

Drittanbieter-Funktionen sind nützlich, wenn Sie etwas tun wollen, das wahrscheinlich schon oft getan wurde

Oft können Sie feststellen, dass jemand anderes eine Lösung erstellt hat und ihr Beispiel online gestellt hat

Websites wie Stack Overflow, sind gute Orte, um danach zu suchen

Code-Bibliotheken und Frameworks enthalten oft eine Reihe nützlicher Funktionen - mehr dazu später ...


#### Funktionen schreiben

Das Erstellen eigener Funktionen ist ein nützlicher Weg, um die Codewiederholung zu reduzieren

Wenn Sie selbst mehrmals denselben Code schreiben, könnte es durch die Erstellung einer Funktion effizienter gemacht werden

```
function doSomething() {
  // code
}
```

Wie Sie eine Website bauen, können Situationen auftreten, in denen eine Funktion helfen könnte

So definieren Sie eine Funktion:

```
function name() {
  // do something
}
```

Dann, um die Funktion aufzurufen:

```
name();
```

Hier ist eine Funktion die einen häufig verwendeten Link ausgibt

```
// output a back to top HTML link
function backToTop() {
  echo '
    <p><a href="#top">Back to top</a></p>
  ';
}
```

Um diese Funktion zu verwenden:

```
backToTop();
```

Jedesmal, wenn die Funktion aufgerufen wird, gibt sie einen Link aus, der zurück zum Anfang der Seite führt


#### Funktionsparameter

Um Variablen einer Funktion zu übergeben, geben Sie sie als Argumente (oder Parameter) an

Sie verweisen auf die Namen dieser Variablen zwischen den Klammern, wenn Sie die Funktion definieren

Sie verwenden dann denselben Variablennamen innerhalb der Funktionsdeklaration

```
function square($num) {
  echo $num * $num;
}

square(3); // === 9
square(5); // === 25
```

Um einen Wert von der Funktion zurück zu geben benutzen Sie das Schlüsselwort `return`:

```
function square($num) {
  return $num * $num;
}

$threeSquared = square(3); // === 9
$fiveSquared  = square(5); // === 25
```

Dies sind einfache Beispiele für die Erstellung und Nutzung von Funktionen

In der realen Welt werden Sie wahrscheinlich komplexere Funktionen nutzen

Sie können Funktionen verwenden, um einen Teil des Codes zu verschieben, den Sie in separate Dateien schreiben

Beispielsweise können Sie eine Funktion erstellen, die prüft, ob der aktuelle Benutzer angemeldet ist. Etwas wie dieses könnte am Anfang jeder Seite einer Website verwendet werden, um festzustellen, ob Inhalte für einen angemeldeten Benutzer oder ein Mitglied der Öffentlichkeit angezeigt werden

***Weitere Informationen:***

 - [http://www.brandonsavage.net/how-to-write-a-function-in-php/](http://www.brandonsavage.net/how-to-write-a-function-in-php/)
 - [http://webhole.net/2010/03/14/php-functions-tutorial/](http://webhole.net/2010/03/14/php-functions-tutorial/)
 - [http://www.tuxradar.com/practicalphp/4/15/0](http://www.tuxradar.com/practicalphp/4/15/0)

#### Variablen Scope

Bei der Verwendung von Funktionen sind keine Variablen, die ausserhalb der Funktion definiert sind, verfügbar

Umgekehrt ist eine innerhalb der Funktion angelegte Variable ausserhalb nicht vorhanden

Dies ist bekannt als Scope und ist sehr nützlich!

Es gibt einige Ausnahmen dazu; Wie bereits erwähnt, sind superglobal Variablen überall zugänglich (global)

 - [Variable Scope documentation](http://www.elated.com/articles/php-variable-scope-all-you-need-to-know/)


### Daten formatieren

In den meisten der bisher gesehenen Beispiele haben wir die Daten direkt aus der Datenbank auf die Seite ausgegeben:

```
echo $something;
```

Manchmal können Sie diese Informationen formatieren, bevor Sie sie auf der Seite ausgeben

Wir haben schon einige grundlegende Beispiele dafür gesehen:

Verknüpfen von Strings - bei der Ausgabe eines Namens haben wir Strings wie folgt kombiniert:

```
echo "<p>" . $firstname . " " . $surname . "</p>";
```

DDatumsfunktionen - zur Ausgabe des heutigen Datums:

```
echo date_format("d/m/y");
```

#### Gross-/Kleinschreibung ändern

Es gibt weitere Möglichkeiten, die wir verwenden könnten, um Textfolgen zu manipulieren:

Um die Gross-/Kleinschreibung eines Textstrings zu ändern, können wir `strtolower()` oder `strtoupper()` verwenden

```
$firstname = "Pete";
$surname = "Goodman";

echo "<p>" . strtolower($firstname) . " " . strtoupper($surname) . "</p>";

// <p>pete GOODMAN</p>
```

#### Zeichen beschränken

Um Text auf eine bestimmte Anzahl von Zeichen zu beschränken, können wir `substr()` verwenden:

```
$text = "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.";

// first param = string
// second param = start position
// third param = number of characters to output
echo "<p>" . substr($text, 0, 140) . "</p>";
```

(Könnte nützlich sein, wenn Sie beispielsweise eine begrenzte Zusammenfassung einer Überprüfung ausgeben möchten)


#### Zeichen ersetzen

Um einen Text mit einem anderen Text zu ersetzen, können Sie `str_replace()` verwenden

```
$original = "hello world";

// first param = replace
// second param = with
// third param = original string
$replaced = str_replace("world", "universe", $original);

echo $replaced; // hello universe
```

Es gibt noch viele Beispiele für String-Funktionen auf der PHP-Website:

 - [http://www.php.net/manual/en/ref.strings.php](http://www.php.net/manual/en/ref.strings.php)


#### Zahlen formatieren

Es gibt auch viele Funktionen, die wir verwenden können, um Zahlen zu manipulieren:

Sie können `round()`, `floor()` und `ceil()` verwenden, um eine Zahl mit einem Dezimalpunkt auf eine ganze Zahl auf- oder abzurunden

```
$lower = 3.254;
$upper = 3.836;

echo round($lower); // === 3
echo round($upper); // === 4
echo floor($lower); // === 3
echo floor($upper); // === 3
echo ceil($lower);  // === 4
echo ceil($upper);  // === 4
```
Könnte nützlich sein für die Berechnung einer durchschnittlichen Bewertung für ein Element, Website-Statistiken, etc


#### Zufallszahlen generieren

Sie können eine zufällige ganze Zahl mit `rand()` erzeugen

Mit `rand(1,10)` wird eine zufällige ganze Zahl zwischen 1 und 10 (einschliesslich) generiert

Könnte verwendet werden, um ein zufälliges Element aus einem Array anzuzeigen

```
$planets = array("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune");
$rand = rand(0, count($planets) - 1);
echo $planet[$rand];
```

Es gibt noch viele Beispiele für Nummernfunktionen auf der PHP-Website:

 - [http://www.php.net/manual/en/book.math.php](http://www.php.net/manual/en/book.math.php)


### Arrays sortieren

Die Beispiele, die wir früher gesehen haben, zeigen, wie wir einfache Variablen - Zahlen und Strings - manipulieren können

Wir können auch Arrays sortieren und filtern

```
$planets = array("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune");
```

Dies ist ein Standard-PHP-Array, wir wissen bereits, wie man auf eine einzelne Position zugreifen kann:

```
echo $planets[2]; // === "Earth"
```

Um einen zufälligen Eintrag aus einem Array auszuwählen, können wir `array_rand()` verwenden

```
$rand = array_rand($planets);
echo $planets[$rand];
```

`count($array)` gibt die Anzahl der Artikel im Array zurück

```
echo count($planets); // === 8
```

`shuffle($array)` wird das Array (zufällig) mischen

```
shuffle($planets);
print_r($planets);
```

`array_reverse($array)` wird ein Array umkehren

```
$reversedPlanets = array_reverse($planets);
print_r($reversedPlanets);
```

`array_unique()` wird alle Duplikate aus einem Array entfernen

Wir können in eine Array hinzufügen oder aus einem Array entfernen:

  - `array_pop()` um den letzten Wert abzurufen und zu entfernen
  - `array_shift()`, um einen Wert an den Anfang eines Arrays zu setzen
  - `array_push()`, um einen Wert ans Ende eines Arrays zu setzen
  - `array_unshift()` um den ersten Wert aus einem Array abzurufen und zu entfernen

Es gibt noch viele Beispiele für Array-Funktionen auf der PHP-Website:

 - [http://www.php.net/manual/en/ref.array.php](http://www.php.net/manual/en/ref.array.php)


### PHP oder MySQL benutzen, um Daten zu sortieren

Bei der Auswahl zwischen der Sortierung von Daten mit PHP oder MySQL, ist es effizienter, so viel wie möglich in der ursprünglichen SQL-Abfrage zu tun

Zum Beispiel könnten Sie `SELECT * FROM Fragen` ausführen, dann alle Ergebnisse in PHP durchlaufen, um zu entscheiden, ob die aktuelle Frage ausgegeben werden soll

Aber es ist effizienter, in der SQL-Abfrage zu filtern ...

... es sei denn, Sie haben vor die anderen Daten anderweitig wiederzuverwenden


### Dateien hochladen

#### Client-seitiger Code

Wir können HTML-Formulare verwenden, um Dateien auf den Server hochzuladen

Wir haben die Standardstruktur eines HTML-Formulars schon gesehen

Um ein Formular zum Hochladen von Daten zu aktivieren, fügen Sie ein zusätzliches Attribut hinzu:

```
<form method="post" action="" enctype="multipart/form-data">
```

Dann in dem Formular fügen wir ein neues `<input>` Element mit einem `type` Attribut von` file` hinzu

```
<input name="upload" id="upload" type="file" />
```

Das ist alles, was wir auf der Client-Seite tun müssen, um eine Datei hochzuladen

Der Rest der Arbeit, die zum Hochladen einer Datei erforderlich ist, erfolgt auf der Serverseite


#### Server-seitiger Code

Wir müssen identifizieren, wann eine Datei hochgeladen wurde

PHP stellt die hochgeladenen Datei-Daten in einer superglobalen Variable namens `$_FILES` bereit

Die hochgeladene Datei wird durch den Namen ihres HTML-Elements identifiziert

Im Falle der Form, die wir gerade gesehen haben, wird es als `$_FILES ['upload']` verfügbar sein

`$_FILES['upload']` wird ein Array mit fünf Schlüsselwerten sein:

  - `name` ist der ursprüngliche Dateiname
  - `type` gibt seinen Mime-Typ an
  - `tmp_name` zeigt den vollständigen Pfadnamen an, wo die temporäre Datei auf dem Server gespeichert ist
  - `Fehler` bedeutet Erfolg oder Misserfolg (0 = falsch, also keine Fehler)
  - `size` zeigt die Dateigrösse in Bytes an.

Diese Werte sind unter `$_FILES['upload']['name']` etc

So laden Sie eine Datei auf den Webserver hoch:

```
// set directory to upload to
$uploadTo = 'path/to/images/';

// get the file name of uploaded file
$filename = basename($_FILES['upload']['name']);

// set location to store uploaded file
$uploadedFile = $uploadTo . $filename;

// get the temporary file name
$tempFile = $_FILES['upload']['tmp_name'];

// move file to its new home
if (move_uploaded_file($tempFile, $uploadedFile)) {
  // file upload was successful
} else {
  // file upload was not successful
}
```

Seien Sie sich der Sicherheitsprobleme bewusst, wenn Sie Personen das Hochladen von Dateien auf Ihren Server erlauben!

***Weitere Informationen:***

 - [http://uk3.php.net/manual/en/features.file-upload.post-method.php](http://uk3.php.net/manual/en/features.file-upload.post-method.php)
 - [http://www.zymic.com/tutorials/php/creating-a-file-upload-form-with-php/](http://www.zymic.com/tutorials/php/creating-a-file-upload-form-with-php/)


### Bilder aus einer Datenbank anzeigen

Sie müssen keine Bilder in Ihrer Datenbank speichern, um Bilder in Ihrer Website anzuzeigen

Sie können auch nur den Namen einer Bilddatei speichern

Wir haben gerade gesehen, wie man eine Datei hochlädt

Beim Hochladen einer Datei können Sie den Dateinamen in der Datenbank speichern

Wenn Sie zum Beispiel Daten aus der Datenbank ausgeben, verwenden Sie das Dateiname-Feld als `src`-Attribut für ein Bild:

```
<img src="images/' . $row['filename'] . '" alt="' . $row['description'] . '" />
```

### E-Mails senden

Um eine E-Mail zu senden, können Sie PHPs `mail()` Funktion benutzen

```
mail('to', 'subject', 'message', 'headers');
```

Ein Beispiel:

```
// set up mail settings
$to       = "you@email.com";
$from     = "me@email.com";
$fromName = "Me";
$subject  = "Email subject";
$message  = "This is where you put your email content";

// set up technical bits needed to send mail
$headers = "From: ".$fromName." <" .$from. ">\r\n" .
    "Reply-To: ". $from . "\r\n" .
    "X-Mailer: PHP/" . phpversion();

// send mail!
if (mail($to, $subject, $message, $headers)) {
  // email sent successfully
} else {
  // there was a problem
}
```

Das funktioniert nicht immer - viele Server unterstützen keine E-Mails

Die `mail()` Funktion wird manchmal von Webserver Administratoren deaktiviert (aus gutem Grund)

Verwenden Sie es nicht exzessiv oder Sie werden in Schwierigkeiten mit Ihrem Web-Hoster bekommen

Ihre Nachricht kann als Spam identifiziert werden, da sie nicht von einem anerkannten E-Mail-Server stammt

Sie könnten eine Drittanbieter-Bibliothek verwenden, aber diese sind oft komplex einzurichten


### Suchen

Um ein einfaches Suchfeld / eine Seite hinzuzufügen, können Sie ein HTML-Formular verwenden

Identifizieren Sie die Spalten, die Sie suchen möchten

Verwenden Sie einen SQL-Befehl wie:

```
$query = "SELECT * FROM `answers` WHERE `answer` LIKE '%".$search_term."%'";
```

Dadurch wird eine Liste aller Elemente in der Datenbank zurückgegeben, die mit dem Abfrageparameter übereinstimmen


#### Aktive Suchanfrage anzeigen

Wir haben die `str_replace()` Funktion vorhin gesehen

Wir können sie benutzen, um den Begriff zu finden, der gesucht wurde, und ihn fett darstellen

```
// make searched term bold
$answer = str_replace($search_term, "<strong>" . $search_term . "</strong>", $row['answer']);
```


### Drittanbieter Bibliotheken

"Warum das Rad neu erfinden"

Sie benötigen möglicherweise eine bestimmte Funktionalität für Ihre Website

Oft ist jemand anderes auf das Problem gestossen, das Sie derzeit haben, hat es gelöst und hat seine Lösung frei und offen gelegt

Es gibt viele Drittanbieter-Scripts, Plug-Ins, Bibliotheken und Frameworks, die Sie verwenden können

Diese reichen in der Grösse von kleinen spezifischen Stücken von Funktionalität bis hin zu Blogs, Einkaufswagen und CMSs

Einige sind frei und Open Source, andere nur gegen Bezahlung verfügbar

Websites wie GitHub und Stack Overflow sind tolle Orte, um nach diesen Skripten zu suchen


## Sicherheit

Im Allgemeinen sind Besucher auf Ihrer Website nette Leute ...

... aber manche Leute sind nicht so nett.

Sie werden versuchen, Sicherheitsfehler in Ihrer Website zu finden und zu nutzen

  - Eingabewerte absichern
  - Schutz gegen SQL-Injektion
  - Passwörter schützen

Entfernen Sie vor der Verarbeitung der Informationen unerwünschte oder potenziell schädliche Inhalte

  - Content-Ausgabe an den Browser
  - Inhalt, der von einem Benutzer in ein Formular hinzugefügt wird
  - Parameter zum Erstellen von SQL-Abfragen
  - Inhalt der in einer Datenbank gespeichert wird


### Inhalte anzeigen

Bei der Anzeige von Inhalten aus einer Datenbank könnten wir unsere Sicherheit verbessern:

```
// get a list of all questions in the database
$query = "SELECT * FROM `questions`";
$result = $db->query($query);

// loop through data returned by database
while ($row = $result->fetch_assoc()) {

  // THIS IS THE POINT WHERE WE SHOULD ESCAPE OUTPUTS!
  $question = $row['question'];

  // output content to page
  echo '<li><strong>' . $question . '</strong></li>';
}
```

### Inhalte speichern

Bei der Eingabe von Inhalten in die Datenbank könnten wir unsere Sicherheit verbessern:

```
// THIS IS THE POINT WHERE WE SHOULD FILTER INPUTS!
$answer = $_POST['answer'];

// create SQL query to insert new answer
$query = "INSERT INTO `answers` (`answer`) VALUES ('" . $answer . "')";

// execute query
$result = $db->query($query);
```

### Inhalte escapen

Im Wesentlichen nimmt die Website die Eingabe von einem Benutzer ein, speichert sie in einer Datenbank und gibt sie dann zur Anzeige aus

Wenn wir den Inhalt nicht absichern, bevor wir ihn ausgeben:

  - Jemand, der HTML zu ihrem Inhalt hinzufügt, könnte das Layout unserer Seite beeinflussen
  - Jemand, der SQL, PHP oder JavaScript zu ihrem Inhalt hinzufügt, könnte viel bösartiger sein ...


#### Testfall

Die folgenden Beispiele verwenden einen einfachen Testfall

Wir werden versuchen, das folgende Stück JavaScript in ein Formular einzufügen:

```
<script>alert('hacked');</script>
```

Sie müssen verhindern, dass Leute in der Lage sind, diesen oder ähnlichen Code in ein Formular einzugeben und in einer Datenbank zu speichern

Wenn Sie diesen Inhalt nicht escapen, bevor Sie ihn anzeigen, wird das JavaScript ausgeführt und ein Warnmeldungsfeld erstellt

(Dieses JavaScript ist harmlos, aber wenn jemand JavaScript eingeben kann, kann man bspw. leicht `window.location.href` verwenden, um einen Benutzer auf eine andere Website umzuleiten)

Es gibt mehrere Möglichkeiten, Inhalte zu reinigen, bevor sie auf eine Seite ausgegeben werden

(Welches Sie wählen hängt oft davon ab, wie streng Sie es handhaben wollen)

 - `htmlspecialchars();`
 - `htmlentities();`
 - `strip_tags();`


#### htmlspecialchars();

konvertiert `' " & < >` in ihr HTML Equivalent

 - `'` = `&apos;`
 - `"` = `&quot;`
 - `&` = `&amp;`
 - `<` = `&lt;`
 - `>` = `&gt;`

Mit `htmlspecialchars();` macht man den Text sicher für die Ausgabe

```
$content = "<script>alert('hacked');</script>";

$escaped = htmlspecialchars($content);

echo $escaped;

// &lt;script&gt;alert('hacked');&lt;/script&gt;
```


#### htmlentities();

Konvertiert alle (anwendbaren) Zeichen in ihr HTML-Entity-Format

In diesem Beispiel ist die Ausgabe die gleiche wie im letzten Beispiel

Diese Funktion wird auch zusätzliche Zeichen umwandeln, wie z.B. Ã© in &eacute;

Mit `htmlentities();` macht man den Text sicher für die Ausgabe

```
$content = "<script>alert('hacked');</script>";

$escaped = htmlentities($content);

echo $escaped;

// &lt;script&gt;alert('hacked');&lt;/script&gt;
```


#### strip_tags();

Entfernt alle HTML-, JavaScript- und PHP-Tags

Diese Funktion validiert das HTML nicht, so dass teilweise oder defekte Tags dazu führen können, dass mehr Inhalt als erwartet entfernt wird

Mit `strip_tags();` macht man den Text sicher für die Ausgabe

```
$content = "<script>alert('hacked');</script>";

$escaped = strip_tags($content);

echo $escaped;

// alert('hacked');
```

*Zusammenfassend:*

Wir sollten alle Inhalte über eine dieser Funktionen verteilen, bevor wir sie ausgeben

Die Wahl der Funktion hängt davon ab, wie streng Sie es handhaben wollen


### Formulareingaben filtern

Sie können eine dieser Funktionen ausführen, bevor Sie die Formulareingabe verarbeiten, damit Sie den schädlichen Code nicht in Ihrer Datenbank speichern

Damit wird sichergestellt, dass kein bösartiger Code von unserer Website gespeichert oder ausgeführt wird

Betrachten Sie alle Daten ungültig, es sei denn, es wurde als gültig bewiesen

Wir müssen alle Benutzereingaben validieren und bereinigen, bevor wir mit diesen Daten etwas tun


### SQL Injection

Wenn Sie Benutzern erlauben, Werte einzugeben, die in einer SQL-Anweisung verwendet werden, benötigen wir auch einen Weg, um sicherzustellen, dass unsere SQL-Anweisungen geschützt werden können

SQL-Injektion ist nicht immer bösartig, es könnte zufällig sein:

```
$sql = "SELECT * FROM `users` WHERE `surname` = '$_GET['name']'";
```

Jemand gibt einen Wert mit einem Apostroph ein und verwandelt dieses SQL in:

```
$sql = "SELECT * FROM `users` WHERE `surname` = 'O'Connor'";
```

(Der extra Apostroph macht die Abfrage syntaktisch ungültig ...)

#### Was ist eine typische SQL Injection?

*Extra Apostrophe*

Aussagen, die immer wahr sind - z.B. `OR 1 = 1` ans Ende einer `WHERE` Abfrage anfügen

Siehe auch:

 - `' OR 1=1--`
 - `" OR 1=1--`
 - `OR 1=1--`
 - `' OR 'a'='a`
 - `" OR "a"="a`
 - `') OR ('a'='a`

Denken Sie an ein einfaches Login Script:

```
SELECT `username`, `password` FROM `users` WHERE `username` = '$_POST['u']' AND `password` = '$_POST['p']';
```

Wenn wir diese SQL-Abfrage ausführen, wenn > 0 Datensätze zurückgegeben werden, gehen wir davon aus, dass die Benutzeranmeldeinformationen gültig sind und melden den Benutzer an

```
SELECT `username`, `password` FROM `users` WHERE `username` = 'xx' AND `password` = '' OR 1 = 1;
```

1 = 1 ist immer wahr, folglich werden > 0 Einträge zurückgegeben

Wir brauchen einen Weg, um alle Benutzereingaben zu filtern (oder zu bereinigen), so dass wir nicht in diese Probleme laufen

Um SQL-Injektion zu vermeiden, können wir `mysqli_real_escape_string()` an allen Benutzereingaben verwenden

```
$escaped_text = mysqli_real_escape_string($db, $text);
```

Diese Funktion erwartet zwei Parameter:

 - `$db` = Die mysqli Datenbankverbindungsvariable (Sie müssen breits mit der MySQL Datenbank verbunden sein)
 - `$text` = Text zum escapen

Beispiel:

```
$username = mysqli_real_escape_string($db, $_POST['username']);
```

Dies sollte mit JEDEM Benutzereingabefeld verwendet werden


### Prepared Statements

Prepared statements sind ein alternativer Weg SQL Abfragen zu schreiben

Sie haben eine etwas andere Syntax zu den SQL-Abfragen, die wir bisher gesehen haben

Sie sind eine sicherere Art, SQL-Abfragen zu schreiben, da sie die Abfragestruktur vollständig von den Abfrageparametern trennen

Bei der Deklaration von Abfrageparametern verwenden Sie zunächst ein Fragezeichen -?- in Ihrer Abfrage anstelle einer Variablen

```
$query = $db->prepare("INSERT INTO `users` (`username`, `password`, `name`) VALUES (?, ?, ?)")
```

Dann binden Sie die Variablen, die Sie in Ihrer Abfrage verwenden möchten:

```
$query->bind_param('sss', $lorem, $ipsum, $dolor);
$query->execute();
```

Der erste Parameter sollte den Typ jeder Variablen identifizieren:

 - `s` = String
 - `i` = Integer - ganze Zahl
 - `d` = Double/Float - Zahlen mit Dezimalpunkt

Anstatt Parameter mit der Hauptabfrageanweisung zu mischen, werden die Parameter separat weitergegeben, bevor Sie die Datenbank abfragen

Die Reihenfolge der Parameter sollte mit der Reihenfolge übereinstimmen, die Sie verwenden möchten

Vorbereitete Aussagen können mit den Filterfunktionen gemischt werden, die wir früher für zusätzliche Sicherheit gesehen haben


***Weitere Informationen:***

 - [Documentation](http://php.net/manual/en/mysqli.quickstart.prepared-statements.php)
 - [bind_param documentation](http://uk3.php.net/manual/en/mysqli-stmt.bind-param.php)


#### Klassisches SQL SELECT Statement

```
$sql = 'SELECT `id`, `username` FROM `users` WHERE `username` = "'.$username.'" AND `password` = "'.$password.'"';

$result = $db->query($sql);
```


#### Prepared SQL SELECT Statement

```
// prepare the query
if ($query = $db->prepare("SELECT `id`, `username` FROM `users` WHERE `username` = ? AND `password` = ?")) {

  // set the parameters to substitute for the ? in the query above
  $query->bind_param('ss', $_POST['username'], $_POST['password']);

  // run the query
  $query->execute();

  // set variable names for each field/attribute you're returning from the query
  $query->bind_result($id, $username);

  // loop through query results
  while ($query->fetch()) {
    echo '
      <p>User: '.$id.' - '.$username.'</p>
    ';
  }

// check for any db query errors
} else {
  echo "SQL Error: " . $db->error;
}
```


#### Klassisches SQL INSERT Statement

```
$sql = 'INSERT INTO `users` (`username`,`password`, `name`) VALUES ("'.$username.'","'.$password.'","'.$name.'")';

$result = $db->query($sql);
```


#### Prepared SQL INSERT Statement...

```
// prepare the query
if ($query = $db->prepare("INSERT INTO `users` (`username`, `password`, `name`) VALUES (?, ?, ?)")) {

  // set the parameters to substitute for the ? in the query above
  $query->bind_param('sss', $_POST['username'], $_POST['password'], $_POST['name']);

  // run the query
  $query->execute();

  // check the query was successful
  if ($query->affected_rows > 0) {
    echo "Query executed: affected rows: ".$query->affected_rows;
  }

// check for any db query errors
} else {
  echo "SQL Error: " . $db->error;
}
```


### Passwörter speichern

Speichern Sie keine Passwörter als Plaintext!

 - Passwörter sind sensible Informationen
 - Wenn jemand Zugriff auf Ihre Datenbank erhält, erhalten sie Zugriff auf alle Passwörter, die Sie gespeichert haben
 - Beachten Sie, dass eine Menge von Internet-Nutzer, egal wie oft Sie ihnen sagen, es nicht zu tun, sie das gleiche Passwort über mehrere Websites verwenden
 - Wir müssen einen Weg finden, um die Passwörter sicher zu speichern, so dass jemand Fremdes nichts mit den Daten anfangen kann

Wir müssen Passwörter verschlüsseln

#### Hashing

Die häufigste Methode zur Verschlüsselung von Passwörtern ist als Hashing bekannt

Hashing wandelt Passwörter in lange zufällige Zeichenfolgen

Zum Beispiel ist das Wort 'Passwort' durch den `SHA-1` Hash-Algorithmus '5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8`

Es ist ein Einweg-Prozess (einfach zu verschlüsseln, nicht zu entschlüsseln)

Dies bedeutet, dass es schwierig ist, den ursprünglichen Text aus einem Hash-Passwort wiederherzustellen

Sie können ganz einfach einen Hash für jede Zeichenfolge generieren

Es ist höchst unwahrscheinlich, dass zwei Zeichenfolgen einen identischen Hash erzeugen werden

Wenn jemand auf Ihre Datenbank zugreifen und Ihre Liste der Passwort Hashes stehlen kann, können sie mit den gestohlenen Informationen nichts anfangen.


#### Hashing Algorithmen

Es gibt viele verschiedene Hash-Algorithmen zur Verfügung

Diese nehmen alle einen String und wandeln ihn in einen Hash von einer gewissen Länge (und Komplexität)

Sie führen die gleiche Aufgabe auf unterschiedliche Weise, mit verschiedenen Algorithmen aus, um den Hash zu berechnen

Um einen Hash mit PHP zu erstellen, können wir eine der vielen verschiedenen Hashing-Funktionen wählen

```
$string = 'password';
echo "Original string: ". $string;
echo "MD5 hash: ". md5($string);
echo "SHA-1 hash: ". sha1($string);
```

Mit diesen Algorithmen wird jedes mit einem String generierte Passwort immer das gleiche Ergebnis erzeugen

`sha1("password")` wird immer `5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8` sein

So können wir einen Hash-Wert und nicht das eigentliche Passwort speichern


#### Ein Login Szenario

  - Speichern Sie den Hash von einem Passwort, anstatt das Passwort selbst
  - Wenn jemand versucht, sich einzuloggen, verschlüsseln Sie das übermittelte Passwort mit der gleichen Methode
  - Überprüfen Sie dies gegen die gespeicherte verschlüsselte Version
  - (anstatt das vorgelegte Klartext-Passwort mit dem gespeicherten Klartext-Passwort zu vergleichen)

#### Wie man einen Hash in einer PHP / MySQL-Website erzeugt und speichert

```
// Hash the password
$passwordHash = sha1($_POST['password']);

// Prepare SQL statement
$sql = 'INSERT INTO user (username, password) VALUES ("'.$_POST['username'].'", "'.$passwordHash.'")';

// Insert user
$result = $db->query($sql);
```

#### So überprüfen Sie einen Hash bei der Anmeldung auf Ihrer PHP / MySQL-Website

```
$passwordHash = sha1($_POST['password']);

$sql = 'SELECT username FROM user WHERE username = "'.$_POST['username'].'" AND password = "'.$passwordHash.'"';

$result = $db->query($sql);

if ($result->numRows() < 1) {
  // user not recognised
} else {
  // user has logged in successfully
}
```

### Salts

Diese Verschlüsselungsstufe ist ein Start, aber es ist nicht sicher genug für die Passwortspeicherung

Wenn jemand Zugang zu Ihrer Datenbank erhält, können sie Ihre Passwort Hashes sehen

Eine gängige Technik, die verwendet wird, um zu versuchen, die ursprünglichen Klartext-Passwörter aus ihren Hashes zu entschlüsseln, heisst Cracking oder "Brute-Forcing"

Jemand, der Zugriff auf Ihre Hash-Passwörter hat, kann eigene Hashes für gemeinsame Passwörter erzeugen

Die erzeugten Hashes werden mit denen in Ihrer Datenbank verglichen

Alle Übereinstimmungen zeigen das Passwort für den jeweiligen Benutzer an

Moderne Computer können MD5 und SHA-1 Hashes sehr schnell erzeugen - Tausende jede Sekunde

Hashes können für jedes Wort in einem ganzen Wörterbuch generiert werden

Sie können vorschlagen, dass Benutzer starke Passwörter einrichten, die ein angemessenes Mass an Schutz gegen solche Angriffe bieten würden ... aber Sie können nicht garantieren, dass Ihre Benutzer das tatsächlich tun werden!


#### Passwort Hashing mit Salt

Bevor wir einen Hash erzeugen, sollten wir dem Passwort ein "Salt" hinzufügen

Ein Salz ist eine zufällige Zeichenfolge einer Satzlänge

Jedes Mal, wenn wir einen Benutzer hinzufügen, sollten wir für sie ein einzigartiges Salt erzeugen

Wir verwenden dann sowohl das Salt als auch das Passwort, um ein einzigartiges Passwort zu erstellen

Dies bietet ein zusätzliches Mass an Sicherheit und schützt vor Brute-Force-Angriffen

 - [This article explains how to use them](http://phpsec.org/articles/2005/password-hashing.html)


### Datei Uploads

Bisher haben wir ein grundlegendes Beispiel für ein Datei-Upload-Skript gesehen

Es läuft derzeit keine Form der Validierung der Datei, die hochgeladen wird

Das könnte verbessert werden!

Wenn es Benutzern erlaubt, Dateien hochzuladen, gibt es ein paar Vorsichtsmassnahmen, die Sie ergreifen könnten:

  - Begrenzt die erlaubten Dateitypen
  - Begrenzt die zulässige Dateigrösse

Andernfalls, wenn ein bösartiger Benutzer weiss, dass Sie einen PHP-Server haben und Sie erlauben ihnen, eine PHP-Datei hochzuladen, können sie ein Script schreiben und hochladen, das ihnen den Zugriff auf Ihren Server ermöglicht

```
// Set allowed file types
$allowedMimeTypes = array(
  "image/jpg", "image/jpeg", "image/pjpeg", "image/JPG",
  "image/X-PNG", "image/PNG", "image/png", "image/x-png"
);

// Check whether to allow this type of file
if (in_array($_FILES['upload']['type'], $allowedMimeTypes)) {
  // file type is allowed
} else {
  // invalid file type, echo error
}
```

Dies ist nur eine grundlegende Form der Datei-Erkennung, und kann leicht überlistet werden, aber es zeigt die Notwendigkeit, Sicherheit zu Datei-Uploads hinzufügen


### Datei Includes

Wenn Sie jemals eine übergebene Variable als Teil eines Dateinamens oder Pfades verwenden, verwenden Sie zuerst `basepath()`, um sie zu filtern

```
$filePath = basepath("/path/to/file.php"); // file.php
```

Dies bedeutet, dass böswillige Benutzer eine Remote-Datei nicht aufrufen können:

```
$fileInclude = basepath("http://malicious.url/file.php");
// file.php
```


### Verschiedene Tips

Unterschieden Sie nicht zwischen ungültigen Benutzernamen und Passwörtern in Fehlermeldungen - Wenn jemand versucht, bösartig auf ein Konto zuzugreifen, sollten Sie ihn nicht wissen lassen, dass er einen gültigen Benutzernamen identifiziert haben, aber das Passwort ist falsch

Begrenzen Sie die Anzahl der Zeiten, in denen sich jemand falsch anmelden kann - Nach ein paar Versuchen von der gleichen IP-Adresse, sollten Sie es zumindest zeitweilig blockieren

Deaktivieren Sie die PHP-Fehlerberichterstattung für eine Live-Site - es ist nützlich für das Debugging während der Entwicklung, aber Sie möchten nicht, dass die Endbenutzer diese Informationen sehen

***Weitere Informationen:***

 - [http://phpsecurity.org/](http://phpsecurity.org/)
 - [http://www.addedbytes.com/writing-secure-php/](http://www.addedbytes.com/writing-secure-php/)
 - [http://www.sk89q.com/2009/08/definitive-php-security-checklist/](http://www.sk89q.com/2009/08/definitive-php-security-checklist/)
 - [http://code.google.com/p/doctype-mirror/wiki/ArticleIntroductionToXSS](http://code.google.com/p/doctype-mirror/wiki/ArticleIntroductionToXSS)
 - [http://www.dvwa.co.uk/](http://www.dvwa.co.uk/)
 - [http://phpsecurity.org/ch02.pdf](http://phpsecurity.org/ch02.pdf)
 - [http://phpsecurity.org/ch04.pdf](http://phpsecurity.org/ch04.pdf)
 - [http://shiflett.org/articles/sql-injection](http://shiflett.org/articles/sql-injection)
 - [http://www.nyphp.org/phundamentals/5_Storing-Data-Submitted-Form-Displaying-Database](http://www.nyphp.org/phundamentals/5_Storing-Data-Submitted-Form-Displaying-Database)
 - [http://unixwiz.net/techtips/sql-injection.html](http://unixwiz.net/techtips/sql-injection.html)
 - [http://shiflett.org/articles/the-truth-about-sessions](http://shiflett.org/articles/the-truth-about-sessions)
 - [http://shiflett.org/articles/storing-sessions-in-a-database](http://shiflett.org/articles/storing-sessions-in-a-database)
 - [http://shiflett.org/articles/file-uploads](http://shiflett.org/articles/file-uploads)


## XML und JSON

Wir haben gesehen, wie einfach es war, Dateien beim Erstellen einer HTML-Seite zu importieren, mit den PHP-Funktionen `include` und` require`

Wir haben das Beispiel für eine generische Kopf- und Fusszeile für eine Website verwendet

Wir können dies auch für repetitive Inhalte verwenden, Informationen, die Sie nur einmal speichern möchten

### Datei Includes - HTML

Nehmen wir an, wir erstellen ein Formular, in dem wir eine Liste von Ländern als ausgewählte Dropdown-Liste importieren möchten

Wenn es eine statische HTML-Seite wäre:

```
<html>
...
<form>
  <select name="country" id="country">
    <option>Afghanistan</option>
    <option>Albania</option>
    ...
    <option>Zimbabwe</option>
  </select>
</form>
...
</html>
```

Wir könnten nur eine Datei mit dem HTML an der entsprechenden Stelle einbinden:

```
<html>
...
<form>
  <select name="country" id="country">
    <?php include "countries.html"; ?>
  </select>
</form>
...
</html>
```

Dies ist eine Möglichkeit, Informationen zu speichern, als fertiges HTML

Aber es gibt einige Probleme:

  - Es ist keine echte Trennung der Daten von der Anzeige
  - Sie können diese Informationen nicht auf andere Weise wiederverwenden
  - (Jeder Ländername wird von einem `<option>`-Element umgeben, also kann es nicht anders verwendet werden)
  - Es gibt effizientere Möglichkeiten, dies zu tun - wir könnten PHP verwenden, um es dynamisch zu verändern


Betrachtet man die Struktur der ursprünglichen HTML Datei, gibt es eine neue Zeile für jedes Datenelement

Auf jeder Zeile gibt es den Landnamen mit einem `<option>` Element, das es umgibt

Wenn wir nur eine Liste von Ländernamen hätten, könnten wir diese programmgesteuert mit PHP neu erstellen

Nun, anstatt nur die Datei in die Seite einzufügen, müssen wir sie mit PHP lesen und verarbeiten

Um die Datei zu lesen, verwenden wir die eingebauten PHP-Funktionen `file()` und `file_get_contents()`

```
<html>
...
<form>
  <select name="country" id="country">
    <?php
      $countries = file("countries.txt");
      foreach ($countries as $country) {
        echo "<option>" . $country . "</option>";
      }
    ?>
  </select>
</form>
...
</html>
```

Wir verwenden jetzt "rohe" Daten, die anderswo in unterschiedlichen Kontexten verwendet werden könnten

Wir sind nicht darauf beschränkt, dies nur aus einer lokalen Datei auf unserem Server zu laden

Wir könnten `file()` und `file_get_contents()` verwenden, um Daten von jeder URL abzurufen*


### file() und file_get_contents()

Es gibt einen Unterschied zwischen diesen beiden Funktionen.

Welches Sie verwenden, hängt davon ab, was Sie tun müssen:


#### file()

Liest den Inhalt einer Datei und setzt jede neue Zeile in ein Array

Nützlich beim Lesen im Inhalt einer Datei oder Webseite mit aufgelisteten Inhalten

(Wir sind jetzt alle Array-Experten!)


#### file_get_contents()

Liest den Inhalt einer Datei und setzt das alles in einen String

Nützlich beim Lesen des Inhalts einer Datei oder Web-Seite mit Prosa, Code (oder etwas, das nicht aufgelistetem Inhalt entspricht)


#### Sicherheit

(Erinnern Sie sich an das Sternchen?)

Wir können `file()` oder `file_get_contents()` auf vielen Servern nicht verwenden, um auf entfernte Dateien zuzugreifen

(Sie funktionieren gut für lokale Dateien)

Dies liegt an Sicherheitsfragen - "Code Injection Vulnerabilities"

Es gibt eine alternative Möglichkeit, Remote-Dateien von anderen Servern zu importieren, um diese Sicherheitsbeschränkung zu umgehen

Setzen Sie dies in einer separaten Datei (z.B. 'curl.php'), verwenden Sie require_once am Anfang der Datei, wenn Sie es verwenden müssen

```
function file_get_contents_curl($url) {
  $ch = curl_init();
  curl_setopt($ch, CURLOPT_URL, $url);
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
  $contents = curl_exec($ch);
  curl_close($ch);
  if ($contents) {
    return $contents;
  } else {
    return false;
  }
}

function file_curl($url) {
  return split("\n", file_get_contents_curl($url));
}
```
Wir verwenden jetzt "rohe" Daten, die in anderen Kontexten verwendet werden könnten

Wir könnten die Daten auch vor der Ausgabe manipulieren

PHP hat viele verschiedene Funktionen um Daten zu manipulieren oder zu sortieren


### Strukturierte Daten

Die Informationen, die wir gerade gesehen haben, sind nicht strukturiert

Diese Methode eignet sich gut für einfache Einzelwert-Informationen, nicht so gut für komplexe Daten

Wir haben gesehen, wie man Arrays benutzt, um strukturierte Informationen zu manipulieren oder zu durchzuschleifen

Was wir brauchen, ist eine Möglichkeit, komplexe Informationen zu speichern, damit wir sie in Arrays verwandeln können

Es gibt ein paar Optionen:

 - CSV
 - XML
 - JSON


### CSV

Komma-getrennte Werte sind eine weitere Möglichkeit, Informationen zu speichern, oft als statische Textdateien

Verwendet eine ähnliche Speichertechnik wie das letzte Beispiel, aber dieses Mal werden verschiedene Datenelemente mit Kommas (oder einem anderen vereinbarten Trennzeichen wie einem Tab) getrennt,

```
England, Europe, English
Switzerland, Europe, German Italian and French
Brazil, South America, Portuguese
```

Diese Informationen können dann verarbeitet werden:

```
<?php
// get the country csv data as an array (one country per line)
$countries = file("countries.csv");

// loop through the array, one country at a time
foreach ($countries as $country) {

  // turn each country string into an array of separate values, split on the comma
  $countryData = explode(",", $country, 4);

  // output country data!
  echo "
    <p>
      Country: " . $countryData[0] . ",
      Location: ".$countryData[1] . ",
      Languages: " . $countryData[3] . "
    </p>
  ";
}
?>
```

Wir haben jetzt einen Weg, um mehrere Stücke von Daten für jeden Artikel zu speichern

Dieses System ist weit verbreitet (z.B. können Excel-Dateien als .csv importiert / exportiert werden)

Immer noch nicht viel Struktur - unter der Annahme "flacher" Informationen, eine Zeile für jeden Artikel

Wir haben Informationen in ein Array geschaltet, damit wir auf die Daten zugreifen können ...

... aber jeder Wert im Array wird durch die Zahl indiziert, je nachdem, wo er in der Zeile auftritt

Wir wissen eigentlich nicht, was diese Daten repräsentieren

Wir setzen auf Standardformatierung. Was wäre, wenn es einen zusätzlichen Tab oder Komma in einer Reihe gibt?

Bessere Systeme existieren für die Speicherung komplexer Daten


### XML

_eXtensible Markup Language_

"data interchange format"

Ähnlich wie bei HTML, indem es Elemente und Attribute verwendet, um Informationen zu umgeben

Es ist ein offener Standard, der vom W3C definiert ist

Das ist wichtig, es bedeutet, dass jeder einverstanden ist, wie man es benutzt

Man sollte erwarten können, dass XML-Daten von einer externen Quelle diese Regeln befolgen

(In der Praxis ist das leider nicht immer so)

Die Syntaxregeln sind einfach und einfach zu befolgen

Es ist selbstdokumentierend, die Elementnamen beschreiben den Inhalt

Es erlaubt uns, komplexe Informationen zu speichern

Es erlaubt zwei Systeme, die in verschiedenen Technologien geschrieben sind, Daten auszutauschen


#### XML Syntax Regeln

Die meisten Tags müssen übereinstimmende Öffnungs- und Schluss-Tags haben

```
<tag>O Rose thou art sick.</tag>
<selfclosing lorem="ipsum" />
```

Tags sollten ordentlich verschachtelt sein

```
<tag>O <another>Rose</another> thou art sick.</tag>
```

Tags sollten immer in Kleinbuchstaben geschrieben werden

```
<tag>O Rose thou art sick.</tag>
```


#### Nebebei: XML, HTML and XHTML

HTML sieht aus wie XML ...

Aber HTML ist kein XML Format:

 - Tags müssen nicht geschlossen werden
 - Gross-/Kleinschreibung bei öffnenden und schliessenden Tags

XHTML war der Versuch die XML Regeln auf HTML anzuwenden

Mit HTML5 können Sie wählen, ob Sie XML benutzen wollen oder nicht


#### XML mit PHP benutzen

Wie bei den Plaintext- und CSV-Beispielen vorhin, können wir PHP auch verwenden, um XML-Dateien zu analysieren

Wir können eine XML-Datei in PHP mit der Funktion `simplexml_load_file()` laden


```
// load the XML file into a variable
$countries = simplexml_load_file("countries.xml");

// loop through the country data array
foreach ($countries as $country) {
  echo "
    <p>
    Country " . $country->id . ": " .
    $country->names->english . "
    (Local name: " . $country->names->local . ")
    </p>
  ";
}
```

Es gibt einen wichtigen Unterschied mit der Syntax für den Zugriff auf die Daten, die wir aus einer XML-Datei geladen haben

Das XML wird als Objekt und nicht als assoziatives Array geladen

Objekte in PHP gehen über den Rahmen dieses Dokuments hinaus, aber in dieser Situation verwenden wir sie in ähnlicher Weise wie ein Array

Der entscheidende Unterschied ist, wie wir auf die Daten zugreifen

Array Syntax:

```
$array['property'] // == value;
```

Object Syntax:

```
$object->property // == value;
```

Um z.B. den Namen der englischen Sprachen zu wählen, müssen wir folgendes schreiben:

```
$country->names->english
```

Die entsprechende Array Syntax lautet:

```
$country['names']['english']
```

Es gibt eine riesige Anzahl von Standards mit der Syntax von XML

Jeder von ihnen hat eine vereinbarte Liste von Elementen und Strukturen

Einige Beispiele:

  - SVG für Vektorbilddaten
  - KML für Kartendaten
  - RSS zur Syndizierung von Webinhalten
  - epub für eBooks
  - (etc...)


### JSON

JSON wird aus ähnlichen Gründen wie XML verwendet - um komplexe Informationen zwischen Systemen zu teilen

Es verwendet JavaScript-Syntax (im Gegensatz zur XML-Syntax), um Daten zu speichern

JSON hat einen grossen Vorteil gegenüber XML - es ist (meist) weniger dicht (es erfordert weniger Code), um Daten zu beschreiben

Das ist wichtig: Beim Teilen von riesigen Datenmengen über ein Netzwerk wollen Sie, dass es effizient ist

Je kleiner die Dateigrösse (je weniger Zeichen) desto besser

Für Benutzer der Daten ist es oft nicht besonders wichtig, ob es im XML- oder JSON-Format gespeichert ist


#### JSON mit PHP benutzen

Wie beim XML-Beispiel können wir PHP verwenden, um JSON-Dateien zu analysieren

Wir laden eine JSON-Datei in PHP mit `file_get_contents()`, dann wandeln wir es in ein PHP-Array mit der `json_decode()` Funktion

```
// load the JSON file into a variable as a string
$json = file_get_contents("countries.json");

// turn the string into an array
$countryData = json_decode($json, true);

// loop through the country data array
foreach ($countryData["countries"] as $country) {
  echo "
  <p>
    Country " . $country["id"] . ": ".
    $country["names"]["english"] . "
    (Local name: " . $country["names"]["local"] . ")
  </p>";
}
```


### Warum sind XML und JSON wichtig

Nützliche Möglichkeit, komplexe Daten zu speichern (oder zu repräsentieren)

Nützliche Möglichkeit für verschiedene Dienste zum Austausch von Daten

Wir können die Daten mit PHP lesen und manipulieren


### Statische Dateien und generierte Inhalte

Sie müssen nicht unbedingt Daten in statischen Dateien speichern

Um die Daten aktuell zu halten, müssen Sie die Dateien manuell aktualisieren

Bedeutet auch, dass man Zugriff auf den Webserver hat und die technischen Fähigkeiten, um dies zu tun

Sie können XML / JSON erzeugen, um Daten darzustellen, die angefordert wurden

Viele Webseiten bieten jetzt XML / JSON-Feeds an


### Daten-Feeds und APIs

Anstatt Daten selbst zu speichern, können Sie Drittanbieterdienste verwenden, um Ihre Daten zu speichern und zu verwalten

_Warum Fotos speichern, wenn Sie flickr verwenden können, warum speichern Sie kurze Stücke von Daten, wenn Sie twitter verwenden können_

Diese Unternehmen geben keinen direkten Zugang zu ihren Datenbanken für jedermann

Sie bieten alternative Möglichkeiten, auf ihre Informationen zuzugreifen - Daten-Feeds und APIs

Daten-Feeds erlauben uns generell den Zugriff auf Daten, meist im XML / JSON-Format

APIs sind in der Regel komplexer, da sie uns oft auch erlauben, Daten zu manipulieren, so können wir Inhalte aktualisieren, ohne die Website selbst zu besuchen

Wir könnten erwägen, Drittanbieterdienste zu verwenden, um eine lokale Datenbank zu ersetzen oder um ergänzende Informationen über ein ausgewähltes Element von unserer Website zu erhalten