# PYSTACK
Project with python language and django framework ⊹˚. ♡.𖥔 ݁ ˖
(Initial Settings)

# Create a virtual environment in Python, separating the interpreter, so there is no confusion of versions with other projects:
  # Linux
  python3 -m venv venv (second venv is random name)
  # Windows
  python -m venv venv (second venv is random name)

# Now you are going to active the virtual environment, like this:
  # Linux
  source venv/bin/activate
  # Windows
  venv\Scripts\Activate
  # If there is an error, and you are using windows, the Poweshell needs to accept permissions for execute scripts, so use this and try again:
  Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

# Let's install Django and the other libraries:
  # pip install django
  # pip install pillow 
  pip is Python's package manager, and through pip, you install the libraries
  The Pillow library is a Python image processing library that offers a number of functionalities for processing

# Inicialize a django project:
  django-admin startproject pystack . (pystack is the name given to the new Django project and the dot at the end specifies the directory in which the project should be 
  created. In this case, it is the current directory)

#  Start the server for test
  # python manage.py runserver
  You will see something like this: Starting development server at http://127.0.0.1:8000/
  Do CTRL+click on https

࣪𖤐 Observation: I advise you to research what Django's communication layer is like, you can start with MVT (Model, Views and Templates)

# Now, stop the server with CTRL+C on top of HTTP and then CTRL+L to clear the server terminal
  # Create the user app:
  Python manage.py StartApp Users (You can change the name Users)
  When you create a new folder (a new app) you will need to go to the application's Core (pystack) and go to the settings so that Django recognizes this folder as one of      its apps. From there, you'll need to insert this new users folder into the constant INSTALLED_APPS=[ ]
  INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'users', 👈🏻
]

# The second step is to configure the application routes (for login, registration, homepage...)
  # Go to Core -> urls.py (This is where we put the urls of our application)
  # Create a URL for users:
  path('users/', include('users.urls')), (This include('users.urls') exists because within the users route, there may be other routes such as registration or login, so        you INCLUDE it so that it can also search for these routes when it is inside the users route, Find within the Users app and within the URL file)
  # Go to users -> create a file urls.py (This is where we register the URLs and the url users find the others urls)
  In the APP users create a URL for registration:
  from django.urls import path
  from . Import Views
  urlpatterns = [ (Inside urlpatterners Django will look for other URLs within users)
  path('registration/', views.registration, name='registration'), (This views.registration is the function we'll call to process the registration page, so we import the 
  from . import views) the dot is a current 
]

# Also, we need the view to process the files within the registration url. So go to users -> views.py where we will have all the functions that will be used for processing
  from django.shortcuts import render
  from django.http import HttpResponse
  # Create your views here.
  def registration(request):
  return HttpResponse("Hello world!")
  # After, turn on the server and put in the search bar:
  http://127.0.0.1:8000/users/registration/
  Make sure the "Hello World!" message is there

# But we're not going to return just a "Hello world!", we're going to return an entire html!
  # First, we'll make settings for Django, from where it will look for our HTML files
  # Go to Core -> settings.py -> TEMPLATES 
  # Import the operating system module in the beginning
  import os (Is used to import the operating system module into Python. The OS module provides an interface for accessing and manipulating operating system resources such 
  as directories, files, processes, and more) 
  # TEMPLATES:
  TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')], (os.path.join() It is used to concatenate directories independent OS and the (BASE_DIR) is a constant, references 
                                                        the path from the root of the computer to the root of our project and the 'templates' is the name of directory that 
                                                        you will create)
        'APP_DIRS': True, (If true, Django will also look for 'templates' within the app, that is, it can create a 'templates' folder where you can create HTML files 
                          within folder users)
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
] 

# Once you have created the templates folder inside the users folder, you will create an html file inside that templates folder
# Now, you will return an html rendering that will receive a request, with the name of the file
  from django.shortcuts import render
  from django.http import HttpResponse
  def registration(request):
    return render(request, 'registers.html')

# Finally, when we have templates made in figma or others and we realize that there are many colors that are repeated, codes and styles, we will do this:
  # Create a base file.html in templates (other than the templates from inside the paste users)
  # And inside this base file, you put the common characteristics of each page that your project will have
  # Inside the base.html (copy & paste):
{% load static %}
<!doctype html>
<html lang="en">
 <head>
 <meta charset="utf-8">
 <meta name="viewport" content="width=device-width, initial-scale=1">
 <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
 <title>Pystack</title>
 {% block 'header' %} {% endblock %}
 </head>
 <body>
 {% block 'content' %}{% endblock %}
 <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
 </body>
</html>

These lines of code are standard settings for html files, such as bootstrap...But {% block 'header' %} {% endblock %} and {% block 'content' %}{% endblock %} are blocks mean that there will be another html file that will extend this base and insert new html code inside these blocks

# Inside the registers file.html you will put: {% extends "base.html" %} to this file to inherit all the characteristics of the base base.html
# Your page will appear empty
# Finally, you'll put {% block 'content' %} and then {% endblock %}. Anything within that will be applied to all page content
# When this is done, you won't need to repeat html code, just extend the base and put the code inside {%%}. Remembering that the codes you put INSIDE will be applied to the line of code that is in the base.html

That was the initial configuration file for my project using the django framework! Follow the same steps to create your own ☆ ★ ✮ ★ ☆☆ ★ ✮ ★ ☆

  
  

  

  
