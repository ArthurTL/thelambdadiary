---
title: "Building my Jetpack in VR : Part 1"
date: 2022-01-08T14:27:12+01:00
slug: 'lab5'
image: 'images/jetpack_part1.png'
description : 'Or my attempt at implementing a new, non sickness-inducing type of continuous virtual locomotion.'
disableComments : true 
draft: false
---

Of the three locomotion proposals I made in my last post, I found the jetpack the most interesting to actually implement. Using Unity's physics engine, there is something very fun to create and tweak here and I'm curious to know if it is really possible to minimize motion sickness using this setup. So let's start coding !

I'll be using Unity 3D for this project and to port it in VR. But first I'll put my Oculus Quest aside and start creating my basic jetpack functionalities in Unity without thinking about how it'll work in a virtual reality setting. Since most of the controls are button-based, it will be easier to create it independantly and test it on my computer before mapping each action to a button on the VR device. After what I will also add some VR-only functionnalities involving leaning etc.

### 1. The model

I'm starting with the look of my jetpack by creating a simple 3D model using the basic Unity primitives (cylinders, spheres and cubes mainly), and taking care to display the four thrusters and the control joysticks. I then create some custom materials to give it a nice metallic look and some colors and *voilà*, here's the result :

![Jetpack Model](/images/jetpack_model.png "Jetpack Model") 

It is still fairly rough looking but it will serve as a base for what I'm trying to do. There isn't a seat to sit on yet but that will come when I change my player from a capsule to something more realistic. Also I am playing around with the particule system to represent the fire coming out of the thrusters, as you will see in the next videos. This (https://www.youtube.com/watch?v=8j_NhBVYz8o) tutorial shows at 1min20 how to get a pretty decent fire particle effect so I'm basing mine on this!

### 2. The Mechanism

Our jetpack is created, now it's time to make it fly. I'm thinking about using the Physic Engine of Unity to add an upward force to the jetpack when the user presses one button. Actually the jetpack has two thrusters, so each one will be activated by its own button on the controller and will also add a lateral force (that will cancel out when summed if both are pressed). It looks like that in the code :

![Code 1](/images/code_1.png "Code 1") 

As I mentionned I am using keyboard inputs for the moment. This seems to work well for the two main thrusters and the fire particles activate correctly, so I am also doing the same thing for the two additional boosters that are used to move straight forward. And I get this result !

{{< rawhtml >}} 

<video width=100% controls autoplay>
    <source src="/videos/movie_001.mp4" type="video/mp4">
    Your browser does not support the video tag.  
</video>

{{< /rawhtml >}}

Now there are a couple of things that aren't quite right yet. First, because I set each of the thruster to have just enough strength for the jetpack to escape gravity, it really takes off at full speed when both are activated and they sum up. We want to avoid that so either I lower the power of each one individually or I scale the sum of the forces by a factor (like 1.5*(forceLeft+forceRight)). I might go for the latter.

Then, controlling the jetpack is still complicated because it is quite unstable so I want to add the "*hover*" ability to stabilize its altitude. By pressing the spacebar (for now), the user should be able to basically cancel gravity so that it doesn't fall down *but* it's not only that because in this case the slightest action of the thrusters would propel it into the stratosphere without ever slowing down. My solution was to cancel out **all** forces when no button is pressed so that nothing moves, but I noticed that this sudden change of state doesn't look very natural so at the end I settled for this: in 'hover' mode, all velocities (including angular velocity) decrease rapidly over time to reach a rest state. The code looks like this:

![Code 3](/images/code3.png "Code 3") 

Even outside of hover mode I have to decrease angular and lateral velocities otherwise it gets quickly out of hand when a booster is fired. Also I get some issues with the input responses if I don't put my code in the right "Update" or "FixedUpdate" function so I need to be careful. But now activating hover mode looks like this !

{{< rawhtml >}} 

<video width=100% controls autoplay>
    <source src="/videos/movie_002.mp4" type="video/mp4">
    Your browser does not support the video tag.  
</video>

{{< /rawhtml >}}

I just realized I forgot to add some smaller fire effect for when the thrusters enter hover mode, right now it just seems to freeze in the air for no apparent reason.
Some movements seem rather abrupt when I try to fly the jetpack in first person view, I hope it won't make one instantly nauseous when ported in VR. We'll see. For now I'm just playing with parameters such as the thrusters and boosters force and finetuning its piloting.

### 3.Adding details

There are many things I think I can add to make it more realistic or useable. First I would like the user to be able to rotate not only along the vertical axis, but also along the 'roll'/forward one when only one thruster is fired. I'm going to unfreeze rotation along this axis but I don't want to totally allow 6 degrees of freedom as it will start to get complex to handle, not to mention the pilot easily getting stuck upside down. So what I'll add is a way for the jetpack rotation (along x and z axis) to progressively get back to a default 'rest' state when hover mode is activated. Nothing too brutal, just a gentle transition back to normal.

My new hover function looks like this:

![Code 4](/images/code_4.png "Code 4") 

I'm also adding a bit of a downward force when hovering so the jetpack continues to fall slightly while floating.
And that is the result in game view:

{{< rawhtml >}} 

<video width=100% controls autoplay>
    <source src="/videos/movie_004.mp4" type="video/mp4">
    Your browser does not support the video tag.  
</video>

{{< /rawhtml >}}

There is still some tweaking to make to some of the speeds, but overall I like how it looks!
Another thing I tried to implement is some kind of "jittering" when the jetpack goes up to add some realism and make it look like a true engine is doing the work. Unfortunately this can quickly go out of control (it turns out it is really hard to create a realistic movement of this type by increasing or decreasing the y-coordinate every other frame) and I fear this artificial jitter will be very disturbing and disorienting when seen in VR. But I'm thinking that we can take advantage of the Occulus device to reimagine this idea, using vibrations not on the display, but on the controller! So be ready for part 2, where I'll focus on porting my jetpack to VR.

To end this post, this is how the locomotion looks currently with a first person camera attached to the jetpack, now placed into the parkour map!

{{< rawhtml >}} 

<video width=100% controls>
    <source src="/videos/jetpack_demo.mp4" type="video/mp4">
    Your browser does not support the video tag.  
</video>

{{< /rawhtml >}}