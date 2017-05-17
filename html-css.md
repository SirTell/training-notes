# HTML & CSS notes

Ein paar Notizen vorbereitet beim Schreiben von Schulungen ...


## Das world-wide Web

Das Internet (als eine Sammlung von vernetzten Computern) existierte seit Jahrzehnten vor der Erstellung des weltweiten Internets.

Die Methoden der Kommunikation zwischen den Computern war nicht so einfach (f�r die durchschnittliche Person), wie es heute ist.

Im Jahr 1990 vereint Tim Berners-Lee, ein britischer Ingenieur, der am CERN arbeitet (Europ�ische Organisation f�r Kernforschung, in der Schweiz) mehrere wichtige Kommunikationsprotokolle, die gemeinsam als "World Wide Web" bekannt sind.

> "Ein Web von Hypertext-Dokumenten, die von Browsern mit einer Client-Server-Architektur betrachtet werden sollen."


### Komponenten des World Wide Web

Die Schl�sselkomponenten des 'World Wide Web'

 - HTML - eine Markup-Sprache, die verwendet wird, um Informationen Struktur zu geben
 - URLs - wird verwendet, um Dokumente eindeutig zu identifizieren
 - Hyperlinks (Hypertext) - um zwischen Dokumenten zu wechseln
 - Web-Browser - eine einfache grafische Benutzeroberfl�che (GUI), um diese Dokumente anzuzeigen
 - Web-Server - eine M�glichkeit, angeforderte Dokumente zur Verf�gung zu stellen

Diese Technologien haben unseren Konsum von Informationen revolutioniert!


### Das World-Wide Web Consortium (W3C)

Eine Organisation, die 1994 von Tim Berners-Lee gegr�ndet wurde.

Sie ist verantwortlich f�r die Entwicklung von "nicht-propriet�ren, interoperablen Technologien" f�r das World Wide Web.

Sie versucht, das Internet universell zug�nglich zu machen, unabh�ngig von der F�higkeit, Sprache oder Kultur.

Sie tut dies durch die Schaffung von Standards f�r Web-Technologien, wie HTML, CSS und XML.


### Web-Browser

Viele verschiedene Optionen

In diesen Tagen sind sie alle ziemlich �hnlich, und konkurrieren durch das Hinzuf�gen neuer Features

Die meisten Browser aktualisieren sich oft

Das war nicht immer so - *Internet Explorer 6 ...*


### Browsertechnologien

3 Hauptsprachen:

  - Inhalt - HTML
  - Styling - CSS
  - Interaktion - JavaScript
  

### Warum Sie lernen sollten, Code von Hand zu schreiben

  - Gewinnen Sie die vollst�ndige Kontrolle �ber Ihre Website
  - Verhindern Sie, dass Ihre Website eine "Black Box" ist, die einfach nur funktioniert
  - Mit ein bisschen �bung ist es der schnellste Weg, um Dinge zu machen
  - Es ist einfacher zu debuggen, wenn etwas nicht funktioniert
  - Einfache, schnelle Fixes kann man von �berall zu machen


## HTML

Beschreibt die Struktur des Inhalts - verwendet, um Struktur zu Informationen zu geben

Es ist eine universelle Sprache - vorausgesetzt, Sie haben einen Web-Browser, der in der Lage ist, HTML zu verstehen, dann k�nnen Sie jedes Betriebssystem oder Ger�t verwenden, um es darzustellen.


### Struktur mit Code eingeben

Wir "beschreiben" ein Dokument, um ihm Struktur zu geben, indem wir die Bedeutung seiner Teile beschreiben

HTML ist eine Art "Beschreibungs"-Sprache


### Wie w�rden wir ein Buch beschreiben?

Nehmen Sie das folgende Beispiel eines Buches:

> "Die Ananas: K�nig der Fr�chte" von Francesca Beauman. Ver�ffentlicht von Chatto & Windus im Jahr 2005.

Oder

> Im Jahr 2005 schrieb Francesca Beauman "The Pineapple: King of Fruits" und ver�ffentlichte mit Chatto & Windus.

