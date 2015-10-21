---
layout: post
title:  "How to use GitRank"
date:   2015-10-21 11:10:00
categories: Projects
---

> This post will be updated as we make changes to the UI

This week, we launched the [GitRank](https://gitrank.io) website. GitRank is a platform to help developers choose and discover projects in the jungle of open source projects out there. The idea is that people should be able to give opinionated feedback on projects in a standardized way so that comparison can be made easily.

<!-- Home -->

## Introducing GitRank !

![Home](/assets/images/gitrank-how-to/home.png)

Not much on this page for now, this is the home page of GitRank. The to do action there is either to Login in the upper right corner or go to a repository to see its rating. To do that you have to know its github repository name. For example the neo4j repository is `neo4j/neo4j`. Putting that in the navigation bar will lead you directly to the repository page.

<!--- repository page -->
On that page, you are able to post reviews on repositories and add some tutorial that you find interesting for that particular project.
![Repository view](/assets/images/gitrank-how-to/repository.png)

When someone has actually already put some feedback onto the page you will see a visualization of the last 100 feedbacks and how they are broken up by categories.
![Repository view](/assets/images/gitrank-how-to/repository2.png)

If you are a Repository owner, you can also take a look at the badges we provide and add them to your repository. There are two badges: one that ask people to come to gitrank to give some feedback on your repo. The other one giving you the score your repository currently has on gitrank.
![Bagdes](/assets/images/gitrank-how-to/badges.png)

## How it works

The scoring system is based on a karma system. People get karma from contributing to open source projects that are well scored. As a consequence when they vote for repositories their vote is weighted with their karma. As a consequence the score is weighted by the people that most contribute to open source.

A restriction that comes with this system is that you cannot vote for the repositories you have contributed to. From the github API restrictions, we only take into account the contributions you have made until 90 days prior to your sign up on gitrank.
