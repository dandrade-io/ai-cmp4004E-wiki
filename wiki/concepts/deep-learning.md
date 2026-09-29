---
title: Deep Learning
type: concept
tags: [ml, neural-networks]
sources: [raw/slides/01_Introduction to Artificial Intelligence.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Deep Learning

**Slides (slide 13).** Theoretical tools existed since the 1960s; the term "deep learning" was introduced in 1986 (per slide). Researchers studied networks whose depth (number of layers) can grow. Yoshua Bengio, Geoffrey Hinton and Yann LeCun established foundations for training them with a modified [[backpropagation]]. Slide timeline places it at 2000.

> ⚠️ Contradiction: the slide's "1986" and "2000" are inconsistent with each other. AIMA's historical notes (p. 836–837): backprop popularised 1986; late 1990s–early 2000s interest waned (Bayes nets, ensembles, kernel machines); interest in deep models was sparked by **Hinton et al. (2006)** (deep generative/Bayesian networks); it exploded after **AlexNet won the 2012 ImageNet competition** (15.3 % top-5 error vs >25 % for the next best). So "1986" fits the popularisation of backprop, and ~2006/2012 the modern deep-learning era.

## What AIMA says (ch. 22, p. 801–802)
"Deep" = hypotheses are algebraic circuits with tunable weights organised in many layers, i.e. **long computation paths**. Linear/logistic regression has very short paths and independent contributions of inputs; decision trees have long paths for only a small fraction of inputs; deep networks let all inputs interact. Currently dominant for vision, machine translation, speech, image synthesis and RL. Names "neural network" reflect origins (McCulloch–Pitts 1943) though the resemblance to real neurons is superficial. Enablers (p. 837): big data, GPUs, ReLU instead of sigmoid, residual networks, mini-batch SGD. Today's LLMs and agents (slide 2) are deep networks.

Details: [[neural-networks-basics]], [[backpropagation]], [[aima-ch22-deep-learning]].

## Related
[[perceptron]], [[backpropagation]], [[support-vector-machine]], [[neural-networks-basics]], [[overfitting-and-generalization]], [[history-of-ai]]

## Exam angles
- Who are the three "godfathers" credited on the slide.
- Depth = number of layers; why backprop is central.
