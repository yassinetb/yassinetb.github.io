---
layout: distill
title:  The North Star of My PhD (Part 2)
show: false
category: open
related_publications: false
date: 2024-12-01
toc:
  - name: System 1 and System 2 - A Paradigm for Progress in AI Research
  - name: Can Neural Networks do System 1?
  - subections: 
    - name: Neural Networks are quintessential System 1
    - name: Foundation Models as generalist System 1 models
    - name: What's missing for good system 1 thinking? 
  - name: Can Neural Networks do System 2?
  - subsections:
    - name: Traditional System 2 - Planners And Search
    - name: What's Missing 
  - name: How do we connect System 1 and System 2?
  - subsections:
     - name: Chain-Of-Thought & Test-Time-Training
     - name: 
     - name: Neuro-Symbolic Approaches 
     - name: What does Neuroscience tell us about System 1 and System 2 thinking? 
  - subsections: 
---

You may have heard of System 1 & System 2 thinking paradigms for AI - inspired from Cognitive Science theory. Greg Brockman (OpenAI's CEO) Tweeted this a couple of weeks ago, upon release of OpenAI's latest model "OpenAI o1". So what's System 1 & System 2 thinking? And what can it teach us about the strengths, limitations and research avenues of AI research?  

{% include figure.liquid loading="eager" path="assets/img/north_star_phd_2/brockman" class="img-fluid rounded z-depth-1" %}

## System 1 and System 2 - A Paradigm for Progress in AI Research

In his famous book "Thinking, Fast and Slow", Daniel Kahneman popularized the concepts of *System 1* and *System 2* thinking. *System 1* refers to humans' fast, intuitive, and automatic thought processes that requires little effort or conscious control. It's what drives quick judgments, emotional reactions, instinctive decisions etc... Some typical examples of System 1 thinking are recognizing a friend's face, understanding simple words (e.g. a STOP sign), or driving a car on an empty road. *System 2*, on the other hand, is our slower, more deliberate, and analytical thinking mode. It involves conscious reasoning, complex problem-solving, or long term planning. Examples of System 2 thinking include solving a complex math problem, choosing what flight you'll take to arrive on vacation, or learning a new skill. Both System 1 and System 2 thinking continuously interact with one another. 

This has become a popular perspective of our intelligence, and often used by the Machine Learning community <d-footnote>NeurIPS now even has a "system 2 workshop": https://openreview.net/group?id=NeurIPS.cc/2024/Workshop/Sys2-Reasoning </d-footnote>. Among the many things System 1 thinking is useful for, one thing of particular importance is the *filtering* through tools and memories to tackle a given situation. Imagine yourself unexpectedly being asked about a Calculus problem by a friend. Almost immediately, you are able to filter out the entirety of what you know from Algebra, Physics, Biology, and the rest of your knowledge space, and start thinking about a very very small subset of possible solutions to the problem. It then becomes a slower thinking process (system 2), but on a very small **search space** compared to the entirety of the toolbox that your brain possesses. 

Even more important than reducing the search space, the system 1 filtering allowed you to already have the right **representation** of the problem. You instinctively know that thinking about a mathematics problem is not the same as thinking about a music or cooking problem - the question that your friend asked you has a specific and adapted representation, and start your system 2 thinking process with the right "cognitive organization". Often, you'll realize that you have the wrong representation of the problem, and "need to think about it differently" - this is your System 2 communicating with your system 1. 

In effect, system 1 unconsciously molds your cognition in the right frame to solve daily problems an learn new skills. It just immediately extracts the right tools from your toolbox, without you ever realizing that it did. All you now have to do is think a bit whether to start working with the hammer or the nail - but never were you suggested to use a computer or a watch or a car to put that nail on the wall. 

## Can Neural Networks do System 1?

Yes, but they also are not so good at it. Let's dive in. 

### Neural Networks are quintessential System 1

Neural Networks are essentially "System 1 Thinkers" - in pretty much all their variations and forms. What fundamentally makes Neural Networks *System 1* thinkers can be summed up to a few points: 

* The speed at which they produce a response is *irrespective of the complexity* of what they must process. It's only constrained by the architectural and computational constrains of the neural network - just like "reflexes" in humans are constrained by the time constants of neural cells and other physiological factors. This is also analogous to the concept of "intuition" in humans - however complex a problem may be, we often have immediate intuitions over what the solution might be. This argument is central to the point - this immediate intuition allows to vastly reduce and guide the search space - it's a pre-requisite to be able to solve the problem in reasonable time-span. System 2 thinking cannot function without a robust System 1 thinking. This argument is also central to the point in showing that System 1 thinking is not sufficient: currently, an LLM would take the same amount of time to compute "Hi, how are you doing?" as "26.9\*124^7" - by virtue of it being the same number of input tokens. 
* It is virtually impossible to obtain a "human interpretable" explanation to why NNs ouput response X as opposed to response Y, Z etc... All System 1 processes are indeed unexplained to humans - they just emerge as a function of architecture (native) and weights (trained).
* Neural Networks produce "*latent representation*" of stimuli and states. A good analogy in humans is the set of expectations one has when encountering a situation, as well as the attention on specific details of the situation. Only recognizing a person that comes talk to you at your desk creates a space of expectation and bounds your behaviour in an immediate way. It also channels your attention on that interaction, rather than your other colleague typing on their computer or what's going on outside the window. This is something I find particularly interesting that I also attribute to System 1 thinking. In symbolic terms - it's a matter of shrinking the action space to search over in response to stimuli. 

### Foundation Models as generalist System 1 models

Today, we call Foundation Models these models that have been trained by large corporations/institutions on vast amount of training data. Some are open source, and some are not. Some focus on language, some on vision, and some on time series, and some on everything. Foundation Models can be considered the first general-purpose System 1 sytemts. As Neural Networks, they perfectly fit the aforementioned categorization as System 1 "thinkers". What is novel and interesting in Foundation Models in that spirit, compared to the vast amount of NNs that have been trained and deployed in the past decades, is the diversity of their training data - they are unlike narrow NN which can only navigate specific problems for which they were trained for. They are trained on different kinds of input format, and most importantly, on a *very high* diversity of "topics". This enables them to do "knowledge interpolation" - giving you the impression that they generalize out-of-distribution. This also enables them to quickly adapt to new categories of knowledge that one may want to fine tune them on. The great paper [A critique of Pure Learning](https://www.nature.com/articles/s41467-019-11786-6) argued that biological brains learn very little - they are just incredibly well wired as a result millenia of genetic evolution, and adapt incredibly fast to new environments. One can think of Foundation models as such - models that have been trained on such vast amount of data that their architecture and weights are perfectly suited to learn new tasks quickly.   

Another interesting aspect of these (multi-modal) foundation models <d-footnote>e.g. Llama, which was trained on a wide range of Data modalities </d-footnote> is that they are well suited to give good initial first guesses on practically any kind of request one might give them. Indeed, the training data they have seen is so large that there are very few situations where they cannot at least have an informed guess over what is being asked relates to. Of course, we know countless papers that expose the failure modes of these models, but they always answer on topic. I believe this is analoguous to us having to tackle daily situations without System 2 thinking - we'd be able to be on topic most of the times, but would much too frequently fail to have the right behaviour or give the right answer to the problems we're asked. It's analoguous to us only having intuition, but never slow deliberate thinking.    

### What's missing for good system 1 thinking? 

In short: grounding, and interaction. 

A fundamental aspect of our learning and intelligence, and of our developing intuitions about how things in the world work is through both *exposure* and *interaction* with these things. As I argue in my [previous post](/_posts/2024-10-10-phd-north-star.md), 


Take a strawberry for instance - we see it with our eyes, hold it with our hands, taste it with our tongues. We see it through time growing and changing in its little tree. All of these things allow us to build a good intuition about all the modalities in which strawberries occur - they allow us to build a good "strawberry-model". 

NNs, in the supervised, unsupervised and self-supervised paradigms < d-footnote>omitting RL here </d-footnote>, only observe static data, and never really get to play with the different components of it, therefore crucially limiting their abilities to internalize a good "strawberry-models", or as the community now calls it, "world-models". 

The core idea of "World Models" is to build the capacity to predict how the environment will evolve through agents' interactions and environment's natural evolution. This allows better planning and decision making, that realistically take into account the environment and its dynamism, as opposed to only static disjoint sensory input as done in current ML architecture. 