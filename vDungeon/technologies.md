---
layout: vdungeon
title: Technologies
permalink: VDungeon/technologies/
---

### Graphics and Technologies

<div class="row">
  <div class="col s12 l6">
    <h4> The Board </h4>
    <p style="text-align: justify;">
    The board uses a simplified coordinate system with grid cells being represented by integer X and Y values, which can be converted to and from world space coordinates (X, Y, Z).
    Wall pieces follow a special rule, where the wall object is offset from the center of the cell in order to stick to the space between cells.
    Objects can also have their rotation defined by four possible directions (North, South, East, West).
    Instead of using traditional colliders, board objects use simplified “logical colliders”: each grid cell can have any combination of five collision tags depending on the objects present on it: center, north, south, east, west.
    Two objects with the same collision tags cannot occupy the same cell.
    When moving players around the board, a pathfinding algorithm can also check if there is an available path between the origin and the destination. The algorithm used is a simple breadth-first pathfinding. 
    </p>

    <p style="text-align: justify;">
    World models were created in Blender, with the textures being hand-painted in GIMP.
    Later on the project, normal maps were also created by sculpting ridges and scraping edges on a high-poly copy of the world models, using the textures as a guideline.
    The details from the hi-poly model can then be “baked” into a normal map for the low-poly model, retaining most of the detail without the performance issues of using extremely complex models.
    </p>
  </div>

  <div class="col s12 l6">
    <img src="/assets/images/vdungeon/normals.png" alt="Normals on a wall." class="responsive-img">
  </div>
  <div class="col s2 l1 right">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/45/The_GIMP_icon_-_gnome.svg/1024px-The_GIMP_icon_-_gnome.svg.png" alt="Normals on a wall." class="responsive-img">
  </div>
  <div class="col s2 l1 right">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0c/Blender_logo_no_text.svg/1252px-Blender_logo_no_text.svg.png" alt="Normals on a wall." class="responsive-img">
  </div>
</div>

<div class="row">
  <div class="col s3">
    <img src="/assets/images/vdungeon/corner.png" alt="Normals on a wall." class="responsive-img">
  </div>
  <div class="col s3">
    <img src="/assets/images/vdungeon/door.png" alt="Normals on a wall." class="responsive-img">
  </div>
  <div class="col s3">
    <img src="/assets/images/vdungeon/pillar.png" alt="Normals on a wall." class="responsive-img">
  </div>
  <div class="col s3">
    <img src="/assets/images/vdungeon/wall.png" alt="Normals on a wall." class="responsive-img">
  </div>
</div>


<div class="row">
  <div class="col s12 m4">
    <h4> Unity </h4>
    <p style="text-align: justify;">
    We builded our application starting from the game engine Unity.
    This was an obvious choice for us since everyone had already at least a little experience with it.
    </p>
  </div>
  <div class="col s3 offset-s7 offset-m1">
    <img src="https://en.usens.com/wp-content/uploads/2017/12/ASJDkM91CLjQmt6oaNdk6g-unity-logo-white-rgb_smaller.png" alt="Normals on a wall." class="responsive-img">
  </div>
  <div class="col s2 offset-m2">
    <img src="/assets/images/vdungeon/mirror.png" alt="Normals on a wall." class="right responsive-img">
  </div>
</div>

#### Mirror Networking
Making a multiplayer game was a crucial part of this project, as we intended it to allow people to meet online. Since no one of us had experience in netcoding we chose to use a pre-existing API to simplify our work.

Mirror was a great choice because it offers high-level functions and it is well documented.
We were able to create a shared environment, where every player can interact with it, and the changes are reflected on the rest of the group that is connected to the same “room”. It was also quite easy to setup a public server, so that multiple people can connect over the internet.

However, Mirror has its own flaws as well: being a predefined tool, ready to use, means that it is especially good to make a particular job, but it is a lot harder to make things work in an unusual way. In this case, it is perfect for creating a MMO game, where every player has the same role as each other. However we wanted to define two very distinct roles: Master and Player. Although we managed to differentiate them, this was very hard to achieve.


