# Finding-Copycat-News-Sites
This project finds similar news articles among turkish news sites between February 2018 - May 2018. It clusters similar web sites together. 

## The Algorithm
LSH (Locality Sensitive Hashing) was used in order to find the similar news articles that are similar above threshold 40%. The parameters of such as number of bands **b** and number of hash functions **h** can be adjusted such that the similarity threshold is changed.Threshold ~ (1/b)^(b/h)

Jaccard Similarity metric was used in the min-hashing phase.

## Optimization and Parallelization of LSH Algorithm
The regular [LSH algorithm ](http://www.cs.bilkent.edu.tr/~mustafa.ozdal/cs425/slides/lecture4_lsh_applications.pdf) takes 3 days to find similarities between 200.000 news articles(300mb of text). Therefore, MapReduce was used in order to fasten the process. Apache Beam libraries were used to implement the MapReduce implementation of LSH algorithm.This way, the task of finding similar artices is parallelized and reduced to 15 minutes from 3 days in terms of time.

## Simple invocation of Program
For a small dataset that includes plagiarised text
```
python corpus_lsh.py

```
For news dataset:

```
python news_lsh.py

```
