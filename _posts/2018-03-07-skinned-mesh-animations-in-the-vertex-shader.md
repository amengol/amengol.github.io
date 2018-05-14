---
title: Skinned Mesh Animations in the Vertex Shader
layout: post
subtitle: The overall idea
category: animation_programming
tags: [Animation Programming, Graphics Programming, OpenGL]
excerpt: In class we have implemented a full skinned mesh animation using Assimp. There are some thorough tutorials on the Internet about this, but here I will try to summarize only the Vertex Shader part of the process, as the solution to pass all the transformation may vary a lot in the C++ side.
image: /img/2018-03-07/Thumbnail.png
comments: true
---

Hi, I'm Jorge Amengol, a fresh graduated student of the [Game Development - Advanced Programming](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year){:target="_blank"} course at [Fanshawe College](https://www.fanshawec.ca/){:target="_blank"}, Canada. I decided to start this series of posts to register my own progress throughout the course and also to serve as a reference for me on important subjects in the future. Though it is a personal record, you might find the subjects discussed here useful. Feel free to make comments at the end of each post.

### Introduction

In class we have implemented a full skinned mesh animation using [Assimp](http://www.assimp.org/){:target="_blank"}. There are some thorough tutorials on the Internet about this, but here I will try to summarize only the Vertex Shader part of the process, as the solution to pass all the transformation may vary a lot in the C++ side.


### The Vertex Shader Changes

As I have already explained in the [previous post]({% post_url 2018-02-27-skinned-mesh-animations %}), a skinned animation (or Skeleton Animation) has a lot of things involved, but some of them will not be done by a Graphics Programmer, rather the animations itself and the bone weights for each vertex will be prepared in a previous stage by an artist in what is called a [Rigging Process](https://en.wikipedia.org/wiki/Skeletal_animation){:target="_blank"}.

For Graphics Programmers, the job is to make an animation work with a skinned mesh. A key aspect to keep in mind is that the animation itself is a separate entity and is completely independent from the mesh. Well, they are infected quite bound together in the sense that both have to follow the same rules as the total number of bones, bone weights per vertex, bones hierarchy, distance between bones etc. However, a skinned mesh can be driven by different animations and even by more than one at the same time.

Thus, a key step that we have to take to be able to start playing with those kinds of animations is understand and prepare our Vertex Shader to deal with them.
Besides the Position, Texture Coordinates and Normal, our Vertex Shader will also have to have two more especial values:  
1.	A `boneID`, representing a unique bone in the hierarchy of bones;  
2.	A `boneWeight`, with the value that a particular bone should influence the vertex;  

In the C++ side of our application we will have an array of bones and each bone will be transformed by the animation that is being called at the time. This is also a little bit involving, but here I will try to keep things only on the Vertex/OpenGL side. 

After each bone is transformed, most of the time using interpolation, we will draw the object, using the transformed values of each bone to calculate the final position of the Vertex.

The first step is to send all of our bones (really matrices transformations) to our vertex shader as a Uniform array when we want to draw the mesh. They should be already transformed to the right Model Space position in the C++ side.

 Back to the Vertex Shader, each vertex will be influenced by four bones. Their values are called `Weights` and are predetermined by the Artist during the Rigging process and usually never change per bone. 
 
So, our shader will need 2 arrays of 4 values, one for the 4 bones that can influence the Vertex and the other for the 4 weights that each bone receives. (They must add up to 1) To receive these values and because they vary per vertex, we should use the in in the Vertex Shader and the pair `glEnableVertexAttribArray()` and `glVertexAttribPointer()` in the C++ side. As we only need 4 values for both of them, it is very convenient to use two vec4 in our shader. The code should look like this:

```c++
in vec4 boneIDs;	
in vec4 boneWeights;
```

Again, these two vec4 are being passed for each vertex. The boneIDs vector will have up to 4 bone IDs. We should convert their values to integers when we try to use them to index our array of Bones.
Finally, to calculate the end position of the vertex, we should add each bone transformation multiplied by its weight like this:

```c++
mat4 BoneTransform  = bones[ int(vBoneIDs_x4[0]) ] * vBoneWeights_x4[0];
     BoneTransform += bones[ int(vBoneIDs_x4[2]) ] * vBoneWeights_x4[2];
     BoneTransform += bones[ int(vBoneIDs_x4[1]) ] * vBoneWeights_x4[1];
     BoneTransform += bones[ int(vBoneIDs_x4[3]) ] * vBoneWeights_x4[3];
```

The `BoneTransform` is the matrix that will store all transformations cumulatively. Then, we take the vertex position and multiply it by the final value stored in this matrix like this:

```c++
vertexPosition = BoneTransform * vertexPosition;
```

After that, we will have our transformed vertex in the world position. From there, we follow the same flow as usual and multiply it by our `MVP` (Model-View-Projection) matrix to have our vertex in Clip Space.

### Conclusion

In this post I tried to summarize what we have to do to our Vertex Shader to be able to have skinned mesh animations working on our applications. I also mentioned that there are several ways to work with the animation itself in the C++ side of our program, but the focus here was only the Vertex Shader.

Keep in mind that, although it may look like a tutorial, this first intention here is to be a journal and serve as a reference to me in the future. However, I hope this was helpful in any way. Please feel free to leave a comment or, if you want to contact me, use any means at the bottom of this page.

Have fun coding,

Jorge Amengol.