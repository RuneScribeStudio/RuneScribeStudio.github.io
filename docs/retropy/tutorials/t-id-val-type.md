---
title: Utilizing ID, VAL & TYPE
layout: default
parent: Tutorials
grand_parent: retroPy
---

## Introduction

In this tutorial, we will be learning how to utilize id, val and type while working on retroPy. This will allow us to give game objects different/unique identities that we can call or compare to when doing calculations or checks. Please note that as this tutorial is covering solely ID/VAL/TYPE, it is recommended that you know the basics of retroPy so that the example codes we start with are more comprehensible to you.

We will start off this tutorial with this code below:
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

p_wall2 = LoadSprite("+RPG-rs4/RPG-Walls2.rs4")
p_wall3 = LoadSprite("+RPG-rs4/RPG-Walls3.rs4")

player = gameObj(p_ske_idle_u, 50, 50, 100, 0, 0, 0)
flip = 180
speed = 100

Blocks = []
Blocks.append(gameObj(p_wall2, 20, 20, 0, 0, 0, 0))


def draw():
    rpy.clear()
    
    player.draw()
    for b in Blocks:
        b.draw()
    
cr = 0
def update(dt):
    global cr
    
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
        
    for b in Blocks:
        if player.collider(b):
            print("normal block")
    
    player.update(dt)
    for b in Blocks:
        b.update(dt)

rpy.run(update, draw)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

This code gives us a controllable player and a block on the screen. When controlling our player to move towards the block, our Thonny SHELL will display the text "normal block" when our player collides with the block.

Now lets say we would like our game to have multiple blocks, some of which have unique properties (for example, colliding with a certain block will damage you). Let us create another block but this time we will give it an id, and append it to our **Blocks** list.

{% capture code %}
{% highlight python linenos %}
b_temp = gameObj(p_wall3, 20, 80, 0, 0, 0, 0)
b_temp.id(1)
Blocks.append(b_temp)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

This creates a new block on our screen with an id of 1. Now when refering to this block specifically when we do any coding to our **Blocks** list.

An easy test is to modify the collider code such that the player will receive a different text in the Thonny SHELL when colliding with a block that has an id of 1.
{% capture code %}
{% highlight python linenos %}
for b in Blocks:
    if player.collider(b):
        if b.id() == 1:
            print("special block")
        else:
            print("normal block")
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

Our final code should be similar to the code shown below:
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

p_wall2 = LoadSprite("+RPG-rs4/RPG-Walls2.rs4")
p_wall3 = LoadSprite("+RPG-rs4/RPG-Walls3.rs4")

player = gameObj(p_ske_idle_u, 50, 50, 100, 0, 0, 0)
flip = 180
speed = 100

Blocks = []
Blocks.append(gameObj(p_wall2, 20, 20, 0, 0, 0, 0))
b_temp = gameObj(p_wall3, 20, 80, 0, 0, 0, 0)
b_temp.id(1)
Blocks.append(b_temp)

def draw():
    rpy.clear()
    
    player.draw()
    for b in Blocks:
        b.draw()
    
cr = 0
def update(dt):
    global cr
    
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
        
    for b in Blocks:
        if player.collider(b):
            if b.id() == 1:
                print("special block")
            else:
                print("normal block")
    
    player.update(dt)
    for b in Blocks:
        b.update(dt)

rpy.run(update, draw)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}