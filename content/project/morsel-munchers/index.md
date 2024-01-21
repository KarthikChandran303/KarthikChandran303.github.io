---
title: Morsel Munchers
summary: Two week long game project.
date: 2023-01-05

featured: true

image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: true

---
{{< video src="mm-gameplay.mp4" controls="yes">}}

Morsel Muncher was a 2 week long project we worked on as a part of our advanced games project class. Following a pachinko-style concept, the player must control paddles to direct morsels of food into heat zones ensuring the food is cooked before it reaches the alien’s mouth.

In this project I worked on:
- Designing the gameplay loop
- Creating shaders and materials: custom skybox shader, heat zone shader, peg color switch shader, and paddle shader.
- Integrating art assets into the scene

I used Unity's shader graph to create a procedural Skybox shader. 

{{<video src="Skybox.mp4" controls="yes">}}

If we use the world coordinates of a skybox to map textures onto it, we will see UV distortion that stretches textures towards the ends of the skybox. This distortion arises because of the non linear nature of spherical coordinates. To address this issue, we use inverse trigonometric functions to map a linear UV coordinate system from world coordinates.

Here is the subgraph I used to generate said UV coordinates. 

[![SubGraph for Skybox UV Coordinates](UVSubGraph.png)]

The stars, clouds, and the wavy lines that you see in the skybox are all generated from simple noises. With the Skybox’s UV coordinates, you can generate almost any effect imaginable in the fragment shader. Below is the complete graph for the skybox shader. Please click on the image to view the graph in full resolution.

[![Shader Graph for Skybox](SkyBoxGraph.png)](/SkyBoxGraph.png)
To optimize the skybox, it might also be worth it to try and export frames that the skybox shader generates as an animated texture. 

I also created a heat distortion effect that samples and distorts the the background.

{{<video src="window.mp4" controls="yes">}}

Here is the graph for it:
[![Shader Graph for Heat Distortion](HeatCopy.png)](/HeatCopy.png)

