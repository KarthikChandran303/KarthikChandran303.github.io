---
title: Rendering Dense Grass Fields
summary: A breakdown of how I used shell texturing to render grass.
weight: 1

image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: true

---
{{< video src="grassvid.mp4" controls="yes">}}

Rendering grass is a topic that has always intrigued me. In the past, I've experimented with GPU instancing 3D grass blade meshes, used billboards, and explored Unity's built-in grass system for terrains. So when I came across Youtubers Acerola and Harry's videos on shell texturing and learned that a friend needed a lightweight solution for stylized grass in his game, it only made sense that I try using shell texturing to render some more grass! I was pleasantly surprised with the results. I learned that it is possible to fabricate dense grass fields from simple textures. While there are certainly trade-offs to using this technique, such as overdraw, visual artifacts, and scalability, if used correctly, one can leverage their artistic vision to create optimized grass fairly quickly. Below is a brief breakdown of the steps to achieve shell-textured grass.

{{< video src="grass-breakdown.mp4" controls="yes">}}

First, a compute shader procedurally generates shells along the normal of the base mesh. Each generated vertex contains normal, UV coordinates, position, and height data. (the height data is normalized so that the highest shell has a height of 1 and the lowest shell has a height of 0) This data is then passed to the vertex and fragment shader where we offset the masking textures, discard pixels, and generate color data. A pixel is discarded if the height of its shell exceeds the value sampled in the masking texture. This creates a tapering effect (since higher shells will have more pixels discarded), effectively simulating a grass blade. For my mask, I used a texture generated in Substance Designer.

{{< figure src="grass-height.png" caption="Grass Masking Texture" numbered="true" data-zoomable=true >}}

The fragment shader is also responsible for displacing the grass wherever the ball moves.

{{< video src="uv-grass.mp4" controls="yes" >}}

The video above demonstrates how a particle system is utilized to bend grass and how a UV space is constructed for reading and using render texture data in each shell. An orthographic camera follows the ball from above, projecting a top-down view onto a render texture. This camera exclusively renders particles emitted from a particle system attached to the ball. It's important to note that the particle color is set to blue, allowing us to extract particle data from a single color channel. To read the particle render texture in the fragment shader, a UV space is constructed using the following code.

{{< figure src="particleCode.png" caption="Constructing Ortho Cam UV Coordinates" numbered="true" >}}

We then use this data to discard pixels based on the shell height, masking texture data, and particle color (where i.color.x stores the height of a shell).

{{< figure src="clipCode.png" caption="Discarding Pixels" numbered="true" >}}

Note that the Clip() function discards a fragment if the value passed to it is below zero.


