---
title: 2D C++ Game Engine
summary: Developed a 2D Game Engine using C++ and the SFML library
weight: 4

featured: true

image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: true

---
{{<video src="GameEngineRec.mp4" controls="yes">}}
I developed a 2D game engine using SFML and C++. For the engine I implemented:

- ​A system where timelines can be anchored onto other timelines to manipulate the passage of time in the engine.
- Multi-threaded Networking using the ZeroMQ library - supports unlimited clients to be connected asynchronously.
- An entity component system that allows for the creation of game objects.
- An event management system - that handles, raises, and registers events.
- Scripting functionality using the V8 library.

I developed two games in the game engine: a simple 2d platformer where multiple characters can join to traverse an environment, and a co-op version of space invaders.

Visit my github repo to try the game engine out: https://github.com/KarthikChandran303/GameEngineDev

Most of the features I've designed for my game engine have been modified over time to work in tandem with the game object model I initially implemented. So I'd like to summarize the game object model I've chosen, discuss how it has fared, and then proceed to explore how other game engine features have changed over the course of the two games I created.

I decided to implement a property-based game object model (although it also exhibits properties of an object-centric model). Each component class encapsulates information related to a game object’s property (e.g., transform data, collision data, render data, etc.). System classes are responsible for updating component classes. In each update loop, systems’ update functions are called, updating information stored in components. For the most part, this game object model has worked really well. Having component-wise updates has allowed me to order game engine updates in a sequence that doesn’t depend on the order of game object updates but rather on similar data. This was especially useful for my first game, a 2D platformer, since I wanted all position updates to happen before collision updates. Components also made it easy to create and destroy objects. Creating objects just meant generating a unique identifier and adding components to it. Destroying objects just meant removing components from a specific ID. Components also made it easy to send objects over the network. For example, my rendering component and system would generate JSON that contained rendering information based on a game object’s components. Clients would then read the JSON file and redraw everything on the screen based on said JSON. Objects would be drawn to the screen with the addition or removal of just one component.

My main use of multithreading was to enable any number of clients to connect to a server without delay. For each player in a scene, a thread is created that listens to information sent to a specific socket. Then all the threads send out controller events that are handled by respective systems. This implementation stayed the same across both games I created. For my second game, Space Invaders, most of my changes were done to server.cpp, the file containing my main function. I added a function that created game objects and added components to said game objects. The game objects and components would define the path that the invaders would follow. A lot of the other functionality for Space Invaders was implemented in the systems.cpp class, either as event handlers or minor changes to how collision worked. 

Overall, it looked like too many changes did not need to be made for the second game. A typical cycle to add more functionality to the game engine would be to create game objects, attach the needed components, and then add a system class that updates its respective components.