Menschen k�nnen diese Information verstehen, aber f�r einen Computer, muss man sie in eine formale Struktur bringen:

  - * Titel *: Die Ananas: K�nig der Fr�chte
  - * Autor *: Francesca Beauman
  - * Datum *: 2005
  - * Herausgeber *: Chatto & Windus
  - * Beschreibung *: Diese bezaubernde, saftige Geschichte


In einer Mock-Markup-Sprache wird dies:

```
<book>
    <title>Die Ananas: K�nig der Fr�chte</title>
    <author>Francesca Beauman</author>
    <date>2005</date>
    <publisher>Chatto & Windus</publisher>
    <description>Diese bezaubernde, saftige Geschichte</description>
</book>
```

### Hyper-Text Markup Language (HTML)

HTML ist eine Sammlung von einfachen `<tags>`

Sie m�ssen nur ein paar wissen, um loszulegen:

 - `<h1>`Titel`</h1>` (es gibt sechs Levels an Titeln, von `<h1>` bis `<h6>`)
 - `<p>`Abschnitte`</p>`
 - `<em>`Hervorhebungen`</em>`
 - `<strong>`Wichtige Informationen`</strong>`
 - Bilder: `<img src="katze.jpg" alt="Meine Katze">`
 - `<a href="http://google.com">Links</a>`


### HTML Regeln

Es gibt ein paar einfache Regeln:


#### �ffnen und Schliessen von Tags

Tags verpacken den Inhalt, den sie beschreiben:

```
<tag>Inhalt</tag>
```

***FALSCH***

```
<p>In Xanadu hat Kubla Khan
<p>Ein stattliches Vergn�gungs-Dom-Dekret
```

***FALSCH***

```
<p>In Xanadu hat Kubla Khan</div>
```

***RICHTIG***

```
<p>In Xanadu hat Kubla Khan</p>
```

Einige Tags sind selbstschliessend, weil sie sich nicht um den Inhalt wickeln:

```
<img src="bild.jpg" alt="Bild-Beschreibung, falls Bilder im Browser nicht dargestellt werden" title="Bild-Beschreibung als Tooltip"/>
```


#### Tags verschachteln

Tags sollten richtig verschachtelt sein

***FALSCH***

```
<p>In <strong>Xanadu hat Kubla Khan</p>
```

***FALSCH***

```
<p>In <strong>Xanadu</p> hat Kubla Khan</strong>
```

***RICHTIG***

```
<p>In <strong>Xanadu</strong> hat Kubla Khan</p>
```


#### Gross-/Kleinschreibung

Tags sollten die gleiche Schreibweise haben (am Besten nur Kleinbuchstaben verwenden)

Beachten Sie, dass dies keine strenge Regel ist, wie die vorherigen zwei, jedoch sollte sie immer eingehalten werden.

***FALSCH***

```
<STRONG>In Xanadu hat Kubla Khan</strong>
```

***FALSCH***

```
<STRONG>In Xanadu hat Kubla Khan</STRONG>
```

***RICHTIG***

```
<strong>In Xanadu hat Kubla Khan</strong>
```


### Attribute

Zus�tzliche Informationen f�r einen Tag k�nnen mit Attributen im Er�ffnungs-Tag angegeben werden

```
<a href="http://google.com">Mit Google suchen</a>
<a href="http://bing.com" title="Eine Suchmaschine">Mit Bing suchen</a>
<img src="katze.jpg" alt="Meine Katze" title="Meine Katze"/>
```


### Klassen und IDs

Manchmal m�chten Sie Styling oder Interaktivit�t nur zu bestimmten Teilen einer Seite hinzuf�gen

Zum Beispiel m�chten Sie vielleicht einen Absatz gr�sser aussehen lassen

Wir k�nnen spezifische HTML-Elemente durch ihre `id` oder` class` Attribute ansprechen

```
<p id="intro">Lorem ipsum dolor sit amet</p>
<p class="beispiel">Lorem ipsum dolor sit amet</p>
```

