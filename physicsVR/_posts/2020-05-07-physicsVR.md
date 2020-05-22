---
layout: post
title:  "PhysicsVR: Spring and Grab"
date:   2020-05-07 08:50:50 +0100
tags: VR gamedev unity physics
---

In order to implement the spring mechanics and the ability to grab objects, we
both have used rigidbodies and colliders, already present in Unity.

Guilherme has started implementing a force-based hand moving system so that the
virtual hand's position isn't modified directly, but rather by calculating the
direction from the virtual hand current position to the one of the controller.
This vector is then multiplied by a configurable "force multiplier" parameter,
and also capped in magnitude by another "maximum force" parameter.  The
rigidbody's velocity is then reset and an instantaneous force based on the
directional vector is immediately applied.  As a result, the collisions between
the hand and objects is a lot more smoother, objects no longer spaz out or get
tossed around easily.  He is now experimenting with using forces to also rotate
the hand. 

I have realized the grab funcionality by setting up listeners on the controller
inputs and simply parenting the object in the proximity of the hand to the hand
itself.  However, this implementation is too simple for the scope of this
project. I have therefore decided, to extend this functionality with an
algorithm that is able to assess whether it is possible to grab a particular
object based on the grip that the hand has on its surface: if the object has a
large flat surface, a hand cannot grab it, but only push it.

Another suggestion proposed by Guilherme, consists of defining particular tools
that, if grabbed in a particular way (e.g. on its handle), can be used for its
purpose. This would allow, for example, to fire a gun.

* Type of project: VR
* Repository: [Github](https://github.com/gdn002/PhysicsVR)