#### Main Menu Scene, UI and Particle Effects
For better management purposes, the whole project is separated into two scenes, the main menu scene and the game scene. The main menu scene is built from a combination of a free pixel-style asset [Voxy Legends](https://assetstore.unity.com/packages/3d/environments/dungeons/voxy-legends-environment-pack-vol-1-95825) and our own world models, which is rendered in real-time with animated particle effects and baked global illumination with soft shadows to create a more realistic dungeon atmosphere.



<div class="row">
  <div class="col s12 m8">
    <img src="/assets/images/vdungeon/room.gif" alt="Normals on a wall." class="responsive-img">
  </div>
  <div class="col m12 l4">
    <p style="text-align: justify;">
      To unify the pixel-style throughout the game, all UIs are pixel arts drawn using Photoshop or modified from assets
      <a href="https://assetstore.unity.com/packages/2d/gui/icons/simple-free-pixel-art-styled-ui-pack-165012?locale=zh-CN">SimplePixelUI</a>, with implemented animation to support smooth hovering/popping up/disappearing effects. The particle effects for fire are also based on a pixelated material, created through accumulating four separated particle systems which represent the outer flame, inner flame, glow, and the sparks separately.
    </p>
  </div>
  
  <div class="col s12 m8 l4">
    <img src="/assets/images/vdungeon/flames.gif" alt="Normals on a wall." class="responsive-img">
    <div class="row">
      <div class="col s3 center">outer flame</div>
      <div class="col s3 center">inner flame</div>
      <div class="col s3 center">glow</div>
      <div class="col s3 center">sparks</div>
    </div>
  </div>
</div>

From the main menu to the game scene, users' choice to be a master/player, and the IP address to connect need to be transferred together with the scene. To achieve this, Unity PlayerPrefs is used to store these data locally.



#### Face Tracking
<div class="row">
  <div class="col s12 m6 l3">
    <figure>
        <img src="/assets/images/vdungeon/landmarks.png" alt="Normals on a wall." class="responsive-img">
        <a href="https://www.researchgate.net/figure/The-68-landmarks-detected-by-dlib-library-This-image-was-created-by-Brandon-Amos-of-CMU_fig2_329392737">researchgate.net</a>
    </figure>
  </div>
  <div class="col s12 m6 l6">
    <p style="text-align: justify;">
      The face tracking system starts with a face landmarks tracking procedure.
      For later estimation of head position, orientation and the facial expression features,
      68 face landmarks are tracked using Dlib and OpenCV library.
    </p>
    <p style="text-align: justify;">
      Based on the tracked landmarks, the orientation and position of  the head in a 3D space can be estimated using a monocular camera through PnP (Perspective-n-Point) measurement.
    </p>
  </div>
  <div class="col s12 m6 l3">
        <img src="https://www.learnopencv.com/wp-content/uploads/2016/09/pose-estimation-requirements-opencv.jpg" alt="Normals on a wall." class="responsive-img">
        <a href="https://www.learnopencv.com/head-pose-estimation-using-opencv-and-dlib/">learnopencv.com</a>
  </div>
</div>

<div class="row">
  <div class="col s12 m6 l3">
        <img src="https://www.learnopencv.com/wp-content/uploads/2016/09/ImageFormationEquation.jpg" alt="Normals on a wall." class="responsive-img">
        <a href="https://www.learnopencv.com/head-pose-estimation-using-opencv-and-dlib/">learnopencv.com</a>
  </div>
  <div class="col s12 m6 l6">
    <p style="text-align: justify;">
In general, the idea is to transform the 3D points in world coordinates to 3D points in camera coordinates. The 3D points in camera coordinates can be projected onto the image plane using the intrinsic parameters of the camera ( focal length, optical center etc.).
    </p>
    <p style="text-align: justify;">
The facial expression features extraction especially focused on tracking the openness of eyes and mouth, together with the distance between eyes and eyebrows. The core algorithm here is  Eye-Aspect-Ratio which is the mostly used feature for detecting eye-blinking. 
    </p>
  </div>
  <div class="col s12 m6 l3">
        <img src="https://lh5.googleusercontent.com/NEdpVPSIHlb6vKjJ86d3Q_spX0MrYB33GeMvdn3J3k4B4kr87Jpy7YBw4shn1JfwpXEOfNzjIhEHpsDh-dndx2j-riFGiDgbqk7diPEGl5mA__sgDKUuczbJd5tCUKSALwIJ6zp3" alt="Normals on a wall." class="responsive-img">
        <a href="https://hackaday.io/project/27552-blinktotext/log/68360-eye-blink-detection-algorithms#:~:text=The%20Eye%20Aspect%20Ratio%20is,defined%20by%20the%20below%20equation.&text=A%20program%20can%20determine%20if,is%20another%20facial%20landmark%20plotter">hackaday.io</a>
  </div>
</div>

This provides the primary base for the openness detection for both mouth and eyes. Based on it, a rotational invariance is added into computation by defining a reference distance which is insensitive to the rotation.

![eye distance](/assets/images/vdungeon/eye-distance.jpg)
![formulas](/assets/images/vdungeon/formulas.png)

Before mapping the face tracking data with the actual model, it can be observed that the detection results are quite noisy and unstable. Therefore a Kalman filter and a Median filter are implemented to reduce noise in image processing and stabilize the model animation. Kalman filter is used during landmarks tracking so that the history information is used rather than just relying on the detected location from the current frame alone. The Median filter is applied for further optimization by running through the signal entry by entry, replacing each entry with the median of neighboring entries in size of 5 frames.

  <div class="row">
    <div class="col s12 m10 offset-m1">
      <div class="video-container">
        <iframe src="https://drive.google.com/file/d/13Ukt8FZSQ7iln_6pwLit37NQ6V0k7RrN/preview" width="100%" height="450px" frameborder="0" allowfullscreen></iframe>
      </div>
    </div>
  </div>

#### Facial Animations
The animation style used to animate the face is called Morph target animation. This is done by having a default neutral face and a bunch of premade expressions that the face can morph into. These premade expressions are called blend shapes and we have created one for each moveable facial  feature. The blend shapes allows us to interpolate between the neutral expression and the modified ones and since this can be done for all blend shapes at the same time it creates a large range of possible facial expressions.

  <div class="row">
    <div class="col s12 m10 offset-m1">
      <div class="video-container">
        <iframe src="/assets/videos/blendshape_Trim.mp4" width="100%" height="450px" frameborder="0" allowfullscreen></iframe>
      </div>
    </div>
  </div>
