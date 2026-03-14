# Lab 02

- The marble drop game
- Creating a Basic First-Person Shooter

## 2.1. The marble drop game

Open Unity Hub and create a new 3D project called MarbleDropGame. Download the [marbleDropGame-urp.unitypackage](../packages/MarbleDropGame-urp.unitypackage), go to your Assets section and import it to the project (right click > import package).

Press **PLAY** to run the game.

Explore the Assets folder and try to understand how and why everything works. Open the
scripts to understand how they work and when they are called.

Try to answer the following questions.

### 2.1.1. Physics

- Why is the ball affected by gravity?
<!-- it contains a Rigigbody component with mass and it is set to "Use Gravity" -->
- What happens if you change the inclination of the board?
<!-- it changes the physics of the ball while it is falling. Some inclination values may even allow the ball to escape the board since there is no "glass" to prevent the ball from bouncing away from the board plane.-->
- The ball is a liitle bit bouncy It doesn't feel like being made of solid metal.Where are the properties that control the behaviour of the collisions? Adjust them in a way that resembles a metallic ball hitting wood pins.
<!-- The properties are inside the Rigidbody component of the Sphere object. It may help to increase its mass and also its angular damping coefficient to help keep the ball on the board when it hits the bottom. -->
- How does the ball reset?
<!-- Through the ResetState() method that places the ball in the original position. It gets called when a collision between the ball and the Slot prefab is detected. -->

### 2.1.2. Scene Graph

- Where and how are the table pins created? Can you have a board with a different number of pins easily?
<!-- The pins are created inside the TableScript. Yes, the number of pins can be easily changed. The number of pins is controlled by the public variables Rows and Columns.-->
- In this example we have used the `localPosition` and `localScale` to place and size the instantiated objects. This requires thinking in the **Local Coordinates** of some object (In this case the "Back" of the board). A "messier" approach would be to work in the **World Coordinates**, using `position` and `scale` and eventually `rotation`. The properties `up`, `right` and `forward` are the axes of the  **Local Coordinates** of the object's transform expressed in **World Coordinates**. They form a left-handed coordinate system. The source code has this alternative approach commented for you to compare both approaches.

- How is the table size obtained? Try to adjust the width of all the table delimiters to a
common different value and see what happens when you run the game.
<!-- The table size is extracted from the Meshilter component of the "Back" object. This object provided access to the mesh, its bounds and size (dimensions). -->

### 2.1.3. Game Mechanics

- What mechanism has been used to collect points?
<!-- Points are collected when the ball "collides" with a Slot prefab Sphere Collider. The Slot Sphere Collider is marked as "Is Trigger". When a collision starts, the OnTriggerEnter() method gets called for the object marked with "Is Trigger". The code can be found in the script assigned to the Slot Prefab (Slot Script) -->
- Try turning on the MeshRenderer of the Slot prefab. What happens?
<!-- The slots are shown as cubes. -->
- Switch off the MeshRenderer of the Slot prefab. Press **Play** and, while the game is running, select the Slot instances in the Hierarchy Browser (they should be right at the bottom). What happened?
<!-- The sphere colliders of the slots are now visible. -->
- What is the condition that makes the ball restart?
<!-- When no significant movement has been detected for the ball for 100 consecutive update cycles. -->
- Press **Play**. Now press the **Stats** button on the top right corner of the **Game** Window. How many triangles are in the scene?
<!-- There are around 23k triangles and 27.8 vertices. -->

### 2.1.4. Suggestions for improvement:
-  The score is kind of buggy. When a ball bounces in a slot it may collect points more than
once. Why does it happen? Devise and implement a solution to solve this problem.
- Create a ball that is around 70% of the separation between adjacent pins
- This is already a simulation, but not yet a game. There is no purpose or challenge. The
player has no play in it. Let the player control where the ball is released. You can limit
the position to lie on a single horizontal line that crosses the current starting position.
- Rules are meant to be broken! Or bent at least! Let’s have the possibility to slightly
shake the board.
- The score is not visible. Add a score text message to a GUI layer.
- It would be great if slots were marked with the points assigned to them. A texture
painting the board would do nicely.
- Let’s have a finite number of ball tries per game.

## 2.2. Creating a Basic First-Person Shooter

