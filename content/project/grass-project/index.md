---
title: Rendering Dense Grass Fields
summary: A breakdown of how I used shell texturing to render grass.
date: 2024-01-07

image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: true

---
{{< video src="grassvid.mp4" controls="yes" >}}

Rendering grass is a topic that has always intrigued me. In the past, I've experimented with GPU instancing 3D grass blade meshes, used billboards, and explored Unity's built-in grass system for terrains. So when I came across Youtubers Acerola and Harry's videos on shell texturing and learned that a friend needed a lightweight solution for stylized grass in his game, it only made sense that I try using shell texturing to render some more grass! I was pleasantly surprised with the results. I learned that it is possible to fabricate dense grass fields from simple textures. While there are certainly trade-offs to using this technique, such as overdraw, visual artifacts, and scalability, if used correctly, one can leverage their artistic vision to create optimized grass fairly quickly. Below is a brief breakdown of the steps to achieve shell-textured grass.

{{< video src="grass-breakdown.mp4" controls="yes" >}}
