---
title: Loading more than PLY files
layout: post
subtitle: The Assimp Loader
category: computer_graphics
tags: [Computer Physics, OpenGL, Assimp]
excerpt: We've been playing around with PLY files for so long now that it just became natural for us to show at a PLY file and say exactly what is going to be rendered at the screen. Ok, not that much though, but they are so easy to read that I'm sure the Matrix universe (the movie) certainly has used them to describe polygons...
image: /img/2018-01-29/dragonsplash.png
comments: true
---

Hi, I'm Jorge Amengol, a student of [Game Development - Advanced Programming](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year){:target="_blank"} at [Fanshawe College](https://www.fanshawec.ca/){:target="_blank"}, Canada. I decided to start this series of posts to register my own progress throughout the course and also to serve as reference for me on important subjects in the future. Though it is a personal record, you might find the subjects discussed here useful. Feel free to make comments at the end of each post.

### Introduction

We've been playing around with PLY files for so long now that it just became natural for us to show at a PLY file and say exactly what is going to be rendered at the screen. Ok, not that much though, but they are so easy to read that I'm sure the Matrix universe (the movie) certainly has used them to describe polygons...  :)   
Anyway, the problem is that there is an infinity of 3D file formats and surprisingly the PLY format is used more in an academic environment. Also, there might be much more information in a file than just vertices, normals and texture coordinates. 3D file formats can have from basic mesh information to a whole scene definition, including materials, cameras and animation to say just a few.    
So this week, the first of the Winter term, we to the point to say farewell to the PLY format limitations and grow our engine a little bit. So, how to load different formats then?

### Loading a new format

![3D formats]({{ "/img/2018-01-29/3d_formats.png" | absolute_url }})

For the PLY file we made our own loader. It was pretty straight forward, due the model being very simple to understand and read. However, with the introduction of **Animation** classes in this Winter term, we are certainly going to need to load a different format, since PLY does not support animations. Also, an "animation" is not usually stored alone, and is very common to have one associated with a Mesh and other 3D informations, therefore the new "loader" will have to read those new information too.  
We could have gone down that path, but besides the extra work to just get the model loaded, we would still have to be written different loaders from each different file format that we wanted to use and also for a different version of the same format, and that happens a lot. Wisely, our professor, Mr. Feeney made the right move and directed us to a very professional loader, so we can focus on more important content during the semester than just being making loaders.

### Assimp

`Open Asset Import Library` (short name: [Assimp](http://assimp.sourceforge.net/){:target="_blank"}) is a portable Open Source library to import various well-known 3D model formats in a uniform manner. This is the open line of the website, but seriously, this tool is just fantastic. It takes almost whichever model we have and gives us a container (*a scene*) with all loaded informations so we can do whatever we want with it. One question though, why we didn't use it since the beginning?  
Well, first of all, it would be like using sledgehammer to crack a nut. The format is a simple and well organize ASCII file.  
Second, the PLY file is quite didactic and help us to understand how vertices and triangles relate in a 3D file. Also, all the normals and texture coordinates are very easy to read, with them in a same line. Making a loader for it just made us more aware of the inners of a 3D model.  
Finally, how would we appreciate a loader like Assimp with we had get it right away?  

Let's briefly take a look at it them.

### What Assimp does and doesn't do for us

Assimp is an awesome tool, but don't think it will put the models onto our VAO for us, or load our samplers with its textures, or make our loaded model and animation just be magic blended together in our engine. What it gives us is its own representation of those things, so we can go ahead an use them. We are still going to build a *loader* to use what Assimp gives us, but the good news is that we won't have to be changing it to conform with new formats every time we need to load a different format, Assimp does all that job and does it pretty well.

### Assimp Structure

So, when we import a model using it, Assimp gives us a so called `aiScene`. For this tool, even if we are loading a simple mesh in a PLY format, it gives us back an "Scene", that is one class with all other informations that we want, like vertices, colours, texture coordinates etc. Most of the time, the *aiScene* will have at least one `aiMesh`, but can have multiples meshes. So, after loading our model, we just have to go thorough those [classes](http://assimp.sourceforge.net/lib_html/annotated.html){:target="_blank}, retrieve what we want and feed our engine pipeline with those information, like our VAO, or our texture loader. Of course this tool is very new to me, but for what it already did for my engine, I'm pretty impressed.

### Conclusion

Being able to load different formats, or even a single format, but doing it fast is really essential for a game engine. Thus, I tried to show here this incredible tool that makes a Game Engine Programmer's life just a lot easier. However, this was just a kind of a "intro" to the tool, please visit their [page](http://assimp.sourceforge.net/){:target="_blank"} to get to know it better.

I hope this has helped you in any way. Please feel free to leave a comment or, if you want to contact me, use any means at the bottom of this page.

Have fun coding,

Jorge Amengol.