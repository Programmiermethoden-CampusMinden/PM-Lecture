# Build-Systeme: Apache Ant

> [!IMPORTANT]
>
> <details open>
>
> <summary><strong>🎯 TL;DR</strong></summary>
>
> Zum Automatisieren von Arbeitsabläufen (Kompilieren, Testen, …) stehen
> in der Java-Welt verschiedene Tools zur Verfügung: Apache Ant, Apache
> Maven und Gradle sind sicher die am bekanntesten darunter.
>
> In Apache Ant werden die Build-Skripte in XML definiert. Die äußere
> Klammer ist dabei das `<project>`. In einem Projekt kann es ein oder
> mehrere Teilziele (*Targets*) geben, die untereinander abhängig sein
> können. Die Targets können quasi “aufgerufen” werden bzw. in der IDE
> selektiert und gestartet werden.
>
> In einem Target kann man schließlich mit *Tasks* Aufgaben wie
> Kompilieren, Testen, Aufräumen, … erledigen lassen. Dazu gibt es eine
> breite Palette an vordefinierten Tasks. Zusätzlich sind umfangreiche
> Operationen auf dem Filesystem möglich (Ordner erstellen, löschen,
> Dinge kopieren, …).
>
> Über *Properties* können Werte und Namen definiert werden, etwa für
> bestimmte Ordner. Die Properties sind unveränderliche Variablen (auch
> wenn man sie im Skript scheinbar neu setzen kann).
>
> Über Apache Ivy können analog zu Maven und Gradle definierte
> Abhängigkeiten aus Maven-Central aufgelöst werden.
>
> Im Unterschied zu Maven und Gradle ist in Ant *kein*
> Java-Entwicklungsmodell eingebaut. Man muss sämtliche Targets selbst
> definieren.
>
> </details>

