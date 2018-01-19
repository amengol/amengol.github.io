---
title: The Stanford Bunny
layout: post
category: game_graphics
tags: [Computer Graphics, OpenGL]
excerpt: Today we got to draw something different than a simple rotating triangle. We draw a rotating bunny! It didn't even looked like a bunny though, just a random number of lines from points to points that I supposed were once vertices of the bunny model, but it is very hard to tell
image: /img/2017-09-11/stanford-bunny.jpg
comments: true
---

Hi, I'm Jorge Amengol, a student of [Game Development - Advanced Programming](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year){:target="_blank"} at [Fanshawe College](https://www.fanshawec.ca/){:target="_blank"}, ON Canada. I decided to start this series of posts to register my own progress throughout the course and also to serve as reference for me on important subjects in the future. Though it is a personal record, you might find the subjects discussed here useful. Feel free to make comments at the end of each post.

### A silly bunny

Today we got to draw something different than a simple rotating triangle. We draw a rotating bunny! It didn't even looked like a bunny though, just a random number of lines from points to points that I suppose were once vertices of the bunny model, but it is very hard to tell:

![GDP Bunny]({{ "/img/2017-09-11/gdp-bunny.jpg" | absolute_url }})

Well, that bunny is not so thrilling at all, but we really made some progress to get to display it. First, the model is being loaded from a [PLY file](https://en.wikipedia.org/wiki/PLY_(file_format)){:target="_blank"}. In other words, we are now able to load any geometry from an external file, and this bunny has 948 triangles, way more than we had before. Second, we had the change to explore more about how the Graphics pipeline works. It is very interesting indeed, but still I think we just scratching the surface of how it works. It seems pretty complicated with all that stages. Let's hope it will get clearer further in the course.

### Not a silly bunny

![GDP Bunny]({{ "/img/2017-09-11/stanford-bunny.jpg" | absolute_url }})

Another interesting thing of today's class was also get to know that the [Stanford Bunny](https://en.wikipedia.org/wiki/Stanford_bunny){:target="_blank"} had really a great contribution for the development of Computer Graphics. It, among other models at the [Stanford 3D Repository](http://graphics.stanford.edu/data/3Dscanrep/){:target="_blank"}, has been used to test graphics algorithms. So, this bunny has history and that is why we see it and the others Stanford Models all over computer Graphics Books. It is good to know where they come from!


Jorge Amengol.