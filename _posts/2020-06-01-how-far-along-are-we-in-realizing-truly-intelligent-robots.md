---
title: How Far Along Are We in Realizing Truly Intelligent Robots?
tags: [Robotics, AI, Computer Vision, Deep Learning, Reinforcement Learning]
style: fill
color: primary
description: A look at the staggering complexity behind building robots like those shown in science fiction, and an honest assessment of where we stand today.
---

Just have a look at this.

![Enthiran robot fight scene](/assets/post_2/enthiran.gif)

This clip is from an Indian film called "Enthiran" which was released in 2012. The movie is about a scientist who builds a truly intelligent humanoid which is capable of doing all the tasks that a human could. Initially, the robot is programmed with the laws of robotics but later learns to defy those laws and poses a threat to human existence. It was a huge commercial success and went on to receive a number of awards for its VFX, art design etc.

Also check this out.

![I Robot fight scene](/assets/post_2/irobot.gif)

Most of you reading this might be familiar with this clip. It's from a movie called "I Robot" which was released in 2004. This movie is one of the best movies with "robotics" as its core theme.

When I saw both these movies, I was in middle school, and as a kid with absolutely no knowledge about the field of robotics, I was filled with awe throughout the entire duration. I had imagined then, that in another 10 to 15 years, when I grow up, humans would share their world with robots just like how it was shown in these movies. At that exact moment, I didn't have enough evidence to think of the question: *How far along are we in realizing truly intelligent robots?*

Now as this question comes to mind, I honestly just feel like laughing out loud. But for me it is also one of those examples that make me sad about the outlook for AI and Computer Vision in Robotics. What would it take for a robot (which is just basically a computer) — for instance — to fight these enemy robots as shown in the "I Robot" clip above? For the non-STEM folk, I challenge you to think explicitly of all the pieces of knowledge that have to fall in place for it to make sense. Here is my short attempt:

1. The good robot, Sonny, has to analyze the scene in front of it to detect the various objects present in it.
2. Now it recognizes two robots in the scene — probably it used the Mask R-CNN algorithm to perform instance segmentation.
3. Next, Sonny has to determine the exact 6D pose in real world frame, of the enemy robots (X, Y, Z, Θ, ɸ, Ψ) in order to approach them.
4. It has to make a decision as to which robot it has to approach first.
5. It has to execute a series of complex kinematic manoeuvres from its limbs and leg joints in order to provide the necessary thrust to lift itself off the ground.
6. Then in order to punch the bad robot once, the robot has to perform a series of Inverse Kinematics algorithms so as to determine what would be the joint angles of the robot arms.
7. Further there would be a lot of complex dynamics problems and intelligent control algorithms involved in this task.
8. After Sonny has done the above steps to land the first punch on the enemy robot, now it has to defend itself from the counter attack — this is where Reinforcement Learning comes in.
9. Sonny has to make decisive actions based on maximizing positive reward, one of the fundamental principles of Deep RL.

Now for the cherry on the cake, all these steps have to be performed in real time using powerful compute hardware. I could write in length about how each of the above steps work, but that is not the point of this blog.

Movies like these are made purely out of the director's imagination and people who watch the movie tend to often misinterpret the job of roboticists. In fact, any roboticist who is reading this blog might be literally in tears. Non-STEM people who watch such movies are often led into believing that the robots shown in movies are very close to becoming a reality. Our family members and friends tend to ask us when are we going to build the next Sonny. (Yes, I feel you). The purpose of this blog is to give the general audience a brief intuition into how extremely meticulous the job of roboticists is. Building each sub-system of the robot is by itself a tremendous achievement — imagine the complexity of putting it all together to build a humanoid like Sonny.

Truly intelligent humanoids like Sonny or Chitti from Enthiran have the ability to think and act on their own. Yes, Deep Learning comes under the subdivision called "Supervised Learning", where we train our models with existing datasets. But in this case, we use "Unsupervised Learning" where the robot is expected to learn from experience. For instance, when a baby is just starting to walk, it doesn't know how to — however it trips, falls, tries to get up and eventually after some time, it is able to walk. Unsupervised Learning works in a similar way, where our models learn from their mistakes. They have a pre-defined reward function, which runs towards a negative quantity if the robot performs the wrong action and runs towards a positive quantity when the robot performs the desired action. Hence, the optimization algorithm would be defined as "Maximize the reward function". Easier said than done — this sub-division of Machine Learning contains some of the most complicated math that you might've ever seen in your life.

Thinking about the complexity and scale of the problem further, a seemingly unavoidable conclusion for me is that we may also need embodiment, and that the only way to build robots that can interpret scenes like we humans do is to allow them to get exposed to all the years of structured, temporally coherent experience we have, the ability to interact with the world, and some magical active learning/inference architecture that I can barely even imagine. When I think backwards about what it should be capable of, the complexity is simply mind-boggling. I hate to say it but the state of CV, AI and robotics, when we consider this task, and when we think about how we can ever go from here to there — the road ahead is long, uncertain, unclear and foggy. In any case, we are very, very far and this depresses me. We will have to continue innovating. What else is the way forward?
