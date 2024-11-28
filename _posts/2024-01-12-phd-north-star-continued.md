---
layout: distill
title:  The North Star of My PhD (Part 2)
show: false
category: open
related_publications: false
date: 2024-11-26
toc:
  - name: System 1 and System 2 - A Paradigm for Progress in AI Research
  - name: Can Neural Networks do System 1?
  - subsections: 
    - name: Neural Networks are quintessential System 1
    - name: Foundation Models as generalist System 1 models
    - name: What's missing for good system 1 thinking? 
  - name: Can Neural Networks do System 2?
  - subsections:
    - name: Traditional System 2 - Planners And Search
    - name: What's Missing 
  - name: How do we connect System 1 and System 2?
  - subsections:
     - name: Chain-Of-Thought and Test-Time-Training
     - name: Neuro-Symbolic Approaches 
     - name: What does Neuroscience tell us about System 1 and System 2 thinking? 
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
* It is virtually impossible to obtain a "human interpretable" explanation to why NNs output response X as opposed to response Y, Z etc... All System 1 processes are indeed unexplained to humans - they just emerge as a function of architecture (native) and weights (trained).
* Neural Networks produce "*latent representation*" of stimuli and states. A good analogy in humans is the set of expectations one has when encountering a situation, as well as the attention on specific details of the situation. Only recognizing a person that comes talk to you at your desk creates a space of expectation and bounds your behavior in an immediate way. It also channels your attention on that interaction, rather than your other colleague typing on their computer or what's going on outside the window. This is something I find particularly interesting that I also attribute to System 1 thinking. In symbolic terms - it's a matter of shrinking the action space to search over in response to stimuli. 

### Foundation Models as generalist System 1 models

*Foundation Models* are models that have been trained by large corporations/institutions on vast amount of training data. Some are open source, and some are not. Some focus on language, some on vision, and some on time series, and some on everything. Foundation Models can be considered the first general-purpose System 1 models. As Neural Networks, they perfectly fit the aforementioned categorization as System 1 models. What is novel and interesting in Foundation Models in that spirit, compared to the vast amount of NNs that have been trained and deployed in the past decades, is the diversity of their training data - they are unlike narrow NN which can only navigate specific problems for which they were trained for. They are trained on different kinds of input format, and most importantly, on a *very high* diversity of "topics". This enables them to do *in-context learning* and *knowledge interpolation*. This makes them capable of dealing with new problem instances that are completely novel, in a way that has never been seen before - as long as the prompt resembles what these models have been trained on before. The reality is that the amount of training data they have been trained on is so vast that there are very little things that one might ask that have never been looked at by the model. Essentially, they are quite capable of having a good initial estimate of how to tackle pretty much any situation. Of course, we know countless papers that expose the failure modes of these models, but they always answer on topic. I believe this is analogous to us having to tackle daily situations without System 2 thinking - we'd be able to be on topic most of the times, but would much too frequently fail to have the right behavior or give the right answer to the problems we're asked. It's analogous to us only having intuition, but never slow deliberate thinking. 

