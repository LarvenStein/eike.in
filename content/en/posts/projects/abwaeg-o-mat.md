+++
title = 'Weigh-o-matic (Abwäg-o-mat)'
summary = 'Your o-matic to easily weigh pro and con situations!'
date = 2025-08-21
showDate = false
showAuthor = false
featureimage = 'https://media.eike.in/data/website/abwaegomat/Screenshot%202025-08-21%20at%2021-45-35%20Abw%C3%A4g-o-mat.png'
showHero = true
showTableOfContents = true
tags = ['web', 'api', 'javascript']
showReadingTime = false
showWordCount = false
+++
## Description

To become more familiar with my tech stack during my internship, I rewrote an old [project](https://github.com/LarvenStein/abwaeg-o-mat/tree/legacy) of mine using `TypeScript` and `Express.js`.

This project allows users to structure and record pros and cons decisions, then obtain insights from the results. Additionally, it lets you save an argumentation, encrypt it with a password for database storage, and associate it with an expiration date.

### Features

* Structured creation of arguments in steps:
    1. Entering a thesis
    2. Entering pro- and con-arguments
    3. Assigning weights to the arguments `(1x/2x/3x/4x/5x)`
* Detailed organization and evaluation of arguments, revealing a winner side
* Continuous display of all arguments along with their weights
* Point distribution breakdown
* Display of the outcome from an argumentation analysis
* Saving of the result of the argumentation evaluation
* Possibility to encrypt the argumentation in the database using a password and `AES256`
* Setting an expiration date for access; upon reaching this date, the argumentation is deleted from the database.
* Automatic deletion via `cron` possible if required.
* Sharing arguments by sharing links
* Support for multiple languages (currently German, English, Dutch)

## Technology

The backend was written in `TypeScript` and `Express.js`. The database uses `SQLite` with `Sequelize`.

The frontend is server-side rendered using `Pug` as the template engine.

## Screenshots

{{< gallery >}}
<img src="https://media.eike.in/data/website/abwaegomat/en/Screenshot%202025-08-24%20at%2019-23-47%20Weigh-o-matic.png" class="grid-w50" alt="Home page of the app" />
<img src="https://media.eike.in/data/website/abwaegomat/en/Screenshot%202025-08-24%20at%2019-24-22%20Weigh-o-matic.png" class="grid-w50" alt="Entry of arguments" />
<img src="https://media.eike.in/data/website/abwaegomat/en/Screenshot%202025-08-24%20at%2019-24-32%20Weigh-o-matic.png" class="grid-w50" alt="Entry of weights for arguments" />
<img src="https://media.eike.in/data/website/abwaegomat/en/Screenshot%202025-08-24%20at%2019-24-39%20Weigh-o-matic.png" class="grid-w50" alt="Argumentation evaluation summary" />
<img src="https://media.eike.in/data/website/abwaegomat/en/Screenshot%202025-08-24%20at%2019-24-47%20Weigh-o-matic.png" class="grid-w50" alt="Save argumentation dialog" />
<img src="https://media.eike.in/data/website/abwaegomat/en/Screenshot%202025-08-24%20at%2019-24-55%20Weigh-o-matic.png" class="grid-w50" alt="Share argumentation dialog" />
{{< /gallery >}}

## Links

### Try it out!
{{< button href="https://abwaeg-o-mat.eike.in/" target="_blank" >}}
abwaeg-o-mat.eike.in
{{< /button >}}

### GitHub Repository
{{< github repo="LarvenStein/abwaeg-o-mat" >}}