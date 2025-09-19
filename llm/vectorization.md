# Vectorization

In vectorization we transform words to vectors. Vectors are a numerical representation of data as a list of numbers. In order to create a vectorization of some input data one needs to run the data through a model that can generate these vectors. An example of such a model can be ``text-embedding-ada-002``.

A good use case for vectorization is search. This happens in a two step process: First, the data is vectorized with a vectorization model. Then the vecotrized data is stored in a search index. When searchring through the data, the search query is also vectorized. With this process it is possible to find relevant search results in large data sets and optimal performance. 