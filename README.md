# Twitter Sentiment Analysis
## This project focuses on classifying sentiments in tweets using the Sentiment140 dataset, which contains 160,000 tweets labeled as either positive or negative.

## 🗂 Dataset Overview
Source: Sentiment140

Fields:

label — original sentiment label (0 = negative, 4 = positive)

id — tweet ID

timestamp — time of tweet

no_query — unused query value

username — Twitter handle

tweet — tweet content

## 🔁 Label Mapping
For binary classification:

Label 0 → Negative

Label 4 → Mapped to 1 (Positive)

## 🔧 Data Preprocessing
The preprocessing pipeline includes:

Mapping labels: 0 → 0 (negative), 4 → 1 (positive)

Cleaning tweet text by:

Removing URLs

Removing user mentions (@username)

Removing hashtags (#example)

Removing special characters and punctuation

Converting text to lowercase

Removing stop words

Removing numeric values

## 🛠 Text Transformation
### 1. Tokenization
Performed using the NLTK library to split tweets into individual tokens.

### 2. Normalization
Although no emoji/emoticons were present in this dataset, the pipeline is ready to handle them.

### Applied stemming/lemmatization to reduce words to their base forms (e.g., "running" → "run").

## 🔍 Modeling and Vectorization
We compared three text vectorization methods:

* TF-IDF
* GloVe (50d vectors)
* Bag of Words embeddings

# 🧪 Experimental Insights
## GloVe50 Vectorization
Aggressive preprocessing (removing stop words, punctuation, etc.) did not improve the model.
In fact, retaining some punctuation and stop words gave better performance.
(See notebook: logistic regression with GloVe50.ipynb for details.)

## Bag of Words Embeddings
Used to capture contextual meaning of tweets.
Required heavier computational resources.
(See notebook: logistic regression with BagOfWord.ipynb)

## TF-IDF (Best Performing)
Achieved the highest accuracy across multiple classifiers.
Lightweight, fast, and highly effective for this binary sentiment classification task.
Likely performed best because:
Tweets are short and sparse.
TF-IDF emphasizes unique, informative terms.
Simpler models benefited from interpretable features.
(See notebook: logistic regression with tf idf.ipynb)

## ✅ Conclusion
The TF-IDF approach outperformed (**81% accuracy**) both GloVe and BERT in this project. It’s well-suited for short text like tweets, and provides a strong baseline for sentiment classification with minimal computational cost.
