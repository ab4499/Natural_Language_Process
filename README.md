# Natural_Language_Process

Introduction and simple practice with NLP

![npl1](https://github.com/ab4499/Natural_Language_Process/blob/master/graphs/npl1.jpeg)

The use of natural language processing has exploded over the last decade. Appilcations that require machines to understand natural human speech patterns are abundant and substantial improvements in these systems has increased their utility. Within the educational space NLP is used to interpret human speech for the prupose of understanding human problems and recently an online tutor passed a limited version of the [Turing Test](https://en.wikipedia.org/wiki/Turing_test) when it was [indistinguishable from teaching assistants in a college class](https://www.news.gatech.edu/2017/01/09/jill-watson-round-three).

This project will process a set of documents, running a sentiment analysis of thise documents and then generating topic models of those documents. The documents we will be using will be student notes from a class. 

#### Import all document files and the list of weeks file

#### Clean the htlm tags from your text

#### Process text using the tm package

```{r}
#Convert the data frame to the corpus format that the tm package uses
corpus <- Corpus(VectorSource(D1$Notes2))
#Remove spaces
corpus <- tm_map(corpus, stripWhitespace)
#Convert to lower case
corpus <- tm_map(corpus, tolower)
#Remove pre-defined stop words ('the', 'a', etc)
corpus <- tm_map(corpus, removeWords, stopwords('english'))
#Convert words to stems ("education" = "edu") for analysis, for more info see  http://tartarus.org/~martin/PorterStemmer/
corpus <- tm_map(corpus, stemDocument)
#Remove numbers
corpus <- tm_map(corpus, removeNumbers)
#remove punctuation
corpus <- tm_map(corpus, removePunctuation)
#Convert to plain text for mapping by wordcloud package
corpus <- tm_map(corpus, PlainTextDocument, lazy = TRUE)

#Convert corpus to a term document matrix - so each word can be analyzed individuallly
tdm.corpus <- TermDocumentMatrix(corpus)

#Note: we won't remove plural words here, plural words in English tend to be highly irregular and difficult to extract reliably
```

What processing steps are being conducted here? Why is this important? Are there any other steps need to be taken to process your text before analyzing?

Above, we are processing text using the tm package. We first convert data frame to corpus format. Then we remove the spaces, convert to lower case, re-define stop words and convert words to stem and etc. Only after processing the text, can we use it for further analysis. 
Some general steps to prepare text for analysis:
-Tokenization: break up a string of sharacters into semantically meaningful parts that can be analyzed.
-Categorization: assign a grammatical category to the tokens that have been detected
-Parsing (Dependency parsing & Constituency parsing): determining the syntactic structure of a text
-Lemmatization and stemming-remove all of the affixes (i.e. suffixes, prefixes, etc.) attached to a word
-Stopword Removal-remove from play all the words that are very frequent but provide very little semantic information or no meaning at all.


#### Find common words

The most common word in the text:

![common_word](https://github.com/ab4499/Natural_Language_Process/blob/master/graphs/common_words.png "github")

Word count:

![word_count](https://github.com/ab4499/Natural_Language_Process/blob/master/graphs/word_count.png "github")

#### Generate a Word Cloud

![word_cloud](https://github.com/ab4499/Natural_Language_Process/blob/master/graphs/Word_cloud.png "github")

#### Merge with week list
#### Generate a visualization of the sum of the sentiment score over weeks

![sentiment](https://github.com/ab4499/Natural_Language_Process/blob/master/graphs/Sentiment.png "github")

#### LDA Topic Modelling

Using the same csv file you have generated the LDA analysis will treat each row of the data frame as a document. 

#### Generate a visualization showing: 

- Sentiment for each week and 

- One important topic for that week

![sentiment_topic](https://github.com/ab4499/Natural_Language_Process/blob/master/graphs/Sentiment_topic.png "github")



## Relevant Materials

[Nadkarni, P. M., Ohno-Machado, L., & Chapman, W. W. (2011). Natural language processing: An Introduction. Journal of the American Medical Informatics Association: JAMIA, 18(5), 544–551.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3168328/)

[Robinson, A. C. (2015). Exploring Class Discussions from a Massive Open Online Course (MOOC) on Cartography. In J. Brus, A. Vondrakova, & V. Vozenilek (Eds.), Modern Trends in Cartography (pp. 173–182). Springer International Publishing.](https://link-springer-com.ezproxy.cul.columbia.edu/chapter/10.1007/978-3-319-07926-4_14)

[McNamara, D. S., Crossley, S. A., & Roscoe, R. (2013). Natural Language Processing in an Intelligent Writing Strategy Tutoring System. Behavior Research Methods, 45(2), 499–515.](https://link-springer-com.ezproxy.cul.columbia.edu/article/10.3758/s13428-012-0258-1)

[Crash Course. (2017). Natural Language Processing.](https://www.youtube.com/watch?v=fOvTtapxa9c)

[Raval, S. (2016). Sentiment Analysis in 4 Minutes.](https://www.youtube.com/watch?v=AJVP96tAWxw)

[Knispelis, A. (2016). LDA Topic Models.](https://www.youtube.com/watch?v=3mHy4OSyRf0)
