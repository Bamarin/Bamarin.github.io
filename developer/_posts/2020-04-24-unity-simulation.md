---
title:  "Behavioral simulation in Unity"
date:   2020-04-24 13:00:42 +0100
tags: unity coding visualization 3D
---

## Introduction
This is a project that I made as part of the course of Introduction to Visualization and Computer Graphics at the Royal Institute of Technology of Stockholm.

It is my first project using Unity and I thought it was perfect for a visualization project because it would allow me to run a simulation and visualize its evolution in real-time in a 3D environment.

## The idea
While searching for cool simulations I got inspired by [Primer](https://www.youtube.com/channel/UCKzJFdi57J53Vr_BkTfN3uQ)'s video about [Simulating Natural Selection](https://www.youtube.com/watch?v=0ZGbIKd0XrM) and simplified the idea to a simple behaviour.

The ecosystem will be populated by 2 type of entities:
1. brainless blob monsters
2. brains

The firsts will have to eat the seconds in order to survive and reporduce: they start as brainless and gain a brain if they find and eat one. After that, for every additional brain they eat, they will give life to a new brainless blob monster. Every monster has a fixed life time, if one doesn't find any brain in that period it will die, if they do the timer will be reset.
The system starts with an arbitrary number of monsters, and brains will spawn continuously with a certain chance (Let's say 10% every second).

## Implementation
### FSM
I've implemented the behaviour described above using Unity's [Pluggable AI](https://learn.unity.com/tutorial/5c515373edbc2a001fd5c79d#) by modelling a finite state machine (FSM) composed of two states: 
1. searching for brain
2. reach brain

Every monster starts in the first state and switches to the second as soon as they see a brain. While in the first state the entity moves randomly and casts a ray that represents its eye sight. When it spots a brain it will switch to the second state and go in that direction trying to be the first one who reaches it. When the brain disappears, because it was eaten by any monster, the entity will switch back to the first state.

### Assets
The models for the simulations were done in blender. I first sculpted in detail every entity and then remeshed them manually to reduce to number of poliygons. I used only quads when remeshing to be able to animate the models and avoid weird stretches. The animations and even the renders were also done in blender. To achieve the fancy looking material I used cycles rendering engine, which uses ray-tracing.

## Conclusions
This project allowed me to experiment using Unity, an important engine for any game developer because it allows to develop a game, or a simulation in this case, rather quickly. I also realized that simulations can be as fun to develop as games and I might expand the behaviour into a more complex one in the future.

Here is a small demonstration of the running simulation
<iframe width="560" height="315" src="https://www.youtube.com/embed/n2_usuTuZDQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* Type of project: simulation
* Repository: [Github](https://github.com/Bamarin/3D-simulation)


