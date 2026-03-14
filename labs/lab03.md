# Lab 03

- Individual Assignment presentation
- Lerp, Animation, Collisions, Audio, Raycasting
- Using GIT and Unity

In today’s class we will explore the several components of Unity3D and learn how to create a
simple game.

Open Unity Hub and create a new 3D project called **lab3**.
Download [lab3.unitypackage](../packages/lab3.unitypackage), go to your Assets section and import it into the project.

## 3.1. Lerp(): Linear Interpolation

Linear interpolation is an important technique to simulate linear movement of objects or linear blending of properties. Linear interpolation can be used on different properties, with different datatypes. Here is one exeample, for 3d vectors:

public static [Vector3](https://docs.unity3d.com/ScriptReference/Vector3.html) [Lerp](https://docs.unity3d.com/ScriptReference/Vector3.Lerp.html) ([Vector3]()https://docs.unity3d.com/ScriptReference/Vector3.html a, [Vector3](https://docs.unity3d.com/ScriptReference/Vector3.html) b, float t);

**Returns:** Vector3 Interpolated value. This value always lies on a line between points a and b.

Check the manual for other variants of Lerp() and other related functions:

- [Vector3 Lerp()](https://docs.unity3d.com/ScriptReference/Vector3.Lerp.html)
- [Mathf.Lerp()](https://docs.unity3d.com/ScriptReference/Mathf.Lerp.html)
- [Quaternion.Slerp()](https://docs.unity3d.com/ScriptReference/Vector3.Slerp.html)
- [Color.Lerp()](https://docs.unity3d.com/ScriptReference/Color.Lerp.html)
- [Material.Lerp()](https://docs.unity3d.com/ScriptReference/Material.Lerp.html)
- [Vector3.MoveTowards()](https://docs.unity3d.com/ScriptReference/Vector3.MoveTowards.html)

Choose the lerpScene.scene in the lab3 project and study the following topics:

- What are the three arguments of the lerp function?
- What are the possible uses of the Linear Interpolation?
- In the two examples how is t calculated and why?
- Why do we use a List of transforms?

Additional Vídeos:
- [Move Objects smoothly using Vector Lerp in Unity](https://www.youtube.com/watch?v=d6BPukJ5QkA)
- [Unity 3d Lerp GameObjects](https://www.youtube.com/watch?v=fIeQG89OOGs&list=WL&index=11&t=284s)
- [10 mins GameDev tips - Quaternions](https://www.youtube.com/watch?v=1yoFjjJRnLY)
- [QUATERNIONS Explained VISUALLY in 381 Seconds](https://www.youtube.com/watch?v=MpyGVvC-13s)

## 3.2. Animation and Animator

In this section we will see an example of an animation using keyframes and a state-machine.

Choose the animatorScene.scene in the lab3 prokect and study the following topics:

- Press Play and press the 'E' key.
- How do we create an animation using the Animation panel?
- How do we create states and transitions in the Animator panel?
- How to create a trigger transition?
- Why are Animations important?

Additional Videos:

- [How to create animations in Unity (Tutorial) by #SyntyStudios](https://www.youtube.com/watch?v=78IrmMtByAU)

## 3.3. onCollisionEnter() and Audio

In this example we will explore how to use the onCollisionEnter event. Please open the collisionScene.scene from the lab3 project.

In this scene we created a Destructible script component. This defines the behaviour of every object that can be destroyed by another object with the tag “Hazzard”. This a standard pattern that you should use in your games. Whenever there is a property that is common between several objects, you should isolate it in a component and reuse code as much as possible.

The Destructible component demonstrates the use of sounds, custom animations and how to instantiate objects in the location of the collision. Study the code and think about the following topics:

- How many objects in the scene are Destructible?
- Which objects have the tag “Hazard”?
- How is the collision detected?
- How is the sound played?

Additional Vídeos:

- [Detecting Collisions (OnCollisionEnter) - Unity Official Tutorials](https://www.youtube.com/watch?v=QRp4V1JTZnM&t=1s)

## 3.4. Raycasting

Raycasting is a useful way to cast a ray and see what objects are intersected. This is useful to place objects, check lines of sight or check direct line collisions.

Open the raycastScene1.scene and experiment with the code:

- Press play and check the #Scene tab.
- Notice the green line in one of the boxes. (If no green line is shown that's probably because you have the Gizmos turned off in the )
- Rotate that box around the Y axis.
- Now change "Mask" in that box’s script from "Nothing" to "Everything".
- Rotate till it hits the other box. Why is it red?
- Analyse the script.
- Uncomment the line where we interact with the hitInfo. Play and check what happens.

Now let’s analyse another example of raycasting. Open the raycastScene2.scene and experiment with the code:

- Check the Unity terrain. Where do we change the material? How do we create a
mountain?
- Play the game.
- Study the script inside the PlaceableObject.
- How do we change its position and rotation?

Additional Videos:
[Raycasting - Unity Official Tutorials](https://www.youtube.com/watch?v=EINgIoTG8D4)
[Introduction to Game Development (E18: raycasting)](https://www.youtube.com/watch?v=fFq5So-UB0E)

## 3.5. Other topics

## 3.6. Using GIT and Unity

