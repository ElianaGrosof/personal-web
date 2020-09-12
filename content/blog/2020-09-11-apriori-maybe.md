---
title: Apriori Machine Learning Algorithm, Explained
author: Eliana Grosof
date: '2020-07-28'
slug: apriori-machine-learning-algorithm-explained
categories: []
tags: []
summary: A powerful yet simple ML algorithm for generating recommendations.
---
<br/><br/> 
 
 
Today, we’re going to learn about the **apriori machine learning algorithm**. Apriori, first proposed by [Agarwal and Srikant](https://www.it.uu.se/edu/course/homepage/infoutv/ht08/vldb94_rj.pdf) in 1994, is a type of Association Rule Mining algorithm that finds relationships within certain kinds of data and presents them as rules. Association Rule Mining is most commonly used in marketing, particularly in the context of shopping carts. This application area is formally known as “market basket analysis”.We’re going to use apriori to learn about the relationships between Oberlin College courses. If you want to follow along, check out my [GitHub repository](https://github.com/ElianaGrosof/OPrestissimoRecommendations).
### The data
Oberlin College students built a [handy website](http://oprestissimo.com/) that lets students evaluate different courses options by adding classes to a virtual cart. After some hard work and perseverance, we generated a [file](https://github.com/ElianaGrosof/OPrestissimoRecommendations/blob/master/data/converted_carts.csv) where each line contains a list of classes that a student considered taking at the same time. For example, if a student considered taking Economics 101 and Biology 100 in Fall 2020, we would have a line in our csv file that looks like:```shECON_101, BIOL_100```
### The algorithm — a brief overview
*Note: if you want to skip to the details, go to “algorithm — the details” section.*

In the broadest possible terms, the apriori algorithm takes a bunch of sets of items (known as *itemsets*), calculates some measures regarding the strength of relationships between items (*support, confidence, lift*), and presents those relationships as rules. 

Compared to some other machine learning algorithms, the results of apriori can seem a little anti-climactic, but the advantage is that you can easily understand the output. If this general approach is good enough for Amazon, it’s good enough for me.Let’s get into the details.
### Key Terms
*Itemsets*: an itemset is collection of related items. In our application, it is a list of classes that an Oberlin student considered taking in the same semester, represented as a “cart” of classes. Another example of an itemset is the items in a grocery store shopping cart, like “Bread, Eggs, Diapers”.
*Antecedent*: the first item in the itemset that I care about
*Consequent*: the second item in the itemset that I care about
_**Rule**_: antecedent → consequent relationship 
### Measures of Strength of Rules
*How strong is the relationship, really?*  

Assume we’ve divided our itemsets into lots of little rules. In this section, we want to understand how strong the rules are.Using our example from above, we know Economics 101 and Biology 100 are associated because a student thought about taking them at the same time. But, how strong is their relationship? Are they just friends, or are they something more? We’ll answer this question using 3 measures.The three main ways to understand how strong the relationship between items in an itemset are:
- Support
- Confidence
- Lift
### Support
Support tells us how often a given item was chosen. In our example, it tells us the absolute popularity of a class.Given class A and the rest of classes offered ~A (not A), the calculation for support is:
![support_calculation](support_image.png#center)