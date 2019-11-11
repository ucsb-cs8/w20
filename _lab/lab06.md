---
layout: lab
num: lab06
ready: false
desc: "More practice writing functions, more accumulator patterns, Monte-Carlo simulation, using plotHistogram function"
assigned: 2019-11-13 9:00am
due: 2019-11-19 08:59am
---

The goals for this lab are:

* perform a Monte Carlo coin flip experiment
* use Python's random module again
* continue to get experience with pair programming
* simulate a random walk
* explore what happens when we add several random numbers together
* use **plotHistogram** function
* see an illustration of the Central Limit Theorem

## This lab should be done solo. 

Make sure that you adhere to the [Academic Integrity](https://studentconduct.sa.ucsb.edu/academic-integrity) standards and do/submit your own work.

## Getting started

## Step 1: Log on and open up a terminal window

This is done following the steps you have performed in lab00.

## Step 2: Create a directory in your cs8 directory named {{page.num}}.

This is done by following the sequence of steps in the first lab (lab00).

## Step 3: Start IDLE. 

The terminal command for this is `idle3`, or `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens.  When you have the IDLE window up, you are ready for some programming!

Remember, you will need to have the cTurtle module, [cTurtle.py](https://sites.cs.ucsb.edu/~buoni/cs8/cTurtle.py), in your home directory or in some other directory in your Python path.


## What to program?
<u>Note: In this lab and all labs that follow, unless otherwise stated please write your functions with the exact same name and parameter list as what is specified. </u>

## Functions to Implement:

### Basic:
1. **coinFlipExperiment(M, N, nTrials)** - return True or False
2. **monteCarloRandomWalkFirstPassage(D, nTrials)** - return a list [average_steps, list_of_steps], and plot a histogram of steps
3. **plotRandomUniformSum(M, N, nBins)** -plot a histogram , and return a list

# Function Details:

## 1. coinFlipExperiment(M, N, nTrials)

Write a function that estimates the probability of getting **M** or more heads out of **N** fair coin flips (by fair we mean the coin has equal chance of turning up heads or tails), repeating this sequence of flips a total of  **nTrials** times.  To perform this experiment, you should define a helper function **coinFlipTrial(M, N)** that performs one sequence of **N** coin flips and returns **True** if the number of heads is greater than or equal to **M**, and **False** otherwise.  A test you can use for your functions is to estimate the probability of getting 8 or more heads out of 10 coin flips, which should be around 5 percent (0.05).

## 2. monteCarloRandomWalkFirstPassage(D, nTrials) - return a list [average_steps, list_of_steps], and plot a histogram of steps.

Consider a random walk in two dimensions.  A walker starts at the origin (0, 0) and takes steps each of unit length and each in a completely random direction until reaching a distance **D** or further away from the origin.  Write a function **monteCarloRandomWalkFirstPassage** that performs **nTrials** of such an experiment, return a list **[average_steps, list_of_steps]**, where the **average_steps** means the average number of steps required to first reach a distance **D** or more from the origin, and the **list_of_steps** is a list of **nTrials** numbers, recording the number of steps for each trial. Also, plots a histogram of the distribution of number of steps required.  You will want to use the **plotHistogram** function from [hist.py](https://sites.cs.ucsb.edu/~buoni/cs8/hist.py). 

Please pay attention that to return means to exit the function. Therefore, you should first plot the histogram and then return the list.

You will want to write a helper function **randomWalkFirstPassageTrial(D)** that returns the number of steps required to reach a distance D or more away for one trial of such an experiment.  One random walk trial consists of a walker starting at the origin **(0,0)** taking unit steps in the **theta = random.uniform(0,2\*math.pi)** direction.  The change in **x** and **y** are simply **math.cos(theta)** and **math.sin(theta)**, respectively.  At any point in the walk, the distance is given by **math.sqrt(x\*\*2 + y\*\*2)**. 

Below is the histogram of distances for D=10, and nTrials = 10000 using nBins = 20.

![Histogram_of_distance_and_nTrials](histogram_of_distance_and_trials.png)

## 3. plotRandomUniformSum(M, N, nBins) –  plot a histogram and return a list.

Let's consider what happens when we add **M** uniform random numbers together.  Since each random number can be between **0** and **1**, we expect this sum will be between **0** and **M**, but somehow we expect that it is more likely for the sum to be near the middle (**M/2**) than near the ends (**0** and **M**) for M > 1.  First write a function **randomUniformSum(M)** that adds up **M** uniform random numbers between **0** and **1**.  Second, write a function that forms a **list** of **N** such numbers by calling **randomUniformSum** a total of **N** times. Third, plot the result in a histogram and return the **list**.

Please pay attention that to return means to exit the function. Therefore, you should first plot the histogram and then return the list.

What values should you use for binMin and binMax?  To answer this, consider the minimum and maximum values that **randomUniformSum** may assume.   Try calling your function four times with **M = 1, 2, 3, 10** setting **N = 1000000** and **nBins = 100** in each case.  You will notice that as **M** increases, the distribution looks more and more like a Normal (or Gaussian) distribution.  This is an illustration of the Central Limit Theorem, a very important theorem from Statistics which states that as you add more and more independent random variables (from any distribution, doesn't have to be uniform) the sum approaches a Normal distribution - very cool :-).

<table>
   <tr>
      <td><center><img src="histogram1.png" /></center></td>
      <td><center><img src="histogram2.png" /></center></td>
   </tr>

   <tr>
      <td><center><img src="histogram3.png" /></center></td>
      <td><center><img src="histogram10.png" /></center></td>
   </tr>
</table>


## Advanced (if you are curious and time permits):

A1. Generalize your **coinFlipExperiment** function to include one extra parameter, p, the probability that a coin flip results in heads, thus allowing for a "weighted" coin.

A2. Improve the efficiency of your helper function **coinFlipTrial** so that the function returns **True as soon as **M** flips resulting in heads is achieved, or **False** as soon as it is impossible to achieve **M** heads.

## Saving your files

Save your functions in a Python file named **{{page.num}}.py** in your directory **{{page.num}}**.

## Upload `{{page.num}}.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "{{page.num}}" on Gradescope and upload your `{{page.num}}.py` files.

Thanks to Matthew Buoni for this lab!


