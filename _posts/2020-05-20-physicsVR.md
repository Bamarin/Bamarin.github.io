---
layout: post
title:  "[PhysicsVR] Fingers interaction"
date:   2020-05-13 14:24:35 +0100
categories: VR gamedev unity physics
---
Some objects, like the crowbar and sledgehammer, have handles which could theoretically be grabbed in many different ways. However, the current implementation meant that these tools always had fixed grab points and could only be held in one way, regardless of where the user initiated the grab. To correct that, we need a system where tools can have the position and length of their handles predefined, and can be grasped in any position along the handle.
The handle is therefore defined by two child objects representing both ends of the handle. What’s important about these objects is their relative position to the main object. Some adaptations had to also be made in the existing code, specifically the specific grab point of an object should no longer be restricted to always its world position, but instead allow for different possible grab positions. Additionally, a “Grab Action” routine had to be added, since the dynamic grab point is defined the moment the user initiates a grab.
Previously, the grab point could be represented as always being (0,0,0) relative to the object (in other words, its transform.position value). Now, whenever the user grabs an object with a handle, a new grab point is calculated and stored, and this relative position is then used to find the grab position in world space. This grab position is then used for the force-based movement of the grabbed object as discussed in a previous entry.
In order to find this grab point, the object needs to take the position of the hand when the grab is initiated, and find the nearest point on the line between both ends of the handle. This is done by first calculating the dot product between the (normalized) direction vector from one end to the other and the direction vector from one end to the hand’s position. The hand’s position is then projected onto the line to find the final grab position. This position is clamped between the two ends if needed. It should be noted that all these operations are performed in the object’s local space.
Naturally, this implementation only works with straight handles as is.


* Type of project: VR
* Repository: [Github](https://github.com/gdn002/PhysicsVR)
