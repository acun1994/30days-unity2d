---
layout: default
title: Day 11
---

# Day 11 Content

## Boundary

Instead of manually checking and destroying Objects as they leave the game area, we can define a region as our game area, and destroy objects as they leave the game area.

We do this by creating a new cube, with a Trigger Collider, and no Mesh Renderer. This sets up an invisible region that acts as a trigger. Resize it to fit the playfield, then attach the following code onto a script.

```
void OnTriggerExit(Collider other) {
    Destroy(other.gameObject);
}
```

The code will destroy any object with a collider that exits the play area.