# Twitter-sentiment-analysis

### About the project
I've seen this project in one youtube video and i loved it.
This is something you all love to try.
There I used some special library like tweepy and Textblob.
There you should also know about NLP little bit and regular expression.
I didn't used any pre provide data..
I've created my developer account on twitter and then get api key and tokens and with the hep of them I can use any user's data.


### Tool Used
Used Python for data analysis for that particular dataset. Libraries used for this project are:
Numpy
Pandas
Matplotlib
Seaborn
re
tweepy
OAuthHandler
TextBlob
WordCloud, STOPWORDS

### Installation
for numpy
'''
import numpy as np
'''  

for Pandas
'''
import pandas as pd
'''

For Matplotlib
'''
import matplotlib.pyplot as plt
'''

For Seaborn
'''
import seaborn as sns
'''

For Regular expression  (Used for text data)
'''
import re
'''

For Tweepy  (used for accessing twitter API)
'''
import tweepy
'''

For OAuthHandler   (authenticatethe api and secret key)
'''
from tweepy import OAuthHandler
'''

For TextBlob   (to use simple NLP task)
'''
from textblob import TextBlob
'''

For wordcloud and stopword
'''
from wordcloud import WordCloud, STOPWORDS
'''


### Key Insights

How I cleaned the all the text from twitter using regular expression.

'''
def cleantwt(text):
    text = re.sub(r'@[A-Za-z0-9]+', '', text) #cleaning the '@' from text
    text = re.sub(r'#', '', text) #cleaning '#'
    text = re.sub(r'https?:\/\/\S+', '', text) # cleaning the http links
    text = re.sub(r'RT[\s]+', '', text) #cleaning retweets
    return text

df['Tweets'] = df['Tweets'].apply(cleantwt)

#Remove emoji
def remove_emoji(text):
    emoji_pattern = re.compile("["
                           u"\U0001F600-\U0001F64F"  # emoticons
                           u"\U0001F300-\U0001F5FF"  # symbols & pictographs
                           u"\U0001F680-\U0001F6FF"  # transport & map symbols
                           u"\U0001F1E0-\U0001F1FF"  # flags (iOS)
                           u"\U00002702-\U000027B0"
                           u"\U000024C2-\U0001F251"
                           "]+", flags=re.UNICODE)
    return emoji_pattern.sub(r'', text)

df['Tweets'] = df['Tweets'].apply(remove_emoji)
df.head()
'''

How I created Word Cloud which is the visual representation of highly frequent words

'''
stopwords = set(STOPWORDS)
Words = ''.join([tweets for tweets in df['Tweets']])
wordcloud = WordCloud(width=600, height=400, stopwords=stopwords, random_state=21, max_font_size=200).generate(Words)

plt.imshow(wordcloud, interpolation='bilinear')
plt.axis('off')
plt.show()
'''

<img width="500" alt="cloud" src="https://user-images.githubusercontent.com/69238621/140746555-28bf6ae0-e9bb-4378-a7bf-1e1b86346bfe.PNG">


Visual representation of relationship between subjectivity and polarity

<img width="600" alt="pol" src="https://user-images.githubusercontent.com/69238621/140746805-b74d70b0-61a6-4e8a-925f-3877a30689e1.PNG">
