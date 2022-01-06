## Find best fit candidates for a role using NLP

Companies are looking to hire personnel that are best fit for their job requirements from the vast number
of applicants that post their resume on sites like Linkedin. They want to get access to best aligned
candidates, with just keyword searches like 'Aspiring human resources' or 'Seeking english teacher'.

### Who benefits?
Any company who would like to catagorize their pool of resumes to find and aggregate best fit
candidates from search strings thus bypassing manually allocating resumes for further evaluation.
The keyword strings used to access the best fit candidates can be succinct and improved to get accessed
to best candidates for the job requirements.

## Dataset
The data comes from sourcing efforts. Removed any field that could directly reveal personal details and
gave a unique identifier for each candidate.

## Data Wrangling
The data had no missing data and about 50% of the data was duplicate and so removed duplicate records

## Text Preprocessing
To do preprocessing, regular expression and nltk libraries was used to remove any punctuation, digits, removal of commonly occurring words and then lowercase the text. And the text was tokenized.

## Exploratory Data Analysis
To verify the preprocessing, a word cloud using the wordcloud package is plotted to get a visual
representation of most common words.

A document term matrix is created with CountVectorizer and plotted to find the most frequent data found
in the entire text of the job titles.

In order to better understand words that can be pairs of two consecutive words, plotting bigrams here
can be useful to understand whether we need to consider consecutive words like 'human resources' or
'new york' together as a term in our modelling to get better results

## Data Modeling
Data modeling is done using Gensim library, which is an open source library in python written by Radim
Rehurek and is used in unsupervised topic modelling and natural language processing. </br>
It is designed to extract semantic topics from documents. It can handle large text collections. Hence it
makes it different from other machine learning software packages which target memory processing.
Gensim also provides efficient multicore implementations for various algorithms to increase processing
speed. </br>
Gensim allows to build corpus (collection of texts) and dictionaries using simple classes and functions.

## Topic Modeling
Topic Modeling refers to the probabilistic modeling of text documents as topics. Topic modeling is a
family of techniques that can be used to describe and summarize the documents in a corpus according to
a set of latent "topics. 

Used both Latent Semantic Indexing(LSI) and Latent Dirichlet Allocation (LDA) for topic modeling

## Doc2Vec
Doc2Vec is a Model that represents each Document as a Vector.
In Gensim, Paragraph Vector model is referred as Doc2Vec.
Paragraph Vector - Distributed Memory (PV-DM) Paragraph Vector - Distributed Bag of Words (PVDBOW) PV-DM is analogous to Word2Vec CBOW. The doc-vectors are obtained by training a neural
network on the synthetic task of predicting a center word based an average of both context word-vectors
and the full document's doc-vector.
