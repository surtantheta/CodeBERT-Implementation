# CodeBERT-Implementation
In this repo we have replicated the paper <b><a href = "https://arxiv.org/abs/2002.08155">CodeBERT: A Pre-Trained Model for Programming and Natural Languages</a></b>. </br>
We are interested in evaluating CodeBERT specifically in Natural Language(NL)-Programming Language(PL) probing. Given an NL-PL pair (c, w), the goal of NL-PL probing is to test model’s ability to correctly predict/recover the masked token of interest (either a code token ci or word token wj) among distractors.
There are two major types of distractors: one is the whole target vocabulary used for the masked language modelling, and another one has fewer candidates which are filter or curated based on experts’ understanding about the ability to be tested. <br>

This code was implemented on a 64-bit Windows system with 8 GB ram and GeForce GTX 1650 4GB graphics card.

Due to limited compuational power, we have trained and evaluated the model on a smaller data compared to the original data. 
<table>
  <tr>
    <th rowspan ="2"> Language </th>
    <th colspan="2">Training data size</th>
    <th colspan="2">Validation data size</th>
    <th colspan="2">Test data size</th>
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
  <tr>
    <td>Go</td>
    <td>635653</td>
    <td>500</td>
    <td>28483</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>PHP</td>
    <td>1047404</td>
    <td>500</td>
    <td>52029</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>Python</td>
    <td>824342</td>
    <td>500</td>
    <td>46213</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>Java</td>
    <td>908886</td>
    <td>500</td>
    <td>30655</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>Javascript</td>
    <td>247773</td>
    <td>500</td>
    <td>16505</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  
  
  </table>
  
Compared to the code in original <a href = "https://github.com/microsoft/CodeBERT/tree/master/CodeBERT/codesearch">repo</a>, this code can be implemented directly in Windows system without any hindrance.
