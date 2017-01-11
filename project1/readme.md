# Code Review for Olivia Chung

## Project Repo

https://github.com/olico852/wdi7project1

## Review

#### Project Purpose

The purpose of this project is to build a two-player implementation of the classic arcade game, Pong.

The project's components are as follows:

* A HTML document
* A CSS stylesheet
* A third-party JavaScript animation polyfill
* A JavaScript file
* A Markdown readme
* A background JPG image
* A directory of sprite sheets
* A directory of previous versions of the main JavaScript file

#### Project Organization

Apart from the third-party polyfill, all the JavaScript code is written in a single file named "main.js". The code is generally well-formatted and indented properly.

The HTML document contains all necessary tags. The CSS stylesheet and viewport meta tag are linked in the head. The jQuery CDN and both the polyfill and main JavaScript files are linked near the end of the body.

#### Features

* Each player moves a paddle along the edge of a game board, either using the 'W' and 'S' keys or the 'Up' and 'Down' keys.
  * This is implemented using the whatKey function at main.js lines 47 to 85.


* The players take turns returning a ball launched from the net in the middle of the board to a randomly-selected player at a random speed, using the 'Space' bar.
  * The ball is a <div> element created using the SpriteCreate function at main.js lines 100 to 120, has its x and y coordinates updated, and is removed upon leaving the vertical edges of the game board using the destroySprite function at main.js lines 123 to 129.


* The ball bounces along the horizontal edges of the game board and off the paddles, and each round continues until a player fails to return the ball, in the event of which the opponent's score increases by 1.
  * This is implemented using the animateSprites function in main.js lines 173 to 223.


* The game starts at level 1 and continues for repeated rounds until one of the players achieves a score of 5, whereupon they progress to level 2 and the background image changes.
  * This is implemented using the isGameOver function at main.js lines 232 to 251.


* At the end of level 2, a message is displayed to identify the winner and the game can be restarted.
  * This is implemented in the newlevel and reset functions at main.js lines 253 to 297.

#### Areas of Success (Code, Organization)

* Naming of variables, functions, selectors and ID tags.
  * Clear and semantic.


* Comments inserted before and within each function.
  * Helpfully describing what each function does.


* Varying speed of ball launched.
  * This feature (see SpriteCreate function at main.js lines 114 and 115) makes gameplay more interesting by adding an element of randomness to each round.


* Many potential extensions possible.
  * Some incomplete code on extended features were included in comments at the end of main.js, which providing a preview of some interesting potential extensions in future.

#### Areas for Improvement (Code, Organization)

* Both vanilla JavaScript and jQuery are used for DOM manipulation.
  * One or the other could be used for consistency.


* Suggest ensuring DOM is loaded before JavaScript and jQuery code is run, e.g. with:
  * $(document).ready(function() {
    // code here
  });


* Functions and variables are defined in the global namespace.
  * They could be defined within objects and thus limited in scope.


* 2 separate randomizing functions (randomizer and randomDir at main.js lines 160 to 171) defined.
  * This code could be consolidated in a single function given their relative brevity.


* Repeated code e.g. in the whatKey function (main.js lines 47 to 85) and the animateSprites function (main.js lines 181 to 218).
  * The code to adjust the paddle distance variables in different keydown and keyup events could be abstracted into a function and called repeatedly, with the different paddle ID tags and paddle distance variables taken as arguments.


* Some code intended for extended features is redundant in the present implementation, e.g. the toggle function at main.js lines 89 to 97 to prevent players from launching more balls.
  * Such code could be labelled as work-in-progress extension code and commented out pending further development.

## Additional Notes

Awesome job! Pong is a lot of fun.
