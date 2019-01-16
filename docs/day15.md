---
layout: default
title: Day 15
---

# Day 15 Content

## Adding Audio

There are 3 main components to Audio: Audio Clip, Audio Source, and Audio Listeners.

Audio clips are the actual sound files that are played. Audio Source is the source of the audio being played IN THE SCENE. Audio Listeners are placeholder objects that act as in-scene microphones, should you wish to change the sound's intensity via relative positions.

You can drag and drop audio clips from the projects folder onto Objects in the Inspector window. This will cause Unity to automatically create an Audio Source with the Audio Clip linked to it already.

If you wish for an Audio source to immediately start playing when the associated object is Spawned/Activated, Check the box of Play on Awake.

To programmatically play a sound, use the following snippet. This will play the linked AudioClip by calling the Audio Source component.

```
GetComponent<AudioSource>().Play();
```