# Robert Turner Data Analytics Github
It's been a while since I've updated this since I've been primarily working on data analytics projects for my job that I'm unable to share, but this GitHub profile contains many of my personal projects that I've worked on.

You may be interested in:

## Topic Modeling Twitter Project
Code, results, and paper drafts for my honor's thesis to develop a topic modeling method for tweets. For this project I created the code to stream tweets from Twitter, store them in datasets for future use, clean those tweets, and fit [Latent Dirichlet Allocation](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation) topic models to the corpus using two different methods. There are a number of topic models visualized using the [LDAvis package](https://github.com/cpsievert/LDAvis) that can be downloaded and viewed. Those topic models attempt to show how the topics discussed on Twitter changed leading up to or following major events in the world. While the project as a whole can't be reproduced using this code due to changes Twitter has made, the project can still be used to guide future attempts. 

The shortest summary I can provide for the results are:

1. Both the number of topics discussed and the words within those topics change quickly in response to major events
2. Both the maptpx and lda packages can be used to generate topic models but those models will often not be the same
3. If this were to be replicated my first focus would be on combining tweets into larger documents before performing analysis. 

Combining tweets into larger documents for analysis could be done by aggregating tweets by their user, by using something similar to [Pablo Barbera's Bayesian Ideal Point Estimation method](https://github.com/pablobarbera/twitter_ideology) to discover a latent variable you feel is worth using to divide different kinds of tweets, or simply aggregating tweets sent around the same time. I found much more consistent and readable topics when fitting them to larger documents.

## parseTweetFiles R Package
The code for my Twitter project in an [R package](https://github.com/rturn/parseTweetFiles/tree/master), which is unfortunately now quite out of date. Twitter has updated their APIs since this package was created, and the APIs now require payment to use as well. This package should no longer be used directly. However, there are many examples within the package you might find useful. This includes:

* Mapping geo-tagged tweets to zip codes or states using a shape file from census.gov. The shape file I used is included in the package, and the mapping is performed with the maptools and sp R packages.
* Cleaning tweets beyond simple stopword cleanup. Tweets are rife with links, unicode, and html tags and require quite a bit more cleanup than a standard document
* Datasets of tweets collected over the course of the project using the twitteR package (now deprecated). While small, these can be used to replicate the topic modeling work done without going through the modern Twitter APIs.

## Spectral Meta Learner
A smaller project in an [R package](https://github.com/rturn/BMI-826-Project) format, I developed two implementations of a Spectral Meta Learner aggregator as described in [Ranking and combining multiple predictors without labeled data](https://arxiv.org/pdf/1303.3257.pdf). The aggregator combines multiple predictions from an ensemble of models while attempting to weight accurate estimates more heavily, and diminishing the weight of incorrect estimates. This learner is unsupervised, and does not require calculated accuracies for each of the predictions given. The learner uses either the leading eigenvector of the covariance matrix or the Singular Value Decomposition of the matrix of predictors to estimate the accuracy of each model and weight them accordingly for aggregation.  This can often produce superior output to any individual model in the ensemble. While the paper describes the method for classifiers, my package operates on continuous data. When tested in a variety of courses and projects, this method was shown to be effective on continuous data.

As this method only uses the predictions from the models it is attempting to aggregate, it is most effective when the ensemble of models is generally accurate. If only a few of the models in the ensemble are generating inaccurate results, this method works well. If the entire ensemble is performing poorly, the SML will have no way of indicating that or improving the situation.

<!--
**rturn/rturn** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
