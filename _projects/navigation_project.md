---
layout: distill
title: Learn to navigate within scenes by leveraging object representation and interaction.
description: 
img: assets/img/hae_project.png
importance: 1
category: open
show: true
related_publications: false
date: 2024-19-07 00:00:00 UTC
duration: 3-6 months
type:
    - Short project
authors:
  - name: Hamza Keurti
    url: "mailto:hkeurti@ethz.ch"
    affiliations:
      name: Institute of Neuroinformatics
  - name: Yassine Taoudi-Benchekroun
    url: "mailto:ytaoudi@student.ethz.ch"
    affiliations:
      name: Institute of Neuroinformatics
  - name: Prof. Benjamin Grewe 
    url: "mailto:bgrewe@ethz.ch"
    affiliations:
      name: Institute of Neuroinformatics
toc:
  - name: Background
  - name: Project
  - name: You Are
  - name: You Get
  - name: We Are
  - name: Starting Date and Duration
  - name: Related Works / Preliminary Readings

---

## Background

A hallmark of biological intelligence is the ability to adapt and generalize rapidly to new tasks and environments by composing previously acquired knowledge. This capability is demonstrated in a wide range of tasks, such as landmark-based navigation, where animals leverage spatial relationships between multiple objects to plan routes, estimate their position, and acquire new reference points. 
Navigation, while straightforward for animals, remains an open problem in machine learning research. Learning navigable representations of scenes presents multiple challenges: the agent needs to understand and predict the effects of its actions on its perception (equivariance). In addition, without supervision, the agent does not know the relative distance (pose) to the objects it sees (localization). Finally, as the agent moves, objects may occlude each other or exit the field of view, which constrains the agent as it cannot rely on a single object to situate itself (occlusion). 

We propose a method that specifically solves the problems of pose estimation in novel environments through composing single object representations into a representation of the pose of the agent in the scene. The approach learns equivariant representations of objects which capture how the actions of the agents transform the image it observes. The composition procedure further leverages interaction to compose these single object representations into a coherent map of the scene. The resulting representation can be used to infer the relative pose to all objects in the scene, to predict the effect of actions and to infer the action to perform to navigate from a source view to a goal view.


## Project

We successfully tested the procedure in a simulated 3D environment of simple 3D objects and an agent moving on the ground. The goal of the project would be to show the approach works in settings closer to real-world settings, for 2D and 3D environments. An example setting of interest is a drone navigating a 3D environment. Another aspect of the project is to show the usefulness of the learned representation in performing different tasks. To achieve this, we are interested in training a Reinforcement Learning agent that uses the composed representation as a world model.

## You Are

a MSc student proficient in Python and one Deep Learning framework (although it is expected we work with Pytorch) and with an interest in robotics application (planning, navigation). Previous experience in Reinforcement Learning, OpenAI Gym environments, and Gazebo is preferred. We are generally looking for students interested in embodied autonomous agents, perception and representation learning, and most importantly, someone keen on fast-paced collaborative projects.

## You Get

With a serious commitment, we guarantee you will enjoy a steep learning curve and you will be introduced to more than one hot topic including Object Centric Representations, Simultaneous Localization and Mapping, Group structured Representations. 

## We Are

* Hamza Keurti (hkeurti@ethz.ch): 4th year PhD student. Project lead. He is generally interested in perception from action. He previously developed the Homomorphism AutoEncoder (HAE), published at ICML and earned a best abstract award at the NeurReps 2022 workshop. We use the HAE in this project.

* Yassine T. Benchekroun (ytaoudi@student.ethz.ch): has experience designing and navigating the daily struggles of RL training. Previously worked on generalization in the context of the ARC challenge.

* Professor Benjamin Grewe (bgrewe@ethz.ch): Main supervisor.
(please email everyone when reaching out for the project)

## Starting Date and Duration

Semester project. Can possibly be extended to a thesis. Starting date possible from July 15th, 2024. 

## Related Works / Preliminary Readings

* [1] Stitching Manifolds: under review at NeurIPS 2024; email us for the manuscript.
* [2] Homomorphism Autoencoder: https://arxiv.org/abs/2207.12067
* [3] Vision-based navigation using Deep RL: https://jkulhanek.com/a2cat-vn/
* [4] Gym environment framework: https://gymnasium.farama.org/
* [5] SLAM: https://www.flyability.com/blog/simultaneous-localization-and-mapping

