---
layout: page
title: Programming Projects
subtitle: Graphics and other Game Programming Projects
---

These are some of the Programming Projects that I was actively developing during the [Game Development - Advanced Game Programming](https://www.fanshawec.ca/programs-and-courses/program/gdp1-game-development-advanced-programming/next-year){:target="_blank"}.

### Game Jam (Graphics Technical Demo)

[![Game Jam]({{ "/img/portfolio/Game_Jam.png" | absolute_url }})]({{ "/img/portfolio/Game_Jam.png" | absolute_url }}){:target="_blank"}

This is my Game Engine showcasing some Graphics and Environment features at `Fanshawe’s Game Jam` on April 25th, 2018. It was based on the first stage of the acclaimed 80’s arcade game **Ghost’s n Goblins**.  
The entire scene and featured technical aspects were assembled in only two weeks.  
Everything were coded from the ground up using C++ and OpenGL (no third-party engines).  
It worth mentioning that the presentation was very well received by the members of the Game Industry attending the event.  

YouTube presentation of the project: 
<iframe width="560" height="315" src="https://www.youtube.com/embed/JC51l57uUAI" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

GitHub project: [Game_Jam](https://github.com/amengol/Game_Jam)

### (Game Physics) Real-time collision detection, AABBs, Debug Render etc (No third party physics)

This is a large complex scene with circa 600k vertices. There are Axis Aligned Bounding Boxes to make a Broad Phase calculation and simplify the physics calculations. A Debug Render was also developed to show exact points of collision, as well as AABBs, normals and faces inside AABBs.

GitHub project: [Physics1_Project2](https://github.com/amengol/Physics1_Project2)

YouTube presentation of the project: 
<iframe width="560" height="315" src="https://www.youtube.com/embed/RQO1KpIkc60?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


### (Game Physics) Dual Physics with "Home-made" and Bullet Physics

Demonstrates collision detection and reactions between sphere-sphere, and sphere-plane pairs. 

GitHub project: [Physics2_Project2](https://github.com/amengol/Physics2_Project2)

[![Dual Physics]({{ "/img/portfolio/Dual_Physics.gif" | absolute_url }})]({{ "/img/portfolio/Dual_Physics.gif" | absolute_url }}){:target="_blank"}


### (Computer Graphics) Point and Spot Lights, Texturing and Transparency, Interactive Camera

This projects explores Dynamic Lightening, Texturing, Specular, Transparency with render order control, Interactive camera and more...

GitHub project: [Graphics1_Project2](https://github.com/amengol/Graphics1_Project2)

YouTube presentation of the project: 
<iframe width="560" height="315" src="https://www.youtube.com/embed/C4p9HCKxRfM?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


### (Artificial Intelligence) Path finding with A*

Demonstrates the the use of the A\* algorithm to find a path through a maze where there are obstacles.

GitHub project: [Artificial_Intelligence_Project1](https://github.com/amengol/Artificial_Intelligence_Project1)

[![BusBunny A*]({{ "/img/portfolio/A_Star.jpg" | absolute_url }})]({{ "/img/portfolio/A_Star.jpg" | absolute_url }}){:target="_blank"}


### (Media Fundamentals) 3D Sounds, channel groups and DSP effects

For this assignment, FMOD lower level API was integrated to the custom OpenGL engine.

GitHub project: [Media_Fundamentals_Project2](https://github.com/amengol/Media_Fundamentals_Project2)

YouTube presentation of the project: 
<iframe width="560" height="315" src="https://www.youtube.com/embed/FC_N4EVUBPQ?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


### (Network Programming) Game Lobby

A game lobby browser that was supposed to be used by players to inform them what game lobbies are open, and which game lobbies they can join. It consists of a game client, game server, authentication server, and database(s) for the game. The code is in in C++, using raw TCP sockets. No websockets, or libraries that handle de-serialization, only BSD Sockets.

GitHub project: [Network_Programming_GameLobby](https://github.com/amengol/Network_Programming_GameLobby)


### (Network Programming) Server/Client Chat Application

We were supposed to develop a Server/Client Chat application. It was most used to achieve a better notion of Network Programming and all the application was developed in C++ using BSD Sockets. A tricky part of it was develop a basic protocol for it, and a serialization/de-serialization process to change numbers from Little Endian to Big Endian. 
There was a second assignment that built upon the first one where we were supposed to add an Authentication Server for the system using Google Protocol Buffers and also use MySQL to store all user login informations.

GitHub project:  [Info-6016_ServerClient](https://github.com/amengol/Info-6016_ServerClient)