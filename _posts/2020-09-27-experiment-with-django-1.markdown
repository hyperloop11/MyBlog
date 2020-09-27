---
layout: post
title:  "My experiments with django 1"
date:   2020-09-27 21:03:36 +0530
---
The setup with django is not as easy as it looks. 

First off, it is always recommended to use django( and almost every project) in a virtual environment. 
FOrtunately, Python 3.3 onwards, we already have the venv module installed in the Python Standard Library. To setup the virtual environment in Windows, head over to the command prompt. Type the following in there:


    python -m venv your_environment’s_name


If you are on any other platform, mre information can be found on [Django’s official Documentation][venv-docs]. 
This activates the python virtual environment that we are going to need to create a django project. Next, we need to activate our virtual environment to install the related packages we need. To do this, we activate the virtual environment by typing the following in the command prompt.


    your_environment’s_name\Scripts\activate.bat

  
Now, the command prompt looks something like this:


	(pro-tracker) C:\Users\username\folder>


Next, we install all the desired packages, for now, it is just django.


	pip install django


Next, to create a basic framework of our project in django, we run the command:


	django-admin startproject your_project_name


From this command, django automatically creates a Django project – a collection of settings for an instance of Django, including database configuration and setting for the applications we are going to create. More information can be found on [Django Documentation][django-docs]


[django-docs]: https://docs.djangoproject.com/en/3.1/intro/tutorial01/
[venv-docs]: https://docs.python.org/3/library/venv.html

