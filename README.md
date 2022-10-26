# Swiss Bracket Manager
[Webtool](https://shinyfinder.github.io/swiss-bracket-manager/) for aiding in the management of Swiss tournaments on Smogon.

# Installation

Obtain a copy of the source code by downloading the [zip](./archive/refs/heads/main.zip) of the repository or, if you have git installed, via the command line in your desired destination folder:

`git clone https://github.com/shinyfinder/swiss-bracket-manager.git`

If you download the zip, extract the file into your desired directory.


# About

This webtool contains two parts: a manager, and a validator. The [manager](./index.html) features:


- A fully integrated management system for a Swiss-style tournament.​
    - Each bracket (2:0, 1:1, 0:1, etc etc) is managed within the client so that there is no need to make separate brackets for each W/L ratio.​
- Persistent storage​
    - As you make edits to the page (choose winners, advance the round), changes are saved on your computer via local storage. Local storage is kinda like a cookie, but it's never sent to the server, so no one else can see it. That means you can refresh or close your browser and reload the tournament later and have the info saved​
- Support for multiple ongoing tournaments at once​
    - Each bracket is saved individually under the name you provide, which means you can manage multiple tournaments at once! You can reload an old bracket any time you'd like. I...have no idea what the limit is on how many you can hold, but it's probably a lot. Like 200 by my calculations? Yeah, that's fine.​
- Supports match extensions​
    - Extensions are limited to 1 round. They are inherently incompatible with Swiss-style brackets, but I tried to support it anyway. There is a small chance that extensions will cause users to face the same opponent they have in the past (more apparent in very small brackets or tournaments that have been going on for many rounds), but there's really no great way around that. The best solution is don't use them.​
- Load/delete brackets on the fly​
    - Deleting a bracket requires you to confirm the deletion in a popup. As always, this can't be undone.​
- Ability to set the number of rounds.​
    - The theoretical max number of rounds for a Swiss tournament is half the number of participants. So for a tournament with 64 participants, you could do 32 rounds...But don't.​
    As the number of rounds approaches this halfway point, there's an increased chance that you won't be able to find a viable grouping of players (i.e. you're stuck with repeat matchups). At this point to tool warns you and spits out the current records and pairs, because it it strict with this requirement of no repeats. So only go a few rounds with a decent sized pool, and you'll probably be fine.​
- Supports byes​
    - Leftover players in an odd group are given byes for that round. Players cannot receive a bye twice. See commentary on extensions and rounds above.​
- Smogon-friendly output​
    - The results for the previous round and the pairings for the current round are printed out for each round. Winners are highlighted bold (in bbcode) and each username is preceded with an @​
- Bracket-maker friendly input​
    - Supports importing the output from the bracket maker to parse the user list. Note that pairings will be remade.​
- Tracks winners as you go​
    - Each matchup results in a form where you can check the winner of the matchup. These boxes are saved across sessions.​
- Dark mode!​
    - Dark mode can be toggled and your choice is saved across browser sessions. Which means you only have to burn your eyes once.​
    - I didn't spend a lot of time on css...​
- Mobile and offline friendly​
    - Idk why you'd want to do that, but it is.​
    - Stuff is saved on your computer, not a server. Which means there's no cross-browser/cross-device syncing. That's not gonna happen.​
- Users are randomized via a Fisher-Yates shuffle algorithm​
- Open source​
- Written in pure HTML/JavaScript​
- Experimental: quits and subs​
    - These features allow you to specify that a user has been subbed or left the tournament.​
    - There are still experimental in nature, so use at your own risk.​

The [validator](./validate.html) is used in conjunction with the [Smogon bracket maker](https://www.smogon.com/bracketmaker/). It keeps a record of previous matchups to validate there have been no duplicates. It also groups users into different brackets based on a record of their wins and losses. The validator features many of the same qualities as the manager, including:

- Persistent storage via local storage.
- Support for multiple on-going tournaments at once
- Load/delete tournaments on the fly
- Loads matchups directly from the bracket maker output (does not support providing a URL. You must copy/paste the output into the appropriate field)
- Minimal additional work to check for duplicated matchups by integrating into the tournament management workflow.
- Automatically keeps track of matchups, wins, and losses and groups users into brackets that can be re-entered into the bracket maker.
- Dark mode
- Mobile and offline friendly
- Open source
- Written in pure HTML/JavaScript

# Usage
## Manager

1. Create a new bracket
    - Specify a name and number of rounds for your tournament
    - Click the Create New Bracket button
1. Alternatively, select an old bracket from the dropdown and click the load button.
2. In the text field at appears, enter the names of the participants.
    - Each entrant should go on their own line.
    - OR, to save some time, you could make a new bracket in the current bracket maker and enter the thread URL to quickly get the list of users. Copy the matchups from the bracket maker, and paste them into the username field on this manager. Click the appropriate box to indicate it should parse the output. Pairs will be remade. (Side note: I can't do this provide-a-url functionality since it is on a different domain).
3. Click Make Bracket.
4. Choose a winner in each matchup at the bottom of the page. Or, don't choose any winners in a matchup to grant an extension for 1 round.
5. Click the Advance button
6. Repeat steps 6-7 until there are no rounds remaining
7. The results of the previous round, the current round, and final round will be printed in the section above.
8. When you're ready to make a new bracket, start back at step 1.

## Validator

1. Create a new bracket
    - Specify a name for your tournament
    - Click the Create New Bracket button
1. Alternatively, select an old bracket from the dropdown and click the load button.
2. Paste the output from the bracket maker into the appropriate field.
3. Click Check for duplicates.
4. Enter the names of the winners of each round in the appropriate field
    - Each name must be entered on a new line
5. Make sure you have entered the matchups exactly as they occurred. Make sure the matchups field contains any extension games, and the winners field includes any extension winners.
6. Click Store matches and update
7. Repeat for how many rounds and brackets you have.


# License
This software is distributed under the [MIT license](./blob/main/LICENSE).