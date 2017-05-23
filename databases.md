# Datenbank Notizen

Ein paar Notizen vorbereitet beim Schreiben von Schulungen ...

Beachten Sie, dass die folgenden Beispiele *MySQL* als die ausgew�hlte Datenbank annehmen. Andere relationale Datenbanken werden dazu neigen, eine �hnliche Logik zu verwenden, obwohl mit etwas unterschiedlicher Syntax.


## Warum eine Datenbank benutzen?

Beim Aufbau von Webanwendungen verwenden wir oft eine Datenbank zum Speichern von Informationen

Wir m�chten unsere Anwendungs-*Daten* trennen von:

  - *Logik* (z.B. Ruby, Python, PHP, ...)
  - *Pr�sentation* (z.B. HTML-Vorlagen)


### Vorteile

Es gibt eine Reihe von Vorteilen f�r die Trennung von Information und Pr�sentation:

  - Inhalte sind einfacher zu verwalten ohne �nderung der Logik
  - Daten k�nnen an anderer Stelle wiederverwendet werden
  - Die Daten k�nnen �ber ein administratives Tool (z.B. ein *Content Management System*) verwaltet werden, wobei wenig oder kein technisches Wissen erforderlich ist
  - Datenbanken sind optimiert, um Daten schnell zu speichern und abzurufen
  

## Datenbank Grundlagen

Eine Datenbank ist nur eine Sammlung von einer oder mehreren Tabellen von Daten

  - Jede Tabelle hat eine Anzahl von **Spalten** (oder Felder, Attribute)
  - Jede Spalte hat einen bestimmten **Namen**
  - Jede Spalte hat auch einen Daten**typ** (z.B. Text, Nummer, Datum / Uhrzeit usw.)
  - Die Daten werden in einer Tabelle in **Zeilen gespeichert**
  - Jede einzelne Spalte innerhalb einer Zeile hei�t **Zelle**

Datenbankfeldnamen enthalten normalerweise keine Leerzeichen. In der Regel wird vorschlagen, sie alle in Kleinbuchstaben zu schreiben und W�rter mit Unterstrichen zu trennen

| id | spalte_1    | spalte_2 |
| ---|-------------|----------|
| 1  | reihe 1     | zelle    |
| 2  | reihe 2     | lorem    |
| 3  | zelle       | ipsum    |


## Ein Beispielszenario

Die folgenden Hinweise basieren auf dem Entwerfen einer Datenbank f�r ein Beispielszenario:

*Entwerfen Sie eine Datenbank f�r eine Webanwendung, die eine t�gliche Frage tweetet und die __@replies__ sammelt. Diese Tweets werden in eine oder mehrere Kategorien eingeteilt*


## Datenbank-Design-Prozess

Wir k�nnen unsere Datenbank entwerfen, indem wir ein paar einfachen Schritten folgen:

1. Entscheiden Sie, welche Daten Sie speichern m�chten
2. W�hlen Sie einen Datentypen f�r jede dieser Informationen aus
3. Normalisieren Sie die Daten

Diese Notizen werden dann erkl�ren, wie Sie Ihre Datenbank:

1. Erstellen
2. F�llen
3. Abfragen


## Daten speichern

Beim Entwerfen einer Datenbank ist es wichtig, zuerst zu entscheiden, welche Daten wir speichern m�chten.

Wenn wir uns unsere Beispieldaten in tabellarischer Form vorstellen w�rden, k�nnten wir so etwas haben:

| id | name | handle         | question         | answer        | categories     | date_added          |
|----|------|----------------|------------------|---------------|----------------|---------------------|
| 1  | Pete | thegingerbloke | Favourite Cheese | Edam          | serious        | 2013-03-21 18:34:23 |
| 2  | Rich | rich_xyz       | Favourite Prince | Fresh         | funny, winner  | 2013-03-21 19:25:16 |
| 3  | Nick | something      | Favourite Prince | TAFKAP        | serious, funny | 2013-03-21 20:12:01 |
| 4  | Mike | dangerous      | Favourite Cheese | Melted cheese | funny, winner  | 2013-03-21 19:25:16 |



## Datentypen ausw�hlen

Dieser Schritt identifiziert die m�glichen Werte f�r die Daten

Datentypen steuern die Art und Weise, wie die Daten in der Datenbank gespeichert werden - um sie so effizient wie m�glich zu machen

Ein paar Beispieldatentypen:

* String (Text):
  - Feste L�nge (bis zu 255 Zeichen)
  - Variable L�nge (bis zu 255 Zeichen)
  - Text (�ber 255 Zeichen)

* Numerisch:
  - Integer - ganze Zahlen
  - Decimal - Dezimalzahlen
  - Datum und Uhrzeit

(Exakte Datentypen k�nnen je nach verwendeter Datenbank variieren)

In unserem Beispielszenario k�nnen wir folgende Datentypen verwenden:

 - **ID**: Integer
 - **name**: variable L�nge
 - **handle**: variable L�nge
 - **question**: variable L�nge
 - **answer**: variable L�nge
 - **categories**: Text
 - **date_added**: Datum und Uhrzeit


## Datennormalisierung

Um Daten zu normalisieren, werden sich wiederholende Informationen entfernt, so dass jede Information nur einmal gespeichert wird

Sobald wir die sich wiederholenden Daten entfernt haben, haben wir auch m�gliche Inkonsistenzen entfernt

Damit wird sichergestellt, dass die "Integrit�t" der Daten beibehalten wird.

*Was bedeutet das:*

Alle sich wiederholenden Daten sollten in einer separaten Datenbanktabelle gespeichert werden

Die Normalisierung von Daten bedeutet auch, Datengruppen aufzul�sen, um sie zu trennen, damit jede Zelle nur ein einziges Datenelement enth�lt

*Was bedeutet das:*

Alle Zellen, die mehrere Daten enthalten, sollten in einer separaten Datenbanktabelle gespeichert werden


