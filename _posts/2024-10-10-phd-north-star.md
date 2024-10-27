---
layout: distill
title:  The North Star of My PhD
show: false
category: open
related_publications: false
date: 2024-10-10
toc:
  - name: A North Star Benchmark to my PhD - The ARC Challenge  
  - subsections:
    - name: What is ARC?
    - name: Why can humans solve ARC perfectly? 
    - name: Why does Machine Learning suck at ARC? 
    - name: The importance of Benchmarks, and the perils of Goodhart's law
---

For the past 9 months, I have been spending a vast amount of time thinking and reading about a large variety of Machine Learning and Neuroscience problems and methods. I'm often asked what my PhD is about <d-footnote>Hi dad</d-footnote> - and I struggle to answer. This is my attempt at answering.

# A North Star Benchmark to my PhD: The ARC Challenge 

Great inventions often hold hidden secrets that only reveal themselves with time. This is what I think of Francois Chollet's [Abstraction And Reasoning Corpus (ARC) Challenge](https://arcprize.org/), which has, since I have started thinking about it in August 2022, made me, and countless others, think about an ocean of different problems and research avenues. This small dataset of little and simple visual puzzles somehow still holds bullet-proof to the entirety of modern Deep Learning (including the latest iterations of LLMs), and encompasses the vast majority of modern "Artificial Intelligence" challenges.

The goal of my PhD is not to solve ARC. However, my PhD somehow keeps ARC as a *North Star* - a source of inspiration, to think and internalize all the sub-challenges one should think of to make progress on ARC - to make progress on better Deep Learning, and maybe even, dare I say it, make progress towards Artificial-General-Intelligence (AGI). 

In this essay, I will introduce some of these sub-problems and discuss some works that I believe to be of great possible impact. Before diving in, let's first go through a little prelude about the ARC challenge, what makes it special, and why it remains unsolved by State-Of-The-Art Deep Learning.

## What is ARC?

