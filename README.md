# The Flask Framework 
 
Flask is a small framework.

pip3 install Flask

### Creating Flask App 

import os
from flask import Flask


app = Flask(__name__)


@app.route("/")
def index():
    return "Hello, World"


if __name__ == "__main__":
    app.run(
        host=os.environ.get("IP", "0.0.0.0"),
        port=int(os.environ.get("PORT", "5000")),
        debug=True)

### Returning HTML code from a Flask function

import render_template
return render_template("index.html")

templates file - index.html

### Routing 

Allows us to switch between views using URLs

@app.route("/about")
def about():
    return render_template("about.html")


@app.route("/contact")
def about():
    return render_template("contact.html")

2 lines between routes - pep8 compliant

templates file - about.html, contact.html

navigation links to work - use jinga templating method of url_for in order to call the appropriate functions.

<li><a href = "{{ url_for('index') }}">Home</a></li>
<li><a href = "{{ url_for('about') }}">About</a></li>
<li><a href = "{{ url_for('contact') }}">Contact</a></li>

### Template Inheritance 

Allows us to inherit code from other templates reducing duplicate code 

templates file - base.html 

{% block content %}
gets inserted here
{% endblock %}

in index.html file - 

{% extends "base.html" %}
{% block content %}
    <h1>Home Page</h1>
{% endblock %}

### Using bootstrap theme 

Start bootstrap - copy link address

Command - mkdir static, cd static, wget(linkaddress), ls, unzip, cd - move all folders into static and delete the zip file.

Inside head element link to css - 
 <link rel="stylesheet" href="{{ url_for('static', filename='css/clean-blog.min.css') }}">

Go to github repo for the bootstrap theme and copy and paste the head bootstrap css vendor file link into base template. 

Copy and paste body element including scripts and update script links/image links with urls

Change nav links to url_for





