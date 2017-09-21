---
layout: post
title: BlocJams Angular
feature-img: "img/blur_bg_1.jpg"
thumbnail-path: "img/jamscollection.png"
short-description: Recreating the BlocJams music app using Angularjs

---

Summary
------------
BlocJams is a simple browser based music player, allowing a user to select and play tracks from a collection of albums. This new implementation uses a Node.js server, and Angularjs to manage states and control the music player functionality, and adds extra features to the original version.

Explanation
------------
Angularjs is a popular JavaScript framework designed to allow easy development of CRUD and Single Page Applications by extending the syntax of HTML. The challenge on this project was to redesign the architecture of the application to suit Angular while still keeping the same functionality as the original, and reusing code where possible.

Problems and Solutions
------------
As with the original version, the functionality of the music player was one of the biggest challenges - making sure controls worked as expected and that the song played and was tracked correctly. The code for this was mainly written in an Angular SongPlayer service which could be accessed from the Album and Player Bar controls.  Rewriting this code was a good illustration of what can be achieved with Angular in terms of making the HTML template itself more informative, for example the code below specifies what controls are shown by means of directives in the HTML elements which pass a true or false value to determine whether they should appear in the view:

{% highlight javascript %}
  <tr class="album-view-song-item" ng-mouseover="hovered = true" ng-mouseleave="hovered = false" ng-repeat="song in album.albumData.songs">
     <td class="song-item-number">
       <span ng-show="!song.playing && !hovered">{{ $index + 1 }}</span>
       <a class="album-song-button" ng-show="hovered && !song.playing" ng-click="album.songPlayer.play(song)"><span class="ion-play"></span></a>
       <a class="album-song-button" ng-show="song.playing" ng-click="album.songPlayer.pause(song)"><span class="ion-pause"></span></a>
{% endhighlight %}

This version also presents the user with a collection of albums stored in a Firebase database. This added the requirement for a new unique url path to be created for each album which added extra complexities. This was achieved by using the Angular $stateParams service to store information about the album which the user had selected, which was then used to navigate to the page with the correct album item and songs.

{:.center}
![]({{ site.baseurl }}/img/albumcovers.png)


Additional functionality included the ability for a user to quickly mute a song, and to return to the previous volume on unmute. This required new methods to display the correct mute/unmute icons and to store and return the user's chosen volume. The ability to autoplay each new track in an album when the previous one had finished was also added.


Results and Conclusion
----------------------
The application was successfully translated into Angularjs while maintaining existing functionality and adding new. Rewriting an existing app was a great way to appreciate the differences between the JQuery and Angular approaches - despite being occasionally confusing and frustrating. Learning when and where to use each type of Angular component, along with best practices for the code that should go in each, and the relationships between all the components is an ongoing learning process, but this was a good introduction to the fundamentals of the framework, and I feel I have learnt enough to use it successfully on future projects.