> [!TIP]
>
> <details>
>
> <summary><strong>🎦 Videos</strong></summary>
>
> - [VL Apache Ant](https://youtu.be/LRA1PeQ2pR0)
> - [Demo Aufruf von Ant (Konsole, IDE:
>   hello.xml)](https://youtu.be/EnAQOU_zL1M)
> - [Demo Properties, Targets, Dependencies
>   (build.xml)](https://youtu.be/ip8xFcSZC1c)
> - [Demo Abhängigkeiten mit Ivy auflösen
>   (ivydemo.xml)](https://youtu.be/jizh0bi2TnU)
>
> </details>

## Automatisieren von Arbeitsabläufen

<div align="center">

Works on my machine …

</div>

- Build-Tools:
  - **Apache Ant**
  - Apache Maven
  - Gradle

<!-- -->

- Aufgaben:
  - Übersetzen des Quellcodes
  - Ausführen der Unit-Tests
  - Generieren der Dokumentation
  - Packen der Distribution
  - Aufräumen temporärer Dateien
  - …

=\> Automatisieren mit Apache Ant:
[ant.apache.org](https://ant.apache.org/)

## Aufbau von Ant-Skripten: Projekte und Targets

``` xml
<project name="Vorlesung" default="clean" basedir=".">
    <target name="init" />
    <target name="compile" depends="init" />
    <target name="test" depends="compile" />
    <target name="dist" depends="compile,test" />
    <target name="clean" />
</project>
```

- Ein Hauptziel: `project`
- Ein oder mehrere Teilziele: `target`
  - Abhängigkeiten der Teilziele untereinander möglich: `depends`
  - Vorbedingung für Targets mit `if` oder `unless`

## Aufgaben erledigen: Tasks

- **Tasks**: Aufgaben bzw. Befehle (“Methodenaufruf”), in Targets
  auszuführen
- Struktur: `<taskname attr1="value1" attr2="value2" />`

``` xml
<target name="simplecompile" depends="clean,init">
    <javac srcdir="src" destdir="build" classpath="." />
</target>
```

- Beispiele: `echo`, `javac`, `jar`, `javadoc`, `junit`, …
- Je Target mehrere Tasks möglich
- Quellen:
  - Eingebaute Tasks
  - Optionale Task-Bibliotheken
  - Selbst definierte Tasks

=\> Überblick:
[ant.apache.org/manual/tasksoverview.html](https://ant.apache.org/manual/tasksoverview.html)

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/building/src/ant/hello.xml">Konsole/IDE: ant -f hello.xml</a></p>

## Properties: Name-Wert-Paare

``` xml
<property name="app"       value="MyProject" />
<property name="build.dir" location="build" />

<target name="init">
    <mkdir dir="${build.dir}" />
</target>
```

- Setzen von Eigenschaften: `<property name="wuppie" value="fluppie" />`
  - Properties lassen sich nur einmal setzen (“immutable”)
    - Erneute Definition ist wirkungslos, erzeugt aber leider keinen
      Fehler
- Nutzung von Properties: `<property name="db" value="${wuppie}.db" />`
- Pfade: “`location`” statt “`value`” nutzen:
  `<property name="ziel" location="${p}/bla/blub" />`

<!-- -->

- Properties beim Aufruf setzen mit Option “`-D`”:
  `ant -Dwuppie=fluppie`

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/building/src/ant/build.xml">Beispiel build.xml, Properties</a></p>

## Tasks zum Umgang mit Dateien und Ordnern

``` xml
<target name="demo">
    <mkdir dir="${build.dir}/lib" />

    <delete dir="${build.dir}" />
    <delete file="${dist.dir}/wuppie.jar" />

    <copy file="myfile.txt" tofile="../bak/mycopy.txt" />
    <move file="src/file.orig" tofile="bak/file.moved" />
</target>
```

- `<mkdir dir="${dist}/lib" />`
  - Legt auch direkte Unterverzeichnisse an
  - Keine Aktion, falls Verzeichnis existiert
- `<delete dir="${builddir}" />`
  - Löscht eine Datei (“`file`”) oder ein Verzeichnis (“`dir`”)
    (rekursiv!)
- `<copy file="myfile.txt" tofile="../bak/mycopy.txt" />`
- `<move file="src/file.orig" tofile="bak/file.moved" />`

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/building/src/ant/build.xml">Beispiel build.xml, init und clean</a></p>

## Nutzung von Filesets in Tasks

``` xml
<copy todir="archive">
    <fileset dir="src">
        <include name="**/*.java" />
        <exclude name="**/*.ba?" />
    </fileset>
</copy>

<delete>
    <fileset dir="." includes="**/*.ba?" />
</delete>
```

- “`*`” für beliebig viele Zeichen
- “`?`” für genau ein Zeichen
- “`**`” alle Unterverzeichnisse

Es gibt auch die Variante `<dirset dir="...">`, um Verzeichnisse zu
gruppieren.

## Pfade und externe Bibliotheken

- Als Element direkt im Task:

  ``` xml
  <classpath>
      <pathelement location="${lib}/helper.jar" />
      <pathelement path="${project.classpath}" />
  </classpath>
  ```

  D.h. die Einbettung in den `javac`-Task würde etwa so erfolgen:

  ``` xml
  <target ... >
      <javac ...>
          <classpath>
              <pathelement location="${lib}/helper.jar" />
              <pathelement path="${project.classpath}" />
          </classpath>
      </javac>
  </target>
  ```

  *Anmerkung*: Neben dem `pathelement` können Sie hier auch (wie im
  nächsten Beispiel gezeigt) ein oder mehrere `fileset` nutzen.

<!-- -->

- Wiederverwendbar durch ID und “`refid`”:

  ``` xml
  <path id="java.class.path">
      <fileset dir="${lib}">
          <include name="**/*.jar" />
      </fileset>
  </path>

  <classpath refid="java.class.path" />
  ```

  Die Einbettung in den `javac`-Task würde hier etwa so erfolgen:

  ``` xml
  <path id="java.class.path">
      <fileset dir="${lib}">
          <include name="**/*.jar" />
      </fileset>
  </path>

  <target ... >
      <javac ...>
          <classpath refid="java.class.path" />
      </javac>
  </target>
  ```

  *Anmerkung*: Neben dem `fileset` können Sie hier auch (wie oben
  gezeigt) ein oder mehrere `pathelement` nutzen.

*Anmerkung*: Laut
[ant.apache.org/manual/Tasks/junit.html](https://ant.apache.org/manual/Tasks/junit.html)
benötigt man neben der aktuellen `junit.jar` noch die `ant-junit.jar` im
Classpath, um mit dem `junit`-Ant-Task entsprechende JUnit4-Testfälle
ausführen zu können.

Für JUnit5 gibt es einen neuen Task `JUnitLauncher` (vgl.
[ant.apache.org/manual/Tasks/junitlauncher.html](https://ant.apache.org/manual/Tasks/junitlauncher.html)).

## Beispiele

### Beispiel-Task: Kompilieren

``` xml
<path id="project.classpath">
    <fileset dir="${lib.dir}" includes="**/*.jar" />
</path>

<target name="compile" depends="init" description="compile the source " >
    <javac srcdir="${src.dir}" destdir="${build.dir}">
        <classpath refid="project.classpath" />
    </javac>
</target>
```

### Beispiel-Task: Packen

``` xml
<target name="dist" depends="compile" description="generate the distribution" >
    <mkdir dir="${dist.dir}" />
    <jar jarfile="${dist.dir}/${app}.jar" basedir="${build.dir}">
        <manifest>
            <attribute name="Main-Class"  value="${app}" />
        </manifest>
    </jar>
</target>
```

### Beispiel-Task: Testen

- Tests einer Testklasse ausführen:

  ``` xml
  <junit>
      <test name="my.test.TestCase" />
  </junit>
  ```

- Test ausführen und XML mit Ergebnissen erzeugen:

  ``` xml
  <junit printsummary="yes" fork="yes" haltonfailure="yes">
      <formatter type="xml" />
      <test name="my.test.TestCase" />
  </junit>
  ```

- Verschiedene Tests als Batch ausführen:

  ``` xml
  <junit printsummary="yes" haltonfailure="yes">
      <classpath>
          <pathelement location="${build.tests}" />
          <pathelement path="${java.class.path}" />
      </classpath>

      <formatter type="plain"/>

      <test name="my.test.TestCase" haltonfailure="no" outfile="result">
          <formatter type="xml" />
      </test>

      <batchtest fork="yes" todir="${reports.tests}">
          <fileset dir="${src.tests}">
              <include name="**/*Test*.java" />
              <exclude name="**/AllTests.java" />
          </fileset>
      </batchtest>
  </junit>
  ```

- Aus Testergebnis (XML) einen Report generieren:

  ``` xml
  <junitreport todir="${reportdir}">
      <fileset dir="...">
          <include name="TEST-*.xml" />
      </fileset>
      <report format="frames" todir="..." />
  </junitreport>
  ```

- Abbruch bei Fehler:

  ``` xml
  <junit ... failureproperty="tests.failed" ... >
      <fail if="tests.failed" />
  </junit>
  ```

=\> `junit.jar` und `ant-junit.jar` (JUnit4.x) im Pfad!

### Programme ausführen

``` xml
<target name="run">
    <java jar="build/jar/HelloWorld.jar" fork="true" classname ="test.Main">
        <arg value ="-h" />
        <classpath>
            <pathelement location="./lib/test.jar" />
        </ classpath>
    </ java>
</target>
```

## Ausblick: Laden von Abhängigkeiten mit Apache Ivy

[Apache Ivy](https://ant.apache.org/ivy/): Dependency Manager für Ant

``` xml
<!-- build.xml -->
<project xmlns:ivy="antlib:org.apache.ivy.ant">
    <target name="resolve">
        <ivy:retrieve/>
    </target>
</project>
```

Wenn Ivy installiert ist, kann man durch den Eintrag
`xmlns:ivy="antlib:org.apache.ivy.ant"` in der Projekt-Deklaration im
Ant-Skript die Ivy-Tasks laden. Der wichtigste Task ist dabei
`ivy:retrieve`, mit dem externe Projektabhängigkeiten heruntergeladen
werden können.

``` xml
<!-- ivy.xml -->
<ivy-module version="2.0">
    <dependencies>
        <dependency org="commons-cli" name="commons-cli" rev="1.5.0" />
        <dependency org="junit" name="junit" rev="4.13.2" />
    </dependencies>
</ivy-module>
```

Zur Steuerung von Ivy legt man eine weitere Datei `ivy.xml` an. Das
Wurzelelement ist `ivy-module`, wobei die `version` die niedrigste
kompatible Ivy-Version angibt.

Der `dependencies`-Abschnitt definiert dann die Abhängigkeiten, die Ivy
auflösen muss. Die Schreibweise ist dabei wie im Maven2 Repository
([mvnrepository.com](https://mvnrepository.com/)) angelegt. Dort findet
man beispielsweise für Apache Commons CLI den Eintrag für Maven
(“POM”-Datei):

``` xml
<!-- https://mvnrepository.com/artifact/commons-cli/commons-cli -->
<dependency>
    <groupId>commons-cli</groupId>
    <artifactId>commons-cli</artifactId>
    <version>1.4</version>
</dependency>
```

Für die Ivy-Konfiguration übernimmt man die `groupId` als `org`, die
`artifactId` als `name` und die `version` als `rev` im Eintrag
`dependency`.

Damit kann Ivy diese Bibliothek über den Ant-Task `ivy:retrieve` vor dem
Bauen herunterladen, sofern die Bibliothek noch nicht lokal vorhanden
ist. Eventuelle Abhängigkeiten werden dabei ebenfalls aufgelöst.

Im Detail: Der Ant-Task `ivy:retrieve` löst zunächst die Abhängigkeiten
auf und lädt die Dateien (sofern sie noch nicht vorhanden oder veraltet
sind) in den Ivy-Cache (per Default: `~/.ivy2/cache/`). Danach werden
die Dateien in den Default-Library-Order im Projekt kopiert (per Defaul:
`./lib/`). Die Ordner kann man über Optionen im `ivy:retrieve`-Task
einstellen.

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/PM-Lecture/blob/master/markdown/building/src/ant/ivydemo.xml">Demo: ivydemo.xml</a></p>

## Ausblick: Weitere Build-Systeme

- [Maven](https://maven.apache.org/)
  - War als Nachfolger von Ant gedacht
  - Statt wie bei Ant explizit Targets zu formulieren, geht Maven von
    einem Standardprojekt aus - nur noch Abweichungen müssen formuliert
    werden
  - Zieht Abhängigkeiten in zentralen `.maven`-Ordner

<!-- -->

- [Gradle](https://gradle.org/)
  - Eine Art Mischung aus Ant und Maven unter Nutzung der Sprache Groovy

<!-- -->

- [Make](https://www.gnu.org/software/make/)
  - DER Klassiker, stammt aus der C-Welt. Kann aber natürlich auch Java.
  - Analog zu Ant: Aktionen und Ziele müssen explizit definiert werden

## Wrap-Up

Apache Ant: [ant.apache.org](https://ant.apache.org/)

- Automatisieren von Arbeitsabläufen
- Apache Ant: Targets, Tasks, Properties
  - Targets sind auswählbare Teilziele
  - Abhängigkeiten zwischen Targets möglich
  - Tasks erledigen Aufgaben (innerhalb Targets)
  - Properties sind nicht änderbare Variablen
  - Umfangreiche Operationen auf Filesystem möglich

## 📖 Zum Nachlesen

- Inden ([2013, Abschn. 2.5.2](#ref-Inden2013))

> [!NOTE]
>
> <details>
>
> <summary><strong>✅ Lernziele</strong></summary>
>
> - k3: Schreiben einfacher Ant-Skripte mit Abhängigkeiten zwischen den
>   Targets
> - k3: Nutzung von Ant-Filesets (Dateisystemoperationen, Classpath)
> - k3: Nutzung von Ant-Properties
> - k3: Ausführen von Ant-Targets aus der IDE heraus
>
> </details>

> [!TIP]
>
> <details>
>
> <summary><strong>🧩 Quizzes</strong></summary>
>
> - [Quiz Apache Ant
>   (ILIAS)](https://www.hsbi.de/elearning/goto.php?target=tst_1106214&client_id=FH-Bielefeld)
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
> <div id="ref-Inden2013" class="csl-entry">
>
> Inden, M. 2013. *Der Weg zum Java-Profi*. 2. Aufl. dpunkt.verlag.
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
