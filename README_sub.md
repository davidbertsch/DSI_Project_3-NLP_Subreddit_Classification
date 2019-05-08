# Project 3

## Executive Summary

In this project, I built a model to classify the subreddit of origin of posts to the Grateful Dead subreddit and the Phish subreddit. These are fan forums for fans of the bands. These fanbases are often linked together because both bands have a similar atistic approach that is distinct from most music in that they emphasize the live concert performance vs. recording studio albums. 

The bands are from different periods. The Grateful Dead rose to prominence in the 60s as part of the countercultural movement in San Francisco. They pioneered a style of playing unique concerts that consisted largely of improvization. As a result of their concerts being different from one another, they attracted fans that became obsessive followers to the point that some fans would actually "tour" with the band. These fans are colloquially known as "Deadheads". Phish - despite having very different musical influences and style - followed the Grateful Dead's model for making their concerts distinct from one another and emphasizing the improvization in their performance. They formed in 1983 as college students, and rapidly built a diehard fanbase.

Many fans of Phish are fans of the Grateful Dead, and vice-versa. Both fanbases are also early pioneers of internet message boards. The message boards are used for things like discussing concerts, favorite versions of songs, ticket trading/selling, etc. I thought these two subreddits would make for an interesting NLP analysis, because both fanbases would be discussing very similar things.

### Hypotheses

Before doing any data collection, I had a few ideas on how an NLP classification model might perform.

1. I thought it would be fairly straightforward to build an accurate model. This was based on the idea that there would be a lot of band-specific terminology that would recur. This would be words like band member names, song titles, album titles, or years during which the bands did not overlap. I figured that most posts to these subreddits would contain at least some of this kind of terminology.

2. I thought that a model would have a hard time with classifying vague posts. I figured that there would be a certain amount of posts that wouldn't explicitly refer to either band.

3. I thought that the model would have a challenge with classifying "crossover" posts where one band is being discussed in the other band's subreddit. Since there are many fans of both bands, I know that this kind of discussion does occur fairly often.

### Modeling

I tried out the following models in my analysis:

- Logistic Regression with Count Vectorization
- Naive Bayes with Count Vectorization
- Logistic Regression with TF-IDF Vectorization
- Naive Bayes with TF-IDF Vectorization
- Support Vector Machines with Count Vectorization
- Random Forests with Count Vectorization
- Support Vector Machines with TF-IDF Vectorization
- Random Forests with TF-IDF Vectorization

All of the models performed fairly accurately, and they all had a fair amount of variance. 

The logistic regression models and the Naive Bayes models had the highest accuracy by a small margin, but the highest variance by a significant margin (~90% testing accuracy/~99% training accuracy). 

The random forests models reduced the variance, but had the highest bias by a substantial margin (~90% testing accuracy/~85% training accuracy).

The support vector machines model with TF-IDF vectorization was my preferred model. It had the lowest variance, and it's testing accuracy was close enough to the best performing logistic regression/Naive Bayes models. This model was 90% accurate on testing data classification and 94% accurate on training data classification.

### Conclusions

This was an interesting exercise in testing out a variety of different NLP models. I think the performance of my models was generally quite good, but I'm sure it could be better. 

Overall, my hypotheses proved to be correct in how the models would likely be accurate, but that they would be susceptible to misclassifications on certain types of posts.

My first idea to improve the model from here in the future would be to acquire more data. I would either do this by getting more posts, or by including the comment text for each of the posts that I analyzed for this modeling process.

As is reflected in my hypotheses, I think it is reasonable that there would be some amount of bias in any model classifying posts between these subreddits. Both subreddits contain a fair amount of similar conversation about music and concerts in general that don't necessarily specifically pertain to either band. Also, both message boards contain a lot of conversation pertaining to the other band. Phish and the Grateful Dead share a lot of fans, and there is a lot of discussion about both bands in both subreddits. At the same time, getting more data would allow the model to have a better sense of all of the band-specific language like band member names, song/album titles, etc.

Interestingly, some of the top buzzwords for each band were common words in both subreddits. Since there is a lot of crossover discussion between the forums, "Phish" and "Dead" are words that, while especially likely to occur in their respective subreddits, are also fairly likely to appear in the other subreddit. This means that simply having a "buzzword" is not enough to correctly classify each post. This would likely be a factor in many of the misclassifications.

It would be interesting to repeat this exercise with two other subreddits of bands that were not as closely linked in terms of their fanbases. It would also be interesting to repeat the exercise on two non-music subreddits. I wonder how the accuracy would compare and if the same kind of model would emerge as the best one.

Another idea that I have is that it might be possible to build a buzzword library that includes any band member names, song titles, and album titles. This might be basically accomplished simply by using larger datasets, but it also wouldn't be that hard to generate such a list manually. In any case, I wonder how a model like that would perform that only considered band-specific language. Of course, it would be basically guessing on posts that were vague, and it would still be susceptible to incorrectly classifying crossover posts, but maybe it would perform well overall. When I was scanning through the lists of wordcounts for each subreddit, I was noticing that most of the top words were all general language and not key terminology or buzzwords. I was expecting there to be more of a concentration of band-specific buzzwords at the top of the list, but that wasn't exactly the case.

Anyway, this project was a good introduction to NLP and some of the various models that can be used for NLP analysis.