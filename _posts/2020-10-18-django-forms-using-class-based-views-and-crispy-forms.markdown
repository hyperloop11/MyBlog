---
layout: post
title:  "Djnago forms using Class Based Views and crispy forms"
date:   2020-09-27 21:03:36 +0530
--- 

While working with forms, we usually require two things: GET request and POST request. While GET requests are used to request data from a specified resource, POST requests are used to send data to update or create a resource. Since, a form creating an object will likely be creating and updating databases, our forms will transfer user data via a post request. 

Now, a great thing about using class based views for our forms is that django automatically handles a lot of logic for us. On top of that, ```crispy_forms```, Django’s application for creating forms which allows adjusting forms' properties, like send button, CSS properties, etc. on the backend without writing them in the template, handles a lot of the frontend part for us.

This tutorial assumes you have a django project and crispy forms already installed, if not, you can create a project using [this][my-blog] tutorial and install crispy forms by following the installation guide on the [official docs][o-docs].

Let us assume, for the purpose of this tutorial that we have to create a Blog post by a certain author using a form. So the Post model in out ```models.py``` file looks something like this:

```python
from django.db import models
from django.contrib.auth.models import User

class Post(models.Model):
	author = models.foreignKey(User)
	Title = models.CharField(max_length=200)
	Content = models.TextField()

	Def __str__(self):
		return self.title
```
The ```__str__``` method simply returns a string representation of the entire object, i.e, calling the post object by the title of the post.

In our views.py file, we can simply configure the ```CreateView``` to suit our needs and Django does the rest of the work for us.

So, we configure our ```views.py``` file like so:

```python
from django.views.generic import CreateView
from .models import Post

class PostCreateView(CreateView):
	Model = Post
	Fields = [‘title’, ‘content’]
``` 

And, that’s it. We don't have to write any kind of post request validation logic ourselves. Also, we don’t not have to specify a template anywhere in our views, CreateView automatically uses a template based on our model name, which in this case is going to be ```post-form.html``` in our templates directory. In this file, the logic for crispy form comes in, we don’t have to write any additional CSS to style our forms. So, let us create this file and add the form to the file. Below, is the relevant section of the post-form.html file:

```html
{% load crispy_forms_tags %}
.
.
.
<form method="POST">
                {% csrf_token %}
                <fieldset class ="form-group">
                    <legend class="border-bottom mb-4">
                        Issue
                    </legend>
                    {{form| crispy}}
                </fieldset>
                <div class="form-group">
                    <button class="btn btn-info" type="submit">Submit</button>
                </div>
            </form>
```
The button and legend classes are simple bootstrap classes. The important thing here is loading the template tags for crispy forms, namely ```crispy_forms_tags``` and while displaying form, simply add ```| crispy``` after the vertical bar. 

The last thing to do is to configure our urls.py file to use PostCreateView in the views.py file when we access the url to create a new post.

```python 
from .views import PostCreateView
#this is used if views are in the same directory as the urls.py file.

urlpatterns = [
…
path('post/new/', views.PostCreateView.as_view(), name='post-create'),
]
```
And this should give us a working form in django, further information can be found on the [django docs][d-docs]

[my-blog]: https://hyperloop11.github.io/MyBlog/posts/experiment-with-django-1/
[o-docs]: https://django-crispy-forms.readthedocs.io/en/latest/install.html
[d-docs]: https://docs.djangoproject.com/en/3.1/topics/class-based-views/generic-editing/
