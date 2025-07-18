# IFM 2.2: Programmiermethoden (Sommer 2023)

> [!WARNING]
>
> ## Abkündigung des Moduls “Programmiermethoden”
>
> Das Modul “Programmiermethoden” wurde im Rahmen der Reakkreditierung
> im Herbst 2023 durch das kleinere Modul [“Programmieren
> 2”](https://github.com/Programmiermethoden-CampusMinden/PM-Lecture)
> ersetzt und kann nicht mehr belegt werden (es werden keine Vorlesungen
> und keine Praktika mehr für “Programmiermethoden” angeboten).
>
> Die Inhalte von “Programmiermethoden” werden hier für Wiederholende
> weiterhin gepflegt. Das zugehörige Lernmodul finden Sie im [offenen
> ILIAS-Bereich](https://www.hsbi.de/elearning/goto.php?target=crs_1181185&client_id=FH-Bielefeld)
> der HSBI.
>
> Bis zum Auslaufen der zugehörigen Prüfungsordnungen
> [PO10](https://www.hsbi.de/multimedia/Hochschulverwaltung/Dezernat+II/StudServ/Prüfungsangelegenheiten/Studiengangs_Downloads/Informatik+_+IFM/Prüfungsordnung+und+Modulhandbuch+Bachelor+Informatik+Version+10+%28Fassung+09_2023%29-p-174010.pdf)
> und
> [PO18](https://www.hsbi.de/multimedia/Hochschulverwaltung/Dezernat+II/StudServ/Prüfungsangelegenheiten/Studiengangs_Downloads/Informatik+_+IFM/Studiengangsprüfungsordnung+und+Modulhandbuch+Bachelor+Informatik+Version+18+%28Fassung+09_2023%29-p-169988.pdf) finden
> auch weiterhin Prüfungen für Wiederholende statt.
>
> ### Regelung für noch offene Prüfungen
>
> Wer in “Programmiermethoden” noch eine Prüfung benötigt, kann diese in
> den Prüfungszeiträumen des Sommersemesters (und ggf. des
> Wintersemesters, falls angeboten) als Klausur nachholen.
>
> Dabei gelten folgende Regelungen (vgl. Mail von Frau Seele vom
> 28.09.2023) für offene Prüfungsverfahren:
>
> - Parcoursprüfung: Bei einer offenen Parcoursprüfung bildet die
>   Klausur die gesamte Prüfung.
> - Performanzprüfung:
>   - Der praktische Teil der Performanzprüfung entfällt, die Note und
>     CP werden über eine Klausur bestimmt.
>   - Wenn Sie aber bereits eine Note bzw. CP für den praktischen Teil
>     haben (und nur die theoretische Leistung noch fehlt), dann nehmen
>     Sie an der weiterhin angebotenen Klausur teil und die Gesamtnote
>     wird sich wie bisher aus den beiden Teilnoten zusammensetzen.
>
> ### Nächste Klausur
>
> Der Termin für die nächste Klausur für “Programmiermethoden” wird über
> den Prüfplan vom Studierendenservice bekanntgegeben. (vgl. LSF und
> [Ankündigungen](https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/discussions/categories/announcements))

------------------------------------------------------------------------

## Kursbeschreibung

Sie haben letztes Semester in **OOP** die *wichtigsten* Elemente und
Konzepte der Programmiersprache Java kennen gelernt.

In diesem Modul geht es darum, diese Kenntnisse sowohl auf der Java- als
auch auf der Methoden-Seite so zu erweitern, dass Sie gemeinsam größere
Anwendungen erstellen und pflegen können. Sie werden fortgeschrittene
Konzepte in Java kennenlernen und sich mit etablierten Methoden in der
Softwareentwicklung wie Versionierung von Code, Einhaltung von Coding
Conventions, Grundlagen des Softwaretests, Anwendung von Refactoring,
Einsatz von Build-Tools und Logging auseinander setzen. Wenn uns dabei
ein Entwurfsmuster “über den Weg läuft”, werden wir die Gelegenheit
nutzen und uns dieses genauer anschauen.

## Überblick Modulinhalte

1.  Fortgeschrittene Konzepte in Java
    - Funktionale Programmierung: Default-Methoden, Funktionsinterfaces,
      Methodenreferenzen, Lambdas, Stream-API
    - Generische Programmierung: Generics
    - Parallele Programmierung: Threads
    - Reguläre Ausdrücke, Annotationen, Reflection
    - CLI, Konfiguration, Fremde APIs nutzen
2.  Fortgeschrittenes OO-Design
    - Entwurfsmuster: Strategy, Template-Method, Factory-Method,
      Singleton, Observer, Visitor, Command, …
3.  Programmiermethoden
    - Versionskontrolle: Git
    - Testen, Coding Conventions, Refactoring
    - Logging, Build-Tools, CI

## Team

- [Carsten
  Gips](https://www.hsbi.de/minden/ueber-uns/personenverzeichnis/carsten-gips)
- Tutoren (siehe ILIAS-Mitgliederliste)

## Kursformat

### Vorlesung (2 SWS)

Fr, 16:30 - 18:00 Uhr (online/J104)

### Praktikum (2+1 SWS)

| Praktikumsgruppe | Zeit                  | Raum        |
|:-----------------|:----------------------|:------------|
| Gruppe 1         | Fr, 09:00 - 10:30 Uhr | online/J104 |
| Gruppe 2         | Fr, 13:30 - 15:00 Uhr | online/J104 |
| Gruppe 3         | Fr, 15:00 - 16:30 Uhr | online/J104 |
| Gruppe 4         | Fr, 10:45 - 12:15 Uhr | online/J104 |

Durchführung als **Flipped Classroom**: Alle Sitzungen online/per Zoom
(**Zugangsdaten siehe
[ILIAS](https://www.hsbi.de/elearning/goto.php?target=crs_1181185&client_id=FH-Bielefeld)**)

## Fahrplan

### Vorlesung

| Woche | Datum Vorlesung | Themen | Bemerkungen |
|:--:|:---|:---|:---|
| 15 | Fr, 14.04. | Orga (**Zoom**) \|\| [Einführung Versionierung](lecture/git/git-intro.md) \| [Git Basics](lecture/git/git-basics.md) \|\| [Lambda-Ausdrücke](lecture/modern-java/lambdas.md) \|\| [Javadoc](lecture/coding/javadoc.md) |  |
| 16 | Fr, 21.04. | Git: [Branches](lecture/git/branches.md) \| [Branching-Strategies](lecture/git/branching-strategies.md) \|\| [Gradle](lecture/building/gradle.md) \|\| [Methodenreferenzen](lecture/modern-java/methodreferences.md) \|\| [Strategy-Pattern](lecture/pattern/strategy.md) |  |
| 17 | Fr, 28.04. | Git: [Remotes](lecture/git/remotes.md) \| [Workflows](lecture/git/workflows.md) \|\| [Stream-API](lecture/modern-java/stream-api.md) \| [Optional](lecture/modern-java/optional.md) |  |
| 18 | Fr, 05.05. | Testen: [Einführung](lecture/testing/testing-intro.md) \| [JUnit-Basics](lecture/testing/junit-basics.md) \| [Testfallermittlung](lecture/testing/testcases.md) \| [Mocking](lecture/testing/mockito.md) \|\| [Logging](lecture/coding/logging.md) |  |
| 19 | Fr, 12.05. | [Code-Smells](lecture/coding/smells.md) \| [Coding-Rules](lecture/coding/codingrules.md) \| [Refactoring](lecture/coding/refactoring.md) \|\| [CI](lecture/building/ci.md) | **Gastvortrag zu JUnit/Mocking in der Praxis von Daniel Rosowski (Smartsquare GmbH, Bielefeld)** |
| 20 | Fr, 19.05. | [Serialisierung](lecture/java-jvm/serialisation.md) \|\| [Records](lecture/modern-java/records.md) \| [Default-Methoden](lecture/modern-java/defaultmethods.md) \|\| [Docker](lecture/building/docker.md) \|\| [Git-Worktree](lecture/git/worktree.md) |  |
| 21 | Fr, 26.05. | Generics: [Klassen und Methoden](lecture/generics/classes-methods.md) \| [Bounds und Wildcards](lecture/generics/bounds-wildcards.md) \| [Type Erasure](lecture/generics/type-erasure.md) \| [Polymorphie](lecture/generics/generics-polymorphism.md) \|\| [Collections](lecture/java-jvm/collections.md) |  |
| 22 | Fr, 02.06. | [RegExp](lecture/java-jvm/regexp.md) \|\| Pattern: [Visitor](lecture/pattern/visitor.md) \| [Observer](lecture/pattern/observer.md) \| [Command](lecture/pattern/command.md) |  |
| 23 | Fr, 09.06. | [Annotationen](lecture/java-jvm/annotations.md) \| [Reflection](lecture/java-jvm/reflection.md) \| [Exception-Handling](lecture/java-jvm/exceptions.md) \|\| [Singleton-Pattern](lecture/pattern/singleton.md) |  |
| 24 | Fr, 16.06. | [Enumerationen](lecture/java-jvm/enums.md) \| [Konfiguration](lecture/java-jvm/configuration.md) \| [ANT](lecture/building/ant.md) \|\| [Template-Method-Pattern](lecture/pattern/template-method.md) \| [Factory-Method-Pattern](lecture/pattern/factory-method.md) |  |
| 25 | Fr, 23.06. | Multi-Threading: [Intro Threads](lecture/threads/threads-intro.md) \| [Synchronisierung](lecture/threads/threads-synchronisation.md) \| [Highlevel Threadkonzepte](lecture/threads/threads-highlevel.md) \|\| [Maven](lecture/building/maven.md) \|\| [Type-Object-Pattern](lecture/pattern/type-object.md) |  |
| 26 | Fr, 30.06. | Rückblick (**Zoom**) \| [Prüfungsvorbereitung](admin/exams.md) |  |
| *27* | *Mi, 05.07.* (Start: 09:00 und 11:00 Uhr) | Klausur (Campus Minden, B40) |  |

### Praktikum

| Woche | Blatt | Abgabe ILIAS und Peer-Feedback (ILIAS) | Vorstellung Praktikum |
|:--:|:---|:---|:---|
| 16 | [B01a](homework/b01a.md) | Abgabe: Do, 20.04., 08 Uhr; Peer-Feedback: Fr, 21.04., 08 Uhr | Praktikum: Fr, 21.04. |
| 17 | [B01b](homework/b01b.md) | Abgabe: Do, 27.04., 08 Uhr; Peer-Feedback: Fr, 28.04., 08 Uhr | Praktikum: Fr, 28.04. |
| 18 | [B02a](homework/b02a.md) | Abgabe: Do, 04.05., 08 Uhr; Peer-Feedback: Fr, 05.05., 08 Uhr | Praktikum: Fr, 05.05. |
| 19 | [B02b](homework/b02b.md) | Abgabe: Do, 11.05., 08 Uhr; Peer-Feedback: Fr, 12.05., 08 Uhr | Praktikum: Fr, 12.05. |
| 20 | [B03a](homework/b03a.md) | Abgabe: Do, 18.05., 08 Uhr; Peer-Feedback: Fr, 19.05., 08 Uhr | Praktikum: Fr, 19.05. |
| 21 | [B03b](homework/b03b.md) | Abgabe: Do, 25.05., 08 Uhr; Peer-Feedback: Fr, 26.05., 08 Uhr | Praktikum: Fr, 26.05. |
| 22 | [B04a](homework/b04a.md) | Abgabe: Do, 01.06., 08 Uhr; Peer-Feedback: Fr, 02.06., 08 Uhr | Praktikum: Fr, 02.06. |
| 23 | [B04b](homework/b04b.md) | Abgabe: Do, 08.06., 08 Uhr; Peer-Feedback: Fr, 09.06., 08 Uhr | Praktikum: Fr, 09.06. |
| 24 | [B05a](homework/b05a.md) | Abgabe: Do, 15.06., 08 Uhr; Peer-Feedback: Fr, 16.06., 08 Uhr | Praktikum: Fr, 16.06. |
| 25 | [B05b](homework/b05b.md) | Abgabe: Do, 22.06., 08 Uhr; Peer-Feedback: Fr, 23.06., 08 Uhr | Praktikum: Fr, 23.06. |
| 26 | [B06](homework/b06.md) | Abgabe: Fr, 30.06., 08 Uhr | Praktikum: Fr, 30.06. |

## Prüfungsform, Note und Credits

**Performanzprüfung**, 7 ECTS

- **Praktische Teilleistung**: Regelmäßige Bearbeitung der
  Praktikumsaufgaben, fristgerechte Abgabe der Lösungen (PDF, ZIP, Link)
  im ILIAS, Erstellung von Peer-Feedback im ILIAS, Vorstellung der
  Lösungen im Praktikum =\> Punkte

  Notenspiegel:

  - 90 Punkte gesamt erreichbar: Zyklus 1 und 2 je 15 Punkte, Zyklus 3
    bis 5 je 15+5 Punkte
  - 4.0: ab 50% (45.0 Punkte), alle 5% nächste Teilnote, 1.0: ab 95%
    (85.5 Punkte)

- **Theoretische Teilleistung**: Digitale Klausur (“**Klausur**”) in den
  Prüfungszeiträumen; [Prüfungsvorbereitung](admin/exams.md).

- **Gesamtnote**: 50% Praxis, 50% Theorie

Wiederholer mit bereits begonnener Parcours-Prüfung absolvieren
stattdessen eine Parcours-Prüfung. Bitte melden Sie sich vor Beginn der
Praktika per E-Mail beim Dozenten.

## Materialien

### Literatur

1.  [“**Java ist auch eine
    Insel**”](https://openbook.rheinwerk-verlag.de/javainsel/index.html).
    Ullenboom, C., Rheinwerk-Verlag, 2021. ISBN
    [978-3-8362-8745-6](https://fhb-bielefeld.digibib.net/openurl?isbn=978-3-8362-8745-6).
2.  [“**Pro Git** (Second Edition)”](https://git-scm.com/book/en/v2).
    Chacon, S. und Straub, B., Apress, 2014. ISBN
    [978-1-4842-0077-3](https://fhb-bielefeld.digibib.net/openurl?isbn=978-1-4842-0077-3).
3.  [“The Java Tutorials”](https://docs.oracle.com/javase/tutorial/).
    Oracle Corporation, 2023.
4.  [“Learn Java”](https://dev.java/learn/). Oracle Corporation, 2023.

### Tools

- JDK: Java SE 21 (LTS)
  ([Oracle](https://www.oracle.com/java/technologies/downloads/) oder
  [Alternativen](https://code.visualstudio.com/docs/languages/java#_install-a-java-development-kit-jdk),
  bitte 64-bit Version nutzen)
- IDE: [Eclipse IDE for Java
  Developers](https://www.eclipse.org/downloads/) oder [IntelliJ IDEA
  (Community Edition)](https://www.jetbrains.com/idea/) oder [Visual
  Studio Code](https://code.visualstudio.com/) oder
  [Vim](https://www.vim.org/) oder …
- [Git](https://git-scm.com/)

## Förderungen und Kooperationen

### Förderung durch DH.NRW (Digi Fellowships)

Die Überarbeitung dieser Lehrveranstaltung wurde vom Ministerium für
Kultur und Wissenschaft (MKW) in NRW im Einvernehmen mit der Digitalen
Hochschule NRW (DH.NRW) gefördert: [“Fellowships für Innovationen in der
digitalen
Hochschulbildung”](https://www.dh.nrw/kooperationen/Digi-Fellows-2)
(*Digi Fellowships*).

### Kooperation mit dem DigikoS-Projekt

Diese Vorlesung wird zudem vom Projekt [“Digitalbaukasten für
kompetenzorientiertes Selbststudium”](https://www.digikos.de)
(*DigikoS*) unterstützt. Ein vom DigikoS-Projekt ausgebildeter Digital
Learning Scout hat insbesondere die Koordination der digitalen
Gruppenarbeiten, des Peer-Feedbacks und der Postersessions in ILIAS
technisch und inhaltlich begleitet. DigikoS wird als Verbundprojekt von
der Stiftung Innovation in der Hochschullehre gefördert.

------------------------------------------------------------------------

## LICENSE

[<img src="https://licensebuttons.net/l/by-sa/4.0/88x31.png">](https://creativecommons.org/licenses/by-sa/4.0/)

Unless otherwise noted, [this
work](https://github.com/Programmiermethoden-CampusMinden/PM-Lecture) by
[Carsten Gips](https://github.com/cagix) and
[contributors](https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/graphs/contributors)
is licensed under [CC BY-SA
4.0](https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/LICENSE.md).
See the [credits](CREDITS.md) for a detailed list of contributing
projects.

> <sup><sub>**Last
> modified:** ac03323 (Readme: remove links to different preview variants, 2025-07-02)</sub></sup>
