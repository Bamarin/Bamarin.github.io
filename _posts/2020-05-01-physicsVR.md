---
layout: post
title:  "Physical Interaction Model for Virtual Reality"
date:   2020-05-01 13:38:17 +0100
categories: VR gamedev unity physics
---

This is an ongoin project that I'll be updating with new posts as it's developed. I'm working on this project together with [Guilherme Neto Diegoli](https://github.com/gdn002) for the course in Computer Graphics and Interaction at the Royal Institute of Technology in Stockholm.

Inspired by "[The Haptic Display of Complex Graphical Environments](robotics.stanford.edu/users/ruspini/publications/siggraph97.pdf)" (Ruspini et al., 1997), we decided to implement a similar solution in a VR context. 
The model is based, like in the paper, of two positions (Figure 1): the real position according to where the controller is located is space, and a virtual (proxy) position that is adjested according to the virtual environment.
This two representations of the player's hand are linked by a spring, in the sense that the second one is dragged by the first one with little (unperceivable) delay, and tries to minimize the discane when it isn't possible to match the real position becasue of virtual obstacles. 

<img src="/assets/images/VR-idea.png"/>

After a first [project specification](/assets/doc/physicsVR/specification.pdf) was developed and updated, we broke down the project into two tasks and started working on them separately.
I would implement the ability to grab objects while my collegue would work on the implementation of the spring through the use of physics.
We decided to develop our project within Unity, because it allows to develop a VR project quite easily.

* Type of project: VR
* Repository: [Github](https://github.com/gdn002/PhysicsVR)
