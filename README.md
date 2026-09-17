# Welcome to the make your first game workshop!

By the end of this workshop, you should hopefully have created a small platformer game with basic enemies.

The below instructions will guide you through creating this platformer game, feel free to follow them as strictly or loosely as you want!

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

    4.3. [A brief overview of the structure of a MonoBehaviour script](#43-a-brief-overview-of-the-structure-of-a-monobehaviour-script)

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

### 4.4. Creating the Player's script functionality

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

## Creating something for the Player to stand on

## Creating an Enemy

## Replacing those boxes with sprites

## Suggested tasks