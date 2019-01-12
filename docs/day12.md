---
layout: default
title: Day 12
---

# Day 12 Content

## Obstacle Generation

![Day 12 Progress - Space Shooter](/30days-unity2d/images/Day12_1.gif)

## Random Rotation

Rotate script on Asteroid Object
```
public float tumble;
private Rigidbody rb;
void Start(){
    rb = GetComponent<Rigidbody>();

    rb.angularVelocity = Random.insideUnitSphere * tumble;     
}
```

## Destroy On Contact

Destroy script on Asteroid Object
```
public GameObject explosion;
public GameObject playerExplosion;
void OnTriggerEnter(Collider other) {
    if (other.tag =="Boundary"){
        return;
    }
    else if (other.tag == "Player"){
        GameObject vfxPlayer = Instantiate(playerExplosion, other.transform.position, other.transform.rotation) as GameObject;
        Destroy(vfxPlayer, 1);
    }
    
    Destroy(other.gameObject);
    Destroy(gameObject);    
    GameObject vfx = Instantiate(explosion, transform.position, transform.rotation) as GameObject;
    Destroy(vfx, 1);
}
```

We keep an instance of the vfx generated so that we can destroy them after the animation is finished. This saves on some memory;