---
layout: default
title: Day 16
---

# Day 16 Content

## Keeping Score

First, we create an UI element to display the text, as in Day 8.

Then, we add this code to the Controller GameObject.

```
void Start(){
    StartCoroutine(spawnAsteroid());
    score = 0;
    UpdateScore();
}

void UpdateScore(){
    scoreText.text = "Score : " + score.ToString();
}

public void addScore(int addAmount){
    score += addAmount;
    UpdateScore();
}
```

Aside from declaring the variables and linking the GUIText object in the definitions, we'll also need to make a new PUBLIC function called addScore(), so that other scripts can add to the score, without the Game Controller having to explicitly keep track of everything in the scene. This way, objects can report to the Game Controller if neccessary.

Now, we need to tell each Asteroid, which script to report back to when it is destroyed. Add this to the Destroy script, in the Start() function. The reason we can't like the Asteroid Prefab to the Game Controller directly and vice versa, is because only INSTANCES may link to one another.

```
GameObject controlObj = GameObject.FindWithTag("GameController");
if (controlObj != null){
    control = controlObj.GetComponent<SpawnerController>();
}
else{
    control = null;
}
```

Then, when we have a confirmed link, we can call the addScore() function of the linked GameController to add to the score.

```
control.addScore(scoreValue);
```