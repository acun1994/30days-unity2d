---
layout: default
title: Day 4
---

# Day 4 Content

Continuing the [tutorial](https://unity3d.com/learn/tutorials/s/roll-ball-tutorial) to create a basic game from scratch.

## Physics

For a GameObject to be able to react according to physics, we first need a RigidBody component. 

## Attaching Scripts to GameObjects

Either create a script in the Scripts folder (Project window) and drag it to the GameObject in the Scene Window, or select the desired GameObject in the Scene/Hierearchy window, and Add the script as a Component.

## Scripting

2 functions govern the behaviour of the GameObject. Update(), and FixedUpdate().

Update() is called every time a frame is rendered. So game-specific behaviours should be defined here.

FixedUpdate is called every time a Physics calculation needs to be performed. So Physics-related behaviours should be defined here.

The Start() function on the other hand, is called when a GameObject is instantiated, and only runs once.

You can also declare variables in C# classes. Public variables can be edited using the Unity Editor itself, so you do not have to recompile verything you want to change a value. Private variables are for internal variables that typically will not change much.

## Getting Player Input

```
    float moveHori = Input.GetAxis("Horizontal");
    float moveVert = Input.GetAxis("Vertical");
```

The above code block gets and stores the horizontal and vertical axis tilt values into variables. This method is platform-agnostic; as such, it works with Joystick controls, and WASD on a keyboard.

```
public Rigidbody rb;

    void Start(){
        rb = GetComponent<Rigidbody>();
    }
```

The declaration of a RigidBody tells the game that you wish to interact with the RigidBody of the GameObject. Linking the script to the GameObject's RigidBody component is done as above.


```
    void FixedUpdate(){
        float moveHori = Input.GetAxis("Horizontal");
        float moveVert = Input.GetAxis("Vertical");

        Vector3 mvmt = new Vector3(moveHori, 0.0f, moveVert);

        rb.AddForce(mvmt); 
    }
```

The above code block creates a force on the ball according to our inputs.


# End of Day Progress

![Day 4 Progress - Movable Ball](/30days-unity2d/images/Day4_1.gif)


# Quick Tips

By highlighting a term, and using "CTRL"/"CMD" +  "'" , a browser window will popup with the relevant Unity documentation to that search term.