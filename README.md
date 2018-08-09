# Advanced JavaScript Assignment: Constructor Word Guess

A Word Guess command-line game using constructor functions

![Word Guess Cli](Images/01-WordGuess-Cli.gif)

### Playing the game

To start the game, run the following command from the project root directory (constructor-hangman):</p>
<pre>node index.js</pre>
<p>When you run this command, you will see the following screen:</p>
<pre>
$ node index.js
  _   _                                            ____
 | | | | __ _ _ __   __ _ _ __ ___   __ _ _ __    / ___| __ _ _ __ ___   ___
 | |_| |/ _` | '_ \ / _` | '_ ` _ \ / _` | '_ \  | |  _ / _` | '_ ` _ \ / _ \
 |  _  | (_| | | | | (_| | | | | | | (_| | | | | | |_| | (_| | | | | | |  __/
 |_| |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|  \____|\__,_|_| |_| |_|\___|
                    |___/
Welcome to the Hangman Game!
Theme is... Minnesota cities.
==========================================================================================================
How to play
==========================================================================================================
When prompted to enter a letter, press any letter (a-z) on the keyboard to guess a letter.
Keep guessing letters. When you guess a letter, your choice is either correct or incorrect.
If incorrect, the letter you guessed does not appear in the word.
For every incorrect guess, the number of guesses remaining decrease by 1.
If correct, the letter you guessed appears in the word.
If you correctly guess all the letters in the word before the number of guesses remaining reaches 0, you win.
If you run out of guesses before the entire word is revealed, you lose. Game over.
===========================================================================================================
You can exit the game at any time by pressing Ctrl + C on your keyboard.
===========================================================================================================

</pre>
<p>At the prompt, enter your name and press <b>Enter</b>.</p>
<pre>? What is your name?</pre>
<p>When prompted, enter <b>Y</b> to begin playing.</p>
<pre>Are you ready to play? (Y/n)</pre>

## <a name="play-game"></a> Playing the game
<p>When the game starts, you will be given a word and the number of letters in that word.</p>
<p>When prompted, try to guess a letter that is in the word.</p>
<pre>Great! Welcome, Phil. Let's begin...
Your word contains 7 letters.
WORD TO GUESS:


</pre>
<p>You start the game with 10 guesses. If your guess is incorrect, the number of guesses remaining decreases by 1.</p>
<pre>
You guessed: Z
┌─────────────────────────────────┐
│                                 │
│   Letters already guessed:  Z   │
│                                 │
└─────────────────────────────────┘
WORD TO GUESS:
 A  A
INCORRECT!
You have 9 guesses left.
=====================================================================
</pre>
<p>If your guess is correct, the letter is added to the word.</p>
<pre>
=====================================================================
? Guess a letter: a
You guessed: A
┌───────────────────────────────────┐
│                                   │
│   Letters already guessed:  Z A   │
│                                   │
└───────────────────────────────────┘
WORD TO GUESS:
 A   A
CORRECT!
=====================================================================
</pre>
<p>If you guess all the letters in the word before the number of guesses reaches 0, you win.</p>
<pre>
WORD TO GUESS:
M A N K A T O
CORRECT!
=====================================================================
=====================================================================
YOU WON! YOU'RE A TRUE MINNESOTAN!
Wins: 1
Losses: 0
=====================================================================
</pre>

## <a name="technologies-used"></a> Technologies used to build app

  * Node.js (https://nodejs.org/en/)
  * Javascript constructor functions
- - -

### Notes

## Project Scope

The completed game should meet the following criteria:

1. The completed game should be able to receive user input using the `inquirer` or `prompt` npm packages.

2. Your solution should have, at minimum, three files:

* **letter.js**: Contains a constructor, Letter. This constructor should be able to either display an underlying character or a blank placeholder (such as an underscore), depending on whether or not the user has guessed the letter. That means the constructor should define:

  * A string value to store the underlying character for the letter

  * A boolean value that stores whether that letter has been guessed yet

  * A function that returns the underlying character if the letter has been guessed, or a placeholder (like an underscore) if the letter has not been guessed

  * A function that takes a character as an argument and checks it against the underlying character, updating the stored boolean value to true if it was guessed correctly

* **word.js**: Contains a constructor, Word that depends on the Letter constructor. This is used to create an object representing the current word the user is attempting to guess. That means the constructor should define:

  * An array of `new` Letter objects representing the letters of the underlying word

  * A function that returns a string representing the word. This should call the function on each letter object (the first function defined in `Letter.js`) that displays the character or an underscore and concatenate those together.

  * A function that takes a character as an argument and calls the guess function on each letter object (the second function defined in `Letter.js`)

* **index.js**: The file containing the logic for the course of the game, which depends on `Word.js` and:

  * Randomly selects a word and uses the `Word` constructor to store it

  * Prompts the user for each guess and keeps track of the user's remaining guesses

### Setup

Your project folder setup should be very simple and look something like this:

```
ConstructorWordGuess
│   README.md
│   images    
│   index.js
│   letter.js
│   Word.js
│   LICENSE

```
Once you have created the above files, navigate the project root and install the following dependencies:

```npm init``` & ```npm i```

* Running ```npm init``` will create your default ```package.json``` file and ```npm i``` is the [npm global install](https://docs.npmjs.com/cli/install). This global npm command that installs a package, and any packages that it depends on. Used in this app to install the remainder npm packages.

```npm i inquirer ```  

* [inquirer npm package] (https://www.npmjs.com/package/inquirer). A collection of common interactive command line user interfaces. Used in this app to prompt users for a letter throughout the game.

```npm i cli-color```

* [cli-color npm package](https://www.npmjs.com/package/cli-color) - Colors, formatting and other goodies for the console. Used in this app to add color to the game.

```npm i figlet```

* [figlet npm package] (https://www.npmjs.com/package/figlet). This project aims to fully implement the FIGfont spec in JavaScript. It works in the browser and with Node.js. Used in this app to convert text into ASCII art - drawings made out of text characters.

```npm i is-letter```

* [is-letter npm package](https://www.npmjs.com/package/is-letter) - Used for form valiation. This package is used to check if the value the user enters is a letter (for example, "a") or not a letter (for example, "aba").

```npm i boxen ```

* [boxen npm package] (https://www.npmjs.com/package/boxen) - Used in this app to create boxes in terminal.

Once installed, review your package.json file (automatically installed when you ran ```npm install`` for version information. 

1. `Letter.js` *should not* `require` any other files.

2. `Word.js` *should only* require `Letter.js`

3. **HINT:** Write `Letter.js` first and test it on its own before moving on, then do the same thing with `Word.js`

4. **HINT:** If you name your letter's display function `toString`, JavaScript will call that function automatically whenever casting that object to a string (check out this example: https://jsbin.com/facawetume/edit?js,console)

* Since this assignment is a command-line application, you don't need to deploy it anywhere. You will, however, be required to upload it to Github.

* Remember to include a `package.json` file containing your project dependencies in your Github repo!

### Minimum Requirements

Attempt to complete homework assignment as described in instructions. If unable to complete certain portions, please pseudocode these portions to describe what remains to be completed. Adding a README.md as well as adding this homework to your portfolio are required as well and more information can be found below.

- - -

### Create a README.md

Add a `README.md` to your repository describing the project. Here are some resources for creating your `README.md`. Here are some resources to help you along the way:

* [About READMEs](https://help.github.com/articles/about-readmes/)

* [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)

- - -
