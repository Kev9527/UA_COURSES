# Introduction

## Stagety of Experimetns

**Definition**:  The general approach to planning and conducting the experiment.

* Best-Guess approach.
  
  Two disadvantages:
  
  1. take too much time.  2. not guaranteed to be the best 

* OFAT(one-factor-at-a-time): 
  
  fail to consider the interaction between the variables.

* Factorial

factors are varied together

## Basic Principles

Three principles of experimental design:

1. randomization 

2. replication 

3. blocking

## Guidlines for Designing Experiments

- Recoginition of and statement of the problem 

a. Factor screening (Screening designs are an efficient way to identify significant main effects)

b. Optimization (ususally a follow-up to a screening experiment.)

c. Confirmation (verify if there is consistency with some theory or past experience)

d. Discovery

e. Robustness

- Selection of the reponse variable

- Choice of factors, levels and ranges

- Choice of experimental design

- Performing the experiment

- Statistical analysis of the data

- Conclusions and recommendations

# One-way ANOVA

## fixed effects model

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-03-12-54-56-image.png)

### assumptions:

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-03-14-02-45-image.png" title="" alt="" width="63">

## random effects model

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-03-14-06-12-image.png)

## Complete randomized design (CRD)

## Random effects model / Components of variance model

# Two-way ANOVA

## Model

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-11-34-03-image.png)

## Assumptions

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-11-35-30-image.png" title="" alt="" width="119">

<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-11-36-11-image.png" alt="" width="110" data-align="inline">

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-11-36-25-image.png" title="" alt="" width="142"><img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-11-36-38-image.png" alt="" width="190">

# RCBD (Randomized complete block design)

The Randomized Complete Block Design is also known as the two-way
ANOVA without interaction.

## Model

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-10-28-53-image.png)

## Assumptions

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-10-29-33-image.png" title="" alt="" width="180">

A key assumption in the analysis is that the
effect of each level of the treatment factor is the same for each level of the
blocking factor.����

# Post ANOVA

## Contrasts

In general, a contrast is a linear combination of parameters of the form

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-03-14-23-23-44-image.png" title="" alt="" width="94">

Assumption:

<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-03-14-23-27-06-image.png" alt="" width="95">

Hypothesis testing:

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-03-14-23-27-22-image.png" title="" alt="" width="149">

### code

```
proc glm data=one;
class percent;
model strength=percent;
contrast 'C1' percent 0 0 0 1 -1;
contrast 'C2' percent 1 0 1 -1 -1;
contrast 'C3' percent 1 0 -1 0 0;
contrast 'C4' percent 1 -4 1 1 1;
run;
```

## Simultaneous confidence intervals

### Comparing all contrasts

* Scheffe's Method  (type one error is at most alpha)

* Bonferroni 

### Comparing all pairs of contrasts

* Tukey's test  (controls experimentwise or family error )

* LSD (not experimentwise)

### Comparing with a control

* Dunnett
  
  <img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-03-15-00-02-00-image.png" title="" alt="" width="88">
  
  choose the number of the observations from control treatment 

<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-03-15-00-03-14-image.png" alt="" width="81"> 

# Factorial Design

<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-04-06-13-53-06-image.png" alt="" width="383">

## Model

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-03-14-59-38-image.png)

fixed.<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-03-15-00-29-image.png" alt="" width="125"><img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-03-15-00-19-image.png" title="" alt="" width="94"><img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-03-15-00-09-image.png" alt="" width="90">

## General 2^k Factorial

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-04-06-13-28-06-image.png)

## A Single/Unreplicated 2^k Design

One approach to the analysis of an unreplicated factorial is to assume that certain high-order interactions are negligible and combine their mean squares to estimate the error. This is an appeal to the **sparsity of effects principle**; that is, most systems are dominated by some of the main effects and loworder interactions, and most high-order interactions are negligible.

Daniel suggests examining **a normal probability plot** of the estimates of the effects. The effects that are negligible are normally distributed, with mean zero and variance  2 and will tend to fall along a straight line on this plot, whereas significant effects will have nonzero means and will not lie along the straight line.

Remember that main effects do not have much meaning when they are involved in significant interactions.

### Design Projection

discard negligible factors and  then (e.g.  2^4. --> 2^3)

we can get a **hidden replication** by this projection

**summary:**

The concept of projecting an unreplicated factorial into a replicated factorial in fewer factors is very useful. In general, if we have a single replicate of a 2 k design, and if h (h  k) factors are negligible and can be dropped, then the original data correspond to a full two-level factorial in the remaining k  h factors with 2 h replicates.

# Blocking and Confounding in the 2^k Factorial Design

## Why do we use block and confounding?

