---
layout: post
title:  "OneToOneField vs ForeignKey in django"
date:   2020-10-3 21:03:36 +0530
---

The basic difference between a OneToOneField and a ForeignKey in django lies in the fact that one creates a one to one relationship between two entities and the other, a many-to-one relationship.


A one to one relationship between object A and B states that one member of A can only be associated with one member of B, and vice-versa. Mathematically, it represents a [bijective function][bij-rel]. An example is the relation between a User and a Profile on a blogging website. A user has a profile and each profile belongs to a particular User. So, we use a OneToOneField for creating this association.  

On the other hand, a many to one relationship between object A and B states that, a member of object A is related to only one member of B, a member of object B can have many associations with member of object A. An example is the relation between a blog and a user. A blog is associated with only one user, whereas a user can be related to (i.e, author) multiple blogs at once.  So, we create a foreignkey for creating this association. 

In our models.py file:

```python

from django.db import models

class Author(models.Model):
    name = models.CharField(max_length=50)

    def __str__(self):
        return self.name

class Profile(models.Model):
    author = models.OneToOneField(Author, on_delete=models.CASCADE)
    bio = models.CharField(max_length=300)

    def __str__(self):
        return self.author.name

class Blog(models.Model):
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
    title = models.CharField(max_length=100)
    content = models.TextField()

    def __str__(self):
        return "%s written by %s" % (self.title, self.author)
```

Let us test the usage of these models in our django shell. After importing these models, let us first save a few Authors.

```
>>> a1 = Author(name='Rohan')
>>> a1.save()
>>> a2 = Author(name='Neha')
>>> a2.save()
```
Let us create a profile for a1:

```
>>> p1 = Profile(author=a1, bio='Life’s good')
>>> p1.save()
```

Since, it is a two way relationship, a profile can access an author, and an author can access a profile(if available).

```
>>>a1.profile
>>>p1.author
```

Both return valid objects.

Coming to the Blog, adding a blog associated with author a1.

```
>>>blog1=a1.blog_set.create(title=’Blog Title!’, content=’First blog content!’)
```
Notice that we don't need to explicitly mention the author for this blog, this method, by default creates the blog with author set as a1.

Django has a lot of functionality when it comes to these relationships, more can be found out about them at [ docs for one to one relationship][docs1] and [docs for many to one relationship][docs2]


[bij-rel]: https://en.wikipedia.org/wiki/Bijection#:~:text=In%20mathematics%2C%20a%20bijection%2C%20bijective,element%20of%20the%20first%20set.
[docs1]: https://docs.djangoproject.com/en/3.1/topics/db/examples/one_to_one/
[docs2]: https://docs.djangoproject.com/en/3.1/topics/db/examples/many_to_one/

