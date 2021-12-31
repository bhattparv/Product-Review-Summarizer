# Product Reviews Summarizer

**Version 1.0.0**

A quick guide on installation of important libraries and running the code.

The project has three .ipynb files - Data Scraper.ipynb, cosine-similarity-wo-tf-idf.ipynb, and cosine-similarity-w-tf-idf.ipynb.

---

## Data Scraper

For the Data Scraper python script, we need to import the following three libraries - [requests](https://pypi.org/project/requests/), [BeautifulSoup](https://pypi.org/project/beautifulsoup4/), and [pandas](https://pandas.pydata.org/docs/getting_started/install.html). The installation process can be viewed by clicking on the respective library names.


### Splash
In this project, instead of using the default web browser to scrape data, we have created a splash container using docker. Splash is a light-weight javascript rendering service with an HTTP API. For easy installation, you can watch this amazing video by John Watson Rooney on YouTube.

https://www.youtube.com/watch?v=8q2K41QC2nQ&t=361s

> **Note:** You need to make sure that you give the **Splash Localhost URL** to the requests.get().

### Running the code
After you have installed and configured everything, you can run the code by providing the URL of your choice. Suppose, you are taking a product from [Amazon](https://www.amazon.com/), make sure to go to **All Reviews** page and go to page #2. Copy this URL upto the last '=' and paste it as an f-string in the code. Add a '{x}' after the '='. The code is ready to run. It will scrape the product name, review title, star rating, and the review body from each page, until the last page is encountered, and save it in .xlsx format.

> **Note:** Specify the required output name and destination.

---

## cosine-similarity-wo-tf-idf

For the cosine similarity model, first we need to download the pretrained [GloVe Word Embeddings](http://nlp.stanford.edu/data/glove.6B.zip). Run the Load GloVe Word Embeddings section in the script once. It is only required if the kernel is restarted.

For this script, we need to import the following libraries - [numpy](https://numpy.org/install/), [pandas](https://pandas.pydata.org/docs/getting_started/install.html), [nltk](https://www.nltk.org/install.html), [nltk.tokenize](https://www.nltk.org/api/nltk.tokenize.html), [nltk.corpus](https://www.nltk.org/api/nltk.corpus.html), [re](https://docs.python.org/3/library/re.html), [sklearn.metrics.pairwise](https://scikit-learn.org/stable/install.html), [networkx](https://networkx.org/documentation/networkx-1.1/install.html), [transformers](https://huggingface.co/docs/transformers/installation), and [time](https://docs.python.org/3/library/time.html). Also run the nltk.download('punkt') and nltk.download('stopwords') lines to download them.

Next step is to load the data as a dataframe. Make sure to give the correct address. Pre-processing of the reviews is done for efficient results. The pre-processing steps include converting to string datatype, converting alphabetical characters to lowercase, removing stopwords, replacing non-alphabetical characters with blank character and tokenizing the sentences.

The pre-processed data is then grouped based on star ratings and sent to the cosine similarity and pagerank algorithm. The top 10 ranked sentences after the applying the pagerank algorithm are sent to huggingface transformers to create an extractive summary (min_lenght = 75, max_length = 300). The summary, along with the product name, star rating, no of reviews, % of total reviews, and the top 5 frequent words along with the count are saved in .xlsx format.

> **Note:** Specify the required output name and destination.

---

## cosine-similarity-w-tf-idf

For this model, along with the above libraries, we need to import the following additional libraries - [spacy](https://spacy.io/usage), and [heapq](https://docs.python.org/3/library/heapq.html). The cosine similarity algorithm has a time complexity of O(n^2). In order to have a fast execution, in this method, we are using tf-idf measure to score the frequent words, and hence the corresponding sentences. Only the top 1000 sentences are then sent to the cosine similarity algorithm. Usage of the tf-idf measure, ensures that each product, irrespective of the number of sentences in the reviews, gives an output within 120 seconds. This method makes sure no important feature is lost, giving similar results as the previous method but in considerately less time.

---

## Contributors

© Parv Bhatt
© Namratha Sri Mateti
© Dominic Thomas






```python

```
