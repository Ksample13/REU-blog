---
title: "Statistical Approaches to Matching Bullets"
subtitle: "Madelaine Quistgaard"
date: "2017-07-28 17:00:00 CDT"
topic: "week7"
layout: post
root: ../../../
tags: [forensics, statistics, assignments]
---

## 1. What data do Hare *et al* use? 

The data that they use is the 3D topographical images of the bullets, along with the x3p format which is the array of surface measurements at the micrometer level. They used x3pr and bulletr for processing the data in R. They got the data from the 6 lands on the bullets. 

## 2. In what ways do the methods used by Hare *et al* differ from the "traditional" methods of bullet matching? 

Traditionally the bullet is place under comparison microscopes and compared in person by a forensic scientist. In this research, computed distributional difference between known matches and known nonmatches using reference database. A set of features were derived which separates the two classes of bullets. The features are then put into a train statistical model. 

## 3. How do Hare *et al* use **clustering** to help perform bullet matching tasks? 

They used random forest to perform bullet matching tasks. The forest is compiled of 300 trees that can correctly identify matches and non-matches.

## 4. Identify one statistics and/or probability concept in the presentation that you have not heard of before. Do a little bit of research (Googling/Wikipedia is ok) and try to describe it to someone who doesn't know about it. You should also consult [this paper](bulletmatchingpaper.pdf) to see if there is more detail on your chosen topic than is presented in the webinar. (Hint: Control + F is useful...) You **don't need** to read the whole paper.

The concept that I hadn’t heard before was cross-correlation function. This is when measuring information between two different locations or time series. The range of data is -1 to 1 such that the closer it is to 1, the more similar the information set. 
