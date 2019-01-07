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

Now that you have a basic pickup object, you can turn it into a Prefab for future use. The easiest way to do this is to drag your GameObject from the Hierarchy window into the Project window. It's best to create another folder for your Prefabs, to reduce clutter. Any changes to the Prefab, will also change any instances of the Prefabs in your Project, making changes to all instances easy.

## Actually Pick Up

### Disabling Collisions (Physics)

First we have to disable the collisions on the Pickup objects, to allow our Player gameObject to pass through them and not bounce off. We do this by checking the checkbox of "IsTrigger" in the Collider component of the Pickup GameObjects. By doing this, we are telling the Physics Engine not to do collision calculations, and instead treat the collider as a trigger point.

Then we need to actually do something when the Player gameObject enters the "Trigger" area of the pickups. We add this code into the PlayerController script.

```
void OnTriggerEnter(Collider other){
    if (other.gameObject.CompareTag ("Pickup")){
        //other.gameObject.SetActive (false);
        Destroy(other.gameObject);
    }
}
```

OnTriggerEnter() is called when a collider enters the trigger area of another collider. In our case, it's when the Player "picks up" the Pickup object. We can then tell it to destroy the other GameObject, or to deactivate the other GameObject. It's best to destroy the GameObject if you do not need it for any other calculations down the line; and to merely deactivate it in Debug/testing mode. By destroying GameObjects, you reduce the load on the host machine.

![Day 7 Progress - Picking Up Pickups](/30days-unity2d/images/Day7_2.gif)

### Optimizing Physics Calculations

As it stands now, the Unity Engine is recalculating the volumes of all the pickup GameObjects every frame, as we have added movement to the pickups. The pickups currently use Static Colliders, which are meant for static non-moving objects. We need to convert them to Dynamic Colliders to save resources. We do this by adding a RigidBody component to the pickup GameObjects. Then, enable Kinematics on the pickup GameObject. This prevents the GameObjects from reacting to any Physics forces.