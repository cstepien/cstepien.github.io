---
layout: post
title: Estimating Domestic Box Office Success of Movie Sequels
---

<div class="message">
Over half of the top 10 movies in the U.S. have been sequels every year since 2010. What if studios could predict future sequel revenue to help determine whether they should greenlight sequels?
</div>

### Project objectives

The goals for this project were two-fold: 1) Create a linear regression model to predict domestic box office revenue for movie sequels and 2) more broadly, identify features of prior movies in the franchise that contributed positively or negatively to sequel revenue. For this project, I considered prequels, remakes, and reboots under the 'sequel' umbrella.

### Gathering a movie sequel dataset

I scraped all listed movie franchises from [Box Office Mojo](http://www.boxofficemojo.com/franchises/) using beautifulsoup in Python. After dropping duplicates (some movies were listed in two different franchises - for example Iron Man 2 was in both the Iron Man franchise and the larger Marvel franchise), I was left with 242 franchises and 631 movie sequels. I also had 242 first movies (the first movie in each franchise) to gather feature data from.

### Selecting features to model

I chose seven features to model based on hyptheses about how movie sequels are made. I calculated the time interval between movies in a franchise, whether the production studio had changed, the genre, revenue of the first and most recent movies in the franchise, number of theaters that most recent movie had been released in, and whether the movie belonged to multiple franchises or only one (like the Iron Man 2 / Marvel Universe example above).

### Modeling sequel success with linear regression

I applied an ordinary least squares linear regression to the dataset, and went through several iterations of the model, each time dropping features with a p value > 0.10. I separately applied a lasso regression to see if this approach yielded a better outcome. Based on the root mean squared error (RMSE), both modeling approaches performed similarly. The pilot model can predict sequel success within $100 million, but interpreting the features provides some more information for studio execs.

### What leads to better performing sequels
If a sequel is an Action movie, belongs to multiple franchises, follows a movie in the franchise that had high revenue, and is the 2nd or 4th+ movie in the franchise, it will do fairly well.

### What leads to worse performing sequels
Horror sequels and foreign movie sequels tend to perform poorly, as well as the 3rd movie in franchises.

### What doesn't impact sequel success
The amount of time since the first movie in the franchise or the most recent movie didn't impact box office revenue, nor did how much the first movie made. So execs shouldn't be shy about rebooting an old favorite, even if a lot of time has elapsed!

### Next steps for this model
I'd like to look at production costs and metacritic reviews for prior movies in franchises, as well as whether the movie star changed in each installment.

### Expanded applications: TV series!
Thanks to a colleague Gilles for pointing out that I might be able to apply this approach to TV shows to try and predict whether a show will be renewed.
