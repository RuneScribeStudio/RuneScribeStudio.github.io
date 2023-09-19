---
title: Arkanoid
layout: default
parent: Challenges
grand_parent: retroPy
---

## Arkanoid

Information on game: 
<br>https://strategywiki.org/wiki/Arkanoid


[Sprites that you might need (click link to download):][1]
<br>Arkanoid-Ball2.rs4
<br>Arkanoid-BlocksGold.rs4
<br>Arkanoid-BlocksSilver.rs4
<br>Arkanoid-BlocksStd-3.rs4
<br>Arkanoid-DoorH.rs4
<br>Arkanoid-PipeCleanH.rs4
<br>Arkanoid-PipeCorner.rs4
<br>Arkanoid-PipeV.rs4
<br>Arkanoid-Pow-Player.rs4
<br>Arkanoid-Vaus32.rs4
<br>Arkanoid-Vaus48.rs4
<br>Arkanoid-VausIcon.rs4

[1]:{{ site.url }}/assets/downloads/Arkanoid_Sprites.zip

### Task 1a (1 pts): Set up the scene

The playing field should be around the rectangle at position (20,y) width = 208 and height = 225.
Draw a rectangle to visually see it on the screen.
Place the player at the bottom of the field as such:


You might want to use the code below to fast start your project.

{% capture code %}
{% highlight python linenos %}
from retroPy import rpy, Rect, gameObj, LoadSprite, LoadSpriteStr
import random

# Load all rs4 resources
p_player = LoadSprite("+Arkanoid-rs4/Arkanoid-Vaus32.rs4")
p_blocks = LoadSprite("+Arkanoid-rs4/Arkanoid-BlocksStd-3.rs4")
p_blocksS = LoadSprite("+Arkanoid-rs4/Arkanoid-BlocksSilver.rs4")
p_blocksG = LoadSprite("+Arkanoid-rs4/Arkanoid-BlocksGold.rs4")
p_wallV = LoadSprite("+Arkanoid-rs4/Arkanoid-PipeV.rs4")
p_wallC = LoadSprite("+Arkanoid-rs4/Arkanoid-PipeCorner.rs4")
p_wallH = LoadSprite("+Arkanoid-rs4/Arkanoid-PipeCleanH.rs4")
p_wallDoor = LoadSprite("+Arkanoid-rs4/Arkanoid-DoorH.rs4")
p_icon = LoadSprite("+Arkanoid-rs4/Arkanoid-VausIcon.rs4")
p_ball = LoadSprite("+Arkanoid-rs4/Arkanoid-Ball2.rs4")

# Init Enviroment
Field_Lx = 16
Field_Ly = 8
Field_W = 208
Field_H = 225
Field_R = Field_Lx + 208
Wall = []

# Init Player
numOfLives = 3
player_pos_y = 224
player_mid_x = Field_Lx+(Field_W//2)-16
player = gameObj(p_player, player_mid_x, player_pos_y, 200, 0, 0)

def update(dt):
    pass

def draw():
    rpy.clear()
    
    player.draw()
    
    rpy.rect(Rect(Field_Lx, Field_Ly, Field_W, Field_H), 8)

#==================================================================================
rpy.run(update, draw)  
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

### Task 1b (1 pts):

Place the bricks at around pos_y = 25.

And place the ball just above the player


### Task 2 (2 pts): Walls

Add the walls around the playing field.


### Task 3 (1 pts): Movements

Extend the script to move the player horizontally using the right and left buttons.  Make sure that to limit the player within the playing field.


### Task 4 (2 pts): Ball Movements

Released at about 30 degrees from the vertical.  Allow the ball to bounce about the playing field.
(Ignore the bricks for now)


### Task 5 (1 pts): Stopping the ball from falling through

Use the player to stop the ball from falling through the bottom.
(Again, ignore the bricks for now)


At this point you might get rid of the red rectangle in draw():
    `rpy.rect(Rect(Field_Lx, Field_Ly, Field_W, Field_H), 8)`


### Task 6 (3 pts): Destroy bricks with ball

Destroy the bricks when the ball collide with the bricks.


### Task 7 (3 pts): Score

Calculate the score obtained when destroying the bricks.
Note:
There are three different kinds of bricks: colored bricks, silver bricks, and gold bricks. Bricks of different colors make up the majority of the walls in each area. They only require one hit to defeat, but they vary in point value from one another.

Silver and Gold bricks, on the other hand, cannot be destroyed with one hit. In fact, Gold bricks cannot be destroyed at all. They are indestructible, and therefore not counted against you towards your attempt to clear an area of bricks. Silver bricks take more than one hit to destroy. In the beginning, they only require two to destroy, but the number of hits it takes to remove them increases by one every eight stages. To calculate the number of points Silver bricks are worth, multiply 50 by the stage number.

### Task 7 (1 pts): Display Score

Display the score obtained by player.


### Task 8 (3 pts): Ball Trajectory

Change the ball trajectory when it hits the side of the player.


### Task 9 (4 pts): Power Up