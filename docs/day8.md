---
layout: default
title: Day 8
---

# Day 8 Content

## User Interface

Begin UI creation by Creating a UI element from the Hierarchy window. You will see 3 items pop up: Canvas, Text, and Event System. All UI Text must be a child of a Canvas Object for it to behave properly.

To change the position/anchoring of the Text, click the box shaped icon on the top left of the Rect Transform Component. You will most likely want to change the Pivot and Position of the Text as well, so hold 'Shift' and 'Alt' while selecting a new anchor position. You can change the default text in the Text component.

You can also change the text from another script. If you wish to use other variables in the Text, be sure to convert them into a String first by using ToString(). Then, link the Text object from the Hierarchy window onto your script. Similar to how we linked the Camera to the Player in Day 5.

```
public Text countTxt;

countTxt.text = "Count : " + count.ToString();
```


You can also get the current number of active objects in the scene with a specific tag.

```
GameObject.FindGameObjectsWithTag("Pickup").Length
```

To hide or show Text, you can either toggle the enabled property of the Text, or simply set the text value to an empty string ("").

```
winTxt.enabled = false;
```
<a href = "/30days-unity2d/builds/Roller Build 1.zip" download="Dev Build Roller">Download Completed Build </a>

![Day 8 Progress - Complete Level](/30days-unity2d/images/Day8_1.gif)


