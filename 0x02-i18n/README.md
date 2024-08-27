i18n
This project contains tasks for learning to create internationalized web pages with Flask.

Tasks To Complete
 0. Basic Flask app
0-app.py contains a Python script that sets up a basic Flask app with the following requirements:

Create a single / route and an index.html template that simply outputs “Welcome to Holberton” as page title (<title>) and “Hello world” as header (<h1>).
 1. Basic Babel setup

Copy 0-app.py into 1-app.py and templates/0-index.html into templates/1-index.html.
Install the Babel Flask extension:
pip3 install flask_babel
Instantiate the Babel object in your app. Store it in a module-level variable named babel.
In order to configure available languages in our app, you will create a Config class that has a LANGUAGES class attribute equal to ["en", "fr"].
Use Config to set Babel’s default locale ("en") and timezone ("UTC").
Use that class as config for your Flask app.
 2. Get locale from request

Copy 1-app.py into 2-app.py and templates/1-index.html into templates/2-index.html.
Create a get_locale function with the babel.localeselector decorator. Use request.accept_languages to determine the best match with our supported languages.
 3. Parametrize templates

Copy 2-app.py into 3-app.py and templates/2-index.html into templates/3-index.html.
Use the _ or gettext function to parametrize your templates. Use the message IDs home_title and home_header.
Create a babel.cfg file containing:
[python: **.py]
[jinja2: **/templates/**.html]
extensions=jinja2.ext.autoescape,jinja2.ext.with_
Initialize your translations with:
~/.local/bin/pybabel extract -F babel.cfg -o messages.pot .
Initialize your two dictionaries with:
~/.local/bin/pybabel init -i messages.pot -d translations -l en
~/.local/bin/pybabel init -i messages.pot -d translations -l fr
Edit files translations/[en|fr]/LC_MESSAGES/messages.po to provide the correct value for each message ID for each language. Use the following translations:
msgid	English	French
home_title	"Welcome to Holberton"	"Bienvenue chez Holberton"
home_header	"Hello world!"	"Bonjour monde!"
Compile your dictionaries with:
~/.local/bin/pybabel compile -d translations
Reload the home page of your app and make sure that the correct messages show up.
