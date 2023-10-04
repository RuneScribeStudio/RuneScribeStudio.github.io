---
title: Changing Sprites
layout: default
parent: Tutorials
grand_parent: retroPy
---

## Introduction

In this tutorial, we will be learning how to change our player's sprite to add different animations to our player.


We will start of with this example code shown below:
{% capture code %}
{% highlight python linenos %}
from retroPy import rpy, gameObj, LoadSprite

p_ske_idle_l = LoadSprite("+RPG-rs4/ske-idle-L.rs4")
p_ske_idle_r = LoadSprite("+RPG-rs4/ske-idle-R.rs4")
p_ske_idle_u = LoadSprite("+RPG-rs4/ske-idle-F.rs4")
p_ske_idle_d = LoadSprite("+RPG-rs4/ske-idle-B.rs4")

p_ske_walk_l = LoadSprite("+RPG-rs4/ske-walk-L.rs4")
p_ske_walk_r = LoadSprite("+RPG-rs4/ske-walk-R.rs4")
p_ske_walk_u = LoadSprite("+RPG-rs4/ske-walk-B.rs4")
p_ske_walk_d = LoadSprite("+RPG-rs4/ske-walk-F.rs4")

player = gameObj(p_ske_idle_u, 50, 50, 100, 0, 0, 0)
flip = 180
speed = 100

def draw():
    rpy.clear()
    player.draw()
    
def update(dt):
    
    if rpy.btnLeftDown():
        player.speed_x = -speed
        
    if rpy.btnLeftUp():
        player.speed_x = 0
        
    if rpy.btnRightDown():
        player.speed_x = speed   
        
    if rpy.btnRightUp():
        player.speed_x = 0
        
    if rpy.btnUpDown():
        player.speed_y = -speed  
        
    if rpy.btnUpUp():
        player.speed_y = 0
        
    if rpy.btnDownDown():
        player.speed_y = speed
        
    if rpy.btnDownUp():
        player.speed_y = 0
    
    player.update(dt)

rpy.run(update, draw)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

When running this code, we will have a skeleton player who is able to move around the screen. However, you will notice that the skeleton looks funny when moving around the screen. This is because we have not made him change his sprite based on where he is looking and moving towards.

Using `sprite()`, we are able to change the sprite of the player.

Right below each button, we should have the corresponding sprite so that the player will look and walk in the right direction. Below is an example of making him move and look left:

{% capture code %}
{% highlight python linenos %}
if rpy.btnLeftDown():
        player.speed_x = -speed
        player.sprite(p_ske_walk_l, flip)

if rpy.btnLeftUp():
        player.speed_x = 0
        player.sprite(p_ske_idle_l, flip)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

Once you have implemented this code, your character should move left when you press the left button, and shoukd be idling left when you let go of the left button.

Let's go ahead and implement this for the other buttons. The finished code should look something like this:

{% capture code %}
{% highlight python linenos %}
from retroPy import rpy, gameObj, LoadSprite

p_ske_idle_l = LoadSprite("+RPG-rs4/ske-idle-L.rs4")
p_ske_idle_r = LoadSprite("+RPG-rs4/ske-idle-R.rs4")
p_ske_idle_u = LoadSprite("+RPG-rs4/ske-idle-F.rs4")
p_ske_idle_d = LoadSprite("+RPG-rs4/ske-idle-B.rs4")

p_ske_walk_l = LoadSprite("+RPG-rs4/ske-walk-L.rs4")
p_ske_walk_r = LoadSprite("+RPG-rs4/ske-walk-R.rs4")
p_ske_walk_u = LoadSprite("+RPG-rs4/ske-walk-B.rs4")
p_ske_walk_d = LoadSprite("+RPG-rs4/ske-walk-F.rs4")

player = gameObj(p_ske_idle_u, 50, 50, 100, 0, 0, 0)
flip = 180
speed = 100

def draw():
    rpy.clear()
    player.draw()
    
def update(dt):
    
    if rpy.btnLeftDown():
        player.speed_x = -speed
        player.sprite(p_ske_walk_l, flip)
        
    if rpy.btnLeftUp():
        player.speed_x = 0
        player.sprite(p_ske_idle_l, flip)
        
    if rpy.btnRightDown():
        player.speed_x = speed   
        player.sprite(p_ske_walk_r, flip)
        
    if rpy.btnRightUp():
        player.speed_x = 0
        player.sprite(p_ske_idle_r, flip)
        
    if rpy.btnUpDown():
        player.speed_y = -speed  
        player.sprite(p_ske_walk_u, flip)
        
    if rpy.btnUpUp():
        player.speed_y = 0
        player.sprite(p_ske_idle_d, flip)
        
    if rpy.btnDownDown():
        player.speed_y = speed
        player.sprite(p_ske_walk_d, flip)
        
    if rpy.btnDownUp():
        player.speed_y = 0
        player.sprite(p_ske_idle_u, flip)
    
    player.update(dt)

rpy.run(update, draw)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

Congratulations, we now have a controllable player that moves and acts naturally according to how and where they are moving.




