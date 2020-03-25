The aim of the project is to :
 - Collect Twitter data based on ‘#candidates’ for the 2020 Democratic Party Presidential Primaries
 - Perform Sentiment Analysis on tweets which mention each candidate
 - Compare sentiment analysis scores to the National Polling for each candidate for the same period
 - Predict sentiment scores based on prior data
 - Check model quality based on available metrics

Step 1.
Downloads from Twitter can be done only via a Twitter API: 
1. Create an account and app 
2. Obtain credentials which will be later used for authentication. 
3. I have used Tweepy library as my code of choice to download the tweets.
Twitter offers 2 types of downloads 'Search' and 'Stream'. I chose the stream option as it has large number of keywords one can use to gather tweets and the number of downloaded tweets is unlimited.
'stream.py_README.md' provides all instructions to get started with downloads.
4. Tweets are downloaded as a .csv file, multiples times a day (whenever one runs the code).

Data Cleaning:
1. Retained -  tweets which had a keyword (candidate), removed all tweets which were missing a keyword 
2. Removed tweets which referred to multiple candidates. 
3. Removed URLs from tweets.
4. Unwrapped contractions (isn’t == is not, haven’t == have not, let’s == let us etc.)
5. Later, I filtered out tweets which had less than 3 tokens (after tokenization). 



Approach - Tokenization, Spacy:
1. Used default Sentiment library
2. Processed text with Textacy  - Spacy  ‘Core En’ processor
3. Used Parts of Speech = ['NOUN', 'ADJ', 'VERB', 'ADV', 'INTJ', 'AUX', 'ADP', 'PART']
4. Used ‘stop words’ excluding ‘No’ and ‘Not’
5. Filtered sentences by token length of 3
6. Obtained - Objectivity score and Polarity score


Approach - Vader
1. Used Vader Sentiment Intensity Analyzer
2. Empirically validated by multiple independent human judges, VADER incorporates a "gold-standard" sentiment lexicon that is 3. especially attuned to microblog-like contexts. Vader interprets:
 - basic emojis  :-)    :)   :-(   :(  
 - acronyms and initialisms (LOL, WTF…), slang with sentiment value (meh, nah…)
  No preprocessing required
4. Score types : Positive, Negative, Objectivity, Compound 