***Weitere Informationen:***

 - [http://phlonx.com/resources/nf3/](http://phlonx.com/resources/nf3/)
 - [http://en.wikipedia.org/wiki/Database_normalization](http://en.wikipedia.org/wiki/Database_normalization)
 - [http://www.devshed.com/c/a/MySQL/An-Introduction-to-Database-Normalization/](http://www.devshed.com/c/a/MySQL/An-Introduction-to-Database-Normalization/)
 - [http://support.microsoft.com/kb/100139](http://support.microsoft.com/kb/100139)


### Begrenzung der Normalisierung

In einer vollst�ndig normalisierten Datenbank sollte es keine Vervielf�ltigung von Informationen geben.

Allerdings kann dies manchmal die Daten zersplittern oder �berkomplizieren und zu unn�tig getrennten Informationen f�hren, die dann zusammengef�hrt werden m�ssen, um Abfragen zu beantworten.

Der Datenbankdesigner kann manchmal eine Datenbank haben, die nicht streng normiert ist, um das System zu vereinfachen und / oder die Abfrageleistung zu verbessern.

***Weitere Informationen:***

 - [http://www.keithjbrown.co.uk/vworks/mysql/mysql_p7.php](http://www.keithjbrown.co.uk/vworks/mysql/mysql_p7.php)
 - [http://www.codinghorror.com/blog/2008/07/maybe-normalizing-isnt-normal.html](http://www.codinghorror.com/blog/2008/07/maybe-normalizing-isnt-normal.html)


### Prim�rschl�ssel

In jeder Tabelle m�ssen wir eine eindeutige ID identifizieren (oder erstellen) (als Prim�rschl�ssel bekannt)

Ein Prim�rschl�ssel hat drei Anforderungen:

1. Er muss immer einen Wert haben (er kann nicht leer sein)
2. Sein Wert darf sich nie �ndern
3. Er muss eindeutig sein

Ein Prim�rschl�ssel muss einen eindeutigen Wert haben, der es uns erm�glicht, eine einzelne Datenzeile zu identifizieren und somit auf alle anderen Daten zuzugreifen

Wenn keine der Datenelemente eindeutig sind, k�nnen sie nicht als Prim�rschl�ssel fungieren

Der einfachste Prim�rschl�ssel ist eine Ganzzahl, die f�r jede neue Zeile inkrementiert wird

Manchmal wollen wir den Prim�rschl�ssel aus einer Tabelle in einer anderen Tabelle eintragen, um eine Beziehung zwischen den beiden herzustellen. Wenn wir dies tun, ist er in der zweiten Tabelle als *Fremdschl�ssel* bekannt


### Entit�ten und Attribute

F�r jedes Szenario, in dem Sie eine Datenbank verwenden m�chten, m�ssen Sie die Entit�ten und Attribute identifizieren

#### Entit�ten

Sollten Darstellungen von realen Gegenst�nden sein - Ereignisse, Personen, Orte, Dinge

z.B. Projekte, Aufgaben, B�cher, Autoren, Verlage, Produkte, Zutaten ...

Jede Entit�t sollte eine eigene Tabelle in der Datenbank haben

Keine leichte Wissenschaft, um die Entit�ten richtig zu identifizieren, sie ist abh�ngig vom Szenario und oft subjektiv

Sobald wir die Entit�ten identifiziert haben, k�nnen wir f�r jede eine Datenbanktabelle erstellen


#### Attribute

St�cke von Informationen, die diese Entit�ten charakterisieren und beschreiben

Diese werden die Felder/Spalten f�r jede Entit�tstabelle in der Datenbank

Es ist notwendig, den Namen des Attributs zu identifizieren - z.B. 'name', 'antwort', 'kategorie'

Es ist notwendig, das Attribut 'type' zu identifizieren - z.B. Text, Integer, Datum, etc

Es ist notwendig zu entscheiden, ob das Attribut optional ist - kann es leer sein?

Kann das Attribut die Entit�t eindeutig identifizieren?


### Beispiel-Datenbanktabellen

Hier sind drei unserer Beispieltabellen:

***Fragentabelle***

| id | question          | date_added          |
|----|-------------------|---------------------|
| 1  | Favourite Cheese? | 2013-03-21 18:34:23 |
| 2  | Favourite Prince? | 2013-03-21 18:34:23 |

***Benutzertabelle***

| id |  handle        | name |
|----|----------------|------|
| 1  | thegingerbloke | Pete |


***Kategorientabelle***

| id | category |
|----|----------|
| 1  | Funny    |


### Beziehungen

Es ist wichtig, die Beziehungen zwischen den Tabellen zu identifizieren

Es gibt drei Arten von Beziehung:

1. Eins-zu-Eins (1:1)
2. Eins-zu-Viele (1:N)
3. Viele-zu-Viele (N:M)


#### Eins-zu-Viele (1:N) Beziehungen

Um eine Eins-zu-Viele-Beziehung (1:N) zu identifizieren, verwenden wir den Prim�rschl�ssel f�r die Fremdschl�ssel-�bereinstimmung.

Wir speichern den Prim�rschl�ssel des "Eins" als Fremdschl�ssel in jedem der "vielen" Elemente, die die Beziehung zwischen ihnen herstellen.

Auf diese Weise k�nnen mit zusammenpassenden Schl�sseln verwandte Informationen aus verschiedenen Tabellen zusammengef�hrt werden, wenn die Datenbank abgefragt wird.

In unserem Beispiel, Fragen:Antworten ist eine Eins-zu-Viele-Beziehung, gibt es f�r jede Frage mehrere Antworten, aber jede Antwort ist nur f�r eine Frage

Anstatt die Frage f�r jede Antwort hinzuzuf�gen, werden wir Fragen in der *Fragen*-Tabelle hinterlegen

Wir f�gen ein neues Feld zur Antworttabelle namens *question_id* hinzu - hier werden wir den eindeutigen Prim�rschl�ssel aus der Fragetabelle als Fremdschl�ssel in der Antworttabelle setzen

Nun m�ssen die Fragendetails nur einmal gespeichert werden. Wenn sich die Fragedetails �ndern, m�ssen wir nur einen einzigen Datensatz in der Fragetabelle aktualisieren und es w�rde f�r alle Antworten gelten

In �hnlicher Weise ist Benutzer:Antworten auch eine Eins-zu-Viele-Beziehung. Jeder Benutzer kann viele Antworten einreichen, aber jede Antwort kann nur von einem einzelnen Benutzer sein.

Hier ist unsere Beispiel *Antworten*tabelle, einschlie�lich der Verwendung von Fremdschl�sseln, um unsere Eins-zu-Viele-Beziehungen zu binden

***Antwortentabelle***

| id | question_id | user_id | answer | tweet_id    | date_added          |
|----|-------------|---------|--------|-------------|---------------------|
| 1  | 1           | 1       | Edam   | 23741876128 | 2013-03-21 18:34:23 |


#### Viele-zu-Viele (N:M) Beziehungen

F�r eine Viele-zu-Viele (M:N) Beziehung, gibt es auf beiden Seiten der Beziehung mehrere Entit�ten in jeder Tabelle, die miteinander verkn�pft sind

Zum Beispiel kann eine Antwort mehrere Kategorien haben; eine Kategorie kann auf mehrere Antworten angewendet werden.

Um diese Beziehung aufzuzeichnen, m�ssen wir eine separate Datenbanktabelle mit zwei Fremdschl�sseln erstellen, die sich auf die Prim�rschl�ssel f�r jede der beiden relevanten Entit�ten beziehen.

Hier ist unsere *Antworten auf Kategorien* (join) Tabelle

***Antworten auf Kategorien (join) Tabelle***

| id | answer_id | category_id |
|----|-----------|-------------|
| 1  | 1         | 5           |



## SQL

Wir haben unsere Datenbank entworfen

Wir m�ssen wissen, wie man sie erstellt, bef�llt und auf diese Daten zugreift

Hierzu brauchen wir SQL

Structured Query Language (SQL) ist die Sprache, die von den meisten Datenbanken verwendet wird, um Abfragen auszuf�hren und Daten zu manipulieren


### SQL Regeln

Ein paar SQL-Regeln sind zu beachten:

SQL ist in der Regel unempfindlich ...

... au�er f�r Tabellen- und Spaltennamen, die in der Regel zwischen Gro�- / Kleinschreibung unterscheiden

Nach der Konvention sollten SQL-Befehle (z.B. `SELECT`,` UPDATE`) in GROSSBUCHSTABEN geschrieben werden

Wie in den meisten Programmiersprachen sollten Strings (Text) von Anf�hrungszeichen ('single' oder "double") umgeben sein

Tabellen- und Spaltennamen k�nnen wahlweise von \`Backticks umgeben sein - beachten Sie, dass diese nicht die gleichen sind wie 'einfache Anf�hrungszeichen'

Alle Befehle sollten mit einem Semikolon enden;


### Erstellen einer Datenbank

Wenn Sie selbst eine neue Datenbank erstellen m�ssen, w�rden Sie den folgenden Befehl verwenden:

```
CREATE DATABASE `dbname`;
```

Um eine Liste aller verf�gbaren Datenbanken zu sehen, w�rden Sie den folgenden Befehl verwenden:

```
SHOW databases;
```

Um eine Datenbank auszuw�hlen:

```
USE `dbname`;
```

Um eine Datenbank zu l�schen:

```
DROP `dbname`;
```

***ES GIBT KEINE R�CKG�NGIG-FUNKTION!***


### Erstellen von Datenbanktabellen

Wir haben bereits die Struktur f�r unsere Datenbanktabellen geplant, jetzt m�ssen wir diese in SQL umwandeln

Um eine Tabelle zu erstellen, verwenden Sie den Befehl CREATE TABLE mit der folgenden Syntax:

```
CREATE TABLE `table_name` (
    `column_name` column_type column_attributes
);
```

Beispiel-Syntax f�r unsere Antworten-Tabelle:

```
CREATE TABLE `answers` (
    `id`          INT           NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `question_id` INT           NOT NULL,
    `user_id`     INT           NOT NULL,
    `tweet_id`    VARCHAR(20)   NOT NULL,
    `answer`      VARCHAR(255)  NOT NULL,
    `date_added`  DATETIME      NOT NULL
);
```

Nehmen wir als Beispiel die Spalte `id`:

```
`id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY
```

  - Sie enth�lt eine Ganzzahl (INT)
  - Diese Spalte darf nicht leer sein (NOT NULL)
  - Diese Spalte soll als eindeutige Kennung f�r Eintr�ge in dieser Tabelle dienen, also m�ssen alle Werte in dieser Spalte eindeutig sein (PRIMARY KEY).
  - Wenn wir beim Hinzuf�gen eines neuen Eintrags keinen Wert angeben, wird der n�chst h�here Wert als der bisher h�chste Wert in der Tabelle ausgew�hlt (AUTO_INCREMENT)

Innerhalb einer Datenbank k�nnen Sie abfragen, welche Tabellen vorhanden sind:

```
SHOW TABLES;
```

Sie k�nnen auch die Struktur einer bestimmten Tabelle anfordern:

```
DESCRIBE `tablename`;
```

Es ist m�glich, die Struktur einer vorhandenen Datenbanktabelle mit dem Befehl ALTER zu aktualisieren

So f�gen Sie eine Spalte hinzu:

```
ALTER TABLE  `tablename` ADD `columnname` TEXT NOT NULL;
```

So aktualisieren Sie den Namen oder die Attribute einer Spalte:

```
ALTER TABLE  `tablename` CHANGE  `oldcolumnname` `newcolumnname`
VARCHAR(255);
```

Um eine Spalte zu entfernen:

```
ALTER TABLE `tablename` DROP `columnname`;
```

Um eine Tabelle zu leeren, verwenden Sie den Befehl TRUNCATE:

```
TRUNCATE TABLE `tablename`;
```

Um eine Tabelle zu l�schen, verwenden Sie den Befehl DROP:

```
DROP TABLE `tablename`;
```

***ES GIBT KEINE R�CKG�NGIG-FUNKTION!***


### Beispieldatenbanktabellen

Die folgenden Befehle werden unsere Beispieltabellen erstellen:

```
CREATE TABLE `questions` (
    `id`          INT           NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `question`    VARCHAR(255)  NOT NULL,
    `date_added`  DATETIME      NOT NULL
);

CREATE TABLE `users` (
    `id`          INT           NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `handle`      VARCHAR(20)   NOT NULL,
    `name`        VARCHAR(255)  NOT NULL
);

CREATE TABLE `categories` (
    `id`          INT           NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `category`    VARCHAR(255)  NOT NULL
);

CREATE TABLE `answers` (
    `id`          INT           NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `user_id`     INT           NOT NULL,
    `question_id` INT           NOT NULL,
    `tweet_id`    VARCHAR(20)   NOT NULL,
    `answer`      VARCHAR(255)  NOT NULL,
    `date_added`  DATETIME      NOT NULL
);

CREATE TABLE `categories_answers` (
    `id`          INT           NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `category_id` INT           NOT NULL,
    `answer_id`   INT           NOT NULL
);
```


### Eine Datenbank mit Daten f�llen

Unsere Datenbank und Tabellen sind nun erstellt

Wir m�ssen wissen, wie man sie mit Daten bef�llt und dann diese Daten abruft

#### CRUD

Datenbezogene Aufgaben fallen weitgehend in eine von vier Kategorien:

  - Erstellen (neue Daten in einer Datenbank erstellen)
  - Anfordern / Lesen (Daten aus einer Datenbank lesen)
  - Aktualisieren (vorhandene Daten in einer Datenbank aktualisieren)
  - L�schen (Daten aus einer Datenbank l�schen)
  
SQL erlaubt uns genau das zu tun:

 - Erstellen = INSERT
 - Lesen =SELECT
 - Aktualisieren = UPDATE
 - L�schen = DELETE


#### INSERT

Um Daten zu den Tabellen hinzuzuf�gen, die wir gerade erstellt haben, verwenden wir einen INSERT-Befehl:

```
INSERT INTO `table_name` SET `columnName1` = 'value1', `columnName2` = 'value2';
```

(oder)

```
INSERT INTO `table_name` (`columnName1`, `columnName2`) VALUES ('value1', 'value2');
```

Die zweite Version erm�glicht es uns, mehrere Zeilen (getrennt durch Kommas) in einer einzigen SQL-Anweisung einzuf�gen

```
INSERT INTO
  `table_name` (`columnName1`, `columnName2`)
VALUES
  ('value1', 'value2'),
  ('value1', 'value2'),
  ('value1', 'value2'),
  ('value1', 'value2'),
  ('value1', 'value2');
```


#### UPDATE

Um Daten in einer Tabelle zu aktualisieren, verwenden wir einen UPDATE-Befehl:

```
UPDATE `table_name` SET `columnName1` = 'value1' WHERE `columnName2` = 'value2';
```

Beachten Sie die Verwendung der WHERE-Klausel - ohne diese werden alle Elemente in der Tabelle aktualisiert!


#### DELETE

Um Daten aus einer Tabelle zu l�schen, verwenden wir einen DELETE-Befehl:

```
DELETE FROM `table_name` WHERE `columnName` = 'value';
```

Beachten Sie die Verwendung der WHERE-Klausel - ohne diese werden alle Elemente in der Tabelle gel�scht!

***ES GIBT KEINE R�CKG�NGIG-FUNKTION!***


#### Bef�llen unserer Beispiel-Datenbanktabellen

```
INSERT INTO `categories` (`id`, `category`) VALUES
(1, 'Funny'),
(2, 'Serious'),
(3, 'Awkward'),
(4, 'Joke'),
(5, 'Winner');

INSERT INTO `categories_answers` (`id`, `category_id`, `answer_id`) VALUES
(1, 1, 1),
(2, 2, 2),
(3, 3, 2),
(4, 4, 1),
(5, 4, 3),
(6, 5, 3),
(7, 1, 4),
(8, 2, 4),
(9, 5, 5),
(10, 3, 6),
(11, 4, 6),
(12, 1, 7),
(13, 2, 8);

INSERT INTO `answers` (`id`, `user_id`, `question_id`, `tweet_id`, `answer`, `date_added`) VALUES
(1, 1, 1, '1347651374', 'Stilton', '2013-03-08 17:29:41'),
(2, 2, 1, '2374234', 'Melted', '2013-03-21 07:13:00'),
(3, 3, 2, '2378461216', 'Michael Fish', '2013-03-05 00:00:00'),
(4, 1, 2, '23746182376', 'humahumanukanukaapuaa', '2013-03-19 00:00:00'),
(5, 1, 3, '982736482764', 'Banned from the petting zoo', '2013-03-15 00:00:00'),
(6, 4, 3, '167312763512', 'Nothing', '2013-03-04 00:00:00'),
(7, 3, 4, '283746821364', 'Queen Latifah', '2013-03-20 00:00:00'),
(8, 4, 4, '71823182763', 'Rich', '2013-03-10 00:00:00');

INSERT INTO `questions` (`id`, `question`, `date_added`) VALUES
(1, 'What''s your favourite cheese?', '2013-03-03 15:30:23'),
(2, 'What''s your favourite fish?', '2013-03-20 15:29:38'),
(3, 'What''s the punchline to your favourite joke?', '2013-03-01 17:36:57'),
(4, 'Who''s your favourite queen?', '2013-03-09 19:45:42');

INSERT INTO `users` (`id`, `handle`, `name`) VALUES
(1, 'thegingerbloke', 'Pete'),
(2, 'rich_xyz', 'Rich'),
(3, 'something', 'Nick'),
(4, 'dangerous', 'Mike');
```


### Eine Datenbank abfragen

Um Daten aus einer Tabelle (oder mehreren Tabellen) zu lesen, verwenden wir einen SELECT-Befehl

Der einfachste SELECT-Befehl gibt alles in einer Datenbanktabelle zur�ck:

```
SELECT * FROM `table`;
```

Anstatt alles zur�ckzugeben, k�nnen Sie nur die gew�nschten Feldnamen (Spalten) angeben:

```
SELECT `field` FROM `table`;
```

Mehrere Feldnamen werden durch Kommas getrennt:

```
SELECT `field1`, `field2`, `field3` FROM `table`;
```

Anstatt alle Ergebnisse zur�ckzugeben, k�nnen wir optionale Parameter hinzuf�gen, um unsere Abfrage mit WHERE zu filtern:

```
SELECT * FROM `table` WHERE `field` = 'value';
```

```
SELECT `field1`, `field2`, `field3` FROM `table` WHERE `field1` > value;
```

Wir k�nnen unsere Ergebnisse mit ORDER BY sortieren:

```
SELECT * FROM `table` ORDER BY `id`;
```

Wir k�nnen die Sortierung mit ASC oder DESC �ndern:

```
SELECT * FROM `table` WHERE `field` > 100 ORDER BY `time` ASC;
```

Wir k�nnen die Anzahl der zur�ckgegebenen Ergebnisse mit LIMIT begrenzen:

```
SELECT * FROM `table` ORDER BY `time` LIMIT 2;
```

Dadurch werden die letzten beiden Datens�tze in der angegebenen Tabelle zur�ckgegeben

Wir k�nnen einen Offset angeben, um den LIMIT zu starten von:

```
SELECT * FROM `table` ORDER BY `time` LIMIT 2, 2;
```

Dies wird zwei Datens�tze zur�ckgeben, beginnend mit Satz 3
(Dies ist n�tzlich f�r die Paginierung der Ergebnisse)

Wir k�nnen Bedingungen mit AND und/oder OR kombinieren:

```
SELECT
    `field1`, `field2`
FROM
    `table`
WHERE
    `field1` = 'lorem'
AND
    `field2` > 12
ORDER BY
    `time` ASC
```

Dabei die Reihenfolge mit Klammern festlegen, falls AND und OR gemeinsam in einer Abfrage verwendet werden.


#### Mehrere Tabellen joinen

Alle SELECT-Beispiele waren bisher nur auf eine einzige Tabelle

Wenn wir die Daten normalisiert haben, haben wir den Inhalt gezielt in separate Tabellen verschoben

Jetzt m�ssen wir wissen, wie man sie mit einander verkn�pft.

Wir m�ssen Klauseln hinzuf�gen, die mit den Prim�rschl�sseln und Fremdschl�sseln �bereinstimmen

***Antwortentabelle***

| id | user_id | answer                                        | date_added          |
|----|---------|---------------------------------------------- |---------------------|
| 1  | 1       | lorem ipsum                                   | 2013-03-21 18:34:23 |
| 2  | 1       | quidquid Latine dictum sit altum videtur      | 2013-03-21 19:32:17 |
| 3  | 2       | Lorem ipsum dolor sit amet                    | 2013-03-21 20:31:25 |
| 4  | 3       | quidquid Latine                               | 2013-03-21 21:32:17 |
| 5  | 2       | ullamco laboris nisi ut aliquip ex ea commodo | 2013-03-21 22:31:25 |


***Benutzertabelle***

| id | handle         | name |
|----|----------------|------|
| 1  | thegingerbloke | Pete |
| 2  | something      | Nick |
| 3  | dangerous      | Mike |


**SELECT mit einem Join**

```
SELECT
  *
FROM
  `answers`
JOIN
  `users`
ON
  `answers`.`user_id` = `users`.`id`
```

| id | user_id | answer                                          | date_added          | handle          | name |
|----|---------|-------------------------------------------------|---------------------|-----------------|------|
| 1  | 1       | lorem ipsum                                     | 2013-03-21 18:34:23 | thegingerbloke  | Pete |
| 2  | 1       | quidquid Latine dictum sit altum videtur        | 2013-03-21 19:32:17 | thegingerbloke  | Pete |
| 3  | 2       | Lorem ipsum dolor sit amet                      | 2013-03-21 20:31:25 | something       | Nick |
| 4  | 3       | quidquid Latine                                 | 2013-03-21 21:32:17 | dangerous       | Mike |
| 5  | 2       | ullamco laboris nisi ut aliquip ex ea commodo   | 2013-03-21 22:31:25 | something       | Nick |


Wir k�nnen dann Bedingungen hinzuf�gen, wie vorher:

```
SELECT
  *
FROM
  `answers`
JOIN
  `users`
ON
  `answers`.`user_id` = `users`.`id`
WHERE
  `users`.`id` = 1
```

| id | user_id | answer                                          | date_added          | handle          | name |
|----|---------|-------------------------------------------------|---------------------|-----------------|------|
| 1  | 1       | lorem ipsum                                     | 2013-03-21 18:34:23 | thegingerbloke  | Pete |
| 2  | 1       | quidquid Latine dictum sit altum videtur        | 2013-03-21 19:32:17 | thegingerbloke  | Pete |


#### SELECT ohne Joins

Wir k�nnten unsere Daten auch ohne explizite Verwendung eines JOIN rekombinieren

Technisch ist das genauso wie ein innerer Join, aber die Syntax ist etwas anders ...

```
SELECT
  *
FROM
  `answers`, `users`
WHERE
  `answers`.`user_id` = `users`.`id`
```

#### Mehrere Tabellen in einer Abfrage

Wir haben gelernt, wie man �ber mehrere Tabellen abfragt, indem wir Prim�r- und Fremdschl�ssel anpassen

Wenn wir �ber mehrere Tabellen abfragen, werden die Attribute aus jeder Tabelle in eine einzelne Tabelle abgeflacht

Es kann Zeiten geben, in denen es Felder gibt, die wir abrufen wollen, die identische Spaltennamen in mehr als einer Tabelle haben (z.B. 'id')

Wenn wir versuchen, dies zu tun, wird nur eine der genannten Spalten abgerufen - die anderen werden nicht in den Ergebnissen vorhanden sein.

Bei PostgreSQL schl�gt eine solche Abfrage fehl, da das Ergebnis nicht eindeutig w�re.

```
SELECT
  `questions`.`question`,
  `questions`.`id`,
  `answers`.`answer`,
  `answers`.`id`
FROM
  `questions`,
  `answers`
WHERE
  `questions`.`id` = `answers`.`question_id`
```

Um dies zu beheben, verwenden wir AS in unserem SQL, um die Feldnamen auf etwas anderes zu verweisen und um sie einzigartig zu machen

```
SELECT
  `questions`.`question`,
  `questions`.`id` AS `question_id`,
  `answers`.`answer`,
  `answers`.`id` AS `answer_id`
FROM
  `questions`,
  `answers`
WHERE
  `questions`.`id` = `answers`.`question_id`
```

***Weitere Informationen:***

 - [http://codular.com/sql-introduction](http://codular.com/sql-introduction)
 - [http://codular.com/mysql-joins](http://codular.com/mysql-joins)
 - [http://en.wikipedia.org/wiki/Join_(SQL)](http://en.wikipedia.org/wiki/Join_(SQL))
 - [http://www.keithjbrown.co.uk/vworks/mysql/mysql_p5.php](http://www.keithjbrown.co.uk/vworks/mysql/mysql_p5.php)
 - [http://www.coderecipes.net/sql-join-inner-join-left-join.aspx](http://www.coderecipes.net/sql-join-inner-join-left-join.aspx)


#### Abrufen von zuf�lligen Ergebnissen mit MySQL

Sie k�nnen einen zuf�lligen Eintrag aus einer MySQL-Tabelle mit dem SQL `RAND ()` Befehl ausw�hlen

F�gen Sie `ORDER BY RAND() LIMIT 0,1` ans Ende Ihrer Abfrage:

```
SELECT * FROM `questions` ORDER BY RAND() LIMIT 0,1
```

Kann f�r die Auswahl einer zuf�lligen Frage auf einer Seite n�tzlich sein


#### Ergebnisse gruppieren

Wenn Sie f�r jede Frage eine Liste aller Antworten ausw�hlen m�chten, k�nnen Sie die folgende Abfrage ausf�hren:

```
SELECT
  `questions`.`question` ,
  `answers`.`answer`
FROM
  `questions` ,
  `answers`
WHERE
  `questions`.`id` = `answers`.`question_id`
```

Dies f�hrt zu folgenden Ergebnissen:

| question         | answer        |
|------------------|---------------|
| Favourite Cheese | Edam          |
| Favourite Prince | Fresh         |
| Favourite Prince | TAFKAP        |
| Favourite Cheese | Melted cheese |

Dies wiederholt die Frage jedes Mal f�r jede Antwort

Um die Antworten in einer einzigen Spalte zusammenzufassen:

```
SELECT
  `questions`.`question ,
  GROUP_CONCAT(`answers`.`answer` SEPARATOR ', ') AS `answer_list`
FROM
  `questions` ,
  `answers`
WHERE
  `questions`.`id` = `answers`.`question_id`
GROUP BY `questions`.`id`
```

Dies f�hrt zu folgenden Ergebnissen:

| question         | answer              |
|------------------|---------------------|
| Favourite Cheese | Edam, Melted cheese |
| Favourite Prince | Fresh, TAFKAP       |


Wenn Sie komplexe Abfragen in Ihrer Datenbank durchf�hren m�chten, lohnt es sich auch, verschiedene Arten von Datenbank-Joins und Unterabfragen zu untersuchen


#### Formatieren eines Datums mit MySQL

Wir haben Daten in MySQL unter Verwendung der Datentypen 'date', 'time' und 'datetime' gespeichert

Wenn diese von MySQL abgerufen werden ...

```
SELECT `date_added` FROM `answers`;
```

... ist die Ausgabe im Format: "2012-02-27 15:20:29"

Wenn Sie das Ausgabeformat �ndern m�chten, benutzen Sie DATE_FORMAT

```
SELECT DATE_FORMAT(`date_added`, '%e/%c/%y, %k:%i' AS `date_added_formatted` FROM `answers`;
```

***Weitere Informationen:***

 - [http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html#function_date-format](http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html#function_date-format)


## �bungsaufgabe

Versuchen Sie SQL-Abfragen zu schreiben, die die folgenden Anforderungen erf�llen:

  - Alle Fragen ausw�hlen
  - Alle Antworten f�r Benutzer 1 ausw�hlen
  - Alle Antworten ausw�hlen, sortiert nach dem Datum der Beantwortung
  - Alle Antworten f�r Frage 1 ausw�hlen, einschlie�lich des Benutzernamens der Person, die beantwortet hat
  - Alle Antworten aus Kategorie 1 ausw�hlen
  - Alle Antworten aus der Kategorie 'funny' ausw�hlen
  - Alle Antworten f�r Frage 1 ausw�hlen, einschlie�lich des Benutzernamens der Person, die beantwortet hat, und ihrer Kategorie
