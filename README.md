![GitHub Logo](https://github.com/IzabellaExeoulitze/twitter_sentiment_analysis/blob/master/compound2.png)




Collect Twitter data based on ‘#candidates’ for the 2020 Democratic Party Presidential Primaries
Perform Sentiment Analysis on tweets which mention each candidate
Compare sentiment analysis scores to the National Polling for each candidate for the same period
Predict sentiment scores based on prior data
Check model quality based on available metrics









The aim of the Twitter Sentiment Analysis project is to:

Collect Twitter data based on ‘#candidates’ for the 2020 Democratic Party Presidential Primaries
Perform Sentiment Analysis on tweets which mention each candidate
Compare sentiment analysis scores to the National Polling for each candidate for the same period
Predict sentiment scores based on prior data
Check model quality based on available metrics
Step 1. Downloads from Twitter can be done only via a Twitter API:

Create an account and app
Obtain credentials which will be later used for authentication.
I have used Tweepy library as my code of choice to download the tweets. Twitter offers 2 types of downloads 'Search' and 'Stream'. I chose the stream option as it has large number of keywords one can use to gather tweets and the number of downloaded tweets is unlimited. 'stream.py_README.md' provides all instructions to get started with downloads.
Tweets are downloaded as a .csv file, multiples times a day (whenever one runs the code).
Data Cleaning:

Retained - tweets which had a keyword (candidate), removed all tweets which were missing a keyword
Removed tweets which referred to multiple candidates.
Removed URLs from tweets.
Unwrapped contractions (isn’t == is not, haven’t == have not, let’s == let us etc.)
Later, I filtered out tweets which had less than 3 tokens (after tokenization).
Approach - Tokenization, Spacy:

Used default Sentiment library
Processed text with Textacy - Spacy ‘Core En’ processor
Used Parts of Speech = ['NOUN', 'ADJ', 'VERB', 'ADV', 'INTJ', 'AUX', 'ADP', 'PART']
Used ‘stop words’ excluding ‘No’ and ‘Not’
Filtered sentences by token length of 3
Obtained - Objectivity score and Polarity score
Approach - Vader

Used Vader Sentiment Intensity Analyzer
Empirically validated by multiple independent human judges, VADER incorporates a "gold-standard" sentiment lexicon that is 3. especially attuned to microblog-like contexts. Vader interprets:
basic emojis :-) :) :-( :(
acronyms and initialisms (LOL, WTF…), slang with sentiment value (meh, nah…) No preprocessing required
Score types : Positive, Negative, Objectivity, Compound