The Abstraction and Reasoning Corpus (ARC) is an ensemble of IQ-test like puzzles [proposed by Francois Chollet in 2019](https://arxiv.org/abs/1911.01547). Chollet introduced ARC as a benchmark on which both humans and AI systems could fairly compete, aiming to steer AI research in a different direction. Indeed, Chollet argued that while everyone was constantly talking about AGI, the community had no clue of how to measure it, and that the current benchmarks and methodologies, overly led to overfitting to single tasks - which is not representative of *intelligence*. His aim was to create a different benchmark, one that would be difficult to solve with the classical Deep Learning framework - one that would force us to rethink how we do Artificial Intelligence. 

The structure of ARC is elegantly simple, and indeed unlike any machine learning benchmark at the time. Solvers are presented with a set of _training_ (demonstration) examples, each consisting of input-output pairs in grid format. The challenge is to infer the underlying rule that transforms the input grid into its corresponding output grid, then apply the inferred rule to a new _test_ input grid. To top it all, there are only 800 puzzles publicly available - all very different from one another - a very low amount of data for today's Deep Learning standards and [scaling laws](https://arxiv.org/abs/2001.08361).

{% include figure.liquid loading="eager" path="assets/img/north_star_phd/ARC_Examples" class="img-fluid rounded z-depth-1" %}

The ARC "world" is clearly defined. It is always built from n>2 training (demonstration) examples, and a single testing grid where one must apply the rule from the demonstration to the new grid. The grids are always sized between 1x1 and 30x30 pixels. Each pixel can take any of 10 colors - represented by numbers from 0 to 9. While clearly defined, the ARC-world is also particularly "open-ended", as the concepts that can be represented and which make up rules are... well.. open-ended. Chollet defined what a solver agent (human or computational) should know of to be able to solve the tasks (paraphrasing Chollet and [Melanie Mitchell](https://aiguide.substack.com/p/why-the-abstraction-and-reasoning)):

* *Objectness*: knowledge that the world can be parsed into _objects_ that have certain physical properties
* *Numerosity*: knowledge of small quantities and notions of “smallest,” “largest,” “greater than,” “less than,” etc
* *Geometry and Topology*: knowledge of lines, simple shapes, symmetries, containment, and copying
* *Agents and Goals*: knowledge that some entities are _agents_ who have their own intentions and act to achieve goals

But how do we go about teaching a model about all of these stuff? Like *actually* teach it what e.g. a "line" is, and all the different things lines can represent and be used for? Let's think about why we understand this as humans first. 

## Why can humans solve ARC perfectly?

A "traditionally" smart human can solve [100% of ARC tasks](https://www.youtube.com/watch?v=UakqL6Pj9xo&t=53s&ab_channel=DwarkeshPatel), and Amazon Turk workers can solve ARC tasks [with 75% to 85% accuracy](https://arxiv.org/html/2409.01374v1).  

But **why**? Why do humans manage so well compared to machines, without any pre-training? We do not have the answer to this question as there is no definite "neuroscience" explanation to our capacity to reason and generalize. However, we can analyze some patterns of capabilities that us humans have to understand what allows us to solve ARC tasks.  

Humans learn about all of the concepts in use in ARC through years of *exposure* and *interaction*. Let's take the concept of number "three" or "3" as an example. Not only do we learn what "three" means by being shown three fingers, three pens, or three heads on Cerebrus' head, but we also learn how to say three words, draw three lines, eat three meals a day. The concept "three" is not only seen but also **interacted** with, and even **produced** in a wide range of different contexts. Its meaning and representation in our brain is multi faceted and highly malleable - specifically because we have *actively* learned about it through interaction and production, as opposed to just *passively* through exposure. 

Because this is not a scientific paper, I'll allow myself an analogy with my other passion - music. When learning to improvise music, there is a lot of theory that one can learn about: scales, harmonies, voicing etc... One can learn all the theory in the world and analyze as much music as they can, but there is nothing replacing actively practicing the concepts learned on one's instrument over and over to fully internalize them. Once the concepts are internalized - one can just stop thinking about them in a strict way, and can freely develop an intuition - a *feel* - to combine all the different concepts together, on the spot, effortlessly and without rationalization. <d-footnote>Today, it's common to use the word "grok" to express this deep internalization of a given concept. The AI model of X (former Twitter) is named Grok. I think that's cool. </d-footnote>.  

This active form of learning through interaction leads us to better internalize concepts, and a wide variety of them that we unconsciously interact with daily. While this internalization is already a strong advantage compared to modern Deep Learning systems, our edge over them doesn't stop there. We are also able to effortlessly **compose** between these different concepts in novel contexts - by virtue of having internalized them the way we did. Because we properly internalized the concept of "three", or the concept "squares", we can on the fly compose them, even in completely novel ways, and understand everything that one can do with these. This is indeed only possible if the essence of these concepts and ideas are properly internalized - which Deep Learning can never achieve through learning by being exposed to data. 

Besides composing concepts, we also have immediate **intuitions** over which concepts to use when first encountering a situation. This is exactly what happens when you look at the ARC puzzles - just by virtue of seeing the colors, grid like structures, and shapes, you immediately discard the toolbox of Maxwell's equations, driving a car, or even Dancing a Waltz. You only need to search through the plausible solutions that are reasonably applicable to the domain you are now facing - and that's mostly intuition. Of course, you need to try a bunch of different ideas, but the ideas you try are all pretty reasonable given the context, and the time you need to reach a solution subsequently dramatically shrinks. Imagine if you had to consider every single thing you know of to solve these puzzles?  

All these aspects are crucial to our intelligence, and they are missing from modern Deep Learning systems, and are exactly the type of things that ARC is meant to test for. 

## Why does Machine Learning suck at ARC?

One thing Deep Learning is very good at is "memorization". This means fitting a training data distribution curve, in such a way that everything that is close enough to what has been seen before can be correctly dealt with. It reminds me of my own self in high school, where we had been introduced to Newton's Laws. While we had already studied integration and differentiation in Mathematics class, I was just completely unable to use the concepts and apply them to Newton's laws (or any Physics related concepts). I had "*memorized*" how to solve the maths exercises about differentiation and integration, but I hadn't "*understood*" what integration and differentiation really were about. 

Modern Deep Learning is exactly like high-school me - incentivized to do "shortcut learning" and minimize a loss function (like when I was maximizing my high school math grades), while never really understanding what things really mean. And this is precisely why ARC has, five year after its release, still not been solved. It is designed to prevent any form of *memorization*, as all puzzles are very different, and very little data is available. It is designed to test *understanding* and *learning efficiency* - as a solver must have a good intuition and conceptualization of the different concepts of the puzzles, and manage to figure out how to use them with very little amount of context. It is designed to need *composing* of different types of knowledge, and so with very little amount of context.  

Five years after its release, ARC indeed held its promise, as it still is very far from having satisfying solutions. State-Of-The-Art Large Language Models (LLMs) are nowhere near solving it <d-footnote> albeit the recent efforts of [Ryan Greenblatt](https://redwoodresearch.substack.com/p/getting-50-sota-on-arc-agi-with-gpt) made us doubt for a brief moment.</d-footnote>, and the current best solution comes from a team which, although doing great work, is vastly over-fitting to ARC, which I believe to be somewhat against the spirit of the challenge. 

<!-- The following sections are about investigating the different design aspects of modern deep learning that make it unable to properly learn and reason through things - the way humans do. -->

## The importance of Benchmarks, and the perils of Goodhart's Law 

Besides important scientific insights into what artificial intelligence (or simply "intelligence") are about, the ARC Challenge taught me quite a few important things.

One central idea is how essential benchmarks are to steer progress. Chollet noted in his essay that the entirety of the ML community was focused on benchmarks that ultimately measures "skill", as opposed to "intelligence". Skill, through unlimited training data, is not what makes any agent intelligent. *Skill acquisition efficiency* however, is much more interesting, because it underlies the potential of a given algorithm to learn new things and adapt when needed - which is what Chollet considers to be a hallmark of intelligence. This strongly reminded me of [Peter Thiel's hiring philosophy](https://www.8vc.com/resources/lessons-from-peter-thiel): "The key in hiring is to value potential skill rather than currently existing skill — potential skill is based on intelligence rather than training". 

This realization by Chollet was no news to most people that had seriously thought about the problem - but the genius of his effort was to provide a benchmark that controlled for what he thought were ways to different (and better) AI research. And well, 6 years after its publication (an eternity in the world of AI), people still talk about this, and it subtly steers the community towards a different kind of progress.  

This is what works in AI, and what works in the world - humans always try to signal quality by performing on some metric, and end up optimizing (and often "over-optimizing") for that specific metric, which ultimately steers evolution. In AI, this really is particularly efficient - if the community judges one benchmark as interesting, one can just let "[graduate student descent](https://x.com/TBen_Yassine/status/1801296865654177913)" do its job, and a plethora of methods improving performance on this metric will follow. 

Obviously, the other side of the coin is the well known Goodhart Law "When a metric becomes the target, it stops being a good metric". And that applies to ARC too, even if it was specifically designed to avoid overfitting <d-footnote>the current SOTA solutions from MindsAI uses a fine tuned transformer on a ton of algorithmically generated ARC-like tasks and all the tricks in the books to optimize performance on transformers is clearly overfitting to ARC. </d-footnote>  

Ultimately, there is no benchmark that cannot be gamed with enough time an effort. This is why it's important to use multiple metrics, and to keep on updating the metrics. Most importantly, it's important to regularly ask ourselves the question, as a community, company or organization - what do we really want to achieve? And what would achieving it look like? 

So what do we really want to achieve in AI research? 


