---
layout: post
title: BlocChat
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/blocchat.png"
short-description: An Angularjs members-only chat room

---

Summary
------------
BlocChat is a browser based chat application, allowing a user to create rooms and send messages to other users.

Explanation
------------
Chatrooms currently available on the World Wide Web exist in a wide variety of guises and formats, and cover pretty much any topic you could ever think of. Bloc Chat is a simple one page chatroom, allowing the user to chat to others about whatever takes their fancy, in a room of their choice, and to create their own new rooms if required.

Problems and Solutions
----------------------
BlocChat required the use of Firebase database application to store details of the chat rooms themselves, and the messages that appear in them. Implementing Firebase in the application is well documented and quite straightforward, but some experimentation was needed to correctly query and display the saved data. AngularFire's authentication API was also used to create temporary guest accounts for users.

Creating modal windows to handle username entry and adding new rooms was another new challenge in this project. Creating a modal in Angular requires two separate steps - opening a modal using Angular's $uibModal service, and then handling the users' input and closing down the modal in a separate controller.

{:.center}
![]({{ site.baseurl }}/img/addroom.png)


Results
------------
The application meets the requirements of allowing the user to create rooms and messages. There are currently some limitations in that there is limited space for the room list and message list, but this is something that could be addressed in a second iteration.

Conclusion
------------
A second Angular project has helped to reinforce my knowledge of the framework, although there were still many stumbling blocks! I look forward to continue to increase my proficiency on future tasks.
