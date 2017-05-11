# JavaScript Notizen

Ein paar Notizen vorbereitet beim Schreiben von Schulungen ...

Diese Anmerkungen nehmen eine geringe Menge an Vorkenntnissen der Programmierung im Allgemeinen und insbesondere JavaScript-Kenntnisse an. Zumindest wird davon ausgegangen, dass bekannt ist, was JavaScript ist, warum wir es benutzen und wie man es in einem Webbrowser ausf�hrt.


## JavaScript Grundlagen

### Variablen

Eine Analogie, die oft verwendet wird, um eine Variable zu beschreiben, ist *ein Container, in den man etwas einsetzen kann*.

Der Name, den Sie einer Variable geben, ist das Etikett, das Sie auf den Container gelegt haben. Sie wissen also, wie man es sp�ter wieder findet. Variablen k�nnen verwendet werden, um alles zu speichern - Zahlen, Text oder andere Arten von Informationen:

```
var nearestStar = "Alpha Centauri";
var lightYearsAway = 4.3;
var age = 6000000000;
var isHot = true;
```

Wenn Sie diese Informationen sp�ter referenzieren m�ssen, beziehen Sie sich auf den Variablennamen:

```
alert(nearestStar); // "Alpha Centauri"
```

Variablen k�nnen mit den Werten aus anderen Variablen gesetzt werden:

```
var planets = 8;
var dwarfPlanets = 5;

var planetCount = 8 + 5; // 13
```

Der Wert einer Variablen kann ge�ndert werden (deshalb heisst es *Variable*):

```
var numberOfPlanets = 9;

numberOfPlanets = numberOfPlanets - 1; // bye bye Pluto
```

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar\_and_types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types)


### Arrays

Wir k�nnen verwandte Listen von Informationen in Arrays speichern. Dies erm�glicht es uns, sie zusammen zu gruppieren und sp�ter einfach Code f�r alle Elemente im Array auszuf�hren.

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

`for` Schleifen sind eine einfache M�glichkeit, um auf die Informationen in einem Array zuzugreifen:

```
for (var counter = 0, planetCount = planets.length; counter < planetCount; counter++) {
    var planet = planets[counter];
    alert("I like the planet " + planet);
}
```

Dieser Code verwendet eine Variable, um die Array-L�nge einmal zu cachen, anstatt sie jedes Mal zu �berpr�fen, wenn wir die Schleife passieren. Dies ist f�r eine (vernachl�ssigbare) Geschwindigkeitsverbesserung. Es ist eine von einer Reihe von kleinen Optimierungen, die Entwickler oft empfehlen, um die JavaScript-Leistung zu beschleunigen. Andere werden ggf. diskutiert.

Ein anderer Weg, um durch ein Array zu durchlaufen ist mit `forEach`:

```
function enthuse (planet) {
    alert("I like the planet " + planet);
}

planets.forEach(enthuse);
```

F�r die Zwecke des Durchschleifens durch das Array kann entweder `for` oder `forEach` verwendet werden, um unsere Anforderungen zu erf�llen.

Diese Wahl der Optionen f�r die Gestaltung von Code zeigt das Programmierprinzip von *es gibt mehr als eine M�glichkeit, etwas zu tun*.

Allerdings kann, wie es oft der Fall ist, eine Option Vor- oder Nachteile haben. In dieser Situation ist man sich bewusst, dass `forEach` dies nicht so weit wie eine einfache `for` Schleife unterst�tzt wird, zumindest in �lteren Browsern.

