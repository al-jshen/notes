# Attention

## Attention is all you need {cite:p}`Vaswani2017`

- attention is a mechanism that allows a model to focus on relevant parts of the input
  \begin{align}
  \text{Attention}(Q, K, V) = \text{softmax}(\frac{QK^T}{\sqrt{d_k}})V
  \end{align}
- attention maps can be pulled out of the model after the softmax and visualized to see which parts of the input the model is focusing on
- multi-head attention (MHA) splits the input into multiple heads and applies attention to each of them in parallel, then concatenates the outputs and projects them back down to the original dimension, allowing you to focus on information from multiple representation subspaces at once
- self-attention is attention where $Q$, $K$, and $V$ are all the same
- attention is permutation invariant, so you need to add positional encodings to the input if you want to preserve order
- implementation in PyTorch: use `F.scaled_dot_product_attention`, which attends over the second last dimension (the other dimensions can be whatever you want)
- standard flow: embed input, add positional encodings, pass through Transformer blocks, pass through output head

## Attention variants

- ReAttention {cite:p}`Zhou2021`: mix the attention head outputs with a linear layer (after softmax) before multiplying with values, which solves the problem of attention collapse, which is when (deep) ViTs learn attention maps that are similar to each other and so do not scale well with depth
  \begin{align}
  \text{ReAttention}(Q, K, V) = \text{Norm}(\theta^T(\text{softmax}(\frac{QK^T}{\sqrt{d_k}})))V
  \end{align}

# Vision Transformers

## Vision Transformers {cite:p}`Dosovitskiy2020`

- ViTs are Transformers applied to images by splitting the image into patches, flattening them into a sequence of patches, embedding each patch into some higher dimensional space, then applying a standard transformer to the sequence
- ViTs have much less inductive bias than CNNs, and spatial relations are learned through the positional embeddings, so ViTs tend to need more data to train
- MLP layers are local and translationally equivariant, and the self-attention layers are global

## Axial attention {cite:p}`Ho2019`

- axial attention works efficiently on high dimensional arrays (e.g., 3 spatial dimensions) by splitting the sequence into multiple axes and applying attention to each axis in parallel rather than patching the array (which quickly becomes unfeasible with $N^2$ scaling in high dimensions)
- implement by reshaping the input to put the axis you want to attend over in the second last position, then applying standard attention, then reshaping the input back, and repeating for each axis you want to attend over, and summing all the inputs

```{bibliography}
  :filter: docname in docnames
```
