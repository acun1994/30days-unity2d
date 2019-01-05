---
layout: main
title: 30 Days
page: index
---

<div class="container">
<div class = "row">
<header>

# Welcome

Welcome to a beginner's attempt to learn Unity within 30 days, and hopefully have a completed demo game. The final aim is to produce a 2D Tower Defence game for Windows.
</header>
</div>
<div class="row">
<div class="col-md-1"></div>
<div class="col-md-5">

# Resources and Other Download Stuff

## Software Used
* VSCode
* Unity
* C# Extension for VS Code
* .NET SDK

## [Integration Unity x VS Code](https://code.visualstudio.com/docs/other/unity)

## Reference: 
* [Unity - Basic Interfaces](https://unity3d.com/learn/tutorials/s/interactive-tutorials)
* [Unity - Simple Game Mechanics](https://unity3d.com/learn/tutorials/s/roll-ball-tutorial)
* [Extra - Tower Defence Template](https://unity3d.com/learn/tutorials/s/tower-defense-template)

</div><div class="col-md-4">

## Links to each day's stuff
{% assign doclist = site.data.list.docs %}
<ul>
{% for item in doclist reversed %}
    <li><a href="{{ item.url }}">{{ item.title }} - {{ item.desc}}</a></li>
{% endfor %}
</ul>
</div>
<div class="col-md-2"></div>
</div></div>
