---
layout: post
title:  "How to keep secrets safe in your first Ruby app"
date:   2016-08-29 13:12:38 +0100
categories:
tags: [Ruby]
---


From the very first app, a developer is responsible for the way their code handles sensitive data. This post looks at one common problem for new programmers: how to store third party API keys safely.

#### The issue
{: class="subheading"}

Third party APIs can greatly enhance what your app does - for example, allowing users to sign up with their Facebook profile, or upload images hosted on Amazon Web Services. These platforms give you a unique token to authenticate your app when making requests, and as a new developer experimenting with different technologies, it is easy to plug these numbers straight into your code. The trouble is that these tokens are personal to your account, and leaving them exposed in your program <a href="http://readwrite.com/2014/04/15/amazon-web-services-hack-bitcoin-miners-github/"> can be a costly mistake</a>. The risk is particularly high if you are pushing your code to an open source platform like Github.

{% highlight html %}
facebook_app_secret: 12345678987654321
{% endhighlight %}
How your code shouldn't look.
{: class="caption"}

Fortunately, this problem can be easily avoided using environment variables.

#### Keeping safe with environment variables
{: class="subheading"}

Environment variables are a collection of key-value pairs that hold important information on the state of your machine, such as the current logged in user, which version of Ruby you're using and where temporary files can be saved. They are accessible to programs running locally, and are therefore a great place to keep app authentication keys available, yet separate, from your app. On a Mac, you can view the environment variables from a terminal using the `env` command.

#### Manual setup
{: class="subheading"}

Environment variables are tied to the current terminal session. You can add an environment variable to an open session using: `export MYVARIABLENAME=VALUE`. If you need your variable to persist into other sessions, it should be permanently saved within your bash profile. Editing your bash profile can be a dangerous endeavour, so it is wise to read up on this and even backup your profile before making changes. Environment variables can be added to your profile using:

`echo "export MYVARIABLENAME=VALUE" >> ~/.bash_profile`

With the variable loaded into the environment, you can now safely refer to it in your app as follows:

{% highlight html %}
facebook_app_secret: <%= ENV["FACEBOOK_APP_SECRET"] %>
{% endhighlight %}


#### Using the Dotenv Gem
{: class="subheading"}

An alternative for Ruby programmers is the Dotenv gem (<a href="https://github.com/bkeepers/dotenv">see documentation here</a>). Variables are loaded into the environment for you via a `.env` file in the project folder, which is ideal for collaborative projects where your app will be tested on different servers (i.e. environments). Again, if you are using a version control system like git it is critical to ensure that this file doesn't get uploaded publicly.
