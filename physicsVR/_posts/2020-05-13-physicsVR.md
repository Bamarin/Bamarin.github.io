---
layout: post
title:  "[PhysicsVR] Tools"
date:   2020-05-13 14:24:35 +0100
tags: VR gamedev unity physics
---
With the force-based hands working, implementing tools is as simple as
replacing the “hands” with the desired tool. This did require a slight rework
of the code so that the handling of the virtual hands would be done in the
controller objects instead of the hand objects. The reason for that is to
enable switching between different “hand objects” during runtime. The routines
themselves remained mostly unchanged.

A free asset pack was used to provide the tool models:
https://assetstore.unity.com/packages/3d/props/tools/tools-pack-1-20510.
Another pack was also used for a handgun that can also be picked up as a tool,
with the potential for it to be functional later:
https://assetstore.unity.com/packages/3d/props/guns/modern-guns-handgun-129821.
Each tool needed a similar hierarchical setup as the hands: an empty base
object with the rigidbody component, and a child model object with the
renderer, colliders and local transformations. 

Each model was transformed so that their handle would match the grip of the
controller, and was also given simple colliders to cover their meshes.
Different objects were given different masses, which translates to how fast
they can be moved in the virtual world.  In order to properly grab these
objects, the grab detection routine had to be adapted a bit. First, multiple
objects may be within grab range, which the previous routine did not handle
very well, so now the hands keep an array of which objects are within grab
range. Another issue was that, if the tool were resting over another grabbable
object, the generic object might get grabbed instead. So, the grab routine
prioritizes objects with a “Tool” component over generic objects.

While the force-based movement gives objects a sense of weight, rotation is
still 1:1, meaning even the heaviest objects can be rotated around
effortlessly. However, the physics do translate nicely to throwing: light
objects can be easily tossed over distance, while heavier objects will often
drop short of the player.

* Type of project: VR
* Repository: [Github](https://github.com/gdn002/PhysicsVR)