***Weitere Informationen:***

 - [http://stackoverflow.com/a/9329476](http://stackoverflow.com/a/9329476)
 - [https://coderwall.com/p/kvzbpa/don-t-use-array-foreach-use-for-instead](https://coderwall.com/p/kvzbpa/don-t-use-array-foreach-use-for-instead)
 - [https://css-tricks.com/snippets/javascript/loop-queryselectorall-matches/](https://css-tricks.com/snippets/javascript/loop-queryselectorall-matches/)


### Objekte

Objekte sind n�tzlich, um verwandte Werte zu gruppieren:

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

Wir k�nnen Arrays und Objekte ineinander setzen. Dies kann eine n�tzliche M�glichkeit sein, komplexe Informationen zu organisieren:

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

Wir k�nnen dann diese Informationen durchlaufen und Funktionen ausf�hren, um n�tzliche Informationen zu extrahieren:

```
function describePlanet (planet) {
    alert(planet.name + " has a radius of " + planet["radius"] + "km");
}

planets.forEach(describePlanet);
```

JavaScript-Objekte sind die Basis f�r JSON (*JavaScript Object Notation*). Die wichtige Regel, die man sich erinnern sollte, ist, dass in g�ltigem JSON alle Schl�ssel mit doppelten Anf�hrungszeichen zitiert werden m�ssen:

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

Funktionen sind eine Reihe von Anweisungen, die jetzt angegeben (oder *definiert*) werden k�nnen, aber sp�ter verwendet (oder *genannt*) werden. Der Hauptvorteil der Verwendung einer Funktion ist, dass Sie sie nur einmal erstellen m�ssen, und dann k�nnen Sie sie wieder verwenden, so oft Sie sie ben�tigen.

Funktionen k�nnen auf zwei Arten definiert werden. Es gibt subtile, aber wichtige Unterschiede.

**Funktions Deklarationen:**

```
function enthuse (planet) {
    return "I like the planet" + planet;
}
```

**Funktion Ausdr�cke:**

```
var enthuse = function (planet) {
    return "I like the planet" + planet;
}
```

Beides kann auf die gleiche Weise verwendet werden:

```
var sentence = enthuse("Mercury"); // "I like the planet Mercury"
```

Der Hauptunterschied besteht darin, dass deklarierte Funktionen *gehisst werden*, d.h. sie werden vom JavaScript-Interpreter an die Spitze des Blocks verschoben. Deshalb k�nnen sie referenziert werden, bevor sie deklariert werden.

***Weitere Informationen:***

 - [http://stackoverflow.com/a/336868](http://stackoverflow.com/a/336868)
 - [http://www.unicodegirl.com/function-statement-versus-function-expression.html](http://www.unicodegirl.com/function-statement-versus-function-expression.html)


### if / else Konditionen

if / else-Bedingungen erlauben es uns, bestimmte Funktionalit�t nur dann auszuf�hren, wenn bestimmte Bedingungen erf�llt sind.

Ihre Verwendung erfordert eine Bedingung, die entweder wahr oder falsch sein wird, worauf wir unsere Entscheidung st�tzen k�nnen:

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

Die meisten Browser haben n�tzliche Entwickler-Tools eingebaut. Hier sind einige Notizen zu den wichtigsten Tools, die n�tzlich f�r JavaScript-Entwicklung sind. Sie sind spezifisch f�r Panels in der aktuellen Version der Chrome-Entwickler-Tools, obwohl �quivalente in der Regel in anderen grossen Browsern zur Verf�gung stehen.


### Konsolen-Panel

Das Konsolen-Panel ist der prim�re Ort, um Nachrichten zu protokollieren, Fehler zu erkennen, Code zu testen und mit der aktuellen Seite zu interagieren.


#### Nachrichten protokollieren

Es kann sinnvoll sein, `console.log();` zu verwenden, um den aktuellen Wert einer Variablen w�hrend der Entwicklung anzuzeigen. Eine oder mehrere Variablen k�nnen als *Parameter* an diese Funktion �bergeben werden.

```
console.log(planets, stuff, somethingElse);
```

Sie k�nnen String-Formatierung und benutzerdefinierte Stile auf verschiedene Nachrichten anwenden, so dass eine Differenzierung in der Anzeige von Nachrichten f�r verschiedene Zwecke protokolliert werden kann.

```
var message = "%c Planet %s has a radius of %d km";
var styles = "color: orange; background: blue; font-size: 16pt";
var planet = "Earth";
var radius = 6371;

console.log(message, styles, planet, radius);
```

Es sind weitere n�tzliche `console`-Optionen verf�gbar, z.B. `console.group()` f�r die Zusammenstellung verwandter Nachrichten in eine zusammenklappbare Gruppe und `console.table()` f�r die Anzeige von sich wiederholenden Daten in einer Tabelle.

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/console-api](https://developer.chrome.com/devtools/docs/console-api)
 - [https://developer.chrome.com/devtools/docs/tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks)


#### Fehler erkennen

Wenn Sie einen Fehler in Ihrem JavaScript-Code machen, wird es in der Konsole referenziert.

Dies sollte einen Dateinamen, Zeilennummer und (hoffentlich) einen Hinweis auf die Art des Fehlers geben.

Wenn Sie auf den Fehler klicken, f�hrt er Sie zum *source*-Panel, um ihn zu debuggen.

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/console#errors-and-warnings](https://developer.chrome.com/devtools/docs/console#errors-and-warnings)


#### Code testen

Vor dem Schreiben von Code kann es hilfreich sein, in der Konsole zu experimentieren. Dies kann dazu beitragen, eine Live-Vorschau Ihrer �nderungen zu sehen, die mit der aktuellen Seite interagiert, wenn Sie einen Befehl ausf�hren. Wenn es fertig ist, kann dieser Code dann in eine externe Datei kopiert werden.

Jedes Mal, wenn Sie die Seite aktualisieren, wird dieser Code zur�ckgesetzt. Es wird immer noch im Verlauf der Konsole verf�gbar sein (genau wie ein Terminal-Fenster), so dass das Dr�cken von oben / unten auf der Tastatur durch vorherige Befehle durchl�uft.


### Elemente Panel

Der Inspektor wird haupts�chlich f�r die Anzeige des aktuellen HTML und CSS verwendet, aber er kann auch f�r das JavaScript-Debugging n�tzlich sein.

Zum Beispiel kann er zeigen, welche Elemente auf der Seite *Event-Listener* haben. Diese werden sp�ter besprochen.

Sie k�nnen auf jedes HTML-Element mit der rechten Maustaste klicken und eine *'break on ...'* Option ausw�hlen, die es Ihnen erm�glicht, JavaScript an der Stelle zu pausieren und zu debuggen, an der das HTML-Element �ber JavaScript manipuliert wird.


### Netzwerk Panel

Das Netzwerk-Panel listet alle HTTP-Anfragen auf, die beim Debuggen von AJAX-Anfragen n�tzlich sein k�nnen - zum Beispiel k�nnen Sie die Parameter anzeigen, die an den Server gesendet wurden, und die Daten, die vom Server zur�ckgegeben wurden (oder nicht).

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/network](https://developer.chrome.com/devtools/docs/network)


### Quellen Panel

Im Quellpanel kann das JavaScript der aktuellen Seite analysiert werden. Diese Debugging-Tools sind leistungsstark und komplex.


#### Quellen

Die Registerkarte "Quellen" listet alle textbasierten Quellen auf der Seite auf, z.B. die HTML-, CSS- und JavaScript-Dateien, aus denen die aktuelle Seite besteht. Wenn Sie auf eine dieser Dateien klicken, wird diese im Hauptfenster angezeigt. Wenn Sie mit der rechten Maustaste auf eine beliebige Datei klicken, werden weitere Optionen angezeigt.

Beim Betrachten einer minifizierten Datei ist die Option "pretty print" im Hauptfenster praktisch, um den Code lesbar zu machen.

Wenn Sie einen *Arbeitsbereich* einrichten, k�nnen Sie Dateien direkt im Editor bearbeiten und Ihre �nderungen an Ihren lokalen Dateien speichern.

***Weitere Informationen:***

 - [https://developer.chrome.com/devtools/docs/workspaces](https://developer.chrome.com/devtools/docs/workspaces)


#### Content-Skripte

Die Registerkarte *Content-Skripte* listet alle Skripts auf, die im aktuellen Browser-Tab von Erweiterungen (und anderen Quellen) und nicht direkt von der Website selbst geladen werden. Zum Beispiel werden hier die Skripts, die von Ihren Browser-Erweiterungen in die aktuelle Seite eingef�gt (injected) werden, angezeigt.


#### Snippets

Auf der Registerkarte *Snippets* k�nnen Sie eigene benutzerdefinierte Skripts erstellen und speichern, die Sie dann manuell auf einer Seite ausf�hren k�nnen.

Diese sind praktisch, wenn Sie st�ndig das gleiche St�ck Code auf einer Seite laufen lassen wollen, aber den Code nicht im produktiven Code haben m�chten.

Klicken Sie mit der rechten Maustaste in das Bedienfeld, um ein neues Snippet zu erstellen. Geben Sie Ihren Code ein und speichern Sie ihn. Klicken Sie mit der rechten Maustaste erneut, um zu starten.

Ein Beispiel f�r Code zum Testen von Snippets:

```
var headings = document.querySelectorAll("h1");
for (var i = 0; i < headings.length; ++i) {
    headings[i].style.color = "#f90";
}
```


#### Debugging

Debugging JavaScript ist ein komplexes Thema, das gr�ndlich anderswo im Internet erkl�rt wird. Die folgenden Anleitungen sind ziemlich umfassend.

Der beste Weg, um Probleme zu debuggen, besteht darin, den Fehler zu isolieren und zu identifizieren, wie es konsequent repliziert werden kann. Dies macht es leichter, den Fehler zu beseitigen.

***Weitere Informationen***

 - [https://developer.chrome.com/devtools/docs/authoring-development-workflow](https://developer.chrome.com/devtools/docs/authoring-development-workflow)
 - [https://remysharp.com/2012/12/21/my-workflow-never-having-to-leave-devtools](https://remysharp.com/2012/12/21/my-workflow-never-having-to-leave-devtools)
 - [https://developer.chrome.com/devtools/docs/javascript-debugging](https://developer.chrome.com/devtools/docs/javascript-debugging)
 - [https://gist.github.com/jedrichards/9942165](https://gist.github.com/jedrichards/9942165)


#### Remote-Debugging

Bei der Arbeit mit einem iOS-Ger�t k�nnen Sie Mobile Safari remote debuggen, indem Sie das Ger�t an den USB-Port eines Mac anschliessen und die Safari Developer-Tools �ffnen.

Wenn Sie mit einem Android-Ger�t arbeiten, k�nnen Sie mit Mobile Chrome debuggen, indem Sie das Ger�t an den USB-Port eines Computers anschliessen und diese [Anweisungen](https://developer.chrome.com/devtools/docs/remote-debugging) befolgen.

Drittanbieter Tools wie [jsconsole.com](http://jsconsole.com/remote-debugging.html) k�nnen beim Debuggen sehr n�tzlich sein.


### Andere Panels

 - Das *Timeline*-Panel ist n�tzlich, um die Renderleistung zu verfolgen: [https://developer.chrome.com/devtools/docs/timeline](https://developer.chrome.com/devtools/docs/timeline)
 - Das *Profile* Panel ist n�tzlich f�r die Verfolgung von CPU- und Speicherverbrauch: [https://developer.chrome.com/devtools/docs/profiles](https://developer.chrome.com/devtools/docs/profiles)
 - Das *Resources* Panel ist n�tzlich f�r die Verfolgung von Informationen, die in Cookies und der Local Storage gespeichert sind: [https://developer.chrome.com/devtools/docs/resources](https://developer.chrome.com/devtools/docs/resources)
 - Das *Audits* Panel ist n�tzlich, um die Leistung einer Seite zu testen und M�glichkeiten zu analysieren, um sie zu verbessern: [https://developer.chrome.com/devtools#audits](https://developer.chrome.com/devtools#audits)


## Die DOM

In einem Webbrowser hat JavaScript zwei spezielle *globale* Variablen - `window` und `document` - das erlaubt uns, mit dem Browser und der Webseite zu interagieren.

Die Variable `window` wird oft verwendet, um zu erkennen, wann eine Seite geladen wird, wenn das Fenster gescrollt wird und auf die Dimensionen zugegriffen wird (z.B. die Fenstergr�sse ver�ndern).

Die h�ufigste Verwendung von `document` besteht darin, auf HTML-Elemente in einer Webseite zuzugreifen, indem auf das _Document Object Model_ (DOM) verwiesen wird, welches die JavaScript-Darstellung der HTML-Seitenstruktur ist:

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

Zwei Beispiele f�r die Interaktion mit dieser Seite �ber JavaScript, mit dem DOM:

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

Wir k�nnen in der Regel alle DOM-Manipulationen, die wir ben�tigen, mit diesen nativen JavaScript-Befehlen durchf�hren, ohne auf eine externe Bibliothek zur�ckgreifen m�ssen. Wir *brauchen* JQuery nicht, um auf das DOM zuzugreifen und zu manipulieren. Aber es macht diese Interaktionen (und viele andere) viel einfacher.

***Weitere Informationen:***

 - [https://developer.mozilla.org/en-US/docs/Web/API/Document\_Object_Model/Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)


## JQuery

Kurz nach seiner Entstehung wurde JQuery schnell zu einem beliebten Werkzeug, um die vielen Inkonsistenzen zu bew�ltigen, wie bspw. die falsche Implementierung von JavaScript in verschiedenen Browsers.

Das ist nicht mehr so relevant, denn moderne Browser setzen in der Regel die gleichen Standards ein. Aber JQuery ist immer noch n�tzlich, und nicht nur f�r DOM-Interaktionen. Es vereinfacht auch *Ajax* Anrufe, Handling *Events* und Objekt / Array Manipulation unter anderem.

Ein grosser Vorteil ist, dass *die meisten* Front-End-Entwickler mit JQuery vertraut sind, und es hilft, die Teams auf einer gemeinsamen Codebasis arbeiten zu lassen.

Die Anwesenheit von JQuery ist in fast jeder Website allgegenw�rtig. Als solches ist es sinnvoll, nicht nur zu lernen, wie man es benutzt, sondern auch seine Macken und M�ngel.

Dieser Leitfaden nimmt ein Grundwissen von JQuery an - wie f�ge es zu einer Webseite hinzu und verwende es, um DOM-Elemente auszuw�hlen und zu manipulieren.


### JQuery Tipps

#### Schreiben Sie nicht alle in *document ready*

Die h�ufigste Verwendung von JQuery ist die Initialisierung von Code, wenn das DOM der Seite geladen hat, mit:

```
$(document).ready(function () { ... });
```

*Das wird manchmal abgek�rzt:*

```
$(function () { ... });
```

Dies f�hrt oft dazu, dass der Code einer ganzen Anwendung in einer einzigen *global.js* Datei gespeichert ist, und alles in der *ready* Funktion referenziert ist:

```
$(document).ready(function () {
    ...
    (an entire application's code goes here)
    ...
});
```

Das ist keine gute Idee, aus mehreren Gr�nden.

Wenn der gesamte JS-Code der Website an einem einzigen Ort gespeichert ist, kann er schnell schwer zu verwalten sein.

Sofern Sie nicht vorsichtig sind, k�nnen Sie in Schwierigkeiten mit dem Scope kommen, wenn keine zwei Variablen den gleichen Namen teilen k�nnen. Dies wird sp�ter noch n�her er�rtert.

Ein weiteres Problem ist, dass es die anf�ngliche Wiedergabe der Website verlangsamen kann, da dieser Code nicht analysiert wird, bis die Seite bereit ist, gerendert zu werden. Es kann Teile des Codes geben, die sofort ausgef�hrt werden k�nnen, anstatt auf das DOM warten zu m�ssen.

Eine L�sung f�r dieses Problem ist, Code modular zu halten, und nur den Code innerhalb der DOM *ready* Funktion zu *initialisieren*.

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

Beachten Sie, dass dies eine Vereinfachung einer L�sung ist, um das Problem zu demonstrieren. Detaillierte L�sungen werden sp�ter gezeigt.

***Weitere Informationen:***

 - [https://learn.jquery.com/code-organization/concepts/](https://learn.jquery.com/code-organization/concepts/)
 - [http://www.elijahmanor.com/dont-initialize-all-the-things-in-jquery-ready/](http://www.elijahmanor.com/dont-initialize-all-the-things-in-jquery-ready/)


#### Erw�gen Sie die Pr�fixierung von JQuery-Objekten mit *$*

Eine weit verbreitete Konvention, die dazu beitragen kann, eine Variable zu unterscheiden, die auf ein JQuery-Objekt von anderen Variablentypen verweist, ist diese Variablennamen mit einem `$` zu pr�fixieren:

```
var $planetsEl = $("#planets .planet");
var planetCount = $planetsEl.length;
```

Dies hilft zu zeigen, welche Variablen auch Zugriff auf JQuerys viele Funktionen haben.

Einige Entwickler m�gen diesen Ansatz, andere nicht. Aber es lohnt sich zu �berlegen und sich f�r die eine oder anderen einer Konvention zu entscheiden.

***Weitere Informationen:***

 - [http://www.bennadel.com/blog/1778-using-variable-in-jquery-code-is-just-hungarian-notation.htm](http://www.bennadel.com/blog/1778-using-variable-in-jquery-code-is-just-hungarian-notation.htm)


#### DOM Elemente cachen

JQuery macht es sehr einfach, schnell mit dem DOM zu interagieren. Die DOM-Interaktion ist jedoch langsam. Aus Geschwindigkeitsgr�nden ist es am besten, mit dem DOM so wenig wie m�glich zu interagieren.

Beim Abfragen des DOM, um nach einem Element zu suchen, speichern Sie das Ergebnis f�r die zuk�nftige Verwendung zwischen.

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

Wenn Sie eine Reihe neuer DOM-Elemente erstellen, ist es ein guter Ansatz, um das neue HTML-Markup zu generieren und dann in die Seite in einem einzigen Befehl einzuf�gen:

```
var planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"];

var $planetList = $(".planet-list");
var planetElements = "";

for (var counter = 0, planetCount = planets.length; counter < planetCount; counter++) {
    planetElements += "<li>" + planets[counter] + "</li>";
}

$planetList.append(planetElements);
```

Eine alternative Methode besteht darin, die Elemente aus dem DOM zu *l�sen*, w�hrend sie manipuliert werden, und sie dann wieder anzuschliessen, wenn sie fertig sind.

***Weitere Informationen:***

 - [http://learn.jquery.com/performance/detach-elements-before-work-with-them/](http://learn.jquery.com/performance/detach-elements-before-work-with-them/)
 - [http://24ways.org/2011/your-jquery-now-with-less-suck](http://24ways.org/2011/your-jquery-now-with-less-suck)


#### Cache $(this)

�hnlich wie der Punkt �ber das Zwischenspeichern von DOM-Elementen, wenn Sie auf `$(this)` mehrere Male verweisen, �berlegen Sie, ob es Sinn macht das Element zwischenzuspeichern, um eine verbesserte Leistung zu erzielen:

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

In diesem Fall, wenn alles, worauf wir hinaus sind, ist die ID des Elements zu bekommen, dann muss es nicht in ein JQuery-Objekt eingeh�llt werden, da es leicht direkt aus dem nativen DOM-Objekt zugegriffen werden kann:

```
$(".el").click(function (e) {
    var id = this.id;
});
```

Das Lernen nativer JavaScript-Methoden kann von Vorteil sein, wenn Sie JQuery nicht benutzen m�ssen.


#### Manipulieren Sie Klassen, nicht Stile

Wenn Sie den Stil eines Elements �ndern m�chten, ver�ndern Sie seine Stile nicht direkt:

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

Und dann f�gen Sie die Klasse mit JavaScript hinzu:

```
$(".planets li").addClass("planet");
```

Dies hilft bei der Aufrechterhaltung des Grundsatzes der *Trennung von Interessen* - CSS ist verantwortlich f�r Styling, JavaScript wird f�r das Verhalten verwendet.

Es erm�glicht auch eine leichtere Pr�fung von Stilen, da es m�glich ist, die Klasse manuell hinzuzuf�gen oder zu entfernen, um das Layout zu testen, ohne JavaScript zu �ndern.

***Weitere Informationen:***

 - [http://www.smashingmagazine.com/2012/11/19/building-relationship-between-css-javascript/](http://www.smashingmagazine.com/2012/11/19/building-relationship-between-css-javascript/)


#### Erw�gen Sie alternative Methoden der Animation

Wenn Sie einen einfachen �bergang erstellen, �berlegen Sie, ob es mit CSS umgesetzt werden kann:

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

Es kann m�glich sein, eine Animation einfach durch Umschalten eines Klassennamens mit JavaScript auszul�sen:

```
$(".planet").on("click", function (e) {
    $(this).toggleClass("is-active");
});
```

Es ist nicht immer m�glich, CSS f�r Animationen zu verwenden. Wenn Sie JavaScript verwenden, sollten Sie das [JQuery animate enhanced](https://github.com/benbarnett/JQuery-Animate-Enhanced) Plugin (oder �hnliches) ausprobieren, weil es hardware-beschleunigte CSS3 �berg�nge  nutzt, wann immer m�glich. Dazu ben�tigt es Tests, denn es wird nicht immer funktionieren und kann u.U. auch seltsame Fehler produzieren.

Eine nicht-JQuery-basierte Alternative f�r Animationen ist die [GSAP](http://greensock.com/gsap) Bibliothek.

***Weitere Informationen:***

 - [http://www.smashingmagazine.com/2014/09/04/animating-without-jquery/](http://www.smashingmagazine.com/2014/09/04/animating-without-jquery/)
 - [https://css-tricks.com/myth-busting-css-animations-vs-javascript/](https://css-tricks.com/myth-busting-css-animations-vs-javascript/)
 - [http://davidwalsh.name/css-js-animation](http://davidwalsh.name/css-js-animation)


#### Durchlaufen Sie keine Schleifen unn�tig

Wenn Sie eine Aktion auf eine Sammlung von Elementen anwenden wollen, m�ssen Sie sie nicht unbedingt durchschleifen.

Zum Beispiel bei der Zuweisung einer Klasse, ist das unn�tig:

```
$("li").each(function () {
    $(this).addClass("planet");
});
```

Stattdessen k�nnen Sie einfach folgenden Ausdruck verwenden:

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


#### Zust�ndigkeitskette

Gerade weil Sie JQuery Methoden verketten k�nnen, bedeutet das nicht, dass Sie es auch immer sollten.

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

Versuchen Sie einen Weg zu finden, um eine Logik so knapp wie m�glich zu schreiben, ohne dabei die Lesbarkeit zu beeintr�chtigen.


### JQuery PROs und CONs:

JQuery ist grossartig. Es ist einfach zu bedienen, gut dokumentiert, und die meisten Entwickler haben zumindest einige Erfahrung, es zu benutzen. Es behandelt eine Reihe von seltsamen Browser-Macken und macht in der Regel das Leben eines Entwicklers einfacher.

Dar�ber hinaus gibt es eine Menge von Plugins zur Verf�gung, um die Durchf�hrung von gemeinsamen Funktionalit�tsanforderungen, ohne dass man eine Menge von benutzerdefinierten Code schreiben muss.

Aber JQuery ist nicht immer die richtige Wahl f�r jede Situation.

Menschen lernen JQuery oft, bevor sie JavaScript verwenden lernen. Als solches kann es schwierig sein zu wissen, wie man aus dem Web heruntergeladene Skripte ver�ndert.

JQuery UI ist insbesondere eine grosse Bibliothek, w�hrend kleinere Alternativen existieren, die m�glicherweise den gleichen Job zu einem Bruchteil der Dateigr�sse machen k�nnten.

Bei der Entscheidung �ber die beste L�sung, betrachten Sie Alternativen, wie bspw. die Verwendung von kleineren Bibliotheken.

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

Deklarieren Sie Variablen immer mit dem `var` Schl�sselwort bevor Sie sie zum ersten Mal verwenden.

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

Es gibt Vorteile f�r den ersten Ansatz, da es leicht ist, das zweite Beispiel versehentlich kaputt zu machen (z.B. indem ein Komma ein Semikolon vergessen wird).


***Weitere Informationen***

 - [http://benalman.com/news/2012/05/multiple-var-statements-javascript/](http://benalman.com/news/2012/05/multiple-var-statements-javascript/)
 - [http://danhough.com/blog/single-var-pattern-rant/](http://danhough.com/blog/single-var-pattern-rant/)
 - [http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
 - [http://james.padolsey.com/javascript/js-adolescence/](http://james.padolsey.com/javascript/js-adolescence/)


### Nameskonventionen

W�hlen Sie eine Namenskonvention f�r Variablen und Funktionen und bleiben Sie dabei.

Es gibt einige ziemlich h�ufige Namenskonventionen f�r JavaScript:

  - `camelCase` f�r Funktionen, Variablen und Objekte.
  - `PascalCase` f�r Konstrukteure und Klassen.

Wenn Sie diese Namenskonvention verwenden, verwenden Sie keine Unterstriche in Variablennamen.

Verwenden Sie beschreibende Namen anstelle von Kurznamen, wo m�glich - schreiben Sie Code, der auch zuk�nftig noch lesbar ist und �berlassen Sie die Optimierung einem Minifier.

Bei der Benennung von Funktionen verwenden Sie *Verben*, um die Art der Funktion zu beschreiben:

```
flyRocketShip();
fireBoosters();
returnToEarth();
eatBiscuit();
```

### "use strict"

Am Anfang einer Funktion sollten Sie das `"use strict"` Statement hinzuf�gen:

```
function flyToMars () {

    "use strict";

    ...

}
```

Damit wird der JavaScript-Interpreter f�r die Dauer dieser Funktion (dem aktuellen *Scope*) in einen *strikten* Kontext gestellt.

Dies �ndert die Natur von einigen JavaScript-Fehlern, die sonst schweigend ausfallen w�rden - stattdessen verursachen sie jetzt Ausnahmen. Dies ist eine gute Sache, denn Sie wollen potenzielle Fehler finden und beheben, anstatt sie unbemerkt zu lassen.

Zum Beispiel, stellt der Strict-Mode sicher, dass Sie eine Variable mit `var` deklarieren m�ssen, bevor Sie sie verwenden k�nnen.

Es kann auch dazu f�hren, dass Code (potenziell) schneller l�uft (marginal) als nicht-strikter Code.

***Weitere Informationen:***

 - [http://ejohn.org/blog/ecmascript-5-strict-mode-json-and-more/](http://ejohn.org/blog/ecmascript-5-strict-mode-json-and-more/)
 - [http://www.nczonline.net/blog/2012/03/13/its-time-to-start-using-javascript-strict-mode/](http://www.nczonline.net/blog/2012/03/13/its-time-to-start-using-javascript-strict-mode/)


### Primitive Typen

Variablen k�nnen einfache St�cke von Informationen wie Texte (*Strings*) und Zahlen speichern:

 - String: `"hello"`
 - Boolean: `true`
 - Zahlen: `3.14`

Beim Erstellen einer Variablen, die einer dieser (primitiven) Typen ist, ist die neue Variable eine ***Kopie*** des Originals. Das �ndern der neuen Variablen bel�sst das Original unver�ndert:

```
var myPlanet = "Earth";
var yourPlanet = myPlanet;
yourPlanet = "Venus";

// myPlanet === "Earth", yourPlanet === "Venus"
```


### Objekttypen

Variablen k�nnen auch komplexere Informationen speichern.

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

Wenn Sie eine neue Variable erstellen, indem Sie ihren Wert einer vorhandenen Variablen zuordnen, die einer dieser komplexen Typen ist, wird es ***die urspr�ngliche Variable*** referenzieren, anstatt sie zu kopieren. Daher �ndert jede �nderung der neuen Variablen *auch* die urspr�ngliche Version:

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

In JavaScript sieht man h�ufig anonyme Funktionen. Wie der Name (ironisch) vorschl�gt, sind sie Funktionen ohne Namen:

```
function () {
    ...
}
```

Sie werden niemals auf eigene Faust benutzt, wie zum Beispiel im Codeblock. Stattdessen werden sie als Teil einer anderen Funktion verwendet. Ein h�ufiges Auftreten bei der Verwendung von JQuery ist die Verwendung einer anonymen Funktion wie folgt:

```
$("a").click(function () { ... });
$(document).ready(function () { ... });
```

Dies k�nnte leicht umgeschrieben werden, um eine benannte Funktion zu verwenden:

```
function doSomethingWhenClicked () { ... }
$("a").click(doSomethingWhenClicked);

function init () { ... }
$(document).ready(init);
```

Anonyme Funktionen werden h�ufig verwendet, wenn man *einige Befehle, die f�r einen bestimmten Zweck verwendet werden sollen,* verkapseln kann, aber es unwahrscheinlich ist, dass dieses St�ck Code anderweitig wieder verwendet wird.

Anonyme Funktionen sind schwer zu debuggen und k�nnen nicht wiederverwendet werden. Ein besserer Ansatz ist, sie niemals zu benutzen und stattdessen immer wieder Funktionen zu nennen und zu benennen.


***Weitere Informationen:***

 - [http://toddmotto.com/avoiding-anonymous-javascript-functions/](http://toddmotto.com/avoiding-anonymous-javascript-functions/)
 - [http://learn.jquery.com/code-organization/beware-anonymous-functions/](http://learn.jquery.com/code-organization/beware-anonymous-functions/)


### Wahr und unwahr

Einige Bedingungen geben einen Wert zur�ck, der ein *boolean* `true` oder` false` ist:

```
var $firstPlanet = $(".planet").first();
var isMercury = ($el.text() === "Mercury"); // true
```

Andere Bedingungen werden einen Wert zur�ckgeben, der nicht streng `true` oder `false` ist, sondern als *true* oder *false* behandelt werden kann:

```
var $planets = $(".planets");
if ($planets.length) {
    flyCloser();
} else {
    flyToNextStar();
}
```

In diesem Szenario wird `$planets.length` weder `true`, noch `false` sein. Stattdessen hat es den numerischen Wert `0` oder h�her. Wenn sein Wert `0` ist, ist das *false*, w�hrend wenn der Wert gr�sser als `0` ist, gilt es als *true*.

Ein weiteres Beispiel, ob ein Eingabefeld einen beliebigen Text enth�lt:

```
var $name = $("input#name");
if (!$name.val()) {
    alert("Don't forget to add your name!");
}
```

Beachten Sie das `!` vor `$name.val()` - das kehrt die Bedingung um (und verwandelt es in Boolean), um einen negativen Wert anstatt positiv zu pr�fen - ob das Textfeld leer ist und daher *false*. In dieser Situation ist es sinnvoll, `!` zu verwenden, weil wir nur die Funktionalit�t hinzuf�gen wollen, wenn es leer ist, und so spart man sich eine leere `if`-Anweisung und einen zus�tzlichen `else`-Block zu schreiben.

Manchmal sieht man `!!` vor einer Bedingung. Dies verwandelt einen `true` oder `false` Wert in ein echtes boolesches `true` oder `false`, aber im Gegensatz zu einem einzigen Ausrufezeichen wechselt es nicht umgekehrt seinen Zustand.

```
var $name = $("input#name");
if (!!$name.val()) {
    alert("Well done for having a name!");
} else {
    alert("You probably should have a name...");
}
```

Das folgende wird einen *false* Wert zur�ckgeben:

 - `false`
 - `0`
 - `""`
 - `null`
 - `undefined`
 - `NaN`

Alles andere wird einen *true* Wert zur�ckgeben.

Seien Sie sich jedoch bewusst, dass `true` und `false` Werte zu Fehlern f�hren k�nnen - zum Beispiel, wenn Sie durch ein Array schleifen, wird der erste Index 0 sein, der als *false* behandelt wird.

***Weitere Informationen:***

 - [http://www.sitepoint.com/javascript-truthy-falsy/](http://www.sitepoint.com/javascript-truthy-falsy/)
 - [http://james.padolsey.com/javascript/truthy-falsey/](http://james.padolsey.com/javascript/truthy-falsey/)


### Strikte Komparatoren (===)

Strenge Komparatoren �berpr�fen den * Typ * einer Variablen zusammen mit ihrem Wert.

Wenn Sie `==` (oder `!=`) verwenden, k�nnen Sie Probleme mit dem testen von `null`-Werten, Verwechselung von Zahlen und Strings sowie Verwechselung von `0` mit dem Boolean `false` feststellen.

```
"1" == 1;  // true
"2" != 2;  // false
```

Stattdessen sollten Sie `===` (oder `!==`) benutzen, um sowohl den Wert, als auch den Typ ztu pr�fen:

```
"1" === 1; // false
"2" !== 2  // true
```

Im Allgemeinen ist es eine gute Praxis, immer einen strengen Komparator zu benutzen.

Unerwartete Fehler k�nnen oft auftreten, wenn Formulareingaben gegen erwartete Werte getestet werden. Es kann notwendig sein, Zahlen in Strings (oder umgekehrt) umzuwandeln. Eine einfache M�glichkeit das zu testen ist zu schauen, was f�r einen *Typ* ein Wert hat.

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

Beim Schreiben von Bl�cken wie `if`-Anweisungen und `for`-Loops ist es technisch nicht zwingend erforderlich, geschweifte Klammern hinzuzuf�gen, da folgende Aussage angenommen werden kann:

```
// works as expected
if (isEarth)
    landRocket();
```

Allerdings ist es gute Praxis, immer geschweifte Klammern zu verwenden. Es ist einfach, Bedingungen zu einer `if`-Anweisung zu einem sp�teren Zeitpunkt hinzuzuf�gen. Aber es ist mitunter nicht so leicht zu merken, dass es keine geschweiften Klammern gab:

```
if (isEarth)
    landRocket();    // controlled by the if statement
    takeOffHelmet(); // not bound to the if statement, will always happen!
```


#### Tabs vs. Leerzeichen

Entscheiden Sie sich  f�r Tabs oder Leerzeichen, aber mischen Sie nicht. Zum schnellen Einr�cken empfehlen sich Tabs. Also sollten Sie diese auch m�glichst verwenden.


#### Anf�hrungszeichen

Entscheiden Sie sich f�r einfache Anf�hrungszeichen oder f�r doppelte, aber mischen Sie nicht. Einfache Anf�hrungszeichen (single quotes) erh�hen die Lesbarkeit, wenn sie h�ufig verwendet werden.


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

Benutzen Sie keine zus�tzliches Komma am Ende einer Liste, weil das Fehler in �lteren Browsern verursachen kann:

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

Anstatt `console.log`-Meldungen in einer Anwendung zu hinterlassen oder sie zur Entwicklung da lassen, aber manuell zu entfernen, wenn der Code "vollst�ndig" ist, k�nnen Sie eine einfache Debugging-Bibliothek verwenden, die man anstelle von `console.log` anruft. Dies erm�glicht Ihnen, Debug-Nachrichten in Ihrem Code zu lassen, die global mit einer einzigen Konfigurationsoption ein- und ausgeschaltet werden k�nnen.

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

Wenn ein Browser in einem HTML-Dokument ein `<script>`-Tag findet, h�rt er standardm�ssig auf, den HTML-Code zu parsen, bis die *script* -Datei heruntergeladen und analysiert wurde.

Aus diesem Grund war die Konvention, dass `<script>` Elemente in HTML-Seiten am unteren Rand der Seite, kurz vor dem Schliessen `</body>` Tags hinzugef�gt werden, so dass sie nach dem Rest gelesen werden, wenn das HTML wurde bereits geparst wurde.

Es gibt M�glichkeiten, dieses Verhalten zu �ndern, indem Sie dem Skript-Tag Attribute wie `async` oder `defer` geben.

```
<script src="venus.js"></script>
<script async src="earth.js"></script>
<script defer src="mars.js"></script>
```


#### Async

Asynchrones Skripte halten das Herunterladen des HTML-Dokuments nicht an. Sie werden sobald wie m�glich ausgef�hrt. W�hrend dessen pausieren Sie das Parsen des HTML-Dokuments. Zudem werden sie in der der Reihenfolge ausgef�hrt, in der das Herunterladen abgeschlossen wurde.


#### Defer

Skripte mit Defer-Attribut werden parallel zu dem HTML-Dokument heruntergeladen, aber ihre Ausf�hrung wird verz�gert, bis das HTML-Parsing abgeschlossen ist. Sie werden in der Reihenfolge ausgef�hrt, in der sie im Dokument erscheinen.

�ltere Versionen von Internet Explorer haben schlechte/keine Unterst�tzung f�r das Defer-Attribut.


***Weitere Informationen:***

 - [http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html](http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)


### js- Klassennamen f�r JS Hooks

Wenn Sie ein HTML Element haben, dass Sie mit JavaScript manipulieren wollen, geben Sie ihm einen Klassennamen (oder ein Data-Attribut), der mit `js-` beginnt. Das macht die Unterscheidung zwischen Klassen f�r Style und Klassen f�r JavaScript einfacher.

***Weitere Informationen:***

 - [http://philipwalton.com/articles/decoupling-html-css-and-javascript/](http://philipwalton.com/articles/decoupling-html-css-and-javascript/)
 - [http://davidwalsh.name/css-do](http://davidwalsh.name/css-do)


### Tern�re Operatoren

Tern�re Operatoren sind ein schneller Weg, um mit einer if/else Anweisung einen einzelnen Wert zu setzen:

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

Betrachten Sie die K�rze vs. Lesbarkeit bei der Pr�fung, wenn Sie tern�re Operatoren verwenden.

***Weitere Informationen:***

 - [http://davidwalsh.name/learning-ternary-operators-tips-tricks](http://davidwalsh.name/learning-ternary-operators-tips-tricks)


### 0.1 + 0.2

H�ten Sie sich vor JavaScripts sonderbaren Macken:

```
0.1 + 0.2 // ...
0.1 + 0.2 === 0.3 // ...
```

Dies tritt in der Regel nicht auf, aber es kann Probleme verursachen.

***Weitere Informationen:***

 - [http://stackoverflow.com/a/588014](http://stackoverflow.com/a/588014)


### �bergeben von Objekten an Funktionen

Beim Erstellen einer Funktion, wenn Sie mehr als ein paar Argumente erwarten, �berlegen Sie, ein einzelnes Objekt anstatt viele Argumente zu �bergeben.

Es gibt ein paar Vorteile f�r diesen Ansatz:

  1. Die Reihenfolge der Argumente spielt keine Rolle
  2. Die Parameter sind benannt und so leichter zu verweisen
  3. Wenn einige der Argumente optional sind, wird automatisch `null` f�r solche Argumente in die Funktion �bergeben

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

Anstatt Funktionalit�t zu haben, die nicht benutzt wird, wenn JavaScript nicht vorhanden ist, versuchen Sie lieber sicherzustellen, dass der urspr�nglich generierte Seiteninhalt f�r Personen, die JavaScript deaktiviert haben, benutzbar ist:

```
<p class="js-relative-date">14th June 2015</a>
```

Dann mit JavaScript k�nnen Sie f�r diejenigen, die es aktiviert haben, diese Elemente erkennen und die Funktionalit�t verbessern:

```
var $relativeDates = $(".js-relative-date");
makeDatesRelative($relativeDates);
```

***Weitere Informationen:***

 - [https://www.gov.uk/service-manual/making-software/progressive-enhancement.html](https://www.gov.uk/service-manual/making-software/progressive-enhancement.html)
 - [http://alistapart.com/article/understandingprogressiveenhancement](http://alistapart.com/article/understandingprogressiveenhancement)


## JavaScript Style-Guide

Es gibt viele M�glichkeiten, JavaScript zu schreiben. Das Festhalten an den Regeln, die in einem _style guide_ (oder _coding standards_ Dokument) angelegt sind, bedeutet, dass Sie Code konsequent �ber ein Team hinaus schreiben k�nnen.

Das Ziel sollte nicht nur sein, die Arbeit zu erledigen, sondern logisch wartbaren Code zu schreiben.

(Als Referenz gibt es beliebte [CSS] (http://cssguidelin.es/) und [SASS] (http://sass-guidelin.es/) �quivalente.)

Es gibt keinen Grund, eigene Codierungsstandards zu schreiben, wenn andere die harte Arbeit f�r Sie bereits getan haben.

Eine n�tzliche Zusammenfassung, warum es sich lohnt, einen JavaScript-Style-Guide zu verwenden:

  - [http://addyosmani.com/blog/javascript-style-guides-und-beautifiers/](http://addyosmani.com/blog/javascript-style-guides-and-beautifiers/)

Einige JavaScript-Style-Guides:

 - [https://github.com/rwaldron/idiomatic.js](https://github.com/rwaldron/idiomatic.js)
 - [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
 - [http://seravo.fi/2013/javascript-the-winning-style](http://seravo.fi/2013/javascript-the-winning-style)
 - [http://www.2ality.com/2013/07/meta-style-guide.html](http://www.2ality.com/2013/07/meta-style-guide.html)


## Ajax

Ajax ist der Begriff, der �blicherweise verwendet wird, um die Technik zum Ausf�hren eines _HTTP Requests_ mit JavaScript zu beschreiben, um Inhalte von einem Server (oder einer anderen Datenquelle von Drittanbietern) abzurufen, ohne die aktuelle Seite aktualisieren zu m�ssen.

Viele JavaScript-Bibliotheken wie JQuery bieten die M�glichkeit, Ajax-Anfragen zu machen.

Ajax kann die HTTP-Methoden *GET* und *POST* verwenden, um mit Servern zu interagieren. Beide *GET* und *POST* k�nnen verwendet werden, um Daten zu senden und zu empfangen, aber sie haben ihre Unterschiede, die jedes f�r verschiedene Szenarien geeignet machen.


### GET Requests

Ein Ajax *GET*-Request wird im Allgemeinen verwendet, um Informationen von einem Server abzurufen. Um ein Beispiel mit JQuery zu geben:

```
$.get("/api/planets/");
```

Dies fragt die URL *http://[domain]/api/planets/* ab.

Es ist m�glich, mit dem Request auch Parameter an den Server zu �bergeben:

```
$.get("/api/planets/", { planet: "Earth"});
```

JQuery konvertiert den zweiten Parameter in einen Abfrage-String und transformiert die angeforderte URL in: *http://[Domain]/api/planets/?planet=Earth*

In den beiden obigen Beispielen k�nnen die Daten vom Server angefordert worden sein, aber es geschieht nichts, wenn diese Daten empfangen werden. Es ist notwendig zu definieren, was getan werden soll, sobald Daten zur�ckgegeben wurden, oder wenn es einen Fehler gab.

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

Wie bereits erw�hnt, ist es m�glich (und empfohlen), diese Funktionen separat zu definieren, anstatt anonyme Funktionen zu verwenden.

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

Beim Senden von Informationen an einen Server sollten *POST*-Requests verwendet werden. Sie beschr�nken nicht die Datenmenge, die an den Server gesendet werden kann, wie bei einem *GET*-Request, und sie k�nnen auch zum Hochladen von Dateien verwendet werden.

Mit *POST*-Requests kommt die Information, die an den Server gesendet wird, oft aus Formulareingaben.

Mit JQuery k�nnen *POST*-Requests in �hnlicher Weise gemacht werden:

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

Die beiden obigen Beispiele gehen davon aus, dass der Server, der die Daten bereitstellt, derselbe Server ist, auf dem die Website liegt. Es gibt zwei M�glichkeiten, mit einem anderen Webserver zu interagieren. Dies ist n�tzlich, wenn es um APIs geht, die von anderen Diensten bereitgestellt werden.


#### CORS

Wenn Sie versuchen, auf einen anderen Server �ber JavaScript zuzugreifen, k�nnen aufgrund einer *Sicherheitsrichtlinie* Fehler in der Konsole angezeigt werden, es sei denn, der Host-Server hat *Cross-Origin Ressource Sharing* (CORS) aktiviert. Obwohl es nicht schwer zu aktivieren ist, gibt es Sicherheitsimplikationen, die verstanden und akzeptiert werden m�ssen, bevor Sie sich f�r die Unterst�tzung von CORS entscheiden.

***Weitere Informationen***

 - [http://enable-cors.org/](http://enable-cors.org/)
 - [http://dev.housetrip.com/2014/04/17/unleash-your-ajax-requests-with-cors/](http://dev.housetrip.com/2014/04/17/unleash-your-ajax-requests-with-cors/)


#### JSONP

Eine alternative Option ist, *JSONP* anzufordern, wenn der Host-Server es bereitstellt.

Dies umgeht das *same-origin* Sicherheitsproblem, indem der Host-Server die angeforderten Daten in ein JavaScript-Objekt eingewickelt. Dies wird dann in die urspr�ngliche Webseite eingebettet.

Wie immer bietet JQuery eine einfache M�glichkeit, JSONP zu verwenden, was m�glicherweise eine einfache Interaktion mit Drittanbieter-APIs erm�glicht.

***Weitere Informationen***

 - [http://www.sitepoint.com/jsonp-examples/](http://www.sitepoint.com/jsonp-examples/)
 - [http://json-p.org/](http://json-p.org/)
 - [https://learn.jquery.com/ajax/working-with-jsonp/](https://learn.jquery.com/ajax/working-with-jsonp/)


## Promises

Bei der Erstellung der Ajax-Anfragen wurden drei Funktionen definiert, um sie zu begleiten:

 - Eine `done` Funktion, die ausgef�hrt wird, wenn der Ajax-Request erfolgreich war
 - Eine `fail` Funktion, die ausgef�hrt wird, wenn der Ajax-Request nicht erfolgreich war
 - Eine `always` Funktion, die ausgef�hrt wird, wenn der Ajax-Request abgeschlossen wurde, unabh�ngig vom Ergebnis

Eine alternative Methode zum Ausl�sen einer Funktion, wenn die Ajax-Anforderung abgeschlossen ist, ist ein *Promise* zu verwenden.

Das Erstellen eines *Promise* ist einfach, mit �hnlicher Syntax zu dem, was bereits gezeigt wurde:

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

Der Vorteil der Verwendung eines *Promise* ist die F�higkeit, eine Anzahl von Funktionen zu verkn�pfen, die asynchron auftreten, wobei sp�tere Funktionen ausgel�st werden, sobald fr�here Funktionen erfolgreich abgeschlossen sind.

***Weitere Informationen:***

 - [https://api.jquery.com/promise/](https://api.jquery.com/promise/)
 - [https://www.promisejs.org/](https://www.promisejs.org/)
 - [http://www.html5rocks.com/en/tutorials/es6/promises/](http://www.html5rocks.com/en/tutorials/es6/promises/)
 - [http://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html](http://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html)


## Callbacks

Eine Anzahl der oben dargestellten Beispiele ist m�glich, weil JavaScript Funktionen als Argumente an andere Funktionen �bergeben kann.

Dies nennt man *Callback*.

```
function init () {
    // define the callback
}

// run the callback on DOM load
$(document).ready(init);
```

Callbacks nutzen die *asynchrone* Natur von JavaScript, die die M�glichkeit bietet, Befehle zum richtigen Zeitpunkt auszuf�hren. Das obige Beispiel zeigt, dass die *init*-Funktion aufgerufen wird, wenn das DOM das Laden beendet hat.

Weitere Beispiele f�r R�ckrufe werden in den folgenden Abschnitten gezeigt.

***Weitere Informationen***

 - [https://gist.github.com/infovore/b6c4bc71a1bffdfd9846](https://gist.github.com/infovore/b6c4bc71a1bffdfd9846)
 - [http://stackoverflow.com/questions/9596276/how-to-explain-callbacks-in-plain-english-how-are-they-different-from-calling-o](http://stackoverflow.com/questions/9596276/how-to-explain-callbacks-in-plain-english-how-are-they-different-from-calling-o)


## Timeouts

Eine der h�ufigsten Verwendungen eines Callbacks ist, eine Funktion nach einer festgelegten Zeitspanne auszul�sen, anstatt sofort.

Manchmal will man jetzt nichts machen, aber sp�ter soll etwas passieren.

```
function doSomethingInTheFuture () {
    alert("It is now the future, here's your jet pack");
}

var timeout = setTimeout(doSomethingInTheFuture, 5000); // 5 seconds
```

Dieser Timeout wird einmal ausgef�hrt, 5 Sekunden ab dem Zeitpunkt der Zeit�berschreitung.

Es ist auch m�glich, eine Funktion wiederholt in einem eingestellten Intervall auszul�sen:

```
function doSomethingContinuously () {
    alert("Is this annoying yet?");
}

var interval = setInterval(doSomethingContinuously, 10000); // every 10 seconds
```

Ein praktischer Nutzen f�r Timeouts und Intervalle k�nnte sein, eine Ajax-Anfrage durchzuf�hren, um nach neuen Inhalten alle paar Sekunden zu suchen.

Timeouts und Intervalle k�nnen abgebrochen werden:

```
clearTimeout(timeout);
clearInterval(interval);
```

Von den beiden gibt es Nachteile bei der Verwendung von Intervallen. Insbesondere wenn sie in einem inaktiven Browser-Tab laufen, kommen sie in die Warteschlange, was bedeutet, dass die Callback-Funktion mehrfach aufgerufen wird (die Warteschlange wird abgearbeitet), wenn der Benutzer endlich wieder den inaktiven Tab aufgerufen hat. Aus diesem Grund wird normalerweise empfohlen, Timeouts anstatt Intervallen zu verwenden.

***Weitere Informationen***

 - [http://ejohn.org/blog/how-javascript-timers-work/](http://ejohn.org/blog/how-javascript-timers-work/)
 - [http://stackoverflow.com/q/6183463](http://stackoverflow.com/q/6183463)


## Events

Eine weitere gebr�uchliche Anwendung von Callbacks sind *events*.

Ein Ereignis kann auf folgende Weise gedacht werden:

> *Wenn dies passiert, mach das*

Die h�ufigste Verwendung von Events h�rt auf Interaktionen mit DOM-Elementen, wie z.B. einen Klick auf einen bestimmten Link oder die Einreichung eines Formulars.

Das folgende Beispiel veranschaulicht, wie man JQuery verwendet, um einen *Event-Listener* einem DOM-Element hinzuzuf�gen. Es l�st eine *Callback*-Funktion aus, wenn der Link geklickt wird:

```
function linkClicked () {
    alert("The link was clicked!");
}

$(".js-my-link").on("click", linkClicked);
```

Es ist m�glich, Event-Listener ohne Verwendung von JQuery hinzuzuf�gen, aber bestimmte �ltere Browser verwenden etwas unterschiedliche Syntax, und erspart man sich mit einer Bibliothek, dass man die gleiche Funktion auf zwei leicht unterschiedliche Weisen definieren muss.

Im obigen Beispiel hat das DOM-Element ein `class`-Attribut, das mit `js-`beginnt - wie oben diskutiert wurde, ist dies eine n�tzliche Konvention, die es uns erm�glicht, zwischen CSS-Klassen zu unterscheiden, die f�r das Styling verwendet werden und diejenigen, die sind F�r JavaScript verwendet.

Obwohl Ereignisse auf fast jedem HTML-Element platziert werden k�nnen, ist es f�r Zug�nglichkeitszwecke vorteilhaft, sie auf `<a>` Elemente zu setzen und Eingabesteuerungen zu bilden, da dies eine einfachere Tastaturnavigation erm�glicht.

***Weitere Informationen:***

 - [http://eloquentjavascript.net/14_event.html](http://eloquentjavascript.net/14_event.html)
 - [http://www.kirupa.com/html5/javascript_events.htm](http://www.kirupa.com/html5/javascript_events.htm)


### Standard-Events verhindern

Beim Hinzuf�gen von benutzerdefinierten Ereignissen k�nnen wir manchmal den urspr�nglichen Link von der Ausf�hrung der Standardaktion abhalten.

Zum Beispiel k�nnen wir einen Link haben, mit dem wir eine bestimmte Funktionalit�t ausl�sen wollen, aber f�r Benutzer ohne JavaScript, die auf denselben Link klicken, w�rde die gesamte Seite aktualisiert.

Wenn ein Ereignis ausgel�st wurde, ist standardm�ssig ein `event`-Objekt verf�gbar, das an die Callback-Funktion �bergeben werden soll.

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

Ein Closure wird gebildet, wenn eine *verschachtelte* Funktion ausserhalb der Funktion, in der sie definiert wurde, zug�nglich gemacht wird, so dass sie ausgef�hrt werden kann, nachdem die �ussere Funktion zur�ckgegeben wurde. Man beh�lt den Zugriff auf die lokalen Variablen, Argumente und inneren Funktionsdeklarationen seiner �usseren Funktion.

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

Ein �bliches Beispiel f�r eine Closure ist das Modulmuster, wie nachstehend gezeigt. Dies gibt ein einfaches Objekt zur�ck, das Verweise auf Methoden enth�lt, die in der �bergeordneten Funktion definiert sind.

Closures sind eine n�tzliche Methode, um komplexe Funktionalit�t zu schaffen und gleichzeitig den Umfang zu sch�tzen.

***Weitere Informationen***

 - [https://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/](https://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/)


## Objektliterale

Wie oben gezeigt wurde, sind Objekte eine n�tzliche Methode, um verwandte Informationen zusammen in einer einzigen Variablen zu speichern.

```
var planet = {
    name: "mars",
    radius: 3396,
    distanceFromSun: 227900000
};
```


### Funktionen in Objekten

Objekte sind f�r mehr als nur das Sammeln von Daten n�tzlich, da sie auch Funktionen enthalten k�nnen.

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

Um die Methode eines Objekts aufzurufen, verweisen Sie zuerst auf den urspr�nglichen Variablennamen, gefolgt von dem Funktionsnamen:

```
var planetName = planet.getName(); // "mars"
```

Das Speichern von verwandten Eigenschaften und Methoden innerhalb eines Objekts kapselt diese verwandten Funktionen in einer einzigen Variablen zusammen.

Es gibt m�gliche Probleme mit diesem Ansatz - vor allem, dass es f�r andere Skripte m�glich ist, auf interne Teile eines Objekts zuzugreifen (und zu �berschreiben), zum Beispiel in dem oben definierten `planet`-Objekt:

```
planet.name = "earth"; // override previous value
```

Die Verwendung von Objekten als Grundlage f�r die Speicherung von Variablen und Funktionen ist ein wichtiges Merkmal des Schreibens von wartbaren JavaScript. Es sind komplexere Methoden vorhanden, um zu verhindern, dass Daten in einem Objekt �berschrieben werden (ob versehentlich oder absichtlich). Diese werden in den folgenden Abschnitten besprochen.

***Weitere Informationen***

 - [http://www.sitepoint.com/back-to-basics-javascript-object-syntax/](http://www.sitepoint.com/back-to-basics-javascript-object-syntax/)
 - [http://rmurphey.com/blog/2009/10/15/using-objects-to-organize-your-code/](http://rmurphey.com/blog/2009/10/15/using-objects-to-organize-your-code/)


### *this* Schl�sselwort

In JavaScript ist der Wert der Variablen `this` besonders. Ihr Wert �ndert sich je nachdem wo und wie sie verwendet wird.

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

Der Wert von `this` kann sich �ndern, wenn er in verschiedenen Kontexten verwendet wird, wie sp�ter gezeigt wird.

***Weitere Informationen***

 - [https://gist.github.com/cjohansen/4135065](https://gist.github.com/cjohansen/4135065)
 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)


## Scope

Wenn Sie eine Variable oder eine Funktion erstellen, wird sie standardm�ssig im *globalen* Scope definiert. Dies bedeutet, dass sie �berall im Code verf�gbar ist.


### Scope verstehen

Variablen, die im *globalen* Scope erstellt wurden, sind f�r Funktionen zug�nglich, die im gleichen Bereich definiert sind:

```
// this variable is defined in the global scope
var planet = "Earth";

function enthuse () {
    // this is now the local scope, but it has access to variables
    // defined in the global scope

    alert("I like the planet " + planet); // "I like the planet Earth"
}
```

Variablen, die innerhalb der Funktionen definiert sind, sind nur *lokal* in dieser Funktion und nicht ausserhalb verf�gbar:

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


Variablen, die in Funktionen �bergeben werden, werden auch Teil des *lokalen* G�ltigkeitsbereichs und �berschreiben daher die Variable des gleichen Namens, die im globalen Geltungsbereich deklariert wurde:

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

Die Flexibilit�t des Scopes kann praktisch sein, aber gleichermassen kann es Probleme verursachen, besonders wenn es nicht ber�cksichtigt wird.

Das Hauptproblem bei der Arbeit im globalen Geltungsbereich ist, dass es einfach ist, versehentlich eine Variable zu �berschreiben, indem man eine andere mit demselben Namen deklariert. JavaScript (in einem Webbrowser) bietet keine Isolierung des Scopes �ber Dateien, d.h. alle Code-Freigaben nutzen den gleichen globalen Bereich, es sei denn, es werden Anstrengungen unternommen, um St�cke des Codes in separate lokale Bereiche zu isolieren.

Viele Webseiten verwenden ihren eigenen JavaScript-Code zusammen mit Drittanbieter-JavaScript, wie zum Beispiel f�r das Tracking oder das Einf�gen von Werbung in eine Website. Es ist wichtig, dass dieser Drittanbieter-Code isoliert behandelt wird, so dass er kein anderes JavaScript st�rt.

Der beste Weg, um Probleme mit dem Scope zu vermeiden, besteht darin, alle Codes innerhalb einzelner lokaler Bereiche einzukapseln, so dass nur wenige (wenn �berhaupt) Variablen im globalen Geltungsbereich definiert sind, was bedeutet, dass sie nicht miteinander in Konflikt stehen.

Methoden dazu werden in K�rze er�rtert.


## Modularit�t

Beim Aufbau einer grossen und komplexen Website, kann eine erhebliche Menge an JavaScript geschrieben werden, um seine verschiedenen Funktionen der Funktionalit�t zu kontrollieren. Obwohl bestimmte Aspekte m�glicherweise miteinander interagieren m�ssen, k�nnen diese St�cke von Code separat verwaltet werden.

Ohne Versuche, diesen Code zu organisieren, kann es schnell schwierig werden, jede Funktionalit�t zu verwalten und zu pflegen, ohne versehentlich andere Teile zu beeintr�chtigen.

Die Organisation von Code in *modulare Komponenten* bedeutet, dass jeder Teil des Codes getrennt von allen anderen Komponenten gehalten werden kann.

Die Verwendung von modularen Komponenten hilft auch bei der Verwaltung des *Scopes* - jede Komponente kann in ihrem eigenen Umfang und nicht in dem globalen Geltungsbereich definiert werden, wodurch das Potenzial f�r eine beliebige Variable reduziert wird, um eine andere versehentlich zu �berschreiben.

Das Aufteilen von JavaScript in separate Dateien ist ein guter Anfang, um logische Komponenten zu identifizieren. Aber das sch�tzt noch nicht das Scope.

Es gibt eine Reihe von M�glichkeiten, um JavaScript in modularen Komponenten zu organisieren, wie unten diskutiert.


### Namespaces

Eine Methode, um modulare Komponenten zu erstellen, besteht darin, Komponenten in einzelne Objekte zu unterteilen und einen *Namespace* zu definieren, in dem jedes Objekt existiert.

Die folgenden zwei Beispiele zeigen, wie solche Codest�cke in einem einzigen Namespace voneinander getrennt sind.

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

Diese beiden Dateien k�nnten in beliebiger Reihenfolge aufgenommen werden. Die erste Zeile der beiden vewrweist auf die globale Variable `PLANETS`. Wenn es bereits erstellt wurde, wird es nicht �berschrieben. Wenn dies die erste Datei ist, wird ein neues leeres Objekt erstellt.

Innerhalb der beiden obigen Objekte sind alle Variablen sicher und werden nicht gegenseitig �berschrieben.

Zu einem sp�teren Zeitpunkt kann ein anderes Skript auf `PLANETS.mars.init();` oder `PLANETS.earth.init();` oder jede andere Methode oder Eigenschaft, die im Namespace definiert ist, verweisen.

***Weitere Informationen:***

 - [http://elegantcode.com/2011/01/26/basic-javascript-part-8-namespaces/](http://elegantcode.com/2011/01/26/basic-javascript-part-8-namespaces/)


### IIFEs

Eine andere Methode, den globalen Bereich zu vermeiden, besteht darin, Code in eine anonyme Funktion zu schreiben, die sofort ausgef�hrt wird.

Die Syntax daf�r ist:

```
(function () {

    // code goes here...

})();
```

Diese Methode wird als *Immediately Invoked Function Expression* bezeichnet. Der Vorteil der Verwendung eines *IIFE* ist, dass der gesamte Code in einer Funktion gehalten wird, und so seinen eigenen Scope hat, anstatt irgendwelche Variablen oder Funktionen im globalen Bereich.

Die Syntax eines *IIFE* kann in zwei Teilen verstanden werden:

  1. Der erste Teil ist die Definition einer Funktion, die in Klammern umgeben ist, wodurch ein lokaler Bereich erstellt werden kann.
  2. Der zweite Teil ist der zweite Satz von Klammern, der unmittelbar dem ersten folgt, der die Funktion sofort aufruft.

IIFEs sind n�tzlich, wenn Sie einen Code haben, der sofort ausgef�hrt werden muss (z.B. bei der Initialisierung), aber dieser Code muss nicht auf irgendetwas anderes auf der Website verweisen oder nach der Einrichtung referenziert werden. Die anonymen Funktion sch�tzt den Code vor dem Rest der Codebasis, w�hrend die sofortige Funktionalit�t sicherstellt, dass sie initialisiert wird, sobald sie erstellt wurde.


#### IIFEs auslagern

Eine M�glichkeit, in der IIFEs Variablen f�r andere Skripte zur Verf�gung stellen k�nnen, ist eine externe Variable oder *Kontext* zu �bergeben. Im folgenden Beispiel wird der Kontext in der abschliessenden Zeile als das Schl�sselwort `this` (das standardm�ssig auf das `window`-Objekt, den globalen Geltungsbereich) verweist, weitergegeben. Innerhalb der anonymen Funktion wird dieser Parameter mit dem Argument `context` bezeichnet:

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
Diese Methode f�gt `window.myPlanet` zum globalen Geltungsbereich hinzu:

```
window.myPlanet.radius           // 6371
window.myPlanet.getPlanetName()  // "Earth"
```

Mit dem obigen Ansatz ist alles, was nicht explizit im `myPlanet` Objekt gesetzt wurde, nicht durch ein externes Skript zug�nglich.

***Weitere Informationen***

 - [http://benalman.com/news/2010/11/immediately-invoked-function-expression/](http://benalman.com/news/2010/11/immediately-invoked-function-expression/)
 - [http://esbueno.noahstokes.com/post/77292606977/self-executing-anonymous-functions-or-how-to-write](http://esbueno.noahstokes.com/post/77292606977/self-executing-anonymous-functions-or-how-to-write)


### Revealing Module Pattern

Eine andere Methode, um auf Funktionen und Variablen zuzugreifen, die in einem IIFE erstellt wurden, ist, dass sie einen Wert zur�ckgibt.

Ein popul�rer Ansatz ist es, das _Revealing Module Pattern_ zu verwenden, um den Bereich mit einem IIFE zu isolieren und dann ein Objekt von �ffentlich zug�nglichen Parametern (Variablen) und Methoden (Funktionen) zur�ckzugeben.

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

In diesem Beispiel wurde eine einzige globale Variable von `myPlanet` definiert, w�hrend der gesamte Code innerhalb der Funktion seinen eigenen lokalen Bereich hat.

Das Ergebnis ist, dass `myPlanet` die folgenden �ffentlich zug�nglichen Werte hat:

```
myPlanet.radius           // 6371
myPlanet.getPlanetName()  // "Earth"
```

Mit dem obigen Ansatz ist alles, was nicht explizit zur�ckgegeben wurde, nicht durch ein externes Skript zug�nglich.

***Weitere Informationen***

 - [http://alistapart.com/article/the-design-of-code-organizing-javascript](http://alistapart.com/article/the-design-of-code-organizing-javascript)
 - [http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)


### IIFEs, Module Pattern und Namespaces verbinden

F�r grosse Codebasen ist es ein gemeinsamer Ansatz, IIFSs, Module Pattern und Namespaces zu kombinieren, um eine logische Struktur f�r Ihren Code zu erstellen:

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

Der gesamte Code ist in einem einzigen *Namespace* von `MyApp` enthalten, in dem jedes St�ck modularer Code seinen eigenen Namen hat, der einen Satz von �ffentlichen Parametern und Methoden zur�ckgibt.

Im obigen Beispiel erstellt es `MyApp.Accordions` im Namespace, also k�nnte man z.B. `MyApp.Accordions.public()` aufrufen;

Diese Methode wird als Grundlage f�r viele komplexe Codebasen verwendet.

***Weitere Informationen:***

 - [http://addyosmani.com/resources/essentialjsdesignpatterns/book/](http://addyosmani.com/resources/essentialjsdesignpatterns/book/)


## Constructors und das *new* Schl�sselwort

Eine alternative M�glichkeit, modularen Code zu erstellen, besteht darin, neue Objekte zu *konstruieren*, die als *Prototyp* anderer Objekte verwendet werden k�nnen.

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

Beachten Sie die Verwendung des Schl�sselwortes `new` vor dem Namen der Funktion. Dies ist entscheidend daf�r, dass wir eine *Instanz* des `Planet`-Objekts erstellen, anstatt eine Variable zu erstellen, die direkt auf sie verweist.

Um dem `Planet`-Objekt eine Funktion hinzuzuf�gen, die von beliebigen Instanzen referenziert werden kann, musst man sie dem `Prototyp` hinzuf�gen:

```
Planet.prototype.revolve = function () {
    ...
};
```

Das Erstellen von Objekten auf diese Weise kann ihre Vorteile haben, insbesondere bei der Erstellung unterschiedlicher Objekttypen, die Eigenschaften und Methoden voneinander erfassen k�nnen.

***Weitere Informationen***

 - [http://wildlyinaccurate.com/understanding-javascript-inheritance-and-the-prototype-chain/](http://wildlyinaccurate.com/understanding-javascript-inheritance-and-the-prototype-chain/)
 - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)



## App Struktur

Wenn Sie zuerst lernen, JavaScript zu benutzen, kann es verlockend sein, eine einzelne JavaScript-Datei zu erstellen, die jede Funktionalit�t enth�lt, die f�r eine Website ben�tigt wird. Wie bereits gezeigt wurde, kann dies zu Problemen f�hren und schwer zu pflegen sein. Stattdessen sollte die Anwendung in Module zerlegt werden, die jeweils mit einer bestimmten Funktionalit�t umgehen.


### Global Init Location

Bei der Erstellung von modularen Komponenten k�nnte jede f�r die Initialisierung und die Kontrolle ihres eigenen Verhaltens verantwortlich gemacht werden.

Dies ist ein akzeptabler Ansatz, wenn jedes Modul vollst�ndig in sich geschlossen ist und keine zwei Module miteinander kommunizieren m�ssen.

Ein alternativer Ansatz ist es, eine globale `init`-Funktion zu schaffen, die f�r die Initialisierung aller anderen Module verantwortlich ist:

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

Die Kommunikation zwischen den Modulen ist m�glich, indem man ihre �ffentlichen Methoden direkt aus einer anderen Funktion verweist.

Betrachten Sie das folgende vereinfachte Beispiel f�r zwei Module:

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

Zwei Module, die direkt kommunizieren, sind bekannt als *tight coupling* und keine gute Idee. Grunds�tzlich sollten Module niemals einander kennen oder sich direkt anrufen. Stattdessen k�nnen wir eine alternative Methode verwenden, um diese Kommunikation  auf Ereignisse - *publishing* und *subscribing* - zu erm�glichen. Dies wird oft zu *pub/sub* verk�rzt.

Native Events wurden fr�her behandelt, mit einem Beispiel f�r die Erkennung, wenn ein Benutzer auf einen Link (oder ein anderes HTML-Element) klickt und eine JavaScript-Funktion ausl�st. Auch benutzerdefinierte Events k�nnen in �hnlicher Weise erstellt und ausgel�st werden.

Wenn etwas wichtiges in einem Modul passiert, kann es ein Ereignis *ver�ffentlichen*, um dies zu verk�nden.

```
// a new row has been added, announce this
MyApp.pubSub.publish("repeating-row-added");
```

Andere Skripte k�nnen bestimmte Ereignisse *abonnieren* und bestimmte Funktionen ausf�hren, wenn sie auftreten.

```
// listen for new repeating rows being added,
// and init show/hide on them
MyApp.pubSub.addSubscriber("repeating-row-added", initShowHide);
```

Es gibt eine Reihe von verschiedenen *pub/sub* JavaScript-Bibliotheken, die diese Form der Kommunikation zwischen den Modulen erm�glichen.

***Weitere Informationen***

 - [http://tech.pro/blog/1402/five-patterns-to-help-you-tame-asynchronous-javascript](http://tech.pro/blog/1402/five-patterns-to-help-you-tame-asynchronous-javascript)
 - [https://github.com/postaljs/postal.js](https://github.com/postaljs/postal.js)


## Plugins und Bibliotheken

Vor vielen Jahren war es ziemlich �blich, eine Datei mit n�tzlichen wiederverwendbaren Funktionen zu haben, die von Projekt zu Projekt kopiert wurden. Diese *Bibliothek* Datei k�nnte einige praktische Verkn�pfungen liefern und spart Zeit das gleiche Verhalten �ber mehrere Projekte erneut zu schreiben.

Open-Source-Bibliotheken wie JQuery haben die Notwendigkeit von massgeschneiderten komplexen Bibliotheken reduziert, um privat von Einzelpersonen gepflegt zu werden.


### JQuery Plugins

JQuery bietet eine Reihe von n�tzlichen Features, aber von sich aus ist es nicht f�r jede m�gliche Anforderung zu gebrauchen.

JQuery *Plugins* erm�glichen, die Kernfunktionalit�t zu erweitern, um Features wie Slideshows, Tabs, Akkordeons und viele andere Features hinzuzuf�gen.


### Standalone Bibliotheken

Andere Bibliotheken existieren, die �hnliche Vorteile von n�tzlicher Funktionalit�t bieten, ohne eine Abh�ngigkeit von JQuery zu haben.

Zum Beispiel ist die [Moment] (http://momentjs.com) JavaScript-Bibliothek n�tzlich, wenn es um Termine geht. Sie bietet eine Reihe von Features wie die Umwandlung von Daten aus einer Reihe von Formaten und die Berechnung der relativen Daten.

Die Bibliothek [Underscore] (http://underscorejs.org) ist n�tzlich, wenn es um komplexe Daten geht, die verarbeitet und manipuliert werden m�ssen.

Die Bibliothek [D3] (http://d3js.org) eignet sich zum Zeichnen von interaktiven Infografiken.

Dies sind nur einige Beispiele f�r Open-Source-Bibliotheken, die von anderen Entwicklern geschrieben und verf�gbar sind.

Es gibt noch viel mehr: [http://microjs.com/](http://microjs.com/)


### Suchen und Pr�fen von Plugins und Bibliotheken

Oft ist der schwierigste Teil eines Projektes, relevante JQuery-Plugins und Bibliotheken, die helfen k�nnen, zu finden.

Es gibt keinen einzigen Ort, um die Suche zu starten. Oft ist eine hilfreiche Methode, um an einigen Stellen wie [Stack Overflow] (http://stackoverflow.com) und [Google] (http://google.com) nach einer L�sung zu suchen. Wenn Sie ein paar relevante Artikel und Antworten lesen, k�nnen Sie feststellen, dass sie die gleiche L�sung suchen.

Die Mehrheit der n�tzlichen Bibliotheken wird auf [GitHub] (https://github.com/) gespeichert. Dies ist ein g�nstiger Standort f�r Entwickler, um Open-Source-Code kostenlos zu speichern und anderen zu erm�glichen, zu ihrer Entwicklung beizutragen.

Bei der �berpr�fung m�glicher Optionen gibt es ein paar hilfreiche Hinweise, die ihre Vorz�ge zeigen k�nnen.

 - **Sterne:** Dies zeigt an, wie viele Entwickler die Bibliothek *gebookmarkt* haben
 - **Probleme:** Wenn man durch die offenen Fragen schaut, kann man auf m�gliche Probleme stossen, die Entwickler mit der Bibliothek hatten. Eine hohe Anzahl offener Fragen kann auf m�gliche Schwierigkeiten hindeuten. Ebenso k�nnen Fragen mit Antworten aus dem Bibliotheksentwickler ein vern�nftiges Mass an Support anzeigen. Es lohnt sich auch zu sehen, wie viele geschlossene Probleme erfolgreich gel�st wurden.
 - **PRs:** *Pull Requests* sind Beitr�ge von anderen Entwicklern, die helfen, Updates f�r die Bibliothek zu erstellen. Eine Anzahl von offenen Pull-Requests kann auf eine Bibliothek hinweisen, die nicht mehr aktiv ist.
 - **Dokumentation und Beispiele:** Zu lernen, wie man eine neue Bibliothek benutzt, kann zun�chst komplex sein. Die Verf�gbarkeit von umfangreichen Dokumentations- und/oder Codebeispielen kann bei der Auswahl einer geeigneten Bibliothek helfen.

Die wichtigste Methode von allen ist, den Code selbst zu �berpr�fen. Das h�ngt von Ihrem JavaScript Wissen ab. [Hier sind einige Tipps f�r die �berpr�fung von Plugin-Code](https://remysharp.com/2010/06/03/signs-of-a-poorly-written-jquery-plugin).


***Weitere Informationen:***

 - [http://davidwalsh.name/13-factors-choosing-javascript-charting-library](http://davidwalsh.name/13-factors-choosing-javascript-charting-library)
 - [https://remysharp.com/2010/06/03/signs-of-a-poorly-written-jquery-plugin](https://remysharp.com/2010/06/03/signs-of-a-poorly-written-jquery-plugin)


### Ein Plugin oder eine Bibliothek erstellen

Es gibt eine Reihe von umfassenden Leitf�den f�r die Erstellung von JQuery-Plugins:

 - [https://learn.jquery.com/plugins/basic-plugin-creation/](https://learn.jquery.com/plugins/basic-plugin-creation/)
 - [http://www.smashingmagazine.com/2011/10/11/essential-jquery-plugin-patterns/](http://www.smashingmagazine.com/2011/10/11/essential-jquery-plugin-patterns/)
 - [http://jqueryboilerplate.com/](http://jqueryboilerplate.com/)

Es gibt keine Standardmethode f�r die Erstellung einer eigenst�ndigen JavaScript-Bibliothek, aber es k�nnte helfen, ein paar beliebte zu �berpr�fen, um zu sehen, wie sie geschrieben und dokumentiert sind.


## JavaScript Frameworks

Wie oben diskutiert wurde, wird jede Website davon profitieren, wenn man sich von der *Code-Suppe* einer JQuery DOM-ready-Funktion verabschiedet. Der erste Schritt besteht darin, die Logik in Module zu trennen.

Wenn das JavaScript weiterhin w�chst und sich die Komplexit�t erh�ht, kann es an der Zeit sein, die Erstellung einer benutzerdefinierten Codestruktur zu stoppen und stattdessen ein anerkanntes Framework zu verwenden.


### Probleme die Frameworks l�sen k�nnen

Das gr�sste Problem mit einer benutzerdefinierten Anwendungsstruktur, die Frameworks zu l�sen versuchen, ist die Trennung von verschiedenen Arten von JavaScript-Logik. Die meisten JavaScript-Frameworks erzwingen eine *Trennung von Interessen* - die Isolierung von Code in verschiedene Funktionen, die f�r verschiedene Zwecke verwendet werden.

Die wichtigsten Teile von JavaScript, die traditionell getrennt sind, betreffen DOM-Interaktion, Datenmanipulation, Templating und Event-Handling.


#### MVC

Das gemeinsame Muster, das die meisten JavaScript Frameworks verfolgen, heisst *Model View Controller*, oft verk�rzt auf *MVC*.

MVC ist ein komplexes Muster, das an anderer Stelle im Internet gut dokumentiert ist. Die folgenden Links geben eine umfassende Erl�uterung ihrer Logik und wie sie f�r den Kontext von JavaScript-Frameworks gilt.

Nach diesen Prinzipien sollte es zu kleineren strukturierten Modulen kommen, die Code besser pflegbar machen.

***Weitere Informationen:***

 - [http://alistapart.com/article/javascript-mvc](http://alistapart.com/article/javascript-mvc)
 - [http://www.smashingmagazine.com/2012/07/27/journey-through-the-javascript-mvc-jungle/](http://www.smashingmagazine.com/2012/07/27/journey-through-the-javascript-mvc-jungle/)
 - [http://addyosmani.com/resources/essentialjsdesignpatterns/book/](http://addyosmani.com/resources/essentialjsdesignpatterns/book/)


### Entscheiden, ob ein Framework verwendet werden soll

Dies ist ein komplexes Thema, bei dem viele Entwickler entweder daf�r oder dagegen sind. Es gibt Hunderte von Artikeln zu diesem Thema.

Letztlich ist die Entscheidung, ob man eines benutzt, abh�ngig vom Kontext:

  - Wie komplex ist die geforderte Funktionalit�t?
  - Wie vertraut sind die Entwickler mit JavaScript?
  - Haben die Entwickler Erfahrung mit JavaScript-Frameworks?
  - W�rde die Seite davon profitieren, eine *Single-Page-Anwendung* zu sein? Soll die Applikationslogik im Browser gespeichert werden oder soll die Funktionalit�t vom Server kommen?

Es gibt mehrere Vor-und Nachteile, die ber�cksichtigt werden sollten, wenn eine Entscheidung dar�ber getroffen wird, ob ein JavaScript-Framework verwendet wird oder nicht.


#### PROs

  - Die meisten etablierten JavaScript-Frameworks wurden sorgf�ltig getestet und lassen Sie sich auf den Aufbau Ihrer Anwendung konzentrieren, ohne sich um Fehler in der Architektur zu sorgen.
  - JavaScript-Frameworks sind in der Regel gut dokumentiert, mit aktiven Communities und vielen n�tzlichen Artikeln und Antworten auf h�ufig gestellte Fragen auf Websites wie Stack Overflow.
  - Wenn ein neuer Entwickler Erfahrung mit einem JavaScript-Framework hat, sollten sie schnell produktiv sein, da sie bereits ein Verst�ndnis von der Logik haben.


#### CONs

 - Die zus�tzliche Dateigr�sse eines JavaScript-Frameworks (und seiner Abh�ngigkeiten) sollte ber�cksichtigt werden.
 - Die Komplexit�t des JavaScript-Codes, die bei der Verwendung eines Frameworks erforderlich ist, kann f�r unerfahrene Front-End-Entwickler schwierig sein.
 - Einige JavaScript-Frameworks leiden unter anf�nglichen Performance-Hits und nehmen eine betr�chtliche Zeitspanne ein, um das erste Mal zu starten, wenn sie verwendet werden.
 - JavaScript Frameworks helfen SEO meist nicht - zumindest nicht im Vergleich zu *traditionellen* Webseiten.
 - Die Reife eines JavaScript-Frameworks sollte ausgewertet werden, bevor es verwendet wird. Neue Frameworks k�nnen sich vor allem deutlich �ndern, was zu grossem Code-Rewriten f�hren k�nnte.
 - Die Auswahl eines JavaScript-Frameworks kann ein langfristiges Engagement und eine bedeutende Investition auf der Grundlage einer Open-Source-L�sung beinhalten.

JavaScript-Frameworks sind nicht die richtige Wahl f�r jedes Projekt. Wenn Sie eine Website bauen, dessen Logik zum Grossteil immer noch auf dem Server stattfindet, und wenn JavaScript in erster Linie verwendet wird, um die Dinge ein wenig interaktiver zu machen, dann kann ein komplexes JavaScript-Framework �bertrieben sein. 


### Popul�re Frameworks

Es gibt keinen Mangel an verf�gbaren JavaScript Frameworks, und neue werden st�ndig erstellt. Hier sind einige der beliebtesten Optionen:

 - [Backbone.js](http://backbonejs.org/)
 - [AngularJS](https://angularjs.org/)
 - [React](https://facebook.github.io/react/)

Es gibt unz�hlige mehr: [http://todomvc.com/](http://todomvc.com/)

Die Ber�cksichtigung des am besten geeigneten Rahmens sollte ihre relativen Vor- und Nachteile abw�gen, f�r die es viele Vergleichsartikel gibt.

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

Viele Programmiersprachen bieten eine native M�glichkeit, Module zu definieren und zu verwenden. JavaScript derzeit nicht (obwohl eine zuk�nftige Version von JavaScript diese F�higkeit beinhalten wird).

Mittlerweile gibt es Werkzeuge, die es Entwicklern erm�glichen, Module jetzt zu verwenden. Diese *Module loader*-Systeme erm�glichen es, komplexe Codebasen in einer einfachen, konsistenten und gut dokumentierten Weise zu organisieren.

Es gibt ein paar beliebte Module Loader-Tools. Es gibt auch zwei verschiedene popul�re Methoden zur Definition von Modulen, bekannt als *AMD* und *Common.js*.

 - [RequireJS](http://requirejs.org/) - Einer der allerersten popul�ren Module-Loader, der die *AMD* Methode zum Deklarieren von Modulen verwendet.
 - [Browserify](http://browserify.org/) - Ein Module-Loader der die *Common.js* Moduldeklaration verwendet
 - [Webpack](http://webpack.github.io/) - Ein weiterer Module-Loader der *Common.js* verwendet

Unabh�ngig von der verwendeten Werkzeug- und Moduldefinition ist das Prinzip gleich; Erstellen Sie zahlreiche Dateien mit kleinen isolierten Modulen mit individuellen Zwecken, und importieren Sie sie an der entsprechenden Stelle, wo sie in der Codebasis verwendet werden.

Module-Loader werden oft in Kombination mit einem JavaScript-Framework verwendet, um weitere Code-Struktur und Trennung zu bieten.

***Weitere Informationen***

 - [https://web-design-weekly.com/2014/09/24/diving-webpack/](https://web-design-weekly.com/2014/09/24/diving-webpack/)
 - [https://github.com/substack/browserify-handbook](https://github.com/substack/browserify-handbook)
 - [http://webpack.github.io/docs/commonjs.html](http://webpack.github.io/docs/commonjs.html)


## Templating

Wenn Sie JavaScript verwenden, um Inhalte zu erstellen, um HTML-Elemente zu f�llen, k�nnen Template-Tools helfen, die Anwendungslogik vom Template-Markup zu trennen.

Die Verwendung eines Templating-Systems ist vorteilhaft, wenn das clientseitige HTML-Rendering erforderlich ist, insbesondere beim Laden von Daten von einem Server und zum Rendern einer komplexen HTML-Struktur.

Es stehen eine Reihe von Template-Systemen zur Verf�gung:

 - [ejs](http://www.embeddedjs.com/)
 - [Handlebars](http://handlebarsjs.com/)
 - [Mustache](https://github.com/janl/mustache.js)

Es gibt unz�hlige mehr: [http://garann.github.io/template-chooser/](http://garann.github.io/template-chooser/)

Unabh�ngig davon, welche Templating-Sprache gew�hlt wird, bieten sie alle �berlegene Funktionalit�t (und Code-Trennung) im Vergleich zum Erstellen von HTML-Elementen und bef�llen mit JQuery.

Allerdings lohnt es sich zu �berlegen, ob das Rendering im Client vorteilhaft ist, da es langsam sein kann und die Duplizierung der bereits vorhandenen Logik auf dem Server erfordert. Stattdessen betrachten Sie das Rendern von Teilen auf dem Server und das Zur�ckgeben von HTML, das direkt in das DOM eingef�gt werden soll.

***Weitere Informationen:***

 - [http://www.smashingmagazine.com/2012/12/05/client-side-templating/](http://www.smashingmagazine.com/2012/12/05/client-side-templating/)
 - [http://www.sitepoint.com/creating-html-templates-with-mustachejs/](http://www.sitepoint.com/creating-html-templates-with-mustachejs/)
 - [http://nimbupani.com/mustache.html](http://nimbupani.com/mustache.html)


## Build Tools

Unabh�ngig davon, ob ein beliebtes JavaScript-Framework oder eine benutzerdefinierte Anwendungsstruktur verwendet wurde, besteht die Chance, dass eine Reihe von individuellen JavaScript-Dateien erstellt wurden, um eine modulare Codebasis bereitzustellen.

Dies kann dazu beitragen, eine Codebasis zu verwalten, aber f�r eine Produktionsumgebung k�nnen diese Dateien kombiniert werden, um HTTP-Anfragen zu minimieren und die Website zu beschleunigen.

Ein *Task Runner* kann helfen, die Verkettung (und Minifizierung) dieser Dateien zu automatisieren.

Diese Werkzeuge k�nnen auch mit anderen Aufgaben wie der Optimierung von Bildern, dem Ausf�hren eines CSS-Vorprozessors, das Pr�fen auf Fehler, durchf�hren von Tests und bereitzustellen von Code, helfen.

Diese Tools sind f�r die Verwendung von Plugins zur Bereitstellung dieser Funktionalit�t gebaut.

Viele dieser Tools werden mit JavaScript erstellt und konfiguriert.

 - [Grunt](http://gruntjs.com/) - Der popul�rste Task Runner
 - [Gulp](http://gulpjs.com/) - Weniger popul�r als Grunt, aber oft schneller und leichter zu konfigurieren
 - [Brocolli](http://broccolijs.com/) - Ein weiterer popul�rer Task Runner

***Weitere Informationen***

 - [http://24ways.org/2013/grunt-is-not-weird-and-hard/](http://24ways.org/2013/grunt-is-not-weird-and-hard/)
 - [http://alistapart.com/blog/post/getting-started-with-gulp](http://alistapart.com/blog/post/getting-started-with-gulp)


## Abh�ngigkeiten Management

Die meisten Webseiten verlassen sich auf Drittanbieter-Bibliotheken und Frameworks - JQuery ist das offensichtlichste und beliebteste Beispiel.

Man kann es ziemlich schnell herunterladen und direkt in die Codebasis einf�gen. Jedoch kann man mit einem *Paket-Manager* die Verwaltung, Installation und Aktualisierung dieser Abh�ngigkeiten vereinfachen - besonders praktisch bei der Arbeit in ein Team.

Es gibt eine Reihe von beliebten Paket-Managern, darunter:

 - [bower](http://bower.io/)
 - [npm](https://www.npmjs.com/)
 - [component](https://github.com/componentjs/component)

Es gibt noch weitere: [https://github.com/wilmoore/frontend-packagers](https://github.com/wilmoore/frontend-packagers)

***Weitere Informationen***

 - [http://frontendbabel.info/articles/bower-why-frontend-package-manager/](http://frontendbabel.info/articles/bower-why-frontend-package-manager/)
 - [https://css-tricks.com/whats-great-bower/](https://css-tricks.com/whats-great-bower/)


## Testen

Testen von JavaScript kann grunds�tzlich wichtig sein, vor allem bei der Unterst�tzung einer grossen und komplexen Website, die sich st�ndig weiterentwickelt.

Es gibt eine Reihe von Frameworks f�r das Testen mit JavaScript:

 - [Jasmine](http://jasmine.github.io/)
 - [Mocha](http://mochajs.org/)
 - [Intern](https://theintern.github.io/)

Und noch weitere: [http://stackoverflow.com/a/680713](http://stackoverflow.com/a/680713)


***Weitere Informationen***

 - [http://alistapart.com/article/writing-testable-javascript](http://alistapart.com/article/writing-testable-javascript)
 - [http://www.smashingmagazine.com/2012/06/27/introduction-to-javascript-unit-testing/](http://www.smashingmagazine.com/2012/06/27/introduction-to-javascript-unit-testing/)
 - [http://www.helpscout.net/blog/functional-testing-casperjs/](http://www.helpscout.net/blog/functional-testing-casperjs/)


## Code Qualit�t

Beim Schreiben von JavaScript ist es einfach, kleine Fehler zu machen, die m�glicherweise zu Problemen f�hren k�nnten, wenn sie unentdeckt bleiben.

[JSHint] (http://jshint.com/) und [JSCS] (http://jscs.info/) sind zwei Werkzeuge, die helfen k�nnen, diese Probleme zu erkennen. Sie k�nnen so konfiguriert werden, dass sie Codierungsregeln �ber ein Team erzwingen und sicherstellen, dass jeder Code eine Reihe von vereinbarten Standards erf�llt.

JSHint und JSCS k�nnen zu verschiedenen Zeiten verwendet werden. Plugins existieren, um sie direkt in viele popul�re Code-Editoren hinzuzuf�gen, um sofort Fehler zu vermeiden. Sie k�nnen auch zu einem *Task Runner* hinzugef�gt werden, um Probleme als Teil eines Buildprozesses zu identifizieren. Sie k�nnten zu einer *Pre-Commit-Phase* der Versionskontrollsoftware hinzugef�gt werden, um sicherzustellen, dass der Code nicht akzeptiert wird, bis er die Validierung bestanden hat.

***Weitere Informationen***

 - [https://yannick.cr/posts/enforcing-coding-rules-in-your-team-with-jscs/post](https://yannick.cr/posts/enforcing-coding-rules-in-your-team-with-jscs/post)
 - [http://davetayls.me/blog/2013/07/01/how-will-i-keep-javascript-code-quality-hight-jshint/](http://davetayls.me/blog/2013/07/01/how-will-i-keep-javascript-code-quality-hight-jshint/)
 - [https://github.com/valueof/home/blob/master/pages/blog/why-jshint.md](https://github.com/valueof/home/blob/master/pages/blog/why-jshint.md)


## Node.js

[Node.js] (https://nodejs.org/) ist eine Plattform, mit der JavaScript auf einem Server ausgef�hrt werden kann. Die asynchrone ereignisgesteuerte Natur von JavaScript eignet sich f�r bestimmte Anwendungsarten, wie z.B. die Echtzeitkommunikation mit *websockets*.

***Weitere Informationen***

 - [http://code.tutsplus.com/tutorials/nodejs-for-beginners--net-26314](http://code.tutsplus.com/tutorials/nodejs-for-beginners--net-26314)
 - [https://github.com/maxogden/art-of-node/#the-art-of-node](https://github.com/maxogden/art-of-node/#the-art-of-node)
 - [http://nodeguide.com/beginner.html](http://nodeguide.com/beginner.html)
 - [http://stackoverflow.com/a/5511507](http://stackoverflow.com/a/5511507)


## Grafik

Es gibt zwei ganz verschiedene Methoden zur Erzeugung von interaktiven Grafiken mit JavaScript: *SVG* und *canvas*.

### SVG

SVG ist ein XML-basiertes Vektorformat f�r das Zeichnen von Bildern �ber das DOM. Die Verwendung von SVGs bedeutet aufl�sungsunabh�ngige Grafiken bei niedrigen Dateigr�ssen.

Es gibt verschiedene Werkzeuge, die dazu beitragen, SVGs mit JavaScript zu arbeiten und zu interagieren:

 - [SnapSVG](http://snapsvg.io/)
 - [D3](http://d3js.org/)
 - [Raphael](http://raphaeljs.com/)

***Weitere Informationen***

 - [https://css-tricks.com/using-svg/](https://css-tricks.com/using-svg/)
 - [http://davidwalsh.name/svg-animation](http://davidwalsh.name/svg-animation)


### Canvas

Canvas ist eine alternative Methode, JavaScript zu verwenden, um Grafiken in einem Browser zu erstellen. Im Gegensatz zu SVG macht es Bitmap-Daten. Der Vorteil der Verwendung von Canvas ist die M�glichkeit, WebGL zu verwenden, um Hardware-gerenderten 3D-Grafiken zu erstellen.

Es gibt eine Reihe von Werkzeugen, um Canvas zu benutzen:

 - [EaselJS](http://www.createjs.com/EaselJS)
 - [Paper.js](http://paperjs.org/)
 - [three.js](http://threejs.org/)

Es gibt viele weitere: [http://www.softr.li/blog/2012/06/20/which-html5-canvas-javascript-library-should-i-use](http://www.softr.li/blog/2012/06/20/which-html5-canvas-javascript-library-should-i-use)

***Weitere Informationen***

 - [https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial)
 - [http://diveintohtml5.info/canvas.html](http://diveintohtml5.info/canvas.html)


## Zuk�nftige Versionen von JavaScript

Zuk�nftige Versionen von JavaScript - *ES 6 / ES 2015* und dar�ber hinaus - werden viele der oben genannten Fragen ansprechen. Es wird ein echtes Module-Loader-System, Methoden f�r die Verwaltung von Scopes und das Erstellen von Templates und vielem mehr geben.

Obwohl es derzeit nicht �ber alle Browser hinweg implementiert ist, erlauben Tools wie [Traceur] (https://github.com/google/traceur-compiler) und [Babel] (https://babeljs.io/) JavaScript auf diese Weise bereits heute zu schreiben, um dann zur�ck in die aktuelle Version von JavaScript *verwandelt* zu werden, die Browser versteht.

***Weitere Informationen***

 - [https://leanpub.com/understandinges6/read](https://leanpub.com/understandinges6/read)
 - [http://24ways.org/2014/javascript-modules-the-es6-way/](http://24ways.org/2014/javascript-modules-the-es6-way/)
 - [https://babeljs.io/docs/learn-es6/](https://babeljs.io/docs/learn-es6/)


## Weitere Informationen

Eine Vielzahl weiterf�hrender Links findet man hier:

 - [https://github.com/dypsilon/frontend-dev-bookmarks](https://github.com/dypsilon/frontend-dev-bookmarks)
