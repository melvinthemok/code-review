# Code Review for Adrian Ke

## Project Repo

https://github.com/adrianke77/project-2-starter

## Review

#### Project Purpose

The purpose of this project is to build an item trading platform for the consumer market.

The project's components are as follows:

* Controllers for (1) authentication; (2) search; (3) the interface; (4) items; and (5) trades
* Models for (1) users; (2) items; (3) trades; and (4) changes tracked using AJAX polling
* Views for (1) authentication; (2) users; (3) items; (4) trades; (5) partials and layout; and (6) search
* Middleware used to check if the user is logged in
* A Passport configuration file
* CSS files and images in a public folder
* An environment variables file
* Miscellaneous package.json, .gitignore, README.md files, etc

#### Project Organization

The app is written in JavaScript, with .ejs files rendered instead of HTML files. The code is organized into controllers, models and views, and is generally well-formatted and indented properly.

#### Features

* The user can either sign up for a new account or sign in
  * This is implemented using forms in the authentication views named login.ejs and signup.ejs, the authentication controller named auth.js, and the user model named user.js
  * The user schema is set up with a name, an email, a password, and references to the items and trades models


* The user can access a 'BarterCenter' to search for items
  * This is implemented using forms in the navigation bar in layout.ejs and the user view named userHome.ejs, the search controller named search.js, and the item and trade models
  * The item schema is set up with a name, description, image link, image public ID, valuation, trade status, and reference to the trade model
  * The trade schema is set up with a deal sweetener, agreement status of the 2 relevant users, their discussion, and their respective references to the user and item models


* In the 'BarterCenter', the user can also view his/her items placed on offer and item details, and list new items
  * This is implemented using the user and item views named userHome.ejs, viewTrade.ejs and createForm.ejs, the interface and item controllers, and the user and item models


* The user can also view, make changes to, and delete his/her ongoing trades in the 'BarterCenter' and the trade view
  * This is implemented using the user and trade views named userHome.ejs and viewTrade.ejs, the iterface, item, and trade controllers, and the user, item, and trade models


* The user can view details of past trades and traded items in the 'BarterCenter'
  * This is implemented using the userHome.ejs and viewTrade.ejs views, the interface, item, and trade controllers, and the item and trade models


* In the trade view for ongoing trades, the user can post and view messages posted on a discussion board
  * These messages are stored in a discussion string in the trade model


* Adrian also set up AJAX polling to check for changes in trades affecting the user, as a result of actions of other users
  * If such changes exist, as tracked in a distinct model, the user's browser window is refreshed to display them

#### Areas of Success (Code, Organization)

* Adrian wrote his own autoPopulate function in his trade model (lines 17 to 28), which was called automatically via pre hooks in the event of 'findOne' and 'find' queries being made
  * This was a neat feature which went some way towards making his code more DRY


* The app has many comprehensive features and actions for trades and items
  * Changes affecting each model are updated via referencing
  * The UX feels quite natural with unnecessary routing to new pages kept to a minimal


* The AJAX polling set up was a very nice feature for the user's browser to be automatically refreshed only when necessary, i.e. changes are made by other users affecting this user
  * Rather than reloading the page frequently with requests made to the server to capture the most current state, refreshes are done only when necessary


* Adrian also set up an image uploading feature using Cloudinary
  * This probably feels more intuitive from a UX angle compared to filling in an image URL

#### Areas for Improvement (Code, Organization)

* Redundant features could be deleted
  * HTML and CSS files in the 'referencelayouts' folder are not used


* EJS manipulation could be reduced
  * The functions in the controller could be written more comprehensively to send more specific data to the views


* This may be quite a subjective design decision, but routes could have been separated from functions in the controllers for good order
  * This accords with conventions e.g. Ruby on Rails

## Additional Notes

Awesome project with a lot of functionality built within a short timeframe
