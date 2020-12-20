---
title: VDungeon
code: VDungeon
category: vDungeon
permalink: /VDungeon
banner: "/assets/images/vdungeon/title.png"
video: "https://drive.google.com/file/d/1vWwAvstuZiCn9L2g9PVEvxkBK_8MLckx/preview"
list_title: Posts
---


#### [Download](https://github.com/Bamarin/AGI20_Group05_VDungeon/releases) and Installation
Download the application by clicking on the link that will take you to the [repository's releases section](https://github.com/Bamarin/AGI20_Group05_VDungeon/releases) and downloading the latest release (`VDungeon.zip`).

Run the file named `VDungeon.exe`, then chose either Master (you will host the game) or player (you will be asked the IP of an host).
Enjoy!

#### The team

<div class="row">
  <div class="col s12 m2">
  </div>

{% for member in site.team_members %}
  <div class="col s12 m5">
    <div class="card horizontal blue-grey darken-1">
      <div class="card-image waves-effect waves-block waves-light">
        <img class="activator" src="{{member.portrait}}" alt="{{member.name}}">
      </div>
      <div class="card-stacked">
        <div class="card-content">
          <span class="card-title activator"><i class="material-icons right">expand_less</i>{{member.name}}</span>
        </div>
        <div class="card-action">
          <a href="#">This is a link</a>
        </div>
      </div>
      <div class="card-reveal blue-grey darken-2">
        <span class="card-title grey-text text-darken-4"><i class="material-icons right">expand_more</i>{{member.roles}}</span>
        <p>{{member.content | markdownify}}</p>
      </div>
    </div>
  </div>
{% endfor %}
</div>


