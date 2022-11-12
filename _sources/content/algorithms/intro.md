# Algorithms

Things that I find interesting and/or useful.

## Hierarchical Navigable Small Worlds (HNSW)

- extremely fast vector similarity search ((approximate) nearest neighbor) algorithm
- combines probability skip lists with navigable small worlds (NSW)
  - probability skip lists are made of multiple layers of linked lists, where the top layers are more coarsely connected (i.e., longer connections, faster to traverse, less accurate) and the lower layers are more finely connected
  - navigable small worlds are graphs with vertices separated by a combination of short and long links
    - (logarithmic) search process is done greedily: start at some entry vertex and keep traversing to the connected vertex which is closest to the search point
    - stop when no connected vertices are closer to the search point than the current vertex (local minimum)
    - can increase network connectivity (number of connections per node) to increase recall at the cost of speed
- HNSW use the layer structure of probability skip lists, and in each layer there is a NSW
- ![hnsw](../figures/hnsw.png)
- paper: {cite:t}`Malkov2020`, FAISS: {cite:t}`Johnson2017`, <https://www.pinecone.io/learn/hnsw>

```{bibliography}
  :filter: docname in docnames
```
