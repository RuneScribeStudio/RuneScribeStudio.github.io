---
title: Movement (Part II)
layout: default
parent: Tutorials
grand_parent: retroPy
---

## Introduction

In this tutorial, we will be continuing our code from the [previous tutorial]({% link docs/retropy/tutorials/t-movement-part-i.md %}) by adding a jumping mechanic for our player.


## Jumping

We will utilize Button A for jumping. In order to jump, we need to give a relatively large value to `player.speed_y` e.g -190. The value is negative since we need the player to move upwards. We will also assign a global variable `player_jumpSpeed`

{% capture code %}
{% highlight python linenos %}
player_jumpSpeed = -190
if rpy.btnADown():
    player.speed_y = player_jumpSpeed
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

Our player can now jump. However, if you continuously press the A Button, the player will be able to jump out of the screen. This is undesirable and we would like to jump once.

To avoid this, we will have to keep track of the player's position and allow him to jump only if he is on the ground by using the code below:

{% capture code %}
{% highlight python linenos %}
    if player.bot_y > groundLevel:
       player.bot_y = groundLevel-1
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

Let's create another global variable `player_isGrounded = False` and set it to `True` when he has hit the ground.

Once everything is implemented, the code should look as follows:

{% capture code %}
{% highlight python linenos %}
player_walkSpeed = 50
player_jumpSpeed = -190
player_isGrounded = False
gAcc = 300
groundLevel = 238

def update(dt):
    global player_isGrounded, player_walkSpeed, player_jumpSpeed, gAcc, groundLevel     
    if rpy.btnLeftDown():
        player.currNdx(0, 1)
        player.speed_x = -player_walkSpeed        
    if rpy.btnRightDown():
        player.currNdx(0, 0)
        player.speed_x = player_walkSpeed
        
    if rpy.btnLeftUp():
        player.speed_x = 0
    if rpy.btnRightUp():
        player.speed_x = 0

    if rpy.btnADown() and player_isGrounded:
        player.speed_y = player_jumpSpeed
        player_isGrounded = False

    player.acc_y = gAcc

    player.update(dt)
    
    if player.bot_y > groundLevel:
       player.bot_y = groundLevel-1
       player_isGrounded = True
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

## Double Jump / Multiple Jumps

To achieve multiple jumps, we need to keep track of a few more states.

{% capture code %}
{% highlight python linenos %}
player_isJumping = False
player_jumpCount = 0
player_jumpMax = 2
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

We need to check if player is Jumping with `player_isJumping`
We need to track how many multiple jump has been made and make sure that it doesn’t exceed the maximum `player_jumpMax`.

{% capture code %}
{% highlight python linenos %}
    if player_isGrounded:
        player.acc_y = 0
        player.speed_y = 0
        player_jumpCount = 0
        player_isJumping = False
        if rpy.btnADown():
            player.speed_y = player_jumpSpeed
            player_jumpCount += 1
            player_isGrounded = False
            player_isJumping = True
    else: # in the air
        player.acc_y = gAcc
        if rpy.btnADown():
            if player_jumpCount < player_jumpMax and player_isJumping:
                player.speed_y = player_jumpSpeed
                player_jumpCount += 1
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

Again, don’t forget to add the globals:
    `global player_isJumping, player_jumpCount, player_jumpMax`

At this point you will be able to do a double jump to increase the number of multiple jumps, just change the value of `player_jumpMax`

Full code:

{% capture code %}
{% highlight python linenos %}
from retroPy import rpy, actor, LoadSprite

p_player = LoadSprite("playerT.rs4")
player = actor(p_player, 112, 112, 0, 0, 0)
player.currNdx(0)

player_walkSpeed = 50
player_jumpSpeed = -190
player_isGrounded = False
player_isJumping = False
player_jumpCount = 0
player_jumpMax = 2

gAcc = 300
groundLevel = 238

def update(dt):
    global player_isGrounded, player_walkSpeed, player_jumpSpeed, gAcc, groundLevel
    global player_isJumping, player_jumpCount, player_jumpMax
    
    if rpy.btnLeftDown():
        player.currNdx(0, 1)
        player.speed_x = -player_walkSpeed        
    if rpy.btnRightDown():
        player.currNdx(0, 0)
        player.speed_x = player_walkSpeed
        
    if rpy.btnLeftUp():
        player.speed_x = 0
    if rpy.btnRightUp():
        player.speed_x = 0

    if player_isGrounded:
        player.acc_y = 0
        player.speed_y = 0
        player_jumpCount = 0
        player_isJumping = False
        if rpy.btnADown():
            player.speed_y = player_jumpSpeed
            player_jumpCount += 1
            player_isGrounded = False
            player_isJumping = True
    else: # in the air
        player.acc_y = gAcc
        if rpy.btnADown():
            if player_jumpCount < player_jumpMax and player_isJumping:
                player.speed_y = player_jumpSpeed
                player_jumpCount += 1
    
    player.update(dt)
    
    if player.bot_y > groundLevel:
       player.bot_y = groundLevel-1
       player_isGrounded = True
        
def draw():
    global player_walkSpeed, gAcc, groundLevel     
    rpy.clear()
    player.draw()
    rpy.hline(0, groundLevel, 240, 7)
    
#=========================================================================
rpy.run(update, draw)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}
