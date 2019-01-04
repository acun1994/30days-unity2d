---
page: day3
---

# Day 3 Content

Now I am following the [tutorial](https://unity3d.com/learn/tutorials/s/roll-ball-tutorial) to create a basic game from scratch.

# Creating GameObjects from scratch

Create GameObjects from stock Unity Assets by clicking Create in the Hierarchy window. Example, Create -> 3D Object -> Plane, creates a flat plane.

You can adjust the position manually, or via the Inspector window, and reset its position to the origin by clicking on the Gear icon in the Transform component.

Pressing 'F' or Edit -> Frame Selected, centers the current GameObject in the view of the Scene window.

Scaling the object can be done by clicking the Scale button in the top toolbar, or directly from the Scale values in the Transform component. For the Plane GameObject, it is simply a flat surface, and does not have volume; therefore, it cannot be scaled on the Y-axis. Planes are single sided objects, meaning they only interact with objects from one side. You can change which side it's facing by inverting the Y-axis in the Transform component.

All Unity objects have a predefined size of 1x1(or 2)x1 units. As such, all scaling and transformations are based around this unit value.

# Changing a Look

![Day 3 Progress - Basic Game Scene](/30days-unity2d/images/Day3_1.jpg)

GameObjects' visual appearances can be changed simply by using a Texture, or a Material (simpler). To apply a Material to a GameObject, simply select and drag the Material from the Project folder, to the target GameObject in the Scene Window.

All Unity scenes come preloaded with a static directional light source. The light thrown by this source is uniform and comes from a set angle to all GameObjects.

