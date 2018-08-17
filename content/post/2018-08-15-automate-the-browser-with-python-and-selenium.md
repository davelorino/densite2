---
title: Automate the Browser with Python and Selenium
author: Davide Lorino
date: '2018-08-15'
slug: automate-the-browser-with-python-and-selenium
categories: []
tags: []
---

Being able to build an algorithm that can scrape a website for data is a commonly desired skill. Whether your challenge is to scrape as much data as possible on a given topic, or to routinely launch a "crawler" that pulls data according to pre-determined filters (most often from the end-users database) your task becomes a lot harder when so many websites today are rendered in Javascript. This is great from a user-interface perspective, but for people interested in building a data pipeline this makes things difficult. Because Javascript variables are named dynamically, that is, things that we would normally use to determine their "id" or "class name" are more or less randomly generated numbers that are different each time we navigate to that location in a website. we can no longer just pass our algorithm a set of html tags or website links. 

To get around this, we use the Selenium module in Python to locate and interact with Javascript-rendered website items (links, menus, filter drop-downs, form filling e.g. username and password, download buttons). The end goal is to build a data pipeline that we can deploy iteratively - say if we have a report that needs to be generated weekly, and this report consists of data that is pooled together from five or six different repositories in different file formats.

This scenario is often the case for people who need produce weekly reports. The time it takes to generate these types of reports can be reduced dramatically by making a script that follows your steps; each week all you need to do is specify a different date range to plug into the databases that you're pulling the data from (assuming that if you run a report weekly, you're looking at temporal data) and the script takes care of the rest.

In this post we will use Python (and the Selenium module) to build a website crawler in order to programmatically fetch a bunch of data that's housed in a website rendered in Javascript. We'll then store the data to disk in csv files. Lastly, to generate our reports we join and summarize the data with dplyr in R. 

The specific Javascript-based challenges covered in this post are:
  - Website Navigation
  - Dynamic Hover-Over 
  - Drop-Down Menu & Selection
  - XPath Coordinate Mapping

## Dodging the Javascript Trap



