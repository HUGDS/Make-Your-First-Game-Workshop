# Welcome to the make your first game workshop!

By the end of this workshop, you should hopefully have created a small platformer game with basic enemies.

The below instructions will guide you through creating this platformer game, feel free to follow them as strictly or loosely as you want!

If at any point you wish to view a completed version of this workshop to reference whilst making your own, a finished version can be found in `Tutorial` &rarr; `Finished` &rarr; `Make-Your-First-Game-Workshop_FINISHED.zip`.

# Index

1. [Downloading the workshop](#1-downloading-the-workshop),

    1.1. [If you do not know your User ID](#11-if-you-do-not-know-your-user-id),

2. [Opening the project](#2-opening-the-project),

3. [Getting to grips with Unity](#3-getting-to-grips-with-unity),

    3.1. [The Hierarchy](#31-the-hierarchy),

    3.2. [Play / Pause](#32-play--pause),

    3.3. [The Inspector](#33-the-inspector),

    3.4. [Scene View](#34-scene-view),

    3.5. [Project View](#35-project-view),

4. [Creating a Player](#4-creating-a-player),

    4.1. [Creating the main Player object](#41-creating-the-main-player-object),

    4.2. [Creating the Player's MonoBehaviour script](#42-creating-the-players-monobehaviour-script),

    4.3. [A brief overview of the structure of a MonoBehaviour script](#43-a-brief-overview-of-the-structure-of-a-monobehaviour-script),

    4.4. [Reading input from the Unity Input System](#44-reading-input-from-the-unity-input-system),

    4.5. [Using input to move the Player](#45-using-the-input-to-move-the-player),

5. [Creating something for the Player to stand on](#5-creating-something-for-the-player-to-stand-on),

    5.1. [Making some ground](#51-making-some-ground),

    5.2. [Extension: Preventing double jumping](#52-extension-preventing-double-jumping),

6. [Creating a Coin](#6-creating-a-coin),

7. [Replacing those boxes with sprites](#7-replacing-those-boxes-with-sprites),

    7.1. [The Ground Sprites](#71-the-ground-sprites),

    7.2. [The Coin Sprites](#72-the-coin-sprites),

8. [Suggested tasks](#8-suggested-tasks),

    8.1. [Prefabs!](#81-prefabs),

    8.2. [Player Animation](#82-player-animation),

    8.3. [More Sound Effects](#83-more-sound-effects),

    8.4. [Score Display](#84-score-display),

    8.5. [Camera Follows Player](#85-camera-follows-player),

    8.6. [An Enemy!](#86-an-enemy),

    8.7. [Power-ups](#87-power-ups),

    8.8. [Win Condition](#88-win-condition).

## 1. Downloading the workshop

To download the project from this GitHub page, first select `Code`, and then `Download ZIP`, as shown below.

![An image showing GitHub's download prompt.](Tutorial/Image/Download/0.webp)

In the download prompt that appears, change the download destination such that it downloads to the folder `C:\Users\XXXXXX\workspace`, where `XXXXXX` is your six digit User ID.

Unlike your documents, downloads, etc folders, this folder exists locally on the machine you are currently working on, with the contents of it being deleted after around three days.

Once downloaded, unzip the downloaded ZIP file and move onto the next section.

### 1.1. If you do not know your User ID

If you do not know your User ID, you can find it out by visiting [this](https://evision.hull.ac.uk/) website, logging in with your student email and then selecting `my Details` from the leftmost menu.

![An image showing the leftmost menu on evision](Tutorial/Image/Download/1.webp)

On the page that shows up, your User ID will be shown in the field titled `User ID`, an example is shown below:

![An image showing an example student's information](Tutorial/Image/Download/2.webp)

## 2. Opening the project

To then open the project, first start by opening the Unity Hub, which can be found via searching for it within the start menu.

Once open, you should be greeted by a screen similar to this one:

![An image showing the Unity Hub with no projects](Tutorial/Image/OpenProject/0.webp)

From here either select `Import projects` or `Add` &rarr; `Add project from disk`.

In the file select prompt that shows up, navigate to the folder that was extracted in the previous step and select that.

![An imge showing the Unity Hub with one project](Tutorial/Image/OpenProject/1.webp)

The Unity Hub should now show the project, from which the project can be clicked on to begin opening it in Unity.

## 3. Getting to grips with Unity

Once the project is open, Unity should look something similar to what is seen below. If you are already familiar with Unity, you are welcome to skip this section as it will simply give a brief overview of the Unity UI.

![An image showing the Unity UI after opening Unity](Tutorial/Image/GripsWithUnity/0.webp)

### 3.1. The Hierarchy

The hierarchy shows a tree view of all GameObjects currently in the scene, along with the scene name, which for this is currently `Untitled`. From the hierarchy, objects can be selected, which will then show up in [the Inspector](#33-the-inspector).

### 3.2. Play / Pause

These two buttons allow you to test your game. Pressing the play button will switch the editor to `Play Mode` and begin running the game, and when pressed during `Play Mode`, the play button will swap the editor back out of `Play Mode`. The pause button pauses `Play Mode`, allowing for you to look at the state of objects in the scene whilst the game is running.

### 3.3. The Inspector

The inspector shows a list of all components currently on the GameObject that is currently selected in [the Hierarchy](#31-the-hierarchy). It also allows for you to change component values on the selected GameObject.

### 3.4. Scene View

The scene view shows the currently active scene, and will swap to the game view when `Play Mode` is started by pressing [the Play](#32-play--pause) button.

### 3.5. Project View

The project view is a directory view of all files in the project. By default it shows the root of the `Assets` folder.

## 4. Creating a Player

### 4.1. Creating the main Player object

Before starting work on a Player, make sure that the currently open scene is `Main`. This scene can be found in [the Project View](#35-project-view) under the path `Assets` &rarr; `Scenes`.

As with every great Unity game, it starts with a cube (in this case a 2D cube, called a square). In [the Hierarchy](#31-the-hierarchy), right click and select `2D Object` &rarr; `Sprites` &rarr; `Square`.

![An image showing the UI flow for creating a square](Tutorial/Image/Player/0.webp)

Once created, you will be able to type out a name for it, name it something appropriate, for this workshop this object will be named `Player`.

As the Player will be our character, they will need to be able to move and collide with other things in the scene. To do this, the Player will need a `Rigidbody 2D` and a `Box Collider 2D`.

To do this, click `Add Component` in [the Inspector](#33-the-inspector) with the Player object selected in [the Hierarchy](#31-the-hierarchy) and then search for `Rigidbody 2D`. Click it when it appears in the search.

![An image showing adding a rigidbody component](Tutorial/Image/Player/1.webp)

Once created, a new component like shown below should appear:

![An image showing the rigidbody component](Tutorial/Image/Player/2.webp)

To prevent the Player from spinning in circles when they start moving later on in the workshop, go to `Constraints` within the Rigidbody 2D and toggle `Freeze Rotation` `Z`.

![An image showing the constraint enabled](Tutorial/Image/Player/3.webp)

Next, follow the same process to add a `Box collider 2D` component to the Player object.

At this point you are welcome to press [the Play button](#32-play--pause) to see what you've made. If you see the Player begin to fall towards the bottom of the screen and then off the screen, congratulations! Otherwise, feel free to ask one of the society execs if you are unsure why this is not happening, or even if you just want any piece of what you've just done explaining in more detail.

### 4.2. Creating the Player's MonoBehaviour script

Next, the movement for the Player will be created. To do this a MonoBehaviour script will need to be created. To do this, go to [the Project View](#35-project-view) and right click, then select `Create` &rarr; `MonoBehaviour Script`. For this workshop, the script will be placed inside a folder named `Script`, which can be created by right clicking in [the Project View](#35-project-view) and selecting `Create` &rarr; `Folder`.

Name the MonoBehaviour script something appropriate, for this tutorial the name `Player_Move` will be used. Once created and named, double click on the new script to open it in Visual Studio.

```csharp
using UnityEngine;

public class Player_Move : MonoBehaviour
{
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

The created script should be the same as shown above. All MonoBehaviour scripts follow the same structure as seen here.

### 4.3. A brief overview of the structure of a MonoBehaviour script

All MonoBehaviour scripts define a single MonoBehaviour class, which follows the format of:

```csharp
public class CLASSNAME : MonoBehaviour
{
...
```

Which means that this class ***is a*** MonoBehaviour class and as such inherits methods and attributes such as the two shown below:

```csharp
...
// Start is called once before the first execution of Update after the MonoBehaviour is created
void Start()
{
    
}

// Update is called once per frame
void Update()
{
    
}
...
```

These two methods are provided by Unity, with the first one `Start` being called on the first frame of the scene being run, and `Update` being called on every subsequent frame.

### 4.4. Reading input from the Unity Input System

Remember when you created the `Rigidbody 2D` and `Box Collider 2D` components on the Player object? Well now you need a way to interact with the `Rididbody 2D` from within the Player's script. To do this, create a variable of type `Rigidbody2D` as shown below and mark it with `[SerializeField]`:

```csharp
public class Player_Move : MonoBehaviour
{
    // Editor Variables
    [SerializeField]
    private Rigidbody2D _rigidBody;
...
```

The tag `[SerializeField]` tells Unity that this variable should be modifiable via the inspector. In fact, let's do that right now. Go back to Unity and on the Player object add the created MonoBehaviour component the same way that the other two components were added (it will show up with the same name that you gave the script).

![An image showing the script being added to the player](Tutorial/Image/Player/4.webp)

As can be seen above, the variable that was added in the script has now appeared as a field on the `Player_Move` component, with its name being a 'pretty-printed' version of the variable name in the script. From here, either drag the `Rigidbody 2D` component onto the `Rigid Body` field or click on the `+` on the field and select `Player` from the menu that appears. The field should now be populated with the Player's rigidbody component.

Next, a way for the Player to detect input should be added. For this workshop, the built-in Unity Input System will be used. Create a pair of variables for holding references to the Input System's built in 'Move' and 'Jump' actions. To modify or view these actions within Unity, navigate to the title bar and select `Edit` &rarr; `Project Settings...` &rarr; `Input System Package`.

```csharp
private Rigidbody2D _rigidBody;

// Private Variables
private InputAction _move;
private InputAction _jump;
...
```

Unity's Input System works with 'Actions' and 'ActionMaps', where a named 'ActionMap' contains a set of named 'Actions', which abstract keyboard / controller / touch input to simple numerical inputs. As an example, the default 'Move' 'Action' within the 'Player' 'ActionMap' returns a 'Vector2' (An X/Y value) from either the left stick on a Gamepad, W,A,S,D, the stick on a Joystick or a 2D axis on an XR controller.

```csharp
void Start()
{
    // Fetch the input action map named "Player"
    InputActionMap map = InputSystem.actions.FindActionMap("Player");

    // Fetch the actions named "Move" and "Jump"
    _move = map.FindAction("Move");
    _jump = map.FindAction("Jump");
}
```

To fetch a reference to these actions, the code above is used, where the `Player` 'ActionMap' is fetched and stored so that it can then be used to fetch the `Move` and `Jump` actions, which are then stored in the variables that were declared earlier.

```csharp
// Update is called once per frame
void Update()
{
    // Poll Move and Jump actions
    Vector2 moveAction = _move.ReadValue<Vector2>();
    bool jumpAction = _jump.WasPressedThisFrame();
}
```

To then read from these actions, the method `ReadValue` is used to return a value of the same type as the action. For the `Move` action this is a `Vector2` as it contains both X and Y components. For the jump action, you only want it to do a jump when the button is pressed rather than held though, and for this Unity provides a built-in method (`WasPressedThisFrame`) that returns either `true` or `false` for whether the button was pressed on this frame.

**Extension:** If you are already quite familiar with C# programming, you may be familiar with the concept of events and observer based programming. Unity's Input System supports this programming paradigm by exposing the `performed` event on the type `InputAction` that is called when the action is performed. Have a go at replacing this per-frame polling with the less expensive event-based input for the `Jump` action.

### 4.5. Using input to move the Player

```csharp
// Update is called once per frame
void Update()
{
    // Poll Move and Jump actions
    Vector2 moveAction = _move.ReadValue<Vector2>();
    bool jumpAction = _jump.WasPressedThisFrame();

    // Do jump
    if (jumpAction)
    {
        // Add force to rigidbody
        _rigidBody.AddForceY(500);
    }
}
```

To then apply movement to the player is fairly simple. Firstly, the `Jump` action can be dealt with by checking if it was pressed this frame, and if it was, the `RigidBody2D` that we stored a reference too earlier can be used to apply an upwards force to the Player via the `AddForceY` method.

```csharp
// Update is called once per frame
void Update()
{
    ...
    // ^ Jump action handling and action polling

    // Do movement
    gameObject.transform.position = new Vector3
        (
            gameObject.transform.position.x + 10 * moveAction.x * Time.deltaTime,
            gameObject.transform.position.y,
            gameObject.transform.position.z
        );
}
```

The same force-based approach could be taken for the Player's movement, however in a platformer game, generally players like to have snappy control over their character's movement, and to do this the `Transform` component of the Player can be directly accessed to modify its position.

In the above code, all that is happening is that the Y and Z co-ordinates of the position are being kept the same, whilst the movement action's left-right value is being used to add or subtract from the Player's X position, to move them left and right.

The `Time.deltaTime` component is a built-in Unity value that returns a value, which if you were to poll every `Update` for a second, would sum to 1. Multiplying by this means that regardless of the framerate that the game is running at, the Player's movement should not become faster or slower.

**Extension:** Have a go at replacing this snappy movement with force-based left-right movement.

## 5. Creating something for the Player to stand on

### 5.1. Making some ground

![An image showing the lack of ground](Tutorial/Image/Ground/0.webp)

If you've been returning to the Unity Editor to run and test your code as you've been working through the prior section, you may have realized that the Player tends to fall into the abyss below the bottom of the screen. In this part of the workshop, ground to stand on will be added.

Similar to creating the player, the ground can be made out of squares. To do this, simply follow the same process as was done for creating the Player object, then drag and scale the square to where you want the ground to be. In the example shown below the square has been placed at (0.06, -4.06) and has been scaled to (20, 1).

![An image showing some ground](Tutorial/Image/Ground/1.webp)

Don't forget to also give the ground a box collider, so that the Player can collide with it!

From this point feel free to tweak the Player's jump height and add more boxes to create platforms. For the rest of this workshop, the ground will look like this:

### 5.2. Extension: Preventing double jumping

You may have noticed that the Player can jump whenever they want, regardless of whether they are on the ground or not. To work around this, the ever-useful Box Collider 2D can be used to add ground detection. To do this, we can add a child to the Player object by selecting the Player and then right clicking on them in [the Hierarchy](#31-the-hierarchy) and selecting `Create Empty`. Name the object something appropriate such as `FloorCheck`.

When an object is a 'child' of another object in Unity, the child object inherits all movement of its parent, maintaining the same offset from its parent as from when it was first parented.

![An image showing FloorCheck being moved](Tutorial/Image/Ground/2.webp)

With the new object selected, navigate to [the Scene View](#34-scene-view) and drag the green arrow such that the object appears slightly below the player. Next we'll add a `Box Collider 2D` to the object.

![An image showing the Box Collider set up](Tutorial/Image/Ground/3.webp)
![An image showing the object ready](Tutorial/Image/Ground/4.webp)

Enable the `Is Trigger` field of the Box Collider and then move and scale it such that the collider is slightly below the bottom of the Player object and spans the width of the Player.

Next make a new MonoBehaviour script and name it something appropriate such as `Player_FloorCheck`. This script will use the built in methods provided from the Box Collider to detect when this object is colliding with something.

```csharp
using UnityEngine;

public class Player_FloorCheck : MonoBehaviour
{
    // Private Variables
    private bool _floored = false;
    private int _collisionCount = 0;

    // Called when something collides with this object
    private void OnTriggerEnter2D(Collider2D collision)
    {
        // Add one to the number of current collisions
        _collisionCount++;

        // Check if we are now on the floor
        AmFloored();
    }
    // Called when something stops colliding with this object
    private void OnTriggerExit2D(Collider2D collision)
    {
        // Subtract one to the number of current collisions
        _collisionCount--;

        // Check if we are still on the floor
        AmFloored();
    }

    // Figures out whether we are standing on anything
    private void AmFloored()
    {
        // Are there any things colliding with this object?
        if (_collisionCount > 0)
        {
            // Then we must be floored
            _floored = true;
        }
        // Otherwise
        else
        {
            // We cannot be on the floor anymore
            _floored = false;
        }
    }

    // Fields
    public bool Floored { get { return _floored; } }
}
```

Paste the above code into the newly created script. Take some time to read over the comments to figure out what the code is doing. If you are unsure about what the code is doing at any point, feel free to reach out to one of the society execs at the workshop, who will be happy to help you with understanding what the code is doing.

Once you feel comfortable that you know what the code is doing, return to Unity and add this newly created script to the object in the same way as the Player's movement script was added.

```csharp
...
private Rigidbody2D _rigidBody;
[SerializeField]
private Player_FloorCheck _floorCheck;

// Private Variables
...
```

Next, return to the Player's movement script in Visual Studio and add an extra field for this newly created script in the same way that the Rigid body was added prior.

Using this, the code to check for jumping can now be changed to read as:

```csharp
// Do jump
if (jumpAction && _floorCheck.Floored)
{
    // Add force to rigidbody
    _rigidBody.AddForceY(500);
}
```

The `&&` means 'and', so both conditions must be true for a jump to be allowed to happen, and the `.Floored` is the field that was created in the other script.

Returning to the Unity editor once more, make sure to drag the `FloorCheck` object onto the new field on the `Player_Move` script. Then click [the Play button](#32-play--pause) to test the floor detection.

## 6. Creating a Coin

As stated prior, all good things in Unity start with a box. So to make a coin, create another square, and to help it stand out, shrink it a little bit.

![An image showing a small box representing a coin](Tutorial/Image/Coin/0.webp)

As with every other object, add a `Box Collider 2D` component to the Coin. Tick the `Is Trigger` field of the `Box Collider 2D`. This field makes the coin not prevent Player movement when the Player collides with the Coin.

![An image showing the state of the coin object](Tutorial/Image/Coin/1.webp)

Add an `Audio Source` component to the Coin as well. This will enable the Coin to play back a 'pickup' sound when picked up. In the `Audio Generator` field click on the '+' and select `coin`. Then disable the `Play On Awake` field.

![An image showing the configured audio source](Tutorial/Image/Coin/2.webp)

Next, create another MonoBehaviour script. Name it something appropriate such as `Coin_Pickup`. Then paste the below code into the script:

```csharp
using UnityEngine;

public class Coin_Pickup : MonoBehaviour
{
    // Editor Variables
    [SerializeField]
    private SpriteRenderer _renderer;
    [SerializeField]
    private AudioSource _playback;

    // Private Variables
    private bool _collected = false;

    // Called when something collides with the coin
    private void OnTriggerEnter2D(Collider2D collision)
    {
        // Ensure that the coin cannot be collected multiple times
        if (_collected) return;

        // Tell audio source to play sound
        _playback.Play();

        // Hide the coin
        _renderer.color = Color.clear;

        // Set the coin to be collected
        _collected = true;
    }
}
```

Take some time to read over the code and see if you can understand what the code is doing.

Similar to the ground, this script uses trigger collisions to detect when something collides with the Coin, and then make the coin transparent along with telling the Audio Source to begin playing the coin pickup sound effect.

If you are still unsure as to how any specific part of this code works, you are welcome to ask one of the execs at the workshop to help you with understanding the code.

![An image showing a completed coin](Tutorial/Image/Coin/3.webp)

Back to Unity, add the new MonoBehaviour script to the Coin object and pass references to the `Sprite Renderer` and `Audio Source` components of the Coin to the script.

Now you should be able to click [the Play button](#32-play--pause) to test the Coin functionality.

**Extension:** Currently the Coin will become collected upon colliding with anything. Can you use Unity's object tag system along with the `collision` object used within the `OnTriggerEnter2D` method to make sure that the Coin only becomes collected when the Player collides with the Coin.

## 7. Replacing those boxes with sprites

### 7.1. The Ground Sprites

Now that there is some functionality in the game, it's about time for some artwork to be added to the game.

To start, take the first 'Ground' object that was made, copy the 'Scale' settings that are currently applied to it and place them in the `Size` field of the object's `Box Collider 2D`, then set the object's scale to (1,1), as seen below:

![An image showing progress being undone](Tutorial/Image/MakeSprites/0.webp)

Fun Fact: The green outline you can see is actually the bounds of the `Box Collider 2D`. The reason you may not have been able to see it before is because a scale of (1,1), which it defaults to, makes it perfectly match the size of the square that we have previously bee scaling.

Now select the `Sprite` field of the `Sprite Renderer` and set it to any tile from the `world_tileset` spritesheet of your choosing. For this workshop `world_tileset_0` will be used.

Once you've done that, select change the `Draw Mode` field of the `Sprite Renderer` from `Simple` to `Tiled` and set the `Width` and `Height` fields to the same values as the `Box Collider 2D` 'Scale' field.

![An image showing the ground correctly done](Tutorial/Image/MakeSprites/1.webp)

Once done, the ground should now tile correctly across the span of the collider.

Feel free to also add sprites to any other ground tiles you have created.

### 7.2. The Coin Sprites

Similar to the ground, change the `Sprite` parameter of the Coin's `Sprite Renderer` to `coin_0`. Now the coin looks like a coin!

However, unlike the Ground, the Coin is going to receive the blessing of being animated. To do this, an `Animator` will be used. Start by adding an `Animator` component to the `Coin` object.

Next, enable the `Animation` window by going to the title bar of the window and selecting `Window` &rarr; `Animation` &rarr; `Animation`. Drag the new window / tab to somewhere comfortable, for this workshop it will be located here:

![An image showing the animation window](Tutorial/Image/MakeSprites/2.webp)

To begin making the Coin's animation, first ensure the Coin is selected in [the Hierarchy](#31-the-hierarchy) and then select the `Create` button found below the text 'To begin animating Coin, create an Animation Clip.'.

In the popup that appears, select a location to store the animation, along with a name for the animation. For this workshop, the animation will be stored at `Assets` &rarr; `Animation` and will be called `CoinAnim`.

**Note:** Ensure that the animation is stored within the Assets folder somewhere, so that it is with all of the other game assets.

![An image showing a blank animation UI](Tutorial/Image/MakeSprites/3.webp)

This is the animation timeline. The time codes at the top of the timeline start at 0:00 and end at 1:00 where 0:00 is 0 seconds and 1:00 is 1 second of animation. To start animating the coin, select `Preview` and then the red 'record' button to the right of the `Preview` button. Now any changes to the Coin object will be recorded as part of the animation.

To start, select the `Sprite` field of the Coin's `Sprite Renderer` and change it to `coin_0`

![An image showing the first frame being set](Tutorial/Image/MakeSprites/4.webp)

Now just drag the timeline marker to the next time code and select the next coin sprite (`coin_1`). Then repeat that until all twelve sprites have been placed on the timeline as seen below:

![The coin done](Tutorial/Image/MakeSprites/5.webp)

With the Coin's sprites laid out, click the 'record' button again to stop recording changes, and feel free to click the 'Play' button to preview the animation.

Now to make the Coin use the animation, navigate to the title bar of the window and select `Window` &rarr; `Animation` &rarr; `Animator`.

![An image showing the animator window](Tutorial/Image/MakeSprites/6.webp)

In the window that pops up, a graph view of the Coin's animator can be seen. This window shows all animations currently on the object, the only one here being `CoinAnim`, along with two conditions:

- `Any State`: This state allows for other animations to point from it, meaning that if the conditions of those 'transitions' become true, the connected animation can be jumped to from any state,
- `Entry`: This state is the starting state of the Animator, the orange line going from it to the `CoinAnim` state means that the Coin will automatically enter the `CoinAnim` animation when the scene starts.

On the left of the winow there are two tabs `Layers` and `Parameters`. For the Coin neither of these are relevant, but the `Parameters` section may be interesting to look at as it allows for variables to be defined within the Animator that can be used to control transitions.

**Extra:** Try right clicking on `Any State` and selecting `Make Transition` to make a transition between the two. Then select the created transition to see its properties in [the Inspector](#33-the-inspector). You can also select animations such as the orange `CoinAnim` to view their properties.

**Congratulations!** You've finished the workshop! You've officially made a simple platformer that you can build on top of.

## 8. Suggested tasks

Below are a list of suggested activities to further what you've created in the workshop. Feel free to have a go at doing any of them!

### 8.1 Prefabs!

You've made some 'components' of a game; a Player and a Coin. Try dragging the Player object or Coin object to [the Project View](#35-project-view) and see what happens! Try dragging the prefab back into the scene and see what happens! Double click on the prefab from [the Project View](#35-project-view), make some changes and see what happens to the two copies of the prefab in the scene! 

### 8.2. Player Animation

With where the workshop left off, the Player is still just a white square. Using what you've learned from making the Ground and the Coin, attempt adding some animation to the Player, such as an Idle animation and Walking animation, that are swapped between when the Player starts and stops walking.

### 8.3. More Sound Effects

Currently only the Coin makes a sound effect when picked up. Have a go at adding extra sounds, such as when the Player jumps (Sound effects are under `Assets` &rarr; `Game Assets` &rarr; `music`).

### 8.4. Score Display

Currently, picking up a coin makes a sound effect, but doesn't really do anything. Have a go at creating a counter on-screen that increments when a Coin is picked up (Hint: A `UI (Canvas)` along with some supporting scripting can be used to achieve this).

### 8.5. Camera Follows Player

The camera is currently static and does not follow the Player as they move, limiting how large the level can be. Try making the camera follow the Player! (Hint: Think back to how the Player's floor detection was made to follow the Player.)

### 8.6. An Enemy!

From what you've learned with moving the Player around and animating the Coin, try adding a slime enemy that either hurts the Player or resets the scene when it collides with the Player.

### 8.7. Power-ups

Have a go at adding a power-up fruit that when touched, has an effect on the Player. One potential effect could be making the Player no longer take damage from the enemy made in [8.6.](#86-an-enemy).

### 8.8. Win Condition

Try adding a win condition (collecting all coins, defeating all enemies, etc), that resets the scene when achieved, or moves to an entirely new scene congratulating the Player on their victory.