#### IDs

Wann f�gen Sie eine ID hinzu?

Ein Element, das nur einmal auf der Seite auftritt

z.B. Eine Seiten�berschrift, Fusszeile, Navigation und Hauptinhaltsbereich

```
<nav id="site-navigation">
    ...
</nav>
```

#### Klassen

Wann f�gen Sie eine Klasse hinzu?

Bei Elementen, die auf einer Seite wiederholt auftauchen k�nnen

```
<article class="news">
    ...
</article>
```


#### Klassen und IDs benutzen

Bei der Benennung von Klassen und IDs, verwenden Sie keine Leerzeichen. Bindestriche und Unterstriche sind in Ordnung.

Jedes Element kann mehr als eine Klasse haben (durch Leerzeichen getrennt)

Ein Element kann nur eine ID haben

Jede ID darf nur einmal auf jeder Seite verwendet werden


### Mit HTML beschreiben

HTML hat eine begrenzte Anzahl von Tags, weil es urspr�nglich f�r lange, lineare technische Dokumente entworfen wurde

Es wird jetzt f�r viele Dinge verwendet, aber es gibt nicht genug Tags f�r jedes m�gliche Szenario

Wie entscheiden Sie, welches HTML-Tag zu verwenden ist?

Tags sind semantisch - sie haben unterschiedliche Bedeutungen

Es gibt keine richtige oder falsche Antwort

Sehen Sie sich den Quellcode anderer Websites an, die Sie besuchen

### Beispiel

Eine Beispiel HTML-Seite:

```
<html>
    <head>
        <title>Meine Website �ber Kekse</title>
    </head>
    <body>
        <h1>Beste Kekse</h1>
        <p id="intro">Dies ist eine Liste der besten Kekse</p>
        <ul class="kekse">
            <li>Schokoladenkekse</li>
            <li class="ingwer">Ingwer-Nuss-Kekse</li>
        </ul>
    </body>
</html>
```

#### `<head>`

Enth�lt Metadaten �ber die Seite

Wo Sie den Seitentitel, die Beschreibung und alle anderen relevanten Informationen hinzuf�gen

Wird nicht auf der Seite selbst dargestellt


#### `<body>`

Enth�lt den Seiteninhalt

Alles, was Sie hier eintragen, wird vom Browser gerendert


### Validierung

#### Was ist das?

�berpr�fen Sie die G�ltigkeit des Codes (haben Sie die Regeln befolgt?)

Stellen Sie sicher, dass sich die Webseiten an den W3C-Standard halten


#### Warum die M�he?

Es wird 90% der einfachen Rendering Bugs sofort zu beseitigen

