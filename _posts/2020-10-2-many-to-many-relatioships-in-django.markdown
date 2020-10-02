---
layout: post
title:  "Many to many relationships in django"
date:   2020-10-2 21:03:36 +0530
---

Many to many relationships in django are very useful, and are used to describe various day to day situations.

For example, lets say, we have many people in different clubs in a college. One person can be in multiple clubs simultaneously and multiple people are assosiated with one club.

To describe such a situation, our models.py file looks something like this:

```
class Student(models.Model):
    name = models.CharField(max_length=50)

class Club(models.Model):
    name = models.CharField(max_length=50)
    members = models.ManyToManyField(Student)
```
models.ManyToManyField(Student) is used to establish this relationship. 

The best way to understand how this works is to use the django shell, which can be opened, quite simply by typing in your command prompt:

```
python manage.py shell
```

After importing the student and club models from our app models, we can start by saving some students, initially:

	>>> student1 = Student(name=’Rohan’)
	>>> student1.save()
	>>> student2 = Student(name=’Neha’)
	>>> student2.save()
	>>> student3 = Student(name=’Rimjhim’)
	>>> student3.save()
	
Let us create a club:

```
>>> club1 = Club(name= ‘Science Club’)
```

Here is a very important part, you cannot associate a club with a student until the club has been saved. So this is something crucial to remember,
if you are working with forms, for example. There, you first need to save the club, and then associate a student with it. So, let's go ahead and save it first.

```
>>> club1.save()
```
  
To add student to the club, simply type the command:

```
>>> club1.members.add(student1)
```

Ww can also add multiple students at once, adding a student1 twice is OK too. It won’t be duplicated.

```
>>> club1.members.add(student1,student2)
```

We can also access all the members of a club at once:

```
>>> club1.members.all()
```

This returns a query set, containing all the members of our clubs.

There is a lot of functionality available, when it comes to many-to-many relationships in django. More information can be found on the [django documentation][d-docs] 
which contains an extensive list as well as examples of all the availabe uses.

[d-docs]: https://docs.djangoproject.com/en/3.1/topics/db/examples/many_to_many/
	
