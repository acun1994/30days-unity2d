---
layout: default
title: Day 10
---

# Day 10 Content

## Creating Shots and Movement

![Day 10 Progress - Space Shooter](/30days-unity2d/images/Day10_1.gif)

Shot Controller

```
private Rigidbody rb;
public float speed;
// Start is called before the first frame update
void Start()
{
    rb = GetComponent<Rigidbody>();
    rb.velocity = transform.forward * speed;
}

// Update is called once per frame
void Update()
{
    if (rb.position.z > 10){
        Destroy(gameObject);
    }
}
```

Player Controller

```
void Update(){
    if (Input.GetButton("Fire1") && Time.time > nextShot){
        nextShot = Time.time + shotDelay;
        Instantiate(shot, shotSpawn.position, shotSpawn.rotation);
    }
}
```
