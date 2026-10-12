1. bag of words
![unnamed_a8cc61f14b444816b38847b6abf4926c](unnamed_a8cc61f14b444816b38847b6abf4926c.png)
- word order is not accounted for, only frequency
- can be represented as vectors
- elements:
   - Term Frequency (TF)
   - Document Frequency (DF)
   - query-document matching score

2. vector space model
![unnamed_d80066c65fb04898919304a0a0f01afd](unnamed_d80066c65fb04898919304a0a0f01afd.png)
- terms are axes of space
- documents are vectors in this space
- very high-dimensional
- very sparse (most entries are zero)

3. Term Frequency (TF)
- number of times a term appears in a document
- relevance does not increase proportionally with term frequency => use log
![unnamed_fb13f2a6ca954cc696acdffcb192cbf3](unnamed_fb13f2a6ca954cc696acdffcb192cbf3.png)

4. Inverse Document Frequency (IDF)
- based on idea that rare terms are more informative than frequent terms
- represents inverse of number of documents that contain the term
IDF~t~ = log~x~(N/df~t~)

5. tf-idf weighting
w~td~ = (1+log(tf~td~)*log(N/df~t~)
- w~td~: weight assigned to term t in document d
- tf~td~: number of term t in document d
- N: number of documents
- df~t~: number of documents with term t

6. query-document match
- represent queries as vectors in vector space
- rank documents according to proximity to query

7. cosine as proximity
- lower the angle, higher the cosine value
![unnamed_45e22a31ff024519b83a257afee6e972](unnamed_45e22a31ff024519b83a257afee6e972.png)
- cosine similarity can be used to measure proximity

8. normalizing vector length
- divide each component by vector's length (L2 norm)
![unnamed_7b7021b07c0f48e0a0cb315258a7a379](unnamed_7b7021b07c0f48e0a0cb315258a7a379.png)

9. tf-idf walkthrough
- calculate weight matrix
![unnamed_ee7589d9147a4581aff99011db8603f0](unnamed_ee7589d9147a4581aff99011db8603f0.png)
- normalize weight matrix
![unnamed_92cb9c6ac8e8497a9daf20da613356c3](unnamed_92cb9c6ac8e8497a9daf20da613356c3.png)
- match query with document
![unnamed_9973f93d798a4f67a09503d43eb56549](unnamed_9973f93d798a4f67a09503d43eb56549.png)

reference:
- Gachon University - Machine learning lecture