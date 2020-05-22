---
layout: post
title:  "[PhysicsVR] Fingers interaction"
date:   2020-05-19 14:24:35 +0100
tags: VR gamedev unity physics
---

<video style="float:left; width:30%; height:auto; margin-right:20px" autoplay controls loop="loop">
  <source src="/assets/videos/hand-animation.mp4" type="video/mp4"  />
</video>
I have spent the past days implementing the animations of the fingers to physically interact with the obects.
In this case an animator isn't useful at all because the finger should fit objects of different shapes.

I started by working directly on rigidbodies and applying forces, but finally
realized that this wasn't an optimal solution because, after I have moved the
fingers around an object, to grab it, I want them to stay in place. Using
object transformations instead I have control over the current rotation and
this also avoids unnatural positions of the fingers.

I therfore created `hand` and `finger` classes, and builded a simple hand object.
and achieved the result shown in the animation above.
The hand is currently working in the following way:

The four fingers move simultaneously (not indipendently), what I'll be
referring as fingers ar actually the 3 segments which they are divided into.
Every finger has its movement limited to a single axis rotation between a min
and a max value.  When the grab button is pressed every finger will start
closing until the maximum rotation is reached, or if the last finger touches
something (through a collider). When the grab button is released, the fingers
will open again.

Initially I added colliders to every finger and the algorithm was more complex
in orther to have every finger touching the object.  However I had to dscard
this solution because in many cases you can't or don't want all the finger
touching the object but just the tip.

* Type of project: VR
* Repository: [Github](https://github.com/gdn002/PhysicsVR)
