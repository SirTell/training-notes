# JavaScript Notizen

Ein paar Notizen vorbereitet beim Schreiben von Schulungen ...

Diese Anmerkungen nehmen eine geringe Menge an Vorkenntnissen der Programmierung im Allgemeinen und insbesondere JavaScript-Kenntnisse an. Zumindest wird davon ausgegangen, dass bekannt ist, was JavaScript ist, warum wir es benutzen und wie man es in einem Webbrowser ausführt.


## JavaScript Grundlagen

### Variablen

Eine Analogie, die oft verwendet wird, um eine Variable zu beschreiben, ist *ein Container, in den man etwas einsetzen kann*.

Der Name, den Sie einer Variable geben, ist das Etikett, das Sie auf den Container gelegt haben. Sie wissen also, wie man es später wieder findet. Variablen können verwendet werden, um alles zu speichern - Zahlen, Text oder andere Arten von Informationen:

```
var nearestStar = "Alpha Centauri";
var lightYearsAway = 4.3;
var age = 6000000000;
var isHot = true;
```

Wenn Sie diese Informationen später referenzieren müssen, beziehen Sie sich auf den Variablennamen:

```
alert(nearestStar); // "Alpha Centauri"
```

Variablen können mit den Werten aus anderen Variablen gesetzt werden:

```
var planets = 8;
var dwarfPlanets = 5;

var planetCount = 8 + 5; // 13
```

Der Wert einer Variablen kann geändert werden (deshalb heisst es *Variable*):

```
var numberOfPlanets = 9;

numberOfPlanets = numberOfPlanets - 1; // bye bye Pluto
```

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar\_and_types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types)


### Arrays

Wir können verwandte Listen von Informationen in Arrays speichern. Dies ermöglicht es uns, sie zusammen zu gruppieren und später einfach Code für alle Elemente im Array auszuführen.

Erstellen eines Arrays:

```
var planets = [
    "Mercury",
    "Venus",
    "Earth",
    "Mars",
    "Jupiter",
    "Saturn",
    "Uranus",
    "Neptune"
];
```

Und auf ein Array zugreifen:

```
var len = planets.length; // 8
var planet = planets[2];  // "Earth"
```

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)


### For Schleifen

`for` Schleifen sind eine einfache Möglichkeit, um auf die Informationen in einem Array zuzugreifen:

```
for (var counter = 0, planetCount = planets.length; counter < planetCount; counter++) {
    var planet = planets[counter];
    alert("I like the planet " + planet);
}
```

Dieser Code verwendet eine Variable, um die Array-Länge einmal zu cachen, anstatt sie jedes Mal zu überprüfen, wenn wir die Schleife passieren. Dies ist für eine (vernachlässigbare) Geschwindigkeitsverbesserung. Es ist eine von einer Reihe von kleinen Optimierungen, die Entwickler oft empfehlen, um die JavaScript-Leistung zu beschleunigen. Andere werden ggf. diskutiert.

Ein anderer Weg, um durch ein Array zu durchlaufen ist mit `forEach`:

```
function enthuse (planet) {
    alert("I like the planet " + planet);
}

planets.forEach(enthuse);
```

Für die Zwecke des Durchschleifens durch das Array kann entweder `for` oder `forEach` verwendet werden, um unsere Anforderungen zu erfüllen.

Diese Wahl der Optionen für die Gestaltung von Code zeigt das Programmierprinzip von *es gibt mehr als eine Möglichkeit, etwas zu tun*.

Allerdings kann, wie es oft der Fall ist, eine Option Vor- oder Nachteile haben. In dieser Situation ist man sich bewusst, dass `forEach` dies nicht so weit wie eine einfache `for` Schleife unterstützt wird, zumindest in älteren Browsern.

