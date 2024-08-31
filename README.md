# Medical Augmented Reality Summer School 2024: Unity 101

## Objective
This Unity exercise will teach you the most important principles of working with **GameObjects**, **Components**, **Materials** and **Scripting**. We will go over the topics of how to use the Unity Editor, set up a basic operating room scene, add some objects to it and create some interactivity.

If you get stuck along the way, there is a exemplary solution in the folder "solution".

## Setup
What you need
*  PC with Unity installed. Version should not really matter for this tutorial, but we recommend Unity 2019.4 LTS or latest LTS version
*  Internet connection
*  about 90min of your time

## Step 0: Setting up
1. You are reading this tutorial, so you were apparently successful in finding the project on the GitHub! If you have never used git before, you can [learn the basics of git in under 10 minutes.](https://www.freecodecamp.org/news/learn-the-basics-of-git-in-under-10-minutes-da548267cc91/) 

## Step 1: Starting a Unity project 
1.  Start the Unity Hub, select **Projects** and click on **New**. Select the **3D** template. Give it some meaningful project name like "Exercise01" and choose any location on your PC that you like, like "C:\Projects".
2.  You should now have an empty Unity project in front of you. On the left you have the **Hierarchy** which shows you the scene graph. On the right you have the **Inspector**, which shows you the properties of the currently selected object (like its position, or any components attached to it), which you can also modify right there. On the bottom you see the contents of the project folder. And in the middle, you see a 3D representation of your scene. If you want to you can rearrange these windows however you want.

<p align="center">
	<img width="80%" src="screenshots/CreateProject02.png">
</p>

## Step 2: Creating a basic scene
1.  Now we can add some simple level geometry. We will create a basic room out of 3D primitives, like cubes and planes. In the **Hierarchy** right click and select **3D Objects > Plane**. Now you have a 10mx10m plane at the center of your world. This should become our operating room floor. Right click the **Plane** in the Hierarchy and rename it to "Floor".
2.  To look at your beautiful new Floor you can change the perspective in the scene view: Use the arrow keys to move the position of your editor camera. If you hold the right mouse button and move the mouse you can change orientation and move around like in a first-person shooter game with the WASD buttons. Scrolling zooms in and out. 
3.  In the same way add some **Cubes** to make the walls. Add one cube to your scene!
4.  A cube primitive by default is 1mx1mx1m in size. Enlarge it by selecting it in the **Hierarchy**, then in the **Inspector** for the **Transform** component set its **Scale** to (10,3,1) to make it 10mx3mx1m. Change its **Position** to put it on the edge of our floor.
5.  Now we can duplicate this wall and move it to the opposing edge: Right click the **Cube** in the **Hierarchy** and select **Duplicate**. Now you can change its **Position** to be at the opposing edge of the "Floor". Because it's a copy of the first **Cube**, its **Scale** is already set appropriately.
6.  Make two more duplicates for the other walls, and move, rotate and/or scale them to be positioned on the remaining two edges.

<p align="center">
	<img width="80%" src="screenshots/CreateRoom01.png">
</p>

## Step 3: Using the camera and play
To be able to see the inside of our operating room, we need to put a Camera object inside of it. By default, our scene already contains an object called **Main Camera**.
1.  Select the **Main Camera** in the **Hierarchy** and change its **Position** to be inside the room.
2.  Now nothing stopping us any more from seeing what we just created live and "in game". The easiest way to test our *game* is to press the **Play** Button on the top of the **Scene View**. It will run the current scene directly in the editor. Now you should see the inside of our (currently very boring) operating room from the perspective of the **Main Camera**.

<p align="center">
	<img width="80%" src="screenshots/Play01.png">
</p>

## Step 4: Creating and Adding Materials
As of now our room looks very boring and not like an OR at all! The easiest way to change this, is to add some nicer materials to the room. Until now all the cubes and plane are rendered in the default material. So, we should create our own.
1.  To create a material, in the **Project** window right click and select **Create** > **Material**. Give it a meaningful name. On the right side in the inspector you can now change all the properties of the material: Albedo describes the base color. You can make the material appear more glossy or rough. Add structure with normal or height maps etc. If you want to create a little bit more special of a material you can even render the material with a different shader, which can have different settings or even create a shader yourself. On the lower right you can see a preview of what your material will look like.
2.  Let's assume we want to make our floor to be made of tiles. You can use the provided [tile texture](https://nextcloud.in.tum.de/index.php/s/Bk2cSgd55eRqfYr). When you drag and drop the image file into your **Assets** folder Unity automatically imports it to be used as a texture. Then you can drag and drop the texture from your **Project** window into the empty field as an albedo texture in your material. Increase the *Tiling* parameter to scale the texture properly.
3.  To assign the material to the floor, simply drag and drop the material from your project view onto your object in the scene view.
4.  Create another material for the walls! Assign it to all your walls. Try to dial in visual properties that you like in the inspector.


<p align="center">
	<img width="80%" src="screenshots/CreateMaterial02.png">
</p>

## Step 5: Loading 3D models
Right now, our scene looks blocky and boring as it is only made of some primitives. We can make it look more interesting by adding some 3D models. Importing them into Unity works just like with textures: Simply put them into the **Assets** folder, Unity will import them for you. Unity can read .fbx, .dae (Collada), .3ds, .dxf, .obj, and .skp and can import proprietary files from the following software: Max, Maya, Blender, Cinema4D, Modo, Lightwave & Cheetah3D, if this software is installed on the computer. Files imported this way are converted into .fbx files by Unity during the import process.

If your 3D model comes in a different scale (millimeters, meters, inches etc.) You can change this scale directly for the 3D model.

We have already collected some [surgery-related assets](https://nextcloud.in.tum.de/index.php/s/AyEWw4r49F2nycn) that you can use. We already converted some of them into *Prefabs* and assigned some materials to them to make their usage a bit easier in Unity.
1.  Choose some 3D models that you like from the ones we provide, copy them into the **Assets** folder and drag and drop the prefab into your scene. By changing their transform on the top right of the **Inspector** place them somewhere where you like them.
2.  If you use 3D models from www.turbosquid.com, www.cadnav.com, www.thingiverse.com etc. you might have to change their scale, fix their normals etc. in the import settings. If you need to modify, convert or fix the models you can for example use the free software [Blender](https://www.blender.org/) or [MeshLab](https://www.meshlab.net/).


## Step 6: Using Scripts
You might have noticed that when you press play, right now you cannot move around the scene. Since this is different for each application, it has to be implemented separately. So let's add some interactivity to our scene and while doing so we can learn something about using scripts in Unity. As a start we would like to move our camera around like in an old-school first-person shooter game.
1.  Start by adding a script component to the **Main Camera** object in your scene. To do this, select the **Main Camera** in the Hierarchy and click **Add Component** > **New Script** in the Inspector. Give it a meaningful name like **KeyboardControl** and hit **Create and Add**. Now this script is attached to the **Main Camera**.
2.  To edit the script click on the small gear icon on the newly added component and select **Edit Script**. This should open Visual Studio (or your source code editor of choice).
3.  Unity uses C# as a scripting language. Game logic is greatly simplified by the helper functions provided by inheriting from the class *MonoBehaviour*. There are several callback functions, most prominently the *Update()* method which is being executed once per frame for each object it is attached to. For now, just copy-paste the script below. It receives button presses of the WASD keys and moves or rotates the object that it is attached to in a way like in an old first-person shooters like DOOM.
4.  If you have a look at the script component, after copy-pasting it in, in the inspector, you can see that there are now two exposed variables (if you don't see them, try clicking somewhere in the Inspector to have unity update the view). By making a variable in the C# code *public* they show up in the inspector and can be modified from the editor without going to the code.
5.  Try it out: Click play, and enjoy going around in your scene with the WASD keys. Change the values of the exposed variables and see the difference it makes.
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class KeyboardControl: MonoBehaviour {

    //as these variables are marked as public they will be visible directly
    //from the editor
    public float rotationSpeed = 100.0f;
    public float movementSpeed = 1.0f;

    // the update callback method is called once every frame
    void Update() {
        if (Input.GetKey( KeyCode.W )) {
            //moving forward
            //we're taking the forward vector to get the current view direction,
            //multiply it with an arbitrary value to change its length and
            //multiply it by the time it took to render the previous to make it
            //independent of the framerate frame.
            //Then we're adding this value to the current position.
            transform.position += this.transform.forward * movementSpeed * Time.deltaTime;
        }
        if (Input.GetKey( KeyCode.S )) {
            //moving backward
            //analogous to moving forward, but in the other direction.
            transform.position += -this.transform.forward * movementSpeed * Time.deltaTime;
        }
        if (Input.GetKey( KeyCode.A )) {
            //rotate left
            //similar to moving forward and backward, but instead of adding
            //something to the position, we're rotating around the up vector.
            transform.Rotate( Vector3.up, -rotationSpeed * Time.deltaTime );
        }
        if (Input.GetKey( KeyCode.D )) {
            //rotate right
            //analogous to rotating left, but in the other direction.
            transform.Rotate( Vector3.up, rotationSpeed * Time.deltaTime );
        }

    }
}
```

## Step 7: Parenting and lighting 
If you have added the 3D model of the OR light to your scene you have noticed, that it is not emitting any light. To change this, we can add a light source to it. Lights can be dynamic and cast shadows on geometry, but if you overdo it, performance might go down (especially on embedded hardware like some head mounted displays).
1. If your scene does not contain an OR light 3D model, add it now! Move it to a position that makes sense.
2. Add a **Spotlight** object to your scene (Right-click in the **Hierarchy** and select **Light** > **Spotlight**).
3. Position the **Spotlight** just below the part of the 3D model where the light comes out.
4. The **Spotlight** and the OR lamp model are not linked yet: If you were to move the lamp to a different position, the light would still be emitted from where you set it up. A powerful way to making a scene more organized and to establish a hierarchy between objects, is to *parent* them to each other: You can simply drag-and-drop the **Spotlight** onto the 3D model of the lamp, which will now show it indented as a child of the parent object. Now if you move the parent around, the child object will follow.
5. The light is not casting any shadows yet. You can change this behavior by changing the **Shadow Type** of the **Light** component. In there you can also change it's **Range**, **Spot Angle** etc. to your liking.

<p align="center">
	<img width="80%" src="screenshots/Lights01.png">
</p>


## Step 8: Physics
With objects, scripts and a camera in your scene you could in theory create everything. But a game engine like Unity is much more powerful. An example of the benefits of using a game engine as opposed to a rendering only engine is the included support for Physics.

Maybe you already noticed that in our game you can pass through the walls. To avoid this, in this example we will add collisions to our camera object.
1. Add a **Sphere Collider** component to the **Main Camera** (**Add Component** > **Physics** > **Sphere Collider**). Its default setting should be fine.
2. Add a **Rigidbody** component to your **Main Camera** (**Add Component** > **Physics** > **Rigidbody**). Set its **Drag** and **Angular Drag** to 100.
3. Try it out in Play mode. Now your camera is not able to pass through the walls anymore.
4. If you also want to have collisions with other object in your Operating Room, you can add collider components to them as well (Box Collider, Sphere Collider etc.) Just make sure to make their dimensions and position match their 3D model.

