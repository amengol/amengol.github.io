---
title: Physics1 - Project 2
layout: post
subtitle: Final Projects for the Fall 2017 Semester
category: game_physics
tags: [Game Physics, Computer Graphics]
excerpt: For this project, Professor Feeney asked us to to show our implementation of the hierarchical bounding boxes, especially the Axis Aligned Bounding Boxes (AABBs). For that, he wanted that we had complex models being moved through a complex world, controlled by Newtonian forces and exhibiting detailed collision information with the environment.
image: /img/2018-01-14/Thumbnail.jpg
comments: true
---

Hi, I'm Jorge Amengol, a student of [Game Development - Advanced Programming](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year){:target="_blank"} at [Fanshawe College](https://www.fanshawec.ca/){:target="_blank"}, Canada. I decided to start this series of posts to register my own progress throughout the course and also to serve as reference for me on important subjects in the future. Though it is a personal record, you might find the subjects discussed here useful. Feel free to make comments at the end of each post.

### Introduction

For this project, **Professor Feeney** asked us to to show our implementation of the hierarchical bounding boxes, especially the Axis Aligned Bounding Boxes (AABBs). For that, he wanted that we had complex models being moved through a complex world, controlled by Newtonian forces and exhibiting detailed collision information with the environment.

The good thing is that I planned this Project together with the [Graphics]({% post_url 2018-01-12-graphics1-project2 %}) one, so I could implement all the necessary stuff into my engine already.

Here are the main requirements:

*- Renders a large, complex 3D environment*  
*- Must contain a user controllable ship that can be manipulated through multiple degrees of translational (and optionally, rotational) freedom*  
*- Must have a complex static environment that the entity navigates through.*  
*- Must detect a reasonably small, exact collision point or volume.*      
*- The location of the collision should be shown somehow.*  

### A Large Complex 3D Environment

Again, I used for this one the same environment used in the [Graphics Project]({% post_url 2018-01-12-graphics1-project2 %}). If you take a look at the session [The Models]({% post_url 2018-01-12-graphics1-project2 %}#models) of that post, you will have an idea of how complex the scene is. But here is an screen overview of it:

[![City Overview]({{ "/img/2018-01-14/Overview.jpg" | absolute_url }})]({{ "/img/2018-01-14/Overview.jpg" | absolute_url }}){:target="_blank"}

### The Delorean (controllable ship)

At my [Building a Camera System]("aboutme") post I explain how I have used `matrices` instead of `vectors` for the camera orientation. Around the same period, I also changed the orientation of the Game Object to use matrices and, like the camera, they were able to be moved around its local axis. From that, all that I needed was to configure my camera to "follow" the object, I mode that I already had implemented before. The result can be seen in this video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/MMC6WuxF3kA" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

<p style="text-align:right;"><i>See other videos on my <a href="https://www.youtube.com/user/JorgeAmengol">YouTube Channel</a></i></p>


### The Collision Detection

### Conclusion

This was somewhat a long post, and I did not mention a lot of details to keep it as short as possible. It was also a very demanding project, however I enjoyed doing it and solve the issues that I have encountered along the way.

I tried to show here the key things that were done and the main tricks that I did to solve some problems. I don't know yet what my grade was but one thing for sure is that I have learned a lot trying to put it all together.

In case you want to see the presentation of this project to **Professor Feeney**, you are welcome to watch it my YouTube channel here:

<iframe width="560" height="315" src="https://www.youtube.com/embed/RQO1KpIkc60" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>

I hope this has helped you in any way. Please feel free to leave a comment or, if you want to contact me, use any means at the bottom of this page.

Have fun coding,

Jorge Amengol.