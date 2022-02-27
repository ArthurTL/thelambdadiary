---
title: "Evaluating my VR locomotion"
date: 2022-01-31T12:03:34+01:00
image: 'images/evaluation.png'
description : 'Time to put my jetpack to the test!'
disableComments : true 
slug: 'homework4'
draft: false
---

I've sent my apk to two classmates and also invited some friends to test my VR jetpack at home, here we will discuss about some results and feedback I've gotten!

### 1. Data and procedure

Before taking any measure, let's take a step back and remind ourselves what are the goals of my VR locomotion design: I've chosen a continous, free type of locomotion to increase **presence**, but also took care of finding a way to reduce **motion sickness** and **fatigue** by some means(such as playing seated). These are three variables that will be evaluated during after testing by a subjective rate ranging from 1 to 10 along with **fun**, which is also one of the main reasons to use these locomotions in VR in the first place :). Speed or maneuverability are other, more practical variables that must be considered as well and will be measured directly with in-game data (time per round and number of coins collected), although they aren't something I am really trying to *maximize*. Indeed, they give us insight about the performance of my locomotion *but* they came secondary in my design choices (a jetpack is not something I would have implemented if I wanted to make something really fast, let alone easy to drive). I am also expecting some kind of noticeable learning curve, meaning I would not expect someone trying the VR jetpack for the first time to get efficient results. This is even intentional: I think it can be part of the fun to learn to master something a bit more challenging than using joystick, and being gratified for practicing. Anyway it won't surprise me if I, as the creator of the locomotion, get largely different results after spending hours tinkering it and get used to its motion than other testers.

The procedure will be the same for everyone : after 2 minutes of exposure to discover and learn the basic commands, each participant will have 10 minutes to finish the VR parkour while collecting coins, after what their in game data will be collected and they will be presented a small questionnaire to assess the 4 criteria mentionned earlier. They will finally be invited to leave any additional feedback as open comments.

### 2. Results

Here are some interesting findings that I had: first, I think it is safe to say that the *presence* is pretty on point. Of all the locomotion presented in class, mine has been evaluated as having the highest amount of it with someone even rating it 10 out of 10, but that seems to come at a huge cost: it is also leading in the sickness category.

![Presence graph](/images/presence.jpg "Presence Graph") 
![Motion sickness graph](/images/sickness.jpg "Motion sickness Graph") 

Turns out that reducing body movements and using a "stable" vehicle type of locomotion isn't enough to prevent the uncomfortable dizziness of being in a simulator. From the feedbacks I've gotten and from my own experience, what really makes it kick in is when you are free-falling from a high place or when you are "rolling" too much, that is when your almost lying horizontal in VR while you are sitting upright in real life. It is these kind of **discontinuities** between R in VR or **high gradients** in position and rotation that should be avoided if we want to have a smooth experience.

Another interesting -but predicted- result is the time it took for participants to finish the parkour, as compared to mine.

![Time graph](/images/time.jpg "Time Graph") 

No real suprise here then, since my own data was taken after I had time to practice and master the locomotion that I designed *myself* (I completed more than a dozen of rounds before that, with gradually better results), so that explains the huge gap. What was less expected however, is the cause their struggle to finish the parkour had on their *enjoyment*.

![Fun graph](/images/fun.jpg "Fun Graph") 

This is due to 1) the motion sickness caused by the initial lack of control of the jetpack and 2) the frustration of not being able to handle it accurately during the parkour (it is important to note that the average number of collected coins is the same than in other's locomotion, meaning that the testers also added some difficulty by taking care of not missing one). They had to use the *hover* mode a lot, which reduces speed (and a bit consequently, *fun*). However, I also think that evaluating the overall enjoyment potential of the jetpack requires more than judging the first 10 minutes of practice, especially when the user hasn't grown accustomed to it OR did not fully understand how it was meant to be used (because the test was done remotely, the instructions weren't as clear as I would have wanted). The reward comes after that, and I can say in all good faith that I am quite having fun swiftly flying from buiding to building in VR !

But I understand that the control are not as intuitive to others as they should be, and by observing the movements that some of my friends made when discovering the jetpack I came up with alternatives. For example, instead of only being able to move the controllers forward or back and turning by having to move only one of them (which is the greatest source of difficulties) one should be able to rotate simply by rotating the controllers in the wanted direction, or tilt them like a joystick (a bit like Rached's *Heliboy*). This would simplify some of the locomotion mechanics while still being a realisitc way to control the engine. What's more, it would also be **less tiring**: indeed my locomotion came up more exhausting than intended, because even if I took care to restrict the amount of movements I didn't realise how taxing it could be for the arms to stay motionless *while* being stretched out. Because of that, the average *fatigue* grade is a **7** which shows that overlooking this aspect (I often did not test it for more than 2-3 minutes when implementing it) has major consequences on playability!

## Conclusion
To sum it up, it seems that these non-(or not sufficiently) intuitive commands is at the core of most of the drawbacks of the jetpack. Even if it would make it less rewarding to master, simplifying them to make them better match what we are accustomed to in current video games would not only reduce tiredness but also help the users reach better results quicker, thus improving their fun, as well as allowing them more control and therefore preventing extreme situations leading to a high amount of sickness (also good for fun).
So, if I am led in the future to improve the model or even implement a similar device, I already know the first thing to fix!