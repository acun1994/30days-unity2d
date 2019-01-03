---
page: index
---


# Welcome

Welcome to a beginner's attempt to learn Unity within 30 days, and hopefully have a completed demo game. The final aim is to produce a 2D Tower Defence game for Windows.

# Resources and Other Download Stuff

## Software Used
* VSCode
* Unity
* C# Extension for VS Code
* .NET SDK

## Integration Unity x VS Code:
* https://code.visualstudio.com/docs/other/unity

## Reference: 
* https://unity3d.com/learn/tutorials/s/interactive-tutorials
* https://unity3d.com/learn/tutorials/s/tower-defense-template

## Links to each day's stuff
{% assign doclist = site.data.list.docs | sort: 'title'  %}
<ol>
{% for item in doclist %}
    <li><a href="{{ item.url }}">{{ item.title }}</a></li>
{% endfor %}
</ol>
