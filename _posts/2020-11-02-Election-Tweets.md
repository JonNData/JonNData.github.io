---
layout: post
title: NLP on Election Tweets Aug-Oct
subtitle: Applying Natural Language Processing to US Election Twweets, visualizing with Tableau
image: https://github.com/JonNData/JonNData.github.io/blob/master/img/twitter.jpg?raw=true
tags: [NLP, Tableau, word clouds, data analysis, python]
---

This post: a very brief brush-up on some Natural Language Processing techniques and Tableau usage.

I took data scraped from twitter regarding the 2020 US election from August 1st to October 30th. I then filtered for tweets with over 20 likes to hone in on tweets with more activity. Here are some word clouds that represents the most common words from tweets based on whether the tweets: mention Trump, mention Biden, or have the top 10% number of likes.
<iframe src="https://public.tableau.com/views/USElection2020Aug-OctWordCloudsall/Dashboard1?:showVizHome=no&:embed=true" width="1024" height="768" frameborder="0"></iframe>

Next I ran some sentiment analysis on tweets with Trump or Biden in it as well. I plotted a scatterplot against the subjectivity of these tweets.
<iframe src="https://public.tableau.com/views/USElection2020Aug-OctWordClouds/Dashboard2?:showVizHome=no&:embed=true" width="600" height="600" frameborder="0"></iframe>

I performed Latent Dirichlet Allocation topic modelling to group together words that are commonly mentioned together.
Some topic groupings for tweets that mentioned Trump

  * win, lose, think, vote, go, know, say, want, uk, hope
  * trump, vote, win, chance, attack, 2020, day, college, electoral, russian
  * say, president, win, american, poll, @realdonaldtrump, supreme, day, republican

And some topic groupings for tweets that mentioned Biden
  * 'american', 'incumbent', 'dakota', 'announce', 'lt', 'south', 'in', 'normalize', 'relation', 'peace'
  * 'relevance', 'north', 'week', 'agree', 'american', 'relation', 'south', 'peace', 'policy', 'president'
  * 'broke', 'north', 'lt', 'dying', 'week', 'agree', 'president', 'in', 'achievement', 'relation'
  
Finally for some fun I experimented with recurrent neural networks to generate some text. These models use deep learning to try and understand text patterns and can be made to output sample texts.

![textgenrnn](https://github.com/JonNData/JonNData.github.io/blob/master/img/textgengif.gif?raw=true)  
Some outputs:  
`campaign to the Republican stronghold over between so deeply entrenched that winning Pennsylvania won't be fired. India hossistened of a link - Who wonder if there’s an elected US senatorawe can endorsement.`  


`"Defunding the point. Trump to Biden in US election angst of US election debate if Biden wins the US election is only two weaker will go for #BidenHarris2020Lands #Trump and Joe Biden is set to New York Post want to go for a no-deal `

Of course moderately gibberish. I trained on 50 epochs, or rounds--more sophisticated models will run for much longer.

Thank you for following along as I brush up on some NLP skills!

You can find my repository [here](https://github.com/JonNData/US-election-2020-tweets)
