---
layout: default
title: Day 7
---

# Day 7 Content

## Creating Pickups

Creating Pickups is just like creating any other GameObject. However, we usually want pickups to be flashier and stand out from the background of the scene. We can do this by adding a shiny Material to it, sure; but adding Movement or Rotation to the GameObject is even better. To accomplish this, we use the Transfrom class and its assoociated functions, Rotate and Translate.

Rotate rotates the object, and Translate moves the object on the x,y and/or z axis.

The following script implements a simple rotation to the object. Note that we use the Update() function and not the FixedUpdate() function. This is because we are not applying any forces to the GameObject, but are rather just modifying the visual appeareance.

```

void Update () {
        transform.Rotate (new Vector3 (15, 30, 45) * Time.deltaTime);
    }
}

```

We can also create a bobbing effect, by using the Translate function.

```
    transform.position += Vector3.up * Mathf.Sin (Time.time) * 0.005f;
```

The above snippet alters the position following a scaled down sine wave. The sine wave takes the playtime as it's input, and as such gives us a consistent smooth wave. The result is shown below.

![Day 7 Progress - Bobbing and Rotating Pickup](/30days-unity2d/images/Day7_1.gif)

## Detecting Collisions