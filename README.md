Identifying Brand/Product Emotions
# Phase 4 Project: Text Classification
**Author**: [Ferdinand Beaman](mailto:ferdinand.beaman@gmail.com)

## Overview

This was a text classification task, to see if I could train models to identify the emotional qualities of text.

I considered building a ternary instead of binary classifier (positive, neutral, and then also negative), but considering both the small size of the third class and my own time remaining in the program, I decided against it.

There was a class imbalance (2:1), but my research suggests that it's only moderate and not strong enough for me to intervene. With that in mind and seeing no other reasons to have special sensitivity for false negatives/positives, I predominately used accuracy scores to rank models' performances. However, if there did happen to be some major issue with either recall/precision regarding the minority class, I would take that into account.

I went with a Naive Bayes classifier because it appears to be approximately as accurate as the more complex classifier while being significantly easier on both my computer and my mind.

## Business problem: 
The organizers of South by Southwest contacted me to collect public opinion about what they did right at a given year's festival in order for them to know what to emphasize next time.

## Data

About ten thousand curated tweets. Thankfully, they have already been labeled by the helpful people here: https://data.world/crowdflower/brands-and-product-emotions

The classes were imbalanced to varying degrees. I ended up dropping the smallest class and merging neutral into negative to form a more general "not positive"
![img](./Images/Bar)

## Methods

This project utilized Count Vectorization and TF-TDF Vectorization. The data was not large enough for me to resort to using a hashing vectorizer.
For the modeling, a simple Naive Bayes was used. Despite the model's shortcomings on paper, it (allegedly) performs just as well as more complex modeling systems but at reduced cost to your machine.

I also made heavy use of the Fuzz library to find ambiguous tweets. You can see how while even when tweets are exactly identical, they are not rated identically:

![img](./Images/Ambiguity)

## Evaluation of Results

![img](./Images/FinalCM)

None of my models reached even 75% accuracy, despite the baseline set by the majority class being about 2/3s. A disappointing result to be sure, but I think that the data is at least partly to blame.

On the bright side, my precision and recall are not wildly imbalanced.

## Conclusions

The short nature of tweets may just not contain enough information for a computer to tell what is and what isn't meaningful. This was exacerbated by the presence of ambiguous messages that even the human raters disagreed about the categorization of. Hopefully if those issues can be addressed, the project can be improved upon.

### Recommendations
Melissa Mayer was mentioned in a lot of positive tweets and not in a lot of negative tweets. Use her for your marketing coming up.
"Google Circle" was mentioned in a lot of negative tweets and not in a lot of positive ones. Try to distance yourself from new social media ventures.

### Next Steps

Get a bigger corpus with hopefully longer messages. Twitter has since upgraded its maximum character limit, so they may have already done that for you.
Iterate through the boundary to optimize the distinction between an ambiguous tweet and an actually different one may be of value.
If possible, take care to increase inter-rater reliability during the labeling process. That's almost certainly key to a lot of this.
