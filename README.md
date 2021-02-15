# Twitter Sentiment Analysis

In this project, we observe the evolution of sentiments (positive/negative) in tweets we gathered, tagged with terms reffering to the Black Lives Matter movement between 29-12-2019 and 20-10-2020. The aim of this work is to portray the effect of events happening during this period and share our results, as well as get accustomed to text preprocessing and sentiment classification.

## Data

We used [Twint](https://github.com/twintproject/twint) to scrap tweets with the hashtags "BlackLivesMatter", "George Floyd", "Breonna Taylor" and "BLM". We set a maximum of 3500 tweets per day for a period of 10 months starting the year 2020. The data is nonuniforrm, we see a significant increase in tweets starting May 25th 2020.

Timeseries observation example:
| Date | Time | Timezone | Tweet | Hashtags
| ----------- | ----------- | ----------- | ----------- | ----------- |
| 6/18/2020 | 23:58:52 | 200 | I hope all my family in buffalo everyone has been to city hall atleast once since the death of George Floyd. We need y'all there at these rallies because we need UNITY!! #BlackLivesMatter | [BLM]

## Preprocessing

The following preprocessing steps are carried out (with the exception of stop-words and stemming, as these yielded worse results):
| Action | Input | Output
| ----------- | ----------- | -----------
| Removing or replacing non-ASCII characters | - “网络”<br>- “éphémère” | - “”- “ephemere”
| Removing URLs | - “check this link: http:// www.example.com/index.html” | - “check this link:”
| Replacing contractions | - “isn’t”<br>- “I’m” | - “is not” - “I am”
| Removing punctuation | - “@barbie - love you ! :D” | - “barbie love you”
| Replacing numbers by text | - “10 gallons of milk please!” | - “ten gallons of milk please!”
| Removing single characters | - “I want a banana” | - “want banana”
| Removing stop-words | - “He attacked Godzilla with an exploding kitten” | - “attacked Godzilla exploding kitten”
| Stemming | - “Quickly ! The exploding kittens !” | - “Quick ! The explode kitten !”
| Lowercasing | - “FoGive mE fAtheR” | - “forgive me father”

Such that the fictive tweet:
- "http://bbc.in/1BO3eWQ Check it quickly héhé ! 网络 It's a test. I got 10 good answers! :) #LOL @brian"

becomes:
- "check it quickly hehe it is test got ten good answers lol brian"

## Classification

We trained our classifier on data from this [Kaggle dataset](https://www.kaggle.com/kazanova/sentiment140).
We obtained best results with an LSTM architecture. See [our report]() for more details and plots.

## Results

![Heatmap](image.jpg)