Open Unity Hub and create a new 3D project called **basicFPS**. Download the [lab2-urp.unitypackage](../packages/lab2-urp.unitypackage), go to your Assets section and import it to the project (right click > import package).

Press **Play** to run the game.
Use the common interface for FPS (**WASD**+**Space**+mouse).
Use **ESC** to unlock the mouse.

### 2.2.1. Scene Graph

Explore the Assets folders. This scene uses trees from the assetstore (converted to the Universal Rendering Pipeline), originally available here:
    [https://assetstore.unity.com/packages/3d/vegetation/trees/free-trees-103208](https://assetstore.unity.com/packages/3d/vegetation/trees/free-trees-103208):

- Create an empty GameObject node with additional trees from the BrokenVector folder.
- Rotate the parent node in the Y axis and observe the position values for each object.

Observe how the red cubes are created using a **prefab**. To create a prefab selec several ojects from the scene and drag them to the Project area:

- Create an additional cube from the prefabs
- Create another object, change its color with an additional material and convert it to a prefab.
- Add several objects of the same prefab type to the scene.

The **Main Camera** is currently a child of the **Player** node `[Pos(0,0,0),Rot(0,0,0)]`. This creates the first person shooter effect. Try these:

- Move the camera so that we can see the player from behind, like in 3rd person games.
- Move the camera to the root of the Scene and point it so that we can see the player and the enemies (thus becoming a regular fixed camera game). Test it!
- Move the camera back to its original position inside the player’s node `[Pos(0,0,0),Rot(0,0,0)]`.

The texture in the ground uses a black and white PNG file called `ground.png`. The color is given by the Material. Try this:

- Change the texture to another created by you. Change the repetition of the texture.

### 2.2.2. Input: Camera movement

As you can see, the camera is located inside the Player node. The Player can be referenced by name or by or by the tag "Player". Since there is only one player, he is in control of the MainScript. Study the MainScript changing the input variables.

- How are the WASD keys mapped iton the script code? See the [Input System documentation](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.19/manual/index.html). Double click the **Player Input** Component of the Player...
- Try changing the initial value of Cursor.lockState in the Start method and see what changes.
<!-- When Locked we have no cursor and the cursor is locket in the middle, no way of clicking on GUI buttons. When Confined, the cursor is visible and we can click on GUI elements. -->
- Why do we need the Time.deltaTime?
<!-- It returns the elapsed time since the last Update() cycle. It allows to program rates of change independent of frame rate. -->
- Try removing the Destroy of the bullets.
<!-- - Change the default values of the parameters. -->

### 2.2.3. Physics: Shooting Bullets

There are several objects that are affected by physics. These objects have two important
components: The **Rigidbody** where you can control the physics and add **Contraints**; The **Collider** component defines what volume will be used to detect collisions.

- How are bullets created inside the **MainScript**?
<!-- Inside the OnAttack() method. -->
- Why does the player have constraints in the rotation? What happens when we remove
them?
<!-- Without the rotation constraints the player will not stand up vertically and fall.-->
- One of the targets is harder to hit, why?
<!-- One of the targets has a smaller Capsule Collider. -->

### 2.2.4. State and Basic GUI

The present UI is very basic and should be used mostly for debug purposes. The state of the game is maintained using variables inside the **MainScript**.

- Try adding bullets while the game is running in the **MainScript** component. What happens when you **Stop** the game?
- Create a toggle that changes a message from “on” to “off” and back when the key ‘O’ is
pressed.

### 2.2.5. Events and Enemies: Targets

The enemies are controlled using the **TargetBehaviour** script. They have a timed event that is triggered at a fixed time, changing directions and firing a ball in the direction of the object with the tag “Player”. Notice anything strange in the `Update()` method?
<!-- The enemies movement should have a speed that is independent of the current frame rate. Need to multiply by Time.deltaTime! -->

### 2.2.6. Challenge (1 week)

Create an improved version of the basicFPS game with:
- Better graphics
- If the ball hits a target, create an explosion sphere in the correct spot.
- Add the concept of 3 lifes to the state.
- Switch between 1st and 3rd person with a button.
- Improve the “AI” of the targets.
- **Extra**: Player rotation follows the mouse position and depends on deltaTime.