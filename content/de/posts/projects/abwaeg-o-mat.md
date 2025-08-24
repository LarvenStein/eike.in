+++
title = 'Abwäg-o-mat'
summary = 'Dein o-mat, mit welchem du einfach Pro/Kontra situationen abwägen kannst!'
date = 2025-08-24
showDate = false
showAuthor = false
featureimage = 'https://media.eike.in/data/website/abwaegomat/Screenshot%202025-08-21%20at%2021-45-35%20Abw%C3%A4g-o-mat.png'
showHero = true
showTableOfContents = true
tags = ['web', 'api', 'javascript']
showReadingTime = false
showWordCount = false
+++

## Kurzbeschreibung
Um mit dem Tech-Stack meines Praktikums vertrauter zu werden, habe ich ein [altes Projekt](https://github.com/LarvenStein/abwaeg-o-mat/tree/legacy) von mir mit `typescript` und `express.js` neu geschrieben. 

Hierbei handelt es sich um ein Projekt welches es einem erlaubt, Pro/Kontra entscheidungen strukturiert aufzuschreiben und am eine aufschlüsseelung der Ergebnisse zu erhalten. 
Mit dem rewrite ist es auch möglich, eine Argumentation zu speichern, diese auf dem Server mittels Passowrt zu verschlüsseln und mit einem Ablaufdatum zu Teilen.

### Features
* Strukturiertes erstellen einer Argumentation in schritten
    1. Eingeben einer These
    2. Eingeben der pro- und kontra Argumente
    3. Zuteilen von Gewichtungen zu den Argumenten `(1x/2x/3x/4x/5x)`
* Deteilierte Aufschlüsselung der Argumente und auswertung einer Gewinnerseite
    * Erneute anzeige aller Argumente inkl. Gewichtungen
    * Aufschlüsselung der Punktevergabe
    * Anzeige des Ergebnisses der Argumentation
* Speichern der Argumentationsauswertung
    * Möglichkeit zum verschlüsseln der Argumentation in der Datenbank mittels Passwort und `AES256`
    * Festlegen eines Ablaufdatums
        * Bei zugriff nach dem Datum wird die Argumentation aus der Datenbank gelöscht
        * Ggf. automatisierte Löschung über `cron` möglich.
* Teilen von Argumentationen mittels Link
* Unterstützung für verschiedene Sprachen (aktuell Deutsch, Englisch und Niederländisch)

## Technologien
Das Backend wurde in `typescript` und `express.js` geschrieben. Als Datenbank wird `sqlite` mittels `sequelize` verwendet.

Das frontend wird serverseitig gerendert. Als Template-engine kommt hier `pug` zum einsatz.

## Screenshots
{{< gallery >}}
  <img src="https://media.eike.in/data/website/abwaegomat/de/Screenshot%202025-08-24%20at%2012-19-21%20Abw%C3%A4g-o-mat.png" class="grid-w50" alt="Startseite der App" />
  <img src="https://media.eike.in/data/website/abwaegomat/de/Screenshot%202025-08-24%20at%2012-18-28%20Abw%C3%A4g-o-mat.png" class="grid-w50" alt="Eintragen der Argumente" />
  <img src="https://media.eike.in/data/website/abwaegomat/de/Screenshot%202025-08-24%20at%2012-18-42%20Abw%C3%A4g-o-mat.png" class="grid-w50" alt="Gewichtungen eintragen" />
  <img src="https://media.eike.in/data/website/abwaegomat/de/Screenshot%202025-08-24%20at%2012-18-52%20Abw%C3%A4g-o-mat.png" class="grid-w50" alt="Die Auswertung" />
  <img src="https://media.eike.in/data/website/abwaegomat/de/Screenshot%202025-08-24%20at%2012-19-01%20Abw%C3%A4g-o-mat.png" class="grid-w50" alt="Dialog zum speichern einer Argumentation" />
  <img src="https://media.eike.in/data/website/abwaegomat/de/Screenshot%202025-08-24%20at%2012-26-05%20Abw%C3%A4g-o-mat.png" class="grid-w50" alt="Dialog zum teilen einer Argumentation" />

{{< /gallery >}}


## Links

### Jetzt probieren!
{{< button href="https://abwaeg-o-mat.eike.in/" target="_blank" >}}
abwaeg-o-mat.eike.in
{{< /button >}}

### GitHub
{{< github repo="LarvenStein/abwaeg-o-mat" >}}
