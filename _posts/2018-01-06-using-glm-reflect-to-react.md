---
title: glm::reflect with Collisions
layout: post
subtitle: Collision Reaction
category: game_physics
tags: [Game Physics, Collision Detection, Collision Reaction]
excerpt: GLM is a toolkit for working with OpenGL and its functions can make a Graphics programmer’s life way easier. However, sometimes we get so used to a function that we may not realize that it can serve to similar purposes. One example of this is using the inverse of a `glm::lookAt()`function to make a matrix orientation “look at” a target, instead of just using it to calculate the camera/view matrix. The other, and that I touch in this post is the `glm::reflect()`.
image: /img/2018-01-06/Thumbnail.jpg
---

Hi, I'm Jorge Amengol, a student of [Game Development - Advanced Programming](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year){:target="_blank"} at [Fanshawe College](https://www.fanshawec.ca/){:target="_blank"}, ON Canada. I decided to start this series of posts to register my own progress throughout the course and also to serve as reference for me on important subjects in the future. Though it is a personal record, you might find the subjects discussed here useful. Feel free to make comments at the end of each post.

### Introduction

GLM is a toolkit for working with OpenGL and its functions can make a Graphics programmer’s life way easier. However, sometimes we get so used to a function that we may not realize that it can serve to similar purposes. One example of this is using the inverse of a `glm::lookAt()`function to make a matrix orientation “look at” a target, instead of just using it to calculate the camera/view matrix. The other, and that I touch in this post is the `glm::reflect()`.

### A bouncing sphere

Making a bouncing sphere is perhaps the simplest example of a physics reaction to a surface. At the very beginning of the Physics classes at my Game Programming course ([GDP1](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year){:target="_blank"}) the first thing that we made to collide with something was a sphere (actually it was a bunny, but let's not make a thing out of it, ok? :D ). The `reaction` was as simple as inverting the velocity 'Y' vector's sign at a certain "limit". For flat completely orthogonal planes, that will do the job, but it will probably mess the things up if we have inclined surfaces. For that, we have to produce a vector that has the same angle between the movement that the sphere had before colliding and the normal, but going out of the surface. 

An image can tell it better:

![Ball reflection]({{ "/img/2018-01-06/TennisBallReflection.jpg" | absolute_url }})

<sup>[Image source](http://ffden-2.phys.uaf.edu/webproj/211_fall_2014/Max_Hesser-Knoll/max_hesserknoll/Slide4.htm){:target="_blank"}</sup>


### Using glm::reflect to calculate the reaction

You probably already figured it out where we are going with this, but yeah, sometimes we don't see obvious things. `glm::reflect` is usually used to calculate `reflections` of the light over a surface, but as we can see, the reaction of the sphere to the surface is also a "reflection", so we can use it to calculate the angle that is described between the movement of the sphere and the normal after the collision. For that we just have to know the `incident vector` and the `normal` of the plane.

If you are using a vector for you velocity, that is a vector that indicates a point that your object should reach after an amount of time, you can use it directly as your `incident vector`. If you are using another way to calculate it, you can store the previous position of your object and get your vector by subtracting it from the current position. Each way will do. The `normal`, of course, is the normal of your plane (in many cases a triangle).

Syntax (from glm documentation):
```c++
genType glm::reflect (genType const& I, genType const& N); 	
```
_For the incident vector I and surface orientation N, returns the reflection direction : result = I - 2.0 * dot(N, I) * N._

If you want to make the same calculation inside a shader, you can use the `glsl reflect` as well.

Here a little video that I made of my `Collision Detection/Reaction` system working:

<iframe width="560" height="315" src="https://www.youtube.com/embed/yiyepbjxi3o" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>

### Conclusion

With this post I tried to demonstrate that sometimes we already have a tool for the job, is this case the glm::reflect function. Its common use is with lights, but here I used it to “reflect” a movement, because it has the same principle. Instead to look for another function or even implement a new one, perhaps the right tool is already in front of us.

I hope this has helped you in any way. Please feel free leave a comment or, if you want to contact me, use any means at the bottom of this page.

Have fun coding,

Jorge Amengol.