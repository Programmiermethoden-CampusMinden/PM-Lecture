# Aufzählungen (Enumerations)

> [!IMPORTANT]
>
> <details open>
>
> <summary><strong>🎯 TL;DR</strong></summary>
>
> Mit Hilfe von `enum` lassen sich Aufzählungstypen definieren (der
> Compiler erzeugt intern passende Klassen). Dabei wird den Konstanten
> eine fortlaufende Nummer zugeordnet, auf die mit `ordinal()`
> zugegriffen werden kann. Mit der Methode `values()` kann über die
> Konstanten iteriert werden, und mit `name()` kann eine
> Stringrepräsentation einer Konstanten erzeugt werden. Es sind keine
> Instanzen von Enum-Klassen erzeugbar, und die Enum-Konstanten sind
> implizit `final` und `static`.
>
> Es lassen sich auch komplexe Enumerations analog zu Klassendefinition
> definieren, die eigene Konstruktoren, Felder und Methoden enthalten.
>
> </details>

> [!TIP]
>
> <details>
>
> <summary><strong>🎦 Videos</strong></summary>
>
> - [VL Enumerations](https://youtu.be/qoeT9jVuQZc)
> - [Demo Enumerations](https://youtu.be/ZCE9AmTluyk)
>
> </details>

## Motivation

``` java
public class Studi {
    public static final int IFM = 0;
    public static final int ELM = 1;
    public static final int ARC = 2;

    public Studi(String name, int credits, int studiengang) {
        // Wert für studiengang muss zwischen 0 und 2 liegen
        // Erwünscht: Konstanten nutzen
    }

    public static void main(String[] args) {
        Studi rainer = new Studi("Rainer", 10, Studi.IFM);
        Studi holger = new Studi("Holger", 3, 4);   // Laufzeit-Problem!
    }
}
```

**Probleme**:

- Keine Typsicherheit
- Konstanten gehören zur Klasse `Studi`, obwohl sie in anderem Kontext
  vermutlich auch interessant sind

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/java-jvm/src/enums/v1/Studi.java">Beispiel enums.v1.Studi</a></p>

## Verbesserung: Einfache Aufzählung

``` java
public enum Fach {
    IFM, ELM, ARC
}


public class Studi {
    public Studi(String name, int credits, Fach studiengang) {
        // Typsicherheit für studiengang :-)
    }

    public static void main(String[] args) {
        Studi rainer = new Studi("Rainer", 10, Fach.IFM);
        Studi holger = new Studi("Holger", 3, 4);   // Syntax-Fehler!
    }
}
```

## Einfache Aufzählungen: Eigenschaften

``` java
public enum Fach {
    IFM, ELM, ARC
}
```

1.  Enum-Konstanten (`IFM`, …) sind implizit `static` und `final`
2.  Enumerations (`Fach`) nicht instantiierbar
3.  Enumerations stellen einen neuen Typ dar: hier der Typ `Fach`
4.  Methoden: `name()`, `ordinal()`, `values()`, `toString()`

### Wiederholung *static*

**Attribute**:

- `static` Attribute sind Eigenschaften/Zustände der **Klasse**
- Gelten in jedem von der Klasse erzeugten Objekt
- Unterschiedliche Lebensdauer:
  - Objektattribute (Instanzvariablen): ab `new` bis zum Garbage
    Collector
  - Statische Variablen: Laufzeitumgebung (JVM) lädt und initialisiert
    die Klasse (`static` Attribute existieren, bis die JVM die Klasse
    entfernt)

**Methoden**:

- `static` deklarierte Methoden sind **Klassenmethoden**
- Können direkt auf der Klasse aufgerufen werden
- Beispiele: `Math.max()`, `Math.sin()`, `Integer.parseInt()`
- **Achtung**: In Klassenmethoden nur Klassenattribute nutzbar (keine
  Instanzattribute!), d.h. keine `this`-Referenz nutzbar

### Wiederholung *final*: Attribute/Methoden/Klassen nicht änderbar

- Attribute: `final` Attribute können nur einmal gesetzt werden

  ``` java
  void foo() {
      int i = 2;
      final int j = 3;
      final int k;
      i = 3;
      j = 4;  // Compilerfehler
      k = 5;
      k = 6;  // Compilerfehler
  }
  ```

  <p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/java-jvm/src/enums/FinalDemo.java">Beispiel enums.FinalDemo</a></p>

- Methoden: `final` deklarierte Methoden können bei Vererbung nicht
  überschrieben werden

- Klassen: von `final` deklarierten Klassen können keine Unterklassen
  gebildet werden

## Einfache Aufzählungen: Eigenschaften (cnt.)

``` java
// Referenzen auf Enum-Objekte können null sein
Fach f = null;
f = Fach.IFM;

// Vergleich mit == möglich
// equals() unnötig, da Vergleich mit Referenz auf statische Variable
if (f == Fach.IFM) {
    System.out.println("Richtiges Fach :-)");
}

// switch/case
switch (f) {
    case IFM:   // Achtung: *NICHT* Fach.IFM
        System.out.println("Richtiges Fach :-)");
        break;
    default:
        throw new IllegalArgumentException("FALSCHES FACH: " + f);
}
```

Außerdem können wir folgende Eigenschaften nutzen (u.a., s.u.):

- Enumerations haben Methode `String toString()` für die Konstanten
- Enumerations haben Methode `final T[] values()` für die Iteration über
  die Konstanten

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/java-jvm/src/enums/v2/Studi.java">Demo: enums.v2.Studi</a></p>

## Enum: Genauer betrachtet

``` java
public enum Fach {  IFM, ELM, ARC  }
```

**Compiler sieht (*in etwa*):**

``` java
public class Fach extends Enum {
    public static final Fach IFM = new Fach("IFM", 0);
    public static final Fach ELM = new Fach("ELM", 1);
    public static final Fach ARC = new Fach("ARC", 2);

    private Fach( String s, int i ) { super( s, i ); }
}
```

=\> **Singleton-Pattern** für Konstanten

## Enum-Klassen: Eigenschaften

``` java
public enum Fach {
    IFM,
    ELM("Elektrotechnik Praxisintegriert", 1, 30),
    ARC("Architektur", 4, 40),
    PHY("Physik", 3, 10);

    private final String description;
    private final int number;
    private final int capacity;

    Fach() { this("Informatik Bachelor", 0, 60); }
    Fach(String descr, int number, int capacity) {
        this.description = descr;  this.number = number;  this.capacity = capacity;
    }
    public String getDescription() {
        return "Konstante: " + name() + " (Beschreibung: " + description
                + ", Kapazitaet: " + capacity + ", Nummer: " + number
                + ", Ordinal: " + ordinal() + ")";
    }
}
```

### Konstruktoren und Methoden für Enum-Klassen definierbar

- Kein eigener Aufruf von `super` (!)
- Konstruktoren implizit `private`

### Compiler fügt automatisch folgende Methoden hinzu (Auswahl):

- Strings:
  - `public final String name()` =\> Name der Konstanten (`final`!)
  - `public String toString()` =\> Ruft `name()` auf, überschreibbar
- Konstanten:
  - `public final T[] values()` =\> Alle Konstanten der Aufzählung
  - `public final int ordinal()` =\> Interne Nummer der Konstanten
    (Reihenfolge des Anlegens der Konstanten!)
  - `public static T valueOf(String)` =\> Zum String passende Konstante
    (via `name()`)

**Hinweis**: Diese Methoden gibt es auch bei den “einfachen”
Enumerationen (s.o.).

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/tree/master/markdown/java-jvm/src/enums/v3/">Demo: enums.v3</a></p>

## Wrap-Up

- Aufzählungen mit Hilfe von `enum` (Compiler erzeugt intern Klassen)

<!-- -->

- Komplexe Enumerations analog zu Klassendefinition: Konstruktoren,
  Felder und Methoden (keine Instanzen von Enum-Klassen erzeugbar)

<!-- -->

- Enum-Konstanten sind implizit `final` und `static`

- Compiler stellt Methoden `name()`, `ordinal()` und `values()` zur
  Verfügung

  - Name der Konstanten
  - Interne Nummer der Konstanten (Reihenfolge des Anlegens)
  - Array mit allen Konstanten der Enum-Klasse

## 📖 Zum Nachlesen

- Oracle Corporation ([2022](#ref-Java-SE-Tutorial))
- Ullenboom ([2021, Kap. 6.4.3](#ref-Ullenboom2021) und 10.7)

> [!NOTE]
>
> <details>
>
> <summary><strong>✅ Lernziele</strong></summary>
>
> - k2: Vorgänge beim Initialisieren von Enum-Klassen (Hinweis: static)
> - k3: Erstellung komplexer Enumerationen mit Feldern und Konstruktoren
> - k3: Nutzung von name(), ordinal() und values() in Enum-Klassen
>
> </details>

> [!TIP]
>
> <details>
>
> <summary><strong>🧩 Quizzes</strong></summary>
>
> - [Quiz Enumerations
>   (ILIAS)](https://www.hsbi.de/elearning/goto.php?target=tst_1106515&client_id=FH-Bielefeld)
>
> </details>

------------------------------------------------------------------------

> [!NOTE]
>
> <details>
>
> <summary><strong>👀 Quellen</strong></summary>
>
> <div id="refs" class="references csl-bib-body hanging-indent"
> entry-spacing="0">
>
> <div id="ref-Java-SE-Tutorial" class="csl-entry">
>
> Oracle Corporation. 2022. „The Java Tutorials“. 2022.
> <https://docs.oracle.com/javase/tutorial/>.
>
> </div>
>
> <div id="ref-Ullenboom2021" class="csl-entry">
>
> Ullenboom, C. 2021. *Java ist auch eine Insel*. 16. Aufl.
> Rheinwerk-Verlag.
> <https://openbook.rheinwerk-verlag.de/javainsel/index.html>.
>
> </div>
>
> </div>
>
> </details>

------------------------------------------------------------------------

<img src="https://licensebuttons.net/l/by-sa/4.0/88x31.png" width="10%">

Unless otherwise noted, this work is licensed under CC BY-SA 4.0.

<blockquote><p><sup><sub><strong>Last modified:</strong> 02b1db8 (markdown: reformat (#32), 2025-08-10)<br></sub></sup></p></blockquote>
