---
title: RPG (Role-Playing Game)
layout: default
parent: Challenges
grand_parent: retroPy
---

## RPG (Role-Playing Game)

[Sprites That you might need (click link to download):][1]
<br>RPG-Walls3.rs4
<br>RPG-HB4.rs4
<br>RPG-HB5.rs4
<br>RPG-HT4.rs4
<br>RPG-HT5.rs4
<br>RPG-VL3.rs4
<br>RPG-VL4.rs4
<br>RPG-VL5.rs4
<br>RPG-VR3.rs4
<br>RPG-VR4.rs4

[1]:{{ site.url }}/assets/downloads/RPG_Sprites.zip

### Task 1a (1 pts): Prepare the map


You might want to use the code below to fast start your project.

{% capture code %}
{% highlight python linenos %}
from retroPy import rpy, Rect, gameObj, LoadSprite, LoadSpriteStr
import random

def appendWall(x, y, walltype, ndx = 0):
    t = gameObj(walltype, x*16, y*16, 0, 0, 0)
    t.currNdx(ndx)
    Wall.append(t)
       
def DrawWall():
    appendWall( 2, 0, p_wallHT4, 0)
    appendWall( 1, 1, p_wallVL4, 0)
    appendWall( 1, 0, p_wall, 6) #ctl
    
# Load all rs4 resources
p_wall = LoadSprite("+RPG-rs4/RPG-Walls3.rs4")
p_wallHT4 = LoadSprite("+RPG-rs4/RPG-HT4.rs4")
p_wallHT5 = LoadSprite("+RPG-rs4/RPG-HT5.rs4")
p_wallHB4 = LoadSprite("+RPG-rs4/RPG-HB4.rs4")
p_wallHB5 = LoadSprite("+RPG-rs4/RPG-HB5.rs4")
p_wallVL3 = LoadSprite("+RPG-rs4/RPG-VL3.rs4")
p_wallVL4 = LoadSprite("+RPG-rs4/RPG-VL4.rs4")
p_wallVL5 = LoadSprite("+RPG-rs4/RPG-VL5.rs4")
p_wallVR3 = LoadSprite("+RPG-rs4/RPG-VR3.rs4")
p_wallVR4 = LoadSprite("+RPG-rs4/RPG-VR4.rs4")

Wall = []
DrawWall()

def update(dt):
    pass
    
def draw():
    rpy.clear()

    for w in Wall:
        w.drawCam()

#=================================================================================
rpy.run(update, draw)  
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}


### Task 2 (1 pts): Camera Control

The code below demonstrates the camera controller:

{% capture code %}
{% highlight python linenos %}
cam_x = 0
cam_y = 0
rpy.cam_pos(0,0)

def update(dt):
    global cam_x, cam_y
    
    if rpy.btnRight == 0:
        cam_x +=2
    if rpy.btnLeft == 0:
        cam_x -=2
    if rpy.btnUp == 0:
        cam_y -=2
    if rpy.btnDown == 0:
        cam_y +=2
        
    rpy.cam_pos(cam_x, cam_y)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

### Task 3a (1 pts): Introduce a player into the game

[You might want to use the skeleton. (click link to download):][2]
<br>ske-death-B.rs4
<br>ske-death-F.rs4
<br>ske-death-L.rs4
<br>ske-death-R.rs4
<br>ske-hurt-B.rs4
<br>ske-hurt-F.rs4
<br>ske-hurt-L.rs4
<br>ske-hurt-R.rs4
<br>ske-idle-B.rs4
<br>ske-idle-F.rs4
<br>ske-idle-L.rs4
<br>ske-idle-R.rs4
<br>ske-walk-B.rs4
<br>ske-walk-F.rs4
<br>ske-walk-L.rs4
<br>ske-walk-R.rs4

[2]:{{ site.url }}/assets/downloads/Skeleton_Sprites.zip

### Task 3b (1 pts): Player controller
Control the player movement using the up, down, left and right buttons.

### Task 4 (1 pts): Player Camera controller
Make sure that the camera follow the player (the player is always at the centre of the screen)

### Task 5 (1 pts): Collision detection
Make sure that player does not move past walls.

### Task 6a (1 pts): Introduce items for the player to collect
Collect items

### Task 6b (1 pts): Keep score
Collected items increase score

### Task 7a (1 pts): Enemies

### Task 7b (1 pts): Weapon
Player can shoot projectile

### Task 7c (1 pts): Score for taking down enemies
Keep score

### Task 8 (1 pts): Map
Extend the map

### Task 9 (1 pts): Portal
Create 2 (or more) portals for the player to travel quickly
