---
title: Technologies
permalink: VDungeon/technologies/
---

### Graphics and Technologies

#### The board
<div class="row">
  <div class="col s12 m6">
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

  <div class="col s12 m6">
    <img src="https://lh5.googleusercontent.com/NQLqUjxrBfdXt2LkUbTrTNyOFIYgIAOZ1eZyaI5wVASlpPZXoh8UbKYHOtZtikFY_RHrupDBkuRYukQ3gbGZIPOLMHf7M0buQnwHP1aEOi1GvblpME0f46nGRvsV3JSKphmVuIG9" alt="" class="responsive-img">
  </div>
</div>

#### Main Menu Scene, UI and Particle Effects
For better management purposes, the whole project is separated into two scenes, the main menu scene and the game scene. The main menu scene is built from a combination of a free pixel-style asset [Voxy Legends](https://assetstore.unity.com/packages/3d/environments/dungeons/voxy-legends-environment-pack-vol-1-95825) and our own world models, which is rendered in real-time with animated particle effects and baked global illumination with soft shadows to create a more realistic dungeon atmosphere.

![animated background](https://lh6.googleusercontent.com/bPRr19agATNEqOvcJCfXVBbKRDlFkZRqMZXlMSEsLb3objrEx_V_I058nfH8XFfEi0_8pmm5qon1gVuml1iRENfGAzA7tQWvt9pSICZw8BFCEeQzeTKH5jIflxYjrzvhWcfbEsOQ)

To unify the pixel-style throughout the game, all UIs are pixel arts drawn using Photoshop or modified from assets [SimplePixelUI](https://assetstore.unity.com/packages/2d/gui/icons/simple-free-pixel-art-styled-ui-pack-165012?locale=zh-CN), with implemented animation to support smooth hovering/popping up/disappearing effects. The particle effects for fire are also based on a pixelated material, created through accumulating four separated particle systems which represent the outer flame, inner flame, glow, and the sparks separately.

![flame particles](https://lh6.googleusercontent.com/kDTE9ud40yldTR9SIoh23axInUiaj_mwRhdJsUVvBYjENYfLCYchgdVVpNJOc7MiQpI5cwSra_G4C7yhHoEsRKY77GALc7uczQRlS0fvaWkQB6G6ELX_hNOl66hpSzWe086BMTVT)

From the main menu to the game scene, users' choice to be a master/player, and the IP address to connect need to be transferred together with the scene. To achieve this, Unity PlayerPrefs is used to store these data locally.

