---
layout: text-img
title: Leonardo Marini
image: /assets/images/vdungeon/leonardo.jpg
permalink: /about/
---

Leonardo is a Computer Science Engineering student pursuing a career in the
gaming industry as a technical artist. His goal is to combine his programming
knowledge with his passion for animation to provide useful tools to other
artists in making videogames.

He started developing his passion for animation at the age of 17, when he
discovered [Blender](https://www.blender.org/), in its current version 2.68,
thanks to one of his teachers.

In his spare time, he enjoys role-playing games. ***Bamarin*** is the name he gave
to his first character, and it continued being his nickname online. It doesn’t
mean anything except that it includes part of his surname (Marini).

If there’s anything else you’d like to know about him, don’t hesitate to send
him an email!

{% assign member = site.team_members[0] %}
{% if member.github %}
<a href="https://github.com/{{ member.github| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#github' | relative_url }}"></use></svg> Github</a>
{% endif %}
{% if member.linkedin %}
<a href="https://www.linkedin.com/in/{{ member.linkedin| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#linkedin' | relative_url }}"></use></svg> Linkedin</a>
{% endif %}
{% if member.facebook %}
<a href="https://www.facebook.com/{{ member.facebook| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#facebook' | relative_url }}"></use></svg> Facebook</a>
{% endif %}
{% if member.instagram %}
<a href="https://www.instagram.com/{{ member.instagram| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#instagram' | relative_url }}"></use></svg> Instagram</a>
{% endif %}
{% if member.youtube %}
<a href="https://youtube.com/{{ member.youtube| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#youtube' | relative_url }}"></use></svg> Youtube</a>
{% endif %}
