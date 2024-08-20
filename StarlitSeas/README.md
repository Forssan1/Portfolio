# Starlit Seas
<img src="Images/StarlitSeas1.png" width="800" />

[Itch.io](https://yrgo-game-creator.itch.io/starlit-seas)

<br/>

## Game Description
Starlit Seas is an atmospheric 3D platformer where you play as a lost soul finding their way to heaven with the guidance of whale spirits.

<br/>

# My Contributions During Development

## The Whales' Path
The whales ended up being the most complicated part for me.  
The idea was simple: create a basic "AI" that moves along a route but can still move around the route to feel more natural.

| The Initial Idea | |
|---|---|
| At first, I considered using Unreal Engine's built-in AI! However, there was a problem with this approach. The AI required a nav mesh that only registers potential paths on solid ground. <br/><br/> I couldn't find any previous examples of using the built-in AI in the air either. Having an invisible ground didn't provide the flexibility I wanted, so this approach was quickly ruled out. | <img src="Images/AI.gif" width="600"/><br/>(I didn't have the correct whale model yet) |

| An Alternative | |
|---|---|
| Instead of using actual AI, I decided to use splines to have more control over the whales. To make it feel more natural, I created a system that allowed the whales to switch between different splines/routes seamlessly. Although I tried my best and got it to work 95% of the time, there were enough bugs, too many tasks left, and barely any time to complete it. | <img src="Images/Transfer1.png" width="600"/><br/><img src="Images/Transfer2.png" width="5000"/><br/>(First version of this system) |

| The Final Method | |
|---|---|
| In the end, I decided to keep the whales on splines without any additional features. While this was disappointing, there wasn't enough time to implement more ideas. | <img src="Images/splines.gif" width="600"/><br/>(The whales following a spline)<br/><img src="Images/versions.png" width="600"/><br/>(Different versions of the whales) |

<details>
<summary>List of Smaller Tasks I Completed for the Whales</summary>

1. The blowhole boost that sprays water and launches the player.
2. Animation retargeting.
3. Troubleshooting various collision issues.

</details>

Links to Whale Blueprints:  
[WhaleParent](https://blueprintue.com/blueprint/wnxxdpmd/)  
[WhaleShark](https://blueprintue.com/blueprint/rpadtoge/)  
[BlowholeWhale](https://blueprintue.com/blueprint/ux194k_4/)

## The Intro Cinematic
Due to the high pressure on the artists, I decided to take on the task of creating the intro cinematic myself and experiment with CineCam in Unreal Engine. Although I'm somewhat happy with the result, it's not perfect, and I didn't have time to improve it further.

| Where to Begin? | |
|---|---|
| I wanted to create a first-person POV with realistic movement. Instead of animating every frame by hand, I used an app called CamTrackAR.<br/><br/> This app allowed me to track my phone's movement by placing anchor points on the ground while filming, resulting in somewhat natural head movement. | <img src="Images/CamTrack.png" width="600"/> |

| The Animation | |
|---|---|
| For the animation where the player's hands appear as they wake up in a foreign place, I used a Mixamo animation. However, the skeletal mesh I received from the artist wasn't compatible, so I had to retarget the player's skeletal mesh to the Mixamo skeletal mesh. | <img src="Images/Cinematic1.gif" width="500"/> |

| Blinking | |
|---|---|
| I also wanted to add some blinking effects to make it feel like the player had just woken up. I created a material that looks like eyelids around the camera and applied it to a post-process component attached to the skeletal mesh. Finally, I added a variable that could be adjusted to control the sphere mask, simulating the eyelids closing and opening. | <img src="Images/Blinking.gif" width="600"/> |

| The Final Product | |
|---|---|
| Finally, I put it all together, and it looks like this:<br/><br/>It's a bit longer and better looking in the actual game. | <img src="Images/Cinematic2.gif" width="600"/> |

Links to Relevant Blueprints:  
[BlinkingMaterial](https://blueprintue.com/blueprint/c5bvtwnn/)  
[BlinkingBlueprint](https://blueprintue.com/blueprint/33l218--/)

## Jellyfish Enemies
During development, we realized that some type of obstacle was needed. One of the other programmers had created a jellyfish-like ribbon visual effect, but we weren't sure what to do with it. So I decided to turn it into an enemy.

| The Straightforward Approach | |
|---|---|
| To start, I made the jellyfish follow the player, so that when it got too close, the player would take damage—much like many other enemies in games. | <img src="Images/Eel.gif" width="600"/> |

| Adding Electricity | |
|---|---|
| The flaw with the previous approach was that in a dark, open sky, it became hard to see where the enemies were and how close they were. To make them more visible, I added lightning effects around the jellyfish. | <img src="Images/ElectricEel.gif" width="600"/> |

| Changing It Up | |
|---|---|
| Although the lightning helped, it still didn't fit the game we were trying to make, and the playtesters agreed. To address this, I repurposed the jellyfish into more of an immovable obstacle. Now, they move in a pattern with lightning between each other, creating different shapes depending on how the paths are structured. I also made them spin faster as the player gets closer. | <img src="Images/Jellyfish.gif" width="600"/> |

Links to Relevant Blueprints:  
[Jellyfish_01](https://blueprintue.com/blueprint/a53mtjgq/)  
[JellyfishElectricity](https://blueprintue.com/blueprint/wv68_grw/)  
[Jellyfish_02](https://blueprintue.com/blueprint/e8uqgz5r/)

## List of Smaller Things I Did

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
<img src="Images/Scanning.gif" width="600"/><br/> As a fun little end credits joke, I suggested to the group that we scan everyone in silly poses and put ourselves inside the game using Polycam.<br/> (I'm the one by the computer)
</details>

<details>
<summary>Optimization</summary>
Due to performance issues, I tried to optimize as much as possible by reducing foliage, adjusting culling, tweaking LOD, using Nanite, and so on.
</details>

