---
title: Webgl & Raytracing Exploration
summary: Advanced Computer Graphics Projects
weight: 9
tags: ["Project"]

featured: true

links:
- name: WebGL
  url: https://www.khronos.org/webgl/
- name: JavaScript
  url: https://developer.mozilla.org/en-US/docs/Web/JavaScript

image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: true

---
{{< video src="Frustum.mp4" controls="yes">}}
The video above demonstrates an implementation of frustum culling in WebGL. You can toggle between having frustum culling on and off to visualize which meshes are culled. For instance, in the video, when the frustum isn't updated with the player's location and rotation, you will notice that the meshes outside of the frustum aren't rendered. The HUD also keeps track of the triangle count, which is a good indicator of the frustum culling functioning as intended.

I also created a simple raytracer in JavaScript.
![Raytracing in JavaScript](raytracer.png)
It incorporates features like global illumination and employs Russian roulette for every indirect light bounce. The program also includes area light support and supports raycasting for spheres and planes.