---
layout: post
title:  "My experiments with django 1"
date:   2021-07-13 21:03:36 +0530
---
# Engaged and Agile

In this blog, I am going to elaborate on some of the strategies I utilized for building my project, how I used the agile methodology to schedule my sprints, my interactions with the mentors and how I incorporated their feedback into my design and thinking patterns.

1. The challenge 
2. First week
3. Second week
4. Third week
5. Last week
6. Conclusion

<hr>

### The challenge

The challenge we received was to build a Microsoft Teams Clone. The minimum qualifying criteria was to build an application, using which at least two people could have a video call.

For me, the most interesting feature was the focus on agile methodology. Something I had heard of frequently every now and then, but never studied in detail, let alone used for my projects. Here is how I utilized it in this project. I divided my week into two sprints. I had a meeting with both my mentors once a week, mostly on Fridays.

Discussing my ideas with them and taking their input into account, I created goals for my next sprints. I decided to try and finish my project by third week, so that I had time to implement the surprise feature, which was to be announced in the last week, as well as keep plenty time for implementing the surprise feature, as well as clean up my code, improve its efficiency and still have enough time for the documentation and the demo. 

<hr>

### First week
My first week started with research about the product I was going to build, I worked on understanding the requirements better, which tools and technologies to use, web frameworks, APIs, etc. Basically trying to make a solid foundation for the project I was going to build and try to schedule the rest of my three weeks, giving me sufficient time for the surprise feature, going to be announced in the fourth week. 

For the video calling API, between webRTC and jtsi, I found webRTC to be much more customizable and useful to incorporate, using the Peer JS library. Lastly, it came down to the choice of Flask or NodeJS for the backend. While, I was quite experienced in Flask, I decided to go with Node JS for the backend because of the ease of handling ansynchronous functions with Javascript, the available libraries for Video calling and web sockets, namely PeerJS and Socket.io as well as ample documentation and developer support for the same.

##### Mentor Input
In the consequent one on one meeting with my mentors on Friday, I discussed my approach. I was suggested to learn and understand agile, and implement my project using it. Also, we discussed the need to make my UI intuitive and easy to understand as well as making the mandatory feature my top priority.

##### Week's progress
By next Monday, I had decided to study about Agile and used the SCRUM framework for this project. As my first sprint, I decided to make a simple To-Do list application using Node JS and Express JS, to familiarize myself and get a good understanding of them. There were no backlogs for Monday.

<hr>

### Second Week
Next week started with a workshop on agile principles, followed by an assignment on the same. My goal for this Thursday was to implement the bare minimum video calling. My plan was to create room using socket IO library, and then transfer the video of each person connecting to the room using Peer JS. Despite my best efforts, this took longer than anticipated and spilled onto Friday. 

##### Mentor Input
By the end of this week, I relayed my progress to my mentors who thought my progress was good. I told them about my plan to improve the current video calling feature, adding mute/unmute toggles and implementing a chat for the same. I also discussed some additional features I was planning on adding, and took their input on it. Fianlly, I decided to go on a chat feature, where users can create rooms and share room IDs with other people. 

##### Week's progress
By Monday, I had finished adding the mute/unmute and Video on/off buttons to the application. I had started working on impementing the in-call chat feature. This took significantly more effort than I had anticipated, particularly because it required a deeper knowledge about web sockets. Next week had a backlog of adding the chat feature.
<hr>

### Third Week
During the first half of the week, I started to read up about web sockets. To realsie my plan of making a chat application, I decided to start form the basics. I firstly created a chat functionality where users could join pre-defined rooms. 

##### Mentor Input
This week's mentor discussions were probably the most engaging and insightful. From the last mentor discussions, I had recieved feedback that I should be more vocal in our one to one sessions, which, being an introvert, was hard for me at first. But this meeting was very insightful because I spoke more freely, and had very good discussion about where should i take my project, the utility of the features I was adding, making the chat and video calling features work cohesively, as well as the general direction the website was going in. 

##### Week's progress
After the mentor's feedback I had decided to implement the feature where users had the capacity of adding rooms too. I also implemented the in-call chats for the users. Now, the only thing left was making the UI look better.

<hr>

### Fourth Week
On Monday morning, the surprise feature was announced, which was to store user chat in a database, so that users can continue the conversation after the meeting, and start the conversation before the meeting. So far, I was right on schedule. But this new feature would be tricky to implement. I thought about how to take this furthur. To implement this not only would I have to add user authentication, but assosiate chats and rooms to a user and also store all messages. I researched about my options in the first half of the week. Also worked on improving the flow of the program and started cleaning up, and refactoring some of the code.

##### Mentor Input
The last discussion with my mentors, we discussed my progress. We discussed whether or not to add the additional feature, keeping the deadline in mind, as well as discussed about the submission, I asked their opinions on how I should structure my demo video, the documentation as well as all the things I was doing to improve my code.

##### Week's progress
After our final call, I decided, it was in the best interest of time that I didn't implement the surprise feature. I deployed the code and started working on improving the look and feel of the UI. I also started on the documentation and video for the project. And with that, my engage journey came to an end.
<hr>

### Concluding thoughts and experience with Agile

It was a very rewarding and enriching experience to build this project in the Engage Mentorship program. As my first experience using Agile, I found it very practical and useful. My interactions with mentors, as well as other mentees, were very insightful. I am definitly using Agile to build my next projects, as well as all the knowledge I recived in the program.
