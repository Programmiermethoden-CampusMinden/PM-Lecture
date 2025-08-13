# Fernkampf

## Ziel

In dieser Aufgabe implementieren Sie Projektile für den Fernkampf, damit
der Held gegen die Monster auf Distanz kämpfen kann.

## Voraussetzung

Um diese Aufgabe lösen zu können, müssen Sie vorher
[“Monster”](tasknpc-monster.md) implementiert haben.

## Fernkampf

In den Vorgaben ist ein Konzept für den [Fernkampf mit
Skills](https://github.com/Dungeon-CampusMinden/Dungeon/tree/master/game/src/ecs/components/skill)
mit einen [Projektil
System](https://github.com/Dungeon-CampusMinden/Dungeon/blob/master/dungeon/src/contrib/systems/ProjectileSystem.java)
implementiert. Führen Sie eine Codeanalyse durch und erklären Sie, wie
das Konzept funktioniert.

Implementieren Sie zwei unterschiedliche Projektile, die sich vom
bereits implementierten Feuerball durch ihr Flugverhalten unterscheiden.
Denkbar wäre ein Bumerang, der im Bogen zurück zum Spieler fliegt, oder
ein Projektil, welches über die Distanz “nach unten fällt”, oder ein
Projektil, das an Wänden abprallt.

Trifft das Projektil auf einen Gegner (oder den Helden), verursacht es
Schaden und fliegt nicht mehr weiter. Trifft das Projektil auf eine
Wand, fliegt es nicht mehr weiter.

Bei einem Treffer soll der Getroffene eine kurze Distanz
zurückgeschleudert werden. Beachten Sie dabei, dass niemand durch eine
Wand bewegt wird.

------------------------------------------------------------------------

<img src="https://licensebuttons.net/l/by-sa/4.0/88x31.png" width="10%">

Unless otherwise noted, this work is licensed under CC BY-SA 4.0.

<blockquote><p><sup><sub><strong>Last modified:</strong> 02b1db8 (markdown: reformat (#32), 2025-08-10)<br></sub></sup></p></blockquote>
