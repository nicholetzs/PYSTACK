# PYSTACK
Project with python language and django framework ⊹˚. ♡.𖥔 ݁ ˖

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

# Now let's install Django and the other libraries:
  # pip install django
  # pip install pillow 
  pip is Python's package manager, and through pip, you install the libraries
  The Pillow library is a Python image processing library that offers a number of functionalities for processing

  # Inicialize a django project:
  django-admin startproject pystack . (pystack is the name given to the new Django project and the dot at the end specifies the directory in which the project should be 
  created. In this case, it is the current directory)

  

  
