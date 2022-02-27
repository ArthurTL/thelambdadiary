---
title: "Building my Jetpack in VR : Part 2"
date: 2022-01-18T11:33:40+01:00
slug: 'lab5-2'
image: 'images/vr.png'
description : "Let's put the actual R in VR."
disableComments : true 
draft: false
---

Now that the main features are implemented in Unity, it is time to experiment with everything the VR offers!

### 1. The controls

All things considered, I think it would be better if controlling the jetpack in VR required more than only pressing two types of triggers. I imagine it would remind the feeling of playing on a computer or a game console (where pressing buttons kind of magically makes things happens) too much, when it should require some "immersive" effort to pilot the engine. Also it would make it less confusing to remember how to turn left or right or which button is associated to which of the four thrusters etc... So I'm thinking to keep the main index triggers to activate the upward thrusters only, while using the boosters to go forward/turn left or right will demand to move the two controllers forward. This is me trying these controls!

{{< rawhtml >}} 

<video width=100% controls autoplay>
    <source src="/videos/demo.mp4" type="video/mp4">
    Your browser does not support the video tag.  
</video>

{{< /rawhtml >}}

Implementing this is a little more complicated than a keyboard to controller button mapping (at least for the boosters) but only demands to detect the hand z-position when the hand trigger is first pressed (which I ultimately used but this one should then stay pressed to signify "I'm holding this handle") then tracking the offset in this direction. 

![Code 5](/images/code_5.png "Code 5") 

I'm also moving the position of the handle object on the jetpack ("*rightHandle*") to go with the hand when it moves to better visualize our action on the jetpack and give some kind of feedback.

Talking about feedback, one thing I really look forward to adding is **haptic feedbacks** to have the controllers vibrate increasingly when the thrusters are fired, which should replace nicely this jittering effect I wanted to have earlier but that didn't work without VR. *Feeling* the engine of the jetpack working each time we press a trigger should add a lot to realism and therefore greatly enhance the presence of my locomotion. 
But first, it's finally time to test how well my jetpack is working in VR!

### 2. Fixin' things

{{< rawhtml >}} 

<video width=100% controls>
    <source src="/videos/fail.mp4" type="video/mp4">
    Your browser does not support the video tag.  
</video>

{{< /rawhtml >}}

Well, my first experience of the VR jetpack was... stomach-turning so to speak. There are many things that don't *feel* the same way when wearing an Occulus. Above all, the speeds matters a lot more : didn't seem like so from the outside, but the thrusters are in fact too powerful and it really feels sickening/disorienting when you are propelled into the air unrealisticly quickly (and even worse when you are experiencing free fall from high up!) or when you rotate around yourself too switfly. So first thing to do is to bring those values **down** a bit so that I can test my locomotion for more than 10 seconds. It demands a lot of tweaking with the parameters and multiplying by some constant here and there while having to rebuild the application each time to test it (as I can't use the occulus link with my laptop), but I think I managed to make it work. Or maybe I've just grown more accustomed to it. We'll have to see during the evaluation phase.

Haptics and sounds will also definitely help to embed some movements in reality and give us a better sense of control over what we are doing (not feel like we are just magically and randomly floating in the air). After searching online a bit, I am relieved to learn that implementing and setting controller vibrations is fairly easy. Here's how I'm doing it:

![Code 6](/images/code_6.png "Code 6") 

And the same thing for the right controller. The "if" statements are here to ensure that I'm not calling the *SetControllerVibration* method each frame (which makes it bug) and deactivate them when nothing is pressed. The frequency of the vibration is different whether the booster or thruster is active, and the amplitude is equal to their intensity (*triggerValue*) clamped between 0 and 1.
I also found some cool thrusters/rocket sound effects that will play whenever a trigger is pressed and stop when everything is released!

![Code 7](/images/code_7.png "Code 7") 

Last thing, I'm also changing some things in the parkour (it is not so adapted for my locomotion). I will move some coins up to add a bit of verticality and let the player get the most out of the jetpack's capabilities. Why having a cool jetpack if it is not to go high up in the air and fly like a bird?
I'm also 

{{< rawhtml >}} 

<video width=100% controls>
    <source src="/videos/win.mp4" type="video/mp4">
    Your browser does not support the video tag.  
</video>

{{< /rawhtml >}}