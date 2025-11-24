# Singleton-Pattern

> [!IMPORTANT]
>
> <details open>
>
> <summary><strong>🎯 TL;DR</strong></summary>
>
> Wenn von einer Klasse nur genau ein Objekt angelegt werden kann, nennt
> man dies auch das “Singleton-Pattern”.
>
> Dazu muss verhindert werden, dass der Konstruktor aufgerufen werden
> kann. Üblicherweise “versteckt” man diesen einfach (Sichtbarkeit auf
> `private` setzen). Für den Zugriff auf die Instanz bietet man eine
> statische Methode an.
>
> Im Prinzip kann man die Instanz direkt beim Laden der Klasse anlegen
> (“Eager”) oder abwarten, bis die Instanz über die statische Methode
> angefordert wird, und das Objekt erst dann anlegen (“Lazy”).
> </details>

> [!TIP]
>
> <details open>
>
> <summary><strong>🎦 Videos</strong></summary>
>
> - [VL Singleton-Pattern](https://youtu.be/ZT3rl1t85aY)
>
> </details>

## Motivation

``` java
public enum Fach { IFM, ELM, ARC }
```

``` java
Logger l = Logger.getLogger(MyClass.class.getName());
```

Von den Enum-Konstanten soll es nur genau eine Instantiierung, also
jeweils nur genau ein Objekt geben. Ähnlich war es beim Logging: Für
jeden Namen soll/darf es nur einen tatsächlichen Logger (== Objekt)
geben.

Dies nennt man “**Singleton Pattern**”.

*Anmerkung*: Im Logger-Fall handelt es sich streng genommen nicht um ein
Singleton, da es vom Logger mehrere Instanzen geben kann (wenn der Name
sich unterscheidet). Aber jeden Logger mit einem bestimmten Namen gibt
es nur einmal im ganzen Programm, insofern ist es doch wieder ein
Beispiel für das Singleton-Pattern …

## Umsetzung: “Eager” Singleton Pattern

Damit man von “außen” keine Instanzen einer Klasse anlegen kann,
versteckt man den Konstruktor, d.h. man setzt die Sichtbarkeit auf
`private`. Zusätzlich benötigt man eine Methode, die das Objekt
zurückliefern kann. Beim Logger war dies beispielsweise der Aufruf
`Logger.getLogger("name")`.

Man kann verschiedene Ausprägungen bei der Umsetzung des Singleton
Patterns beobachten. Die beiden wichtigsten sind das “Eager Singleton
Pattern” und das “Lazy Singleton Pattern”. Der Unterschied liegt darin,
wann genau das Objekt erzeugt wird: Beim “Eager Singleton Pattern” wird
es direkt beim Laden der Klasse erzeugt.

``` java
public class SingletonEager {
    private static final SingletonEager inst = new SingletonEager();

    // Privater Constructor: Niemand kann Objekte außerhalb der Klasse anlegen
    private SingletonEager() {}

    public static SingletonEager getInst() {
        return inst;
    }
}
```

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/pattern/src/singleton/SingletonEager.java">Beispiel: singleton.SingletonEager</a></p>

## Umsetzung: “Lazy” Singleton Pattern

Beim “Lazy Singleton Pattern” wird das Objekt erst erzeugt, wenn die
Instanz tatsächlich benötigt wird (also erst beim Aufruf der
`get`-Methode).

``` java
public class SingletonLazy {
    private static SingletonLazy inst = null;

    // Privater Constructor: Niemand kann Objekte außerhalb der Klasse anlegen
    private SingletonLazy() {}

    public static SingletonLazy getInst() {
        // Thread-safe. Kann weggelassen werden bei Single-Threaded-Gebrauch
        synchronized (SingletonLazy.class) {
            if (inst == null) {
                inst = new SingletonLazy();
            }
        }
        return inst;
    }
}
```

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/pattern/src/singleton/SingletonLazy.java">Beispiel: singleton.SingletonLazy</a></p>

## Vorsicht!

<div align="center">

Sie schaffen damit eine globale Variable!

</div>

Da es von der Klasse nur eine Instanz gibt, und Sie sich diese dank der
statischen Methode an jeder Stelle im Programm “geben” lassen können,
haben Sie in der Praxis eine globale Variable geschaffen. Das kann
direkt zu schlechter Programmierung (ver-) führen. Zudem wird der Code
schwerer lesbar/navigierbar, da diese Singletons nicht über die
Schnittstellen von Methoden übergeben werden müssen.

Nutzen Sie das Pattern **sparsam**.

## Wrap-Up

Singleton-Pattern: Klasse, von der nur genau ein Objekt instantiiert
werden kann

1.  Konstruktor “verstecken” (Sichtbarkeit auf `private` setzen)
2.  Methode zum Zugriff auf die eine Instanz
3.  Anlegen der Instanz beispielsweise beim Laden der Klasse (“Eager”)
    oder beim Aufruf der Zugriffsmethode (“Lazy”)

## 📖 Zum Nachlesen

- Nystrom ([2014, Kap. 6](#ref-Nystrom2014))

> [!NOTE]
>
> <details>
>
> <summary><strong>✅ Lernziele</strong></summary>
>
> - k2: Was ist ein Singleton? Was ist der Unterschied zw. einem Lazy
>   und einem Eager Singleton?
> - k3: Anwendung des Singleton-Patterns
>
> </details>

> [!TIP]
>
> <details>
>
> <summary><strong>🧩 Quizzes</strong></summary>
>
> - [Quiz Singleton-Pattern
>   (ILIAS)](https://www.hsbi.de/elearning/goto.php?target=tst_1106536&client_id=FH-Bielefeld)
>
> </details>

------------------------------------------------------------------------

> [!NOTE]
>
> <details>
>
> <summary><strong>👀 Quellen</strong></summary>
>
> <div id="refs" class="references csl-bib-body hanging-indent">
>
> <div id="ref-Nystrom2014" class="csl-entry">
>
> Nystrom, R. 2014. *Game Programming Patterns*. Genever Benning.
> <https://github.com/munificent/game-programming-patterns>.
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
