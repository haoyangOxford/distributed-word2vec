## Distributed training of Word2Vec
Distributed training of a word embedding model (Word2vec) for large vocabularies

### Quick Start
(instructions added later)

### Project Idea 
Many modern natural language (NLP) models rely on word embeddings. Embeddings are vectors of various sizes (ranging from 50 to 1000 floats most usually) that represent a given word. It is common for a word embedding model to be trained on very large corpuses of text, producing embeddings for a massive vocabulary. One popular model consists of 3 million vectors, each of length 300, trained on Wikipedia. Because these vectors are hugely helpful for Machine Learning, they have been extended to be used on other types of data, such as advertisement data. These datasets are even larger, which can make training hard, or even impossible. 


### Tech Stack
- Spark: distributed processing, fine-grained load balancing, failure recovery, in-memory operations
- Parameter Server (PS): Used typically for sync models, incremental updates during training, or sometimes even some vector math. In
![text here](https://github.com/haoyangOxford/distributed-word2vec/blob/master/parameter%20servers.png)

### Data Source
 - [Common Crawl](https://registry.opendata.aws/commoncrawl/): A corpus of web crawl data composed of over 25 billion web pages hosted on AWS S3 Bucket and updated monthly
 - [Reddit data](https://bigquery.cloud.google.com/table/fh-bigquery:reddit_comments.all): Comments on Reddit Between 2005 - 2018.
 
### Engineering Challenge
Training word vectors on a single machine is a well studied problem. The goal of this project is to build a pipeline that is distributed to both:
Build vectors for sets that are too large to fit in memory (such as the ad dataset mentioned in the paper)
Have the ability to train many word vector models in parallel on multiple different datasets

## Business Value


### MVP
Build a scalable distributed training pipeline for word vectors, that can both train on very large datasets, and train as fast as possible. 


### Stretch Goals
As a stretch goal, expose an API where anyone can submit a large dataset (for example a link to an S3 bucket), and train embeddings on it. A good place to start would be by re-implementing this paper on Spark/Hadoop. You could for-example compare its results with a naive implementation of word vectors (in particular the one in SparkMlib, but they cite 4 different ones).

