# Parenthood
<img src="Images/Logo.png" width="800" />

[Itch.io](https://yrgo-game-creator.itch.io/parenthood)

<br/>

## Game Description
PARENTHOOD explores the need to protect what is innocent and vulnerable. It tells you the story of love and growth, without a single word spoken.
<br/>
### Personal comment
I'm not very proud of the level of programming that i did in this game. However, it was very early in my coding journey and it was essential for learning.
<br/>

# My Contributions During Development

## The child
So there were many challenges with making the movement of the child that will follow you while still acting like a child. With the obstacles there is also a need for situational behaviour depending on which obstacle was ahead. As the first proper project, this ended up being quite challenging.

| A sketch of obstacles | |
|---|---|
|In the beginning, it was expected that the child can move properly and expect help from you, the parent, just like in the sketch made by Axel Björkman. <br/><br/> Some of the obstacles are:<br/> Jump up on ledge with help from parent. <br/> Stop at crushers giving the parent a chance to save the child. <br/> And child running away through a passage giving the parent a limited time to complete a task.| <img src="Images/ParenthoodSketch.png" width="800"/><br/> |

### The Ledges:
|||
|---|---|
| As quite newbie to coding the first idea that came to mind was to use RayCast to decide if the child was close enough to the step and after that use AddForce to make the child leap upwards over and over so that eventually the child clears the stairs. <br/> This of course is very flawed in many ways. The steps in every map varied in size making it difficult to predict the amount of force needed. It also could make the child stuck if it lands too far into each step.| |

| Simpler but better | |
|---|---|
| There were some more versions before this but in the end i decided that simpler was better and laid out points for each landing per each step. There were some minor things that needed fixing aswell. For example, the childs random jumping needed to be stopped before the approach of the steps. | <img src="Images/LedgeJump.gif" width="400"/><br/>|
<details>
<summary>LedgeJumpScript</summary>

```C# 
    private Follow follow;
    private SquishAndStretch squishAndStretch;
    private SpriteRenderer sprite;
    private RaycastHit2D stepRay;

    private int jumpIndex = 0;
    private List<Vector3> childrenPositions = new List<Vector3>();

    [SerializeField] private LayerMask childJumpStepLayer;

    private float maxRaycastDistance = 4f;
    private float jumpDistanceThreshold = 0.3f;

    float stepDistance;
    private bool isJumpInProgress = false;
    public bool smallStepRay = false;

    void Start()
    {

        squishAndStretch = GetComponent<SquishAndStretch>();
        follow = GetComponent<Follow>();
        sprite = GetComponentInChildren<SpriteRenderer>();
    }

    void Update()
    {
        RayCast();

        if (stepRay.collider != null)
        {
            smallStepRay = true;
            follow.canJump = false;
            StartCoroutine(StartProcessCoroutine());
        }
        else
        {
            smallStepRay = false;
        }
    }

    private IEnumerator StartProcessCoroutine()
    {
        yield return new WaitForEndOfFrame(); 
        follow.canJump = false;
        if (!isJumpInProgress)  
        {
            InitiateJump();
        }
    }

    private void RayCast()
    {
        stepRay = Physics2D.Raycast(transform.position, Vector2.right * (sprite.flipX ? -1f : 1f), maxRaycastDistance, childJumpStepLayer);
        stepDistance = Mathf.Abs(stepRay.point.x - transform.position.x);

        if (stepRay.collider != null)
        {
            Transform parentTransform = stepRay.collider.transform;
            childrenPositions.Clear();

            foreach (Transform childTransform in parentTransform)
            {
                Vector3 childPosition = childTransform.position;
                childrenPositions.Add(childPosition);
            }
        }
    }


    private void InitiateJump()
    {
        if (jumpIndex < childrenPositions.Count)
        {
            if (stepDistance < jumpDistanceThreshold && follow.isGrounded)
            {
                Sequence sequence = DOTween.Sequence();
                isJumpInProgress = true; 
                for (int i = 0; i <= childrenPositions.Count; i++)
                {
                    squishAndStretch.enabled = false;
                    sequence.Append(transform.DOJump(childrenPositions[i], 0.15f, 1, 0.4f));
                    jumpIndex++;
                    if (jumpIndex >= childrenPositions.Count)
                    {
                        squishAndStretch.enabled = true;
                        Kill();
                        childrenPositions.Clear();
                        isJumpInProgress = false;
                        jumpIndex = 0;
                    }
                }
            }

        }
        else
        {
            isJumpInProgress = false;
        }
    }


    private void OnDisable()
    {
        Kill();
    }

    private void Kill()
    {
        if (squishAndStretch != null)
        {
            squishAndStretch.enabled = true;
        }
        transform.DOKill();
    }

    private void OnCollisionEnter2D(Collision2D collision)
    {
        if (collision.gameObject.layer == 11 && isJumpInProgress)
        {
            StopCoroutine(StartProcessCoroutine());
            Kill();
            childrenPositions.Clear();
            isJumpInProgress = false;
            jumpIndex = 0;
        }
    }

```
</details>

### Assisted Jumps:
|Same as before||
|---|---|
|Similiar to the steps like before, there was another step for the child where it was too high for it to reach. For the child to make it over, the child needed help from the player/parent. <br/><br/> Before this task, we were taugh what DOTween was which help immensely with the solution. For this task i decided to check if the parent was next to the wall and then getting the top position of the parents collider. With that i made the child "jump" from it's original position to the top of the parent and after that using a bit of AddForce to make it completely over the ledge. | <img src="Images/LedgeJump2.gif" width="800">|










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