***Weitere Informationen:***

 - [http://stackoverflow.com/a/9329476](http://stackoverflow.com/a/9329476)
 - [https://coderwall.com/p/kvzbpa/don-t-use-array-foreach-use-for-instead](https://coderwall.com/p/kvzbpa/don-t-use-array-foreach-use-for-instead)
 - [https://css-tricks.com/snippets/javascript/loop-queryselectorall-matches/](https://css-tricks.com/snippets/javascript/loop-queryselectorall-matches/)


### Objekte

Objekte sind nützlich, um verwandte Werte zu gruppieren:

```
var mars = {
    radius: 3396,
    distanceFromSun: 227900000
};

var earth = {
    radius: 6371,
    distanceFromSun: 149600000
};
```

Auf diese Werte kann unterschiedlich zugegriffen werden:

```
earth["radius"] // 6371
earth.radius // 6371
```

Wir können Arrays und Objekte ineinander setzen. Dies kann eine nützliche Möglichkeit sein, komplexe Informationen zu organisieren:

```
var planets = [
    {
        name: "mars",
        radius: 3396,
        distanceFromSun: 227900000
    },
    {
        name: "earth",
        radius: 6371,
        distanceFromSun: 149600000
    }
];
```

Wir können dann diese Informationen durchlaufen und Funktionen ausführen, um nützliche Informationen zu extrahieren:

```
function describePlanet (planet) {
    alert(planet.name + " has a radius of " + planet["radius"] + "km");
}

planets.forEach(describePlanet);
```

JavaScript-Objekte sind die Basis für JSON (*JavaScript Object Notation*). Die wichtige Regel, die man sich erinnern sollte, ist, dass in gültigem JSON alle Schlüssel mit doppelten Anführungszeichen zitiert werden müssen:

```
[
    {
        "name": "mars",
        "radius": 3396,
        "distanceFromSun": 227900000
    },
    {
        "name": "earth",
        "radius": 6371,
        "distanceFromSun": 149600000
    }
];

```

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working\_with_Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
 - [http://www.sitepoint.com/back-to-basics-javascript-object-syntax/](http://www.sitepoint.com/back-to-basics-javascript-object-syntax/)


### Funktionen

Funktionen sind eine Reihe von Anweisungen, die jetzt angegeben (oder *definiert*) werden können, aber später verwendet (oder *genannt*) werden. Der Hauptvorteil der Verwendung einer Funktion ist, dass Sie sie nur einmal erstellen müssen, und dann können Sie sie wieder verwenden, so oft Sie sie benötigen.

Funktionen können auf zwei Arten definiert werden. Es gibt subtile, aber wichtige Unterschiede.

**Funktions Deklarationen:**

```
function enthuse (planet) {
    return "I like the planet" + planet;
}
```

**Funktion Ausdrücke:**

```
var enthuse = function (planet) {
    return "I like the planet" + planet;
}
```

Beides kann auf die gleiche Weise verwendet werden:

```
var sentence = enthuse("Mercury"); // "I like the planet Mercury"
```

Der Hauptunterschied besteht darin, dass deklarierte Funktionen *gehisst werden*, d.h. sie werden vom JavaScript-Interpreter an die Spitze des Blocks verschoben. Deshalb können sie referenziert werden, bevor sie deklariert werden.

***Weitere Informationen:***

 - [http://stackoverflow.com/a/336868](http://stackoverflow.com/a/336868)
 - [http://www.unicodegirl.com/function-statement-versus-function-expression.html](http://www.unicodegirl.com/function-statement-versus-function-expression.html)


### if / else Konditionen

if / else-Bedingungen erlauben es uns, bestimmte Funktionalität nur dann auszuführen, wenn bestimmte Bedingungen erfüllt sind.

Ihre Verwendung erfordert eine Bedingung, die entweder wahr oder falsch sein wird, worauf wir unsere Entscheidung stützen können:

```
if (planet === "Earth") {
    asYouWere();
} else if (planetHasOxygen()) {
    breatheDeeply();
    thinkAboutHome();
} else {
    holdYourBreath();
    lookForRocketShip();
}
```

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)


## Entwickler Tools

Die meisten Browser haben nützliche Entwickler-Tools eingebaut. Hier sind einige Notizen zu den wichtigsten Tools, die nützlich für JavaScript-Entwicklung sind. Sie sind spezifisch für Panels in der aktuellen Version der Chrome-Entwickler-Tools, obwohl Äquivalente in der Regel in anderen grossen Browsern zur Verfügung stehen.


### Konsolen-Panel

Das Konsolen-Panel ist der primäre Ort, um Nachrichten zu protokollieren, Fehler zu erkennen, Code zu testen und mit der aktuellen Seite zu interagieren.


#### Nachrichten protokollieren

Es kann sinnvoll sein, `console.log();` zu verwenden, um den aktuellen Wert einer Variablen während der Entwicklung anzuzeigen. Eine oder mehrere Variablen können als *Parameter* an diese Funktion übergeben werden.

```
console.log(planets, stuff, somethingElse);
```

Sie können String-Formatierung und benutzerdefinierte Stile auf verschiedene Nachrichten anwenden, so dass eine Differenzierung in der Anzeige von Nachrichten für verschiedene Zwecke protokolliert werden kann.

```
var message = "%c Planet %s has a radius of %d km";
var styles = "color: orange; background: blue; font-size: 16pt";
var planet = "Earth";
var radius = 6371;

console.log(message, styles, planet, radius);
```

Es sind weitere nützliche `console`-Optionen verfügbar, z.B. `console.group()` für die Zusammenstellung verwandter Nachrichten in eine zusammenklappbare Gruppe und `console.table()` für die Anzeige von sich wiederholenden Daten in einer Tabelle.

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/console-api](https://developer.chrome.com/devtools/docs/console-api)
 - [https://developer.chrome.com/devtools/docs/tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks)


#### Fehler erkennen

Wenn Sie einen Fehler in Ihrem JavaScript-Code machen, wird es in der Konsole referenziert.

Dies sollte einen Dateinamen, Zeilennummer und (hoffentlich) einen Hinweis auf die Art des Fehlers geben.

Wenn Sie auf den Fehler klicken, führt er Sie zum *source*-Panel, um ihn zu debuggen.

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/console#errors-and-warnings](https://developer.chrome.com/devtools/docs/console#errors-and-warnings)


#### Code testen

Vor dem Schreiben von Code kann es hilfreich sein, in der Konsole zu experimentieren. Dies kann dazu beitragen, eine Live-Vorschau Ihrer Änderungen zu sehen, die mit der aktuellen Seite interagiert, wenn Sie einen Befehl ausführen. Wenn es fertig ist, kann dieser Code dann in eine externe Datei kopiert werden.

Jedes Mal, wenn Sie die Seite aktualisieren, wird dieser Code zurückgesetzt. Es wird immer noch im Verlauf der Konsole verfügbar sein (genau wie ein Terminal-Fenster), so dass das Drücken von oben / unten auf der Tastatur durch vorherige Befehle durchläuft.


### Elemente Panel

Der Inspektor wird hauptsächlich für die Anzeige des aktuellen HTML und CSS verwendet, aber er kann auch für das JavaScript-Debugging nützlich sein.

Zum Beispiel kann er zeigen, welche Elemente auf der Seite *Event-Listener* haben. Diese werden später besprochen.

Sie können auf jedes HTML-Element mit der rechten Maustaste klicken und eine *'break on ...'* Option auswählen, die es Ihnen ermöglicht, JavaScript an der Stelle zu pausieren und zu debuggen, an der das HTML-Element über JavaScript manipuliert wird.


### Netzwerk Panel

Das Netzwerk-Panel listet alle HTTP-Anfragen auf, die beim Debuggen von AJAX-Anfragen nützlich sein können - zum Beispiel können Sie die Parameter anzeigen, die an den Server gesendet wurden, und die Daten, die vom Server zurückgegeben wurden (oder nicht).

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/network](https://developer.chrome.com/devtools/docs/network)


### Quellen Panel

Im Quellpanel kann das JavaScript der aktuellen Seite analysiert werden. Diese Debugging-Tools sind leistungsstark und komplex.


#### Quellen

Die Registerkarte "Quellen" listet alle textbasierten Quellen auf der Seite auf, z.B. die HTML-, CSS- und JavaScript-Dateien, aus denen die aktuelle Seite besteht. Wenn Sie auf eine dieser Dateien klicken, wird diese im Hauptfenster angezeigt. Wenn Sie mit der rechten Maustaste auf eine beliebige Datei klicken, werden weitere Optionen angezeigt.

Beim Betrachten einer minifizierten Datei ist die Option "pretty print" im Hauptfenster praktisch, um den Code lesbar zu machen.

Wenn Sie einen *Arbeitsbereich* einrichten, können Sie Dateien direkt im Editor bearbeiten und Ihre Änderungen an Ihren lokalen Dateien speichern.

***Weitere Informationen:***

 - [https://developer.chrome.com/devtools/docs/workspaces](https://developer.chrome.com/devtools/docs/workspaces)


#### Content-Skripte

Die Registerkarte *Content-Skripte* listet alle Skripts auf, die im aktuellen Browser-Tab von Erweiterungen (und anderen Quellen) und nicht direkt von der Website selbst geladen werden. Zum Beispiel werden hier die Skripts, die von Ihren Browser-Erweiterungen in die aktuelle Seite eingefügt (injected) werden, angezeigt.


#### Snippets

Auf der Registerkarte *Snippets* können Sie eigene benutzerdefinierte Skripts erstellen und speichern, die Sie dann manuell auf einer Seite ausführen können.

Diese sind praktisch, wenn Sie ständig das gleiche Stück Code auf einer Seite laufen lassen wollen, aber den Code nicht im produktiven Code haben möchten.

Klicken Sie mit der rechten Maustaste in das Bedienfeld, um ein neues Snippet zu erstellen. Geben Sie Ihren Code ein und speichern Sie ihn. Klicken Sie mit der rechten Maustaste erneut, um zu starten.

Ein Beispiel für Code zum Testen von Snippets:

```
var headings = document.querySelectorAll("h1");
for (var i = 0; i < headings.length; ++i) {
    headings[i].style.color = "#f90";
}
```


#### Debugging

Debugging JavaScript ist ein komplexes Thema, das gründlich anderswo im Internet erklärt wird. Die folgenden Anleitungen sind ziemlich umfassend.

Der beste Weg, um Probleme zu debuggen, besteht darin, den Fehler zu isolieren und zu identifizieren, wie es konsequent repliziert werden kann. Dies macht es leichter, den Fehler zu beseitigen.

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/authoring-development-workflow](https://developer.chrome.com/devtools/docs/authoring-development-workflow)
 - [https://remysharp.com/2012/12/21/my-workflow-never-having-to-leave-devtools](https://remysharp.com/2012/12/21/my-workflow-never-having-to-leave-devtools)
 - [https://developer.chrome.com/devtools/docs/javascript-debugging](https://developer.chrome.com/devtools/docs/javascript-debugging)
 - [https://gist.github.com/jedrichards/9942165](https://gist.github.com/jedrichards/9942165)


#### Remote-Debugging

Bei der Arbeit mit einem iOS-Gerät können Sie Mobile Safari remote debuggen, indem Sie das Gerät an den USB-Port eines Mac anschliessen und die Safari Developer-Tools öffnen.

Wenn Sie mit einem Android-Gerät arbeiten, können Sie mit Mobile Chrome debuggen, indem Sie das Gerät an den USB-Port eines Computers anschliessen und diese [Anweisungen](https://developer.chrome.com/devtools/docs/remote-debugging) befolgen.

Drittanbieter Tools wie [jsconsole.com](http://jsconsole.com/remote-debugging.html) können beim Debuggen sehr nützlich sein.


### Andere Panels

 - Das *Timeline*-Panel ist nützlich, um die Renderleistung zu verfolgen: [https://developer.chrome.com/devtools/docs/timeline](https://developer.chrome.com/devtools/docs/timeline)
 - Das *Profile* Panel ist nützlich für die Verfolgung von CPU- und Speicherverbrauch: [https://developer.chrome.com/devtools/docs/profiles](https://developer.chrome.com/devtools/docs/profiles)
 - Das *Resources* Panel ist nützlich für die Verfolgung von Informationen, die in Cookies und der Local Storage gespeichert sind: [https://developer.chrome.com/devtools/docs/resources](https://developer.chrome.com/devtools/docs/resources)
 - Das *Audits* Panel ist nützlich, um die Leistung einer Seite zu testen und Möglichkeiten zu analysieren, um sie zu verbessern: [https://developer.chrome.com/devtools#audits](https://developer.chrome.com/devtools#audits)


## Die DOM

In einem Webbrowser hat JavaScript zwei spezielle *globale* Variablen - `window` und `document` - das erlaubt uns, mit dem Browser und der Webseite zu interagieren.

Die Variable `window` wird oft verwendet, um zu erkennen, wann eine Seite geladen wird, wenn das Fenster gescrollt wird und auf die Dimensionen zugegriffen wird (z.B. die Fenstergrösse verändern).

Die häufigste Verwendung von `document` besteht darin, auf HTML-Elemente in einer Webseite zuzugreifen, indem auf das _Document Object Model_ (DOM) verwiesen wird, welches die JavaScript-Darstellung der HTML-Seitenstruktur ist:

**HTML**

```
<html>
    <body>
        <h1>Stuff in space</h1>
        <ul class="planets js-planets">
        </ul>
    </body>
</html>
```

**JS**

Zwei Beispiele für die Interaktion mit dieser Seite über JavaScript, mit dem DOM:

```
var heading = document.querySelector("h1");
heading.textContent = "The Planets";
heading.style.color = "#f90";
heading.setAttribute("class", "heading-main");
```

Und eine weitere:

```
var planetList = document.querySelector(".js-planets");
var planet = document.createElement("li");
planet.id = "planet-earth";
planet.classList.add("planet");
planet.textContent = "Earth";
planetList.appendChild(planet);
```

Wir können in der Regel alle DOM-Manipulationen, die wir benötigen, mit diesen nativen JavaScript-Befehlen durchführen, ohne auf eine externe Bibliothek zurückgreifen müssen. Wir *brauchen* JQuery nicht, um auf das DOM zuzugreifen und zu manipulieren. Aber es macht diese Interaktionen (und viele andere) viel einfacher.

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/API/Document\_Object_Model/Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)


## JQuery

Kurz nach seiner Entstehung wurde JQuery schnell zu einem beliebten Werkzeug, um die vielen Inkonsistenzen zu bewältigen, wie bspw. die falsche Implementierung von JavaScript in verschiedenen Browsers.

Das ist nicht mehr so relevant, denn moderne Browser setzen in der Regel die gleichen Standards ein. Aber JQuery ist immer noch nützlich, und nicht nur für DOM-Interaktionen. Es vereinfacht auch *Ajax* Anrufe, Handling *Events* und Objekt / Array Manipulation unter anderem.

Ein grosser Vorteil ist, dass *die meisten* Front-End-Entwickler mit JQuery vertraut sind, und es hilft, die Teams auf einer gemeinsamen Codebasis arbeiten zu lassen.

Die Anwesenheit von JQuery ist in fast jeder Website allgegenwärtig. Als solches ist es sinnvoll, nicht nur zu lernen, wie man es benutzt, sondern auch seine Macken und Mängel.

Dieser Leitfaden nimmt ein Grundwissen von JQuery an - wie füge es zu einer Webseite hinzu und verwende es, um DOM-Elemente auszuwählen und zu manipulieren.


### JQuery Tipps

#### Schreiben Sie nicht alle in *document ready*

Die häufigste Verwendung von JQuery ist die Initialisierung von Code, wenn das DOM der Seite geladen hat, mit:

```
$(document).ready(function () { ... });
```

*Das wird manchmal abgekürzt:*

```
$(function () { ... });
```

Dies führt oft dazu, dass der Code einer ganzen Anwendung in einer einzigen *global.js* Datei gespeichert ist, und alles in der *ready* Funktion referenziert ist:

```
$(document).ready(function () {
    ...
    (an entire application's code goes here)
    ...
});
```

Das ist keine gute Idee, aus mehreren Gründen.

Wenn der gesamte JS-Code der Website an einem einzigen Ort gespeichert ist, kann er schnell schwer zu verwalten sein.

Sofern Sie nicht vorsichtig sind, können Sie in Schwierigkeiten mit dem Scope kommen, wenn keine zwei Variablen den gleichen Namen teilen können. Dies wird später noch näher erörtert.

Ein weiteres Problem ist, dass es die anfängliche Wiedergabe der Website verlangsamen kann, da dieser Code nicht analysiert wird, bis die Seite bereit ist, gerendert zu werden. Es kann Teile des Codes geben, die sofort ausgeführt werden können, anstatt auf das DOM warten zu müssen.

Eine Lösung für dieses Problem ist, Code modular zu halten, und nur den Code innerhalb der DOM *ready* Funktion zu *initialisieren*.

```
// set up all tab functionality
function tabs () {
    ...
}

// set up all slideshow functionality
function slideshows () {
    ...
}

// start all functionality
function init () {
    tabs.init();
    slideshows.init();
}

// run on DOM load
$(document).ready(init);
```

Beachten Sie, dass dies eine Vereinfachung einer Lösung ist, um das Problem zu demonstrieren. Detaillierte Lösungen werden später gezeigt.

***Weitere Informationen:***

 - [https://learn.jquery.com/code-organization/concepts/](https://learn.jquery.com/code-organization/concepts/)
 - [http://www.elijahmanor.com/dont-initialize-all-the-things-in-jquery-ready/](http://www.elijahmanor.com/dont-initialize-all-the-things-in-jquery-ready/)


#### Erwägen Sie die Präfixierung von JQuery-Objekten mit *$*

Eine weit verbreitete Konvention, die dazu beitragen kann, eine Variable zu unterscheiden, die auf ein JQuery-Objekt von anderen Variablentypen verweist, ist diese Variablennamen mit einem `$` zu präfixieren:

```
var $planetsEl = $("#planets .planet");
var planetCount = $planetsEl.length;
```

Dies hilft zu zeigen, welche Variablen auch Zugriff auf JQuerys viele Funktionen haben.

Einige Entwickler mögen diesen Ansatz, andere nicht. Aber es lohnt sich zu überlegen und sich für die eine oder anderen einer Konvention zu entscheiden.

***Weitere Informationen:***

 - [http://www.bennadel.com/blog/1778-using-variable-in-jquery-code-is-just-hungarian-notation.htm](http://www.bennadel.com/blog/1778-using-variable-in-jquery-code-is-just-hungarian-notation.htm)


#### DOM Elemente cachen

JQuery macht es sehr einfach, schnell mit dem DOM zu interagieren. Die DOM-Interaktion ist jedoch langsam. Aus Geschwindigkeitsgründen ist es am besten, mit dem DOM so wenig wie möglich zu interagieren.

Beim Abfragen des DOM, um nach einem Element zu suchen, speichern Sie das Ergebnis für die zukünftige Verwendung zwischen.

```
var $el = $(".list-item");

$el.addClass("active");

$el.on("click", function (e) {
    $el.toggleClass("active");
});
```

***Weitere Informationen:***

 - [http://ttmm.io/tech/selector-caching-jquery/](http://ttmm.io/tech/selector-caching-jquery/)
 - [http://james.padolsey.com/javascript/js-adolescence/](http://james.padolsey.com/javascript/js-adolescence/)


#### DOM Elemente erstellen

Nochmal, die DOM Interaktion ist langsam.

Wenn Sie eine Reihe neuer DOM-Elemente erstellen, ist es ein guter Ansatz, um das neue HTML-Markup zu generieren und dann in die Seite in einem einzigen Befehl einzufügen:

```
var planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"];

var $planetList = $(".planet-list");
var planetElements = "";

for (var counter = 0, planetCount = planets.length; counter < planetCount; counter++) {
    planetElements += "<li>" + planets[counter] + "</li>";
}

$planetList.append(planetElements);
```

Eine alternative Methode besteht darin, die Elemente aus dem DOM zu *lösen*, während sie manipuliert werden, und sie dann wieder anzuschliessen, wenn sie fertig sind.

***Weitere Informationen:***

 - [http://learn.jquery.com/performance/detach-elements-before-work-with-them/](http://learn.jquery.com/performance/detach-elements-before-work-with-them/)
 - [http://24ways.org/2011/your-jquery-now-with-less-suck](http://24ways.org/2011/your-jquery-now-with-less-suck)


#### Cache $(this)

Ähnlich wie der Punkt über das Zwischenspeichern von DOM-Elementen, wenn Sie auf `$(this)` mehrere Male verweisen, überlegen Sie, ob es Sinn macht das Element zwischenzuspeichern, um eine verbesserte Leistung zu erzielen:

```
$(".el").click(function (e) {
    var $this = $(this);
    $this.addClass("active");
    $this.slideDown();
    var $a = $this.find("a");
});
```


#### Verzichten Sie auf $(this) generell

Manchmal ist es nicht notwendig, ein Element in einem JQuery-Objekt zu umwickeln.

Betrachten Sie das folgende Beispiel:

```
$(".el").click(function (e) {
    var $this = $(this);
    var id = $this.attr("id");
});
```

In diesem Fall, wenn alles, worauf wir hinaus sind, ist die ID des Elements zu bekommen, dann muss es nicht in ein JQuery-Objekt eingehüllt werden, da es leicht direkt aus dem nativen DOM-Objekt zugegriffen werden kann:

```
$(".el").click(function (e) {
    var id = this.id;
});
```

Das Lernen nativer JavaScript-Methoden kann von Vorteil sein, wenn Sie JQuery nicht benutzen müssen.


#### Manipulieren Sie Klassen, nicht Stile

Wenn Sie den Stil eines Elements ändern möchten, verändern Sie seine Stile nicht direkt:

```
// Bad
$(".planet").css({
    "background": "#036",
    "border-color": "#f90"
});
```
Stattdessen definieren Sie diese Stile in CSS:

```
.planet {
    background: #036;
    border-color: #f90;
}
```

Und dann fügen Sie die Klasse mit JavaScript hinzu:

```
$(".planets li").addClass("planet");
```

Dies hilft bei der Aufrechterhaltung des Grundsatzes der *Trennung von Interessen* - CSS ist verantwortlich für Styling, JavaScript wird für das Verhalten verwendet.

Es ermöglicht auch eine leichtere Prüfung von Stilen, da es möglich ist, die Klasse manuell hinzuzufügen oder zu entfernen, um das Layout zu testen, ohne JavaScript zu ändern.

***Weitere Informationen:***

 - [http://www.smashingmagazine.com/2012/11/19/building-relationship-between-css-javascript/](http://www.smashingmagazine.com/2012/11/19/building-relationship-between-css-javascript/)


#### Erwägen Sie alternative Methoden der Animation

Wenn Sie einen einfachen Übergang erstellen, überlegen Sie, ob es mit CSS umgesetzt werden kann:

```
.planet {
    position: absolute;
    top: 0;
    left: 0;
    width: 25%;
    height: 25%;
    transition: all .25s ease-in-out;
}

.planet.is-active {
    top: 25%;
    left: 25%;
    width: 50%;
    height: 50%;
}
```

Es kann möglich sein, eine Animation einfach durch Umschalten eines Klassennamens mit JavaScript auszulösen:

```
$(".planet").on("click", function (e) {
    $(this).toggleClass("is-active");
});
```

Es ist nicht immer möglich, CSS für Animationen zu verwenden. Wenn Sie JavaScript verwenden, sollten Sie das [JQuery animate enhanced](https://github.com/benbarnett/JQuery-Animate-Enhanced) Plugin (oder ähnliches) ausprobieren, weil es hardware-beschleunigte CSS3 Übergänge  nutzt, wann immer möglich. Dazu benötigt es Tests, denn es wird nicht immer funktionieren und kann u.U. auch seltsame Fehler produzieren.

Eine nicht-JQuery-basierte Alternative für Animationen ist die [GSAP](http://greensock.com/gsap) Bibliothek.

***Weitere Informationen:***

 - [http://www.smashingmagazine.com/2014/09/04/animating-without-jquery/](http://www.smashingmagazine.com/2014/09/04/animating-without-jquery/)
 - [https://css-tricks.com/myth-busting-css-animations-vs-javascript/](https://css-tricks.com/myth-busting-css-animations-vs-javascript/)
 - [http://davidwalsh.name/css-js-animation](http://davidwalsh.name/css-js-animation)


#### Durchlaufen Sie keine Schleifen unnötig

Wenn Sie eine Aktion auf eine Sammlung von Elementen anwenden wollen, müssen Sie sie nicht unbedingt durchschleifen.

Zum Beispiel bei der Zuweisung einer Klasse, ist das unnötig:

```
$("li").each(function () {
    $(this).addClass("planet");
});
```

Stattdessen können Sie einfach folgenden Ausdruck verwenden:

```
$("li").addClass("planet");
```


#### $el.find();

Wenn Sie JQuery bereits verwendet haben, um eine Element zu finden:

```
var $planetList = $(".planets");
```

Wenn Sie dann ein weiteres Element darin finden wollen, bietet JQuery eine Vielzahl verschiedener Wege an, danach zu suchen. Allerdings ist die einfachste und in der Regel beste Methode `.find()` zu benutzen, um solche Elemente zu finden.

```
var $planets = $planetList.find("li");
```

***Weitere Informationen:***

 - [http://vaughnroyko.com/the-real-scoop-on-jquery-find-performance/](http://vaughnroyko.com/the-real-scoop-on-jquery-find-performance/)


#### Zuständigkeitskette

Gerade weil Sie JQuery Methoden verketten können, bedeutet das nicht, dass Sie es auch immer sollten.

Es gibt hier zwar keine absoluten Regeln, aber achten Sie auf Lesbarkeit des Codes bei der Organisation von Logik.

```
$(this)
    .addClass("done")
    .find("span")
        .addClass("done")
    .end()
    .show("slow", function(){
        $(this).removeClass("done");
    });
```

Versuchen Sie einen Weg zu finden, um eine Logik so knapp wie möglich zu schreiben, ohne dabei die Lesbarkeit zu beeinträchtigen.


### JQuery PROs und CONs:

JQuery ist grossartig. Es ist einfach zu bedienen, gut dokumentiert, und die meisten Entwickler haben zumindest einige Erfahrung, es zu benutzen. Es behandelt eine Reihe von seltsamen Browser-Macken und macht in der Regel das Leben eines Entwicklers einfacher.

Darüber hinaus gibt es eine Menge von Plugins zur Verfügung, um die Durchführung von gemeinsamen Funktionalitätsanforderungen, ohne dass man eine Menge von benutzerdefinierten Code schreiben muss.

Aber JQuery ist nicht immer die richtige Wahl für jede Situation.

Menschen lernen JQuery oft, bevor sie JavaScript verwenden lernen. Als solches kann es schwierig sein zu wissen, wie man aus dem Web heruntergeladene Skripte verändert.

JQuery UI ist insbesondere eine grosse Bibliothek, während kleinere Alternativen existieren, die möglicherweise den gleichen Job zu einem Bruchteil der Dateigrösse machen könnten.

Bei der Entscheidung über die beste Lösung, betrachten Sie Alternativen, wie bspw. die Verwendung von kleineren Bibliotheken.

***Weitere Informationen***

 - [http://lea.verou.me/2015/04/jquery-considered-harmful/](http://lea.verou.me/2015/04/jquery-considered-harmful/)
 - [http://youmightnotneedjquery.com/](http://youmightnotneedjquery.com/)
 - [https://gist.github.com/rwaldron/8720084#file-reasons-md](https://gist.github.com/rwaldron/8720084#file-reasons-md)
 - [https://etherpad.mozilla.org/jquery-browser-bug-analysis](https://etherpad.mozilla.org/jquery-browser-bug-analysis)
 - [http://blog.romanliutikov.com/post/63383858003/how-to-forget-about-jquery-and-start-using-native](http://blog.romanliutikov.com/post/63383858003/how-to-forget-about-jquery-and-start-using-native)
 - [http://microjs.com/](http://microjs.com/)


## JavaScript Tipps

Einige Tipps, die allgemeine JavaScript-Funktionen (und Macken) abdecken.

### Variablen deklarieren

Deklarieren Sie Variablen immer mit dem `var` Schlüsselwort bevor Sie sie zum ersten Mal verwenden.

Obwohl es nicht zwingend ist, bevorzugen viele Entwickler ihre Variablen am Anfang eines Codeblocks zu definieren:

```
function flyToMars () {

    var home = "Earth";
    var self = this;
    var pi = 3.14;
    var $rocket, $thing, $stuff; // empty for now but will be used later

    ...
}
```

Bleiben Sie konsistent in der Verwendung von `var`, egal ob es einzelne Deklarationen oder eine Verkettung mehrerer Variablen ist:

```
var home = "Earth";
var self = this;
var pi = 3.14;
```

*oder*

```
var home = "Earth",
    self = this,
    pi = 3.14;
```

Es gibt Vorteile für den ersten Ansatz, da es leicht ist, das zweite Beispiel versehentlich kaputt zu machen (z.B. indem ein Komma ein Semikolon vergessen wird).


***Weitere Informationen***

 - [http://benalman.com/news/2012/05/multiple-var-statements-javascript/](http://benalman.com/news/2012/05/multiple-var-statements-javascript/)
 - [http://danhough.com/blog/single-var-pattern-rant/](http://danhough.com/blog/single-var-pattern-rant/)
 - [http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
 - [http://james.padolsey.com/javascript/js-adolescence/](http://james.padolsey.com/javascript/js-adolescence/)


### Nameskonventionen

Wählen Sie eine Namenskonvention für Variablen und Funktionen und bleiben Sie dabei.

Es gibt einige ziemlich häufige Namenskonventionen für JavaScript:

  - `camelCase` für Funktionen, Variablen und Objekte.
  - `PascalCase` für Konstrukteure und Klassen.

Wenn Sie diese Namenskonvention verwenden, verwenden Sie keine Unterstriche in Variablennamen.

Verwenden Sie beschreibende Namen anstelle von Kurznamen, wo möglich - schreiben Sie Code, der auch zukünftig noch lesbar ist und überlassen Sie die Optimierung einem Minifier.

Bei der Benennung von Funktionen verwenden Sie *Verben*, um die Art der Funktion zu beschreiben:

```
flyRocketShip();
fireBoosters();
returnToEarth();
eatBiscuit();
```

### "use strict"

Am Anfang einer Funktion sollten Sie das `"use strict"` Statement hinzufügen:

```
function flyToMars () {

    "use strict";

    ...

}
```

Damit wird der JavaScript-Interpreter für die Dauer dieser Funktion (dem aktuellen *Scope*) in einen *strikten* Kontext gestellt.

Dies ändert die Natur von einigen JavaScript-Fehlern, die sonst schweigend ausfallen würden - stattdessen verursachen sie jetzt Ausnahmen. Dies ist eine gute Sache, denn Sie wollen potenzielle Fehler finden und beheben, anstatt sie unbemerkt zu lassen.

Zum Beispiel, stellt der Strict-Mode sicher, dass Sie eine Variable mit `var` deklarieren müssen, bevor Sie sie verwenden können.

Es kann auch dazu führen, dass Code (potenziell) schneller läuft (marginal) als nicht-strikter Code.

***Weitere Informationen:***

 - [http://ejohn.org/blog/ecmascript-5-strict-mode-json-and-more/](http://ejohn.org/blog/ecmascript-5-strict-mode-json-and-more/)
 - [http://www.nczonline.net/blog/2012/03/13/its-time-to-start-using-javascript-strict-mode/](http://www.nczonline.net/blog/2012/03/13/its-time-to-start-using-javascript-strict-mode/)


### Primitive Typen

Variablen können einfache Stücke von Informationen wie Texte (*Strings*) und Zahlen speichern:

 - String: `"hello"`
 - Boolean: `true`
 - Zahlen: `3.14`

Beim Erstellen einer Variablen, die einer dieser (primitiven) Typen ist, ist die neue Variable eine ***Kopie*** des Originals. Das Ändern der neuen Variablen belässt das Original unverändert:

```
var myPlanet = "Earth";
var yourPlanet = myPlanet;
yourPlanet = "Venus";

// myPlanet === "Earth", yourPlanet === "Venus"
```


### Objekttypen

Variablen können auch komplexere Informationen speichern.

**Arrays:**

```
var planets = [
    "Earth",
    "Mars"
]
```

**Objekte:**

```
var earth = {
    "weather": "not bad"
}
```

**Funktionen:**

```
function flyToVenus () {
    ...
}
```

Wenn Sie eine neue Variable erstellen, indem Sie ihren Wert einer vorhandenen Variablen zuordnen, die einer dieser komplexen Typen ist, wird es ***die ursprüngliche Variable*** referenzieren, anstatt sie zu kopieren. Daher ändert jede Änderung der neuen Variablen *auch* die ursprüngliche Version:

```
var myPlanet = {
    "name": "Earth",
    "atmosphere": "Air",
    "water": "wet"
};

var yourPlanet = myPlanet;
yourPlanet["atmosphere"] = "Not air";

// myPlanet.atmosphere === "Not air"
```

***Weitere Informationen***

 - [http://snook.ca/archives/javascript/javascript_pass](http://snook.ca/archives/javascript/javascript_pass)


#### Verwenden Sie benannte Funktionen, nicht anonyme Funktionen

In JavaScript sieht man häufig anonyme Funktionen. Wie der Name (ironisch) vorschlägt, sind sie Funktionen ohne Namen:

```
function () {
    ...
}
```

Sie werden niemals auf eigene Faust benutzt, wie zum Beispiel im Codeblock. Stattdessen werden sie als Teil einer anderen Funktion verwendet. Ein häufiges Auftreten bei der Verwendung von JQuery ist die Verwendung einer anonymen Funktion wie folgt:

```
$("a").click(function () { ... });
$(document).ready(function () { ... });
```

Dies könnte leicht umgeschrieben werden, um eine benannte Funktion zu verwenden:

```
function doSomethingWhenClicked () { ... }
$("a").click(doSomethingWhenClicked);

function init () { ... }
$(document).ready(init);
```

Anonyme Funktionen werden häufig verwendet, wenn man *einige Befehle, die für einen bestimmten Zweck verwendet werden sollen,* verkapseln kann, aber es unwahrscheinlich ist, dass dieses Stück Code anderweitig wieder verwendet wird.

Anonyme Funktionen sind schwer zu debuggen und können nicht wiederverwendet werden. Ein besserer Ansatz ist, sie niemals zu benutzen und stattdessen immer wieder Funktionen zu nennen und zu benennen.


***Weitere Informationen:***

 - [http://toddmotto.com/avoiding-anonymous-javascript-functions/](http://toddmotto.com/avoiding-anonymous-javascript-functions/)
 - [http://learn.jquery.com/code-organization/beware-anonymous-functions/](http://learn.jquery.com/code-organization/beware-anonymous-functions/)


### Wahr und unwahr

Einige Bedingungen geben einen Wert zurück, der ein *boolean* `true` oder` false` ist:

```
var $firstPlanet = $(".planet").first();
var isMercury = ($el.text() === "Mercury"); // true
```

Andere Bedingungen werden einen Wert zurückgeben, der nicht streng `true` oder `false` ist, sondern als *true* oder *false* behandelt werden kann:

```
var $planets = $(".planets");
if ($planets.length) {
    flyCloser();
} else {
    flyToNextStar();
}
```

In diesem Szenario wird `$planets.length` weder `true`, noch `false` sein. Stattdessen hat es den numerischen Wert `0` oder höher. Wenn sein Wert `0` ist, ist das *false*, während wenn der Wert grösser als `0` ist, gilt es als *true*.

Ein weiteres Beispiel, ob ein Eingabefeld einen beliebigen Text enthält:

```
var $name = $("input#name");
if (!$name.val()) {
    alert("Don't forget to add your name!");
}
```

Beachten Sie das `!` vor `$name.val()` - das kehrt die Bedingung um (und verwandelt es in Boolean), um einen negativen Wert anstatt positiv zu prüfen - ob das Textfeld leer ist und daher *false*. In dieser Situation ist es sinnvoll, `!` zu verwenden, weil wir nur die Funktionalität hinzufügen wollen, wenn es leer ist, und so spart man sich eine leere `if`-Anweisung und einen zusätzlichen `else`-Block zu schreiben.

Manchmal sieht man `!!` vor einer Bedingung. Dies verwandelt einen `true` oder `false` Wert in ein echtes boolesches `true` oder `false`, aber im Gegensatz zu einem einzigen Ausrufezeichen wechselt es nicht umgekehrt seinen Zustand.

```
var $name = $("input#name");
if (!!$name.val()) {
    alert("Well done for having a name!");
} else {
    alert("You probably should have a name...");
}
```

Das folgende wird einen *false* Wert zurückgeben:

 - `false`
 - `0`
 - `""`
 - `null`
 - `undefined`
 - `NaN`

Alles andere wird einen *true* Wert zurückgeben.

Seien Sie sich jedoch bewusst, dass `true` und `false` Werte zu Fehlern führen können - zum Beispiel, wenn Sie durch ein Array schleifen, wird der erste Index 0 sein, der als *false* behandelt wird.

***Weitere Informationen:***

 - [http://www.sitepoint.com/javascript-truthy-falsy/](http://www.sitepoint.com/javascript-truthy-falsy/)
 - [http://james.padolsey.com/javascript/truthy-falsey/](http://james.padolsey.com/javascript/truthy-falsey/)


### Strikte Komparatoren (===)

Strenge Komparatoren überprüfen den * Typ * einer Variablen zusammen mit ihrem Wert.

Wenn Sie `==` (oder `!=`) verwenden, können Sie Probleme mit dem testen von `null`-Werten, Verwechselung von Zahlen und Strings sowie Verwechselung von `0` mit dem Boolean `false` feststellen.

```
"1" == 1;  // true
"2" != 2;  // false
```

Stattdessen sollten Sie `===` (oder `!==`) benutzen, um sowohl den Wert, als auch den Typ ztu prüfen:

```
"1" === 1; // false
"2" !== 2  // true
```

Im Allgemeinen ist es eine gute Praxis, immer einen strengen Komparator zu benutzen.

Unerwartete Fehler können oft auftreten, wenn Formulareingaben gegen erwartete Werte getestet werden. Es kann notwendig sein, Zahlen in Strings (oder umgekehrt) umzuwandeln. Eine einfache Möglichkeit das zu testen ist zu schauen, was für einen *Typ* ein Wert hat.

```
// assume the user has entered '10' into this text field
var $age = $("input#age");
var age = $age.val();

typeof age // "string"
age == 10  // true
age === 10 // false

age = parseInt(age, 10); // convert to number
typeof age // "number"
age == 10  // true
age === 10 // true
```

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)
 - [http://www.2ality.com/2011/06/javascript-equality.html](http://www.2ality.com/2011/06/javascript-equality.html)


### Syntax

#### Geschweifte Klammern

Beim Schreiben von Blöcken wie `if`-Anweisungen und `for`-Loops ist es technisch nicht zwingend erforderlich, geschweifte Klammern hinzuzufügen, da folgende Aussage angenommen werden kann:

```
// works as expected
if (isEarth)
    landRocket();
```

Allerdings ist es gute Praxis, immer geschweifte Klammern zu verwenden. Es ist einfach, Bedingungen zu einer `if`-Anweisung zu einem späteren Zeitpunkt hinzuzufügen. Aber es ist mitunter nicht so leicht zu merken, dass es keine geschweiften Klammern gab:

```
if (isEarth)
    landRocket();    // controlled by the if statement
    takeOffHelmet(); // not bound to the if statement, will always happen!
```


#### Tabs vs. Leerzeichen

Entscheiden Sie sich  für Tabs oder Leerzeichen, aber mischen Sie nicht. Zum schnellen Einrücken empfehlen sich Tabs. Also sollten Sie diese auch möglichst verwenden.


#### Anführungszeichen

Entscheiden Sie sich für einfache Anführungszeichen oder für doppelte, aber mischen Sie nicht. Einfache Anführungszeichen (single quotes) erhöhen die Lesbarkeit, wenn sie häufig verwendet werden.


#### Kommas und Semikolons

Entscheiden Sie sich wo Sie Kommas setzen. am Ende eines Items oder am Anfang eines neuen Items.

```
var innerPlanets = [
      "Mercury"
    , "Venus"
    , "Earth"
    , "Mars"
];
```

oder

```
var outerPlanets = [
    "Jupiter",
    "Saturn",
    "Uranus",
    "Neptune"
];
```

Benutzen Sie keine zusätzliches Komma am Ende einer Liste, weil das Fehler in älteren Browsern verursachen kann:

```
// Don't do this
var planets = [
    "Uranus",
    "Neptune",
];
```

Entscheiden Sie, ob am Ende der Zeile ein Semikolon notwendig ist.

***Weitere Informationen:***

 - [http://benalman.com/news/2013/01/advice-javascript-semicolon-haters/](http://benalman.com/news/2013/01/advice-javascript-semicolon-haters/)
 - [http://www.codecademy.com/blog/78-your-guide-to-semicolons-in-javascript](http://www.codecademy.com/blog/78-your-guide-to-semicolons-in-javascript)


### Debugmeldungen loggen

Anstatt `console.log`-Meldungen in einer Anwendung zu hinterlassen oder sie zur Entwicklung da lassen, aber manuell zu entfernen, wenn der Code "vollständig" ist, können Sie eine einfache Debugging-Bibliothek verwenden, die man anstelle von `console.log` anruft. Dies ermöglicht Ihnen, Debug-Nachrichten in Ihrem Code zu lassen, die global mit einer einzigen Konfigurationsoption ein- und ausgeschaltet werden können.

```
// log messages like so:
debug.log("Log message");
debug.warn("Warning message");

// set the level of messages to display
debug.setLevel(0);
```

Client-seitige Fehler abzufangen kann fundamental sein, um sicherzustellen, dass eine Applikation auch wie erwartet funktioniert. Daher werfen Sie einen Blick auf [JSLogger](http://jslogger.com/).

***Weitere Informationen:***

 - [http://benalman.com/projects/javascript-debug-console-log/](http://benalman.com/projects/javascript-debug-console-log/)
 - [http://jslogger.com/](http://jslogger.com/)


### Async und Defer

Wenn ein Browser in einem HTML-Dokument ein `<script>`-Tag findet, hört er standardmässig auf, den HTML-Code zu parsen, bis die *script* -Datei heruntergeladen und analysiert wurde.

Aus diesem Grund war die Konvention, dass `<script>` Elemente in HTML-Seiten am unteren Rand der Seite, kurz vor dem Schliessen `</body>` Tags hinzugefügt werden, so dass sie nach dem Rest gelesen werden, wenn das HTML wurde bereits geparst wurde.

Es gibt Möglichkeiten, dieses Verhalten zu ändern, indem Sie dem Skript-Tag Attribute wie `async` oder `defer` geben.

```
<script src="venus.js"></script>
<script async src="earth.js"></script>
<script defer src="mars.js"></script>
```


#### Async

Asynchrones Skripte halten das Herunterladen des HTML-Dokuments nicht an. Sie werden sobald wie möglich ausgeführt. Während dessen pausieren Sie das Parsen des HTML-Dokuments. Zudem werden sie in der der Reihenfolge ausgeführt, in der das Herunterladen abgeschlossen wurde.


#### Defer

Skripte mit Defer-Attribut werden parallel zu dem HTML-Dokument heruntergeladen, aber ihre Ausführung wird verzögert, bis das HTML-Parsing abgeschlossen ist. Sie werden in der Reihenfolge ausgeführt, in der sie im Dokument erscheinen.

Ältere Versionen von Internet Explorer haben schlechte/keine Unterstützung für das Defer-Attribut.


***Weitere Informationen:***

 - [http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html](http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)


### js- Klassennamen für JS Hooks

Wenn Sie ein HTML Element haben, dass Sie mit JavaScript manipulieren wollen, geben Sie ihm einen Klassennamen (oder ein Data-Attribut), der mit `js-` beginnt. Das macht die Unterscheidung zwischen Klassen für Style und Klassen für JavaScript einfacher.

***Weitere Informationen:***

 - [http://philipwalton.com/articles/decoupling-html-css-and-javascript/](http://philipwalton.com/articles/decoupling-html-css-and-javascript/)
 - [http://davidwalsh.name/css-do](http://davidwalsh.name/css-do)


### Ternäre Operatoren

Ternäre Operatoren sind ein schneller Weg, um mit einer if/else Anweisung einen einzelnen Wert zu setzen:

```
if (planet === "Earth") {
    var dinner = "chips";
} else {
    var dinner = "salad";
}
```

Kann auch so geschrieben werden:

```
var dinner = (planet === "Earth") ? "chips" : "salad";
```

Betrachten Sie die Kürze vs. Lesbarkeit bei der Prüfung, wenn Sie ternäre Operatoren verwenden.

***Weitere Informationen:***

 - [http://davidwalsh.name/learning-ternary-operators-tips-tricks](http://davidwalsh.name/learning-ternary-operators-tips-tricks)


### 0.1 + 0.2

Hüten Sie sich vor JavaScripts sonderbaren Macken:

```
0.1 + 0.2 // ...
0.1 + 0.2 === 0.3 // ...
```

Dies tritt in der Regel nicht auf, aber es kann Probleme verursachen.

***Weitere Informationen:***

 - [http://stackoverflow.com/a/588014](http://stackoverflow.com/a/588014)


### Übergeben von Objekten an Funktionen

Beim Erstellen einer Funktion, wenn Sie mehr als ein paar Argumente erwarten, überlegen Sie, ein einzelnes Objekt anstatt viele Argumente zu übergeben.

Es gibt ein paar Vorteile für diesen Ansatz:

  1. Die Reihenfolge der Argumente spielt keine Rolle
  2. Die Parameter sind benannt und so leichter zu verweisen
  3. Wenn einige der Argumente optional sind, wird automatisch `null` für solche Argumente in die Funktion übergeben

```
// function usage
modelSolarSystem({
    star: "The Sun",
    planets: ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
});

// function definition
function modelSolarSystem (data) {
    var star = data.star;
    data.planets.forEach(create);
    ...
}
```

***Weitere Informationen:***

 - [http://rmurphey.com/blog/2011/04/25/objects-as-arguments/](http://rmurphey.com/blog/2011/04/25/objects-as-arguments/)


### Verbessern Sie mit JavaScript, verlassen Sie sich nicht darauf

Anstatt Funktionalität zu haben, die nicht benutzt wird, wenn JavaScript nicht vorhanden ist, versuchen Sie lieber sicherzustellen, dass der ursprünglich generierte Seiteninhalt für Personen, die JavaScript deaktiviert haben, benutzbar ist:

```
<p class="js-relative-date">14th June 2015</a>
```

Dann mit JavaScript können Sie für diejenigen, die es aktiviert haben, diese Elemente erkennen und die Funktionalität verbessern:

```
var $relativeDates = $(".js-relative-date");
makeDatesRelative($relativeDates);
```

***Weitere Informationen:***

 - [https://www.gov.uk/service-manual/making-software/progressive-enhancement.html](https://www.gov.uk/service-manual/making-software/progressive-enhancement.html)
 - [http://alistapart.com/article/understandingprogressiveenhancement](http://alistapart.com/article/understandingprogressiveenhancement)


## JavaScript Style-Guide

Es gibt viele Möglichkeiten, JavaScript zu schreiben. Das Festhalten an den Regeln, die in einem _style guide_ (oder _coding standards_ Dokument) angelegt sind, bedeutet, dass Sie Code konsequent über ein Team hinaus schreiben können.

Das Ziel sollte nicht nur sein, die Arbeit zu erledigen, sondern logisch wartbaren Code zu schreiben.

(Als Referenz gibt es beliebte [CSS] (http://cssguidelin.es/) und [SASS] (http://sass-guidelin.es/) Äquivalente.)

Es gibt keinen Grund, eigene Codierungsstandards zu schreiben, wenn andere die harte Arbeit für Sie bereits getan haben.

Eine nützliche Zusammenfassung, warum es sich lohnt, einen JavaScript-Style-Guide zu verwenden:

  - [http://addyosmani.com/blog/javascript-style-guides-und-beautifiers/](http://addyosmani.com/blog/javascript-style-guides-and-beautifiers/)

Einige JavaScript-Style-Guides:

 - [https://github.com/rwaldron/idiomatic.js](https://github.com/rwaldron/idiomatic.js)
 - [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
 - [http://seravo.fi/2013/javascript-the-winning-style](http://seravo.fi/2013/javascript-the-winning-style)
 - [http://www.2ality.com/2013/07/meta-style-guide.html](http://www.2ality.com/2013/07/meta-style-guide.html)


## Ajax

Ajax ist der Begriff, der üblicherweise verwendet wird, um die Technik zum Ausführen eines _HTTP Requests_ mit JavaScript zu beschreiben, um Inhalte von einem Server (oder einer anderen Datenquelle von Drittanbietern) abzurufen, ohne die aktuelle Seite aktualisieren zu müssen.

Viele JavaScript-Bibliotheken wie JQuery bieten die Möglichkeit, Ajax-Anfragen zu machen.

Ajax kann die HTTP-Methoden *GET* und *POST* verwenden, um mit Servern zu interagieren. Beide *GET* und *POST* können verwendet werden, um Daten zu senden und zu empfangen, aber sie haben ihre Unterschiede, die jedes für verschiedene Szenarien geeignet machen.


### GET Requests

Ein Ajax *GET*-Request wird im Allgemeinen verwendet, um Informationen von einem Server abzurufen. Um ein Beispiel mit JQuery zu geben:

```
$.get("/api/planets/");
```

Dies fragt die URL *http://[domain]/api/planets/* ab.

Es ist möglich, mit dem Request auch Parameter an den Server zu übergeben:

```
$.get("/api/planets/", { planet: "Earth"});
```

JQuery konvertiert den zweiten Parameter in einen Abfrage-String und transformiert die angeforderte URL in: *http://[Domain]/api/planets/?planet=Earth*

In den beiden obigen Beispielen können die Daten vom Server angefordert worden sein, aber es geschieht nichts, wenn diese Daten empfangen werden. Es ist notwendig zu definieren, was getan werden soll, sobald Daten zurückgegeben wurden, oder wenn es einen Fehler gab.

```
$.get("/api/planets/", { planet: "Earth"})
    .done(function () {
        // this function will be called if
        // the request completes successfully
    })
    .fail(function () {
        // this function will be called if
        // there was an error with the request
    })
    .always(function () {
        // this function will always be called
    });
```

Wie bereits erwähnt, ist es möglich (und empfohlen), diese Funktionen separat zu definieren, anstatt anonyme Funktionen zu verwenden.

```
function done () { ... }
function fail () { ... }
function always () { ... }

$.get("/api/planets/", { planet: "Earth"})
    .done(done)
    .fail(fail)
    .always(always);
```

***Weitere Informationen:***

- [https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)
- [https://api.jquery.com/jquery.get/](https://api.jquery.com/jquery.get/)
- [http://visionmedia.github.io/superagent/](http://visionmedia.github.io/superagent/)


### POST Requests

Beim Senden von Informationen an einen Server sollten *POST*-Requests verwendet werden. Sie beschränken nicht die Datenmenge, die an den Server gesendet werden kann, wie bei einem *GET*-Request, und sie können auch zum Hochladen von Dateien verwendet werden.

Mit *POST*-Requests kommt die Information, die an den Server gesendet wird, oft aus Formulareingaben.

Mit JQuery können *POST*-Requests in ähnlicher Weise gemacht werden:

```
function done () { ... }
function fail () { ... }
function always () { ... }

$.post("/api/planets/", { planet: "Earth"})
    .done(done)
    .fail(fail)
    .always(always);

```

***Weitere Informationen:***

- [https://api.jquery.com/jquery.post/](https://api.jquery.com/jquery.post/)
- [http://www.sitepoint.com/key-differences-post/](http://www.sitepoint.com/key-differences-post/)


### Cross-domain Requests

Die beiden obigen Beispiele gehen davon aus, dass der Server, der die Daten bereitstellt, derselbe Server ist, auf dem die Website liegt. Es gibt zwei Möglichkeiten, mit einem anderen Webserver zu interagieren. Dies ist nützlich, wenn es um APIs geht, die von anderen Diensten bereitgestellt werden.


#### CORS

Wenn Sie versuchen, auf einen anderen Server über JavaScript zuzugreifen, können aufgrund einer *Sicherheitsrichtlinie* Fehler in der Konsole angezeigt werden, es sei denn, der Host-Server hat *Cross-Origin Ressource Sharing* (CORS) aktiviert. Obwohl es nicht schwer zu aktivieren ist, gibt es Sicherheitsimplikationen, die verstanden und akzeptiert werden müssen, bevor Sie sich für die Unterstützung von CORS entscheiden.

***Weitere Informationen***

 - [http://enable-cors.org/](http://enable-cors.org/)
 - [http://dev.housetrip.com/2014/04/17/unleash-your-ajax-requests-with-cors/](http://dev.housetrip.com/2014/04/17/unleash-your-ajax-requests-with-cors/)


#### JSONP

Eine alternative Option ist, *JSONP* anzufordern, wenn der Host-Server es bereitstellt.

Dies umgeht das *same-origin* Sicherheitsproblem, indem der Host-Server die angeforderten Daten in ein JavaScript-Objekt eingewickelt. Dies wird dann in die ursprüngliche Webseite eingebettet.

Wie immer bietet JQuery eine einfache Möglichkeit, JSONP zu verwenden, was möglicherweise eine einfache Interaktion mit Drittanbieter-APIs ermöglicht.

***Weitere Informationen***

 - [http://www.sitepoint.com/jsonp-examples/](http://www.sitepoint.com/jsonp-examples/)
 - [http://json-p.org/](http://json-p.org/)
 - [https://learn.jquery.com/ajax/working-with-jsonp/](https://learn.jquery.com/ajax/working-with-jsonp/)


## Promises

Bei der Erstellung der Ajax-Anfragen wurden drei Funktionen definiert, um sie zu begleiten:

 - Eine `done` Funktion, die ausgeführt wird, wenn der Ajax-Request erfolgreich war
 - Eine `fail` Funktion, die ausgeführt wird, wenn der Ajax-Request nicht erfolgreich war
 - Eine `always` Funktion, die ausgeführt wird, wenn der Ajax-Request abgeschlossen wurde, unabhängig vom Ergebnis

Eine alternative Methode zum Auslösen einer Funktion, wenn die Ajax-Anforderung abgeschlossen ist, ist ein *Promise* zu verwenden.

Das Erstellen eines *Promise* ist einfach, mit ähnlicher Syntax zu dem, was bereits gezeigt wurde:

```
function done () { ... }
function fail () { ... }
function always () { ... }

var request = $.post("/api/planets/", { planet: "Earth"});

request.done(done);
request.fail(fail);
request.always(always);
```

Der Unterschied hierbei ist, dass die Ajax-POST-Anfrage in einer Variablen namens `request` gespeichert wurde, die dann verwendet wird, um zu definieren, was mit dem Ergebnis der Ajax-Anfrage geschehen soll.

Der Vorteil der Verwendung eines *Promise* ist die Fähigkeit, eine Anzahl von Funktionen zu verknüpfen, die asynchron auftreten, wobei spätere Funktionen ausgelöst werden, sobald frühere Funktionen erfolgreich abgeschlossen sind.

***Weitere Informationen:***

 - [https://api.jquery.com/promise/](https://api.jquery.com/promise/)
 - [https://www.promisejs.org/](https://www.promisejs.org/)
 - [http://www.html5rocks.com/en/tutorials/es6/promises/](http://www.html5rocks.com/en/tutorials/es6/promises/)
 - [http://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html](http://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html)


## Callbacks

Eine Anzahl der oben dargestellten Beispiele ist möglich, weil JavaScript Funktionen als Argumente an andere Funktionen übergeben kann.

Dies nennt man *Callback*.

```
function init () {
    // define the callback
}

// run the callback on DOM load
$(document).ready(init);
```

Callbacks nutzen die *asynchrone* Natur von JavaScript, die die Möglichkeit bietet, Befehle zum richtigen Zeitpunkt auszuführen. Das obige Beispiel zeigt, dass die *init*-Funktion aufgerufen wird, wenn das DOM das Laden beendet hat.

Weitere Beispiele für Rückrufe werden in den folgenden Abschnitten gezeigt.

***Weitere Informationen***

 - [https://gist.github.com/infovore/b6c4bc71a1bffdfd9846](https://gist.github.com/infovore/b6c4bc71a1bffdfd9846)
 - [http://stackoverflow.com/questions/9596276/how-to-explain-callbacks-in-plain-english-how-are-they-different-from-calling-o](http://stackoverflow.com/questions/9596276/how-to-explain-callbacks-in-plain-english-how-are-they-different-from-calling-o)


## Timeouts

Eine der häufigsten Verwendungen eines Callbacks ist, eine Funktion nach einer festgelegten Zeitspanne auszulösen, anstatt sofort.

Manchmal will man jetzt nichts machen, aber später soll etwas passieren.

```
function doSomethingInTheFuture () {
    alert("It is now the future, here's your jet pack");
}

var timeout = setTimeout(doSomethingInTheFuture, 5000); // 5 seconds
```

Dieser Timeout wird einmal ausgeführt, 5 Sekunden ab dem Zeitpunkt der Zeitüberschreitung.

Es ist auch möglich, eine Funktion wiederholt in einem eingestellten Intervall auszulösen:

```
function doSomethingContinuously () {
    alert("Is this annoying yet?");
}

var interval = setInterval(doSomethingContinuously, 10000); // every 10 seconds
```

Ein praktischer Nutzen für Timeouts und Intervalle könnte sein, eine Ajax-Anfrage durchzuführen, um nach neuen Inhalten alle paar Sekunden zu suchen.

Timeouts und Intervalle können abgebrochen werden:

```
clearTimeout(timeout);
clearInterval(interval);
```

Von den beiden gibt es Nachteile bei der Verwendung von Intervallen. Insbesondere wenn sie in einem inaktiven Browser-Tab laufen, kommen sie in die Warteschlange, was bedeutet, dass die Callback-Funktion mehrfach aufgerufen wird (die Warteschlange wird abgearbeitet), wenn der Benutzer endlich wieder den inaktiven Tab aufgerufen hat. Aus diesem Grund wird normalerweise empfohlen, Timeouts anstatt Intervallen zu verwenden.

***Weitere Informationen***

 - [http://ejohn.org/blog/how-javascript-timers-work/](http://ejohn.org/blog/how-javascript-timers-work/)
 - [http://stackoverflow.com/q/6183463](http://stackoverflow.com/q/6183463)


## Events

Eine weitere gebräuchliche Anwendung von Callbacks sind *events*.

Ein Ereignis kann auf folgende Weise gedacht werden:

> *Wenn dies passiert, mach das*

Die häufigste Verwendung von Events hört auf Interaktionen mit DOM-Elementen, wie z.B. einen Klick auf einen bestimmten Link oder die Einreichung eines Formulars.

Das folgende Beispiel veranschaulicht, wie man JQuery verwendet, um einen *Event-Listener* einem DOM-Element hinzuzufügen. Es löst eine *Callback*-Funktion aus, wenn der Link geklickt wird:

```
function linkClicked () {
    alert("The link was clicked!");
}

$(".js-my-link").on("click", linkClicked);
```

Es ist möglich, Event-Listener ohne Verwendung von JQuery hinzuzufügen, aber bestimmte ältere Browser verwenden etwas unterschiedliche Syntax, und erspart man sich mit einer Bibliothek, dass man die gleiche Funktion auf zwei leicht unterschiedliche Weisen definieren muss.

Im obigen Beispiel hat das DOM-Element ein `class`-Attribut, das mit `js-`beginnt - wie oben diskutiert wurde, ist dies eine nützliche Konvention, die es uns ermöglicht, zwischen CSS-Klassen zu unterscheiden, die für das Styling verwendet werden und diejenigen, die sind Für JavaScript verwendet.

Obwohl Ereignisse auf fast jedem HTML-Element platziert werden können, ist es für Zugänglichkeitszwecke vorteilhaft, sie auf `<a>` Elemente zu setzen und Eingabesteuerungen zu bilden, da dies eine einfachere Tastaturnavigation ermöglicht.

***Weitere Informationen:***

 - [http://eloquentjavascript.net/14_event.html](http://eloquentjavascript.net/14_event.html)
 - [http://www.kirupa.com/html5/javascript_events.htm](http://www.kirupa.com/html5/javascript_events.htm)


### Standard-Events verhindern

Beim Hinzufügen von benutzerdefinierten Ereignissen können wir manchmal den ursprünglichen Link von der Ausführung der Standardaktion abhalten.

Zum Beispiel können wir einen Link haben, mit dem wir eine bestimmte Funktionalität auslösen wollen, aber für Benutzer ohne JavaScript, die auf denselben Link klicken, würde die gesamte Seite aktualisiert.

Wenn ein Ereignis ausgelöst wurde, ist standardmässig ein `event`-Objekt verfügbar, das an die Callback-Funktion übergeben werden soll.

Die Methode, dieses Standardverhalten zu verhindern, ist:

```
$(".js-my-link").on("click", function (e) {
    e.preventDefault();
});
```

***Weitere Informationen***

 - [https://css-tricks.com/return-false-and-prevent-default/](https://css-tricks.com/return-false-and-prevent-default/)
 - [https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault](https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault)


## Closures

Ein Closure wird gebildet, wenn eine *verschachtelte* Funktion ausserhalb der Funktion, in der sie definiert wurde, zugänglich gemacht wird, so dass sie ausgeführt werden kann, nachdem die äussere Funktion zurückgegeben wurde. Man behält den Zugriff auf die lokalen Variablen, Argumente und inneren Funktionsdeklarationen seiner äusseren Funktion.

```
var myPlanet = (function () {
    var atmosphere = "Air";
    return function() {
        // We have access to *atmosphere*
        // because it is defined in the same scope as this function
        alert(atmosphere);
    };
})();
```

Ein übliches Beispiel für eine Closure ist das Modulmuster, wie nachstehend gezeigt. Dies gibt ein einfaches Objekt zurück, das Verweise auf Methoden enthält, die in der übergeordneten Funktion definiert sind.

Closures sind eine nützliche Methode, um komplexe Funktionalität zu schaffen und gleichzeitig den Umfang zu schützen.

***Weitere Informationen***

 - [https://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/](https://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/)


## Objektliterale

Wie oben gezeigt wurde, sind Objekte eine nützliche Methode, um verwandte Informationen zusammen in einer einzigen Variablen zu speichern.

```
var planet = {
    name: "mars",
    radius: 3396,
    distanceFromSun: 227900000
};
```


### Funktionen in Objekten

Objekte sind für mehr als nur das Sammeln von Daten nützlich, da sie auch Funktionen enthalten können.

```
var planet = {
    name: "mars",
    radius: 3396,
    distanceFromSun: 227900000,
    getName: function () {
        return this.name;
    },
    revolve: function () {
        ...
    }
};
```

Funktionen innerhalb von Objekten werden oft als ***Methoden*** bezeichnet, und Variablen innerhalb von Objekten werden oft als ***Eigenschaften*** bezeichnet.

Um die Methode eines Objekts aufzurufen, verweisen Sie zuerst auf den ursprünglichen Variablennamen, gefolgt von dem Funktionsnamen:

```
var planetName = planet.getName(); // "mars"
```

Das Speichern von verwandten Eigenschaften und Methoden innerhalb eines Objekts kapselt diese verwandten Funktionen in einer einzigen Variablen zusammen.

Es gibt mögliche Probleme mit diesem Ansatz - vor allem, dass es für andere Skripte möglich ist, auf interne Teile eines Objekts zuzugreifen (und zu überschreiben), zum Beispiel in dem oben definierten `planet`-Objekt:

```
planet.name = "earth"; // override previous value
```

Die Verwendung von Objekten als Grundlage für die Speicherung von Variablen und Funktionen ist ein wichtiges Merkmal des Schreibens von wartbaren JavaScript. Es sind komplexere Methoden vorhanden, um zu verhindern, dass Daten in einem Objekt überschrieben werden (ob versehentlich oder absichtlich). Diese werden in den folgenden Abschnitten besprochen.

***Weitere Informationen***

 - [http://www.sitepoint.com/back-to-basics-javascript-object-syntax/](http://www.sitepoint.com/back-to-basics-javascript-object-syntax/)
 - [http://rmurphey.com/blog/2009/10/15/using-objects-to-organize-your-code/](http://rmurphey.com/blog/2009/10/15/using-objects-to-organize-your-code/)


### *this* Schlüsselwort

In JavaScript ist der Wert der Variablen `this` besonders. Ihr Wert ändert sich je nachdem wo und wie sie verwendet wird.

Wenn Sie beispielsweise auf andere Eigenschaften oder Methoden in einem Objektliteral verweisen, verwenden Sie `this`, um auf andere Teile des Objekts zuzugreifen (oder einzustellen).

```
var planet = {
    name: "mars",
    init: function (name) {
        this.setName(name);
        this.rotate();
    },
    getName: function () {
        return this.name;
    },
    setName: function (newName) {
        this.name = newName;
    },
    rotate: function () {
        ...
    }
};
```

Der Wert von `this` kann sich ändern, wenn er in verschiedenen Kontexten verwendet wird, wie später gezeigt wird.

***Weitere Informationen***

 - [https://gist.github.com/cjohansen/4135065](https://gist.github.com/cjohansen/4135065)
 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)


## Scope

Wenn Sie eine Variable oder eine Funktion erstellen, wird sie standardmässig im *globalen* Scope definiert. Dies bedeutet, dass sie überall im Code verfügbar ist.


### Scope verstehen

Variablen, die im *globalen* Scope erstellt wurden, sind für Funktionen zugänglich, die im gleichen Bereich definiert sind:

```
// this variable is defined in the global scope
var planet = "Earth";

function enthuse () {
    // this is now the local scope, but it has access to variables
    // defined in the global scope

    alert("I like the planet " + planet); // "I like the planet Earth"
}
```

Variablen, die innerhalb der Funktionen definiert sind, sind nur *lokal* in dieser Funktion und nicht ausserhalb verfügbar:

```
function enthuse () {
    var planet = "Earth";
}
alert("I like the planet " + planet); // ERROR: unknown variable *planet*
```


Variablen innerhalb der Funktionen haben Vorrang vor den ausserhalb definierten Variablen:

```
var planet = "Earth";

function enthuse () {
    var planet = "Mars";
    alert("I like the planet " + planet); // "I like the planet Mars"
}
enthuse();
alert("I like the planet " + planet); // "I like the planet Earth"
```


Variablen, die in Funktionen übergeben werden, werden auch Teil des *lokalen* Gültigkeitsbereichs und überschreiben daher die Variable des gleichen Namens, die im globalen Geltungsbereich deklariert wurde:

```
var planet = "Earth";
function enthuse (planet) {
    alert("I like the planet " + planet); // "I like the planet *undefined*"
    planet = "Mars";
    alert("I like the planet " + planet); // "I like the planet Mars"
}
enthuse(); // no planet passed to function
alert("I like the planet " + planet); // "I like the planet Earth"
```

Auch:

```
var planet = "Earth";
function enthuse (planet) {
    alert("I like the planet " + planet); // "I like the planet Venus"
    planet = "Mars";
    alert("I like the planet " + planet); // "I like the planet Mars"
}
enthuse("Venus"); // planet passed to function
alert("I like the planet " + planet); // "I like the planet Earth"
```

***Weitere Informationen:***

 - [http://stackoverflow.com/a/500459](http://stackoverflow.com/a/500459)
 - [http://toddmotto.com/everything-you-wanted-to-know-about-javascript-scope/](http://toddmotto.com/everything-you-wanted-to-know-about-javascript-scope/)


### Probleme mit dem Scope

Die Flexibilität des Scopes kann praktisch sein, aber gleichermassen kann es Probleme verursachen, besonders wenn es nicht berücksichtigt wird.

Das Hauptproblem bei der Arbeit im globalen Geltungsbereich ist, dass es einfach ist, versehentlich eine Variable zu überschreiben, indem man eine andere mit demselben Namen deklariert. JavaScript (in einem Webbrowser) bietet keine Isolierung des Scopes über Dateien, d.h. alle Code-Freigaben nutzen den gleichen globalen Bereich, es sei denn, es werden Anstrengungen unternommen, um Stücke des Codes in separate lokale Bereiche zu isolieren.

Viele Webseiten verwenden ihren eigenen JavaScript-Code zusammen mit Drittanbieter-JavaScript, wie zum Beispiel für das Tracking oder das Einfügen von Werbung in eine Website. Es ist wichtig, dass dieser Drittanbieter-Code isoliert behandelt wird, so dass er kein anderes JavaScript stört.

Der beste Weg, um Probleme mit dem Scope zu vermeiden, besteht darin, alle Codes innerhalb einzelner lokaler Bereiche einzukapseln, so dass nur wenige (wenn überhaupt) Variablen im globalen Geltungsbereich definiert sind, was bedeutet, dass sie nicht miteinander in Konflikt stehen.

Methoden dazu werden in Kürze erörtert.


## Modularität

Beim Aufbau einer grossen und komplexen Website, kann eine erhebliche Menge an JavaScript geschrieben werden, um seine verschiedenen Funktionen der Funktionalität zu kontrollieren. Obwohl bestimmte Aspekte möglicherweise miteinander interagieren müssen, können diese Stücke von Code separat verwaltet werden.

Ohne Versuche, diesen Code zu organisieren, kann es schnell schwierig werden, jede Funktionalität zu verwalten und zu pflegen, ohne versehentlich andere Teile zu beeinträchtigen.

Die Organisation von Code in *modulare Komponenten* bedeutet, dass jeder Teil des Codes getrennt von allen anderen Komponenten gehalten werden kann.

Die Verwendung von modularen Komponenten hilft auch bei der Verwaltung des *Scopes* - jede Komponente kann in ihrem eigenen Umfang und nicht in dem globalen Geltungsbereich definiert werden, wodurch das Potenzial für eine beliebige Variable reduziert wird, um eine andere versehentlich zu überschreiben.

Das Aufteilen von JavaScript in separate Dateien ist ein guter Anfang, um logische Komponenten zu identifizieren. Aber das schützt noch nicht das Scope.

Es gibt eine Reihe von Möglichkeiten, um JavaScript in modularen Komponenten zu organisieren, wie unten diskutiert.


### Namespaces

Eine Methode, um modulare Komponenten zu erstellen, besteht darin, Komponenten in einzelne Objekte zu unterteilen und einen *Namespace* zu definieren, in dem jedes Objekt existiert.

Die folgenden zwei Beispiele zeigen, wie solche Codestücke in einem einzigen Namespace voneinander getrennt sind.

File 1 - *earth.js*:

```
var PLANETS = PLANETS || {};

PLANETS.earth = {
    name: "Earth",
    radius: 6371,
    distanceFromSun: 149600000,
    moons: ["The Moon"],
    init: function () {
        ...
    }
};
```

File 2 - *mars.js*:

```
var PLANETS = PLANETS || {};

PLANETS.mars = {
    name: "Mars",
    radius: 3396,
    distanceFromSun: 227900000,
    moons: ["Phobos", "Deimos"],
    init: function () {
        ...
    }
};
```

Der oben genannte Ansatz bedeutet, dass es nur eine einzige globale Variable gibt, in diesem Fall `PLANETS` genannt. Dies ist unser *Namespace*.

Diese beiden Dateien könnten in beliebiger Reihenfolge aufgenommen werden. Die erste Zeile der beiden vewrweist auf die globale Variable `PLANETS`. Wenn es bereits erstellt wurde, wird es nicht überschrieben. Wenn dies die erste Datei ist, wird ein neues leeres Objekt erstellt.

Innerhalb der beiden obigen Objekte sind alle Variablen sicher und werden nicht gegenseitig überschrieben.

Zu einem späteren Zeitpunkt kann ein anderes Skript auf `PLANETS.mars.init();` oder `PLANETS.earth.init();` oder jede andere Methode oder Eigenschaft, die im Namespace definiert ist, verweisen.

***Weitere Informationen:***

 - [http://elegantcode.com/2011/01/26/basic-javascript-part-8-namespaces/](http://elegantcode.com/2011/01/26/basic-javascript-part-8-namespaces/)


### IIFEs

Eine andere Methode, den globalen Bereich zu vermeiden, besteht darin, Code in eine anonyme Funktion zu schreiben, die sofort ausgeführt wird.

Die Syntax dafür ist:

```
(function () {

    // code goes here...

})();
```

Diese Methode wird als *Immediately Invoked Function Expression* bezeichnet. Der Vorteil der Verwendung eines *IIFE* ist, dass der gesamte Code in einer Funktion gehalten wird, und so seinen eigenen Scope hat, anstatt irgendwelche Variablen oder Funktionen im globalen Bereich.

Die Syntax eines *IIFE* kann in zwei Teilen verstanden werden:

  1. Der erste Teil ist die Definition einer Funktion, die in Klammern umgeben ist, wodurch ein lokaler Bereich erstellt werden kann.
  2. Der zweite Teil ist der zweite Satz von Klammern, der unmittelbar dem ersten folgt, der die Funktion sofort aufruft.

IIFEs sind nützlich, wenn Sie einen Code haben, der sofort ausgeführt werden muss (z.B. bei der Initialisierung), aber dieser Code muss nicht auf irgendetwas anderes auf der Website verweisen oder nach der Einrichtung referenziert werden. Die anonymen Funktion schützt den Code vor dem Rest der Codebasis, während die sofortige Funktionalität sicherstellt, dass sie initialisiert wird, sobald sie erstellt wurde.


#### IIFEs auslagern

Eine Möglichkeit, in der IIFEs Variablen für andere Skripte zur Verfügung stellen können, ist eine externe Variable oder *Kontext* zu übergeben. Im folgenden Beispiel wird der Kontext in der abschliessenden Zeile als das Schlüsselwort `this` (das standardmässig auf das `window`-Objekt, den globalen Geltungsbereich) verweist, weitergegeben. Innerhalb der anonymen Funktion wird dieser Parameter mit dem Argument `context` bezeichnet:

```
(function (context) {
    var planet = "Earth";
    var radius = 6371;
    function setPlanetName () {
        // do something private
    }
    context.myPlanet = {
        radius: radius,
        getPlanetName: function () {
            return planet;
        }
    };

})(this);
```
Diese Methode fügt `window.myPlanet` zum globalen Geltungsbereich hinzu:

```
window.myPlanet.radius           // 6371
window.myPlanet.getPlanetName()  // "Earth"
```

Mit dem obigen Ansatz ist alles, was nicht explizit im `myPlanet` Objekt gesetzt wurde, nicht durch ein externes Skript zugänglich.

***Weitere Informationen***

 - [http://benalman.com/news/2010/11/immediately-invoked-function-expression/](http://benalman.com/news/2010/11/immediately-invoked-function-expression/)
 - [http://esbueno.noahstokes.com/post/77292606977/self-executing-anonymous-functions-or-how-to-write](http://esbueno.noahstokes.com/post/77292606977/self-executing-anonymous-functions-or-how-to-write)


### Revealing Module Pattern

Eine andere Methode, um auf Funktionen und Variablen zuzugreifen, die in einem IIFE erstellt wurden, ist, dass sie einen Wert zurückgibt.

Ein populärer Ansatz ist es, das _Revealing Module Pattern_ zu verwenden, um den Bereich mit einem IIFE zu isolieren und dann ein Objekt von öffentlich zugänglichen Parametern (Variablen) und Methoden (Funktionen) zurückzugeben.

```
var myPlanet = (function () {

    var planet = "Earth";
    var radius = 6371;

    function setPlanetName () {
        // do something private
    }

    function getPlanetName () {
        return planet;
    }

    // publicly available things
    return {
        radius: radius,
        getPlanetName: getPlanetName
    };

})();
```

In diesem Beispiel wurde eine einzige globale Variable von `myPlanet` definiert, während der gesamte Code innerhalb der Funktion seinen eigenen lokalen Bereich hat.

Das Ergebnis ist, dass `myPlanet` die folgenden öffentlich zugänglichen Werte hat:

```
myPlanet.radius           // 6371
myPlanet.getPlanetName()  // "Earth"
```

Mit dem obigen Ansatz ist alles, was nicht explizit zurückgegeben wurde, nicht durch ein externes Skript zugänglich.

***Weitere Informationen***

 - [http://alistapart.com/article/the-design-of-code-organizing-javascript](http://alistapart.com/article/the-design-of-code-organizing-javascript)
 - [http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)


### IIFEs, Module Pattern und Namespaces verbinden

Für grosse Codebasen ist es ein gemeinsamer Ansatz, IIFSs, Module Pattern und Namespaces zu kombinieren, um eine logische Struktur für Ihren Code zu erstellen:

```
var MyApp = MyApp || {};

MyApp.Accordions = (function () {

    var foo = "Foo";
    var bar = "Bar";

    function private () {
        // do something
    }

    function public () {
        // do something
    }

    return {
        foo: foo,
        public: public
    };

})();
```

Der gesamte Code ist in einem einzigen *Namespace* von `MyApp` enthalten, in dem jedes Stück modularer Code seinen eigenen Namen hat, der einen Satz von öffentlichen Parametern und Methoden zurückgibt.

Im obigen Beispiel erstellt es `MyApp.Accordions` im Namespace, also könnte man z.B. `MyApp.Accordions.public()` aufrufen;

Diese Methode wird als Grundlage für viele komplexe Codebasen verwendet.

***Weitere Informationen:***

 - [http://addyosmani.com/resources/essentialjsdesignpatterns/book/](http://addyosmani.com/resources/essentialjsdesignpatterns/book/)


## Constructors und das *new* Schlüsselwort

Eine alternative Möglichkeit, modularen Code zu erstellen, besteht darin, neue Objekte zu *konstruieren*, die als *Prototyp* anderer Objekte verwendet werden können.

Betrachten Sie das folgende Beispiel:

```
function Planet (name, radius) {
    this.name = name;
    this.radius = radius;
}
```

Der Weg, dieses Objekt zu verwenden, besteht darin, eine *Instanz* des `Planet` Objektes zu erstellen:

```
var earth = new Planet("Earth", 6371);
var mars = new Planet("Mars", 3396);
```

Beachten Sie die Verwendung des Schlüsselwortes `new` vor dem Namen der Funktion. Dies ist entscheidend dafür, dass wir eine *Instanz* des `Planet`-Objekts erstellen, anstatt eine Variable zu erstellen, die direkt auf sie verweist.

Um dem `Planet`-Objekt eine Funktion hinzuzufügen, die von beliebigen Instanzen referenziert werden kann, musst man sie dem `Prototyp` hinzufügen:

```
Planet.prototype.revolve = function () {
    ...
};
```

Das Erstellen von Objekten auf diese Weise kann ihre Vorteile haben, insbesondere bei der Erstellung unterschiedlicher Objekttypen, die Eigenschaften und Methoden voneinander erfassen können.

***Weitere Informationen***

 - [http://wildlyinaccurate.com/understanding-javascript-inheritance-and-the-prototype-chain/](http://wildlyinaccurate.com/understanding-javascript-inheritance-and-the-prototype-chain/)
 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)



## App Struktur

Wenn Sie zuerst lernen, JavaScript zu benutzen, kann es verlockend sein, eine einzelne JavaScript-Datei zu erstellen, die jede Funktionalität enthält, die für eine Website benötigt wird. Wie bereits gezeigt wurde, kann dies zu Problemen führen und schwer zu pflegen sein. Stattdessen sollte die Anwendung in Module zerlegt werden, die jeweils mit einer bestimmten Funktionalität umgehen.


### Global Init Location

Bei der Erstellung von modularen Komponenten könnte jede für die Initialisierung und die Kontrolle ihres eigenen Verhaltens verantwortlich gemacht werden.

Dies ist ein akzeptabler Ansatz, wenn jedes Modul vollständig in sich geschlossen ist und keine zwei Module miteinander kommunizieren müssen.

Ein alternativer Ansatz ist es, eine globale `init`-Funktion zu schaffen, die für die Initialisierung aller anderen Module verantwortlich ist:

```
// create namespace
var MyApp = {};

// set up all tab functionality
MyApp.tabs = (function () {
    function init () {
        console.log("tabs init");
    }
    return {
        init: init
    };
})();

// set up all slideshow functionality
MyApp.slideshows = (function () {
    function init () {
        console.log("slideshows init");
    }
    return {
        init: init
    };
})();

// start all functionality
MyApp.init = function () {
    var tabs = MyApp.tabs.init();
    var slideshows = MyApp.slideshows.init();
};

// run on DOM load
$(document).ready(MyApp.init);
```

Der Vorteil der Verwendung eines einzigen Standortes, um alles zu initialisieren ist, dass man einen *Mediator* erstellt, der die verschiedenen Komponenten der Applikation kennt und bei Bedarf Interaktion und Kommunikation verarbeiten kann.

***Weitere Informationen***

 - [https://css-tricks.com/how-do-you-structure-javascript-the-module-pattern-edition/](https://css-tricks.com/how-do-you-structure-javascript-the-module-pattern-edition/)


### Kommunikation zwischen Modulen

Die Kommunikation zwischen den Modulen ist möglich, indem man ihre öffentlichen Methoden direkt aus einer anderen Funktion verweist.

Betrachten Sie das folgende vereinfachte Beispiel für zwei Module:

```
MyApp.tabs = function () {
    $(".tab").on("click", MyApp.slideshows.init);
}

MyApp.slideshows = function () {
    function init (selectedTab) {
        // do something with the selected tab
    }
}
```

Zwei Module, die direkt kommunizieren, sind bekannt als *tight coupling* und keine gute Idee. Grundsätzlich sollten Module niemals einander kennen oder sich direkt anrufen. Stattdessen können wir eine alternative Methode verwenden, um diese Kommunikation  auf Ereignisse - *publishing* und *subscribing* - zu ermöglichen. Dies wird oft zu *pub/sub* verkürzt.

Native Events wurden früher behandelt, mit einem Beispiel für die Erkennung, wenn ein Benutzer auf einen Link (oder ein anderes HTML-Element) klickt und eine JavaScript-Funktion auslöst. Auch benutzerdefinierte Events können in ähnlicher Weise erstellt und ausgelöst werden.

Wenn etwas wichtiges in einem Modul passiert, kann es ein Ereignis *veröffentlichen*, um dies zu verkünden.

```
// a new row has been added, announce this
MyApp.pubSub.publish("repeating-row-added");
```

Andere Skripte können bestimmte Ereignisse *abonnieren* und bestimmte Funktionen ausführen, wenn sie auftreten.

```
// listen for new repeating rows being added,
// and init show/hide on them
MyApp.pubSub.addSubscriber("repeating-row-added", initShowHide);
```

Es gibt eine Reihe von verschiedenen *pub/sub* JavaScript-Bibliotheken, die diese Form der Kommunikation zwischen den Modulen ermöglichen.

***Weitere Informationen***

 - [http://tech.pro/blog/1402/five-patterns-to-help-you-tame-asynchronous-javascript](http://tech.pro/blog/1402/five-patterns-to-help-you-tame-asynchronous-javascript)
 - [https://github.com/postaljs/postal.js](https://github.com/postaljs/postal.js)


## Plugins und Bibliotheken

Vor vielen Jahren war es ziemlich üblich, eine Datei mit nützlichen wiederverwendbaren Funktionen zu haben, die von Projekt zu Projekt kopiert wurden. Diese *Bibliothek* Datei könnte einige praktische Verknüpfungen liefern und spart Zeit das gleiche Verhalten über mehrere Projekte erneut zu schreiben.

Open-Source-Bibliotheken wie JQuery haben die Notwendigkeit von massgeschneiderten komplexen Bibliotheken reduziert, um privat von Einzelpersonen gepflegt zu werden.


### JQuery Plugins

JQuery bietet eine Reihe von nützlichen Features, aber von sich aus ist es nicht für jede mögliche Anforderung zu gebrauchen.

JQuery *Plugins* ermöglichen, die Kernfunktionalität zu erweitern, um Features wie Slideshows, Tabs, Akkordeons und viele andere Features hinzuzufügen.


### Standalone Bibliotheken

Andere Bibliotheken existieren, die ähnliche Vorteile von nützlicher Funktionalität bieten, ohne eine Abhängigkeit von JQuery zu haben.

Zum Beispiel ist die [Moment] (http://momentjs.com) JavaScript-Bibliothek nützlich, wenn es um Termine geht. Sie bietet eine Reihe von Features wie die Umwandlung von Daten aus einer Reihe von Formaten und die Berechnung der relativen Daten.

Die Bibliothek [Underscore] (http://underscorejs.org) ist nützlich, wenn es um komplexe Daten geht, die verarbeitet und manipuliert werden müssen.

Die Bibliothek [D3] (http://d3js.org) eignet sich zum Zeichnen von interaktiven Infografiken.

Dies sind nur einige Beispiele für Open-Source-Bibliotheken, die von anderen Entwicklern geschrieben und verfügbar sind.

Es gibt noch viel mehr: [http://microjs.com/](http://microjs.com/)


### Suchen und Prüfen von Plugins und Bibliotheken

Oft ist der schwierigste Teil eines Projektes, relevante JQuery-Plugins und Bibliotheken, die helfen können, zu finden.

Es gibt keinen einzigen Ort, um die Suche zu starten. Oft ist eine hilfreiche Methode, um an einigen Stellen wie [Stack Overflow] (http://stackoverflow.com) und [Google] (http://google.com) nach einer Lösung zu suchen. Wenn Sie ein paar relevante Artikel und Antworten lesen, können Sie feststellen, dass sie die gleiche Lösung suchen.

Die Mehrheit der nützlichen Bibliotheken wird auf [GitHub] (https://github.com/) gespeichert. Dies ist ein günstiger Standort für Entwickler, um Open-Source-Code kostenlos zu speichern und anderen zu ermöglichen, zu ihrer Entwicklung beizutragen.

Bei der Überprüfung möglicher Optionen gibt es ein paar hilfreiche Hinweise, die ihre Vorzüge zeigen können.

 - **Sterne:** Dies zeigt an, wie viele Entwickler die Bibliothek *gebookmarkt* haben
 - **Probleme:** Wenn man durch die offenen Fragen schaut, kann man auf mögliche Probleme stossen, die Entwickler mit der Bibliothek hatten. Eine hohe Anzahl offener Fragen kann auf mögliche Schwierigkeiten hindeuten. Ebenso können Fragen mit Antworten aus dem Bibliotheksentwickler ein vernünftiges Mass an Support anzeigen. Es lohnt sich auch zu sehen, wie viele geschlossene Probleme erfolgreich gelöst wurden.
 - **PRs:** *Pull Requests* sind Beiträge von anderen Entwicklern, die helfen, Updates für die Bibliothek zu erstellen. Eine Anzahl von offenen Pull-Requests kann auf eine Bibliothek hinweisen, die nicht mehr aktiv ist.
 - **Dokumentation und Beispiele:** Zu lernen, wie man eine neue Bibliothek benutzt, kann zunächst komplex sein. Die Verfügbarkeit von umfangreichen Dokumentations- und/oder Codebeispielen kann bei der Auswahl einer geeigneten Bibliothek helfen.

Die wichtigste Methode von allen ist, den Code selbst zu überprüfen. Das hängt von Ihrem JavaScript Wissen ab. [Hier sind einige Tipps für die Überprüfung von Plugin-Code](https://remysharp.com/2010/06/03/signs-of-a-poorly-written-jquery-plugin).


***Weitere Informationen:***

 - [http://davidwalsh.name/13-factors-choosing-javascript-charting-library](http://davidwalsh.name/13-factors-choosing-javascript-charting-library)
 - [https://remysharp.com/2010/06/03/signs-of-a-poorly-written-jquery-plugin](https://remysharp.com/2010/06/03/signs-of-a-poorly-written-jquery-plugin)


### Ein Plugin oder eine Bibliothek erstellen

Es gibt eine Reihe von umfassenden Leitfäden für die Erstellung von JQuery-Plugins:

 - [https://learn.jquery.com/plugins/basic-plugin-creation/](https://learn.jquery.com/plugins/basic-plugin-creation/)
 - [http://www.smashingmagazine.com/2011/10/11/essential-jquery-plugin-patterns/](http://www.smashingmagazine.com/2011/10/11/essential-jquery-plugin-patterns/)
 - [http://jqueryboilerplate.com/](http://jqueryboilerplate.com/)

Es gibt keine Standardmethode für die Erstellung einer eigenständigen JavaScript-Bibliothek, aber es könnte helfen, ein paar beliebte zu überprüfen, um zu sehen, wie sie geschrieben und dokumentiert sind.


## JavaScript Frameworks

Wie oben diskutiert wurde, wird jede Website davon profitieren, wenn man sich von der *Code-Suppe* einer JQuery DOM-ready-Funktion verabschiedet. Der erste Schritt besteht darin, die Logik in Module zu trennen.

Wenn das JavaScript weiterhin wächst und sich die Komplexität erhöht, kann es an der Zeit sein, die Erstellung einer benutzerdefinierten Codestruktur zu stoppen und stattdessen ein anerkanntes Framework zu verwenden.


### Probleme die Frameworks lösen können

Das grösste Problem mit einer benutzerdefinierten Anwendungsstruktur, die Frameworks zu lösen versuchen, ist die Trennung von verschiedenen Arten von JavaScript-Logik. Die meisten JavaScript-Frameworks erzwingen eine *Trennung von Interessen* - die Isolierung von Code in verschiedene Funktionen, die für verschiedene Zwecke verwendet werden.

Die wichtigsten Teile von JavaScript, die traditionell getrennt sind, betreffen DOM-Interaktion, Datenmanipulation, Templating und Event-Handling.


#### MVC

Das gemeinsame Muster, das die meisten JavaScript Frameworks verfolgen, heisst *Model View Controller*, oft verkürzt auf *MVC*.

MVC ist ein komplexes Muster, das an anderer Stelle im Internet gut dokumentiert ist. Die folgenden Links geben eine umfassende Erläuterung ihrer Logik und wie sie für den Kontext von JavaScript-Frameworks gilt.

Nach diesen Prinzipien sollte es zu kleineren strukturierten Modulen kommen, die Code besser pflegbar machen.

***Weitere Informationen:***

 - [http://alistapart.com/article/javascript-mvc](http://alistapart.com/article/javascript-mvc)
 - [http://www.smashingmagazine.com/2012/07/27/journey-through-the-javascript-mvc-jungle/](http://www.smashingmagazine.com/2012/07/27/journey-through-the-javascript-mvc-jungle/)
 - [http://addyosmani.com/resources/essentialjsdesignpatterns/book/](http://addyosmani.com/resources/essentialjsdesignpatterns/book/)


### Entscheiden, ob ein Framework verwendet werden soll

Dies ist ein komplexes Thema, bei dem viele Entwickler entweder dafür oder dagegen sind. Es gibt Hunderte von Artikeln zu diesem Thema.

Letztlich ist die Entscheidung, ob man eines benutzt, abhängig vom Kontext:

  - Wie komplex ist die geforderte Funktionalität?
  - Wie vertraut sind die Entwickler mit JavaScript?
  - Haben die Entwickler Erfahrung mit JavaScript-Frameworks?
  - Würde die Seite davon profitieren, eine *Single-Page-Anwendung* zu sein? Soll die Applikationslogik im Browser gespeichert werden oder soll die Funktionalität vom Server kommen?

Es gibt mehrere Vor-und Nachteile, die berücksichtigt werden sollten, wenn eine Entscheidung darüber getroffen wird, ob ein JavaScript-Framework verwendet wird oder nicht.


#### PROs

  - Die meisten etablierten JavaScript-Frameworks wurden sorgfältig getestet und lassen Sie sich auf den Aufbau Ihrer Anwendung konzentrieren, ohne sich um Fehler in der Architektur zu sorgen.
  - JavaScript-Frameworks sind in der Regel gut dokumentiert, mit aktiven Communities und vielen nützlichen Artikeln und Antworten auf häufig gestellte Fragen auf Websites wie Stack Overflow.
  - Wenn ein neuer Entwickler Erfahrung mit einem JavaScript-Framework hat, sollten sie schnell produktiv sein, da sie bereits ein Verständnis von der Logik haben.


#### CONs

 - Die zusätzliche Dateigrösse eines JavaScript-Frameworks (und seiner Abhängigkeiten) sollte berücksichtigt werden.
 - Die Komplexität des JavaScript-Codes, die bei der Verwendung eines Frameworks erforderlich ist, kann für unerfahrene Front-End-Entwickler schwierig sein.
 - Einige JavaScript-Frameworks leiden unter anfänglichen Performance-Hits und nehmen eine beträchtliche Zeitspanne ein, um das erste Mal zu starten, wenn sie verwendet werden.
 - JavaScript Frameworks helfen SEO meist nicht - zumindest nicht im Vergleich zu *traditionellen* Webseiten.
 - Die Reife eines JavaScript-Frameworks sollte ausgewertet werden, bevor es verwendet wird. Neue Frameworks können sich vor allem deutlich ändern, was zu grossem Code-Rewriten führen könnte.
 - Die Auswahl eines JavaScript-Frameworks kann ein langfristiges Engagement und eine bedeutende Investition auf der Grundlage einer Open-Source-Lösung beinhalten.

JavaScript-Frameworks sind nicht die richtige Wahl für jedes Projekt. Wenn Sie eine Website bauen, dessen Logik zum Grossteil immer noch auf dem Server stattfindet, und wenn JavaScript in erster Linie verwendet wird, um die Dinge ein wenig interaktiver zu machen, dann kann ein komplexes JavaScript-Framework übertrieben sein. 


### Populäre Frameworks

Es gibt keinen Mangel an verfügbaren JavaScript Frameworks, und neue werden ständig erstellt. Hier sind einige der beliebtesten Optionen:

 - [Backbone.js](http://backbonejs.org/)
 - [AngularJS](https://angularjs.org/)
 - [React](https://facebook.github.io/react/)

Es gibt unzählige mehr: [http://todomvc.com/](http://todomvc.com/)

Die Berücksichtigung des am besten geeigneten Rahmens sollte ihre relativen Vor- und Nachteile abwägen, für die es viele Vergleichsartikel gibt.

***Weitere Informationen:***

 - [http://davidwalsh.name/6-reasons-to-use-javascript-libraries-frameworks](http://davidwalsh.name/6-reasons-to-use-javascript-libraries-frameworks)
 - [http://bitworking.org/news/2014/05/zero\_framework_manifesto](http://bitworking.org/news/2014/05/zero_framework_manifesto)
 - [http://netpoetica.com/why-i-dont-want-your-javascript-framework-but-i-love-you/](http://netpoetica.com/why-i-dont-want-your-javascript-framework-but-i-love-you/)
 - [https://andywalpole.me/#!/blog/142134/2015-the-end-the-monolithic-javascript-framework](https://andywalpole.me/#!/blog/142134/2015-the-end-the-monolithic-javascript-framework)
 - [http://tantek.com/2015/069/t1/js-dr-javascript-required-dead](http://tantek.com/2015/069/t1/js-dr-javascript-required-dead)


### Isomorphes JavaScript

Die Zukunft der JavaScript Frameworks mag in einem neuen Konzept namens *Isomorphes JavaScript* liegen. Die Idee dahinter ist, den gleichen Code zum rendern einer Seite zu verwenden, ganz gleich, ob das auf dem Server oder Client geschieht.

***Weitere Informationen:***

 - [http://isomorphic.net/javascript](http://isomorphic.net/javascript)
 - [http://nerds.airbnb.com/isomorphic-javascript-future-web-apps/](http://nerds.airbnb.com/isomorphic-javascript-future-web-apps/)
 - [http://www.sitepoint.com/isomorphic-javascript-applications/](http://www.sitepoint.com/isomorphic-javascript-applications/)
 - [http://www.smashingmagazine.com/2015/04/21/react-to-the-future-with-isomorphic-apps/](http://www.smashingmagazine.com/2015/04/21/react-to-the-future-with-isomorphic-apps/)
 - [http://blog.neutrondrive.com/posts/252697-isomorphic-javascript-is-not-the-answer](http://blog.neutrondrive.com/posts/252697-isomorphic-javascript-is-not-the-answer)


## JavaScript Module Loader

Viele Programmiersprachen bieten eine native Möglichkeit, Module zu definieren und zu verwenden. JavaScript derzeit nicht (obwohl eine zukünftige Version von JavaScript diese Fähigkeit beinhalten wird).

Mittlerweile gibt es Werkzeuge, die es Entwicklern ermöglichen, Module jetzt zu verwenden. Diese *Module loader*-Systeme ermöglichen es, komplexe Codebasen in einer einfachen, konsistenten und gut dokumentierten Weise zu organisieren.

Es gibt ein paar beliebte Module Loader-Tools. Es gibt auch zwei verschiedene populäre Methoden zur Definition von Modulen, bekannt als *AMD* und *Common.js*.

 - [RequireJS](http://requirejs.org/) - Einer der allerersten populären Module-Loader, der die *AMD* Methode zum Deklarieren von Modulen verwendet.
 - [Browserify](http://browserify.org/) - Ein Module-Loader der die *Common.js* Moduldeklaration verwendet
 - [Webpack](http://webpack.github.io/) - Ein weiterer Module-Loader der *Common.js* verwendet

Unabhängig von der verwendeten Werkzeug- und Moduldefinition ist das Prinzip gleich; Erstellen Sie zahlreiche Dateien mit kleinen isolierten Modulen mit individuellen Zwecken, und importieren Sie sie an der entsprechenden Stelle, wo sie in der Codebasis verwendet werden.

Module-Loader werden oft in Kombination mit einem JavaScript-Framework verwendet, um weitere Code-Struktur und Trennung zu bieten.

***Weitere Informationen***

 - [https://web-design-weekly.com/2014/09/24/diving-webpack/](https://web-design-weekly.com/2014/09/24/diving-webpack/)
 - [https://github.com/substack/browserify-handbook](https://github.com/substack/browserify-handbook)
 - [http://webpack.github.io/docs/commonjs.html](http://webpack.github.io/docs/commonjs.html)


## Templating

Wenn Sie JavaScript verwenden, um Inhalte zu erstellen, um HTML-Elemente zu füllen, können Template-Tools helfen, die Anwendungslogik vom Template-Markup zu trennen.

Die Verwendung eines Templating-Systems ist vorteilhaft, wenn das clientseitige HTML-Rendering erforderlich ist, insbesondere beim Laden von Daten von einem Server und zum Rendern einer komplexen HTML-Struktur.

Es stehen eine Reihe von Template-Systemen zur Verfügung:

 - [ejs](http://www.embeddedjs.com/)
 - [Handlebars](http://handlebarsjs.com/)
 - [Mustache](https://github.com/janl/mustache.js)

Es gibt unzählige mehr: [http://garann.github.io/template-chooser/](http://garann.github.io/template-chooser/)

Unabhängig davon, welche Templating-Sprache gewählt wird, bieten sie alle überlegene Funktionalität (und Code-Trennung) im Vergleich zum Erstellen von HTML-Elementen und befüllen mit JQuery.

Allerdings lohnt es sich zu überlegen, ob das Rendering im Client vorteilhaft ist, da es langsam sein kann und die Duplizierung der bereits vorhandenen Logik auf dem Server erfordert. Stattdessen betrachten Sie das Rendern von Teilen auf dem Server und das Zurückgeben von HTML, das direkt in das DOM eingefügt werden soll.

***Weitere Informationen:***

 - [http://www.smashingmagazine.com/2012/12/05/client-side-templating/](http://www.smashingmagazine.com/2012/12/05/client-side-templating/)
 - [http://www.sitepoint.com/creating-html-templates-with-mustachejs/](http://www.sitepoint.com/creating-html-templates-with-mustachejs/)
 - [http://nimbupani.com/mustache.html](http://nimbupani.com/mustache.html)


## Build Tools

Unabhängig davon, ob ein beliebtes JavaScript-Framework oder eine benutzerdefinierte Anwendungsstruktur verwendet wurde, besteht die Chance, dass eine Reihe von individuellen JavaScript-Dateien erstellt wurden, um eine modulare Codebasis bereitzustellen.

Dies kann dazu beitragen, eine Codebasis zu verwalten, aber für eine Produktionsumgebung können diese Dateien kombiniert werden, um HTTP-Anfragen zu minimieren und die Website zu beschleunigen.

Ein *Task Runner* kann helfen, die Verkettung (und Minifizierung) dieser Dateien zu automatisieren.

Diese Werkzeuge können auch mit anderen Aufgaben wie der Optimierung von Bildern, dem Ausführen eines CSS-Vorprozessors, das Prüfen auf Fehler, durchführen von Tests und bereitzustellen von Code, helfen.

Diese Tools sind für die Verwendung von Plugins zur Bereitstellung dieser Funktionalität gebaut.

Viele dieser Tools werden mit JavaScript erstellt und konfiguriert.

 - [Grunt](http://gruntjs.com/) - Der populärste Task Runner
 - [Gulp](http://gulpjs.com/) - Weniger populär als Grunt, aber oft schneller und leichter zu konfigurieren
 - [Brocolli](http://broccolijs.com/) - Ein weiterer populärer Task Runner

***Weitere Informationen***

 - [http://24ways.org/2013/grunt-is-not-weird-and-hard/](http://24ways.org/2013/grunt-is-not-weird-and-hard/)
 - [http://alistapart.com/blog/post/getting-started-with-gulp](http://alistapart.com/blog/post/getting-started-with-gulp)


## Abhängigkeiten Management

Die meisten Webseiten verlassen sich auf Drittanbieter-Bibliotheken und Frameworks - JQuery ist das offensichtlichste und beliebteste Beispiel.

Man kann es ziemlich schnell herunterladen und direkt in die Codebasis einfügen. Jedoch kann man mit einem *Paket-Manager* die Verwaltung, Installation und Aktualisierung dieser Abhängigkeiten vereinfachen - besonders praktisch bei der Arbeit in ein Team.

Es gibt eine Reihe von beliebten Paket-Managern, darunter:

 - [bower](http://bower.io/)
 - [npm](https://www.npmjs.com/)
 - [component](https://github.com/componentjs/component)

Es gibt noch weitere: [https://github.com/wilmoore/frontend-packagers](https://github.com/wilmoore/frontend-packagers)

***Weitere Informationen***

 - [http://frontendbabel.info/articles/bower-why-frontend-package-manager/](http://frontendbabel.info/articles/bower-why-frontend-package-manager/)
 - [https://css-tricks.com/whats-great-bower/](https://css-tricks.com/whats-great-bower/)


## Testen

Testen von JavaScript kann grundsätzlich wichtig sein, vor allem bei der Unterstützung einer grossen und komplexen Website, die sich ständig weiterentwickelt.

Es gibt eine Reihe von Frameworks für das Testen mit JavaScript:

 - [Jasmine](http://jasmine.github.io/)
 - [Mocha](http://mochajs.org/)
 - [Intern](https://theintern.github.io/)

Und noch weitere: [http://stackoverflow.com/a/680713](http://stackoverflow.com/a/680713)


***Weitere Informationen***

 - [http://alistapart.com/article/writing-testable-javascript](http://alistapart.com/article/writing-testable-javascript)
 - [http://www.smashingmagazine.com/2012/06/27/introduction-to-javascript-unit-testing/](http://www.smashingmagazine.com/2012/06/27/introduction-to-javascript-unit-testing/)
 - [http://www.helpscout.net/blog/functional-testing-casperjs/](http://www.helpscout.net/blog/functional-testing-casperjs/)


## Code Qualität

Beim Schreiben von JavaScript ist es einfach, kleine Fehler zu machen, die möglicherweise zu Problemen führen könnten, wenn sie unentdeckt bleiben.

[JSHint] (http://jshint.com/) und [JSCS] (http://jscs.info/) sind zwei Werkzeuge, die helfen können, diese Probleme zu erkennen. Sie können so konfiguriert werden, dass sie Codierungsregeln über ein Team erzwingen und sicherstellen, dass jeder Code eine Reihe von vereinbarten Standards erfüllt.

JSHint und JSCS können zu verschiedenen Zeiten verwendet werden. Plugins existieren, um sie direkt in viele populäre Code-Editoren hinzuzufügen, um sofort Fehler zu vermeiden. Sie können auch zu einem *Task Runner* hinzugefügt werden, um Probleme als Teil eines Buildprozesses zu identifizieren. Sie könnten zu einer *Pre-Commit-Phase* der Versionskontrollsoftware hinzugefügt werden, um sicherzustellen, dass der Code nicht akzeptiert wird, bis er die Validierung bestanden hat.

***Weitere Informationen***

 - [https://yannick.cr/posts/enforcing-coding-rules-in-your-team-with-jscs/post](https://yannick.cr/posts/enforcing-coding-rules-in-your-team-with-jscs/post)
 - [http://davetayls.me/blog/2013/07/01/how-will-i-keep-javascript-code-quality-hight-jshint/](http://davetayls.me/blog/2013/07/01/how-will-i-keep-javascript-code-quality-hight-jshint/)
 - [https://github.com/valueof/home/blob/master/pages/blog/why-jshint.md](https://github.com/valueof/home/blob/master/pages/blog/why-jshint.md)


## Node.js

[Node.js] (https://nodejs.org/) ist eine Plattform, mit der JavaScript auf einem Server ausgeführt werden kann. Die asynchrone ereignisgesteuerte Natur von JavaScript eignet sich für bestimmte Anwendungsarten, wie z.B. die Echtzeitkommunikation mit *websockets*.

***Weitere Informationen***

 - [http://code.tutsplus.com/tutorials/nodejs-for-beginners--net-26314](http://code.tutsplus.com/tutorials/nodejs-for-beginners--net-26314)
 - [https://github.com/maxogden/art-of-node/#the-art-of-node](https://github.com/maxogden/art-of-node/#the-art-of-node)
 - [http://nodeguide.com/beginner.html](http://nodeguide.com/beginner.html)
 - [http://stackoverflow.com/a/5511507](http://stackoverflow.com/a/5511507)


## Grafik

Es gibt zwei ganz verschiedene Methoden zur Erzeugung von interaktiven Grafiken mit JavaScript: *SVG* und *canvas*.

### SVG

SVG ist ein XML-basiertes Vektorformat für das Zeichnen von Bildern über das DOM. Die Verwendung von SVGs bedeutet auflösungsunabhängige Grafiken bei niedrigen Dateigrössen.

Es gibt verschiedene Werkzeuge, die dazu beitragen, SVGs mit JavaScript zu arbeiten und zu interagieren:

 - [SnapSVG](http://snapsvg.io/)
 - [D3](http://d3js.org/)
 - [Raphael](http://raphaeljs.com/)

***Weitere Informationen***

 - [https://css-tricks.com/using-svg/](https://css-tricks.com/using-svg/)
 - [http://davidwalsh.name/svg-animation](http://davidwalsh.name/svg-animation)


### Canvas

Canvas ist eine alternative Methode, JavaScript zu verwenden, um Grafiken in einem Browser zu erstellen. Im Gegensatz zu SVG macht es Bitmap-Daten. Der Vorteil der Verwendung von Canvas ist die Möglichkeit, WebGL zu verwenden, um Hardware-gerenderten 3D-Grafiken zu erstellen.

Es gibt eine Reihe von Werkzeugen, um Canvas zu benutzen:

 - [EaselJS](http://www.createjs.com/EaselJS)
 - [Paper.js](http://paperjs.org/)
 - [three.js](http://threejs.org/)

Es gibt viele weitere: [http://www.softr.li/blog/2012/06/20/which-html5-canvas-javascript-library-should-i-use](http://www.softr.li/blog/2012/06/20/which-html5-canvas-javascript-library-should-i-use)

***Weitere Informationen***

 - [https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial)
 - [http://diveintohtml5.info/canvas.html](http://diveintohtml5.info/canvas.html)


## Zukünftige Versionen von JavaScript

Zukünftige Versionen von JavaScript - *ES 6 / ES 2015* und darüber hinaus - werden viele der oben genannten Fragen ansprechen. Es wird ein echtes Module-Loader-System, Methoden für die Verwaltung von Scopes und das Erstellen von Templates und vielem mehr geben.

Obwohl es derzeit nicht über alle Browser hinweg implementiert ist, erlauben Tools wie [Traceur] (https://github.com/google/traceur-compiler) und [Babel] (https://babeljs.io/) JavaScript auf diese Weise bereits heute zu schreiben, um dann zurück in die aktuelle Version von JavaScript *verwandelt* zu werden, die Browser versteht.

***Weitere Informationen***

 - [https://leanpub.com/understandinges6/read](https://leanpub.com/understandinges6/read)
 - [http://24ways.org/2014/javascript-modules-the-es6-way/](http://24ways.org/2014/javascript-modules-the-es6-way/)
 - [https://babeljs.io/docs/learn-es6/](https://babeljs.io/docs/learn-es6/)


## Weitere Informationen

Eine Vielzahl weiterführender Links findet man hier:

 - [https://github.com/dypsilon/frontend-dev-bookmarks](https://github.com/dypsilon/frontend-dev-bookmarks)
