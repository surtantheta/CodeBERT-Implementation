# CodeBert
In this repo we have replicated the paper <b><a href = "https://arxiv.org/abs/2002.08155">CodeBERT: A Pre-Trained Model for Programming and Natural Languages</a></b>. </br>
We are interested in evaluating CodeBERT specifically in Natural Language(NL)-Programming Language(PL) probing. Given an NL-PL pair (c, w), the goal of NL-PL probing is to test model’s ability to correctly predict/recover the masked token of interest (either a code token ci or word token wj) among distractors.
There are two major types of distractors: one is the whole target vocabulary used for the masked language modelling, and another one has fewer candidates which are filter or curated based on experts’ understanding about the ability to be tested.