In many problems it is impossible to perform a complete replicate of a factorial design in one block. Confounding is a design technique for arranging a complete factorial experiment in blocks, where the block size is smaller than the number of treatment combinations in one replicate.

In each block, we still have all the treatment combinations and thus the block doesn't affect the main affects.

## How to construct the blocks?

The usual practice is to confound the highest order interaction with blocks.

# Two Level Fractional Factorial Design

## Why do you want to use two level fractional factorial design ?

1. If the experimenter can reasonably assume that certain high-order interactions are negligible, information on the main effects and low-order interactions may be obtained by running only a fraction of the complete factorial experiment.

2. A major use of fractional factorials is in **screening experiments**.

Eg

If there are three factors, the full factorial design has 2^3=8 treatment combinations.

Then the 2^(3-1) fractorial design gives 4 treatment combinations. The generator of the design is I=ABC.  (A = BC, B= AC ...)

## Key ideas of a successful fractional design

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-15-39-35-image.png)

## One-Half Fraction of 2^k Design

Example:

Consider a 2 ^3 full factorial design in which 8 treatment combinations are required. However, we can affrod only 4 runs.  Therefore, the design contains 2^(3-1)=4 treatment combinations. It is called 2^(3-1) design.

ABC is the **generator** of the defining relation.  It is also called **word**.

**Definition relation:**  I = ABC

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-18-14-35-image.png" title="" alt="" width="356">

**Aliases**

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-21-40-50-image.png)

## Resolution

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-07-21-51-06-image.png)

## Construction

The $2_{|||}^{3-1}$1fractional factorial is obtained by writing down the full 2^2 factorial as the **basic design** and then equating factor C to the AB interaction. The alternate fraction would be obtained by equating factor C to the -AB interaction.

## Difference between fractional and confounding

# Nested Design

## Two-Stage Nested Design

### Model

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-23-41-image.png)

The subscript j(i) indicates that the jth level of factor B is nested under the ith level of factor A. It is convenient to think of the replicates as being nested within the combination of levels of A and B; thus, the subscript (ij)k is used for the error term.

No interaction.

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-12-11-52-33-image.png)

### Both factors fixed

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-35-35-image.png" title="" alt="" width="116">    <img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-35-47-image.png" alt="" width="298">

* �Hypothesis for $\tau$

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-39-29-image.png" title="" alt="" width="102">

* test statistic

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-40-05-image.png" title="" alt="" width="98">

* �Hypothesis for $\beta$

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-41-26-image.png" title="" alt="" width="120">

* test statistic

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-41-52-image.png" title="" alt="" width="118">

### Both factors random

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-15-36-47-image.png" title="" alt="" width="330">

* test statistic

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-20-32-48-image.png" title="" alt="" width="544">

### Mixed

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-20-33-20-image.png" title="" alt="" width="373">

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-20-33-36-image.png)

# Split-plot design

When some factors are harder to vary than others, a split plot design can be efficient.

When the factors can be nested, it is more efficient to apply a difficult-to-change factor to the units at the top of the hierarchy and then apply the easier-to-change factor to a nested unit. This is called a split plot design.

Whole-plots/main treatments

Split-plot/subplot treatments

## Model

two models with different error structure

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-20-37-19-image.png)

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-20-38-48-image.png)

# Experiment with Random Factors

If the experimenter randomly selects a of these levels from the population of factor levels, then we say that the factor is **random**.

We **assume** that the population of factor levels is either of **in?nite** size or is large enough to be considered in?nite

## A single random factor

### Random effects model

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-09-07-52-image.png" title="" alt="" width="371">

### Assumptions

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-30-29-image.png" title="" alt="" width="155">

$\tau_i$ is independent of $\epsilon_{ij}$

#### Variance Components

![](/Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-09-08-54-image.png)

### Estimation of model parameters

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-03-12-image.png" title="" alt="" width="431">

### Hypothesis testing

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-46-39-image.png" title="" alt="" width="140">

## Two-Factor Factorial with Random Factors

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-49-31-image.png" title="" alt="" width="517">

<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-50-03-image.png" alt="" width="714">

### Estimation

<img src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-50-30-image.png" title="" alt="" width="236"><img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-54-16-image.png" alt="" width="185">

### Hypothesis

<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-56-37-image.png" alt="" width="403">

<img title="" src="file:///Users/kaiwenliu/Library/Application%20Support/marktext/images/2022-05-08-10-56-20-image.png" alt="" width="403">

# Questions

1. What is randomization in CRD ? Does it refer to the randomized order of treatment combinations. Do all the treatments combinations appear in the design?  Do all the treatments combinations appear in a block in RCBD? Do we control that every treatment combinations appear for a certain times ?

2. If we find block factor is significant, 
