+++
title = 'Multiplayer Hangman'
summary = 'Eine API , welche es ermöglicht, als Team Galgenmännchen zu spielen'
date = 2025-05-18
showDate = false
showAuthor = false
featureimage = 'https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-18-35%20The%20hangman%20game.png'
showHero = true
showTableOfContents = true
tags = ['web', 'api', 'c#', 'javascript']
showReadingTime = false
showWordCount = false
+++

## Kurzbeschreibung
Dieses Projekt entstand im Rahmen eines Praktikums, bei welchem ich mich mit dem erstellen von REST-APIs in `C#` beschäftigt habe.

Multiplayer Hangman bietet eine REST-API, welche es ermöglicht, als Team Galgenmännchen zu spielen. Die Wörter kommen aus vorgegebenen Listen.
Für dieses Projekt habe ich außerdem ein kleines Frontend gebastelt, damit man das Spiel auch spielen kann :)

### Features
* Erstellen und Beitreten von Räumen
* Anpassen von Spielparametern
    * Anzahl der Runden
    * Maximale Spielerzahl
    * Ändern der Wortliste
* Verschiedene Wortlisten
* Gemeinsames Raten an einem Wort
* Auswertungen nach jeder Runde und jedem Spiel
* Echtzeitkommunikation für relevante Funktionen durch `Websockets` (SignalR)

## Technologien
Das Backend des Spiels habe ich in `C#` mit `dotNet` umgesetzt, da diese Technonolgien vom Praktikumsbetrieb vorgegeben wurden. Als Datenbank habe ich `Maria DB` verwendet.

Für das Frontend habe ich das `Svelte` Framework verwendet, da ich mit diesem bereits Erfahrungen gemacht habe und es die Entwicklung in meinem Fall vereinfacht.

## Screenshots
{{< gallery >}}
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-24-32%20The%20hangman%20game.png" class="grid-w50" alt="Startseite des Spiels" />
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-25-30%20The%20hangman%20game.png" class="grid-w50" alt="Admin-ansicht eines Raumes" />
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-26-07%20The%20hangman%20game.png" class="grid-w50" alt="Die eigentliche Spielansicht" />
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-28-21%20The%20hangman%20game.png" class="grid-w50" alt="Ansicht, wenn ein Spiel gewonnen wurde" />
{{< /gallery >}}


## Links

### Jetzt Spielen!
{{< button href="https://hangman.eike.in/" target="_blank" >}}
hangman.eike.in
{{< /button >}}

### Backend GitHub
{{< github repo="LarvenStein/multiplayer-hangman-api" >}}

### Frontend GitHub
{{< github repo="LarvenStein/multiplayer-hangman-frontend" >}}