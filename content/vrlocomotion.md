---
title: "Locomotion in VR"
date: 2021-12-29T17:37:11+01:00
slug: 'homework3'
image: 'images/locomotioninvr.png'
description : "Let's explore some ways to move in Virtual Reality worlds."
disableComments : true 
draft: false
---

There are two main ways with which we can approach locomotion in VR: teleportation or 'free' movement. While the latter is more immersive, it also induces more motion sickness so every locomotion design will contain a trade-off between the two. Today I will propose three of them: one of each type as well as one that combines both in some way.

### 1.The Dash Gun

Teleportation in VR can have two major drawbacks, depending on game design choices. First, having your screen fade to black or cut instantly to another frame can rapidly be immersion-breaking and disorienting. There is no real sense of being rooted in a world with actual physical laws. That's why I would prefer to use blinking, which has a similar concept but rather uses a fast transition between the two states, as if you were propelled at high speed in a particular direction. With enough velocity, a directional blur and a reduced field of vision it should avoid a great deal of motion sickness while still permitting to stay grounded in the world.
Second, teleportation can feel a bit like cheating as you could virtually move with infinite speed or even pass through or over obstacles. In some games that would be unfair, so there should be a way to integrate this into the game mechanics: for instance, blinking should have a *cost* and need a lot of energy.
Introducing the **Dash Gun**, a tool that let's you aim at a target and shoots an energy ray in which you travel at supersonic speed to reach a destination, as illustrated below: 


![Dash Gun](/images/Teleportgun.png "Dash gun") 

The gun needs to be fully charged in order to shoot again and then cannot be spammed. When you press and hold the trigger of the controller (which is the only action needed to use the device), the beam also takes time to load and aim further so you can feel that it takes a lot of energy: the point of this gun is to make such types of instant locomotion feel somewhat grounded in reality.

### 2. The Jetpack

Ever played *Jetpack Joyride*? The mobile phone game where you control this tiny man on a big jetpack that goes up and down at high speed. Well this is what inspired my idea for this type of 'free movement' locomotion, minus the machine guns. My primary goal with this design is to reduce the motion sickness induced when freely roaming a virtual world while still making it interesting to use. I've read (somewhere? but don't quote me on that) that sitting while playing actually reduces the dizziness because of the lesser amount of body movement, not to mention it really is useful when you have a limited playing space. So, if you imagine that your two controllers are the handles of a big jetpack that allows you to sit, you can think of this device as follows:

![Jetpack](/images/jetpack.png "Jetpack") 

Pressing a controller trigger would activate the corresponding thruster, allowing you to go up or rotate (if only one is pressed). You are then able to be propelled forward by leaning your body, but of course you would still move up unless you're capable of bending 90 degrees while sitting. Therefore, another possibility is to activate *hover* mode by pressing another button to maintain your elevation while using smaller boosters (pictured at the back of the jetpack on the above drawing) to be pushed in the direction you want. The entire process of piloting this machine does not require physical effort that could wear you out in the long run and minimizes motion sickness by restricting unecessary movements and velocity. Maybe adding a cockpit to stabilize the player with an UI would also help in that regard.
After consideration, this is the locomotion I am going to present in class!

### 3. Bilocomotion

Now I have thought of something a bit different that would combine both types of locomotion as well as first and third-person PoVs. Let's picture a virtual board game where your player is a pawn that moves across the game board but also needs to perform real-time actions such as fighting or looking around. This aspect of game design could be directly integrated into the method of locomotion used and enable you to break out of first-person view by pressing a button in order to have a global overview of the game world and actually grab your character to place it somewhere else. Then, you can get back into your character and freely roam the world at least to a certain extent (using joysticks or hand movements etc.).

![Bilocomotion](/images/bilocomotion.png "Bilocomotion") 

That way you are free to explore an area without having to move for a long period of time while also having a non game-breaking way of "teleporting". Again, it all comes down to game design choices and how well our type of locomotion fits these choices.