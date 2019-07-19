1. Installation
Create an environment
Create a project folder and a venv folder within:

mkdir myproject
cd myproject
python3 -m venv venv
On Windows:

py -3 -m venv venv
If you needed to install virtualenv because you are on an older version of Python, use the following command instead:

virtualenv venv
On Windows:

\Python27\Scripts\virtualenv.exe venv
Activate the environment
Before you work on your project, activate the corresponding environment:

. venv/bin/activate
On Windows:

venv\Scripts\activate
Your shell prompt will change to show the name of the activated environment.

Install Flask
Within the activated environment, use the following command to install Flask:

pip install Flask
Flask is now installed. Check out the Quickstart or go to the Documentation Overview.

Living on the edge
If you want to work with the latest Flask code before it’s released, install or update the code from the master branch:

pip install -U https://github.com/pallets/flask/archive/master.tar.gz
Install virtualenv
If you are using Python 2, the venv module is not available. Instead, install virtualenv.

On Linux, virtualenv is provided by your package manager:

# Debian, Ubuntu
sudo apt-get install python-virtualenv

# CentOS, Fedora
sudo yum install python-virtualenv

# Arch
sudo pacman -S python-virtualenv
If you are on Mac OS X or Windows, download get-pip.py, then:

sudo python2 Downloads/get-pip.py
sudo python2 -m pip install virtualenv
On Windows, as an administrator:

\Python27\python.exe Downloads\get-pip.py
\Python27\python.exe -m pip install virtualenv
Now you can return above and Create an environment.


2 Project layout 

/home/user/Projects/flask-tutorial
├── flaskr/
│   ├── __init__.py
│   ├── db.py
│   ├── schema.sql
│   ├── auth.py
│   ├── blog.py
│   ├── templates/
│   │   ├── base.html
│   │   ├── auth/
│   │   │   ├── login.html
│   │   │   └── register.html
│   │   └── blog/
│   │       ├── create.html
│   │       ├── index.html
│   │       └── update.html
│   └── static/
│       └── style.css
├── tests/
│   ├── conftest.py
│   ├── data.sql
│   ├── test_factory.py
│   ├── test_db.py
│   ├── test_auth.py
│   └── test_blog.py
├── venv/
├── setup.py
└── MANIFEST.in


3. Files ignored 

venv/

*.pyc
__pycache__/

instance/

.pytest_cache/
.coverage
htmlcov/

dist/
build/
*.egg-info/


3. Templates 

Templates are files that contain static data as well as placeholders for dynamic data. A template is rendered with specific data to produce a final document. Flask uses the Jinja template library to render templates.

In your application, you will use templates to render HTML which will display in the user’s browser. In Flask, Jinja is configured to autoescape any data that is rendered in HTML templates. This means that it’s safe to render user input; any characters they’ve entered that could mess with the HTML, such as < and > will be escaped with safe values that look the same in the browser but don’t cause unwanted effects.

Jinja looks and behaves mostly like Python. Special delimiters are used to distinguish Jinja syntax from the static data in the template. Anything between {{ and }} is an expression that will be output to the final document. {% and %} denotes a control flow statement like if and for. Unlike Python, blocks are denoted by start and end tags rather than indentation since static text within a block could change indentation.

quick notes: {{ }}


<!doctype html>
<title>{% block title %}{% endblock %} - Flaskr</title>
<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
<nav>
  <h1>Flaskr</h1>
  <ul>
    {% if g.user %}
      <li><span>{{ g.user['username'] }}</span>
      <li><a href="{{ url_for('auth.logout') }}">Log Out</a>
    {% else %}
      <li><a href="{{ url_for('auth.register') }}">Register</a>
      <li><a href="{{ url_for('auth.login') }}">Log In</a>
    {% endif %}
  </ul>
</nav>
<section class="content">
  <header>
    {% block header %}{% endblock %}
  </header>
  {% for message in get_flashed_messages() %}
    <div class="flash">{{ message }}</div>
  {% endfor %}
  {% block content %}{% endblock %}
</section>


Note: The one thing that  I like flask is that this api modulizes the layout 


The {% extends %} tag is the key here. It tells the template engine that this template “extends” another template. When the template system evaluates this template, first it locates the parent. The extends tag must be the first tag in the template. To render the contents of a block defined in the parent template, use {{ super() }}.


Common errors: 

...the issue is that Flask raises an HTTP error when it fails to find a key in the args and form dictionaries. What Flask assumes by default is that if you are asking for a particular key and it's not there then something got left out of the request and the entire request is invalid.


