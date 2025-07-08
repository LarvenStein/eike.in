+++
title = 'Multiplayer Hangman'
summary = 'An API that enables playing hangman as a team'
date = 2025-05-18
draft = false
showDate = false
showAuthor = false
featureimage = 'https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-18-35%20The%20hangman%20game.png'
showHero = true
showTableOfContents = true
tags = ['web', 'api', 'c#', 'javascript']
showReadingTime = false
showWordCount = false

+++

## Short Description
This project was created during an internship in which I focused on building REST APIs using C#.

Multiplayer Hangman provides a REST API that allows players to play hangman collaboratively as a team. The words come from predefined lists.  
I also built a small frontend so that the game can actually be played :)

### Features
* Create and join rooms
* Customize game parameters
    * Number of rounds
    * Maximum number of players
    * Select a different word list
* Multiple word lists
* Team-based guessing of a single word
* Statistics after each round and each game
* Real-time communication for essential functions using **Websockets** (SignalR)

## Technologies
The backend was built in **C#** using **dotNet**, as these technologies were required by the internship company.  
For the database, I used **MariaDB**.

The frontend was developed using the **Svelte** framework, which I had prior experience with and which made development easier in this case.

## Screenshots
{{< gallery >}}
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-24-32%20The%20hangman%20game.png" class="grid-w50" alt="Home page of the game" />
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-25-30%20The%20hangman%20game.png" class="grid-w50" alt="Admin view of a room" />
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-26-07%20The%20hangman%20game.png" class="grid-w50" alt="Main game view" />
  <img src="https://media.eike.in/data/website/hangman/Screenshot%202025-05-18%20at%2021-28-21%20The%20hangman%20game.png" class="grid-w50" alt="View when a game is won" />
{{< /gallery >}}

## Links

### Play Now!
{{< button href="https://hangman.eike.in/" target="_blank" >}}
hangman.eike.in
{{< /button >}}

### Backend GitHub
{{< github repo="LarvenStein/multiplayer-hangman-api" >}}

### Frontend GitHub
{{< github repo="LarvenStein/multiplayer-hangman-frontend" >}}
