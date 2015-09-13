---
layout: post
title: Where Are Your Data Science Jobs
modified:
categories: Data-Science
excerpt: ""
comments: true
tags: [python, geomap, web crawling, data visualization]
image: 
  feature: posts/stackoverflow-job.png
date: 2015-09-03T21:35:33+08:00
use_toc: true
---

# TL;DR

In this article, I will show to how to plot a job location map in python using basebase and job data from Stackoverflow. The outcome map is what you saw in the featured image shown above.

# Foreword

Few weeks ago, when I was doing the ICDM 2015 competition on Kaggle, Kaggle sent me job notifications every few days. Since our big project came to a milestone, we finally could have a little vacation. I just went to the east Taiwan. Then, a question hit my mind again.

> 1. Where is your data science job?
> 2. What skill is required by these jobs for a candidate?
> 3. Who is recruiting our people? 

For all data science practicers and workers, the job opportinuty is our number 1 concern, because, obviously, the job market somehow reflects the growth and committment for the data science industry from the country. 


# Data sources

When people look for a job, we usually go and browse the following websites for new opportunities. Of course there are many of others, but hese websites are intuitive choices because of the global job oppurtinity.

1. [LinkedIn](http://www.linkedin.com/){:target="_blank"}
2. [Indeed.com](http://www.indeed.com){:target="_blank"}
3. [Kaggle](https://www.kaggle.com/){:target="_blank"}
4. [StackOverflow Careers](http://careers.stackoverflow.com){:target="_blank"}

However, all of the websites above don't provide API to access jobs data we want, so we either have to find some way to get the job data or crawl the data on our own. For this data scraping task, I had tried several methods to scrape those data. The table below is the tools I used and the target website. [import.io](https://www.import.io/) was the first try for scraping the data. Yes, import.io and [Kimono](https://www.kimonolabs.com/) successfully downloaded all the job data on Kaggle and Stackoverflow Careers. But when I wanted to scrape LinkedIn search results. 

|----
|               | import.io | Kimono | Python scrapy |
|---------------|:---------:|:------:|:-------------:|
| LinkedIn      |     x     |    x   |       o       |
|----
| Stackoverflow |     o     |    o   |       o       |
|----
| Kaggle        |     o     |    o   |       o       |
|----
{: rules="groups"}

After some poking around, I found out LinkedIn is a clever ass preventing tools like import.io and Kimono from crawling its data. 


# Map plotting

# Discussion
