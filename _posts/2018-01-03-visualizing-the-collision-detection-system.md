---
title: Visualizing the Collision Detection System
layout: post
category: DesignPartterns
subtitle: Visualize it before doing it for real
categories: Game Physics, Collision Detection
excerpt: Bla bla bla
---

Hi, I'm Jorge Amengol, a student of [Game Development - Advanced Programming](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year) at [Fanshawe College](https://www.fanshawec.ca/), ON Canada. I decided to start this series of post to register my own progress through the course and also to serve as reference for myself in important subjects in the future. You are welcome to leave any constructive comment after each post.

### Introduction

When I as trying to implement `Collision Detection` to my engine last week, I had some problemns trying to figure out if the design was even right. I put some scratch in the paper and went directly to the code when I realized that I dind't know if what I was thinking had a coherent logic. So I figure it out that I needed to visualize it before anything else, so I started a series of visual aiding to be able to tell if I was right or wrong before trying to implement the logic in the Physics engine.

### Visualizing the Axis-aligned Bounding Boxes (AABBs)

The first thing I needed to make sure was working right was the AABBs. I have already wrote about them and how I implemented them [here]("aboutme"). Basically they are construct to narrow your collision calculations. My first try was using the `cDebugRender` class that Professor Feeney gave us in class. I got it working for the bouding boxes, printing lines for the sides of the cube and assemblying all togeteher to display them. It worked great for the job. 

The way I created the AABB was that it would be there for all triangles and even more than one for triangle if the triangle was too big for it. I loaded a mesh and then got this result:

![AABBs throughtout the mesh terrain]({{ "/img/2018-01-03/AABBs_FULL.jpg" | absolute_url }})

As it can be seen, there was no AABB where it would  not have a triangle inside it. So, it was working fine.

### Printing only one AABB where it matters

At first, Feeney's class worked great, but now I wanted to print only one AABB where a debug sphere would represent the object to test the collision. In other words, wherever was the sphere and if there was an AABB there, it should print the AABB. The problem was that the way `cDebugRenderer` worked it would not allow me to print one AABB and then erase it and print another one. Of course I could change his class to do so, but as it was already very complex I decided to build my own to do the job: `cSimpleDebugRenderer`. I deceided to not create a specific shader for it, as the previous class, but to have its own VAO, so I could create a geometry and reuse it whenever I wanted it. The first geometry was obviusly a cube. 

There was two basic methods: `genDebugGeometry()` and `drawDebugGeometry()` that would do the job (parameters ommited).

![Dynamic AABBs print]({{ "/img/2018-01-03/Sphere_Run.gif" | absolute_url }})

Nice. I got it working too. Now lets test for a different sized AABB!

![Dynamic AABBs print]({{ "/img/2018-01-03/Sphere_Run2.gif" | absolute_url }})

Cool huh? Ok, time for the normals...

### Visualizing the normals



The first thing I needed to make sure was about the normals of the triangles. 

### Conclusion

As you can see, the `Abstract Factor Pattern` can be very handy when you want to control how you create families of objects, mainly if you want to limit how those objects are "interfaced" with other classes. It is very easy to implement in C++, as long as you pay special attention to how an `interface` should be created. The downside of using this pattern is the great dependence your code can create to interfaces and if they change, the chain reaction it could cause in your code is huge.

### C++ Source Files

I developed this code using Visual Studio 2017 Community. If you want to see the entire code or even run it in your machine, please go to my GitHub page about Design Patters and look for `Abstract Pattern`.

I hope this has help you in any way, and if you have questions or any suggestion to make this text or the code better, please feel free to contact me by any means at the bottom of this page.

Have fun coding,

Jorge Amengol.



