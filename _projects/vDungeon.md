---
title: VDungeon
code: VDungeon
category: vDungeon
permalink: /VDungeon
banner: "/assets/images/vdungeon/title.png"
video: "https://drive.google.com/file/d/1jL_kE5HZTKgDHRbU3h5bVWXLN9uZ-Y48/preview"
list_title: Posts
---

  <div class="row">
    <div class="col s12 m10 offset-m1">
      <div class="video-container">
        <iframe src="https://drive.google.com/file/d/1vWwAvstuZiCn9L2g9PVEvxkBK_8MLckx/preview" width="100%" height="450px" frameborder="0" allowfullscreen></iframe>
      </div>
    </div>
  </div>

### Goals and Motivation
###### We want to provide a more engaging way to play Roleplaying Games (RPGs) at a distance.
<div class="row">
  <div class="col s12 m7">
    <p style="text-align: justify;">
    The current pandemic has forced the majority of us to stay at home, so we wanted to create something that could bring people together online.
    We thought of the many people that started approaching RPGs online and what could be the difficulties with it.
    Clearly, communication is the crucial part in this kind of game, and most of it is non-verbal so showing your face with a webcam helps a lot.
    </p>

    <p>But what if I don't feel confortable with showing my face to, possibly, strangers?</p>

    <p style="text-align: justify;">
    VDungeon solves this problem by providing a virtual avatar that will match your facial expression.
    This also allows to fully immerse into the story, by being able to see what your teammates look like, and even letting you see the world from the eyes of your character!
    </p>
  </div>
</div>

### The team

<div class="row">
  <div class="col s2"></div>
{% for member in site.team_members %}
  {% if member.abc == 5 %}
  <div class="col s12 l5 offset-l2">
  {% else %}
  <div class="col s12 l5">
  {% endif %}
    <div class="card horizontal blue-grey darken-1">
      <div class="card-image waves-effect waves-block waves-light">
        <img class="activator" src="{{member.portrait}}" alt="{{member.name}}">
      </div>
      <div class="card-stacked">
        <div class="card-content">
          <span class="card-title activator"><i class="material-icons right">expand_less</i>{{member.name}}</span>
        </div>
        <div class="card-action">
          {% if member.github %}
          <a href="https://github.com/{{ member.github| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#github' | relative_url }}"></use></svg></a>
          {% endif %}
          {% if member.linkedin %}
          <a href="https://www.linkedin.com/in/{{ member.linkedin| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#linkedin' | relative_url }}"></use></svg></a>
          {% endif %}
          {% if member.facebook %}
          <a href="https://www.facebook.com/{{ member.facebook| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#facebook' | relative_url }}"></use></svg></a>
          {% endif %}
          {% if member.instagram %}
          <a href="https://www.instagram.com/{{ member.instagram| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#instagram' | relative_url }}"></use></svg></a>
          {% endif %}
          {% if member.youtube %}
          <a href="https://youtube.com/{{ member.youtube| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#youtube' | relative_url }}"></use></svg></a>
          {% endif %}
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

