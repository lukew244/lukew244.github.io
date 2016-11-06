---
layout: post
title:  "What I learned building a mock API server"
date:   2016-09-03 13:12:38 +0100
categories:
tags: [API, Rails, Ruby, Bootstrap]
---

This project was a three day sprint to address a problem a number of us had experienced firsthand. In the early stages of development, it's often not convenient to make frequent requests to the APIs your app will need. The response data might vary between requests; the information you want could be buried within other content; and you can quickly exceed API request limits.

Our solution was Spy API ([see it on Heroku here](https://spy-api.herokuapp.com/)), a site that allows users to make API requests and receive their own, pre-configured JSON responses.

Here are three lessons I will take away for future projects:

#### 1. Pick an appropriate MVP
{: class="subheading"}

Even within our tight timeframe, getting a basic API server up and running was comfortably achievable. This allowed us to strengthen the core product by adding further database-level validations, refactoring code and more thoroughly testing edge cases. Pushing for more features was a tempting but wrong approach, as it would have forced compromises in the quality of our code.


#### 2. The framework really matters
{: class="subheading"}

Using Rails - a highly opinionated framework with strong off-the-shelf configuration - was an obvious choice for this project. While we considered deploying a lighter framework like Sinatra or Node Express, Rails simply allowed us to get more done. It's the best option when you need to scale up a project quickly.

#### 3. Know your shortcuts well
{: class="subheading"}

Early on, we added Bootstrap to give our product a makeshift front end. This ended up costing us time when we tried to incorporate our own CSS, which was frequently distorted by the styles inherited from Bootstrap. Ease of use and simplicity are not the same thing; if you don't fully understand how a shortcut is working, you are better off without it.  
