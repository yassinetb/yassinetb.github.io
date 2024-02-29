---
layout: distill
title: Building and ARC task-generator with Reinforcement Learning
description: 
img: assets/img/ARC.png
importance: 1
category: open
show: true
permalink: /arc_project/
url: /arc_project/
related_publications: false
date: 2024-01-01 00:00:00 UTC
duration: 3-6 months
type:
    - Thesis
    - Short project
authors:
  - name: Yassine Taoudi-Benchekroun
    url: "ytaoudi@student.ethz.ch"
    affiliations:
      name: Institute of Neuroinformatics
  - name: Alexander Nedergaard
    url: "anederga@student.ethz.ch"
    affiliations:
      name: Institute of Neuroinformatics
  - name: Prof. Benjamin Grewe 
    url: "bgrewe@ethz.ch"
    affiliations:
      name: Institute of Neuroinformatics
toc:
  - name: Background
  - name: Short project/thesis topic
  - name: Your task
  - name: Your benefits
  - name: Related works / Preliminary readings
  - name: Your profile
  - name: ARC-Group
  - name: Start Date and Duration
  - name: Collaborators

---

## Background

ARC was introduced by François Chollet as a benchmark for measuring generalization capabilities of artificial intelligence systems. It provides a set of tasks that require execution of rules, use of analogies, and understanding of structured relationships - echoing the type of intelligence tests used in human IQ assessments. While humans can perfectly solve all the ARC tasks, state-of-the-art computational performance is at 22% only. Interestingly, these state-of-the-art computational solutions are not learned, but are rather brute force search over a set of of hard-coded “primitive” functions (i.e. Domain Specific Language).

## Short project/thesis topic

In order to develop learning-based solutions, as opposed to more popular brute force Domain-Specific-Language based solutions, our group has developed a set of algorithmic data generators. While these allow us to generate a high number of tasks, they present a set of important shortcomings with regards to diversity and difficulty. To alleviate this, we have started building an RL framework, where an agent must *learn* to generate increasingly difficult and diverse tasks.

## Your task 

In this project, your task will be to continue building and improve the custom ARC-RL environment (with “Gym”). First, you will need to characterize different formulation of the environment in order to reach better performance of the RL generator-agent. This entails choosing specific configurations of the action and observation space that led to better learning – this is a study that has the potential of benefitting the RL community as a whole. Second, we would like to use our transformers-based solvers to ensure task validity and incentivize the RL generator-agent to generate tasks at the limit of the solver’s capacity. If working for a long thesis, adversarial learning between generator-agent and solver can be investigated (once the previous steps have been successfully completed).

## Your benefits 

As we are the first and only ones working on such an approach for ARC generation, we would like to publish a proof-of-concept ASAP, which should realistically be within the next 3-6 months of work; you would be a co-author on this publication, provided enough contribution. Furthermore, in this project, you will learn how to build custom RL environments, which is often the most critical part of any RL problem in real-world applications. In addition to hands-on experience, you will need to reason through the findings from a theoretical standpoint, thereby also learning about the theoretical aspect of RL.

## Related works / Preliminary readings:

- **POET:** <https://arxiv.org/abs/1901.01753>
- **PAIRED**: <https://blog.research.google/2021/03/paired-new-multi-agent-approach-for.html>
- **AlphaTensor**: <https://www.nature.com/articles/s41586-022-05172-4>
- **ARC Original Paper:** <https://arxiv.org/abs/1911.01547>

## Your profile 

We are looking for a student proficient in Python and machine learning. Previous experience in RL is preferred but not required.

## ARC-Group

Become part of a fast-paced and polyvalent team of machine intelligence researchers, incrementally building solutions to the Abstraction and Reasoning Challenge (ARC) <https://www.kaggle.com/competitions/abstraction-and-reasoning-challenge/overview>. This research group, started in September 2022, developed several important building blocks, including custom data-generators, transformer-based solvers, dedicated domain specific language (DSL) and a custom reinforcement learning (RL) environment for data generation.

## Start Date and Duration

Semester project. Can possibly be envisioned as a thesis. Starting date possible from February 1st 2024.

## Collaborators

Yassine Taoudi Benchekroun: [ytaoudi@student.ethz.ch ](mailto:ytaoudi@student.ethz.ch)Alexander Nedergaard: [anederga@student.ethz.ch ](mailto:anederga@student.ethz.ch)Professor Benjamin Grewe: <bgrewe@ethz.ch>

