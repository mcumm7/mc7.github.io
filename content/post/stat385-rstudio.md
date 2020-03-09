---
author: Michael Cummings
categories:
- rstudio
- development
date: "2020-03-09"
description: An overview of what I have been learning about R in STAT 385.
tags:
- r
- stat385
title: STAT 385 RStudio
---

This blog is about what I have been learning about R and RStudio in STAT 385.
<!--more-->

## Introduction

RStudio is a really great program that makes learning R feel more 'approachable'. It is farily intuitive in nature and I have yet to encounter any problems using the program. 

{{< figure src="/rstudio.png" caption="A screenshot of RStudio." >}}

## The language

Already knowing a few programming languages, I felt more at ease when I began to learn R. There are some similarities between R and the other languages I am familiar with, as well as some differences. On the first day of class, the first difference I noticed was the syntax for assigning values to objects.

#### PHP
{{< highlight php >}}
<?php
name = "Michael";
?>
{{< /highlight >}}

#### R
{{< highlight r >}}
name <- "Michael"
{{< /highlight >}}

There are also some other differences, such as not needing to 'open' and 'close' the code. And also not needing a character to denote a new line. These are just a few examples.

## Progress
The first couple of homeworks I was able to get through pretty easily. Homework 3, vectorizing code, was definitley the assignment I struggled with the most. In this assignment, the objective was to take code that we had previously written and re-write a vectorized version of it.


The code below is my non-vectorized function. As you can see, it is very long.

{{< highlight r >}}
roulette <- function(bet, amount = 1){ 
  if(bet == "low")
  {
    low <- c(1:18)
    outcome <- sample(x = wheel[, 1], size=1)
    if(outcome %in% low)
    {
      return(cat("$",amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "high")
  {
    high <- c(19:36)
    outcome <- sample(x = wheel[, 1], size=1)
    if(outcome %in% high)
    {
      return(cat("$",amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "red")
  {
    outcome <- sample(x = wheel[, 2], size=1)
    if(outcome == "red")
    {
      return(cat("$",amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "black")
  {
    outcome <- sample(x = wheel[, 2], size=1)
    if(outcome == "black")
    {
      return(cat("$",amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "odd")
  {
    outcome <- sample(x = wheel[, 1], size=1, replace=TRUE)
    if((outcome %% 2) != 0)
    {
      return(cat("$",amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "even")
  {
    outcome <- sample(x = wheel[, 1], size=1, replace=TRUE)
    if((outcome %% 2) == 0)
    {
      return(cat("$",amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "first")
  {
    first <- c(1:12)
    outcome <- sample(x = wheel[, 1], size=1)
    if(outcome %in% first)
    {
      return(cat("$",2*amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "second")
  {
    second <- c(13:24)
    outcome <- sample(x = wheel[, 1], size=1)
    if(outcome %in% second)
    {
      return(cat("$",2*amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else if(bet == "third")
  {
    third <- c(25:36)
    outcome <- sample(x = wheel[, 1], size=1)
    if(outcome %in% third)
    {
      return(cat("$",2*amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
  else
  {
    outcome <- sample(x = wheel[, 1], size=1, replace=TRUE)
    if(outcome == bet)
    {
      return(cat("$",36*amount))
    }
    else
    {
      return(cat("$",-amount))
    }
  }
}
{{< /highlight >}}

Having completed the successfully completed the assignment, the advantages of having vectorized code are extremely clear to me. I was able to calculate the same result in 0.5 seconds vs 20 seconds, using the vectorized code vs the non-vectorized code respectively.

Below is the vectorized version of the code from above. Vectorizing the code took it from 126 lines to only 6.

{{< highlight r >}}
roulette_vec <- function(many_bets)
{
  win_lose_random <- sample(x = c(TRUE, FALSE), size = length(many_bets), replace = TRUE)
  prize = c('low' = 10, 'high' = 10, 'red' = 20, 'black' = 20, 'odd' = 15, 'even' = 15, 'first' = 50, 'second' = 50, 'third' = 50)
  total_prize <- unname(prize[many_bets])*win_lose_random
  total_prize
}
{{< /highlight >}}

