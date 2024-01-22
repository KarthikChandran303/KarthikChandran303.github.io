---
title: Paddle Dodge
summary: Breakout but there's a twist!
weight: 3

featured: true

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