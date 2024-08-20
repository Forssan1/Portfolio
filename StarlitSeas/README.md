# Starlit Seas
<img src="Images/StarlitSeas1.png" width = 800 />

 [Itch.io](https://yrgo-game-creator.itch.io/starlit-seas)

<br/>

## Game description
Starlit Seas is a atmospheric 3D platformer where you play as a lost soul finding their way up to heaven with the guidance of whale spirits.

<br/>

# My contributions during development

## The whales path
The whales ended up being the most complicated part for me.
<br/> 
The idea is simple. A simple "AI" that moves along a route 
<br/> 
but can still move around said routes to make it feel natural.
<br/> 


|The initial idea|       |
|------|------|
|At the beginning the initial thought was the Unreal Engines built in AI!<br/>There was a problem with this. The AI required a nav mesh that only registers the potential path on solid ground. <br/><br/>I didn't manage to find any previous example of the built in Ai in the air either. <br/> Having a invisible ground instead didn't give the flexibilty that i wanted either.|<img src="Images/AI.gif" width="600"/><br/> (i didn't have the correct whale model yet)|
|An alternative|       | 
|Instead of using actual AI, i decided to use splines to have more control over the whales.<br/> To make it more natural feeling i decided to make a system so that the whales could switch between different<br/> splines/routes seamlessly. Although i tried my best and got it to work 95% of times, there were enough bugs, <br/> too many tasks left and barely any time to complete it.<br/>| <img src="Images/Transfer1.png" width="600"/><br/>  <img src="Images/Transfer2.png" width="600"/><br/>(first version of this system)|
|The final method|       |
|In the end i decided to just keep the whales on splines without anything extra added. <br/> There were many more smaller ideas i tried to implement but none added anything substantial. <br/> While this is disappointing of course, there wasn't enough time.|<img src="Images/splines.gif" width="600"/><br/>(The whales following a splines)<img src="Images/versions.png" width="600"/><br/>(the amount of different versions of whales)|

<details>

<summary>List of smaller things i did on the whales</summary>

1. The blowhole boost that sprays water that also launches the player

2. Animation retargeting

3. Lots of collision troubleshooting


</details>

Links to Whale blueprints:
[WhaleParent](https://blueprintue.com/blueprint/wnxxdpmd/)
[WhaleShark](https://blueprintue.com/blueprint/rpadtoge/)
[BlowholeWhale](https://blueprintue.com/blueprint/ux194k_4/)


## 




## The Intro cinematic
Due to high pressure that was on the artist already i decided
<br/> 
to take the task upon myself and experiment with the cinecam in UE.
<br/> 
Although i'm somewhat happy with the result, it's not perfect and i
<br/> 
didn't have time to make it much better
<br/> 


|Where to begin?|       |
|------|------|
|I wanted to make the first person POV have realistic movement.<br/>And instead of animating every frame by hand, i found this app called CamTrackAR<br/><br/> This app made it so that i could track the movement of my phone by placing anchor points along the ground when filming leading to somewhat natural head movement. |<img src="Images/CamTrack.png" width="600"/>|
|The Animation|       | 
|As for the animation where i wanted the hands to show as the player wakes up in a foreign place, i took a mixamo animation. The Skeletal mesh i got from the artist wasn't compatible though so i had to retarget the player SM to the mixamo SM.| <img src="Images/Cinematic1.gif" width="500"/><br/>  |       |
|Blinking|       | 
|I also wanted to add some blinking so that it really feels like you've just woken up. I made a material that looks like the eyelids around the camera and applied it to a post process component that was attached to the skeletal mesh. Finally i added a variable that i could change wherever that changed the sphere mask making it seem as if the eyelids closed and opened.|<img src="Images/Blinking.gif" width="600"/><br/>|
|The Final Product|       | 
|Finally i put it all together and it looks like this: <br/> <br/>It's a bit longer and better looking in the actual game.|<img src="Images/Cinematic2.gif" width="600"/><br/>|

Links to relevant blueprints:
[BlinkingMaterial](https://blueprintue.com/blueprint/c5bvtwnn/)
[BlinkingBlueprint](https://blueprintue.com/blueprint/33l218--/)

##


## Jellyfish Enemies
During development we realised that some type of obstacle is needed.
<br/> 
One of the other programmers had made a jellyfish looking ribbon visual effect
<br/> 
but we weren't sure what to do with it. So i decided to take it upon myself 
<br/> 
to make an enemy out of it.
<br/> 


|The straight forward approach|       |
|------|------|
|To begin with i simply wanted to try to make the jellyfish just follow you so that when it gets too close the player takes damage much like many other enemies in games. |<img src="Images/Eel.gif" width="600"/>|
|Adding electricity|       | 
|The flaw with the previous method was that in a dark open sky it started getting quite hard to see where the enemies are and how close they actually were. To try to make them more visible i decided to add lightning around the jellyfish.| <img src="Images/ElectricEel.gif" width="600"/><br/>  |       |
|Changing it up|       | 
|Although the lightning did help it still didn't feel like it fit into the game we were trying to make and the play testers agreed. To combat this, instead of making a sort of approaching enemy, i decided to recycle the jellyfish into more of a immovable obstacle instead. Now they move in a pattern with lightning between each other making different type of shapes depending on how i structure the paths. I also added so that they spin faster the closer you get.|<img src="Images/Jellyfish.gif" width="600"/><br/>|



Links to relevant blueprints:
[Jellyfish_01](https://blueprintue.com/blueprint/a53mtjgq/)
[JellyfishElectricity](https://blueprintue.com/blueprint/wv68_grw/)
[Jellyfish_02](https://blueprintue.com/blueprint/e8uqgz5r/)

##

## List of smaller things i did
<details>
<summary>Boost Ring</summary>
<img src="Images/BoostRing.gif" width="600"/><br/>
</details>

<details>
<summary>Fog</summary>
<img src="Images/Fog.gif" width="600"/><br/>
</details>

<details>
<summary>Scanning</summary>
<img src="Images/Scanning.gif" width="600"/><br/> As a fun little end credits joke i suggested to the group to scan <br/> everyone in dumb poses and put ourselves inside the game using polycam <br/> (I'm the one by the computer)
</details>

<details>
<summary>Omptimization</summary>

due to lack of perfomance i tried to optimize as much as possible with<br/>foliage reduction, culling, LOD, nanite and so on.
</details>

