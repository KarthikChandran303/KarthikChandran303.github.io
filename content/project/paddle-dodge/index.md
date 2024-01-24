---
title: Paddle Dodge
summary: Breakout but there's a twist!
weight: 3
tags: ["Game"]

featured: true

Custom links (uncomment lines below)
links:
- name: Unity 3D
- url: http://example.org

image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: true

---
{{< video src="Game_trimmed.mp4" controls="yes">}}

I recreated Breakout and added my own spin to it - players must dodge incoming obstacles while also keeping the ball in play! Inspired by segments in Star fox shooter-type games.

For this game I worked on:
- Designing the gameplay loop: players must dodge incoming obstacles while keeping the ball in play. The game will restart if either of two conditions are met: the players loses all their lives, or the platform is hit by too many obstacles.
- Writing c# code to implement paddle movement and ball bouncing.
- Using shader graph to create the visual effects (fog and abstract wall), and materials.
- Implementing UI for scores and lives.

The visuals of the game were fairly simple to implement. The long corridor-like background is composed of instantiated planes, each equipped with a shader. This shader generates procedural patterns and scrolls them towards the camera. The fog that you see is also a plane whose transparency depends on the depth of the scene sampled at a fragment - this causes the walls near the fog plane to taper slowly into the fog. Here is a breakdown of what the scene looks like while the game is in play.
{{< video src="paddlebreak.mp4" controls="yes">}}