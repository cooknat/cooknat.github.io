---
layout: post
title: BlocJams
feature-img: "img/blur_bg_1.jpg"
thumbnail-path: img/jamshp.png"
short-description: BlocJams - JavaScript and jQuery music player

---


Summary
------------
BlocJams is a simple browser based music player, allowing a user to select and play tracks from a collection of albums.

Explanation
------------
An introduction to the building blocks of web development, BlocJams uses CSS, HTML, JavaScript and jQuery, along with custom music library Buzz, to create a site which allows users to view a collection of albums before playing and controlling the music through a player overlaid on the album page.

The problem
------------
The main complexities in this project were around controlling the playback of the music, while ensuring the user would always be presented a view which reflected the available options.

This logic required that a play button would only show when a song was highlighted by the user, a pause button would only show when a song was playing, and that multiple songs would not be able to play simultaneously. These controls were made available to the user both within the album list and on the music player overlay itself.

There was also a requirement to reflect the progress of a track on a bar, allowing the user to see where in the track they are, and to use a 'thumb' to skip backwards and forwards within the current track. There was also a similar bar allowing the user to alter the volume.

{:.center}
![]({{ site.baseurl }}/img/jamsalbum.png)

The solution
------------
The logic was handled using JavaScript and jQuery, split between a clickHandler function which dealt with playing, pausing and stopping songs, a mouseover function showing a play button to a user as they hovered over a song, and various helper functions to set album details, move between tracks and create the seek bars - amongst other things.

One of the most complex parts was ensuring that the 'thumb' - a draggable circle on the music player seek-bar, would accurately reflect the position in the track.  

The first step was to make this work visually. This involved taking the length of the song and reflecting that in a fixed width seek bar. On click, the position clicked was converted into a percentage to update the styling of the seek bar, making sure the bar was 'filled' to the left of the click and moving the thumb to the clicked position.

The second step was to allow the user to drag the thumb to a different position on the seek bar. This involved adding an event listener for the mousedown event:
{% highlight javascript %}
     $seekBars.find('.thumb').mousedown(function(event) {...
{% endhighlight %}  

using the jQuery bind() event to attach the mousemove event to the document:
{% highlight javascript %}
     $(document).bind('mousemove.thumb', function(event) {...
{% endhighlight %}  

and unbinding on mouse up:
{% highlight javascript %}
     $(document).bind('mouseup.thumb', function() {
         $(document).unbind('mousemove.thumb');
         $(document).unbind('mouseup.thumb');
{% endhighlight %}           

The third step was to update the seek bar as a track played. For this we created a function using a custom Buzz event, timeupdate, which we bound to the current track object before updating the seek bar.

The final step was to allow users to seek to a new part of the song by clicking the seek bar or dragging the thumb. This was a fairly simple function which used the Buzz setTime() method to skip around in the track.
{% highlight javascript %}
var seek = function(time) {
     if (currentSoundFile) {
         currentSoundFile.setTime(time);
     }
 }
{% endhighlight %}    

Results
------------
The application was tested at each stage of development and the final version met all requirements, allowing the user to browse between albums and play and control the music.

Conclusion
------------
This was a very interesting learning exercise which showed how much can be achieved with JavaScript and JQuery. It was enjoyable to move away from more static display type webpages to work on an application style project which allows the user to do so much more. Working with JQuery was a useful introduction to the world of libraries and frameworks, and encouraged thinking about the DOM in a new way.