Their training modality also enables them to quickly adapt to new categories of knowledge that one may want to fine tune them on. The great paper [A critique of Pure Learning](https://www.nature.com/articles/s41467-019-11786-6) argued that biological brains learn very little - they are just incredibly well wired as a result millennia of genetic evolution, and adapt incredibly fast to new environments. One can think of Foundation models as such - models that have been trained on such vast amount of data that their architecture and weights are perfectly suited to learn new tasks quickly. This is what we see in practice - your average computer vision model is not trained from scratch anymore - one always loads a pre-trained model and fine tunes with their own (often-limited) data - and that usually does the job well <d-footnote>compared to training from scratch. Of course, these models still have significant issues.</d-footnote>.   

### What's missing for good system 1 thinking? 

In short: interaction and grounding. 

#### Interaction

A fundamental aspect of our learning and intelligence, and of our developing intuitions about how things in the world work is through both *exposure* and *interaction* with these things. As I argue in my [previous post](/_posts/2024-10-10-phd-north-star.md), taking the number "3" as a demonstrating example: *"not only do we learn what "three" means by being shown three fingers, three pens, or three heads on Cerebrus' head, but we also learn how to say three words, draw three lines, eat three meals a day. The concept "three" is not only seen but also **interacted** with, and even **produced** in a wide range of different contexts. Its meaning and representation in our brain is multi faceted and highly malleable - specifically because we have *actively* learned about it through interaction and production, as opposed to just *passively* through exposure.*. Learning from data is not enough. 

One research direction that tries to go beyond passively learning from data is the one of World Models. According to Claude, "World Models work by learning to create internal, predictive representations of an environment that allow an AI agent to simulate potential scenarios, forecast outcomes, and make more intelligent decisions by "dreaming" or exploring hypothetical trajectories before taking actual actions."

In the original World Model paper <d-footnote>arXiv:1803.10122v4</d-footnote>, Ha & Schmidhuber write: 

>"One way of understanding the predictive model inside of our brains is that it might not be about >just predicting the future in general, but predicting future sensory data given our current motor >actions. 

By attempting to predict future sensory input (data) based on current actions, one essentially gets this sense of interaction - one can see the direct effect of their actions on the world, and most importantly, accordingly correct their prediction errors in a more grounded way. Working with World Models come with plenty of other advantages (and limitations), but this will be for another blogpost. This research direction is a major one of my PhD. 

#### Grounding

Symbolic grounding is a fundamental question in AI, which looks at how abstract symbolic representations (like words, concepts, or logical statements) acquire meaning and connection to real-world sensory experiences and perceptual data. Many make the argument that Neural Networks simply do not learn good symbolic representations by learning in the statistical way they do. However, some people argue otherwise. Ellie Pavlick dedicated an [entire (and beautiful) article](convincingly(https://royalsocietypublishing.org/doi/10.1098/rsta.2022.0041)) to outlining counterarguments to the common criticism of LLMs: 1) their lack of symbolic structure and 2) their lack of grounding. She points to research that, instead of showing failures of Neural Networks and using this as an argument against symbolic structure or grounding, looks at the representations that models use under the hood, which paints a much more positive picture. 

Long story short, I am now a bit unsure what to think about this. 

## Can Neural Networks do System 2?

###  Traditional System 2 - Planners And Search

### What's Missing 

## How do we connect System 1 and System 2?

### Chain-Of-Thought & Test-Time-Training

### Neuro-Symbolic Approaches 

### What does Neuroscience tell us about System 1 and System 2 thinking? 


  <!-- - name: System 1 and System 2 - A Paradigm for Progress in AI Research
  - name: Can Neural Networks do System 1?
  - subsections: 
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
     - name: Neuro-Symbolic Approaches 
     - name: What does Neuroscience tell us about System 1 and System 2 thinking?  -->

<!-- 
"In the 1980s and 1990s a schism emerged in the artificial intelligence community. On one side were 
those in the symbolic AI camp, who were focused on decomposing human intelligence into its 
constituent parts in an attempt to imbue AI systems with our most cherished
skills: reasoning, language, problem solving and logic. In opposition were those in the behavioral
AI camp, led by the roboticist Rodney Brooks at MIT, who believed the symbolic approach was doomed to fail because “we will never understand how to 
decompose human level intelligence until we’ve had a lot of practice with simpler level intelligences.”

Brooks’s argument was partly based on evolution: it took billions of years before life could simply 
sense and respond to its environment; it took another five hundred million years of tinkering for 
brains to get good at motor skills and navigation; and only after all of this hard work did 
language and logic appear. To Brooks, compared to how long it took for sensing and moving to 
evolve, logic and language appeared in a blink of an eye. Thus he concluded that “language . . . 
and reason, are all pretty simple once the essence of being and reacting are available. 
That essence is the ability to move around in a dynamic environment, sensing the surroundings to a degree sufficient to achieve the necessary 
maintenance of life and reproduction. 
This part of intelligence is where evolution has concentrated its time—it is much harder.”

To Brooks, while humans “provided us with an existence proof of [human-level intelligence], we must be careful about what the lessons are to be gained 
from it.” To illustrate this, he offered a metaphor:

Suppose it is the 1890s. Artificial flight is the
glamor subject in science, engineering, and venture
capital circles. A bunch of AF researchers are
miraculously transported by a time machine to the
1980s for a few hours. They spend the whole time in
the passenger cabin of a commercial passenger
Boeing 747 on a medium duration flight.
Returned to the 1890s they feel vigorated, knowing
that AF is possible on a grand scale. They
immediately set to work duplicating what they have
seen. They make great progress in designing pitched
seats, double pane windows, and know that if only
they can figure out those weird "plastics" they will
have their grail within their grasp. (A few
connectionists amongst them caught a glimpse of an
engine with its cover off and they are preoccupied
with inspirations from that experience.) -->
