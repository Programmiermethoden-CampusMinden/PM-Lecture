# Fähigkeiten

## Ziel

In dieser Aufgabe sollen Sie den Levelaufstieg[^1] und verschiedene
Fähigkeiten implementieren, die dann vom Spieler verwendet werden
können.

## Fähigkeiten

In den Vorgaben ist bereits ein
[Projectile-System](https://github.com/Dungeon-CampusMinden/Dungeon/blob/master/dungeon/src/contrib/systems/ProjectileSystem.java)
und ein
[Feuerball-Skill](https://github.com/Dungeon-CampusMinden/Dungeon/blob/master/dungeon/src/contrib/utils/components/skill/FireballSkill.java)
implementiert. Führen Sie eine Codeanalyse durch und erklären Sie die
Funktionalität.

Implementieren Sie ein Magie-Konzept. Der Spieler soll in der Lage sein,
verschiedene Zauber zu verwenden.

Beachten Sie dabei, dass es sich nicht um Zauber handeln soll, die
Schaden verursachen. Zauber, die Monster anderweitig manipulieren, sind
erlaubt.

Überlegen Sie sich zwei verschiedene Zaubersprüche wie Gedankenkontrolle
oder Telekinese oder Upgrade von Waffen/Rüstungen.

Eine der Fähigkeiten soll eine Form von Ressourcenkosten haben. Sie
verbraucht also Lebenspunkte, Ausdauerpunkte,
[Mana-Punkte](https://de.wikipedia.org/wiki/Mana_(Spiele)) oder
ähnliches.

## Levelaufstieg

In den Vorgaben gibt es bereits ein
[XP-System](https://github.com/Dungeon-CampusMinden/Dungeon/blob/master/game/src/ecs/systems/XPSystem.java)
um Erfahrungspunkte zu sammeln und um Level aufzusteigen. Führen Sie
eine Codeanalyse durch und erklären Sie die Funktionalität.

Verbessern Sie beim Levelaufstieg des Helden seine Charakterwerte und
lassen Sie ihn die oben implementierten Zaubersprüche erlernen.

------------------------------------------------------------------------

<img src="https://licensebuttons.net/l/by-sa/4.0/88x31.png" width="10%">

Unless otherwise noted, this work is licensed under CC BY-SA 4.0.

<blockquote><p><sup><sub><strong>Last modified:</strong> e9b0bb0 (markdown: switch to leaner yaml header (#31), 2025-08-08)<br></sub></sup></p></blockquote>

[^1]: “Levelaufstieg” bezieht sich nicht auf die Dungeon-Ebenen
    (“Dungeon-Level”), sondern auf die Erfahrungen und die (Level-)
    Einstufung des Spielers.
