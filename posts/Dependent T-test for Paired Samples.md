<!--
.. title: Test a Perceptual Phenomenon
.. slug: test-a-erceptual-phenomenon
.. tags: statics, dependent-t-test, paired-sample
.. category: Statistics Report
.. guid: 01
.. description: A Practice of Dependent T-test for Paired Samples
.. date: 2017-08-26 00:05:00 UTC+08:00
.. base_url: http://www.testfield.cc/
.. type: text
-->

>## Background Information
>  In a Stroop task, participants are presented with a list of words, with each word displayed in a color of ink. The participant’s task is >to say out loud the color of the ink in which the word is printed. The task has two conditions: a congruent words condition, and an >incongruent words condition. In the congruent words condition, the words being displayed are color words whose names match the colors in >which they are printed: for example RED, BLUE. In the incongruent words condition, the words displayed are color words whose names do not >match the colors in which they are printed: for example PURPLE, ORANGE. In each case, we measure the time it takes to name the ink colors >in equally-sized lists. Each participant will go through and record a time from each condition.
>  [Dataset](https://drive.google.com/file/d/0B9Yf01UaIbUgQXpYb2NhZ29yX1U/view) from [Udacity](http://www.udacity.com/)

![](/images/dependent1.png)

**Distribution of time taken in congruent group**

**Participants who spent between 12  and 13 are the most.**


![](/images/dependent2.png)

**Distribution of time taken in incongruent group**

**Participants who spent between 17 and 18, 20 and 21 are the most.**


![](/images/dependent3.png)

**Distribution of time taken in both  the congruent group and the  incongruent group.**

**Every participant spends more time in the incongruent condition than that in  the congruent group.**



## Dependent T-test for Paired Samples


## Why is a t-test chosen? 

1.The sample size is below 30.

2.The population standard deviation is unknown.


## Why is a dependent test  chosen?

In the Stroop task, each participant will go through and record a time from each condition. 


## Independent Variable: 

a congruent words condition, and an incongruent words condition.


## Dependent Variable: 

 the time it takes to name the ink colors in equally-sized lists in a congruent words condition and an incongruent words condition. 


## Null hypothesis (Ho):

The mean of time taken in congruent condition and that in incongruent condition  of  the population are almost equal.  The mean of  time  taken in both condition of the population are almost equal (μc-μI = 0).  And the difference of the population mean is equal to zero (μD = 0).


## Alternative Hypothesis (HA):

The mean of  time  taken in both condition of the population are significantly different (μc-μI ≠ 0) and not by chance. And the difference of population mean is not  equal to zero (μD ≠ 0). 


## Hypothesis:

Ho: μD = 0

HA: μD ≠ 0


**two trail test**

α = 0.05

df = 23

t critical value = ±2.069


mean of Congruent  Group = 14.05

mean of Incongruent Group = 22.02

SD of Difference = 4.86

t-statistics = -8.02

p<.05


Confidence interval on the mean difference; 95% CI = （-10.02， 5.91）

d = 1.64


## Result: reject Ho

Because the probability of getting t-statistics which is -8.03 is less than 5%. Time taken in congruent group is statistical significantly less than that in Incongruent group.











