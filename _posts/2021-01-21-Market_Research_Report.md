---
layout: post
title: Street Stall Economy Market Research Report
date: 2021-01-21
Author: Yihan
categories: [Research]
tags: [Research Presentation]
comments: true
---

<img src="http://pic1.hebei.com.cn/003/024/737/00302473754_9d022ac0.jpg" style="zoom:50%" />

### Research Objectives

This research mainly focuses on *Mining Potential Customers and Analyzing Traits For Street Stall Economy*. After the pandemic COVID-19, most large and medium-sized real economies have suffered severe setbacks, and their revenues greatly reduced. At the same time, because of the virus' superior infectious ability, most residents were required to be in quarantine at home. 

Nevertheless, in the post-COVID-19 era, after several months of isolation, residents walk out of their houses with their long-repressed social desire. And they also need some kind of stimulus to reignite consumption. Stall economy can be such a stimulus, for its convenience both for customers and vendors. Stall vendors only need a car for transporting and displaying goods, and interested stall customers will grab something when passing by. Many residents always choose to take a walk after meal, go to large shopping centers and markets. Stall vendors see this phenomenon as an opportunity, and provide relatively cheap commodities to attract customers.

However, problems still exist. The competition between the protection of city environment and economy development becomes extremely obvious under the stall economy situation. After Beijing relaxed rules and allowed more vendors to set up on the road, on the square, many citizens complained that the environment is ruined, and vendors' forgetting to clean up the garbages had caused lots of unconvenience. Besides this, for many novices and specultors who want to start their own stalls, the choice of a suitable good to sell is hard to make. Even if they have chosen the suitable product, they will still have problems with their target crowd. Also, street-stall economy, which is full of unlicensed hawkers, is always characterized by disorder, filth and shoddy goods. The image needs to be rehabilitated, so that street vendors can be embraced, and their existence can be reboosted.

To solve these problems, we performed this investigation. The research object is Wuhan citizens. Because of the COVID-19, we cannot perform our supposed sampling procedure, which is a regret. This investigation will dive into the analysis of factors influencing citizens' choices of buying products, and clustering methods will be used to group these potential customers. We hope that this project can provide some advice for you.

### Hot-button Issues Analysis Based on Text Mining

By crawling online reports on Stall Economy, we want to know, what is the hot-button issues that residents and governments care about. During our investigation, we discover that Xinhua.net has a dynamic composition, which is suitable for crawling. We crawled around 1000 reports on Xinhua.net about Street Market Economy, ranging from February 2018 to June 2020. 

#### Word Cloud Analysis

We used `Jieba` in `Python` for analysis. `Jieba` is a chinese-oriented word segmental tool. By counting the word frequency, `Jieba` can predict the phrase and the context that the word belongs to. 

The result is shown below.

![word_cloud.png](../images/posts_images/reports/word_cloud.png)

We can see from the word cloud that, *Street Stall Economy*/*Employment*/*cars*/*boost*/*generation*/*Internet*/*Concept Stock* is what people most cared about. This reveals that, the development of Stall economy is not development in 'an' industry, but developments from all industries. Except for this, words like *Employment* reveal that, encouraging street stall economy can provide lots of job opportunities for the society, and also a relatively convenient employment platform for young people who are out of work.

#### Sentimental Analysis

Using the chinese-oriented natural language processing package, `snownlp`, we can perform sentimental analysis easily according to the reports we crawled from Xinhua.net. The sentimental analysis algorithm used in `snownlp` is based on Bayesian Inference. Compared to traditional sentimental analysis algos, this approach will provide more accurate results.

### Analysis of Factors Affecting Customer Purchase Based on Lasso-Logistic Model

### Potential Customer Mining Based on Clustering Methods

### Results

### Download Our Report Here!

