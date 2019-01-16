---
layout: default
title: Day 14
---

# Day 14 Content

## Using Coroutines

```
IEnumerator spawnAsteroid(){
    while (true){
        float hori = transform.position.x;
        hori += Random.Range(-3,3);
        GameObject ast = Instantiate(asteroid,new Vector3(hori, transform.position.y, transform.position.z), Quaternion.identity) as GameObject;
        Rigidbody astRb = ast.GetComponent<Rigidbody>();
        
        Quaternion rotation = Quaternion.Euler(0,Random.Range(-20f, 20f),0);

        Vector3 heading = ast.transform.position - center.position;
        float distance = heading.magnitude;
        heading = heading / distance;

        astRb.velocity = rotation * heading* -asteroidFallSpeed;

        yield return new WaitForSeconds (spawnDelay + Random.Range(-0.5f, 0.5f));
    }
}

void Start(){
    StartCoroutine(spawnAsteroid());
}
```

Coroutines are a way of implementing multiple threads into each script. The most common use of this is to allow the script to wait for a timer, while still allowing other parts of the script to go on as intended, a.k.a. non locking.