Zug�nglichkeit - Mit kompatiblen Code kann jedes Browsing-Ger�t es rendern

 - [http://validator.w3.org/](http://validator.w3.org/)


***Weitere Informationen:***

 - [http://www.htmldog.com/](http://www.htmldog.com/)
 - [https://www.codecademy.com/tracks/web](https://www.codecademy.com/tracks/web)
 - [http://learn.shayhowe.com/html-css/](http://learn.shayhowe.com/html-css/)


## CSS

CSS macht Seiten h�bsch

 - HTML l�sst uns Inhalte hinzuf�gen - Text, Bilder und Videos
 - CSS f�gt Stil hinzu - Layout, Farben, Schriftarten

Alle Aspekte von Design und Layout werden von CSS abgedeckt

  - Layout
  - Farbe
  - Typografie
  - Hintergrundbilder
  - Grenzen
  - Schatten
  - Animation


### CSS hinzuf�gen

Angenommen, wir wollen die folgende HTML-Seite gestalten:

```
<html>
    <head>
        <title>Meine Website �ber Kekse</title>
    </head>
    <body>
        <h1>Beste Kekse</h1>
        <p id="intro">Dies ist eine Liste der besten Kekse</p>
        <ul class="kekse">
            <li>Schokoladenkekse</li>
            <li class="ingwer">Ingwer-Nuss-Kekse</li>
        </ul>
    </body>
</html>
```

#### Styling nach Tag-Namen

```
h1 {
    color: red;
}
```


#### Styling �ber die ID

```
#intro {
    font-weight: bold;
}
```


#### Styling �ber die Klasse

```
.ingwer {
    color: orange;
}
```


#### Styling mehrerer Elemente

```
li {
    font-size: 200%;
}
```


#### Styling von Dingen in anderen Dingen

```
.kekse li {
    background: green;
}
```


#### Stile gruppieren

Statt getrennter Stile f�r alles:

```
p {
    color: red;
}
h1 {
    color: red;
}
```

K�nnen Sie die Stile kombinieren:

```
p, h1 {
    color: red;
}
```

(Dies wirkt sich auf alle `<p>` und `<h1>` Elemente aus)


### CSS anwenden

#### CSS Inline (in einer HTML-Seite; nicht empfohlen!)

```
<html>
    <head>
        <title>Meine Seite</title>
        <style>
            h1 {
                background-color: purple;
                color: white;
            }
        </style>
    </head>
    <body>
        <h1>Hallo Welt</h1>
    </body>
</html>
```


#### CSS in einer separaten Datei (so wird's gemacht!)

index.html

```
<html>
    <head>
        <title>Meine Seite</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <h1>Hallo Welt</h1>
    </body>
</html>
```

style.css

```
h1 {
    background-color: purple;
}
```

***Weitere Informationen:***

 - [http://www.htmldog.com/](http://www.htmldog.com/)
 - [https://www.codecademy.com/tracks/web](https://www.codecademy.com/tracks/web)
 - [http://learn.shayhowe.com/html-css/](http://learn.shayhowe.com/html-css/)


## Seitenlayout mit CSS

### Block- und Inline-Elemente

Es ist wichtig, den Unterschied zwischen den beiden zu kennen


### Block-Elemente:

`<h1>`-`<h6>`, `<p>`, `<ul>`, `<ol>`, `<li>`, `<div>`, `<table>`, `<form>`, etc.

 - haben ihre eigene Zeile
 - nehmen 100% der Seitenbreite ein, falls nicht anders definiert


###�Inline-Elemente

`<a>`, `<em>`, `<strong>`, `<span>`, etc.

  - sitzen nebeneinander auf der gleichen Linie
  - bekommen nicht immer automatisch alle CSS-Styles (padding / margin / width / height etc.) - das kann verwirrend sein!
  - das Einf�gen von Block-Elementen innerhalb eines Inline-Elements (wie zB ein Link) kann zu unerwarteten Ergebnissen f�hren
  
Einfach mit CSS anpassen - `display: block` oder `display: inline`

Siehe:

 - [http://www.quirksmode.org/css/display.html](http://www.quirksmode.org/css/display.html)
 - [http://learnlayout.com/inline-block.html](http://learnlayout.com/inline-block.html)


### Layout

Die wichtigsten CSS-Eigenschaften, die wir f�r das Layout verwenden, sind `display`, `float` und `position`

Ein grossartiges Tutorial:

 - [http://learnlayout.com/](http://learnlayout.com/)


### Positionierung

Standardm�ssig haben alle HTML-Elemente ein CSS-Positionsattribut von `static`

```
<div id="main">...</div>
<div id="sidebar">...</div>
<div id="footer">...</div>
```

```
#main,
#sidebar,
#footer {
  position: static; /* dies ist der Standardwert */
}
```

Diese Block-HTML-Elemente werden auf ihrer eigenen Zeile sein

Durch das �ndern des CSS-Positionsattributs k�nnen Sie die oberen / unteren / linken / rechten Werte einstellen - relativ zum `<body>`, oder einen �bergeordneten Container der die Definition `position: relative` besitzt:

```
#main {
  position: absolute;
  left: 10px;
  width: 75%;
  background: #eee;
}

#sidebar {
  position: absolute;
  right: 10px;
  width: 20%;
  background: #ffd;
}
```

Eine Seite, die mit `position: absolute` ausgelegt ist, hat ihre Grenzen

  - "feste" H�hen des Inhalts
  - das Layout passt sich nicht dem Inhalt an

`position` ist n�tzlich, aber nicht f�r das Hauptseitenlayout


### Floats

HTML-Elemente k�nnen mit CSS als schwimmend definiert werden - `float: left;` oder `float: right;`

```
#main {
  background: #eee;
  float: left;
  width: 80%;
}

#sidebar {
  background: #ffd;
  float: right;
  width: 15%;
}
```

Ein schwimmendes Element wird so weit wie m�glich nach links oder rechts von seinem Containerelement verschoben

Wenn wir ein anderes Element in die gleiche Richtung schwimmen lassen, wird es verschoben, bis sein Rand den Rand des ersten schwimmenden Elements erreicht

Nicht-schwimmender Inhalt fliesst um schwimmende Elemente herum

Schwimmende Elemente sind besser, als die starre Positionierung f�r Layout - im Gegensatz zu absolut positionierten Elementen, beliben schwimmende Elemente im Dokumentenfluss und erlauben es den Inhalt auf einfacher Weise zu erweitern

Sie sollten (fast) immer eine Breite bei schwimmenden Elementen setzen, obwohl Elemente mit inh�renten Breiten (z.B. Bilder) keine Breite ben�tigen

#### Floats steuern

Wenn wir steuern wollen, wie viele Floating-Elemente auf einer Linie erscheinen, k�nnen wir ein div-Element um den floatenen Inhalt wickeln und eine Breite setzen:

```
<div id="block-container">
  <div class="block">Block 1</div>
  ...
  <div class="block">Block 10</div>
</div>
```

```
#block-container {
  width: 500px;
}
.block {
  float: left;
  width: 100px;
  margin-right: 20px;
}
```

#### Zwei Hauptanwendungen f�r Floats:

 - Seitenlayout
 - Layout von Elementen innerhalb eines Blocks


#### float: center?

Sie k�nnen kein Element im Mittelpunkt schwimmen lassen - daf�r gibt es noch andere Techniken

```
body {
  width: 600px;
  margin: 0 auto;
}
```


## Responsive Webseiten

Wir k�nnen nicht mehr davon ausgehen, dass die meisten Menschen in erster Linie einen Desktop- oder Laptop-Computer verwenden, um das Internet zu durchsuchen

Die Menschen nutzen eine Vielzahl von Internet-Browsern und Betriebssystemen

Heutzutage haben die meisten Leute mindestens ein anderes Ger�t, das sie benutzen, um das Internet zu durchsuchen

Diese Ger�te werden zunehmend anstelle von "traditionellen" Browsern eingesetzt

Wir m�ssen sicherstellen, dass unsere Webseiten �ber alle g�ngigen Browser hinweg arbeiten

Bei der Erstellung einer Website m�ssen wir neben Desktop-Browsern auch Mobile-Browser/-Ger�te ber�cksichtigen

Diese Ger�te haben unterschiedliche Anzeigeaufl�sungen (oder Browser-Dimensionen)

Diese Ger�te haben auch unterschiedliche Methoden der Interaktion


### Medien-Abfragen

Sie k�nnen CSS f�r verschiedene Browseraufl�sungen (oder Dimensionen) mit CSS `@media` Abfragen angeben.

F�r eine typische Website k�nnen Sie drei S�tze von Stilen erstellen:

  - einen Satz generischer Seitenstile, die auf jedem Ger�t/Browser verwendet werden
  - einen weiteren Satz von Stilen f�r Low-Resolution (mobile) Browser
  - einen dritten Satz nur f�r hochaufl�sende (Desktop/Tablet) Browser

Der Punkt, an dem das Design von einem Layout zum n�chsten wechselt, wird allgemein als "Bruchpunkt" bezeichnet,

Diese Medien-Abfragen k�nnen im CSS inline erscheinen:

```
@media (max-width: 480px) {
  #main-content,
  #aside {
    width: 100%;
    float: none;
  }
}
```

Styles, die in die `@media`-Abfrage geschrieben werden, werden nur verwendet, wenn die angegebenen Bedingungen wahr sind.

Die Verwendung von `@media` Abfragen, um verschiedene Layouts f�r verschiedene Aufl�sungen (oder Browser-Dimensionen) zu erstellen, ist allgemein als Responsive Design bekannt

Das Layout der Inhalte sollte sich anpassen, um f�r verschiedene Browser-Gr�ssen zu passen


### Meta Viewport

Sie k�nnen steuern, wie eine Seite in einem (modernen) mobilen Browser mit einer `<meta>` Viewport-Deklaration rendert:

```
<meta name="viewport" content="width=device-width, initial-scale=1" />
```


### Mobile zuerst

Es ist m�glich, eine bestehende Website responsive zu machen, indem Sie zus�tzliche Stile (innerhalb einer `@media` Abfrage) f�r mobile Ger�te hinzuf�gen

Bandbreitenprobleme f�r Desktop-Browser sind heutzutage aufgrund von Breitbandleitungen weniger relevant, teils aber immer noch ein Anliegen f�r mobile Browser

Die Benutzung von `@media` Abfragen bedeutet, dass ein Mobiltelefon eine ganze Desktop-Seite herunterladen muss plus die zus�tzlichen Styles

Es kann sinnvoller sein, zuerst ein grundlegendes Design f�r mobile zu erstellen und dann zus�tzliche Layout-Stile f�r Desktop-Browser hinzuzuf�gen

Dieser Ansatz ist bekannt als mobile-first

Dieser Ansatz ist ger�teintegrativ

Der Standard-Satz von Stilen, die an jeden Browser und jedes Ger�t gesendet werden, sollte f�r das grundlegendste Seitenlayout sein

In dieser Eigenschaft sollte ein Mangel an �nterst�tztung von `@media` Abfragen als Ihre erste `@media` Abfrage gesehen werden

D.h. alte Browser oder Ger�te unterst�tzen keine `@media` Abfragen, so dass diese Ger�te die Standard-Mobile-Version erhalten


***Weitere Informationen:***

 - [http://blog.cloudfour.com/responsive-design-for-apps-part-1/](http://blog.cloudfour.com/responsive-design-for-apps-part-1/)
 - [http://www.webdesignerdepot.com/2011/09/the-ultimate-responsive-web-design-roundup/](http://www.webdesignerdepot.com/2011/09/the-ultimate-responsive-web-design-roundup/)
 - [http://www.designbyfront.com/demo/goldilocks-approach/](http://www.designbyfront.com/demo/goldilocks-approach/)
 - [http://coding.smashingmagazine.com/2010/07/19/how-to-use-css3-media-queries-to-create-a-mobile-version-of-your-website/](http://coding.smashingmagazine.com/2010/07/19/how-to-use-css3-media-queries-to-create-a-mobile-version-of-your-website/)
 - [http://marcdrummond.com/web-standards/2011/06/20/hell-bad-devices-responsive-web-design-and-web-standards](http://marcdrummond.com/web-standards/2011/06/20/hell-bad-devices-responsive-web-design-and-web-standards)
 - [http://stefangirard.com/2012/01/responsive-design-is-bad/](http://stefangirard.com/2012/01/responsive-design-is-bad/)
 - [http://www.webdesignshock.com/responsive-design-problems/](http://www.webdesignshock.com/responsive-design-problems/)



## Web-Standards

### Was sind Web-Standards?

Eine "vereinbarte" Spezifikation f�r HTML, CSS und JavaScript

  - Wie sollten wir Code schreiben
  - Wie Web-Browser Code lesen und rendern

Web-Standards erlauben Web-Entwicklern, sich auf ihren Code zu konzentrieren

Wenn der Code g�ltig ist, sollte die Seite in einem Webbrowser wie erwartet rendern

Ein gutes Beispiel kommt aus der Geschichte des `<img>` Elementes:
 - [Eine lange Abschweifung, wie Standards gemacht werden](http://diveintohtml5.info/past.html#history-of-the-img-element)


#### Eine kurze Zusammenfassung der Web-Standards

  - Verwenden Sie g�ltiges, semantisches HTML f�r Inhalt
  - Verwenden Sie CSS f�r das Layout
  - Verwenden Sie JavaScript um das Verhalten der Webseite zu steuern


### Web-Standards und Zug�nglichkeit

Web-Standards definieren Regeln f�r die Zug�nglichkeit

> "Die Macht des Internets liegt in seiner Universalit�t. Der Zugang f�r jedermann unabh�ngig von Behinderung ist ein wesentlicher Aspekt."
>
> [W3C Web Content Accessibility Guidelines](http://www.w3.org/TR/WCAG20/)


### Warum sind Web-Standards wichtig?

Tim Berners-Lee schuf HTML als Sprache, um die Informationen in einer konsistenten Weise darzustellen

Wenn jeder sich auf ein gemeinsames Vokabular einigen kann, dann sollte ein Webbrowser in der Lage sein zu interpretieren, was ich erstellt habe und es Ihnen in einer vorhersagbaren Weise zeigen

Dies wurde von der W3C beaufsichtigt, die Standards definiert, die von allen befolgt werden sollten

In der Theorie war das ein guter Plan - bis das Web popul�rer wurde, als man es sich vorstellen konnte

In den fr�hen Tagen des Internets wurden konkurrierende Webbrowser erstellt und in einem Versuch, Marktanteile zu gewinnen, wurden zahlreiche neue Features eingef�hrt, die in rivalisierenden Browsern nicht verf�gbar waren. Neue Elemente, neue Wege zur Auslegung und Interaktion mit Webseiten

Dies f�hrte einerseits zu einer Vielzahl von Innovationen. Das ist in der Theorie eine gute Sache. Aber in der Praxis ... es f�hrte zu Fragmentierung, wie Browser HTML gerendert haben

Diese Fragmentierung verursachte grosse Probleme f�r Entwickler und Webbenutzer gleichermassen

Um eine Website zu schaffen, die �berall arbeitete, musste man oft die gleiche Sache zweimal, auf zwei verschiedene Arten machen. Oder h�ufiger den Aufbau einer Website und die Optimierung nur f�r einen einzigen Browser entwickeln

Browser-Hersteller wollten neue Funktionalit�ten implementieren, die Web-Entwickler nutzen wollten, was jedoch in einem Browser nicht m�glich war, weil man sich nicht einigen konnte, wie man es implementiert

Gruppen von Entwicklern bildeten Kollektive wie das Web Standards Project (WaSP), um konkurrierende Browser-Hersteller zu �berzeugen, die gemeinsamen Standards des W3C zum Nutzen aller zu benutzen

Es dauerte eine Reihe von Jahren bis ihre Botschaft erh�rt wurde, aber schliesslich haben die grossen Browser-Hersteller irgendwann realisiert, dass der Ansatz auch ihnen zugute kommen w�rde


### Web-Standards heute

Web-Standards sind heute relevanter denn je - wir haben eine Reihe von Desktop- und mobilen Browsern

Um sicherzustellen, dass diese Browser in einer konsistenten Weise arbeiten, m�ssen sie weiterhin einen gegenseitig vereinbarten Satz von Designprinzipien und Regeln befolgen

Um alles effizient zu machen, brauchen Entwickler einen Konsens. Wir m�ssen wissen, dass das, was wir bauen, funktionieren wird

Der Unterschied heute ist, mit Web-Standards, haben wir einige Sicherheit, dass dies in der Tat der Fall ist

Die Browser-Hersteller selbst sind nun aktiv am Prozess der Definition der neuen Standards f�r HTML, CSS und JavaScript beteiligt

Sie folgen in der Regel vereinbarten Standards und Konventionen bei der Erstellung dieser Innovationen, d.h. innovative Funktionen k�nnen zuverl�ssig implementiert werden, um eine Erfahrung zu schaffen, die in jedem Browser funktioniert