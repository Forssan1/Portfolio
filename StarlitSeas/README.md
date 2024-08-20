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



Links to Whale blueprints:
[WhaleParent](https://blueprintue.com/blueprint/wnxxdpmd/)
[WhaleShark](https://blueprintue.com/blueprint/rpadtoge/)
[BlowholeWhale](https://blueprintue.com/blueprint/ux194k_4/)
