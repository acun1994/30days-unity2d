---
layout: default
title: Day 9
---

# Day 9 Content

Now using the [Space Shooter tutorial](https://unity3d.com/learn/tutorials/s/space-shooter-tutorial)

## Lighting

To create lightings, one uses the Directional Light. a Directional Light shines light on all surfaces in a scene from a single direction. As such, its location doesn't really matter,only its rotation, as this defines from where the light will shine. You can change the light intensity and colour from the Inspector window.

## Movement and 3D Rotation

![Day 9 Progress - Space Shooter](/30days-unity2d/images/Day9_1.gif)

```
[System.Serializable]
public class Boundary{
    public float xMin, xMax, zMin, zMax;
}

public class PlayerController : MonoBehaviour
{
    private Rigidbody rb;
    public Boundary bounds;
    public float speed;
    public float tilt;

    void Start(){
        rb = GetComponent<Rigidbody>();
    }
    void FixedUpdate()    {
        float moveHori = Input.GetAxis("Horizontal");
        float moveVert = Input.GetAxis("Vertical");

        rb.velocity = new Vector3(moveHori, 0.0f, moveVert);
        rb.velocity *= speed;

        rb.position = new Vector3(
            Mathf.Clamp(rb.position.x, bounds.xMin, bounds.xMax),
            0.0f,
            Mathf.Clamp(rb.position.z, bounds.zMin, bounds.zMax)
        );

        rb.rotation = Quaternion.Euler(
            0.0f,
            0.0f,
            rb.velocity.x * -tilt
        );
    }
}
```

As before, you can get the movement inputs by using Input.GetAxis(). 

### Restricting Movement
Mathf.Clamp() is used to clamp a value within an interval. This is useful if you want to limit movement to within a certain area for example.

### Rotation
Rotation is mostly done using Quaternion.Euler(). This is a new type of object that takes in rotational values for each of x,y, and z axes.

### Serializable
Serializables are a way of bundling similar or related variables together in a class; **WHILE** allowing the Editor to still see and edit those variables.