---
layout: default
title: Day 6
---

# Day 6 Content

## Creating Empty GameObjects

You can create empty GameObjects to organize your other GameObjects into a folder-like structure in the Hierarchy window. Be sure to reset the "Parent" to origin, so that transformations of its child GameObjects aren't affected.

For example, you can bind multiple 'Wall's to a 'Walls' parent object, so that it doesn't clutter up your hierarchy when you work on other GameObjects.

![Day 6 Progress - Walls and Tracking Camera](/30days-unity2d/images/Day6_1.gif)

## Viewing during Play Mode

During PlayMode, you may want to visualize certain GameObjects's position and rotation. You can do this by changing the Tool Handle Rotation in the top toolbar. In Global Mode, the axes visualised are fixed to the origin's axes; in Local Mode, the axes are shown relative to the GameObject that is selected.