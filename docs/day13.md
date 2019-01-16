---
layout: default
title: Day 13
---

# Day 13 Content

![Day 13 Progress - Space Shooter](/30days-unity2d/images/Day13_1.gif)

## Randomizing Fall Vectors

Used in a spawner control GameObject
```
public GameObject asteroid;
public Transform center;
public float asteroidFallSpeed;
public float spawnDelay;
private float timeNext;

void Update(){
    if (Time.time > timeNext){
        timeNext += spawnDelay + Random.Range(-0.5f, 0.5f);
        float hori = transform.position.x;
        hori += Random.Range(-3,3);
        GameObject ast = Instantiate(asteroid,new Vector3(hori, transform.position.y, transform.position.z), transform.rotation) as GameObject;
        Rigidbody astRb = ast.GetComponent<Rigidbody>();
        
        Quaternion rotation = Quaternion.Euler(0,Random.Range(-20f, 20f),0);

        Vector3 heading = ast.transform.position - center.position;
        float distance = heading.magnitude;
        heading = heading / distance;

        astRb.velocity = rotation * heading* -asteroidFallSpeed;
    }
}
```

Heading is a marker GameObject. It is used to provide an initial heading for the asteroids, so that they kinda converge in the center of the screen. It is then randomly rotated within a range of +- 20 degrees, to spread them out a bit.

## Spawning Smaller Asteroids on Explosion

Used in the Destroy code of the Asteroid GameObject
```
if (nestLevel > 1){
    List<GameObject> astChild = new List<GameObject>();
    int childs = Random.Range(0,3);
    for (int i = 0; i<childs; i++){
        GameObject ast = Instantiate(gameObject, transform.position + new Vector3(Random.Range(-0.5f, 0.5f), 0, Random.Range(0.0f, -0.5f)), Quaternion.Euler(0,0,0)) as GameObject;
        astChild.Add(ast);
    }

    foreach (GameObject ast in astChild){
        ast.transform.localScale = Vector3.one * Mathf.Pow(0.5f,3 - (nestLevel-1));
        ast.GetComponent<Rigidbody>().velocity = Quaternion.Euler(0,Random.Range(-20f, 20f),0) * GetComponent<Rigidbody>().velocity;
        ast.GetComponent<DestroyOnContact>().nestLevel = nestLevel - 1;
        ast.GetComponent<RandomRotator>().Start();
    }
}
```

You may need to call Start() on certain scripts if you overrode their variables during instantiation.

