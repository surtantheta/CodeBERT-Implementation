# CodeBERT-Implementation
In this repo we have replicated the paper <b><a href = "https://arxiv.org/abs/2002.08155">CodeBERT: A Pre-Trained Model for Programming and Natural Languages</a></b>. </br>
We are interested in evaluating CodeBERT specifically in Natural Language(NL)-Programming Language(PL) probing. Given an NL-PL pair (c, w), the goal of NL-PL probing is to test model’s ability to correctly predict/recover the masked token of interest (either a code token ci or word token wj) among distractors.
There are two major types of distractors: one is the whole target vocabulary used for the masked language modelling, and another one has fewer candidates which are filter or curated based on experts’ understanding about the ability to be tested. <br>

This code was implemented on a 64-bit Windows system with 8 GB ram and GeForce GTX 1650 4GB graphics card.

Due to limited compuational power, we have trained and evaluated the model on a smaller data compared to the original data. 
<table>
  <tr>
    <th rowspan ="2"> Language </th>
    <th colspan="2">Training data</th>
    <th colspan="2">Validation data</th>
    <th colspan="2">Test data</th>
  </tr>
  <tr>
    <td>Original</td>
    <td>Our</td>
    <td>Original</td>
    <td>Our</td>
    <td>Original</td>
    <td>Our</td>
  </tr>
  <tr>
    <td>Ruby</td>
    <td>97580</td>
    <td>500</td>
    <td>4417</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  </table>
