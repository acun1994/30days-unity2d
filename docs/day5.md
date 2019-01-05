---
layout: default
title: Day 5
---

# Day 5 Content

## Linking Camera to Player

You can create a simple link between GameObjects by dragging a child GameObject to a parent GameObject ibn the Hierarchy window. This causes any transformations performed on the parent GameObject to also be applied to the child GameObject. 

However, a camera cannot be tied to a player simply in this manner, as **ALL** transformations will be carried over to the child object (i.e. the Camera). This includes rotations, and we do not typically want the camera to rotate with the object.

```
public GameObject player;

private Vector3 offset;

// Start is called before the first frame update
void Start()
{
    offset = transform.position - player.transform.position;
}

// Update is called once per frame
void LateUpdate()
{
    transform.position = player.transform.position + offset;
}
```

By using the above script tied to the Camera object, the camera will follow the position of the tied Player, thus creating a tracking camera shot. Now we need to tie the target GameObject (player) to the Camera. We do this by dragging the Player GameObject from the Hierarchy window onto the exposed Player variable in the camera's script component.
