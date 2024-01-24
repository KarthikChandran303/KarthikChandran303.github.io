---
title: Cell Circuit
summary: Race around the circulatory system to keep organs healthy!
weight: 6
tags: ["Game"]

featured: true

links:
- name: Unity 3D
  url: https://unity.com/
- name: C#
  url: https://learn.microsoft.com/en-us/dotnet/csharp/
- name: HLSL
  url: https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl

image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: true

---
{{< video src="cell-circuit-trailer.mp4" controls="yes">}}

Cell circuit was a semester long project we worked on as a part of our advanced games project class. The player controls Leuko, a white blood cell whose duty is to race around the circulatory system, managing oxygenated and deoxygenated red blood cells, to ensure the optimal health of each organ.

The majority of my work in this project involved:
- Creating shaders and materials for 3D assets which included developing: cel shader, acid pool shader, grass wavy shader, and translucent shield shader
- GPU instanced alveoli that interact with the player
- 3D modelling organs and cell receptacles
- Particle effects for cell receptacles

Shader work:
{{< video src="ShaderForCell.mp4" controls="yes">}}

GPU Instance Alveoli:
{{< video src="CellCircuit.mp4" controls="yes">}}

You can play the game on itch.io here: https://rakthalekk.itch.io/cell-circuit